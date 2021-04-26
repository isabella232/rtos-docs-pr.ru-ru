---
title: Глава 5. Драйверы ввода-вывода для ОСРВ Azure FileX
description: Разработчики могут использовать представленные в этой главе сведения о драйверах ввода-вывода для ОСРВ Azure FileX при написании драйверов для конкретных приложений.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8f2ef697f68a269b24a34147a4bc076b8a2b1660
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/07/2021
ms.locfileid: "106550088"
---
# <a name="chapter-5---io-drivers-for-azure-rtos-filex"></a><span data-ttu-id="24740-103">Глава 5. Драйверы ввода-вывода для ОСРВ Azure FileX</span><span class="sxs-lookup"><span data-stu-id="24740-103">Chapter 5 - I/O Drivers for Azure RTOS FileX</span></span>

<span data-ttu-id="24740-104">Разработчики могут использовать представленные в этой главе сведения о драйверах ввода-вывода для ОСРВ Azure FileX при написании драйверов для конкретных приложений.</span><span class="sxs-lookup"><span data-stu-id="24740-104">This chapter contains a description of I/O drivers for Azure RTOS FileX and is designed to help developers write application-specific drivers.</span></span>

## <a name="io-driver-introduction"></a><span data-ttu-id="24740-105">Основные сведения о драйверах ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="24740-105">I/O Driver Introduction</span></span>

<span data-ttu-id="24740-106">FileX поддерживает несколько носителей.</span><span class="sxs-lookup"><span data-stu-id="24740-106">FileX supports multiple media devices.</span></span> <span data-ttu-id="24740-107">Структура FX_MEDIA определяет все, что необходимо для управления носителем.</span><span class="sxs-lookup"><span data-stu-id="24740-107">The FX_MEDIA structure defines everything required to manage a media device.</span></span> <span data-ttu-id="24740-108">Эта структура содержит все сведения о носителе, включая драйвер ввода-вывода для конкретного носителя и связанные параметры для передачи информации и состояния между драйвером и FileX.</span><span class="sxs-lookup"><span data-stu-id="24740-108">This structure contains all media information, including the media-specific I/O driver and associated parameters for passing information and status between the driver and FileX.</span></span> <span data-ttu-id="24740-109">В большинстве систем имеется уникальный драйвер ввода-вывода для каждого экземпляра носителя FileX.</span><span class="sxs-lookup"><span data-stu-id="24740-109">In most systems, there is a unique I/O driver for each FileX media instance.</span></span>

## <a name="io-driver-entry"></a><span data-ttu-id="24740-110">Вход в драйвер ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="24740-110">I/O Driver Entry</span></span>

<span data-ttu-id="24740-111">Каждый драйвер ввода-вывода FileX имеет единственную функцию входа, которая определяется вызовом службы ***fx_media_open***.</span><span class="sxs-lookup"><span data-stu-id="24740-111">Each FileX I/O driver has a single entry function that is defined by the ***fx_media_open*** service call.</span></span> <span data-ttu-id="24740-112">Функция входа драйвера имеет следующий формат:</span><span class="sxs-lookup"><span data-stu-id="24740-112">The driver entry function has the following format:</span></span>

```c
void my_driver_entry(FX_MEDIA *media_ptr);
```

<span data-ttu-id="24740-113">FileX вызывает функцию входа драйвера ввода-вывода, чтобы запросить полный доступ к физическому носителю, в том числе с помощью инициализации и чтения загрузочного сектора.</span><span class="sxs-lookup"><span data-stu-id="24740-113">FileX calls the I/O driver entry function to request all physical media access, including initialization and boot sector reading.</span></span> <span data-ttu-id="24740-114">Запросы к драйверу выполняются последовательно (т. е. FileX ожидает завершения текущего запроса до отправки последующего).</span><span class="sxs-lookup"><span data-stu-id="24740-114">Requests made to the driver are done sequentially; i.e., FileX waits for the current request to complete before another request is sent.</span></span>

## <a name="io-driver-requests"></a><span data-ttu-id="24740-115">Запросы драйвера ввода-вывода</span><span class="sxs-lookup"><span data-stu-id="24740-115">I/O Driver Requests</span></span>

<span data-ttu-id="24740-116">Так как каждый драйвер ввода-вывода имеет одну функцию входа, FileX выполняет определенные запросы через блок управления носителем.</span><span class="sxs-lookup"><span data-stu-id="24740-116">Because each I/O driver has a single entry function, FileX makes specific requests through the media control block.</span></span> <span data-ttu-id="24740-117">В частности, для указания точного запроса драйвера используется элемент **fx_media_driver_request** из **FX_MEDIA**.</span><span class="sxs-lookup"><span data-stu-id="24740-117">Specifically, the  **fx_media_driver_request** member of **FX_MEDIA** is used to specify the exact driver request.</span></span> <span data-ttu-id="24740-118">Драйвер ввода-вывода сообщает об успешном или неуспешном выполнении запроса с помощью элемента **fx_media_driver_status** из **FX_MEDIA**.</span><span class="sxs-lookup"><span data-stu-id="24740-118">The I/O driver communicates the success or failure of the request through the **fx_media_driver_status** member of **FX_MEDIA**.</span></span> <span data-ttu-id="24740-119">Если запрос драйвера был успешным, **FX_SUCCESS** помещается в это поле перед возвратом драйвера.</span><span class="sxs-lookup"><span data-stu-id="24740-119">If the driver request was successful, **FX_SUCCESS** is placed in this field before the driver returns.</span></span> <span data-ttu-id="24740-120">В противном случае при обнаружении ошибки в это поле помещается FX_IO_ERROR.</span><span class="sxs-lookup"><span data-stu-id="24740-120">Otherwise, if an error is detected, FX_IO_ERROR is placed in this field.</span></span>

