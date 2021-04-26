---
title: Глава 5. API классов узлов USBX
description: Сведения об API классов узлов USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: bf5876042e08a59979adcd429917bfc3fbfdbc20
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816467"
---
# <a name="chapter-5---usbx-host-classes-api"></a><span data-ttu-id="efde9-103">Глава 5. API классов узлов USBX</span><span class="sxs-lookup"><span data-stu-id="efde9-103">Chapter 5 - USBX Host Classes API</span></span>

<span data-ttu-id="efde9-104">В этой главе рассматриваются все предоставляемые API классов узлов USBX.</span><span class="sxs-lookup"><span data-stu-id="efde9-104">This chapter covers all the exposed APIs of the USBX host classes.</span></span> <span data-ttu-id="efde9-105">Ниже подробно описаны следующие интерфейсы API для каждого класса.</span><span class="sxs-lookup"><span data-stu-id="efde9-105">The following APIs for each class are described in detail.</span></span>

- <span data-ttu-id="efde9-106">Класс HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-106">HID class</span></span>
- <span data-ttu-id="efde9-107">Класс CDC-ACM.</span><span class="sxs-lookup"><span data-stu-id="efde9-107">CDC-ACM class</span></span>
- <span data-ttu-id="efde9-108">Класс CDC-ECM.</span><span class="sxs-lookup"><span data-stu-id="efde9-108">CDC-ECM class</span></span>
- <span data-ttu-id="efde9-109">Класс хранения</span><span class="sxs-lookup"><span data-stu-id="efde9-109">Storage class</span></span>

## <a name="ux_host_class_hid_client_register"></a><span data-ttu-id="efde9-110">ux_host_class_hid_client_register</span><span class="sxs-lookup"><span data-stu-id="efde9-110">ux_host_class_hid_client_register</span></span>

<span data-ttu-id="efde9-111">Регистрация клиента HID для класса HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-111">Register a HID client to the HID class.</span></span>

### <a name="prototype"></a><span data-ttu-id="efde9-112">Прототип</span><span class="sxs-lookup"><span data-stu-id="efde9-112">Prototype</span></span>

```c
UINT ux_host_class_hid_client_register(
    UCHAR *hid_client_name,
    UINT (*hid_client_handler)
    (struct UX_HOST_CLASS_HID_CLIENT_COMMAND_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="efde9-113">Описание</span><span class="sxs-lookup"><span data-stu-id="efde9-113">Description</span></span>

<span data-ttu-id="efde9-114">Эта функция используется для регистрации клиента HID в классе HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-114">This function is used to register a HID client to the HID class.</span></span> <span data-ttu-id="efde9-115">Классу HID необходимо найти соответствие между HID-устройством и клиентом HID перед запросом данных с этого устройства.</span><span class="sxs-lookup"><span data-stu-id="efde9-115">The HID class needs to find a match between a HID device and HID client before requesting data from this device.</span></span>

> [!NOTE]
> <span data-ttu-id="efde9-116">Строка C объекта hid_client_name должна завершаться нулем и ее длина (без конечного нуля) не должна быть больше, чем **UX_HOST_CLASS_HID_MAX_CLIENT_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="efde9-116">The C string of hid_client_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_HOST_CLASS_HID_MAX_CLIENT_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="efde9-117">Параметры</span><span class="sxs-lookup"><span data-stu-id="efde9-117">Parameters</span></span>

- <span data-ttu-id="efde9-118">**hid_client_name** — указатель на имя клиента HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-118">**hid_client_name** Pointer to the HID client name.</span></span>
- <span data-ttu-id="efde9-119">**hid_client_handler** — указатель на обработчик клиента HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-119">**hid_client_handler** Pointer to the HID client handler.</span></span>

### <a name="return-values"></a><span data-ttu-id="efde9-120">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="efde9-120">Return Values</span></span>

- <span data-ttu-id="efde9-121">**UX_SUCCESS** (0x00) — передача данных завершена</span><span class="sxs-lookup"><span data-stu-id="efde9-121">**UX_SUCCESS** (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="efde9-122">**UX_MEMORY_INSUFFICIENT** (0x12) — сбой выделения памяти для клиента.</span><span class="sxs-lookup"><span data-stu-id="efde9-122">**UX_MEMORY_INSUFFICIENT** (0x12) Memory allocation for client failed.</span></span>
- <span data-ttu-id="efde9-123">**UX_MEMORY_ARRAY_FULL** (0X1a) — максимальное количество клиентов уже зарегистрировано.</span><span class="sxs-lookup"><span data-stu-id="efde9-123">**UX_MEMORY_ARRAY_FULL** (0x1a) Max clients already registered.</span></span>
- <span data-ttu-id="efde9-124">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) — этот класс уже существует.</span><span class="sxs-lookup"><span data-stu-id="efde9-124">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) This class already exists</span></span>

### <a name="example"></a><span data-ttu-id="efde9-125">Пример</span><span class="sxs-lookup"><span data-stu-id="efde9-125">Example</span></span>

```c
UINT status;

/* The following example illustrates how to register a HID client, in
this case a USB mouse, to the HID class. */

status = ux_host_class_hid_client_register("ux_host_class_hid_client_mouse",
    ux_host_class_hid_mouse_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_callback_register"></a><span data-ttu-id="efde9-126">ux_host_class_hid_report_callback_register</span><span class="sxs-lookup"><span data-stu-id="efde9-126">ux_host_class_hid_report_callback_register</span></span>

<span data-ttu-id="efde9-127">Регистрация обратного вызова из класса HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-127">Register a callback from the HID class.</span></span>

### <a name="prototype"></a><span data-ttu-id="efde9-128">Прототип</span><span class="sxs-lookup"><span data-stu-id="efde9-128">Prototype</span></span>

```c
UINT ux_host_class_hid_report_callback_register(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_REPORT_CALLBACK *call_back);
```

### <a name="description"></a><span data-ttu-id="efde9-129">Описание</span><span class="sxs-lookup"><span data-stu-id="efde9-129">Description</span></span>

<span data-ttu-id="efde9-130">Эта функция используется для регистрации обратного вызова из класса HID к клиенту HID при получении отчета.</span><span class="sxs-lookup"><span data-stu-id="efde9-130">This function is used to register a callback from the HID class to the HID client when a report is received.</span></span>

### <a name="parameters"></a><span data-ttu-id="efde9-131">Параметры</span><span class="sxs-lookup"><span data-stu-id="efde9-131">Parameters</span></span>

- <span data-ttu-id="efde9-132">**hid** — указатель на экземпляр класса HID</span><span class="sxs-lookup"><span data-stu-id="efde9-132">**hid** Pointer to the HID class instance</span></span>
- <span data-ttu-id="efde9-133">**call_back** — указатель на структуру call_back.</span><span class="sxs-lookup"><span data-stu-id="efde9-133">**call_back** Pointer to the call_back structure</span></span>

### <a name="return-values"></a><span data-ttu-id="efde9-134">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="efde9-134">Return values</span></span>

- <span data-ttu-id="efde9-135">**UX_SUCCESS** (0x00) — передача данных завершена</span><span class="sxs-lookup"><span data-stu-id="efde9-135">**UX_SUCCESS** (0x00) The data transfer was completed</span></span>
- <span data-ttu-id="efde9-136">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — недопустимый экземпляр HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-136">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) Invalid HID instance.</span></span>
- <span data-ttu-id="efde9-137">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x79) — ошибка при регистрации обратного вызова в отчете.</span><span class="sxs-lookup"><span data-stu-id="efde9-137">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x79) Error in the report callback registration.</span></span>

### <a name="example"></a><span data-ttu-id="efde9-138">Пример</span><span class="sxs-lookup"><span data-stu-id="efde9-138">Example</span></span>

