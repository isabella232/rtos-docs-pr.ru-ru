---
title: Реализация PictBridge в USBX
description: USBX поддерживает полную реализацию PictBridge как на узле, так и на устройстве. С обеих сторон PictBridge размещается поверх класса USBX PIMA.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ce291f794cbc458d402cbefa3fd81dcc6f371b57
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816079"
---
# <a name="chapter-4-usbx-pictbridge-implementation"></a><span data-ttu-id="25d23-104">Глава 4. Реализация PictBridge в USBX</span><span class="sxs-lookup"><span data-stu-id="25d23-104">Chapter 4: USBX Pictbridge implementation</span></span>

<span data-ttu-id="25d23-105">USBX поддерживает полную реализацию PictBridge как на узле, так и на устройстве.</span><span class="sxs-lookup"><span data-stu-id="25d23-105">UBSX supports the full Pictbridge implementation both on the host and the device.</span></span> <span data-ttu-id="25d23-106">С обеих сторон PictBridge размещается поверх класса USBX PIMA.</span><span class="sxs-lookup"><span data-stu-id="25d23-106">Pictbridge sits on top of USBX PIMA class on both sides.</span></span> 

<span data-ttu-id="25d23-107">Стандарты PictBridge обеспечивают подключение цифровой фотокамеры или смартфона непосредственно к принтеру, без компьютера в качестве посредника, и позволяют напрямую выполнять печатать на принтерах, поддерживающих этот стандарт PictBridge.</span><span class="sxs-lookup"><span data-stu-id="25d23-107">The PictBridge standards allows the connection of a digital still camera or a smart phone directly to a printer without a PC, enabling direct printing to certain Pictbridge aware printers.</span></span>

<span data-ttu-id="25d23-108">Когда камера или телефон подключаются к принтеру, этот принтер является USB-узлом, а камера — USB-устройством.</span><span class="sxs-lookup"><span data-stu-id="25d23-108">When a camera or phone is connected to a printer, the printer is the USB host and the camera is the USB device.</span></span> <span data-ttu-id="25d23-109">Но при работе с PictBridge камера отображается как узел и управляет командами для печати.</span><span class="sxs-lookup"><span data-stu-id="25d23-109">However, with Pictbridge, the camera will appear as being the host and commands are driven from the camera.</span></span> <span data-ttu-id="25d23-110">Камера является сервером хранилища, а принтер выполняет роль клиента хранилища.</span><span class="sxs-lookup"><span data-stu-id="25d23-110">The camera is the storage server, the printer the storage client.</span></span> <span data-ttu-id="25d23-111">С другой стороны, принтер является сервером печати, а камера подключается к нему как клиент.</span><span class="sxs-lookup"><span data-stu-id="25d23-111">The camera is the print client and the printer is, of course, the print server.</span></span>

<span data-ttu-id="25d23-112">PictBridge использует транспортный уровень USB и протокол связи PTP (протокол передачи изображений).</span><span class="sxs-lookup"><span data-stu-id="25d23-112">Pictbridge uses USB as a transport layer but relies on PTP (Picture Transfer Protocol) for the communication protocol.</span></span>

<span data-ttu-id="25d23-113">Ниже представлена схема передачи команд и ответов между клиентом DPS и сервером DPS при выполнении задания печати.</span><span class="sxs-lookup"><span data-stu-id="25d23-113">The following is a diagram of the commands/responses between the DPS client and the DPS server when a print job occurs.</span></span>

![Схема передачи команд и ответов между клиентом DPS и сервером DPS при выполнении задания печати.](./media/usbx-host-stack-supplemental/dps-client-server.png)

## <a name="pictbridge-client-implementation"></a><span data-ttu-id="25d23-115">Реализация клиента PictBridge</span><span class="sxs-lookup"><span data-stu-id="25d23-115">Pictbridge client implementation</span></span>

<span data-ttu-id="25d23-116">Для использования PictBridge на клиенте нужно сначала запустить стек устройств USBX и класс PIMA.</span><span class="sxs-lookup"><span data-stu-id="25d23-116">The Pictbridge on the client requires the USBX device stack and the PIMA class to be running first.</span></span>

<span data-ttu-id="25d23-117">Платформа устройства описывает класс PIMA следующим образом.</span><span class="sxs-lookup"><span data-stu-id="25d23-117">A device framework describes the PIMA class in the following way.</span></span>

```C
UCHAR device_framework_full_speed[] =
{
    /* Device descriptor */
       0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x20,
       0xA9, 0x04, 0xB6, 0x30, 0x00, 0x00, 0x00, 0x00,
       0x00, 0x01,
    /* Configuration descriptor */
       0x09, 0x02, 0x27, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,
    /* Interface descriptor */
       0x09, 0x04, 0x00, 0x00, 0x03, 0x06, 0x01, 0x01, 0x00,
    /* Endpoint descriptor (Bulk Out) */
       0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,
    /* Endpoint descriptor (Bulk In) */
       0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00,
    /* Endpoint descriptor (Interrupt) */
       0x07, 0x05, 0x83, 0x03, 0x08, 0x00, 0x60
};
```

