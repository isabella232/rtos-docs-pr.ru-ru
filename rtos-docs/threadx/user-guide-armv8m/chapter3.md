---
title: Глава 3. API-интерфейсы ThreadX для архитектуры ARMv8-M
description: В этой главе содержится описание служб ThreadX, относящихся к архитектуре ARMv8-M.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 14bdfab3d56476d52ba91f859cec4af4ab7f4bef
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377539"
---
# <a name="chapter-3--threadx-apis-for-armv8-m"></a><span data-ttu-id="2a5a2-103">Глава 3. API-интерфейсы ThreadX для архитектуры ARMv8-M</span><span class="sxs-lookup"><span data-stu-id="2a5a2-103">Chapter 3  ThreadX APIs for ARMv8-M</span></span>

<span data-ttu-id="2a5a2-104">В этой главе содержится описание служб ThreadX, относящихся к архитектуре ARMv8-M. Службы указаны в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-104">This chapter contains a description of the ARMv8-M-specific ThreadX services in alphabetic order.</span></span> <span data-ttu-id="2a5a2-105">Их имена реализованы так, что все аналогичные службы группируются вместе.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-105">Their names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="2a5a2-106">В разделе "Возвращаемые значения" приведенных ниже описаний **выделенные полужирным шрифтом** значения не затрагиваются определением **TX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки ошибок API. Значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-106">In the "Return Values" section in the following descriptions, values in **BOLD** are not affected by the **TX_DISABLE_ERROR_CHECKING** define used to disable API error checking; while values shown in non-bold are completely disabled.</span></span>