```c
UINT status;

/* This example illustrates how to register a HID client, in this case a USB mouse, to the HID class. In this case, the HID client is asking the HID class to call the client for each usage received in the HID report. */

call_back.ux_host_class_hid_report_callback_id = 0;
call_back.ux_host_class_hid_report_callback_function = ux_host_class_hid_mouse_callback;

call_back.ux_host_class_hid_report_callback_buffer = UX_NULL;
call_back.ux_host_class_hid_report_callback_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

call_back.ux_host_class_hid_report_callback_length = 0;

status = ux_host_class_hid_report_callback_register(hid, &call_back);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_start"></a><span data-ttu-id="efde9-139">ux_host_class_hid_periodic_report_start</span><span class="sxs-lookup"><span data-stu-id="efde9-139">ux_host_class_hid_periodic_report_start</span></span>

<span data-ttu-id="efde9-140">Запуск периодической конечной точки для экземпляра класса HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-140">Start the periodic endpoint for a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="efde9-141">Прототип</span><span class="sxs-lookup"><span data-stu-id="efde9-141">Prototype</span></span>

```c
UINT ux_host_class_hid_periodic_report_start(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a><span data-ttu-id="efde9-142">Описание</span><span class="sxs-lookup"><span data-stu-id="efde9-142">Description</span></span>

<span data-ttu-id="efde9-143">Эта функция используется для запуска периодической (с прерываниями) конечной точки для экземпляра класса HID, привязанного к этому клиенту HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-143">This function is used to start the periodic (interrupt) endpoint for the instance of the HID class that is bound to this HID client.</span></span> <span data-ttu-id="efde9-144">Класс HID не может запустить периодическую конечную точку, пока клиент HID не будет активирован и, следовательно, клиент HID должен запустить эту конечную точку для получения отчетов.</span><span class="sxs-lookup"><span data-stu-id="efde9-144">The HID class cannot start the periodic endpoint until the HID client is activated and therefore it is left to the HID client to start this endpoint to receive reports.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="efde9-145">Входной параметр</span><span class="sxs-lookup"><span data-stu-id="efde9-145">Input Parameter</span></span>

- <span data-ttu-id="efde9-146">**hid** — указатель на экземпляр класса HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-146">**hid** Pointer to the HID class instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="efde9-147">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="efde9-147">Return Values</span></span>

- <span data-ttu-id="efde9-148">**UX_SUCCESS** (0x00) — периодическая отчетность успешно запущена.</span><span class="sxs-lookup"><span data-stu-id="efde9-148">**UX_SUCCESS** (0x00) Periodic reporting successfully started.</span></span>
- <span data-ttu-id="efde9-149">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) — ошибка в периодическом отчете.</span><span class="sxs-lookup"><span data-stu-id="efde9-149">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Error in the periodic report.</span></span>
- <span data-ttu-id="efde9-150">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — экземпляр класса HID не существует.</span><span class="sxs-lookup"><span data-stu-id="efde9-150">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="efde9-151">Пример</span><span class="sxs-lookup"><span data-stu-id="efde9-151">Example</span></span>

```c
UINT status;

/* The following example illustrates how to start the periodic
endpoint. */

status = ux_host_class_hid_periodic_report_start(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_periodic_report_stop"></a><span data-ttu-id="efde9-152">ux_host_class_hid_periodic_report_stop</span><span class="sxs-lookup"><span data-stu-id="efde9-152">ux_host_class_hid_periodic_report_stop</span></span>

<span data-ttu-id="efde9-153">Остановка периодической конечной точки для экземпляра класса HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-153">Stop the periodic endpoint for a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="efde9-154">Прототип</span><span class="sxs-lookup"><span data-stu-id="efde9-154">Prototype</span></span>

```c
UINT ux_host_class_hid_periodic_report_stop(UX_HOST_CLASS_HID *hid);
```

### <a name="description"></a><span data-ttu-id="efde9-155">Описание</span><span class="sxs-lookup"><span data-stu-id="efde9-155">Description</span></span>

<span data-ttu-id="efde9-156">Эта функция используется для остановки периодической (с прерываниями) конечной точки для экземпляра класса HID, привязанного к этому клиенту HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-156">This function is used to stop the periodic (interrupt) endpoint for the instance of the HID class that is bound to this HID client.</span></span> <span data-ttu-id="efde9-157">Класс HID не может остановить периодическую конечную точку, пока клиент HID не будет деактивирован с освобождением всех его ресурсов и, следовательно, клиент HID должен запустить эту конечную точку для получения отчетов.</span><span class="sxs-lookup"><span data-stu-id="efde9-157">The HID class cannot stop the periodic endpoint until the HID client is deactivated, all its resources freed and therefore it is left to the HID client to stop this endpoint.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="efde9-158">Входной параметр</span><span class="sxs-lookup"><span data-stu-id="efde9-158">Input Parameter</span></span>

- <span data-ttu-id="efde9-159">**hid** — указатель на экземпляр класса HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-159">**hid** Pointer to the HID class instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="efde9-160">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="efde9-160">Return Values</span></span>

- <span data-ttu-id="efde9-161">**UX_SUCCESS** (0x00) — периодическая отчетность успешно остановлена.</span><span class="sxs-lookup"><span data-stu-id="efde9-161">**UX_SUCCESS** (0x00) Periodic reporting successfully stopped.</span></span>
- <span data-ttu-id="efde9-162">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) — ошибка в периодическом отчете.</span><span class="sxs-lookup"><span data-stu-id="efde9-162">**ux_host_class_hid_PERIODIC_REPORT_ERROR** (0x7A) Error in the periodic report.</span></span>
- <span data-ttu-id="efde9-163">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — экземпляр класса HID не существует</span><span class="sxs-lookup"><span data-stu-id="efde9-163">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist</span></span>

### <a name="example"></a><span data-ttu-id="efde9-164">Пример</span><span class="sxs-lookup"><span data-stu-id="efde9-164">Example</span></span>

```c
UINT status;

/* The following example illustrates how to stop the periodic endpoint. */

status = ux_host_class_hid_periodic_report_stop(hid);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_get"></a><span data-ttu-id="efde9-165">ux_host_class_hid_report_get</span><span class="sxs-lookup"><span data-stu-id="efde9-165">ux_host_class_hid_report_get</span></span>

<span data-ttu-id="efde9-166">Получение отчета из экземпляра класса HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-166">Get a report from a HID class instance.</span></span>

### <a name="prototype"></a><span data-ttu-id="efde9-167">Прототип</span><span class="sxs-lookup"><span data-stu-id="efde9-167">Prototype</span></span>

```c
UINT ux_host_class_hid_report_get(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a><span data-ttu-id="efde9-168">Описание</span><span class="sxs-lookup"><span data-stu-id="efde9-168">Description</span></span>

<span data-ttu-id="efde9-169">Эта функция используется для получения отчета непосредственно с устройства, не полагаясь на периодическую конечную точку.</span><span class="sxs-lookup"><span data-stu-id="efde9-169">This function is used to receive a report directly from the device without relying on the periodic endpoint.</span></span> <span data-ttu-id="efde9-170">Этот отчет поступает от конечной точки элемента управления, но его обработка будет такой же, как если бы он поступал на периодическую конечную точку.</span><span class="sxs-lookup"><span data-stu-id="efde9-170">This report is coming from the control endpoint but its treatment is the same as though it were coming on the periodic endpoint.</span></span>

### <a name="parameters"></a><span data-ttu-id="efde9-171">Параметры</span><span class="sxs-lookup"><span data-stu-id="efde9-171">Parameters</span></span>

- <span data-ttu-id="efde9-172">**hid** — указатель на экземпляр класса HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-172">**hid** Pointer to the HID class instance.</span></span>
- <span data-ttu-id="efde9-173">**client_report** — указатель на отчет клиента HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-173">**client_report** Pointer to the HID client report.</span></span>

### <a name="return-values"></a><span data-ttu-id="efde9-174">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="efde9-174">Return Values</span></span>

- <span data-ttu-id="efde9-175">**UX_SUCCESS** (0x00) — отчет успешно получен.</span><span class="sxs-lookup"><span data-stu-id="efde9-175">**UX_SUCCESS** (0x00) The report was successfully received.</span></span>
- <span data-ttu-id="efde9-176">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) — отчет клиента был недопустимым или произошла ошибка во время передачи.</span><span class="sxs-lookup"><span data-stu-id="efde9-176">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) Either client report was invalid or error during transfer.</span></span>
- <span data-ttu-id="efde9-177">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — экземпляр класса HID не существует.</span><span class="sxs-lookup"><span data-stu-id="efde9-177">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>
- <span data-ttu-id="efde9-178">**UX_BUFFER_OVERFLOW** (0x5d) — предоставленный буфер недостаточно большой для размещения несжатого отчета.</span><span class="sxs-lookup"><span data-stu-id="efde9-178">**UX_BUFFER_OVERFLOW** (0x5d) The buffer supplied is not big enough to accommodate the uncompressed report.</span></span>

### <a name="example"></a><span data-ttu-id="efde9-179">Пример</span><span class="sxs-lookup"><span data-stu-id="efde9-179">Example</span></span>

```c
UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