<span data-ttu-id="25d23-118">Класс PIMA использует значение 0x06 в поле ID (идентификатор), а также подкласс 0x01 для изображения и протокол 0x01 для PIMA 15740.</span><span class="sxs-lookup"><span data-stu-id="25d23-118">The Pima class is using the ID field 0x06 and has its subclass is 0x01 for Still Image and the protocol is 0x01 for PIMA 15740.</span></span>

<span data-ttu-id="25d23-119">В этом классе определены три конечные точки, из них две — для отправки и получения данных, а третья — для прерываний по событиям.</span><span class="sxs-lookup"><span data-stu-id="25d23-119">3 endpoints are defined in this class, 2 bulks for sending/receiving data and one interrupt for events.</span></span>

<span data-ttu-id="25d23-120">В отличие от реализаций других устройств USBX, приложению PictBridge не нужно определять сам класс.</span><span class="sxs-lookup"><span data-stu-id="25d23-120">Unlike other USBX device implementations, the Pictbridge application does not need to define a class itself.</span></span> <span data-ttu-id="25d23-121">Достаточно вызвать функцию ***ux_pictbridge_dpsclient_start***.</span><span class="sxs-lookup"><span data-stu-id="25d23-121">Rather it invokes the function ***ux_pictbridge_dpsclient_start***.</span></span> <span data-ttu-id="25d23-122">Пример представлен ниже.</span><span class="sxs-lookup"><span data-stu-id="25d23-122">An example is below:</span></span>

```C
/* Initialize the Pictbridge string components. */
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name,
    "Azure RTOS",10);
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name,
    "EL_Pictbridge_Camera",21);
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no, "ABC_123",7);
ux_utility_memory_copy
    (pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions,
    "1.0 1.1",7);

pictbridge.ux_pictbridge_dpslocal.
    ux_pictbridge_devinfo_vendor_specific_version = 0x0100;

/* Start the Pictbridge client. */
status = ux_pictbridge_dpsclient_start(&pictbridge);

if(status != UX_SUCCESS)
    return;
```

<span data-ttu-id="25d23-123">Ниже перечислены параметры, которые передаются клиенту PictBridge:</span><span class="sxs-lookup"><span data-stu-id="25d23-123">The parameters passed to the pictbridge client are as follows:</span></span>

```C
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name
    : String of Vendor name pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name
    : String of product name pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no,
    : String of serial number pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions
    : String of version pictbridge.ux_pictbridge_dpslocal. ux_pictbridge_devinfo_vendor_specific_version
    : Value set to 0x0100;
```

<span data-ttu-id="25d23-124">После этого требуется синхронизация устройства и узла и переход к состоянию готовности к обмену данными.</span><span class="sxs-lookup"><span data-stu-id="25d23-124">The next step is for the device and the host to synchronize and be ready to exchange information.</span></span>

<span data-ttu-id="25d23-125">Для этого мы ожидаем изменения флага событий, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="25d23-125">This is done by waiting on an event flag as follows:</span></span>

```C
/* We should wait for the host and the client to discover one another. */
status = ux_utility_event_flags_get
    (&pictbridge.ux_pictbridge_event_flags_group,
    UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY,TX_AND_CLEAR, &actual_flags,
    UX_PICTBRIDGE_EVENT_TIMEOUT);
```

<span data-ttu-id="25d23-126">Когда конечный автомат перейдет в состояние **DISCOVERY_COMPLETE** (Обнаружение завершено), сторона камеры (клиент DPS) будет собирать сведения о принтере и его возможностях.</span><span class="sxs-lookup"><span data-stu-id="25d23-126">If the state machine is in the **DISCOVERY_COMPLETE** state, the camera side (the DPS client) will gather information regarding the printer and its capabilities.</span></span>

<span data-ttu-id="25d23-127">Когда клиент DPS будет готов принять задание печати, он перейдет в состояние **UX_PICTBRIDGE_NEW_JOB_TRUE**.</span><span class="sxs-lookup"><span data-stu-id="25d23-127">If the DPS client is ready to accept a print job, its status will be set to **UX_PICTBRIDGE_NEW_JOB_TRUE**.</span></span> <span data-ttu-id="25d23-128">Это можно проверить в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="25d23-128">It can be checked below:</span></span>

```C
/* Check if the printer is ready for a print job. */
if (pictbridge.ux_pictbridge_dpsclient.ux_pictbridge_devinfo_newjobok ==
    UX_PICTBRIDGE_NEW_JOB_TRUE)

    /* We can print something … */
```

<span data-ttu-id="25d23-129">Теперь нужно заполнить дескрипторы задания печати, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="25d23-129">Next some print joib descriptors need to be filled as follows:</span></span>

