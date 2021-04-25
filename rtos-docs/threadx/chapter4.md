---
title: Глава 4. Описание служб ThreadX для ОСРВ Azure
description: В этой главе содержится описание всех служб ThreadX для ОСРВ Azure в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 60ecc96df07b1f77b9b448814c4420133f3e2afc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814359"
---
# <a name="chapter-4---description-of-azure-rtos-threadx-services"></a><span data-ttu-id="27adc-103">Глава 4. Описание служб ThreadX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="27adc-103">Chapter 4 - Description of Azure RTOS ThreadX Services</span></span>

<span data-ttu-id="27adc-104">В этой главе содержится описание всех служб ThreadX для ОСРВ Azure в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="27adc-104">This chapter contains a description of all Azure RTOS ThreadX services in alphabetic order.</span></span> <span data-ttu-id="27adc-105">Их имена сформированы таким образом, что все аналогичные службы группируются вместе.</span><span class="sxs-lookup"><span data-stu-id="27adc-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="27adc-106">В разделе "Возвращаемые значения" приведенных ниже описаний **выделенные полужирным шрифтом** значения не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки ошибок API. Значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="27adc-106">In the "Return Values" section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in nonbold are completely disabled.</span></span> <span data-ttu-id="27adc-107">Кроме того, слово "**Да**" под заголовком "**Возможно вытеснение**" указывает на то, что вызов службы может возобновить поток с более высоким приоритетом, что приведет к вытеснению вызывающего потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-107">In addition, a "**Yes**" listed under the "**Preemption Possible**" heading indicates that calling the service may resume a higher-priority thread, thus preempting the calling thread.</span></span>

## <a name="tx_block_allocate"></a><span data-ttu-id="27adc-108">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="27adc-108">tx_block_allocate</span></span>

<span data-ttu-id="27adc-109">Выделение блока памяти фиксированного размера</span><span class="sxs-lookup"><span data-stu-id="27adc-109">Allocate fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-110">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-110">Prototype</span></span>

```c
UINT tx_block_allocate(
    TX_BLOCK_POOL *pool_ptr, 
    VOID **block_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="27adc-111">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-111">Description</span></span>

<span data-ttu-id="27adc-112">Эта служба выделяет блок памяти фиксированного размера из указанного пула памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-112">This service allocates a fixed-size memory block from the specified memory pool.</span></span> <span data-ttu-id="27adc-113">Фактический размер блока памяти определяется во время создания пула памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-113">The actual size of the memory block is determined during memory pool creation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-114">*Важно убедиться, что код приложения не выполняет запись за пределы выделенного блока памяти. Если это случится, произойдет повреждение в смежном (обычно последующем) блоке памяти. Результаты являются непредсказуемыми и часто неустранимыми.*</span><span class="sxs-lookup"><span data-stu-id="27adc-114">*It is important to ensure application code does not write outside the allocated memory block. If this happens, corruption occurs in an adjacent (usually subsequent) memory block. The results are unpredictable and often fatal!*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-115">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-115">Parameters</span></span>

- <span data-ttu-id="27adc-116">**pool_ptr**</span><span class="sxs-lookup"><span data-stu-id="27adc-116">**pool_ptr**</span></span> <br><span data-ttu-id="27adc-117">Указатель на ранее созданный пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-117">Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="27adc-118">**block_ptr**</span><span class="sxs-lookup"><span data-stu-id="27adc-118">**block_ptr**</span></span> <br><span data-ttu-id="27adc-119">Указатель на указатель блока назначения.</span><span class="sxs-lookup"><span data-stu-id="27adc-119">Pointer to a destination block pointer.</span></span> <span data-ttu-id="27adc-120">При успешном выделении адрес выделенного блока памяти помещается в место, куда указывает этот параметр.</span><span class="sxs-lookup"><span data-stu-id="27adc-120">On successful allocation, the address of the allocated memory block is placed where this parameter points.</span></span>
- <span data-ttu-id="27adc-121">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="27adc-121">**wait_option**</span></span> <br><span data-ttu-id="27adc-122">Определяет, как служба будет вести себя, если нет доступных блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-122">Defines how the service behaves if there are no memory blocks available.</span></span> <span data-ttu-id="27adc-123">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="27adc-123">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="27adc-124">**TX_NO_WAIT** (0x00000000) — немедленный возврат из этой службы независимо от того, было ли выделение успешным.</span><span class="sxs-lookup"><span data-stu-id="27adc-124">**TX_NO_WAIT** (0x00000000) - Selecting **TX_NO_WAIT** results in an immediate return from this service regardless if it was successful or not.</span></span> <span data-ttu-id="27adc-125">*Это единственный допустимый параметр, если служба вызывается из непотока, например инициализации, таймера или ISR*.</span><span class="sxs-lookup"><span data-stu-id="27adc-125">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR*.</span></span>
  - <span data-ttu-id="27adc-126">**TX_WAIT_FOREVER** (0xFFFFFFF) — вызывающий поток приостанавливается на неопределенное время, пока не станет доступен блок памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-126">**TX_WAIT_FOREVER** (0xFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until a memory block is available.</span></span>
  - <span data-ttu-id="27adc-127">*значение времени ожидания* (от 0x00000001 до 0xFFFFFFFE) — задать максимальное число тактов таймера для приостановки работы при ожидании блока памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-127">*timeout value* (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-128">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-128">Return Values</span></span>

- <span data-ttu-id="27adc-129">**TX_SUCCESS** (0x00) — успешное выделение блока памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-129">**TX_SUCCESS**    (0x00)  Successful memory block allocation.</span></span>
- <span data-ttu-id="27adc-130">**TX_DELETED** (0x01) — пул блоков памяти был удален, пока поток был приостановлен.</span><span class="sxs-lookup"><span data-stu-id="27adc-130">**TX_DELETED**    (0x01)  Memory block pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="27adc-131">**TX_NO_MEMORY** (0x10) — службе не удалось выделить блок памяти в течение указанного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="27adc-131">**TX_NO_MEMORY**  (0x10)  Service was unable to allocate a block of memory within the specified time to wait.</span></span>
- <span data-ttu-id="27adc-132">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="27adc-132">**TX_WAIT_ABORTED**   (0x1A)  Suspension was aborted by another thread, timer or ISR.</span></span>
- <span data-ttu-id="27adc-133">**TX_POOL_ERROR** (0x02) — недопустимый указатель на пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-133">**TX_POOL_ERROR** (0x02)  Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="27adc-134">**TX_WAIT_ERROR** (0x04) — в вызове из непотокового запроса был указан параметр ожидания, отличный от TX_NO_WAIT.</span><span class="sxs-lookup"><span data-stu-id="27adc-134">**TX_WAIT_ERROR** (0x04)  A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="27adc-135">**TX_PTR_ERROR** (0x03) — недопустимый указатель на указатель назначения.</span><span class="sxs-lookup"><span data-stu-id="27adc-135">**TX_PTR_ERROR**  (0x03)  Invalid pointer to destination pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-136">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-136">Allowed From</span></span>

<span data-ttu-id="27adc-137">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-137">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-138">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-138">Preemption Possible</span></span>

<span data-ttu-id="27adc-139">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-139">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-140">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-140">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-141">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-141">See Also</span></span>

- <span data-ttu-id="27adc-142">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="27adc-142">tx_block_pool_create</span></span>
- <span data-ttu-id="27adc-143">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-143">tx_block_pool_delete</span></span>
- <span data-ttu-id="27adc-144">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-144">tx_block_pool_info_get</span></span>
- <span data-ttu-id="27adc-145">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-145">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="27adc-146">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-146">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-147">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-147">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="27adc-148">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="27adc-148">tx_block_release</span></span>

## <a name="tx_block_pool_create"></a><span data-ttu-id="27adc-149">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="27adc-149">tx_block_pool_create</span></span>

<span data-ttu-id="27adc-150">Создание пула блоков памяти фиксированного размера</span><span class="sxs-lookup"><span data-stu-id="27adc-150">Create pool of fixed-size memory blocks</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-151">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-151">Prototype</span></span>

```c
UINT tx_block_pool_create(
    TX_BLOCK_POOL pool_ptr,
    CHAR name_ptr, 
    ULONG block_size,
    VOID pool_start, 
    ULONG pool_size);
```

### <a name="description"></a><span data-ttu-id="27adc-152">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-152">Description</span></span>

<span data-ttu-id="27adc-153">Эта служба создает пул блоков памяти фиксированного размера.</span><span class="sxs-lookup"><span data-stu-id="27adc-153">This service creates a pool of fixed-size memory blocks.</span></span> <span data-ttu-id="27adc-154">Указанная область памяти делится на максимально возможное количество блоков памяти фиксированного размера по формуле:</span><span class="sxs-lookup"><span data-stu-id="27adc-154">The memory area specified is divided into as many fixed-size memory blocks as possible using the formula:</span></span>

<span data-ttu-id="27adc-155">**всего блоков** = (**всего байт**) / (**размер блока** + sizeof(void \*))</span><span class="sxs-lookup"><span data-stu-id="27adc-155">**total blocks** = (**total bytes**) / (**block size** + sizeof(void \*))</span></span>

> [!NOTE]
><span data-ttu-id="27adc-156">\* Каждый блок памяти содержит один указатель на служебные данные, который невидим для пользователя и представлен в предыдущей формуле членом "sizeof (void *)".*</span><span class="sxs-lookup"><span data-stu-id="27adc-156">\*Each memory block contains one pointer of overhead that is invisible to the user and is represented by the "sizeof(void *)" in the preceding formula.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-157">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-157">Parameters</span></span>

- <span data-ttu-id="27adc-158">**pool_ptr** — указатель на блок управления пулом блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-158">**pool_ptr**  Pointer to a memory block pool control block.</span></span>
- <span data-ttu-id="27adc-159">**name_ptr** — указатель на имя пула блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-159">**name_ptr**  Pointer to the name of the memory block pool.</span></span>
- <span data-ttu-id="27adc-160">**block_size** — число байтов в каждом блоке памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-160">**block_size**    Number of bytes in each memory block.</span></span>
- <span data-ttu-id="27adc-161">**pool_start** — начальный адрес пула блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-161">**pool_start**    Starting address of the memory block pool.</span></span> <span data-ttu-id="27adc-162">Начальный адрес должен быть выровнен по размеру типа данных ULONG.</span><span class="sxs-lookup"><span data-stu-id="27adc-162">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="27adc-163">**pool_size** — общее число байт, доступных для пула блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-163">**pool_size** Total number of bytes available for the memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-164">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-164">Return Values</span></span>

- <span data-ttu-id="27adc-165">**TX_SUCCESS** (0x00) — успешное создание пула блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-165">**TX_SUCCESS**    (0x00)  Successful memory block pool creation.</span></span>
- <span data-ttu-id="27adc-166">**TX_POOL_ERROR** (0x02) — недопустимый указатель на пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-166">**TX_POOL_ERROR** (0x02)  Invalid memory block pool pointer.</span></span> <span data-ttu-id="27adc-167">Либо указатель имеет значение NULL, либо пул уже создан.</span><span class="sxs-lookup"><span data-stu-id="27adc-167">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="27adc-168">**TX_PTR_ERROR** (0x03) — недопустимый начальный адрес пула.</span><span class="sxs-lookup"><span data-stu-id="27adc-168">**TX_PTR_ERROR**  (0x03)  Invalid starting address of the pool.</span></span>
- <span data-ttu-id="27adc-169">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-169">**TX_CALLER_ERROR**   (0x13)  Invalid caller of this service.</span></span>
- <span data-ttu-id="27adc-170">**TX_SIZE_ERROR** (0x05) — недопустимый размер пула.</span><span class="sxs-lookup"><span data-stu-id="27adc-170">**TX_SIZE_ERROR** (0x05)  Size of pool is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-171">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-171">Allowed From</span></span>

<span data-ttu-id="27adc-172">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-172">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-173">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-173">Preemption Possible</span></span>

<span data-ttu-id="27adc-174">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-174">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-175">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-175">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-176">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-176">See Also</span></span>

- <span data-ttu-id="27adc-177">tx_block_allocate, tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-177">tx_block_allocate, tx_block_pool_delete</span></span>
- <span data-ttu-id="27adc-178">tx_block_pool_info_get, tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-178">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="27adc-179">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-179">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-180">tx_block_pool_prioritize, tx_block_release</span><span class="sxs-lookup"><span data-stu-id="27adc-180">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_delete"></a><span data-ttu-id="27adc-181">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-181">tx_block_pool_delete</span></span>

<span data-ttu-id="27adc-182">Удаление пула блоков памяти</span><span class="sxs-lookup"><span data-stu-id="27adc-182">Delete memory block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-183">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-183">Prototype</span></span>

```c
UINT tx_block_pool_delete(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-184">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-184">Description</span></span>

<span data-ttu-id="27adc-185">Эта служба удаляет указанный пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-185">This service deletes the specified block-memory pool.</span></span> <span data-ttu-id="27adc-186">Все потоки, приостановленные в ожидании блока памяти из этого пула, возобновляются и получают состояние возврата **TX_DELETED**.</span><span class="sxs-lookup"><span data-stu-id="27adc-186">All threads suspended waiting for a memory block from this pool are resumed and given a **TX_DELETED** return status.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-187">*За управление областью памяти, связанной с пулом, которая становится доступна после завершения этой службы,отвечает приложение. Кроме того, приложение должно предотвращать использование удаленного пула или его прежних блоков памяти.*</span><span class="sxs-lookup"><span data-stu-id="27adc-187">*It is the application's responsibility to manage the memory area associated with the pool, which is available after this service completes. In addition, the application must prevent use of a deleted pool or its former memory blocks.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-188">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-188">Parameters</span></span>

- <span data-ttu-id="27adc-189">**pool_ptr** — указатель на ранее созданный пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-189">**pool_ptr** Pointer to a previously created memory block pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-190">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-190">Return Values</span></span>

- <span data-ttu-id="27adc-191">**TX_SUCCESS** (0x00) — успешное удаление пула блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-191">**TX_SUCCESS** (0x00) Successful memory block pool deletion.</span></span>
- <span data-ttu-id="27adc-192">**TX_POOL_ERROR** (0x02) — недопустимый указатель на пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-192">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>
- <span data-ttu-id="27adc-193">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-193">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-194">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-194">Allowed From</span></span>

<span data-ttu-id="27adc-195">Потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-195">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-196">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-196">Preemption Possible</span></span>

<span data-ttu-id="27adc-197">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-197">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-198">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-198">Example</span></span>

```c
TX_BLOCK_POOL my_pool;

UINT           status;

/* Delete entire memory block
pool. Assume that the pool has already been created with a call to
tx_block_pool_create. */
status = tx_block_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, the memory block pool is deleted.*/
```

### <a name="see-also"></a><span data-ttu-id="27adc-199">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-199">See Also</span></span>

- <span data-ttu-id="27adc-200">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="27adc-200">tx_block_allocate</span></span>
- <span data-ttu-id="27adc-201">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="27adc-201">tx_block_pool_create</span></span>
- <span data-ttu-id="27adc-202">tx_block_pool_info_get, tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-202">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="27adc-203">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-203">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-204">tx_block_pool_prioritize, tx_block_release</span><span class="sxs-lookup"><span data-stu-id="27adc-204">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_info_get"></a><span data-ttu-id="27adc-205">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-205">tx_block_pool_info_get</span></span>

<span data-ttu-id="27adc-206">Получение сведений о пуле блоков</span><span class="sxs-lookup"><span data-stu-id="27adc-206">Retrieve information about block pool</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-207">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-207">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="27adc-208">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-208">Description</span></span>

<span data-ttu-id="27adc-209">Эта служба получает сведения об указанном пуле блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-209">This service retrieves information about the specified block memory pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-210">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-210">Parameters</span></span>

- <span data-ttu-id="27adc-211">**pool_ptr** — указатель на ранее созданный пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-211">**pool_ptr**  Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="27adc-212">**name** — указатель на назначение для указателя на имя пула блоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-212">**name**  Pointer to destination for the pointer to the block pool's name.</span></span>
- <span data-ttu-id="27adc-213">**available** — указатель на назначение для количества доступных блоков в пуле блоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-213">**available** Pointer to destination for the number of available blocks in the block pool.</span></span>
- <span data-ttu-id="27adc-214">**total_blocks** — указатель на назначение для общего числа блоков в пуле блоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-214">**total_blocks**  Pointer to destination for the total number of blocks in the block pool.</span></span>
- <span data-ttu-id="27adc-215">**first_suspended** — указатель на назначение для указателя на поток, который находится первым в списке приостановки этого пула блоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-215">**first_suspended**   Pointer to destination for the pointer to the thread that is first on the suspension list of this block pool.</span></span>
- <span data-ttu-id="27adc-216">**suspended_count** — указатель на назначение для количества потоков, приостановленных в этом пуле блоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-216">**suspended_count**   Pointer to destination for the number of threads currently suspended on this block pool.</span></span>
- <span data-ttu-id="27adc-217">**next_pool** — указатель на назначение для указателя следующего созданного пула блоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-217">**next_pool** Pointer to destination for the pointer of the next created block pool.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-218">*Указание TX_NULL для любого параметра указывает, что это параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-218">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-219">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-219">Return Values</span></span>

- <span data-ttu-id="27adc-220">**TX_SUCCESS** (0x00) — успешное получение сведений о пуле блоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-220">**TX_SUCCESS** (0x00) Successful block pool information retrieve.</span></span>
- <span data-ttu-id="27adc-221">**TX_POOL_ERROR** (0x02) — недопустимый указатель на пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-221">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-222">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-222">Allowed From</span></span>

<span data-ttu-id="27adc-223">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-223">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-224">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-224">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-225">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-225">See Also</span></span>

- <span data-ttu-id="27adc-226">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="27adc-226">tx_block_allocate</span></span>
- <span data-ttu-id="27adc-227">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="27adc-227">tx_block_pool_create</span></span>
- <span data-ttu-id="27adc-228">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-228">tx_block_pool_delete</span></span>
- <span data-ttu-id="27adc-229">tx_block_pool_info_get, tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-229">tx_block_pool_info_get, tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="27adc-230">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-230">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-231">tx_block_pool_prioritize, tx_block_release</span><span class="sxs-lookup"><span data-stu-id="27adc-231">tx_block_pool_prioritize, tx_block_release</span></span>

## <a name="tx_block_pool_performance_info_get"></a><span data-ttu-id="27adc-232">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-232">tx_block_pool_performance_info_get</span></span>

<span data-ttu-id="27adc-233">Получение сведений о производительности пула блоков</span><span class="sxs-lookup"><span data-stu-id="27adc-233">Get block pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-234">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-234">Prototype</span></span>

```c
UINT tx_block_pool_performance_info_get(
    TX_BLOCK_POOL *pool_ptr,
    ULONG *allocates, 
    ULONG *releases,
    ULONG *suspensions, 
    ULONG *timeouts));
```

### <a name="description"></a><span data-ttu-id="27adc-235">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-235">Description</span></span>

<span data-ttu-id="27adc-236">Эта служба получает сведения о производительности указанного пула блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-236">This service retrieves performance information about the specified memory block pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-237">*Библиотека ThreadX и приложение должны быть построены с определенным параметром* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *, чтобы служба могла вернуть сведения о производительности.*</span><span class="sxs-lookup"><span data-stu-id="27adc-237">*The ThreadX library and application must be built with* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-238">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-238">Parameters</span></span>

- <span data-ttu-id="27adc-239">**pool_ptr** — указатель на ранее созданный пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-239">**pool_ptr**  Pointer to previously created memory block pool.</span></span>
- <span data-ttu-id="27adc-240">**allocates** — указатель на место назначения для количества запросов на выделение, выполненных в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="27adc-240">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="27adc-241">**releases** — указатель на место назначения для количества запросов на освобождение, выполненных в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="27adc-241">**releases**  Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="27adc-242">**suspensions** — указатель на место назначения для количества приостановок потоков для выделения в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="27adc-242">**suspensions**   Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="27adc-243">**timeouts** — указатель на место назначения для количества истечений времени ожидания во время приостановки для выделения в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="27adc-243">**timeouts**  Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

>[!NOTE]
> <span data-ttu-id="27adc-244">*Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-244">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-245">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-245">Return Values</span></span>

- <span data-ttu-id="27adc-246">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности пула блоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-246">**TX_SUCCESS**    (0x00)  Successful block pool performance get.</span></span>
- <span data-ttu-id="27adc-247">**TX_PTR_ERROR** (0x03) — недопустимый указатель на пул блоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-247">**TX_PTR_ERROR**  (0x03)  Invalid block pool pointer.</span></span>
- <span data-ttu-id="27adc-248">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.</span><span class="sxs-lookup"><span data-stu-id="27adc-248">**TX_FEATURE_NOT_ENABLED**    (0xFF)  The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-249">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-249">Allowed From</span></span>

<span data-ttu-id="27adc-250">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-250">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-251">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-251">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-252">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-252">See Also</span></span>

- <span data-ttu-id="27adc-253">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="27adc-253">tx_block_allocate</span></span>
- <span data-ttu-id="27adc-254">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="27adc-254">tx_block_pool_create</span></span>
- <span data-ttu-id="27adc-255">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-255">tx_block_pool_delete</span></span>
- <span data-ttu-id="27adc-256">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-256">tx_block_pool_info_get</span></span>
- <span data-ttu-id="27adc-257">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-257">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="27adc-258">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-258">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-259">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="27adc-259">tx_block_release</span></span>

## <a name="tx_block_pool_performance_system_info_get"></a><span data-ttu-id="27adc-260">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-260">tx_block_pool_performance_system_info_get</span></span>

<span data-ttu-id="27adc-261">Получение сведений о производительности системы пулов блоков</span><span class="sxs-lookup"><span data-stu-id="27adc-261">Get block pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-262">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-262">Prototype</span></span>

```c
UINT tx_block_pool_performance_system_info_get(
    ULONG *allocates,
    ULONG *releases, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="27adc-263">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-263">Description</span></span>

<span data-ttu-id="27adc-264">Эта служба получает сведения о производительности всех пулов блоков памяти в приложении.</span><span class="sxs-lookup"><span data-stu-id="27adc-264">This service retrieves performance information about all memory block pools in the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-265">*Библиотека ThreadX и приложение должны быть построены с определенным параметром* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *, чтобы служба могла вернуть сведения о производительности.*</span><span class="sxs-lookup"><span data-stu-id="27adc-265">*The ThreadX library and application must be built with* **TX_BLOCK_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-266">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-266">Parameters</span></span>

- <span data-ttu-id="27adc-267">**allocates** — указатель на место назначения для общего количества запросов на выделение, выполненных во всех пулах блоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-267">**allocates** Pointer to destination for the total number of allocate requests performed on all block pools.</span></span>
- <span data-ttu-id="27adc-268">**releases** — указатель на место назначения для общего количества запросов на освобождение, выполненных во всех пулах блоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-268">**releases**  Pointer to destination for the total number of release requests performed on all block pools.</span></span>
- <span data-ttu-id="27adc-269">**suspensions** — указатель на место назначения для общего количества приостановок потоков для выделения во всех пулах блоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-269">**suspensions**   Pointer to destination for the total number of thread allocation suspensions on all block pools.</span></span>
- <span data-ttu-id="27adc-270">**timeouts** — указатель на место назначения для общего количества истечений времени ожидания во время приостановки для выделения во всех пулах блоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-270">**timeouts**  Pointer to destination for the total number of allocate suspension timeouts on all block pools.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-271">*Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-271">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-272">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-272">Return Values</span></span>

- <span data-ttu-id="27adc-273">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности системы пулов блоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-273">**TX_SUCCESS** (0x00) Successful block pool system performance get.</span></span>
- <span data-ttu-id="27adc-274">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.</span><span class="sxs-lookup"><span data-stu-id="27adc-274">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-275">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-275">Allowed From</span></span>

<span data-ttu-id="27adc-276">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-276">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-277">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-277">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-278">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-278">See Also</span></span>

- <span data-ttu-id="27adc-279">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="27adc-279">tx_block_allocate</span></span>
- <span data-ttu-id="27adc-280">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="27adc-280">tx_block_pool_create</span></span>
- <span data-ttu-id="27adc-281">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-281">tx_block_pool_delete</span></span>
- <span data-ttu-id="27adc-282">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-282">tx_block_pool_info_get</span></span>
- <span data-ttu-id="27adc-283">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-283">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="27adc-284">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-284">tx_block_pool_prioritize</span></span>
- <span data-ttu-id="27adc-285">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="27adc-285">tx_block_release</span></span>

## <a name="tx_block_pool_prioritize"></a><span data-ttu-id="27adc-286">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-286">tx_block_pool_prioritize</span></span>

<span data-ttu-id="27adc-287">Назначение приоритетов списку приостановки пула блоков</span><span class="sxs-lookup"><span data-stu-id="27adc-287">Prioritize block pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-288">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-288">Prototype</span></span>

```c
UINT tx_block_pool_prioritize(TX_BLOCK_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-289">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-289">Description</span></span>

<span data-ttu-id="27adc-290">Эта служба размещает поток с наибольшим приоритетом, приостановленный для выделения блока памяти в этом пуле, в начало списка приостановки.</span><span class="sxs-lookup"><span data-stu-id="27adc-290">This service places the highest priority thread suspended for a block of memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="27adc-291">Все остальные потоки остаются в том же порядке FIFO, в котором они были приостановлены.</span><span class="sxs-lookup"><span data-stu-id="27adc-291">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-292">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-292">Parameters</span></span>

- <span data-ttu-id="27adc-293">**pool_ptr** — указатель на блок управления пулом блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-293">**pool_ptr** Pointer to a memory block pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-294">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-294">Return Values</span></span>

- <span data-ttu-id="27adc-295">**TX_SUCCESS** (0x00) — успешное назначение приоритетов в пуле блоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-295">**TX_SUCCESS** (0x00) Successful block pool prioritize.</span></span>
- <span data-ttu-id="27adc-296">**TX_POOL_ERROR** (0x02) — недопустимый указатель на пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-296">**TX_POOL_ERROR** (0x02) Invalid memory block pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-297">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-297">Allowed From</span></span>

<span data-ttu-id="27adc-298">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-298">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-299">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-299">Preemption Possible</span></span>

<span data-ttu-id="27adc-300">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-300">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-301">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-301">Example</span></span>
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

### <a name="see-also"></a><span data-ttu-id="27adc-302">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-302">See Also</span></span>

- <span data-ttu-id="27adc-303">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="27adc-303">tx_block_allocate</span></span>
- <span data-ttu-id="27adc-304">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="27adc-304">tx_block_pool_create</span></span>
- <span data-ttu-id="27adc-305">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-305">tx_block_pool_delete</span></span>
- <span data-ttu-id="27adc-306">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-306">tx_block_pool_info_get</span></span>
- <span data-ttu-id="27adc-307">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-307">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="27adc-308">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-308">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-309">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="27adc-309">tx_block_release</span></span>

## <a name="tx_block_release"></a><span data-ttu-id="27adc-310">tx_block_release</span><span class="sxs-lookup"><span data-stu-id="27adc-310">tx_block_release</span></span>

<span data-ttu-id="27adc-311">Освобождение блока памяти фиксированного размера</span><span class="sxs-lookup"><span data-stu-id="27adc-311">Release fixed-size block of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-312">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-312">Prototype</span></span>

```c
UINT tx_block_release(VOID *block_ptr);
``````

### <a name="description"></a><span data-ttu-id="27adc-313">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-313">Description</span></span>

<span data-ttu-id="27adc-314">Эта служба освобождает ранее выделенный блок обратно в соответствующий пул памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-314">This service releases a previously allocated block back to its associated memory pool.</span></span> <span data-ttu-id="27adc-315">Если один или несколько потоков приостановили работу в ожидании блоков памяти из этого пула, первый приостановленный поток получает этот блок памяти и возобновляет работу.</span><span class="sxs-lookup"><span data-stu-id="27adc-315">If there are one or more threads suspended waiting for memory blocks from this pool, the first thread suspended is given this memory block and resumed.</span></span>

>[!IMPORTANT]
><span data-ttu-id="27adc-316">*Приложение должно предотвратить использование области блока памяти после ее освобождения в пул.*</span><span class="sxs-lookup"><span data-stu-id="27adc-316">*The application must prevent using a memory block area after it has been released back to the pool.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-317">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-317">Parameters</span></span>

- <span data-ttu-id="27adc-318">**block_ptr** — указатель на ранее выделенный блок памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-318">**block_ptr** Pointer to the previously allocated memory block.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-319">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-319">Return Values</span></span>

- <span data-ttu-id="27adc-320">**TX_SUCCESS** (0x00) — успешное освобождение блока памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-320">**TX_SUCCESS** (0x00) Successful memory block release.</span></span>
- <span data-ttu-id="27adc-321">**TX_PTR_ERROR** (0x03) — недопустимый указатель на блок памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-321">**TX_PTR_ERROR** (0x03) Invalid pointer to memory block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-322">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-322">Allowed From</span></span>

<span data-ttu-id="27adc-323">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-323">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-324">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-324">Preemption Possible</span></span>

<span data-ttu-id="27adc-325">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-325">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-326">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-326">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-327">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-327">See Also</span></span>

- <span data-ttu-id="27adc-328">tx_block_allocate</span><span class="sxs-lookup"><span data-stu-id="27adc-328">tx_block_allocate</span></span>
- <span data-ttu-id="27adc-329">tx_block_pool_create</span><span class="sxs-lookup"><span data-stu-id="27adc-329">tx_block_pool_create</span></span>
- <span data-ttu-id="27adc-330">tx_block_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-330">tx_block_pool_delete</span></span>
- <span data-ttu-id="27adc-331">tx_block_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-331">tx_block_pool_info_get</span></span>
- <span data-ttu-id="27adc-332">tx_block_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-332">tx_block_pool_performance_info_get</span></span>
- <span data-ttu-id="27adc-333">tx_block_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-333">tx_block_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-334">tx_block_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-334">tx_block_pool_prioritize</span></span>

## <a name="tx_byte_allocate"></a><span data-ttu-id="27adc-335">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="27adc-335">tx_byte_allocate</span></span>

<span data-ttu-id="27adc-336">Выделение байтов памяти</span><span class="sxs-lookup"><span data-stu-id="27adc-336">Allocate bytes of memory</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-337">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-337">Prototype</span></span>

```c
UINT tx_byte_allocate(
    TX_BYTE_POOL *pool_ptr,
    VOID **memory_ptr, 
    ULONG memory_size,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="27adc-338">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-338">Description</span></span>

<span data-ttu-id="27adc-339">Эта служба выделяет указанное число байтов из указанного пула байтов памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-339">This service allocates the specified number of bytes from the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-340">*Важно убедиться, что код приложения не выполняет запись за пределы выделенного блока памяти. Если это случится, произойдет повреждение в смежном (обычно последующем) блоке памяти. Результаты являются непредсказуемыми и часто неустранимыми.*</span><span class="sxs-lookup"><span data-stu-id="27adc-340">*It is important to ensure application code does not write outside the allocated memory block. If this happens, corruption occurs in an adjacent (usually subsequent) memory block. The results are unpredictable and often fatal!*</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-341">*Производительность этой службы является функцией от размера блока и степени фрагментации в пуле. Таким образом, эта служба не должна использоваться во время критических по времени потоков выполнения.*</span><span class="sxs-lookup"><span data-stu-id="27adc-341">*The performance of this service is a function of the block size and the amount of fragmentation in the pool. Hence, this service should not be used during time-critical threads of execution.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-342">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-342">Parameters</span></span>

- <span data-ttu-id="27adc-343">**pool_ptr**</span><span class="sxs-lookup"><span data-stu-id="27adc-343">**pool_ptr**</span></span> <br><span data-ttu-id="27adc-344">Указатель на ранее созданный пул блоков памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-344">Pointer to a previously created memory block pool.</span></span>
- <span data-ttu-id="27adc-345">**memory_ptr**</span><span class="sxs-lookup"><span data-stu-id="27adc-345">**memory_ptr**</span></span> <br><span data-ttu-id="27adc-346">Указатель на указатель целевой памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-346">Pointer to a destination memory pointer.</span></span> <span data-ttu-id="27adc-347">При успешном выделении адрес выделенной области памяти помещается в место, куда указывает этот параметр.</span><span class="sxs-lookup"><span data-stu-id="27adc-347">On successful allocation, the address of the allocated memory area is placed where this parameter points to.</span></span>
- <span data-ttu-id="27adc-348">**memory_size**</span><span class="sxs-lookup"><span data-stu-id="27adc-348">**memory_size**</span></span> <br><span data-ttu-id="27adc-349">Запрошенное число байтов.</span><span class="sxs-lookup"><span data-stu-id="27adc-349">Number of bytes requested.</span></span>
- <span data-ttu-id="27adc-350">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="27adc-350">**wait_option**</span></span> <br><span data-ttu-id="27adc-351">Определяет, как работает служба, если объем доступной памяти недостаточен.</span><span class="sxs-lookup"><span data-stu-id="27adc-351">Defines how the service behaves if there is not enough memory available.</span></span> <span data-ttu-id="27adc-352">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="27adc-352">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="27adc-353">**TX_NO_WAIT** (0x00000000) — немедленный возврат из этой службы независимо от того, было ли выполнение успешным.</span><span class="sxs-lookup"><span data-stu-id="27adc-353">**TX_NO_WAIT** (0x00000000) - Selecting **TX_NO_WAIT** results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="27adc-354">*Это единственный допустимый параметр, если служба вызывается из инициализации.*</span><span class="sxs-lookup"><span data-stu-id="27adc-354">*This is the only valid option if the service is called from initialization.*</span></span>
  - <span data-ttu-id="27adc-355">**TX_WAIT_FOREVER** (0xFFFFFFFF) — вызывающий поток приостанавливается на неопределенное время, пока не станет доступным достаточный объем памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-355">**TX_WAIT_FOREVER** 0xFFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until enough memory is available.</span></span>
  - <span data-ttu-id="27adc-356">*значение времени ожидания* (от 0x00000001 до 0xFFFFFFFE) — задать максимальное число тактов таймера для приостановки работы при ожидании памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-356">*timeout value* (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-357">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-357">Return Values</span></span>

- <span data-ttu-id="27adc-358">**TX_SUCCESS** (0x00) — успешное выделение памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-358">**TX_SUCCESS** (0x00) Successful memory allocation.</span></span>
- <span data-ttu-id="27adc-359">**TX_DELETED** (0x01) — пул памяти был удален, пока поток был приостановлен.</span><span class="sxs-lookup"><span data-stu-id="27adc-359">**TX_DELETED** (0x01) Memory pool was deleted while thread was suspended.</span></span>
- <span data-ttu-id="27adc-360">**TX_NO_MEMORY** (0x10) — службе не удалось выделить память в течение указанного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="27adc-360">**TX_NO_MEMORY** (0x10) Service was unable to allocate the memory within the specified time to wait.</span></span>
- <span data-ttu-id="27adc-361">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="27adc-361">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="27adc-362">**TX_POOL_ERROR** (0x02) — недопустимый указатель на пул памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-362">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="27adc-363">**TX_PTR_ERROR** (0x03) — недопустимый указатель на указатель назначения.</span><span class="sxs-lookup"><span data-stu-id="27adc-363">**TX_PTR_ERROR** (0x03) Invalid pointer to destination pointer.</span></span>
- <span data-ttu-id="27adc-364">**TX_SIZE_ERROR** (0x05) — запрошенный размер равен нулю или больше размера пула.</span><span class="sxs-lookup"><span data-stu-id="27adc-364">**TX_SIZE_ERROR** (0X05) Requested size is zero or larger than the pool.</span></span>
- <span data-ttu-id="27adc-365">**TX_WAIT_ERROR** (0x04) — в вызове из непотокового запроса был указан параметр ожидания, отличный от TX_NO_WAIT.</span><span class="sxs-lookup"><span data-stu-id="27adc-365">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="27adc-366">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-366">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-367">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-367">Allowed From</span></span>

<span data-ttu-id="27adc-368">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-368">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-369">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-369">Preemption Possible</span></span>

<span data-ttu-id="27adc-370">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-370">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-371">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-371">Example</span></span>
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

### <a name="see-also"></a><span data-ttu-id="27adc-372">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-372">See Also</span></span>

- <span data-ttu-id="27adc-373">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="27adc-373">tx_byte_pool_create</span></span>
- <span data-ttu-id="27adc-374">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-374">tx_byte_pool_delete</span></span>
- <span data-ttu-id="27adc-375">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-375">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="27adc-376">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-376">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="27adc-377">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-377">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-378">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-378">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="27adc-379">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="27adc-379">tx_byte_release</span></span>

## <a name="tx_byte_pool_create"></a><span data-ttu-id="27adc-380">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="27adc-380">tx_byte_pool_create</span></span>

<span data-ttu-id="27adc-381">Создание пула байтов памяти</span><span class="sxs-lookup"><span data-stu-id="27adc-381">Create memory pool of bytes</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-382">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-382">Prototype</span></span>

```c
UINT tx_byte_pool_create(
    TX_BYTE_POOL *pool_ptr,
    CHAR *name_ptr, 
    VOID *pool_start,
    ULONG pool_size);
```

### <a name="description"></a><span data-ttu-id="27adc-383">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-383">Description</span></span>

<span data-ttu-id="27adc-384">Эта служба создает пул байтов памяти в указанной области.</span><span class="sxs-lookup"><span data-stu-id="27adc-384">This service creates a memory byte pool in the area specified.</span></span> <span data-ttu-id="27adc-385">Изначально пул состоит из одного очень большого свободного блока.</span><span class="sxs-lookup"><span data-stu-id="27adc-385">Initially the pool consists of basically one very large free block.</span></span> <span data-ttu-id="27adc-386">Однако при выделении памяти пул разбивается на более мелкие блоки.</span><span class="sxs-lookup"><span data-stu-id="27adc-386">However, the pool is broken into smaller blocks as allocations are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-387">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-387">Parameters</span></span>

- <span data-ttu-id="27adc-388">**pool_ptr** — указатель на блок управления пулом памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-388">**pool_ptr** Pointer to a memory pool control block.</span></span>
- <span data-ttu-id="27adc-389">**name_ptr** — указатель на имя пула памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-389">**name_ptr** Pointer to the name of the memory pool.</span></span>
- <span data-ttu-id="27adc-390">**pool_start** — начальный адрес пула памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-390">**pool_start** Starting address of the memory pool.</span></span> <span data-ttu-id="27adc-391">Начальный адрес должен быть выровнен по размеру типа данных ULONG.</span><span class="sxs-lookup"><span data-stu-id="27adc-391">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="27adc-392">**pool_size** — общее число байт, доступных для пула памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-392">**pool_size** Total number of bytes available for the memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-393">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-393">Return Values</span></span>

- <span data-ttu-id="27adc-394">**TX_SUCCESS** (0x00) — успешное создание пула памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-394">**TX_SUCCESS** (0x00) Successful memory pool creation.</span></span>
- <span data-ttu-id="27adc-395">**TX_POOL_ERROR** (0x02) — недопустимый указатель на пул памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-395">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span> <span data-ttu-id="27adc-396">Либо указатель имеет значение NULL, либо пул уже создан.</span><span class="sxs-lookup"><span data-stu-id="27adc-396">Either the pointer is NULL or the pool is already created.</span></span>
- <span data-ttu-id="27adc-397">**TX_PTR_ERROR** (0x03) — недопустимый начальный адрес пула.</span><span class="sxs-lookup"><span data-stu-id="27adc-397">**TX_PTR_ERROR** (0x03) Invalid starting address of the pool.</span></span>
- <span data-ttu-id="27adc-398">**TX_SIZE_ERROR** (0x05) — недопустимый размер пула.</span><span class="sxs-lookup"><span data-stu-id="27adc-398">**TX_SIZE_ERROR** (0x05) Size of pool is invalid.</span></span>
- <span data-ttu-id="27adc-399">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-399">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-400">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-400">Allowed From</span></span>

<span data-ttu-id="27adc-401">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-401">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-402">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-402">Preemption Possible</span></span>

<span data-ttu-id="27adc-403">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-403">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-404">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-404">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-405">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-405">See Also</span></span>

- <span data-ttu-id="27adc-406">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="27adc-406">tx_byte_allocate</span></span>
- <span data-ttu-id="27adc-407">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-407">tx_byte_pool_delete</span></span>
- <span data-ttu-id="27adc-408">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-408">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="27adc-409">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-409">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="27adc-410">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-410">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-411">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-411">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="27adc-412">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="27adc-412">tx_byte_release</span></span>

## <a name="tx_byte_pool_delete"></a><span data-ttu-id="27adc-413">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-413">tx_byte_pool_delete</span></span>

<span data-ttu-id="27adc-414">Удаление пула байтов памяти</span><span class="sxs-lookup"><span data-stu-id="27adc-414">Delete memory byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-415">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-415">Prototype</span></span>

```c
UINT tx_byte_pool_delete(TX_BYTE_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-416">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-416">Description</span></span>

<span data-ttu-id="27adc-417">Эта служба удаляет указанный пул байтов памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-417">This service deletes the specified memory byte pool.</span></span> <span data-ttu-id="27adc-418">Все потоки, приостановленные в ожидании памяти из этого пула, возобновляются и получают состояние возврата **TX_DELETED**.</span><span class="sxs-lookup"><span data-stu-id="27adc-418">All threads suspended waiting for memory from this pool are resumed and given a **TX_DELETED** return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-419">*За управление областью памяти, связанной с пулом, которая становится доступна после завершения этой службы,отвечает приложение. Кроме того, приложение должно предотвращать использование удаленного пула или памяти, выделенной из него ранее.*</span><span class="sxs-lookup"><span data-stu-id="27adc-419">*It is the application's responsibility to manage the memory area associated with the pool, which is available after this service completes. In addition, the application must prevent use of a deleted pool or memory previously allocated from it.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-420">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-420">Parameters</span></span>

- <span data-ttu-id="27adc-421">**pool_ptr** — указатель на ранее созданный пул памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-421">**pool_ptr** Pointer to a previously created memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-422">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-422">Return Values</span></span>

- <span data-ttu-id="27adc-423">**TX_SUCCESS** (0x00) — успешное удаление пула памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-423">**TX_SUCCESS** (0x00) Successful memory pool deletion.</span></span>
- <span data-ttu-id="27adc-424">**TX_POOL_ERROR** (0x02) — недопустимый указатель на пул памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-424">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>
- <span data-ttu-id="27adc-425">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-425">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-426">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-426">Allowed From</span></span>

<span data-ttu-id="27adc-427">Потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-427">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-428">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-428">Preemption Possible</span></span>

<span data-ttu-id="27adc-429">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-429">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-430">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-430">Example</span></span>

```c
TX_BYTE_POOL my_pool;
UINT status;
/* Delete entire memory pool. Assume that the pool has already
been created with a call to tx_byte_pool_create. */
status = tx_byte_pool_delete(&my_pool);

/* If status equals TX_SUCCESS, memory pool is deleted. */
```

### <a name="see-also"></a><span data-ttu-id="27adc-431">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-431">See Also</span></span>

- <span data-ttu-id="27adc-432">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="27adc-432">tx_byte_allocate</span></span>
- <span data-ttu-id="27adc-433">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="27adc-433">tx_byte_pool_create</span></span>
- <span data-ttu-id="27adc-434">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-434">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="27adc-435">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-435">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="27adc-436">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-436">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-437">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-437">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="27adc-438">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="27adc-438">tx_byte_release</span></span>

## <a name="tx_byte_pool_info_get"></a><span data-ttu-id="27adc-439">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-439">tx_byte_pool_info_get</span></span>

<span data-ttu-id="27adc-440">Получение сведений о пуле байтов</span><span class="sxs-lookup"><span data-stu-id="27adc-440">Retrieve information about byte pool</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-441">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-441">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="27adc-442">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-442">Description</span></span>

<span data-ttu-id="27adc-443">Эта служба получает сведения об указанном пуле байтов памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-443">This service retrieves information about the specified memory byte pool.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-444">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-444">Parameters</span></span>

- <span data-ttu-id="27adc-445">**pool_ptr** — указатель на ранее созданный пул памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-445">**pool_ptr** Pointer to previously created memory pool.</span></span>
- <span data-ttu-id="27adc-446">**name** — указатель на назначение для указателя на имя пула байтов.</span><span class="sxs-lookup"><span data-stu-id="27adc-446">**name** Pointer to destination for the pointer to the byte pool's name.</span></span>
- <span data-ttu-id="27adc-447">**available** — указатель на назначение для количества доступных байтов в пуле.</span><span class="sxs-lookup"><span data-stu-id="27adc-447">**available** Pointer to destination for the number of available bytes in the pool.</span></span>
- <span data-ttu-id="27adc-448">**fragments** — указатель на место назначения для общего числа фрагментов памяти в пуле байтов.</span><span class="sxs-lookup"><span data-stu-id="27adc-448">**fragments** Pointer to destination for the total number of memory fragments in the byte pool.</span></span>
- <span data-ttu-id="27adc-449">**first_suspended** — указатель на назначение для указателя на поток, который находится первым в списке приостановки этого пула байтов.</span><span class="sxs-lookup"><span data-stu-id="27adc-449">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this byte pool.</span></span>
- <span data-ttu-id="27adc-450">**suspended_count** — указатель на назначение для количества потоков, приостановленных в этом пуле байтов.</span><span class="sxs-lookup"><span data-stu-id="27adc-450">**suspended_count** Pointer to destination for the number of threads currently suspended on this byte pool.</span></span>
- <span data-ttu-id="27adc-451">**next_pool** — указатель на назначение для указателя следующего созданного пула байтов.</span><span class="sxs-lookup"><span data-stu-id="27adc-451">**next_pool** Pointer to destination for the pointer of the next created byte pool.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-452">*Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-452">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-453">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-453">Return Values</span></span>

- <span data-ttu-id="27adc-454">**TX_SUCCESS** (0x00) — успешное получение сведений о пуле.</span><span class="sxs-lookup"><span data-stu-id="27adc-454">**TX_SUCCESS** (0x00) Successful pool information retrieve.</span></span>
- <span data-ttu-id="27adc-455">**TX_POOL_ERROR** (0x02) — недопустимый указатель на пул памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-455">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-456">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-456">Allowed From</span></span>

<span data-ttu-id="27adc-457">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-457">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-458">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-458">Preemption Possible</span></span>

<span data-ttu-id="27adc-459">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-459">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-460">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-460">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-461">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-461">See Also</span></span>

- <span data-ttu-id="27adc-462">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="27adc-462">tx_byte_allocate</span></span>
- <span data-ttu-id="27adc-463">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="27adc-463">tx_byte_pool_create</span></span>
- <span data-ttu-id="27adc-464">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-464">tx_byte_pool_delete</span></span>
- <span data-ttu-id="27adc-465">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-465">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="27adc-466">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-466">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-467">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-467">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="27adc-468">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="27adc-468">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_info_get"></a><span data-ttu-id="27adc-469">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-469">tx_byte_pool_performance_info_get</span></span>

<span data-ttu-id="27adc-470">Получение сведений о производительности пула байтов</span><span class="sxs-lookup"><span data-stu-id="27adc-470">Get byte pool performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-471">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-471">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="27adc-472">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-472">Description</span></span>

<span data-ttu-id="27adc-473">Эта служба получает сведения о производительности указанного пула байтов памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-473">This service retrieves performance information about the specified memory byte pool.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-474">*Библиотека ThreadX и приложение должны быть построены с определенным параметром* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *, чтобы служба могла вернуть сведения о производительности.*</span><span class="sxs-lookup"><span data-stu-id="27adc-474">*The ThreadX library and application must be built with* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-475">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-475">Parameters</span></span>

- <span data-ttu-id="27adc-476">**pool_ptr** — указатель на ранее созданный пул байтов памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-476">**pool_ptr** Pointer to previously created memory byte pool.</span></span>
- <span data-ttu-id="27adc-477">**allocates** — указатель на место назначения для количества запросов на выделение, выполненных в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="27adc-477">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="27adc-478">**releases** — указатель на место назначения для количества запросов на освобождение, выполненных в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="27adc-478">**releases** Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="27adc-479">**fragments_searched** — указатель на место назначения для количества фрагментов внутренней памяти, найденных во время запросов на выделение в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="27adc-479">**fragments_searched** Pointer to destination for the number of internal memory fragments searched during allocation requests on this pool.</span></span>
- <span data-ttu-id="27adc-480">**merges** — указатель на место назначения для количества внутренних блоков памяти, объединенных во время запросов на выделение в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="27adc-480">**merges** Pointer to destination for the number of internal memory blocks merged during allocation requests on this pool.</span></span>
- <span data-ttu-id="27adc-481">**splits** — указатель на место назначения для количества разделенных блоков внутренней памяти (фрагментов), созданных во время запросов на выделение в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="27adc-481">**splits** Pointer to destination for the number of internal memory blocks split (fragments) created during allocation requests on this pool.</span></span>
- <span data-ttu-id="27adc-482">**suspensions** — указатель на место назначения для количества приостановок потоков для выделения в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="27adc-482">**suspensions** Pointer to destination for the number of thread allocation suspensions on this pool.</span></span>
- <span data-ttu-id="27adc-483">**timeouts** — указатель на место назначения для количества истечений времени ожидания во время приостановки для выделения в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="27adc-483">**timeouts** Pointer to destination for the number of allocate suspension timeouts on this pool.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-484">*Указание TX_NULL для любого параметра указывает, что это параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-484">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-485">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-485">Return Values</span></span>

- <span data-ttu-id="27adc-486">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности пула байтов.</span><span class="sxs-lookup"><span data-stu-id="27adc-486">**TX_SUCCESS** (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="27adc-487">**TX_PTR_ERROR** (0x03) — недопустимый указатель на пул байтов.</span><span class="sxs-lookup"><span data-stu-id="27adc-487">**TX_PTR_ERROR** (0x03) Invalid byte pool pointer.</span></span>
- <span data-ttu-id="27adc-488">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.</span><span class="sxs-lookup"><span data-stu-id="27adc-488">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-489">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-489">Allowed From</span></span>

<span data-ttu-id="27adc-490">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-490">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-491">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-491">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="27adc-492">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-492">See Also</span></span>

- <span data-ttu-id="27adc-493">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="27adc-493">tx_byte_allocate</span></span>
- <span data-ttu-id="27adc-494">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="27adc-494">tx_byte_pool_create</span></span>
- <span data-ttu-id="27adc-495">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-495">tx_byte_pool_delete</span></span>
- <span data-ttu-id="27adc-496">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-496">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="27adc-497">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-497">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-498">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-498">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="27adc-499">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="27adc-499">tx_byte_release</span></span>

## <a name="tx_byte_pool_performance_system_info_get"></a><span data-ttu-id="27adc-500">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-500">tx_byte_pool_performance_system_info_get</span></span>

<span data-ttu-id="27adc-501">Получение сведений о производительности системы пулов байтов</span><span class="sxs-lookup"><span data-stu-id="27adc-501">Get byte pool system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-502">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-502">Prototype</span></span>

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
### <a name="description"></a><span data-ttu-id="27adc-503">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-503">Description</span></span>

<span data-ttu-id="27adc-504">Эта служба получает сведения о производительности всех пулов байтов памяти в системе.</span><span class="sxs-lookup"><span data-stu-id="27adc-504">This service retrieves performance information about all memory byte pools in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-505">*Библиотека ThreadX и приложение должны быть построены с определенным параметром* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *, чтобы служба могла вернуть сведения о производительности.*</span><span class="sxs-lookup"><span data-stu-id="27adc-505">*The ThreadX library and application must be built with* **TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-506">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-506">Parameters</span></span>

- <span data-ttu-id="27adc-507">**allocates** — указатель на место назначения для количества запросов на выделение, выполненных в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="27adc-507">**allocates** Pointer to destination for the number of allocate requests performed on this pool.</span></span>
- <span data-ttu-id="27adc-508">**releases** — указатель на место назначения для количества запросов на освобождение, выполненных в этом пуле.</span><span class="sxs-lookup"><span data-stu-id="27adc-508">**releases** Pointer to destination for the number of release requests performed on this pool.</span></span>
- <span data-ttu-id="27adc-509">**fragments_searched** — указатель на место назначения для общего количества фрагментов внутренней памяти, найденных во время запросов на выделение во всех пулах байтов.</span><span class="sxs-lookup"><span data-stu-id="27adc-509">**fragments_searched** Pointer to destination for the total number of internal memory fragments searched during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="27adc-510">**merges** — указатель на место назначения для общего количества внутренних блоков памяти, объединенных во время запросов на выделение во всех пулах байтов.</span><span class="sxs-lookup"><span data-stu-id="27adc-510">**merges** Pointer to destination for the total number of internal memory blocks merged during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="27adc-511">**splits** — указатель на место назначения для общего количества разделенных блоков внутренней памяти (фрагментов), созданных во время запросов на выделение во всех пулах байтов.</span><span class="sxs-lookup"><span data-stu-id="27adc-511">**splits** Pointer to destination for the total number of internal memory blocks split (fragments) created during allocation requests on all byte pools.</span></span>
- <span data-ttu-id="27adc-512">**suspensions** — указатель на место назначения для общего количества приостановок потоков для выделения во всех пулах байтов.</span><span class="sxs-lookup"><span data-stu-id="27adc-512">**suspensions** Pointer to destination for the total number of thread allocation suspensions on all byte pools.</span></span>
- <span data-ttu-id="27adc-513">**timeouts** — указатель на место назначения для общего количества истечений времени ожидания во время приостановки для выделения во всех пулах байтов.</span><span class="sxs-lookup"><span data-stu-id="27adc-513">**timeouts** Pointer to destination for the total number of allocate suspension timeouts on all byte pools.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-514">*Указание TX_NULL для любого параметра указывает, что это параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-514">*Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-515">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-515">Return Values</span></span>

- <span data-ttu-id="27adc-516">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности пула байтов.</span><span class="sxs-lookup"><span data-stu-id="27adc-516">**TX_SUCCESS** (0x00) Successful byte pool performance get.</span></span>
- <span data-ttu-id="27adc-517">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.</span><span class="sxs-lookup"><span data-stu-id="27adc-517">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-518">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-518">Allowed From</span></span>

 <span data-ttu-id="27adc-519">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-519">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-520">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-520">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-521">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-521">See Also</span></span>

- <span data-ttu-id="27adc-522">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="27adc-522">tx_byte_allocate</span></span>
- <span data-ttu-id="27adc-523">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="27adc-523">tx_byte_pool_create</span></span>
- <span data-ttu-id="27adc-524">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-524">tx_byte_pool_delete</span></span>
- <span data-ttu-id="27adc-525">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-525">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="27adc-526">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-526">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="27adc-527">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-527">tx_byte_pool_prioritize</span></span>
- <span data-ttu-id="27adc-528">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="27adc-528">tx_byte_release</span></span>

## <a name="tx_byte_pool_prioritize"></a><span data-ttu-id="27adc-529">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-529">tx_byte_pool_prioritize</span></span>

<span data-ttu-id="27adc-530">Назначение приоритетов списку приостановки пула байтов</span><span class="sxs-lookup"><span data-stu-id="27adc-530">Prioritize byte pool suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-531">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-531">Prototype</span></span>

```c
UINT tx_byte_pool_prioritize(TX_BYTE_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="27adc-532">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-532">Description</span></span>

<span data-ttu-id="27adc-533">Эта служба размещает поток с наибольшим приоритетом, приостановленный для выделения памяти в этом пуле, в начало списка приостановки.</span><span class="sxs-lookup"><span data-stu-id="27adc-533">This service places the highest priority thread suspended for memory on this pool at the front of the suspension list.</span></span> <span data-ttu-id="27adc-534">Все остальные потоки остаются в том же порядке FIFO, в котором они были приостановлены.</span><span class="sxs-lookup"><span data-stu-id="27adc-534">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-535">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-535">Parameters</span></span>

- <span data-ttu-id="27adc-536">**pool_ptr** — указатель на блок управления пулом памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-536">**pool_ptr** Pointer to a memory pool control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-537">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-537">Return Values</span></span>

- <span data-ttu-id="27adc-538">**TX_SUCCESS** (0x00) — успешное назначение приоритетов в пуле памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-538">**TX_SUCCESS** (0x00) Successful memory pool prioritize.</span></span>
- <span data-ttu-id="27adc-539">**TX_POOL_ERROR** (0x02) — недопустимый указатель на пул памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-539">**TX_POOL_ERROR** (0x02) Invalid memory pool pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-540">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-540">Allowed From</span></span>

<span data-ttu-id="27adc-541">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-541">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-542">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-542">Preemption Possible</span></span>

<span data-ttu-id="27adc-543">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-543">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-544">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-544">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-545">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-545">See Also</span></span>

- <span data-ttu-id="27adc-546">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="27adc-546">tx_byte_allocate</span></span>
- <span data-ttu-id="27adc-547">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="27adc-547">tx_byte_pool_create</span></span>
- <span data-ttu-id="27adc-548">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-548">tx_byte_pool_delete</span></span>
- <span data-ttu-id="27adc-549">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-549">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="27adc-550">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-550">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="27adc-551">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-551">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-552">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="27adc-552">tx_byte_release</span></span>

## <a name="tx_byte_release"></a><span data-ttu-id="27adc-553">tx_byte_release</span><span class="sxs-lookup"><span data-stu-id="27adc-553">tx_byte_release</span></span>

<span data-ttu-id="27adc-554">Освобождение байтов обратно в пул памяти</span><span class="sxs-lookup"><span data-stu-id="27adc-554">Release bytes back to memory pool</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-555">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-555">Prototype</span></span>

```c
UINT tx_byte_release(VOID *memory_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-556">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-556">Description</span></span>

<span data-ttu-id="27adc-557">Эта служба освобождает ранее выделенную память обратно в соответствующий пул.</span><span class="sxs-lookup"><span data-stu-id="27adc-557">This service releases a previously allocated memory area back to its associated pool.</span></span> <span data-ttu-id="27adc-558">Если один или несколько потоков приостановили работу в ожидании памяти из этого пула, то каждому приостановленному потоку выделяется память и он возобновляет работу. Этот процесс продолжается, пока не исчерпается память или не кончатся все приостановленные потоки.</span><span class="sxs-lookup"><span data-stu-id="27adc-558">If there are one or more threads suspended waiting for memory from this pool, each suspended thread is given memory and resumed until the memory is exhausted or until there are no more suspended threads.</span></span> <span data-ttu-id="27adc-559">Этот процесс выделения памяти для приостановленных потоков всегда начинается с первого приостановленного потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-559">This process of allocating memory to suspended threads always begins with the first thread suspended.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-560">*Приложение должно предотвращать использование области памяти после ее освобождения.*</span><span class="sxs-lookup"><span data-stu-id="27adc-560">*The application must prevent using the memory area after it is released.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-561">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-561">Parameters</span></span>

- <span data-ttu-id="27adc-562">**memory_ptr** — указатель на ранее выделенную область памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-562">**memory_ptr** Pointer to the previously allocated memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-563">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-563">Return Values</span></span>

- <span data-ttu-id="27adc-564">**TX_SUCCESS** (0x00) — успешное освобождение памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-564">**TX_SUCCESS** (0x00) Successful memory release.</span></span>
- <span data-ttu-id="27adc-565">**TX_PTR_ERROR** (0x03) — недопустимый указатель на область памяти.</span><span class="sxs-lookup"><span data-stu-id="27adc-565">**TX_PTR_ERROR** (0x03) Invalid memory area pointer.</span></span>
- <span data-ttu-id="27adc-566">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-566">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-567">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-567">Allowed From</span></span>

<span data-ttu-id="27adc-568">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-568">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-569">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-569">Preemption Possible</span></span>

<span data-ttu-id="27adc-570">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-570">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-571">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-571">Example</span></span>

```c
unsigned char *memory_ptr;
UINT status;

/* Release a memory back to my_pool. Assume that the memory
area was previously allocated from my_pool. */
status = tx_byte_release((VOID *) memory_ptr);

/* If status equals TX_SUCCESS, the memory pointed to by
memory_ptr has been returned to the pool. */
```

### <a name="see-also"></a><span data-ttu-id="27adc-572">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-572">See Also</span></span>

- <span data-ttu-id="27adc-573">tx_byte_allocate</span><span class="sxs-lookup"><span data-stu-id="27adc-573">tx_byte_allocate</span></span>
- <span data-ttu-id="27adc-574">tx_byte_pool_create</span><span class="sxs-lookup"><span data-stu-id="27adc-574">tx_byte_pool_create</span></span>
- <span data-ttu-id="27adc-575">tx_byte_pool_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-575">tx_byte_pool_delete</span></span>
- <span data-ttu-id="27adc-576">tx_byte_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-576">tx_byte_pool_info_get</span></span>
- <span data-ttu-id="27adc-577">tx_byte_pool_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-577">tx_byte_pool_performance_info_get</span></span>
- <span data-ttu-id="27adc-578">tx_byte_pool_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-578">tx_byte_pool_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-579">tx_byte_pool_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-579">tx_byte_pool_prioritize</span></span>

## <a name="tx_event_flags_create"></a><span data-ttu-id="27adc-580">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="27adc-580">tx_event_flags_create</span></span>

<span data-ttu-id="27adc-581">Создать группу флагов событий</span><span class="sxs-lookup"><span data-stu-id="27adc-581">Create event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-582">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-582">Prototype</span></span>

```c
UINT tx_event_flags_create(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-583">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-583">Description</span></span>

<span data-ttu-id="27adc-584">Эта служба создает группу из 32 флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-584">This service creates a group of 32 event flags.</span></span> <span data-ttu-id="27adc-585">Все 32 флага событий в группе инициализируются значением 0.</span><span class="sxs-lookup"><span data-stu-id="27adc-585">All 32 event flags in the group are initialized to zero.</span></span> <span data-ttu-id="27adc-586">Каждый флаг события представлен одним битом.</span><span class="sxs-lookup"><span data-stu-id="27adc-586">Each event flag is represented by a single bit.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-587">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-587">Parameters</span></span>

- <span data-ttu-id="27adc-588">**group_ptr** — указатель на блок управления группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-588">**group_ptr** Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="27adc-589">**name_ptr** — указатель на имя группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-589">**name_ptr** Pointer to the name of the event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-590">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-590">Return Values</span></span>

- <span data-ttu-id="27adc-591">**TX_SUCCESS** (0x00) — успешное создание группы событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-591">**TX_SUCCESS** (0x00) Successful event group creation.</span></span>
- <span data-ttu-id="27adc-592">**TX_GROUP_ERROR** (0x06) — недопустимый указатель на группу событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-592">**TX_GROUP_ERROR** (0x06) Invalid event group pointer.</span></span> <span data-ttu-id="27adc-593">Либо указатель имеет значение **NULL**, либо группа событий уже создана.</span><span class="sxs-lookup"><span data-stu-id="27adc-593">Either the pointer is **NULL** or the event group is already created.</span></span>
- <span data-ttu-id="27adc-594">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-594">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-595">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-595">Allowed From</span></span>

<span data-ttu-id="27adc-596">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-596">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-597">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-597">Preemption Possible</span></span>

<span data-ttu-id="27adc-598">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-598">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-599">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-599">Example</span></span>

```c
TX_EVENT_FLAGS_GROUP my_event_group;
UINT status;

/* Create an event flags group. */
status = tx_event_flags_create(&my_event_group,
  "my_event_group_name");

/* If status equals TX_SUCCESS, my_event_group is ready
for get and set services. */
```

### <a name="see-also"></a><span data-ttu-id="27adc-600">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-600">See Also</span></span>

- <span data-ttu-id="27adc-601">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-601">tx_event_flags_delete</span></span>
- <span data-ttu-id="27adc-602">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="27adc-602">tx_event_flags_get</span></span>
- <span data-ttu-id="27adc-603">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-603">tx_event_flags_info_get</span></span>
- <span data-ttu-id="27adc-604">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-604">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="27adc-605">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-605">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-606">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="27adc-606">tx_event_flags_set</span></span>
- <span data-ttu-id="27adc-607">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-607">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_delete"></a><span data-ttu-id="27adc-608">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-608">tx_event_flags_delete</span></span>

<span data-ttu-id="27adc-609">Удалить группу флагов событий</span><span class="sxs-lookup"><span data-stu-id="27adc-609">Delete event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-610">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-610">Prototype</span></span>

```c
UINT tx_event_flags_delete(TX_EVENT_FLAGS_GROUP *group_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-611">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-611">Description</span></span>

<span data-ttu-id="27adc-612">Эта служба удаляет указанную группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-612">This service deletes the specified event flags group.</span></span> <span data-ttu-id="27adc-613">Все потоки, приостановленные в ожидании событий из этой группы, возобновляются и получают состояние возврата TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="27adc-613">All threads suspended waiting for events from this group are resumed and given a TX_DELETED return status.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="27adc-614">*Перед удалением группы флагов событий приложение должно убедиться, что обратный вызов уведомления об установке значения для этой группы флагов событий завершен (или отключен). Кроме того, приложение должно предотвращать все будущие использования удаленной группы флагов событий.*</span><span class="sxs-lookup"><span data-stu-id="27adc-614">*The application must ensure that a set notify callback for this event flags group is completed (or disabled) before deleting the event flags group. In addition, the application must prevent all future use of a deleted event flags group.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-615">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-615">Parameters</span></span>

- <span data-ttu-id="27adc-616">**group_ptr** — указатель на ранее созданную группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-616">**group_ptr** Pointer to a previously created event flags group.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-617">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-617">Return Values</span></span>

- <span data-ttu-id="27adc-618">**TX_SUCCESS** (0x00) — успешное удаление группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-618">**TX_SUCCESS** (0x00) Successful event flags group deletion.</span></span>
- <span data-ttu-id="27adc-619">**TX_GROUP_ERROR** (0x06) — недопустимый указатель на группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-619">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="27adc-620">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-620">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-621">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-621">Allowed From</span></span>

<span data-ttu-id="27adc-622">Потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-622">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-623">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-623">Preemption Possible</span></span>

<span data-ttu-id="27adc-624">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-624">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-625">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-625">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-626">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-626">See Also</span></span>

- <span data-ttu-id="27adc-627">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="27adc-627">tx_event_flags_create</span></span>
- <span data-ttu-id="27adc-628">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="27adc-628">tx_event_flags_get</span></span>
- <span data-ttu-id="27adc-629">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-629">tx_event_flags_info_get</span></span>
- <span data-ttu-id="27adc-630">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-630">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="27adc-631">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-631">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-632">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="27adc-632">tx_event_flags_set</span></span>
- <span data-ttu-id="27adc-633">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-633">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_get"></a><span data-ttu-id="27adc-634">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="27adc-634">tx_event_flags_get</span></span>

<span data-ttu-id="27adc-635">Получение флагов событий из группы флагов событий</span><span class="sxs-lookup"><span data-stu-id="27adc-635">Get event flags from event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-636">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-636">Prototype</span></span>

```c
UINT tx_event_flags_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG requested_flags, 
    UINT get_option,
    ULONG *actual_flags_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="27adc-637">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-637">Description</span></span>

<span data-ttu-id="27adc-638">Эта служба получает флаги событий из указанной группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-638">This service retrieves event flags from the specified event flags group.</span></span> <span data-ttu-id="27adc-639">Каждая группа флагов событий содержит 32 флага.</span><span class="sxs-lookup"><span data-stu-id="27adc-639">Each event flags group contains 32 event flags.</span></span> <span data-ttu-id="27adc-640">Каждый флаг представлен одним битом.</span><span class="sxs-lookup"><span data-stu-id="27adc-640">Each flag is represented by a single bit.</span></span> <span data-ttu-id="27adc-641">Эта служба может извлекать различные сочетания флагов событий, указанные входными параметрами.</span><span class="sxs-lookup"><span data-stu-id="27adc-641">This service can retrieve a variety of event flag combinations, as selected by the input parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-642">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-642">Parameters</span></span>

- <span data-ttu-id="27adc-643">**group_ptr**</span><span class="sxs-lookup"><span data-stu-id="27adc-643">**group_ptr**</span></span> <br><span data-ttu-id="27adc-644">Указатель на ранее созданную группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-644">Pointer to a previously created event flags group.</span></span>
- <span data-ttu-id="27adc-645">**requested_flags**</span><span class="sxs-lookup"><span data-stu-id="27adc-645">**requested_flags**</span></span> <br><span data-ttu-id="27adc-646">32-разрядная переменная без знака, представляющая флаги запрошенных событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-646">32-bit unsigned variable that represents the requested event flags.</span></span>
- <span data-ttu-id="27adc-647">**get_option**</span><span class="sxs-lookup"><span data-stu-id="27adc-647">**get_option**</span></span> <br><span data-ttu-id="27adc-648">Указывает, требуются ли все или некоторые из запрошенных флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-648">Specifies whether all or any of the requested event flags are required.</span></span> <span data-ttu-id="27adc-649">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="27adc-649">The following are valid selections:</span></span>

  - <span data-ttu-id="27adc-650">**TX_AND** (0x02)</span><span class="sxs-lookup"><span data-stu-id="27adc-650">**TX_AND** (0x02)</span></span>
  - <span data-ttu-id="27adc-651">**TX_AND_CLEAR** (0x03)</span><span class="sxs-lookup"><span data-stu-id="27adc-651">**TX_AND_CLEAR** (0x03)</span></span>
  - <span data-ttu-id="27adc-652">**TX_OR** (0x00)</span><span class="sxs-lookup"><span data-stu-id="27adc-652">**TX_OR** (0x00)</span></span>
  - <span data-ttu-id="27adc-653">**TX_OR_CLEAR** (0x01)</span><span class="sxs-lookup"><span data-stu-id="27adc-653">**TX_OR_CLEAR** (0x01)</span></span>

    <span data-ttu-id="27adc-654">TX_AND или TX_AND_CLEAR указывают, что все флаги событий должны присутствовать в группе.</span><span class="sxs-lookup"><span data-stu-id="27adc-654">Selecting TX_AND or TX_AND_CLEAR specifies that all event flags must be present in the group.</span></span> <span data-ttu-id="27adc-655">TX_OR или TX_OR_CLEAR указывают, что какой-либо флаг события удовлетворяет условию.</span><span class="sxs-lookup"><span data-stu-id="27adc-655">Selecting TX_OR or TX_OR_CLEAR     specifies that any event flag is satisfactory.</span></span> <span data-ttu-id="27adc-656">Если указаны TX_AND_CLEAR или TX_OR_CLEAR, то флаги событий, которые соответствуют запросу, очищаются (устанавливается значение 0).</span><span class="sxs-lookup"><span data-stu-id="27adc-656">Event flags that satisfy the request are cleared (set to zero) if TX_AND_CLEAR or TX_OR_CLEAR are specified.</span></span>

- <span data-ttu-id="27adc-657">**actual_flags_ptr**</span><span class="sxs-lookup"><span data-stu-id="27adc-657">**actual_flags_ptr**</span></span> <br><span data-ttu-id="27adc-658">Указатель на место назначения, куда помещаются извлеченные флаги событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-658">Pointer to destination of where the retrieved event flags are placed.</span></span> <span data-ttu-id="27adc-659">Обратите внимание, что фактически получаемые данные могут содержать флаги, которые не были запрошены.</span><span class="sxs-lookup"><span data-stu-id="27adc-659">Note that the actual flags obtained may contain flags that were not requested.</span></span>
- <span data-ttu-id="27adc-660">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="27adc-660">**wait_option**</span></span>  <br><span data-ttu-id="27adc-661">Определяет, как служба ведет себя, если не заданы выбранные флаги событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-661">Defines how the service behaves if the selected event flags are not set.</span></span> <span data-ttu-id="27adc-662">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="27adc-662">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="27adc-663">**TX_NO_WAIT** (0x00000000) — немедленный возврат из этой службы независимо от того, было ли выполнение успешным.</span><span class="sxs-lookup"><span data-stu-id="27adc-663">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="27adc-664">Это единственный допустимый параметр, если служба вызывается из непотока, например инициализации, таймера или ISR.</span><span class="sxs-lookup"><span data-stu-id="27adc-664">This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.</span></span>
  - <span data-ttu-id="27adc-665">**TX_WAIT_FOREVER** (значение времени ожидания 0xFFFFFFFF) — вызывающий поток приостанавливается на неопределенное время, пока флаги событий не станут доступными.</span><span class="sxs-lookup"><span data-stu-id="27adc-665">**TX_WAIT_FOREVER** timeout value  (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the event flags are available.</span></span>
  - <span data-ttu-id="27adc-666">значение времени ожидания (от 0x00000001 до 0xFFFFFFFE) — задать максимальное число тактов таймера для приостановки работы при ожидании флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-666">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the event flags.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-667">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-667">Return Values</span></span>

- <span data-ttu-id="27adc-668">**TX_SUCCESS** (0x00) — успешное получение флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-668">**TX_SUCCESS** (0x00) Successful event flags get.</span></span>
- <span data-ttu-id="27adc-669">**TX_DELETED** (0x01) — группа флагов событий была удалена, пока поток был приостановлен.</span><span class="sxs-lookup"><span data-stu-id="27adc-669">**TX_DELETED** (0x01) Event flags group was deleted while thread was suspended.</span></span>
- <span data-ttu-id="27adc-670">**TX_NO_EVENTS** (0x07) — службе не удалось получить указанные события в течение заданного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="27adc-670">**TX_NO_EVENTS** (0x07) Service was unable to get the specified events within the specified time to wait.</span></span>
- <span data-ttu-id="27adc-671">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="27adc-671">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="27adc-672">**TX_GROUP_ERROR** (0x06) — недопустимый указатель на группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-672">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="27adc-673">**TX_PTR_ERROR** (0x03) — недопустимый указатель для фактических флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-673">**TX_PTR_ERROR** (0x03) Invalid pointer for actual event flags.</span></span>
- <span data-ttu-id="27adc-674">**TX_WAIT_ERROR** (0x04) — в вызове из непотокового запроса был указан параметр ожидания, отличный от TX_NO_WAIT.</span><span class="sxs-lookup"><span data-stu-id="27adc-674">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>
- <span data-ttu-id="27adc-675">**TX_OPTION_ERROR** (0x08) — указан недопустимый параметр get_option.</span><span class="sxs-lookup"><span data-stu-id="27adc-675">**TX_OPTION_ERROR** (0x08) Invalid get-option was specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-676">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-676">Allowed From</span></span>

<span data-ttu-id="27adc-677">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-677">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-678">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-678">Preemption Possible</span></span>

<span data-ttu-id="27adc-679">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-679">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-680">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-680">Example</span></span>

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

<span data-ttu-id="27adc-681">**См. также:**</span><span class="sxs-lookup"><span data-stu-id="27adc-681">**See Also**</span></span>

- <span data-ttu-id="27adc-682">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="27adc-682">tx_event_flags_create</span></span>
- <span data-ttu-id="27adc-683">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-683">tx_event_flags_delete</span></span>
- <span data-ttu-id="27adc-684">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-684">tx_event_flags_info_get</span></span>
- <span data-ttu-id="27adc-685">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-685">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="27adc-686">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-686">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-687">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="27adc-687">tx_event_flags_set</span></span>
- <span data-ttu-id="27adc-688">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-688">tx_event_flags_set_notify</span></span>

### <a name="tx_event_flags_info_get"></a><span data-ttu-id="27adc-689">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-689">tx_event_flags_info_get</span></span>

<span data-ttu-id="27adc-690">Получение сведений о группе флагов событий</span><span class="sxs-lookup"><span data-stu-id="27adc-690">Retrieve information about event flags group</span></span>

<span data-ttu-id="27adc-691">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="27adc-691">**Prototype**</span></span>

```c
UINT tx_event_flags_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    CHAR **name, ULONG *current_flags,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_EVENT_FLAGS_GROUP **next_group);
```

<span data-ttu-id="27adc-692">**Описание**</span><span class="sxs-lookup"><span data-stu-id="27adc-692">**Description**</span></span>

<span data-ttu-id="27adc-693">Эта служба получает сведения об указанной группе флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-693">This service retrieves information about the specified event flags group.</span></span>

<span data-ttu-id="27adc-694">**Параметры**</span><span class="sxs-lookup"><span data-stu-id="27adc-694">**Parameters**</span></span>

- <span data-ttu-id="27adc-695">**group_ptr** — указатель на блок управления группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-695">**group_ptr** Pointer to an event flags group control block.</span></span>
- <span data-ttu-id="27adc-696">**name** — указатель на назначение для указателя на имя группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-696">**name** Pointer to destination for the pointer to the event flags group's name.</span></span>
- <span data-ttu-id="27adc-697">**current_flags** — указатель на назначение для текущего набора флагов в группе флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-697">**current_flags** Pointer to destination for the current set flags in the event flags group.</span></span>
- <span data-ttu-id="27adc-698">**first_suspended** — указатель на назначение для указателя на поток, который находится первым в списке приостановки этой группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-698">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this event flags group.</span></span>
- <span data-ttu-id="27adc-699">**suspended_count** — указатель на назначения для количества потоков, приостановленных в этой группе флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-699">**suspended_count** Pointer to destination for the number of threads currently suspended on this event flags group.</span></span>
- <span data-ttu-id="27adc-700">**next_group** — указатель на назначение для указателя следующей созданной группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-700">**next_group** Pointer to destination for the pointer of the next created event flags group.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-701">*Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-701">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-702">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-702">Return Values</span></span>

- <span data-ttu-id="27adc-703">**TX_SUCCESS** (0x00) — успешное получение сведений группы событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-703">**TX_SUCCESS** (0x00) Successful event group information retrieval.</span></span>
- <span data-ttu-id="27adc-704">**TX_GROUP_ERROR** (0x06) — недопустимый указатель на группу событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-704">**TX_GROUP_ERROR** (0x06) Invalid event group pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-705">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-705">Allowed From</span></span>

<span data-ttu-id="27adc-706">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-706">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-707">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-707">Preemption Possible</span></span>

<span data-ttu-id="27adc-708">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-708">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-709">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-709">Example</span></span>

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
<span data-ttu-id="27adc-710">**См. также:**</span><span class="sxs-lookup"><span data-stu-id="27adc-710">**See Also**</span></span>

- <span data-ttu-id="27adc-711">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="27adc-711">tx_event_flags_create</span></span>
- <span data-ttu-id="27adc-712">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-712">tx_event_flags_delete</span></span>
- <span data-ttu-id="27adc-713">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="27adc-713">tx_event_flags_get</span></span>
- <span data-ttu-id="27adc-714">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-714">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="27adc-715">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-715">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-716">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="27adc-716">tx_event_flags_set</span></span>
- <span data-ttu-id="27adc-717">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-717">tx_event_flags_set_notify</span></span>

### <a name="tx_event_flags_performance_info_get"></a><span data-ttu-id="27adc-718">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-718">tx_event_flags_performance_info_get</span></span>

<span data-ttu-id="27adc-719">Получение сведений о производительности группы флагов событий</span><span class="sxs-lookup"><span data-stu-id="27adc-719">Get event flags group performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-720">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-720">Prototype</span></span>

```c
UINT tx_event_flags_performance_info_get(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG *sets, ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="27adc-721">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-721">Description</span></span>

<span data-ttu-id="27adc-722">Эта служба получает сведения о производительности указанной группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-722">This service retrieves performance information about the specified event flags group.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-723">*Библиотека ThreadX и приложение должны быть построены с определенным параметром* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *, чтобы служба могла вернуть сведения о производительности.*</span><span class="sxs-lookup"><span data-stu-id="27adc-723">*ThreadX library and application must be built with* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-724">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-724">Parameters</span></span>

- <span data-ttu-id="27adc-725">**group_ptr** — указатель на ранее созданную группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-725">**group_ptr** Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="27adc-726">**sets** — указатель на место назначения для числа запросов на установку флагов событий в этой группе.</span><span class="sxs-lookup"><span data-stu-id="27adc-726">**sets** Pointer to destination for the number of event flags set requests performed on this group.</span></span>
- <span data-ttu-id="27adc-727">**gets** — указатель на место назначения для числа запросов на получение флагов событий в этой группе.</span><span class="sxs-lookup"><span data-stu-id="27adc-727">**gets** Pointer to destination for the number of event flags get requests performed on this group.</span></span>
- <span data-ttu-id="27adc-728">**suspensions** — указатель на место назначения для количества приостановок потоков для получения флагов событий в этой группе.</span><span class="sxs-lookup"><span data-stu-id="27adc-728">**suspensions** Pointer to destination for the number of thread event flags get suspensions on this group.</span></span>
- <span data-ttu-id="27adc-729">**timeouts** — указатель на место назначения для количества истечений времени ожидания во время приостановки для получения флагов событий в этой группе.</span><span class="sxs-lookup"><span data-stu-id="27adc-729">**timeouts** Pointer to destination for the number of event flags get suspension timeouts on this group.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-730">*Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-730">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-731">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-731">Return Values</span></span>

- <span data-ttu-id="27adc-732">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-732">**TX_SUCCESS** (0x00) Successful event flags group performance get.</span></span>
- <span data-ttu-id="27adc-733">**TX_PTR_ERROR** (0x03) — недопустимый указатель на группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-733">**TX_PTR_ERROR** (0x03) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="27adc-734">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.</span><span class="sxs-lookup"><span data-stu-id="27adc-734">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-735">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-735">Allowed From</span></span>

<span data-ttu-id="27adc-736">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-736">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-737">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-737">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-738">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-738">See Also</span></span>

- <span data-ttu-id="27adc-739">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="27adc-739">tx_event_flags_create</span></span>
- <span data-ttu-id="27adc-740">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-740">tx_event_flags_delete</span></span>
- <span data-ttu-id="27adc-741">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="27adc-741">tx_event_flags_get</span></span>
- <span data-ttu-id="27adc-742">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-742">tx_event_flags_info_get</span></span>
- <span data-ttu-id="27adc-743">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-743">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-744">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="27adc-744">tx_event_flags_set</span></span>
- <span data-ttu-id="27adc-745">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-745">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_performance_system_info_get"></a><span data-ttu-id="27adc-746">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-746">tx_event_flags_performance_system_info_get</span></span>

<span data-ttu-id="27adc-747">Получение сведений о производительности системы</span><span class="sxs-lookup"><span data-stu-id="27adc-747">Retrieve performance system information</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-748">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-748">Prototype</span></span>

```c
UINT tx_event_flags_performance_system_info_get(
    ULONG *sets,
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="27adc-749">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-749">Description</span></span>

<span data-ttu-id="27adc-750">Эта служба получает сведения о производительности всех групп флагов событий в системе.</span><span class="sxs-lookup"><span data-stu-id="27adc-750">This service retrieves performance information about all event flags groups in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-751">*Библиотека ThreadX и приложение должны быть построены с определенным параметром* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *, чтобы служба могла вернуть сведения о производительности.*</span><span class="sxs-lookup"><span data-stu-id="27adc-751">*ThreadX library and application must be built with* **TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-752">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-752">Parameters</span></span>

- <span data-ttu-id="27adc-753">**sets** — указатель на место назначения для общего числа запросов на установку флагов событий во всех группах.</span><span class="sxs-lookup"><span data-stu-id="27adc-753">**sets** Pointer to destination for the total number of event flags set requests performed on all groups.</span></span>
- <span data-ttu-id="27adc-754">**gets** — указатель на место назначения для общего числа запросов на получение флагов событий во всех группах.</span><span class="sxs-lookup"><span data-stu-id="27adc-754">**gets** Pointer to destination for the total number of event flags get requests performed on all groups.</span></span>
- <span data-ttu-id="27adc-755">**suspensions** — указатель на место назначения для общего количества приостановок потоков для получения флагов событий во всех группах.</span><span class="sxs-lookup"><span data-stu-id="27adc-755">**suspensions** Pointer to destination for the total number of thread event flags get suspensions on all groups.</span></span>
- <span data-ttu-id="27adc-756">**timeouts** — указатель на место назначения для общего количества истечений времени ожидания во время приостановки для получения флагов событий во всех группах.</span><span class="sxs-lookup"><span data-stu-id="27adc-756">**timeouts** Pointer to destination for the total number of event flags get suspension timeouts on all groups.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-757">*Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-757">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-758">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-758">Return Values</span></span>

- <span data-ttu-id="27adc-759">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности системы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-759">**TX_SUCCESS** (0x00) Successful event flags system performance get.</span></span>
- <span data-ttu-id="27adc-760">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.</span><span class="sxs-lookup"><span data-stu-id="27adc-760">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="example"></a><span data-ttu-id="27adc-761">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-761">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-762">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-762">See Also</span></span>

- <span data-ttu-id="27adc-763">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="27adc-763">tx_event_flags_create</span></span>
- <span data-ttu-id="27adc-764">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-764">tx_event_flags_delete</span></span>
- <span data-ttu-id="27adc-765">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="27adc-765">tx_event_flags_get</span></span>
- <span data-ttu-id="27adc-766">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-766">tx_event_flags_info_get</span></span>
- <span data-ttu-id="27adc-767">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-767">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="27adc-768">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="27adc-768">tx_event_flags_set</span></span>
- <span data-ttu-id="27adc-769">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-769">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set"></a><span data-ttu-id="27adc-770">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="27adc-770">tx_event_flags_set</span></span>

<span data-ttu-id="27adc-771">Установка флагов событий в группе флагов событий</span><span class="sxs-lookup"><span data-stu-id="27adc-771">Set event flags in an event flags group</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-772">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-772">Prototype</span></span>

```c
UINT tx_event_flags_set(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    ULONG flags_to_set,
    UINT set_option);
```

### <a name="description"></a><span data-ttu-id="27adc-773">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-773">Description</span></span>

<span data-ttu-id="27adc-774">Эта служба устанавливает или снимает флаги событий в группе флагов событий в зависимости от указанного параметра set_option.</span><span class="sxs-lookup"><span data-stu-id="27adc-774">This service sets or clears event flags in an event flags group, depending upon the specified set-option.</span></span> <span data-ttu-id="27adc-775">Все приостановленные потоки, для которых запрос флагов событий теперь удовлетворен, возобновляются.</span><span class="sxs-lookup"><span data-stu-id="27adc-775">All suspended threads whose event flags request is now satisfied are resumed.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-776">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-776">Parameters</span></span>

- <span data-ttu-id="27adc-777">**group_ptr**</span><span class="sxs-lookup"><span data-stu-id="27adc-777">**group_ptr**</span></span> <br><span data-ttu-id="27adc-778">Указатель на ранее созданный блок управления группы флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-778">Pointer to the previously created event flags group control block.</span></span>
- <span data-ttu-id="27adc-779">**flags_to_set**</span><span class="sxs-lookup"><span data-stu-id="27adc-779">**flags_to_set**</span></span> <br><span data-ttu-id="27adc-780">Указание флагов событий, которые необходимо задать или очистить в зависимости от указанного параметра set_option.</span><span class="sxs-lookup"><span data-stu-id="27adc-780">Specifies the event flags to set or clear based upon the set option selected.</span></span>
- <span data-ttu-id="27adc-781">**set_option**</span><span class="sxs-lookup"><span data-stu-id="27adc-781">**set_option**</span></span> <br><span data-ttu-id="27adc-782">Указывает, связаны ли указанные флаги событий операциями И или ИЛИ с текущими флагами событий группы.</span><span class="sxs-lookup"><span data-stu-id="27adc-782">Specifies whether the event flags specified are ANDed or ORed into the current event flags of the group.</span></span> <span data-ttu-id="27adc-783">Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="27adc-783">The following are valid selections:</span></span>
  - <span data-ttu-id="27adc-784">**TX_AND** (0x02)</span><span class="sxs-lookup"><span data-stu-id="27adc-784">**TX_AND** (0x02)</span></span>
  - <span data-ttu-id="27adc-785">**TX_OR** (0x00)</span><span class="sxs-lookup"><span data-stu-id="27adc-785">**TX_OR** (0x00)</span></span>

  <span data-ttu-id="27adc-786">Указание TX_AND указывает, что указанные флаги событий связываются операцией **И** с текущими флагами событий в группе.</span><span class="sxs-lookup"><span data-stu-id="27adc-786">Selecting TX_AND specifies that the specified event flags are **AND** ed into the current event flags in the group.</span></span> <span data-ttu-id="27adc-787">Этот параметр часто используется для очистки флагов событий в группе.</span><span class="sxs-lookup"><span data-stu-id="27adc-787">This option is often used to clear event flags in a group.</span></span> <span data-ttu-id="27adc-788">В противном случае, если указан параметр TX_OR, указанные флаги событий связываются операцией **ИЛИ** с текущими флагами событий в группе.</span><span class="sxs-lookup"><span data-stu-id="27adc-788">Otherwise, if TX_OR is specified, the specified event flags are **OR** ed with the current event in the group.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-789">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-789">Return Values</span></span>
- <span data-ttu-id="27adc-790">**TX_SUCCESS** (0x00) — успешная установка флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-790">**TX_SUCCESS** (0x00) Successful event flags set.</span></span>
- <span data-ttu-id="27adc-791">**TX_GROUP_ERROR** (0x06) — недопустимый указатель на группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-791">**TX_GROUP_ERROR** (0x06) Invalid pointer to event flags group.</span></span>
- <span data-ttu-id="27adc-792">**TX_OPTION_ERROR** (0x08) — указан недопустимый параметр set_option.</span><span class="sxs-lookup"><span data-stu-id="27adc-792">**TX_OPTION_ERROR** (0x08) Invalid set-option specified.</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-793">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-793">Preemption Possible</span></span>

<span data-ttu-id="27adc-794">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-794">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-795">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-795">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-796">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-796">See Also</span></span>

- <span data-ttu-id="27adc-797">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="27adc-797">tx_event_flags_create</span></span>
- <span data-ttu-id="27adc-798">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-798">tx_event_flags_delete</span></span>
- <span data-ttu-id="27adc-799">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="27adc-799">tx_event_flags_get</span></span>
- <span data-ttu-id="27adc-800">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-800">tx_event_flags_info_get</span></span>
- <span data-ttu-id="27adc-801">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-801">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="27adc-802">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-802">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-803">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-803">tx_event_flags_set_notify</span></span>

## <a name="tx_event_flags_set_notify"></a><span data-ttu-id="27adc-804">tx_event_flags_set_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-804">tx_event_flags_set_notify</span></span>

<span data-ttu-id="27adc-805">Уведомлять приложение, когда заданы флаги событий</span><span class="sxs-lookup"><span data-stu-id="27adc-805">Notify application when event flags are set</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-806">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-806">Prototype</span></span>

```c
UINT tx_event_flags_set_notify(
    TX_EVENT_FLAGS_GROUP *group_ptr,
    VOID (*events_set_notify)(TX_EVENT_FLAGS_GROUP *));
```

### <a name="description"></a><span data-ttu-id="27adc-807">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-807">Description</span></span>

<span data-ttu-id="27adc-808">Эта служба регистрирует функцию обратного вызова уведомлений, которая вызывается, когда один или несколько флагов событий задаются в указанной группе флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-808">This service registers a notification callback function that is called whenever one or more event flags are set in the specified event flags group.</span></span> <span data-ttu-id="27adc-809">Обработка обратного вызова уведомления определяется приложением</span><span class="sxs-lookup"><span data-stu-id="27adc-809">The processing of the notification callback is defined by the</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-810">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-810">Parameters</span></span>
- <span data-ttu-id="27adc-811">**group_ptr** — указатель на ранее созданную группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-811">**group_ptr** Pointer to previously created event flags group.</span></span>
- <span data-ttu-id="27adc-812">**events_set_notify** — указатель на функцию приложения для уведомления о задании флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-812">**events_set_notify** Pointer to application's event flags set notification function.</span></span> <span data-ttu-id="27adc-813">Если это значение равно TX_NULL, уведомление отключено.</span><span class="sxs-lookup"><span data-stu-id="27adc-813">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-814">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-814">Return Values</span></span>

- <span data-ttu-id="27adc-815">**TX_SUCCESS** (0x00) — успешная регистрация уведомлений задания флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-815">**TX_SUCCESS** (0x00) Successful registration of event flags set notification.</span></span>
- <span data-ttu-id="27adc-816">**TX_GROUP_ERROR** (0x06) — недопустимый указатель на группу флагов событий.</span><span class="sxs-lookup"><span data-stu-id="27adc-816">**TX_GROUP_ERROR** (0x06) Invalid event flags group pointer.</span></span>
- <span data-ttu-id="27adc-817">**TX_FEATURE_NOT_ENABLED** (0xFF) — система была скомпилирована с отключенными возможностями уведомлений.</span><span class="sxs-lookup"><span data-stu-id="27adc-817">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="example"></a><span data-ttu-id="27adc-818">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-818">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-819">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-819">See Also</span></span>

- <span data-ttu-id="27adc-820">tx_event_flags_create</span><span class="sxs-lookup"><span data-stu-id="27adc-820">tx_event_flags_create</span></span>
- <span data-ttu-id="27adc-821">tx_event_flags_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-821">tx_event_flags_delete</span></span>
- <span data-ttu-id="27adc-822">tx_event_flags_get</span><span class="sxs-lookup"><span data-stu-id="27adc-822">tx_event_flags_get</span></span>
- <span data-ttu-id="27adc-823">tx_event_flags_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-823">tx_event_flags_info_get</span></span>
- <span data-ttu-id="27adc-824">tx_event_flags_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-824">tx_event_flags_performance_info_get</span></span>
- <span data-ttu-id="27adc-825">tx_event_flags_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-825">tx_event_flags_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-826">tx_event_flags_set</span><span class="sxs-lookup"><span data-stu-id="27adc-826">tx_event_flags_set</span></span>

## <a name="tx_interrupt_control"></a><span data-ttu-id="27adc-827">tx_interrupt_control</span><span class="sxs-lookup"><span data-stu-id="27adc-827">tx_interrupt_control</span></span>

<span data-ttu-id="27adc-828">Включение и отключение прерываний</span><span class="sxs-lookup"><span data-stu-id="27adc-828">Enable and disable interrupts</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-829">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-829">Prototype</span></span>

```c
UINT tx_interrupt_control(UINT new_posture);
```

### <a name="description"></a><span data-ttu-id="27adc-830">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-830">Description</span></span>

<span data-ttu-id="27adc-831">Эта служба включает или отключает прерывания, как указано во входном параметре *new_posture*.</span><span class="sxs-lookup"><span data-stu-id="27adc-831">This service enables or disables interrupts as specified by the input parameter *new_posture*.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-832">*Если эта служба вызывается из потока приложения, то уровень прерывания остается частью контекста этого потока. Например, если поток вызывает эту подпрограмму для отключения прерываний, а затем приостанавливает работу, то прерывания снова отключаются.*</span><span class="sxs-lookup"><span data-stu-id="27adc-832">*If this service is called from an application thread, the interrupt posture remains part of that thread's context. For example, if the thread calls this routine to disable interrupts and then suspends, when it is resumed, interrupts are disabled again.*</span></span>

> [!WARNING]
> <span data-ttu-id="27adc-833">*Эта служба не должна использоваться для включения прерываний во время инициализации. Это может привести к непредсказуемым результатам.*</span><span class="sxs-lookup"><span data-stu-id="27adc-833">*This service should not be used to enable interrupts during initialization! Doing so could cause unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-834">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-834">Parameters</span></span>

- <span data-ttu-id="27adc-835">**new_posture** — этот параметр указывает, отключены или включены прерывания.</span><span class="sxs-lookup"><span data-stu-id="27adc-835">**new_posture** This parameter specifies whether interrupts are disabled or enabled.</span></span> <span data-ttu-id="27adc-836">Допустимые значения: **TX_INT_DISABLE** и **TX_INT_ENABLE**.</span><span class="sxs-lookup"><span data-stu-id="27adc-836">Legal values include **TX_INT_DISABLE** and **TX_INT_ENABLE**.</span></span> <span data-ttu-id="27adc-837">Фактические значения для этих параметров зависят от порта.</span><span class="sxs-lookup"><span data-stu-id="27adc-837">The actual values for these parameters are port specific.</span></span> <span data-ttu-id="27adc-838">Кроме того, некоторые архитектуры обработки могут поддерживать дополнительные варианты отключения прерываний.</span><span class="sxs-lookup"><span data-stu-id="27adc-838">In addition, some processing architectures might support additional interrupt disable postures.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-839">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-839">Return Values</span></span>
- <span data-ttu-id="27adc-840">**Предыдущее состояние** — эта служба возвращает вызывающему объекту предыдущее состояние прерываний.</span><span class="sxs-lookup"><span data-stu-id="27adc-840">**previous posture** This service returns the previous interrupt posture to the caller.</span></span> <span data-ttu-id="27adc-841">Это позволяет пользователям службы восстанавливать предыдущее состояние после отключения прерываний.</span><span class="sxs-lookup"><span data-stu-id="27adc-841">This allows users of the service to restore the previous posture after interrupts are disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-842">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-842">Allowed From</span></span>

<span data-ttu-id="27adc-843">Потоки, таймеры и ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-843">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-844">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-844">Preemption Possible</span></span>

<span data-ttu-id="27adc-845">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-845">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-846">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-846">Example</span></span>

```c
UINT my_old_posture;

/* Lockout interrupts */
my_old_posture = tx_interrupt_control(TX_INT_DISABLE);

/* Perform critical operations that need interrupts
locked-out.... */

/* Restore previous interrupt lockout posture. */
tx_interrupt_control(my_old_posture);
```

### <a name="see-also"></a><span data-ttu-id="27adc-847">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-847">See Also</span></span>

<span data-ttu-id="27adc-848">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-848">None</span></span>

## <a name="tx_mutex_create"></a><span data-ttu-id="27adc-849">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="27adc-849">tx_mutex_create</span></span>

<span data-ttu-id="27adc-850">Создание мьютекса взаимного исключения</span><span class="sxs-lookup"><span data-stu-id="27adc-850">Create mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-851">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-851">Prototype</span></span>

```c
UINT tx_mutex_create(
    TX_MUTEX *mutex_ptr,
    CHAR *name_ptr, 
    UINT priority_inherit);
```

### <a name="description"></a><span data-ttu-id="27adc-852">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-852">Description</span></span>

<span data-ttu-id="27adc-853">Эта служба создает мьютекс для взаимного исключения между потоками для защиты ресурсов.</span><span class="sxs-lookup"><span data-stu-id="27adc-853">This service creates a mutex for inter-thread mutual exclusion for resource protection.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-854">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-854">Parameters</span></span>

- <span data-ttu-id="27adc-855">**mutex_ptr** — указатель на блок управления мьютексом.</span><span class="sxs-lookup"><span data-stu-id="27adc-855">**mutex_ptr** Pointer to a mutex control block.</span></span>
- <span data-ttu-id="27adc-856">**name_ptr** — указатель на имя мьютекса.</span><span class="sxs-lookup"><span data-stu-id="27adc-856">**name_ptr** Pointer to the name of the mutex.</span></span>
- <span data-ttu-id="27adc-857">**priority_inherit** — указывает, поддерживает ли этот мьютекс наследование приоритета.</span><span class="sxs-lookup"><span data-stu-id="27adc-857">**priority_inherit** Specifies whether or not this mutex supports priority inheritance.</span></span> <span data-ttu-id="27adc-858">Если это значение равно TX_INHERIT, то наследование приоритета поддерживается.</span><span class="sxs-lookup"><span data-stu-id="27adc-858">If this value is TX_INHERIT, then priority inheritance is supported.</span></span> <span data-ttu-id="27adc-859">Если указано значение TX_NO_INHERIT, то мьютекс не поддерживает наследование приоритета.</span><span class="sxs-lookup"><span data-stu-id="27adc-859">However, if TX_NO_INHERIT is specified, priority inheritance is not supported by this mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-860">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-860">Return Values</span></span>

- <span data-ttu-id="27adc-861">**TX_SUCCESS** (0x00) — успешное создание мьютекса.</span><span class="sxs-lookup"><span data-stu-id="27adc-861">**TX_SUCCESS** (0x00) Successful mutex creation.</span></span>
- <span data-ttu-id="27adc-862">**TX_MUTEX_ERROR** (0x1C) — недопустимый указатель на мьютекс.</span><span class="sxs-lookup"><span data-stu-id="27adc-862">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span> <span data-ttu-id="27adc-863">Либо указатель имеет значение NULL, либо мьютекс уже создан.</span><span class="sxs-lookup"><span data-stu-id="27adc-863">Either the pointer is NULL or the mutex is already created.</span></span>
- <span data-ttu-id="27adc-864">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-864">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>
- <span data-ttu-id="27adc-865">**TX_INHERIT_ERROR** (0x1F) — недопустимый параметр наследования приоритета.</span><span class="sxs-lookup"><span data-stu-id="27adc-865">**TX_INHERIT_ERROR** (0x1F) Invalid priority inherit parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-866">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-866">Allowed From</span></span>

<span data-ttu-id="27adc-867">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-867">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-868">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-868">Preemption Possible</span></span>

<span data-ttu-id="27adc-869">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-869">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-870">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-870">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-871">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-871">See Also</span></span>

- <span data-ttu-id="27adc-872">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-872">tx_mutex_delete</span></span>
- <span data-ttu-id="27adc-873">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="27adc-873">tx_mutex_get</span></span>
- <span data-ttu-id="27adc-874">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-874">tx_mutex_info_get</span></span>
- <span data-ttu-id="27adc-875">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-875">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="27adc-876">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-876">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-877">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-877">tx_mutex_prioritize</span></span>
- <span data-ttu-id="27adc-878">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="27adc-878">tx_mutex_put</span></span>

## <a name="tx_mutex_delete"></a><span data-ttu-id="27adc-879">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-879">tx_mutex_delete</span></span>

<span data-ttu-id="27adc-880">Удаление мьютекса взаимного исключения</span><span class="sxs-lookup"><span data-stu-id="27adc-880">Delete mutual exclusion mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-881">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-881">Prototype</span></span>

```c
UINT tx_mutex_delete(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-882">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-882">Description</span></span>

<span data-ttu-id="27adc-883">Эта служба удаляет указанный мьютекс.</span><span class="sxs-lookup"><span data-stu-id="27adc-883">This service deletes the specified mutex.</span></span> <span data-ttu-id="27adc-884">Все потоки, приостановленные в ожидании мьютекса, возобновляются и получают состояние возврата **TX_DELETED**.</span><span class="sxs-lookup"><span data-stu-id="27adc-884">All threads suspended waiting for the mutex are resumed and given a **TX_DELETED** return status.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-885">*Ответственность за предотвращение использования удаленного мьютекса лежит на приложении.*</span><span class="sxs-lookup"><span data-stu-id="27adc-885">*It is the application's responsibility to prevent use of a deleted mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-886">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-886">Parameters</span></span>

- <span data-ttu-id="27adc-887">**mutex_ptr** — указатель на ранее созданный мьютекс.</span><span class="sxs-lookup"><span data-stu-id="27adc-887">**mutex_ptr** Pointer to a previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-888">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-888">Return Values</span></span>

- <span data-ttu-id="27adc-889">**TX_SUCCESS** (0x00) — успешное удаление мьютекса.</span><span class="sxs-lookup"><span data-stu-id="27adc-889">**TX_SUCCESS** (0x00) Successful mutex deletion.</span></span>
- <span data-ttu-id="27adc-890">**TX_MUTEX_ERROR** (0x1C) — недопустимый указатель на мьютекс.</span><span class="sxs-lookup"><span data-stu-id="27adc-890">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="27adc-891">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-891">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-892">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-892">Allowed From</span></span>

<span data-ttu-id="27adc-893">Потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-893">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-894">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-894">Preemption Possible</span></span>

<span data-ttu-id="27adc-895">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-895">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-896">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-896">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Delete a mutex. Assume that the mutex
has already been created. */
status = tx_mutex_delete(&my_mutex);

/* If status equals TX_SUCCESS, the mutex is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="27adc-897">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-897">See Also</span></span>

- <span data-ttu-id="27adc-898">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="27adc-898">tx_mutex_create</span></span>
- <span data-ttu-id="27adc-899">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="27adc-899">tx_mutex_get</span></span>
- <span data-ttu-id="27adc-900">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-900">tx_mutex_info_get</span></span>
- <span data-ttu-id="27adc-901">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-901">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="27adc-902">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-902">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-903">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-903">tx_mutex_prioritize</span></span>
- <span data-ttu-id="27adc-904">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="27adc-904">tx_mutex_put</span></span>

## <a name="tx_mutex_get"></a><span data-ttu-id="27adc-905">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="27adc-905">tx_mutex_get</span></span>

<span data-ttu-id="27adc-906">Получение владения мьютексом</span><span class="sxs-lookup"><span data-stu-id="27adc-906">Obtain ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-907">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-907">Prototype</span></span>

```c
UINT tx_mutex_get(
    TX_MUTEX *mutex_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="27adc-908">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-908">Description</span></span>

<span data-ttu-id="27adc-909">Эта служба пытается получить монопольное владение указанным мьютексом.</span><span class="sxs-lookup"><span data-stu-id="27adc-909">This service attempts to obtain exclusive ownership of the specified mutex.</span></span> <span data-ttu-id="27adc-910">Если вызывающий поток уже владеет мьютексом, то внутренний счетчик увеличивается и возвращается состояние успешного выполнения.</span><span class="sxs-lookup"><span data-stu-id="27adc-910">If the calling thread already owns the mutex, an internal counter is incremented and a successful status is returned.</span></span>

<span data-ttu-id="27adc-911">Если мьютекс принадлежит другому потоку, а текущий поток имеет более высокий приоритет и при создании мьютекса было задано наследование приоритета, приоритет потока с более низким приоритетом будет временно повышен до приоритета вызывающего потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-911">If the mutex is owned by another thread and this thread is higher priority and priority inheritance was specified at mutex create, the lower priority thread's priority will be temporarily raised to that of the calling thread.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-912">*Приоритет потока с низким приоритетом, который владеет мьютексом с наследованием приоритета, никогда не должен изменяться внешним потоком во время владения мьютексом.*</span><span class="sxs-lookup"><span data-stu-id="27adc-912">*The priority of the lower priority thread owning a mutex with priorityinheritance should never be modified by an external thread during mutex ownership.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-913">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-913">Parameters</span></span>

- <span data-ttu-id="27adc-914">**mutex_ptr**</span><span class="sxs-lookup"><span data-stu-id="27adc-914">**mutex_ptr**</span></span>   <br><span data-ttu-id="27adc-915">Указатель на ранее созданный мьютекс.</span><span class="sxs-lookup"><span data-stu-id="27adc-915">Pointer to a previously created mutex.</span></span>
- <span data-ttu-id="27adc-916">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="27adc-916">**wait_option**</span></span> <br><span data-ttu-id="27adc-917">Определяет, как работает служба, если мьютекс уже принадлежит другому потоку.</span><span class="sxs-lookup"><span data-stu-id="27adc-917">Defines how the service behaves if the mutex is already owned by another thread.</span></span> <span data-ttu-id="27adc-918">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="27adc-918">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="27adc-919">**TX_NO_WAIT** (0x00000000) — немедленный возврат из этой службы независимо от того, было ли выполнение успешным.</span><span class="sxs-lookup"><span data-stu-id="27adc-919">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="27adc-920">*Это единственный допустимый параметр, если служба вызывается из инициализации.*</span><span class="sxs-lookup"><span data-stu-id="27adc-920">*This is the only valid option if the service is called from Initialization.*</span></span>
  - <span data-ttu-id="27adc-921">**TX_WAIT_FOREVER** (значение времени ожидания 0xFFFFFFFF) — вызывающий поток приостанавливается на неопределенное время, пока мьютекс не станет доступным.</span><span class="sxs-lookup"><span data-stu-id="27adc-921">**TX_WAIT_FOREVER** timeout value (0xFFFFFFFF) - Selecting **TX_WAIT_FOREVER** causes the calling thread to suspend indefinitely until the mutex is available.</span></span>
  - <span data-ttu-id="27adc-922">значение времени ожидания (от 0x00000001 до 0xFFFFFFFE) — задать максимальное число тактов таймера для приостановки работы при ожидании мьютекса.</span><span class="sxs-lookup"><span data-stu-id="27adc-922">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-923">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-923">Return Values</span></span>

- <span data-ttu-id="27adc-924">**TX_SUCCESS** (0x00) — успешная операция получения мьютекса.</span><span class="sxs-lookup"><span data-stu-id="27adc-924">**TX_SUCCESS** (0x00) Successful mutex get operation.</span></span>
- <span data-ttu-id="27adc-925">**TX_DELETED** (0x01) — мьютекс был удален, пока поток был приостановлен.</span><span class="sxs-lookup"><span data-stu-id="27adc-925">**TX_DELETED** (0x01) Mutex was deleted while thread was suspended.</span></span>
- <span data-ttu-id="27adc-926">**TX_NOT_AVAILABLE** (0x1D) — службе не удалось получить владение мьютексом в течение указанного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="27adc-926">**TX_NOT_AVAILABLE** (0x1D) Service was unable to get ownership of the mutex within the specified time to wait.</span></span>
- <span data-ttu-id="27adc-927">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="27adc-927">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="27adc-928">**TX_MUTEX_ERROR** (0x1C) — недопустимый указатель на мьютекс.</span><span class="sxs-lookup"><span data-stu-id="27adc-928">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>
- <span data-ttu-id="27adc-929">**TX_WAIT_ERROR** (0x04) — в вызове из непотокового запроса был указан параметр ожидания, отличный от TX_NO_WAIT.</span><span class="sxs-lookup"><span data-stu-id="27adc-929">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>
- <span data-ttu-id="27adc-930">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-930">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-931">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-931">Allowed From</span></span>

<span data-ttu-id="27adc-932">Инициализация, потоки, таймеры</span><span class="sxs-lookup"><span data-stu-id="27adc-932">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-933">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-933">Preemption Possible</span></span>

<span data-ttu-id="27adc-934">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-934">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-935">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-935">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Obtain exclusive ownership of the mutex "my_mutex".
If the mutex "my_mutex" is not available, suspend until it
becomes available. */
status = tx_mutex_get(&my_mutex, TX_WAIT_FOREVER);
```

### <a name="see-also"></a><span data-ttu-id="27adc-936">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-936">See Also</span></span>

- <span data-ttu-id="27adc-937">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="27adc-937">tx_mutex_create</span></span>
- <span data-ttu-id="27adc-938">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-938">tx_mutex_delete</span></span>
- <span data-ttu-id="27adc-939">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-939">tx_mutex_info_get</span></span>
- <span data-ttu-id="27adc-940">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-940">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="27adc-941">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-941">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-942">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-942">tx_mutex_prioritize</span></span>
- <span data-ttu-id="27adc-943">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="27adc-943">tx_mutex_put</span></span>

## <a name="tx_mutex_info_get"></a><span data-ttu-id="27adc-944">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-944">tx_mutex_info_get</span></span>

<span data-ttu-id="27adc-945">Получение сведений о мьютексе</span><span class="sxs-lookup"><span data-stu-id="27adc-945">Retrieve information about mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-946">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-946">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="27adc-947">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-947">Description</span></span>

<span data-ttu-id="27adc-948">Эта служба получает сведения из указанного мьютекса.</span><span class="sxs-lookup"><span data-stu-id="27adc-948">This service retrieves information from the specified mutex.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-949">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-949">Parameters</span></span>

- <span data-ttu-id="27adc-950">**mutex_ptr** — указатель на блок управления мьютексом.</span><span class="sxs-lookup"><span data-stu-id="27adc-950">**mutex_ptr** Pointer to mutex control block.</span></span>
- <span data-ttu-id="27adc-951">**name** — указатель на назначение для указателя на имя мьютекса.</span><span class="sxs-lookup"><span data-stu-id="27adc-951">**name** Pointer to destination for the pointer to the mutex's name.</span></span>
- <span data-ttu-id="27adc-952">**count** — указатель на назначение для счетчика владения мьютексом.</span><span class="sxs-lookup"><span data-stu-id="27adc-952">**count** Pointer to destination for the ownership count of the mutex.</span></span>
- <span data-ttu-id="27adc-953">**owner** — указатель на назначение для указателя потока-владельца.</span><span class="sxs-lookup"><span data-stu-id="27adc-953">**owner** Pointer to destination for the owning thread's pointer.</span></span>
- <span data-ttu-id="27adc-954">**first_suspended** — указатель на назначение для указателя на поток, который находится первым в списке приостановки этого мьютекса.</span><span class="sxs-lookup"><span data-stu-id="27adc-954">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this mutex.</span></span>
- <span data-ttu-id="27adc-955">**suspended_count** — указатель на назначения для количества потоков, приостановленных в этом мьютексе.</span><span class="sxs-lookup"><span data-stu-id="27adc-955">**suspended_count** Pointer to destination for the number of threads currently suspended on this mutex.</span></span>
- <span data-ttu-id="27adc-956">**next_mutex** — указатель на назначение для указателя следующего созданного мьютекса.</span><span class="sxs-lookup"><span data-stu-id="27adc-956">**next_mutex** Pointer to destination for the pointer of the next created mutex.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-957">*Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-957">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-958">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-958">Return Values</span></span>

- <span data-ttu-id="27adc-959">**TX_SUCCESS** (0x00) — успешное получение сведений о мьютексе.</span><span class="sxs-lookup"><span data-stu-id="27adc-959">**TX_SUCCESS** (0x00) Successful mutex information retrieval.</span></span>
- <span data-ttu-id="27adc-960">**TX_MUTEX_ERROR** (0x1C) — недопустимый указатель на мьютекс.</span><span class="sxs-lookup"><span data-stu-id="27adc-960">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-961">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-961">Allowed From</span></span>

<span data-ttu-id="27adc-962">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-962">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-963">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-963">Preemption Possible</span></span>

<span data-ttu-id="27adc-964">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-964">No</span></span>

<span data-ttu-id="27adc-965">**Пример**</span><span class="sxs-lookup"><span data-stu-id="27adc-965">**Example**</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-966">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-966">See Also</span></span>

- <span data-ttu-id="27adc-967">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="27adc-967">tx_mutex_create</span></span>
- <span data-ttu-id="27adc-968">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-968">tx_mutex_delete</span></span>
- <span data-ttu-id="27adc-969">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="27adc-969">tx_mutex_get</span></span>
- <span data-ttu-id="27adc-970">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-970">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="27adc-971">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-971">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-972">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-972">tx_mutex_prioritize</span></span>
- <span data-ttu-id="27adc-973">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="27adc-973">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_info_get"></a><span data-ttu-id="27adc-974">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-974">tx_mutex_performance_info_get</span></span>

<span data-ttu-id="27adc-975">Получение сведений о производительности мьютекса</span><span class="sxs-lookup"><span data-stu-id="27adc-975">Get mutex performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-976">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-976">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="27adc-977">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-977">Description</span></span>

<span data-ttu-id="27adc-978">Эта служба получает сведения о производительности указанного мьютекса.</span><span class="sxs-lookup"><span data-stu-id="27adc-978">This service retrieves performance information about the specified mutex.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-979">*Библиотека ThreadX и приложение должны быть построены с определенным параметром* ***TX_MUTEX_ENABLE_PERFORMANCE_INFO** _ _, чтобы служба могла вернуть сведения о производительности*.</span><span class="sxs-lookup"><span data-stu-id="27adc-979">*The ThreadX library and application must be built with* ***TX_MUTEX_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-980">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-980">Parameters</span></span>

- <span data-ttu-id="27adc-981">**mutex_ptr** — указатель на ранее созданный мьютекс.</span><span class="sxs-lookup"><span data-stu-id="27adc-981">**mutex_ptr** Pointer to previously created mutex.</span></span>
- <span data-ttu-id="27adc-982">**puts** — указатель на место назначения для количества запросов на размещение, выполненных в этом мьютексе.</span><span class="sxs-lookup"><span data-stu-id="27adc-982">**puts** Pointer to destination for the number of put requests performed on this mutex.</span></span>
- <span data-ttu-id="27adc-983">**gets** — указатель на место назначения для количества запросов на получение, выполненных в этом мьютексе.</span><span class="sxs-lookup"><span data-stu-id="27adc-983">**gets** Pointer to destination for the number of get requests performed on this mutex.</span></span>
- <span data-ttu-id="27adc-984">**suspensions** — указатель на место назначения для количества приостановок потоков для получения мьютекса в этом мьютексе.</span><span class="sxs-lookup"><span data-stu-id="27adc-984">**suspensions** Pointer to destination for the number of thread mutex get suspensions on this mutex.</span></span>
- <span data-ttu-id="27adc-985">**timeouts** — указатель на место назначения для количества истечений времени ожидания во время приостановки для получения мьютекса в этом мьютексе.</span><span class="sxs-lookup"><span data-stu-id="27adc-985">**timeouts** Pointer to destination for the number of mutex get suspension timeouts on this mutex.</span></span>
- <span data-ttu-id="27adc-986">**inversions** — указатель на место назначения для числа инверсий приоритета потока для этого мьютекса.</span><span class="sxs-lookup"><span data-stu-id="27adc-986">**inversions** Pointer to destination for the number of thread priority inversions on this mutex.</span></span>
- <span data-ttu-id="27adc-987">**inheritances** — указатель на место назначения для числа операций наследования приоритета потоков для этого мьютекса.</span><span class="sxs-lookup"><span data-stu-id="27adc-987">**inheritances** Pointer to destination for the number of thread priority inheritance operations on this mutex.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-988">*Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-988">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-989">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-989">Return Values</span></span>

- <span data-ttu-id="27adc-990">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности мьютекса.</span><span class="sxs-lookup"><span data-stu-id="27adc-990">**TX_SUCCESS** (0x00) Successful mutex performance get.</span></span>
- <span data-ttu-id="27adc-991">**TX_PTR_ERROR** (0x03) — недопустимый указатель на мьютекс.</span><span class="sxs-lookup"><span data-stu-id="27adc-991">**TX_PTR_ERROR** (0x03) Invalid mutex pointer.</span></span>
- <span data-ttu-id="27adc-992">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.</span><span class="sxs-lookup"><span data-stu-id="27adc-992">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-993">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-993">Allowed From</span></span>

<span data-ttu-id="27adc-994">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-994">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-995">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-995">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-996">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-996">See Also</span></span>

- <span data-ttu-id="27adc-997">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="27adc-997">tx_mutex_create</span></span>
- <span data-ttu-id="27adc-998">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-998">tx_mutex_delete</span></span>
- <span data-ttu-id="27adc-999">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="27adc-999">tx_mutex_get</span></span>
- <span data-ttu-id="27adc-1000">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1000">tx_mutex_info_get</span></span>
- <span data-ttu-id="27adc-1001">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1001">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1002">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1002">tx_mutex_prioritize</span></span>
- <span data-ttu-id="27adc-1003">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1003">tx_mutex_put</span></span>

## <a name="tx_mutex_performance_system_info_get"></a><span data-ttu-id="27adc-1004">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1004">tx_mutex_performance_system_info_get</span></span>

<span data-ttu-id="27adc-1005">Получение сведений о производительности системы мьютексов</span><span class="sxs-lookup"><span data-stu-id="27adc-1005">Get mutex system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1006">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1006">Prototype</span></span>

```c
UINT tx_mutex_performance_system_info_get(
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts,
    ULONG *inversions, 
    ULONG *inheritances);
```

### <a name="description"></a><span data-ttu-id="27adc-1007">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1007">Description</span></span>

<span data-ttu-id="27adc-1008">Эта служба получает сведения о производительности всех мьютексов в системе.</span><span class="sxs-lookup"><span data-stu-id="27adc-1008">This service retrieves performance information about all the mutexes in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-1009">*Библиотека ThreadX и приложение должны быть построены с определенным параметром* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** *, чтобы служба могла вернуть сведения о производительности.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1009">*The ThreadX library and application must be built with* **TX_MUTEX_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1010">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1010">Parameters</span></span>

- <span data-ttu-id="27adc-1011">**puts** — указатель на место назначения для общего количества запросов на размещение, выполненных во всех мьютексах.</span><span class="sxs-lookup"><span data-stu-id="27adc-1011">**puts** Pointer to destination for the total number of put requests performed on all mutexes.</span></span>
- <span data-ttu-id="27adc-1012">**gets** — указатель на место назначения для общего количества запросов на получение, выполненных во всех мьютексах.</span><span class="sxs-lookup"><span data-stu-id="27adc-1012">**gets** Pointer to destination for the total number of get requests performed on all mutexes.</span></span>
- <span data-ttu-id="27adc-1013">**suspensions** — указатель на место назначения для общего количества приостановок потоков для получения мьютекса во всех мьютексах.</span><span class="sxs-lookup"><span data-stu-id="27adc-1013">**suspensions** Pointer to destination for the total number of thread mutex get suspensions on all mutexes.</span></span>
- <span data-ttu-id="27adc-1014">**timeouts** — указатель на место назначения для общего количества истечений времени ожидания во время приостановки для получения мьютекса во всех мьютексах.</span><span class="sxs-lookup"><span data-stu-id="27adc-1014">**timeouts** Pointer to destination for the total number of mutex get suspension timeouts on all mutexes.</span></span>
- <span data-ttu-id="27adc-1015">**inversions** — указатель на место назначения для общего числа инверсий приоритета потока во всех мьютексах.</span><span class="sxs-lookup"><span data-stu-id="27adc-1015">**inversions** Pointer to destination for the total number of thread priority inversions on all mutexes.</span></span>
- <span data-ttu-id="27adc-1016">**inheritances** — указатель на место назначения для общего числа операций наследования приоритета потоков во всех мьютексах.</span><span class="sxs-lookup"><span data-stu-id="27adc-1016">**inheritances** Pointer to destination for the total number of thread priority inheritance operations on all mutexes.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-1017">*Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1017">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1018">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1018">Return Values</span></span>

- <span data-ttu-id="27adc-1019">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности системы мьютексов.</span><span class="sxs-lookup"><span data-stu-id="27adc-1019">**TX_SUCCESS** (0x00) Successful mutex system performance get.</span></span>
- <span data-ttu-id="27adc-1020">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.</span><span class="sxs-lookup"><span data-stu-id="27adc-1020">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1021">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1021">Allowed From</span></span>

<span data-ttu-id="27adc-1022">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1022">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1023">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1023">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1024">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1024">See Also</span></span>

- <span data-ttu-id="27adc-1025">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1025">tx_mutex_create</span></span>
- <span data-ttu-id="27adc-1026">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1026">tx_mutex_delete</span></span>
- <span data-ttu-id="27adc-1027">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1027">tx_mutex_get</span></span>
- <span data-ttu-id="27adc-1028">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1028">tx_mutex_info_get</span></span>
- <span data-ttu-id="27adc-1029">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1029">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="27adc-1030">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1030">tx_mutex_prioritize</span></span>
- <span data-ttu-id="27adc-1031">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1031">tx_mutex_put</span></span>

## <a name="tx_mutex_prioritize"></a><span data-ttu-id="27adc-1032">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1032">tx_mutex_prioritize</span></span>

<span data-ttu-id="27adc-1033">Назначение приоритета в списке приостановки мьютекса</span><span class="sxs-lookup"><span data-stu-id="27adc-1033">Prioritize mutex suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1034">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1034">Prototype</span></span>

```c
UINT tx_mutex_prioritize(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-1035">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1035">Description</span></span>

<span data-ttu-id="27adc-1036">Эта служба размещает поток с наибольшим приоритетом, приостановленный для получения владения мьютексом, в начало списка приостановки.</span><span class="sxs-lookup"><span data-stu-id="27adc-1036">This service places the highest priority thread suspended for ownership of the mutex at the front of the suspension list.</span></span> <span data-ttu-id="27adc-1037">Все остальные потоки остаются в том же порядке FIFO, в котором они были приостановлены.</span><span class="sxs-lookup"><span data-stu-id="27adc-1037">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1038">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1038">Parameters</span></span>

- <span data-ttu-id="27adc-1039">**mutex_ptr** — указатель на ранее созданный мьютекс.</span><span class="sxs-lookup"><span data-stu-id="27adc-1039">**mutex_ptr** Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1040">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1040">Return Values</span></span>

- <span data-ttu-id="27adc-1041">**TX_SUCCESS** (0x00) — успешное назначение приоритета в мьютексе.</span><span class="sxs-lookup"><span data-stu-id="27adc-1041">**TX_SUCCESS** (0x00) Successful mutex prioritize.</span></span>
- <span data-ttu-id="27adc-1042">**TX_MUTEX_ERROR** (0x1C) — недопустимый указатель на мьютекс.</span><span class="sxs-lookup"><span data-stu-id="27adc-1042">**TX_MUTEX_ERROR** (0x1C) Invalid mutex pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1043">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1043">Allowed From</span></span>

<span data-ttu-id="27adc-1044">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1044">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1045">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1045">Preemption Possible</span></span>

<span data-ttu-id="27adc-1046">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-1046">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1047">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1047">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1048">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1048">See Also</span></span>

- <span data-ttu-id="27adc-1049">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1049">tx_mutex_create</span></span>
- <span data-ttu-id="27adc-1050">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1050">tx_mutex_delete</span></span>
- <span data-ttu-id="27adc-1051">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1051">tx_mutex_get</span></span>
- <span data-ttu-id="27adc-1052">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1052">tx_mutex_info_get</span></span>
- <span data-ttu-id="27adc-1053">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1053">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="27adc-1054">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1054">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1055">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1055">tx_mutex_put</span></span>

## <a name="tx_mutex_put"></a><span data-ttu-id="27adc-1056">tx_mutex_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1056">tx_mutex_put</span></span>

<span data-ttu-id="27adc-1057">Освобождение владения мьютексом</span><span class="sxs-lookup"><span data-stu-id="27adc-1057">Release ownership of mutex</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1058">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1058">Prototype</span></span>

```c
UINT tx_mutex_put(TX_MUTEX *mutex_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-1059">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1059">Description</span></span>

<span data-ttu-id="27adc-1060">Эта служба уменьшает счетчик владения указанного мьютекса.</span><span class="sxs-lookup"><span data-stu-id="27adc-1060">This service decrements the ownership count of the specified mutex.</span></span> <span data-ttu-id="27adc-1061">Если счетчик владения равен нулю, мьютекс становится доступным.</span><span class="sxs-lookup"><span data-stu-id="27adc-1061">If the ownership count is zero, the mutex is made available.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-1062">*Если во время создания мьютекса включено наследование приоритета, приоритет освобождающего потока будет восстановлен до приоритета, который он имел, когда изначально получил право владения мьютексом. Все другие изменения приоритета, внесенные в освобождающий поток во время владения мьютексом, могут быть отменены.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1062">*If priority inheritance was selected during mutex creation, the priority of the releasing thread will be restored to the priority it had when it originally obtained ownership of the mutex. Any other priority changes made to the releasing thread during ownership of the mutex may be undone.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1063">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1063">Parameters</span></span>
- <span data-ttu-id="27adc-1064">mutex_ptr — указатель на ранее созданный мьютекс.</span><span class="sxs-lookup"><span data-stu-id="27adc-1064">mutex_ptr Pointer to the previously created mutex.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1065">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1065">Return Values</span></span>
- <span data-ttu-id="27adc-1066">**TX_SUCCESS** (0x00) — успешное освобождение мьютекса.</span><span class="sxs-lookup"><span data-stu-id="27adc-1066">**TX_SUCCESS** (0x00) Successful mutex release.</span></span>
- <span data-ttu-id="27adc-1067">**TX_NOT_OWNED** (0x1E) — мьютекс не принадлежит вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="27adc-1067">**TX_NOT_OWNED** (0x1E) Mutex is not owned by caller.</span></span>
- <span data-ttu-id="27adc-1068">**TX_MUTEX_ERROR** (0x1C) — недопустимый указатель на мьютекс.</span><span class="sxs-lookup"><span data-stu-id="27adc-1068">**TX_MUTEX_ERROR** (0x1C) Invalid pointer to mutex.</span></span>
- <span data-ttu-id="27adc-1069">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-1069">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1070">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1070">Allowed From</span></span>

<span data-ttu-id="27adc-1071">Инициализация, потоки, таймеры</span><span class="sxs-lookup"><span data-stu-id="27adc-1071">Initialization and threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1072">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1072">Preemption Possible</span></span>

<span data-ttu-id="27adc-1073">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-1073">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1074">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1074">Example</span></span>

```c
TX_MUTEX my_mutex;
UINT status;

/* Release ownership of "my_mutex." */
status = tx_mutex_put(&my_mutex);

/* If status equals TX_SUCCESS, the mutex ownership
count has been decremented and if zero, released. */
```

### <a name="see-also"></a><span data-ttu-id="27adc-1075">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1075">See Also</span></span>

- <span data-ttu-id="27adc-1076">tx_mutex_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1076">tx_mutex_create</span></span>
- <span data-ttu-id="27adc-1077">tx_mutex_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1077">tx_mutex_delete</span></span>
- <span data-ttu-id="27adc-1078">tx_mutex_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1078">tx_mutex_get</span></span>
- <span data-ttu-id="27adc-1079">tx_mutex_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1079">tx_mutex_info_get</span></span>
- <span data-ttu-id="27adc-1080">tx_mutex_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1080">tx_mutex_performance_info_get</span></span>
- <span data-ttu-id="27adc-1081">tx_mutex_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1081">tx_mutex_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1082">tx_mutex_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1082">tx_mutex_prioritize</span></span>

## <a name="tx_queue_create"></a><span data-ttu-id="27adc-1083">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1083">tx_queue_create</span></span>

<span data-ttu-id="27adc-1084">Создание очереди сообщений</span><span class="sxs-lookup"><span data-stu-id="27adc-1084">Create message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1085">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1085">Prototype</span></span>

```c
UINT tx_queue_create(
    TX_QUEUE *queue_ptr, 
    CHAR *name_ptr,
    UINT message_size,
    VOID *queue_start, 
    ULONG queue_size);
```

### <a name="description"></a><span data-ttu-id="27adc-1086">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1086">Description</span></span>

<span data-ttu-id="27adc-1087">Эта служба создает очередь сообщений, которая обычно используется для взаимодействия между потоками.</span><span class="sxs-lookup"><span data-stu-id="27adc-1087">This service creates a message queue that is typically used for interthread communication.</span></span> <span data-ttu-id="27adc-1088">Общее количество сообщений вычисляется на основе указанного размера сообщения и общего числа байтов в очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1088">The total number of messages is calculated from the specified message size and the total number of bytes in the queue.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-1089">*Если общее число байтов, указанное в области памяти очереди, не делится на указанный размер сообщения, оставшиеся байты в области памяти не используются.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1089">*If the total number of bytes specified in the queue's memory area is not evenly divisible by the specified message size, the remaining bytes in the memory area are not used.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1090">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1090">Parameters</span></span>

- <span data-ttu-id="27adc-1091">**queue_ptr** — указатель на управляющий блок очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1091">**queue_ptr** Pointer to a message queue control block.</span></span>
- <span data-ttu-id="27adc-1092">**name_ptr** — указатель на имя пула очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1092">**name_ptr** Pointer to the name of the message queue.</span></span>
- <span data-ttu-id="27adc-1093">**message_size** — задает размер каждого сообщения в очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1093">**message_size** Specifies the size of each message in the queue.</span></span> <span data-ttu-id="27adc-1094">Размеры сообщений находятся в диапазоне от 1 до 16 32-разрядных слов.</span><span class="sxs-lookup"><span data-stu-id="27adc-1094">Message sizes range from 1 32-bit word to 16 32-bit words.</span></span> <span data-ttu-id="27adc-1095">Допустимые параметры размера сообщения — это числовые значения от 1 до 16 включительно.</span><span class="sxs-lookup"><span data-stu-id="27adc-1095">Valid message size options are numerical values from 1 through 16, inclusive.</span></span>
- <span data-ttu-id="27adc-1096">**queue_start** — начальный адрес очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1096">**queue_start** Starting address of the message queue.</span></span> <span data-ttu-id="27adc-1097">Начальный адрес должен быть выровнен по размеру типа данных ULONG.</span><span class="sxs-lookup"><span data-stu-id="27adc-1097">The starting address must be aligned to the size of the ULONG data type.</span></span>
- <span data-ttu-id="27adc-1098">**queue_size** — общее число байт, доступных для очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1098">**queue_size** Total number of bytes available for the message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1099">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1099">Return Values</span></span>

- <span data-ttu-id="27adc-1100">**TX_SUCCESS** (0x00) — успешное создание очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1100">**TX_SUCCESS** (0x00) Successful message queue creation.</span></span>
- <span data-ttu-id="27adc-1101">**TX_QUEUE_ERROR** (0x09) — недопустимый указатель на очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1101">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span> <span data-ttu-id="27adc-1102">Либо указатель имеет значение NULL, либо очередь уже создана.</span><span class="sxs-lookup"><span data-stu-id="27adc-1102">Either the pointer is NULL or the queue is already created.</span></span>
- <span data-ttu-id="27adc-1103">**TX_PTR_ERROR** (0x03) — недопустимый начальный адрес очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1103">**TX_PTR_ERROR** (0x03) Invalid starting address of the message queue.</span></span>
- <span data-ttu-id="27adc-1104">**TX_SIZE_ERROR** (0x05) — недопустимый размер очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1104">**TX_SIZE_ERROR** (0x05) Size of message queue is invalid.</span></span>
- <span data-ttu-id="27adc-1105">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-1105">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1106">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1106">Allowed From</span></span>

<span data-ttu-id="27adc-1107">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-1107">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1108">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1108">Preemption Possible</span></span>

<span data-ttu-id="27adc-1109">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-1109">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1110">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1110">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1111">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1111">See Also</span></span>

- <span data-ttu-id="27adc-1112">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1112">tx_queue_delete</span></span>
- <span data-ttu-id="27adc-1113">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27adc-1113">tx_queue_flush</span></span>
- <span data-ttu-id="27adc-1114">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1114">tx_queue_front_send</span></span>
- <span data-ttu-id="27adc-1115">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1115">tx_queue_info_get</span></span>
- <span data-ttu-id="27adc-1116">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1116">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27adc-1117">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1117">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1118">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1118">tx_queue_prioritize</span></span>
- <span data-ttu-id="27adc-1119">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27adc-1119">tx_queue_receive</span></span>
- <span data-ttu-id="27adc-1120">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1120">tx_queue_send</span></span>
- <span data-ttu-id="27adc-1121">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1121">tx_queue_send_notify</span></span>

## <a name="tx_queue_delete"></a><span data-ttu-id="27adc-1122">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1122">tx_queue_delete</span></span>

<span data-ttu-id="27adc-1123">Удаление очереди сообщений</span><span class="sxs-lookup"><span data-stu-id="27adc-1123">Delete message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1124">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1124">Prototype</span></span>

```c
UINT tx_queue_delete(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-1125">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1125">Description</span></span>

<span data-ttu-id="27adc-1126">Эта служба удаляет указанную очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1126">This service deletes the specified message queue.</span></span> <span data-ttu-id="27adc-1127">Все потоки, приостановленные в ожидании сообщения из этой очереди, возобновляются и получают состояние возврата TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="27adc-1127">All threads suspended waiting for a message from this queue are resumed and given a TX_DELETED return status.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="27adc-1128">*Перед удалением очереди приложение должно убедиться в том, что все функции обратного вызова уведомления об отправке для этой очереди завершены (или отключены). Кроме того, приложение должно предотвратить использование удаленной очереди в будущем.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1128">*The application must ensure that any send notify callback for this queue is completed (or disabled) before deleting the queue. In addition, the application must prevent any future use of a deleted queue.*</span></span> <br><br><span data-ttu-id="27adc-1129">*Кроме того, обязанность по управлению областью памяти, связанной с очередью, которая станет доступна после завершения этой службы, лежит на приложении.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1129">*It is also the application's responsibility to manage the memory area associated with the queue, which is available after this service completes.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1130">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1130">Parameters</span></span>

- <span data-ttu-id="27adc-1131">**queue_ptr** — указатель на ранее созданную очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1131">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1132">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1132">Return Values</span></span>

- <span data-ttu-id="27adc-1133">**TX_SUCCESS** (0x00) — успешное удаление очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1133">**TX_SUCCESS** (0x00) Successful message queue deletion.</span></span>
- <span data-ttu-id="27adc-1134">**TX_QUEUE_ERROR** (0x09) — недопустимый указатель на очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1134">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="27adc-1135">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-1135">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1136">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1136">Allowed From</span></span>

<span data-ttu-id="27adc-1137">Потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-1137">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1138">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1138">Preemption Possible</span></span>

<span data-ttu-id="27adc-1139">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-1139">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1140">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1140">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1141">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1141">See Also</span></span>

- <span data-ttu-id="27adc-1142">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1142">tx_queue_create</span></span>
- <span data-ttu-id="27adc-1143">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27adc-1143">tx_queue_flush</span></span>
- <span data-ttu-id="27adc-1144">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1144">tx_queue_front_send</span></span>
- <span data-ttu-id="27adc-1145">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1145">tx_queue_info_get</span></span>
- <span data-ttu-id="27adc-1146">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1146">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27adc-1147">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1147">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1148">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1148">tx_queue_prioritize</span></span>
- <span data-ttu-id="27adc-1149">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27adc-1149">tx_queue_receive</span></span>
- <span data-ttu-id="27adc-1150">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1150">tx_queue_send</span></span>
- <span data-ttu-id="27adc-1151">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1151">tx_queue_send_notify</span></span>

## <a name="tx_queue_flush"></a><span data-ttu-id="27adc-1152">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27adc-1152">tx_queue_flush</span></span>

<span data-ttu-id="27adc-1153">Очистка очереди сообщений</span><span class="sxs-lookup"><span data-stu-id="27adc-1153">Empty messages in message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1154">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1154">Prototype</span></span>

```c
UINT tx_queue_flush(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-1155">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1155">Description</span></span>

<span data-ttu-id="27adc-1156">Эта служба удаляет все сообщения, хранящиеся в указанной очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1156">This service deletes all messages stored in the specified message queue.</span></span>

<span data-ttu-id="27adc-1157">Если очередь заполнена, сообщения всех приостановленных потоков будут удалены.</span><span class="sxs-lookup"><span data-stu-id="27adc-1157">If the queue is full, messages of all suspended threads are discarded.</span></span> <span data-ttu-id="27adc-1158">После этого каждый приостановленный поток возобновляет работу с состоянием возврата, указывающим, что сообщение успешно отправлено.</span><span class="sxs-lookup"><span data-stu-id="27adc-1158">Each suspended thread is then resumed with a return status that indicates the message send was successful.</span></span> <span data-ttu-id="27adc-1159">Если очередь пуста, эта служба не выполняет никаких действий.</span><span class="sxs-lookup"><span data-stu-id="27adc-1159">If the queue is empty, this service does nothing.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1160">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1160">Parameters</span></span>

- <span data-ttu-id="27adc-1161">**queue_ptr** — указатель на ранее созданную очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1161">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1162">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1162">Return Values</span></span>

- <span data-ttu-id="27adc-1163">**TX_SUCCESS** (0x00) — успешная очистка очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1163">**TX_SUCCESS** (0x00) Successful message queue flush.</span></span>
- <span data-ttu-id="27adc-1164">**TX_QUEUE_ERROR** (0x09) — недопустимый указатель на очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1164">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1165">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1165">Allowed From</span></span>

<span data-ttu-id="27adc-1166">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1166">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1167">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1167">Preemption Possible</span></span>

<span data-ttu-id="27adc-1168">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-1168">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1169">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1169">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1170">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1170">See Also</span></span>

- <span data-ttu-id="27adc-1171">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1171">tx_queue_create</span></span>
- <span data-ttu-id="27adc-1172">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1172">tx_queue_delete</span></span>
- <span data-ttu-id="27adc-1173">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1173">tx_queue_front_send</span></span>
- <span data-ttu-id="27adc-1174">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1174">tx_queue_info_get</span></span>
- <span data-ttu-id="27adc-1175">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1175">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27adc-1176">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1176">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1177">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1177">tx_queue_prioritize</span></span>
- <span data-ttu-id="27adc-1178">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27adc-1178">tx_queue_receive</span></span>
- <span data-ttu-id="27adc-1179">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1179">tx_queue_send</span></span>
- <span data-ttu-id="27adc-1180">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1180">tx_queue_send_notify</span></span>

## <a name="tx_queue_front_send"></a><span data-ttu-id="27adc-1181">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1181">tx_queue_front_send</span></span>

<span data-ttu-id="27adc-1182">Отправка сообщения в начало очереди</span><span class="sxs-lookup"><span data-stu-id="27adc-1182">Send message to the front of queue</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1183">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1183">Prototype</span></span>

```c
UINT tx_queue_front_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="27adc-1184">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1184">Description</span></span>

<span data-ttu-id="27adc-1185">Эта служба отправляет сообщение в начало указанной очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1185">This service sends a message to the front location of the specified message queue.</span></span> <span data-ttu-id="27adc-1186">Сообщение **копируется** в начало очереди из области памяти, заданной указателем источника.</span><span class="sxs-lookup"><span data-stu-id="27adc-1186">The message is **copied** to the front of the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1187">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1187">Parameters</span></span>

- <span data-ttu-id="27adc-1188">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="27adc-1188">**queue_ptr**</span></span> <br><span data-ttu-id="27adc-1189">Указатель на управляющий блок очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1189">Pointer to a message queue control block.</span></span>
- <span data-ttu-id="27adc-1190">**source_ptr**</span><span class="sxs-lookup"><span data-stu-id="27adc-1190">**source_ptr**</span></span> <br><span data-ttu-id="27adc-1191">Указатель на сообщение.</span><span class="sxs-lookup"><span data-stu-id="27adc-1191">Pointer to the message.</span></span>
- <span data-ttu-id="27adc-1192">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="27adc-1192">**wait_option**</span></span>  <br><span data-ttu-id="27adc-1193">Определяет, как работает служба, если очередь сообщений заполнена.</span><span class="sxs-lookup"><span data-stu-id="27adc-1193">Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="27adc-1194">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="27adc-1194">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="27adc-1195">**TX_NO_WAIT** (0x00000000) — немедленный возврат из этой службы независимо от того, было ли выполнение успешным.</span><span class="sxs-lookup"><span data-stu-id="27adc-1195">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="27adc-1196">*Это единственный допустимый параметр, если служба вызывается из непотока, например инициализации, таймера или ISR.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1196">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR.*</span></span>
  - <span data-ttu-id="27adc-1197">**TX_WAIT_FOREVER** (0xFFFFFFFF) — вызывающий поток приостанавливается на неопределенное время, пока в очереди не освободится место.</span><span class="sxs-lookup"><span data-stu-id="27adc-1197">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>
  - <span data-ttu-id="27adc-1198">значение времени ожидания (от 0x00000001 до 0xFFFFFFFE) — задать максимальное число тактов таймера для приостановки работы при ожидании свободного места в очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1198">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1199">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1199">Return Values</span></span>

- <span data-ttu-id="27adc-1200">**TX_SUCCESS** (0x00) — успешная отправка сообщения.</span><span class="sxs-lookup"><span data-stu-id="27adc-1200">**TX_SUCCESS** (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="27adc-1201">**TX_DELETED** (0x01) — очередь сообщений была удалена, пока поток был приостановлен.</span><span class="sxs-lookup"><span data-stu-id="27adc-1201">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="27adc-1202">**TX_QUEUE_FULL** (0x0B) — службе не удалось отправить сообщение, так как очередь была заполнена в течение всего указанного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="27adc-1202">**TX_QUEUE_FULL** (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="27adc-1203">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="27adc-1203">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="27adc-1204">**TX_QUEUE_ERROR** (0x09) — недопустимый указатель на очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1204">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="27adc-1205">**TX_PTR_ERROR** (0x03) — недопустимый указатель источника для сообщения.</span><span class="sxs-lookup"><span data-stu-id="27adc-1205">**TX_PTR_ERROR** (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="27adc-1206">**TX_WAIT_ERROR** (0x04) — в вызове из непотокового запроса был указан параметр ожидания, отличный от TX_NO_WAIT.</span><span class="sxs-lookup"><span data-stu-id="27adc-1206">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1207">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1207">Allowed From</span></span>

<span data-ttu-id="27adc-1208">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1208">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1209">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1209">Preemption Possible</span></span>

<span data-ttu-id="27adc-1210">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-1210">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1211">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1211">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1212">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1212">See Also</span></span>

- <span data-ttu-id="27adc-1213">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1213">tx_queue_create</span></span>
- <span data-ttu-id="27adc-1214">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1214">tx_queue_delete</span></span>
- <span data-ttu-id="27adc-1215">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27adc-1215">tx_queue_flush</span></span>
- <span data-ttu-id="27adc-1216">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1216">tx_queue_info_get</span></span>
- <span data-ttu-id="27adc-1217">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1217">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27adc-1218">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1218">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1219">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1219">tx_queue_prioritize</span></span>
- <span data-ttu-id="27adc-1220">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27adc-1220">tx_queue_receive</span></span>
- <span data-ttu-id="27adc-1221">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1221">tx_queue_send</span></span>
- <span data-ttu-id="27adc-1222">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1222">tx_queue_send_notify</span></span>

## <a name="tx_queue_info_get"></a><span data-ttu-id="27adc-1223">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1223">tx_queue_info_get</span></span>

<span data-ttu-id="27adc-1224">Получение сведений об очереди</span><span class="sxs-lookup"><span data-stu-id="27adc-1224">Retrieve information about queue</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1225">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1225">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="27adc-1226">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1226">Description</span></span>

<span data-ttu-id="27adc-1227">Эта служба получает сведения об указанной очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1227">This service retrieves information about the specified message queue.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1228">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1228">Parameters</span></span>

- <span data-ttu-id="27adc-1229">**queue_ptr** — указатель на ранее созданную очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1229">**queue_ptr** Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="27adc-1230">**name** — указатель на назначение для указателя на имя очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1230">**name** Pointer to destination for the pointer to the queue's name.</span></span>
- <span data-ttu-id="27adc-1231">**enqueued** — указатель на место назначения для количества сообщений, находящихся в очереди в данный момент.</span><span class="sxs-lookup"><span data-stu-id="27adc-1231">**enqueued** Pointer to destination for the number of messages currently in the queue.</span></span>
- <span data-ttu-id="27adc-1232">**available_storage** — указатель на место назначения для количества сообщений в очереди, для которых в настоящий момент имеется место.</span><span class="sxs-lookup"><span data-stu-id="27adc-1232">**available_storage** Pointer to destination for the number of messages the queue currently has space for.</span></span>
- <span data-ttu-id="27adc-1233">**first_suspended** — указатель на назначение для указателя на поток, который находится первым в списке приостановки этой очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1233">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this queue.</span></span>
- <span data-ttu-id="27adc-1234">**suspended_count** — указатель на назначения для количества потоков, приостановленных в этой очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1234">**suspended_count** Pointer to destination for the number of threads currently suspended on this queue.</span></span>
- <span data-ttu-id="27adc-1235">**next_queue** — указатель на назначение для указателя следующей созданной очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1235">**next_queue** Pointer to destination for the pointer of the next created queue.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-1236">*Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1236">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1237">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1237">Return Values</span></span>

- <span data-ttu-id="27adc-1238">**TX_SUCCESS** (0x00) — успешное получение сведений об очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1238">**TX_SUCCESS** (0x00) Successful queue information get.</span></span>
- <span data-ttu-id="27adc-1239">**TX_QUEUE_ERROR** (0x09) — недопустимый указатель на очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1239">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1240">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1240">Allowed From</span></span>

<span data-ttu-id="27adc-1241">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1241">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1242">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1242">Preemption Possible</span></span>

<span data-ttu-id="27adc-1243">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-1243">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1244">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1244">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1245">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1245">See Also</span></span>

- <span data-ttu-id="27adc-1246">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1246">tx_queue_create</span></span>
- <span data-ttu-id="27adc-1247">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1247">tx_queue_delete</span></span>
- <span data-ttu-id="27adc-1248">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27adc-1248">tx_queue_flush</span></span>
- <span data-ttu-id="27adc-1249">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1249">tx_queue_front_send</span></span>
- <span data-ttu-id="27adc-1250">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1250">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27adc-1251">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1251">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1252">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1252">tx_queue_prioritize</span></span>
- <span data-ttu-id="27adc-1253">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27adc-1253">tx_queue_receive</span></span>
- <span data-ttu-id="27adc-1254">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1254">tx_queue_send</span></span>
- <span data-ttu-id="27adc-1255">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1255">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_info_get"></a><span data-ttu-id="27adc-1256">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1256">tx_queue_performance_info_get</span></span>

<span data-ttu-id="27adc-1257">Получение сведений о производительности очереди</span><span class="sxs-lookup"><span data-stu-id="27adc-1257">Get queue performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1258">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1258">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="27adc-1259">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1259">Description</span></span>

<span data-ttu-id="27adc-1260">Эта служба получает сведения о производительности указанной очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1260">This service retrieves performance information about the specified queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-1261">*Библиотека ThreadX и приложение должны быть построены с определенным параметром* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _, чтобы служба могла вернуть сведения о производительности*.</span><span class="sxs-lookup"><span data-stu-id="27adc-1261">*The ThreadX library and application must be built with* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1262">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1262">Parameters</span></span>

- <span data-ttu-id="27adc-1263">**queue_ptr** — указатель на ранее созданную очередь.</span><span class="sxs-lookup"><span data-stu-id="27adc-1263">**queue_ptr** Pointer to previously created queue.</span></span>
- <span data-ttu-id="27adc-1264">**messages_sent** — указатель на место назначения для количества запросов на отправку, выполненных в этой очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1264">**messages_sent** Pointer to destination for the number of send requests performed on this queue.</span></span>
- <span data-ttu-id="27adc-1265">**messages_received** — указатель на место назначения для количества запросов на получение, выполненных в этой очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1265">**messages_received** Pointer to destination for the number of receive requests performed on this queue.</span></span>
- <span data-ttu-id="27adc-1266">**empty_suspensions** — указатель на место назначения для количества приостановок при пустой очереди в этой очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1266">**empty_suspensions** Pointer to destination for the number of queue empty suspensions on this queue.</span></span>
- <span data-ttu-id="27adc-1267">**full_suspensions** — указатель на место назначения для количества приостановок при заполненной очереди в этой очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1267">**full_suspensions** Pointer to destination for the number of queue full suspensions on this queue.</span></span>
- <span data-ttu-id="27adc-1268">**full_errors** — указатель на место назначения для количества ошибок при заполненной очереди в этой очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1268">**full_errors** Pointer to destination for the number of queue full errors on this queue.</span></span>
- <span data-ttu-id="27adc-1269">**timeouts** — указатель на место назначения для количества истечений времени ожидания во время приостановки потока в этой очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1269">**timeouts** Pointer to destination for the number of thread suspension timeouts on this queue.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-1270">*Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1270">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1271">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1271">Return Values</span></span>

- <span data-ttu-id="27adc-1272">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1272">**TX_SUCCESS** (0x00) Successful queue performance get.</span></span>
- <span data-ttu-id="27adc-1273">**TX_PTR_ERROR** (0x03) — недопустимый указатель на очередь.</span><span class="sxs-lookup"><span data-stu-id="27adc-1273">**TX_PTR_ERROR** (0x03) Invalid queue pointer.</span></span>
- <span data-ttu-id="27adc-1274">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.</span><span class="sxs-lookup"><span data-stu-id="27adc-1274">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1275">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1275">Allowed From</span></span>

<span data-ttu-id="27adc-1276">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1276">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1277">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1277">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1278">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1278">See Also</span></span>

- <span data-ttu-id="27adc-1279">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1279">tx_queue_create</span></span>
- <span data-ttu-id="27adc-1280">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1280">tx_queue_delete</span></span>
- <span data-ttu-id="27adc-1281">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27adc-1281">tx_queue_flush</span></span>
- <span data-ttu-id="27adc-1282">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1282">tx_queue_front_send</span></span>
- <span data-ttu-id="27adc-1283">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1283">tx_queue_info_get</span></span>
- <span data-ttu-id="27adc-1284">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1284">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1285">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1285">tx_queue_prioritize</span></span>
- <span data-ttu-id="27adc-1286">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27adc-1286">tx_queue_receive</span></span>
- <span data-ttu-id="27adc-1287">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1287">tx_queue_send</span></span>
- <span data-ttu-id="27adc-1288">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1288">tx_queue_send_notify</span></span>

## <a name="tx_queue_performance_system_info_get"></a><span data-ttu-id="27adc-1289">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1289">tx_queue_performance_system_info_get</span></span>

<span data-ttu-id="27adc-1290">Получение сведений о производительности системы очередей</span><span class="sxs-lookup"><span data-stu-id="27adc-1290">Get queue system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1291">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1291">Prototype</span></span>

```c
UINT tx_queue_performance_system_info_get(
    ULONG *messages_sent,
    ULONG *messages_received, 
    ULONG *empty_suspensions,
    ULONG *full_suspensions, 
    ULONG *full_errors,
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="27adc-1292">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1292">Description</span></span>

<span data-ttu-id="27adc-1293">Эта служба получает сведения о производительности всех очередей в системе.</span><span class="sxs-lookup"><span data-stu-id="27adc-1293">This service retrieves performance information about all the queues in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-1294">*Библиотека ThreadX и приложение должны быть построены с определенным параметром* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _, чтобы служба могла вернуть сведения о производительности*.</span><span class="sxs-lookup"><span data-stu-id="27adc-1294">*The ThreadX library and application must be built with* ***TX_QUEUE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1295">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1295">Parameters</span></span>

- <span data-ttu-id="27adc-1296">**messages_sent** — указатель на место назначения для общего количества запросов на отправку, выполненных во всех очередях.</span><span class="sxs-lookup"><span data-stu-id="27adc-1296">**messages_sent** Pointer to destination for the total number of send requests performed on all queues.</span></span>
- <span data-ttu-id="27adc-1297">**messages_received** — указатель на место назначения для общего количества запросов на получение, выполненных во всех очередях.</span><span class="sxs-lookup"><span data-stu-id="27adc-1297">**messages_received** Pointer to destination for the total number of receive requests performed on all queues.</span></span>
- <span data-ttu-id="27adc-1298">**empty_suspensions** — указатель на место назначения для общего количества приостановок при пустой очереди во всех очередях.</span><span class="sxs-lookup"><span data-stu-id="27adc-1298">**empty_suspensions** Pointer to destination for the total number of queue empty suspensions on all queues.</span></span>
- <span data-ttu-id="27adc-1299">**full_suspensions** — указатель на место назначения для общего количества приостановок при заполненной очереди во всех очередях.</span><span class="sxs-lookup"><span data-stu-id="27adc-1299">**full_suspensions** Pointer to destination for the total number of queue full suspensions on all queues.</span></span>
- <span data-ttu-id="27adc-1300">**full_errors** — указатель на место назначения для общего количества ошибок при заполненной очереди во всех очередях.</span><span class="sxs-lookup"><span data-stu-id="27adc-1300">**full_errors** Pointer to destination for the total number of queue full errors on all queues.</span></span>
- <span data-ttu-id="27adc-1301">**timeouts** — указатель на место назначения для общего количества истечений времени ожидания во время приостановки потока во всех очередях.</span><span class="sxs-lookup"><span data-stu-id="27adc-1301">**timeouts** Pointer to destination for the total number of thread suspension timeouts on all queues.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-1302">*Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1302">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

<span data-ttu-id="27adc-1303">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="27adc-1303">**Return Values**</span></span>

- <span data-ttu-id="27adc-1304">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности системы очередей.</span><span class="sxs-lookup"><span data-stu-id="27adc-1304">**TX_SUCCESS** (0x00) Successful queue system performance get.</span></span>
- <span data-ttu-id="27adc-1305">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.</span><span class="sxs-lookup"><span data-stu-id="27adc-1305">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1306">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1306">Allowed From</span></span>

<span data-ttu-id="27adc-1307">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1307">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1308">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1308">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1309">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1309">See Also</span></span>

- <span data-ttu-id="27adc-1310">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1310">tx_queue_create</span></span>
- <span data-ttu-id="27adc-1311">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1311">tx_queue_delete</span></span>
- <span data-ttu-id="27adc-1312">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27adc-1312">tx_queue_flush</span></span>
- <span data-ttu-id="27adc-1313">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1313">tx_queue_front_send</span></span>
- <span data-ttu-id="27adc-1314">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1314">tx_queue_info_get</span></span>
- <span data-ttu-id="27adc-1315">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1315">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27adc-1316">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1316">tx_queue_prioritize</span></span>
- <span data-ttu-id="27adc-1317">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27adc-1317">tx_queue_receive</span></span>
- <span data-ttu-id="27adc-1318">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1318">tx_queue_send</span></span>
- <span data-ttu-id="27adc-1319">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1319">tx_queue_send_notify</span></span>

## <a name="tx_queue_prioritize"></a><span data-ttu-id="27adc-1320">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1320">tx_queue_prioritize</span></span>

<span data-ttu-id="27adc-1321">Назначение приоритета в списке приостановки очереди</span><span class="sxs-lookup"><span data-stu-id="27adc-1321">Prioritize queue suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1322">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1322">Prototype</span></span>

```c
UINT tx_queue_prioritize(TX_QUEUE *queue_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-1323">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1323">Description</span></span>

<span data-ttu-id="27adc-1324">Эта служба помещает поток с наибольшим приоритетом, приостановленный для получения (или размещения) сообщения в этой очереди, в начало списка приостановки.</span><span class="sxs-lookup"><span data-stu-id="27adc-1324">This service places the highest priority thread suspended for a message (or to place a message) on this queue at the front of the suspension list.</span></span>

<span data-ttu-id="27adc-1325">Все остальные потоки остаются в том же порядке FIFO, в котором они были приостановлены.</span><span class="sxs-lookup"><span data-stu-id="27adc-1325">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1326">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1326">Parameters</span></span>

- <span data-ttu-id="27adc-1327">**queue_ptr** — указатель на ранее созданную очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1327">**queue_ptr** Pointer to a previously created message queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1328">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1328">Return Values</span></span>

- <span data-ttu-id="27adc-1329">**TX_SUCCESS** (0x00) — успешное назначение приоритета в очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1329">**TX_SUCCESS** (0x00) Successful queue prioritize.</span></span>
- <span data-ttu-id="27adc-1330">**TX_QUEUE_ERROR** (0x09) — недопустимый указатель на очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1330">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1331">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1331">Allowed From</span></span>

<span data-ttu-id="27adc-1332">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1332">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1333">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1333">Preemption Possible</span></span>

<span data-ttu-id="27adc-1334">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-1334">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1335">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1335">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1336">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1336">See Also</span></span>

- <span data-ttu-id="27adc-1337">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1337">tx_queue_create</span></span>
- <span data-ttu-id="27adc-1338">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1338">tx_queue_delete</span></span>
- <span data-ttu-id="27adc-1339">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27adc-1339">tx_queue_flush</span></span>
- <span data-ttu-id="27adc-1340">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1340">tx_queue_front_send</span></span>
- <span data-ttu-id="27adc-1341">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1341">tx_queue_info_get</span></span>
- <span data-ttu-id="27adc-1342">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1342">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27adc-1343">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1343">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1344">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27adc-1344">tx_queue_receive</span></span>
- <span data-ttu-id="27adc-1345">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1345">tx_queue_send</span></span>
- <span data-ttu-id="27adc-1346">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1346">tx_queue_send_notify</span></span>

## <a name="tx_queue_receive"></a><span data-ttu-id="27adc-1347">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27adc-1347">tx_queue_receive</span></span>

<span data-ttu-id="27adc-1348">Получение сообщения из очереди сообщений</span><span class="sxs-lookup"><span data-stu-id="27adc-1348">Get message from message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1349">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1349">Prototype</span></span>

```c
UINT tx_queue_receive(
    TX_QUEUE *queue_ptr,
    VOID *destination_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="27adc-1350">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1350">Description</span></span>

<span data-ttu-id="27adc-1351">Эта служба получает сообщение из указанной очереди сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1351">This service retrieves a message from the specified message queue.</span></span> <span data-ttu-id="27adc-1352">Полученное сообщение **копируется** из очереди в область памяти, указанную указателем назначения.</span><span class="sxs-lookup"><span data-stu-id="27adc-1352">The retrieved message is **copied** from the queue into the memory area specified by the destination pointer.</span></span> <span data-ttu-id="27adc-1353">Затем это сообщение удаляется из очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1353">That message is then removed from the queue.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-1354">*Указанная область памяти назначения должна быть достаточно большой, чтобы вместить сообщение. То есть место назначения сообщения, на которое указывает*  \***destination_ptr** _ _, должно быть не меньше размера сообщения в этой очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1354">*The specified destination memory area must be large enough to hold the message; i.e., the message destination pointed to by* \***destination_ptr** _ _must be at least as large as the message size for this queue.</span></span> <span data-ttu-id="27adc-1355">В противном случае, если место назначения недостаточно велико, происходит повреждение памяти в следующей области памяти\*.</span><span class="sxs-lookup"><span data-stu-id="27adc-1355">Otherwise, if the destination is not large enough, memory corruption occurs in the following memory area.\*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1356">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1356">Parameters</span></span>

- <span data-ttu-id="27adc-1357">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="27adc-1357">**queue_ptr**</span></span> <br><span data-ttu-id="27adc-1358">Указатель на ранее созданную очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1358">Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="27adc-1359">**destination_ptr**</span><span class="sxs-lookup"><span data-stu-id="27adc-1359">**destination_ptr**</span></span> <br><span data-ttu-id="27adc-1360">Расположение для копирования сообщения.</span><span class="sxs-lookup"><span data-stu-id="27adc-1360">Location of where to copy the message.</span></span>
- <span data-ttu-id="27adc-1361">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="27adc-1361">**wait_option**</span></span> <br><span data-ttu-id="27adc-1362">Определяет, как работает служба, если очередь сообщений пуста.</span><span class="sxs-lookup"><span data-stu-id="27adc-1362">Defines how the service behaves if the message queue is empty.</span></span> <span data-ttu-id="27adc-1363">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="27adc-1363">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="27adc-1364">**TX_NO_WAIT** (0x00000000) — немедленный возврат из этой службы независимо от того, было ли выполнение успешным.</span><span class="sxs-lookup"><span data-stu-id="27adc-1364">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="27adc-1365">Это единственный допустимый параметр, если служба вызывается из непотока, например инициализации, таймера или ISR.</span><span class="sxs-lookup"><span data-stu-id="27adc-1365">This is the only valid option if the service is called from a non-thread; e.g.,  Initialization, timer, or ISR.</span></span>
  - <span data-ttu-id="27adc-1366">**TX_WAIT_FOREVER** (0xFFFFFFFF) — вызывающий поток приостанавливается на неопределенное время, пока не станет доступно сообщение.</span><span class="sxs-lookup"><span data-stu-id="27adc-1366">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a message is available.</span></span>
  - <span data-ttu-id="27adc-1367">значение времени ожидания (от 0x00000001 до 0xFFFFFFFE) — задать максимальное число тактов таймера для приостановки работы при ожидании сообщения.</span><span class="sxs-lookup"><span data-stu-id="27adc-1367">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1368">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1368">Return Values</span></span>

- <span data-ttu-id="27adc-1369">**TX_SUCCESS** (0x00) — успешное получение сообщения.</span><span class="sxs-lookup"><span data-stu-id="27adc-1369">**TX_SUCCESS** (0x00) Successful retrieval of message.</span></span>
- <span data-ttu-id="27adc-1370">**TX_DELETED** (0x01) — очередь сообщений была удалена, пока поток был приостановлен.</span><span class="sxs-lookup"><span data-stu-id="27adc-1370">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="27adc-1371">**TX_QUEUE_EMPTY** (0x0A) — службе не удалось получить сообщение, так как очередь была пуста в течение указанного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="27adc-1371">**TX_QUEUE_EMPTY** (0x0A) Service was unable to retrieve a message because the queue was empty for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="27adc-1372">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="27adc-1372">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="27adc-1373">**TX_QUEUE_ERROR** (0x09) — недопустимый указатель на очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1373">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="27adc-1374">**TX_PTR_ERROR** (0x03) — недопустимый указатель назначения для сообщения.</span><span class="sxs-lookup"><span data-stu-id="27adc-1374">**TX_PTR_ERROR** (0x03) Invalid destination pointer for message.</span></span>
- <span data-ttu-id="27adc-1375">**TX_WAIT_ERROR** (0x04) — в вызове из непотокового запроса был указан параметр ожидания, отличный от TX_NO_WAIT.</span><span class="sxs-lookup"><span data-stu-id="27adc-1375">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1376">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1376">Allowed From</span></span>

<span data-ttu-id="27adc-1377">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1377">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1378">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1378">Preemption Possible</span></span>

<span data-ttu-id="27adc-1379">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-1379">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1380">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1380">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1381">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1381">See Also</span></span>

- <span data-ttu-id="27adc-1382">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1382">tx_queue_create</span></span>
- <span data-ttu-id="27adc-1383">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1383">tx_queue_delete</span></span>
- <span data-ttu-id="27adc-1384">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27adc-1384">tx_queue_flush</span></span>
- <span data-ttu-id="27adc-1385">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1385">tx_queue_front_send</span></span>
- <span data-ttu-id="27adc-1386">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1386">tx_queue_info_get</span></span>
- <span data-ttu-id="27adc-1387">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1387">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27adc-1388">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1388">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1389">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1389">tx_queue_prioritize</span></span>
- <span data-ttu-id="27adc-1390">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1390">tx_queue_send</span></span>
- <span data-ttu-id="27adc-1391">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1391">tx_queue_send_notify</span></span>

## <a name="tx_queue_send"></a><span data-ttu-id="27adc-1392">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1392">tx_queue_send</span></span>

<span data-ttu-id="27adc-1393">Отправка сообщения в очередь сообщений</span><span class="sxs-lookup"><span data-stu-id="27adc-1393">Send message to message queue</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1394">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1394">Prototype</span></span>

```c
UINT tx_queue_send(
    TX_QUEUE *queue_ptr,
    VOID *source_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="27adc-1395">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1395">Description</span></span>

<span data-ttu-id="27adc-1396">Эта служба отправляет сообщение в указанную очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1396">This service sends a message to the specified message queue.</span></span> <span data-ttu-id="27adc-1397">Отправленное сообщение **копируется** в очередь из области памяти, заданной указателем источника.</span><span class="sxs-lookup"><span data-stu-id="27adc-1397">The sent message is **copied** to the queue from the memory area specified by the source pointer.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1398">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1398">Parameters</span></span>
- <span data-ttu-id="27adc-1399">**queue_ptr**</span><span class="sxs-lookup"><span data-stu-id="27adc-1399">**queue_ptr**</span></span> <br><span data-ttu-id="27adc-1400">Указатель на ранее созданную очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1400">Pointer to a previously created message queue.</span></span>
- <span data-ttu-id="27adc-1401">**source_ptr**</span><span class="sxs-lookup"><span data-stu-id="27adc-1401">**source_ptr**</span></span> <br><span data-ttu-id="27adc-1402">Указатель на сообщение.</span><span class="sxs-lookup"><span data-stu-id="27adc-1402">Pointer to the message.</span></span>
- <span data-ttu-id="27adc-1403">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="27adc-1403">**wait_option**</span></span> <br><span data-ttu-id="27adc-1404">Определяет, как работает служба, если очередь сообщений заполнена.</span><span class="sxs-lookup"><span data-stu-id="27adc-1404">Defines how the service behaves if the message queue is full.</span></span> <span data-ttu-id="27adc-1405">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="27adc-1405">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="27adc-1406">**TX_NO_WAIT** (0x00000000) — немедленный возврат из этой службы независимо от того, было ли выполнение успешным.</span><span class="sxs-lookup"><span data-stu-id="27adc-1406">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="27adc-1407">*Это единственный допустимый параметр, если служба вызывается из непотока, например инициализации, таймера или ISR*.</span><span class="sxs-lookup"><span data-stu-id="27adc-1407">*This is the only valid option if the service is called from a non-thread; e.g., Initialization, timer, or ISR*.</span></span>
  - <span data-ttu-id="27adc-1408">**TX_WAIT_FOREVER** (0xFFFFFFFF) — вызывающий поток приостанавливается на неопределенное время, пока в очереди не освободится место.</span><span class="sxs-lookup"><span data-stu-id="27adc-1408">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until there is room in the queue.</span></span>
  - <span data-ttu-id="27adc-1409">значение времени ожидания (от 0x00000001 до 0xFFFFFFFE) — задать максимальное число тактов таймера для приостановки работы при ожидании свободного места в очереди.</span><span class="sxs-lookup"><span data-stu-id="27adc-1409">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for room in the queue.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1410">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1410">Return Values</span></span>

- <span data-ttu-id="27adc-1411">**TX_SUCCESS** (0x00) — успешная отправка сообщения.</span><span class="sxs-lookup"><span data-stu-id="27adc-1411">**TX_SUCCESS** (0x00) Successful sending of message.</span></span>
- <span data-ttu-id="27adc-1412">**TX_DELETED** (0x01) — очередь сообщений была удалена, пока поток был приостановлен.</span><span class="sxs-lookup"><span data-stu-id="27adc-1412">**TX_DELETED** (0x01) Message queue was deleted while thread was suspended.</span></span>
- <span data-ttu-id="27adc-1413">**TX_QUEUE_FULL** (0x0B) — службе не удалось отправить сообщение, так как очередь была заполнена в течение всего указанного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="27adc-1413">**TX_QUEUE_FULL** (0x0B) Service was unable to send message because the queue was full for the duration of the specified time to wait.</span></span>
- <span data-ttu-id="27adc-1414">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="27adc-1414">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="27adc-1415">**TX_QUEUE_ERROR** (0x09) — недопустимый указатель на очередь сообщений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1415">**TX_QUEUE_ERROR** (0x09) Invalid message queue pointer.</span></span>
- <span data-ttu-id="27adc-1416">**TX_PTR_ERROR** (0x03) — недопустимый указатель источника для сообщения.</span><span class="sxs-lookup"><span data-stu-id="27adc-1416">**TX_PTR_ERROR** (0x03) Invalid source pointer for message.</span></span>
- <span data-ttu-id="27adc-1417">**TX_WAIT_ERROR** (0x04) — в вызове из непотокового запроса был указан параметр ожидания, отличный от TX_NO_WAIT.</span><span class="sxs-lookup"><span data-stu-id="27adc-1417">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1418">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1418">Allowed From</span></span>

<span data-ttu-id="27adc-1419">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1419">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1420">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1420">Preemption Possible</span></span>

<span data-ttu-id="27adc-1421">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-1421">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1422">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1422">Example</span></span>

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

<span data-ttu-id="27adc-1423">**См. также:**</span><span class="sxs-lookup"><span data-stu-id="27adc-1423">**See Also**</span></span>

- <span data-ttu-id="27adc-1424">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1424">tx_queue_create</span></span>
- <span data-ttu-id="27adc-1425">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1425">tx_queue_delete</span></span>
- <span data-ttu-id="27adc-1426">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27adc-1426">tx_queue_flush</span></span>
- <span data-ttu-id="27adc-1427">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1427">tx_queue_front_send</span></span>
- <span data-ttu-id="27adc-1428">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1428">tx_queue_info_get</span></span>
- <span data-ttu-id="27adc-1429">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1429">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27adc-1430">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1430">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1431">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1431">tx_queue_prioritize</span></span>
- <span data-ttu-id="27adc-1432">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27adc-1432">tx_queue_receive</span></span>
- <span data-ttu-id="27adc-1433">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1433">tx_queue_send_notify</span></span>

## <a name="tx_queue_send_notify"></a><span data-ttu-id="27adc-1434">tx_queue_send_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1434">tx_queue_send_notify</span></span>

<span data-ttu-id="27adc-1435">Уведомление приложения при отправке сообщения в очередь</span><span class="sxs-lookup"><span data-stu-id="27adc-1435">Notify application when message is sent to queue</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1436">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1436">Prototype</span></span>

```c
UINT tx_queue_send_notify(
    TX_QUEUE *queue_ptr,
    VOID (*queue_send_notify)(TX_QUEUE *));
```

### <a name="description"></a><span data-ttu-id="27adc-1437">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1437">Description</span></span>

<span data-ttu-id="27adc-1438">Эта служба регистрирует функцию обратного вызова для уведомлений, которая вызывается при каждой отправке сообщения в указанную очередь.</span><span class="sxs-lookup"><span data-stu-id="27adc-1438">This service registers a notification callback function that is called whenever a message is sent to the specified queue.</span></span> <span data-ttu-id="27adc-1439">Обработка обратного вызова уведомления определяется приложением.</span><span class="sxs-lookup"><span data-stu-id="27adc-1439">The processing of the notification callback is defined by the application.</span></span>

>[!NOTE]
> <span data-ttu-id="27adc-1440">*Обратному вызову уведомления приложения об отправке в очередь не разрешено вызывать никакой API ThreadX с параметром приостановки.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1440">*The application's queue send notification callback is not allowed to call any ThreadX API with a suspension option.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1441">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1441">Parameters</span></span>

- <span data-ttu-id="27adc-1442">**queue_ptr** — указатель на ранее созданную очередь.</span><span class="sxs-lookup"><span data-stu-id="27adc-1442">**queue_ptr** Pointer to previously created queue.</span></span>
- <span data-ttu-id="27adc-1443">**queue_send_notify** — указатель на функцию уведомления приложения об отправке в очередь.</span><span class="sxs-lookup"><span data-stu-id="27adc-1443">**queue_send_notify** Pointer to application's queue send notification function.</span></span> <span data-ttu-id="27adc-1444">Если это значение равно TX_NULL, уведомление отключено.</span><span class="sxs-lookup"><span data-stu-id="27adc-1444">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1445">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1445">Return Values</span></span>

- <span data-ttu-id="27adc-1446">**TX_SUCCESS** (0x00) — успешная регистрация уведомления об отправке в очередь.</span><span class="sxs-lookup"><span data-stu-id="27adc-1446">**TX_SUCCESS** (0x00) Successful registration of queue send notification.</span></span>
- <span data-ttu-id="27adc-1447">**TX_QUEUE_ERROR** (0x09) — недопустимый указатель на очередь.</span><span class="sxs-lookup"><span data-stu-id="27adc-1447">**TX_QUEUE_ERROR** (0x09) Invalid queue pointer.</span></span>
- <span data-ttu-id="27adc-1448">**TX_FEATURE_NOT_ENABLED** (0xFF) — система была скомпилирована с отключенными возможностями уведомлений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1448">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1449">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1449">Allowed From</span></span>

<span data-ttu-id="27adc-1450">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1450">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1451">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1451">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1452">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1452">See Also</span></span>

- <span data-ttu-id="27adc-1453">tx_queue_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1453">tx_queue_create</span></span>
- <span data-ttu-id="27adc-1454">tx_queue_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1454">tx_queue_delete</span></span>
- <span data-ttu-id="27adc-1455">tx_queue_flush</span><span class="sxs-lookup"><span data-stu-id="27adc-1455">tx_queue_flush</span></span>
- <span data-ttu-id="27adc-1456">tx_queue_front_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1456">tx_queue_front_send</span></span>
- <span data-ttu-id="27adc-1457">tx_queue_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1457">tx_queue_info_get</span></span>
- <span data-ttu-id="27adc-1458">tx_queue_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1458">tx_queue_performance_info_get</span></span>
- <span data-ttu-id="27adc-1459">tx_queue_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1459">tx_queue_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1460">tx_queue_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1460">tx_queue_prioritize</span></span>
- <span data-ttu-id="27adc-1461">tx_queue_receive</span><span class="sxs-lookup"><span data-stu-id="27adc-1461">tx_queue_receive</span></span>
- <span data-ttu-id="27adc-1462">tx_queue_send</span><span class="sxs-lookup"><span data-stu-id="27adc-1462">tx_queue_send</span></span>

## <a name="tx_semaphore_ceiling_put"></a><span data-ttu-id="27adc-1463">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1463">tx_semaphore_ceiling_put</span></span>

<span data-ttu-id="27adc-1464">Размещение экземпляра в семафоре со счетчиком с верхним пределом</span><span class="sxs-lookup"><span data-stu-id="27adc-1464">Place an instance in counting semaphore with ceiling</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1465">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1465">Prototype</span></span>

```c
UINT tx_semaphore_ceiling_put(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG ceiling);
```

### <a name="description"></a><span data-ttu-id="27adc-1466">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1466">Description</span></span>

<span data-ttu-id="27adc-1467">Эта служба помещает экземпляр в указанный семафор со счетчиком, который в действительности увеличивает счетчик семафора на единицу.</span><span class="sxs-lookup"><span data-stu-id="27adc-1467">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span> <span data-ttu-id="27adc-1468">Если текущее значение семафора со счетчиком больше или равно указанному пороговому значению, экземпляр не будет размещен и будет возвращена ошибка TX_CEILING_EXCEEDED.</span><span class="sxs-lookup"><span data-stu-id="27adc-1468">If the counting semaphore's current value is greater than or equal to the specified ceiling, the instance will not be put and a TX_CEILING_EXCEEDED error will be returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1469">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1469">Parameters</span></span>

- <span data-ttu-id="27adc-1470">**semaphore_ptr** — указатель на ранее созданный семафор.</span><span class="sxs-lookup"><span data-stu-id="27adc-1470">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="27adc-1471">**ceiling** — максимально допустимый предел для семафора (допустимые значения находятся в диапазоне от 1 до 0xFFFFFFFF).</span><span class="sxs-lookup"><span data-stu-id="27adc-1471">**ceiling** Maximum limit allowed for the semaphore (valid values range from 1 through 0xFFFFFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1472">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1472">Return Values</span></span>

- <span data-ttu-id="27adc-1473">**TX_SUCCESS (0x00)**  — успешное размещение в пределах семафора.</span><span class="sxs-lookup"><span data-stu-id="27adc-1473">**TX_SUCCESS (0x00)** Successful semaphore ceiling put.</span></span>
- <span data-ttu-id="27adc-1474">**TX_CEILING_EXCEEDED** (0x21) — запрос на размещение превышает допустимый предел.</span><span class="sxs-lookup"><span data-stu-id="27adc-1474">**TX_CEILING_EXCEEDED** (0x21) Put request exceeds ceiling.</span></span>
- <span data-ttu-id="27adc-1475">**TX_INVALID_CEILING** (0x22) — для параметра ceiling указано недопустимое нулевое значение.</span><span class="sxs-lookup"><span data-stu-id="27adc-1475">**TX_INVALID_CEILING** (0x22) An invalid value of zero was supplied for ceiling.</span></span>
- <span data-ttu-id="27adc-1476">**TX_SEMAPHORE_ERROR** (0x0C) — недопустимый указатель на семафор.</span><span class="sxs-lookup"><span data-stu-id="27adc-1476">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1477">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1477">Allowed From</span></span>

<span data-ttu-id="27adc-1478">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1478">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1479">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1479">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;

/* Increment the counting semaphore "my_semaphore" but make sure
that it never exceeds 7 as specified in the call. */
status = tx_semaphore_ceiling_put(&my_semaphore, 7);

/* If status is TX_SUCCESS the semaphore count has been
incremented. */
```

### <a name="see-also"></a><span data-ttu-id="27adc-1480">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1480">See Also</span></span>

- <span data-ttu-id="27adc-1481">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1481">tx_semaphore_create</span></span>
- <span data-ttu-id="27adc-1482">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1482">tx_semaphore_delete</span></span>
- <span data-ttu-id="27adc-1483">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1483">tx_semaphore_get</span></span>
- <span data-ttu-id="27adc-1484">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1484">tx_semaphore_info_get</span></span>
- <span data-ttu-id="27adc-1485">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1485">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="27adc-1486">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1486">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1487">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1487">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="27adc-1488">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1488">tx_semaphore_put</span></span>
- <span data-ttu-id="27adc-1489">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1489">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_create"></a><span data-ttu-id="27adc-1490">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1490">tx_semaphore_create</span></span>

<span data-ttu-id="27adc-1491">Создание семафора со счетчиком</span><span class="sxs-lookup"><span data-stu-id="27adc-1491">Create counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1492">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1492">Prototype</span></span>

```c
UINT tx_semaphore_create(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR *name_ptr, 
    ULONG initial_count);
```

### <a name="description"></a><span data-ttu-id="27adc-1493">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1493">Description</span></span>

<span data-ttu-id="27adc-1494">Эта служба создает семафор со счетчиком для синхронизации между потоками.</span><span class="sxs-lookup"><span data-stu-id="27adc-1494">This service creates a counting semaphore for inter-thread synchronization.</span></span> <span data-ttu-id="27adc-1495">Начальное значение счетчика семафора указывается в качестве входного параметра.</span><span class="sxs-lookup"><span data-stu-id="27adc-1495">The initial semaphore count is specified as an input parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1496">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1496">Parameters</span></span>

- <span data-ttu-id="27adc-1497">**semaphore_ptr** — указатель на блок управления семафором.</span><span class="sxs-lookup"><span data-stu-id="27adc-1497">**semaphore_ptr** Pointer to a semaphore control block.</span></span>
- <span data-ttu-id="27adc-1498">**name_ptr** — указатель на имя семафора.</span><span class="sxs-lookup"><span data-stu-id="27adc-1498">**name_ptr** Pointer to the name of the semaphore.</span></span>
- <span data-ttu-id="27adc-1499">**initial_count** — указывает начальное значение счетчика для семафора.</span><span class="sxs-lookup"><span data-stu-id="27adc-1499">**initial_count** Specifies the initial count for this semaphore.</span></span> <span data-ttu-id="27adc-1500">Допустимые значения находятся в диапазоне от 0x00000000 до 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="27adc-1500">Legal values range from 0x00000000 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1501">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1501">Return Values</span></span>

- <span data-ttu-id="27adc-1502">**TX_SUCCESS (0x00)**  — успешное создание семафора.</span><span class="sxs-lookup"><span data-stu-id="27adc-1502">**TX_SUCCESS** (0x00) Successful semaphore creation.</span></span>
- <span data-ttu-id="27adc-1503">**TX_SEMAPHORE_ERROR** (0x0C) — недопустимый указатель на семафор.</span><span class="sxs-lookup"><span data-stu-id="27adc-1503">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span> <span data-ttu-id="27adc-1504">Либо указатель имеет значение NULL, либо семафор уже создан.</span><span class="sxs-lookup"><span data-stu-id="27adc-1504">Either the pointer is NULL or the semaphore is already created.</span></span>
- <span data-ttu-id="27adc-1505">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-1505">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1506">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1506">Allowed From</span></span>

<span data-ttu-id="27adc-1507">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-1507">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1508">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1508">Preemption Possible</span></span>

<span data-ttu-id="27adc-1509">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-1509">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1510">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1510">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1511">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1511">See Also</span></span>

- <span data-ttu-id="27adc-1512">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1512">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="27adc-1513">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1513">tx_semaphore_delete</span></span>
- <span data-ttu-id="27adc-1514">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1514">tx_semaphore_get</span></span>
- <span data-ttu-id="27adc-1515">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1515">tx_semaphore_info_get</span></span>
- <span data-ttu-id="27adc-1516">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1516">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="27adc-1517">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1517">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1518">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1518">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="27adc-1519">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1519">tx_semaphore_put</span></span>
- <span data-ttu-id="27adc-1520">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1520">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_delete"></a><span data-ttu-id="27adc-1521">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1521">tx_semaphore_delete</span></span>

<span data-ttu-id="27adc-1522">Удаление семафора со счетчиком</span><span class="sxs-lookup"><span data-stu-id="27adc-1522">Delete counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1523">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1523">Prototype</span></span>
```c
UINT tx_semaphore_delete(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-1524">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1524">Description</span></span>

<span data-ttu-id="27adc-1525">Эта служба удаляет указанный семафор со счетчиком.</span><span class="sxs-lookup"><span data-stu-id="27adc-1525">This service deletes the specified counting semaphore.</span></span> <span data-ttu-id="27adc-1526">Все потоки, приостановленные в ожидании экземпляра семафора, возобновляются и получают состояние возврата TX_DELETED.</span><span class="sxs-lookup"><span data-stu-id="27adc-1526">All threads suspended waiting for a semaphore instance are resumed and given a TX_DELETED return status.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-1527">*Перед удалением семафора приложение должно убедиться в том, что функция обратного вызова уведомления о размещении для этого семафора завершена (или отключена). Кроме того, приложение должно предотвратить использование удаленного семафора в будущем.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1527">*The application must ensure that a put notify callback for this semaphore is completed (or disabled) before deleting the semaphore. In addition, the application must prevent all future use of a deleted semaphore.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1528">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1528">Parameters</span></span>

- <span data-ttu-id="27adc-1529">**semaphore_ptr** — указатель на ранее созданный семафор.</span><span class="sxs-lookup"><span data-stu-id="27adc-1529">**semaphore_ptr** Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1530">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1530">Return Values</span></span>

- <span data-ttu-id="27adc-1531">**TX_SUCCESS** (0x00) — успешное удаление семафора.</span><span class="sxs-lookup"><span data-stu-id="27adc-1531">**TX_SUCCESS** (0x00) Successful counting semaphore deletion.</span></span>
- <span data-ttu-id="27adc-1532">**TX_SEMAPHORE_ERROR** (0x0C) — недопустимый указатель на семафор со счетчиком.</span><span class="sxs-lookup"><span data-stu-id="27adc-1532">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="27adc-1533">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-1533">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1534">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1534">Allowed From</span></span>

<span data-ttu-id="27adc-1535">Потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-1535">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1536">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1536">Preemption Possible</span></span>

<span data-ttu-id="27adc-1537">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-1537">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1538">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1538">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Delete counting semaphore. Assume that the counting
semaphore has already been created. */
status = tx_semaphore_delete(&my_semaphore);

/* If status equals TX_SUCCESS, the counting semaphore is
deleted. */
```

<span data-ttu-id="27adc-1539">**См. также:**</span><span class="sxs-lookup"><span data-stu-id="27adc-1539">**See Also**</span></span>

- <span data-ttu-id="27adc-1540">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1540">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="27adc-1541">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1541">tx_semaphore_create</span></span>
- <span data-ttu-id="27adc-1542">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1542">tx_semaphore_get</span></span>
- <span data-ttu-id="27adc-1543">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1543">tx_semaphore_info_get</span></span>
- <span data-ttu-id="27adc-1544">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1544">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="27adc-1545">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1545">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1546">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1546">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="27adc-1547">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1547">tx_semaphore_put</span></span>
- <span data-ttu-id="27adc-1548">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1548">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_get"></a><span data-ttu-id="27adc-1549">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1549">tx_semaphore_get</span></span>

<span data-ttu-id="27adc-1550">Получение экземпляра из семафора со счетчиком</span><span class="sxs-lookup"><span data-stu-id="27adc-1550">Get instance from counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1551">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1551">Prototype</span></span>

```c
UINT tx_semaphore_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="27adc-1552">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1552">Description</span></span>

<span data-ttu-id="27adc-1553">Эта служба извлекает экземпляр (единицу счетчика) из указанного семафора со счетчиком.</span><span class="sxs-lookup"><span data-stu-id="27adc-1553">This service retrieves an instance (a single count) from the specified counting semaphore.</span></span> <span data-ttu-id="27adc-1554">В результате счетчик указанного семафора уменьшается на единицу.</span><span class="sxs-lookup"><span data-stu-id="27adc-1554">As a result, the specified semaphore's count is decreased by one.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1555">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1555">Parameters</span></span>

- <span data-ttu-id="27adc-1556">**semaphore_ptr**</span><span class="sxs-lookup"><span data-stu-id="27adc-1556">**semaphore_ptr**</span></span> <br><span data-ttu-id="27adc-1557">Указатель на ранее созданный семафор со счетчиком.</span><span class="sxs-lookup"><span data-stu-id="27adc-1557">Pointer to a previously created counting semaphore.</span></span>
- <span data-ttu-id="27adc-1558">**wait_option**</span><span class="sxs-lookup"><span data-stu-id="27adc-1558">**wait_option**</span></span> <br><span data-ttu-id="27adc-1559">Определяет, как служба ведет себя, если нет доступных экземпляров семафора, то есть счетчик семафора равен нулю.</span><span class="sxs-lookup"><span data-stu-id="27adc-1559">Defines how the service behaves if there are no instances of the semaphore available; i.e., the semaphore count is zero.</span></span> <span data-ttu-id="27adc-1560">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="27adc-1560">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="27adc-1561">**TX_NO_WAIT** (0x00000000) — немедленный возврат из этой службы независимо от того, было ли выполнение успешным.</span><span class="sxs-lookup"><span data-stu-id="27adc-1561">**TX_NO_WAIT** (0x00000000) - Selecting TX_NO_WAIT results in an immediate return from this service regardless of whether or not it was successful.</span></span> <span data-ttu-id="27adc-1562">*Это единственный допустимый параметр, если служба вызывается из непотока, например инициализации, таймера или ISR.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1562">*This is the only valid option if the service is called from a non-thread; e.g., initialization, timer, or ISR.*</span></span>
  - <span data-ttu-id="27adc-1563">**TX_WAIT_FOREVER** (0xFFFFFFFF) — вызывающий поток приостанавливается на неопределенное время, пока не станет доступен экземпляр семафора.</span><span class="sxs-lookup"><span data-stu-id="27adc-1563">**TX_WAIT_FOREVER** (0xFFFFFFFF) - Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a semaphore instance is available.</span></span>
  - <span data-ttu-id="27adc-1564">значение времени ожидания (от 0x00000001 до 0xFFFFFFFE) — задать максимальное число тактов таймера для приостановки работы при ожидании экземпляра семафора.</span><span class="sxs-lookup"><span data-stu-id="27adc-1564">timeout value (0x00000001 through 0xFFFFFFFE) - Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for a semaphore instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1565">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1565">Return Values</span></span>

- <span data-ttu-id="27adc-1566">**TX_SUCCESS** (0x00) — успешное получение экземпляра семафора.</span><span class="sxs-lookup"><span data-stu-id="27adc-1566">**TX_SUCCESS** (0x00) Successful retrieval of a semaphore instance.</span></span>
- <span data-ttu-id="27adc-1567">**TX_DELETED** (0x01) — семафор со счетчиком был удален, пока поток был приостановлен.</span><span class="sxs-lookup"><span data-stu-id="27adc-1567">**TX_DELETED** (0x01) Counting semaphore was deleted while thread was suspended.</span></span>
- <span data-ttu-id="27adc-1568">**TX_NO_INSTANCE** (0x0D) — службе не удалось получить экземпляр семафора со счетчиком (число семафоров в течение всего заданного времени ожидания было равно нулю).</span><span class="sxs-lookup"><span data-stu-id="27adc-1568">**TX_NO_INSTANCE** (0x0D) Service was unable to retrieve an instance of the counting semaphore (semaphore count is zero within the specified time to wait).</span></span>
- <span data-ttu-id="27adc-1569">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="27adc-1569">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="27adc-1570">**TX_SEMAPHORE_ERROR** (0x0C) — недопустимый указатель на семафор со счетчиком.</span><span class="sxs-lookup"><span data-stu-id="27adc-1570">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="27adc-1571">**TX_WAIT_ERROR** (0x04) — в вызове из непотокового запроса был указан параметр ожидания, отличный от TX_NO_WAIT.</span><span class="sxs-lookup"><span data-stu-id="27adc-1571">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1572">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1572">Allowed From</span></span>

<span data-ttu-id="27adc-1573">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1573">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1574">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1574">Preemption Possible</span></span>

<span data-ttu-id="27adc-1575">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-1575">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1576">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1576">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1577">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1577">See Also</span></span>

- <span data-ttu-id="27adc-1578">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1578">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="27adc-1579">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1579">tx_semaphore_create</span></span>
- <span data-ttu-id="27adc-1580">tx_semahore_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1580">tx_semahore_delete</span></span>
- <span data-ttu-id="27adc-1581">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1581">tx_semaphore_info_get</span></span>
- <span data-ttu-id="27adc-1582">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1582">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="27adc-1583">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1583">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="27adc-1584">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1584">tx_semaphore_put</span></span>
- <span data-ttu-id="27adc-1585">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1585">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_info_get"></a><span data-ttu-id="27adc-1586">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1586">tx_semaphore_info_get</span></span>

<span data-ttu-id="27adc-1587">Получение сведений о семафоре</span><span class="sxs-lookup"><span data-stu-id="27adc-1587">Retrieve information about semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1588">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1588">Prototype</span></span>

```c
UINT tx_semaphore_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    CHAR **name, ULONG *current_value,
    TX_THREAD **first_suspended,
    ULONG *suspended_count,
    TX_SEMAPHORE **next_semaphore);
```

### <a name="description"></a><span data-ttu-id="27adc-1589">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1589">Description</span></span>

<span data-ttu-id="27adc-1590">Эта служба получает сведения об указанном семафоре.</span><span class="sxs-lookup"><span data-stu-id="27adc-1590">This service retrieves information about the specified semaphore.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1591">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1591">Parameters</span></span>

- <span data-ttu-id="27adc-1592">**semaphore_ptr** — указатель на блок управления семафором.</span><span class="sxs-lookup"><span data-stu-id="27adc-1592">**semaphore_ptr** Pointer to semaphore control block.</span></span>
- <span data-ttu-id="27adc-1593">**name** — указатель на назначение для указателя на имя семафора.</span><span class="sxs-lookup"><span data-stu-id="27adc-1593">**name** Pointer to destination for the pointer to the semaphore's name.</span></span>
- <span data-ttu-id="27adc-1594">**current_value** — указатель на назначение для счетчика текущего семафора.</span><span class="sxs-lookup"><span data-stu-id="27adc-1594">**current_value** Pointer to destination for the current semaphore's count.</span></span>
- <span data-ttu-id="27adc-1595">**first_suspended** — указатель на назначение для указателя на поток, который находится первым в списке приостановки этого семафора.</span><span class="sxs-lookup"><span data-stu-id="27adc-1595">**first_suspended** Pointer to destination for the pointer to the thread that is first on the suspension list of this semaphore.</span></span>
- <span data-ttu-id="27adc-1596">**suspended_count** — указатель на назначения для количества потоков, приостановленных в этом семафоре.</span><span class="sxs-lookup"><span data-stu-id="27adc-1596">**suspended_count** Pointer to destination for the number of threads currently suspended on this semaphore.</span></span>
- <span data-ttu-id="27adc-1597">**next_semaphore** — указатель на назначение для указателя следующего созданного семафора.</span><span class="sxs-lookup"><span data-stu-id="27adc-1597">**next_semaphore** Pointer to destination for the pointer of the next created semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-1598">*Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1598">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1599">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1599">Return Values</span></span>

- <span data-ttu-id="27adc-1600">**TX_SUCCESS** (0x00) — сведения получены.</span><span class="sxs-lookup"><span data-stu-id="27adc-1600">**TX_SUCCESS** (0x00) information retrieval.</span></span>

- <span data-ttu-id="27adc-1601">**TX_SEMAPHORE_ERROR** (0x0C) — недопустимый указатель на семафор.</span><span class="sxs-lookup"><span data-stu-id="27adc-1601">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1602">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1602">Allowed From</span></span>

<span data-ttu-id="27adc-1603">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1603">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1604">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1604">Preemption Possible</span></span>

<span data-ttu-id="27adc-1605">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-1605">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1606">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1606">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1607">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1607">See Also</span></span>

- <span data-ttu-id="27adc-1608">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1608">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="27adc-1609">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1609">tx_semaphore_create</span></span>
- <span data-ttu-id="27adc-1610">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1610">tx_semaphore_delete</span></span>
- <span data-ttu-id="27adc-1611">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1611">tx_semaphore_get</span></span>
- <span data-ttu-id="27adc-1612">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1612">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="27adc-1613">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1613">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1614">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1614">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="27adc-1615">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1615">tx_semaphore_put</span></span>
- <span data-ttu-id="27adc-1616">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1616">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_info_get"></a><span data-ttu-id="27adc-1617">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1617">tx_semaphore_performance_info_get</span></span>

<span data-ttu-id="27adc-1618">Получение сведений о производительности семафора</span><span class="sxs-lookup"><span data-stu-id="27adc-1618">Get semaphore performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1619">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1619">Prototype</span></span>

```c
UINT tx_semaphore_performance_info_get(
    TX_SEMAPHORE *semaphore_ptr,
    ULONG *puts, 
    ULONG *gets,
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="27adc-1620">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1620">Description</span></span>

<span data-ttu-id="27adc-1621">Эта служба получает сведения о производительности указанного семафора.</span><span class="sxs-lookup"><span data-stu-id="27adc-1621">This service retrieves performance information about the specified semaphore.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-1622">*Библиотека ThreadX и приложение должны быть построены с определенным параметром* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _, чтобы служба могла вернуть сведения о производительности*.</span><span class="sxs-lookup"><span data-stu-id="27adc-1622">*The ThreadX library and application must be built with* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

<span data-ttu-id="27adc-1623">**Параметры**</span><span class="sxs-lookup"><span data-stu-id="27adc-1623">**Parameters**</span></span>

-  <span data-ttu-id="27adc-1624">**semaphore_ptr** — указатель на ранее созданный семафор.</span><span class="sxs-lookup"><span data-stu-id="27adc-1624">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
-  <span data-ttu-id="27adc-1625">**puts** — указатель на место назначения для количества запросов на размещение, выполненных в этом семафоре.</span><span class="sxs-lookup"><span data-stu-id="27adc-1625">**puts** Pointer to destination for the number of put requests performed on this semaphore.</span></span>
-  <span data-ttu-id="27adc-1626">**gets** — указатель на место назначения для количества запросов на получение, выполненных в этом семафоре.</span><span class="sxs-lookup"><span data-stu-id="27adc-1626">**gets** Pointer to destination for the number of get requests performed on this semaphore.</span></span>
-  <span data-ttu-id="27adc-1627">**suspensions** — указатель на место назначения для количества приостановок потоков на этом семафоре.</span><span class="sxs-lookup"><span data-stu-id="27adc-1627">**suspensions** Pointer to destination for the number of thread suspensions on this semaphore.</span></span>
-  <span data-ttu-id="27adc-1628">**timeouts** — указатель на место назначения для количества истечений времени ожидания во время приостановки потока на этом семафоре.</span><span class="sxs-lookup"><span data-stu-id="27adc-1628">**timeouts** Pointer to destination for the number of thread suspension timeouts on this semaphore.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-1629">*Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1629">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1630">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1630">Return Values</span></span>

- <span data-ttu-id="27adc-1631">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности семафора.</span><span class="sxs-lookup"><span data-stu-id="27adc-1631">**TX_SUCCESS** (0x00) Successful semaphore performance get.</span></span>
- <span data-ttu-id="27adc-1632">**TX_PTR_ERROR** (0x03) — недопустимый указатель на семафор.</span><span class="sxs-lookup"><span data-stu-id="27adc-1632">**TX_PTR_ERROR** (0x03) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="27adc-1633">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.</span><span class="sxs-lookup"><span data-stu-id="27adc-1633">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1634">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1634">Allowed From</span></span>

<span data-ttu-id="27adc-1635">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1635">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1636">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1636">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1637">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1637">See Also</span></span>

- <span data-ttu-id="27adc-1638">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1638">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="27adc-1639">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1639">tx_semaphore_create</span></span>
- <span data-ttu-id="27adc-1640">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1640">tx_semaphore_delete</span></span>
- <span data-ttu-id="27adc-1641">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1641">tx_semaphore_get</span></span>
- <span data-ttu-id="27adc-1642">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1642">tx_semaphore_info_get</span></span>
- <span data-ttu-id="27adc-1643">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1643">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1644">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1644">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="27adc-1645">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1645">tx_semaphore_put</span></span>
- <span data-ttu-id="27adc-1646">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1646">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_performance_system_info_get"></a><span data-ttu-id="27adc-1647">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1647">tx_semaphore_performance_system_info_get</span></span>

<span data-ttu-id="27adc-1648">Получение сведений о производительности системы семафоров</span><span class="sxs-lookup"><span data-stu-id="27adc-1648">Get semaphore system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1649">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1649">Prototype</span></span>

```c
UINT tx_semaphore_performance_system_info_get(
    ULONG *puts,
    ULONG *gets, 
    ULONG *suspensions, 
    ULONG *timeouts);
```

### <a name="description"></a><span data-ttu-id="27adc-1650">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1650">Description</span></span>

<span data-ttu-id="27adc-1651">Эта служба получает сведения о производительности всех семафоров в системе.</span><span class="sxs-lookup"><span data-stu-id="27adc-1651">This service retrieves performance information about all the semaphores in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-1652">*Библиотека ThreadX и приложение должны быть построены с определенным параметром* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _, чтобы служба могла вернуть сведения о производительности*</span><span class="sxs-lookup"><span data-stu-id="27adc-1652">*The ThreadX library and application must be built with* ***TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1653">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1653">Parameters</span></span>

- <span data-ttu-id="27adc-1654">**puts** — указатель на место назначения для общего количества запросов на размещение, выполненных во всех семафорах.</span><span class="sxs-lookup"><span data-stu-id="27adc-1654">**puts** Pointer to destination for the total number of put requests performed on all semaphores.</span></span>
- <span data-ttu-id="27adc-1655">**gets** — указатель на место назначения для общего количества запросов на получение, выполненных во всех семафорах.</span><span class="sxs-lookup"><span data-stu-id="27adc-1655">**gets** Pointer to destination for the total number of get requests performed on all semaphores.</span></span>
- <span data-ttu-id="27adc-1656">**suspensions** — указатель на место назначения для общего количества приостановок потоков на всех семафорах.</span><span class="sxs-lookup"><span data-stu-id="27adc-1656">**suspensions** Pointer to destination for the total number of thread suspensions on all semaphores.</span></span>
- <span data-ttu-id="27adc-1657">**timeouts** — указатель на место назначения для общего количества истечений времени ожидания во время приостановки потока на всех семафорах.</span><span class="sxs-lookup"><span data-stu-id="27adc-1657">**timeouts** Pointer to destination for the total number of thread suspension timeouts on all semaphores.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-1658">*Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1658">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1659">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1659">Return Values</span></span>

- <span data-ttu-id="27adc-1660">**TX_SUCCESS** (0x00) — получены сведения о производительности системы.</span><span class="sxs-lookup"><span data-stu-id="27adc-1660">**TX_SUCCESS** (0x00) system performance get.</span></span>
- <span data-ttu-id="27adc-1661">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.</span><span class="sxs-lookup"><span data-stu-id="27adc-1661">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1662">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1662">Allowed From</span></span>

<span data-ttu-id="27adc-1663">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1663">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1664">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1664">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1665">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1665">See Also</span></span>

- <span data-ttu-id="27adc-1666">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1666">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="27adc-1667">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1667">tx_semaphore_create</span></span>
- <span data-ttu-id="27adc-1668">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1668">tx_semaphore_delete</span></span>
- <span data-ttu-id="27adc-1669">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1669">tx_semaphore_get</span></span>
- <span data-ttu-id="27adc-1670">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1670">tx_semaphore_info_get</span></span>
- <span data-ttu-id="27adc-1671">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1671">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="27adc-1672">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1672">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="27adc-1673">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1673">tx_semaphore_put</span></span>
- <span data-ttu-id="27adc-1674">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1674">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_prioritize"></a><span data-ttu-id="27adc-1675">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1675">tx_semaphore_prioritize</span></span>

<span data-ttu-id="27adc-1676">Назначение приоритета в списке приостановки семафора</span><span class="sxs-lookup"><span data-stu-id="27adc-1676">Prioritize semaphore suspension list</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1677">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1677">Prototype</span></span>

```c
UINT tx_semaphore_prioritize(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-1678">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1678">Description</span></span>

<span data-ttu-id="27adc-1679">Эта служба размещает поток с наибольшим приоритетом, приостановленный для получения экземпляра семафора, в начало списка приостановки.</span><span class="sxs-lookup"><span data-stu-id="27adc-1679">This service places the highest priority thread suspended for an instance of the semaphore at the front of the suspension list.</span></span> <span data-ttu-id="27adc-1680">Все остальные потоки остаются в том же порядке FIFO, в котором они были приостановлены.</span><span class="sxs-lookup"><span data-stu-id="27adc-1680">All other threads remain in the same FIFO order they were suspended in.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1681">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1681">Parameters</span></span>

- <span data-ttu-id="27adc-1682">**semaphore_ptr** — указатель на ранее созданный семафор.</span><span class="sxs-lookup"><span data-stu-id="27adc-1682">**semaphore_ptr** Pointer to a previously created semaphore.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1683">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1683">Return Values</span></span>

- <span data-ttu-id="27adc-1684">**TX_SUCCESS (0x00)**  — успешное назначение приоритета в семафоре.</span><span class="sxs-lookup"><span data-stu-id="27adc-1684">**TX_SUCCESS** (0x00) Successful semaphore prioritize.</span></span>
- <span data-ttu-id="27adc-1685">**TX_SEMAPHORE_ERROR** (0x0C) — недопустимый указатель на семафор со счетчиком.</span><span class="sxs-lookup"><span data-stu-id="27adc-1685">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1686">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1686">Allowed From</span></span>

<span data-ttu-id="27adc-1687">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1687">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1688">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1688">Preemption Possible</span></span>

<span data-ttu-id="27adc-1689">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-1689">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1690">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1690">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1691">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1691">See Also</span></span>

- <span data-ttu-id="27adc-1692">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1692">tx_semaphore_create</span></span>
- <span data-ttu-id="27adc-1693">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1693">tx_semaphore_delete</span></span>
- <span data-ttu-id="27adc-1694">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1694">tx_semaphore_get</span></span>
- <span data-ttu-id="27adc-1695">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1695">tx_semaphore_info_get</span></span>
- <span data-ttu-id="27adc-1696">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1696">tx_semaphore_put</span></span>

## <a name="tx_semaphore_put"></a><span data-ttu-id="27adc-1697">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1697">tx_semaphore_put</span></span>

<span data-ttu-id="27adc-1698">Размещение экземпляра в семафоре со счетчиком</span><span class="sxs-lookup"><span data-stu-id="27adc-1698">Place an instance in counting semaphore</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1699">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1699">Prototype</span></span>

```c
UINT tx_semaphore_put(TX_SEMAPHORE *semaphore_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-1700">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1700">Description</span></span>

<span data-ttu-id="27adc-1701">Эта служба помещает экземпляр в указанный семафор со счетчиком, который в действительности увеличивает счетчик семафора на единицу.</span><span class="sxs-lookup"><span data-stu-id="27adc-1701">This service puts an instance into the specified counting semaphore, which in reality increments the counting semaphore by one.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-1702">*Если эта служба вызывается, когда семафор полностью заполнен единицами (0xFFFFFFFF), новая операция размещения приведет к сбросу семафора на нулевое значение.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1702">*If this service is called when the semaphore is all ones (OxFFFFFFFF), the new put operation will cause the semaphore to be reset to zero.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1703">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1703">Parameters</span></span>

- <span data-ttu-id="27adc-1704">**semaphore_ptr** — указатель на ранее созданный блок управления семафором со счетчиком.</span><span class="sxs-lookup"><span data-stu-id="27adc-1704">**semaphore_ptr** Pointer to the previously created counting semaphore control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1705">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1705">Return Values</span></span>

- <span data-ttu-id="27adc-1706">**TX_SUCCESS (0x00)**  — успешная операция размещения в семафоре.</span><span class="sxs-lookup"><span data-stu-id="27adc-1706">**TX_SUCCESS** (0x00) Successful semaphore put.</span></span>
- <span data-ttu-id="27adc-1707">**TX_SEMAPHORE_ERROR** (0x0C) — недопустимый указатель на семафор со счетчиком.</span><span class="sxs-lookup"><span data-stu-id="27adc-1707">**TX_SEMAPHORE_ERROR** (0x0C) Invalid pointer to counting semaphore.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1708">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1708">Allowed From</span></span>

<span data-ttu-id="27adc-1709">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1709">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1710">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1710">Preemption Possible</span></span>

<span data-ttu-id="27adc-1711">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-1711">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1712">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1712">Example</span></span>

```c
TX_SEMAPHORE my_semaphore;
UINT status;

/* Increment the counting semaphore "my_semaphore." */
status = tx_semaphore_put(&my_semaphore);

/* If status equals TX_SUCCESS, the semaphore count has
been incremented. Of course, if a thread was waiting,
it was given the semaphore instance and resumed. */
```

### <a name="see-also"></a><span data-ttu-id="27adc-1713">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1713">See Also</span></span>

- <span data-ttu-id="27adc-1714">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1714">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="27adc-1715">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1715">tx_semaphore_create</span></span>
- <span data-ttu-id="27adc-1716">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1716">tx_semaphore_delete</span></span>
- <span data-ttu-id="27adc-1717">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1717">tx_semaphore_info_get</span></span>
- <span data-ttu-id="27adc-1718">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1718">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="27adc-1719">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1719">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1720">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1720">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="27adc-1721">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1721">tx_semaphore_get</span></span>
- <span data-ttu-id="27adc-1722">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1722">tx_semaphore_put_notify</span></span>

## <a name="tx_semaphore_put_notify"></a><span data-ttu-id="27adc-1723">tx_semaphore_put_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1723">tx_semaphore_put_notify</span></span>

<span data-ttu-id="27adc-1724">Уведомление приложения о выполнении операции размещения в семафоре</span><span class="sxs-lookup"><span data-stu-id="27adc-1724">Notify application when semaphore is put</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1725">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1725">Prototype</span></span>

```c
UINT tx_semaphore_put_notify(
    TX_SEMAPHORE *semaphore_ptr,
    VOID (*semaphore_put_notify)(TX_SEMAPHORE *));
```

### <a name="description"></a><span data-ttu-id="27adc-1726">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1726">Description</span></span>

<span data-ttu-id="27adc-1727">Эта служба регистрирует функцию обратного вызова для уведомлений, которая вызывается при каждой операции размещения в семафоре.</span><span class="sxs-lookup"><span data-stu-id="27adc-1727">This service registers a notification callback function that is called whenever the specified semaphore is put.</span></span> <span data-ttu-id="27adc-1728">Обработка обратного вызова уведомления определяется приложением.</span><span class="sxs-lookup"><span data-stu-id="27adc-1728">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-1729">*Обратному вызову уведомления приложения о семафоре не разрешено вызывать никакой API ThreadX с параметром приостановки.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1729">*The application's semaphore notification callback is not allowed to call any ThreadX API with a suspension option.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1730">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1730">Parameters</span></span>

- <span data-ttu-id="27adc-1731">**semaphore_ptr** — указатель на ранее созданный семафор.</span><span class="sxs-lookup"><span data-stu-id="27adc-1731">**semaphore_ptr** Pointer to previously created semaphore.</span></span>
- <span data-ttu-id="27adc-1732">**semaphore_put_notify** — указатель на функцию уведомления приложения о размещении в семафоре.</span><span class="sxs-lookup"><span data-stu-id="27adc-1732">**semaphore_put_notify** Pointer to application's semaphore put notification function.</span></span> <span data-ttu-id="27adc-1733">Если это значение равно TX_NULL, уведомление отключено.</span><span class="sxs-lookup"><span data-stu-id="27adc-1733">If this value is TX_NULL, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1734">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1734">Return Values</span></span>

- <span data-ttu-id="27adc-1735">**TX_SUCCESS** (0x00) — успешная регистрация уведомления о размещении в семафоре.</span><span class="sxs-lookup"><span data-stu-id="27adc-1735">**TX_SUCCESS** (0x00) Successful registration of semaphore put notification.</span></span>
- <span data-ttu-id="27adc-1736">**TX_SEMAPHORE_ERROR** (0x0C) — недопустимый указатель на семафор.</span><span class="sxs-lookup"><span data-stu-id="27adc-1736">**TX_SEMAPHORE_ERROR** (0x0C) Invalid semaphore pointer.</span></span>
- <span data-ttu-id="27adc-1737">**TX_FEATURE_NOT_ENABLED** (0xFF) — система была скомпилирована с отключенными возможностями уведомлений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1737">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1738">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1738">Allowed From</span></span>

<span data-ttu-id="27adc-1739">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1739">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1740">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1740">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1741">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1741">See Also</span></span>

- <span data-ttu-id="27adc-1742">tx_semaphore_ceiling_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1742">tx_semaphore_ceiling_put</span></span>
- <span data-ttu-id="27adc-1743">tx_semaphore_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1743">tx_semaphore_create</span></span>
- <span data-ttu-id="27adc-1744">tx_semaphore_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1744">tx_semaphore_delete</span></span>
- <span data-ttu-id="27adc-1745">tx_semaphore_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1745">tx_semaphore_get</span></span>
- <span data-ttu-id="27adc-1746">tx_semaphore_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1746">tx_semaphore_info_get</span></span>
- <span data-ttu-id="27adc-1747">tx_semaphore_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1747">tx_semaphore_performance_info_get</span></span>
- <span data-ttu-id="27adc-1748">tx_semaphore_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1748">tx_semaphore_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1749">tx_semaphore_prioritize</span><span class="sxs-lookup"><span data-stu-id="27adc-1749">tx_semaphore_prioritize</span></span>
- <span data-ttu-id="27adc-1750">tx_semaphore_put</span><span class="sxs-lookup"><span data-stu-id="27adc-1750">tx_semaphore_put</span></span>

## <a name="tx_thread_create"></a><span data-ttu-id="27adc-1751">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1751">tx_thread_create</span></span>

<span data-ttu-id="27adc-1752">Создание потока приложения</span><span class="sxs-lookup"><span data-stu-id="27adc-1752">Create application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1753">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1753">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="27adc-1754">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1754">Description</span></span>

<span data-ttu-id="27adc-1755">Эта служба создает поток приложения, который запускает выполнение с указанной функции входа в задачу.</span><span class="sxs-lookup"><span data-stu-id="27adc-1755">This service creates an application thread that starts execution at the specified task entry function.</span></span> <span data-ttu-id="27adc-1756">Стек, приоритет, порог вытеснения и временной срез являются атрибутами, задаваемыми входными параметрами.</span><span class="sxs-lookup"><span data-stu-id="27adc-1756">The stack, priority, preemption-threshold, and time-slice are among the attributes specified by the input parameters.</span></span> <span data-ttu-id="27adc-1757">Кроме того, также указывается начальное состояние выполнения потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1757">In addition, the initial execution state of the thread is also specified.</span></span>

<span data-ttu-id="27adc-1758">**Параметры**</span><span class="sxs-lookup"><span data-stu-id="27adc-1758">**Parameters**</span></span>

- <span data-ttu-id="27adc-1759">**thread_ptr** — указатель на блок управления потоком.</span><span class="sxs-lookup"><span data-stu-id="27adc-1759">**thread_ptr** Pointer to a thread control block.</span></span>
- <span data-ttu-id="27adc-1760">**name_ptr** — указатель на имя потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1760">**name_ptr** Pointer to the name of the thread.</span></span>
- <span data-ttu-id="27adc-1761">**entry_function** — задает начальную функцию C для выполнения потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1761">**entry_function** Specifies the initial C function for thread execution.</span></span> <span data-ttu-id="27adc-1762">Когда поток возвращается из этой функции входа, он помещается в *завершенное* состояние и приостанавливается на неопределенное время.</span><span class="sxs-lookup"><span data-stu-id="27adc-1762">When a thread returns from this entry function, it is placed in a *completed* state and suspended indefinitely.</span></span>
- <span data-ttu-id="27adc-1763">**entry_input** — 32-разрядное значение, которое передается в функцию входа потока при первом выполнении.</span><span class="sxs-lookup"><span data-stu-id="27adc-1763">**entry_input** A 32-bit value that is passed to the thread's entry function when it first executes.</span></span> <span data-ttu-id="27adc-1764">Использование этих входных данных определяется исключительно приложением.</span><span class="sxs-lookup"><span data-stu-id="27adc-1764">The use for this input is determined exclusively by the application.</span></span>
- <span data-ttu-id="27adc-1765">**stack_start** — начальный адрес области памяти стека.</span><span class="sxs-lookup"><span data-stu-id="27adc-1765">**stack_start** Starting address of the stack's memory area.</span></span>
- <span data-ttu-id="27adc-1766">**stack_size** — число байтов в области памяти стека.</span><span class="sxs-lookup"><span data-stu-id="27adc-1766">**stack_size** Number bytes in the stack memory area.</span></span> <span data-ttu-id="27adc-1767">Область стека потока должна быть достаточно большой, чтобы справиться с вложением вызовов функций и использованием локальных переменных в худшем случае.</span><span class="sxs-lookup"><span data-stu-id="27adc-1767">The thread's stack area must be large enough to handle its worst-case function call nesting and local variable usage.</span></span>
- <span data-ttu-id="27adc-1768">**priority** — числовое значение приоритета потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1768">**priority** Numerical priority of thread.</span></span> <span data-ttu-id="27adc-1769">Допустимые значения находятся в диапазоне от 0 до (TX_MAX_PRIORITES-1), где значение 0 соответствует наивысшему приоритету.</span><span class="sxs-lookup"><span data-stu-id="27adc-1769">Legal values range from 0 through (TX_MAX_PRIORITES-1), where a value of 0 represents the highest priority.</span></span>
- <span data-ttu-id="27adc-1770">**preempt_threshold** — уровень наивысшего приоритета (от 0 до (TX_MAX_PRIORITIES-1)) при отключенном вытеснении.</span><span class="sxs-lookup"><span data-stu-id="27adc-1770">**preempt_threshold** Highest priority level (0 through (TX_MAX_PRIORITIES-1)) of disabled preemption.</span></span> <span data-ttu-id="27adc-1771">Только приоритеты выше этого уровня могут вытеснять этот поток.</span><span class="sxs-lookup"><span data-stu-id="27adc-1771">Only priorities higher than this level are allowed to preempt this thread.</span></span> <span data-ttu-id="27adc-1772">Это значение должно быть меньше или равно указанному приоритету.</span><span class="sxs-lookup"><span data-stu-id="27adc-1772">This value must be less than or equal to the specified priority.</span></span> <span data-ttu-id="27adc-1773">Значение, равное приоритету потока, отключает приоритет вытеснения.</span><span class="sxs-lookup"><span data-stu-id="27adc-1773">A value equal to the thread priority disables preemption-threshold.</span></span>
- <span data-ttu-id="27adc-1774">**time_slice** — количество тактов таймера, которое этот поток может выполнять до того, как другие готовые потоки с таким же приоритетом получают возможность запуска.</span><span class="sxs-lookup"><span data-stu-id="27adc-1774">**time_slice** Number of timer-ticks this thread is allowed to run before other ready threads of the same priority are given a chance to run.</span></span> <span data-ttu-id="27adc-1775">Обратите внимание, что при использовании порогового значения вытеснения временной срез отключается.</span><span class="sxs-lookup"><span data-stu-id="27adc-1775">Note that using preemption-threshold disables time-slicing.</span></span> <span data-ttu-id="27adc-1776">Допустимое значение временного среза находится в диапазоне от 1 до 0xFFFFFFFF (включительно).</span><span class="sxs-lookup"><span data-stu-id="27adc-1776">Legal time-slice values range from 1 to 0xFFFFFFFF (inclusive).</span></span> <span data-ttu-id="27adc-1777">Значение **TX_NO_TIME_SLICE** (значение 0) отключает временной срез для этого потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1777">A value of **TX_NO_TIME_SLICE** (a value of 0) disables time-slicing of this thread.</span></span>

  > [!NOTE]
  > <span data-ttu-id="27adc-1778">*Использование временного среза приводит к небольшому количеству системных издержек. Так как временной срез полезен только в случаях, когда несколько потоков имеют одинаковый приоритет, для потоков с уникальными приоритетами не следует назначать временной срез.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1778">*Using time-slicing results in a slight amount of system overhead.   Since time-slicing is only useful in cases where multiple threads   share the same priority, threads having a unique priority should not   be assigned a time-slice.*</span></span>

- <span data-ttu-id="27adc-1779">**auto_start** — указывает, запускается ли поток немедленно или помещается в приостановленное состояние.</span><span class="sxs-lookup"><span data-stu-id="27adc-1779">**auto_start** Specifies whether the thread starts immediately or is placed in a suspended state.</span></span> <span data-ttu-id="27adc-1780">Допустимые значения: **TX_AUTO_START** (0x01) и **TX_DONT_START** (0x00).</span><span class="sxs-lookup"><span data-stu-id="27adc-1780">Legal options are **TX_AUTO_START** (0x01) and **TX_DONT_START** (0x00).</span></span> <span data-ttu-id="27adc-1781">Если указано TX_DONT_START, приложение должно затем вызвать tx_thread_resume для выполнения потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1781">If TX_DONT_START is specified, the application must later call tx_thread_resume in order for the thread to run.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1782">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1782">Return Values</span></span>

- <span data-ttu-id="27adc-1783">**TX_SUCCESS** (0x00) — успешное создание потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1783">**TX_SUCCESS** (0x00) Successful thread creation.</span></span>
- <span data-ttu-id="27adc-1784">**TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="27adc-1784">**TX_THREAD_ERROR** (0x0E) Invalid thread control pointer.</span></span> <span data-ttu-id="27adc-1785">Либо указатель имеет значение NULL, либо поток уже создан.</span><span class="sxs-lookup"><span data-stu-id="27adc-1785">Either the pointer is NULL or the thread is already created.</span></span>
- <span data-ttu-id="27adc-1786">**TX_PTR_ERROR** (0x03) — недопустимый начальный адрес точки входа или недопустимая область стека, обычно имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="27adc-1786">**TX_PTR_ERROR** (0x03) Invalid starting address of the entry point or the stack area is invalid, usually NULL.</span></span>
- <span data-ttu-id="27adc-1787">**TX_SIZE_ERROR** (0x05) —недопустимый размер области стека.</span><span class="sxs-lookup"><span data-stu-id="27adc-1787">**TX_SIZE_ERROR** (0x05) Size of stack area is invalid.</span></span> <span data-ttu-id="27adc-1788">Потоки должны иметь по крайней мере **TX_MINIMUM_STACK** байтов для выполнения.</span><span class="sxs-lookup"><span data-stu-id="27adc-1788">Threads must have at least **TX_MINIMUM_STACK** bytes to execute.</span></span>
- <span data-ttu-id="27adc-1789">**TX_PRIORITY_ERROR** (0x0F) — приоритет потока имеет значение вне допустимого диапазона (от 0 до (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="27adc-1789">**TX_PRIORITY_ERROR** (0x0F) Invalid thread priority, which is a value outside the range of (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="27adc-1790">**TX_THRESH_ERROR** (0x18) — указан недопустимый порог вытеснения.</span><span class="sxs-lookup"><span data-stu-id="27adc-1790">**TX_THRESH_ERROR** (0x18) Invalid preemptionthreshold specified.</span></span> <span data-ttu-id="27adc-1791">Это значение должно быть допустимым приоритетом, меньшим или равным начальному приоритету потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1791">This value must be a valid priority less than or equal to the initial priority of the thread.</span></span>
- <span data-ttu-id="27adc-1792">**TX_START_ERROR** (0x10) — недопустимое значения параметра автоматического запуска (auto_start).</span><span class="sxs-lookup"><span data-stu-id="27adc-1792">**TX_START_ERROR** (0x10) Invalid auto-start selection.</span></span>
- <span data-ttu-id="27adc-1793">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-1793">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1794">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1794">Allowed From</span></span>

<span data-ttu-id="27adc-1795">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-1795">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1796">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1796">Preemption Possible</span></span>

<span data-ttu-id="27adc-1797">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-1797">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1798">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1798">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1799">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1799">See Also</span></span>

- <span data-ttu-id="27adc-1800">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1800">tx_thread_delete</span></span>
- <span data-ttu-id="27adc-1801">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1801">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27adc-1802">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27adc-1802">tx_thread_identify</span></span>
- <span data-ttu-id="27adc-1803">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1803">tx_thread_info_get</span></span>
- <span data-ttu-id="27adc-1804">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1804">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27adc-1805">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1805">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1806">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27adc-1806">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27adc-1807">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27adc-1807">tx_thread_priority_change</span></span>
- <span data-ttu-id="27adc-1808">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27adc-1808">tx_thread_relinquish</span></span>
- <span data-ttu-id="27adc-1809">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27adc-1809">tx_thread_reset</span></span>
- <span data-ttu-id="27adc-1810">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27adc-1810">tx_thread_resume</span></span>
- <span data-ttu-id="27adc-1811">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27adc-1811">tx_thread_sleep</span></span>
- <span data-ttu-id="27adc-1812">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1812">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27adc-1813">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27adc-1813">tx_thread_suspend</span></span>
- <span data-ttu-id="27adc-1814">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27adc-1814">tx_thread_terminate</span></span>
- <span data-ttu-id="27adc-1815">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27adc-1815">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27adc-1816">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27adc-1816">tx_thread_wait_abort</span></span>

## <a name="tx_thread_delete"></a><span data-ttu-id="27adc-1817">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1817">tx_thread_delete</span></span>

<span data-ttu-id="27adc-1818">Удаление потока приложения</span><span class="sxs-lookup"><span data-stu-id="27adc-1818">Delete application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1819">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1819">Prototype</span></span>

```c
UINT tx_thread_delete(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-1820">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1820">Description</span></span>

<span data-ttu-id="27adc-1821">Эта служба удаляет указанный поток приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-1821">This service deletes the specified application thread.</span></span> <span data-ttu-id="27adc-1822">Так как указанный поток должен находиться в состоянии TERMINATED или COMPLETED, эту службу нельзя вызвать из потока, пытающегося удалить самого себя.</span><span class="sxs-lookup"><span data-stu-id="27adc-1822">Since the specified thread must be in a terminated or completed state, this service cannot be called from a thread attempting to delete itself.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-1823">*За управление областью памяти, связанной со стеком потока, которая становится доступна после завершения этой службы,отвечает приложение. Кроме того, приложение должно предотвращать использование удаленного потока.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1823">*It is the application's responsibility to manage the memory area associated with the thread's stack, which is available after this service completes. In addition, the application must prevent use of a deleted thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1824">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1824">Parameters</span></span>

- <span data-ttu-id="27adc-1825">**thread_ptr** — указатель на ранее созданный поток приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-1825">**thread_ptr** Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1826">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1826">Return Values</span></span>

- <span data-ttu-id="27adc-1827">**TX_SUCCESS** (0x00) — успешное удаление потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1827">**TX_SUCCESS** (0x00) Successful thread deletion.</span></span>
- <span data-ttu-id="27adc-1828">**TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-1828">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="27adc-1829">**TX_DELETE_ERROR** (0x11) — указанный поток не находится в состоянии TERMINATED или COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="27adc-1829">**TX_DELETE_ERROR** (0x11) Specified thread is not in a terminated or completed state.</span></span>
- <span data-ttu-id="27adc-1830">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-1830">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1831">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1831">Allowed From</span></span>

<span data-ttu-id="27adc-1832">Потоки и таймеры</span><span class="sxs-lookup"><span data-stu-id="27adc-1832">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1833">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1833">Preemption Possible</span></span>

<span data-ttu-id="27adc-1834">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-1834">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1835">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1835">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1836">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1836">See Also</span></span>

- <span data-ttu-id="27adc-1837">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1837">tx_thread_create</span></span>
- <span data-ttu-id="27adc-1838">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1838">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27adc-1839">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27adc-1839">tx_thread_identify</span></span>
- <span data-ttu-id="27adc-1840">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1840">tx_thread_info_get</span></span>
- <span data-ttu-id="27adc-1841">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1841">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27adc-1842">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1842">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1843">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27adc-1843">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27adc-1844">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27adc-1844">tx_thread_priority_change</span></span>
- <span data-ttu-id="27adc-1845">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27adc-1845">tx_thread_relinquish</span></span>
- <span data-ttu-id="27adc-1846">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27adc-1846">tx_thread_reset</span></span>
- <span data-ttu-id="27adc-1847">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27adc-1847">tx_thread_resume</span></span>
- <span data-ttu-id="27adc-1848">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27adc-1848">tx_thread_sleep</span></span>
- <span data-ttu-id="27adc-1849">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1849">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27adc-1850">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27adc-1850">tx_thread_suspend</span></span>
- <span data-ttu-id="27adc-1851">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27adc-1851">tx_thread_terminate</span></span>
- <span data-ttu-id="27adc-1852">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27adc-1852">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27adc-1853">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27adc-1853">tx_thread_wait_abort</span></span>

## <a name="tx_thread_entry_exit_notify"></a><span data-ttu-id="27adc-1854">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1854">tx_thread_entry_exit_notify</span></span>

<span data-ttu-id="27adc-1855">Уведомление приложения при входе и выходе из потока</span><span class="sxs-lookup"><span data-stu-id="27adc-1855">Notify application upon thread entry and exit</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1856">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1856">Prototype</span></span>

```c
UINT tx_thread_entry_exit_notify(
    TX_THREAD *thread_ptr,
    VOID (*entry_exit_notify)(TX_THREAD *, UINT));
```

### <a name="description"></a><span data-ttu-id="27adc-1857">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1857">Description</span></span>

<span data-ttu-id="27adc-1858">Эта служба регистрирует функцию обратного вызова для уведомлений, которая вызывается при каждом входе и выходе из потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1858">This service registers a notification callback function that is called whenever the specified thread is entered or exits.</span></span> <span data-ttu-id="27adc-1859">Обработка обратного вызова уведомления определяется приложением.</span><span class="sxs-lookup"><span data-stu-id="27adc-1859">The processing of the notification callback is defined by the application.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-1860">Обратному вызову уведомления приложения о входе или выходе из потока не разрешено вызывать никакой API ThreadX с параметром приостановки.</span><span class="sxs-lookup"><span data-stu-id="27adc-1860">The application's thread entry/exit notification callback is not allowed to call any ThreadX API with a suspension option.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1861">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1861">Parameters</span></span>

- <span data-ttu-id="27adc-1862">**thread_ptr** — указатель на ранее созданный поток.</span><span class="sxs-lookup"><span data-stu-id="27adc-1862">**thread_ptr** Pointer to previously created thread.</span></span>
- <span data-ttu-id="27adc-1863">**entry_exit_notify**— указатель на функцию уведомления приложения о входе или выходе из потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1863">**entry_exit_notify** Pointer to application's thread entry/exit notification function.</span></span> <span data-ttu-id="27adc-1864">Второй параметр функции уведомления о входе или выходе указывает на значение входа или выхода.</span><span class="sxs-lookup"><span data-stu-id="27adc-1864">The second parameter to the entry/exit notification function designates if an entry or exit is present.</span></span> <span data-ttu-id="27adc-1865">Значение **TX_THREAD_ENTRY** (0x00) указывает на регистрацию входа в поток, а значение **TX_THREAD_EXIT** (0x01) — на регистрацию выхода из потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1865">The value **TX_THREAD_ENTRY** (0x00) indicates the thread was entered, while the value **TX_THREAD_EXIT** (0x01) indicates the thread was exited.</span></span> <span data-ttu-id="27adc-1866">Если это значение равно **TX_NULL**, уведомление отключено.</span><span class="sxs-lookup"><span data-stu-id="27adc-1866">If this value is **TX_NULL**, notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1867">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1867">Return Values</span></span>

- <span data-ttu-id="27adc-1868">**TX_SUCCESS** (0x00) — успешная регистрация функции уведомления о входе и выходе из потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1868">**TX_SUCCESS** (0x00) Successful registration of the thread entry/exit notification function.</span></span>
- <span data-ttu-id="27adc-1869">**TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="27adc-1869">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="27adc-1870">**TX_FEATURE_NOT_ENABLED** (0xFF) — система была скомпилирована с отключенными возможностями уведомлений.</span><span class="sxs-lookup"><span data-stu-id="27adc-1870">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled with notification capabilities disabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1871">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1871">Allowed From</span></span>

<span data-ttu-id="27adc-1872">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1872">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1873">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1873">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1874">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1874">See Also</span></span>

- <span data-ttu-id="27adc-1875">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1875">tx_thread_create</span></span>
- <span data-ttu-id="27adc-1876">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1876">tx_thread_delete</span></span>
- <span data-ttu-id="27adc-1877">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1877">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27adc-1878">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27adc-1878">tx_thread_identify</span></span>
- <span data-ttu-id="27adc-1879">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1879">tx_thread_info_get</span></span>
- <span data-ttu-id="27adc-1880">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1880">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27adc-1881">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1881">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1882">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27adc-1882">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27adc-1883">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27adc-1883">tx_thread_priority_change</span></span>
- <span data-ttu-id="27adc-1884">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27adc-1884">tx_thread_relinquish</span></span>
- <span data-ttu-id="27adc-1885">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27adc-1885">tx_thread_reset</span></span>
- <span data-ttu-id="27adc-1886">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27adc-1886">tx_thread_resume</span></span>
- <span data-ttu-id="27adc-1887">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27adc-1887">tx_thread_sleep</span></span>
- <span data-ttu-id="27adc-1888">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1888">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27adc-1889">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27adc-1889">tx_thread_suspend</span></span>
- <span data-ttu-id="27adc-1890">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27adc-1890">tx_thread_terminate</span></span>
- <span data-ttu-id="27adc-1891">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27adc-1891">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27adc-1892">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27adc-1892">tx_thread_wait_abort</span></span>

## <a name="tx_thread_identify"></a><span data-ttu-id="27adc-1893">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27adc-1893">tx_thread_identify</span></span>

<span data-ttu-id="27adc-1894">Возвращает указатель на выполняющийся в данный момент поток</span><span class="sxs-lookup"><span data-stu-id="27adc-1894">Retrieves pointer to currently executing thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1895">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1895">Prototype</span></span>

```c
TX_THREAD* tx_thread_identify(VOID);
```
### <a name="description"></a><span data-ttu-id="27adc-1896">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1896">Description</span></span>

<span data-ttu-id="27adc-1897">Эта служба возвращает указатель на выполняющийся в данный момент поток.</span><span class="sxs-lookup"><span data-stu-id="27adc-1897">This service returns a pointer to the currently executing thread.</span></span> <span data-ttu-id="27adc-1898">Если ни один поток не выполняется, служба возвращает пустой указатель.</span><span class="sxs-lookup"><span data-stu-id="27adc-1898">If no thread is executing, this service returns a null pointer.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-1899">*Если эта служба вызывается из ISR, возвращаемое значение представляет собой поток, запущенный до выполнения обработчика прерываний.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1899">*If this service is called from an ISR, the return value represents the thread running prior to the executing interrupt handler.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1900">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1900">Parameters</span></span>

<span data-ttu-id="27adc-1901">None</span><span class="sxs-lookup"><span data-stu-id="27adc-1901">None</span></span>

### <a name="retuen-values"></a><span data-ttu-id="27adc-1902">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1902">Retuen Values</span></span>

- <span data-ttu-id="27adc-1903">**указатель на поток** — указатель на выполняющийся в данный момент поток.</span><span class="sxs-lookup"><span data-stu-id="27adc-1903">**thread pointer** Pointer to the currently executing thread.</span></span> <span data-ttu-id="27adc-1904">Если ни один поток не выполняется, возвращается значение **TX_NULL**.</span><span class="sxs-lookup"><span data-stu-id="27adc-1904">If no thread is executing, the return value is **TX_NULL**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1905">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1905">Allowed From</span></span>

<span data-ttu-id="27adc-1906">Потоки и ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1906">Threads and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1907">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1907">Preemption Possible</span></span>

<span data-ttu-id="27adc-1908">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-1908">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1909">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1909">Example</span></span>

<span data-ttu-id="27adc-1910">TX_THREAD \*my_thread_ptr;</span><span class="sxs-lookup"><span data-stu-id="27adc-1910">TX_THREAD \*my_thread_ptr;</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1911">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1911">See Also</span></span>

- <span data-ttu-id="27adc-1912">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1912">tx_thread_create</span></span>
- <span data-ttu-id="27adc-1913">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1913">tx_thread_delete</span></span>
- <span data-ttu-id="27adc-1914">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1914">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27adc-1915">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1915">tx_thread_info_get</span></span>
- <span data-ttu-id="27adc-1916">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1916">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27adc-1917">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1917">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1918">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27adc-1918">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27adc-1919">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27adc-1919">tx_thread_priority_change</span></span>
- <span data-ttu-id="27adc-1920">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27adc-1920">tx_thread_relinquish</span></span>
- <span data-ttu-id="27adc-1921">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27adc-1921">tx_thread_reset</span></span>
- <span data-ttu-id="27adc-1922">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27adc-1922">tx_thread_resume</span></span>
- <span data-ttu-id="27adc-1923">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27adc-1923">tx_thread_sleep</span></span>
- <span data-ttu-id="27adc-1924">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1924">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27adc-1925">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27adc-1925">tx_thread_suspend</span></span>
- <span data-ttu-id="27adc-1926">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27adc-1926">tx_thread_terminate</span></span>
- <span data-ttu-id="27adc-1927">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27adc-1927">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27adc-1928">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27adc-1928">tx_thread_wait_abort</span></span>

## <a name="tx_thread_info_get"></a><span data-ttu-id="27adc-1929">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1929">tx_thread_info_get</span></span>

<span data-ttu-id="27adc-1930">Получение сведений о потоке</span><span class="sxs-lookup"><span data-stu-id="27adc-1930">Retrieve information about thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1931">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1931">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="27adc-1932">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1932">Description</span></span>

<span data-ttu-id="27adc-1933">Эта служба получает сведения об указанном потоке.</span><span class="sxs-lookup"><span data-stu-id="27adc-1933">This service retrieves information about the specified thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1934">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1934">Parameters</span></span>
- <span data-ttu-id="27adc-1935">**thread_ptr** — указатель на блок управления потоком.</span><span class="sxs-lookup"><span data-stu-id="27adc-1935">**thread_ptr** Pointer to thread control block.</span></span>
- <span data-ttu-id="27adc-1936">**name** — указатель на назначение для указателя на имя потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1936">**name** Pointer to destination for the pointer to the thread's name.</span></span>
- <span data-ttu-id="27adc-1937">**state** — указатель на назначение для текущего состояния выполнения потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1937">**state** Pointer to destination for the thread's current execution state.</span></span> <span data-ttu-id="27adc-1938">Возможны следующие значения.</span><span class="sxs-lookup"><span data-stu-id="27adc-1938">Possible values are as follows.</span></span>
    - <span data-ttu-id="27adc-1939">**TX_READY** (0x00)</span><span class="sxs-lookup"><span data-stu-id="27adc-1939">**TX_READY** (0x00)</span></span>
    - <span data-ttu-id="27adc-1940">**TX_COMPLETED** (0x01)</span><span class="sxs-lookup"><span data-stu-id="27adc-1940">**TX_COMPLETED** (0x01)</span></span>
    - <span data-ttu-id="27adc-1941">**TX_TERMINATED** (0x02)</span><span class="sxs-lookup"><span data-stu-id="27adc-1941">**TX_TERMINATED** (0x02)</span></span>
    - <span data-ttu-id="27adc-1942">**TX_SUSPENDED** (0x03)</span><span class="sxs-lookup"><span data-stu-id="27adc-1942">**TX_SUSPENDED** (0x03)</span></span>
    - <span data-ttu-id="27adc-1943">**TX_SLEEP** (0x04)</span><span class="sxs-lookup"><span data-stu-id="27adc-1943">**TX_SLEEP** (0x04)</span></span>
    - <span data-ttu-id="27adc-1944">**TX_QUEUE_SUSP** (0x05)</span><span class="sxs-lookup"><span data-stu-id="27adc-1944">**TX_QUEUE_SUSP** (0x05)</span></span>
    - <span data-ttu-id="27adc-1945">**TX_SEMAPHORE_SUSP** (0x06)</span><span class="sxs-lookup"><span data-stu-id="27adc-1945">**TX_SEMAPHORE_SUSP** (0x06)</span></span>
    - <span data-ttu-id="27adc-1946">**TX_EVENT_FLAG** (0x07)</span><span class="sxs-lookup"><span data-stu-id="27adc-1946">**TX_EVENT_FLAG** (0x07)</span></span>
    - <span data-ttu-id="27adc-1947">**TX_BLOCK_MEMORY** (0x08)</span><span class="sxs-lookup"><span data-stu-id="27adc-1947">**TX_BLOCK_MEMORY** (0x08)</span></span>
    - <span data-ttu-id="27adc-1948">**TX_BYTE_MEMORY** (0x09)</span><span class="sxs-lookup"><span data-stu-id="27adc-1948">**TX_BYTE_MEMORY** (0x09)</span></span>
    - <span data-ttu-id="27adc-1949">**TX_MUTEX_SUSP** (0x0D)</span><span class="sxs-lookup"><span data-stu-id="27adc-1949">**TX_MUTEX_SUSP** (0x0D)</span></span>  

- <span data-ttu-id="27adc-1950">**run_count** — указатель на назначение для счетчика выполнения потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1950">**run_count** Pointer to destination for the thread's run count.</span></span>
- <span data-ttu-id="27adc-1951">**priority** — указатель на место назначения для приоритета потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1951">**priority** Pointer to destination for the thread's priority.</span></span>
- <span data-ttu-id="27adc-1952">**preemption_threshold** — указатель на назначение для порога вытеснения потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1952">**preemption_threshold** Pointer to destination for the thread's preemption-threshold.</span></span>
<span data-ttu-id="27adc-1953">**time_slice** — указатель на назначение для временного среза потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1953">**time_slice** Pointer to destination for the thread's time-slice.</span></span>
<span data-ttu-id="27adc-1954">**next_thread** — указатель на назначение для указателя на следующий созданный поток.</span><span class="sxs-lookup"><span data-stu-id="27adc-1954">**next_thread** Pointer to destination for next created thread pointer.</span></span>

<span data-ttu-id="27adc-1955">**suspended_thread** — указатель на назначение для указателя на следующий поток в списке приостановки.</span><span class="sxs-lookup"><span data-stu-id="27adc-1955">**suspended_thread** Pointer to destination for pointer to next thread in suspension list.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-1956">*Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-1956">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-1957">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-1957">Return Values</span></span>

- <span data-ttu-id="27adc-1958">**TX_SUCCESS** (0x00) — успешное получение сведений о потоке.</span><span class="sxs-lookup"><span data-stu-id="27adc-1958">**TX_SUCCESS** (0x00) Successful thread information retrieval.</span></span>
- <span data-ttu-id="27adc-1959">**TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="27adc-1959">**TX_THREAD_ERROR** (0x0E) Invalid thread control pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-1960">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-1960">Allowed From</span></span>

<span data-ttu-id="27adc-1961">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-1961">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-1962">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-1962">Preemption Possible</span></span>

<span data-ttu-id="27adc-1963">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-1963">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-1964">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-1964">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-1965">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-1965">See Also</span></span>

- <span data-ttu-id="27adc-1966">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27adc-1966">tx_thread_create</span></span>
- <span data-ttu-id="27adc-1967">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-1967">tx_thread_delete</span></span>
- <span data-ttu-id="27adc-1968">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1968">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27adc-1969">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27adc-1969">tx_thread_identify</span></span>
- <span data-ttu-id="27adc-1970">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1970">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27adc-1971">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1971">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-1972">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27adc-1972">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27adc-1973">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27adc-1973">tx_thread_priority_change</span></span>
- <span data-ttu-id="27adc-1974">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27adc-1974">tx_thread_relinquish</span></span>
- <span data-ttu-id="27adc-1975">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27adc-1975">tx_thread_reset</span></span>
- <span data-ttu-id="27adc-1976">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27adc-1976">tx_thread_resume</span></span>
- <span data-ttu-id="27adc-1977">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27adc-1977">tx_thread_sleep</span></span>
- <span data-ttu-id="27adc-1978">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-1978">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27adc-1979">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27adc-1979">tx_thread_suspend</span></span>
- <span data-ttu-id="27adc-1980">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27adc-1980">tx_thread_terminate</span></span>
- <span data-ttu-id="27adc-1981">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27adc-1981">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27adc-1982">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27adc-1982">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_info_get"></a><span data-ttu-id="27adc-1983">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-1983">tx_thread_performance_info_get</span></span>

<span data-ttu-id="27adc-1984">Получение сведений о производительности потока</span><span class="sxs-lookup"><span data-stu-id="27adc-1984">Get thread performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-1985">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-1985">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="27adc-1986">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-1986">Description</span></span>

<span data-ttu-id="27adc-1987">Эта служба получает сведения о производительности указанного потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1987">This service retrieves performance information about the specified thread.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-1988">*Библиотека ThreadX и приложение должны быть построены с определенным параметром* ***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _, чтобы служба могла вернуть сведения о производительности*.</span><span class="sxs-lookup"><span data-stu-id="27adc-1988">*The ThreadX library and application must be built with* ***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-1989">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-1989">Parameters</span></span>
- <span data-ttu-id="27adc-1990">**thread_ptr** — указатель на ранее созданный поток.</span><span class="sxs-lookup"><span data-stu-id="27adc-1990">**thread_ptr** Pointer to previously created thread.</span></span>
- <span data-ttu-id="27adc-1991">**resumptions** — указатель на место назначения для числа возобновлений этого потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1991">**resumptions** Pointer to destination for the number of resumptions of this thread.</span></span>
- <span data-ttu-id="27adc-1992">**suspensions** — указатель на место назначения для числа приостановок этого потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1992">**suspensions** Pointer to destination for the number of suspensions of this thread.</span></span>
- <span data-ttu-id="27adc-1993">**solicited_preemptions** — указатель на назначение для числа вытеснений в результате вызова службы API ThreadX, выполненного этим потоком.</span><span class="sxs-lookup"><span data-stu-id="27adc-1993">**solicited_preemptions** Pointer to destination for the number of preemptions as a result of a ThreadX API service call made by this thread.</span></span>
- <span data-ttu-id="27adc-1994">**interrupt_preemptions** — указатель на место назначения для количества вытеснений этого потока в результате обработки прерываний.</span><span class="sxs-lookup"><span data-stu-id="27adc-1994">**interrupt_preemptions** Pointer to destination for the number of preemptions of this thread as a result of interrupt processing.</span></span>
- <span data-ttu-id="27adc-1995">**inversions** — указатель на место назначения для числа инверсий приоритета для этого потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1995">**priority_inversions** Pointer to destination for the number of priority inversions of this thread.</span></span>
- <span data-ttu-id="27adc-1996">**time_slices** — указатель на место назначения для числа временных срезов для этого потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-1996">**time_slices** Pointer to destination for the number of time-slices of this thread.</span></span>
- <span data-ttu-id="27adc-1997">**relinquishes** — указатель на место назначения для числа освобождений потоков, выполненных этим потоком.</span><span class="sxs-lookup"><span data-stu-id="27adc-1997">**relinquishes** Pointer to destination for the number of thread relinquishes performed by this thread.</span></span>
- <span data-ttu-id="27adc-1998">**timeouts** — указатель на место назначения для количества истечений времени ожидания во время приостановки в этом потоке.</span><span class="sxs-lookup"><span data-stu-id="27adc-1998">**timeouts** Pointer to destination for the number of suspension timeouts on this thread.</span></span>
- <span data-ttu-id="27adc-1999">**wait_aborts** — указатель на место назначения для количества прерываний ожидания, выполненных в этом потоке.</span><span class="sxs-lookup"><span data-stu-id="27adc-1999">**wait_aborts** Pointer to destination for the number of wait aborts performed on this thread.</span></span>
- <span data-ttu-id="27adc-2000">**last_preempted_by** — указатель на место назначения для указателя на поток, который последним вытеснял этот поток.</span><span class="sxs-lookup"><span data-stu-id="27adc-2000">**last_preempted_by** Pointer to destination for the thread pointer that last preempted this thread.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-2001">*Указание TX_NULL для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2001">*Supplying a TX_NULL for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2002">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2002">Return Values</span></span>

- <span data-ttu-id="27adc-2003">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-2003">**TX_SUCCESS** (0x00) Successful thread performance get.</span></span>
- <span data-ttu-id="27adc-2004">**TX_PTR_ERROR** (0x03) — недопустимый указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="27adc-2004">**TX_PTR_ERROR** (0x03) Invalid thread pointer.</span></span>
- <span data-ttu-id="27adc-2005">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.</span><span class="sxs-lookup"><span data-stu-id="27adc-2005">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2006">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2006">Allowed From</span></span>

<span data-ttu-id="27adc-2007">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-2007">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2008">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2008">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-2009">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2009">See Also</span></span>

- <span data-ttu-id="27adc-2010">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2010">tx_thread_create</span></span>
- <span data-ttu-id="27adc-2011">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2011">tx_thread_delete</span></span>
- <span data-ttu-id="27adc-2012">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2012">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27adc-2013">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27adc-2013">tx_thread_identify</span></span>
- <span data-ttu-id="27adc-2014">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2014">tx_thread_info_get</span></span>
- <span data-ttu-id="27adc-2015">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2015">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-2016">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2016">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27adc-2017">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2017">tx_thread_priority_change</span></span>
- <span data-ttu-id="27adc-2018">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27adc-2018">tx_thread_relinquish</span></span>
- <span data-ttu-id="27adc-2019">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27adc-2019">tx_thread_reset</span></span>
- <span data-ttu-id="27adc-2020">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27adc-2020">tx_thread_resume</span></span>
- <span data-ttu-id="27adc-2021">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27adc-2021">tx_thread_sleep</span></span>
- <span data-ttu-id="27adc-2022">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2022">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27adc-2023">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27adc-2023">tx_thread_suspend</span></span>
- <span data-ttu-id="27adc-2024">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27adc-2024">tx_thread_terminate</span></span>
- <span data-ttu-id="27adc-2025">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2025">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27adc-2026">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27adc-2026">tx_thread_wait_abort</span></span>

## <a name="tx_thread_performance_system_info_get"></a><span data-ttu-id="27adc-2027">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2027">tx_thread_performance_system_info_get</span></span>

<span data-ttu-id="27adc-2028">Получение сведений о производительности системы потоков</span><span class="sxs-lookup"><span data-stu-id="27adc-2028">Get thread system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2029">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2029">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="27adc-2030">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2030">Description</span></span>

<span data-ttu-id="27adc-2031">Эта служба получает сведения о производительности всех потоков в системе.</span><span class="sxs-lookup"><span data-stu-id="27adc-2031">This service retrieves performance information about all the threads in the system.</span></span>

<span data-ttu-id="27adc-2032">*Библиотека ThreadX и приложение должны быть построены с определенным параметром*</span><span class="sxs-lookup"><span data-stu-id="27adc-2032">*The ThreadX library and application must be built with*</span></span>

<span data-ttu-id="27adc-2033">***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _, чтобы служба могла вернуть сведения о производительности*.</span><span class="sxs-lookup"><span data-stu-id="27adc-2033">***TX_THREAD_ENABLE_PERFORMANCE_INFO** _ _defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2034">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2034">Parameters</span></span>

- <span data-ttu-id="27adc-2035">**resumptions** — указатель на место назначения для общего числа возобновлений потоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-2035">**resumptions** Pointer to destination for the total number of thread resumptions.</span></span>
- <span data-ttu-id="27adc-2036">**suspensions** — указатель на место назначения для общего числа приостановок потоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-2036">**suspensions** Pointer to destination for the total number of thread suspensions.</span></span>
- <span data-ttu-id="27adc-2037">**solicited_preemptions** — указатель на назначение для общего числа вытеснений потоков в результате вызова потоком службы API ThreadX.</span><span class="sxs-lookup"><span data-stu-id="27adc-2037">**solicited_preemptions** Pointer to destination for the total number of thread preemptions as a result of a thread calling a ThreadX API service.</span></span>
- <span data-ttu-id="27adc-2038">**interrupt_preemptions** — указатель на место назначения для общего числа вытеснений потоков в результате обработки прерываний.</span><span class="sxs-lookup"><span data-stu-id="27adc-2038">**interrupt_preemptions** Pointer to destination for the total number of thread preemptions as a result of interrupt processing.</span></span>
- <span data-ttu-id="27adc-2039">**priority_inversions** — указатель на место назначения для общего числа инверсий приоритета потоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-2039">**priority_inversions** Pointer to destination for the total number of thread priority inversions.</span></span>
- <span data-ttu-id="27adc-2040">**time_slices** — указатель на место назначения для общего числа временных срезов потоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-2040">**time_slices** Pointer to destination for the total number of thread time-slices.</span></span>
- <span data-ttu-id="27adc-2041">**relinquishes** — указатель на место назначения для общего числа освобождений потоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-2041">**relinquishes** Pointer to destination for the total number of thread relinquishes.</span></span>
- <span data-ttu-id="27adc-2042">**timeouts** — указатель на место назначения для общего количества истечений времени ожидания во время приостановки потоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-2042">**timeouts** Pointer to destination for the total number of thread suspension timeouts.</span></span>
- <span data-ttu-id="27adc-2043">**wait_aborts** — указатель на место назначения для общего количества прерываний ожидания потоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-2043">**wait_aborts** Pointer to destination for the total number of thread wait aborts.</span></span>
- <span data-ttu-id="27adc-2044">**non_idle_returns** — указатель на место назначения, указывающее, сколько раз поток возвращался в систему, когда другой поток был готов к выполнению.</span><span class="sxs-lookup"><span data-stu-id="27adc-2044">**non_idle_returns** Pointer to destination for the number of times a thread returns to the system when another thread is ready to execute.</span></span>
- <span data-ttu-id="27adc-2045">**idle_returns** — указатель на место назначения, указывающее, сколько раз поток возвращался в систему, когда не было других потоков, готовых к выполнению (простаивающая система).</span><span class="sxs-lookup"><span data-stu-id="27adc-2045">**idle_returns** Pointer to destination for the number of times a thread returns to the system when no other thread is ready to execute (idle system).</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-2046">*Указание **TX_NULL** для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2046">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2047">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2047">Return Values</span></span>

- <span data-ttu-id="27adc-2048">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности системы потоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-2048">**TX_SUCCESS** (0x00) Successful thread system performance get.</span></span>
- <span data-ttu-id="27adc-2049">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.</span><span class="sxs-lookup"><span data-stu-id="27adc-2049">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2050">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2050">Allowed From</span></span>

<span data-ttu-id="27adc-2051">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-2051">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2052">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2052">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-2053">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2053">See Also</span></span>

- <span data-ttu-id="27adc-2054">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2054">tx_thread_create</span></span>
- <span data-ttu-id="27adc-2055">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2055">tx_thread_delete</span></span>
- <span data-ttu-id="27adc-2056">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2056">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27adc-2057">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27adc-2057">tx_thread_identify</span></span>
- <span data-ttu-id="27adc-2058">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2058">tx_thread_info_get</span></span>
- <span data-ttu-id="27adc-2059">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2059">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27adc-2060">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2060">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27adc-2061">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2061">tx_thread_priority_change</span></span>
- <span data-ttu-id="27adc-2062">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27adc-2062">tx_thread_relinquish</span></span>
- <span data-ttu-id="27adc-2063">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27adc-2063">tx_thread_reset</span></span>
- <span data-ttu-id="27adc-2064">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27adc-2064">tx_thread_resume</span></span>
- <span data-ttu-id="27adc-2065">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27adc-2065">tx_thread_sleep</span></span>
- <span data-ttu-id="27adc-2066">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2066">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27adc-2067">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27adc-2067">tx_thread_suspend</span></span>
- <span data-ttu-id="27adc-2068">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27adc-2068">tx_thread_terminate</span></span>
- <span data-ttu-id="27adc-2069">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2069">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27adc-2070">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27adc-2070">tx_thread_wait_abort</span></span>

## <a name="tx_thread_preemption_change"></a><span data-ttu-id="27adc-2071">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2071">tx_thread_preemption_change</span></span>

<span data-ttu-id="27adc-2072">Изменение порога вытеснения для потока приложения</span><span class="sxs-lookup"><span data-stu-id="27adc-2072">Change preemption-threshold of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2073">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2073">Prototype</span></span>

```c
UINT tx_thread_preemption_change(
    TX_THREAD *thread_ptr,
    UINT new_threshold, 
    UINT *old_threshold);
```

### <a name="description"></a><span data-ttu-id="27adc-2074">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2074">Description</span></span>

<span data-ttu-id="27adc-2075">Эта служба изменяет порог вытеснения указанного потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-2075">This service changes the preemption-threshold of the specified thread.</span></span> <span data-ttu-id="27adc-2076">Порог вытеснения предотвращает вытеснение указанного потока потоками с приоритетом равным или меньшим значения порога вытеснения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2076">The preemption-threshold prevents preemption of the specified thread by threads equal to or less than the preemption-threshold value.</span></span>

>[!NOTE]
> <span data-ttu-id="27adc-2077">*При использовании порога вытеснения отключаются временные срезы для указанного потока.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2077">*Using preemption-threshold disables time-slicing for the specified thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2078">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2078">Parameters</span></span>
- <span data-ttu-id="27adc-2079">**thread_ptr** — указатель на ранее созданный поток приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2079">**thread_ptr** Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="27adc-2080">**new_threshold** — новый уровень приоритета для порога вытеснения (от 0 до (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="27adc-2080">**new_threshold** New preemption-threshold priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="27adc-2081">**old_threshold** — указатель на расположение для возврата предыдущего значения порога вытеснения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2081">**old_threshold** Pointer to a location to return the previous preemption-threshold.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2082">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2082">Return Values</span></span>

- <span data-ttu-id="27adc-2083">**TX_SUCCESS** (0x00) — успешное изменение порога вытеснения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2083">**TX_SUCCESS** (0x00) Successful preemption-threshold change.</span></span>
- <span data-ttu-id="27adc-2084">**TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2084">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="27adc-2085">**TX_THRESH_ERROR** (0x18) — указанный новый приоритет вытеснения либо не является допустимым приоритетом потока (значение вне диапазона от 0 до (**TX_MAX_PRIORITIES**-1)), либо больше (низкий приоритет), чем текущее значение приоритета потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-2085">**TX_THRESH_ERROR** (0x18) Specified new preemption-threshold is not a valid thread priority (a value other than (0 through (**TX_MAX_PRIORITIES**-1)) or is greater than (lower priority) than the current thread priority.</span></span>
- <span data-ttu-id="27adc-2086">**TX_PTR_ERROR** (0x03) — недопустимый указатель на расположение для хранения предыдущего значения порога вытеснения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2086">**TX_PTR_ERROR** (0x03) Invalid pointer to previous preemptionthreshold storage location.</span></span>
- <span data-ttu-id="27adc-2087">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-2087">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2088">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2088">Allowed From</span></span>

<span data-ttu-id="27adc-2089">Потоки и таймеры</span><span class="sxs-lookup"><span data-stu-id="27adc-2089">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-2090">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-2090">Preemption Possible</span></span>

<span data-ttu-id="27adc-2091">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-2091">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2092">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2092">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-2093">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2093">See Also</span></span>

- <span data-ttu-id="27adc-2094">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2094">tx_thread_create</span></span>
- <span data-ttu-id="27adc-2095">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2095">tx_thread_delete</span></span>
- <span data-ttu-id="27adc-2096">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2096">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27adc-2097">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27adc-2097">tx_thread_identify</span></span>
- <span data-ttu-id="27adc-2098">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2098">tx_thread_info_get</span></span>
- <span data-ttu-id="27adc-2099">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2099">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27adc-2100">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2100">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-2101">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2101">tx_thread_priority_change</span></span>
- <span data-ttu-id="27adc-2102">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27adc-2102">tx_thread_relinquish</span></span>
- <span data-ttu-id="27adc-2103">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27adc-2103">tx_thread_reset</span></span>
- <span data-ttu-id="27adc-2104">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27adc-2104">tx_thread_resume</span></span>
- <span data-ttu-id="27adc-2105">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27adc-2105">tx_thread_sleep</span></span>
- <span data-ttu-id="27adc-2106">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2106">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27adc-2107">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27adc-2107">tx_thread_suspend</span></span>
- <span data-ttu-id="27adc-2108">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27adc-2108">tx_thread_terminate</span></span>
- <span data-ttu-id="27adc-2109">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2109">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27adc-2110">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27adc-2110">tx_thread_wait_abort</span></span>

## <a name="tx_thread_priority_change"></a><span data-ttu-id="27adc-2111">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2111">tx_thread_priority_change</span></span>

<span data-ttu-id="27adc-2112">Изменение приоритета потока приложения</span><span class="sxs-lookup"><span data-stu-id="27adc-2112">Change priority of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2113">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2113">Prototype</span></span>

```c
UINT tx_thread_priority_change(
    TX_THREAD *thread_ptr,
    UINT new_priority, 
    UINT *old_priority);
```

### <a name="description"></a><span data-ttu-id="27adc-2114">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2114">Description</span></span>

<span data-ttu-id="27adc-2115">Эта служба изменяет приоритет указанного потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-2115">This service changes the priority of the specified thread.</span></span> <span data-ttu-id="27adc-2116">Допустимые значения находятся в диапазоне от 0 до (TX_MAX_PRIORITES-1), где значение 0 соответствует наивысшему приоритету.</span><span class="sxs-lookup"><span data-stu-id="27adc-2116">Valid priorities range from 0 through (TX_MAX_PRIORITES-1), where 0 represents the highest priority level.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-2117">\* Порог вытеснения указанного потока автоматически устанавливается в соответствии с новым приоритетом.</span><span class="sxs-lookup"><span data-stu-id="27adc-2117">\*The preemption-threshold of the specified thread is automatically set to the new priority.</span></span> <span data-ttu-id="27adc-2118">Если требуется установить новое пороговое значение, после вызова этой службы необходимо вызвать службу \***tx_thread_preemption_change** _._</span><span class="sxs-lookup"><span data-stu-id="27adc-2118">If a new threshold is desired, the \***tx_thread_preemption_change** _ service must be used after this call._</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2119">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2119">Parameters</span></span>

- <span data-ttu-id="27adc-2120">**thread_ptr** — указатель на ранее созданный поток приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2120">**thread_ptr** Pointer to a previously created application thread.</span></span>
- <span data-ttu-id="27adc-2121">**new_priority** — новый уровень приоритета потока (от 0 до (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="27adc-2121">**new_priority** New thread priority level (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="27adc-2122">**old_priority** — указатель на расположение для возврата предыдущего приоритета потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-2122">**old_priority** Pointer to a location to return the thread's previous priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2123">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2123">Return Values</span></span>

- <span data-ttu-id="27adc-2124">**TX_SUCCESS** (0x00) — успешное изменение приоритета.</span><span class="sxs-lookup"><span data-stu-id="27adc-2124">**TX_SUCCESS** (0x00) Successful priority change.</span></span>
- <span data-ttu-id="27adc-2125">**TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2125">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="27adc-2126">**TX_PRIORITY_ERROR** (0x0F) указан недопустимый новый приоритет (значение вне диапазона от 0 до (TX_MAX_PRIORITIES-1)).</span><span class="sxs-lookup"><span data-stu-id="27adc-2126">**TX_PRIORITY_ERROR** (0x0F) Specified new priority is not valid (a value other than (0 through (TX_MAX_PRIORITIES-1)).</span></span>
- <span data-ttu-id="27adc-2127">**TX_PTR_ERROR** (0x03) — недопустимый указатель на расположение для хранения предыдущего значения приоритета.</span><span class="sxs-lookup"><span data-stu-id="27adc-2127">**TX_PTR_ERROR** (0x03) Invalid pointer to previous priority storage location.</span></span>
- <span data-ttu-id="27adc-2128">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-2128">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2129">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2129">Allowed From</span></span>

<span data-ttu-id="27adc-2130">Потоки и таймеры</span><span class="sxs-lookup"><span data-stu-id="27adc-2130">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-2131">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-2131">Preemption Possible</span></span>

<span data-ttu-id="27adc-2132">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-2132">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2133">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2133">Example</span></span>

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
### <a name="see-also"></a><span data-ttu-id="27adc-2134">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2134">See Also</span></span>

- <span data-ttu-id="27adc-2135">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2135">tx_thread_create</span></span>
- <span data-ttu-id="27adc-2136">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2136">tx_thread_delete</span></span>
- <span data-ttu-id="27adc-2137">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2137">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27adc-2138">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27adc-2138">tx_thread_identify</span></span>
- <span data-ttu-id="27adc-2139">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2139">tx_thread_info_get</span></span>
- <span data-ttu-id="27adc-2140">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2140">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27adc-2141">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2141">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-2142">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2142">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27adc-2143">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27adc-2143">tx_thread_relinquish</span></span>
- <span data-ttu-id="27adc-2144">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27adc-2144">tx_thread_reset</span></span>
- <span data-ttu-id="27adc-2145">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27adc-2145">tx_thread_resume</span></span>
- <span data-ttu-id="27adc-2146">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27adc-2146">tx_thread_sleep</span></span>
- <span data-ttu-id="27adc-2147">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2147">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27adc-2148">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27adc-2148">tx_thread_suspend</span></span>
- <span data-ttu-id="27adc-2149">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27adc-2149">tx_thread_terminate</span></span>
- <span data-ttu-id="27adc-2150">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2150">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27adc-2151">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27adc-2151">tx_thread_wait_abort</span></span>

## <a name="tx_thread_relinquish"></a><span data-ttu-id="27adc-2152">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27adc-2152">tx_thread_relinquish</span></span>

<span data-ttu-id="27adc-2153">Передача управления другим потокам приложений</span><span class="sxs-lookup"><span data-stu-id="27adc-2153">Relinquish control to other application threads</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2154">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2154">Prototype</span></span>

```c
VOID tx_thread_relinquish(VOID);
```

### <a name="description"></a><span data-ttu-id="27adc-2155">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2155">Description</span></span>

<span data-ttu-id="27adc-2156">Эта служба передает управление процессором другим готовым к запуску потокам с таким же или более высоким приоритетом.</span><span class="sxs-lookup"><span data-stu-id="27adc-2156">This service relinquishes processor control to other ready-to-run threads at the same or higher priority.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-2157">*Помимо передачи управления потоками с таким же приоритетом, эта служба также передает управление потоку с наивысшим приоритетом, выполнение которого запрещено из-за настройки порога вытеснения текущего потока.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2157">*In addition to relinquishing control to threads of the same priority, this service also relinquishes control to the highest-priority thread prevented from execution because of the current thread's preemption-threshold setting.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2158">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2158">Parameters</span></span>

<span data-ttu-id="27adc-2159">None</span><span class="sxs-lookup"><span data-stu-id="27adc-2159">None</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2160">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2160">Return Values</span></span>

<span data-ttu-id="27adc-2161">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-2161">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2162">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2162">Allowed From</span></span>

<span data-ttu-id="27adc-2163">Потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-2163">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-2164">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-2164">Preemption Possible</span></span>

<span data-ttu-id="27adc-2165">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-2165">Yes</span></span>

### <a name="examples"></a><span data-ttu-id="27adc-2166">Примеры</span><span class="sxs-lookup"><span data-stu-id="27adc-2166">Examples</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-2167">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2167">See Also</span></span>

- <span data-ttu-id="27adc-2168">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2168">tx_thread_create</span></span>
- <span data-ttu-id="27adc-2169">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2169">tx_thread_delete</span></span>
- <span data-ttu-id="27adc-2170">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2170">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27adc-2171">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27adc-2171">tx_thread_identify</span></span>
- <span data-ttu-id="27adc-2172">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2172">tx_thread_info_get</span></span>
- <span data-ttu-id="27adc-2173">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2173">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27adc-2174">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2174">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-2175">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2175">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27adc-2176">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2176">tx_thread_priority_change</span></span>
- <span data-ttu-id="27adc-2177">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27adc-2177">tx_thread_reset</span></span>
- <span data-ttu-id="27adc-2178">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27adc-2178">tx_thread_resume</span></span>
- <span data-ttu-id="27adc-2179">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27adc-2179">tx_thread_sleep</span></span>
- <span data-ttu-id="27adc-2180">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2180">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27adc-2181">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27adc-2181">tx_thread_suspend</span></span>
- <span data-ttu-id="27adc-2182">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27adc-2182">tx_thread_terminate</span></span>
- <span data-ttu-id="27adc-2183">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2183">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27adc-2184">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27adc-2184">tx_thread_wait_abort</span></span>

## <a name="tx_thread_reset"></a><span data-ttu-id="27adc-2185">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27adc-2185">tx_thread_reset</span></span>

<span data-ttu-id="27adc-2186">Сброс потока</span><span class="sxs-lookup"><span data-stu-id="27adc-2186">Reset thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2187">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2187">Prototype</span></span>

```c
UINT tx_thread_reset(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-2188">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2188">Description</span></span>

<span data-ttu-id="27adc-2189">Эта служба сбрасывает указанный поток для выполнения в точке входа, определенной при создании потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-2189">This service resets the specified thread to execute at the entry point defined at thread creation.</span></span> <span data-ttu-id="27adc-2190">Для выполнения сброса поток должен находиться либо в состоянии **TX_COMPLETED**, либо в состоянии **TX_TERMINATED**.</span><span class="sxs-lookup"><span data-stu-id="27adc-2190">The thread must be in either a **TX_COMPLETED** or **TX_TERMINATED** state for it to be reset</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-2191">*Для повторного выполнения поток необходимо возобновить.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2191">*The thread must be resumed for it to execute again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2192">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2192">Parameters</span></span>

- <span data-ttu-id="27adc-2193">**thread_ptr** — указатель на ранее созданный поток.</span><span class="sxs-lookup"><span data-stu-id="27adc-2193">**thread_ptr** Pointer to a previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2194">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2194">Return Values</span></span>

- <span data-ttu-id="27adc-2195">**TX_SUCCESS** (0x00) — успешный сброс потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-2195">**TX_SUCCESS** (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="27adc-2196">**TX_NOT_DONE** (0x20) — указанный поток не находится в состоянии **TX_COMPLETED** или **TX_TERMINATED**.</span><span class="sxs-lookup"><span data-stu-id="27adc-2196">**TX_NOT_DONE** (0x20) Specified thread is not in a **TX_COMPLETED** or **TX_TERMINATED** state.</span></span>
- <span data-ttu-id="27adc-2197">**TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток.</span><span class="sxs-lookup"><span data-stu-id="27adc-2197">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>
- <span data-ttu-id="27adc-2198">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-2198">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2199">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2199">Allowed From</span></span>

<span data-ttu-id="27adc-2200">Потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-2200">Threads</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2201">Например, .</span><span class="sxs-lookup"><span data-stu-id="27adc-2201">Example</span></span>

<span data-ttu-id="27adc-2202">TX_THREAD my_thread;</span><span class="sxs-lookup"><span data-stu-id="27adc-2202">TX_THREAD my_thread;</span></span>

```c
TX_THREAD my_thread;

/* Reset the previously created thread "my_thread." */

status = tx_thread_reset(&my_thread);

/* If status is TX_SUCCESS the thread is reset. */
```

### <a name="see-also"></a><span data-ttu-id="27adc-2203">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2203">See Also</span></span>

- <span data-ttu-id="27adc-2204">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2204">tx_thread_create</span></span>
- <span data-ttu-id="27adc-2205">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2205">tx_thread_delete</span></span>
- <span data-ttu-id="27adc-2206">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2206">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27adc-2207">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27adc-2207">tx_thread_identify</span></span>
- <span data-ttu-id="27adc-2208">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2208">tx_thread_info_get</span></span>
- <span data-ttu-id="27adc-2209">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2209">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27adc-2210">tx_thread_preformance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2210">tx_thread_preformance_system_info_get</span></span>
- <span data-ttu-id="27adc-2211">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2211">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27adc-2212">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2212">tx_thread_priority_change</span></span>
- <span data-ttu-id="27adc-2213">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27adc-2213">tx_thread_relinquish</span></span>
- <span data-ttu-id="27adc-2214">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27adc-2214">tx_thread_resume</span></span>
- <span data-ttu-id="27adc-2215">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27adc-2215">tx_thread_sleep</span></span>
- <span data-ttu-id="27adc-2216">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2216">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27adc-2217">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27adc-2217">tx_thread_suspend</span></span>
- <span data-ttu-id="27adc-2218">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27adc-2218">tx_thread_terminate</span></span>
- <span data-ttu-id="27adc-2219">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2219">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27adc-2220">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27adc-2220">tx_thread_wait_abort</span></span>

## <a name="tx_thread_resume"></a><span data-ttu-id="27adc-2221">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27adc-2221">tx_thread_resume</span></span>

<span data-ttu-id="27adc-2222">Возобновление приостановленного потока приложения</span><span class="sxs-lookup"><span data-stu-id="27adc-2222">Resume suspended application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2223">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2223">Prototype</span></span>

```c
UINT tx_thread_resume(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-2224">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2224">Description</span></span>

<span data-ttu-id="27adc-2225">Эта служба возобновляет или готовит к выполнению поток, который ранее был приостановлен вызовом ***tx_thread_suspend***.</span><span class="sxs-lookup"><span data-stu-id="27adc-2225">This service resumes or prepares for execution a thread that was previously suspended by a ***tx_thread_suspend*** call.</span></span> <span data-ttu-id="27adc-2226">Кроме того, эта служба возобновляет потоки, созданные без автоматического запуска.</span><span class="sxs-lookup"><span data-stu-id="27adc-2226">In addition, this service resumes threads that were created without an automatic start.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2227">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2227">Parameters</span></span>

- <span data-ttu-id="27adc-2228">**thread_ptr** — указатель на приостановленный поток приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2228">**thread_ptr** Pointer to a suspended application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2229">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2229">Return Values</span></span>

- <span data-ttu-id="27adc-2230">**TX_SUCCESS** (0x00) — успешное возобновление потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-2230">**TX_SUCCESS** (0x00) Successful thread resume.</span></span>
- <span data-ttu-id="27adc-2231">**TX_SUSPEND_LIFTED** (0x19) — ранее установленная отсроченная приостановка была снята.</span><span class="sxs-lookup"><span data-stu-id="27adc-2231">**TX_SUSPEND_LIFTED** (0x19) Previously set delayed suspension was lifted.</span></span>
- <span data-ttu-id="27adc-2232">**TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2232">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="27adc-2233">**TX_RESUME_ERROR** (0x12) — указанный поток не приостановлен или приостановлен службой, отличной от **_tx_thread_suspend_**.</span><span class="sxs-lookup"><span data-stu-id="27adc-2233">**TX_RESUME_ERROR** (0x12) Specified thread is not suspended or was previously suspended by a service other than **_tx_thread_suspend_**.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2234">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2234">Allowed From</span></span>

<span data-ttu-id="27adc-2235">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-2235">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-2236">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-2236">Preemption Possible</span></span>

<span data-ttu-id="27adc-2237">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-2237">Yes</span></span>

<span data-ttu-id="27adc-2238">TX_THREAD my_thread;</span><span class="sxs-lookup"><span data-stu-id="27adc-2238">TX_THREAD my_thread;</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2239">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2239">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Resume the thread represented by "my_thread". */
status = tx_thread_resume(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
now ready to execute. */
```

### <a name="see-also"></a><span data-ttu-id="27adc-2240">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2240">See Also</span></span>

- <span data-ttu-id="27adc-2241">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2241">tx_thread_create</span></span>
- <span data-ttu-id="27adc-2242">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2242">tx_thread_delete</span></span>
- <span data-ttu-id="27adc-2243">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2243">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27adc-2244">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27adc-2244">tx_thread_identify</span></span>
- <span data-ttu-id="27adc-2245">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2245">tx_thread_info_get</span></span>
- <span data-ttu-id="27adc-2246">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2246">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27adc-2247">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2247">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-2248">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2248">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27adc-2249">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2249">tx_thread_priority_change</span></span>
- <span data-ttu-id="27adc-2250">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27adc-2250">tx_thread_relinquish</span></span>
- <span data-ttu-id="27adc-2251">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27adc-2251">tx_thread_reset</span></span>
- <span data-ttu-id="27adc-2252">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27adc-2252">tx_thread_sleep</span></span>
- <span data-ttu-id="27adc-2253">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2253">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27adc-2254">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27adc-2254">tx_thread_suspend</span></span>
- <span data-ttu-id="27adc-2255">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27adc-2255">tx_thread_terminate</span></span>
- <span data-ttu-id="27adc-2256">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2256">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27adc-2257">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27adc-2257">tx_thread_wait_abort</span></span>

## <a name="tx_thread_sleep"></a><span data-ttu-id="27adc-2258">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27adc-2258">tx_thread_sleep</span></span>

<span data-ttu-id="27adc-2259">Приостановка текущего потока на указанное время</span><span class="sxs-lookup"><span data-stu-id="27adc-2259">Suspend current thread for specified time</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2260">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2260">Prototype</span></span>

```c
UINT tx_thread_sleep(ULONG timer_ticks);
```

### <a name="description"></a><span data-ttu-id="27adc-2261">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2261">Description</span></span>

<span data-ttu-id="27adc-2262">Эта служба приводит к приостановке вызывающего потока на указанное число тактов таймера.</span><span class="sxs-lookup"><span data-stu-id="27adc-2262">This service causes the calling thread to suspend for the specified number of timer ticks.</span></span> <span data-ttu-id="27adc-2263">Количество физического времени, связанное с тактом таймера, зависит от приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2263">The amount of physical time associated with a timer tick is application specific.</span></span> <span data-ttu-id="27adc-2264">Эту службу можно вызывать только из потока приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2264">This service can be called only from an application thread.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2265">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2265">Parameters</span></span>

- <span data-ttu-id="27adc-2266">**timer_ticks** — число тактов таймера для приостановки вызывающего потока приложения в диапазоне от 0 до 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="27adc-2266">**timer_ticks** The number of timer ticks to suspend the calling application thread, ranging from 0 through 0xFFFFFFFF.</span></span> <span data-ttu-id="27adc-2267">Если указано значение 0, служба завершает работу немедленно.</span><span class="sxs-lookup"><span data-stu-id="27adc-2267">If 0 is specified, the service returns immediately.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2268">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2268">Return Values</span></span>

- <span data-ttu-id="27adc-2269">**TX_SUCCESS** (0x00) — успешная приостановка работы потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-2269">**TX_SUCCESS** (0x00) Successful thread sleep.</span></span>
- <span data-ttu-id="27adc-2270">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="27adc-2270">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="27adc-2271">**TX_CALLER_ERROR** (0x13) — служба вызывается из непотока.</span><span class="sxs-lookup"><span data-stu-id="27adc-2271">**TX_CALLER_ERROR** (0x13) Service called from a non-thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2272">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2272">Allowed From</span></span>

<span data-ttu-id="27adc-2273">Потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-2273">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-2274">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-2274">Preemption Possible</span></span>

<span data-ttu-id="27adc-2275">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-2275">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2276">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2276">Example</span></span>

```c
UINT status;

/* Make the calling thread sleep for 100
timer-ticks. */
status = tx_thread_sleep(100);

/* If status equals TX_SUCCESS, the currently running
application thread slept for the specified number of
timer-ticks. */
```

### <a name="see-also"></a><span data-ttu-id="27adc-2277">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2277">See Also</span></span>

- <span data-ttu-id="27adc-2278">tx_thread_create, tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2278">tx_thread_create, tx_thread_delete</span></span>
- <span data-ttu-id="27adc-2279">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2279">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27adc-2280">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27adc-2280">tx_thread_identify</span></span>
- <span data-ttu-id="27adc-2281">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2281">tx_thread_info_get</span></span>
- <span data-ttu-id="27adc-2282">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2282">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27adc-2283">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2283">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-2284">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2284">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27adc-2285">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2285">tx_thread_priority_change</span></span>
- <span data-ttu-id="27adc-2286">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27adc-2286">tx_thread_relinquish</span></span>
- <span data-ttu-id="27adc-2287">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27adc-2287">tx_thread_reset</span></span>
- <span data-ttu-id="27adc-2288">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27adc-2288">tx_thread_resume</span></span>
- <span data-ttu-id="27adc-2289">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2289">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27adc-2290">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27adc-2290">tx_thread_suspend</span></span>
- <span data-ttu-id="27adc-2291">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27adc-2291">tx_thread_terminate</span></span>
- <span data-ttu-id="27adc-2292">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2292">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27adc-2293">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27adc-2293">tx_thread_wait_abort</span></span>

## <a name="tx_thread_stack_error_notify"></a><span data-ttu-id="27adc-2294">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2294">tx_thread_stack_error_notify</span></span>

<span data-ttu-id="27adc-2295">Регистрация обратного вызова уведомления об ошибках стека потока</span><span class="sxs-lookup"><span data-stu-id="27adc-2295">Register thread stack error notification callback</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2296">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2296">Prototype</span></span>

```c
UINT tx_thread_stack_error_notify(VOID (*error_handler)(TX_THREAD *));
```

### <a name="description"></a><span data-ttu-id="27adc-2297">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2297">Description</span></span>

<span data-ttu-id="27adc-2298">Эта служба регистрирует функцию обратного вызова уведомлений для обработки ошибок стека потоков.</span><span class="sxs-lookup"><span data-stu-id="27adc-2298">This service registers a notification callback function for handling thread stack errors.</span></span> <span data-ttu-id="27adc-2299">Когда ThreadX обнаруживает ошибку стека потока во время выполнения, он вызывает эту функцию уведомления для обработки ошибки.</span><span class="sxs-lookup"><span data-stu-id="27adc-2299">When ThreadX detects a thread stack error during execution, it will call this notification function to process the error.</span></span> <span data-ttu-id="27adc-2300">Порядок обработки ошибки полностью определяется приложением.</span><span class="sxs-lookup"><span data-stu-id="27adc-2300">Processing of the error is completely defined by the application.</span></span> <span data-ttu-id="27adc-2301">Может быть выполнено все, что угодно: от приостановки нарушающего потока до перезагрузки всей системы.</span><span class="sxs-lookup"><span data-stu-id="27adc-2301">Anything from suspending the violating thread to resetting the entire system may be done.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-2302">*Библиотека ThreadX должна быть построена с определенным параметром* **TX_ENABLE_STACK_CHECKING** *, чтобы служба могла вернуть сведения о производительности.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2302">*The ThreadX library must be built with* **TX_ENABLE_STACK_CHECKING** *defined in order for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2303">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2303">Parameters</span></span>
- <span data-ttu-id="27adc-2304">**error_handler** — указатель на функцию обработки ошибок стека приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2304">**error_handler** Pointer to application's stack error handling function.</span></span> <span data-ttu-id="27adc-2305">Если это значение равно TX_NULL, уведомление отключено.</span><span class="sxs-lookup"><span data-stu-id="27adc-2305">If this value is TX_NULL, the notification is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2306">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2306">Return Values</span></span>

- <span data-ttu-id="27adc-2307">**TX_SUCCESS** (0x00) — успешный сброс потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-2307">**TX_SUCCESS** (0x00) Successful thread reset.</span></span>
- <span data-ttu-id="27adc-2308">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.</span><span class="sxs-lookup"><span data-stu-id="27adc-2308">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2309">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2309">Allowed From</span></span>

<span data-ttu-id="27adc-2310">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-2310">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2311">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2311">Example</span></span>

```c
void my_stack_error_handler(TX_THREAD *thread_ptr);

/* Register the "my_stack_error_handler" function with ThreadX
so that thread stack errors can be handled by the application. */
status = tx_thread_stack_error_notify(my_stack_error_handler);

/* If status is TX_SUCCESS the stack error handler is registered.*/
```

### <a name="see-also"></a><span data-ttu-id="27adc-2312">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2312">See Also</span></span>

- <span data-ttu-id="27adc-2313">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2313">tx_thread_create</span></span>
- <span data-ttu-id="27adc-2314">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2314">tx_thread_delete</span></span>
- <span data-ttu-id="27adc-2315">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2315">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27adc-2316">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27adc-2316">tx_thread_identify</span></span>
- <span data-ttu-id="27adc-2317">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2317">tx_thread_info_get</span></span>
- <span data-ttu-id="27adc-2318">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2318">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27adc-2319">tx_thread_preformance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2319">tx_thread_preformance_system_info_get</span></span>
- <span data-ttu-id="27adc-2320">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2320">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27adc-2321">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2321">tx_thread_priority_change</span></span>
- <span data-ttu-id="27adc-2322">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27adc-2322">tx_thread_relinquish</span></span>
- <span data-ttu-id="27adc-2323">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27adc-2323">tx_thread_reset</span></span>
- <span data-ttu-id="27adc-2324">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27adc-2324">tx_thread_resume</span></span>
- <span data-ttu-id="27adc-2325">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27adc-2325">tx_thread_sleep</span></span>
- <span data-ttu-id="27adc-2326">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27adc-2326">tx_thread_suspend</span></span>
- <span data-ttu-id="27adc-2327">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27adc-2327">tx_thread_terminate</span></span>
- <span data-ttu-id="27adc-2328">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2328">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27adc-2329">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27adc-2329">tx_thread_wait_abort</span></span>

## <a name="tx_thread_suspend"></a><span data-ttu-id="27adc-2330">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27adc-2330">tx_thread_suspend</span></span>

<span data-ttu-id="27adc-2331">Приостановка потока приложения</span><span class="sxs-lookup"><span data-stu-id="27adc-2331">Suspend application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2332">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2332">Prototype</span></span>

```c
UINT tx_thread_suspend(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-2333">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2333">Description</span></span>

<span data-ttu-id="27adc-2334">Эта служба приостанавливает указанный поток приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2334">This service suspends the specified application thread.</span></span> <span data-ttu-id="27adc-2335">Поток может вызывать эту службу для приостановки самого себя.</span><span class="sxs-lookup"><span data-stu-id="27adc-2335">A thread may call this service to suspend itself.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-2336">*Если указанный поток уже приостановлен по другой причине, эта приостановка сохраняется до тех пор, пока предыдущая приостановка не будет снята. Когда это случится, выполняется безусловная приостановка указанного потока. Дальнейшие запросы на безусловную приостановку не будут иметь силы.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2336">*If the specified thread is already suspended for another reason, this suspension is held internally until the prior suspension is lifted. When that happens, this unconditional suspension of the specified thread is performed. Further unconditional suspension requests have no effect.*</span></span>

<span data-ttu-id="27adc-2337">После приостановки поток должен быть возобновлен с помощью ***tx_thread_resume*** для продолжения выполнения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2337">After being suspended, the thread must be resumed by ***tx_thread_resume*** to execute again.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2338">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2338">Parameters</span></span>

- <span data-ttu-id="27adc-2339">**thread_ptr** — указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2339">**thread_ptr** Pointer to an application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2340">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2340">Return Values</span></span>

- <span data-ttu-id="27adc-2341">**TX_SUCCESS** (0x00) — успешная приостановка потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-2341">**TX_SUCCESS** (0x00) Successful thread suspend.</span></span>
- <span data-ttu-id="27adc-2342">**TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2342">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="27adc-2343">**TX_SUSPEND_ERROR** (0x14) — указанный поток находится в состоянии TERMINATED или COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="27adc-2343">**TX_SUSPEND_ERROR** (0x14) Specified thread is in a terminated or completed state.</span></span>
- <span data-ttu-id="27adc-2344">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-2344">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2345">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2345">Allowed From</span></span>

<span data-ttu-id="27adc-2346">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-2346">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-2347">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-2347">Preemption Possible</span></span>

<span data-ttu-id="27adc-2348">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-2348">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2349">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2349">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Suspend the thread represented by "my_thread". */
status = tx_thread_suspend(&my_thread);

/* If status equals TX_SUCCESS, the application thread is
unconditionally suspended. */
```

### <a name="see-also"></a><span data-ttu-id="27adc-2350">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2350">See Also</span></span>

- <span data-ttu-id="27adc-2351">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2351">tx_thread_create</span></span>
- <span data-ttu-id="27adc-2352">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2352">tx_thread_delete</span></span>
- <span data-ttu-id="27adc-2353">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2353">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27adc-2354">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27adc-2354">tx_thread_identify</span></span>
- <span data-ttu-id="27adc-2355">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2355">tx_thread_info_get</span></span>
- <span data-ttu-id="27adc-2356">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2356">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27adc-2357">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2357">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-2358">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2358">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27adc-2359">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2359">tx_thread_priority_change</span></span>
- <span data-ttu-id="27adc-2360">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27adc-2360">tx_thread_relinquish</span></span>
- <span data-ttu-id="27adc-2361">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27adc-2361">tx_thread_reset</span></span>
- <span data-ttu-id="27adc-2362">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27adc-2362">tx_thread_resume</span></span>
- <span data-ttu-id="27adc-2363">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27adc-2363">tx_thread_sleep</span></span>
- <span data-ttu-id="27adc-2364">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2364">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27adc-2365">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27adc-2365">tx_thread_terminate</span></span>
- <span data-ttu-id="27adc-2366">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2366">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27adc-2367">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27adc-2367">tx_thread_wait_abort</span></span>

## <a name="tx_thread_terminate"></a><span data-ttu-id="27adc-2368">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27adc-2368">tx_thread_terminate</span></span>

<span data-ttu-id="27adc-2369">Завершение потока приложения</span><span class="sxs-lookup"><span data-stu-id="27adc-2369">Terminates application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2370">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2370">Prototype</span></span>

```c
UINT tx_thread_terminate(TX_THREAD *thread_ptr);
```
### <a name="description"></a><span data-ttu-id="27adc-2371">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2371">Description</span></span>

<span data-ttu-id="27adc-2372">Эта служба завершает указанный поток приложения независимо от того, приостановлен ли поток.</span><span class="sxs-lookup"><span data-stu-id="27adc-2372">This service terminates the specified application thread regardless of whether the thread is suspended or not.</span></span> <span data-ttu-id="27adc-2373">Поток может вызывать эту службу для завершения самого себя.</span><span class="sxs-lookup"><span data-stu-id="27adc-2373">A thread may call this service to terminate itself.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-2374">*Ответственность за то, что поток находится в состоянии, подходящем для завершения, лежит на приложении. Например, поток не должен завершаться во время выполнения критической обработки приложения или внутри других компонентов промежуточного слоя, где он может оставить такую обработку в неизвестном состоянии.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2374">*It is the application's responsibility to ensure that the thread is in a state suitable for termination. For example, a thread should not be terminated during critical application processing or inside of other middleware components where it could leave such processing in an unknown state.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-2375">*После завершения работы поток должен быть сброшен для его повторного выполнения.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2375">*After being terminated, the thread must be reset for it to execute again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2376">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2376">Parameters</span></span>

- <span data-ttu-id="27adc-2377">**thread_ptr** — указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2377">**thread_ptr** Pointer to application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2378">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2378">Return Values</span></span>
- <span data-ttu-id="27adc-2379">**TX_SUCCESS** (0x00) — успешное завершение потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-2379">**TX_SUCCESS** (0x00) Successful thread terminate.</span></span>
- <span data-ttu-id="27adc-2380">**TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2380">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="27adc-2381">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-2381">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2382">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2382">Allowed From</span></span>

<span data-ttu-id="27adc-2383">Потоки и таймеры</span><span class="sxs-lookup"><span data-stu-id="27adc-2383">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-2384">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-2384">Preemption Possible</span></span>

<span data-ttu-id="27adc-2385">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-2385">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2386">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2386">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Terminate the thread represented by "my_thread". */
status = tx_thread_terminate(&my_thread);

/* If status equals TX_SUCCESS, the thread is terminated
and cannot execute again until it is reset. */
```

### <a name="see-also"></a><span data-ttu-id="27adc-2387">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2387">See Also</span></span>

- <span data-ttu-id="27adc-2388">tx_thread_create tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2388">tx_thread_create tx_thread_delete</span></span>
- <span data-ttu-id="27adc-2389">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2389">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27adc-2390">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27adc-2390">tx_thread_identify</span></span>
- <span data-ttu-id="27adc-2391">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2391">tx_thread_info_get</span></span>
- <span data-ttu-id="27adc-2392">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2392">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27adc-2393">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2393">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-2394">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2394">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27adc-2395">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2395">tx_thread_priority_change</span></span>
- <span data-ttu-id="27adc-2396">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27adc-2396">tx_thread_relinquish</span></span>
- <span data-ttu-id="27adc-2397">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27adc-2397">tx_thread_reset</span></span>
- <span data-ttu-id="27adc-2398">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27adc-2398">tx_thread_resume</span></span>
- <span data-ttu-id="27adc-2399">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27adc-2399">tx_thread_sleep</span></span>
- <span data-ttu-id="27adc-2400">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2400">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27adc-2401">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27adc-2401">tx_thread_suspend</span></span>
- <span data-ttu-id="27adc-2402">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2402">tx_thread_time_slice_change</span></span>
- <span data-ttu-id="27adc-2403">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27adc-2403">tx_thread_wait_abort</span></span>

## <a name="tx_thread_time_slice_change"></a><span data-ttu-id="27adc-2404">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2404">tx_thread_time_slice_change</span></span>

<span data-ttu-id="27adc-2405">Изменяет временной срез потока приложения</span><span class="sxs-lookup"><span data-stu-id="27adc-2405">Changes time-slice of application thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2406">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2406">Prototype</span></span>

```c
UINT tx_thread_time_slice_change(
    TX_THREAD *thread_ptr,
    ULONG new_time_slice, 
    ULONG *old_time_slice);
```

### <a name="description"></a><span data-ttu-id="27adc-2407">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2407">Description</span></span>

<span data-ttu-id="27adc-2408">Эта служба изменяет временной срез указанного потока приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2408">This service changes the time-slice of the specified application thread.</span></span> <span data-ttu-id="27adc-2409">Выбор временного среза для потока гарантирует, что он не будет выполняться больше указанного количества тактов таймера, прежде чем другие потоки с такими же или более высокими приоритетами получат возможность запуска.</span><span class="sxs-lookup"><span data-stu-id="27adc-2409">Selecting a time-slice for a thread insures that it won't execute more than the specified number of timer ticks before other threads of the same or higher priorities have a chance to execute.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-2410">*При использовании порога вытеснения отключаются временные срезы для указанного потока.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2410">*Using preemption-threshold disables time-slicing for the specified thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2411">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2411">Parameters</span></span>

- <span data-ttu-id="27adc-2412">**thread_ptr** — указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2412">**thread_ptr** Pointer to application thread.</span></span>
- <span data-ttu-id="27adc-2413">**new_time_slice** — новое значение временного среза.</span><span class="sxs-lookup"><span data-stu-id="27adc-2413">**new_time_slice** New time slice value.</span></span> <span data-ttu-id="27adc-2414">Допустимые значения: TX_NO_TIME_SLICE и числовые значения от 1 до 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="27adc-2414">Legal values include TX_NO_TIME_SLICE and numeric values from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="27adc-2415">**old_time_slice** — указатель на расположение для хранения предыдущего значения временного среза указанного потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-2415">**old_time_slice** Pointer to location for storing the previous timeslice value of the specified thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2416">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2416">Return Values</span></span>

- <span data-ttu-id="27adc-2417">**TX_SUCCESS** (0x00) — успешное изменение временного среза.</span><span class="sxs-lookup"><span data-stu-id="27adc-2417">**TX_SUCCESS** (0x00) Successful time-slice chance.</span></span>
- <span data-ttu-id="27adc-2418">**TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2418">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="27adc-2419">**TX_PTR_ERROR** (0x03) — недопустимый указатель на расположение для хранения предыдущего значения временного среза.</span><span class="sxs-lookup"><span data-stu-id="27adc-2419">**TX_PTR_ERROR** (0x03) Invalid pointer to previous time-slice storage location.</span></span>
- <span data-ttu-id="27adc-2420">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-2420">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2421">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2421">Allowed From</span></span>

<span data-ttu-id="27adc-2422">Потоки и таймеры</span><span class="sxs-lookup"><span data-stu-id="27adc-2422">Threads and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-2423">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-2423">Preemption Possible</span></span>

<span data-ttu-id="27adc-2424">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-2424">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2425">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2425">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-2426">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2426">See Also</span></span>

- <span data-ttu-id="27adc-2427">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2427">tx_thread_create</span></span>
- <span data-ttu-id="27adc-2428">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2428">tx_thread_delete</span></span>
- <span data-ttu-id="27adc-2429">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2429">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27adc-2430">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27adc-2430">tx_thread_identify</span></span>
- <span data-ttu-id="27adc-2431">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2431">tx_thread_info_get</span></span>
- <span data-ttu-id="27adc-2432">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2432">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27adc-2433">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2433">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-2434">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2434">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27adc-2435">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2435">tx_thread_priority_change</span></span>
- <span data-ttu-id="27adc-2436">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27adc-2436">tx_thread_relinquish</span></span>
- <span data-ttu-id="27adc-2437">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27adc-2437">tx_thread_reset</span></span>
- <span data-ttu-id="27adc-2438">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27adc-2438">tx_thread_resume</span></span>
- <span data-ttu-id="27adc-2439">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27adc-2439">tx_thread_sleep</span></span>
- <span data-ttu-id="27adc-2440">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2440">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27adc-2441">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27adc-2441">tx_thread_suspend</span></span>
- <span data-ttu-id="27adc-2442">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27adc-2442">tx_thread_terminate</span></span>
- <span data-ttu-id="27adc-2443">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27adc-2443">tx_thread_wait_abort</span></span>

## <a name="tx_thread_wait_abort"></a><span data-ttu-id="27adc-2444">tx_thread_wait_abort</span><span class="sxs-lookup"><span data-stu-id="27adc-2444">tx_thread_wait_abort</span></span>

<span data-ttu-id="27adc-2445">Прерывание приостановки указанного потока</span><span class="sxs-lookup"><span data-stu-id="27adc-2445">Abort suspension of specified thread</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2446">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2446">Prototype</span></span>

```c
UINT tx_thread_wait_abort(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-2447">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2447">Description</span></span>

<span data-ttu-id="27adc-2448">Эта служба прерывает спящий режим или любую другую приостановку объекта указанного потока.</span><span class="sxs-lookup"><span data-stu-id="27adc-2448">This service aborts sleep or any other object suspension of the specified thread.</span></span> <span data-ttu-id="27adc-2449">Если ожидание прерывается, то из службы, которую ожидает поток, возвращается значение **TX_WAIT_ABORTED**.</span><span class="sxs-lookup"><span data-stu-id="27adc-2449">If the wait is aborted, a **TX_WAIT_ABORTED** value is returned from the service that the thread was waiting on.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-2450">*Эта служба не освобождает явную приостановку, выполненную службой tx_thread_suspend.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2450">*This service does not release explicit suspension that is made by the tx_thread_suspend service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2451">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2451">Parameters</span></span>

- <span data-ttu-id="27adc-2452">**thread_ptr** — указатель на ранее созданный поток приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2452">**thread_ptr** Pointer to a previously created application thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2453">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2453">Return Values</span></span>

- <span data-ttu-id="27adc-2454">**TX_SUCCESS** (0x00) — успешное прерывание приостановки.</span><span class="sxs-lookup"><span data-stu-id="27adc-2454">**TX_SUCCESS** (0x00) Successful thread wait abort.</span></span>
- <span data-ttu-id="27adc-2455">**TX_THREAD_ERROR** (0x0E) — недопустимый указатель на поток приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2455">**TX_THREAD_ERROR** (0x0E) Invalid application thread pointer.</span></span>
- <span data-ttu-id="27adc-2456">**TX_WAIT_ABORT_ERROR** (0x1B) — указанный поток не находится в состоянии ожидания.</span><span class="sxs-lookup"><span data-stu-id="27adc-2456">**TX_WAIT_ABORT_ERROR** (0x1B) Specified thread is not in a waiting state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2457">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2457">Allowed From</span></span>

<span data-ttu-id="27adc-2458">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-2458">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-2459">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-2459">Preemption Possible</span></span>
<span data-ttu-id="27adc-2460">Да</span><span class="sxs-lookup"><span data-stu-id="27adc-2460">Yes</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2461">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2461">Example</span></span>

```c
TX_THREAD my_thread;
UINT status;

/* Abort the suspension condition of "my_thread." */
status = tx_thread_wait_abort(&my_thread);

/* If status equals TX_SUCCESS, the thread is now ready
again, with a return value showing its suspension
was aborted (TX_WAIT_ABORTED). */
```

### <a name="see-also"></a><span data-ttu-id="27adc-2462">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2462">See Also</span></span>

- <span data-ttu-id="27adc-2463">tx_thread_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2463">tx_thread_create</span></span>
- <span data-ttu-id="27adc-2464">tx_thread_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2464">tx_thread_delete</span></span>
- <span data-ttu-id="27adc-2465">tx_thread_entry_exit_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2465">tx_thread_entry_exit_notify</span></span>
- <span data-ttu-id="27adc-2466">tx_thread_identify</span><span class="sxs-lookup"><span data-stu-id="27adc-2466">tx_thread_identify</span></span>
- <span data-ttu-id="27adc-2467">tx_thread_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2467">tx_thread_info_get</span></span>
- <span data-ttu-id="27adc-2468">tx_thread_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2468">tx_thread_performance_info_get</span></span>
- <span data-ttu-id="27adc-2469">tx_thread_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2469">tx_thread_performance_system_info_get</span></span>
- <span data-ttu-id="27adc-2470">tx_thread_preemption_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2470">tx_thread_preemption_change</span></span>
- <span data-ttu-id="27adc-2471">tx_thread_priority_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2471">tx_thread_priority_change</span></span>
- <span data-ttu-id="27adc-2472">tx_thread_relinquish</span><span class="sxs-lookup"><span data-stu-id="27adc-2472">tx_thread_relinquish</span></span>
- <span data-ttu-id="27adc-2473">tx_thread_reset</span><span class="sxs-lookup"><span data-stu-id="27adc-2473">tx_thread_reset</span></span>
- <span data-ttu-id="27adc-2474">tx_thread_resume</span><span class="sxs-lookup"><span data-stu-id="27adc-2474">tx_thread_resume</span></span>
- <span data-ttu-id="27adc-2475">tx_thread_sleep</span><span class="sxs-lookup"><span data-stu-id="27adc-2475">tx_thread_sleep</span></span>
- <span data-ttu-id="27adc-2476">tx_thread_stack_error_notify</span><span class="sxs-lookup"><span data-stu-id="27adc-2476">tx_thread_stack_error_notify</span></span>
- <span data-ttu-id="27adc-2477">tx_thread_suspend</span><span class="sxs-lookup"><span data-stu-id="27adc-2477">tx_thread_suspend</span></span>
- <span data-ttu-id="27adc-2478">tx_thread_terminate</span><span class="sxs-lookup"><span data-stu-id="27adc-2478">tx_thread_terminate</span></span>
- <span data-ttu-id="27adc-2479">tx_thread_time_slice_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2479">tx_thread_time_slice_change</span></span>

## <a name="tx_time_get"></a><span data-ttu-id="27adc-2480">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2480">tx_time_get</span></span>

<span data-ttu-id="27adc-2481">Получение текущего времени</span><span class="sxs-lookup"><span data-stu-id="27adc-2481">Retrieves the current time</span></span>

<span data-ttu-id="27adc-2482">Таймеры приложения</span><span class="sxs-lookup"><span data-stu-id="27adc-2482">Application Timers</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2483">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2483">Prototype</span></span>

```c
ULONG tx_time_get(VOID);
```

### <a name="description"></a><span data-ttu-id="27adc-2484">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2484">Description</span></span>

<span data-ttu-id="27adc-2485">Эта служба возвращает содержимое внутренних системных часов.</span><span class="sxs-lookup"><span data-stu-id="27adc-2485">This service returns the contents of the internal system clock.</span></span> <span data-ttu-id="27adc-2486">Каждый такт таймера увеличивает значение внутренних системных часов на единицу.</span><span class="sxs-lookup"><span data-stu-id="27adc-2486">Each timertick increases the internal system clock by one.</span></span> <span data-ttu-id="27adc-2487">Во время инициализации системные часы устанавливаются в нулевое значение, а их значение можно изменить с помощью службы ***tx_time_set***.</span><span class="sxs-lookup"><span data-stu-id="27adc-2487">The system clock is set to zero during initialization and can be changed to a specific value by the service ***tx_time_set***.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-2488">*Фактическое время, которое представляет каждый такт таймера, зависит от конкретного приложения.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2488">*The actual time each timer-tick represents is application specific.*</span></span>

<span data-ttu-id="27adc-2489">**Параметры**</span><span class="sxs-lookup"><span data-stu-id="27adc-2489">**Parameters**</span></span>

<span data-ttu-id="27adc-2490">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-2490">None</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2491">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2491">Return Values</span></span>

- <span data-ttu-id="27adc-2492">**такты системных часов** — значение внутренних, автономных системных часов.</span><span class="sxs-lookup"><span data-stu-id="27adc-2492">**system clock ticks** Value of the internal, free running, system clock.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2493">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2493">Allowed From</span></span>

<span data-ttu-id="27adc-2494">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-2494">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-2495">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-2495">Preemption Possible</span></span>
<span data-ttu-id="27adc-2496">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-2496">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2497">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2497">Example</span></span>

```c
ULONG current_time;

/* Pickup the current system time, in timer-ticks. */
current_time = tx_time_get();

/* Current time now contains a copy of the internal system
clock. */
```

### <a name="see-also"></a><span data-ttu-id="27adc-2498">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2498">See Also</span></span>

- <span data-ttu-id="27adc-2499">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="27adc-2499">tx_time_set</span></span>

## <a name="tx_time_set"></a><span data-ttu-id="27adc-2500">tx_time_set</span><span class="sxs-lookup"><span data-stu-id="27adc-2500">tx_time_set</span></span>

<span data-ttu-id="27adc-2501">Установка текущего времени</span><span class="sxs-lookup"><span data-stu-id="27adc-2501">Sets the current time</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2502">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2502">Prototype</span></span>

```c
VOID tx_time_set(ULONG new_time);
```

### <a name="description"></a><span data-ttu-id="27adc-2503">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2503">Description</span></span>

<span data-ttu-id="27adc-2504">Эта служба устанавливает для внутренних системных часов указанное значение.</span><span class="sxs-lookup"><span data-stu-id="27adc-2504">This service sets the internal system clock to the specified value.</span></span> <span data-ttu-id="27adc-2505">Каждый такт таймера увеличивает значение внутренних системных часов на единицу.</span><span class="sxs-lookup"><span data-stu-id="27adc-2505">Each timer-tick increases the internal system clock by one.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-2506">*Фактическое время, которое представляет каждый такт таймера, зависит от конкретного приложения.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2506">*The actual time each timer-tick represents is application specific.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2507">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2507">Parameters</span></span>

- <span data-ttu-id="27adc-2508">**new_time** — новое значение времени для размещения в системных часах, допустимы значения от 0 до 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="27adc-2508">**new_time** New time to put in the system clock, legal values range from 0 through 0xFFFFFFFF.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2509">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2509">Return Values</span></span>

<span data-ttu-id="27adc-2510">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-2510">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2511">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2511">Allowed From</span></span>

<span data-ttu-id="27adc-2512">Потоки, таймеры и ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-2512">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-2513">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-2513">Preemption Possible</span></span>

<span data-ttu-id="27adc-2514">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-2514">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2515">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2515">Example</span></span>

```c
/* Set the internal system time to 0x1234. */
tx_time_set(0x1234);

/* Current time now contains 0x1234 until the next timer
interrupt. */
```

### <a name="see-also"></a><span data-ttu-id="27adc-2516">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2516">See Also</span></span>

- <span data-ttu-id="27adc-2517">tx_time_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2517">tx_time_get</span></span>

## <a name="tx_timer_activate"></a><span data-ttu-id="27adc-2518">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="27adc-2518">tx_timer_activate</span></span>

<span data-ttu-id="27adc-2519">Активация таймера приложения</span><span class="sxs-lookup"><span data-stu-id="27adc-2519">Activate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2520">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2520">Prototype</span></span>

```c
UINT tx_timer_activate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-2521">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2521">Description</span></span>

<span data-ttu-id="27adc-2522">Эта служба активирует указанный таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2522">This service activates the specified application timer.</span></span> <span data-ttu-id="27adc-2523">Подпрограммы после истечения срока действия таймеров, которые истекают одновременно, выполняются в том порядке, в котором они были активированы.</span><span class="sxs-lookup"><span data-stu-id="27adc-2523">The expiration routines of timers that expire at the same time are executed in the order they were activated.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-2524">*Таймер с истекшим сроком действия должен быть сброшен с помощью* ***tx_timer_change** _, _прежде чем его можно будет активировать снова*.</span><span class="sxs-lookup"><span data-stu-id="27adc-2524">*An expired one-shot timer must be reset via* ***tx_timer_change** _ _before it can be activated again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2525">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2525">Parameters</span></span>

- <span data-ttu-id="27adc-2526">**timer_ptr** — указатель на ранее созданный таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2526">**timer_ptr** Pointer to a previously created application timer.</span></span>

<span data-ttu-id="27adc-2527">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="27adc-2527">**Return Values**</span></span>

- <span data-ttu-id="27adc-2528">**TX_SUCCESS** (0x00) — успешная активация таймера приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2528">**TX_SUCCESS** (0x00) Successful application timer activation.</span></span>
- <span data-ttu-id="27adc-2529">**TX_TIMER_ERROR** (0x15) — недопустимый указатель на таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2529">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="27adc-2530">**TX_ACTIVATE_ERROR** (0x17) — таймер уже активен или является одноразовым таймером, срок действия которого уже истек.</span><span class="sxs-lookup"><span data-stu-id="27adc-2530">**TX_ACTIVATE_ERROR** (0x17) Timer was already active or is a one-shot timer that has already expired.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2531">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2531">Allowed From</span></span>

<span data-ttu-id="27adc-2532">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-2532">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-2533">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-2533">Preemption Possible</span></span>

<span data-ttu-id="27adc-2534">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-2534">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2535">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2535">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Activate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_activate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now active. */
```

### <a name="see-also"></a><span data-ttu-id="27adc-2536">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2536">See Also</span></span>

- <span data-ttu-id="27adc-2537">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2537">tx_timer_change</span></span>
- <span data-ttu-id="27adc-2538">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2538">tx_timer_create</span></span>
- <span data-ttu-id="27adc-2539">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="27adc-2539">tx_timer_deactivate</span></span>
- <span data-ttu-id="27adc-2540">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2540">tx_timer_delete</span></span>
- <span data-ttu-id="27adc-2541">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2541">tx_timer_info_get</span></span>
- <span data-ttu-id="27adc-2542">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2542">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="27adc-2543">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2543">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_change"></a><span data-ttu-id="27adc-2544">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2544">tx_timer_change</span></span>

<span data-ttu-id="27adc-2545">Изменение таймера приложения</span><span class="sxs-lookup"><span data-stu-id="27adc-2545">Change application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2546">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2546">Prototype</span></span>

```c
UINT tx_timer_change(
    TX_TIMER *timer_ptr,
    ULONG initial_ticks, 
    ULONG reschedule_ticks);
```

### <a name="description"></a><span data-ttu-id="27adc-2547">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2547">Description</span></span>

<span data-ttu-id="27adc-2548">Эта служба изменяет характеристики срока действия указанного таймера приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2548">This service changes the expiration characteristics of the specified application timer.</span></span> <span data-ttu-id="27adc-2549">Перед вызовом этой службы таймер должен быть деактивирован.</span><span class="sxs-lookup"><span data-stu-id="27adc-2549">The timer must be deactivated prior to calling this service.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-2550">*Для повторного запуска таймера после вызова этой службы требуется вызов службы* ***tx_timer_activate** _ _*.</span><span class="sxs-lookup"><span data-stu-id="27adc-2550">*A call to the* ***tx_timer_activate** _ _service is required after this service in order to start the timer again.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2551">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2551">Parameters</span></span>

- <span data-ttu-id="27adc-2552">**timer_ptr** — указатель на управляющий блок таймера.</span><span class="sxs-lookup"><span data-stu-id="27adc-2552">**timer_ptr** Pointer to a timer control block.</span></span>
- <span data-ttu-id="27adc-2553">**initial_ticks** — указывает начальное число тактов для расчета срока действия таймера.</span><span class="sxs-lookup"><span data-stu-id="27adc-2553">**initial_ticks** Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="27adc-2554">Допустимые значения находятся в диапазоне от 1 до 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="27adc-2554">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="27adc-2555">**reschedule_ticks** — задает количество тактов для всех истечений таймера после первого.</span><span class="sxs-lookup"><span data-stu-id="27adc-2555">**reschedule_ticks** Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="27adc-2556">Значение ноль для этого параметра делает таймер *одноразовым*.</span><span class="sxs-lookup"><span data-stu-id="27adc-2556">A zero for this parameter makes the timer a *one-shot* timer.</span></span> <span data-ttu-id="27adc-2557">В противном случае для периодических таймеров допустимы значения в диапазоне от 1 до 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="27adc-2557">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-2558">*Таймер с истекшим сроком действия должен быть сброшен с помощью*
***tx_timer_change** _, _прежде чем его можно будет активировать снова*.</span><span class="sxs-lookup"><span data-stu-id="27adc-2558">*An expired one-shot timer must be reset via*
***tx_timer_change** _ _before it can be activated again.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2559">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2559">Return Values</span></span>

- <span data-ttu-id="27adc-2560">**TX_SUCCESS** (0x00) — успешное изменение таймера приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2560">**TX_SUCCESS** (0x00) Successful application timer change.</span></span>
- <span data-ttu-id="27adc-2561">**TX_TIMER_ERROR** (0x15) — недопустимый указатель на таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2561">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="27adc-2562">**TX_TICK_ERROR** (0x16) — указано недопустимое значение (ноль) для начальных тактов.</span><span class="sxs-lookup"><span data-stu-id="27adc-2562">**TX_TICK_ERROR** (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="27adc-2563">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-2563">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2564">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2564">Allowed From</span></span>

<span data-ttu-id="27adc-2565">Потоки, таймеры и ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-2565">Threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-2566">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-2566">Preemption Possible</span></span>

<span data-ttu-id="27adc-2567">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-2567">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2568">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2568">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-2569">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2569">See Also</span></span>

- <span data-ttu-id="27adc-2570">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="27adc-2570">tx_timer_activate</span></span>
- <span data-ttu-id="27adc-2571">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2571">tx_timer_create</span></span>
- <span data-ttu-id="27adc-2572">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="27adc-2572">tx_timer_deactivate</span></span>
- <span data-ttu-id="27adc-2573">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2573">tx_timer_delete</span></span>
- <span data-ttu-id="27adc-2574">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2574">tx_timer_info_get</span></span>
- <span data-ttu-id="27adc-2575">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2575">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="27adc-2576">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2576">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_create"></a><span data-ttu-id="27adc-2577">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2577">tx_timer_create</span></span>

<span data-ttu-id="27adc-2578">Создание таймера приложения</span><span class="sxs-lookup"><span data-stu-id="27adc-2578">Create application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2579">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2579">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="27adc-2580">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2580">Description</span></span>

<span data-ttu-id="27adc-2581">Эта служба создает таймер приложения с указанной функцией истечения срока действия и периодичностью.</span><span class="sxs-lookup"><span data-stu-id="27adc-2581">This service creates an application timer with the specified expiration function and periodic.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2582">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2582">Parameters</span></span>

- <span data-ttu-id="27adc-2583">**timer_ptr** — указатель на управляющий блок таймера.</span><span class="sxs-lookup"><span data-stu-id="27adc-2583">**timer_ptr** Pointer to a timer control block</span></span>
- <span data-ttu-id="27adc-2584">**name_ptr** — указатель на имя таймера.</span><span class="sxs-lookup"><span data-stu-id="27adc-2584">**name_ptr** Pointer to the name of the timer.</span></span>
- <span data-ttu-id="27adc-2585">**expiration_function** — функция приложения, вызываемая по истечении срока действия таймера.</span><span class="sxs-lookup"><span data-stu-id="27adc-2585">**expiration_function** Application function to call when the timer expires.</span></span>
- <span data-ttu-id="27adc-2586">**expiration_input** — входные данные для передачи в функцию истечения срока действия по истечении срока действия таймера.</span><span class="sxs-lookup"><span data-stu-id="27adc-2586">**expiration_input** Input to pass to expiration function when timer expires.</span></span>
- <span data-ttu-id="27adc-2587">**initial_ticks** — указывает начальное число тактов для расчета срока действия таймера.</span><span class="sxs-lookup"><span data-stu-id="27adc-2587">**initial_ticks** Specifies the initial number of ticks for timer expiration.</span></span> <span data-ttu-id="27adc-2588">Допустимые значения находятся в диапазоне от 1 до 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="27adc-2588">Legal values range from 1 through 0xFFFFFFFF.</span></span>
- <span data-ttu-id="27adc-2589">**reschedule_ticks** — задает количество тактов для всех истечений таймера после первого.</span><span class="sxs-lookup"><span data-stu-id="27adc-2589">**reschedule_ticks** Specifies the number of ticks for all timer expirations after the first.</span></span> <span data-ttu-id="27adc-2590">Значение ноль для этого параметра делает таймер *одноразовым*.</span><span class="sxs-lookup"><span data-stu-id="27adc-2590">A zero for this parameter makes the timer a *one-shot* timer.</span></span> <span data-ttu-id="27adc-2591">В противном случае для периодических таймеров допустимы значения в диапазоне от 1 до 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="27adc-2591">Otherwise, for periodic timers, legal values range from 1 through 0xFFFFFFFF.</span></span>

  > [!NOTE]
  > <span data-ttu-id="27adc-2592">*После истечения срока действия одноразового таймера его необходимо сбросить с помощью tx_timer_change, прежде чем его можно будет активировать снова.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2592">*After a one-shot timer expires, it must be reset via   tx_timer_change before it can be activated again.*</span></span>

- <span data-ttu-id="27adc-2593">**auto_activate** — определяет, активируется ли таймер автоматически во время создания.</span><span class="sxs-lookup"><span data-stu-id="27adc-2593">**auto_activate** Determines if the timer is automatically activated during creation.</span></span> <span data-ttu-id="27adc-2594">Если это значение равно **TX_AUTO_ACTIVATE** (0x01), таймер становится активным.</span><span class="sxs-lookup"><span data-stu-id="27adc-2594">If this value is **TX_AUTO_ACTIVATE** (0x01) the timer is made active.</span></span> <span data-ttu-id="27adc-2595">В противном случае, если указано значение **TX_NO_ACTIVATE** (0x00), таймер создается в неактивном состоянии.</span><span class="sxs-lookup"><span data-stu-id="27adc-2595">Otherwise, if the value **TX_NO_ACTIVATE** (0x00) is selected, the timer is created in a non-active state.</span></span> <span data-ttu-id="27adc-2596">В этом случае для фактического запуска таймера необходим последующий вызов службы **_tx_timer_activate_**.</span><span class="sxs-lookup"><span data-stu-id="27adc-2596">In this case, a subsequent **_tx_timer_activate_** service call is necessary to get the timer actually started.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2597">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2597">Return Values</span></span>

- <span data-ttu-id="27adc-2598">**TX_SUCCESS** (0x00) — успешное создание таймера приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2598">**TX_SUCCESS** (0x00) Successful application timer creation.</span></span>
- <span data-ttu-id="27adc-2599">**TX_TIMER_ERROR** (0x15) — недопустимый указатель на таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2599">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span> <span data-ttu-id="27adc-2600">Либо указатель имеет значение NULL, либо таймер уже создан.</span><span class="sxs-lookup"><span data-stu-id="27adc-2600">Either the pointer is NULL or the timer is already created.</span></span>
- <span data-ttu-id="27adc-2601">**TX_TICK_ERROR** (0x16) — указано недопустимое значение (ноль) для начальных тактов.</span><span class="sxs-lookup"><span data-stu-id="27adc-2601">**TX_TICK_ERROR** (0x16) Invalid value (a zero) supplied for initial ticks.</span></span>
- <span data-ttu-id="27adc-2602">**TX_ACTIVATE_ERROR** (0x17) — задано неверное значение параметра активации.</span><span class="sxs-lookup"><span data-stu-id="27adc-2602">**TX_ACTIVATE_ERROR** (0x17) Invalid activation selected.</span></span>
- <span data-ttu-id="27adc-2603">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-2603">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2604">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2604">Allowed From</span></span>

<span data-ttu-id="27adc-2605">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-2605">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-2606">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-2606">Preemption Possible</span></span>

<span data-ttu-id="27adc-2607">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-2607">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2608">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2608">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-2609">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2609">See Also</span></span>

- <span data-ttu-id="27adc-2610">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="27adc-2610">tx_timer_activate</span></span>
- <span data-ttu-id="27adc-2611">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2611">tx_timer_change</span></span>
- <span data-ttu-id="27adc-2612">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="27adc-2612">tx_timer_deactivate</span></span>
- <span data-ttu-id="27adc-2613">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2613">tx_timer_delete</span></span>
- <span data-ttu-id="27adc-2614">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2614">tx_timer_info_get</span></span>
- <span data-ttu-id="27adc-2615">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2615">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="27adc-2616">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2616">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_deactivate"></a><span data-ttu-id="27adc-2617">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="27adc-2617">tx_timer_deactivate</span></span>

<span data-ttu-id="27adc-2618">Деактивация таймера приложения</span><span class="sxs-lookup"><span data-stu-id="27adc-2618">Deactivate application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2619">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2619">Prototype</span></span>

```c
UINT tx_timer_deactivate(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-2620">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2620">Description</span></span>

<span data-ttu-id="27adc-2621">Эта служба деактивирует указанный таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2621">This service deactivates the specified application timer.</span></span> <span data-ttu-id="27adc-2622">Если таймер уже деактивирован, эта служба не оказывает никакого эффекта.</span><span class="sxs-lookup"><span data-stu-id="27adc-2622">If the timer is already deactivated, this service has no effect.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2623">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2623">Parameters</span></span>

- <span data-ttu-id="27adc-2624">**timer_ptr** — указатель на ранее созданный таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2624">**timer_ptr** Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2625">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2625">Return Values</span></span>

- <span data-ttu-id="27adc-2626">**TX_SUCCESS** (0x00) — успешная деактивация таймера приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2626">**TX_SUCCESS** (0x00) Successful application timer deactivation.</span></span>
- <span data-ttu-id="27adc-2627">**TX_TIMER_ERROR** (0x15) — недопустимый указатель на таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2627">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2628">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2628">Allowed From</span></span>

<span data-ttu-id="27adc-2629">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-2629">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-2630">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-2630">Preemption Possible</span></span>

<span data-ttu-id="27adc-2631">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-2631">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2632">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2632">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Deactivate an application timer. Assume that the
application timer has already been created. */
status = tx_timer_deactivate(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
now deactivated. */
```

### <a name="see-also"></a><span data-ttu-id="27adc-2633">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2633">See Also</span></span>

- <span data-ttu-id="27adc-2634">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="27adc-2634">tx_timer_activate</span></span>
- <span data-ttu-id="27adc-2635">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2635">tx_timer_change</span></span>
- <span data-ttu-id="27adc-2636">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2636">tx_timer_create</span></span>
- <span data-ttu-id="27adc-2637">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2637">tx_timer_delete</span></span>
- <span data-ttu-id="27adc-2638">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2638">tx_timer_info_get</span></span>
- <span data-ttu-id="27adc-2639">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2639">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="27adc-2640">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2640">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_delete"></a><span data-ttu-id="27adc-2641">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2641">tx_timer_delete</span></span>

<span data-ttu-id="27adc-2642">Удаление таймера приложения</span><span class="sxs-lookup"><span data-stu-id="27adc-2642">Delete application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2643">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2643">Prototype</span></span>

```c
UINT tx_timer_delete(TX_TIMER *timer_ptr);
```

### <a name="description"></a><span data-ttu-id="27adc-2644">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2644">Description</span></span>

<span data-ttu-id="27adc-2645">Эта служба удаляет указанный таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2645">This service deletes the specified application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-2646">*Ответственность за предотвращение использования удаленного таймера лежит на приложении.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2646">*It is the application's responsibility to prevent use of a deleted timer.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2647">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2647">Parameters</span></span>

- <span data-ttu-id="27adc-2648">**timer_ptr** — указатель на ранее созданный таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2648">**timer_ptr** Pointer to a previously created application timer.</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2649">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2649">Return Values</span></span>

- <span data-ttu-id="27adc-2650">**TX_SUCCESS** (0x00) — успешное удаление таймера приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2650">**TX_SUCCESS** (0x00) Successful application timer deletion.</span></span>
- <span data-ttu-id="27adc-2651">**TX_TIMER_ERROR** (0x15) — недопустимый указатель на таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2651">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>
- <span data-ttu-id="27adc-2652">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="27adc-2652">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2653">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2653">Allowed From</span></span>

<span data-ttu-id="27adc-2654">Потоки</span><span class="sxs-lookup"><span data-stu-id="27adc-2654">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-2655">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-2655">Preemption Possible</span></span>

<span data-ttu-id="27adc-2656">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-2656">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2657">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2657">Example</span></span>

```c
TX_TIMER my_timer;
UINT status;

/* Delete application timer. Assume that the application
timer has already been created. */
status = tx_timer_delete(&my_timer);

/* If status equals TX_SUCCESS, the application timer is
deleted. */
```

### <a name="see-also"></a><span data-ttu-id="27adc-2658">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2658">See Also</span></span>

- <span data-ttu-id="27adc-2659">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="27adc-2659">tx_timer_activate</span></span>
- <span data-ttu-id="27adc-2660">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2660">tx_timer_change</span></span>
- <span data-ttu-id="27adc-2661">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2661">tx_timer_create</span></span>
- <span data-ttu-id="27adc-2662">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="27adc-2662">tx_timer_deactivate</span></span>
- <span data-ttu-id="27adc-2663">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2663">tx_timer_info_get</span></span>
- <span data-ttu-id="27adc-2664">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2664">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="27adc-2665">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2665">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_info_get"></a><span data-ttu-id="27adc-2666">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2666">tx_timer_info_get</span></span>

<span data-ttu-id="27adc-2667">Получение сведений о таймере приложения</span><span class="sxs-lookup"><span data-stu-id="27adc-2667">Retrieve information about an application timer</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2668">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2668">Prototype</span></span>

```c
UINT tx_timer_info_get(
    TX_TIMER *timer_ptr, 
    CHAR **name,
    UINT *active,
    ULONG *remaining_ticks,
    ULONG *reschedule_ticks,
    TX_TIMER **next_timer);
```

### <a name="description"></a><span data-ttu-id="27adc-2669">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2669">Description</span></span>

<span data-ttu-id="27adc-2670">Эта служба получает сведения об указанном таймере приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2670">This service retrieves information about the specified application timer.</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2671">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2671">Parameters</span></span>

- <span data-ttu-id="27adc-2672">**timer_ptr** — указатель на ранее созданный таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2672">**timer_ptr** Pointer to a previously created application timer.</span></span>
- <span data-ttu-id="27adc-2673">**name** — указатель на назначение для указателя на имя таймера.</span><span class="sxs-lookup"><span data-stu-id="27adc-2673">**name** Pointer to destination for the pointer to the timer's name.</span></span>
- <span data-ttu-id="27adc-2674">**active** — указатель на назначение для индикации активности таймера.</span><span class="sxs-lookup"><span data-stu-id="27adc-2674">**active** Pointer to destination for the timer active indication.</span></span> <span data-ttu-id="27adc-2675">Если таймер неактивен или эта служба вызывается из самого таймера, возвращается значение **TX_FALSE**.</span><span class="sxs-lookup"><span data-stu-id="27adc-2675">If the timer is inactive or this service is called from the timer itself, a **TX_FALSE** value is returned.</span></span> <span data-ttu-id="27adc-2676">В противном случае, если таймер активен, возвращается значение **TX_TRUE**.</span><span class="sxs-lookup"><span data-stu-id="27adc-2676">Otherwise, if the timer is active, a **TX_TRUE** value is returned.</span></span>
- <span data-ttu-id="27adc-2677">**remaining_ticks** — указатель на место назначения для количества тактов таймера, оставшихся до истечения его срока действия.</span><span class="sxs-lookup"><span data-stu-id="27adc-2677">**remaining_ticks** Pointer to destination for the number of timer ticks left before the timer expires.</span></span>
- <span data-ttu-id="27adc-2678">**reschedule_ticks** — указатель на место назначения для количества тактов таймера, которые будут использоваться для автоматического повторного планирования этого таймера.</span><span class="sxs-lookup"><span data-stu-id="27adc-2678">**reschedule_ticks** Pointer to destination for the number of timer ticks that will be used to automatically reschedule this timer.</span></span> <span data-ttu-id="27adc-2679">Если значение равно нулю, то таймер является одноразовым и не будет перепланирован.</span><span class="sxs-lookup"><span data-stu-id="27adc-2679">If the value is zero, then the timer is a one-shot and won't be rescheduled.</span></span>
- <span data-ttu-id="27adc-2680">**next_timer** — указатель на назначение для указателя следующего созданного таймера приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2680">**next_timer** Pointer to destination for the pointer of the next created application timer.</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-2681">*Указание **TX_NULL** для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2681">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2682">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2682">Return Values</span></span>

- <span data-ttu-id="27adc-2683">**TX_SUCCESS** (0x00) — успешное получение сведений о таймере.</span><span class="sxs-lookup"><span data-stu-id="27adc-2683">**TX_SUCCESS** (0x00) Successful timer information retrieval.</span></span>
- <span data-ttu-id="27adc-2684">**TX_TIMER_ERROR** (0x15) — недопустимый указатель на таймер приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2684">**TX_TIMER_ERROR** (0x15) Invalid application timer pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2685">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2685">Allowed From</span></span>

<span data-ttu-id="27adc-2686">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-2686">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="27adc-2687">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="27adc-2687">Preemption Possible</span></span>

<span data-ttu-id="27adc-2688">Нет</span><span class="sxs-lookup"><span data-stu-id="27adc-2688">No</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2689">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2689">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-2690">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2690">See Also</span></span>

- <span data-ttu-id="27adc-2691">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="27adc-2691">tx_timer_activate</span></span>
- <span data-ttu-id="27adc-2692">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2692">tx_timer_change</span></span>
- <span data-ttu-id="27adc-2693">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2693">tx_timer_create</span></span>
- <span data-ttu-id="27adc-2694">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="27adc-2694">tx_timer_deactivate</span></span>
- <span data-ttu-id="27adc-2695">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2695">tx_timer_delete</span></span>
- <span data-ttu-id="27adc-2696">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2696">tx_timer_info_get</span></span>
- <span data-ttu-id="27adc-2697">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2697">tx_timer_performance_info_get</span></span>
- <span data-ttu-id="27adc-2698">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2698">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_info_get"></a><span data-ttu-id="27adc-2699">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2699">tx_timer_performance_info_get</span></span>

<span data-ttu-id="27adc-2700">Получение сведений о производительности таймера</span><span class="sxs-lookup"><span data-stu-id="27adc-2700">Get timer performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2701">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2701">Prototype</span></span>

```c
UINT tx_timer_performance_info_get(
    TX_TIMER *timer_ptr,
    ULONG *activates, 
    ULONG *reactivates,
    ULONG *deactivates, 
    ULONG *expirations,
    ULONG *expiration_adjusts);
```

### <a name="description"></a><span data-ttu-id="27adc-2702">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2702">Description</span></span>

<span data-ttu-id="27adc-2703">Эта служба получает сведения о производительности указанного таймера приложения.</span><span class="sxs-lookup"><span data-stu-id="27adc-2703">This service retrieves performance information about the specified application timer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-2704">*Библиотека ThreadX и приложение должны быть построены с определенным параметром* ***TX_TIMER_ENABLE_PERFORMANCE_INFO** _ _, чтобы служба могла вернуть сведения о производительности*.</span><span class="sxs-lookup"><span data-stu-id="27adc-2704">*The ThreadX library and application must be built with* ***TX_TIMER_ENABLE_PERFORMANCE_INFO** _ _defined for this service to return performance information.*</span></span>

### <a name="parameters"></a><span data-ttu-id="27adc-2705">Параметры</span><span class="sxs-lookup"><span data-stu-id="27adc-2705">Parameters</span></span>
- <span data-ttu-id="27adc-2706">**timer_ptr** — указатель на ранее созданный таймер.</span><span class="sxs-lookup"><span data-stu-id="27adc-2706">**timer_ptr** Pointer to previously created timer.</span></span>
- <span data-ttu-id="27adc-2707">**activates** — указатель на место назначения для количества запросов на активацию, выполненных для этого таймера.</span><span class="sxs-lookup"><span data-stu-id="27adc-2707">**activates** Pointer to destination for the number of activation requests performed on this timer.</span></span>
- <span data-ttu-id="27adc-2708">**reactivates** — указатель на место назначения для количества автоматических повторных активаций, выполненных для этого периодического таймера.</span><span class="sxs-lookup"><span data-stu-id="27adc-2708">**reactivates** Pointer to destination for the number of automatic reactivations performed on this periodic timer.</span></span>
- <span data-ttu-id="27adc-2709">**deactivates** — указатель на место назначения для количества запросов на деактивацию, выполненных для этого таймера.</span><span class="sxs-lookup"><span data-stu-id="27adc-2709">**deactivates** Pointer to destination for the number of deactivation requests performed on this timer.</span></span>
- <span data-ttu-id="27adc-2710">**expirations** — указатель на место назначения для количества истечений срока действия этого таймера.</span><span class="sxs-lookup"><span data-stu-id="27adc-2710">**expirations** Pointer to destination for the number of expirations of this timer.</span></span>
- <span data-ttu-id="27adc-2711">**expiration_adjusts** — указатель на место назначения для количества внутренних корректировок срока действия, выполненных для этого таймера.</span><span class="sxs-lookup"><span data-stu-id="27adc-2711">**expiration_adjusts** Pointer to destination for the number of internal expiration adjustments performed on this timer.</span></span> <span data-ttu-id="27adc-2712">Эти корректировки выполняются при обработке прерываний для таймеров, размер которых превышает размер списка таймеров по умолчанию (по умолчанию — таймеры со сроком действия более 32 тактов).</span><span class="sxs-lookup"><span data-stu-id="27adc-2712">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> <span data-ttu-id="27adc-2713">[ПРИМЕЧАНИЕ] *Указание TX_NULL для любого параметра сообщает, что это параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2713">[NOTE] *Supplying a TX_NULL for any parameter indicates the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2714">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2714">Return Values</span></span>

- <span data-ttu-id="27adc-2715">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности таймера.</span><span class="sxs-lookup"><span data-stu-id="27adc-2715">**TX_SUCCESS** (0x00) Successful timer performance get.</span></span>
- <span data-ttu-id="27adc-2716">**TX_PTR_ERROR** (0x03) — недопустимый указатель на таймер.</span><span class="sxs-lookup"><span data-stu-id="27adc-2716">**TX_PTR_ERROR** (0x03) Invalid timer pointer.</span></span>
- <span data-ttu-id="27adc-2717">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.</span><span class="sxs-lookup"><span data-stu-id="27adc-2717">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2718">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2718">Allowed From</span></span>

<span data-ttu-id="27adc-2719">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-2719">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2720">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2720">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-2721">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2721">See Also</span></span>

- <span data-ttu-id="27adc-2722">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="27adc-2722">tx_timer_activate</span></span>
- <span data-ttu-id="27adc-2723">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2723">tx_timer_change</span></span>
- <span data-ttu-id="27adc-2724">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2724">tx_timer_create</span></span>
- <span data-ttu-id="27adc-2725">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="27adc-2725">tx_timer_deactivate</span></span>
- <span data-ttu-id="27adc-2726">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2726">tx_timer_delete</span></span>
- <span data-ttu-id="27adc-2727">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2727">tx_timer_info_get</span></span>
- <span data-ttu-id="27adc-2728">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2728">tx_timer_performance_system_info_get</span></span>

## <a name="tx_timer_performance_system_info_get"></a><span data-ttu-id="27adc-2729">tx_timer_performance_system_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2729">tx_timer_performance_system_info_get</span></span>

<span data-ttu-id="27adc-2730">Получение сведений о производительности системы таймеров</span><span class="sxs-lookup"><span data-stu-id="27adc-2730">Get timer system performance information</span></span>

### <a name="prototype"></a><span data-ttu-id="27adc-2731">Прототип</span><span class="sxs-lookup"><span data-stu-id="27adc-2731">Prototype</span></span>

```c
UINT tx_timer_performance_system_info_get(
    ULONG *activates,
    ULONG *reactivates, 
    ULONG *deactivates,
    ULONG *expirations, 
    ULONG *expiration_adjusts);
```

### <a name="description"></a><span data-ttu-id="27adc-2732">Описание</span><span class="sxs-lookup"><span data-stu-id="27adc-2732">Description</span></span>

<span data-ttu-id="27adc-2733">Эта служба получает сведения о производительности всех таймеров приложений в системе.</span><span class="sxs-lookup"><span data-stu-id="27adc-2733">This service retrieves performance information about all the application timers in the system.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27adc-2734">*Библиотека ThreadX и приложение должны быть построены с определенным параметром* **TX_TIMER_ENABLE_PERFORMANCE_INFO**, *чтобы служба могла вернуть сведения о производительности.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2734">*The ThreadX library and application must be built with* **TX_TIMER_ENABLE_PERFORMANCE_INFO** *defined for this service to return performance information.*</span></span>

<span data-ttu-id="27adc-2735">**Параметры**</span><span class="sxs-lookup"><span data-stu-id="27adc-2735">**Parameters**</span></span>

- <span data-ttu-id="27adc-2736">**activates** — указатель на место назначения для общего количества запросов на активацию, выполненных для всех таймеров.</span><span class="sxs-lookup"><span data-stu-id="27adc-2736">**activates** Pointer to destination for the total number of activation requests performed on all timers.</span></span>
- <span data-ttu-id="27adc-2737">**reactivates** — указатель на место назначения для общего количества автоматических повторных активаций, выполненных для всех периодических таймеров.</span><span class="sxs-lookup"><span data-stu-id="27adc-2737">**reactivates** Pointer to destination for the total number of automatic reactivation performed on all periodic timers.</span></span>
- <span data-ttu-id="27adc-2738">**deactivates** — указатель на место назначения для общего количества запросов на деактивацию, выполненных для всех таймеров.</span><span class="sxs-lookup"><span data-stu-id="27adc-2738">**deactivates** Pointer to destination for the total number of deactivation requests performed on all timers.</span></span>
- <span data-ttu-id="27adc-2739">**expirations** — указатель на место назначения для общего количества истечений срока действия всех таймеров.</span><span class="sxs-lookup"><span data-stu-id="27adc-2739">**expirations** Pointer to destination for the total number of expirations on all timers.</span></span>
- <span data-ttu-id="27adc-2740">**expiration_adjusts** — указатель на место назначения для общего количества внутренних корректировок срока действия, выполненных для всех таймеров.</span><span class="sxs-lookup"><span data-stu-id="27adc-2740">**expiration_adjusts** Pointer to destination for the total number of internal expiration adjustments performed on all timers.</span></span> <span data-ttu-id="27adc-2741">Эти корректировки выполняются при обработке прерываний для таймеров, размер которых превышает размер списка таймеров по умолчанию (по умолчанию — таймеры со сроком действия более 32 тактов).</span><span class="sxs-lookup"><span data-stu-id="27adc-2741">These adjustments are done in the timer interrupt processing for timers that are larger than the default timer list size (by default timers with expirations greater than 32 ticks).</span></span>

> [!NOTE]
> <span data-ttu-id="27adc-2742">*Указание **TX_NULL** для любого параметра сообщает, что этот параметр не является обязательным.*</span><span class="sxs-lookup"><span data-stu-id="27adc-2742">*Supplying a **TX_NULL** for any parameter indicates that the parameter is not required.*</span></span>

### <a name="return-values"></a><span data-ttu-id="27adc-2743">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="27adc-2743">Return Values</span></span>

- <span data-ttu-id="27adc-2744">**TX_SUCCESS** (0x00) — успешное получение сведений о производительности системы таймеров.</span><span class="sxs-lookup"><span data-stu-id="27adc-2744">**TX_SUCCESS** (0x00) Successful timer system performance get.</span></span>
- <span data-ttu-id="27adc-2745">**TX_FEATURE_NOT_ENABLED** (0xFF) — система не была скомпилирована с включением информации о производительности.</span><span class="sxs-lookup"><span data-stu-id="27adc-2745">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was not compiled with performance information enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="27adc-2746">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="27adc-2746">Allowed From</span></span>

<span data-ttu-id="27adc-2747">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="27adc-2747">Initialization, threads, timers, and ISRs</span></span>

### <a name="example"></a><span data-ttu-id="27adc-2748">Пример</span><span class="sxs-lookup"><span data-stu-id="27adc-2748">Example</span></span>

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

### <a name="see-also"></a><span data-ttu-id="27adc-2749">См. также:</span><span class="sxs-lookup"><span data-stu-id="27adc-2749">See Also</span></span>

- <span data-ttu-id="27adc-2750">tx_timer_activate</span><span class="sxs-lookup"><span data-stu-id="27adc-2750">tx_timer_activate</span></span>
- <span data-ttu-id="27adc-2751">tx_timer_change</span><span class="sxs-lookup"><span data-stu-id="27adc-2751">tx_timer_change</span></span>
- <span data-ttu-id="27adc-2752">tx_timer_create</span><span class="sxs-lookup"><span data-stu-id="27adc-2752">tx_timer_create</span></span>
- <span data-ttu-id="27adc-2753">tx_timer_deactivate</span><span class="sxs-lookup"><span data-stu-id="27adc-2753">tx_timer_deactivate</span></span>
- <span data-ttu-id="27adc-2754">tx_timer_delete</span><span class="sxs-lookup"><span data-stu-id="27adc-2754">tx_timer_delete</span></span>
- <span data-ttu-id="27adc-2755">tx_timer_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2755">tx_timer_info_get</span></span>
- <span data-ttu-id="27adc-2756">tx_timer_performance_info_get</span><span class="sxs-lookup"><span data-stu-id="27adc-2756">tx_timer_performance_info_get</span></span>