### <a name="driver-initialization"></a><span data-ttu-id="24740-121">Инициализация драйвера</span><span class="sxs-lookup"><span data-stu-id="24740-121">Driver Initialization</span></span>

<span data-ttu-id="24740-122">Хотя фактическая обработка инициализации драйвера зависит от приложения, обычно она состоит из инициализации структуры данных и, возможно, предварительной инициализации оборудования.</span><span class="sxs-lookup"><span data-stu-id="24740-122">Although the actual driver initialization processing is application specific, it usually consists of data structure initialization and possibly some preliminary hardware initialization.</span></span> <span data-ttu-id="24740-123">Этот запрос впервые делает FileX. Он выполняется в службе fx_media_open.</span><span class="sxs-lookup"><span data-stu-id="24740-123">This request is the first made by FileX and is done from within the fx_media_open service.</span></span>

<span data-ttu-id="24740-124">Если обнаружена защита от записи на носитель, то элементу драйвера fx_media_driver_write_protect (FX_MEDIA) следует присвоить значение FX_TRUE.</span><span class="sxs-lookup"><span data-stu-id="24740-124">If media write protection is detected, the driver fx_media_driver_write_protect member of FX_MEDIA should be set to FX_TRUE.</span></span>

<span data-ttu-id="24740-125">Для запроса инициализации драйвера ввода-вывода используются следующие элементы FX_MEDIA:</span><span class="sxs-lookup"><span data-stu-id="24740-125">The following FX_MEDIA members are used for the I/O driver initialization request:</span></span>

|<span data-ttu-id="24740-126">Элемент FX_MEDIA</span><span class="sxs-lookup"><span data-stu-id="24740-126">FX_MEDIA member</span></span>|<span data-ttu-id="24740-127">Значение</span><span class="sxs-lookup"><span data-stu-id="24740-127">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="24740-128">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="24740-128">fx_media_driver_request</span></span>|<span data-ttu-id="24740-129">FX_DRIVER_INIT</span><span class="sxs-lookup"><span data-stu-id="24740-129">FX_DRIVER_INIT</span></span>|

<span data-ttu-id="24740-130">FileX предоставляет механизм для информирования драйвера приложения о том, что секторы больше не используются.</span><span class="sxs-lookup"><span data-stu-id="24740-130">FileX provides a mechanism to inform the application driver when sectors are no longer being used.</span></span> <span data-ttu-id="24740-131">Это особенно полезно для диспетчеров FLASH-памяти, которые должны управлять всеми логическими секторами, сопоставляемыми с FLASH-памятью.</span><span class="sxs-lookup"><span data-stu-id="24740-131">This is especially useful for FLASH memory managers that must manage all in-use logical sectors mapped to the FLASH.</span></span>

<span data-ttu-id="24740-132">Если требуется такое уведомление о свободных секторах, драйвер приложения устанавливает для поля *fx_media_driver_free_sector_update* в связанной структуре **FX_MEDIA** значение **FX_TRUE**.</span><span class="sxs-lookup"><span data-stu-id="24740-132">If such notification of free sectors is required, the application driver simply sets the *fx_media_driver_free_sector_update* field in the associated **FX_MEDIA** structure to **FX_TRUE**.</span></span> <span data-ttu-id="24740-133">Если задать это поле, FileX вызовет драйвер ввода-вывода **_FX_DRIVER_RELEASE_SECTORS_**, уведомляющий об освобождении одного или нескольких последовательных секторов.</span><span class="sxs-lookup"><span data-stu-id="24740-133">After set, FileX makes a **_FX_DRIVER_RELEASE_SECTORS_** I/O driver call indicating when one or more consecutive sectors becomes free.</span></span>

### <a name="boot-sector-read"></a><span data-ttu-id="24740-134">Чтение загрузочного сектора</span><span class="sxs-lookup"><span data-stu-id="24740-134">Boot Sector Read</span></span>

<span data-ttu-id="24740-135">Вместо использования стандартного запроса на чтение FileX создает конкретный запрос на чтение загрузочного сектора носителя.</span><span class="sxs-lookup"><span data-stu-id="24740-135">Instead of using a standard read request, FileX makes a specific request to read the media's boot sector.</span></span> <span data-ttu-id="24740-136">Для запроса на чтение загрузочного сектора драйвера ввода-вывода используются следующие элементы **FX_MEDIA**:</span><span class="sxs-lookup"><span data-stu-id="24740-136">The following **FX_MEDIA** members are used for the I/O driver boot sector read request:</span></span>