```C
/* We can start a new job. Fill in the JobConfig and PrintInfo structures. */
jobinfo = &pictbridge.ux_pictbridge_jobinfo;

/* Attach a printinfo structure to the job. */
jobinfo ->ux_pictbridge_jobinfo_printinfo_start = &printinfo;

/* Set the default values for print job. */
jobinfo ->ux_pictbridge_jobinfo_quality =
    UX_PICTBRIDGE_QUALITIES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_papersize =
    UX_PICTBRIDGE_PAPER_SIZES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_papertype =
    UX_PICTBRIDGE_PAPER_TYPES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_filetype =
    UX_PICTBRIDGE_FILE_TYPES_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_dateprint =
    UX_PICTBRIDGE_DATE_PRINTS_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_filenameprint =
    UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_imageoptimize =
    UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF;
jobinfo ->ux_pictbridge_jobinfo_layout =
    UX_PICTBRIDGE_LAYOUTS_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_fixedsize =
    UX_PICTBRIDGE_FIXED_SIZE_DEFAULT;
jobinfo ->ux_pictbridge_jobinfo_cropping =
    UX_PICTBRIDGE_CROPPINGS_DEFAULT;

/* Program the callback function for reading the object data. */
jobinfo ->ux_pictbridge_jobinfo_object_data_read =
    ux_demo_object_data_copy;

/* This is a demo, the fileID is hardwired (1 and 2 for scripts, 3 for photo to be printed. */

printinfo.ux_pictbridge_printinfo_fileid =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;

ux_utility_memory_copy(printinfo.ux_pictbridge_printinfo_filename,
    "Pictbridge demo file", 20);
ux_utility_memory_copy(printinfo.ux_pictbridge_printinfo_date, "01/01/2008",
    10);

/* Fill in the object info to be printed. First get the pointer to the object container in the job info structure. */
object = (UX_SLAVE_CLASS_PIMA_OBJECT *) jobinfo ->
    ux_pictbridge_jobinfo_object;

/* Store the object format: JPEG picture. */
object ->ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_EXIF_JPEG;
object ->ux_device_class_pima_object_compressed_size = IMAGE_LEN; object ->ux_device_class_pima_object_offset = 0;
object ->ux_device_class_pima_object_handle_id =
    UX_PICTBRIDGE_OBJECT_HANDLE_PRINT;
object ->ux_device_class_pima_object_length = IMAGE_LEN;

/* File name is in Unicode. */
ux_utility_string_to_unicode("JPEG Image", object ->
    ux_device_class_pima_object_filename);

/* And start the job. */
status =ux_pictbridge_dpsclient_api_start_job(&pictbridge);
```

<span data-ttu-id="25d23-130">Теперь клиент PictBridge получил задание для печати и будет постепенно получать блоки изображений от приложения через обратный вызов, определенный в соответствующем поле.</span><span class="sxs-lookup"><span data-stu-id="25d23-130">The Pictbridge client now has a print job to do and will fetch the image blocks at a time from the application through the callback defined in the field.</span></span>

```C
jobinfo ->ux_pictbridge_jobinfo_object_data_read
```

<span data-ttu-id="25d23-131">Прототип этой функции определяется следующим образом.</span><span class="sxs-lookup"><span data-stu-id="25d23-131">The prototype of that function is defined as follows.</span></span>

## <a name="ux_pictbridge_jobinfo_object_data_read"></a><span data-ttu-id="25d23-132">ux_pictbridge_jobinfo_object_data_read</span><span class="sxs-lookup"><span data-stu-id="25d23-132">ux_pictbridge_jobinfo_object_data_read</span></span>

<span data-ttu-id="25d23-133">Копирование блока данных для печати из пользовательского пространства.</span><span class="sxs-lookup"><span data-stu-id="25d23-133">Copying a block of data from user space for printing.</span></span>

### <a name="prototype"></a><span data-ttu-id="25d23-134">Прототип</span><span class="sxs-lookup"><span data-stu-id="25d23-134">Prototype</span></span>

```C
UINT **ux_pictbridge_jobinfo_object_data_read(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length,
    ULONG *actual_length)
```

### <a name="description"></a><span data-ttu-id="25d23-135">Описание</span><span class="sxs-lookup"><span data-stu-id="25d23-135">Description</span></span>

<span data-ttu-id="25d23-136">Эта функция вызывается, когда клиенту DPS требуется получить блок данных для печати на целевом принтере PictBridge.</span><span class="sxs-lookup"><span data-stu-id="25d23-136">This function is called when the DPS client needs to retrieve a data block to print to the target Pictbridge printer.</span></span>

### <a name="parameters"></a><span data-ttu-id="25d23-137">Параметры</span><span class="sxs-lookup"><span data-stu-id="25d23-137">Parameters</span></span>

- <span data-ttu-id="25d23-138">**pictbridge** — указатель на экземпляр класса PictBridge.</span><span class="sxs-lookup"><span data-stu-id="25d23-138">**pictbridge**: Pointer to the pictbridge class instance.</span></span>
- <span data-ttu-id="25d23-139">**object_buffer** — указатель на буфер объектов.</span><span class="sxs-lookup"><span data-stu-id="25d23-139">**object_buffer**: Pointer to object buffer</span></span>
- <span data-ttu-id="25d23-140">**object_offset** — позиция для начала чтения блока данных.</span><span class="sxs-lookup"><span data-stu-id="25d23-140">**object_offset**: Where we are starting to read the data block</span></span>
- <span data-ttu-id="25d23-141">**object_length** — требуемая длина ответа.</span><span class="sxs-lookup"><span data-stu-id="25d23-141">**object_length**: Length to be returned</span></span>
- <span data-ttu-id="25d23-142">**actual_length** — длина фактически полученного ответа.</span><span class="sxs-lookup"><span data-stu-id="25d23-142">**actual_length**: Actual length returned</span></span>

