---
title: Глава 4. Описание служб ThreadX для ОСРВ Azure
description: В этой главе содержится описание всех служб ThreadX для ОСРВ Azure в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dabc1603423d8422ed6f8f540f8a06e80d14ec0098c886ca8731ac8ce981f15d
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116783413"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-services"></a>Глава 4. Описание служб ThreadX для ОСРВ Azure

В этой главе содержится описание всех служб ThreadX для ОСРВ Azure в алфавитном порядке. Их имена сформированы таким образом, что все аналогичные службы группируются вместе. В разделе "Возвращаемые значения" приведенных ниже описаний **выделенные полужирным шрифтом** значения не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки ошибок API. Значения, не выделенные полужирным шрифтом, полностью отключены. Кроме того, слово "**Да**" под заголовком "**Возможно вытеснение**" указывает на то, что вызов службы может возобновить поток с более высоким приоритетом, что приведет к вытеснению вызывающего потока.

## <a name="tx_block_allocate"></a>tx_block_allocate

Выделение блока памяти фиксированного размера

### <a name="prototype"></a>Прототип

```c
UINT tx_block_allocate(
    TX_BLOCK_POOL *pool_ptr, 
    VOID **block_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба выделяет блок памяти фиксированного размера из указанного пула памяти. Фактический размер блока памяти определяется во время создания пула памяти.

> [!IMPORTANT]
> *Важно убедиться, что код приложения не выполняет запись за пределы выделенного блока памяти. Если это случится, произойдет повреждение в смежном (обычно последующем) блоке памяти. Результаты являются непредсказуемыми и часто неустранимыми.*

### <a name="parameters"></a>Параметры

- **pool_ptr** <br>Указатель на ранее созданный пул блоков памяти.
- **block_ptr** <br>Указатель на указатель блока назначения. При успешном выделении адрес выделенного блока памяти помещается в место, куда указывает этот параметр.
- **wait_option** <br>Определяет, как служба будет вести себя, если нет доступных блоков памяти. Параметры ожидания определяются следующим образом:
  - **TX_NO_WAIT** (0x00000000) — немедленный возврат из этой службы независимо от того, было ли выделение успешным. *Это единственный допустимый параметр, если служба вызывается из непотока, например инициализации, таймера или ISR*.
  - **TX_WAIT_FOREVER** (0xFFFFFFF) — вызывающий поток приостанавливается на неопределенное время, пока не станет доступен блок памяти.
  - *значение времени ожидания* (от 0x00000001 до 0xFFFFFFFE) — задать максимальное число тактов таймера для приостановки работы при ожидании блока памяти.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное выделение блока памяти.
- **TX_DELETED** (0x01) — пул блоков памяти был удален, пока поток был приостановлен.
- **TX_NO_MEMORY** (0x10) — службе не удалось выделить блок памяти в течение указанного времени ожидания.
- **TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.
- **TX_POOL_ERROR** (0x02) — недопустимый указатель на пул блоков памяти.
- **TX_WAIT_ERROR** (0x04) — в вызове из непотокового запроса был указан параметр ожидания, отличный от TX_NO_WAIT.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель на указатель назначения.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;

UINT status;

/* Allocate a memory block from my_pool. Assume that the pool has
already been created with a call to tx_block_pool_create. */

status = tx_block_allocate(&my_pool, (VOID **) &memory_ptr,
  TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the address of
the allocated block of memory. */
```

### <a name="see-also"></a>См. также:

- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_create"></a>tx_block_pool_create

Создание пула блоков памяти фиксированного размера

### <a name="prototype"></a>Прототип

```c
UINT tx_block_pool_create(
    TX_BLOCK_POOL pool_ptr,
    CHAR name_ptr, 
    ULONG block_size,
    VOID pool_start, 
    ULONG pool_size);
```

### <a name="description"></a>Описание

Эта служба создает пул блоков памяти фиксированного размера. Указанная область памяти разделяется на максимально возможное количество блоков памяти фиксированного размера по формуле:

**всего блоков** = (**всего байт**) / (**размер блока** + sizeof(void *))

> [!NOTE]
>* Каждый блок памяти содержит один указатель на служебные данные, который невидим для пользователя и представлен в предыдущей формуле членом "sizeof (void *)".*

### <a name="parameters"></a>Параметры

- **pool_ptr** — указатель на блок управления пулом блоков памяти.
- **name_ptr** — указатель на имя пула блоков памяти.
- **block_size** — число байтов в каждом блоке памяти.
- **pool_start** — начальный адрес пула блоков памяти. Начальный адрес должен быть выровнен по размеру типа данных ULONG.
- **pool_size** — общее число байт, доступных для пула блоков памяти.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное создание пула блоков памяти.
- **TX_POOL_ERROR** (0x02) — недопустимый указатель на пул блоков памяти. Либо указатель имеет значение NULL, либо пул уже создан.
- **TX_PTR_ERROR** (0x03) — недопустимый начальный адрес пула.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.
- **TX_SIZE_ERROR** (0x05) — недопустимый размер пула.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
TX_BLOCK_POOL my_pool;

UINT status;

/* Create a memory pool whose total size is 1000 bytes starting at
address 0x100000. Each block in this pool is defined to be 50 bytes
long. */
status = tx_block_pool_create(&my_pool, "my_pool_name",
  50, (VOID *) 0x100000, 1000);

/* If status equals TX_SUCCESS, my_pool contains 18 memory blocks
of 50 bytes each. The reason there are not 20 blocks in the pool is
because of the one overhead pointer associated with each block. */
```

### <a name="see-also"></a>См. также:

- tx_block_allocate, tx_block_pool_delete
- tx_block_pool_info_get, tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize, tx_block_release

## <a name="tx_block_pool_delete"></a>tx_block_pool_delete

Удаление пула блоков памяти

### <a name="prototype"></a>Прототип

```c
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет указанный пул блоков памяти. Все потоки, приостановленные в ожидании блока памяти из этого пула, возобновляются и получают состояние возврата **TX_DELETED**.

> [!NOTE]
> *За управление областью памяти, связанной с пулом, которая становится доступна после завершения этой службы,отвечает приложение. Кроме того, приложение должно предотвращать использование удаленного пула или его прежних блоков памяти.*

### <a name="parameters"></a>Параметры

- **pool_ptr** — указатель на ранее созданный пул блоков памяти.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное удаление пула блоков памяти.
- **TX_POOL_ERROR** (0x02) — недопустимый указатель на пул блоков памяти.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_BLOCK_POOL my_pool;

UINT           status;

/* Delete entire memory block
pool. Assume that the pool has already been created with a call to
tx_block_pool_create. */
status = tx_block_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, the memory block pool is deleted.*/
```

### <a name="see-also"></a>См. также:

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_info_get, tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize, tx_block_release

## <a name="tx_block_pool_info_get"></a>tx_block_pool_info_get

Получение сведений о пуле блоков

### <a name="prototype"></a>Прототип

```c
UINT tx_block_pool_info_get(
    TX_BLOCK_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *total_blocks,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BLOCK_POOL **next_pool);
```

### <a name="description"></a>Описание

Эта служба получает сведения об указанном пуле блоков памяти.

### <a name="parameters"></a>Параметры

- **pool_ptr** — указатель на ранее созданный пул блоков памяти.
- **name** — указатель на назначение для указателя на имя пула блоков.
- **available** — указатель на назначение для количества доступных блоков в пуле блоков.
- **total_blocks** — указатель на назначение для общего числа блоков в пуле блоков.
- **first_suspended** — указатель на назначение для указателя на поток, который находится первым в списке приостановки этого пула блоков.
- **suspended_count** — указатель на назначение для количества потоков, приостановленных в этом пуле блоков.
- **next_pool** — указатель на назначение для указателя следующего созданного пула блоков.

> [!NOTE]
> *Указание TX_NULL для любого параметра указывает, что это параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о пуле блоков.
- **TX_POOL_ERROR** (0x02) — недопустимый указатель на пул блоков памяти.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
TX_BLOCK_POOL my_pool;
CHAR *name;
ULONG available;
ULONG total_blocks;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BLOCK_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_block_pool_info_get(&my_pool, &name,
  &available,&total_blocks,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>См. также:

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get, tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize, tx_block_release

## <a name="tx_block_pool_performance_info_get"></a>tx_block_pool_performance_info_get

Получение сведений о производительности пула блоков

### <a name="prototype"></a>Прототип

```c
UINT tx_block_pool_performance_info_get(
    TX_BLOCK_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *suspensions, 
    ULONG *timeouts));
```

### <a name="description"></a>Описание

Эта служба получает сведения о производительности указанного пула блоков памяти.

> [!IMPORTANT]
> *Библиотека ThreadX и приложение должны быть построены с определенным параметром* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *, чтобы служба могла вернуть сведения о производительности.*

### <a name="parameters"></a>Параметры

- **pool_ptr** — указатель на ранее созданный пул блоков памяти.
- **allocates** — указатель на место назначения для количества запросов на выделение, выполненных в этом пуле.
- **releases** — указатель на место назначения для количества запросов на освобождение, выполненных в этом пуле.
- **suspensions** — указатель на место назначения для количества приостановок потоков для выделения в этом пуле.
- **timeouts** — указатель на место назначения для количества истечений времени ожидания во время приостановки для выделения в этом пуле.

>[!NOTE]
> *Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о производительности пула блоков.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель на пул блоков.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
TX_BLOCK_POOL my_pool;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created block
pool. */
status = tx_block_pool_performance_info_get(&my_pool, &allocates,
  &releases,
  &suspensions,
  &timeouts);

/* If status is TX_SUCCESS the performance information was successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_release

## <a name="tx_block_pool_performance_system_info_get"></a>tx_block_pool_performance_system_info_get

Получение сведений о производительности системы пулов блоков

### <a name="prototype"></a>Прототип

```c
UINT tx_block_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Описание

Эта служба получает сведения о производительности всех пулов блоков памяти в приложении.

> [!IMPORTANT]
> *Библиотека ThreadX и приложение должны быть построены с определенным параметром* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *, чтобы служба могла вернуть сведения о производительности.*

### <a name="parameters"></a>Параметры

- **allocates** — указатель на место назначения для общего количества запросов на выделение, выполненных во всех пулах блоков.
- **releases** — указатель на место назначения для общего количества запросов на освобождение, выполненных во всех пулах блоков.
- **suspensions** — указатель на место назначения для общего количества приостановок потоков для выделения во всех пулах блоков.
- **timeouts** — указатель на место назначения для общего количества истечений времени ожидания во время приостановки для выделения во всех пулах блоков.

> [!NOTE]
> *Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о производительности системы пулов блоков.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
ULONG       allocates;
ULONG       releases;
ULONG       suspensions;
ULONG       timeouts;

