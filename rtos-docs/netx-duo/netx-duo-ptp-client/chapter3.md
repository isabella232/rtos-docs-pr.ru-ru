---
title: Глава 3. Описание служб клиента PTP для NetX Duo в ОСРВ Azure
description: Эта глава содержит описание всех служб клиента PTP для NetX Duo в алфавитном порядке.
author: v-condav
ms.author: v-condav
ms.date: 01/27/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b4cdeca81c157934e35a219cd5535ec38f2c0746
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814588"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-ptp-client-services"></a>Глава 3. Описание служб клиента PTP для NetX Duo в ОСРВ Azure

Эта глава содержит описание всех служб клиента PTP для NetX Duo, которые перечислены ниже в алфавитном порядке.

[!NOTE]
> *В разделе **Возвращаемые значения** для приведенных ниже описаний функций API значения, **выделенные полужирным шрифтом**, не затрагиваются определением параметра **NX_DISABLE_ERROR_CHECKING**, используемым для отключения проверки ошибок API, в то время как значения без такого выделения полностью отключаются.*

## <a name="nx_ptp_client_create"></a>nx_ptp_client_create

Создание экземпляра клиента PTP.

### <a name="prototype"></a>Прототип

```C
UINT nx_ptp_client_create(
    NX_PTP_CLIENT *client_ptr, NX_IP *ip_ptr, 
    UINT interface_index,
    NX_PACKET_POOL *packet_pool_ptr, 
    UINT thread_priority, 
    UCHAR *thread_stack, 
    UINT stack_size,
    NX_PTP_CLIENT_CLOCK_CALLBACK clock_callback, 
    VOID *clock_callback_data);
```

### <a name="description"></a>Описание

Эта служба создает экземпляр клиента PTP.

Обратите внимание, что приложение должно сначала создать экземпляр IP-адреса и пул пакетов, чтобы клиент PTP мог передавать пакеты. Что касается пула пакетов, приложение может использовать тот же пул пакетов в экземпляре IP-адреса или создать выделенный пул пакетов для клиента PTP.  Подход с выделенным пулом пакетов имеет преимущество использования небольших пакетов (128 байт, если используется IPv6, или 108 байт, если используется только IPv4).

### <a name="input-parameters"></a>Входные параметры
* **client_ptr** — указатель на создаваемый клиент PTP.
* **ip_ptr** — указатель на экземпляр IP-адреса.
* **interface_index** — индекс сетевого интерфейса PTP.
* **packet_pool_ptr** — указатель на пул пакетов клиента.
* **thread_priority** — приоритет потока PTP.
* **thread_stack** — указатель на стек потоков.
* **stack_size** — размер стека потоков.
* **clock_callback** — обратный вызов тактового генератора PTP.
* **clock_callback_data** — данные для обратного вызова тактового генератора.

### <a name="return-values"></a>Возвращаемые значения
* **NX_SUCCESS** (0x00) — клиент успешно создан.
* **NX_PTP_CLIENT_INSUFFICIENT_PACKET_PAYLOAD** (0xD04) — слишком короткие полезные данные пакетов.
* **NX_PTP_CLIENT_CLOCK_CALLBACK_FAILURE** (0xD05) — сбой обратного вызова тактового генератора.
* **status** — состояние завершения вызовов служб NetX Duo и ThreadX.
* NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.
* NX_INVALID_INTERFACE (0x4C) — недопустимый интерфейс.

### <a name="allowed-from"></a>Допустимые источники
Потоки