UINT status;

/* The following example illustrates how to get a report. */

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_get(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_report_set"></a><span data-ttu-id="efde9-180">ux_host_class_hid_report_set</span><span class="sxs-lookup"><span data-stu-id="efde9-180">ux_host_class_hid_report_set</span></span>

<span data-ttu-id="efde9-181">Отправка отчета</span><span class="sxs-lookup"><span data-stu-id="efde9-181">Send a report</span></span>

### <a name="prototype"></a><span data-ttu-id="efde9-182">Прототип</span><span class="sxs-lookup"><span data-stu-id="efde9-182">Prototype</span></span>

```c
UINT ux_host_class_hid_report_set(
    UX_HOST_CLASS_HID *hid,
    UX_HOST_CLASS_HID_CLIENT_REPORT *client_report);
```

### <a name="description"></a><span data-ttu-id="efde9-183">Описание</span><span class="sxs-lookup"><span data-stu-id="efde9-183">Description</span></span>

<span data-ttu-id="efde9-184">Эта функция используется для отправки отчета непосредственно на устройство.</span><span class="sxs-lookup"><span data-stu-id="efde9-184">This function is used to send a report directly to the device.</span></span>

### <a name="parameters"></a><span data-ttu-id="efde9-185">Параметры</span><span class="sxs-lookup"><span data-stu-id="efde9-185">Parameters</span></span>

- <span data-ttu-id="efde9-186">**hid** — указатель на экземпляр класса HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-186">**hid** Pointer to the HID class instance.</span></span>
- <span data-ttu-id="efde9-187">**client_report** — указатель на отчет клиента HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-187">**client_report** Pointer to the HID client report.</span></span>

### <a name="return-values"></a><span data-ttu-id="efde9-188">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="efde9-188">Return Values</span></span>

- <span data-ttu-id="efde9-189">**UX_SUCCESS** (0x00) — отчет успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="efde9-189">**UX_SUCCESS** (0x00) The report was successfully sent.</span></span>
- <span data-ttu-id="efde9-190">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) — отчет клиента был недопустимым или произошла ошибка во время передачи.</span><span class="sxs-lookup"><span data-stu-id="efde9-190">**UX_HOST_CLASS_HID_REPORT_ERROR** (0x70) Either client report was invalid or error during transfer.</span></span>
- <span data-ttu-id="efde9-191">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — экземпляр класса HID не существует.</span><span class="sxs-lookup"><span data-stu-id="efde9-191">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>
- <span data-ttu-id="efde9-192">**UX_HOST_CLASS_HID_REPORT_OVERFLOW** (0x5d) — предоставленный буфер недостаточно большой для размещения несжатого отчета.</span><span class="sxs-lookup"><span data-stu-id="efde9-192">**UX_HOST_CLASS_HID_REPORT_OVERFLOW** (0x5d) The buffer supplied is not big enough to accommodate the uncompressed report.</span></span>

### <a name="example"></a><span data-ttu-id="efde9-193">Пример</span><span class="sxs-lookup"><span data-stu-id="efde9-193">Example</span></span>

```c
/* The following example illustrates how to send a report. */

UX_HOST_CLASS_HID_CLIENT_REPORT input_report;

input_report.ux_host_class_hid_client_report = hid_report;
input_report.ux_host_class_hid_client_report_buffer = buffer;
input_report.ux_host_class_hid_client_report_length = length;
input_report.ux_host_class_hid_client_report_flags = UX_HOST_CLASS_HID_REPORT_INDIVIDUAL_USAGE;

status = ux_host_class_hid_report_set(hid, &input_report);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_buttons_get"></a><span data-ttu-id="efde9-194">ux_host_class_hid_mouse_buttons_get</span><span class="sxs-lookup"><span data-stu-id="efde9-194">ux_host_class_hid_mouse_buttons_get</span></span>

<span data-ttu-id="efde9-195">Получение кнопок мыши.</span><span class="sxs-lookup"><span data-stu-id="efde9-195">Get mouse buttons.</span></span>

### <a name="prototype"></a><span data-ttu-id="efde9-196">Прототип</span><span class="sxs-lookup"><span data-stu-id="efde9-196">Prototype</span></span>

```c
UINT ux_host_class_hid_mouse_buttons_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    ULONG *mouse_buttons);
```

### <a name="description"></a><span data-ttu-id="efde9-197">Описание</span><span class="sxs-lookup"><span data-stu-id="efde9-197">Description</span></span>

<span data-ttu-id="efde9-198">Эта функция используется для получения кнопок мыши.</span><span class="sxs-lookup"><span data-stu-id="efde9-198">This function is used to get the mouse buttons</span></span>

### <a name="parameters"></a><span data-ttu-id="efde9-199">Параметры</span><span class="sxs-lookup"><span data-stu-id="efde9-199">Parameters</span></span>

- <span data-ttu-id="efde9-200">**mouse_instance** — указатель на экземпляр мыши HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-200">**mouse_instance** Pointer to the HID mouse instance.</span></span>
- <span data-ttu-id="efde9-201">**mouse_buttons** — указатель на кнопки возврата.</span><span class="sxs-lookup"><span data-stu-id="efde9-201">**mouse_buttons** Pointer to the return buttons.</span></span>

### <a name="return-values"></a><span data-ttu-id="efde9-202">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="efde9-202">Return Values</span></span>

- <span data-ttu-id="efde9-203">**UX_SUCCESS** (0x00) — кнопка мыши успешно извлечена.</span><span class="sxs-lookup"><span data-stu-id="efde9-203">**UX_SUCCESS** (0x00) Mouse button successfully retrieved.</span></span>
- <span data-ttu-id="efde9-204">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — экземпляр класса HID не существует.</span><span class="sxs-lookup"><span data-stu-id="efde9-204">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="efde9-205">Пример</span><span class="sxs-lookup"><span data-stu-id="efde9-205">Example</span></span>

```c
/* The following example illustrates how to obtain mouse buttons. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

ULONG mouse_buttons;

status = ux_host_class_hid_mouse_button_get(mouse_instance, &mouse_buttons);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_mouse_position_get"></a><span data-ttu-id="efde9-206">ux_host_class_hid_mouse_position_get</span><span class="sxs-lookup"><span data-stu-id="efde9-206">ux_host_class_hid_mouse_position_get</span></span>

<span data-ttu-id="efde9-207">Получение расположения мыши.</span><span class="sxs-lookup"><span data-stu-id="efde9-207">Get mouse position.</span></span>

### <a name="prototype"></a><span data-ttu-id="efde9-208">Прототип</span><span class="sxs-lookup"><span data-stu-id="efde9-208">Prototype</span></span>

```c
UINT ux_host_class_hid_mouse_position_get(
    UX_HOST_CLASS_HID_MOUSE *mouse_instance,
    SLONG *mouse_x_position, 
    SLONG *mouse_y_position);
```

### <a name="description"></a><span data-ttu-id="efde9-209">Описание</span><span class="sxs-lookup"><span data-stu-id="efde9-209">Description</span></span>

<span data-ttu-id="efde9-210">Эта функция используется для получения расположения мыши с координатами x и y.</span><span class="sxs-lookup"><span data-stu-id="efde9-210">This function is used to get the mouse position in x & y coordinates.</span></span>

### <a name="parameters"></a><span data-ttu-id="efde9-211">Параметры</span><span class="sxs-lookup"><span data-stu-id="efde9-211">Parameters</span></span>

- <span data-ttu-id="efde9-212">**mouse_instance** — указатель на экземпляр мыши HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-212">**mouse_instance** Pointer to the HID mouse instance.</span></span>
- <span data-ttu-id="efde9-213">**mouse_x_position** —указатель на координату x.</span><span class="sxs-lookup"><span data-stu-id="efde9-213">**mouse_x_position** Pointer to the x coordinate.</span></span>
- <span data-ttu-id="efde9-214">**mouse_y_position** —указатель на координату y.</span><span class="sxs-lookup"><span data-stu-id="efde9-214">**mouse_y_position** Pointer to the y coordinate.</span></span>

### <a name="return-values"></a><span data-ttu-id="efde9-215">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="efde9-215">Return Values</span></span>

- <span data-ttu-id="efde9-216">**UX_SUCCESS** (0x00) — координаты X и Y успешно извлечены.</span><span class="sxs-lookup"><span data-stu-id="efde9-216">**UX_SUCCESS** (0x00) X &amp; Y coordinates successfully retrieved.</span></span>
- <span data-ttu-id="efde9-217">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — экземпляр класса HID не существует.</span><span class="sxs-lookup"><span data-stu-id="efde9-217">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="efde9-218">Пример</span><span class="sxs-lookup"><span data-stu-id="efde9-218">Example</span></span>

```c
/* The following example illustrates how to obtain mouse coordinates. */