|<span data-ttu-id="24740-137">Элемент FX_MEDIA</span><span class="sxs-lookup"><span data-stu-id="24740-137">FX_MEDIA member</span></span>|<span data-ttu-id="24740-138">Значение</span><span class="sxs-lookup"><span data-stu-id="24740-138">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="24740-139">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="24740-139">fx_media_driver_request</span></span>| <span data-ttu-id="24740-140">FX_DRIVER_BOOT_READ</span><span class="sxs-lookup"><span data-stu-id="24740-140">FX_DRIVER_BOOT_READ</span></span>|
|<span data-ttu-id="24740-141">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="24740-141">fx_media_driver_buffer</span></span>| <span data-ttu-id="24740-142">Адрес назначения для загрузочного сектора.</span><span class="sxs-lookup"><span data-stu-id="24740-142">Address of destination for boot sector.</span></span>|

### <a name="boot-sector-write"></a><span data-ttu-id="24740-143">Запись загрузочного сектора</span><span class="sxs-lookup"><span data-stu-id="24740-143">Boot Sector Write</span></span>

<span data-ttu-id="24740-144">Вместо использования стандартного запроса на запись FileX создает конкретный запрос на запись загрузочного сектора носителя.</span><span class="sxs-lookup"><span data-stu-id="24740-144">Instead of using a standard write request, FileX makes a specific request to write the media's boot sector.</span></span> <span data-ttu-id="24740-145">Для запроса на запись загрузочного сектора драйвера ввода-вывода используются следующие элементы **FX_MEDIA**:</span><span class="sxs-lookup"><span data-stu-id="24740-145">The following **FX_MEDIA** members are used for the I/O driver boot sector write request:</span></span>

|<span data-ttu-id="24740-146">Элемент FX_MEDIA</span><span class="sxs-lookup"><span data-stu-id="24740-146">FX_MEDIA member</span></span>|<span data-ttu-id="24740-147">Значение</span><span class="sxs-lookup"><span data-stu-id="24740-147">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="24740-148">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="24740-148">fx_media_driver_request</span></span>| <span data-ttu-id="24740-149">FX_DRIVER_BOOT_WRITE</span><span class="sxs-lookup"><span data-stu-id="24740-149">FX_DRIVER_BOOT_WRITE</span></span>|
|<span data-ttu-id="24740-150">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="24740-150">fx_media_driver_buffer</span></span>| <span data-ttu-id="24740-151">Адрес источника для загрузочного сектора.</span><span class="sxs-lookup"><span data-stu-id="24740-151">Address of source for boot sector.</span></span>|

### <a name="sector-read"></a><span data-ttu-id="24740-152">Чтение сектора</span><span class="sxs-lookup"><span data-stu-id="24740-152">Sector Read</span></span>

<span data-ttu-id="24740-153">FileX считывает один или несколько секторов в память, отправляя запрос на чтение для драйвера ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="24740-153">FileX reads one or more sectors into memory by issuing a read request to the I/O driver.</span></span> <span data-ttu-id="24740-154">Для запроса на чтение драйвера ввода-вывода используются следующие элементы **FX_MEDIA**:</span><span class="sxs-lookup"><span data-stu-id="24740-154">The following **FX_MEDIA** members are used for the I/O driver read request:</span></span>

|<span data-ttu-id="24740-155">Элемент FX_MEDIA</span><span class="sxs-lookup"><span data-stu-id="24740-155">FX_MEDIA member</span></span>|<span data-ttu-id="24740-156">Значение</span><span class="sxs-lookup"><span data-stu-id="24740-156">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="24740-157">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="24740-157">fx_media_driver_request</span></span>| <span data-ttu-id="24740-158">FX_DRIVER_READ</span><span class="sxs-lookup"><span data-stu-id="24740-158">FX_DRIVER_READ</span></span>|
|<span data-ttu-id="24740-159">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="24740-159">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="24740-160">Логический сектор для чтения</span><span class="sxs-lookup"><span data-stu-id="24740-160">Logical sector to read</span></span>|
|<span data-ttu-id="24740-161">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="24740-161">fx_media_driver_sectors</span></span>|<span data-ttu-id="24740-162">Число секторов для чтения</span><span class="sxs-lookup"><span data-stu-id="24740-162">Number of sectors to read</span></span>|
|<span data-ttu-id="24740-163">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="24740-163">fx_media_driver_buffer</span></span>|<span data-ttu-id="24740-164">Буфер назначения для чтения секторов</span><span class="sxs-lookup"><span data-stu-id="24740-164">Destination buffer for sector(s) read</span></span>|
|<span data-ttu-id="24740-165">fx_media_driver_data_sector_read</span><span class="sxs-lookup"><span data-stu-id="24740-165">fx_media_driver_data_sector_read</span></span>|<span data-ttu-id="24740-166">Задайте значение FX_TRUE, если запрашивается сектор данных файла.</span><span class="sxs-lookup"><span data-stu-id="24740-166">Set to FX_TRUE if a file data sector is requested.</span></span> <span data-ttu-id="24740-167">В противном случае, если запрашивается системный сектор (FAT или сектор каталога), укажите значение FX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="24740-167">Otherwise, FX_FALSE if a system sector (FAT or directory sector) is requested.</span></span>|
|<span data-ttu-id="24740-168">fx_media_driver_sector_type</span><span class="sxs-lookup"><span data-stu-id="24740-168">fx_media_driver_sector_type</span></span>|<span data-ttu-id="24740-169">Определяет явный тип запрашиваемого сектора, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="24740-169">Defines the explicit type of sector requested, as follows:</span></span><br /><span data-ttu-id="24740-170">FX_FAT_SECTOR (2)</span><span class="sxs-lookup"><span data-stu-id="24740-170">FX_FAT_SECTOR (2)</span></span><br /><span data-ttu-id="24740-171">FX_DIRECTORY_SECTOR (3)</span><span class="sxs-lookup"><span data-stu-id="24740-171">FX_DIRECTORY_SECTOR (3)</span></span><br /><span data-ttu-id="24740-172">FX_DATA_SECTOR (4)</span><span class="sxs-lookup"><span data-stu-id="24740-172">FX_DATA_SECTOR (4)</span></span>|

