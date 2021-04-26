---
title: API классов узлов USBX
description: В этой главе рассматриваются все предоставляемые API классов узлов USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 39f3a71c28dd14e0093f72d1a3b1ff6837c6f1f7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816128"
---
# <a name="chapter-2-usbx-host-classes-api"></a><span data-ttu-id="ea67e-103">Глава 2. API классов узлов USBX</span><span class="sxs-lookup"><span data-stu-id="ea67e-103">Chapter 2: USBX Host Classes API</span></span>

<span data-ttu-id="ea67e-104">В этой главе рассматриваются все предоставляемые API классов узлов USBX.</span><span class="sxs-lookup"><span data-stu-id="ea67e-104">This chapter covers all the exposed APIs of the USBX host classes.</span></span> <span data-ttu-id="ea67e-105">Ниже подробно описаны следующие интерфейсы API для каждого класса.</span><span class="sxs-lookup"><span data-stu-id="ea67e-105">The following APIs for each class are described in detail.</span></span>

- <span data-ttu-id="ea67e-106">Класс Printer.</span><span class="sxs-lookup"><span data-stu-id="ea67e-106">Printer class</span></span>
- <span data-ttu-id="ea67e-107">Класс Audio.</span><span class="sxs-lookup"><span data-stu-id="ea67e-107">Audio class</span></span>
- <span data-ttu-id="ea67e-108">Класс Asix.</span><span class="sxs-lookup"><span data-stu-id="ea67e-108">Asix class</span></span>
- <span data-ttu-id="ea67e-109">Класс Pima/PTP.</span><span class="sxs-lookup"><span data-stu-id="ea67e-109">Pima/PTP class</span></span>
- <span data-ttu-id="ea67e-110">Класс Prolific.</span><span class="sxs-lookup"><span data-stu-id="ea67e-110">Prolific class</span></span>
- <span data-ttu-id="ea67e-111">Класс Generic Serial.</span><span class="sxs-lookup"><span data-stu-id="ea67e-111">Generic Serial class</span></span>

## <a name="ux_host_class_printer_read"></a><span data-ttu-id="ea67e-112">ux_host_class_printer_read</span><span class="sxs-lookup"><span data-stu-id="ea67e-112">ux_host_class_printer_read</span></span>

<span data-ttu-id="ea67e-113">Чтение из интерфейса принтера.</span><span class="sxs-lookup"><span data-stu-id="ea67e-113">Read from the printer interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-114">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-114">Prototype</span></span>