UX_HOST_CLASS_HID_MOUSE *mouse_instance;

SLONG mouse_x_position;
SLONG mouse_y_position;

status = ux_host_class_hid_mouse_position_get(mouse_instance,
    &mouse_x_position, &mouse_y_position);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_keyboard_key_get"></a><span data-ttu-id="efde9-219">ux_host_class_hid_keyboard_key_get</span><span class="sxs-lookup"><span data-stu-id="efde9-219">ux_host_class_hid_keyboard_key_get</span></span>

<span data-ttu-id="efde9-220">Получение клавиши и состояния клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="efde9-220">Get keyboard key and state.</span></span>

### <a name="prototype"></a><span data-ttu-id="efde9-221">Прототип</span><span class="sxs-lookup"><span data-stu-id="efde9-221">Prototype</span></span>

```c
UINT ux_host_class_hid_keyboard_key_get(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG *keyboard_key, 
    ULONG *keyboard_state);
```

### <a name="description"></a><span data-ttu-id="efde9-222">Описание</span><span class="sxs-lookup"><span data-stu-id="efde9-222">Description</span></span>

<span data-ttu-id="efde9-223">Эта функция используется для получения клавиши и состояния клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="efde9-223">This function is used to get the keyboard key and state.</span></span>

### <a name="parameters"></a><span data-ttu-id="efde9-224">Параметры</span><span class="sxs-lookup"><span data-stu-id="efde9-224">Parameters</span></span>

- <span data-ttu-id="efde9-225">**keyboard_instance** — указатель на экземпляр клавиатуры HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-225">**keyboard_instance** Pointer to the HID keyboard instance.</span></span>
- <span data-ttu-id="efde9-226">**keyboard_key** — указатель на контейнер клавиши клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="efde9-226">**keyboard_key** Pointer to keyboard key container.</span></span>
- <span data-ttu-id="efde9-227">**keyboard_state** — указатель на контейнер состояния клавиатуры.</span><span class="sxs-lookup"><span data-stu-id="efde9-227">**keyboard_state** Pointer to the keyboard state container.</span></span>

### <a name="return-values"></a><span data-ttu-id="efde9-228">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="efde9-228">Return Values</span></span>

- <span data-ttu-id="efde9-229">**UX_SUCCESS** (0x00) — клавиша и состояние успешно извлечены.</span><span class="sxs-lookup"><span data-stu-id="efde9-229">**UX_SUCCESS** (0x00) Key and state successfully retrieved.</span></span>
- <span data-ttu-id="efde9-230">**UX_ERROR** (0xff) — данные для отчета отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="efde9-230">**UX_ERROR** (0xff) Nothing to report.</span></span>
- <span data-ttu-id="efde9-231">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — экземпляр класса HID не существует.</span><span class="sxs-lookup"><span data-stu-id="efde9-231">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

<span data-ttu-id="efde9-232">Состояние клавиатуры может принимать указанные ниже значения.</span><span class="sxs-lookup"><span data-stu-id="efde9-232">The keyboard state can have the following values.</span></span>

- <span data-ttu-id="efde9-233">**UX_HID_KEYBOARD_STATE_KEY_UP** 0x10000</span><span class="sxs-lookup"><span data-stu-id="efde9-233">**UX_HID_KEYBOARD_STATE_KEY_UP** 0x10000</span></span>
- <span data-ttu-id="efde9-234">**UX_HID_KEYBOARD_STATE_NUM_LOCK** 0x0001</span><span class="sxs-lookup"><span data-stu-id="efde9-234">**UX_HID_KEYBOARD_STATE_NUM_LOCK** 0x0001</span></span>
- <span data-ttu-id="efde9-235">**UX_HID_KEYBOARD_STATE_CAPS_LOCK** 0x0002</span><span class="sxs-lookup"><span data-stu-id="efde9-235">**UX_HID_KEYBOARD_STATE_CAPS_LOCK** 0x0002</span></span>
- <span data-ttu-id="efde9-236">**UX_HID_KEYBOARD_STATE_SCROLL_LOCK** 0x0004</span><span class="sxs-lookup"><span data-stu-id="efde9-236">**UX_HID_KEYBOARD_STATE_SCROLL_LOCK** 0x0004</span></span>
- <span data-ttu-id="efde9-237">**UX_HID_KEYBOARD_STATE_MASK_LOCK** 0x0007</span><span class="sxs-lookup"><span data-stu-id="efde9-237">**UX_HID_KEYBOARD_STATE_MASK_LOCK** 0x0007</span></span>
- <span data-ttu-id="efde9-238">**UX_HID_KEYBOARD_STATE_LEFT_SHIFT** 0x0100</span><span class="sxs-lookup"><span data-stu-id="efde9-238">**UX_HID_KEYBOARD_STATE_LEFT_SHIFT** 0x0100</span></span>
- <span data-ttu-id="efde9-239">**UX_HID_KEYBOARD_STATE_RIGHT_SHIFT** 0x0200</span><span class="sxs-lookup"><span data-stu-id="efde9-239">**UX_HID_KEYBOARD_STATE_RIGHT_SHIFT** 0x0200</span></span>
- <span data-ttu-id="efde9-240">**UX_HID_KEYBOARD_STATE_SHIFT** 0x0300</span><span class="sxs-lookup"><span data-stu-id="efde9-240">**UX_HID_KEYBOARD_STATE_SHIFT** 0x0300</span></span>
- <span data-ttu-id="efde9-241">**UX_HID_KEYBOARD_STATE_LEFT_ALT** 0x0400</span><span class="sxs-lookup"><span data-stu-id="efde9-241">**UX_HID_KEYBOARD_STATE_LEFT_ALT** 0x0400</span></span>
- <span data-ttu-id="efde9-242">**UX_HID_KEYBOARD_STATE_RIGHT_ALT** 0x0800</span><span class="sxs-lookup"><span data-stu-id="efde9-242">**UX_HID_KEYBOARD_STATE_RIGHT_ALT** 0x0800</span></span>
- <span data-ttu-id="efde9-243">**UX_HID_KEYBOARD_STATE_ALT** 0x0a00</span><span class="sxs-lookup"><span data-stu-id="efde9-243">**UX_HID_KEYBOARD_STATE_ALT** 0x0a00</span></span>
- <span data-ttu-id="efde9-244">**UX_HID_KEYBOARD_STATE_LEFT_CTRL** 0x1000</span><span class="sxs-lookup"><span data-stu-id="efde9-244">**UX_HID_KEYBOARD_STATE_LEFT_CTRL** 0x1000</span></span>
- <span data-ttu-id="efde9-245">**UX_HID_KEYBOARD_STATE_RIGHT_CTRL** 0x2000</span><span class="sxs-lookup"><span data-stu-id="efde9-245">**UX_HID_KEYBOARD_STATE_RIGHT_CTRL** 0x2000</span></span>
- <span data-ttu-id="efde9-246">**UX_HID_KEYBOARD_STATE_CTRL** 0x3000</span><span class="sxs-lookup"><span data-stu-id="efde9-246">**UX_HID_KEYBOARD_STATE_CTRL** 0x3000</span></span>
- <span data-ttu-id="efde9-247">**UX_HID_KEYBOARD_STATE_LEFT_GUI** 0x4000</span><span class="sxs-lookup"><span data-stu-id="efde9-247">**UX_HID_KEYBOARD_STATE_LEFT_GUI** 0x4000</span></span>
- <span data-ttu-id="efde9-248">**UX_HID_KEYBOARD_STATE_RIGHT_GUI** 0x8000</span><span class="sxs-lookup"><span data-stu-id="efde9-248">**UX_HID_KEYBOARD_STATE_RIGHT_GUI** 0x8000</span></span>
- <span data-ttu-id="efde9-249">**UX_HID_KEYBOARD_STATE_GUI** 0xa000</span><span class="sxs-lookup"><span data-stu-id="efde9-249">**UX_HID_KEYBOARD_STATE_GUI** 0xa000</span></span>