### <a name="sector-write"></a><span data-ttu-id="24740-173">Операции записи секторов</span><span class="sxs-lookup"><span data-stu-id="24740-173">Sector Write</span></span>

<span data-ttu-id="24740-174">FileX записывает один или несколько секторов на физический носитель, отправляя запрос на запись в драйвер ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="24740-174">FileX writes one or more sectors to the physical media by issuing a write request to the I/O driver.</span></span> <span data-ttu-id="24740-175">Для запроса на запись драйвера ввода-вывода используются следующие элементы FX_MEDIA:</span><span class="sxs-lookup"><span data-stu-id="24740-175">The following FX_MEDIA members are used for the I/O driver write request:</span></span>

|<span data-ttu-id="24740-176">Элемент FX_MEDIA</span><span class="sxs-lookup"><span data-stu-id="24740-176">FX_MEDIA member</span></span>| <span data-ttu-id="24740-177">Значение</span><span class="sxs-lookup"><span data-stu-id="24740-177">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="24740-178">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="24740-178">fx_media_driver_request</span></span>|<span data-ttu-id="24740-179">FX_DRIVER_WRITE</span><span class="sxs-lookup"><span data-stu-id="24740-179">FX_DRIVER_WRITE</span></span>|
|<span data-ttu-id="24740-180">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="24740-180">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="24740-181">Логический сектор для записи</span><span class="sxs-lookup"><span data-stu-id="24740-181">Logical sector to write</span></span>|
|<span data-ttu-id="24740-182">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="24740-182">fx_media_driver_sectors</span></span>|<span data-ttu-id="24740-183">Число секторов для записи</span><span class="sxs-lookup"><span data-stu-id="24740-183">Number of sectors to write</span></span>|
|<span data-ttu-id="24740-184">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="24740-184">fx_media_driver_buffer</span></span>|<span data-ttu-id="24740-185">Исходный буфер для записи секторов</span><span class="sxs-lookup"><span data-stu-id="24740-185">Source buffer for sector(s) to write</span></span>|
|<span data-ttu-id="24740-186">fx_media_driver_system_write</span><span class="sxs-lookup"><span data-stu-id="24740-186">fx_media_driver_system_write</span></span>| <span data-ttu-id="24740-187">Задайте значение FX_TRUE, если запрашивается системный сектор (FAT или сектор каталога).</span><span class="sxs-lookup"><span data-stu-id="24740-187">Set to FX_TRUE if a system sector is requested (FAT or directory sector).</span></span> <span data-ttu-id="24740-188">В противном случае, если запрашивается сектор данных файла, укажите значение FX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="24740-188">Otherwise, FX_FALSE if a file data sector is requested.</span></span>|
|<span data-ttu-id="24740-189">fx_media_driver_sector_type</span><span class="sxs-lookup"><span data-stu-id="24740-189">fx_media_driver_sector_type</span></span>|<span data-ttu-id="24740-190">Определяет явный тип запрашиваемого сектора, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="24740-190">Defines the explicit type of sector requested, as follows:</span></span><br> <br><span data-ttu-id="24740-191">FX_FAT_SECTOR (2)</span><span class="sxs-lookup"><span data-stu-id="24740-191">FX_FAT_SECTOR (2)</span></span> <br> <span data-ttu-id="24740-192">FX_DIRECTORY_SECTOR (3)</span><span class="sxs-lookup"><span data-stu-id="24740-192">FX_DIRECTORY_SECTOR (3)</span></span> <br><span data-ttu-id="24740-193">FX_DATA_SECTOR (4).</span><span class="sxs-lookup"><span data-stu-id="24740-193">FX_DATA_SECTOR (4).</span></span>|

