---
title: Глава 5. Создание буферов трассировки
description: В этой главе описано, как создать буфер событий в TraceX для ОСРВ Azure, а также содержатся сведения о базовом формате буфера.
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 7d5c90675728fc7e374d625f5a9ae27340268ca8398200c68fb7113a84aa2983
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801790"
---
# <a name="chapter-5---generating-trace-buffers"></a>Глава 5. Создание буферов трассировки

В этой главе описано, как создать буфер событий в TraceX для ОСРВ Azure, а также содержатся сведения о базовом формате буфера.

## <a name="threadx-event-trace-support"></a>Поддержка трассировки событий в ThreadX

ThreadX предоставляет встроенную поддержку трассировки событий для всех служб ThreadX, изменений состояния потоков и определяемых пользователем событий. Возможность отслеживания событий ThreadX в основном разработана как средство заключительного анализа, позволяющее анализировать последние n действий в приложении. С помощью этих сведений разработчик может выявить проблемы и (или) потенциальные цели для оптимизации.

TraceX графически отображает буфер трассировки событий, созданный ThreadX. Ниже описано, как создать буфер, а также приведены сведения о базовом формате буфера.

## <a name="enabling-event-trace"></a>Включение трассировки событий

Чтобы включить трассировку событий, определите константы метки времени, создайте библиотеку ThreadX с заданным параметром **TX_ENABLE_EVENT_TRACE** и включите трассировку, вызвав функцию **tx_trace_enable**.

## <a name="defining-time-stamp-constants"></a>Определение констант метки времени

Константы метки времени предназначены для предоставления разработчику элемента контроля над меткой времени, используемой в записях трассировки событий. Ниже показано две константы метки времени и их значения по умолчанию.

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ++_tx_trace_simulated_time
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK   0xFFFFFFFFUL
#endif
```

Указанные выше константы определяются в файле **tx_port. h** и создают "фиктивную" метку времени, которая просто увеличивается на единицу при каждом событии. Ниже приведен пример фактического определения метки времени.

```c
#ifndef TX_TRACE_TIME_SOURCE
#define TX_TRACE_TIME_SOURCE ((ULONG) 0x0x13000004)
#endif
#ifndef TX_TRACE_TIME_MASK
#define TX_TRACE_TIME_MASK 0xFFFFFFFFUL
#endif
```

Приведенные выше константы задают 32-разрядный таймер, полученный путем считывания адреса 0x13000004. Большинство меток времени конкретного приложения следует настраивать аналогичным образом.

## <a name="exporting-the-trace-buffer"></a>Экспорт буфера трассировки

Для TraceX требуется буфер трассировки в двоичном формате, шестнадцатеричном формате Intel или формате файла Motorola S-Record на узле. Самый простой способ сделать это — приостановить работу целевого объекта и настроить отладчик для создания дампа области памяти, которую вы указали для функции ***tx_trace_enable*** в файле на узле.

> [!WARNING]
>***Следите за тем, чтобы не остановить целевой объект в самом коде, собирающем трассировку. Это может привести к недопустимым данным трассировки. Если программа остановлена в ThreadX, то перед созданием дампа буфера трассировки лучше выполнить шаг с обходом любым макросом вставки трассировки.***

> [!IMPORTANT]
> *В приложении D показано, как создать дамп буфера трассировки с помощью различных средств разработки.*

## <a name="extended-event-trace-api"></a>API трассировки расширенных событий

Если ThreadX создан с заданным параметром **TX_ENABLE_EVENT_TRACE**, то для приложения доступны следующие новые API-интерфейсы трассировки событий:

- tx_trace_enable — *включение трассировки событий.*
- tx_trace_event_filter — *фильтрация указанных событий.*
- tx_trace_event_unfilter — *отмена фильтрации указанных событий.*
- tx_trace_disable — *отключение трассировки событий.*
- tx_trace_isr_enter_insert — *вставка события трассировки входа в ISR.*
- tx_trace_isr_exit_insert — *вставка события трассировки выхода ISR.*
- tx_trace_buffer_full_notify — *регистрация обратного вызова приложения для информирования о заполнении буфера трассировки.*
- tx_trace_user_event_insert — *вставка пользовательского события.*

### <a name="tx_trace_enable"></a>tx_trace_enable

Включение трассировки событий

#### <a name="prototype"></a>Прототип

```c
UINT tx_trace_enable (VOID *trace_buffer_start,
     ULONG trace_buffer_size, ULONG registry_entries);