### <a name="example"></a><span data-ttu-id="efde9-250">Пример</span><span class="sxs-lookup"><span data-stu-id="efde9-250">Example</span></span>

```c
while (1)
{

    /* Get a key/state from the keyboard. */
    status = ux_host_class_hid_keyboard_key_get(keyboard,
        &keyboard_char, &keyboard_state);

    /* Check if there is something. */
    if (status == UX_SUCCESS)
    {

        #ifdef UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE
            if (keyboard_state & UX_HID_KEYBOARD_STATE_KEY_UP)
            {
                /* The key was released. */
            } else
            {
                /* The key was pressed. */
            }
        #endif

        /* We have a character in the queue. */
        keyboard_queue[keyboard_queue_index] = (UCHAR) keyboard_char;

        /* Can we accept more ? */
        if(keyboard_queue_index < 1024)
            keyboard_queue_index++;
    }

    tx_thread_sleep(10);

}
```

## <a name="ux_host_class_hid_keyboard_ioctl"></a><span data-ttu-id="efde9-251">ux_host_class_hid_keyboard_ioctl</span><span class="sxs-lookup"><span data-stu-id="efde9-251">ux_host_class_hid_keyboard_ioctl</span></span>

<span data-ttu-id="efde9-252">Выполнение функции IOCTL для клавиатуры HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-252">Perform an IOCTL function to the HID keyboard.</span></span>

### <a name="prototype"></a><span data-ttu-id="efde9-253">Прототип</span><span class="sxs-lookup"><span data-stu-id="efde9-253">Prototype</span></span>

```c
UINT ux_host_class_hid_keyboard_ioctl(
    UX_HOST_CLASS_HID_KEYBOARD *keyboard_instance,
    ULONG ioctl_function, VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="efde9-254">Описание</span><span class="sxs-lookup"><span data-stu-id="efde9-254">Description</span></span>

<span data-ttu-id="efde9-255">Эта функция выполняет конкретную функцию IOCTL для клавиатуры HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-255">This function performs a specific ioctl function to the HID keyboard.</span></span> <span data-ttu-id="efde9-256">Вызов блокируется и возвращается только в случае ошибки или после завершения выполнения команды.</span><span class="sxs-lookup"><span data-stu-id="efde9-256">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="efde9-257">Параметры</span><span class="sxs-lookup"><span data-stu-id="efde9-257">Parameters</span></span>

- <span data-ttu-id="efde9-258">**keyboard_instance** — указатель на экземпляр клавиатуры HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-258">**keyboard_instance** Pointer to the HID keyboard instance.</span></span>
- <span data-ttu-id="efde9-259">**ioctl_function** — функция IOCTL для выполнения.</span><span class="sxs-lookup"><span data-stu-id="efde9-259">**ioctl_function** ioctl function to be performed.</span></span> <span data-ttu-id="efde9-260">Допустимые функции IOCTL см. в приведенной ниже таблице.</span><span class="sxs-lookup"><span data-stu-id="efde9-260">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="efde9-261">**parameter** — указатель на параметр, относящийся к IOCTL.</span><span class="sxs-lookup"><span data-stu-id="efde9-261">**parameter** Pointer to a parameter specific to the ioctl.</span></span>

### <a name="return-values"></a><span data-ttu-id="efde9-262">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="efde9-262">Return Values</span></span>

- <span data-ttu-id="efde9-263">**UX_SUCCESS** (0x00) — функция IOCTL успешно завершена.</span><span class="sxs-lookup"><span data-stu-id="efde9-263">**UX_SUCCESS** (0x00) The ioctl function completed successfully.</span></span>
- <span data-ttu-id="efde9-264">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) — неизвестная функция IOCTL</span><span class="sxs-lookup"><span data-stu-id="efde9-264">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Unknown IOCTL function</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="efde9-265">Функции IOCTL</span><span class="sxs-lookup"><span data-stu-id="efde9-265">IOCTL functions</span></span>

- <span data-ttu-id="efde9-266">UX_HID_KEYBOARD_IOCTL_SET_LAYOUT</span><span class="sxs-lookup"><span data-stu-id="efde9-266">UX_HID_KEYBOARD_IOCTL_SET_LAYOUT</span></span>
- <span data-ttu-id="efde9-267">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_ENABLE</span><span class="sxs-lookup"><span data-stu-id="efde9-267">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_ENABLE</span></span>
- <span data-ttu-id="efde9-268">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_DISABLE</span><span class="sxs-lookup"><span data-stu-id="efde9-268">UX_HID_KEYBOARD_IOCTL_KEY_DECODING_DISABLE</span></span>

### <a name="example--change-keyboard-layout"></a><span data-ttu-id="efde9-269">Пример. Изменение раскладки клавиатуры</span><span class="sxs-lookup"><span data-stu-id="efde9-269">Example – change keyboard layout</span></span>

```c
UINT status;

/* This example shows usage of the SET_LAYOUT IOCTL function.
    USBX receives raw key values from the device (these raw values
    are defined in the HID usage table specification) and optionally
    decodes them for application usage. The decoding is performed
    based on a set of arrays that act as maps – which array is used
    depends on the raw key value (i.e. keypad and non-keypad) and
    the current state of the keyboard (i.e. shift, caps lock, etc.). */

/* When the shift condition is not present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_unshifted_map[] =
{
    0,0,0,0,
    'a','b','c','d','e','f','g',
    'h','i','j','k','l','m','n',
    'o','p','q','r','s','t',
    'u','v','w','x','y','z',
    '1','2','3','4','5','6','7','8','9','0',
    0x0d,0x1b,0x08,0x07,0x20,'-','=','[',']',
    '\\','#',';',0x27,'`',',','.','/',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When the shift condition is present and the raw key value
    is not within the keypad value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_shifted_map[] =
{
    0,0,0,0,
    'A','B','C','D','E','F','G',
    'H','I','J','K','L','M','N',
    'O','P','Q','R','S','T',
    'U','V','W','X','Y','Z',
    '!','@','#','$','%','^','&','*','(',')',
    0x0d,0x1b,0x08,0x07,0x20,'_','+','{','}',
    '|','~',':','"','~','<','>','?',0xf0,
    0xbb,0xbc,0xbd,0xbe,0xbf,0xc0,0xc1,0xc2,0xc3,0xc4,0xc5,0xc6,
    0x00,0xf1,0x00,0xd2,0xc7,0xc9,0xd3,0xcf,0xd1,0xcd,0xcd,0xd0,0xc8,0xf2,
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
    0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,0x00,
};

/* When numlock is on and the raw key value is within the keypad
    value range, this array will be used to decode the raw key value. */

static UCHAR keyboard_layout_raw_to_numlock_on_map[] =
{
    '/','*','-','+',
    0x0d,'1','2','3','4','5','6','7','8','9','0','.','\\',0x00,0x00,'=',
};

/* When numlock is off and the raw key value is within the keypad value
    range, this array will be used to decode the raw key value. */
static UCHAR keyboard_layout_raw_to_numlock_off_map[] =
{
    '/','*','-','+',
    0x0d,0xcf,0xd0,0xd1,0xcb,'5',0xcd,0xc7,0xc8,0xc9,0xd2,0xd3,'\\',0x00,0x
    00,'=',
};