### <a name="example"></a>Пример
```C
/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_delete"></a>nx_ptp_client_delete

Удаляет экземпляр клиента PTP.

### <a name="prototype"></a>Прототип

```C
UINT nx_ptp_client_delete(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет экземпляр клиента PTP.

### <a name="input-parameters"></a>Входные параметры
* **client_ptr** — указатель на удаляемый клиент PTP.

### <a name="return-values"></a>Возвращаемые значения
* **NX_SUCCESS** (0x00) — клиент успешно удален.
* NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники
Потоки

### <a name="example"></a>Пример
```C
/* Delete the PTP client instance */
status = nx_ptp_client_delete(&ptp_client);

/* If the client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_master_info_get"></a>nx_ptp_client_master_info_get

Получение сведений о главном тактовом генераторе.

### <a name="prototype"></a>Прототип

```C
UINT nx_ptp_client_master_info_get(
    NX_PTP_CLIENT_MASTER *master_ptr, 
    NXD_ADDRESS *address, 
    UCHAR **port_identity, 
    UINT *port_identity_length, 
    UCHAR *priority1, 
    UCHAR *priority2, 
    UCHAR *clock_class, UCHAR *clock_accuracy, 
    USHORT *clock_variance, 
    UCHAR **grandmaster_identity,
    UINT *grandmaster_identity_length, 
    USHORT *steps_removed, 
    UCHAR *time_source);
```

### <a name="description"></a>Описание
Эта служба получает сведения о главном тактовом генераторе. Основной блок управления передается пользовательскому приложению посредством функции обратного вызова события.

### <a name="input-parameters"></a>Входные параметры
* **master_ptr** — указатель на главный тактовый генератор PTP.
* **address** — адрес главного тактового генератора.
* **port_identity** — главный порт и главное удостоверение PTP.
* **port_identity_length** — длина главного порта и главного удостоверения PTP.
* **priority1** — приоритет Priority1 главного тактового генератора PTP.
* **priority2** — приоритет Priority2 главного тактового генератора PTP.
* **clock_class** — класс главного тактового генератора PTP.
* **clock_accuracy** — точность главного тактового генератора PTP.
* **clock_variance** — дисперсия главного тактового генератора PTP.
* **grandmaster_identity** — удостоверение тактового генератора-грандмастера.
* **grandmaster_identity_length** — длина удостоверения тактового генератора-грандмастера.
* **steps_removed** — шаги, удаленные из заголовка PTP.
* **time_source** — источник таймера, используемый тактовым генератором-грандмастером.

### <a name="return-values"></a>Возвращаемые значения
* **NX_SUCCESS** (0x00) — сведения о ведущем тактовом генераторе успешно получены.
* NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники
Потоки

### <a name="example"></a>Пример
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
NXD_ADDRESS address;
UCHAR *port_identity;
UINT port_identity_length;
UCHAR priority1, priority2;
UCHAR clock_class, clock_accuracy;
USHORT clock_variance;
UCHAR *grandmaster_identity;
UINT grandmaster_identity_length;
USHORT steps_removed;
UCHAR time_source;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_MASTER:
        {
            status = nx_ptp_client_master_info_get((NX_PTP_CLIENT_MASTER *)event_data, 
                                                   &address, &port_identity,
                                                   &port_identity_length, &priority1, 
                                                   &priority2, &clock_class,
                                                   &clock_accuracy, &clock_variance, 
                                                   &grandmaster_identity,
                                                   &grandmaster_identity_length, 
                                                   &steps_removed, &time_source);

            /* If the master clock information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_packet_timestamp_notify"></a>nx_ptp_client_packet_timestamp_notify

Уведомление клиента PTP о метке времени пакета.

### <a name="prototype"></a>Прототип

```C
VOID nx_ptp_client_packet_timestamp_notify(
    NX_PTP_CLIENT *client_ptr, 
    NX_PACKET *packet_ptr, 
    NX_PTP_TIME *timestamp_ptr);
```

### <a name="description"></a>Описание
Эта служба уведомляет клиент PTP о том, что пакет передается с меткой времени. Эта служба разработана для сетевого драйвера и вызывается при передаче пакета. Метка времени обычно создается оборудованием.

### <a name="input-parameters"></a>Входные параметры
* **client_ptr** — указатель на создаваемый клиент PTP.
* **packet_ptr** — указатель на передаваемый пакет PTP.
* **timestamp_ptr** — указатель на метку времени пакета PTP.

### <a name="return-values"></a>Возвращаемые значения
Нет

### <a name="allowed-from"></a>Допустимые источники
Потоки

### <a name="example"></a>Пример
```C
/* Call notification callback */
nx_ptp_client_packet_timestamp_notify(client_ptr, packet_ptr, &ts);
```

## <a name="nx_ptp_client_soft_clock_callback"></a>nx_ptp_client_soft_clock_callback

Программная реализация тактового генератора PTP.

### <a name="prototype"></a>Прототип

```C
UINT nx_ptp_client_soft_clock_callback(
    NX_PTP_CLIENT *client_ptr, 
    UINT operation,
    NX_PTP_TIME *time_ptr, 
    NX_PACKET *packet_ptr,
    VOID *callback_data);
```

### <a name="description"></a>Описание
Эта функция обратного вызова выступает в качестве источника имитированного тактового генератора низкого разрешения для PTP. Эта подпрограммы предоставляется только для справки и не может использоваться для рабочей среды.

### <a name="input-parameters"></a>Входные параметры
* **client_ptr** — указатель на создаваемый клиент PTP.
* **operation** — операция обратного вызова, допустимые значения определяются следующим образом:
  * **NX_PTP_CLIENT_CLOCK_INIT** — инициализация тактового генератора.
  * **NX_PTP_CLIENT_CLOCK_SET** — настройка текущей метки времени, которая задана `time_ptr`.
  * **NX_PTP_CLIENT_CLOCK_GET** — передача текущей метки времени в `time_ptr`.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_EXTRACT** — извлечение метки времени из `packet_ptr` в `time_ptr`.
  * **NX_PTP_CLIENT_CLOCK_ADJUST** — корректировка текущей метки времени менее чем на *1* секунду.
  * **NX_PTP_CLIENT_CLOCK_PACKET_TS_PREPARE** — отметка `packet_ptr`, предписывающая уведомить клиента PTP о метке времени при ее передаче.
  * **NX_PTP_CLIENT_CLOCK_SOFT_TIMER_UPDATE** — обновление программного таймера. Может игнорироваться аппаратными часами.
* **time_ptr** — указатель на метку времени.
* **packet_ptr** — указатель на пакет.
* **callback_data** — указатель на непрозрачные данные обратного вызова.

### <a name="return-values"></a>Возвращаемые значения
* **NX_SUCCESS** (0x00) — операция успешно выполнена.
* **NX_PTP_PARAM_ERROR** (0xD03) — недопустимый параметр.

### <a name="allowed-from"></a>Допустимые источники
Внутренняя часть PTP.

### <a name="example"></a>Пример
```C/* Create the PTP client instance */
status = nx_ptp_client_create(&ptp_client, &ip_0, 0, &pool_0, 
                              PTP_THREAD_PRIORITY, (UCHAR *)ptp_stack, sizeof(ptp_stack),
                              nx_ptp_client_soft_clock_callback, NX_NULL);

/* If the client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_start"></a>nx_ptp_client_start

Запуск клиента PTP.

### <a name="prototype"></a>Прототип

```C
UINT nx_ptp_client_start(
    NX_PTP_CLIENT *client_ptr, 
    UCHAR *client_port_identity_ptr, 
    UINT client_port_identity_length,
    UINT domain, 
    UINT transport_specific, 
    NX_PTP_CLIENT_EVENT_CALLBACK event_callback,
    VOID *event_callback_data)
```

### <a name="description"></a>Описание
Эта служба запускает ранее созданный экземпляр клиента PTP.

### <a name="input-parameters"></a>Входные параметры
* **client_ptr** — указатель на создаваемый клиент PTP.
* **client_port_identity_ptr** — указатель на порт и удостоверение клиента, может иметь значение NULL.
* **client_port_identity_length** — длина порта и удостоверения клиента. Она должна быть равна 0, если client_port_identity_ptr имеет значение NULL или NX_PTP_CLOCK_PORT_IDENTITY_SIZE (10)
* **domain** — домен таковых генераторов PTP.
* **transport_specific** — 4 бита, относящиеся к транспорту.
* **event_callback** — функция обратного вызова, вызванная для события.
* **event_callback_data** — данные для обратного вызова события.

### <a name="return-values"></a>Возвращаемые значения
* **NX_SUCCESS** (0x00) — клиент успешно запущен.
* **NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) — клиент PTP уже запущен.
* **status** — состояние завершения вызовов служб NetX Duo и ThreadX.
* NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники
Потоки

### <a name="example"></a>Пример
```C
status = nx_ptp_client_start(&ptp_client, NX_NULL, 0, 0, 0, ptp_event_callback, NX_NULL);

/* If the client was successfully started, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_stop"></a>nx_ptp_client_stop

Остановка клиента PTP.  После остановки клиент PTP не обрабатывает пакеты PTP и не передает их.

### <a name="prototype"></a>Прототип

```C
UINT nx_ptp_client_stop(NX_PTP_CLIENT *client_ptr);
```

### <a name="description"></a>Описание
Эта служба останавливает ранее созданный и запущенный экземпляр клиента PTP.

### <a name="input-parameters"></a>Входные параметры
* **client_ptr** — указатель на останавливаемый клиент PTP.

### <a name="return-values"></a>Возвращаемые значения
* **NX_SUCCESS** (0x00) — клиент успешно остановлен.
* **NX_PTP_CLIENT_NOT_STARTED** (0xD01) клиент не запущен.
* NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники
Потоки

### <a name="example"></a>Пример
```C
status = nx_ptp_client_stop(&ptp_client);

/* If the client was successfully stopped, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_sync_info_get"></a>nx_ptp_client_sync_info_get

Получение сведений о синхронизации.

### <a name="prototype"></a>Прототип

```C
UINT nx_ptp_client_sync_info_get(
    NX_PTP_CLIENT_SYNC *sync_ptr, 
    USHORT *flags, 
    SHORT *utc_offset);
```

### <a name="description"></a>Описание
Эта служба получает сведения о сообщении синхронизации. Блок управления синхронизацией передается пользовательскому приложению посредством функции обратного вызова события.

### <a name="input-parameters"></a>Входные параметры
* **client_ptr** — указатель на создаваемый клиент PTP.
* **flags** — флаги в сообщении синхронизации.
* **utc_offset** — смещение между TAI и UTC.

### <a name="return-values"></a>Возвращаемые значения
* **NX_SUCCESS** (0x00) — сведения о синхронизации успешно получены.
* NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники
Потоки

### <a name="example"></a>Пример
```C
static UINT ptp_event_callback(NX_PTP_CLIENT *ptp_client_ptr, UINT event, VOID *event_data, VOID *callback_data)
{
USHORT utc_offset;

    switch (event)
    {
        case NX_PTP_CLIENT_EVENT_SYNC:
        {
            nx_ptp_client_sync_info_get((NX_PTP_CLIENT_SYNC *)event_data, NX_NULL, &utc_offset);

            /* If the Sync information was successfully get, status = NX_SUCCESS. */
            break;
        }

        /* Other event process. */
    }
}
```

## <a name="nx_ptp_client_time_get"></a>nx_ptp_client_time_get

Получение текущего времени.

### <a name="prototype"></a>Прототип

```C
UINT nx_ptp_client_time_get(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a>Описание
Эта служба получает текущее значение тактового генератора PTP. Она доступна независимо от того, синхронизирован ли клиент PTP с главным тактовым генератором.

### <a name="input-parameters"></a>Входные параметры
* **client_ptr** — указатель на создаваемый клиент PTP.
* **time_ptr** — указатель на время PTP.

### <a name="return-values"></a>Возвращаемые значения
* **NX_SUCCESS** (0x00) — клиент успешно создан.
* NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники
Потоки

### <a name="example"></a>Пример
```C
/* Get the PTP clock */
nx_ptp_client_time_get(&ptp_client, &tm);
```

## <a name="nx_ptp_client_time_set"></a>nx_ptp_client_time_set

Задание текущего времени.

### <a name="prototype"></a>Прототип

```C
UINT nx_ptp_client_time_set(
    NX_PTP_CLIENT *client_ptr, 
    NX_PTP_TIME *time_ptr);
```

### <a name="description"></a>Описание
Эта служба задает текущее значение тактового генератора PTP. Она должна быть вызвана до запуска клиента PTP.

### <a name="input-parameters"></a>Входные параметры
* **client_ptr** — указатель на создаваемый клиент PTP.
* **time_ptr** — указатель на время PTP.

### <a name="return-values"></a>Возвращаемые значения
* **NX_SUCCESS** (0x00) — клиент успешно создан.
* **NX_PTP_CLIENT_ALREADY_STARTED** (0xD02) — клиент PTP уже запущен.
* NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники
Потоки

### <a name="example"></a>Пример
```C
/* Set current time before PTP client started.  */
status = nx_ptp_client_time_set(&ptp_client, &tm);
```

## <a name="nx_ptp_client_utility_convert_time_to_date"></a>nx_ptp_client_utility_convert_time_to_date

Преобразование времени PTP в дату и время в формате UTC.

### <a name="prototype"></a>Прототип

```C
UINT nx_ptp_client_utility_convert_time_to_date(
    NX_PTP_TIME *time_ptr, 
    LONG offset, 
    NX_PTP_DATE_TIME *date_time_ptr);
```

### <a name="description"></a>Описание
Эта служба преобразует время PTP в дату и время в формате UTC.

### <a name="input-parameters"></a>Входные параметры
* **time_ptr** — указатель на время PTP.
* **offset** — второе смещение со знаком, добавляемое ко времени PTP.
* **date_time_ptr** — указатель на результирующую дату.

### <a name="return-values"></a>Возвращаемые значения
* **NX_SUCCESS** (0x00) — клиент успешно создан.
* **Указатель на результирующую дату** (0xD03) — недопустимый параметр.
* NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники
Потоки

### <a name="example"></a>Пример
```C
/* convert PTP time to UTC date and time */
status = nx_ptp_client_utility_convert_time_to_date(&tm, -ptp_utc_offset, &date);

/* If the time was successfully converted, status = NX_SUCCESS. */
```

## <a name="nx_ptp_client_utility_time_diff"></a>nx_ptp_client_utility_time_diff

Разница между двумя значениями времени PTP.

### <a name="prototype"></a>Прототип

```C
UINT nx_ptp_client_utility_time_diff(
    NX_PTP_TIME *time1_ptr, 
    NX_PTP_TIME *time2_ptr, 
    NX_PTP_TIME *result_ptr);
```

### <a name="description"></a>Описание
Эта служба рассчитывает разницу между двумя значениями времени PTP.

### <a name="input-parameters"></a>Входные параметры
* **time1_ptr** — указатель на первое время PTP.
* **time2_ptr** — указатель на второе время PTP.
* **result_ptr** — указатель на разность первого и второго значений времени.

### <a name="return-values"></a>Возвращаемые значения
* **NX_SUCCESS** (0x00) — клиент успешно создан.
* NX_PTR_ERROR (0x07) — недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники
Потоки

### <a name="example"></a>Пример
```C
/* Diff time.  */
status = nx_ptp_client_utility_time_diff(&time1, &time2, &result);

/* If the calculation was successfully, status = NX_SUCCESS. */
```