### <a name="driver-flush"></a><span data-ttu-id="24740-194">Очистка драйвера</span><span class="sxs-lookup"><span data-stu-id="24740-194">Driver Flush</span></span>

<span data-ttu-id="24740-195">FileX записывает все секторы, находящиеся в кэше секторов драйвера, на физический носитель, отправляя запрос на очистку к драйверу ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="24740-195">FileX flushes all sectors currently in the driver's sector cache to the physical media by issuing a flush request to the I/O driver.</span></span> <span data-ttu-id="24740-196">Конечно, если драйвер не кэширует секторы, этот запрос не требует обработки драйвера.</span><span class="sxs-lookup"><span data-stu-id="24740-196">Of course, if the driver is not caching sectors, this request requires no driver processing.</span></span> <span data-ttu-id="24740-197">Для запроса на очистку драйвера ввода-вывода используются следующие элементы FX_MEDIA:</span><span class="sxs-lookup"><span data-stu-id="24740-197">The following FX_MEDIA members are used for the I/O driver flush request:</span></span>

|<span data-ttu-id="24740-198">Элемент FX_MEDIA</span><span class="sxs-lookup"><span data-stu-id="24740-198">FX_MEDIA member</span></span>| <span data-ttu-id="24740-199">Значение</span><span class="sxs-lookup"><span data-stu-id="24740-199">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="24740-200">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="24740-200">fx_media_driver_request</span></span>|<span data-ttu-id="24740-201">FX_DRIVER_FLUSH</span><span class="sxs-lookup"><span data-stu-id="24740-201">FX_DRIVER_FLUSH</span></span>|

### <a name="driver-abort"></a><span data-ttu-id="24740-202">Прекращение работы драйвера</span><span class="sxs-lookup"><span data-stu-id="24740-202">Driver Abort</span></span>

<span data-ttu-id="24740-203">FileX информирует драйвер о необходимости прервать все дальнейшие физические операции ввода-вывода с физическим носителем, выполнив запрос прерывания для драйвера ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="24740-203">FileX informs the driver to abort all further physical I/O activity with the physical media by issuing an abort request to the I/O driver.</span></span> <span data-ttu-id="24740-204">Драйвер не должен повторно выполнять операции ввода-вывода, пока он не будет инициализирован повторно.</span><span class="sxs-lookup"><span data-stu-id="24740-204">The driver should not perform any I/O again until it is re-initialized.</span></span> <span data-ttu-id="24740-205">Для запроса на прерывание драйвера ввода-вывода используются следующие элементы FX_MEDIA:</span><span class="sxs-lookup"><span data-stu-id="24740-205">The following FX_MEDIA members are used for the I/O driver abort request:</span></span>

|<span data-ttu-id="24740-206">Элемент FX_MEDIA</span><span class="sxs-lookup"><span data-stu-id="24740-206">FX_MEDIA member</span></span>| <span data-ttu-id="24740-207">Значение</span><span class="sxs-lookup"><span data-stu-id="24740-207">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="24740-208">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="24740-208">fx_media_driver_request</span></span>| <span data-ttu-id="24740-209">FX_DRIVER_ABORT</span><span class="sxs-lookup"><span data-stu-id="24740-209">FX_DRIVER_ABORT</span></span>|

### <a name="release-sectors"></a><span data-ttu-id="24740-210">Освобождение секторов</span><span class="sxs-lookup"><span data-stu-id="24740-210">Release Sectors</span></span>

<span data-ttu-id="24740-211">Если в ходе инициализации ранее был выбран драйвер, FileX информирует его о том, что один или несколько последовательных секторов освобождены.</span><span class="sxs-lookup"><span data-stu-id="24740-211">If previously selected by the driver during initialization, FileX informs the driver whenever one or more consecutive sectors become free.</span></span> <span data-ttu-id="24740-212">Если драйвер на самом деле является диспетчером FLASH-памяти, эти сведения можно использовать, чтобы сообщить диспетчеру, что эти сектора больше не нужны.</span><span class="sxs-lookup"><span data-stu-id="24740-212">If the driver is actually a FLASH manager, this information can be used to tell the FLASH manager that these sectors are no longer needed.</span></span> <span data-ttu-id="24740-213">Для запроса на освобождение драйвера ввода-вывода используются следующие элементы **FX_MEDIA**:</span><span class="sxs-lookup"><span data-stu-id="24740-213">The following **FX_MEDIA** members are used for the I/O release sectors request:</span></span>

|<span data-ttu-id="24740-214">Элемент FX_MEDIA</span><span class="sxs-lookup"><span data-stu-id="24740-214">FX_MEDIA member</span></span>| <span data-ttu-id="24740-215">Значение</span><span class="sxs-lookup"><span data-stu-id="24740-215">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="24740-216">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="24740-216">fx_media_driver_request</span></span>|<span data-ttu-id="24740-217">FX_DRIVER_RELEASE_SECTORS</span><span class="sxs-lookup"><span data-stu-id="24740-217">FX_DRIVER_RELEASE_SECTORS</span></span>|
|<span data-ttu-id="24740-218">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="24740-218">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="24740-219">Начало свободного сектора</span><span class="sxs-lookup"><span data-stu-id="24740-219">Start of free sector</span></span>|
|<span data-ttu-id="24740-220">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="24740-220">fx_media_driver_sectors</span></span>|<span data-ttu-id="24740-221">Количество свободных секторов</span><span class="sxs-lookup"><span data-stu-id="24740-221">Number of free sectors</span></span>|