/* Specify the keyboard layout for USBX usage. */
static UX_HOST_CLASS_HID_KEYBOARD_LAYOUT keyboard_layout =
{
    keyboard_layout_raw_to_shifted_map,
    keyboard_layout_raw_to_unshifted_map,
    keyboard_layout_raw_to_numlock_on_map,
    keyboard_layout_raw_to_numlock_off_map,
    /* The maximum raw key value. Values larger than this are discarded. */
    UX_HID_KEYBOARD_KEYS_UPPER_RANGE,
    /* The raw key value for the letter 'a'. */
    UX_HID_KEYBOARD_KEY_LETTER_A,
    /* The raw key value for the letter 'z'. */
    UX_HID_KEYBOARD_KEY_LETTER_Z,
    /* The lower range raw key value for keypad keys - inclusive. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_LOWER_RANGE,
    /* The upper range raw key value for keypad keys. */
    UX_HID_KEYBOARD_KEYS_KEYPAD_UPPER_RANGE
};

/* Call the IOCTL function to change the keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_SET_LAYOUT, (VOID *)&keyboard_layout);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="example--disable-keyboard-key-decode"></a><span data-ttu-id="efde9-270">Пример. Отключение декодирования клавиш клавиатуры</span><span class="sxs-lookup"><span data-stu-id="efde9-270">Example – disable keyboard key decode</span></span>

```c
UINT status;

/* The following example illustrates IOCTL function of Disable key decode from keyboard layout. */
status = ux_host_class_hid_keyboard_ioctl(keyboard,
    UX_HID_KEYBOARD_IOCTL_DISABLE_KEYS_DECODE, UX_NULL);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_hid_remote_control_usage_get"></a><span data-ttu-id="efde9-271">ux_host_class_hid_remote_control_usage_get</span><span class="sxs-lookup"><span data-stu-id="efde9-271">ux_host_class_hid_remote_control_usage_get</span></span>

<span data-ttu-id="efde9-272">Получение использования удаленного управления</span><span class="sxs-lookup"><span data-stu-id="efde9-272">Get remote control usage</span></span>

### <a name="prototype"></a><span data-ttu-id="efde9-273">Прототип</span><span class="sxs-lookup"><span data-stu-id="efde9-273">Prototype</span></span>

```c
UINT ux_host_class_hid_remote_control_usage_get(
    UX_HOST_CLASS_HID_REMOTE_CONTROL *remote_control_instance,
    LONG *usage, 
    ULONG *value);
```

### <a name="description"></a><span data-ttu-id="efde9-274">Описание</span><span class="sxs-lookup"><span data-stu-id="efde9-274">Description</span></span>

<span data-ttu-id="efde9-275">Эта функция используется для получения использований удаленного управления.</span><span class="sxs-lookup"><span data-stu-id="efde9-275">This function is used to get the remote control usages.</span></span>

### <a name="parameters"></a><span data-ttu-id="efde9-276">Параметры</span><span class="sxs-lookup"><span data-stu-id="efde9-276">Parameters</span></span>

- <span data-ttu-id="efde9-277">**remote_control_instance** — указатель на экземпляр удаленного управления HID.</span><span class="sxs-lookup"><span data-stu-id="efde9-277">**remote_control_instance** Pointer to the HID remote control instance.</span></span>
- <span data-ttu-id="efde9-278">**usage** — указатель на использование.</span><span class="sxs-lookup"><span data-stu-id="efde9-278">**usage** Pointer to the usage.</span></span>
- <span data-ttu-id="efde9-279">**value** — указатель на значение для использования.</span><span class="sxs-lookup"><span data-stu-id="efde9-279">**value** Pointer to the value for the usage.</span></span>

### <a name="return-values"></a><span data-ttu-id="efde9-280">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="efde9-280">Return Values</span></span>

- <span data-ttu-id="efde9-281">**UX_SUCCESS** (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="efde9-281">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="efde9-282">**UX_ERROR** (0xff) — данные для отчета отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="efde9-282">**UX_ERROR** (0xff) Nothing to report.</span></span>
- <span data-ttu-id="efde9-283">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — экземпляр класса HID не существует.</span><span class="sxs-lookup"><span data-stu-id="efde9-283">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) HID class instance does not exist.</span></span>

<span data-ttu-id="efde9-284">Список всех возможных использований слишком длинный и не вмещается в этом руководстве пользователя.</span><span class="sxs-lookup"><span data-stu-id="efde9-284">The list of all possible usages is too long to fit in this user guide.</span></span> <span data-ttu-id="efde9-285">Полное описание можно просмотреть в файле ux_host_class_hid.h, в котором приведен полный набор возможных значений.</span><span class="sxs-lookup"><span data-stu-id="efde9-285">For a full description, the ux_host_class_hid.h has the entire set of possible values.</span></span>

### <a name="example"></a><span data-ttu-id="efde9-286">Пример</span><span class="sxs-lookup"><span data-stu-id="efde9-286">Example</span></span>

```c
/* Read usages and values as the user changes the vol/bass/treble buttons on the speaker */

while (remote_control != UX_NULL)
{
    status = ux_host_class_hid_remote_control_usage_get(remote_control, &usage, &value);
    if (status == UX_SUCCESS)
    {
        /* We have something coming from the HID remote control,
        we filter the usage here and only allow the
        volume usage which can be VOLUME, VOLUME_INCREMENT or VOLUME_DECREMENT */
        switch(usage)
        {
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_INCREMENT :
            case UX_HOST_CLASS_HID_CONSUMER_VOLUME_DECREMENT :

            if (value<0x80)
            {
                if (current_volume + audio_control.ux_host_class_audio_control_res < 0xffff)
                    current_volume = current_volume + audio_control.ux_host_class_audio_control_res;
                } else {
                if (current_volume > audio_control.ux_host_class_audio_control_res)
                    current_volume = current_volumeaudio_control.ux_host_class_audio_control_res;
            }

            audio_control.ux_host_class_audio_control_channel = 1;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            audio_control.ux_host_class_audio_control_channel = 2;
            audio_control.ux_host_class_audio_control = UX_HOST_CLASS_AUDIO_VOLUME_CONTROL;
            audio_control.ux_host_class_audio_control_cur = current_volume;
            status = ux_host_class_audio_control_value_set(audio, &audio_control);
            break;

        }
    }
    tx_thread_sleep(10);

}
```

### <a name="ux_host_class_cdc_acm_read"></a><span data-ttu-id="efde9-287">ux_host_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="efde9-287">ux_host_class_cdc_acm_read</span></span>