### <a name="return-value"></a><span data-ttu-id="25d23-143">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="25d23-143">Return Value</span></span>

- <span data-ttu-id="25d23-144">**UX_SUCCESS** (0x00): операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="25d23-144">**UX_SUCCESS**: (0x00) This operation was successful.</span></span>
- <span data-ttu-id="25d23-145">**UX_ERROR** (0x01): приложению не удалось извлечь данные.</span><span class="sxs-lookup"><span data-stu-id="25d23-145">**UX_ERROR**: (0x01) The application could not retrieve data.</span></span>

### <a name="example"></a><span data-ttu-id="25d23-146">Например, .</span><span class="sxs-lookup"><span data-stu-id="25d23-146">Example</span></span>

```C
/* Copy the object data. */

UINT ux_demo_object_data_copy(UX_PICTBRIDGE *pictbridge,UCHAR *object_buffer,
    ULONG object_offset, ULONG object_length, ULONG *actual_length)
{
    /* Copy the demanded object data portion. */
    ux_utility_memory_copy(object_buffer, image + object_offset,
        object_length);

    /* Update the actual length. */
    *actual_length = object_length;

    /* We have copied the requested data. Return OK. */
    return(UX_SUCCESS);
}
```

## <a name="pictbridge-host-implementation"></a><span data-ttu-id="25d23-147">Реализация узла PictBridge</span><span class="sxs-lookup"><span data-stu-id="25d23-147">Pictbridge host implementation</span></span>

<span data-ttu-id="25d23-148">Реализация узла PictBridge довольно сильно отличается от реализации клиента.</span><span class="sxs-lookup"><span data-stu-id="25d23-148">The host implementation of Pictbridge is different from the client.</span></span>

<span data-ttu-id="25d23-149">Первое, что нужно сделать в среде размещения PictBridge, — зарегистрировать класс PIMA, как показано в примере ниже.</span><span class="sxs-lookup"><span data-stu-id="25d23-149">The first thing to do in a Pictbridge host environment is to register the Pima class as the example below shows:</span></span>

```C
status = ux_host_stack_class_register(ux_system_host_class_pima_name,
    ux_host_class_pima_entry);
if(status != UX_SUCCESS)
    return;
```

<span data-ttu-id="25d23-150">Этот класс реализует универсальный слой PTP, размещенный между стеком узла USB и слоем PictBridge.</span><span class="sxs-lookup"><span data-stu-id="25d23-150">This class is the generic PTP layer sitting between the USB host stack and the Pictbridge layer.</span></span>

<span data-ttu-id="25d23-151">Следующим этапом мы инициализируем значения по умолчанию для служб печати PictBridge, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="25d23-151">The next step is to initialize the Pictbridge default values for print services as follows.</span></span>