```C
UINT ux_host_class_printer_read(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="ea67e-115">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-115">Description</span></span>

<span data-ttu-id="ea67e-116">Эта функция считывает данные из интерфейса принтера.</span><span class="sxs-lookup"><span data-stu-id="ea67e-116">This function reads from the printer interface.</span></span> <span data-ttu-id="ea67e-117">Вызов блокируется и возвращается только в случае ошибки или завершения передачи.</span><span class="sxs-lookup"><span data-stu-id="ea67e-117">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span> <span data-ttu-id="ea67e-118">Чтение разрешено только на двунаправленных принтерах.</span><span class="sxs-lookup"><span data-stu-id="ea67e-118">A read is allowed only on bi-directional printers.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-119">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-119">Parameters</span></span>

- <span data-ttu-id="ea67e-120">**printer** — указатель на экземпляр класса Printer.</span><span class="sxs-lookup"><span data-stu-id="ea67e-120">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="ea67e-121">**data_pointer** — указатель на адрес буфера полезных данных.</span><span class="sxs-lookup"><span data-stu-id="ea67e-121">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="ea67e-122">**requested_length** — длина для получения.</span><span class="sxs-lookup"><span data-stu-id="ea67e-122">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="ea67e-123">**actual_length** — фактическая полученная длина.</span><span class="sxs-lookup"><span data-stu-id="ea67e-123">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-124">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-124">Return Value</span></span>

- <span data-ttu-id="ea67e-125">**UX_SUCCESS**: (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-125">**UX_SUCCESS**:  (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="ea67e-126">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) — функция не поддерживается, так как принтер не является двунаправленным.</span><span class="sxs-lookup"><span data-stu-id="ea67e-126">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported because the printer is not bi-directional.</span></span>
- <span data-ttu-id="ea67e-127">**UX_TRANSFER_TIMEOUT**: (0x5c) — превышение времени ожидания передачи, чтение не завершено.</span><span class="sxs-lookup"><span data-stu-id="ea67e-127">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-128">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-128">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_read(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_write"></a><span data-ttu-id="ea67e-129">ux_host_class_printer_write</span><span class="sxs-lookup"><span data-stu-id="ea67e-129">ux_host_class_printer_write</span></span>

<span data-ttu-id="ea67e-130">Запись в интерфейс принтера.</span><span class="sxs-lookup"><span data-stu-id="ea67e-130">Write to the printer interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-131">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-131">Prototype</span></span>

```C
UINT ux_host_class_printer_write(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,  
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="ea67e-132">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-132">Description</span></span>

<span data-ttu-id="ea67e-133">Эта функция записывает данные в интерфейс принтера.</span><span class="sxs-lookup"><span data-stu-id="ea67e-133">This function writes to the printer interface.</span></span> <span data-ttu-id="ea67e-134">Вызов блокируется и возвращается только в случае ошибки или завершения передачи.</span><span class="sxs-lookup"><span data-stu-id="ea67e-134">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-135">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-135">Parameters</span></span>

- <span data-ttu-id="ea67e-136">**printer** — указатель на экземпляр класса Printer.</span><span class="sxs-lookup"><span data-stu-id="ea67e-136">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="ea67e-137">**data_pointer** — указатель на адрес буфера полезных данных.</span><span class="sxs-lookup"><span data-stu-id="ea67e-137">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="ea67e-138">**requested_length** — длина для отправки.</span><span class="sxs-lookup"><span data-stu-id="ea67e-138">**requested_length**: Length to be sent.</span></span>
- <span data-ttu-id="ea67e-139">**actual_length** — фактическая отправленная длина.</span><span class="sxs-lookup"><span data-stu-id="ea67e-139">**actual_length**: Length actually sent.</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-140">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-140">Return Value</span></span>

- <span data-ttu-id="ea67e-141">**UX_SUCCESS**: (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-141">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="ea67e-142">**UX_TRANSFER_TIMEOUT**: (0x5c) — превышение времени ожидания передачи, запись не завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-142">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-143">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-143">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_write(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_soft_reset"></a><span data-ttu-id="ea67e-144">ux_host_class_printer_soft_reset</span><span class="sxs-lookup"><span data-stu-id="ea67e-144">ux_host_class_printer_soft_reset</span></span>

<span data-ttu-id="ea67e-145">Выполнение программного сброса принтера.</span><span class="sxs-lookup"><span data-stu-id="ea67e-145">Perform a soft reset to the printer.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-146">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-146">Prototype</span></span>

```C
UINT ux_host_class_printer_soft_reset(UX_HOST_CLASS_PRINTER *printer)
```

### <a name="description"></a><span data-ttu-id="ea67e-147">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-147">Description</span></span>

<span data-ttu-id="ea67e-148">Эта функция выполняет программный сброс принтера.</span><span class="sxs-lookup"><span data-stu-id="ea67e-148">This function performs a soft reset to the printer.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="ea67e-149">Входной параметр</span><span class="sxs-lookup"><span data-stu-id="ea67e-149">Input Parameter</span></span>

- <span data-ttu-id="ea67e-150">**printer** — указатель на экземпляр класса Printer.</span><span class="sxs-lookup"><span data-stu-id="ea67e-150">**printer**: Pointer to the printer class instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-151">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-151">Return Value</span></span>

- <span data-ttu-id="ea67e-152">**UX_SUCCESS**: (0x00) — сброс завершен.</span><span class="sxs-lookup"><span data-stu-id="ea67e-152">**UX_SUCCESS**: (0x00)The reset was completed.</span></span>
- <span data-ttu-id="ea67e-153">**UX_TRANSFER_TIMEOUT**: (0x5c) — превышение времени ожидания передачи, сброс не завершен.</span><span class="sxs-lookup"><span data-stu-id="ea67e-153">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reset not completed.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-154">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-154">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_soft_reset(printer);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_status_get"></a><span data-ttu-id="ea67e-155">ux_host_class_printer_status_get</span><span class="sxs-lookup"><span data-stu-id="ea67e-155">ux_host_class_printer_status_get</span></span>

<span data-ttu-id="ea67e-156">Получение состояния принтера</span><span class="sxs-lookup"><span data-stu-id="ea67e-156">Get the printer status</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-157">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-157">Prototype</span></span>

```C
UINT ux_host_class_printer_status_get( 
    UX_HOST_CLASS_PRINTER *printer,
    ULONG *printer_status)
```

### <a name="description"></a><span data-ttu-id="ea67e-158">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-158">Description</span></span>

<span data-ttu-id="ea67e-159">Эта функция получает состояние принтера.</span><span class="sxs-lookup"><span data-stu-id="ea67e-159">This function obtains the printer status.</span></span> <span data-ttu-id="ea67e-160">Состояние принтера похоже на состояние LPT (стандарт 1284).</span><span class="sxs-lookup"><span data-stu-id="ea67e-160">The printer status is similar to the LPT status (1284 standard).</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-161">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-161">Parameters</span></span>

- <span data-ttu-id="ea67e-162">**printer** — указатель на экземпляр класса Printer.</span><span class="sxs-lookup"><span data-stu-id="ea67e-162">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="ea67e-163">**printer_status** — адрес возвращаемого состояния.</span><span class="sxs-lookup"><span data-stu-id="ea67e-163">**printer_status**: Address of the status to be returned.</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-164">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-164">Return Value</span></span>

- <span data-ttu-id="ea67e-165">**UX_SUCCESS** (0x00) — сброс завершен.</span><span class="sxs-lookup"><span data-stu-id="ea67e-165">**UX_SUCCESS** (0x00): The reset was completed.</span></span>
- <span data-ttu-id="ea67e-166">**UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для выполнения этой операции.</span><span class="sxs-lookup"><span data-stu-id="ea67e-166">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to perform the operation.</span></span>
- <span data-ttu-id="ea67e-167">**UX_TRANSFER_TIMEOUT**: (0x5c) — превышение времени ожидания передачи, сброс не завершен</span><span class="sxs-lookup"><span data-stu-id="ea67e-167">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reset not completed</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-168">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-168">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_status_get(printer, printer_status);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_device_id_get"></a><span data-ttu-id="ea67e-169">ux_host_class_printer_device_id_get</span><span class="sxs-lookup"><span data-stu-id="ea67e-169">ux_host_class_printer_device_id_get</span></span>

<span data-ttu-id="ea67e-170">Получение кода устройства принтера.</span><span class="sxs-lookup"><span data-stu-id="ea67e-170">Get the printer device id.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-171">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-171">Prototype</span></span>

```C
UINT ux_host_class_printer_device_id_get( 
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *descriptor_buffer, 
    ULONG length)
```

### <a name="description"></a><span data-ttu-id="ea67e-172">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-172">Description</span></span>

<span data-ttu-id="ea67e-173">Эта функция получает строку кода устройства принтера IEEE 1284 (включая длину первых двух байтов в формате с обратным порядком байтов).</span><span class="sxs-lookup"><span data-stu-id="ea67e-173">This function obtains the printer IEEE 1284 device ID string (including length in the first two bytes in big endian format).</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-174">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-174">Parameters</span></span>

- <span data-ttu-id="ea67e-175">**printer** — указатель на экземпляр класса Printer.</span><span class="sxs-lookup"><span data-stu-id="ea67e-175">**printer**: Pointer to the printer class instance.</span></span>
- <span data-ttu-id="ea67e-176">**descriptor_buffer** — указатель на буфер для заполнения строки кода устройства IEEE 1284 (включая длину первых двух байтов в формате с обратным порядком байтов).</span><span class="sxs-lookup"><span data-stu-id="ea67e-176">**descriptor_buffer**: Pointer to a buffer to fill IEEE 1284 device ID string (including length in the first two bytes in BE format)</span></span> 
- <span data-ttu-id="ea67e-177">**length** — длина буфера в байтах.</span><span class="sxs-lookup"><span data-stu-id="ea67e-177">**length**: Length of buffer in bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-178">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-178">Return Value</span></span>

- <span data-ttu-id="ea67e-179">**UX_SUCCESS** (0x00) — операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-179">**UX_SUCCESS** (0x00): The operation was successful.</span></span>
- <span data-ttu-id="ea67e-180">**UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для выполнения этой операции.</span><span class="sxs-lookup"><span data-stu-id="ea67e-180">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to perform the operation.</span></span>
- <span data-ttu-id="ea67e-181">**UX_TRANSFER_TIMEOUT**: (0x5c) — превышение времени ожидания передачи, запрос не завершен.</span><span class="sxs-lookup"><span data-stu-id="ea67e-181">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, request not completed</span></span>
- <span data-ttu-id="ea67e-182">**UX_TRANSFER_NOT_READY**: (0x25) — устройство находилось в недопустимом состоянии (допустимые состояния: ATTACHED, ADDRESSED или CONFIGURED).</span><span class="sxs-lookup"><span data-stu-id="ea67e-182">**UX_TRANSFER_NOT_READY**: (0x25) The device was in an invalid state – must be ATTACHED,ADDRESSED, or CONFIGURED.</span></span>
- <span data-ttu-id="ea67e-183">**UX_TRANSFER_STALL**: (0x21) — передача остановлена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-183">**UX_TRANSFER_STALL**: (0x21) Transfer stalled.</span></span>
- <span data-ttu-id="ea67e-184">**TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.</span><span class="sxs-lookup"><span data-stu-id="ea67e-184">**TX_WAIT_ABORTED** (0x1A) Suspension was aborted by another thread, timer, or ISR.</span></span>
- <span data-ttu-id="ea67e-185">**TX_SEMAPHORE_ERROR** (0x0C) — недопустимый указатель на семафор со счетчиком.</span><span class="sxs-lookup"><span data-stu-id="ea67e-185">**TX_SEMAPHORE_ERROR** (0x0C) Invalid counting semaphore pointer.</span></span>
- <span data-ttu-id="ea67e-186">**TX_WAIT_ERROR** (0x04) — в вызове из непотокового запроса был указан параметр ожидания, отличный от TX_NO_WAIT.</span><span class="sxs-lookup"><span data-stu-id="ea67e-186">**TX_WAIT_ERROR** (0x04) A wait option other than TX_NO_WAIT was specified on a call from a non-thread.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-187">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-187">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_device_id_get(printer, descriptor_buffer, length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_read"></a><span data-ttu-id="ea67e-188">ux_host_class_audio_read</span><span class="sxs-lookup"><span data-stu-id="ea67e-188">ux_host_class_audio_read</span></span>

<span data-ttu-id="ea67e-189">Чтение из интерфейса аудио.</span><span class="sxs-lookup"><span data-stu-id="ea67e-189">Read from the audio interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-190">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-190">Prototype</span></span>

```C
UINT ux_host_class_audio_read(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST
    *audio_transfer_request)
```

### <a name="description"></a><span data-ttu-id="ea67e-191">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-191">Description</span></span>

<span data-ttu-id="ea67e-192">Эта функция считывает данные из интерфейса аудио.</span><span class="sxs-lookup"><span data-stu-id="ea67e-192">This function reads from the audio interface.</span></span> <span data-ttu-id="ea67e-193">Этот вызов не блокируется.</span><span class="sxs-lookup"><span data-stu-id="ea67e-193">The call is non-blocking.</span></span> <span data-ttu-id="ea67e-194">Приложение должно убедиться, что для интерфейса потоковой передачи аудио выбран соответствующий альтернативный параметр.</span><span class="sxs-lookup"><span data-stu-id="ea67e-194">The application must ensure that the appropriate alternate setting has been selected for the audio streaming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-195">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-195">Parameters</span></span>

- <span data-ttu-id="ea67e-196">**audio** — указатель на экземпляр класса Audio.</span><span class="sxs-lookup"><span data-stu-id="ea67e-196">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="ea67e-197">**audio_transfer_request** — указатель на структуру передачи аудио.</span><span class="sxs-lookup"><span data-stu-id="ea67e-197">**audio_transfer_request**: Pointer to the audio transfer structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-198">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-198">Return Value</span></span>

- <span data-ttu-id="ea67e-199">**UX_SUCCESS**: (0x00) — передача данных завершена</span><span class="sxs-lookup"><span data-stu-id="ea67e-199">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="ea67e-200">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) — функция не поддерживается</span><span class="sxs-lookup"><span data-stu-id="ea67e-200">**UX_FUNCTION_NOT_SUPPORTED**" (0x54) Function not supported</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-201">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-201">Example</span></span>

```C
/* The following example reads from the audio interface. */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;

status = ux_host_class_audio_read(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_write"></a><span data-ttu-id="ea67e-202">ux_host_class_audio_write</span><span class="sxs-lookup"><span data-stu-id="ea67e-202">ux_host_class_audio_write</span></span>

<span data-ttu-id="ea67e-203">Запись в интерфейс аудио.</span><span class="sxs-lookup"><span data-stu-id="ea67e-203">Write to the audio interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-204">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-204">Prototype</span></span>

```C
UINT ux_host_class_audio_write(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST *audio_transfer_request)
```

### <a name="description"></a><span data-ttu-id="ea67e-205">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-205">Description</span></span>

<span data-ttu-id="ea67e-206">Эта функция записывает данные в интерфейс аудио.</span><span class="sxs-lookup"><span data-stu-id="ea67e-206">This function writes to the audio interface.</span></span> <span data-ttu-id="ea67e-207">Этот вызов не блокируется.</span><span class="sxs-lookup"><span data-stu-id="ea67e-207">The call is non-blocking.</span></span> <span data-ttu-id="ea67e-208">Приложение должно убедиться, что для интерфейса потоковой передачи аудио выбран соответствующий альтернативный параметр.</span><span class="sxs-lookup"><span data-stu-id="ea67e-208">The application must ensure that the appropriate alternate setting has been selected for the audio streaming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-209">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-209">Parameters</span></span>

- <span data-ttu-id="ea67e-210">**audio** — указатель на экземпляр класса Audio</span><span class="sxs-lookup"><span data-stu-id="ea67e-210">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="ea67e-211">**audio_transfer_request** — указатель на структуру передачи аудио</span><span class="sxs-lookup"><span data-stu-id="ea67e-211">**audio_transfer_request**: Pointer to the audio transfer structure</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-212">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-212">Return Value</span></span>

- <span data-ttu-id="ea67e-213">**UX_SUCCESS**: (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-213">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="ea67e-214">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) — функция не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="ea67e-214">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported.</span></span>
- <span data-ttu-id="ea67e-215">**ux_host_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) — недопустимый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ea67e-215">**ux_host_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-216">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-216">Example</span></span>

```C
UINT status;

/* The following example writes to the audio interface */

audio_transfer_request.ux_host_class_audio_transfer_request_completion_function = tx_audio_transfer_completion_function;
audio_transfer_request.ux_host_class_audio_transfer_request_class_instance = audio;
audio_transfer_request.ux_host_class_audio_transfer_request_next_audio_audio_transfer_request = UX_NULL;
audio_transfer_request.ux_host_class_audio_transfer_request_data_pointer = audio_buffer;
audio_transfer_request.ux_host_class_audio_transfer_request_requested_length = requested_length;
audio_transfer_request.ux_host_class_audio_transfer_request_packet_length = AUDIO_FRAME_LENGTH;
status = ux_host_class_audio_write(audio, audio_transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_get"></a><span data-ttu-id="ea67e-217">ux_host_class_audio_control_get</span><span class="sxs-lookup"><span data-stu-id="ea67e-217">ux_host_class_audio_control_get</span></span>

<span data-ttu-id="ea67e-218">Получение конкретного элемента управления из интерфейса управления звуком.</span><span class="sxs-lookup"><span data-stu-id="ea67e-218">Get a specific control from the audio control interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-219">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-219">Prototype</span></span>

```C
UINT ux_host_class_audio_control_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

### <a name="description"></a><span data-ttu-id="ea67e-220">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-220">Description</span></span>

<span data-ttu-id="ea67e-221">Эта функция считывает конкретный элемент управления из интерфейса управления звуком.</span><span class="sxs-lookup"><span data-stu-id="ea67e-221">This function reads a specific control from the audio control interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-222">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-222">Parameters</span></span>

- <span data-ttu-id="ea67e-223">**audio** — указатель на экземпляр класса Audio</span><span class="sxs-lookup"><span data-stu-id="ea67e-223">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="ea67e-224">**audio_control** — указатель на структуру управления аудио.</span><span class="sxs-lookup"><span data-stu-id="ea67e-224">**audio_control**: Pointer to the audio control structure</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-225">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-225">Return Value</span></span>

- <span data-ttu-id="ea67e-226">**UX_SUCCESS**: (0x00) — передача данных завершена</span><span class="sxs-lookup"><span data-stu-id="ea67e-226">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="ea67e-227">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) — функция не поддерживается</span><span class="sxs-lookup"><span data-stu-id="ea67e-227">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="ea67e-228">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) — недопустимый интерфейс</span><span class="sxs-lookup"><span data-stu-id="ea67e-228">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-229">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-229">Example</span></span>

```C
UINT status;

/* The following example reads the volume control from a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */

audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;

status = ux_host_class_audio_control_get(audio, &audio_control);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_control_value_set"></a><span data-ttu-id="ea67e-230">ux_host_class_audio_control_value_set</span><span class="sxs-lookup"><span data-stu-id="ea67e-230">ux_host_class_audio_control_value_set</span></span>

<span data-ttu-id="ea67e-231">Указание конкретного элемента управления для интерфейса управления аудио.</span><span class="sxs-lookup"><span data-stu-id="ea67e-231">Set a specific control to the audio control interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-232">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-232">Prototype</span></span>

```C
UINT ux_host_class_audio_control_value_set(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

<span data-ttu-id="ea67e-233">**Описание **</span><span class="sxs-lookup"><span data-stu-id="ea67e-233">\*\*Description \*\*</span></span>

<span data-ttu-id="ea67e-234">Эта функция задает конкретный элемент управления для интерфейса управления аудио.</span><span class="sxs-lookup"><span data-stu-id="ea67e-234">This function sets a specific control to the audio control interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-235">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-235">Parameters</span></span>

- <span data-ttu-id="ea67e-236">**audio** — указатель на экземпляр класса Audio</span><span class="sxs-lookup"><span data-stu-id="ea67e-236">**audio**: Pointer to the audio class instance</span></span>
- <span data-ttu-id="ea67e-237">**audio_control** — указатель на структуру управления аудио.</span><span class="sxs-lookup"><span data-stu-id="ea67e-237">**audio_control**: Pointer to the audio control structure</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-238">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-238">Return Value</span></span>

- <span data-ttu-id="ea67e-239">**UX_SUCCESS**: (0x00) — передача данных завершена</span><span class="sxs-lookup"><span data-stu-id="ea67e-239">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="ea67e-240">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) — функция не поддерживается</span><span class="sxs-lookup"><span data-stu-id="ea67e-240">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="ea67e-241">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) — недопустимый интерфейс</span><span class="sxs-lookup"><span data-stu-id="ea67e-241">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-242">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-242">Example</span></span>

```C
/* The following example sets the volume control of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_CONTROL audio_control;

UINT status;

audio_control.ux_host_class_audio_control_channel = 1;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */

current_volume = audio_control.audio_control_cur;
audio_control.ux_host_class_audio_control_channel = 2;
audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
audio_control.ux_host_class_audio_control_cur = 0xf000;

status = ux_host_class_audio_control_value_set(audio, &audio_control);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_set"></a><span data-ttu-id="ea67e-243">ux_host_class_audio_streaming_sampling_set</span><span class="sxs-lookup"><span data-stu-id="ea67e-243">ux_host_class_audio_streaming_sampling_set</span></span>

<span data-ttu-id="ea67e-244">Указание альтернативного параметра для интерфейса потоковой передачи аудио.</span><span class="sxs-lookup"><span data-stu-id="ea67e-244">Set an alternate setting interface of the audio streaming interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-245">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-245">Prototype</span></span>

```C
UINT ux_host_class_audio_streaming_sampling_set
    (UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING *audio_sampling)
```

### <a name="description"></a><span data-ttu-id="ea67e-246">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-246">Description</span></span>

<span data-ttu-id="ea67e-247">Эта функция задает подходящий альтернативный параметр для интерфейса потоковой передачи аудио в соответствии с определенной структурой выборки.</span><span class="sxs-lookup"><span data-stu-id="ea67e-247">This function sets the appropriate alternate setting interface of the audio streaming interface according to a specific sampling structure.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-248">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-248">Parameters</span></span>

- <span data-ttu-id="ea67e-249">**audio** — указатель на экземпляр класса Audio.</span><span class="sxs-lookup"><span data-stu-id="ea67e-249">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="ea67e-250">**audio_sampling** — указатель на структуру выборки аудио.</span><span class="sxs-lookup"><span data-stu-id="ea67e-250">**audio_sampling**: Pointer to the audio sampling structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-251">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-251">Return Value</span></span>

- <span data-ttu-id="ea67e-252">**UX_SUCCESS**: (0x00) — передача данных завершена</span><span class="sxs-lookup"><span data-stu-id="ea67e-252">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="ea67e-253">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) — функция не поддерживается</span><span class="sxs-lookup"><span data-stu-id="ea67e-253">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="ea67e-254">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) — недопустимый интерфейс</span><span class="sxs-lookup"><span data-stu-id="ea67e-254">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>
- <span data-ttu-id="ea67e-255">**UX_NO_ALTERNATE_SETTING**: (0x5e) — отсутствует альтернативный параметр для значений выборки.</span><span class="sxs-lookup"><span data-stu-id="ea67e-255">**UX_NO_ALTERNATE_SETTING**: (0x5e) No alternate setting for the sampling values</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-256">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-256">Example</span></span>

```C
/* The following example sets the alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels = 2;
sampling.ux_host_class_audio_sampling_frequency = AUDIO_FREQUENCY;
sampling. ux_host_class_audio_sampling_resolution = 16;

status = ux_host_class_audio_streaming_sampling_set(audio, &sampling);
/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_streaming_sampling_get"></a><span data-ttu-id="ea67e-257">ux_host_class_audio_streaming_sampling_get</span><span class="sxs-lookup"><span data-stu-id="ea67e-257">ux_host_class_audio_streaming_sampling_get</span></span>

<span data-ttu-id="ea67e-258">Получение возможных параметров выборки для интерфейса потоковой передачи аудио.</span><span class="sxs-lookup"><span data-stu-id="ea67e-258">Get possible sampling settings of audio streaming interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-259">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-259">Prototype</span></span>

```C
UINT ux_host_class_audio_streaming_sampling_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS *audio_sampling)
```

### <a name="description"></a><span data-ttu-id="ea67e-260">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-260">Description</span></span>

<span data-ttu-id="ea67e-261">Эта функция получает по очереди все возможные параметры выборки, доступные в каждом из альтернативных параметров интерфейса потоковой передачи звука.</span><span class="sxs-lookup"><span data-stu-id="ea67e-261">This function gets, one by one, all the possible sampling settings available in each of the alternate settings of the audio streaming interface.</span></span> <span data-ttu-id="ea67e-262">При первом использовании функции все поля в указателе структуры вызовов должны быть сброшены.</span><span class="sxs-lookup"><span data-stu-id="ea67e-262">The first time the function is used, all the fields in the calling structure pointer must be reset.</span></span> <span data-ttu-id="ea67e-263">Функция будет возвращать конкретный набор значений потоковой передачи при возврате, если не достигнут конец альтернативных параметров.</span><span class="sxs-lookup"><span data-stu-id="ea67e-263">The function will return a specific set of streaming values upon return unless the end of the alternate settings has been reached.</span></span> <span data-ttu-id="ea67e-264">При повторном использовании этой функции для поиска следующих значений выборки будут использоваться ее предыдущие значения.</span><span class="sxs-lookup"><span data-stu-id="ea67e-264">When this function is reused, the previous sampling values will be used to find the next sampling values.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-265">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-265">Parameters</span></span>

- <span data-ttu-id="ea67e-266">**audio** — указатель на экземпляр класса Audio.</span><span class="sxs-lookup"><span data-stu-id="ea67e-266">**audio**: Pointer to the audio class instance.</span></span>
- <span data-ttu-id="ea67e-267">**audio_sampling** — указатель на структуру выборки аудио.</span><span class="sxs-lookup"><span data-stu-id="ea67e-267">**audio_sampling**: Pointer to the audio sampling structure.</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-268">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-268">Return Value</span></span>

- <span data-ttu-id="ea67e-269">**UX_SUCCESS**: (0x00) — передача данных завершена</span><span class="sxs-lookup"><span data-stu-id="ea67e-269">**UX_SUCCESS**: (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="ea67e-270">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) — функция не поддерживается</span><span class="sxs-lookup"><span data-stu-id="ea67e-270">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Function not supported</span></span>
- <span data-ttu-id="ea67e-271">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) — недопустимый интерфейс</span><span class="sxs-lookup"><span data-stu-id="ea67e-271">**UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) Interface incorrect</span></span>
- <span data-ttu-id="ea67e-272">**UX_NO_ALTERNATE_SETTING**: (0x5e) — отсутствует альтернативный параметр для значений выборки.</span><span class="sxs-lookup"><span data-stu-id="ea67e-272">**UX_NO_ALTERNATE_SETTING**: (0x5e) No alternate setting for the sampling values</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-273">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-273">Example</span></span>

```C
/* The following example gets the sampling values for the first alternate setting interface of a stereo USB speaker. */

UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS audio_sampling;

UINT status;

sampling.ux_host_class_audio_sampling_channels=0;
sampling.ux_host_class_audio_sampling_frequency_low=0;
sampling.ux_host_class_audio_sampling_frequency_high=0;
sampling.ux_host_class_audio_sampling_resolution=0;

status = ux_host_class_audio_streaming_sampling_get(audio, &sampling);

/* If status equals UX_SUCCESS, the operation was successful and information could be displayed as follows:

printf("Number of channels %d, Resolution %d bits, frequency range %d-%d\n",
    sampling.audio_channels, sampling.audio_resolution,
    sampling.audio_frequency_low, sampling.audio_frequency_high);

*/
```

## <a name="ux_host_class_asix_read"></a><span data-ttu-id="ea67e-274">ux_host_class_asix_read</span><span class="sxs-lookup"><span data-stu-id="ea67e-274">ux_host_class_asix_read</span></span>

<span data-ttu-id="ea67e-275">Чтение из интерфейса asix.</span><span class="sxs-lookup"><span data-stu-id="ea67e-275">Read from the asix interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-276">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-276">Prototype</span></span>

```C
UINT ux_host_class_asix_read(
    UX_HOST_CLASS_ASIX *asix,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="ea67e-277">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-277">Description</span></span>

<span data-ttu-id="ea67e-278">Эта функция считывает данные из интерфейса asix.</span><span class="sxs-lookup"><span data-stu-id="ea67e-278">This function reads from the asix interface.</span></span> <span data-ttu-id="ea67e-279">Вызов блокируется и возвращается только в случае ошибки или завершения передачи.</span><span class="sxs-lookup"><span data-stu-id="ea67e-279">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-280">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-280">Parameters</span></span>

- <span data-ttu-id="ea67e-281">**asix** — указатель на экземпляр класса Asix.</span><span class="sxs-lookup"><span data-stu-id="ea67e-281">**asix**: Pointer to the asix class instance.</span></span>
- <span data-ttu-id="ea67e-282">**data_pointer** — указатель на адрес буфера полезных данных.</span><span class="sxs-lookup"><span data-stu-id="ea67e-282">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="ea67e-283">**requested_length** — длина для получения.</span><span class="sxs-lookup"><span data-stu-id="ea67e-283">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="ea67e-284">**actual_length** — фактическая полученная длина.</span><span class="sxs-lookup"><span data-stu-id="ea67e-284">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-285">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-285">Return Value</span></span>

- <span data-ttu-id="ea67e-286">**UX_SUCCESS**: (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-286">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="ea67e-287">**UX_TRANSFER_TIMEOUT**: (0x5c) — превышение времени ожидания передачи, чтение не завершено.</span><span class="sxs-lookup"><span data-stu-id="ea67e-287">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-288">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-288">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_read(asix, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_asix_write"></a><span data-ttu-id="ea67e-289">ux_host_class_asix_write</span><span class="sxs-lookup"><span data-stu-id="ea67e-289">ux_host_class_asix_write</span></span>

<span data-ttu-id="ea67e-290">Запись в интерфейс asix.</span><span class="sxs-lookup"><span data-stu-id="ea67e-290">Write to the asix interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-291">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-291">Prototype</span></span>

```C
UINT ux_host_class_asix_write(
    VOID *asix_class,
    NX_PACKET *packet)
```

### <a name="description"></a><span data-ttu-id="ea67e-292">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-292">Description</span></span>

<span data-ttu-id="ea67e-293">Эта функция записывает данные в интерфейс asix.</span><span class="sxs-lookup"><span data-stu-id="ea67e-293">This function writes to the asix interface.</span></span> <span data-ttu-id="ea67e-294">Этот вызов не блокируется.</span><span class="sxs-lookup"><span data-stu-id="ea67e-294">The call is non blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-295">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-295">Parameters</span></span>

- <span data-ttu-id="ea67e-296">**asix** — указатель на экземпляр класса Asix.</span><span class="sxs-lookup"><span data-stu-id="ea67e-296">**asix**: Pointer to the asix class instance.</span></span>
- <span data-ttu-id="ea67e-297">**packet** — пакет данных Netx.</span><span class="sxs-lookup"><span data-stu-id="ea67e-297">**packet**: Netx data packet</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-298">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-298">Return Value</span></span>

- <span data-ttu-id="ea67e-299">**UX_SUCCESS**: (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-299">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="ea67e-300">**UX_ERROR**: (0xFF) — невозможно запросить передачу.</span><span class="sxs-lookup"><span data-stu-id="ea67e-300">**UX_ERROR**: (0xFF) Transfer could not be requested.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-301">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-301">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_write(asix, packet);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_pima_session_open"></a><span data-ttu-id="ea67e-302">ux_host_class_pima_session_open</span><span class="sxs-lookup"><span data-stu-id="ea67e-302">ux_host_class_pima_session_open</span></span>

<span data-ttu-id="ea67e-303">Открытие сеанса между инициатором и отвечающим устройством.</span><span class="sxs-lookup"><span data-stu-id="ea67e-303">Open a session between Initiator and Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-304">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-304">Prototype</span></span>

```C
UINT ux_host_class_pima_session_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a><span data-ttu-id="ea67e-305">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-305">Description</span></span>

<span data-ttu-id="ea67e-306">Эта функция открывает сеанс между инициатором PIMA и отвечающим устройством PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-306">This function opens a session between a PIMA Initiator and a PIMA Responder.</span></span> <span data-ttu-id="ea67e-307">После успешного открытия сеанса можно выполнить большинство команд PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-307">Once a session is successfully opened, most PIMA commands can be executed.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-308">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-308">Parameters</span></span>

- <span data-ttu-id="ea67e-309">**pima** — указатель на экземпляр класса Pima.</span><span class="sxs-lookup"><span data-stu-id="ea67e-309">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="ea67e-310">**pima_session** — указатель на сеанс PIMA<</span><span class="sxs-lookup"><span data-stu-id="ea67e-310">**pima_sessio**: Pointer to PIMA session<</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-311">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-311">Return Value</span></span>

- <span data-ttu-id="ea67e-312">**UX_SUCCESS**: (0X00) — сеанс успешно открыт.</span><span class="sxs-lookup"><span data-stu-id="ea67e-312">**UX_SUCCESS**: (0x00) Session successfully opened</span></span>
- <span data-ttu-id="ea67e-313">**UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201E) — сеанс уже открыт.</span><span class="sxs-lookup"><span data-stu-id="ea67e-313">**UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201E) Session already opened</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-314">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-314">Example</span></span>

```C
/* Open a pima session. */

status = ux_host_class_pima_session_open(pima, pima_session);

if (status != UX_SUCCESS)
    return(UX_PICTBRIDGE_ERROR_SESSION_NOT_OPEN);
```

## <a name="ux_host_class_pima_session_close"></a><span data-ttu-id="ea67e-315">ux_host_class_pima_session_close</span><span class="sxs-lookup"><span data-stu-id="ea67e-315">ux_host_class_pima_session_close</span></span>

<span data-ttu-id="ea67e-316">Закрытие сеанса между инициатором и отвечающим устройством.</span><span class="sxs-lookup"><span data-stu-id="ea67e-316">Close a session between Initiator and Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-317">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-317">Prototype</span></span>

```C
UINT ux_host_class_pima_session_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a><span data-ttu-id="ea67e-318">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-318">Description</span></span>

<span data-ttu-id="ea67e-319">Эта функция закрывает сеанс, который ранее открывался между инициатором PIMA и отвечающим устройством PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-319">This function closes a session that was previously opened between a PIMA Initiator and a PIMA Responder.</span></span> <span data-ttu-id="ea67e-320">После закрытия сеанса большинство команд PIMA больше не будут выполняться.</span><span class="sxs-lookup"><span data-stu-id="ea67e-320">Once a session is closed, most PIMA commands can no longer be executed.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-321">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-321">Parameters</span></span>

- <span data-ttu-id="ea67e-322">**pima** — указатель на экземпляр класса Pima.</span><span class="sxs-lookup"><span data-stu-id="ea67e-322">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="ea67e-323">**pima_session** — указатель на сеанс PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-323">**pima_session**: Pointer to PIMA session.</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-324">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-324">Return Value</span></span>

- <span data-ttu-id="ea67e-325">**UX_SUCCESS**: (0x00) — сеанс закрыт.</span><span class="sxs-lookup"><span data-stu-id="ea67e-325">**UX_SUCCESS**: (0x00) The session was closed.</span></span>
- <span data-ttu-id="ea67e-326">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт.</span><span class="sxs-lookup"><span data-stu-id="ea67e-326">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-327">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-327">Example</span></span>

```C
/* Close the pima session. */

status = ux_host_class_pima_session_close(pima, pima_session);
```

## <a name="ux_host_class_pima_storage_ids_get"></a><span data-ttu-id="ea67e-328">ux_host_class_pima_storage_ids_get</span><span class="sxs-lookup"><span data-stu-id="ea67e-328">ux_host_class_pima_storage_ids_get</span></span>

<span data-ttu-id="ea67e-329">Получение массива идентификаторов хранилища из отвечающего устройства.</span><span class="sxs-lookup"><span data-stu-id="ea67e-329">Obtain the storage ID array from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-330">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-330">Prototype</span></span>

```C
UINT ux_host_class_pima_storage_ids_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *storage_ids_array,
    ULONG storage_id_length)
```

### <a name="description"></a><span data-ttu-id="ea67e-331">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-331">Description</span></span>

<span data-ttu-id="ea67e-332">Эта функция получает массив идентификаторов хранилища из отвечающего устройства.</span><span class="sxs-lookup"><span data-stu-id="ea67e-332">This function obtains the storage ID array from the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-333">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-333">Parameters</span></span>

- <span data-ttu-id="ea67e-334">**pima** — указатель на экземпляр класса Pima.</span><span class="sxs-lookup"><span data-stu-id="ea67e-334">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="ea67e-335">**pima_session** — указатель на сеанс PIMA</span><span class="sxs-lookup"><span data-stu-id="ea67e-335">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="ea67e-336">**storage_ids_array** — массив, в который будут возвращены идентификаторы хранилища.</span><span class="sxs-lookup"><span data-stu-id="ea67e-336">**storage_ids_array**: Array where storage IDs will be returned</span></span>
- <span data-ttu-id="ea67e-337">**storage_id_length** — длина массива хранения.</span><span class="sxs-lookup"><span data-stu-id="ea67e-337">**storage_id_length**: Length of the storage array</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-338">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-338">Return Value</span></span>

- <span data-ttu-id="ea67e-339">**UX_SUCCESS**: (0x00) — массив идентификаторов хранилища заполнен.</span><span class="sxs-lookup"><span data-stu-id="ea67e-339">**UX_SUCCESS**: (0x00) The storage ID array has been populated</span></span>
- <span data-ttu-id="ea67e-340">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт</span><span class="sxs-lookup"><span data-stu-id="ea67e-340">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="ea67e-341">**UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-341">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-342">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-342">Example</span></span>

```C
/* Get the number of storage IDs. */
status = ux_host_class_pima_storage_ids_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids, 64);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_storage_info_get"></a><span data-ttu-id="ea67e-343">ux_host_class_pima_storage_info_get</span><span class="sxs-lookup"><span data-stu-id="ea67e-343">ux_host_class_pima_storage_info_get</span></span>

<span data-ttu-id="ea67e-344">Получение сведений о хранилище из отвечающего устройства.</span><span class="sxs-lookup"><span data-stu-id="ea67e-344">Obtain the storage information from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-345">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-345">Prototype</span></span>

```C
UINT ux_host_class_pima_storage_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    UX_HOST_CLASS_PIMA_STORAGE *storage)
```

### <a name="description"></a><span data-ttu-id="ea67e-346">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-346">Description</span></span>

<span data-ttu-id="ea67e-347">Эта функция получает сведения о хранилище для контейнера хранилища со значением *storage_id*.</span><span class="sxs-lookup"><span data-stu-id="ea67e-347">This function obtains the storage information for a storage container of value *storage_id*.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-348">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-348">Parameters</span></span>

- <span data-ttu-id="ea67e-349">**pima** — указатель на экземпляр класса Pima.</span><span class="sxs-lookup"><span data-stu-id="ea67e-349">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="ea67e-350">**pima_session** — указатель на сеанс PIMA</span><span class="sxs-lookup"><span data-stu-id="ea67e-350">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="ea67e-351">**storage_id** — идентификатор контейнера хранилища.</span><span class="sxs-lookup"><span data-stu-id="ea67e-351">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="ea67e-352">**storage** — указатель на контейнер сведений о хранилище.</span><span class="sxs-lookup"><span data-stu-id="ea67e-352">**storage**: Pointer to storage information container</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-353">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-353">Return Value</span></span>

- <span data-ttu-id="ea67e-354">**UX_SUCCESS**: (0x00) — сведения о хранилище получены.</span><span class="sxs-lookup"><span data-stu-id="ea67e-354">**UX_SUCCESS**: (0x00) The storage information was retrieved</span></span>
- <span data-ttu-id="ea67e-355">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт</span><span class="sxs-lookup"><span data-stu-id="ea67e-355">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="ea67e-356">**UX_MEMORY_INSUFFICIENT** (0x12) — недостаточно памяти для создания команды PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-356">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-357">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-357">Example</span></span>

```C
/* Get the first storage ID info container. */
status = ux_host_class_pima_storage_info_get(pima, pima_session,
    pictbridge ->ux_pictbridge_storage_ids[0],
    (UX_HOST_CLASS_PIMA_STORAGE *)pictbridge ->ux_pictbridge_storage);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pictbridge ->
        ux_pictbridge_pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_num_objects_get"></a><span data-ttu-id="ea67e-358">ux_host_class_pima_num_objects_get</span><span class="sxs-lookup"><span data-stu-id="ea67e-358">ux_host_class_pima_num_objects_get</span></span>

<span data-ttu-id="ea67e-359">Получение количества объектов в контейнере хранилища из отвечающего устройства.</span><span class="sxs-lookup"><span data-stu-id="ea67e-359">Obtain the number of objects on a storage container from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-360">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-360">Prototype</span></span>

```C
UINT ux_host_class_pima_num_objects_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG object_format_code)
```

### <a name="description"></a><span data-ttu-id="ea67e-361">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-361">Description</span></span>

<span data-ttu-id="ea67e-362">Эта функция получает количество объектов, хранящихся в определенном контейнере хранилища со значением storage_id, соответствующим определенному коду формата.</span><span class="sxs-lookup"><span data-stu-id="ea67e-362">This function obtains the number of objects stored on a specific storage container of value storage_id matching a specific format code.</span></span> <span data-ttu-id="ea67e-363">Количество объектов возвращается в поле: ux_host_class_pima_session_nb_objects структуры pima_session.</span><span class="sxs-lookup"><span data-stu-id="ea67e-363">The number of objects is returned in the field: ux_host_class_pima_session_nb_objects of the pima_session structure.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-364">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-364">Parameters</span></span>

- <span data-ttu-id="ea67e-365">**pima** — указатель на экземпляр класса Pima.</span><span class="sxs-lookup"><span data-stu-id="ea67e-365">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="ea67e-366">**pima_session** — указатель на сеанс PIMA</span><span class="sxs-lookup"><span data-stu-id="ea67e-366">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="ea67e-367">**storage_id** — идентификатор контейнера хранилища.</span><span class="sxs-lookup"><span data-stu-id="ea67e-367">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="ea67e-368">**object_format_code** — фильтр кода формата объектов.</span><span class="sxs-lookup"><span data-stu-id="ea67e-368">**object_format_code**: Objects format code filter.</span></span>

<span data-ttu-id="ea67e-369">Эти коды формата объекта могут иметь одно из приведенных ниже значений.</span><span class="sxs-lookup"><span data-stu-id="ea67e-369">The Object Format Codes can have one of the following values.</span></span>

| <span data-ttu-id="ea67e-370">Код формата объекта</span><span class="sxs-lookup"><span data-stu-id="ea67e-370">Object Format Code</span></span>               | <span data-ttu-id="ea67e-371">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-371">Description</span></span>   |     <span data-ttu-id="ea67e-372">Код USBX</span><span class="sxs-lookup"><span data-stu-id="ea67e-372">USBX code</span></span>                          |
|----------------------------------|---------------|------------------------------------------|
| <span data-ttu-id="ea67e-373">0x3000</span><span class="sxs-lookup"><span data-stu-id="ea67e-373">0x3000</span></span>                           | <span data-ttu-id="ea67e-374">Не определено. Неопределенный объект, не являющийся изображением</span><span class="sxs-lookup"><span data-stu-id="ea67e-374">Undefined Undefined non-image object</span></span> | <span data-ttu-id="ea67e-375">UX_HOST_CLASS_PIMA_OFC_UNDEFINED</span><span class="sxs-lookup"><span data-stu-id="ea67e-375">UX_HOST_CLASS_PIMA_OFC_UNDEFINED</span></span>   |
| <span data-ttu-id="ea67e-376">0x3001</span><span class="sxs-lookup"><span data-stu-id="ea67e-376">0x3001</span></span>                           | <span data-ttu-id="ea67e-377">Связь. Связь (например, папка)</span><span class="sxs-lookup"><span data-stu-id="ea67e-377">Association Association (e.g. folder)</span></span> | <span data-ttu-id="ea67e-378">UX_HOST_CLASS_PIMA_OFC_ASSOCIATION</span><span class="sxs-lookup"><span data-stu-id="ea67e-378">UX_HOST_CLASS_PIMA_OFC_ASSOCIATION</span></span> |
| <span data-ttu-id="ea67e-379">0x3002</span><span class="sxs-lookup"><span data-stu-id="ea67e-379">0x3002</span></span>                           | <span data-ttu-id="ea67e-380">Скрипт. Скрипт конкретной модели устройства</span><span class="sxs-lookup"><span data-stu-id="ea67e-380">Script Device-model specific script</span></span> | <span data-ttu-id="ea67e-381">UX_HOST_CLASS_PIMA_OFC_SCRIPT</span><span class="sxs-lookup"><span data-stu-id="ea67e-381">UX_HOST_CLASS_PIMA_OFC_SCRIPT</span></span>      |
| <span data-ttu-id="ea67e-382">0x3003</span><span class="sxs-lookup"><span data-stu-id="ea67e-382">0x3003</span></span>                           | <span data-ttu-id="ea67e-383">Исполняемый файл. Двоичный исполняемый файл конкретной модели устройства</span><span class="sxs-lookup"><span data-stu-id="ea67e-383">Executable Device model-specific binary executable</span></span> | <span data-ttu-id="ea67e-384">UX_HOST_CLASS_PIMA_OFC_EXECUTABLE</span><span class="sxs-lookup"><span data-stu-id="ea67e-384">UX_HOST_CLASS_PIMA_OFC_EXECUTABLE</span></span>  |
| <span data-ttu-id="ea67e-385">0x3004</span><span class="sxs-lookup"><span data-stu-id="ea67e-385">0x3004</span></span>                           | <span data-ttu-id="ea67e-386">Текст. Текстовый файл</span><span class="sxs-lookup"><span data-stu-id="ea67e-386">Text Text file</span></span>  |   <span data-ttu-id="ea67e-387">UX_HOST_CLASS_PIMA_OFC_TEXT</span><span class="sxs-lookup"><span data-stu-id="ea67e-387">UX_HOST_CLASS_PIMA_OFC_TEXT</span></span>        |
| <span data-ttu-id="ea67e-388">0x3005</span><span class="sxs-lookup"><span data-stu-id="ea67e-388">0x3005</span></span>                           | <span data-ttu-id="ea67e-389">HTML. Файл языка гипертекстовой разметки (текст)</span><span class="sxs-lookup"><span data-stu-id="ea67e-389">HTML HyperText Markup Language file (text)</span></span> | <span data-ttu-id="ea67e-390">UX_HOST_CLASS_PIMA_OFC_HTML</span><span class="sxs-lookup"><span data-stu-id="ea67e-390">UX_HOST_CLASS_PIMA_OFC_HTML</span></span>        |
| <span data-ttu-id="ea67e-391">0x3006</span><span class="sxs-lookup"><span data-stu-id="ea67e-391">0x3006</span></span>                           | <span data-ttu-id="ea67e-392">DPOF. Файл цифрового формата управления печатью (текст)</span><span class="sxs-lookup"><span data-stu-id="ea67e-392">DPOF Digital Print Order Format file (text)</span></span> | <span data-ttu-id="ea67e-393">UX_HOST_CLASS_PIMA_OFC_DPOF</span><span class="sxs-lookup"><span data-stu-id="ea67e-393">UX_HOST_CLASS_PIMA_OFC_DPOF</span></span>        |
| <span data-ttu-id="ea67e-394">0x3007</span><span class="sxs-lookup"><span data-stu-id="ea67e-394">0x3007</span></span>                           | <span data-ttu-id="ea67e-395">AIFF. Аудиоклип</span><span class="sxs-lookup"><span data-stu-id="ea67e-395">AIFF Audio clip</span></span>  |  <span data-ttu-id="ea67e-396">UX_HOST_CLASS_PIMA_OFC_AIFF</span><span class="sxs-lookup"><span data-stu-id="ea67e-396">UX_HOST_CLASS_PIMA_OFC_AIFF</span></span>        |
| <span data-ttu-id="ea67e-397">0x3008</span><span class="sxs-lookup"><span data-stu-id="ea67e-397">0x3008</span></span>                           | <span data-ttu-id="ea67e-398">WAV. Аудиоклип</span><span class="sxs-lookup"><span data-stu-id="ea67e-398">WAV Audio clip</span></span>   |  <span data-ttu-id="ea67e-399">UX_HOST_CLASS_PIMA_OFC_WAV</span><span class="sxs-lookup"><span data-stu-id="ea67e-399">UX_HOST_CLASS_PIMA_OFC_WAV</span></span>         |
| <span data-ttu-id="ea67e-400">0x3009</span><span class="sxs-lookup"><span data-stu-id="ea67e-400">0x3009</span></span>                           | <span data-ttu-id="ea67e-401">MP3. Аудиоклип</span><span class="sxs-lookup"><span data-stu-id="ea67e-401">MP3 Audio clip</span></span>   |  <span data-ttu-id="ea67e-402">UX_HOST_CLASS_PIMA_OFC_MP3</span><span class="sxs-lookup"><span data-stu-id="ea67e-402">UX_HOST_CLASS_PIMA_OFC_MP3</span></span>         |
| <span data-ttu-id="ea67e-403">0x300A</span><span class="sxs-lookup"><span data-stu-id="ea67e-403">0x300A</span></span>                           | <span data-ttu-id="ea67e-404">AVI. Видеоролик</span><span class="sxs-lookup"><span data-stu-id="ea67e-404">AVI Video clip</span></span>   |  <span data-ttu-id="ea67e-405">UX_HOST_CLASS_PIMA_OFC_AVI</span><span class="sxs-lookup"><span data-stu-id="ea67e-405">UX_HOST_CLASS_PIMA_OFC_AVI</span></span>         |
| <span data-ttu-id="ea67e-406">0x300B</span><span class="sxs-lookup"><span data-stu-id="ea67e-406">0x300B</span></span>                           | <span data-ttu-id="ea67e-407">MPEG. Видеоролик</span><span class="sxs-lookup"><span data-stu-id="ea67e-407">MPEG Video clip</span></span>  |  <span data-ttu-id="ea67e-408">UX_HOST_CLASS_PIMA_OFC_MPEG</span><span class="sxs-lookup"><span data-stu-id="ea67e-408">UX_HOST_CLASS_PIMA_OFC_MPEG</span></span>        |
| <span data-ttu-id="ea67e-409">0x300C</span><span class="sxs-lookup"><span data-stu-id="ea67e-409">0x300C</span></span>                           | <span data-ttu-id="ea67e-410">ASF. Формат Microsoft Advanced Streaming Format (видео)</span><span class="sxs-lookup"><span data-stu-id="ea67e-410">ASF Microsoft Advanced Streaming Format (video)</span></span> | <span data-ttu-id="ea67e-411">UX_HOST_CLASS_PIMA_OFC_ASF</span><span class="sxs-lookup"><span data-stu-id="ea67e-411">UX_HOST_CLASS_PIMA_OFC_ASF</span></span>         |
| <span data-ttu-id="ea67e-412">0x3800</span><span class="sxs-lookup"><span data-stu-id="ea67e-412">0x3800</span></span>                           | <span data-ttu-id="ea67e-413">Не определено. Неизвестный объект изображения</span><span class="sxs-lookup"><span data-stu-id="ea67e-413">Undefined Unknown image object</span></span> | <span data-ttu-id="ea67e-414">UX_HOST_CLASS_PIMA_OFC_QT</span><span class="sxs-lookup"><span data-stu-id="ea67e-414">UX_HOST_CLASS_PIMA_OFC_QT</span></span>          |
| <span data-ttu-id="ea67e-415">0x3801</span><span class="sxs-lookup"><span data-stu-id="ea67e-415">0x3801</span></span>                           | <span data-ttu-id="ea67e-416">EXIF/JPEG. Формат Exchangeable File Format, стандарт JEIDA</span><span class="sxs-lookup"><span data-stu-id="ea67e-416">EXIF/JPEG Exchangeable File Format, JEIDA standard</span></span> | <span data-ttu-id="ea67e-417">UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG</span><span class="sxs-lookup"><span data-stu-id="ea67e-417">UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG</span></span>   |
| <span data-ttu-id="ea67e-418">0x3802</span><span class="sxs-lookup"><span data-stu-id="ea67e-418">0x3802</span></span>                           | <span data-ttu-id="ea67e-419">TIFF/EP. Формат файла Tag Image File Format для электронной фотографии</span><span class="sxs-lookup"><span data-stu-id="ea67e-419">TIFF/EP Tag Image File Format for Electronic Photography</span></span> | <span data-ttu-id="ea67e-420">UX_HOST_CLASS_PIMA_OFC_TIFF_EP</span><span class="sxs-lookup"><span data-stu-id="ea67e-420">UX_HOST_CLASS_PIMA_OFC_TIFF_EP</span></span>     |
| <span data-ttu-id="ea67e-421">0x3803</span><span class="sxs-lookup"><span data-stu-id="ea67e-421">0x3803</span></span>                           | <span data-ttu-id="ea67e-422">FlashPix. Формат Structured Storage Image Format</span><span class="sxs-lookup"><span data-stu-id="ea67e-422">FlashPix Structured Storage Image Format</span></span> | <span data-ttu-id="ea67e-423">UX_HOST_CLASS_PIMA_OFC_FLASHPIX</span><span class="sxs-lookup"><span data-stu-id="ea67e-423">UX_HOST_CLASS_PIMA_OFC_FLASHPIX</span></span>    |
| <span data-ttu-id="ea67e-424">0x3804</span><span class="sxs-lookup"><span data-stu-id="ea67e-424">0x3804</span></span>                           | <span data-ttu-id="ea67e-425">BMP. Файл в формате Microsoft Windows Bitmap</span><span class="sxs-lookup"><span data-stu-id="ea67e-425">BMP Microsoft Windows Bitmap file</span></span> | <span data-ttu-id="ea67e-426">UX_HOST_CLASS_PIMA_OFC_BMP</span><span class="sxs-lookup"><span data-stu-id="ea67e-426">UX_HOST_CLASS_PIMA_OFC_BMP</span></span>         |
| <span data-ttu-id="ea67e-427">0x3805</span><span class="sxs-lookup"><span data-stu-id="ea67e-427">0x3805</span></span>                           | <span data-ttu-id="ea67e-428">CIFF. Формат файла Canon Camera Image File Format</span><span class="sxs-lookup"><span data-stu-id="ea67e-428">CIFF Canon Camera Image File Format</span></span> | <span data-ttu-id="ea67e-429">UX_HOST_CLASS_PIMA_OFC_CIFF</span><span class="sxs-lookup"><span data-stu-id="ea67e-429">UX_HOST_CLASS_PIMA_OFC_CIFF</span></span>        |
| <span data-ttu-id="ea67e-430">0x3806</span><span class="sxs-lookup"><span data-stu-id="ea67e-430">0x3806</span></span>                           | <span data-ttu-id="ea67e-431">Не определено. Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="ea67e-431">Undefined Reserved</span></span> |  |
| <span data-ttu-id="ea67e-432">0x3807</span><span class="sxs-lookup"><span data-stu-id="ea67e-432">0x3807</span></span>                           | <span data-ttu-id="ea67e-433">GIF. Формат Graphics Interchange Format</span><span class="sxs-lookup"><span data-stu-id="ea67e-433">GIF Graphics Interchange Format</span></span> | <span data-ttu-id="ea67e-434">UX_HOST_CLASS_PIMA_OFC_GIF</span><span class="sxs-lookup"><span data-stu-id="ea67e-434">UX_HOST_CLASS_PIMA_OFC_GIF</span></span>         |
| <span data-ttu-id="ea67e-435">0x3808</span><span class="sxs-lookup"><span data-stu-id="ea67e-435">0x3808</span></span>                           | <span data-ttu-id="ea67e-436">JFIF. Формат обмена файлами JPEG</span><span class="sxs-lookup"><span data-stu-id="ea67e-436">JFIF JPEG File Interchange Format</span></span> | <span data-ttu-id="ea67e-437">UX_HOST_CLASS_PIMA_OFC_JFIF</span><span class="sxs-lookup"><span data-stu-id="ea67e-437">UX_HOST_CLASS_PIMA_OFC_JFIF</span></span>        |
| <span data-ttu-id="ea67e-438">0x3809</span><span class="sxs-lookup"><span data-stu-id="ea67e-438">0x3809</span></span>                           | <span data-ttu-id="ea67e-439">PCD. Формат PhotoCD Image Pac</span><span class="sxs-lookup"><span data-stu-id="ea67e-439">PCD PhotoCD Image Pac</span></span> | <span data-ttu-id="ea67e-440">UX_HOST_CLASS_PIMA_OFC_PCD</span><span class="sxs-lookup"><span data-stu-id="ea67e-440">UX_HOST_CLASS_PIMA_OFC_PCD</span></span>         |
| <span data-ttu-id="ea67e-441">0x380A</span><span class="sxs-lookup"><span data-stu-id="ea67e-441">0x380A</span></span>                           | <span data-ttu-id="ea67e-442">PICT. Формат Quickdraw Image Format</span><span class="sxs-lookup"><span data-stu-id="ea67e-442">PICT Quickdraw Image Format</span></span> | <span data-ttu-id="ea67e-443">UX_HOST_CLASS_PIMA_OFC_PICT</span><span class="sxs-lookup"><span data-stu-id="ea67e-443">UX_HOST_CLASS_PIMA_OFC_PICT</span></span>        |
| <span data-ttu-id="ea67e-444">0x380B</span><span class="sxs-lookup"><span data-stu-id="ea67e-444">0x380B</span></span>                           | <span data-ttu-id="ea67e-445">PNG. Формат Portable Network Graphics</span><span class="sxs-lookup"><span data-stu-id="ea67e-445">PNG Portable Network Graphics</span></span> | <span data-ttu-id="ea67e-446">UX_HOST_CLASS_PIMA_OFC_PNG</span><span class="sxs-lookup"><span data-stu-id="ea67e-446">UX_HOST_CLASS_PIMA_OFC_PNG</span></span>         |
| <span data-ttu-id="ea67e-447">0x380C</span><span class="sxs-lookup"><span data-stu-id="ea67e-447">0x380C</span></span>                           | <span data-ttu-id="ea67e-448">Не определено. Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="ea67e-448">Undefined Reserved</span></span> |   |
| <span data-ttu-id="ea67e-449">0x380D</span><span class="sxs-lookup"><span data-stu-id="ea67e-449">0x380D</span></span>                           | <span data-ttu-id="ea67e-450">TIFF. Формат Tag Image File Format</span><span class="sxs-lookup"><span data-stu-id="ea67e-450">TIFF Tag Image File Format</span></span> | <span data-ttu-id="ea67e-451">UX_HOST_CLASS_PIMA_OFC_TIFF</span><span class="sxs-lookup"><span data-stu-id="ea67e-451">UX_HOST_CLASS_PIMA_OFC_TIFF</span></span>        |
| <span data-ttu-id="ea67e-452">0x380E</span><span class="sxs-lookup"><span data-stu-id="ea67e-452">0x380E</span></span>                           | <span data-ttu-id="ea67e-453">TIFF/IT. Формат Tag Image File Format for Information Technology (графика)</span><span class="sxs-lookup"><span data-stu-id="ea67e-453">TIFF/IT Tag Image File Format for Information Technology (graphic arts)</span></span> | <span data-ttu-id="ea67e-454">UX_HOST_CLASS_PIMA_OFC_TIFF_IT</span><span class="sxs-lookup"><span data-stu-id="ea67e-454">UX_HOST_CLASS_PIMA_OFC_TIFF_IT</span></span>     |
| <span data-ttu-id="ea67e-455">0x380F</span><span class="sxs-lookup"><span data-stu-id="ea67e-455">0x380F</span></span>                           | <span data-ttu-id="ea67e-456">JP2. Базовый формат файла JPEG2000</span><span class="sxs-lookup"><span data-stu-id="ea67e-456">JP2 JPEG2000 Baseline File Format</span></span> | <span data-ttu-id="ea67e-457">UX_HOST_CLASS_PIMA_OFC_JP2</span><span class="sxs-lookup"><span data-stu-id="ea67e-457">UX_HOST_CLASS_PIMA_OFC_JP2</span></span>         |
| <span data-ttu-id="ea67e-458">0x3810</span><span class="sxs-lookup"><span data-stu-id="ea67e-458">0x3810</span></span>                           | <span data-ttu-id="ea67e-459">JPX. Расширенный формат файла JPEG2000</span><span class="sxs-lookup"><span data-stu-id="ea67e-459">JPX JPEG2000 Extended File Format</span></span> | <span data-ttu-id="ea67e-460">UX_HOST_CLASS_PIMA_OFC_JPX</span><span class="sxs-lookup"><span data-stu-id="ea67e-460">UX_HOST_CLASS_PIMA_OFC_JPX</span></span>         |
| <span data-ttu-id="ea67e-461">Все остальные коды с MSN 0011</span><span class="sxs-lookup"><span data-stu-id="ea67e-461">All other codes with MSN of 0011</span></span> | <span data-ttu-id="ea67e-462">Не определено (любые). Зарезервировано для будущего использования</span><span class="sxs-lookup"><span data-stu-id="ea67e-462">Any Undefined Reserved for future use</span></span> |                                    |
| <span data-ttu-id="ea67e-463">Все остальные коды с MSN 1011</span><span class="sxs-lookup"><span data-stu-id="ea67e-463">All other codes with MSN of 1011</span></span> | <span data-ttu-id="ea67e-464">Любой определенный поставщиком. Определенный поставщиком тип: изображение</span><span class="sxs-lookup"><span data-stu-id="ea67e-464">Any Vendor-Defined Vendor-Defined type: Image</span></span> |                                    |

### <a name="return-value"></a><span data-ttu-id="ea67e-465">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-465">Return Value</span></span>

- <span data-ttu-id="ea67e-466">**UX_SUCCESS**: (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-466">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="ea67e-467">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт</span><span class="sxs-lookup"><span data-stu-id="ea67e-467">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="ea67e-468">**UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-468">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-469">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-469">Example</span></span>

```C
/* Get the number of objects on all containers matching a SCRIPT object. */
status = ux_host_class_pima_num_objects_get(pima, pima_session,
    UX_PICTBRIDGE_ALL_CONTAINERS, UX_PICTBRIDGE_OBJECT_SCRIPT);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_**host_class_pima_session_close(pima, pima_session);

    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
} else
    /* The number of objects is returned in the field: pima_session -> ux_host_class_pima_session_nb_objects */
```

## <a name="ux_host_class_pima_object_handles_get"></a><span data-ttu-id="ea67e-470">ux_host_class_pima_object_handles_get</span><span class="sxs-lookup"><span data-stu-id="ea67e-470">ux_host_class_pima_object_handles_get</span></span>

<span data-ttu-id="ea67e-471">Получение дескрипторов объектов из отвечающего устройства.</span><span class="sxs-lookup"><span data-stu-id="ea67e-471">Obtain object handles from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-472">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-472">Prototype</span></span>

```C
UINT ux_host_class_pima_object_handles_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *object_handles_array,
    ULONG object_handles_length,
    ULONG storage_id,
    ULONG object_format_code,
    ULONG object_handle_association)
```

### <a name="description"></a><span data-ttu-id="ea67e-473">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-473">Description</span></span>

<span data-ttu-id="ea67e-474">Возвращает массив дескрипторов объектов, имеющихся в контейнере хранилища, указанном параметром storage_id.</span><span class="sxs-lookup"><span data-stu-id="ea67e-474">Returns an array of Object Handles present in the storage container indicated by the storage_id parameter.</span></span> <span data-ttu-id="ea67e-475">Если требуется агрегированный список по всем хранилищам, это значение должно быть 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="ea67e-475">If an aggregated list across all stores is desired, this value shall be set to 0xFFFFFFFF.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-476">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-476">Parameters</span></span>

- <span data-ttu-id="ea67e-477">**pima** — указатель на экземпляр класса Pima.</span><span class="sxs-lookup"><span data-stu-id="ea67e-477">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="ea67e-478">**pima_session** — указатель на сеанс PIMA</span><span class="sxs-lookup"><span data-stu-id="ea67e-478">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="ea67e-479">**object_handes_array** — массив, в который возвращаются дескрипторы.</span><span class="sxs-lookup"><span data-stu-id="ea67e-479">**object_handes_array**: Array where handles are returned</span></span>
- <span data-ttu-id="ea67e-480">**object_handles_length** — длина массива.</span><span class="sxs-lookup"><span data-stu-id="ea67e-480">**object_handles_length**: Length of the array</span></span>
- <span data-ttu-id="ea67e-481">**storage_id** — идентификатор контейнера хранилища.</span><span class="sxs-lookup"><span data-stu-id="ea67e-481">**storage_id**: ID of the storage container</span></span>
- <span data-ttu-id="ea67e-482">**object_format_code** — код формата для объекта (см. таблицу для функции ux_host_class_pima_num_objects_get).</span><span class="sxs-lookup"><span data-stu-id="ea67e-482">**object_format_code**: Format code for object (see table for function ux_host_class_pima_num_objects_get)</span></span>
- <span data-ttu-id="ea67e-483">**object_handle_association** — необязательное значение связи объекта.</span><span class="sxs-lookup"><span data-stu-id="ea67e-483">**object_handle_association**: Optional object association value</span></span>

<span data-ttu-id="ea67e-484">Связь дескриптора объекта может быть одним из значений из следующей таблицы:</span><span class="sxs-lookup"><span data-stu-id="ea67e-484">The object handle association can be one of the value from the table below:</span></span>

| <span data-ttu-id="ea67e-485">AssociationCode</span><span class="sxs-lookup"><span data-stu-id="ea67e-485">AssociationCode</span></span>                        | <span data-ttu-id="ea67e-486">AssociationType</span><span class="sxs-lookup"><span data-stu-id="ea67e-486">AssociationType</span></span>      | <span data-ttu-id="ea67e-487">Интерпретация</span><span class="sxs-lookup"><span data-stu-id="ea67e-487">Interpretation</span></span>       |
|----------------------------------------|----------------------|----------------------|
| <span data-ttu-id="ea67e-488">0x0000</span><span class="sxs-lookup"><span data-stu-id="ea67e-488">0x0000</span></span>                                 | <span data-ttu-id="ea67e-489">Не определено</span><span class="sxs-lookup"><span data-stu-id="ea67e-489">Undefined</span></span>            | <span data-ttu-id="ea67e-490">Не определено</span><span class="sxs-lookup"><span data-stu-id="ea67e-490">Undefined</span></span>            |
| <span data-ttu-id="ea67e-491">0x0001</span><span class="sxs-lookup"><span data-stu-id="ea67e-491">0x0001</span></span>                                 | <span data-ttu-id="ea67e-492">GenericFolder</span><span class="sxs-lookup"><span data-stu-id="ea67e-492">GenericFolder</span></span>        | <span data-ttu-id="ea67e-493">Не используется</span><span class="sxs-lookup"><span data-stu-id="ea67e-493">Unused</span></span>               |
| <span data-ttu-id="ea67e-494">0x0002</span><span class="sxs-lookup"><span data-stu-id="ea67e-494">0x0002</span></span>                                 | <span data-ttu-id="ea67e-495">Album</span><span class="sxs-lookup"><span data-stu-id="ea67e-495">Album</span></span>                | <span data-ttu-id="ea67e-496">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="ea67e-496">Reserved</span></span>             |
| <span data-ttu-id="ea67e-497">0x0003</span><span class="sxs-lookup"><span data-stu-id="ea67e-497">0x0003</span></span>                                 | <span data-ttu-id="ea67e-498">TimeSequence</span><span class="sxs-lookup"><span data-stu-id="ea67e-498">TimeSequence</span></span>         | <span data-ttu-id="ea67e-499">DefaultPlaybackDelta</span><span class="sxs-lookup"><span data-stu-id="ea67e-499">DefaultPlaybackDelta</span></span> |
| <span data-ttu-id="ea67e-500">0x0004</span><span class="sxs-lookup"><span data-stu-id="ea67e-500">0x0004</span></span>                                 | <span data-ttu-id="ea67e-501">HorizontalPanoramic</span><span class="sxs-lookup"><span data-stu-id="ea67e-501">HorizontalPanoramic</span></span>  | <span data-ttu-id="ea67e-502">Не используется</span><span class="sxs-lookup"><span data-stu-id="ea67e-502">Unused</span></span>               |
| <span data-ttu-id="ea67e-503">0x0005</span><span class="sxs-lookup"><span data-stu-id="ea67e-503">0x0005</span></span>                                 | <span data-ttu-id="ea67e-504">VerticalPanoramic</span><span class="sxs-lookup"><span data-stu-id="ea67e-504">VerticalPanoramic</span></span>    | <span data-ttu-id="ea67e-505">Не используется</span><span class="sxs-lookup"><span data-stu-id="ea67e-505">Unused</span></span>               |
| <span data-ttu-id="ea67e-506">0x0006</span><span class="sxs-lookup"><span data-stu-id="ea67e-506">0x0006</span></span>                                 | <span data-ttu-id="ea67e-507">2DPanoramic</span><span class="sxs-lookup"><span data-stu-id="ea67e-507">2DPanoramic</span></span>          | <span data-ttu-id="ea67e-508">ImagesPerRow</span><span class="sxs-lookup"><span data-stu-id="ea67e-508">ImagesPerRow</span></span>         |
| <span data-ttu-id="ea67e-509">0x0007</span><span class="sxs-lookup"><span data-stu-id="ea67e-509">0x0007</span></span>                                 | <span data-ttu-id="ea67e-510">AncillaryData</span><span class="sxs-lookup"><span data-stu-id="ea67e-510">AncillaryData</span></span>        | <span data-ttu-id="ea67e-511">Не определено.</span><span class="sxs-lookup"><span data-stu-id="ea67e-511">Undefined</span></span>            |
| <span data-ttu-id="ea67e-512">Все остальные значения с битом 15 равным 0</span><span class="sxs-lookup"><span data-stu-id="ea67e-512">All other values with bit 15 set to 0</span></span>  | <span data-ttu-id="ea67e-513">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="ea67e-513">Reserved</span></span>             | <span data-ttu-id="ea67e-514">Не определено.</span><span class="sxs-lookup"><span data-stu-id="ea67e-514">Undefined</span></span>            |
| <span data-ttu-id="ea67e-515">Все остальные значения с битом 15 равным 1</span><span class="sxs-lookup"><span data-stu-id="ea67e-515">All values with bit 15 set to 1</span></span>        | <span data-ttu-id="ea67e-516">Определяется поставщиком</span><span class="sxs-lookup"><span data-stu-id="ea67e-516">Vendor-Defined</span></span>       | <span data-ttu-id="ea67e-517">Определяется поставщиком</span><span class="sxs-lookup"><span data-stu-id="ea67e-517">Vendor-Defined</span></span>       |

### <a name="return-value"></a><span data-ttu-id="ea67e-518">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-518">Return Value</span></span>

- <span data-ttu-id="ea67e-519">**UX_SUCCESS**: (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-519">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="ea67e-520">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт</span><span class="sxs-lookup"><span data-stu-id="ea67e-520">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="ea67e-521">**UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-521">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-522">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-522">Example</span></span>

```C
/* Get the array of objects handles on the container. */
status = ux_**host_class_pima_object_handles_get(pima, pima_session,
    pictbridge ->ux_pictbridge_object_handles_array,
    4 * pima_session ->ux_host_class_pima_session_nb_objects,
    UX_PICTBRIDGE_ALL_CONTAINERS,
    UX_PICTBRIDGE_OBJECT_SCRIPT, 0);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);
    return(UX_PICTBRIDGE_ERROR_STORE_NOT_AVAILABLE);
}
```

## <a name="ux_host_class_pima_object_info_get"></a><span data-ttu-id="ea67e-523">ux_host_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="ea67e-523">ux_host_class_pima_object_info_get</span></span>

<span data-ttu-id="ea67e-524">Получение сведений об объекте из отвечающего устройства.</span><span class="sxs-lookup"><span data-stu-id="ea67e-524">Obtain the object information from Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-525">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-525">Prototype</span></span>

```C
UINT ux_host_class_pima_object_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="ea67e-526">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-526">Description</span></span>

<span data-ttu-id="ea67e-527">Эта функция получает сведения об объекте для дескриптора объекта.</span><span class="sxs-lookup"><span data-stu-id="ea67e-527">This function obtains the object information for an object handle.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-528">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-528">Parameters</span></span>

- <span data-ttu-id="ea67e-529">**pima** — указатель на экземпляр класса Pima.</span><span class="sxs-lookup"><span data-stu-id="ea67e-529">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="ea67e-530">**pima_session** — указатель на сеанс PIMA</span><span class="sxs-lookup"><span data-stu-id="ea67e-530">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="ea67e-531">**object_handle** — дескриптор объекта</span><span class="sxs-lookup"><span data-stu-id="ea67e-531">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="ea67e-532">**object** — указатель на контейнер сведений об объекте</span><span class="sxs-lookup"><span data-stu-id="ea67e-532">**object**: Pointer to object information container</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-533">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-533">Return Value</span></span>

- <span data-ttu-id="ea67e-534">**UX_SUCCESS**: (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-534">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="ea67e-535">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт</span><span class="sxs-lookup"><span data-stu-id="ea67e-535">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="ea67e-536">**UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-536">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-537">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-537">Example</span></span>

```C
/* We search for an object that is a picture or a script. */
object_index = 0;

while (object_index < pima_session -> ux_host_class_pima_session_nb_objects)
{
    /* Get the object info structure. */
    status = ux_**host_class_pima_object_info_get(pima, pima_session,
        pictbridge -> ux_pictbridge_object_handles_array[object_index], 
        pima_object);

    if (status != UX_SUCCESS)
    {
        /* Close the pima session. */
        status = ux_host_class_pima_session_close(pima, pima_session);

        return(UX_PICTBRIDGE_ERROR_INVALID_OBJECT_HANDLE );
    }
}
```

## <a name="ux_host_class_pima_object_info_send"></a><span data-ttu-id="ea67e-538">ux_host_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="ea67e-538">ux_host_class_pima_object_info_send</span></span>

<span data-ttu-id="ea67e-539">Отправка сведений об объекте в отвечающее устройство.</span><span class="sxs-lookup"><span data-stu-id="ea67e-539">Send the object information to Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-540">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-540">Prototype</span></span>

```C
UINT ux_host_class_pima_object_info_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG parent_object_id,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="ea67e-541">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-541">Description</span></span>

<span data-ttu-id="ea67e-542">Эта функция отправляет сведения о хранилище для контейнера хранилища со значением storage_id.</span><span class="sxs-lookup"><span data-stu-id="ea67e-542">This function sends the storage information for a storage container of value storage_id.</span></span> <span data-ttu-id="ea67e-543">Инициатор должен использовать эту команду перед отправкой объекта в отвечающее устройство.</span><span class="sxs-lookup"><span data-stu-id="ea67e-543">The Initiator should use this command before sending an object to the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-544">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-544">Parameters</span></span>

- <span data-ttu-id="ea67e-545">**pima** — указатель на экземпляр класса Pima.</span><span class="sxs-lookup"><span data-stu-id="ea67e-545">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="ea67e-546">**pima_session** — указатель на сеанс PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-546">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="ea67e-547">**storage_id** — идентификатор целевого хранилища.</span><span class="sxs-lookup"><span data-stu-id="ea67e-547">**storage_id**: Destination storage ID.</span></span>
- <span data-ttu-id="ea67e-548">**parent_object_id** — родительский ObjectHandle в отвечающем устройстве, в котором следует разместить объект.</span><span class="sxs-lookup"><span data-stu-id="ea67e-548">**parent_object_id**: Parent ObjectHandle on Responder where object should be placed.</span></span>
- <span data-ttu-id="ea67e-549">**object** — указатель на контейнер сведений об объекте.</span><span class="sxs-lookup"><span data-stu-id="ea67e-549">**object**: Pointer to object information container.</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-550">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-550">Return Value</span></span>

- <span data-ttu-id="ea67e-551">**UX_SUCCESS**: (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-551">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="ea67e-552">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт</span><span class="sxs-lookup"><span data-stu-id="ea67e-552">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="ea67e-553">**UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-553">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-554">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-554">Example</span></span>

```C
/* Send a script info. */
status = ux_host_class_pima_object_info_send(pima, pima_session,
    0, 0, pima_object);

if (status != UX_SUCCESS)
{
    /* Close the pima session. */
    status = ux_host_class_pima_session_close(pima, pima_session);

    return(UX_ERROR);
}
```

## <a name="ux_host_class_pima_object_open"></a><span data-ttu-id="ea67e-555">ux_host_class_pima_object_open</span><span class="sxs-lookup"><span data-stu-id="ea67e-555">ux_host_class_pima_object_open</span></span>

<span data-ttu-id="ea67e-556">Открытие объекта, хранящегося в отвечающем устройстве.</span><span class="sxs-lookup"><span data-stu-id="ea67e-556">Open an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-557">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-557">Prototype</span></span>

```C
UINT ux_host_class_pima_object_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="ea67e-558">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-558">Description</span></span>

<span data-ttu-id="ea67e-559">Эта функция открывает объект на стороне отвечающего устройства перед чтением или записью.</span><span class="sxs-lookup"><span data-stu-id="ea67e-559">This function opens an object on the responder before reading or writing.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-560">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-560">Parameters</span></span>

- <span data-ttu-id="ea67e-561">**pima** — указатель на экземпляр класса Pima.</span><span class="sxs-lookup"><span data-stu-id="ea67e-561">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="ea67e-562">**pima_session** — указатель на сеанс PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-562">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="ea67e-563">**object_handle** — дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="ea67e-563">**object_handle**: handle of the object.</span></span>
- <span data-ttu-id="ea67e-564">**object** — указатель на контейнер сведений об объекте.</span><span class="sxs-lookup"><span data-stu-id="ea67e-564">**objec**: Pointer to object information container.</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-565">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-565">Return Value</span></span>

- <span data-ttu-id="ea67e-566">**UX_SUCCESS**: (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-566">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="ea67e-567">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт</span><span class="sxs-lookup"><span data-stu-id="ea67e-567">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="ea67e-568">**UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) — объект уже открыт.</span><span class="sxs-lookup"><span data-stu-id="ea67e-568">**UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) Object already opened.</span></span>
- <span data-ttu-id="ea67e-569">**UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-569">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-570">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-570">Example</span></span>

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_get"></a><span data-ttu-id="ea67e-571">ux_host_class_pima_object_get</span><span class="sxs-lookup"><span data-stu-id="ea67e-571">ux_host_class_pima_object_get</span></span>

<span data-ttu-id="ea67e-572">Получение объекта, хранящегося в отвечающем устройстве.</span><span class="sxs-lookup"><span data-stu-id="ea67e-572">Get an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-573">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-573">Prototype</span></span>

```C
UINT ux_host_class_pima_object_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer,
    ULONG object_buffer_length,
    ULONG *object_actual_length)
```

### <a name="description"></a><span data-ttu-id="ea67e-574">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-574">Description</span></span>

<span data-ttu-id="ea67e-575">Эта функция получает объект на стороне отвечающего устройства.</span><span class="sxs-lookup"><span data-stu-id="ea67e-575">This function gets an object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-576">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-576">Parameters</span></span>

- <span data-ttu-id="ea67e-577">**pima** — указатель на экземпляр класса Pima.</span><span class="sxs-lookup"><span data-stu-id="ea67e-577">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="ea67e-578">**pima_session** — указатель на сеанс PIMA</span><span class="sxs-lookup"><span data-stu-id="ea67e-578">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="ea67e-579">**object_handle** — дескриптор объекта</span><span class="sxs-lookup"><span data-stu-id="ea67e-579">**object_handle**: handle of the object</span></span>
- <span data-ttu-id="ea67e-580">**object** — указатель на контейнер сведений об объекте</span><span class="sxs-lookup"><span data-stu-id="ea67e-580">**object**: Pointer to object information container</span></span>
- <span data-ttu-id="ea67e-581">**object_buffer** — адрес данных объекта.</span><span class="sxs-lookup"><span data-stu-id="ea67e-581">**object_buffer**: Address of object data</span></span>
- <span data-ttu-id="ea67e-582">**object_buffer_length** — запрошенная длина объекта.</span><span class="sxs-lookup"><span data-stu-id="ea67e-582">**object_buffer_length**: Requested length of object</span></span>
- <span data-ttu-id="ea67e-583">**object_actual_length** — длина возвращаемого объекта.</span><span class="sxs-lookup"><span data-stu-id="ea67e-583">**object_actual_length**: Length of object returned</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-584">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-584">Return Value</span></span>

- <span data-ttu-id="ea67e-585">**UX_SUCCESS**: (0x00) — объект передан.</span><span class="sxs-lookup"><span data-stu-id="ea67e-585">**UX_SUCCESS**: (0x00) The object was transfered</span></span>
- <span data-ttu-id="ea67e-586">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт</span><span class="sxs-lookup"><span data-stu-id="ea67e-586">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="ea67e-587">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) — объект не открыт.</span><span class="sxs-lookup"><span data-stu-id="ea67e-587">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="ea67e-588">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) — отказано в доступе к объекту</span><span class="sxs-lookup"><span data-stu-id="ea67e-588">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied</span></span>
- <span data-ttu-id="ea67e-589">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) — передача не завершена</span><span class="sxs-lookup"><span data-stu-id="ea67e-589">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete</span></span>
- <span data-ttu-id="ea67e-590">**UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-590">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="ea67e-591">**UX_TRANSFER_ERROR**: (0x23) — ошибка передачи при чтении объекта</span><span class="sxs-lookup"><span data-stu-id="ea67e-591">**UX_TRANSFER_ERROR**: (0x23) Transfer error while reading object</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-592">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-592">Example</span></span>

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);

/* Set the object buffer pointer. */
object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Obtain all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Get the object data. */
    status = ux_host_class_pima_object_get(pima, pima_session,
        object_handle, pima_object, object_buffer,
        requested_length, &actual_length);

    if (status != UX_SUCCESS)
    {
        /* We had a problem, abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* And close the object. */
        ux_host_class_pima_object_close(pima, pima_session,
            object_handle, pima_object, object);

        return(status);

    }

    /* We have received some data, update the length remaining. */
    object_length -= actual_length;

    /* Update the buffer address. */
    object_buffer += actual_length;

}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session,
    object_handle, pima_object, object);
```

## <a name="ux_host_class_pima_object_send"></a><span data-ttu-id="ea67e-593">ux_host_class_pima_object_send</span><span class="sxs-lookup"><span data-stu-id="ea67e-593">ux_host_class_pima_object_send</span></span>

<span data-ttu-id="ea67e-594">Отправка объекта, хранящегося в отвечающем устройстве.</span><span class="sxs-lookup"><span data-stu-id="ea67e-594">Send an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-595">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-595">Prototype</span></span>

```C
UINT ux_host_class_pima_object_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer, ULONG object_buffer_length)
```

### <a name="description"></a><span data-ttu-id="ea67e-596">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-596">Description</span></span>

<span data-ttu-id="ea67e-597">Эта функция отправляет объект в отвечающее устройство.</span><span class="sxs-lookup"><span data-stu-id="ea67e-597">This function sends an object to the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-598">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-598">Parameters</span></span>

- <span data-ttu-id="ea67e-599">**pima** — указатель на экземпляр класса Pima.</span><span class="sxs-lookup"><span data-stu-id="ea67e-599">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="ea67e-600">**pima_session** — указатель на сеанс PIMA</span><span class="sxs-lookup"><span data-stu-id="ea67e-600">**pima_sessio**: Pointer to PIMA session</span></span>
- <span data-ttu-id="ea67e-601">**object_handle** — дескриптор объекта</span><span class="sxs-lookup"><span data-stu-id="ea67e-601">**object_handle**: handle of the object</span></span>
- <span data-ttu-id="ea67e-602">**object** — указатель на контейнер сведений об объекте</span><span class="sxs-lookup"><span data-stu-id="ea67e-602">**object**: Pointer to object information container</span></span>
- <span data-ttu-id="ea67e-603">**object_buffer** — адрес данных объекта.</span><span class="sxs-lookup"><span data-stu-id="ea67e-603">**object_buffer**: Address of object data</span></span>
- <span data-ttu-id="ea67e-604">**object_buffer_length** — запрошенная длина объекта.</span><span class="sxs-lookup"><span data-stu-id="ea67e-604">**object_buffer_length**: Requested length of object</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-605">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-605">Return Value</span></span>

- <span data-ttu-id="ea67e-606">**UX_SUCCESS**: (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-606">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="ea67e-607">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт</span><span class="sxs-lookup"><span data-stu-id="ea67e-607">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened</span></span>
- <span data-ttu-id="ea67e-608">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) — объект не открыт.</span><span class="sxs-lookup"><span data-stu-id="ea67e-608">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="ea67e-609">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) — отказано в доступе к объекту</span><span class="sxs-lookup"><span data-stu-id="ea67e-609">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied</span></span>
- <span data-ttu-id="ea67e-610">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) — передача не завершена</span><span class="sxs-lookup"><span data-stu-id="ea67e-610">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete</span></span>
- <span data-ttu-id="ea67e-611">**UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-611">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="ea67e-612">**UX_TRANSFER_ERROR**: (0x23) — ошибка передачи при записи объекта.</span><span class="sxs-lookup"><span data-stu-id="ea67e-612">**UX_TRANSFER_ERROR**: (0x23) Transfer error while writing object</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-613">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-613">Example</span></span>

```C
/* Open the object. */
status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Get the object length. */
object_length = pima_object ->ux_host_class_pima_object_compressed_size;

/* Recall the object buffer address. */
pima_object_buffer = pima_object ->ux_host_class_pima_object_buffer;

/* Send all the object data. */
while(object_length != 0)
{
    /* Calculate what length to request. */
    if (object_length > UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER)
        /* Request maximum length. */
        requested_length = UX_PICTBRIDGE_MAX_PIMA_OBJECT_BUFFER;
    else
        /* Request remaining length. */
        requested_length = object_length;

    /* Send the object data. */
    status = ux_host_class_pima_object_send(pima,
        pima_session, pima_object,
        pima_object_buffer, requested_length);

    if (status != UX_SUCCESS)
    {
        /* Abort the transfer. */
        ux_host_class_pima_object_transfer_abort(pima, pima_session,
            object_handle, pima_object);

        /* Return status. */
        return(status);
    }

    /* We have sent some data, update the length remaining. */
    object_length -= requested_length;
}

/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle,
    pima_object, object);
```

## <a name="ux_host_class_pima_thumb_get"></a><span data-ttu-id="ea67e-614">ux_host_class_pima_thumb_get</span><span class="sxs-lookup"><span data-stu-id="ea67e-614">ux_host_class_pima_thumb_get</span></span>

<span data-ttu-id="ea67e-615">Получение объекта Thumb, хранящегося в отвечающем устройстве.</span><span class="sxs-lookup"><span data-stu-id="ea67e-615">Get a thumb object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-616">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-616">Prototype</span></span>

```C
UINT ux_host_class_pima_thumb_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *thumb_buffer, ULONG thumb_buffer_length,
    ULONG *thumb_actual_length)
```

### <a name="description"></a><span data-ttu-id="ea67e-617">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-617">Description</span></span>

<span data-ttu-id="ea67e-618">Эта функция получает объект Thumb на стороне отвечающего устройства.</span><span class="sxs-lookup"><span data-stu-id="ea67e-618">This function gets a thumb object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-619">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-619">Parameters</span></span>

- <span data-ttu-id="ea67e-620">**pima** — указатель на экземпляр класса Pima.</span><span class="sxs-lookup"><span data-stu-id="ea67e-620">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="ea67e-621">**pima_session** — указатель на сеанс PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-621">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="ea67e-622">**object_handle** — дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="ea67e-622">**object_handle**: handle of the object.</span></span>
- <span data-ttu-id="ea67e-623">**object** — указатель на контейнер сведений об объекте.</span><span class="sxs-lookup"><span data-stu-id="ea67e-623">**object**: Pointer to object information container.</span></span>
- <span data-ttu-id="ea67e-624">**thumb_buffer** — адрес данных объекта Thumb.</span><span class="sxs-lookup"><span data-stu-id="ea67e-624">**thumb_buffer**: Address of thumb object data.</span></span>
- <span data-ttu-id="ea67e-625">**thumb_buffer_length** — запрошенная длина объекта Thumb.</span><span class="sxs-lookup"><span data-stu-id="ea67e-625">**thumb_buffer_length**: Requested length of thumb object.</span></span>
- <span data-ttu-id="ea67e-626">**thumb_actual_length** — длина возвращаемого объекта Thumb.</span><span class="sxs-lookup"><span data-stu-id="ea67e-626">**thumb_actual_length**: Length of thumb object returned.</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-627">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-627">Return Value</span></span>

- <span data-ttu-id="ea67e-628">**UX_SUCCESS**: (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-628">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="ea67e-629">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт.</span><span class="sxs-lookup"><span data-stu-id="ea67e-629">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="ea67e-630">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) — объект не открыт.</span><span class="sxs-lookup"><span data-stu-id="ea67e-630">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="ea67e-631">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) — отказано в доступе к объекту.</span><span class="sxs-lookup"><span data-stu-id="ea67e-631">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Access to object denied.</span></span>
- <span data-ttu-id="ea67e-632">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) — передача не завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-632">**UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) Transfer is incomplete.</span></span>
- <span data-ttu-id="ea67e-633">**UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-633">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>
- <span data-ttu-id="ea67e-634">**UX_TRANSFER_ERROR**: (0x23) — ошибка передачи при чтении объекта.</span><span class="sxs-lookup"><span data-stu-id="ea67e-634">**UX_TRANSFER_ERROR**: (0x23) Transfer error while reading object.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-635">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-635">Example</span></span>

```C
/* Get the thumb object data. */

status = ux_host_class_pima_thumb_get(pima, pima_session,
    object_handle, pima_object, object_buffer,
    requested_length, &actual_length);

if (status != UX_SUCCESS)
{
    /* And close the object. */
    ux_host_class_pima_object_close(pima, pima_session, object_handle, pima_object, object);

    return(status);
}
```

## <a name="ux_host_class_pima_object_delete"></a><span data-ttu-id="ea67e-636">ux_host_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="ea67e-636">ux_host_class_pima_object_delete</span></span>

<span data-ttu-id="ea67e-637">Удаление объекта, хранящегося в отвечающем устройстве.</span><span class="sxs-lookup"><span data-stu-id="ea67e-637">Delete an object stored in the Responder.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-638">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-638">Prototype</span></span>

```C
UINT ux_host_class_pima_object_delete(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle)
```

### <a name="description"></a><span data-ttu-id="ea67e-639">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-639">Description</span></span>

<span data-ttu-id="ea67e-640">Эта функция удаляет объект на стороне отвечающего устройства.</span><span class="sxs-lookup"><span data-stu-id="ea67e-640">This function deletes an object on the responder</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-641">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-641">Parameters</span></span>

- <span data-ttu-id="ea67e-642">**pima** — указатель на экземпляр класса Pima.</span><span class="sxs-lookup"><span data-stu-id="ea67e-642">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="ea67e-643">**pima_session** — указатель на сеанс PIMA</span><span class="sxs-lookup"><span data-stu-id="ea67e-643">**pima_session**: Pointer to PIMA session</span></span>
- <span data-ttu-id="ea67e-644">**object_handle** — дескриптор объекта</span><span class="sxs-lookup"><span data-stu-id="ea67e-644">**object_handle**: handle of the object</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-645">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-645">Return Value</span></span>

- <span data-ttu-id="ea67e-646">**UX_SUCCESS**: (0x00) — объект удален.</span><span class="sxs-lookup"><span data-stu-id="ea67e-646">**UX_SUCCESS**: (0x00) The object was deleted.</span></span>
- <span data-ttu-id="ea67e-647">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт.</span><span class="sxs-lookup"><span data-stu-id="ea67e-647">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="ea67e-648">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0X200f) — не удается удалить объект.</span><span class="sxs-lookup"><span data-stu-id="ea67e-648">**UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) Cannot delete object.</span></span>
- <span data-ttu-id="ea67e-649">**UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-649">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-650">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-650">Example</span></span>

```C
/* Delete the object. */
status = ux_host_class_pima_object_delete(pima, pima_session, object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_close"></a><span data-ttu-id="ea67e-651">ux_host_class_pima_object_close</span><span class="sxs-lookup"><span data-stu-id="ea67e-651">ux_host_class_pima_object_close</span></span>

<span data-ttu-id="ea67e-652">Закрытие объекта, хранящегося в отвечающем устройстве.</span><span class="sxs-lookup"><span data-stu-id="ea67e-652">Close an object stored in the Responder</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-653">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-653">Prototype</span></span>

```C
UINT ux_host_class_pima_object_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle, UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a><span data-ttu-id="ea67e-654">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-654">Description</span></span>

<span data-ttu-id="ea67e-655">Эта функция закрывает объект на стороне отвечающего устройства.</span><span class="sxs-lookup"><span data-stu-id="ea67e-655">This function closes an object on the responder.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-656">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-656">Parameters</span></span>

- <span data-ttu-id="ea67e-657">**pima** — указатель на экземпляр класса Pima.</span><span class="sxs-lookup"><span data-stu-id="ea67e-657">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="ea67e-658">**pima_session** — указатель на сеанс PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-658">**pima_session**: Pointer to PIMA session.</span></span>
- <span data-ttu-id="ea67e-659">**object_handle** — дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="ea67e-659">**object_handle**: Handle of the object.</span></span>
- <span data-ttu-id="ea67e-660">**object** — указатель на объект.</span><span class="sxs-lookup"><span data-stu-id="ea67e-660">**object**: Pointer to object.</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-661">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-661">Return Value</span></span>

- <span data-ttu-id="ea67e-662">**UX_SUCCESS**: (0x00) — объект закрыт.</span><span class="sxs-lookup"><span data-stu-id="ea67e-662">**UX_SUCCESS**: (0x00) The object was closed.</span></span>
- <span data-ttu-id="ea67e-663">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт.</span><span class="sxs-lookup"><span data-stu-id="ea67e-663">**UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) Session not opened.</span></span>
- <span data-ttu-id="ea67e-664">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) — объект не открыт.</span><span class="sxs-lookup"><span data-stu-id="ea67e-664">**UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) Object not opened.</span></span>
- <span data-ttu-id="ea67e-665">**UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.</span><span class="sxs-lookup"><span data-stu-id="ea67e-665">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory to create PIMA command.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-666">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-666">Example</span></span>