<span data-ttu-id="efde9-288">Чтение из интерфейса cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="efde9-288">Read from the cdc_acm interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="efde9-289">Прототип</span><span class="sxs-lookup"><span data-stu-id="efde9-289">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_read(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="efde9-290">Описание</span><span class="sxs-lookup"><span data-stu-id="efde9-290">Description</span></span>

<span data-ttu-id="efde9-291">Эта функция считывает данные из интерфейса cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="efde9-291">This function reads from the cdc_acm interface.</span></span> <span data-ttu-id="efde9-292">Вызов блокируется и возвращается только в случае ошибки или завершения передачи.</span><span class="sxs-lookup"><span data-stu-id="efde9-292">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="efde9-293">Параметры</span><span class="sxs-lookup"><span data-stu-id="efde9-293">Parameters</span></span>

- <span data-ttu-id="efde9-294">**cdc_acm** — указатель на экземпляр класса cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="efde9-294">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="efde9-295">**data_pointer** — указатель на адрес буфера полезных данных.</span><span class="sxs-lookup"><span data-stu-id="efde9-295">**data_pointer** Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="efde9-296">**requested_length** — длина для получения.</span><span class="sxs-lookup"><span data-stu-id="efde9-296">**requested_length** Length to be received.</span></span>
- <span data-ttu-id="efde9-297">**actual_length** — фактическая полученная длина.</span><span class="sxs-lookup"><span data-stu-id="efde9-297">**actual_length** Length actually received.</span></span>

### <a name="return-values"></a><span data-ttu-id="efde9-298">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="efde9-298">Return Values</span></span>

- <span data-ttu-id="efde9-299">**UX_SUCCESS** (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="efde9-299">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="efde9-300">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — недопустимый экземпляр cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="efde9-300">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The cdc_acm instance is invalid.</span></span>
- <span data-ttu-id="efde9-301">**UX_TRANSFER_TIMEOUT** (0x5c) — превышение времени ожидания передачи, чтение не завершено.</span><span class="sxs-lookup"><span data-stu-id="efde9-301">**UX_TRANSFER_TIMEOUT** (0x5c) Transfer timeout, reading incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="efde9-302">Пример</span><span class="sxs-lookup"><span data-stu-id="efde9-302">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_read(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_write"></a><span data-ttu-id="efde9-303">ux_host_class_cdc_acm_write</span><span class="sxs-lookup"><span data-stu-id="efde9-303">ux_host_class_cdc_acm_write</span></span>

<span data-ttu-id="efde9-304">Запись в интерфейс cdc_acm</span><span class="sxs-lookup"><span data-stu-id="efde9-304">Write to the cdc_acm interface</span></span>

### <a name="prototype"></a><span data-ttu-id="efde9-305">Прототип</span><span class="sxs-lookup"><span data-stu-id="efde9-305">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_write(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UCHAR *data_pointer, 
    ULONG requested_length, 
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="efde9-306">Описание</span><span class="sxs-lookup"><span data-stu-id="efde9-306">Description</span></span>

<span data-ttu-id="efde9-307">Эта функция записывает данные в интерфейс cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="efde9-307">This function writes to the cdc_acm interface.</span></span> <span data-ttu-id="efde9-308">Вызов блокируется и возвращается только в случае ошибки или завершения передачи.</span><span class="sxs-lookup"><span data-stu-id="efde9-308">The call is blocking and only returns when there is either an error or when the transfer is complete.</span></span>

### <a name="parameters"></a><span data-ttu-id="efde9-309">Параметры</span><span class="sxs-lookup"><span data-stu-id="efde9-309">Parameters</span></span>

- <span data-ttu-id="efde9-310">**cdc_acm** — указатель на экземпляр класса cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="efde9-310">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="efde9-311">**data_pointer** — указатель на адрес буфера полезных данных.</span><span class="sxs-lookup"><span data-stu-id="efde9-311">**data_pointer** Pointer to the buffer address of the data payload.</span></span>
- <span data-ttu-id="efde9-312">**requested_length** — длина для отправки.</span><span class="sxs-lookup"><span data-stu-id="efde9-312">**requested_length** Length to be sent.</span></span>
- <span data-ttu-id="efde9-313">**actual_length** — фактическая отправленная длина.</span><span class="sxs-lookup"><span data-stu-id="efde9-313">**actual_length** Length actually sent.</span></span>

### <a name="return-values"></a><span data-ttu-id="efde9-314">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="efde9-314">Return Values</span></span>

- <span data-ttu-id="efde9-315">**UX_SUCCESS** (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="efde9-315">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="efde9-316">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — недопустимый экземпляр cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="efde9-316">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The cdc_acm instance is invalid.</span></span>
- <span data-ttu-id="efde9-317">**UX_TRANSFER_TIMEOUT** (0x5c) — превышение времени ожидания передачи, запись не завершена.</span><span class="sxs-lookup"><span data-stu-id="efde9-317">**UX_TRANSFER_TIMEOUT** (0x5c) Transfer timeout, writing incomplete.</span></span>

### <a name="example"></a><span data-ttu-id="efde9-318">Пример</span><span class="sxs-lookup"><span data-stu-id="efde9-318">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_write(cdc_acm, data_pointer,
    requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_ioctl"></a><span data-ttu-id="efde9-319">ux_host_class_cdc_acm_ioctl</span><span class="sxs-lookup"><span data-stu-id="efde9-319">ux_host_class_cdc_acm_ioctl</span></span>

<span data-ttu-id="efde9-320">Выполнение функции IOCTL для интерфейса cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="efde9-320">Perform an IOCTL function to the cdc_acm interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="efde9-321">Прототип</span><span class="sxs-lookup"><span data-stu-id="efde9-321">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_ioctl(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function, 
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="efde9-322">Описание</span><span class="sxs-lookup"><span data-stu-id="efde9-322">Description</span></span>

<span data-ttu-id="efde9-323">Эта функция выполняет конкретную функцию IOCTL для интерфейса cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="efde9-323">This function performs a specific ioctl function to the cdc_acm interface.</span></span> <span data-ttu-id="efde9-324">Вызов блокируется и возвращается только в случае ошибки или после завершения выполнения команды.</span><span class="sxs-lookup"><span data-stu-id="efde9-324">The call is blocking and only returns when there is either an error or when the command is completed.</span></span>

### <a name="parameters"></a><span data-ttu-id="efde9-325">Параметры</span><span class="sxs-lookup"><span data-stu-id="efde9-325">Parameters</span></span>

- <span data-ttu-id="efde9-326">**cdc_acm** — указатель на экземпляр класса cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="efde9-326">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="efde9-327">**ioctl_function** — функция IOCTL для выполнения.</span><span class="sxs-lookup"><span data-stu-id="efde9-327">**ioctl_function** ioctl function to be performed.</span></span> <span data-ttu-id="efde9-328">Допустимые функции IOCTL см. в приведенной ниже таблице.</span><span class="sxs-lookup"><span data-stu-id="efde9-328">See table below for one of the allowed ioctl functions.</span></span>
- <span data-ttu-id="efde9-329">**parameter** — указатель на параметр, относящийся к IOCTL</span><span class="sxs-lookup"><span data-stu-id="efde9-329">**parameter** Pointer to a parameter specific to the ioctl</span></span>

### <a name="return-value"></a><span data-ttu-id="efde9-330">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="efde9-330">Return Value</span></span>

- <span data-ttu-id="efde9-331">**UX_SUCCESS** (0x00) — передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="efde9-331">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="efde9-332">**UX_MEMORY_INSUFFICIENT** (0x12) — недостаточно памяти.</span><span class="sxs-lookup"><span data-stu-id="efde9-332">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory.</span></span>
- <span data-ttu-id="efde9-333">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — недопустимое состояние экземпляра CDC-ACM.</span><span class="sxs-lookup"><span data-stu-id="efde9-333">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) CDC-ACM instance is in an invalid state.</span></span>
- <span data-ttu-id="efde9-334">**UX_FUNCTION_NOT_SUPPORTED** (0x54) — неизвестная функция IOCTL.</span><span class="sxs-lookup"><span data-stu-id="efde9-334">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Unknown IOCTL function.</span></span>

### <a name="ioctl-functions"></a><span data-ttu-id="efde9-335">Функции IOCTL:</span><span class="sxs-lookup"><span data-stu-id="efde9-335">IOCTL functions:</span></span>

- <span data-ttu-id="efde9-336">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="efde9-336">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="efde9-337">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="efde9-337">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>
- <span data-ttu-id="efde9-338">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="efde9-338">UX_HOST_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="efde9-339">UX_HOST_CLASS_CDC_ACM_IOCTL_SEND_BREAK</span><span class="sxs-lookup"><span data-stu-id="efde9-339">UX_HOST_CLASS_CDC_ACM_IOCTL_SEND_BREAK</span></span>
- <span data-ttu-id="efde9-340">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_IN_PIPE</span><span class="sxs-lookup"><span data-stu-id="efde9-340">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_IN_PIPE</span></span>
- <span data-ttu-id="efde9-341">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_OUT_PIPE</span><span class="sxs-lookup"><span data-stu-id="efde9-341">UX_HOST_CLASS_CDC_ACM_IOCTL_ABORT_OUT_PIPE</span></span>
- <span data-ttu-id="efde9-342">UX_HOST_CLASS_CDC_ACM_IOCTL_NOTIFICATION_CALLBACK</span><span class="sxs-lookup"><span data-stu-id="efde9-342">UX_HOST_CLASS_CDC_ACM_IOCTL_NOTIFICATION_CALLBACK</span></span>
- <span data-ttu-id="efde9-343">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_DEVICE_STATUS</span><span class="sxs-lookup"><span data-stu-id="efde9-343">UX_HOST_CLASS_CDC_ACM_IOCTL_GET_DEVICE_STATUS</span></span>

```c
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_cdc_acm_ioctl(cdc_acm,
    UX_HOST_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_cdc_acm_reception_start"></a><span data-ttu-id="efde9-344">ux_host_class_cdc_acm_reception_start</span><span class="sxs-lookup"><span data-stu-id="efde9-344">ux_host_class_cdc_acm_reception_start</span></span>

<span data-ttu-id="efde9-345">Начинает фоновый прием данных с устройства.</span><span class="sxs-lookup"><span data-stu-id="efde9-345">Begins background reception of data from the device.</span></span>

### <a name="prototype"></a><span data-ttu-id="efde9-346">Прототип</span><span class="sxs-lookup"><span data-stu-id="efde9-346">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_reception_start(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a><span data-ttu-id="efde9-347">Описание</span><span class="sxs-lookup"><span data-stu-id="efde9-347">Description</span></span>

<span data-ttu-id="efde9-348">С помощью этой функции USBX непрерывно считывает данные с устройства в фоновом режиме.</span><span class="sxs-lookup"><span data-stu-id="efde9-348">This function causes USBX to continuously read data from the device in the background.</span></span> <span data-ttu-id="efde9-349">По завершении каждой транзакции выполняется обратный вызов, указанный в **cdc_acm_reception**. Он необходим для того, чтобы приложение могло выполнять дальнейшую обработку данных транзакции.</span><span class="sxs-lookup"><span data-stu-id="efde9-349">Upon completion of each transaction, the callback specified in **cdc_acm_reception** is invoked so the application may perform further processing of the transaction's data.</span></span>

> [!NOTE]
> <span data-ttu-id="efde9-350">Функцию **ux_host_class_cdc_acm_read** нельзя использовать, пока выполняется фоновый прием.</span><span class="sxs-lookup"><span data-stu-id="efde9-350">**ux_host_class_cdc_acm_read** must not be used while background reception is in use.</span></span>

### <a name="parameters"></a><span data-ttu-id="efde9-351">Параметры</span><span class="sxs-lookup"><span data-stu-id="efde9-351">Parameters</span></span>

- <span data-ttu-id="efde9-352">**cdc_acm** — указатель на экземпляр класса cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="efde9-352">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="efde9-353">**cdc_acm_reception** — указатель на параметр, который содержит значения, определяющие поведение фонового приема.</span><span class="sxs-lookup"><span data-stu-id="efde9-353">**cdc_acm_reception** Pointer to parameter that contains values defining behavior of background reception.</span></span> <span data-ttu-id="efde9-354">Структура этого параметра выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="efde9-354">The layout of this parameter follows:</span></span>

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a><span data-ttu-id="efde9-355">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="efde9-355">Return Value</span></span>

- <span data-ttu-id="efde9-356">**UX_SUCCESS** (0x00) — фоновый прием успешно запущен.</span><span class="sxs-lookup"><span data-stu-id="efde9-356">**UX_SUCCESS** (0x00) Background reception successfully started.</span></span>
- <span data-ttu-id="efde9-357">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — неправильный экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="efde9-357">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Wrong class instance.</span></span>

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Setup the background reception parameter. */

/* Set the desired max read size for each transaction.
    For example, if this value is 64, then the maximum amount of
    data received from the device in a single transaction is 64.
    If the amount of data received from the device is less than this value,
    the callback will still be invoked with the actual amount of data received. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_block_size = block_size;

/* Set the buffer where the data from the device is read to. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer = cdc_acm_reception_buffer;

/* Set the size of the data reception buffer.
    Note that this should be at least as large as ux_host_class_cdc_acm_reception_block_size. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_data_buffer_size = cdc_acm_reception_buffer_size;

/* Set the callback that is to be invoked upon each reception transfer completion. */
cdc_acm_reception.ux_host_class_cdc_acm_reception_callback = reception_callback;

/* Start background reception using the values we defined in the reception parameter. */
status = ux_host_class_cdc_acm_reception_start(cdc_acm_host_data, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully started. */
```

## <a name="ux_host_class_cdc_acm_reception_stop"></a><span data-ttu-id="efde9-358">ux_host_class_cdc_acm_reception_stop</span><span class="sxs-lookup"><span data-stu-id="efde9-358">ux_host_class_cdc_acm_reception_stop</span></span>

<span data-ttu-id="efde9-359">Останавливает фоновый прием пакетов.</span><span class="sxs-lookup"><span data-stu-id="efde9-359">Stops background reception of packets.</span></span>

### <a name="prototype"></a><span data-ttu-id="efde9-360">Прототип</span><span class="sxs-lookup"><span data-stu-id="efde9-360">Prototype</span></span>

```c
UINT ux_host_class_cdc_acm_reception_stop(
    UX_HOST_CLASS_CDC_ACM *cdc_acm,
    UX_HOST_CLASS_CDC_ACM_RECEPTION *cdc_acm_reception);
```

### <a name="description"></a><span data-ttu-id="efde9-361">Описание</span><span class="sxs-lookup"><span data-stu-id="efde9-361">Description</span></span>

<span data-ttu-id="efde9-362">С помощью этой функции USBX останавливает фоновый прием, ранее запущенный **ux_host_class_cdc_acm_reception_start**.</span><span class="sxs-lookup"><span data-stu-id="efde9-362">This function causes USBX to stop background reception previously started by **ux_host_class_cdc_acm_reception_start**.</span></span>

### <a name="parameters"></a><span data-ttu-id="efde9-363">Параметры</span><span class="sxs-lookup"><span data-stu-id="efde9-363">Parameters</span></span>

- <span data-ttu-id="efde9-364">**cdc_acm** — указатель на экземпляр класса cdc_acm.</span><span class="sxs-lookup"><span data-stu-id="efde9-364">**cdc_acm** Pointer to the cdc_acm class instance.</span></span>
- <span data-ttu-id="efde9-365">**cdc_acm_reception** — указатель на тот же параметр, который использовался для запуска фонового приема.</span><span class="sxs-lookup"><span data-stu-id="efde9-365">**cdc_acm_reception** Pointer to the same parameter that was used to start background reception.</span></span> <span data-ttu-id="efde9-366">Структура этого параметра выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="efde9-366">The layout of this parameter follows:</span></span>

```c
typedef struct UX_HOST_CLASS_CDC_ACM_RECEPTION_STRUCT
{
    ULONG ux_host_class_cdc_acm_reception_state;
    ULONG ux_host_class_cdc_acm_reception_block_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_buffer;
    ULONG ux_host_class_cdc_acm_reception_data_buffer_size;
    UCHAR *ux_host_class_cdc_acm_reception_data_head;
    UCHAR *ux_host_class_cdc_acm_reception_data_tail;
    VOID (*ux_host_class_cdc_acm_reception_callback)(
            struct UX_HOST_CLASS_CDC_ACM_STRUCT *cdc_acm, UINT status,
            UCHAR *reception_buffer, ULONG reception_size);
} UX_HOST_CLASS_CDC_ACM_RECEPTION;
```

### <a name="return-value"></a><span data-ttu-id="efde9-367">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="efde9-367">Return Value</span></span>

- <span data-ttu-id="efde9-368">**UX_SUCCESS** (0x00) — фоновый прием успешно остановлен.</span><span class="sxs-lookup"><span data-stu-id="efde9-368">**UX_SUCCESS** (0x00) Background reception successfully stopped.</span></span>
- <span data-ttu-id="efde9-369">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — неправильный экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="efde9-369">**UX_HOST_CLASS_INSTANCE _UNKNOWN** (0x5b) Wrong class instance.</span></span>

```c
UINT status;
UX_HOST_CLASS_CDC_ACM_RECEPTION cdc_acm_reception;

/* Stop background reception. The reception parameter should be the same
    that was passed to ux_host_class_cdc_acm_reception_start. */
status = ux_host_class_cdc_acm_reception_stop(cdc_acm, &cdc_acm_reception);

/* If status equals UX_SUCCESS, background reception has successfully stopped. */
```