| <span data-ttu-id="25d23-152">Поле PictBridge</span><span class="sxs-lookup"><span data-stu-id="25d23-152">Pictbridge field</span></span>       | <span data-ttu-id="25d23-153">Значение</span><span class="sxs-lookup"><span data-stu-id="25d23-153">Value</span></span>                                  |
|------------------------|----------------------------------------|
| <span data-ttu-id="25d23-154">DpsVersion[0]</span><span class="sxs-lookup"><span data-stu-id="25d23-154">DpsVersion[0]</span></span>          | <span data-ttu-id="25d23-155">0x00010000</span><span class="sxs-lookup"><span data-stu-id="25d23-155">0x00010000</span></span>                             |
| <span data-ttu-id="25d23-156">DpsVersion[1]</span><span class="sxs-lookup"><span data-stu-id="25d23-156">DpsVersion[1]</span></span>          | <span data-ttu-id="25d23-157">0x00010001</span><span class="sxs-lookup"><span data-stu-id="25d23-157">0x00010001</span></span>                             |
| <span data-ttu-id="25d23-158">DpsVersion[2]</span><span class="sxs-lookup"><span data-stu-id="25d23-158">DpsVersion[2]</span></span>          | <span data-ttu-id="25d23-159">0x00000000</span><span class="sxs-lookup"><span data-stu-id="25d23-159">0x00000000</span></span>                             |
| <span data-ttu-id="25d23-160">VendorSpecificVersion</span><span class="sxs-lookup"><span data-stu-id="25d23-160">VendorSpecificVersion</span></span>  | <span data-ttu-id="25d23-161">0x00010000</span><span class="sxs-lookup"><span data-stu-id="25d23-161">0x00010000</span></span>                             |
| <span data-ttu-id="25d23-162">PrintServiceAvailable</span><span class="sxs-lookup"><span data-stu-id="25d23-162">PrintServiceAvailable</span></span>  | <span data-ttu-id="25d23-163">0x30010000</span><span class="sxs-lookup"><span data-stu-id="25d23-163">0x30010000</span></span>                             |
| <span data-ttu-id="25d23-164">Qualities[0]</span><span class="sxs-lookup"><span data-stu-id="25d23-164">Qualities[0]</span></span>           | <span data-ttu-id="25d23-165">UX_PICTBRIDGE_QUALITIES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="25d23-165">UX_PICTBRIDGE_QUALITIES_DEFAULT</span></span>        |
| <span data-ttu-id="25d23-166">Qualities[1]</span><span class="sxs-lookup"><span data-stu-id="25d23-166">Qualities[1]</span></span>           | <span data-ttu-id="25d23-167">UX_PICTBRIDGE_QUALITIES_NORMAL</span><span class="sxs-lookup"><span data-stu-id="25d23-167">UX_PICTBRIDGE_QUALITIES_NORMAL</span></span>         |
| <span data-ttu-id="25d23-168">Qualities[2]</span><span class="sxs-lookup"><span data-stu-id="25d23-168">Qualities[2]</span></span>           | <span data-ttu-id="25d23-169">UX_PICTBRIDGE_QUALITIES_DRAFT</span><span class="sxs-lookup"><span data-stu-id="25d23-169">UX_PICTBRIDGE_QUALITIES_DRAFT</span></span>          |
| <span data-ttu-id="25d23-170">Qualities[3]</span><span class="sxs-lookup"><span data-stu-id="25d23-170">Qualities[3]</span></span>           | <span data-ttu-id="25d23-171">UX_PICTBRIDGE_QUALITIES_FINE</span><span class="sxs-lookup"><span data-stu-id="25d23-171">UX_PICTBRIDGE_QUALITIES_FINE</span></span>           |
| <span data-ttu-id="25d23-172">PaperSizes[0]</span><span class="sxs-lookup"><span data-stu-id="25d23-172">PaperSizes[0]</span></span>          | <span data-ttu-id="25d23-173">UX_PICTBRIDGE_PAPER_SIZES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="25d23-173">UX_PICTBRIDGE_PAPER_SIZES_DEFAULT</span></span>      |
| <span data-ttu-id="25d23-174">PaperSizes[1]</span><span class="sxs-lookup"><span data-stu-id="25d23-174">PaperSizes[1]</span></span>          | <span data-ttu-id="25d23-175">UX_PICTBRIDGE_PAPER_SIZES_4IX6I</span><span class="sxs-lookup"><span data-stu-id="25d23-175">UX_PICTBRIDGE_PAPER_SIZES_4IX6I</span></span>        |
| <span data-ttu-id="25d23-176">PaperSizes[2]</span><span class="sxs-lookup"><span data-stu-id="25d23-176">PaperSizes[2]</span></span>          | <span data-ttu-id="25d23-177">UX_PICTBRIDGE_PAPER_SIZES_L</span><span class="sxs-lookup"><span data-stu-id="25d23-177">UX_PICTBRIDGE_PAPER_SIZES_L</span></span>            |
| <span data-ttu-id="25d23-178">PaperSizes[3]</span><span class="sxs-lookup"><span data-stu-id="25d23-178">PaperSizes[3]</span></span>          | <span data-ttu-id="25d23-179">UX_PICTBRIDGE_PAPER_SIZES_2L</span><span class="sxs-lookup"><span data-stu-id="25d23-179">UX_PICTBRIDGE_PAPER_SIZES_2L</span></span>           |
| <span data-ttu-id="25d23-180">PaperSizes[4]</span><span class="sxs-lookup"><span data-stu-id="25d23-180">PaperSizes[4]</span></span>          | <span data-ttu-id="25d23-181">UX_PICTBRIDGE_PAPER_SIZES_LETTER</span><span class="sxs-lookup"><span data-stu-id="25d23-181">UX_PICTBRIDGE_PAPER_SIZES_LETTER</span></span>       |
| <span data-ttu-id="25d23-182">PaperTypes[0]</span><span class="sxs-lookup"><span data-stu-id="25d23-182">PaperTypes[0]</span></span>          | <span data-ttu-id="25d23-183">UX_PICTBRIDGE_PAPER_TYPES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="25d23-183">UX_PICTBRIDGE_PAPER_TYPES_DEFAULT</span></span>      |
| <span data-ttu-id="25d23-184">PaperTypes[1]</span><span class="sxs-lookup"><span data-stu-id="25d23-184">PaperTypes[1]</span></span>          | <span data-ttu-id="25d23-185">UX_PICTBRIDGE_PAPER_TYPES_PLAIN</span><span class="sxs-lookup"><span data-stu-id="25d23-185">UX_PICTBRIDGE_PAPER_TYPES_PLAIN</span></span>        |
| <span data-ttu-id="25d23-186">PaperTypes[2]</span><span class="sxs-lookup"><span data-stu-id="25d23-186">PaperTypes[2]</span></span>          | <span data-ttu-id="25d23-187">UX_PICTBRIDGE_PAPER_TYPES_PHOTO</span><span class="sxs-lookup"><span data-stu-id="25d23-187">UX_PICTBRIDGE_PAPER_TYPES_PHOTO</span></span>        |
| <span data-ttu-id="25d23-188">FileTypes[0]</span><span class="sxs-lookup"><span data-stu-id="25d23-188">FileTypes[0]</span></span>           | <span data-ttu-id="25d23-189">UX_PICTBRIDGE_FILE_TYPES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="25d23-189">UX_PICTBRIDGE_FILE_TYPES_DEFAULT</span></span>       |
| <span data-ttu-id="25d23-190">FileTypes[1]</span><span class="sxs-lookup"><span data-stu-id="25d23-190">FileTypes[1]</span></span>           | <span data-ttu-id="25d23-191">UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG</span><span class="sxs-lookup"><span data-stu-id="25d23-191">UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG</span></span>     |
| <span data-ttu-id="25d23-192">FileTypes[2]</span><span class="sxs-lookup"><span data-stu-id="25d23-192">FileTypes[2]</span></span>           | <span data-ttu-id="25d23-193">UX_PICTBRIDGE_FILE_TYPES_JFIF</span><span class="sxs-lookup"><span data-stu-id="25d23-193">UX_PICTBRIDGE_FILE_TYPES_JFIF</span></span>          |
| <span data-ttu-id="25d23-194">FileTypes[3]</span><span class="sxs-lookup"><span data-stu-id="25d23-194">FileTypes[3]</span></span>           | <span data-ttu-id="25d23-195">UX_PICTBRIDGE_FILE_TYPES_DPOF</span><span class="sxs-lookup"><span data-stu-id="25d23-195">UX_PICTBRIDGE_FILE_TYPES_DPOF</span></span>          |
| <span data-ttu-id="25d23-196">DatePrints[0]</span><span class="sxs-lookup"><span data-stu-id="25d23-196">DatePrints[0]</span></span>          | <span data-ttu-id="25d23-197">UX_PICTBRIDGE_DATE_PRINTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="25d23-197">UX_PICTBRIDGE_DATE_PRINTS_DEFAULT</span></span>      |
| <span data-ttu-id="25d23-198">DatePrints[1]</span><span class="sxs-lookup"><span data-stu-id="25d23-198">DatePrints[1]</span></span>          | <span data-ttu-id="25d23-199">UX_PICTBRIDGE_DATE_PRINTS_OFF</span><span class="sxs-lookup"><span data-stu-id="25d23-199">UX_PICTBRIDGE_DATE_PRINTS_OFF</span></span>          |
| <span data-ttu-id="25d23-200">DatePrints[2]</span><span class="sxs-lookup"><span data-stu-id="25d23-200">DatePrints[2]</span></span>          | <span data-ttu-id="25d23-201">UX_PICTBRIDGE_DATE_PRINTS_ON</span><span class="sxs-lookup"><span data-stu-id="25d23-201">UX_PICTBRIDGE_DATE_PRINTS_ON</span></span>           |
| <span data-ttu-id="25d23-202">FileNamePrints[0]</span><span class="sxs-lookup"><span data-stu-id="25d23-202">FileNamePrints[0]</span></span>      | <span data-ttu-id="25d23-203">UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="25d23-203">UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT</span></span> |
| <span data-ttu-id="25d23-204">FileNamePrints[1]</span><span class="sxs-lookup"><span data-stu-id="25d23-204">FileNamePrints[1]</span></span>      | <span data-ttu-id="25d23-205">UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF</span><span class="sxs-lookup"><span data-stu-id="25d23-205">UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF</span></span>     |
| <span data-ttu-id="25d23-206">FileNamePrints[2]</span><span class="sxs-lookup"><span data-stu-id="25d23-206">FileNamePrints[2]</span></span>      | <span data-ttu-id="25d23-207">UX_PICTBRIDGE_FILE_NAME_PRINTS_ON</span><span class="sxs-lookup"><span data-stu-id="25d23-207">UX_PICTBRIDGE_FILE_NAME_PRINTS_ON</span></span>      |
| <span data-ttu-id="25d23-208">ImageOptimizes[0]</span><span class="sxs-lookup"><span data-stu-id="25d23-208">ImageOptimizes[0]</span></span>      | <span data-ttu-id="25d23-209">UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="25d23-209">UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT</span></span>  |
| <span data-ttu-id="25d23-210">ImageOptimizes[1]</span><span class="sxs-lookup"><span data-stu-id="25d23-210">ImageOptimizes[1]</span></span>      | <span data-ttu-id="25d23-211">UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF</span><span class="sxs-lookup"><span data-stu-id="25d23-211">UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF</span></span>      |
| <span data-ttu-id="25d23-212">ImageOptimizes[2]</span><span class="sxs-lookup"><span data-stu-id="25d23-212">ImageOptimizes[2]</span></span>      | <span data-ttu-id="25d23-213">UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON</span><span class="sxs-lookup"><span data-stu-id="25d23-213">UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON</span></span>       |
| <span data-ttu-id="25d23-214">Layouts[0]</span><span class="sxs-lookup"><span data-stu-id="25d23-214">Layouts[0]</span></span>             | <span data-ttu-id="25d23-215">UX_PICTBRIDGE_LAYOUTS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="25d23-215">UX_PICTBRIDGE_LAYOUTS_DEFAULT</span></span>          |
| <span data-ttu-id="25d23-216">Layouts[1]</span><span class="sxs-lookup"><span data-stu-id="25d23-216">Layouts[1]</span></span>             | <span data-ttu-id="25d23-217">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER</span><span class="sxs-lookup"><span data-stu-id="25d23-217">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER</span></span>      |
| <span data-ttu-id="25d23-218">Layouts[2]</span><span class="sxs-lookup"><span data-stu-id="25d23-218">Layouts[2]</span></span>             | <span data-ttu-id="25d23-219">UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT</span><span class="sxs-lookup"><span data-stu-id="25d23-219">UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT</span></span>      |
| <span data-ttu-id="25d23-220">Layouts[3]</span><span class="sxs-lookup"><span data-stu-id="25d23-220">Layouts[3]</span></span>             | <span data-ttu-id="25d23-221">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS</span><span class="sxs-lookup"><span data-stu-id="25d23-221">UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS</span></span>  |
| <span data-ttu-id="25d23-222">FixedSizes[0]</span><span class="sxs-lookup"><span data-stu-id="25d23-222">FixedSizes[0]</span></span>          | <span data-ttu-id="25d23-223">UX_PICTBRIDGE_FIXED_SIZE_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="25d23-223">UX_PICTBRIDGE_FIXED_SIZE_DEFAULT</span></span>       |
| <span data-ttu-id="25d23-224">FixedSizes[1]</span><span class="sxs-lookup"><span data-stu-id="25d23-224">FixedSizes[1]</span></span>          | <span data-ttu-id="25d23-225">UX_PICTBRIDGE_FIXED_SIZE_35IX5I</span><span class="sxs-lookup"><span data-stu-id="25d23-225">UX_PICTBRIDGE_FIXED_SIZE_35IX5I</span></span>        |
| <span data-ttu-id="25d23-226">FixedSizes[2]</span><span class="sxs-lookup"><span data-stu-id="25d23-226">FixedSizes[2]</span></span>          | <span data-ttu-id="25d23-227">UX_PICTBRIDGE_FIXED_SIZE_4IX6I</span><span class="sxs-lookup"><span data-stu-id="25d23-227">UX_PICTBRIDGE_FIXED_SIZE_4IX6I</span></span>         |
| <span data-ttu-id="25d23-228">FixedSizes[3]</span><span class="sxs-lookup"><span data-stu-id="25d23-228">FixedSizes[3]</span></span>          | <span data-ttu-id="25d23-229">UX_PICTBRIDGE_FIXED_SIZE_5IX7I</span><span class="sxs-lookup"><span data-stu-id="25d23-229">UX_PICTBRIDGE_FIXED_SIZE_5IX7I</span></span>         |
| <span data-ttu-id="25d23-230">FixedSizes[4]</span><span class="sxs-lookup"><span data-stu-id="25d23-230">FixedSizes[4]</span></span>          | <span data-ttu-id="25d23-231">UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM</span><span class="sxs-lookup"><span data-stu-id="25d23-231">UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM</span></span>      |
| <span data-ttu-id="25d23-232">FixedSizes[5]</span><span class="sxs-lookup"><span data-stu-id="25d23-232">FixedSizes[5]</span></span>          | <span data-ttu-id="25d23-233">UX_PICTBRIDGE_FIXED_SIZE_LETTER</span><span class="sxs-lookup"><span data-stu-id="25d23-233">UX_PICTBRIDGE_FIXED_SIZE_LETTER</span></span>        |
| <span data-ttu-id="25d23-234">FixedSizes[6]</span><span class="sxs-lookup"><span data-stu-id="25d23-234">FixedSizes[6]</span></span>          | <span data-ttu-id="25d23-235">UX_PICTBRIDGE_FIXED_SIZE_A4</span><span class="sxs-lookup"><span data-stu-id="25d23-235">UX_PICTBRIDGE_FIXED_SIZE_A4</span></span>            |
| <span data-ttu-id="25d23-236">Croppings[0]</span><span class="sxs-lookup"><span data-stu-id="25d23-236">Croppings[0]</span></span>           | <span data-ttu-id="25d23-237">UX_PICTBRIDGE_CROPPINGS_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="25d23-237">UX_PICTBRIDGE_CROPPINGS_DEFAULT</span></span>        |
| <span data-ttu-id="25d23-238">Croppings[1]</span><span class="sxs-lookup"><span data-stu-id="25d23-238">Croppings[1]</span></span>           | <span data-ttu-id="25d23-239">UX_PICTBRIDGE_CROPPINGS_OFF</span><span class="sxs-lookup"><span data-stu-id="25d23-239">UX_PICTBRIDGE_CROPPINGS_OFF</span></span>            |
| <span data-ttu-id="25d23-240">Croppings[2]</span><span class="sxs-lookup"><span data-stu-id="25d23-240">Croppings[2]</span></span>           | <span data-ttu-id="25d23-241">UX_PICTBRIDGE_CROPPINGS_ON</span><span class="sxs-lookup"><span data-stu-id="25d23-241">UX_PICTBRIDGE_CROPPINGS_ON</span></span>             |