### <a name="driver-suspension"></a><span data-ttu-id="24740-222">Приостановка драйвера</span><span class="sxs-lookup"><span data-stu-id="24740-222">Driver Suspension</span></span>

<span data-ttu-id="24740-223">Поскольку выполнение операций ввода-вывода на физических носителях может занять некоторое время, иногда желательно приостанавливать вызывающий поток.</span><span class="sxs-lookup"><span data-stu-id="24740-223">Because I/O with physical media may take some time, suspending the calling thread is often desirable.</span></span> <span data-ttu-id="24740-224">Предполагается, что выполнение базовой операции ввода-вывода прерывается.</span><span class="sxs-lookup"><span data-stu-id="24740-224">Of course, this assumes completion of the underlying I/O operation is interrupt driven.</span></span> <span data-ttu-id="24740-225">В этом случае приостановка потока легко реализуется с помощью семафора ThreadX.</span><span class="sxs-lookup"><span data-stu-id="24740-225">If so, thread suspension is easily implemented with a ThreadX semaphore.</span></span> <span data-ttu-id="24740-226">После запуска операции ввода или вывода драйвер ввода-вывода приостанавливает действие с помощью собственного внутреннего семафора ввода-вывода (создается с начальным числом, равным нулю, во время инициализации драйвера).</span><span class="sxs-lookup"><span data-stu-id="24740-226">After starting the input or output operation, the I/O driver suspends on its own internal I/O semaphore (created with an initial count of zero during driver initialization).</span></span> <span data-ttu-id="24740-227">В рамках обработки прерываний ввода-вывода драйвера устанавливается один и тот же семафор ввода-вывода, который, в свою очередь, пробуждает приостановленный поток.</span><span class="sxs-lookup"><span data-stu-id="24740-227">As part of the driver I/O completion interrupt processing, the same I/O semaphore is set, which in turn wakes up the suspended thread.</span></span>

### <a name="sector-translation"></a><span data-ttu-id="24740-228">Преобразование секторов</span><span class="sxs-lookup"><span data-stu-id="24740-228">Sector Translation</span></span>

<span data-ttu-id="24740-229">Так как FileX просматривает носитель в виде линейных логических секторов, запросы ввода-вывода к драйверу ввода-вывода создаются с помощью логических секторов.</span><span class="sxs-lookup"><span data-stu-id="24740-229">Because FileX views the media as linear logical sectors, I/O requests made to the I/O driver are made with logical sectors.</span></span> <span data-ttu-id="24740-230">Драйвер отвечает за преобразование между логическими секторами и физической геометрией носителя, которая может включать в себя головки, дорожки и физические секторы.</span><span class="sxs-lookup"><span data-stu-id="24740-230">It is the driver's responsibility to translate between logical sectors and the physical geometry of the media, which may include heads, tracks, and physical sectors.</span></span> <span data-ttu-id="24740-231">Для дисковых носителей FLASH и ОЗУ логические секторы обычно сопоставляют каталог с физическими секторами.</span><span class="sxs-lookup"><span data-stu-id="24740-231">For FLASH and RAM disk media, the logical sectors typically map directory to physical sectors.</span></span> <span data-ttu-id="24740-232">Ниже приведены типичные формулы для сопоставления логических и физических секторов в драйвере ввода-вывода.</span><span class="sxs-lookup"><span data-stu-id="24740-232">In any case, here are the typical formulas to perform the logical to physical sector mapping in the I/O driver:</span></span>

```c
media_ptr -> fx_media_driver_physical_sector =
    (media_ptr -> fx_media_driver_logical_sector % media_ptr -> fx_media_sectors_per_track) + 1;

media_ptr -> fx_media_driver_physical_head =
    (media_ptr -> fx_media_driver_logical_sector/ media_ptr ->
    fx_media_sectors_per_track) % media_ptr -> fx_media_heads;

media_ptr -> fx_media_driver_physical_track =(media_ptr ->
    fx_media_driver_logical_sector/ (media_ptr -> fx_media_sectors_per_track *
    media_ptr -> fx_media_heads)));
```

<span data-ttu-id="24740-233">Обратите внимание, что физические секторы начинаются с единицы, а логические — с нуля.</span><span class="sxs-lookup"><span data-stu-id="24740-233">Note that physical sectors start at one, while logical sectors start at zero.</span></span>

### <a name="hidden-sectors"></a><span data-ttu-id="24740-234">Скрытые секторы</span><span class="sxs-lookup"><span data-stu-id="24740-234">Hidden Sectors</span></span>