```

#### <a name="description"></a>Описание
Эта служба включает трассировку событий в ThreadX. Приложение предоставляет буфер трассировки и максимальное количество объектов ThreadX.

> [!IMPORTANT]
> Для использования трассировки событий библиотеку ThreadX и приложение необходимо создавать с заданным параметром **TX_ENABLE_EVENT_TRACE**.

#### <a name="input-parameters"></a>Входные параметры

- **trace_buffer_start** — указатель на начало буфера трассировки, предоставляемого пользователем.
- **trace_buffer_size** — общее количество байтов в памяти для буфера трассировки. Чем больше буфер трассировки, тем больше записей в нем можно хранить.
- **registry_entries** — количество объектов приложения ThreadX, которые необходимо сохранить в реестре трассировки. Реестр используется для сопоставления адресов объектов с именами объектов. Это очень удобно для средств анализа трассировки графического пользовательского интерфейса.

#### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное включение трассировки событий.
- **TX_SIZE_ERROR** (0x05) — указанный размер буфера трассировки слишком мал. Он должен вмещать заголовок трассировки, реестр объектов и хотя бы одну запись трассировки.
- **TX_NOT_DONE** (0x20) — трассировка событий уже включена.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включенной трассировкой.

#### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

#### <a name="example"></a>Пример

```c
UCHAR my_trace_buffer[64000];

/* Enable event tracing using the global "my_trace_buffer" memory and supporting a maximum of 30 ThreadX objects in the registry. */
status = tx_trace_enable (&my_trace_buffer, 64000, 30);

/* If status is TX_SUCCESS the event tracing is enabled. */
```

#### <a name="see-also"></a>См. также:

tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert.

### <a name="tx_trace_event_filter"></a>tx_trace_event_filter

Фильтрация указанных событий

#### <a name="prototype"></a>Прототип

```c
UINT tx_trace_event_filter (ULONG  vent_filter_bits);
```

#### <a name="description"></a>Описание

Эта служба фильтрует указанные события от вставки в активный буфер трассировки. Обратите внимание, что по умолчанию события не отфильтрованы после вызова *tx_trace_enable*.

> [!IMPORTANT]
> Для использования трассировки событий библиотеку ThreadX и приложение необходимо создавать с заданным параметром **TX_ENABLE_EVENT_TRACE**.

#### <a name="input-parameters"></a>Входные параметры

- **event_filter_bits** — биты, соответствующие фильтруемым событиям. Несколько событий можно отфильтровать простой операцией ИЛИ вместе с соответствующими константами. Допустимые константы для этой переменной определяются следующим образом:

```c
TX_TRACE_ALL_EVENTS                   0x000007FF
TX_TRACE_INTERNAL_EVENTS              0x00000001
TX_TRACE_BLOCK_POOL_EVENTS            0x00000002
TX_TRACE_BYTE_POOL_EVENTS             0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS           0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT      0x00000010
TX_TRACE_MUTEX_EVENTS                 0x00000020
TX_TRACE_QUEUE_EVENTS                 0x00000040
TX_TRACE_SEMAPHORE_EVENTS             0x00000080
TX_TRACE_THREAD_EVENTS                0x00000100
TX_TRACE_TIME_EVENTS                  0x00000200
TX_TRACE_TIMER_EVENTS                 0x00000400
FX_TRACE_ALL_EVENTS                   0x00007800
FX_TRACE_INTERNAL_EVENTS              0x00000800
FX_TRACE_MEDIA_EVENTS                 0x00001000
FX_TRACE_DIRECTORY_EVENTS             0x00002000
FX_TRACE_FILE_EVENTS                  0x00004000
NX_TRACE_ALL_EVENTS                   0x00FF8000
NX_TRACE_INTERNAL_EVENTS              0x00008000
NX_TRACE_ARP_EVENTS                   0x00010000
NX_TRACE_ICMP_EVENTS                  0x00020000
NX_TRACE_IGMP_EVENTS                  0x00040000
NX_TRACE_IP_EVENTS                    0x00080000
NX_TRACE_PACKET_EVENTS                0x00100000
NX_TRACE_RARP_EVENTS                  0x00200000
NX_TRACE_TCP_EVENTS                   0x00400000
NX_TRACE_UDP_EVENTS                   0x00800000
UX_TRACE_ALL_EVENTS                   0x7F000000
UX_TRACE_ERRORS                       0x01000000
UX_TRACE_HOST_STACK_EVENTS            0x02000000
UX_TRACE_DEVICE_STACK_EVENTS          0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS       0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS     0x10000000
UX_TRACE_HOST_CLASS_EVENTS            0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS          0x40000000
```

#### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS**: (0x00) — успешное применение фильтра событий.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включенной трассировкой.

#### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

#### <a name="example"></a>Пример

```c
/* Filter queue and byte pool events from trace buffer. */