<span data-ttu-id="25d23-242">Конечный автомат узла DPS перейдет состояние бездействия и будет ожидать новое задание для печати.</span><span class="sxs-lookup"><span data-stu-id="25d23-242">The state machine of the DPS host will be set to Idle and ready to accept a new print job.</span></span>

<span data-ttu-id="25d23-243">Теперь вы можете запустить PictBridge на стороне узла, как показано в примере ниже.</span><span class="sxs-lookup"><span data-stu-id="25d23-243">The host portion of Pictbridge can now be started as the example below shows.</span></span>

```C
/* Activate the pictbridge dpshost. */

status = ux_pictbridge_dpshost_start(&pictbridge, pima);
if (status != UX_SUCCESS)
    return;
```

<span data-ttu-id="25d23-244">Для работы узла PictBridge нужен обратный вызов, информирующий о готовности данных к печати.</span><span class="sxs-lookup"><span data-stu-id="25d23-244">The Pictbridge host function requires a callback when data is ready to be printed.</span></span> <span data-ttu-id="25d23-245">Для реализации этого в структуре узла PictBridge передается указатель функции, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="25d23-245">This is accomplished by passing a function pointer in the pictbridge host structure as follows.</span></span>

```C
/* Set a callback when an object is being received. */

pictbridge.ux_pictbridge_application_object_data_write =
    tx_demo_object_data_write;
```