```C
/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle, object);
```

## <a name="ux_host_class_gser_read"></a><span data-ttu-id="ea67e-667">ux_host_class_gser_read</span><span class="sxs-lookup"><span data-stu-id="ea67e-667">ux_host_class_gser_read</span></span>

<span data-ttu-id="ea67e-668">Чтение из универсального последовательного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ea67e-668">Read from the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-669">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-669">Prototype</span></span>

```C
UINT ux_host_class_gser_read(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="ea67e-670">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-670">Description</span></span>

<span data-ttu-id="ea67e-671">Эта функция считывает данные из универсального последовательного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ea67e-671">This function reads from the generic serial interface.</span></span> <span data-ttu-id="ea67e-672">Вызов блокируется и возвращается только в случае ошибки или завершения передачи.</span><span class="sxs-lookup"><span data-stu-id="ea67e-672">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-673">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-673">Parameters</span></span>

- <span data-ttu-id="ea67e-674">**gser** — указатель на экземпляр класса gser.</span><span class="sxs-lookup"><span data-stu-id="ea67e-674">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="ea67e-675">**interface_index** — индекс интерфейса для считывания.</span><span class="sxs-lookup"><span data-stu-id="ea67e-675">**interface_index**: Interface index to read from.</span></span>
- <span data-ttu-id="ea67e-676">**data_pointer** — указатель на адрес буфера полезных данных.</span><span class="sxs-lookup"><span data-stu-id="ea67e-676">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="ea67e-677">**requested_length** — длина для получения.</span><span class="sxs-lookup"><span data-stu-id="ea67e-677">**requested_length**: Length to be received.</span></span>
- <span data-ttu-id="ea67e-678">**actual_length** — фактическая полученная длина.</span><span class="sxs-lookup"><span data-stu-id="ea67e-678">**actual_length**: Length actually received.</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-679">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-679">Return Value</span></span>

- <span data-ttu-id="ea67e-680">**UX_SUCCESS**: (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-680">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="ea67e-681">**UX_TRANSFER_TIMEOUT**: (0x5c) — превышение времени ожидания передачи, чтение не завершено.</span><span class="sxs-lookup"><span data-stu-id="ea67e-681">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-682">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-682">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_gser_read(cdc_acm, interface_index,data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_write"></a><span data-ttu-id="ea67e-683">ux_host_class_gser_write</span><span class="sxs-lookup"><span data-stu-id="ea67e-683">ux_host_class_gser_write</span></span>

<span data-ttu-id="ea67e-684">Запись в универсальный последовательный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ea67e-684">Write to the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-685">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-685">Prototype</span></span>

```C
UINT ux_host_class_gser_write(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="ea67e-686">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-686">Description</span></span>

<span data-ttu-id="ea67e-687">Эта функция выполняет запись в универсальный последовательный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ea67e-687">This function writes to the generic serial interface.</span></span> <span data-ttu-id="ea67e-688">Вызов блокируется и возвращается только в случае ошибки или завершения передачи.</span><span class="sxs-lookup"><span data-stu-id="ea67e-688">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-689">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-689">Parameters</span></span>

- <span data-ttu-id="ea67e-690">**gser** — указатель на экземпляр класса gser.</span><span class="sxs-lookup"><span data-stu-id="ea67e-690">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="ea67e-691">**interface_index** — интерфейс для записи.</span><span class="sxs-lookup"><span data-stu-id="ea67e-691">**interface_index**: Interface to which to write.</span></span>
- <span data-ttu-id="ea67e-692">**data_pointer** — указатель на адрес буфера полезных данных.</span><span class="sxs-lookup"><span data-stu-id="ea67e-692">**data_pointer**: Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="ea67e-693">**requested_length** — длина для отправки.</span><span class="sxs-lookup"><span data-stu-id="ea67e-693">**requested_length**: Length to be sent.</span></span>
- <span data-ttu-id="ea67e-694">**actual_length** — фактическая отправленная длина.</span><span class="sxs-lookup"><span data-stu-id="ea67e-694">**actual_length**: Length actually sent.</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-695">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-695">Return Value</span></span>

- <span data-ttu-id="ea67e-696">**UX_SUCCESS**: (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-696">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="ea67e-697">**UX_TRANSFER_TIMEOUT**: (0x5c) — превышение времени ожидания передачи, запись не завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-697">**UX_TRANSFER_TIMEOUT**: (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-698">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-698">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_cdc_acm_write(gser, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_ioctl"></a><span data-ttu-id="ea67e-699">ux_host_class_gser_ioctl</span><span class="sxs-lookup"><span data-stu-id="ea67e-699">ux_host_class_gser_ioctl</span></span>

<span data-ttu-id="ea67e-700">Выполнение функции IOCTL для универсального последовательного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ea67e-700">Perform an IOCTL function to the generic serial interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-701">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-701">Prototype</span></span>

```C
UINT ux_host_class_gser_ioctl(
    UX_HOST_CLASS_GSER *gser,
    ULONG ioctl_function,
    VOID *parameter)
```

### <a name="description"></a><span data-ttu-id="ea67e-702">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-702">Description</span></span>

<span data-ttu-id="ea67e-703">Эта функция выполняет конкретную функцию IOCTL в интерфейсе gser.</span><span class="sxs-lookup"><span data-stu-id="ea67e-703">This function performs a specific ioctl function to the gser interface.</span></span> <span data-ttu-id="ea67e-704">Вызов блокируется и возвращается только в случае ошибки или после завершения выполнения команды.</span><span class="sxs-lookup"><span data-stu-id="ea67e-704">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-705">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-705">Parameters</span></span>

- <span data-ttu-id="ea67e-706">**gser** — указатель на экземпляр класса gser.</span><span class="sxs-lookup"><span data-stu-id="ea67e-706">**gser**: Pointer to the gser class instance.</span></span>
- <span data-ttu-id="ea67e-707">**ioctl_function** — функция IOCTL для выполнения.</span><span class="sxs-lookup"><span data-stu-id="ea67e-707">**ioctl_function**: ioctl function to be performed.</span></span> <span data-ttu-id="ea67e-708">Допустимые функции IOCTL см. в приведенной ниже таблице.</span><span class="sxs-lookup"><span data-stu-id="ea67e-708">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="ea67e-709">**parameter** — указатель на параметр, относящийся к IOCTL</span><span class="sxs-lookup"><span data-stu-id="ea67e-709">**parameter**: Pointerto a parameter specific to the ioctl</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-710">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-710">Return Value</span></span>

- <span data-ttu-id="ea67e-711">**UX_SUCCESS**: (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-711">**UX_SUCCESS**: (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="ea67e-712">**UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти.</span><span class="sxs-lookup"><span data-stu-id="ea67e-712">**UX_MEMORY_INSUFFICIENT**: (0x12) Not enough memory.</span></span>
- <span data-ttu-id="ea67e-713">**UX_HOST_CLASS_UNKNOWN**: (0X59) — неправильный экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="ea67e-713">**UX_HOST_CLASS_UNKNOWN**: (0x59) Wrong class instance</span></span>
- <span data-ttu-id="ea67e-714">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) — неизвестная функция IOCTL.</span><span class="sxs-lookup"><span data-stu-id="ea67e-714">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) Unknown IOCTL function.</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="ea67e-715">Функции IOCTL</span><span class="sxs-lookup"><span data-stu-id="ea67e-715">IOCTL functions</span></span>

- <span data-ttu-id="ea67e-716">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="ea67e-716">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="ea67e-717">UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="ea67e-717">UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING</span></span>
- <span data-ttu-id="ea67e-718">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="ea67e-718">UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="ea67e-719">UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK</span><span class="sxs-lookup"><span data-stu-id="ea67e-719">UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK</span></span>
- <span data-ttu-id="ea67e-720">UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE</span><span class="sxs-lookup"><span data-stu-id="ea67e-720">UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE</span></span>
- <span data-ttu-id="ea67e-721">UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE</span><span class="sxs-lookup"><span data-stu-id="ea67e-721">UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE</span></span>
- <span data-ttu-id="ea67e-722">UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK</span><span class="sxs-lookup"><span data-stu-id="ea67e-722">UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK</span></span>
- <span data-ttu-id="ea67e-723">UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS</span><span class="sxs-lookup"><span data-stu-id="ea67e-723">UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-724">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-724">Example</span></span>

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_gser_ioctl(gser,
    UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING,
    (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_reception_start"></a><span data-ttu-id="ea67e-725">ux_host_class_gser_reception_start</span><span class="sxs-lookup"><span data-stu-id="ea67e-725">ux_host_class_gser_reception_start</span></span>

<span data-ttu-id="ea67e-726">Начало приема в универсальном последовательном интерфейсе</span><span class="sxs-lookup"><span data-stu-id="ea67e-726">Start reception on the generic serial interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-727">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-727">Prototype</span></span>

```C
UINT ux_host_class_gser_reception_start(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a><span data-ttu-id="ea67e-728">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-728">Description</span></span>

<span data-ttu-id="ea67e-729">Эта функция запускает прием в универсальном последовательном интерфейсе класса.</span><span class="sxs-lookup"><span data-stu-id="ea67e-729">This function starts the reception on the generic serial class interface.</span></span> <span data-ttu-id="ea67e-730">Эта функция разрешает прием без блокировки.</span><span class="sxs-lookup"><span data-stu-id="ea67e-730">This function allows for non-blocking reception.</span></span> <span data-ttu-id="ea67e-731">После получения буфера в приложении выполняется обратный вызов.</span><span class="sxs-lookup"><span data-stu-id="ea67e-731">When a buffer is received, a callback in invoked into the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-732">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-732">Parameters</span></span>

- <span data-ttu-id="ea67e-733">**gser** — указатель на экземпляр класса gser.</span><span class="sxs-lookup"><span data-stu-id="ea67e-733">**gser** Pointer to the gser class instance.</span></span>
- <span data-ttu-id="ea67e-734">**gser_reception** — структура, содержащая параметры приема.</span><span class="sxs-lookup"><span data-stu-id="ea67e-734">**gser_reception** Structure containing the reception parameters</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-735">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-735">Return Value</span></span>

- <span data-ttu-id="ea67e-736">**UX_SUCCESS** (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-736">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="ea67e-737">**UX_HOST_CLASS_UNKNOWN** (0X59) — неправильный экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="ea67e-737">**UX_HOST_CLASS_UNKNOWN** (0x59) Wrong class instance</span></span>
- <span data-ttu-id="ea67e-738">**UX_ERROR** (0x01) — ошибка.</span><span class="sxs-lookup"><span data-stu-id="ea67e-738">**UX_ERROR** (0x01) Error</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-739">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-739">Example</span></span>

```C
/* Start the reception for gser. AT commands are on interface 2. */
gser_reception.ux_host_class_gser_reception_interface_index =
    UX_DEMO_GSER_AT_INTERFACE;
gser_reception.ux_host_class_gser_reception_block_size =
    UX_DEMO_RECEPTION_BLOCK_SIZE;
gser_reception.ux_host_class_gser_reception_data_buffer =
    gser_reception_buffer;
gser_reception.ux_host_class_gser_reception_data_buffer_size =
    UX_DEMO_RECEPTION_BUFFER_SIZE;
gser_reception.ux_host_class_gser_reception_callback =
    tx_demo_thread_callback;

ux_host_class_gser_reception_start(gser, &gser_reception);
```

## <a name="ux_host_class_gser_reception_stop"></a><span data-ttu-id="ea67e-740">ux_host_class_gser_reception_stop</span><span class="sxs-lookup"><span data-stu-id="ea67e-740">ux_host_class_gser_reception_stop</span></span>

<span data-ttu-id="ea67e-741">Остановка приема на универсальном последовательном интерфейсе</span><span class="sxs-lookup"><span data-stu-id="ea67e-741">Stop reception on the generic serial interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ea67e-742">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea67e-742">Prototype</span></span>

```C
UINT ux_host_class_gser_reception_stop(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a><span data-ttu-id="ea67e-743">Описание</span><span class="sxs-lookup"><span data-stu-id="ea67e-743">Description</span></span>

<span data-ttu-id="ea67e-744">Эта функция останавливает прием на интерфейсе универсального последовательного класса.</span><span class="sxs-lookup"><span data-stu-id="ea67e-744">This function stops the reception on the generic serial class interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="ea67e-745">Параметры</span><span class="sxs-lookup"><span data-stu-id="ea67e-745">Parameters</span></span>

- <span data-ttu-id="ea67e-746">**gser** — указатель на экземпляр класса gser.</span><span class="sxs-lookup"><span data-stu-id="ea67e-746">**gser** Pointer to the gser class instance.</span></span>
- <span data-ttu-id="ea67e-747">**gser_reception** — структура, содержащая параметры приема.</span><span class="sxs-lookup"><span data-stu-id="ea67e-747">**gser_reception** Structure containing the reception parameters</span></span>

### <a name="return-value"></a><span data-ttu-id="ea67e-748">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="ea67e-748">Return Value</span></span>

- <span data-ttu-id="ea67e-749">**UX_SUCCESS** (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="ea67e-749">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="ea67e-750">**UX_HOST_CLASS_UNKNOWN** (0X59) — неправильный экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="ea67e-750">**UX_HOST_CLASS_UNKNOWN** (0x59) Wrong class instance</span></span>
- <span data-ttu-id="ea67e-751">**UX_ERROR** (0x01) — ошибка.</span><span class="sxs-lookup"><span data-stu-id="ea67e-751">**UX_ERROR** (0x01) Error</span></span>

### <a name="example"></a><span data-ttu-id="ea67e-752">Пример</span><span class="sxs-lookup"><span data-stu-id="ea67e-752">Example</span></span>

```C
/* Stops the reception for gser. */
ux_host_class_gser_reception_stop(gser, &gser_reception);
```