status = tx_trace_event_filter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are filtered. */
```

#### <a name="see-also"></a>См. также:

tx_trace_enable, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert.

### <a name="tx_trace_event_unfilter"></a>tx_trace_event_unfilter

Отмена фильтрации указанных событий

#### <a name="prototype"></a>Прототип

```c
UINT tx_trace_event_unfilter (ULONG event_unfilter_bits);
```

#### <a name="description"></a>Описание

Эта служба отменяет фильтрацию указанных событий, поэтому они будут вставлены в активный буфер трассировки.

> [!IMPORTANT]
> Для использования трассировки событий библиотеку ThreadX и приложение необходимо создавать с заданным параметром **TX_ENABLE_EVENT_TRACE**.

#### <a name="input-parameters"></a>Входные параметры

- **event_unfilter_bits** — биты, соответствующие нефильтруемым событиям. Фильтрацию нескольких событий можно отменить простой операцией ИЛИ вместе с соответствующими константами. Допустимые константы для этой переменной определяются следующим образом:

```c
TX_TRACE_ALL_EVENTS                  0x000007FF
TX_TRACE_INTERNAL_EVENTS             0x00000001
TX_TRACE_BLOCK_POOL_EVENTS           0x00000002
TX_TRACE_BYTE_POOL_EVENTS            0x00000004
TX_TRACE_EVENT_FLAGS_EVENTS          0x00000008
TX_TRACE_INTERRUPT_CONTROL_EVENT     0x00000010
TX_TRACE_MUTEX_EVENTS                0x00000020
TX_TRACE_QUEUE_EVENTS                0x00000040
TX_TRACE_SEMAPHORE_EVENTS            0x00000080
TX_TRACE_THREAD_EVENTS               0x00000100
TX_TRACE_TIME_EVENTS                 0x00000200
TX_TRACE_TIMER_EVENTS                0x00000400
FX_TRACE_ALL_EVENTS                  0x00007800
FX_TRACE_INTERNAL_EVENTS             0x00000800
FX_TRACE_MEDIA_EVENTS                0x00001000
FX_TRACE_DIRECTORY_EVENTS            0x00002000
FX_TRACE_FILE_EVENTS                 0x00004000
NX_TRACE_ALL_EVENTS                  0x00FF8000
NX_TRACE_INTERNAL_EVENTS             0x00008000
NX_TRACE_ARP_EVENTS                  0x00010000
NX_TRACE_ICMP_EVENTS                 0x00020000
NX_TRACE_IGMP_EVENTS                 0x00040000
NX_TRACE_IP_EVENTS                   0x00080000
NX_TRACE_PACKET_EVENTS               0x00100000
NX_TRACE_RARP_EVENTS                 0x00200000
NX_TRACE_TCP_EVENTS                  0x00400000
NX_TRACE_UDP_EVENTS                  0x00800000
UX_TRACE_ALL_EVENTS                  0x7F000000
UX_TRACE_ERRORS                      0x01000000
UX_TRACE_HOST_STACK_EVENTS           0x02000000
UX_TRACE_DEVICE_STACK_EVENTS         0x04000000
UX_TRACE_HOST_CONTROLLER_EVENTS      0x08000000
UX_TRACE_DEVICE_CONTROLLER_EVENTS    0x10000000
UX_TRACE_HOST_CLASS_EVENTS           0x20000000
UX_TRACE_DEVICE_CLASS_EVENTS         0x40000000
```

#### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS**: (0x00) — успешная отмена фильтрации событий.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включенной трассировкой.

#### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

#### <a name="example"></a>Пример

```c
/* Un-filter queue and byte pool events from trace buffer. */ 
status = 
  tx_trace_event_unfilter (TX_TRACE_QUEUE_EVENTS | TX_TRACE_BYTE_POOL_EVENTS);