<span data-ttu-id="25d23-246">Эта функция имеет следующие свойства.</span><span class="sxs-lookup"><span data-stu-id="25d23-246">This function has the following properties:</span></span>

## <a name="ux_pictbridge_application_object_data_write"></a><span data-ttu-id="25d23-247">ux_pictbridge_application_object_data_write</span><span class="sxs-lookup"><span data-stu-id="25d23-247">ux_pictbridge_application_object_data_write</span></span>

<span data-ttu-id="25d23-248">Запись блока данных для печати.</span><span class="sxs-lookup"><span data-stu-id="25d23-248">Writing a block of data for printing.</span></span>

### <a name="prototype"></a><span data-ttu-id="25d23-249">Прототип</span><span class="sxs-lookup"><span data-stu-id="25d23-249">Prototype</span></span>

```C
UINT **ux_pictbridge_application_object_data_write(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG offset,
    ULONG total_length,
    ULONG length);
```

### <a name="description"></a><span data-ttu-id="25d23-250">Описание</span><span class="sxs-lookup"><span data-stu-id="25d23-250">Description</span></span>

<span data-ttu-id="25d23-251">Эта функция вызывается, когда серверу DPS нужно получить блок данных от клиента DPS для печати на локальном принтере.</span><span class="sxs-lookup"><span data-stu-id="25d23-251">This function is called when the DPS server needs to retrieve a data block from the DPS client to print to the local printer.</span></span>