<span data-ttu-id="24740-235">Скрытые секторы размещаются перед загрузочной записью на носителе.</span><span class="sxs-lookup"><span data-stu-id="24740-235">Hidden sectors resided prior to the boot record on the media.</span></span> <span data-ttu-id="24740-236">Так как они действительно выходят за рамки структуры файловой системы FAT, их необходимо включить в каждую операцию логического сектора, которую выполняет драйвер.</span><span class="sxs-lookup"><span data-stu-id="24740-236">Because they are really outside the scope of the FAT file system layout, they must be accounted for in each logical sector operation the driver does.</span></span>

### <a name="media-write-protect"></a><span data-ttu-id="24740-237">Защита от записи на носитель</span><span class="sxs-lookup"><span data-stu-id="24740-237">Media Write Protect</span></span>

<span data-ttu-id="24740-238">Драйвер FileX может включить защиту от записи, задавая поле fx_media_driver_write_protect в блоке управления носителем.</span><span class="sxs-lookup"><span data-stu-id="24740-238">The FileX driver can turn on write protect by setting the fx_media_driver_write_protect field in the media control block.</span></span> <span data-ttu-id="24740-239">Это приведет к ошибке, которая будет возвращена, если при попытке записи на носитель выполняются какие либо вызовы FileX.</span><span class="sxs-lookup"><span data-stu-id="24740-239">This will cause an error to be returned if any FileX calls are made in an attempt to write to the media.</span></span>

## <a name="sample-ram-driver"></a><span data-ttu-id="24740-240">Пример драйвера ОЗУ</span><span class="sxs-lookup"><span data-stu-id="24740-240">Sample RAM Driver</span></span>

<span data-ttu-id="24740-241">Демонстрационная система FileX поставляется с драйвером для небольшого диска ОЗУ, который определен в файле fx_ram_driver.c.</span><span class="sxs-lookup"><span data-stu-id="24740-241">The FileX demonstration system is delivered with a small RAM disk driver, which is defined in the file fx_ram_driver.c.</span></span> <span data-ttu-id="24740-242">Драйвер предполагает наличие дискового пространства объемом 32 КБ и создает загрузочную запись для 256 128-байтовых секторов.</span><span class="sxs-lookup"><span data-stu-id="24740-242">The driver assumes a 32K memory space and creates a boot record for 256 128-byte sectors.</span></span> <span data-ttu-id="24740-243">В этом файле представлен хороший пример реализации драйверов ввода-вывода FileX для конкретного приложения.</span><span class="sxs-lookup"><span data-stu-id="24740-243">This file provides a good example of how to implement application specific FileX I/O drivers.</span></span>