- <span data-ttu-id="2a5a2-107">[tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) Выделение стека потоков в защищенной памяти.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-107">[tx_thread_secure_stack_allocate](#tx_thread_secure_stack_allocate) Allocate a thread stack in secure memory.</span></span>
- <span data-ttu-id="2a5a2-108">[tx_thread_secure_stack_free](#tx_thread_secure_stack_free) Высвобождение стека потоков в защищенной памяти.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-108">[tx_thread_secure_stack_free](#tx_thread_secure_stack_free) Free thread stack in secure memory</span></span>

## <a name="tx_thread_secure_stack_allocate"></a><span data-ttu-id="2a5a2-109">tx_thread_secure_stack_allocate</span><span class="sxs-lookup"><span data-stu-id="2a5a2-109">tx_thread_secure_stack_allocate</span></span>

<span data-ttu-id="2a5a2-110">Выделение стека потоков в защищенной памяти.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-110">Allocate a thread stack in secure memory.</span></span>

### <a name="prototype"></a><span data-ttu-id="2a5a2-111">Прототип</span><span class="sxs-lookup"><span data-stu-id="2a5a2-111">Prototype</span></span>

```c
UINT tx_thread_secure_stack_allocate(
    TX_THREAD *thread_ptr, 
    ULONG stack_size);
```

### <a name="description"></a><span data-ttu-id="2a5a2-112">Описание</span><span class="sxs-lookup"><span data-stu-id="2a5a2-112">Description</span></span>

<span data-ttu-id="2a5a2-113">Эта служба выделяет стек размером stack_size байт в защищенной памяти.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-113">This service allocates a stack of size stack_size bytes in secure memory.</span></span> <span data-ttu-id="2a5a2-114">Эта функция должна вызываться для каждого потока, который вызывает безопасные функции.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-114">This function should be called for every thread that calls secure functions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2a5a2-115">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2a5a2-115">Input Parameters</span></span>

- <span data-ttu-id="2a5a2-116">**ip_ptr** Указатель на ранее созданный поток.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-116">**thread_ptr** Pointer to previously created thread.</span></span>

- <span data-ttu-id="2a5a2-117">**stack_size** Размер безопасного стека.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-117">**stack_size** Size of secure stack.</span></span>

### <a name="return-values"></a><span data-ttu-id="2a5a2-118">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2a5a2-118">Return Values</span></span>

- <span data-ttu-id="2a5a2-119">**TX_SUCCESS** (0x00) Запрос выполнен.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-119">**TX_SUCCESS** (0x00) Successful request.</span></span>

- <span data-ttu-id="2a5a2-120">**TX_SIZE_ERROR** (0x05) Размер стека вне допустимого диапазона.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-120">**TX_SIZE_ERROR** (0x05) Stack size out of range.</span></span>

- <span data-ttu-id="2a5a2-121">**TX_THREAD_ERROR** (0x0E) Недопустимый указатель потока.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-121">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>

- <span data-ttu-id="2a5a2-122">**TX_NO_MEMORY** (0x10) Не удалось выделить память.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-122">**TX_NO_MEMORY** (0x10) Unable to allocate memory.</span></span>

- <span data-ttu-id="2a5a2-123">**NX_CALLER_ERROR (0x13)** Недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-123">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

- <span data-ttu-id="2a5a2-124">**TX_FEATURE_NOT_ENABLED** (0xFF) Система была скомпилирована для запуска в безопасном режиме.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-124">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled to run in secure mode.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2a5a2-125">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2a5a2-125">Allowed From</span></span>

<span data-ttu-id="2a5a2-126">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="2a5a2-126">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="2a5a2-127">Пример</span><span class="sxs-lookup"><span data-stu-id="2a5a2-127">Example</span></span>

```c
/* Create thread.  */
tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0, pointer, DEMO_STACK_SIZE, 1, 1, TX_NO_TIME_SLICE, TX_AUTO_START);

/* Allocate secure stack so this thread can call secure functions.  */
status = tx_thread_secure_stack_allocate(&thread_0, 256);

/* If status is TX_SUCCESS the request was successful.  */
```

### <a name="see-also"></a><span data-ttu-id="2a5a2-128">См. также:</span><span class="sxs-lookup"><span data-stu-id="2a5a2-128">See Also</span></span>

<span data-ttu-id="2a5a2-129">tx_thread_secure_stack_free</span><span class="sxs-lookup"><span data-stu-id="2a5a2-129">tx_thread_secure_stack_free</span></span>

##  <a name="tx_thread_secure_stack_free"></a><span data-ttu-id="2a5a2-130">tx_thread_secure_stack_free</span><span class="sxs-lookup"><span data-stu-id="2a5a2-130">tx_thread_secure_stack_free</span></span>

<span data-ttu-id="2a5a2-131">Высвобождение стека потоков в защищенной памяти.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-131">Free a thread stack in secure memory.</span></span> 

### <a name="prototype"></a><span data-ttu-id="2a5a2-132">Прототип</span><span class="sxs-lookup"><span data-stu-id="2a5a2-132">Prototype</span></span>

```c
UINT tx_thread_secure_stack_free(TX_THREAD *thread_ptr);
```

### <a name="description"></a><span data-ttu-id="2a5a2-133">Описание</span><span class="sxs-lookup"><span data-stu-id="2a5a2-133">Description</span></span>

<span data-ttu-id="2a5a2-134">Эта служба высвобождает безопасный стек потоков в защищенной памяти.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-134">This service frees a thread's secure stack in secure memory.</span></span> <span data-ttu-id="2a5a2-135">Эта функция должна вызываться, если поток имеет безопасный стек и когда потоку больше не требуется вызывать безопасные функции либо поток удален.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-135">This function should be called if a thread has a secure stack and when the thread no longer needs to call secure functions or the thread is deleted.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2a5a2-136">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2a5a2-136">Input Parameters</span></span>

- <span data-ttu-id="2a5a2-137">**ip_ptr** Указатель на ранее созданный поток.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-137">**thread_ptr** Pointer to previously created thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="2a5a2-138">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2a5a2-138">Return Values</span></span>

- <span data-ttu-id="2a5a2-139">**TX_SUCCESS** (0x00) Запрос выполнен.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-139">**TX_SUCCESS** (0x00) Successful request.</span></span>

- <span data-ttu-id="2a5a2-140">**TX_THREAD_ERROR** (0x0E) Недопустимый указатель потока.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-140">**TX_THREAD_ERROR** (0x0E) Invalid thread pointer.</span></span>

- <span data-ttu-id="2a5a2-141">**NX_CALLER_ERROR (0x13)** Недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-141">**TX_CALLER_ERROR** (0x13) Invalid caller of this service.</span></span>

- <span data-ttu-id="2a5a2-142">**TX_FEATURE_NOT_ENABLED** (0xFF) Система была скомпилирована для запуска в безопасном режиме.</span><span class="sxs-lookup"><span data-stu-id="2a5a2-142">**TX_FEATURE_NOT_ENABLED** (0xFF) The system was compiled to run in secure mode.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2a5a2-143">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2a5a2-143">Allowed From</span></span>

<span data-ttu-id="2a5a2-144">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="2a5a2-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="2a5a2-145">Пример</span><span class="sxs-lookup"><span data-stu-id="2a5a2-145">Example</span></span>

```c
/* Free thread’s secure stack.  */
status = tx_thread_secure_stack_free(&thread_0);

/* If status is TX_SUCCESS the request was successful.  */

/* Delete thread.  */
tx_thread_delete(&thread_0);
```

## <a name="see-also"></a><span data-ttu-id="2a5a2-146">См. также:</span><span class="sxs-lookup"><span data-stu-id="2a5a2-146">See Also</span></span>

<span data-ttu-id="2a5a2-147">tx_thread_secure_stack_allocate</span><span class="sxs-lookup"><span data-stu-id="2a5a2-147">tx_thread_secure_stack_allocate</span></span>