### <a name="parameters"></a><span data-ttu-id="25d23-252">Параметры</span><span class="sxs-lookup"><span data-stu-id="25d23-252">Parameters</span></span>

- <span data-ttu-id="25d23-253">**pictbridge** — указатель на экземпляр класса PictBridge.</span><span class="sxs-lookup"><span data-stu-id="25d23-253">**pictbridge**: Pointer to the pictbridge class instance.</span></span>
- <span data-ttu-id="25d23-254">**object_buffer** — указатель на буфер объектов.</span><span class="sxs-lookup"><span data-stu-id="25d23-254">**object_buffer**: Pointer to object buffer</span></span>
- <span data-ttu-id="25d23-255">**object_offset** — позиция для начала чтения блока данных.</span><span class="sxs-lookup"><span data-stu-id="25d23-255">**object_offset**: Where we are starting to read the data block</span></span>
- <span data-ttu-id="25d23-256">**total_length** — полная длина объекта.</span><span class="sxs-lookup"><span data-stu-id="25d23-256">**total_length**: Entire length of object</span></span>
- <span data-ttu-id="25d23-257">**length** — длина этого буфера.</span><span class="sxs-lookup"><span data-stu-id="25d23-257">**length**: Length of this buffer</span></span>

### <a name="return-value"></a><span data-ttu-id="25d23-258">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="25d23-258">Return Value</span></span>

- <span data-ttu-id="25d23-259">**UX_SUCCESS** (0x00): операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="25d23-259">**UX_SUCCESS**: (0x00) This operation was successful.</span></span>
- <span data-ttu-id="25d23-260">**UX_ERROR** (0x01): приложению не удалось распечатать данные.</span><span class="sxs-lookup"><span data-stu-id="25d23-260">**UX_ERROR**: (0x01) The application could not print data.</span></span>

### <a name="example"></a><span data-ttu-id="25d23-261">Пример</span><span class="sxs-lookup"><span data-stu-id="25d23-261">Example</span></span>

```C
/* Copy the object data. */

UINT tx_demo_object_data_write(UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer, ULONG offset, ULONG total_length, ULONG length);
{
    UINT status;

    /* Send the data to the local printer. */
    status = local_printer_data_send(object_buffer, length);

    /* We have printed the requested data. Return status. */
    return(status);
}
```