/* If status is TX_SUCCESS all queue and byte pool events are un-filtered. */
```

#### <a name="see-also"></a>См. также:

tx_trace_enable, tx_trace_event_filter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert.

### <a name="tx_trace_disable"></a>tx_trace_disable

#### <a name="disable-event-tracing"></a>Отключение трассировки событий

#### <a name="prototype"></a>Прототип

```c
UINT tx_trace_disable (VOID);
```

#### <a name="description"></a>Описание

Эта служба отключает трассировку событий в ThreadX. Это может пригодиться, если для приложения нужно заморозить текущий буфер трассировки событий и, возможно, передать его на внешний ресурс во время выполнения. После отключения можно вызвать **tx_trace_enable**, чтобы снова начать трассировку.

> [!IMPORTANT]
> Для использования трассировки событий библиотеку ThreadX и приложение необходимо создавать с заданным параметром **TX_ENABLE_EVENT_TRACE**.

#### <a name="input-parameters"></a>Входные параметры

Отсутствует.

#### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное отключение трассировки событий.
- **TX_NOT_DONE** (0x20) — трассировка событий не была включена.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включенной трассировкой.

#### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

#### <a name="example"></a>Пример 

```c
/* Disable event tracing. */ 
status = tx_trace_disable ();

/* If status is TX_SUCCESS the event tracing is disabled. */
```

#### <a name="see-also"></a>См. также:

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert.

### <a name="tx_trace_isr_enter_insert"></a>tx_trace_isr_enter_insert

#### <a name="insert-isr-enter-event"></a>Вставка события ввода ISR

#### <a name="prototype"></a>Прототип

```c
VOID tx_trace_isr_enter_insert (ULONG isr_id);
```

#### <a name="description"></a>Описание

Эта служба вставляет событие ввода ISR в буфер трассировки событий. Ее следует вызывать через приложение в начале обработки ISR. Заданный параметр должен определять конкретную ISR для приложения.

> [!IMPORTANT]
> Для использования трассировки событий библиотеку ThreadX и приложение необходимо создавать с заданным параметром **TX_ENABLE_EVENT_TRACE**.

#### <a name="input-parameters"></a>Входные параметры 
- **isr_id** — значение конкретного приложения для определения ISR.

#### <a name="return-values"></a>Возвращаемые значения

**None**

#### <a name="allowed-from"></a>Допустимые источники 

Подпрограммы ISR

#### <a name="example"></a>Пример

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */

status = tx_trace_isr_enter_insert (3);

/* If status is TX_SUCCESS the ISR entry event was inserted. */
```

#### <a name="see-also"></a>См. также:

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert.

### <a name="tx_trace_isr_exit_insert"></a>tx_trace_isr_exit_insert

#### <a name="insert-isr-exit-event"></a>Вставка события выхода ISR

#### <a name="prototype"></a>Прототип

```c
VOID tx_trace_isr_exit_insert (ULONG isr_id);
```

#### <a name="description"></a>Описание

Эта служба вставляет событие записи ISR в буфер трассировки событий. Ее следует вызывать через приложение в начале обработки ISR. Заданный параметр должен определять ISR для приложения.

> [!IMPORTANT]
> Для использования трассировки событий библиотеку ThreadX и приложение необходимо создавать с заданным параметром **TX_ENABLE_EVENT_TRACE**.

#### <a name="input-parameters"></a>Входные параметры 

- **isr_id** — значение конкретного приложения для определения ISR.

#### <a name="return-values"></a>Возвращаемые значения

**None**

#### <a name="allowed-from"></a>Допустимые источники

Подпрограммы ISR

#### <a name="example"></a>Пример