/* Retrieve performance information on all the block pools in
the system. */
status = tx_block_pool_performance_system_info_get(&allocates,
    &releases,&suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_prioritize
- tx_block_release

## <a name="tx_block_pool_prioritize"></a>tx_block_pool_prioritize

Назначение приоритета списку приостановки пула блоков

### <a name="prototype"></a>Прототип

```c
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a>Описание

Эта служба помещает поток с наивысшим приоритетом, приостановленный для блока памяти в этом пуле, в начале списка приостановки. Все остальные потоки остаются в том же порядке FIFO, в котором они были приостановлены.

### <a name="parameters"></a>Параметры

- **pool_ptr** — указатель на блок управления пулом блоков памяти.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное назначение приоритетов в пуле блоков.
- **TX_POOL_ERROR** (0x02) — недопустимый указатель на пул блоков памяти.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример
```c
TX_BLOCK_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free block in this pool. */
status = tx_block_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_block_release call will wake up this thread. */
```

### <a name="see-also"></a>См. также:

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_release

## <a name="tx_block_release"></a>tx_block_release

Освобождение блока памяти фиксированного размера

### <a name="prototype"></a>Прототип

```c
UINT tx_block_release(VOID *block_ptr);
``````

### <a name="description"></a>Описание

Эта служба освобождает ранее выделенный блок обратно в соответствующий пул памяти. Если один или несколько потоков приостановили работу в ожидании блоков памяти из этого пула, первый приостановленный поток получает этот блок памяти и возобновляет работу.

>[!IMPORTANT]
>*Приложение должно предотвратить использование области блока памяти после ее освобождения в пул.*

### <a name="parameters"></a>Параметры

- **block_ptr** — указатель на ранее выделенный блок памяти.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное освобождение блока памяти.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель на блок памяти.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_BLOCK_POOL my_pool;
unsigned char *memory_ptr;
UINT status;

/* Release a memory block back to my_pool. Assume that the
pool has been created and the memory block has been
allocated. */
status = tx_block_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the block of memory pointed
to by memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a>См. также:

- tx_block_allocate
- tx_block_pool_create
- tx_block_pool_delete
- tx_block_pool_info_get
- tx_block_pool_performance_info_get
- tx_block_pool_performance_system_info_get
- tx_block_pool_prioritize

## <a name="tx_byte_allocate"></a>tx_byte_allocate

Выделение байтов памяти

### <a name="prototype"></a>Прототип

```c
UINT tx_byte_allocate(
    TX_BYTE_POOL *pool_ptr,
    VOID **memory_ptr, 
    ULONG memory_size,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба выделяет указанное число байтов из указанного пула байтов памяти.

> [!IMPORTANT]
> *Важно убедиться, что код приложения не выполняет запись за пределы выделенного блока памяти. Если это случится, произойдет повреждение в смежном (обычно последующем) блоке памяти. Результаты являются непредсказуемыми и часто неустранимыми.*

> [!NOTE]
> *Производительность этой службы является функцией от размера блока и степени фрагментации в пуле. Таким образом, эта служба не должна использоваться во время критических по времени потоков выполнения.*

### <a name="parameters"></a>Параметры

- **pool_ptr** <br>Указатель на ранее созданный пул блоков памяти.
- **memory_ptr** <br>Указатель на указатель целевой памяти. При успешном выделении адрес выделенной области памяти помещается в место, куда указывает этот параметр.
- **memory_size** <br>Запрошенное число байтов.
- **wait_option** <br>Определяет, как работает служба, если объем доступной памяти недостаточен. Параметры ожидания определяются следующим образом:
  - **TX_NO_WAIT** (0x00000000) — немедленный возврат из этой службы независимо от того, было ли выполнение успешным. *Это единственный допустимый параметр, если служба вызывается из инициализации.*
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) — вызывающий поток приостанавливается на неопределенное время, пока не станет доступным достаточный объем памяти.
  - *значение времени ожидания* (от 0x00000001 до 0xFFFFFFFE) — задать максимальное число тактов таймера для приостановки работы при ожидании памяти.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное выделение памяти.
- **TX_DELETED** (0x01) — пул памяти был удален, пока поток был приостановлен.
- **TX_NO_MEMORY** (0x10) — службе не удалось выделить память в течение указанного времени ожидания.
- **TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.
- **TX_POOL_ERROR** (0x02) — недопустимый указатель на пул памяти.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель на указатель назначения.
- **TX_SIZE_ERROR** (0x05) — запрошенный размер равен нулю или больше размера пула.
- **TX_WAIT_ERROR** (0x04) — в вызове из непотокового запроса был указан параметр ожидания, отличный от TX_NO_WAIT.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример
```c
TX_BYTE_POOL my_pool;
unsigned char*memory_ptr;
UINT status;
/* Allocate a 112 byte memory area from my_pool. Assume
that the pool has already been created with a call to
tx_byte_pool_create. */
status = tx_byte_allocate(&my_pool, (VOID **) &memory_ptr,
    112, TX_NO_WAIT);

/* If status equals TX_SUCCESS, memory_ptr contains the
address of the allocated memory area. */
```

### <a name="see-also"></a>См. также:

- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_create"></a>tx_byte_pool_create

Создание пула памяти в байтах

### <a name="prototype"></a>Прототип

```c
UINT tx_byte_pool_create(
    TX_BYTE_POOL *pool_ptr,
    CHAR *name_ptr, 
    VOID *pool_start,
    ULONG pool_size);
```

### <a name="description"></a>Описание

Эта служба создает пул байтов памяти в указанной области. Изначально пул состоит из одного очень большого свободного блока. Однако при выделении памяти пул разбивается на более мелкие блоки.

### <a name="parameters"></a>Параметры

- **pool_ptr** — указатель на блок управления пулом памяти.
- **name_ptr** — указатель на имя пула памяти.
- **pool_start** — начальный адрес пула памяти. Начальный адрес должен быть выровнен по размеру типа данных ULONG.
- **pool_size** — общее число байт, доступных для пула памяти.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное создание пула памяти.
- **TX_POOL_ERROR** (0x02) — недопустимый указатель на пул памяти. Либо указатель имеет значение NULL, либо пул уже создан.
- **TX_PTR_ERROR** (0x03) — недопустимый начальный адрес пула.
- **TX_SIZE_ERROR** (0x05) — недопустимый размер пула.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Create a memory pool whose total size is 2000 bytes
starting at address 0x500000. */
status = tx_byte_pool_create(&my_pool, "my_pool_name",
    (VOID *) 0x500000, 2000);

/* If status equals TX_SUCCESS, my_pool is available for
allocating memory. */
```

### <a name="see-also"></a>См. также:

- tx_byte_allocate
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_delete"></a>tx_byte_pool_delete

Удаление пула байтов памяти

### <a name="prototype"></a>Прототип

```c
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет указанный пул байтов памяти. Все потоки, приостановленные в ожидании памяти из этого пула, возобновляются и получают состояние возврата **TX_DELETED**.

> [!IMPORTANT]
> *За управление областью памяти, связанной с пулом, которая становится доступна после завершения этой службы,отвечает приложение. Кроме того, приложение должно предотвращать использование удаленного пула или памяти, выделенной из него ранее.*

### <a name="parameters"></a>Параметры

- **pool_ptr** — указатель на ранее созданный пул памяти.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное удаление пула памяти.
- **TX_POOL_ERROR** (0x02) — недопустимый указатель на пул памяти.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Delete entire memory pool. Assume that the pool has already
been created with a call to tx_byte_pool_create. */
status = tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```

### <a name="see-also"></a>См. также:

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_info_get"></a>tx_byte_pool_info_get

Получение сведений о пуле байтов

### <a name="prototype"></a>Прототип

```c
UINT tx_byte_pool_info_get(
    TX_BYTE_POOL *pool_ptr, 
    CHAR **name,
    ULONG *available, 
    ULONG *fragments,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_BYTE_POOL **next_pool);
```

### <a name="description"></a>Описание

Эта служба получает сведения об указанном пуле байтов памяти.

### <a name="parameters"></a>Параметры

- **pool_ptr** — указатель на ранее созданный пул памяти.
- **name** — указатель на назначение для указателя на имя пула байтов.
- **available** — указатель на назначение для количества доступных байтов в пуле.
- **fragments** — указатель на место назначения для общего числа фрагментов памяти в пуле байтов.
- **first_suspended** — указатель на назначение для указателя на поток, который находится первым в списке приостановки этого пула байтов.
- **suspended_count** — указатель на назначение для количества потоков, приостановленных в этом пуле байтов.
- **next_pool** — указатель на назначение для указателя следующего созданного пула байтов.

> [!NOTE]
> *Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о пуле.
- **TX_POOL_ERROR** (0x02) — недопустимый указатель на пул памяти.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
TX_BYTE_POOL my_pool;
CHAR *name;
ULONG available;
ULONG fragments;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_BYTE_POOL *next_pool;
UINT status;

/* Retrieve information about the previously created
block pool "my_pool." */
status = tx_byte_pool_info_get(&my_pool, &name,
  &available, &fragments,
  &first_suspended, &suspended_count,
  &next_pool);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>См. также:

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_performance_info_get"></a>tx_byte_pool_performance_info_get

Получение сведений о производительности пула байтов

### <a name="prototype"></a>Прототип

```c
UINT tx_byte_pool_performance_info_get(
    TX_BYTE_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *fragments_searched, 
    ULONG *merges, 
    ULONG *splits,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Описание

Эта служба получает сведения о производительности указанного пула байтов памяти.

> [!IMPORTANT]
> *Библиотека ThreadX и приложение должны быть построены с определенным параметром* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *, чтобы служба могла вернуть сведения о производительности.*

### <a name="parameters"></a>Параметры

- **pool_ptr** — указатель на ранее созданный пул байтов памяти.
- **allocates** — указатель на место назначения для количества запросов на выделение, выполненных в этом пуле.
- **releases** — указатель на место назначения для количества запросов на освобождение, выполненных в этом пуле.
- **fragments_searched** — указатель на место назначения для количества фрагментов внутренней памяти, найденных во время запросов на выделение в этом пуле.
- **merges** — указатель на место назначения для количества внутренних блоков памяти, объединенных во время запросов на выделение в этом пуле.
- **splits** — указатель на место назначения для количества разделенных блоков внутренней памяти (фрагментов), созданных во время запросов на выделение в этом пуле.
- **suspensions** — указатель на место назначения для количества приостановок потоков для выделения в этом пуле.
- **timeouts** — указатель на место назначения для количества истечений времени ожидания во время приостановки для выделения в этом пуле.

> [!NOTE]
> *Указание TX_NULL для любого параметра указывает, что это параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о производительности пула байтов.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель на пул байтов.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
TX_BYTE_POOL my_pool;
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created byte
pool. */
status = tx_byte_pool_performance_info_get(&my_pool,
  &fragments_searched,
  &merges, &splits,
  &allocates, &releases,
  &suspensions,&timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```
### <a name="see-also"></a>См. также:

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_performance_system_info_get"></a>tx_byte_pool_performance_system_info_get

Получение сведений о производительности системы пула байтов

### <a name="prototype"></a>Прототип

```c
UINT tx_byte_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *fragments_searched, 
    ULONG *merges,
    ULONG *splits, 
    ULONG *suspensions, 
    ULONG *timeouts);
```
### <a name="description"></a>Описание

Эта служба получает сведения о производительности всех пулов байтов памяти в системе.

> [!IMPORTANT]
> *Библиотека ThreadX и приложение должны быть построены с определенным параметром* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *, чтобы служба могла вернуть сведения о производительности.*

### <a name="parameters"></a>Параметры

- **allocates** — указатель на место назначения для количества запросов на выделение, выполненных в этом пуле.
- **releases** — указатель на место назначения для количества запросов на освобождение, выполненных в этом пуле.
- **fragments_searched** — указатель на место назначения для общего количества фрагментов внутренней памяти, найденных во время запросов на выделение во всех пулах байтов.
- **merges** — указатель на место назначения для общего количества внутренних блоков памяти, объединенных во время запросов на выделение во всех пулах байтов.
- **splits** — указатель на место назначения для общего количества разделенных блоков внутренней памяти (фрагментов), созданных во время запросов на выделение во всех пулах байтов.
- **suspensions** — указатель на место назначения для общего количества приостановок потоков для выделения во всех пулах байтов.
- **timeouts** — указатель на место назначения для общего количества истечений времени ожидания во время приостановки для выделения во всех пулах байтов.

> [!NOTE]
> *Указание TX_NULL для любого параметра указывает, что это параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о производительности пула байтов.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.

### <a name="allowed-from"></a>Допустимые источники

 Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
ULONG fragments_searched;
ULONG merges;
ULONG splits;
ULONG allocates;
ULONG releases;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all byte pools in the
system. */
status =
tx_byte_pool_performance_system_info_get(&fragments_searched,
  &merges, &splits, &allocates, &releases,
  &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_prioritize
- tx_byte_release

## <a name="tx_byte_pool_prioritize"></a>tx_byte_pool_prioritize

Назначение приоритета списку приостановки пула байтов

### <a name="prototype"></a>Прототип

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a>Описание

Эта служба размещает поток с наивысшим приоритетом, приостановленный для выделения памяти в этом пуле, в начале списка приостановки. Все остальные потоки остаются в том же порядке FIFO, в котором они были приостановлены.

### <a name="parameters"></a>Параметры

- **pool_ptr** — указатель на блок управления пулом памяти.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное назначение приоритетов в пуле памяти.
- **TX_POOL_ERROR** (0x02) — недопустимый указатель на пул памяти.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
TX_BYTE_POOL my_pool;
UINT status;

/* Ensure that the highest priority thread will receive
the next free memory from this pool. */
status = tx_byte_pool_prioritize(&my_pool);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_byte_release call will wake up this thread,
if there is enough memory to satisfy its request. */
```

### <a name="see-also"></a>См. также:

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_release

## <a name="tx_byte_release"></a>tx_byte_release

Выход байтов обратно в пул памяти

### <a name="prototype"></a>Прототип

```c
UINT tx_byte_release(VOID *memory_ptr);
```

### <a name="description"></a>Описание

Эта служба освобождает ранее выделенную память обратно в соответствующий пул. Если один или несколько потоков приостановили работу в ожидании памяти из этого пула, то каждому приостановленному потоку выделяется память и он возобновляет работу. Этот процесс продолжается, пока не исчерпается память или не закончатся все приостановленные потоки. Этот процесс выделения памяти для приостановленных потоков всегда начинается с первого приостановленного потока.

> [!IMPORTANT]
> *Приложение должно предотвращать использование области памяти после ее освобождения.*

### <a name="parameters"></a>Параметры

- **memory_ptr** — указатель на ранее выделенную область памяти.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное освобождение памяти.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель на область памяти.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
unsigned char *memory_ptr;
UINT status;

/* Release a memory back to my_pool. Assume that the memory
area was previously allocated from my_pool. */
status = tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a>См. также:

- tx_byte_allocate
- tx_byte_pool_create
- tx_byte_pool_delete
- tx_byte_pool_info_get
- tx_byte_pool_performance_info_get
- tx_byte_pool_performance_system_info_get
- tx_byte_pool_prioritize

## <a name="tx_event_flags_create"></a>tx_event_flags_create

Создание группы флагов событий

### <a name="prototype"></a>Прототип

```c
UINT tx_event_flags_create(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR *name_ptr);
```

### <a name="description"></a>Описание

Эта служба создает группу из 32 флагов событий. Все 32 флага событий в группе инициализируются значением 0. Каждый флаг события представлен одним битом.

### <a name="parameters"></a>Параметры

- **group_ptr** — указатель на блок управления группы флагов событий.
- **name_ptr** — указатель на имя группы флагов событий.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное создание группы событий.
- **TX_GROUP_ERROR** (0x06) — недопустимый указатель на группу событий. Либо указатель имеет значение **NULL**, либо группа событий уже создана.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
TX_EVENT_FLAGS_GROUP my_event_group;
UINT status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
  "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
for get and set services. */
```

### <a name="see-also"></a>См. также:

- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_delete"></a>tx_event_flags_delete

Удаление группы флагов событий

### <a name="prototype"></a>Прототип

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет указанную группу флагов событий. Все потоки, приостановленные в ожидании событий из этой группы, возобновляются и получают состояние возврата TX_DELETED.

>[!IMPORTANT]
> *Перед удалением группы флагов событий приложение должно убедиться, что обратный вызов уведомления об установке значения для этой группы флагов событий завершен (или отключен). Кроме того, приложение должно предотвращать все будущие использования удаленной группы флагов событий.*

### <a name="parameters"></a>Параметры

- **group_ptr** — указатель на ранее созданную группу флагов событий.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное удаление группы флагов событий.
- **TX_GROUP_ERROR** (0x06) — недопустимый указатель на группу флагов событий.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Delete event flags group. Assume that the group has
already been created with a call to
tx_event_flags_create. */
status = tx_event_flags_delete(&my_event_flags_group);

/* If status equals TX_SUCCESS, the event flags group is
deleted. */
```

### <a name="see-also"></a>См. также:

- tx_event_flags_create
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_get"></a>tx_event_flags_get

Получение флагов событий из группы флагов событий

### <a name="prototype"></a>Прототип

```c
UINT tx_event_flags_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG requested_flags, 
    UINT get_option,
    ULONG *actual_flags_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба получает флаги событий из указанной группы флагов событий. Каждая группа флагов событий содержит 32 флага событий. Каждый флаг представлен одним битом. Эта служба может получать различные сочетания флагов событий, указанные входными параметрами.

### <a name="parameters"></a>Параметры

- **group_ptr** <br>Указатель на ранее созданную группу флагов событий.
- **requested_flags** <br>32-разрядная переменная без знака, представляющая флаги запрошенных событий.
- **get_option** <br>Указывает, требуются ли все или некоторые из запрошенных флагов событий. Допустимые значения:

  - **TX_AND** (0x02)
  - **TX_AND_CLEAR** (0x03)
  - **TX_OR** (0x00)
  - **TX_OR_CLEAR** (0x01)

    TX_AND или TX_AND_CLEAR указывают, что все флаги событий должны присутствовать в группе. TX_OR или TX_OR_CLEAR указывают, что какой-либо флаг события удовлетворяет условию. Если указаны TX_AND_CLEAR или TX_OR_CLEAR, то флаги событий, которые соответствуют запросу, очищаются (устанавливается значение 0).

- **actual_flags_ptr** <br>Указатель на место назначения, куда помещаются извлеченные флаги событий. Обратите внимание, что фактически получаемые данные могут содержать флаги, которые не были запрошены.
- **wait_option**  <br>Определяет, как служба ведет себя, если не заданы выбранные флаги событий. Параметры ожидания определяются следующим образом:
  - **TX_NO_WAIT** (0x00000000) — немедленный возврат из этой службы независимо от того, было ли выполнение успешным. Это единственный допустимый параметр, если служба вызывается из непотока, например инициализации, таймера или ISR.
  - **TX_WAIT_FOREVER** (значение времени ожидания 0xFFFFFFFF) — вызывающий поток приостанавливается на неопределенное время, пока флаги событий не станут доступными.
  - значение времени ожидания (от 0x00000001 до 0xFFFFFFFE) — задать максимальное число тактов таймера для приостановки работы при ожидании флагов событий.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение флагов событий.
- **TX_DELETED** (0x01) — группа флагов событий была удалена, пока поток был приостановлен.
- **TX_NO_EVENTS** (0x07) — службе не удалось получить указанные события в течение заданного времени ожидания.
- **TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.
- **TX_GROUP_ERROR** (0x06) — недопустимый указатель на группу флагов событий.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель для фактических флагов событий.
- **TX_WAIT_ERROR** (0x04) — в вызове из непотокового запроса был указан параметр ожидания, отличный от TX_NO_WAIT.
- **TX_OPTION_ERROR** (0x08) — указан недопустимый параметр get_option.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
ULONG actual_events;
UINT status;

/* Request that event flags 0, 4, and 8 are all set. Also,
if they are set they should be cleared. If the event
flags are not set, this service suspends for a maximum of
20 timer-ticks. */
status = tx_event_flags_get(&my_event_flags_group, 0x111,
    TX_AND_CLEAR, &actual_events, 20);

/* If status equals TX_SUCCESS, actual_events contains the
actual events obtained. */
```

**См. также:**

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

### <a name="tx_event_flags_info_get"></a>tx_event_flags_info_get

Получение сведений о группе флагов событий

**Прототип**

```c
UINT tx_event_flags_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR **name, ULONG *current_flags,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_EVENT_FLAGS_GROUP **next_group);
```

**Описание**

Эта служба получает сведения об указанной группе флагов событий.

**Параметры**

- **group_ptr** — указатель на блок управления группы флагов событий.
- **name** — указатель на назначение для указателя на имя группы флагов событий.
- **current_flags** — указатель на назначение для текущего набора флагов в группе флагов событий.
- **first_suspended** — указатель на назначение для указателя на поток, который находится первым в списке приостановки этой группы флагов событий.
- **suspended_count** — указатель на назначения для количества потоков, приостановленных в этой группе флагов событий.
- **next_group** — указатель на назначение для указателя следующей созданной группы флагов событий.

> [!NOTE]
> *Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений группы событий.
- **TX_GROUP_ERROR** (0x06) — недопустимый указатель на группу событий.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
TX_EVENT_FLAGS_GROUP my_event_group;
CHAR *name;
ULONG current_flags;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_EVENT_FLAGS_GROUP *next_group;
UINT status;

/* Retrieve information about the previously created
event flags group "my_event_group." */
status = tx_event_flags_info_get(&my_event_group, &name,
    &current_flags,
    &first_suspended, &suspended_count,
    &next_group);
/* If status equals TX_SUCCESS, the information requested is
valid. */
```
**См. также:**

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

### <a name="tx_event_flags_performance_info_get"></a>tx_event_flags_performance_info_get

Получение сведений о производительности группы флагов событий

### <a name="prototype"></a>Прототип

```c
UINT tx_event_flags_performance_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG *sets, ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Описание

Эта служба получает сведения о производительности указанной группы флагов событий.

> [!IMPORTANT]
> *Библиотека ThreadX и приложение должны быть построены с определенным параметром* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *, чтобы служба могла вернуть сведения о производительности.*

### <a name="parameters"></a>Параметры

- **group_ptr** — указатель на ранее созданную группу флагов событий.
- **sets** — указатель на место назначения для числа запросов на установку флагов событий в этой группе.
- **gets** — указатель на место назначения для числа запросов на получение флагов событий в этой группе.
- **suspensions** — указатель на место назначения для количества приостановок потоков для получения флагов событий в этой группе.
- **timeouts** — указатель на место назначения для количества истечений времени ожидания во время приостановки для получения флагов событий в этой группе.

> [!NOTE]
> *Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о производительности группы флагов событий.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель на группу флагов событий.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
TX_EVENT_FLAGS_GROUP my_event_flag_group;
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created event
flag group. */
status = tx_event_flags_performance_info_get(&my_event_flag_group,
    &sets, &gets, &suspensions,
    &timeouts);

/* If status is TX_SUCCESS the performance information was successfully
retrieved. */
```

### <a name="see-also"></a>См. также:

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_performance_system_info_get"></a>tx_event_flags_performance_system_info_get

Получение сведений о производительности системы

### <a name="prototype"></a>Прототип

```c
UINT tx_event_flags_performance_system_info_get(
    ULONG *sets,
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Описание

Эта служба получает сведения о производительности всех групп флагов событий в системе.

> [!IMPORTANT]
> *Библиотека ThreadX и приложение должны быть построены с определенным параметром* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *, чтобы служба могла вернуть сведения о производительности.*

### <a name="parameters"></a>Параметры

- **sets** — указатель на место назначения для общего числа запросов на установку флагов событий во всех группах.
- **gets** — указатель на место назначения для общего числа запросов на получение флагов событий во всех группах.
- **suspensions** — указатель на место назначения для общего количества приостановок потоков для получения флагов событий во всех группах.
- **timeouts** — указатель на место назначения для общего количества истечений времени ожидания во время приостановки для получения флагов событий во всех группах.

> [!NOTE]
> *Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о производительности системы флагов событий.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.

### <a name="example"></a>Пример

```c
ULONG sets;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created event
flag groups. */
status = tx_event_flags_performance_system_info_get(&sets, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_set
- tx_event_flags_set_notify

## <a name="tx_event_flags_set"></a>tx_event_flags_set

Установка флагов событий в группе флагов событий

### <a name="prototype"></a>Прототип

```c
UINT tx_event_flags_set(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG flags_to_set,
    UINT set_option);
```

### <a name="description"></a>Описание

Эта служба устанавливает или очищает флаги событий в группе флагов событий в зависимости от указанного параметра установки. Все приостановленные потоки, чей запрос флагов событий удовлетворен, возобновляются.

### <a name="parameters"></a>Параметры

- **group_ptr** <br>Указатель на ранее созданный блок управления группы флагов событий.
- **flags_to_set** <br>Указание флагов событий, которые необходимо задать или очистить в зависимости от указанного параметра set_option.
- **set_option** <br>Указывает, связаны ли указанные флаги событий операциями И или ИЛИ с текущими флагами событий группы. Допустимые значения:
  - **TX_AND** (0x02)
  - **TX_OR** (0x00)

  Указание TX_AND указывает, что указанные флаги событий связываются операцией **И** с текущими флагами событий в группе. Этот параметр часто используется для очистки флагов событий в группе. В противном случае, если указан параметр TX_OR, указанные флаги событий объединяются логическим **ИЛИ** с текущими флагами событий в группе.

### <a name="return-values"></a>Возвращаемые значения
- **TX_SUCCESS** (0x00) — успешная установка флагов событий.
- **TX_GROUP_ERROR** (0x06) — недопустимый указатель на группу флагов событий.
- **TX_OPTION_ERROR** (0x08) — указан недопустимый параметр set_option.

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_EVENT_FLAGS_GROUP my_event_flags_group;
UINT status;

/* Set event flags 0, 4, and 8. */
status = tx_event_flags_set(&my_event_flags_group,
    0x111, TX_OR);

/* If status equals TX_SUCCESS, the event flags have been
set and any suspended thread whose request was satisfied
has been resumed. */
```

### <a name="see-also"></a>См. также:

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set_notify

## <a name="tx_event_flags_set_notify"></a>tx_event_flags_set_notify

Уведомление приложения, когда установлены флаги событий

### <a name="prototype"></a>Прототип

```c
UINT tx_event_flags_set_notify(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```

### <a name="description"></a>Описание

Эта служба регистрирует функцию обратного вызова уведомлений, которая вызывается, когда один или несколько флагов событий задаются в указанной группе флагов событий. Обработка обратного вызова уведомления определяется приложением

### <a name="parameters"></a>Параметры
- **group_ptr** — указатель на ранее созданную группу флагов событий.
- **events_set_notify** — указатель на функцию приложения для уведомления о задании флагов событий. Если это значение равно TX_NULL, уведомление отключено.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная регистрация уведомлений задания флагов событий.
- **TX_GROUP_ERROR** (0x06) — недопустимый указатель на группу флагов событий.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система была скомпилирована с отключенными возможностями уведомлений.

### <a name="example"></a>Пример

```c
TX_EVENT_FLAGS_GROUP my_group;

/* Register the "my_event_flags_set_notify" function for monitoring
event flags set in the event flags group "my_group." */
status = tx_event_flags_set_notify(&my_group, my_event_flags_set_notify);

/* If status is TX_SUCCESS the event flags set notification function
was successfully registered. */
void my_event_flags_set_notify(TX_EVENT_FLAGS_GROUP *group_ptr)

/* One or more event flags was set in this group! */
```

### <a name="see-also"></a>См. также:

- tx_event_flags_create
- tx_event_flags_delete
- tx_event_flags_get
- tx_event_flags_info_get
- tx_event_flags_performance_info_get
- tx_event_flags_performance_system_info_get
- tx_event_flags_set

## <a name="tx_interrupt_control"></a>tx_interrupt_control

Включение и отключение прерываний

### <a name="prototype"></a>Прототип

```c
UINT tx_interrupt_control(UINT new_posture);
```

### <a name="description"></a>Описание

Эта служба включает или отключает прерывания, как указано во входном параметре *new_posture*.

> [!NOTE]
> *Если эта служба вызывается из потока приложения, то уровень прерывания остается частью контекста этого потока. Например, если поток вызывает эту подпрограмму для отключения прерываний, а затем приостанавливает работу, то прерывания снова отключаются.*

> [!WARNING]
> *Эта служба не должна использоваться для включения прерываний во время инициализации. Это может привести к непредсказуемым результатам.*

### <a name="parameters"></a>Параметры

- **new_posture** — этот параметр указывает, отключены или включены прерывания. Допустимые значения: **TX_INT_DISABLE** и **TX_INT_ENABLE**. Фактические значения для этих параметров зависят от порта. Кроме того, некоторые архитектуры обработки могут поддерживать дополнительные варианты отключения прерываний.

### <a name="return-values"></a>Возвращаемые значения
- **Предыдущее состояние** — эта служба возвращает вызывающему объекту предыдущее состояние прерываний. Это позволяет пользователям службы восстанавливать предыдущее состояние после отключения прерываний.

### <a name="allowed-from"></a>Допустимые источники

Потоки, таймеры и подпрограммы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture = tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```

### <a name="see-also"></a>См. также:

Нет

## <a name="tx_mutex_create"></a>tx_mutex_create

Создание мьютекса взаимного исключения

### <a name="prototype"></a>Прототип

```c
UINT tx_mutex_create(
    TX_MUTEX *mutex_ptr,
    CHAR *name_ptr, 
    UINT priority_inherit);
```

### <a name="description"></a>Описание

Эта служба создает мьютекс для взаимного исключения между потоками для защиты ресурсов.

### <a name="parameters"></a>Параметры

- **mutex_ptr** — указатель на блок управления мьютексом.
- **name_ptr** — указатель на имя мьютекса.
- **priority_inherit** — указывает, поддерживает ли этот мьютекс наследование приоритета. Если это значение равно TX_INHERIT, то наследование приоритета поддерживается. Если же указано TX_NO_INHERIT, то наследование приоритета мьютексом не поддерживается.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное создание мьютекса.
- **TX_MUTEX_ERROR** (0x1C) — недопустимый указатель на мьютекс. Либо указатель имеет значение NULL, либо мьютекс уже создан.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.
- **TX_INHERIT_ERROR** (0x1F) — недопустимый параметр наследования приоритета.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
TX_MUTEX my_mutex;
UINT status;

/* Create a mutex to provide protection over a
common resource. */
status = tx_mutex_create(&my_mutex,"my_mutex_name",
    TX_NO_INHERIT);

/* If status equals TX_SUCCESS, my_mutex is ready for
use. */
```

### <a name="see-also"></a>См. также:

- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_delete"></a>tx_mutex_delete

Удаление мьютекса взаимного исключения

### <a name="prototype"></a>Прототип

```c
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет указанный мьютекс. Все потоки, приостановленные в ожидании мьютекса, возобновляются и получают состояние возврата **TX_DELETED**.

> [!NOTE]
> *Ответственность за предотвращение использования удаленного мьютекса лежит на приложении.*

### <a name="parameters"></a>Параметры

- **mutex_ptr** — указатель на ранее созданный мьютекс.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное удаление мьютекса.
- **TX_MUTEX_ERROR** (0x1C) — недопустимый указатель на мьютекс.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_MUTEX my_mutex;
UINT status;

/* Delete a mutex. Assume that the mutex
has already been created. */
status = tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
deleted. */
```

### <a name="see-also"></a>См. также:

- tx_mutex_create
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_get"></a>tx_mutex_get

Получение прав на владение мьютексом

### <a name="prototype"></a>Прототип

```c
UINT tx_mutex_get(
    TX_MUTEX *mutex_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба пытается получить право на монопольное владение указанным мьютексом. Если вызывающий поток уже владеет мьютексом, то внутренний счетчик увеличивается и возвращается состояние успешного выполнения.

Если мьютекс принадлежит другому потоку, а текущий поток имеет более высокий приоритет и при создании мьютекса было задано наследование приоритета, приоритет потока с более низким приоритетом будет временно повышен до приоритета вызывающего потока.

> [!NOTE]
> *Приоритет потока с низким приоритетом, который владеет мьютексом с наследованием приоритета, никогда не должен изменяться внешним потоком во время владения мьютексом.*

### <a name="parameters"></a>Параметры

- **mutex_ptr**   <br>Указатель на ранее созданный мьютекс.
- **wait_option** <br>Определяет, как работает служба, если мьютекс уже принадлежит другому потоку. Параметры ожидания определяются следующим образом:
  - **TX_NO_WAIT** (0x00000000) — немедленный возврат из этой службы независимо от того, было ли выполнение успешным. *Это единственный допустимый параметр, если служба вызывается из инициализации.*
  - **TX_WAIT_FOREVER** (значение времени ожидания 0xFFFFFFFF) — вызывающий поток приостанавливается на неопределенное время, пока мьютекс не станет доступным.
  - значение времени ожидания (от 0x00000001 до 0xFFFFFFFE) — задать максимальное число тактов таймера для приостановки работы при ожидании мьютекса.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная операция получения мьютекса.
- **TX_DELETED** (0x01) — мьютекс был удален, пока поток был приостановлен.
- **TX_NOT_AVAILABLE** (0x1D) — службе не удалось получить владение мьютексом в течение указанного времени ожидания.
- **TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.
- **TX_MUTEX_ERROR** (0x1C) — недопустимый указатель на мьютекс.
- **TX_WAIT_ERROR** (0x04) — в вызове из непотокового запроса был указан параметр ожидания, отличный от TX_NO_WAIT.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки и таймеры

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_MUTEX my_mutex;
UINT status;

/* Obtain exclusive ownership of the mutex "my_mutex".
If the mutex "my_mutex" is not available, suspend until it
becomes available. */
status = tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```

### <a name="see-also"></a>См. также:

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_info_get"></a>tx_mutex_info_get

Получение сведений о мьютексе

### <a name="prototype"></a>Прототип

```c
UINT tx_mutex_info_get(
    TX_MUTEX *mutex_ptr, 
    CHAR **name,
    ULONG *count, 
    TX_THREAD **owner,
    TX_THREAD **first_suspended,
    ULONG *suspended_count, 
    TX_MUTEX **next_mutex);
```

### <a name="description"></a>Описание

Эта служба получает сведения из указанного мьютекса.

### <a name="parameters"></a>Параметры

- **mutex_ptr** — указатель на блок управления мьютексом.
- **name** — указатель на назначение для указателя на имя мьютекса.
- **count** — указатель на назначение для счетчика владения мьютексом.
- **owner** — указатель на назначение для указателя потока-владельца.
- **first_suspended** — указатель на назначение для указателя на поток, который находится первым в списке приостановки этого мьютекса.
- **suspended_count** — указатель на назначения для количества потоков, приостановленных в этом мьютексе.
- **next_mutex** — указатель на назначение для указателя следующего созданного мьютекса.

> [!NOTE]
> *Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о мьютексе.
- **TX_MUTEX_ERROR** (0x1C) — недопустимый указатель на мьютекс.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

**Пример**

```c
TX_MUTEX my_mutex;
CHAR *name;
ULONG count;
TX_THREAD *owner;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_MUTEX *next_mutex;
UINT status;

/* Retrieve information about the previously created
mutex "my_mutex." */
status = tx_mutex_info_get(&my_mutex, &name,
    &count, &owner,
    &first_suspended, &suspended_count,
    &next_mutex);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>См. также:

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_performance_info_get"></a>tx_mutex_performance_info_get

Получение сведений о производительности мьютекса

### <a name="prototype"></a>Прототип

```c
UINT tx_mutex_performance_info_get(
    TX_MUTEX *mutex_ptr, 
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a>Описание

Эта служба получает сведения о производительности указанного мьютекса.

> [!IMPORTANT]
> *Библиотека ThreadX и приложение должны быть построены с определенным параметром* ***TX_MUTEX_ENABLE_PERFORMANCE_INFO** _ _, чтобы служба могла вернуть сведения о производительности*.

### <a name="parameters"></a>Параметры

- **mutex_ptr** — указатель на ранее созданный мьютекс.
- **puts** — указатель на место назначения для количества запросов на размещение, выполненных в этом мьютексе.
- **gets** — указатель на место назначения для количества запросов на получение, выполненных в этом мьютексе.
- **suspensions** — указатель на место назначения для количества приостановок потоков для получения мьютекса в этом мьютексе.
- **timeouts** — указатель на место назначения для количества истечений времени ожидания во время приостановки для получения мьютекса в этом мьютексе.
- **inversions** — указатель на место назначения для числа инверсий приоритета потока для этого мьютекса.
- **inheritances** — указатель на место назначения для числа операций наследования приоритета потоков для этого мьютекса.

> [!NOTE]
> *Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о производительности мьютекса.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель на мьютекс.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
TX_MUTEX my_mutex;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on the previously created
mutex. */
status = tx_mutex_performance_info_get(&my_mutex_ptr, &puts, &gets,
    &suspensions, &timeouts, &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_performance_system_info_get"></a>tx_mutex_performance_system_info_get

Получение сведений о производительности системы мьютексов

### <a name="prototype"></a>Прототип

```c
UINT tx_mutex_performance_system_info_get(
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a>Описание

Эта служба получает сведения о производительности всех мьютексов в системе.

> [!IMPORTANT]
> *Библиотека ThreadX и приложение должны быть построены с определенным параметром* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** *, чтобы служба могла вернуть сведения о производительности.*

### <a name="parameters"></a>Параметры

- **puts** — указатель на место назначения для общего количества запросов на размещение, выполненных во всех мьютексах.
- **gets** — указатель на место назначения для общего количества запросов на получение, выполненных во всех мьютексах.
- **suspensions** — указатель на место назначения для общего количества приостановок потоков для получения мьютекса во всех мьютексах.
- **timeouts** — указатель на место назначения для общего количества истечений времени ожидания во время приостановки для получения мьютекса во всех мьютексах.
- **inversions** — указатель на место назначения для общего числа инверсий приоритета потока во всех мьютексах.
- **inheritances** — указатель на место назначения для общего числа операций наследования приоритета потоков во всех мьютексах.

> [!NOTE]
> *Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о производительности системы мьютексов.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;
ULONG inversions;
ULONG inheritances;

/* Retrieve performance information on all previously created
mutexes. */
status = tx_mutex_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts,
    &inversions, &inheritances);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_prioritize
- tx_mutex_put

## <a name="tx_mutex_prioritize"></a>tx_mutex_prioritize

Назначение приоритета списку приостановки мьютекса

### <a name="prototype"></a>Прототип

```c
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a>Описание

Эта служба размещает поток с наивысшим приоритетом, приостановленный для получения права владения мьютексом, в начале списка приостановки. Все остальные потоки остаются в том же порядке FIFO, в котором они были приостановлены.

### <a name="parameters"></a>Параметры

- **mutex_ptr** — указатель на ранее созданный мьютекс.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное назначение приоритета в мьютексе.
- **TX_MUTEX_ERROR** (0x1C) — недопустимый указатель на мьютекс.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
TX_MUTEX my_mutex;
UINT status;

/* Ensure that the highest priority thread will receive
ownership of the mutex when it becomes available. */
status = tx_mutex_prioritize(&my_mutex);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_mutex_put call that releases ownership of the
mutex will give ownership to this thread and wake it
up. */
```

### <a name="see-also"></a>См. также:

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_put

## <a name="tx_mutex_put"></a>tx_mutex_put

Освобождение владения мьютексом

### <a name="prototype"></a>Прототип

```c
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a>Описание

Эта служба уменьшает количество владений указанным мьютексом. Если счетчик владения равен нулю, мьютекс становится доступным.

> [!NOTE]
> *Если во время создания мьютекса включено наследование приоритета, приоритет освобождающего потока будет восстановлен до приоритета, который он имел, когда изначально получил право владения мьютексом. Все другие изменения приоритета, внесенные в освобождающий поток во время владения мьютексом, могут быть отменены.*

### <a name="parameters"></a>Параметры
- mutex_ptr — указатель на ранее созданный мьютекс.

### <a name="return-values"></a>Возвращаемые значения
- **TX_SUCCESS** (0x00) — успешное освобождение мьютекса.
- **TX_NOT_OWNED** (0x1E) — мьютекс не принадлежит вызывающему объекту.
- **TX_MUTEX_ERROR** (0x1C) — недопустимый указатель на мьютекс.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки и таймеры

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_MUTEX my_mutex;
UINT status;

/* Release ownership of "my_mutex." */
status = tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
count has been decremented and if zero, released. */
```

### <a name="see-also"></a>См. также:

- tx_mutex_create
- tx_mutex_delete
- tx_mutex_get
- tx_mutex_info_get
- tx_mutex_performance_info_get
- tx_mutex_performance_system_info_get
- tx_mutex_prioritize

## <a name="tx_queue_create"></a>tx_queue_create

Создание очереди сообщений

### <a name="prototype"></a>Прототип

```c
UINT tx_queue_create(
    TX_QUEUE *queue_ptr, 
    CHAR *name_ptr,
    UINT message_size,
    VOID *queue_start, 
    ULONG queue_size);
```

### <a name="description"></a>Описание

Эта служба создает очередь сообщений, которая обычно используется для взаимодействия между потоками. Общее количество сообщений вычисляется на основе указанного размера сообщения и общего числа байтов в очереди.

> [!NOTE]
> *Если общее число байтов, указанное в области памяти очереди, не делится на указанный размер сообщения, оставшиеся байты в области памяти не используются.*

### <a name="parameters"></a>Параметры

- **queue_ptr** — указатель на управляющий блок очереди сообщений.
- **name_ptr** — указатель на имя пула очереди сообщений.
- **message_size** — задает размер каждого сообщения в очереди. Размеры сообщений находятся в диапазоне от 1 до 16 32-разрядных слов. Допустимые параметры размера сообщения — это числовые значения от 1 до 16 включительно.
- **queue_start** — начальный адрес очереди сообщений. Начальный адрес должен быть выровнен по размеру типа данных ULONG.
- **queue_size** — общее число байт, доступных для очереди сообщений.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное создание очереди сообщений.
- **TX_QUEUE_ERROR** (0x09) — недопустимый указатель на очередь сообщений. Либо указатель имеет значение NULL, либо очередь уже создана.
- **TX_PTR_ERROR** (0x03) — недопустимый начальный адрес очереди сообщений.
- **TX_SIZE_ERROR** (0x05) — недопустимый размер очереди сообщений.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
TX_QUEUE my_queue;
UINT status;

/* Create a message queue whose total size is 2000 bytes
starting at address 0x300000. Each message in this
queue is defined to be 4 32-bit words long. */
status = tx_queue_create(&my_queue, "my_queue_name",
    4, (VOID *) 0x300000, 2000);

/* If status equals TX_SUCCESS, my_queue contains room
for storing 125 messages (2000 bytes/ 16 bytes per
message). */
```

### <a name="see-also"></a>См. также:

- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_delete"></a>tx_queue_delete

Удаление очереди сообщений

### <a name="prototype"></a>Прототип

```c
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет указанную очередь сообщений. Все потоки, приостановленные в ожидании сообщения из этой очереди, возобновляются и получают состояние возврата TX_DELETED.

>[!IMPORTANT]
> *Перед удалением очереди приложение должно убедиться в том, что все функции обратного вызова уведомления об отправке для этой очереди завершены (или отключены). Кроме того, приложение должно предотвратить использование удаленной очереди в будущем.* <br><br>*Кроме того, обязанность по управлению областью памяти, связанной с очередью, которая станет доступна после завершения этой службы, лежит на приложении.*

### <a name="parameters"></a>Параметры

- **queue_ptr** — указатель на ранее созданную очередь сообщений.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное удаление очереди сообщений.
- **TX_QUEUE_ERROR** (0x09) — недопустимый указатель на очередь сообщений.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_QUEUE my_queue;
UINT status;

/* Delete entire message queue. Assume that the queue
has already been created with a call to
tx_queue_create. */
status = tx_queue_delete(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
deleted. */
```

### <a name="see-also"></a>См. также:

- tx_queue_create
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_flush"></a>tx_queue_flush

Очистка сообщений в очереди сообщений

### <a name="prototype"></a>Прототип

```c
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет все сообщения, хранящиеся в указанной очереди сообщений.

Если очередь заполнена, сообщения о всех приостановленных потоках будут удалены. Затем каждый приостановленный поток возобновляется со статусом возврата, который указывает, что отправка сообщения прошла успешно. Если очередь пуста, эта служба не выполняет никаких действий.

### <a name="parameters"></a>Параметры

- **queue_ptr** — указатель на ранее созданную очередь сообщений.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная очистка очереди сообщений.
- **TX_QUEUE_ERROR** (0x09) — недопустимый указатель на очередь сообщений.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_QUEUE my_queue;
UINT status;

/* Flush out all pending messages in the specified message
queue. Assume that the queue has already been created
with a call to tx_queue_create. */
status = tx_queue_flush(&my_queue);

/* If status equals TX_SUCCESS, the message queue is
empty. */
```

### <a name="see-also"></a>См. также:

- tx_queue_create
- tx_queue_delete
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_front_send"></a>tx_queue_front_send

Отправка сообщения в начало очереди

### <a name="prototype"></a>Прототип

```c
UINT tx_queue_front_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба отправляет сообщение в начало указанной очереди сообщений. Сообщение **копируется** в начало очереди из области памяти, заданной указателем источника.

### <a name="parameters"></a>Параметры

- **queue_ptr** <br>Указатель на управляющий блок очереди сообщений.
- **source_ptr** <br>Указатель на сообщение.
- **wait_option**  <br>Определяет, как работает служба, если очередь сообщений заполнена. Параметры ожидания определяются следующим образом:
  - **TX_NO_WAIT** (0x00000000) — немедленный возврат из этой службы независимо от того, было ли выполнение успешным. *Это единственный допустимый параметр, если служба вызывается из непотока, например инициализации, таймера или ISR.*
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) — вызывающий поток приостанавливается на неопределенное время, пока в очереди не освободится место.
  - значение времени ожидания (от 0x00000001 до 0xFFFFFFFE) — задать максимальное число тактов таймера для приостановки работы при ожидании свободного места в очереди.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная отправка сообщения.
- **TX_DELETED** (0x01) — очередь сообщений была удалена, пока поток был приостановлен.
- **TX_QUEUE_FULL** (0x0B) — службе не удалось отправить сообщение, так как очередь была заполнена в течение всего указанного времени ожидания.
- **TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.
- **TX_QUEUE_ERROR** (0x09) — недопустимый указатель на очередь сообщений.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель источника для сообщения.
- **TX_WAIT_ERROR** (0x04) — в вызове из непотокового запроса был указан параметр ожидания, отличный от TX_NO_WAIT.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to the front of "my_queue." Return
immediately, regardless of success. This wait
option is used for calls from initialization, timers,
and ISRs. */
status = tx_queue_front_send(&my_queue, my_message,
    TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is at the front
of the specified queue. */
```

### <a name="see-also"></a>См. также:

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_info_get"></a>tx_queue_info_get

Получение сведений об очереди

### <a name="prototype"></a>Прототип

```c
UINT tx_queue_info_get(
    TX_QUEUE *queue_ptr, 
    CHAR **name,
    ULONG *enqueued, 
    ULONG *available_storage
    TX_THREAD **first_suspended, 
    ULONG *suspended_count,
    TX_QUEUE **next_queue);
```

### <a name="description"></a>Описание

Эта служба получает сведения об указанной очереди сообщений.

### <a name="parameters"></a>Параметры

- **queue_ptr** — указатель на ранее созданную очередь сообщений.
- **name** — указатель на назначение для указателя на имя очереди.
- **enqueued** — указатель на место назначения для количества сообщений, находящихся в очереди в данный момент.
- **available_storage** — указатель на место назначения для количества сообщений в очереди, для которых в настоящий момент имеется место.
- **first_suspended** — указатель на назначение для указателя на поток, который находится первым в списке приостановки этой очереди.
- **suspended_count** — указатель на назначения для количества потоков, приостановленных в этой очереди.
- **next_queue** — указатель на назначение для указателя следующей созданной очереди.

> [!NOTE]
> *Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений об очереди.
- **TX_QUEUE_ERROR** (0x09) — недопустимый указатель на очередь сообщений.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
TX_QUEUE my_queue;
CHAR *name;
ULONG enqueued;
ULONG available_storage;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_QUEUE *next_queue;
UINT status;

/* Retrieve information about the previously created
message queue "my_queue." */
status = tx_queue_info_get(&my_queue, &name,
    &enqueued, &available_storage,
    &first_suspended, &suspended_count,
    &next_queue);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>См. также:

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_performance_info_get"></a>tx_queue_performance_info_get

Получение сведений о производительности очереди

### <a name="prototype"></a>Прототип

```c
UINT tx_queue_performance_info_get(
    TX_QUEUE *queue_ptr,
    ULONG *messages_sent, 
    ULONG *messages_received,
    ULONG *empty_suspensions, 
    ULONG *full_suspensions,
    ULONG *full_errors, 
    ULONG *timeouts);
```

### <a name="description"></a>Описание

Эта служба получает сведения о производительности указанной очереди.

> [!IMPORTANT]
> *Библиотека ThreadX и приложение должны быть построены с определенным параметром* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _, чтобы служба могла вернуть сведения о производительности*.

### <a name="parameters"></a>Параметры

- **queue_ptr** — указатель на ранее созданную очередь.
- **messages_sent** — указатель на место назначения для количества запросов на отправку, выполненных в этой очереди.
- **messages_received** — указатель на место назначения для количества запросов на получение, выполненных в этой очереди.
- **empty_suspensions** — указатель на место назначения для количества приостановок при пустой очереди в этой очереди.
- **full_suspensions** — указатель на место назначения для количества приостановок при заполненной очереди в этой очереди.
- **full_errors** — указатель на место назначения для количества ошибок при заполненной очереди в этой очереди.
- **timeouts** — указатель на место назначения для количества истечений времени ожидания во время приостановки потока в этой очереди.

> [!NOTE]
> *Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о производительности очереди.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель на очередь.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
TX_QUEUE my_queue;
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on the previously created
queue. */
status = tx_queue_performance_info_get(&my_queue, &messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_performance_system_info_get"></a>tx_queue_performance_system_info_get

Получение сведений о производительности системы очередей

### <a name="prototype"></a>Прототип

```c
UINT tx_queue_performance_system_info_get(
    ULONG *messages_sent,
    ULONG *messages_received, 
    ULONG *empty_suspensions,
    ULONG *full_suspensions, 
    ULONG *full_errors,
    ULONG *timeouts);
```

### <a name="description"></a>Описание

Эта служба получает сведения о производительности всех очередей в системе.

> [!IMPORTANT]
> *Библиотека ThreadX и приложение должны быть построены с определенным параметром* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _, чтобы служба могла вернуть сведения о производительности*.

### <a name="parameters"></a>Параметры

- **messages_sent** — указатель на место назначения для общего количества запросов на отправку, выполненных во всех очередях.
- **messages_received** — указатель на место назначения для общего количества запросов на получение, выполненных во всех очередях.
- **empty_suspensions** — указатель на место назначения для общего количества приостановок при пустой очереди во всех очередях.
- **full_suspensions** — указатель на место назначения для общего количества приостановок при заполненной очереди во всех очередях.
- **full_errors** — указатель на место назначения для общего количества ошибок при заполненной очереди во всех очередях.
- **timeouts** — указатель на место назначения для общего количества истечений времени ожидания во время приостановки потока во всех очередях.

> [!NOTE]
> *Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*

**Возвращаемые значения**

- **TX_SUCCESS** (0x00) — успешное получение сведений о производительности системы очередей.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
ULONG messages_sent;
ULONG messages_received;
ULONG empty_suspensions;
ULONG full_suspensions;
ULONG full_errors;
ULONG timeouts;

/* Retrieve performance information on all previously created
queues. */
status = tx_queue_performance_system_info_get(&messages_sent,
    &messages_received, &empty_suspensions,
    &full_suspensions, &full_errors, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_prioritize"></a>tx_queue_prioritize

Назначение приоритета в списке приостановки очереди

### <a name="prototype"></a>Прототип

```c
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a>Описание

Эта служба помещает поток с наивысшим приоритетом, приостановленный для сообщения (или для размещения сообщения) в этой очереди, в начало списка приостановки.

Все остальные потоки остаются в том же порядке FIFO, в котором они были приостановлены.

### <a name="parameters"></a>Параметры

- **queue_ptr** — указатель на ранее созданную очередь сообщений.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное назначение приоритета в очереди.
- **TX_QUEUE_ERROR** (0x09) — недопустимый указатель на очередь сообщений.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
TX_QUEUE my_queue;
UINT status;

/* Ensure that the highest priority thread will receive
the next message placed on this queue. */
status = tx_queue_prioritize(&my_queue);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_queue_send or tx_queue_front_send call made
to this queue will wake up this thread. */
```

### <a name="see-also"></a>См. также:

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_receive
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_receive"></a>tx_queue_receive

Получение сообщения из очереди сообщений

### <a name="prototype"></a>Прототип

```c
UINT tx_queue_receive(
    TX_QUEUE *queue_ptr,
    VOID *destination_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба получает сообщение из указанной очереди сообщений. Полученное сообщение **копируется** из очереди в область памяти, заданную указателем назначения. Затем это сообщение удаляется из очереди.

> [!IMPORTANT]
> *Указанная область памяти назначения должна быть достаточно большой, чтобы вместить сообщение. То есть место назначения сообщения, на которое указывает*  ***destination_ptr** _ _, должно быть не меньше размера сообщения в этой очереди. В противном случае, если место назначения недостаточно велико, происходит повреждение памяти в следующей области памяти*.

### <a name="parameters"></a>Параметры

- **queue_ptr** <br>Указатель на ранее созданную очередь сообщений.
- **destination_ptr** <br>Расположение для копирования сообщения.
- **wait_option** <br>Определяет, как работает служба, если очередь сообщений пуста. Параметры ожидания определяются следующим образом:
  - **TX_NO_WAIT** (0x00000000) — немедленный возврат из этой службы независимо от того, было ли выполнение успешным. Это единственный допустимый параметр, если служба вызывается из непотока, например инициализации, таймера или ISR.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) — вызывающий поток приостанавливается на неопределенное время, пока не станет доступно сообщение.
  - значение времени ожидания (от 0x00000001 до 0xFFFFFFFE) — задать максимальное число тактов таймера для приостановки работы при ожидании сообщения.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сообщения.
- **TX_DELETED** (0x01) — очередь сообщений была удалена, пока поток был приостановлен.
- **TX_QUEUE_EMPTY** (0x0A) — службе не удалось получить сообщение, так как очередь была пуста в течение указанного времени ожидания.
- **TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.
- **TX_QUEUE_ERROR** (0x09) — недопустимый указатель на очередь сообщений.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель назначения для сообщения.
- **TX_WAIT_ERROR** (0x04) — в вызове из непотокового запроса был указан параметр ожидания, отличный от TX_NO_WAIT.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Retrieve a message from "my_queue." If the queue is
empty, suspend until a message is present. Note that
this suspension is only possible from application
threads. */
status = tx_queue_receive(&my_queue, my_message,
    TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the message is in
"my_message." */
```

### <a name="see-also"></a>См. также:

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_send
- tx_queue_send_notify

## <a name="tx_queue_send"></a>tx_queue_send

Отправка сообщения в очередь сообщений

### <a name="prototype"></a>Прототип

```c
UINT tx_queue_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба отправляет сообщение в указанную очередь сообщений. Отправленное сообщение **копируется** в очередь из области памяти, заданной указателем источника.

### <a name="parameters"></a>Параметры
- **queue_ptr** <br>Указатель на ранее созданную очередь сообщений.
- **source_ptr** <br>Указатель на сообщение.
- **wait_option** <br>Определяет, как работает служба, если очередь сообщений заполнена. Параметры ожидания определяются следующим образом:
  - **TX_NO_WAIT** (0x00000000) — немедленный возврат из этой службы независимо от того, было ли выполнение успешным. *Это единственный допустимый параметр, если служба вызывается из непотока, например инициализации, таймера или ISR*.
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) — вызывающий поток приостанавливается на неопределенное время, пока в очереди не освободится место.
  - значение времени ожидания (от 0x00000001 до 0xFFFFFFFE) — задать максимальное число тактов таймера для приостановки работы при ожидании свободного места в очереди.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная отправка сообщения.
- **TX_DELETED** (0x01) — очередь сообщений была удалена, пока поток был приостановлен.
- **TX_QUEUE_FULL** (0x0B) — службе не удалось отправить сообщение, так как очередь была заполнена в течение всего указанного времени ожидания.
- **TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.
- **TX_QUEUE_ERROR** (0x09) — недопустимый указатель на очередь сообщений.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель источника для сообщения.
- **TX_WAIT_ERROR** (0x04) — в вызове из непотокового запроса был указан параметр ожидания, отличный от TX_NO_WAIT.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_QUEUE my_queue;
UINT status;
ULONG my_message[4];

/* Send a message to "my_queue." Return immediately,
regardless of success. This wait option is used for
calls from initialization, timers, and ISRs. */
status = tx_queue_send(&my_queue, my_message, TX_NO_WAIT);

/* If status equals TX_SUCCESS, the message is in the
queue. */
```

**См. также:**

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send_notify

## <a name="tx_queue_send_notify"></a>tx_queue_send_notify

Уведомление приложения при отправке сообщения в очередь

### <a name="prototype"></a>Прототип

```c
UINT tx_queue_send_notify(
    TX_QUEUE *queue_ptr,
    VOID (*queue_send_notify)(TX_QUEUE *));
```

### <a name="description"></a>Описание

Эта служба регистрирует функцию обратного вызова уведомления, которая вызывается всякий раз, когда сообщение отправляется в указанную очередь. Обработка обратного вызова уведомления определяется приложением.

>[!NOTE]
> *Обратному вызову уведомления приложения об отправке в очередь не разрешено вызывать никакой API ThreadX с параметром приостановки.*

### <a name="parameters"></a>Параметры

- **queue_ptr** — указатель на ранее созданную очередь.
- **queue_send_notify** — указатель на функцию уведомления приложения об отправке в очередь. Если это значение равно TX_NULL, уведомление отключено.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная регистрация уведомления об отправке в очередь.
- **TX_QUEUE_ERROR** (0x09) — недопустимый указатель на очередь.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система была скомпилирована с отключенными возможностями уведомлений.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
TX_QUEUE my_queue;
/* Register the "my_queue_send_notify" function for monitoring
messages sent to the queue "my_queue." */
status = tx_queue_send_notify(&my_queue, my_queue_send_notify);

/* If status is TX_SUCCESS the queue send notification function was
successfully registered. */
void my_queue_send_notify(TX_QUEUE *queue_ptr)
{
    /* A message was just sent to this queue! */
}
```

### <a name="see-also"></a>См. также:

- tx_queue_create
- tx_queue_delete
- tx_queue_flush
- tx_queue_front_send
- tx_queue_info_get
- tx_queue_performance_info_get
- tx_queue_performance_system_info_get
- tx_queue_prioritize
- tx_queue_receive
- tx_queue_send

## <a name="tx_semaphore_ceiling_put"></a>tx_semaphore_ceiling_put

Размещение экземпляра в семафоре со счетчиком с верхним пределом

### <a name="prototype"></a>Прототип

```c
UINT tx_semaphore_ceiling_put(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG ceiling);
```

### <a name="description"></a>Описание

Эта служба помещает экземпляр в указанный семафор со счетчиком, который в действительности увеличивает счетчик семафора на единицу. Если текущее значение семафора со счетчиком больше или равно указанному пороговому значению, экземпляр не будет размещен и будет возвращена ошибка TX_CEILING_EXCEEDED.

### <a name="parameters"></a>Параметры

- **semaphore_ptr** — указатель на ранее созданный семафор.
- **ceiling** — максимально допустимый предел для семафора (допустимые значения находятся в диапазоне от 1 до 0xFFFFFFFF).

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS (0x00)**  — успешное размещение в пределах семафора.
- **TX_CEILING_EXCEEDED** (0x21) — запрос на размещение превышает допустимый предел.
- **TX_INVALID_CEILING** (0x22) — для параметра ceiling указано недопустимое нулевое значение.
- **TX_SEMAPHORE_ERROR** (0x0C) — недопустимый указатель на семафор.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
TX_SEMAPHORE my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
incremented. */
```

### <a name="see-also"></a>См. также:

- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_create"></a>tx_semaphore_create

Создание семафора со счетчиком

### <a name="prototype"></a>Прототип

```c
UINT tx_semaphore_create(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR *name_ptr, 
    ULONG initial_count);
```

### <a name="description"></a>Описание

Эта служба создает семафор со счетчиком для синхронизации между потоками. Начальное значение семафора указывается в качестве входного параметра.

### <a name="parameters"></a>Параметры

- **semaphore_ptr** — указатель на блок управления семафором.
- **name_ptr** — указатель на имя семафора.
- **initial_count** — указывает начальное значение счетчика для семафора. Допустимые значения находятся в диапазоне от 0x00000000 до 0xFFFFFFFF.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS (0x00)**  — успешное создание семафора.
- **TX_SEMAPHORE_ERROR** (0x0C) — недопустимый указатель на семафор. Либо указатель имеет значение NULL, либо семафор уже создан.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Create a counting semaphore whose initial value is 1.
This is typically the technique used to make a binary
semaphore. Binary semaphores are used to provide
protection over a common resource. */
status = tx_semaphore_create(&my_semaphore,
    "my_semaphore_name", 1);

/* If status equals TX_SUCCESS, my_semaphore is ready for
use. */
```

### <a name="see-also"></a>См. также:

- tx_semaphore_ceiling_put
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_delete"></a>tx_semaphore_delete

Удаление вычисляющего семафора

### <a name="prototype"></a>Прототип
```c
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет указанный семафор со счетчиком. Все потоки, приостановленные в ожидании экземпляра семафора, возобновляются и получают состояние возврата TX_DELETED.

> [!IMPORTANT]
> *Перед удалением семафора приложение должно убедиться в том, что функция обратного вызова уведомления о размещении для этого семафора завершена (или отключена). Кроме того, приложение должно предотвратить использование удаленного семафора в будущем.*

### <a name="parameters"></a>Параметры

- **semaphore_ptr** — указатель на ранее созданный семафор.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное удаление семафора.
- **TX_SEMAPHORE_ERROR** (0x0C) — недопустимый указатель на семафор со счетчиком.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Delete counting semaphore. Assume that the counting
semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
deleted. */
```

**См. также:**

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_get"></a>tx_semaphore_get

Получение экземпляра из вычисляющего семафора

### <a name="prototype"></a>Прототип

```c
UINT tx_semaphore_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба извлекает экземпляр (единицу счетчика) из указанного семафора со счетчиком. В результате счетчик указанного семафора уменьшается на единицу.

### <a name="parameters"></a>Параметры

- **semaphore_ptr** <br>Указатель на ранее созданный семафор со счетчиком.
- **wait_option** <br>Определяет, как служба ведет себя, если нет доступных экземпляров семафора, то есть счетчик семафора равен нулю. Параметры ожидания определяются следующим образом:
  - **TX_NO_WAIT** (0x00000000) — немедленный возврат из этой службы независимо от того, было ли выполнение успешным. *Это единственный допустимый параметр, если служба вызывается из непотока, например инициализации, таймера или ISR.*
  - **TX_WAIT_FOREVER** (0xFFFFFFFF) — вызывающий поток приостанавливается на неопределенное время, пока не станет доступен экземпляр семафора.
  - значение времени ожидания (от 0x00000001 до 0xFFFFFFFE) — задать максимальное число тактов таймера для приостановки работы при ожидании экземпляра семафора.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение экземпляра семафора.
- **TX_DELETED** (0x01) — семафор со счетчиком был удален, пока поток был приостановлен.
- **TX_NO_INSTANCE** (0x0D) — службе не удалось получить экземпляр семафора со счетчиком (число семафоров в течение всего заданного времени ожидания было равно нулю).
- **TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.
- **TX_SEMAPHORE_ERROR** (0x0C) — недопустимый указатель на семафор со счетчиком.
- **TX_WAIT_ERROR** (0x04) — в вызове из непотокового запроса был указан параметр ожидания, отличный от TX_NO_WAIT.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Get a semaphore instance from the semaphore
"my_semaphore." If the semaphore count is zero,
suspend until an instance becomes available.
Note that this suspension is only possible from
application threads. */
status = tx_semaphore_get(&my_semaphore, TX_WAIT_FOREVER);

/* If status equals TX_SUCCESS, the thread has obtained
an instance of the semaphore. */
```

### <a name="see-also"></a>См. также:

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semahore_delete
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_info_get"></a>tx_semaphore_info_get

Получение сведений о семафоре

### <a name="prototype"></a>Прототип

```c
UINT tx_semaphore_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR **name, ULONG *current_value,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_SEMAPHORE **next_semaphore);
```

### <a name="description"></a>Описание

Эта служба получает сведения об указанном семафоре.

### <a name="parameters"></a>Параметры

- **semaphore_ptr** — указатель на блок управления семафором.
- **name** — указатель на назначение для указателя на имя семафора.
- **current_value** — указатель на назначение для счетчика текущего семафора.
- **first_suspended** — указатель на назначение для указателя на поток, который находится первым в списке приостановки этого семафора.
- **suspended_count** — указатель на назначения для количества потоков, приостановленных в этом семафоре.
- **next_semaphore** — указатель на назначение для указателя следующего созданного семафора.

> [!NOTE]
> *Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — сведения получены.

- **TX_SEMAPHORE_ERROR** (0x0C) — недопустимый указатель на семафор.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
TX_SEMAPHORE my_semaphore;
CHAR *name;
ULONG current_value;
TX_THREAD *first_suspended;
ULONG suspended_count;
TX_SEMAPHORE *next_semaphore;
UINT status;

/* Retrieve information about the previously created
semaphore "my_semaphore." */
status = tx_semaphore_info_get(&my_semaphore, &name,
    &current_value,
    &first_suspended, &suspended_count,
    &next_semaphore);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>См. также:

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_performance_info_get"></a>tx_semaphore_performance_info_get

Получение сведений о производительности семафоров

### <a name="prototype"></a>Прототип

```c
UINT tx_semaphore_performance_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Описание

Эта служба получает сведения о производительности указанного семафора.

> [!IMPORTANT]
> *Библиотека ThreadX и приложение должны быть построены с определенным параметром* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _, чтобы служба могла вернуть сведения о производительности*.

**Параметры**

-  **semaphore_ptr** — указатель на ранее созданный семафор.
-  **puts** — указатель на место назначения для количества запросов на размещение, выполненных в этом семафоре.
-  **gets** — указатель на место назначения для количества запросов на получение, выполненных в этом семафоре.
-  **suspensions** — указатель на место назначения для количества приостановок потоков на этом семафоре.
-  **timeouts** — указатель на место назначения для количества истечений времени ожидания во время приостановки потока на этом семафоре.

> [!NOTE]
> *Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о производительности семафора.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель на семафор.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
TX_SEMAPHORE my_semaphore;
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on the previously created
semaphore. */
status = tx_semaphore_performance_info_get(&my_semaphore, &puts,
    &gets, &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_performance_system_info_get"></a>tx_semaphore_performance_system_info_get

Получение сведений о производительности системы семафоров

### <a name="prototype"></a>Прототип

```c
UINT tx_semaphore_performance_system_info_get(
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a>Описание

Эта служба получает сведения о производительности всех семафоров в системе.

> [!IMPORTANT]
> *Библиотека ThreadX и приложение должны быть построены с определенным параметром* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _, чтобы служба могла вернуть сведения о производительности*

### <a name="parameters"></a>Параметры

- **puts** — указатель на место назначения для общего количества запросов на размещение, выполненных во всех семафорах.
- **gets** — указатель на место назначения для общего количества запросов на получение, выполненных во всех семафорах.
- **suspensions** — указатель на место назначения для общего количества приостановок потоков на всех семафорах.
- **timeouts** — указатель на место назначения для общего количества истечений времени ожидания во время приостановки потока на всех семафорах.

> [!NOTE]
> *Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — получены сведения о производительности системы.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
ULONG puts;
ULONG gets;
ULONG suspensions;
ULONG timeouts;

/* Retrieve performance information on all previously created
semaphores. */
status = tx_semaphore_performance_system_info_get(&puts, &gets,
    &suspensions, &timeouts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_prioritize
- tx_semaphore_put
- tx_semaphore_put_notify

## <a name="tx_semaphore_prioritize"></a>tx_semaphore_prioritize

Назначение приоритета списку приостановки семафора

### <a name="prototype"></a>Прототип

```c
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a>Описание

Эта служба размещает поток с наивысшим приоритетом, приостановленный для получения экземпляра семафора, в начале списка приостановки. Все остальные потоки остаются в том же порядке FIFO, в котором они были приостановлены.

### <a name="parameters"></a>Параметры

- **semaphore_ptr** — указатель на ранее созданный семафор.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS (0x00)**  — успешное назначение приоритета в семафоре.
- **TX_SEMAPHORE_ERROR** (0x0C) — недопустимый указатель на семафор со счетчиком.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Ensure that the highest priority thread will receive
the next instance of this semaphore. */
status = tx_semaphore_prioritize(&my_semaphore);

/* If status equals TX_SUCCESS, the highest priority
suspended thread is at the front of the list. The
next tx_semaphore_put call made to this semaphore will
wake up this thread. */
```

### <a name="see-also"></a>См. также:

- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_put

## <a name="tx_semaphore_put"></a>tx_semaphore_put

Размещение экземпляра в вычисляющем семафоре

### <a name="prototype"></a>Прототип

```c
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a>Описание

Эта служба помещает экземпляр в указанный семафор со счетчиком, который в действительности увеличивает счетчик семафора на единицу.

> [!NOTE]
> *Если эта служба вызывается, когда семафор полностью заполнен единицами (0xFFFFFFFF), новая операция размещения приведет к сбросу семафора на нулевое значение.*

### <a name="parameters"></a>Параметры

- **semaphore_ptr** — указатель на ранее созданный блок управления семафором со счетчиком.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS (0x00)**  — успешная операция размещения в семафоре.
- **TX_SEMAPHORE_ERROR** (0x0C) — недопустимый указатель на семафор со счетчиком.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Increment the counting semaphore "my_semaphore." */
status = tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
been incremented. Of course, if a thread was waiting,
it was given the semaphore instance and resumed. */
```

### <a name="see-also"></a>См. также:

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_get
- tx_semaphore_put_notify

## <a name="tx_semaphore_put_notify"></a>tx_semaphore_put_notify

Уведомление приложения об установке семафора

### <a name="prototype"></a>Прототип

```c
UINT tx_semaphore_put_notify(
    TX_SEMAPHORE *semaphore_ptr,
    VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```

### <a name="description"></a>Описание

Эта служба регистрирует функцию обратного вызова уведомлений, которая вызывается всякий раз, когда помещается указанный семафор. Обработка обратного вызова уведомления определяется приложением.

> [!NOTE]
> *Обратному вызову уведомления приложения о семафоре не разрешено вызывать никакой API ThreadX с параметром приостановки.*

### <a name="parameters"></a>Параметры

- **semaphore_ptr** — указатель на ранее созданный семафор.
- **semaphore_put_notify** — указатель на функцию уведомления приложения о размещении в семафоре. Если это значение равно TX_NULL, уведомление отключено.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная регистрация уведомления о размещении в семафоре.
- **TX_SEMAPHORE_ERROR** (0x0C) — недопустимый указатель на семафор.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система была скомпилирована с отключенными возможностями уведомлений.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
TX_SEMAPHORE my_semaphore;

/* Register the "my_semaphore_put_notify" function for monitoring
the put operations on the semaphore "my_semaphore." */
status = tx_semaphore_put_notify(&my_semaphore, my_semaphore_put_notify);

/* If status is TX_SUCCESS the semaphore put notification function
was successfully registered. */
void my_semaphore_put_notify(TX_SEMAPHORE *semaphore_ptr)
{
    /* The semaphore was just put! */
}
```

### <a name="see-also"></a>См. также:

- tx_semaphore_ceiling_put
- tx_semaphore_create
- tx_semaphore_delete
- tx_semaphore_get
- tx_semaphore_info_get
- tx_semaphore_performance_info_get
- tx_semaphore_performance_system_info_get
- tx_semaphore_prioritize
- tx_semaphore_put

## <a name="tx_thread_create"></a>tx_thread_create

Создание потока приложения

### <a name="prototype"></a>Прототип

```c
UINT tx_thread_create(
    TX_THREAD *thread_ptr,
    CHAR *name_ptr, 
    VOID (*entry_function)(ULONG),
    ULONG entry_input, 
    VOID *stack_start,
    ULONG stack_size, 
    UINT priority,
    UINT preempt_threshold, 
    ULONG time_slice,
    UINT auto_start);
```

### <a name="description"></a>Описание

Эта служба создает поток приложения, который начинает выполнение с указанной функции входа в задачу. Стек, приоритет, порог вытеснения и интервал времени являются атрибутами, задаваемыми входными параметрами. Кроме того, также указывается начальное состояние выполнения потока.

**Параметры**

- **thread_ptr** — указатель на блок управления потоком.
- **name_ptr** — указатель на имя потока.
- **entry_function** — задает начальную функцию C для выполнения потока. Когда поток возвращается из этой функции входа, он помещается в *завершенное* состояние и приостанавливается на неопределенное время.
- **entry_input** — 32-разрядное значение, которое передается в функцию входа потока при первом выполнении. Использование этих входных данных определяется исключительно приложением.
- **stack_start** — начальный адрес области памяти стека.
- **stack_size** — число байтов в области памяти стека. Область стека потока должна быть достаточно большой, чтобы справиться с вложением вызовов функций и использованием локальных переменных в худшем случае.
- **priority** — числовое значение приоритета потока. Допустимые значения находятся в диапазоне от 0 до (TX_MAX_PRIORITES-1), где значение 0 соответствует наивысшему приоритету.
- **preempt_threshold** — уровень наивысшего приоритета (от 0 до (TX_MAX_PRIORITIES-1)) при отключенном вытеснении. Только приоритеты выше этого уровня могут вытеснять этот поток. Это значение должно быть меньше указанного приоритета или равно ему. Значение, равное приоритету потока, отключает приоритет вытеснения.
- **time_slice** — количество тактов таймера, которое этот поток может выполнять до того, как другие готовые потоки с таким же приоритетом получают возможность запуска. Обратите внимание, что при использовании порогового значения вытеснения временной срез отключается. Допустимые значение интервала времени варьируются от 1 до 0xFFFFFFFF (включительно). Значение **TX_NO_TIME_SLICE** (значение 0) отключает временной срез для этого потока.

  > [!NOTE]
  > *Использование временного среза приводит к небольшому количеству системных издержек. Так как временной срез полезен только в случаях, когда несколько потоков имеют одинаковый приоритет, для потоков с уникальными приоритетами не следует назначать временной срез.*

- **auto_start** — указывает, запускается ли поток немедленно или помещается в приостановленное состояние. Допустимые значения: **TX_AUTO_START** (0x01) и **TX_DONT_START** (0x00). Если указано TX_DONT_START, приложение должно затем вызвать tx_thread_resume для того, чтобы запустить поток.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное создание потока.
- **TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток. Либо указатель имеет значение NULL, либо поток уже создан.
- **TX_PTR_ERROR** (0x03) — недопустимый начальный адрес точки входа или недопустимая область стека, обычно имеет значение NULL.
- **TX_SIZE_ERROR** (0x05) —недопустимый размер области стека. Потоки должны иметь по крайней мере **TX_MINIMUM_STACK** байтов для выполнения.
- **TX_PRIORITY_ERROR** (0x0F) — приоритет потока имеет значение вне допустимого диапазона (от 0 до (TX_MAX_PRIORITIES-1)).
- **TX_THRESH_ERROR** (0x18) — указан недопустимый порог вытеснения. Это значение должно быть допустимым приоритетом, меньшим или равным начальному приоритету потока.
- **TX_START_ERROR** (0x10) — недопустимое значения параметра автоматического запуска (auto_start).
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_THREAD my_thread;
UINT status;

/* Create a thread of priority 15 whose entry point is
"my_thread_entry". This thread’s stack area is 1000
bytes in size, starting at address 0x400000. The
preemption-threshold is setup to allow preemption of threads
with priorities ranging from 0 through 14. Time-slicing is
disabled. This thread is automatically put into a ready
condition. */
status = tx_thread_create(&my_thread, "my_thread_name",
    my_thread_entry, 0x1234,
    (VOID *) 0x400000, 1000,
    15, 15, TX_NO_TIME_SLICE,
    TX_AUTO_START);

/* If status equals TX_SUCCESS, my_thread is ready
for execution! */

...

/* Thread’s entry function. When "my_thread" actually
begins execution, control is transferred to this
function. */

VOID my_thread_entry (ULONG initial_input)
{
    /* When we get here, the value of initial_input is
    0x1234. See how this was specified during
    creation. */
    /* The real work of the thread, including calls to
    other function should be called from here! */
    /* When this function returns, the corresponding
    thread is placed into a "completed" state. */
}
```

### <a name="see-also"></a>См. также:

- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_delete"></a>tx_thread_delete

Удаление потока приложения

### <a name="prototype"></a>Прототип

```c
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет указанный поток приложения. Так как указанный поток должен находиться в состоянии TERMINATED или COMPLETED, эту службу нельзя вызвать из потока, пытающегося удалить самого себя.

> [!NOTE]
> *За управление областью памяти, связанной со стеком потока, которая становится доступна после завершения этой службы,отвечает приложение. Кроме того, приложение должно предотвращать использование удаленного потока.*

### <a name="parameters"></a>Параметры

- **thread_ptr** — указатель на ранее созданный поток приложения.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное удаление потока.
- **TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток приложения.
- **TX_DELETE_ERROR** (0x11) — указанный поток не находится в состоянии TERMINATED или COMPLETED.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки и таймеры

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
TX_THREAD my_thread;
UINT status;

/* Delete an application thread whose control block is
"my_thread". Assume that the thread has already been
created with a call to tx_thread_create. */
status = tx_thread_delete(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
deleted. */
```

### <a name="see-also"></a>См. также:

- tx_thread_create
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_entry_exit_notify"></a>tx_thread_entry_exit_notify

Уведомление приложения о входе в поток и выходе из него

### <a name="prototype"></a>Прототип

```c
UINT tx_thread_entry_exit_notify(
    TX_THREAD *thread_ptr,
    VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```

### <a name="description"></a>Описание

Эта служба регистрирует функцию обратного вызова уведомления, которая вызывается при входе в указанный поток или выходе из него. Обработка обратного вызова уведомления определяется приложением.

> [!NOTE]
> Обратному вызову уведомления приложения о входе или выходе из потока не разрешено вызывать никакой API ThreadX с параметром приостановки.

### <a name="parameters"></a>Параметры

- **thread_ptr** — указатель на ранее созданный поток.
- **entry_exit_notify**— указатель на функцию уведомления приложения о входе или выходе из потока. Второй параметр функции уведомления о входе или выходе указывает на значение входа или выхода. Значение **TX_THREAD_ENTRY** (0x00) указывает на регистрацию входа в поток, а значение **TX_THREAD_EXIT** (0x01) — на регистрацию выхода из потока. Если это значение равно **TX_NULL**, уведомление отключено.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная регистрация функции уведомления о входе и выходе из потока.
- **TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система была скомпилирована с отключенными возможностями уведомлений.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
TX_THREAD my_thread;
/* Register the "my_entry_exit_notify" function for monitoring
the entry/exit of the thread "my_thread." */
status = tx_thread_entry_exit_notify(&my_thread,
    my_entry_exit_notify);

/* If status is TX_SUCCESS the entry/exit notification function was
successfully registered. */
void my_entry_exit_notify(TX_THREAD *thread_ptr, UINT condition)
{
    /* Determine if the thread was entered or exited. */
    if (condition == TX_THREAD_ENTRY)
        /* Thread entry! */
    else if (condition == TX_THREAD_EXIT)
        /* Thread exit! */
}
```

### <a name="see-also"></a>См. также:

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_identify"></a>tx_thread_identify

Получает указатель на выполняющийся в данный момент поток

### <a name="prototype"></a>Прототип

```c
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a>Описание

Эта служба возвращает указатель на выполняющийся в данный момент поток. Если ни один поток не выполняется, служба возвращает пустой указатель.

> [!NOTE]
> *Если эта служба вызывается из ISR, возвращаемое значение представляет собой поток, запущенный до выполнения обработчика прерываний.*

### <a name="parameters"></a>Параметры

None

### <a name="retuen-values"></a>Возвращаемые значения

- **указатель на поток** — указатель на выполняющийся в данный момент поток. Если ни один поток не выполняется, возвращается значение **TX_NULL**.

### <a name="allowed-from"></a>Допустимые источники

Потоки и подпрограммы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

TX_THREAD *my_thread_ptr;

```c
TX_THREAD *my_thread_ptr;

/* Find out who we are! */
my_thread_ptr = tx_thread_identify();

/* If my_thread_ptr is non-null, we are currently executing
from that thread or an ISR that interrupted that thread.
Otherwise, this service was called
from an ISR when no thread was running when the
interrupt occurred. */
```

### <a name="see-also"></a>См. также:

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_info_get"></a>tx_thread_info_get

Получение сведений о потоке

### <a name="prototype"></a>Прототип

```c
UINT tx_thread_info_get(
    TX_THREAD *thread_ptr, 
    CHAR **name,
    UINT *state, 
    ULONG *run_count,
    UINT *priority,
    UINT *preemption_threshold,
    ULONG *time_slice,
    TX_THREAD **next_thread,
    TX_THREAD **suspended_thread);
```

### <a name="description"></a>Описание

Эта служба получает сведения об указанном потоке.

### <a name="parameters"></a>Параметры
- **thread_ptr** — указатель на блок управления потоком.
- **name** — указатель на назначение для указателя на имя потока.
- **state** — указатель на назначение для текущего состояния выполнения потока. Возможны следующие значения.
    - **TX_READY** (0x00)
    - **TX_COMPLETED** (0x01)
    - **TX_TERMINATED** (0x02)
    - **TX_SUSPENDED** (0x03)
    - **TX_SLEEP** (0x04)
    - **TX_QUEUE_SUSP** (0x05)
    - **TX_SEMAPHORE_SUSP** (0x06)
    - **TX_EVENT_FLAG** (0x07)
    - **TX_BLOCK_MEMORY** (0x08)
    - **TX_BYTE_MEMORY** (0x09)
    - **TX_MUTEX_SUSP** (0x0D)  

- **run_count** — указатель на назначение для счетчика выполнения потока.
- **priority** — указатель на место назначения для приоритета потока.
- **preemption_threshold** — указатель на назначение для порога вытеснения потока.
**time_slice** — указатель на назначение для временного среза потока.
**next_thread** — указатель на назначение для указателя на следующий созданный поток.

**suspended_thread** — указатель на назначение для указателя на следующий поток в списке приостановки.

> [!NOTE]
> *Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о потоке.
- **TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
TX_THREAD my_thread;
CHAR *name;
UINT state;
ULONG run_count;
UINT priority;
UINT preemption_threshold;
UINT time_slice;
TX_THREAD *next_thread;
TX_THREAD *suspended_thread;
UINT status;

/* Retrieve information about the previously created
thread "my_thread." */

status = tx_thread_info_get(&my_thread, &name,
    &state, &run_count,
    &priority, &preemption_threshold,
    &time_slice, &next_thread,&suspended_thread);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>См. также:

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_performance_info_get"></a>tx_thread_performance_info_get

Получение информации о производительности потока

### <a name="prototype"></a>Прототип

```c
UINT tx_thread_performance_info_get(
    TX_THREAD *thread_ptr,
    LONG *resumptions, 
    ULONG *suspensions,
    ULONG *solicited_preemptions, 
    ULONG *interrupt_preemptions,
    ULONG *priority_inversions, 
    ULONG *time_slices,
    ULONG *relinquishes, 
    ULONG *timeouts, 
    ULONG *wait_aborts,
    TX_THREAD **last_preempted_by);
```

### <a name="description"></a>Описание

Эта служба получает сведения о производительности указанного потока.

> [!IMPORTANT]
> *Библиотека ThreadX и приложение должны быть построены с определенным параметром* ***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _, чтобы служба могла вернуть сведения о производительности*.

### <a name="parameters"></a>Параметры
- **thread_ptr** — указатель на ранее созданный поток.
- **resumptions** — указатель на место назначения для числа возобновлений этого потока.
- **suspensions** — указатель на место назначения для числа приостановок этого потока.
- **solicited_preemptions** — указатель на назначение для числа вытеснений в результате вызова службы API ThreadX, выполненного этим потоком.
- **interrupt_preemptions** — указатель на место назначения для количества вытеснений этого потока в результате обработки прерываний.
- **inversions** — указатель на место назначения для числа инверсий приоритета для этого потока.
- **time_slices** — указатель на место назначения для числа временных срезов для этого потока.
- **relinquishes** — указатель на место назначения для числа освобождений потоков, выполненных этим потоком.
- **timeouts** — указатель на место назначения для количества истечений времени ожидания во время приостановки в этом потоке.
- **wait_aborts** — указатель на место назначения для количества прерываний ожидания, выполненных в этом потоке.
- **last_preempted_by** — указатель на место назначения для указателя на поток, который последним вытеснял этот поток.

> [!NOTE]
> *Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о производительности потока.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель на поток.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
TX_THREAD my_thread;
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
TX_THREAD *last_preempted_by;

/* Retrieve performance information on the previously created
thread. */

status = tx_thread_performance_info_get(&my_thread, &resumptions,
    &suspensions,
    &solicited_preemptions, &interrupt_preemptions,
    &priority_inversions, &time_slices,
    &relinquishes, &timeouts,
    &wait_aborts, &last_preempted_by);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_performance_system_info_get"></a>tx_thread_performance_system_info_get

Получение сведений о производительности системы потоков

### <a name="prototype"></a>Прототип

```c
UINT tx_thread_performance_system_info_get(
    ULONG *resumptions,
    ULONG *suspensions, 
    ULONG *solicited_preemptions,
    ULONG *interrupt_preemptions, 
    ULONG *priority_inversions,
    ULONG *time_slices, 
    ULONG *relinquishes, 
    ULONG *timeouts,
    ULONG *wait_aborts, 
    ULONG *non_idle_returns,
    ULONG *idle_returns);
```

### <a name="description"></a>Описание

Эта служба получает сведения о производительности всех потоков в системе.

*Библиотека ThreadX и приложение должны быть построены с определенным параметром*

***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _, чтобы служба могла вернуть сведения о производительности*.

### <a name="parameters"></a>Параметры

- **resumptions** — указатель на место назначения для общего числа возобновлений потоков.
- **suspensions** — указатель на место назначения для общего числа приостановок потоков.
- **solicited_preemptions** — указатель на назначение для общего числа вытеснений потоков в результате вызова потоком службы API ThreadX.
- **interrupt_preemptions** — указатель на место назначения для общего числа вытеснений потоков в результате обработки прерываний.
- **priority_inversions** — указатель на место назначения для общего числа инверсий приоритета потоков.
- **time_slices** — указатель на место назначения для общего числа временных срезов потоков.
- **relinquishes** — указатель на место назначения для общего числа освобождений потоков.
- **timeouts** — указатель на место назначения для общего количества истечений времени ожидания во время приостановки потоков.
- **wait_aborts** — указатель на место назначения для общего количества прерываний ожидания потоков.
- **non_idle_returns** — указатель на место назначения, указывающее, сколько раз поток возвращался в систему, когда другой поток был готов к выполнению.
- **idle_returns** — указатель на место назначения, указывающее, сколько раз поток возвращался в систему, когда не было других потоков, готовых к выполнению (простаивающая система).

> [!NOTE]
> *Указание **TX_NULL** для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о производительности системы потоков.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
ULONG resumptions;
ULONG suspensions;
ULONG solicited_preemptions;
ULONG interrupt_preemptions;
ULONG priority_inversions;
ULONG time_slices;
ULONG relinquishes;
ULONG timeouts;
ULONG wait_aborts;
ULONG non_idle_returns;
ULONG idle_returns;

/* Retrieve performance information on all previously created
thread. */

status = tx_thread_performance_system_info_get(&resumptions,
    &suspensions,
    &solicited_preemptions, &interrupt_preemptions,
    &priority_inversions, &time_slices, &relinquishes,
    &timeouts, &wait_aborts, &non_idle_returns,
    &idle_returns);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_preemption_change"></a>tx_thread_preemption_change

Изменение порога вытеснения потока приложения

### <a name="prototype"></a>Прототип

```c
UINT tx_thread_preemption_change(
    TX_THREAD *thread_ptr,
    UINT new_threshold, 
    UINT *old_threshold);
```

### <a name="description"></a>Описание

Эта служба изменяет порог вытеснения указанного потока. Порог вытеснения предотвращает вытеснение указанного потока потоками с приоритетом равным или меньшим значения порога вытеснения.

>[!NOTE]
> *При использовании порога вытеснения отключаются временные срезы для указанного потока.*

### <a name="parameters"></a>Параметры
- **thread_ptr** — указатель на ранее созданный поток приложения.
- **new_threshold** — новый уровень приоритета для порога вытеснения (от 0 до (TX_MAX_PRIORITIES-1)).
- **old_threshold** — указатель на расположение для возврата предыдущего значения порога вытеснения.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное изменение порога вытеснения.
- **TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток приложения.
- **TX_THRESH_ERROR** (0x18) — указанный новый приоритет вытеснения либо не является допустимым приоритетом потока (значение вне диапазона от 0 до (**TX_MAX_PRIORITIES**-1)), либо больше (низкий приоритет), чем текущее значение приоритета потока.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель на расположение для хранения предыдущего значения порога вытеснения.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки и таймеры

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_THREAD my_thread;
UINT my_old_threshold;
UINT status;

/* Disable all preemption of the specified thread. The
current preemption-threshold is returned in
"my_old_threshold". Assume that "my_thread" has
already been created. */

status = tx_thread_preemption_change(&my_thread,
    0, &my_old_threshold);

/* If status equals TX_SUCCESS, the application thread is
non-preemptable by another thread. Note that ISRs are
not prevented by preemption disabling. */
```

### <a name="see-also"></a>См. также:

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_priority_change"></a>tx_thread_priority_change

Изменение приоритета потока приложения

### <a name="prototype"></a>Прототип

```c
UINT tx_thread_priority_change(
    TX_THREAD *thread_ptr,
    UINT new_priority, 
    UINT *old_priority);
```

### <a name="description"></a>Описание

Эта служба изменяет приоритет указанного потока. Допустимые значения находятся в диапазоне от 0 до (TX_MAX_PRIORITES-1), где значение 0 соответствует наивысшему приоритету.

> [!IMPORTANT]
> * Порог вытеснения указанного потока автоматически устанавливается в соответствии с новым приоритетом. Если требуется установить новое пороговое значение, после вызова этой службы необходимо вызвать службу ***tx_thread_preemption_change** _._

### <a name="parameters"></a>Параметры

- **thread_ptr** — указатель на ранее созданный поток приложения.
- **new_priority** — новый уровень приоритета потока (от 0 до (TX_MAX_PRIORITIES-1)).
- **old_priority** — указатель на расположение для возврата предыдущего приоритета потока.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное изменение приоритета.
- **TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток приложения.
- **TX_PRIORITY_ERROR** (0x0F) указан недопустимый новый приоритет (значение вне диапазона от 0 до (TX_MAX_PRIORITIES-1)).
- **TX_PTR_ERROR** (0x03) — недопустимый указатель на расположение для хранения предыдущего значения приоритета.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки и таймеры

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_THREAD my_thread;
UINT my_old_priority;
UINT status;

/* Change the thread represented by "my_thread" to priority
0. */

status = tx_thread_priority_change(&my_thread,
    0, &my_old_priority);

/* If status equals TX_SUCCESS, the application thread is
now at the highest priority level in the system. */
```
### <a name="see-also"></a>См. также:

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_relinquish"></a>tx_thread_relinquish

Передача управления другим потокам приложений

### <a name="prototype"></a>Прототип

```c
VOID tx_thread_relinquish(VOID);
```

### <a name="description"></a>Описание

Эта служба передает управление процессором другим готовым к запуску потокам с таким же или более высоким приоритетом.

> [!NOTE]
> *Помимо передачи управления потоками с таким же приоритетом, эта служба также передает управление потоку с наивысшим приоритетом, выполнение которого запрещено из-за настройки порога вытеснения текущего потока.*

### <a name="parameters"></a>Параметры

None

### <a name="return-values"></a>Возвращаемые значения

Нет

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="examples"></a>Примеры

```c
ULONG run_counter_1 = 0;
ULONG run_counter_2 = 0;

/* Example of two threads relinquishing control to
each other in an infinite loop. Assume that
both of these threads are ready and have the same
priority. The run counters will always stay within one
of each other. */

VOID my_first_thread(ULONG thread_input)
{
    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_1++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}

VOID my_second_thread(ULONG thread_input)
{

    /* Endless loop of relinquish. */
    while(1)
    {
        /* Increment the run counter. */
        run_counter_2++;

        /* Relinquish control to other thread. */
        tx_thread_relinquish();
    }
}
```

### <a name="see-also"></a>См. также:

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_reset"></a>tx_thread_reset

Сброс потока

### <a name="prototype"></a>Прототип

```c
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Описание

Эта служба сбрасывает указанный поток для выполнения в точке входа, определенной при создании потока. Для выполнения сброса поток должен находиться либо в состоянии **TX_COMPLETED**, либо в состоянии **TX_TERMINATED**.

> [!IMPORTANT]
> *Для повторного выполнения поток необходимо возобновить.*

### <a name="parameters"></a>Параметры

- **thread_ptr** — указатель на ранее созданный поток.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешный сброс потока.
- **TX_NOT_DONE** (0x20) — указанный поток не находится в состоянии **TX_COMPLETED** или **TX_TERMINATED**.
- **TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

TX_THREAD my_thread;

```c
TX_THREAD my_thread;

/* Reset the previously created thread "my_thread." */

status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```

### <a name="see-also"></a>См. также:

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preformance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_resume"></a>tx_thread_resume

Возобновление приостановленного потока приложения

### <a name="prototype"></a>Прототип

```c
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Описание

Эта служба возобновляет или подготавливает к выполнению поток, который ранее был приостановлен вызовом ***tx_thread_suspend***. Кроме того, эта служба возобновляет потоки, созданные без автоматического запуска.

### <a name="parameters"></a>Параметры

- **thread_ptr** — указатель на приостановленный поток приложения.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное возобновление потока.
- **TX_SUSPEND_LIFTED** (0x19) — ранее установленная отсроченная приостановка была снята.
- **TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток приложения.
- **TX_RESUME_ERROR** (0x12) — указанный поток не приостановлен или приостановлен службой, отличной от **_tx_thread_suspend_**.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Да

TX_THREAD my_thread;

### <a name="example"></a>Пример

```c
TX_THREAD my_thread;
UINT status;

/* Resume the thread represented by "my_thread". */
status = tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
now ready to execute. */
```

### <a name="see-also"></a>См. также:

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_sleep"></a>tx_thread_sleep

Приостановка текущего потока на указанное время

### <a name="prototype"></a>Прототип

```c
UINT tx_thread_sleep(ULONG timer_ticks);
```

### <a name="description"></a>Описание

Эта служба приводит к приостановке вызывающего потока на указанное количество тактов таймера. Количество физического времени, связанное с тактом таймера, зависит от приложения. Эту службу можно вызывать только из потока приложения.

### <a name="parameters"></a>Параметры

- **timer_ticks** — число тактов таймера для приостановки вызывающего потока приложения в диапазоне от 0 до 0xFFFFFFFF. Если указано значение 0, служба завершает работу немедленно.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная приостановка работы потока.
- **TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.
- **TX_CALLER_ERROR** (0x13) — служба вызывается из непотока.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
UINT status;

/* Make the calling thread sleep for 100
timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
application thread slept for the specified number of
timer-ticks. */
```

### <a name="see-also"></a>См. также:

- tx_thread_create, tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_stack_error_notify"></a>tx_thread_stack_error_notify

Регистрация обратного вызова уведомления об ошибках стека потока

### <a name="prototype"></a>Прототип

```c
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```

### <a name="description"></a>Описание

Эта служба регистрирует функцию обратного вызова уведомлений для обработки ошибок стека потоков. Когда ThreadX обнаруживает ошибку стека потока во время выполнения, он вызывает эту функцию уведомления для обработки ошибки. Порядок обработки ошибки полностью определяется приложением. Может быть выполнено все, что угодно: от приостановки нарушающего потока до перезагрузки всей системы.

> [!IMPORTANT]
> *Библиотека ThreadX должна быть построена с определенным параметром* **TX_ENABLE_STACK_CHECKING** *, чтобы служба могла вернуть сведения о производительности.*

### <a name="parameters"></a>Параметры
- **error_handler** — указатель на функцию обработки ошибок стека приложения. Если это значение равно TX_NULL, уведомление отключено.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешный сброс потока.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX
so that thread stack errors can be handled by the application. */
status = tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```

### <a name="see-also"></a>См. также:

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_preformance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_suspend"></a>tx_thread_suspend

Приостановка потока приложения

### <a name="prototype"></a>Прототип

```c
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Описание

Эта служба приостанавливает указанный поток приложения. Поток может вызывать эту службу для приостановки самого себя.

> [!NOTE]
> *Если указанный поток уже приостановлен по другой причине, эта приостановка сохраняется до тех пор, пока предыдущая приостановка не будет снята. Когда это случится, выполняется безусловная приостановка указанного потока. Дальнейшие запросы на безусловную приостановку не будут иметь силы.*

После приостановки поток должен быть возобновлен с помощью ***tx_thread_resume*** для продолжения выполнения.

### <a name="parameters"></a>Параметры

- **thread_ptr** — указатель на поток приложения.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная приостановка потока.
- **TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток приложения.
- **TX_SUSPEND_ERROR** (0x14) — указанный поток находится в состоянии TERMINATED или COMPLETED.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_THREAD my_thread;
UINT status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
unconditionally suspended. */
```

### <a name="see-also"></a>См. также:

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_terminate
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_terminate"></a>tx_thread_terminate

Прекращение потока приложения

### <a name="prototype"></a>Прототип

```c
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a>Описание

Эта служба прекращает указанный поток приложения независимо от того, приостановлен ли он. Поток может вызывать эту службу для завершения самого себя.

> [!NOTE]
> *Ответственность за то, что поток находится в состоянии, подходящем для завершения, лежит на приложении. Например, поток не должен завершаться во время выполнения критической обработки приложения или внутри других компонентов промежуточного слоя, где он может оставить такую обработку в неизвестном состоянии.*

> [!IMPORTANT]
> *После завершения работы поток должен быть сброшен для его повторного выполнения.*

### <a name="parameters"></a>Параметры

- **thread_ptr** — указатель на поток приложения.

### <a name="return-values"></a>Возвращаемые значения
- **TX_SUCCESS** (0x00) — успешное завершение потока.
- **TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток приложения.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки и таймеры

### <a name="preemption-possible"></a>Возможно вытеснение

Да

### <a name="example"></a>Пример

```c
TX_THREAD my_thread;
UINT status;

/* Terminate the thread represented by "my_thread". */
status = tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
and cannot execute again until it is reset. */
```

### <a name="see-also"></a>См. также:

- tx_thread_create tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_time_slice_change
- tx_thread_wait_abort

## <a name="tx_thread_time_slice_change"></a>tx_thread_time_slice_change

Изменение интервала времени потока приложения

### <a name="prototype"></a>Прототип

```c
UINT tx_thread_time_slice_change(
    TX_THREAD *thread_ptr,
    ULONG new_time_slice, 
    ULONG *old_time_slice);
```

### <a name="description"></a>Описание

Эта служба изменяет временной срез указанного потока приложения. Выбор временного среза для потока гарантирует, что он не будет выполняться больше указанного количества тактов таймера, прежде чем другие потоки с такими же или более высокими приоритетами получат возможность запуска.

> [!NOTE]
> *При использовании порога вытеснения отключаются временные срезы для указанного потока.*

### <a name="parameters"></a>Параметры

- **thread_ptr** — указатель на поток приложения.
- **new_time_slice** — новое значение временного среза. Допустимые значения: TX_NO_TIME_SLICE и числовые значения от 1 до 0xFFFFFFFF.
- **old_time_slice** — указатель на расположение для хранения предыдущего значения временного среза указанного потока.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное изменение временного среза.
- **TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток приложения.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель на расположение для хранения предыдущего значения временного среза.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки и таймеры

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
TX_THREAD my_thread;
ULONG my_old_time_slice;
UINT status;

/* Change the time-slice of the thread associated with
"my_thread" to 20. This will mean that "my_thread"
can only run for 20 timer-ticks consecutively before
other threads of equal or higher priority get a chance
to run. */
status = tx_thread_time_slice_change(&my_thread, 20,
    &my_old_time_slice);

/* If status equals TX_SUCCESS, the thread’s time-slice
has been changed to 20 and the previous time-slice is
in "my_old_time_slice." */
```

### <a name="see-also"></a>См. также:

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_wait_abort

## <a name="tx_thread_wait_abort"></a>tx_thread_wait_abort

Прерывание приостановки указанного потока

### <a name="prototype"></a>Прототип

```c
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a>Описание

Эта служба прерывает спящий режим или любую другую приостановку объекта указанного потока. Если ожидание прерывается, то из службы, которую ожидает поток, возвращается значение **TX_WAIT_ABORTED**.

> [!NOTE]
> *Эта служба не освобождает явную приостановку, выполненную службой tx_thread_suspend.*

### <a name="parameters"></a>Параметры

- **thread_ptr** — указатель на ранее созданный поток приложения.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное прерывание приостановки.
- **TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток приложения.
- **TX_WAIT_ABORT_ERROR** (0x1B) — указанный поток не находится в состоянии ожидания.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение
Да

### <a name="example"></a>Пример

```c
TX_THREAD my_thread;
UINT status;

/* Abort the suspension condition of "my_thread." */
status = tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
again, with a return value showing its suspension
was aborted (TX_WAIT_ABORTED). */
```

### <a name="see-also"></a>См. также:

- tx_thread_create
- tx_thread_delete
- tx_thread_entry_exit_notify
- tx_thread_identify
- tx_thread_info_get
- tx_thread_performance_info_get
- tx_thread_performance_system_info_get
- tx_thread_preemption_change
- tx_thread_priority_change
- tx_thread_relinquish
- tx_thread_reset
- tx_thread_resume
- tx_thread_sleep
- tx_thread_stack_error_notify
- tx_thread_suspend
- tx_thread_terminate
- tx_thread_time_slice_change

## <a name="tx_time_get"></a>tx_time_get

Получение текущего времени

Таймеры приложения

### <a name="prototype"></a>Прототип

```c
ULONG tx_time_get(VOID);
```

### <a name="description"></a>Описание

Эта служба возвращает информацию, содержащуюся во внутренних системных часах. Каждый такт таймера увеличивает значение внутренних системных часов на единицу. Во время инициализации системные часы устанавливаются в нулевое значение, а их значение можно изменить с помощью службы ***tx_time_set***.

> [!NOTE]
> *Фактическое время, которое представляет каждый такт таймера, зависит от конкретного приложения.*

**Параметры**

Нет

### <a name="return-values"></a>Возвращаемые значения

- **такты системных часов** — значение внутренних, автономных системных часов.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение
Нет

### <a name="example"></a>Пример

```c
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time = tx_time_get();

/* Current time now contains a copy of the internal system
clock. */
```

### <a name="see-also"></a>См. также:

- tx_time_set

## <a name="tx_time_set"></a>tx_time_set

Установка текущего времени

### <a name="prototype"></a>Прототип

```c
VOID tx_time_set(ULONG new_time);
```

### <a name="description"></a>Описание

Эта служба устанавливает для внутренних системных часов указанное значение. Каждый такт таймера увеличивает значение внутренних системных часов на единицу.

> [!NOTE]
> *Фактическое время, которое представляет каждый такт таймера, зависит от конкретного приложения.*

### <a name="parameters"></a>Параметры

- **new_time** — новое значение времени для размещения в системных часах, допустимы значения от 0 до 0xFFFFFFFF.

### <a name="return-values"></a>Возвращаемые значения

Нет

### <a name="allowed-from"></a>Допустимые источники

Потоки, таймеры и подпрограммы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
interrupt. */
```

### <a name="see-also"></a>См. также:

- tx_time_get

## <a name="tx_timer_activate"></a>tx_timer_activate

Активация таймера приложения

### <a name="prototype"></a>Прототип

```c
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```

### <a name="description"></a>Описание

Эта служба активирует указанный таймер приложения. Подпрограммы после истечения срока действия таймеров, которые истекают одновременно, выполняются в том порядке, в котором они были активированы.

> [!NOTE]
> *Таймер с истекшим сроком действия должен быть сброшен с помощью* ***tx_timer_change** _, _прежде чем его можно будет активировать снова*.

### <a name="parameters"></a>Параметры

- **timer_ptr** — указатель на ранее созданный таймер приложения.

**Возвращаемые значения**

- **TX_SUCCESS** (0x00) — успешная активация таймера приложения.
- **TX_TIMER_ERROR** (0x15) — недопустимый указатель на таймер приложения.
- **TX_ACTIVATE_ERROR** (0x17) — таймер уже активен или является одноразовым таймером, срок действия которого уже истек.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
TX_TIMER my_timer;
UINT status;

/* Activate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now active. */
```

### <a name="see-also"></a>См. также:

- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_change"></a>tx_timer_change

Изменение таймера приложения

### <a name="prototype"></a>Прототип

```c
UINT tx_timer_change(
    TX_TIMER *timer_ptr,
    ULONG initial_ticks, 
    ULONG reschedule_ticks);
```

### <a name="description"></a>Описание

Эта служба изменяет характеристики истечения срока действия указанного таймера приложения. Перед вызовом этой службы таймер должен быть деактивирован.

> [!NOTE]
> *Для повторного запуска таймера после вызова этой службы требуется вызов службы* ***tx_timer_activate** _ _*.

### <a name="parameters"></a>Параметры

- **timer_ptr** — указатель на управляющий блок таймера.
- **initial_ticks** — указывает начальное число тактов для расчета срока действия таймера. Допустимые значения находятся в диапазоне от 1 до 0xFFFFFFFF.
- **reschedule_ticks** — задает количество тактов для всех истечений таймера после первого. Значение ноль для этого параметра делает таймер *одноразовым*. В противном случае для периодических таймеров допустимы значения в диапазоне от 1 до 0xFFFFFFFF.

> [!NOTE]
> *Таймер с истекшим сроком действия должен быть сброшен с помощью*
***tx_timer_change** _, _прежде чем его можно будет активировать снова*.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное изменение таймера приложения.
- **TX_TIMER_ERROR** (0x15) — недопустимый указатель на таймер приложения.
- **TX_TICK_ERROR** (0x16) — указано недопустимое значение (ноль) для начальных тактов.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки, таймеры и подпрограммы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
TX_TIMER my_timer;
UINT status;

/* Change a previously created and now deactivated timer
to expire every 50 timer ticks, including the initial
expiration. */
status = tx_timer_change(&my_timer,50, 50);

/* If status equals TX_SUCCESS, the specified timer is
changed to expire every 50 ticks. */

/* Activate the specified timer to get it started again. */
status = tx_timer_activate(&my_timer);
```

### <a name="see-also"></a>См. также:

- tx_timer_activate
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_create"></a>tx_timer_create

Создание таймера приложения

### <a name="prototype"></a>Прототип

```c
UINT tx_timer_create(
    TX_TIMER *timer_ptr, 
    CHAR *name_ptr,
    VOID (*expiration_function)(ULONG),
    ULONG expiration_input, 
    ULONG initial_ticks,
    ULONG reschedule_ticks, 
    UINT auto_activate);
```

### <a name="description"></a>Описание

Эта служба создает таймер приложения с указанной функцией истечения времени, а также периодичностью.

### <a name="parameters"></a>Параметры

- **timer_ptr** — указатель на управляющий блок таймера.
- **name_ptr** — указатель на имя таймера.
- **expiration_function** — функция приложения, вызываемая по истечении срока действия таймера.
- **expiration_input** — входные данные для передачи в функцию истечения срока действия по истечении срока действия таймера.
- **initial_ticks** — указывает начальное число тактов для расчета срока действия таймера. Допустимые значения находятся в диапазоне от 1 до 0xFFFFFFFF.
- **reschedule_ticks** — задает количество тактов для всех истечений таймера после первого. Значение ноль для этого параметра делает таймер *одноразовым*. В противном случае для периодических таймеров допустимы значения в диапазоне от 1 до 0xFFFFFFFF.

  > [!NOTE]
  > *После истечения срока действия одноразового таймера его необходимо сбросить с помощью tx_timer_change, прежде чем его можно будет активировать снова.*

- **auto_activate** — определяет, активируется ли таймер автоматически во время создания. Если это значение равно **TX_AUTO_ACTIVATE** (0x01), таймер становится активным. В противном случае, если выбрано значение **TX_NO_ACTIVATE** (0x00), таймер создается в неактивном состоянии. В этом случае для фактического запуска таймера необходим последующий сервисный вызов **_tx_timer_activate_**.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное создание таймера приложения.
- **TX_TIMER_ERROR** (0x15) — недопустимый указатель на таймер приложения. Либо указатель имеет значение NULL, либо таймер уже создан.
- **TX_TICK_ERROR** (0x16) — указано недопустимое значение (ноль) для начальных тактов.
- **TX_ACTIVATE_ERROR** (0x17) — задано неверное значение параметра активации.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
TX_TIMER my_timer;
UINT status;

/* Create an application timer that executes
"my_timer_function" after 100 ticks initially and then
after every 25 ticks. This timer is specified to start
immediately! */
status = tx_timer_create(&my_timer,"my_timer_name",
    my_timer_function, 0x1234, 100, 25,
    TX_AUTO_ACTIVATE);

/* If status equals TX_SUCCESS, my_timer_function will
be called 100 timer ticks later and then called every
25 timer ticks. Note that the value 0x1234 is passed to
my_timer_function every time it is called. */
```

### <a name="see-also"></a>См. также:

- tx_timer_activate
- tx_timer_change
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_deactivate"></a>tx_timer_deactivate

Деактивация таймера приложения

### <a name="prototype"></a>Прототип

```c
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a>Описание

Эта служба деактивирует указанный таймер приложения. Если таймер уже деактивирован, эта служба не действует.

### <a name="parameters"></a>Параметры

- **timer_ptr** — указатель на ранее созданный таймер приложения.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешная деактивация таймера приложения.
- **TX_TIMER_ERROR** (0x15) — недопустимый указатель на таймер приложения.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
TX_TIMER my_timer;
UINT status;

/* Deactivate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now deactivated. */
```

### <a name="see-also"></a>См. также:

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_delete"></a>tx_timer_delete

Удаление таймера приложения

### <a name="prototype"></a>Прототип

```c
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет указанный таймер приложения.

> [!NOTE]
> *Ответственность за предотвращение использования удаленного таймера лежит на приложении.*

### <a name="parameters"></a>Параметры

- **timer_ptr** — указатель на ранее созданный таймер приложения.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное удаление таймера приложения.
- **TX_TIMER_ERROR** (0x15) — недопустимый указатель на таймер приложения.
- **TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="preemption-possible"></a>Возможно вытеснение

Нет

### <a name="example"></a>Пример

```c
TX_TIMER my_timer;
UINT status;

/* Delete application timer. Assume that the application
timer has already been created. */
status = tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
deleted. */
```

### <a name="see-also"></a>См. также:

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_info_get"></a>tx_timer_info_get

Получение сведений о таймере приложения

### <a name="prototype"></a>Прототип

```c
UINT tx_timer_info_get(
    TX_TIMER *timer_ptr, 
    CHAR **name,
    UINT *active,
    ULONG *remaining_ticks,
    ULONG *reschedule_ticks,
    TX_TIMER **next_timer);
```

### <a name="description"></a>Описание

Эта служба получает сведения об указанном таймере приложения.

### <a name="parameters"></a>Параметры

- **timer_ptr** — указатель на ранее созданный таймер приложения.
- **name** — указатель на назначение для указателя на имя таймера.
- **active** — указатель на назначение для индикации активности таймера. Если таймер неактивен или эта служба вызывается из самого таймера, возвращается значение **TX_FALSE**. В противном случае, если таймер активен, возвращается значение **TX_TRUE**.
- **remaining_ticks** — указатель на место назначения для количества тактов таймера, оставшихся до истечения его срока действия.
- **reschedule_ticks** — указатель на место назначения для количества тактов таймера, которые будут использоваться для автоматического повторного планирования этого таймера. Если значение равно нулю, то таймер является одноразовым и не будет перепланирован.
- **next_timer** — указатель на назначение для указателя следующего созданного таймера приложения.

> [!NOTE]
> *Указание **TX_NULL** для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о таймере.
- **TX_TIMER_ERROR** (0x15) — недопустимый указатель на таймер приложения.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="preemption-possible"></a>Возможно вытеснение

нет

### <a name="example"></a>Пример

```c
TX_TIMER my_timer;
CHAR *name;
UINT active;
ULONG remaining_ticks;
ULONG reschedule_ticks;
TX_TIMER *next_timer;
UINT status;

/* Retrieve information about the previously created
application timer "my_timer." */
status = tx_timer_info_get(&my_timer, &name,
    &active,&remaining_ticks,
    &reschedule_ticks,
    &next_timer);

/* If status equals TX_SUCCESS, the information requested is
valid. */
```

### <a name="see-also"></a>См. также:

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_performance_info_get"></a>tx_timer_performance_info_get

Получение сведений о производительности таймера

### <a name="prototype"></a>Прототип

```c
UINT tx_timer_performance_info_get(
    TX_TIMER *timer_ptr,
    ULONG *activates, 
    ULONG *reactivates,
    ULONG *deactivates, 
    ULONG *expirations,
    ULONG *expiration_adjusts);
```

### <a name="description"></a>Описание

Эта служба получает сведения о производительности указанного таймера приложения.

> [!IMPORTANT]
> *Библиотека ThreadX и приложение должны быть построены с определенным параметром* ***TX_TIMER_ENABLE_PERFORMANCE_INFO** _ _, чтобы служба могла вернуть сведения о производительности*.

### <a name="parameters"></a>Параметры
- **timer_ptr** — указатель на ранее созданный таймер.
- **activates** — указатель на место назначения для количества запросов на активацию, выполненных для этого таймера.
- **reactivates** — указатель на место назначения для количества автоматических повторных активаций, выполненных для этого периодического таймера.
- **deactivates** — указатель на место назначения для количества запросов на деактивацию, выполненных для этого таймера.
- **expirations** — указатель на место назначения для количества истечений срока действия этого таймера.
- **expiration_adjusts** — указатель на место назначения для количества внутренних корректировок срока действия, выполненных для этого таймера. Эти корректировки выполняются при обработке прерываний для таймеров, размер которых превышает размер списка таймеров по умолчанию (по умолчанию — таймеры со сроком действия более 32 тактов).

> [ПРИМЕЧАНИЕ] *Указание TX_NULL для любого параметра сообщает, что это параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о производительности таймера.
- **TX_PTR_ERROR** (0x03) — недопустимый указатель на таймер.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
TX_TIMER my_timer;
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on the previously created
timer. */
status = tx_timer_performance_info_get(&my_timer, &activates,
    &reactivates,&deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_system_info_get

## <a name="tx_timer_performance_system_info_get"></a>tx_timer_performance_system_info_get

Получение сведений о производительности системы таймеров

### <a name="prototype"></a>Прототип

```c
UINT tx_timer_performance_system_info_get(
    ULONG *activates,
    ULONG *reactivates, 
    ULONG *deactivates,
    ULONG *expirations, 
    ULONG *expiration_adjusts);
```

### <a name="description"></a>Описание

Эта служба получает сведения о производительности всех таймеров приложений в системе.

> [!IMPORTANT]
> *Библиотека ThreadX и приложение должны быть построены с определенным параметром* **TX_TIMER_ENABLE_PERFORMANCE_INFO**, *чтобы служба могла вернуть сведения о производительности.*

**Параметры**

- **activates** — указатель на место назначения для общего количества запросов на активацию, выполненных для всех таймеров.
- **reactivates** — указатель на место назначения для общего количества автоматических повторных активаций, выполненных для всех периодических таймеров.
- **deactivates** — указатель на место назначения для общего количества запросов на деактивацию, выполненных для всех таймеров.
- **expirations** — указатель на место назначения для общего количества истечений срока действия всех таймеров.
- **expiration_adjusts** — указатель на место назначения для общего количества внутренних корректировок срока действия, выполненных для всех таймеров. Эти корректировки выполняются при обработке прерываний для таймеров, размер которых превышает размер списка таймеров по умолчанию (по умолчанию — таймеры со сроком действия более 32 тактов).

> [!NOTE]
> *Указание **TX_NULL** для любого параметра сообщает, что этот параметр не является обязательным.*

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00) — успешное получение сведений о производительности системы таймеров.
- **TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки, таймеры, запросы ISR

### <a name="example"></a>Пример

```c
ULONG activates;
ULONG reactivates;
ULONG deactivates;
ULONG expirations;
ULONG expiration_adjusts;

/* Retrieve performance information on all previously created
timers. */
status = tx_timer_performance_system_info_get(&activates,
    &reactivates, &deactivates, &expirations,
    &expiration_adjusts);

/* If status is TX_SUCCESS the performance information was
successfully retrieved. */
```

### <a name="see-also"></a>См. также:

- tx_timer_activate
- tx_timer_change
- tx_timer_create
- tx_timer_deactivate
- tx_timer_delete
- tx_timer_info_get
- tx_timer_performance_info_get