```c
/*FUNCTION: _fx_ram_driver
RELEASE: PORTABLE C 5.7
AUTHOR: William E. Lamie, Microsoft, Inc.
DESCRIPTION: This function is the entry point to the generic
    RAM disk driver that is delivered with all versions of FileX.
    The format of the RAM disk is easily modified by calling fx_media_format prior to opening the media.

    This driver also serves as a template for developing FileX drivers
    for actual devices. Simply replace the read/write sector logic
    with calls to read/write from the appropriate physical device.

FileX RAM/FLASH structures look like the following:
Physical Sector             Contents
    0                         Boot record
    1                         FAT Area Start
    +FAT Sectors             Root Directory Start
    +Directory Sectors         Data Sector Start

INPUT: media_ptr Media control block pointer
OUTPUT: None
CALLS:     _fx_utility_memory_copy Copy sector memory
        _fx_utility_16_unsigned_read Read 16-bit unsigned
CALLED BY: FileX System Functions
RELEASE HISTORY:

    DATE         NAME         DESCRIPTION
    12-12-2005     William E.     Lamie Initial Version 5.0
    07-18-2007     William E.     Lamie Modified comment(s),
                                resulting in version 5.1
    03-01-2009     William E.     Lamie Modified comment(s),
                                resulting in version 5.2
    11-01-2015     William E.     Lamie Modified comment(s),
                                resulting in version 5.3
    04-15-2016     William E.     Lamie Modified comment(s),
                                resulting in version 5.4
    04-03-2017     William E.     Lamie Modified comment(s),
                                fixed compiler warnings,
                                resulting in version 5.5
    12-01-2018     William E.     Lamie Modified comment(s),
                                checked buffer overflow,
                                resulting in version 5.6
    08-15-2019     William E.     Lamie Modified comment(s),
                                resulting in version 5.7
*/

VOID _fx_ram_driver(FX_MEDIA *media_ptr) { UCHAR *source_buffer;
                                           UCHAR *destination_buffer;
                                           UINT bytes_per_sector;

    /* There are several useful/important pieces of information contained
        in the media structure, some of which are supplied by FileX and
        others are for the driver to setup. The following
        is a summary of the necessary FX_MEDIA structure members:
    FX_MEDIA Member                     Meaning

    fx_media_driver_request             FileX request type.
        Valid requests from FileX are as follows:
        FX_DRIVER_READ
        FX_DRIVER_WRITE
        FX_DRIVER_FLUSH
        FX_DRIVER_ABORT
        FX_DRIVER_INIT
        FX_DRIVER_BOOT_READ
        FX_DRIVER_RELEASE_SECTORS
        FX_DRIVER_BOOT_WRITE FX_DRIVER_UNINIT

    fx_media_driver_status              This value is RETURNED by the driver.
        If the operation is successful, this field should be set to FX_SUCCESS
        for before returning. Otherwise, if an error occurred, this field should be set to FX_IO_ERROR.

    fx_media_driver_buffer              Pointer to buffer to read or write sector data. This is supplied by FileX.

    fx_media_driver_logical_sector      Logical sector FileX is requesting.
    fx_media_driver_sectors             Number of sectors FileX is requesting.

    The following is a summary of the optional FX_MEDIA structure members: FX_MEDIA Member Meaning

    fx_media_driver_info                Pointer to any additional information or memory.
        This is optional for the driver use and is setup from the fx_media_open call.
        The RAM disk uses this pointer for the RAM disk memory itself.

    fx_media_driver_write_protect       The DRIVER sets this to FX_TRUE when media is write protected.
        This is typically done in initialization, but can be done anytime.

    fx_media_driver_free_sector_update  The DRIVER sets this to FX_TRUE when it needs
        to know when clusters are released. This is important for FLASH wear-leveling drivers.

    fx_media_driver_system_write        FileX sets this flag to FX_TRUE if the sector
        being written is a system sector, e.g., a boot, FAT, or directory sector.
        The driver may choose to use this to initiate error recovery logic for greater fault
        tolerance. fx_media_driver_data_sector_read FileX sets this flag to FX_TRUE
        if the sector(s) being read are file data sectors, i.e., NOT system sectors.

    fx_media_driver_sector_type         FileX sets this variable to the specific type of
        sector being read or written. The following sector types are identified:
            FX_UNKNOWN_SECTOR
            FX_BOOT_SECTOR
            FX_FAT_SECTOR
            FX_DIRECTORY_SECTOR
            FX_DATA_SECTOR */

    /* Process the driver request specified in the media control block. */

    switch (media_ptr -> fx_media_driver_request){

        case FX_DRIVER_READ: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
            is pointed to by the fx_media_driver_info pointer, which is supplied
            by the application in the call to fx_media_open. */

            source_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the RAM sector into the destination. */

             _fx_utility_memory_copy(source_buffer,
                media_ptr -> fx_media_driver_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_WRITE: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
                is pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */

            destination_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the source to the RAM sector. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_FLUSH: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_ABORT: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_INIT: {

            /* FLASH drivers are responsible for setting several fields
                in the media structure, as follows:
                media_ptr -> fx_media_driver_free_sector_update media_ptr ->
                fx_media_driver_write_protect
                The fx_media_driver_free_sector_update flag is used to instruct
                FileX to inform the driver whenever sectors are not being used.
                This is especially useful for FLASH managers so they don't have
                maintain mapping for sectors no longer in use.
                The fx_media_driver_write_protect flag can be set anytime by
                the driver to indicate the media is not writable. Write attempts
                made when this flag is set are returned as errors. */
            /* Perform basic initialization here... since the boot record is going
                to be read subsequently and again for volume name requests. */
            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

         case FX_DRIVER_UNINIT: {

            /* There is nothing to do in this case for the RAM driver.
                For actual devices some shutdown processing may be necessary. */

            /* Successful driver request. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_READ: {
            /* Read the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is pointed
                to by the fx_media_driver_info pointer, which is supplied by the
                application in the call to fx_media_open. */

            source_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* For RAM driver, determine if the boot record is valid. */

            if ((source_buffer[0] != (UCHAR)0xEB) ||

            ((source_buffer[1] != (UCHAR)0x34) &&

            (source_buffer[1] != (UCHAR)0x76)) || /* exFAT jump code. */

            (source_buffer[2] != (UCHAR)0x90)) {

            /* Invalid boot record, return an error! */
            media_ptr -> fx_media_driver_status = FX_MEDIA_INVALID; return; }

            /* For RAM disk only, pickup the bytes per sector. */

            bytes_per_sector =
                _fx_utility_16_unsigned_read(&source_buffer[FX_BYTES_SECTOR]); #ifdef FX_ENABLE_EXFAT

            /* if byte per sector is zero, then treat it as exFAT volume. */

            if (bytes_per_sector == 0 && (source_buffer[1] == (UCHAR)0x76)) {

            /* Pickup the byte per sector shift, and calculate byte per sector. */ 
            bytes_per_sector = (UINT)(1 << source_buffer[FX_EF_BYTE_PER_SECTOR_SHIFT]);

            }

            #endif /* FX_ENABLE_EXFAT */

            /* Ensure this is less than the media memory size. */
            if (bytes_per_sector \media_ptr -> fx_media_memory_size) {

            media_ptr -> fx_media_driver_status = FX_BUFFER_ERROR; break; }

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(source_buffer, media_ptr -> fx_media_driver_buffer, bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_WRITE: {

            /* Write the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is
                pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */ 
            destination_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        default: {
            /* Invalid driver request. */
            media_ptr -> fx_media_driver_status = FX_IO_ERROR; break;}
    }
}
```