```c
/* Insert trace event to identify the application's ISR with an ID of 3. */ 

status = tx_trace_isr_exit_insert (3);

/* If status is TX_SUCCESS the ISR exit event was inserted. */
```

#### <a name="see-also"></a>См. также:

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_buffer_full_notify, tx_trace_user_event_insert.

### <a name="tx_trace_buffer_full_notify"></a>tx_trace_buffer_full_notify

#### <a name="register-trace-buffer-full-application-callback"></a>Регистрация обратного вызова приложения для информирования о заполнении буфера трассировки

#### <a name="prototype"></a>Прототип

```c
VOID tx_trace_buffer_full_notify (VOID (*full_buffer_callback)(VOID *));
```

#### <a name="description"></a>Описание

Эта служба регистрирует функцию обратного вызова приложения, вызываемую ThreadX при заполнении буфера трассировки. Затем приложение может отключить трассировку и (или) настроить новый буфер трассировки.

> [!IMPORTANT]
> Для использования трассировки событий библиотеку ThreadX и приложение необходимо создавать с заданным параметром **TX_ENABLE_EVENT_TRACE**.

#### <a name="input-parameters"></a>Входные параметры

- **full_buffer_callback** — функция приложения для вызова при заполнении буфера трассировки. Значение NULL отключает обратный вызов уведомления.

#### <a name="return-values"></a>Возвращаемые значения

**None**

#### <a name="allowed-from"></a>Допустимые источники

Подпрограммы ISR

#### <a name="example"></a>Пример

```c
y_trace_is_full(void *trace_buffer_start)

{

     /* Application specific processing goes here! */

}

/* Register the "my_trace_is_full" function to be called whenever the trace buffer fills. */

status = tx_trace_buffer_full_notify (my_trace_is_full);

/* If status is TX_SUCCESS the "my_trace_is_full" function is registered. */
```

#### <a name="see-also"></a>См. также:

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_user_event_insert.

### <a name="tx_trace_user_event_insert"></a>tx_trace_user_event_insert

#### <a name="insert-user-event"></a>Вставка пользовательского события

#### <a name="prototype"></a>Прототип

```c
UINT tx_trace_user_event_insert (ULONG event_id, 
   ULONG info_field_1, ULONG info_field_2,
   ULONG info_field_3, ULONG info_field_4);
```

#### <a name="description"></a>Описание

Эта служба вставляет пользовательское событие в буфер трассировки. Идентификаторы пользовательских событий должны быть больше константы **TX_TRACE_USER_EVENT_START**, которая определена со значением 4096. Максимальное пользовательское событие определяется константой **TX_TRACE_USER_EVENT_END** со значением 65535. Все события в этом диапазоне доступны для приложения. Поля сведений зависят от приложения.

> [!IMPORTANT]
> Для использования трассировки событий библиотеку ThreadX и приложение необходимо создавать с заданным параметром **TX_ENABLE_EVENT_TRACE**.

#### <a name="input-parameters"></a>Входные параметры

- **event_id** — идентификация события конкретного приложения должна начинаться со значения большего чем **TX_TRACE_USER_EVENT_START**, но не большего чем **TX_TRACE_USER_EVENT_END**.
- **info_field_1** — поле сведений конкретного приложения.
- **info_field_2** — поле сведений конкретного приложения.
- **info_field_3** — поле сведений конкретного приложения.
- **info_field_4** — поле сведений конкретного приложения.

#### <a name="return-values"></a>Возвращаемые значения
- **TX_SUCCESS** (0X00) — успешная вставка пользовательского события.
- **TX_NOT_DONE** (0x20) — трассировка событий не включена.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включенной трассировкой.

#### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

#### <a name="example"></a>Пример

```c
/* Insert user event 3000, with info fields of 1, 2, 3, 4. */ 

status = tx_trace_user_event_insert (3000, 1, 2, 3, 4);

/* If status is TX_SUCCESS the user event was inserted. */
```

#### <a name="see-also"></a>См. также:

tx_trace_enable, tx_trace_event_filter, tx_trace_event_unfilter, tx_trace_disable, tx_trace_isr_enter_insert, tx_trace_isr_exit_insert, tx_trace_buffer_full_notify.