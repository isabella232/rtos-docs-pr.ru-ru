---
title: Глава 5. Сведения о классах устройств USBX
description: Сведения о классах устройств USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 84f215ad990a2fe185a08f3876276528787ef8bc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815080"
---
# <a name="chapter-5---usbx-device-class-considerations"></a><span data-ttu-id="456ca-103">Глава 5. Сведения о классах устройств USBX</span><span class="sxs-lookup"><span data-stu-id="456ca-103">Chapter 5 - USBX Device Class Considerations</span></span>

## <a name="device-class-registration"></a><span data-ttu-id="456ca-104">Регистрация класса устройства</span><span class="sxs-lookup"><span data-stu-id="456ca-104">Device Class registration</span></span>

<span data-ttu-id="456ca-105">Принцип регистрации каждого класса устройства один и тот же.</span><span class="sxs-lookup"><span data-stu-id="456ca-105">Each device class follows the same principle for registration.</span></span> <span data-ttu-id="456ca-106">Структура, содержащая параметры конкретного класса, передается функции инициализации класса.</span><span class="sxs-lookup"><span data-stu-id="456ca-106">A structure containing specific class parameters is passed to the class initialize function.</span></span>

```c
/* Set the parameters for callback when insertion/extraction of a HID device. */

hid_parameter.ux_slave_class_hid_instance_activate = tx_demo_hid_instance_activate;

hid_parameter.ux_slave_class_hid_instance_deactivate = tx_demo_hid_instance_deactivate;

/* Initialize the hid class parameters for the device. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_device_report;

hid_parameter.ux_device_class_hid_parameter_report_length = HID_DEVICE_REPORT_LENGTH;

hid_parameter.ux_device_class_hid_parameter_report_id = UX_TRUE;
hid_parameter.ux_device_class_hid_parameter_callback = demo_thread_hid_callback;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry,1,0, (VOID *)&hid_parameter);
```

<span data-ttu-id="456ca-107">Каждый класс может зарегистрировать (при необходимости) функцию обратного вызова при активации экземпляра класса.</span><span class="sxs-lookup"><span data-stu-id="456ca-107">Each class can register, optionally, a callback function when a instance of the class gets activated.</span></span> <span data-ttu-id="456ca-108">Затем обратный вызов вызывается стеком устройств для информирования приложения о том, что был создан экземпляр.</span><span class="sxs-lookup"><span data-stu-id="456ca-108">The callback is then called by the device stack to inform the application that an instance was created.</span></span>

<span data-ttu-id="456ca-109">Приложение будет иметь в своем теле две функции для активации и отключения, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="456ca-109">The application would have in its body the 2 functions for activation and deactivation, as shown in the following example.</span></span>

```c
VOID tx_demo_hid_instance_activate(VOID *hid_instance)
{
    /* Save the HID instance. */
    hid_slave = (UX_SLAVE_CLASS_HID *) hid_instance;
}

VOID tx_demo_hid_instance_deactivate(VOID *hid_instance)
{
    /* Reset the HID instance. */
    hid_slave = UX_NULL;
}
```

<span data-ttu-id="456ca-110">Не рекомендуется выполнять какие-либо действия в этих функциях, кроме запоминания экземпляра класса и его синхронизации с остальной частью приложения.</span><span class="sxs-lookup"><span data-stu-id="456ca-110">It is not recommended to do anything within these functions but to memorize the instance of the class and synchronize with the rest of the application.</span></span>

## <a name="usb-device-storage-class"></a><span data-ttu-id="456ca-111">Класс хранения USB-устройства</span><span class="sxs-lookup"><span data-stu-id="456ca-111">USB Device Storage Class</span></span>

<span data-ttu-id="456ca-112">Класс хранения USB-устройства позволяет сделать запоминающее устройство, внедренное в систему, видимым для USB-хоста.</span><span class="sxs-lookup"><span data-stu-id="456ca-112">The USB device storage class allows for a storage device embedded in the system to be made visible to a USB host.</span></span>

<span data-ttu-id="456ca-113">Класс хранения USB-устройства сам по себе не предоставляет решение для хранения данных.</span><span class="sxs-lookup"><span data-stu-id="456ca-113">The USB device storage class does not by itself provide a storage solution.</span></span> <span data-ttu-id="456ca-114">Он просто принимает и интерпретирует запросы SCSI, поступающие от узла.</span><span class="sxs-lookup"><span data-stu-id="456ca-114">It merely accepts and interprets SCSI requests coming from the host.</span></span> <span data-ttu-id="456ca-115">Если один из этих запросов является командой на чтение или запись, он вызывает предварительно заданный обратный вызов к реальному обработчику запоминающего устройства, например драйверу устройства ATA или драйверу устройства флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="456ca-115">When one of these requests is a read or a write command, it will invoke a pre-defined call back to a real storage device handler, such as an ATA device driver or a Flash device driver.</span></span>

<span data-ttu-id="456ca-116">При инициализации класса хранения устройства классу, который содержит всю необходимую информацию, присваивается структура указателя.</span><span class="sxs-lookup"><span data-stu-id="456ca-116">When initializing the device storage class, a pointer structure is given to the class that contains all the information necessary.</span></span> <span data-ttu-id="456ca-117">Ниже приведен пример кода.</span><span class="sxs-lookup"><span data-stu-id="456ca-117">An example is given below.</span></span>

```c
/* Initialize the storage class parameters to customize vendor strings. */

storage_parameter.ux_slave_class_storage_parameter_vendor_id
    = demo_ux_system_slave_class_storage_vendor_id;

storage_parameter.ux_slave_class_storage_parameter_product_id
    = demo_ux_system_slave_class_storage_product_id;

storage_parameter.ux_slave_class_storage_parameter_product_rev
    = demo_ux_system_slave_class_storage_product_rev;

storage_parameter.ux_slave_class_storage_parameter_product_serial
    = demo_ux_system_slave_class_storage_product_serial;

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read_only_flag
    = UX_FALSE;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read
    = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write
    = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status
    = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,
    ux_device_class_storage_entry, ux_device_class_storage_thread, 0, (VOID *)&storage_parameter);
```

<span data-ttu-id="456ca-118">В этом примере строки хранилища драйвера настраиваются путем присвоения указателей строк соответствующему параметру.</span><span class="sxs-lookup"><span data-stu-id="456ca-118">In this example, the driver storage strings are customized by assigning string pointers to corresponding parameter.</span></span> <span data-ttu-id="456ca-119">Если какой-либо из указателей остается UX_NULL, используется строка ОСРВ Azure по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="456ca-119">If any one of the string pointer is left to UX_NULL, the default Azure RTOS string is used.</span></span>

<span data-ttu-id="456ca-120">В этом примере адрес последнего блока диска или LBA указывается как размер логического сектора.</span><span class="sxs-lookup"><span data-stu-id="456ca-120">In this example, the drive's last block address or LBA is given as well as the logical sector size.</span></span> <span data-ttu-id="456ca-121">LBA — это количество секторов, доступных на носителе (1).</span><span class="sxs-lookup"><span data-stu-id="456ca-121">The LBA is the number of sectors available in the media –1.</span></span> <span data-ttu-id="456ca-122">На обычном носителе данных длина блока составляет 512.</span><span class="sxs-lookup"><span data-stu-id="456ca-122">The block length is set to 512 in regular storage media.</span></span> <span data-ttu-id="456ca-123">Для дисководов оптических дисков можно задать значение 2048.</span><span class="sxs-lookup"><span data-stu-id="456ca-123">It can be set to 2048 for optical drives.</span></span>

<span data-ttu-id="456ca-124">Приложению необходимо передать три указателя на функцию обратного вызова, чтобы класс хранения считывал, записывал и получал сведения о состоянии носителя.</span><span class="sxs-lookup"><span data-stu-id="456ca-124">The application needs to pass three callback function pointers to allow the storage class to read, write and obtain status for the media.</span></span>

<span data-ttu-id="456ca-125">Прототипы для функций чтения и записи показаны в примере ниже.</span><span class="sxs-lookup"><span data-stu-id="456ca-125">The prototypes for the read and write functions are shown in the example below.</span></span>

```c
UINT media_read( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);

UINT media_write( 
    VOID *storage,  
    ULONG lun,  
    UCHAR *data_pointer,
    ULONG number_blocks,  
    ULONG lba,  
    ULONG *media_status);
```

<span data-ttu-id="456ca-126">Где:</span><span class="sxs-lookup"><span data-stu-id="456ca-126">Where:</span></span>

- <span data-ttu-id="456ca-127">*storage* — экземпляр класса хранения.</span><span class="sxs-lookup"><span data-stu-id="456ca-127">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="456ca-128">*lun* — логический номер устройства (LUN), на который отправляется команда.</span><span class="sxs-lookup"><span data-stu-id="456ca-128">*lun* is the LUN the command is directed to.</span></span>
- <span data-ttu-id="456ca-129">*data_pointer* — адрес буфера, используемого для чтения или записи.</span><span class="sxs-lookup"><span data-stu-id="456ca-129">*data_pointer* is the address of the buffer to be used for reading or writing.</span></span>
- <span data-ttu-id="456ca-130">*number_blocks* — количество секторов для чтения и записи.</span><span class="sxs-lookup"><span data-stu-id="456ca-130">*number_blocks* is the number of sectors to read/write.</span></span>
- <span data-ttu-id="456ca-131">*lba* — адрес сектора для чтения.</span><span class="sxs-lookup"><span data-stu-id="456ca-131">*lba* is the sector address to read.</span></span>
- <span data-ttu-id="456ca-132">*media_status* должен полностью совпадать с возвращаемым значением обратного вызова состояния носителя.</span><span class="sxs-lookup"><span data-stu-id="456ca-132">*media_status* should be filled out exactly like the media status callback return value.</span></span>

<span data-ttu-id="456ca-133">Возвращаемое значение может быть либо UX_SUCCESS, либо UX_ERROR, указывающие на успешную или неудачную операцию.</span><span class="sxs-lookup"><span data-stu-id="456ca-133">The return value can have either the value UX_SUCCESS or UX_ERROR indicating a successful or unsuccessful operation.</span></span> <span data-ttu-id="456ca-134">Этим операциям не требуется возвращать другие коды ошибок.</span><span class="sxs-lookup"><span data-stu-id="456ca-134">These operations do not need to return any other error codes.</span></span> <span data-ttu-id="456ca-135">Если при выполнении какой-либо операции возникает ошибка, класс хранения вызовет функцию обратного вызова состояния.</span><span class="sxs-lookup"><span data-stu-id="456ca-135">If there is an error in any operation, the storage class will invoke the status call back function.</span></span>

<span data-ttu-id="456ca-136">Эта функция имеет следующий прототип.</span><span class="sxs-lookup"><span data-stu-id="456ca-136">This function has the following prototype.</span></span>

```c
ULONG media_status( 
    VOID *storage,  
    ULONG lun,  
    ULONG media_id,  
    ULONG *media_status);
```

<span data-ttu-id="456ca-137">Параметр вызова media_id в настоящее время не используется и всегда должен быть равен нулю.</span><span class="sxs-lookup"><span data-stu-id="456ca-137">The calling parameter media_id is not currently used and should always be 0.</span></span> <span data-ttu-id="456ca-138">В будущем его можно использовать для различения нескольких запоминающих устройств или запоминающих устройств с несколькими LUN SCSI.</span><span class="sxs-lookup"><span data-stu-id="456ca-138">In the future it may be used to distinguish multiple storage devices or storage devices with multiple SCSI LUNs.</span></span> <span data-ttu-id="456ca-139">Эта версия класса хранения не поддерживает несколько экземпляров класса хранения или запоминающих устройств с несколькими LUN SCSI.</span><span class="sxs-lookup"><span data-stu-id="456ca-139">This version of the storage class does not support multiple instances of the storage class or storage devices with multiple SCSI LUNs.</span></span>

<span data-ttu-id="456ca-140">Возвращаемое значение — это код ошибки SCSI, который может иметь следующий формат.</span><span class="sxs-lookup"><span data-stu-id="456ca-140">The return value is a SCSI error code that can have the following format.</span></span>

- <span data-ttu-id="456ca-141">**Биты 0–7**: смысловой ключ</span><span class="sxs-lookup"><span data-stu-id="456ca-141">**Bits 0-7** Sense_key</span></span>
- <span data-ttu-id="456ca-142">**Биты 8–15**: дополнительный смысловой код</span><span class="sxs-lookup"><span data-stu-id="456ca-142">**Bits 8-15** Additional Sense Code</span></span>
- <span data-ttu-id="456ca-143">**Биты 16–23**: квалификатор дополнительного смыслового кода</span><span class="sxs-lookup"><span data-stu-id="456ca-143">**Bits 16-23** Additional Sense Code Qualifier</span></span>

<span data-ttu-id="456ca-144">В следующей таблице приведены возможные сочетания смыслового ключа/ASC/ASCQ.</span><span class="sxs-lookup"><span data-stu-id="456ca-144">The following table provides the possible Sense/ASC/ASCQ combinations.</span></span>

| <span data-ttu-id="456ca-145">Смысловой ключ</span><span class="sxs-lookup"><span data-stu-id="456ca-145">Sense Key</span></span> | <span data-ttu-id="456ca-146">ASC</span><span class="sxs-lookup"><span data-stu-id="456ca-146">ASC</span></span> | <span data-ttu-id="456ca-147">ASCQ</span><span class="sxs-lookup"><span data-stu-id="456ca-147">ASCQ</span></span> | <span data-ttu-id="456ca-148">Описание</span><span class="sxs-lookup"><span data-stu-id="456ca-148">Description</span></span>                                       |
| --------- | --- | ---- | ------------------------------------------------- |
| <span data-ttu-id="456ca-149">00</span><span class="sxs-lookup"><span data-stu-id="456ca-149">00</span></span>        | <span data-ttu-id="456ca-150">00</span><span class="sxs-lookup"><span data-stu-id="456ca-150">00</span></span>  | <span data-ttu-id="456ca-151">00</span><span class="sxs-lookup"><span data-stu-id="456ca-151">00</span></span>   | <span data-ttu-id="456ca-152">НЕТ СМЫСЛА</span><span class="sxs-lookup"><span data-stu-id="456ca-152">NO SENSE</span></span>                                          |
| <span data-ttu-id="456ca-153">01</span><span class="sxs-lookup"><span data-stu-id="456ca-153">01</span></span>        | <span data-ttu-id="456ca-154">17</span><span class="sxs-lookup"><span data-stu-id="456ca-154">17</span></span>  | <span data-ttu-id="456ca-155">01</span><span class="sxs-lookup"><span data-stu-id="456ca-155">01</span></span>   | <span data-ttu-id="456ca-156">ВОССТАНОВЛЕННЫЕ ДАННЫЕ С ПОВТОРНЫМИ ПОПЫТКАМИ</span><span class="sxs-lookup"><span data-stu-id="456ca-156">RECOVERED DATA WITH RETRIES</span></span>                       |
| <span data-ttu-id="456ca-157">01</span><span class="sxs-lookup"><span data-stu-id="456ca-157">01</span></span>        | <span data-ttu-id="456ca-158">18</span><span class="sxs-lookup"><span data-stu-id="456ca-158">18</span></span>  | <span data-ttu-id="456ca-159">00</span><span class="sxs-lookup"><span data-stu-id="456ca-159">00</span></span>   | <span data-ttu-id="456ca-160">ВОССТАНОВЛЕННЫЕ ДАННЫЕ С ECC</span><span class="sxs-lookup"><span data-stu-id="456ca-160">RECOVERED DATA WITH ECC</span></span>                           |
| <span data-ttu-id="456ca-161">02</span><span class="sxs-lookup"><span data-stu-id="456ca-161">02</span></span>        | <span data-ttu-id="456ca-162">04</span><span class="sxs-lookup"><span data-stu-id="456ca-162">04</span></span>  | <span data-ttu-id="456ca-163">01</span><span class="sxs-lookup"><span data-stu-id="456ca-163">01</span></span>   | <span data-ttu-id="456ca-164">ЛОГИЧЕСКИЙ ДИСК НЕ ГОТОВ — ГОТОВИТСЯ К РАБОТЕ</span><span class="sxs-lookup"><span data-stu-id="456ca-164">LOGICAL DRIVE NOT READY - BECOMING READY</span></span>          |
| <span data-ttu-id="456ca-165">02</span><span class="sxs-lookup"><span data-stu-id="456ca-165">02</span></span>        | <span data-ttu-id="456ca-166">04</span><span class="sxs-lookup"><span data-stu-id="456ca-166">04</span></span>  | <span data-ttu-id="456ca-167">02</span><span class="sxs-lookup"><span data-stu-id="456ca-167">02</span></span>   | <span data-ttu-id="456ca-168">ЛОГИЧЕСКИЙ ДИСК НЕ ГОТОВ — ТРЕБУЕТСЯ ИНИЦИАЛИЗАЦИЯ</span><span class="sxs-lookup"><span data-stu-id="456ca-168">LOGICAL DRIVE NOT READY - INITIALIZATION REQUIRED</span></span> |
| <span data-ttu-id="456ca-169">02</span><span class="sxs-lookup"><span data-stu-id="456ca-169">02</span></span>        | <span data-ttu-id="456ca-170">04</span><span class="sxs-lookup"><span data-stu-id="456ca-170">04</span></span>  | <span data-ttu-id="456ca-171">04</span><span class="sxs-lookup"><span data-stu-id="456ca-171">04</span></span>   | <span data-ttu-id="456ca-172">ЛОГИЧЕСКОЕ УСТРОЙСТВО НЕ ГОТОВО — ВЫПОЛНЯЕТСЯ ФОРМАТИРОВАНИЕ</span><span class="sxs-lookup"><span data-stu-id="456ca-172">LOGICAL UNIT NOT READY - FORMAT IN PROGRESS</span></span>       |
| <span data-ttu-id="456ca-173">02</span><span class="sxs-lookup"><span data-stu-id="456ca-173">02</span></span>        | <span data-ttu-id="456ca-174">04</span><span class="sxs-lookup"><span data-stu-id="456ca-174">04</span></span>  | <span data-ttu-id="456ca-175">FF</span><span class="sxs-lookup"><span data-stu-id="456ca-175">FF</span></span>   | <span data-ttu-id="456ca-176">ЛОГИЧЕСКИЙ ДИСК НЕ ГОТОВ — УСТРОЙСТВО ЗАНЯТО</span><span class="sxs-lookup"><span data-stu-id="456ca-176">LOGICAL DRIVE NOT READY - DEVICE IS BUSY</span></span>          |
| <span data-ttu-id="456ca-177">02</span><span class="sxs-lookup"><span data-stu-id="456ca-177">02</span></span>        | <span data-ttu-id="456ca-178">06</span><span class="sxs-lookup"><span data-stu-id="456ca-178">06</span></span>  | <span data-ttu-id="456ca-179">00</span><span class="sxs-lookup"><span data-stu-id="456ca-179">00</span></span>   | <span data-ttu-id="456ca-180">ИСХОДНОЕ ПОЛОЖЕНИЕ НЕ НАЙДЕНО</span><span class="sxs-lookup"><span data-stu-id="456ca-180">NO REFERENCE POSITION FOUND</span></span>                       |
| <span data-ttu-id="456ca-181">02</span><span class="sxs-lookup"><span data-stu-id="456ca-181">02</span></span>        | <span data-ttu-id="456ca-182">08</span><span class="sxs-lookup"><span data-stu-id="456ca-182">08</span></span>  | <span data-ttu-id="456ca-183">00</span><span class="sxs-lookup"><span data-stu-id="456ca-183">00</span></span>   | <span data-ttu-id="456ca-184">СБОЙ СВЯЗИ С ЛОГИЧЕСКИМ УСТРОЙСТВОМ</span><span class="sxs-lookup"><span data-stu-id="456ca-184">LOGICAL UNIT COMMUNICATION FAILURE</span></span>                |
| <span data-ttu-id="456ca-185">02</span><span class="sxs-lookup"><span data-stu-id="456ca-185">02</span></span>        | <span data-ttu-id="456ca-186">08</span><span class="sxs-lookup"><span data-stu-id="456ca-186">08</span></span>  | <span data-ttu-id="456ca-187">01</span><span class="sxs-lookup"><span data-stu-id="456ca-187">01</span></span>   | <span data-ttu-id="456ca-188">ВРЕМЯ ОЖИДАНИЯ СВЯЗИ С ЛОГИЧЕСКИМ УСТРОЙСТВОМ ИСТЕКЛО</span><span class="sxs-lookup"><span data-stu-id="456ca-188">LOGICAL UNIT COMMUNICATION TIME-OUT</span></span>               |
| <span data-ttu-id="456ca-189">02</span><span class="sxs-lookup"><span data-stu-id="456ca-189">02</span></span>        | <span data-ttu-id="456ca-190">08</span><span class="sxs-lookup"><span data-stu-id="456ca-190">08</span></span>  | <span data-ttu-id="456ca-191">80</span><span class="sxs-lookup"><span data-stu-id="456ca-191">80</span></span>   | <span data-ttu-id="456ca-192">ПЕРЕПОЛНЕНИЕ СВЯЗИ С ЛОГИЧЕСКИМ УСТРОЙСТВОМ</span><span class="sxs-lookup"><span data-stu-id="456ca-192">LOGICAL UNIT COMMUNICATION OVERRUN</span></span>                |
| <span data-ttu-id="456ca-193">02</span><span class="sxs-lookup"><span data-stu-id="456ca-193">02</span></span>        | <span data-ttu-id="456ca-194">3A</span><span class="sxs-lookup"><span data-stu-id="456ca-194">3A</span></span>  | <span data-ttu-id="456ca-195">00</span><span class="sxs-lookup"><span data-stu-id="456ca-195">00</span></span>   | <span data-ttu-id="456ca-196">НОСИТЕЛЬ ОТСУТСТВУЕТ</span><span class="sxs-lookup"><span data-stu-id="456ca-196">MEDIUM NOT PRESENT</span></span>                                |
| <span data-ttu-id="456ca-197">02</span><span class="sxs-lookup"><span data-stu-id="456ca-197">02</span></span>        | <span data-ttu-id="456ca-198">54</span><span class="sxs-lookup"><span data-stu-id="456ca-198">54</span></span>  | <span data-ttu-id="456ca-199">00</span><span class="sxs-lookup"><span data-stu-id="456ca-199">00</span></span>   | <span data-ttu-id="456ca-200">СБОЙ ИНТЕРФЕЙСА МЕЖДУ USB И ХОСТ-СИСТЕМОЙ</span><span class="sxs-lookup"><span data-stu-id="456ca-200">USB TO HOST SYSTEM INTERFACE FAILURE</span></span>              |
| <span data-ttu-id="456ca-201">02</span><span class="sxs-lookup"><span data-stu-id="456ca-201">02</span></span>        | <span data-ttu-id="456ca-202">80</span><span class="sxs-lookup"><span data-stu-id="456ca-202">80</span></span>  | <span data-ttu-id="456ca-203">00</span><span class="sxs-lookup"><span data-stu-id="456ca-203">00</span></span>   | <span data-ttu-id="456ca-204">НЕДОСТАТОЧНО РЕСУРСОВ</span><span class="sxs-lookup"><span data-stu-id="456ca-204">INSUFFICIENT RESOURCES</span></span>                            |
| <span data-ttu-id="456ca-205">02</span><span class="sxs-lookup"><span data-stu-id="456ca-205">02</span></span>        | <span data-ttu-id="456ca-206">FF</span><span class="sxs-lookup"><span data-stu-id="456ca-206">FF</span></span>  | <span data-ttu-id="456ca-207">FF</span><span class="sxs-lookup"><span data-stu-id="456ca-207">FF</span></span>   | <span data-ttu-id="456ca-208">НЕИЗВЕСТНАЯ ОШИБКА</span><span class="sxs-lookup"><span data-stu-id="456ca-208">UNKNOWN ERROR</span></span>                                     |
| <span data-ttu-id="456ca-209">03</span><span class="sxs-lookup"><span data-stu-id="456ca-209">03</span></span>        | <span data-ttu-id="456ca-210">02</span><span class="sxs-lookup"><span data-stu-id="456ca-210">02</span></span>  | <span data-ttu-id="456ca-211">00</span><span class="sxs-lookup"><span data-stu-id="456ca-211">00</span></span>   | <span data-ttu-id="456ca-212">ПОИСК НЕ ЗАВЕРШЕН</span><span class="sxs-lookup"><span data-stu-id="456ca-212">NO SEEK COMPLETE</span></span>                                  |
| <span data-ttu-id="456ca-213">03</span><span class="sxs-lookup"><span data-stu-id="456ca-213">03</span></span>        | <span data-ttu-id="456ca-214">03</span><span class="sxs-lookup"><span data-stu-id="456ca-214">03</span></span>  | <span data-ttu-id="456ca-215">00</span><span class="sxs-lookup"><span data-stu-id="456ca-215">00</span></span>   | <span data-ttu-id="456ca-216">ОШИБКА ЗАПИСИ</span><span class="sxs-lookup"><span data-stu-id="456ca-216">WRITE FAULT</span></span>                                       |
| <span data-ttu-id="456ca-217">03</span><span class="sxs-lookup"><span data-stu-id="456ca-217">03</span></span>        | <span data-ttu-id="456ca-218">10</span><span class="sxs-lookup"><span data-stu-id="456ca-218">10</span></span>  | <span data-ttu-id="456ca-219">00</span><span class="sxs-lookup"><span data-stu-id="456ca-219">00</span></span>   | <span data-ttu-id="456ca-220">ОШИБКА CRC ИДЕНТИФИКАТОРА</span><span class="sxs-lookup"><span data-stu-id="456ca-220">ID CRC ERROR</span></span>                                      |
| <span data-ttu-id="456ca-221">03</span><span class="sxs-lookup"><span data-stu-id="456ca-221">03</span></span>        | <span data-ttu-id="456ca-222">11</span><span class="sxs-lookup"><span data-stu-id="456ca-222">11</span></span>  | <span data-ttu-id="456ca-223">00</span><span class="sxs-lookup"><span data-stu-id="456ca-223">00</span></span>   | <span data-ttu-id="456ca-224">НЕУСТРАНЕННАЯ ОШИБКА ЧТЕНИЯ</span><span class="sxs-lookup"><span data-stu-id="456ca-224">UNRECOVERED READ ERROR</span></span>                            |
| <span data-ttu-id="456ca-225">03</span><span class="sxs-lookup"><span data-stu-id="456ca-225">03</span></span>        | <span data-ttu-id="456ca-226">12</span><span class="sxs-lookup"><span data-stu-id="456ca-226">12</span></span>  | <span data-ttu-id="456ca-227">00</span><span class="sxs-lookup"><span data-stu-id="456ca-227">00</span></span>   | <span data-ttu-id="456ca-228">НЕ УДАЛОСЬ НАЙТИ МЕТКУ АДРЕСА ДЛЯ ПОЛЯ ИДЕНТИФИКАТОРА</span><span class="sxs-lookup"><span data-stu-id="456ca-228">ADDRESS MARK NOT FOUND FOR ID FIELD</span></span>               |
| <span data-ttu-id="456ca-229">03</span><span class="sxs-lookup"><span data-stu-id="456ca-229">03</span></span>        | <span data-ttu-id="456ca-230">13</span><span class="sxs-lookup"><span data-stu-id="456ca-230">13</span></span>  | <span data-ttu-id="456ca-231">00</span><span class="sxs-lookup"><span data-stu-id="456ca-231">00</span></span>   | <span data-ttu-id="456ca-232">НЕ УДАЛОСЬ НАЙТИ МЕТКУ АДРЕСА ДЛЯ ПОЛЯ ДАННЫХ</span><span class="sxs-lookup"><span data-stu-id="456ca-232">ADDRESS MARK NOT FOUND FOR DATA FIELD</span></span>             |
| <span data-ttu-id="456ca-233">03</span><span class="sxs-lookup"><span data-stu-id="456ca-233">03</span></span>        | <span data-ttu-id="456ca-234">14</span><span class="sxs-lookup"><span data-stu-id="456ca-234">14</span></span>  | <span data-ttu-id="456ca-235">00</span><span class="sxs-lookup"><span data-stu-id="456ca-235">00</span></span>   | <span data-ttu-id="456ca-236">ЗАРЕГИСТРИРОВАННАЯ СУЩНОСТЬ НЕ НАЙДЕНА</span><span class="sxs-lookup"><span data-stu-id="456ca-236">RECORDED ENTITY NOT FOUND</span></span>                         |
| <span data-ttu-id="456ca-237">03</span><span class="sxs-lookup"><span data-stu-id="456ca-237">03</span></span>        | <span data-ttu-id="456ca-238">30</span><span class="sxs-lookup"><span data-stu-id="456ca-238">30</span></span>  | <span data-ttu-id="456ca-239">01</span><span class="sxs-lookup"><span data-stu-id="456ca-239">01</span></span>   | <span data-ttu-id="456ca-240">НЕ УДАЕТСЯ СЧИТАТЬ ДАННЫЕ С НОСИТЕЛЯ — НЕИЗВЕСТНЫЙ ФОРМАТ</span><span class="sxs-lookup"><span data-stu-id="456ca-240">CANNOT READ MEDIUM - UNKNOWN FORMAT</span></span>               |
| <span data-ttu-id="456ca-241">03</span><span class="sxs-lookup"><span data-stu-id="456ca-241">03</span></span>        | <span data-ttu-id="456ca-242">31</span><span class="sxs-lookup"><span data-stu-id="456ca-242">31</span></span>  | <span data-ttu-id="456ca-243">01</span><span class="sxs-lookup"><span data-stu-id="456ca-243">01</span></span>   | <span data-ttu-id="456ca-244">СБОЙ КОМАНДЫ ФОРМАТИРОВАНИЯ</span><span class="sxs-lookup"><span data-stu-id="456ca-244">FORMAT COMMAND FAILED</span></span>                             |
| <span data-ttu-id="456ca-245">04</span><span class="sxs-lookup"><span data-stu-id="456ca-245">04</span></span>        | <span data-ttu-id="456ca-246">40</span><span class="sxs-lookup"><span data-stu-id="456ca-246">40</span></span>  | <span data-ttu-id="456ca-247">NN</span><span class="sxs-lookup"><span data-stu-id="456ca-247">NN</span></span>   | <span data-ttu-id="456ca-248">СБОЙ ДИАГНОСТИКИ В КОМПОНЕНТЕ NN (80H-FFH)</span><span class="sxs-lookup"><span data-stu-id="456ca-248">DIAGNOSTIC FAILURE ON COMPONENT NN (80H-FFH)</span></span>      |
| <span data-ttu-id="456ca-249">05</span><span class="sxs-lookup"><span data-stu-id="456ca-249">05</span></span>        | <span data-ttu-id="456ca-250">1A</span><span class="sxs-lookup"><span data-stu-id="456ca-250">1A</span></span>  | <span data-ttu-id="456ca-251">00</span><span class="sxs-lookup"><span data-stu-id="456ca-251">00</span></span>   | <span data-ttu-id="456ca-252">ОШИБКА ДЛИНЫ СПИСКА ПАРАМЕТРОВ</span><span class="sxs-lookup"><span data-stu-id="456ca-252">PARAMETER LIST LENGTH ERROR</span></span>                       |
| <span data-ttu-id="456ca-253">05</span><span class="sxs-lookup"><span data-stu-id="456ca-253">05</span></span>        | <span data-ttu-id="456ca-254">20</span><span class="sxs-lookup"><span data-stu-id="456ca-254">20</span></span>  | <span data-ttu-id="456ca-255">00</span><span class="sxs-lookup"><span data-stu-id="456ca-255">00</span></span>   | <span data-ttu-id="456ca-256">НЕДОПУСТИМЫЙ КОД ОПЕРАЦИИ КОМАНДЫ</span><span class="sxs-lookup"><span data-stu-id="456ca-256">INVALID COMMAND OPERATION CODE</span></span>                    |
| <span data-ttu-id="456ca-257">05</span><span class="sxs-lookup"><span data-stu-id="456ca-257">05</span></span>        | <span data-ttu-id="456ca-258">21</span><span class="sxs-lookup"><span data-stu-id="456ca-258">21</span></span>  | <span data-ttu-id="456ca-259">00</span><span class="sxs-lookup"><span data-stu-id="456ca-259">00</span></span>   | <span data-ttu-id="456ca-260">АДРЕС ЛОГИЧЕСКОГО БЛОКА ВНЕ ДОПУСТИМОГО ДИАПАЗОНА</span><span class="sxs-lookup"><span data-stu-id="456ca-260">LOGICAL BLOCK ADDRESS OUT OF RANGE</span></span>                |
| <span data-ttu-id="456ca-261">05</span><span class="sxs-lookup"><span data-stu-id="456ca-261">05</span></span>        | <span data-ttu-id="456ca-262">24</span><span class="sxs-lookup"><span data-stu-id="456ca-262">24</span></span>  | <span data-ttu-id="456ca-263">00</span><span class="sxs-lookup"><span data-stu-id="456ca-263">00</span></span>   | <span data-ttu-id="456ca-264">НЕДОПУСТИМОЕ ПОЛЕ В КОМАНДНОМ ПАКЕТЕ</span><span class="sxs-lookup"><span data-stu-id="456ca-264">INVALID FIELD IN COMMAND PACKET</span></span>                   |
| <span data-ttu-id="456ca-265">05</span><span class="sxs-lookup"><span data-stu-id="456ca-265">05</span></span>        | <span data-ttu-id="456ca-266">25</span><span class="sxs-lookup"><span data-stu-id="456ca-266">25</span></span>  | <span data-ttu-id="456ca-267">00</span><span class="sxs-lookup"><span data-stu-id="456ca-267">00</span></span>   | <span data-ttu-id="456ca-268">ЛОГИЧЕСКОЕ УСТРОЙСТВО НЕ ПОДДЕРЖИВАЕТСЯ</span><span class="sxs-lookup"><span data-stu-id="456ca-268">LOGICAL UNIT NOT SUPPORTED</span></span>                        |
| <span data-ttu-id="456ca-269">05</span><span class="sxs-lookup"><span data-stu-id="456ca-269">05</span></span>        | <span data-ttu-id="456ca-270">26</span><span class="sxs-lookup"><span data-stu-id="456ca-270">26</span></span>  | <span data-ttu-id="456ca-271">00</span><span class="sxs-lookup"><span data-stu-id="456ca-271">00</span></span>   | <span data-ttu-id="456ca-272">НЕДОПУСТИМОЕ ПОЛЕ В СПИСКЕ ПАРАМЕТРОВ</span><span class="sxs-lookup"><span data-stu-id="456ca-272">INVALID FIELD IN PARAMETER LIST</span></span>                   |
| <span data-ttu-id="456ca-273">05</span><span class="sxs-lookup"><span data-stu-id="456ca-273">05</span></span>        | <span data-ttu-id="456ca-274">26</span><span class="sxs-lookup"><span data-stu-id="456ca-274">26</span></span>  | <span data-ttu-id="456ca-275">01</span><span class="sxs-lookup"><span data-stu-id="456ca-275">01</span></span>   | <span data-ttu-id="456ca-276">НЕПОДДЕРЖИВАЕМЫЙ ПАРАМЕТР</span><span class="sxs-lookup"><span data-stu-id="456ca-276">PARAMETER NOT SUPPORTED</span></span>                           |
| <span data-ttu-id="456ca-277">05</span><span class="sxs-lookup"><span data-stu-id="456ca-277">05</span></span>        | <span data-ttu-id="456ca-278">26</span><span class="sxs-lookup"><span data-stu-id="456ca-278">26</span></span>  | <span data-ttu-id="456ca-279">02</span><span class="sxs-lookup"><span data-stu-id="456ca-279">02</span></span>   | <span data-ttu-id="456ca-280">НЕДОПУСТИМОЕ ЗНАЧЕНИЕ ПАРАМЕТРА</span><span class="sxs-lookup"><span data-stu-id="456ca-280">PARAMETER VALUE INVALID</span></span>                           |
| <span data-ttu-id="456ca-281">05</span><span class="sxs-lookup"><span data-stu-id="456ca-281">05</span></span>        | <span data-ttu-id="456ca-282">39</span><span class="sxs-lookup"><span data-stu-id="456ca-282">39</span></span>  | <span data-ttu-id="456ca-283">00</span><span class="sxs-lookup"><span data-stu-id="456ca-283">00</span></span>   | <span data-ttu-id="456ca-284">СОХРАНЕНИЕ ПАРАМЕТРОВ НЕ ПОДДЕРЖИВАЕТСЯ</span><span class="sxs-lookup"><span data-stu-id="456ca-284">SAVING PARAMETERS NOT SUPPORT</span></span>                     |
| <span data-ttu-id="456ca-285">06</span><span class="sxs-lookup"><span data-stu-id="456ca-285">06</span></span>        | <span data-ttu-id="456ca-286">28</span><span class="sxs-lookup"><span data-stu-id="456ca-286">28</span></span>  | <span data-ttu-id="456ca-287">00</span><span class="sxs-lookup"><span data-stu-id="456ca-287">00</span></span>   | <span data-ttu-id="456ca-288">НЕ ГОТОВО К ПЕРЕХОДУ В СОСТОЯНИЕ ГОТОВНОСТИ — НОСИТЕЛЬ ИЗМЕНЕН</span><span class="sxs-lookup"><span data-stu-id="456ca-288">NOT READY TO READY TRANSITION – MEDIA CHANGED</span></span>     |
| <span data-ttu-id="456ca-289">06</span><span class="sxs-lookup"><span data-stu-id="456ca-289">06</span></span>        | <span data-ttu-id="456ca-290">29</span><span class="sxs-lookup"><span data-stu-id="456ca-290">29</span></span>  | <span data-ttu-id="456ca-291">00</span><span class="sxs-lookup"><span data-stu-id="456ca-291">00</span></span>   | <span data-ttu-id="456ca-292">ПРОИЗОШЕЛ СБРОС ПИТАНИЯ ИЛИ СБРОС УСТРОЙСТВА ШИНЫ</span><span class="sxs-lookup"><span data-stu-id="456ca-292">POWER ON RESET OR BUS DEVICE RESET OCCURRED</span></span>       |
| <span data-ttu-id="456ca-293">06</span><span class="sxs-lookup"><span data-stu-id="456ca-293">06</span></span>        | <span data-ttu-id="456ca-294">2F</span><span class="sxs-lookup"><span data-stu-id="456ca-294">2F</span></span>  | <span data-ttu-id="456ca-295">00</span><span class="sxs-lookup"><span data-stu-id="456ca-295">00</span></span>   | <span data-ttu-id="456ca-296">КОМАНДЫ УДАЛЕНЫ ДРУГИМ ИНИЦИАТОРОМ</span><span class="sxs-lookup"><span data-stu-id="456ca-296">COMMANDS CLEARED BY ANOTHER INITIATOR</span></span>             |
| <span data-ttu-id="456ca-297">07</span><span class="sxs-lookup"><span data-stu-id="456ca-297">07</span></span>        | <span data-ttu-id="456ca-298">27</span><span class="sxs-lookup"><span data-stu-id="456ca-298">27</span></span>  | <span data-ttu-id="456ca-299">00</span><span class="sxs-lookup"><span data-stu-id="456ca-299">00</span></span>   | <span data-ttu-id="456ca-300">НОСИТЕЛЬ С ЗАЩИТОЙ ОТ ЗАПИСИ</span><span class="sxs-lookup"><span data-stu-id="456ca-300">WRITE PROTECTED MEDIA</span></span>                             |
| <span data-ttu-id="456ca-301">0B</span><span class="sxs-lookup"><span data-stu-id="456ca-301">0B</span></span>        | <span data-ttu-id="456ca-302">4E</span><span class="sxs-lookup"><span data-stu-id="456ca-302">4E</span></span>  | <span data-ttu-id="456ca-303">00</span><span class="sxs-lookup"><span data-stu-id="456ca-303">00</span></span>   | <span data-ttu-id="456ca-304">ПОПЫТКА ВЫПОЛНЕНИЯ ПЕРЕКРЫВАЮЩЕЙ КОМАНДЫ</span><span class="sxs-lookup"><span data-stu-id="456ca-304">OVERLAPPED COMMAND ATTEMPTED</span></span>                      |

<span data-ttu-id="456ca-305">Существует два дополнительных необязательных обратных вызова, которые может реализовать приложение. Один предназначен для реагирования на команду **GET_STATUS_NOTIFICATION**, а другой — для ответа на команду **SYNCHRONIZE_CACHE**.</span><span class="sxs-lookup"><span data-stu-id="456ca-305">There are two additional, optional callbacks the application may implement; one is for responding to a **GET_STATUS_NOTIFICATION** command and the other is for responding to the **SYNCHRONIZE_CACHE** command.</span></span>

<span data-ttu-id="456ca-306">Если приложение должно обработать команду GET_STATUS_NOTIFICATION от узла, оно должно реализовать обратный вызов со следующим прототипом.</span><span class="sxs-lookup"><span data-stu-id="456ca-306">If the application would like to handle the GET_STATUS_NOTIFICATION command from the host, it should implement a callback with the following prototype.</span></span>

```c
UINT ux_slave_class_storage_media_notification( 
    VOID *storage,  
    ULONG lun,
    ULONG media_id,  
    ULONG notification_class,
    UCHAR **media_notification,  
    ULONG *media_notification_length);
```

<span data-ttu-id="456ca-307">Где:</span><span class="sxs-lookup"><span data-stu-id="456ca-307">Where:</span></span>

- <span data-ttu-id="456ca-308">*storage* — экземпляр класса хранения.</span><span class="sxs-lookup"><span data-stu-id="456ca-308">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="456ca-309">*media_id* — в настоящее время не используется.</span><span class="sxs-lookup"><span data-stu-id="456ca-309">*media_id* is not currently used.</span></span> <span data-ttu-id="456ca-310">notification_class указывает класс уведомления.</span><span class="sxs-lookup"><span data-stu-id="456ca-310">notification_class specifies the class of notification.</span></span>
- <span data-ttu-id="456ca-311">*media_notification* задается приложением для буфера, содержащего ответ для уведомления.</span><span class="sxs-lookup"><span data-stu-id="456ca-311">*media_notification* should be set by the application to the buffer containing the response for the notification.</span></span>
- <span data-ttu-id="456ca-312">*media_notification_length* задается приложением для хранения длины буфера ответа.</span><span class="sxs-lookup"><span data-stu-id="456ca-312">*media_notification_length* should be set by the application to contain the length of the response buffer.</span></span>

<span data-ttu-id="456ca-313">Возвращаемое значение указывает, была ли команда успешной: должно быть либо **UX_SUCCESS**, либо **UX_ERROR**.</span><span class="sxs-lookup"><span data-stu-id="456ca-313">The return value indicates whether or not the command succeeded – should be either **UX_SUCCESS** or **UX_ERROR**.</span></span>

<span data-ttu-id="456ca-314">Если приложение не реализует этот обратный вызов, то после получения команды **GET_STATUS_NOTIFICATION** USBX будет уведомлять узел о том, что команда не реализована.</span><span class="sxs-lookup"><span data-stu-id="456ca-314">If the application does not implement this callback, then upon receiving the **GET_STATUS_NOTIFICATION** command, USBX will notify the host that the command is not implemented.</span></span>

<span data-ttu-id="456ca-315">Команда **SYNCHRONIZE_CACHE** должна быть обработана, если приложение использует кэш для записи с узла.</span><span class="sxs-lookup"><span data-stu-id="456ca-315">The **SYNCHRONIZE_CACHE** command should be handled if the application is utilizing a cache for writes from the host.</span></span> <span data-ttu-id="456ca-316">Узел может отправить эту команду, если известно, что запоминающее устройство будет отключено. Например, если в ОС Windows щелкнуть значок устройства флэш-памяти на панели инструментов правой кнопкой мыши и выбрать команду "Извлечь \[имя запоминающего устройства\]", Windows выдаст этому устройству команду **SYNCHRONIZE_CACHE**.</span><span class="sxs-lookup"><span data-stu-id="456ca-316">A host may send this command if it knows the storage device is about to be disconnected, for example, in Windows, if you right click a flash drive icon in the toolbar and select "Eject \[storage device name\]", Windows will issue the **SYNCHRONIZE_CACHE** command to that device.</span></span>

<span data-ttu-id="456ca-317">Если приложение должно обработать команду **GET_STATUS_NOTIFICATION** от узла, оно должно реализовать обратный вызов со следующим прототипом.</span><span class="sxs-lookup"><span data-stu-id="456ca-317">If the application would like to handle the **GET_STATUS_NOTIFICATION** command from the host, it should implement a callback with the following prototype.</span></span>

```c
UINT ux_slave_class_storage_media_flush(
    VOID *storage, 
    ULONG lun,
    ULONG number_blocks, 
    ULONG lba, 
    ULONG *media_status);
```

<span data-ttu-id="456ca-318">Где:</span><span class="sxs-lookup"><span data-stu-id="456ca-318">Where:</span></span>

- <span data-ttu-id="456ca-319">*storage* — экземпляр класса хранения.</span><span class="sxs-lookup"><span data-stu-id="456ca-319">*storage* is the instance of the storage class.</span></span>
- <span data-ttu-id="456ca-320">*lun* указывает, к какому LUN направлена команда.</span><span class="sxs-lookup"><span data-stu-id="456ca-320">*lun* parameter specifies which LUN the command is directed to.</span></span>
- <span data-ttu-id="456ca-321">*number_blocks* — количество синхронизируемых блоков.</span><span class="sxs-lookup"><span data-stu-id="456ca-321">*number_blocks* specifies the number of blocks to synchronize.</span></span>
- <span data-ttu-id="456ca-322">*lba* — адрес сектора первого блока для синхронизации.</span><span class="sxs-lookup"><span data-stu-id="456ca-322">*lba* is the sector address of the first block to synchronize.</span></span>
- <span data-ttu-id="456ca-323">*media_status* должен полностью совпадать с возвращаемым значением обратного вызова состояния носителя.</span><span class="sxs-lookup"><span data-stu-id="456ca-323">*media_status* should be filled out exactly like the media status callback return value.</span></span>

<span data-ttu-id="456ca-324">Возвращаемое значение указывает, была ли команда успешной: должно быть либо **UX_SUCCESS**, либо **UX_ERROR**.</span><span class="sxs-lookup"><span data-stu-id="456ca-324">The return value indicates whether or not the command succeeded – should be either **UX_SUCCESS** or **UX_ERROR**.</span></span>

### <a name="multiple-scsi-lun"></a><span data-ttu-id="456ca-325">Несколько LUN SCSI</span><span class="sxs-lookup"><span data-stu-id="456ca-325">Multiple SCSI LUN</span></span>

<span data-ttu-id="456ca-326">Класс хранения устройства USBX поддерживает несколько LUN.</span><span class="sxs-lookup"><span data-stu-id="456ca-326">The USBX device storage class supports multiple LUNs.</span></span> <span data-ttu-id="456ca-327">Поэтому можно создать запоминающее устройство, которое будет одновременно работать как компакт-диск и устройство флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="456ca-327">It is therefore possible to create a storage device that acts as a CD-ROM and a Flash disk at the same time.</span></span> <span data-ttu-id="456ca-328">В этом случае инициализация будет немного отличаться.</span><span class="sxs-lookup"><span data-stu-id="456ca-328">In such a case, the initialization would be slightly different.</span></span> <span data-ttu-id="456ca-329">Ниже приведен пример для устройства флэш-памяти и компакт-диска.</span><span class="sxs-lookup"><span data-stu-id="456ca-329">Here is an example for a Flash Disk and CD-ROM:</span></span>

```c
/* Store the number of LUN in this device storage instance. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 2;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x7bbff;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the storage class LUN parameters for reading/writing to the CD-ROM. */

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_last_lba = 0x04caaf;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_block_length = 2048;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_type = 5;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_removable_flag = 0x80;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_read = tx_demo_thread_cdrom_media_read;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_write = tx_demo_thread_cdrom_media_write;

storage_parameter.ux_slave_class_storage_parameter_lun[1].ux_slave_class_storage_media_status = tx_demo_thread_cdrom_media_status;

/* Initialize the device storage class for a Flash disk and CD-ROM. The class is connected with interface 0 */ status = ux_device_stack_class_register(_ux_system_slave_class_storage_name,ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *) &storage_parameter);
```

## <a name="usb-device-cdc-acm-class"></a><span data-ttu-id="456ca-330">Класс CDC-ACM USB-устройства</span><span class="sxs-lookup"><span data-stu-id="456ca-330">USB Device CDC-ACM Class</span></span>

<span data-ttu-id="456ca-331">Класс CDC-ACM USB-устройства позволяет хост-системе USB обмениваться данными с устройством как с устройством с последовательным интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="456ca-331">The USB device CDC-ACM class allows for a USB host system to communicate with the device as a serial device.</span></span> <span data-ttu-id="456ca-332">Этот класс основан на стандарте USB и является подмножеством стандарта CDC.</span><span class="sxs-lookup"><span data-stu-id="456ca-332">This class is based on the USB standard and is a subset of the CDC standard.</span></span>

<span data-ttu-id="456ca-333">В стеке устройств необходимо объявить совместимую с CDC-ACM платформу устройств.</span><span class="sxs-lookup"><span data-stu-id="456ca-333">A CDC-ACM compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="456ca-334">Ниже приведен пример этого.</span><span class="sxs-lookup"><span data-stu-id="456ca-334">An example is found here below.</span></span>

```c
unsigned char device_framework_full_speed[] = {

    /*
    Device descriptor 18 bytes
    0x02 bDeviceClass: CDC class code
    0x00 bDeviceSubclass: CDC class sub code 0x00 bDeviceProtocol: CDC Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    0x12, 0x01, 0x10, 0x01,
    0xEF, 0x02, 0x01, 0x08,
    0x84, 0x84, 0x00, 0x00,
    0x00, 0x01, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration 1 descriptor 9 bytes */
    0x09, 0x02, 0x4b, 0x00, 0x02, 0x01, 0x00,0x40, 0x00,

    /* Interface association descriptor. 8 bytes. */
    0x08, 0x0b, 0x00,
    0x02, 0x02, 0x02, 0x00, 0x00,

    /* Communication Class Interface Descriptor Requirement. 9 bytes. */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x02, 0x01, 0x00,

    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00,0x10, 0x01,

    /* ACM Functional Descriptor 4 bytes */
    0x04, 0x24, 0x02,0x0f,

    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,

    /* Master interface */
    0x01, /* Slave interface */

    /* Call Management Functional Descriptor 5 bytes */
    0x05, 0x24, 0x01,0x03, 0x01, /* Data interface */

    /* Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x83, 0x03,0x08, 0x00, 0xFF,

    /* Data Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x02,0x0A, 0x00, 0x00, 0x00,

    /* First alternate setting Endpoint 1 descriptor 7 bytes*/
    0x07, 0x05, 0x02,0x02,0x40, 0x00,0x00,

    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81,0x02,0x40, 0x00, 0x00,

};
```

<span data-ttu-id="456ca-335">Класс CDC-ACM использует составную платформу устройств для группирования интерфейсов (элементов управления и данных).</span><span class="sxs-lookup"><span data-stu-id="456ca-335">The CDC-ACM class uses a composite device framework to group interfaces (control and data).</span></span> <span data-ttu-id="456ca-336">В результате при определении дескриптора устройства следует проявлять осторожность.</span><span class="sxs-lookup"><span data-stu-id="456ca-336">As a result care should be taken when defining the device descriptor.</span></span> <span data-ttu-id="456ca-337">USBX использует дескриптор IAD для определения внутреннего порядка привязки интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="456ca-337">USBX relies on the IAD descriptor to know internally how to bind interfaces.</span></span> <span data-ttu-id="456ca-338">Дескриптор IAD должен быть объявлен перед интерфейсами. Он должен содержать первый интерфейс класса CDC-ACM и количество присоединенных интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="456ca-338">The IAD descriptor should be declared before the interfaces and contain the first interface of the CDC-ACM class and how many interfaces are attached.</span></span>

<span data-ttu-id="456ca-339">Класс CDC-ACM также использует функциональный дескриптор объединения, который выполняет ту же функцию, что и новый дескриптор IAD.</span><span class="sxs-lookup"><span data-stu-id="456ca-339">The CDC-ACM class also uses a union functional descriptor which performs the same function as the newer IAD descriptor.</span></span> <span data-ttu-id="456ca-340">Несмотря на то что функциональный дескриптор объединения должен быть объявлен по историческим причинам и для обеспечения совместимости на стороне узла, он не используется USBX.</span><span class="sxs-lookup"><span data-stu-id="456ca-340">Although a Union Functional descriptor must be declared for historical reasons and compatibility with the host side, it is not used by USBX.</span></span>

<span data-ttu-id="456ca-341">При инициализации класса CDC-ACM требуются следующие параметры.</span><span class="sxs-lookup"><span data-stu-id="456ca-341">The initialization of the CDC-ACM class expects the following parameters.</span></span>

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. */

parameter.ux_slave_class_cdc_acm_instance_activate = tx_demo_cdc_instance_activate;

parameter.ux_slave_class_cdc_acm_instance_deactivate = tx_demo_cdc_instance_deactivate;

parameter.ux_slave_class_cdc_acm_parameter_change = tx_demo_cdc_instance_parameter_change;

/* Initialize the device cdc class. This class owns both interfaces starting with 0. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_acm_name,ux_device_class_cdc_acm_entry,
    1,0, &parameter);
```

<span data-ttu-id="456ca-342">Два определенных параметра — это указатели обратного вызова в пользовательские приложения, которые будут вызываться при активации или отключении этого класса стеком.</span><span class="sxs-lookup"><span data-stu-id="456ca-342">The 2 parameters defined are callback pointers into the user applications that will be called when the stack activates or deactivate this class.</span></span>

<span data-ttu-id="456ca-343">Третий параметр — это указатель обратного вызова в пользовательское приложение, которое будет вызываться при изменении параметра кода строки или состояния строки.</span><span class="sxs-lookup"><span data-stu-id="456ca-343">The third parameter defined is a callback pointer to the user application that will be called when there is line coding or line states parameter change.</span></span> <span data-ttu-id="456ca-344">Например, при получении от узла запроса на изменение состояния DTR на **TRUE** вызывается обратный вызов. В пользовательском приложении можно проверить состояние строки с помощью функции IOCTL, чтобы знать, что узел готов к обмену данными.</span><span class="sxs-lookup"><span data-stu-id="456ca-344">E.g., when there is request from host to change DTR state to **TRUE**, the callback is invoked, in it user application can check line states through IOCTL function to kow host is ready for communication.</span></span>

<span data-ttu-id="456ca-345">CDC-ACM основан на стандарте USB-IF, и он автоматически распознается операционными системами MacOs и Linux.</span><span class="sxs-lookup"><span data-stu-id="456ca-345">The CDC-ACM is based on a USB-IF standard and is automatically recognized by MACOs and Linux operating systems.</span></span> <span data-ttu-id="456ca-346">В платформах Windows, предшествующих версии 10, для этого класса требуется INF-файл.</span><span class="sxs-lookup"><span data-stu-id="456ca-346">On Windows platforms, this class requires a .inf file for Windows version prior to 10.</span></span> <span data-ttu-id="456ca-347">В Windows 10 не требуется никаких INF-файлов.</span><span class="sxs-lookup"><span data-stu-id="456ca-347">Windows 10 does not require any .inf files.</span></span> <span data-ttu-id="456ca-348">Мы предоставляем шаблон для класса CDC-ACM, который находится в каталоге ***usbx_windows_host_files***.</span><span class="sxs-lookup"><span data-stu-id="456ca-348">We supply a template for the CDC-ACM class and it can be found in the ***usbx_windows_host_files*** directory.</span></span> <span data-ttu-id="456ca-349">Для более поздней версии Windows следует использовать файл CDC_ACM_Template_Win7_64bit.INF (кроме Win10).</span><span class="sxs-lookup"><span data-stu-id="456ca-349">For more recent version of Windows the file CDC_ACM_Template_Win7_64bit.inf should be used (except Win10).</span></span> <span data-ttu-id="456ca-350">Этот файл необходимо изменить в соответствии с идентификатором PID/VID, используемым устройством.</span><span class="sxs-lookup"><span data-stu-id="456ca-350">This file needs to be modified to reflect the PID/VID used by the device.</span></span> <span data-ttu-id="456ca-351">PID/VID зависит от клиента, если компания и продукт зарегистрированы с использованием USB-IF.</span><span class="sxs-lookup"><span data-stu-id="456ca-351">The PID/VID will be specific to the final customer when the company and the product are registered with the USB-IF.</span></span> <span data-ttu-id="456ca-352">В INF-файле поля для изменения находятся здесь.</span><span class="sxs-lookup"><span data-stu-id="456ca-352">In the inf file, the fields to modify are located here.</span></span>

```INF
[DeviceList]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000

[DeviceList.NTamd64]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000
```

<span data-ttu-id="456ca-353">В платформе устройств устройства CDC-ACM идентификатор PID/VID хранится в дескрипторе устройства (см. дескриптор устройства, объявленный выше).</span><span class="sxs-lookup"><span data-stu-id="456ca-353">In the device framework of the CDC-ACM device, the PID/VID are stored in the device descriptor (see the device descriptor declared above).</span></span>

<span data-ttu-id="456ca-354">Когда хост-системы USB обнаруживают устройство USB CDC-ACM, они подключают последовательный класс и устройство можно использовать с любой последовательной терминальной программой.</span><span class="sxs-lookup"><span data-stu-id="456ca-354">When a USB host systems discovers the USB CDC-ACM device, it will mount a serial class and the device can be used with any serial terminal program.</span></span> <span data-ttu-id="456ca-355">Подробнее см. в разделе "Операционная система узла".</span><span class="sxs-lookup"><span data-stu-id="456ca-355">See the host Operating System for reference.</span></span>

<span data-ttu-id="456ca-356">Функции API класса CDC-ACM определены ниже.</span><span class="sxs-lookup"><span data-stu-id="456ca-356">The CDC-ACM class API functions are defined below.</span></span>

### <a name="ux_device_class_cdc_acm_ioctl"></a><span data-ttu-id="456ca-357">ux_device_class_cdc_acm_ioctl</span><span class="sxs-lookup"><span data-stu-id="456ca-357">ux_device_class_cdc_acm_ioctl</span></span>

<span data-ttu-id="456ca-358">Выполнение IOCTL в интерфейсе CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="456ca-358">Perform IOCTL on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="456ca-359">Прототип</span><span class="sxs-lookup"><span data-stu-id="456ca-359">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm, 
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="456ca-360">Описание</span><span class="sxs-lookup"><span data-stu-id="456ca-360">Description</span></span>

<span data-ttu-id="456ca-361">Эта функция вызывается, когда приложению требуется выполнить различные вызовы IOCTL в интерфейс CDC ACM.</span><span class="sxs-lookup"><span data-stu-id="456ca-361">This function is called when an application needs to perform various ioctl calls to the cdc acm interface</span></span>

### <a name="parameters"></a><span data-ttu-id="456ca-362">Параметры</span><span class="sxs-lookup"><span data-stu-id="456ca-362">Parameters</span></span>

- <span data-ttu-id="456ca-363">**cdc_acm**: указатель на экземпляр класса CDC.</span><span class="sxs-lookup"><span data-stu-id="456ca-363">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="456ca-364">**ioctl_function**: функция IOCTL для выполнения.</span><span class="sxs-lookup"><span data-stu-id="456ca-364">**ioctl_function**: Ioctl function to be performed.</span></span>
- <span data-ttu-id="456ca-365">**parameter**: указатель на параметр, относящийся к вызову IOCTL.</span><span class="sxs-lookup"><span data-stu-id="456ca-365">**parameter**: Pointer to a parameter specific to the ioctl call.</span></span>

### <a name="return-value"></a><span data-ttu-id="456ca-366">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="456ca-366">Return Value</span></span>

- <span data-ttu-id="456ca-367">**UX_SUCCESS** (0x00) — операция успешно выполнена</span><span class="sxs-lookup"><span data-stu-id="456ca-367">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="456ca-368">**UX_ERROR** (0xFF) — ошибка в функции</span><span class="sxs-lookup"><span data-stu-id="456ca-368">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="456ca-369">Например, .</span><span class="sxs-lookup"><span data-stu-id="456ca-369">Example</span></span>

```c
/* Start cdc acm callback transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

if(status != UX_SUCCESS)
    return;
```

### <a name="ioctl-functions"></a><span data-ttu-id="456ca-370">Функции IOCTL</span><span class="sxs-lookup"><span data-stu-id="456ca-370">Ioctl functions:</span></span>

| <span data-ttu-id="456ca-371">Функция</span><span class="sxs-lookup"><span data-stu-id="456ca-371">Function</span></span>                                        | <span data-ttu-id="456ca-372">Значение</span><span class="sxs-lookup"><span data-stu-id="456ca-372">Value</span></span> |
| ----------------------------------------------- | - |
| <span data-ttu-id="456ca-373">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="456ca-373">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>    | <span data-ttu-id="456ca-374">1</span><span class="sxs-lookup"><span data-stu-id="456ca-374">1</span></span> |
| <span data-ttu-id="456ca-375">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="456ca-375">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>    | <span data-ttu-id="456ca-376">2</span><span class="sxs-lookup"><span data-stu-id="456ca-376">2</span></span> |
| <span data-ttu-id="456ca-377">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="456ca-377">UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>     | <span data-ttu-id="456ca-378">3</span><span class="sxs-lookup"><span data-stu-id="456ca-378">3</span></span> |
| <span data-ttu-id="456ca-379">UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="456ca-379">UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>         | <span data-ttu-id="456ca-380">4</span><span class="sxs-lookup"><span data-stu-id="456ca-380">4</span></span> |
| <span data-ttu-id="456ca-381">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="456ca-381">UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>     | <span data-ttu-id="456ca-382">5</span><span class="sxs-lookup"><span data-stu-id="456ca-382">5</span></span> |
| <span data-ttu-id="456ca-383">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="456ca-383">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span> | <span data-ttu-id="456ca-384">6</span><span class="sxs-lookup"><span data-stu-id="456ca-384">6</span></span> |
| <span data-ttu-id="456ca-385">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span><span class="sxs-lookup"><span data-stu-id="456ca-385">UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span></span>  | <span data-ttu-id="456ca-386">7</span><span class="sxs-lookup"><span data-stu-id="456ca-386">7</span></span> |

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_coding"></a><span data-ttu-id="456ca-387">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="456ca-387">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>

<span data-ttu-id="456ca-388">Выполнение IOCTL: настройка кодирования строк в интерфейсе CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="456ca-388">Perform IOCTL Set Line Coding on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="456ca-389">Прототип</span><span class="sxs-lookup"><span data-stu-id="456ca-389">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="456ca-390">Описание</span><span class="sxs-lookup"><span data-stu-id="456ca-390">Description</span></span>

<span data-ttu-id="456ca-391">Эта функция вызывается, когда приложению необходимо задать параметры кодирования строк.</span><span class="sxs-lookup"><span data-stu-id="456ca-391">This function is called when an application needs to Set the Line Coding parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="456ca-392">Параметры</span><span class="sxs-lookup"><span data-stu-id="456ca-392">Parameters</span></span>

- <span data-ttu-id="456ca-393">**cdc_acm**: указатель на экземпляр класса CDC.</span><span class="sxs-lookup"><span data-stu-id="456ca-393">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="456ca-394">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING.</span><span class="sxs-lookup"><span data-stu-id="456ca-394">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING</span></span>
- <span data-ttu-id="456ca-395">**parameter**: указатель на структуру параметров строки.</span><span class="sxs-lookup"><span data-stu-id="456ca-395">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="456ca-396">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="456ca-396">Return Value</span></span>

<span data-ttu-id="456ca-397">**UX_SUCCESS** (0x00) — операция успешно выполнена</span><span class="sxs-lookup"><span data-stu-id="456ca-397">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="456ca-398">Например, .</span><span class="sxs-lookup"><span data-stu-id="456ca-398">Example</span></span>

```c
/* Change the line coding values. */

line_coding.ux_slave_class_cdc_acm_line_coding_dter = 9600;
line_coding.ux_slave_class_cdc_acm_line_coding_stop_bit =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_STOP_BIT_15;

line_coding.ux_slave_class_cdc_acm_line_coding_parity =
    UX_HOST_CLASS_CDC_ACM_LINE_CODING_PARITY_EVEN;

line_coding.ux_slave_class_cdc_acm_line_coding_data_bits = 5;

status = _ux_slave_class_cdc_acm_ioctl(cdc_acm,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING, &line_coding);

if (status != UX_SUCCESS)
    break;
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_coding"></a><span data-ttu-id="456ca-399">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span><span class="sxs-lookup"><span data-stu-id="456ca-399">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING</span></span>

<span data-ttu-id="456ca-400">Выполнение IOCTL: получение кода строки для интерфейса CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="456ca-400">Perform IOCTL Get Line Coding on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="456ca-401">Прототип</span><span class="sxs-lookup"><span data-stu-id="456ca-401">Prototype</span></span>

```c
device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="456ca-402">Описание</span><span class="sxs-lookup"><span data-stu-id="456ca-402">Description</span></span>

<span data-ttu-id="456ca-403">Эта функция вызывается, когда приложению требуется получить параметры кодирования строки.</span><span class="sxs-lookup"><span data-stu-id="456ca-403">This function is called when an application needs to Get the Line Coding parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="456ca-404">Параметры</span><span class="sxs-lookup"><span data-stu-id="456ca-404">Parameters</span></span>

- <span data-ttu-id="456ca-405">**cdc_acm**: указатель на экземпляр класса CDC.</span><span class="sxs-lookup"><span data-stu-id="456ca-405">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="456ca-406">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING.</span><span class="sxs-lookup"><span data-stu-id="456ca-406">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING</span></span>
- <span data-ttu-id="456ca-407">**parameter**: указатель на структуру параметров строки.</span><span class="sxs-lookup"><span data-stu-id="456ca-407">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="456ca-408">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="456ca-408">Return Value</span></span>

- <span data-ttu-id="456ca-409">**UX_SUCCESS** (0x00) — операция успешно выполнена</span><span class="sxs-lookup"><span data-stu-id="456ca-409">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="456ca-410">Например, .</span><span class="sxs-lookup"><span data-stu-id="456ca-410">Example</span></span>

```c
/* This is to retrieve BAUD rate. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING, &line_coding);

/* Any error ? */
if (status == UX_SUCCESS)
{
    /* Decode BAUD rate. */
    switch (line_coding.ux_slave_class_cdc_acm_parameter_baudrate)
    {
        case 1200 :
            status = tx_demo_thread_slave_cdc_acm_response("1200", 4);
            break;
        case 2400 :
            status = tx_demo_thread_slave_cdc_acm_response("2400", 4);
            break;
        case 4800 :
            status = tx_demo_thread_slave_cdc_acm_response("4800", 4);
            break;
        case 9600 :
            status = tx_demo_thread_slave_cdc_acm_response("9600", 4);
            break;
        case 115200 :
            status = tx_demo_thread_slave_cdc_acm_response("115200", 6);
            break;
    }
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_state"></a><span data-ttu-id="456ca-411">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="456ca-411">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>

<span data-ttu-id="456ca-412">Выполнение IOCTL: получение состояния строки в интерфейсе CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="456ca-412">Perform IOCTL Get Line State on the CDC-ACM interface</span></span>

## <a name="prototype"></a><span data-ttu-id="456ca-413">Прототип</span><span class="sxs-lookup"><span data-stu-id="456ca-413">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="456ca-414">Описание</span><span class="sxs-lookup"><span data-stu-id="456ca-414">Description</span></span>

<span data-ttu-id="456ca-415">Эта функция вызывается, когда приложению требуется получить параметры состояния строки.</span><span class="sxs-lookup"><span data-stu-id="456ca-415">This function is called when an application needs to Get the Line State parameters.</span></span>

### <a name="parameters"></a><span data-ttu-id="456ca-416">Параметры</span><span class="sxs-lookup"><span data-stu-id="456ca-416">Parameters</span></span>

- <span data-ttu-id="456ca-417">**cdc_acm**: указатель на экземпляр класса CDC.</span><span class="sxs-lookup"><span data-stu-id="456ca-417">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="456ca-418">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE.</span><span class="sxs-lookup"><span data-stu-id="456ca-418">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE</span></span>
- <span data-ttu-id="456ca-419">**parameter**: указатель на структуру параметров строки.</span><span class="sxs-lookup"><span data-stu-id="456ca-419">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="456ca-420">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="456ca-420">Return Value</span></span>

- <span data-ttu-id="456ca-421">**UX_SUCCESS** (0x00) — операция успешно выполнена</span><span class="sxs-lookup"><span data-stu-id="456ca-421">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="456ca-422">Например, .</span><span class="sxs-lookup"><span data-stu-id="456ca-422">Example</span></span>

```c
/* This is to retrieve RTS state. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE, &line_state);

/* Any error ? */
if (status == UX_SUCCESS)
{
/* Check state. */
    if (line_state.ux_slave_class_cdc_acm_parameter_rts == UX_TRUE)
        /* State is ON. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS ON", 6);
    else
        /* State is OFF. */
        status = tx_demo_thread_slave_cdc_acm_response("RTS OFF", 7);
}
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_state"></a><span data-ttu-id="456ca-423">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span><span class="sxs-lookup"><span data-stu-id="456ca-423">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>

<span data-ttu-id="456ca-424">Выполнение IOCTL: задание состояния строки в интерфейсе CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="456ca-424">Perform IOCTL Set Line State on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="456ca-425">Прототип</span><span class="sxs-lookup"><span data-stu-id="456ca-425">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="456ca-426">Описание</span><span class="sxs-lookup"><span data-stu-id="456ca-426">Description</span></span>

<span data-ttu-id="456ca-427">Эта функция вызывается, когда приложению требуется получить параметры состояния строки.</span><span class="sxs-lookup"><span data-stu-id="456ca-427">This function is called when an application needs to Get the Line State parameters</span></span>

### <a name="parameters"></a><span data-ttu-id="456ca-428">Параметры</span><span class="sxs-lookup"><span data-stu-id="456ca-428">Parameters</span></span>

- <span data-ttu-id="456ca-429">**cdc_acm**: указатель на экземпляр класса CDC.</span><span class="sxs-lookup"><span data-stu-id="456ca-429">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="456ca-430">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE.</span><span class="sxs-lookup"><span data-stu-id="456ca-430">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE</span></span>
- <span data-ttu-id="456ca-431">**parameter**: указатель на структуру параметров строки.</span><span class="sxs-lookup"><span data-stu-id="456ca-431">**parameter**: Pointer to a line parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="456ca-432">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="456ca-432">Return Value</span></span>

- <span data-ttu-id="456ca-433">**UX_SUCCESS** (0x00) — операция успешно выполнена</span><span class="sxs-lookup"><span data-stu-id="456ca-433">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="456ca-434">Например, .</span><span class="sxs-lookup"><span data-stu-id="456ca-434">Example</span></span>

```c
/* This is to set RTS state. */

line_state.ux_slave_class_cdc_acm_parameter_rts = UX_TRUE;
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE, &line_state);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_abort_pipe"></a><span data-ttu-id="456ca-435">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span><span class="sxs-lookup"><span data-stu-id="456ca-435">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>

<span data-ttu-id="456ca-436">Выполнение IOCTL: прерывание канала в интерфейсе CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="456ca-436">Perform IOCTL ABORT PIPE on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="456ca-437">Прототип</span><span class="sxs-lookup"><span data-stu-id="456ca-437">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="456ca-438">Описание</span><span class="sxs-lookup"><span data-stu-id="456ca-438">Description</span></span>

<span data-ttu-id="456ca-439">Эта функция вызывается, когда приложению требуется прервать канал.</span><span class="sxs-lookup"><span data-stu-id="456ca-439">This function is called when an application needs to abort a pipe.</span></span> <span data-ttu-id="456ca-440">Например, чтобы прервать текущую операцию записи, в качестве параметра следует передать UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT.</span><span class="sxs-lookup"><span data-stu-id="456ca-440">For example, to abort an ongoing write, UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT should be passed as the parameter.</span></span>

### <a name="parameters"></a><span data-ttu-id="456ca-441">Параметры</span><span class="sxs-lookup"><span data-stu-id="456ca-441">Parameters</span></span>

- <span data-ttu-id="456ca-442">**cdc_acm**: указатель на экземпляр класса CDC.</span><span class="sxs-lookup"><span data-stu-id="456ca-442">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="456ca-443">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE.</span><span class="sxs-lookup"><span data-stu-id="456ca-443">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE</span></span>
- <span data-ttu-id="456ca-444">**parameter**: направление канала.</span><span class="sxs-lookup"><span data-stu-id="456ca-444">**parameter**: The pipe direction:</span></span>

```c
UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT 1

UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_RCV 2
```

### <a name="return-value"></a><span data-ttu-id="456ca-445">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="456ca-445">Return Value</span></span>

- <span data-ttu-id="456ca-446">**UX_SUCCESS** (0x00) — операция успешно выполнена</span><span class="sxs-lookup"><span data-stu-id="456ca-446">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="456ca-447">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) — недопустимое направление канала</span><span class="sxs-lookup"><span data-stu-id="456ca-447">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Invalid pipe direction.</span></span>

### <a name="example"></a><span data-ttu-id="456ca-448">Например, .</span><span class="sxs-lookup"><span data-stu-id="456ca-448">Example</span></span>

```c
/* This is to abort the Xmit pipe. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE,
    UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_start"></a><span data-ttu-id="456ca-449">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span><span class="sxs-lookup"><span data-stu-id="456ca-449">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span>

<span data-ttu-id="456ca-450">Выполнение IOCTL: запуск передачи в интерфейсе CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="456ca-450">Perform IOCTL Transmission Start on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="456ca-451">Прототип</span><span class="sxs-lookup"><span data-stu-id="456ca-451">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="456ca-452">Описание</span><span class="sxs-lookup"><span data-stu-id="456ca-452">Description</span></span>

<span data-ttu-id="456ca-453">Эта функция вызывается, когда приложению требуется использовать передачу с обратным вызовом.</span><span class="sxs-lookup"><span data-stu-id="456ca-453">This function is called when an application wants to use transmission with callback.</span></span>

### <a name="parameters"></a><span data-ttu-id="456ca-454">Параметры</span><span class="sxs-lookup"><span data-stu-id="456ca-454">Parameters</span></span>

- <span data-ttu-id="456ca-455">**cdc_acm**: указатель на экземпляр класса CDC.</span><span class="sxs-lookup"><span data-stu-id="456ca-455">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="456ca-456">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.</span><span class="sxs-lookup"><span data-stu-id="456ca-456">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START</span></span>
- <span data-ttu-id="456ca-457">**parameter**: указатель на структуру параметров запуска передачи.</span><span class="sxs-lookup"><span data-stu-id="456ca-457">**parameter**: Pointer to the Start Transmission parameter structure:</span></span>

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER_STRUCT
{
    UINT (*ux_device_class_cdc_acm_parameter_write_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, ULONG length);
    UINT (*ux_device_class_cdc_acm_parameter_read_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *data_pointer, ULONG length);
} UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER;
```

### <a name="return-value"></a><span data-ttu-id="456ca-458">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="456ca-458">Return Value</span></span>

- <span data-ttu-id="456ca-459">**UX_SUCCESS** (0x00) — операция успешно выполнена</span><span class="sxs-lookup"><span data-stu-id="456ca-459">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="456ca-460">**UX_ERROR** (0xFF) — передача уже запущена</span><span class="sxs-lookup"><span data-stu-id="456ca-460">**UX_ERROR** (0xFF) Transmission already started.</span></span>
- <span data-ttu-id="456ca-461">**UX_MEMORY_INSUFFICIENT** (0x12) — сбой выделения памяти</span><span class="sxs-lookup"><span data-stu-id="456ca-461">**UX_MEMORY_INSUFFICIENT** (0x12) A memory allocation failed.</span></span>

### <a name="example"></a><span data-ttu-id="456ca-462">Например, .</span><span class="sxs-lookup"><span data-stu-id="456ca-462">Example</span></span>

```c
/* Set the callback parameter. */

callback.ux_device_class_cdc_acm_parameter_write_callback
    = tx_demo_thread_slave_write_callback;

callback.ux_device_class_cdc_acm_parameter_read_callback
    = tx_demo_thread_slave_read_callback;

/* Program the start of transmission. */
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_stop"></a><span data-ttu-id="456ca-463">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span><span class="sxs-lookup"><span data-stu-id="456ca-463">ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP</span></span>

<span data-ttu-id="456ca-464">Выполнение IOCTL: остановка передачи в интерфейсе CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="456ca-464">Perform IOCTL Transmission Stop on the CDC-ACM interface</span></span>

### <a name="prototype"></a><span data-ttu-id="456ca-465">Прототип</span><span class="sxs-lookup"><span data-stu-id="456ca-465">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_ioctl( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="456ca-466">Описание</span><span class="sxs-lookup"><span data-stu-id="456ca-466">Description</span></span>

<span data-ttu-id="456ca-467">Эта функция вызывается, когда приложению требуется отключить передачу с помощью обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="456ca-467">This function is called when an application wants to stop using transmission with callback.</span></span>

### <a name="parameters"></a><span data-ttu-id="456ca-468">Параметры</span><span class="sxs-lookup"><span data-stu-id="456ca-468">Parameters</span></span>

- <span data-ttu-id="456ca-469">**cdc_acm**: указатель на экземпляр класса CDC.</span><span class="sxs-lookup"><span data-stu-id="456ca-469">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="456ca-470">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP.</span><span class="sxs-lookup"><span data-stu-id="456ca-470">**ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP</span></span>
- <span data-ttu-id="456ca-471">**parameter**: не используется.</span><span class="sxs-lookup"><span data-stu-id="456ca-471">**parameter**: Not used</span></span>

### <a name="return-value"></a><span data-ttu-id="456ca-472">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="456ca-472">Return Value</span></span>

- <span data-ttu-id="456ca-473">**UX_SUCCESS** (0x00) — операция успешно выполнена</span><span class="sxs-lookup"><span data-stu-id="456ca-473">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="456ca-474">**UX_ERROR** (0xFF) — нет текущих передач.</span><span class="sxs-lookup"><span data-stu-id="456ca-474">**UX_ERROR** (0xFF) No ongoing transmission.</span></span>

### <a name="example"></a><span data-ttu-id="456ca-475">Например, .</span><span class="sxs-lookup"><span data-stu-id="456ca-475">Example</span></span>

```c
/* Program the stop of transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP, UX_NULL);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_read"></a><span data-ttu-id="456ca-476">ux_device_class_cdc_acm_read</span><span class="sxs-lookup"><span data-stu-id="456ca-476">ux_device_class_cdc_acm_read</span></span>

<span data-ttu-id="456ca-477">Чтение из канала CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="456ca-477">Read from CDC-ACM pipe</span></span>

### <a name="prototype"></a><span data-ttu-id="456ca-478">Прототип</span><span class="sxs-lookup"><span data-stu-id="456ca-478">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_read( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="456ca-479">Описание</span><span class="sxs-lookup"><span data-stu-id="456ca-479">Description</span></span>

<span data-ttu-id="456ca-480">Эта функция вызывается, когда приложению требуется выполнить чтение из канала данных OUT (OUT — с узла, IN —с устройства).</span><span class="sxs-lookup"><span data-stu-id="456ca-480">This function is called when an application needs to read from the OUT data pipe (OUT from the host, IN from the device).</span></span> <span data-ttu-id="456ca-481">Он блокируется.</span><span class="sxs-lookup"><span data-stu-id="456ca-481">It is blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="456ca-482">Параметры</span><span class="sxs-lookup"><span data-stu-id="456ca-482">Parameters</span></span>

- <span data-ttu-id="456ca-483">**cdc_acm**: указатель на экземпляр класса CDC.</span><span class="sxs-lookup"><span data-stu-id="456ca-483">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="456ca-484">**buffer**: адрес буфера, где будут храниться данные.</span><span class="sxs-lookup"><span data-stu-id="456ca-484">**buffer**: Buffer address where data will be stored.</span></span>
- <span data-ttu-id="456ca-485">**requested_length**: максимально допустимая длина.</span><span class="sxs-lookup"><span data-stu-id="456ca-485">**requested_length**: The maximum length we expect.</span></span>
- <span data-ttu-id="456ca-486">**actual_length**: длина, возвращаемая в буфер.</span><span class="sxs-lookup"><span data-stu-id="456ca-486">**actual_length**: The length returned into the buffer.</span></span>

### <a name="return-value"></a><span data-ttu-id="456ca-487">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="456ca-487">Return Value</span></span>

- <span data-ttu-id="456ca-488">**UX_SUCCESS** (0x00) — операция успешно выполнена</span><span class="sxs-lookup"><span data-stu-id="456ca-488">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="456ca-489">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) — устройство больше не находится в настроенном состоянии</span><span class="sxs-lookup"><span data-stu-id="456ca-489">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="456ca-490">**UX_TRANSFER_NO_ANSWER** (0x22) — нет ответа от устройства</span><span class="sxs-lookup"><span data-stu-id="456ca-490">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="456ca-491">Возможно, устройство было отключено, пока ожидалась передача.</span><span class="sxs-lookup"><span data-stu-id="456ca-491">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="456ca-492">Например, .</span><span class="sxs-lookup"><span data-stu-id="456ca-492">Example</span></span>

```c
/* Read from the CDC class. */

status = ux_device_class_cdc_acm_read(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS) return;
```

### <a name="ux_device_class_cdc_acm_write"></a><span data-ttu-id="456ca-493">ux_device_class_cdc_acm_write</span><span class="sxs-lookup"><span data-stu-id="456ca-493">ux_device_class_cdc_acm_write</span></span>

<span data-ttu-id="456ca-494">Запись в канал CDC-ACM</span><span class="sxs-lookup"><span data-stu-id="456ca-494">Write to a CDC-ACM pipe</span></span>

### <a name="prototype"></a><span data-ttu-id="456ca-495">Прототип</span><span class="sxs-lookup"><span data-stu-id="456ca-495">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_write( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a><span data-ttu-id="456ca-496">Описание</span><span class="sxs-lookup"><span data-stu-id="456ca-496">Description</span></span>

<span data-ttu-id="456ca-497">Эта функция вызывается, когда приложению требуется выполнить запись в канал данных IN (IN — с узла, OUT — с устройства).</span><span class="sxs-lookup"><span data-stu-id="456ca-497">This function is called when an application needs to write to the IN data pipe (IN from the host, OUT from the device).</span></span> <span data-ttu-id="456ca-498">Он блокируется.</span><span class="sxs-lookup"><span data-stu-id="456ca-498">It is blocking.</span></span>

### <a name="parameters"></a><span data-ttu-id="456ca-499">Параметры</span><span class="sxs-lookup"><span data-stu-id="456ca-499">Parameters</span></span>

- <span data-ttu-id="456ca-500">**cdc_acm**: указатель на экземпляр класса CDC.</span><span class="sxs-lookup"><span data-stu-id="456ca-500">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="456ca-501">**buffer**: адрес буфера, где хранятся данные.</span><span class="sxs-lookup"><span data-stu-id="456ca-501">**buffer**: Buffer address where data is stored.</span></span>
- <span data-ttu-id="456ca-502">**requested_length**: длина буфера для записи.</span><span class="sxs-lookup"><span data-stu-id="456ca-502">**requested_length**: The length of the buffer to write.</span></span>
- <span data-ttu-id="456ca-503">**actual_length**: длина, возвращенная в буфер после выполнения операции записи.</span><span class="sxs-lookup"><span data-stu-id="456ca-503">**actual_length**: The length returned into the buffer after write is performed.</span></span>

### <a name="return-value"></a><span data-ttu-id="456ca-504">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="456ca-504">Return Value</span></span>
- <span data-ttu-id="456ca-505">**UX_SUCCESS** (0x00) — операция успешно выполнена</span><span class="sxs-lookup"><span data-stu-id="456ca-505">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="456ca-506">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) — устройство больше не находится в настроенном состоянии</span><span class="sxs-lookup"><span data-stu-id="456ca-506">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="456ca-507">**UX_TRANSFER_NO_ANSWER** (0x22) — нет ответа от устройства</span><span class="sxs-lookup"><span data-stu-id="456ca-507">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="456ca-508">Возможно, устройство было отключено, пока ожидалась передача.</span><span class="sxs-lookup"><span data-stu-id="456ca-508">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="456ca-509">Например, .</span><span class="sxs-lookup"><span data-stu-id="456ca-509">Example</span></span>

```c
/* Write to the CDC class bulk in pipe. */

status = ux_device_class_cdc_acm_write(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS)
    return;
```

### <a name="ux_device_class_cdc_acm_write_with_callback"></a><span data-ttu-id="456ca-510">ux_device_class_cdc_acm_write_with_callback</span><span class="sxs-lookup"><span data-stu-id="456ca-510">ux_device_class_cdc_acm_write_with_callback</span></span>

<span data-ttu-id="456ca-511">Запись в канал CDC-ACM с обратным вызовом</span><span class="sxs-lookup"><span data-stu-id="456ca-511">Writing to a CDC-ACM pipe with callback</span></span>

### <a name="prototype"></a><span data-ttu-id="456ca-512">Прототип</span><span class="sxs-lookup"><span data-stu-id="456ca-512">Prototype</span></span>

```c
UINT ux_device_class_cdc_acm_write_with_callback( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length);
```

### <a name="description"></a><span data-ttu-id="456ca-513">Описание</span><span class="sxs-lookup"><span data-stu-id="456ca-513">Description</span></span>

<span data-ttu-id="456ca-514">Эта функция вызывается, когда приложению требуется выполнить запись в канал данных IN (IN — с узла, OUT — с устройства).</span><span class="sxs-lookup"><span data-stu-id="456ca-514">This function is called when an application needs to write to the IN data pipe (IN from the host, OUT from the device).</span></span> <span data-ttu-id="456ca-515">Эта функция не блокируется, и она выполняется через обратный вызов, заданный в UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.</span><span class="sxs-lookup"><span data-stu-id="456ca-515">This function is non-blocking and the completion will be done through a callback set in UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.</span></span>

### <a name="parameters"></a><span data-ttu-id="456ca-516">Параметры</span><span class="sxs-lookup"><span data-stu-id="456ca-516">Parameters</span></span>

- <span data-ttu-id="456ca-517">**cdc_acm**: указатель на экземпляр класса CDC.</span><span class="sxs-lookup"><span data-stu-id="456ca-517">**cdc_acm**: Pointer to the cdc class instance.</span></span>
- <span data-ttu-id="456ca-518">**buffer**: адрес буфера, где хранятся данные.</span><span class="sxs-lookup"><span data-stu-id="456ca-518">**buffer**: Buffer address where data is stored.</span></span>
- <span data-ttu-id="456ca-519">**requested_length**: длина буфера для записи.</span><span class="sxs-lookup"><span data-stu-id="456ca-519">**requested_length**: The length of the buffer to write.</span></span>
- <span data-ttu-id="456ca-520">**actual_length**: длина, возвращенная в буфер после выполнения операции записи.</span><span class="sxs-lookup"><span data-stu-id="456ca-520">**actual_length**: The length returned into the buffer after write is performed</span></span>

### <a name="return-value"></a><span data-ttu-id="456ca-521">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="456ca-521">Return Value</span></span>

- <span data-ttu-id="456ca-522">**UX_SUCCESS** (0x00) — операция успешно выполнена</span><span class="sxs-lookup"><span data-stu-id="456ca-522">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="456ca-523">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) — устройство больше не находится в настроенном состоянии</span><span class="sxs-lookup"><span data-stu-id="456ca-523">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) Device is no longer in the configured state.</span></span>
- <span data-ttu-id="456ca-524">**UX_TRANSFER_NO_ANSWER** (0x22) — нет ответа от устройства</span><span class="sxs-lookup"><span data-stu-id="456ca-524">**UX_TRANSFER_NO_ANSWER** (0x22) No answer from device.</span></span> <span data-ttu-id="456ca-525">Возможно, устройство было отключено, пока ожидалась передача.</span><span class="sxs-lookup"><span data-stu-id="456ca-525">The device was probably disconnected while the transfer was pending.</span></span>

### <a name="example"></a><span data-ttu-id="456ca-526">Например, .</span><span class="sxs-lookup"><span data-stu-id="456ca-526">Example</span></span>

```c
/* Write to the CDC class bulk in pipe non blocking mode. */
status = ux_device_class_cdc_acm_write_with_callback(cdc, buffer, UX_DEMO_BUFFER_SIZE);

if(status != UX_SUCCESS)
    return;
```

### <a name="usb-device-cdc-ecm-class"></a><span data-ttu-id="456ca-527">Класс CDC-ECM USB-устройства</span><span class="sxs-lookup"><span data-stu-id="456ca-527">USB Device CDC-ECM Class</span></span>

<span data-ttu-id="456ca-528">Класс CDC-ECM USB-устройства позволяет хост-системе USB обмениваться данными с устройством как с устройством Ethernet.</span><span class="sxs-lookup"><span data-stu-id="456ca-528">The USB device CDC-ECM class allows for a USB host system to communicate with the device as a ethernet device.</span></span> <span data-ttu-id="456ca-529">Этот класс основан на стандарте USB и является подмножеством стандарта CDC.</span><span class="sxs-lookup"><span data-stu-id="456ca-529">This class is based on the USB standard and is a subset of the CDC standard.</span></span>

<span data-ttu-id="456ca-530">В стеке устройств необходимо объявить совместимую с CDC-ACM платформу устройств.</span><span class="sxs-lookup"><span data-stu-id="456ca-530">A CDC-ACM compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="456ca-531">Ниже приведен пример этого.</span><span class="sxs-lookup"><span data-stu-id="456ca-531">An example is found here below.</span></span>

```c
unsigned char device_framework_full_speed[] = {

    /* Device descriptor 18 bytes
    0x02 bDeviceClass: CDC_ECM class code
    0x06 bDeviceSubclass: CDC_ECM class sub code
    0x00 bDeviceProtocol: CDC_ECM Device protocol
    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    0x3939 idVendor: Azure RTOS test.
    */
    
    0x12, 0x01, 0x10, 0x01,
    0x02, 0x00, 0x00, 0x08,
    0x39, 0x39, 0x08, 0x08, 0x00, 0x01, 0x01, 0x02, 03,0x01,
    
    /* Configuration 1 descriptor 9 bytes. */
    0x09, 0x02, 0x58, 0x00,0x02, 0x01, 0x00,0x40, 0x00,
    
    /* Interface association descriptor. 8 bytes. */
    
    0x08, 0x0b, 0x00, 0x02, 0x02, 0x06, 0x00, 0x00,
    
    /* Communication Class Interface Descriptor Requirement 9 bytes */
    0x09, 0x04, 0x00, 0x00,0x01,0x02, 0x06, 0x00, 0x00,
    
    /* Header Functional Descriptor 5 bytes */
    0x05, 0x24, 0x00, 0x10, 0x01,
    
    /* ECM Functional Descriptor 13 bytes */
    0x0D, 0x24, 0x0F, 0x04,0x00, 0x00, 0x00, 0x00, 0xEA, 0x05, 0x00,
    0x00,0x00,
    
    /* Union Functional Descriptor 5 bytes */
    0x05, 0x24, 0x06, 0x00,0x01,
    
    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x83, 0x03, 0x08, 0x00, 0x08,
    
    /* Data Class Interface Descriptor Alternate Setting 0, 0 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x00, 0x00, 0x0A, 0x00, 0x00, 0x00,
    
    /* Data Class Interface Descriptor Alternate Setting 1, 2 endpoints. 9 bytes */
    0x09, 0x04, 0x01, 0x01, 0x02, 0x0A, 0x00, 0x00,0x00,
    
    /* First alternate setting Endpoint 1 descriptor 7 bytes */
    0x07, 0x05, 0x02, 0x02, 0x40, 0x00, 0x00,
    
    /* Endpoint 2 descriptor 7 bytes */
    0x07, 0x05, 0x81, 0x02, 0x40, 0x00,0x00

};
```

<span data-ttu-id="456ca-532">Класс CDC-ECM использует подход, близко схожий с подходом на основе дескриптора устройства CDC-ACM, а также требует наличия дескриптора IAD.</span><span class="sxs-lookup"><span data-stu-id="456ca-532">The CDC-ECM class uses a very similar device descriptor approach to the CDC-ACM and also requires an IAD descriptor.</span></span> <span data-ttu-id="456ca-533">Определение см. в описании класса CDC-ACM.</span><span class="sxs-lookup"><span data-stu-id="456ca-533">See the CDC-ACM class for definition.</span></span>

<span data-ttu-id="456ca-534">Помимо обычной платформы устройств, CDC-ECM требует специальных дескрипторов строк.</span><span class="sxs-lookup"><span data-stu-id="456ca-534">In addition to the regular device framework, the CDC-ECM requires special string descriptors.</span></span> <span data-ttu-id="456ca-535">Ниже приведен пример кода.</span><span class="sxs-lookup"><span data-stu-id="456ca-535">An example is given below.</span></span>

```c
unsigned char string_framework[] = {
    /* Manufacturer string descriptor: Index 1 - "Azure RTOS" */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,
    
    /* Product string descriptor: Index 2 - "EL CDCECM Device" */
    0x09, 0x04, 0x02, 0x10,
    0x45, 0x4c, 0x20, 0x43, 0x44, 0x43, 0x45, 0x43,
    0x4d, 0x20, 0x44, 0x65, 0x76, 0x69, 0x63, 0x64,
    
    /* Serial Number string descriptor: Index 3 - "0001" */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31,
    
    /* MAC Address string descriptor: Index 4 - "001E5841B879" */
    0x09, 0x04, 0x04, 0x0C,
    0x30, 0x30, 0x31, 0x45, 0x35, 0x38,
    0x34, 0x31, 0x42, 0x38, 0x37, 0x39

};
```

<span data-ttu-id="456ca-536">Дескриптор строки MAC-адреса используется классом CDC ECM для ответа на запросы к узлу в соответствии с MAC-адресом устройства, отвечающего по протоколу TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="456ca-536">The MAC address string descriptor is used by the CDC-ECM class to reply to the host queries as to what MAC address the device is answering to at the TCP/IP protocol.</span></span> <span data-ttu-id="456ca-537">Его можно задать в соответствии с выбранным устройством, однако его необходимо определить здесь.</span><span class="sxs-lookup"><span data-stu-id="456ca-537">It can be set to the device choice but must be defined here.</span></span>

<span data-ttu-id="456ca-538">Инициализация класса CDC-ECM выполняется следующим образом.</span><span class="sxs-lookup"><span data-stu-id="456ca-538">The initialization of the CDC-ECM class is as follows.</span></span>

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_activate = UX_NULL;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_instance_deactivate = UX_NULL;

/* Define a NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[0] = 0x00;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[1] = 0x1e;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[2] = 0x58;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[3] = 0x41;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[4] = 0xb8;
cdc_ecm_parameter.ux_slave_class_cdc_ecm_parameter_remote_node_id[5] = 0x79;

/* Initialize the device cdc_ecm class. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_ecm_name,
    ux_device_class_cdc_ecm_entry, 1,0,&cdc_ecm_parameter);
```

<span data-ttu-id="456ca-539">Инициализация этого класса ожидает один и тот же обратный вызов функции для активации и отключения, однако здесь в качестве упражнения задано значение NULL, поэтому обратный вызов не выполняется.</span><span class="sxs-lookup"><span data-stu-id="456ca-539">The initialization of this class expects the same function callback for activation and deactivation, although here as an exercise they are set to NULL so that no callback is performed.</span></span>

<span data-ttu-id="456ca-540">Следующие параметры предназначены для определения идентификаторов узлов.</span><span class="sxs-lookup"><span data-stu-id="456ca-540">The next parameters are for the definition of the node IDs.</span></span> <span data-ttu-id="456ca-541">Для репликации CDC-ECM требуется два узла: локальный узел и удаленный узел.</span><span class="sxs-lookup"><span data-stu-id="456ca-541">2 Nodes are necessary for the CDC-ECM, a local node and a remote node.</span></span> <span data-ttu-id="456ca-542">Локальный узел задает MAC-адрес устройства, а удаленный узел — MAC-адрес узла.</span><span class="sxs-lookup"><span data-stu-id="456ca-542">The local node specifies the MAC address of the device, while the remote node specifies the MAC address of the host.</span></span> <span data-ttu-id="456ca-543">Удаленный узел должен быть таким же, как тот, который объявлен в дескрипторе строки платформы устройства.</span><span class="sxs-lookup"><span data-stu-id="456ca-543">The remote node must be the same one as the one declared in the device framework string descriptor.</span></span>

<span data-ttu-id="456ca-544">Класс CDC-ECM содержит встроенные API для передачи данных обоими способами, однако они скрыты для приложения, поскольку пользовательское приложение взаимодействует с USB-устройством Ethernet через NetX.</span><span class="sxs-lookup"><span data-stu-id="456ca-544">The CDC-ECM class has built-in APIs for transferring data both ways but they are hidden to the application as the user application will communicate with the USB Ethernet device through NetX.</span></span>

<span data-ttu-id="456ca-545">Класс USBX CDC-ECM тесно привязан к сетевому стеку NetX ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="456ca-545">The USBX CDC-ECM class is closely tied to Azure RTOS NetX Network stack.</span></span> <span data-ttu-id="456ca-546">Приложение, использующее и NetX, и класс USBX CDC-ECM, активирует сетевой стек NetX обычным образом, но в дополнение необходимо активировать сетевой стек USB, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="456ca-546">An application using both NetX and USBX CDC-ECM class will activate the NetX network stack in its usual way but in addition needs to activate the USB network stack as follows.</span></span>

```c
/* Initialize the NetX system. */
nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

<span data-ttu-id="456ca-547">Сетевой стек USB следует активировать только один раз, и он не зависит от CDCECM, однако он необходим для любого класса USB, которому требуются службы NetX.</span><span class="sxs-lookup"><span data-stu-id="456ca-547">The USB network stack needs to be activated only once and is not specific to CDCECM but is required by any USB class that requires NetX services.</span></span>

<span data-ttu-id="456ca-548">Класс CDC-ECM распознается узлами MAC OS и Linux.</span><span class="sxs-lookup"><span data-stu-id="456ca-548">The CDC-ECM class will be recognized by MAC OS and Linux hosts.</span></span> <span data-ttu-id="456ca-549">Однако в Microsoft Windows отсутствует собственный драйвер для распознавания CDC-ECM.</span><span class="sxs-lookup"><span data-stu-id="456ca-549">But there is no driver supplied by Microsoft Windows to recognize CDC-ECM natively.</span></span> <span data-ttu-id="456ca-550">Для платформ Windows существуют некоторые коммерческие продукты, которые предоставляют собственный INF-файл.</span><span class="sxs-lookup"><span data-stu-id="456ca-550">Some commercial products do exist for Windows platforms and they supply their own .inf file.</span></span> <span data-ttu-id="456ca-551">Этот файл потребуется изменить так же, как шаблон CDC-ACM INF, чтобы он соответствовал идентификатору PID/VID сетевого USB-устройства.</span><span class="sxs-lookup"><span data-stu-id="456ca-551">This file will need to be modified the same way as the CDC-ACM inf template to match the PID/VID of the USB network device.</span></span>

## <a name="usb-device-hid-class"></a><span data-ttu-id="456ca-552">Класс HID USB-устройства</span><span class="sxs-lookup"><span data-stu-id="456ca-552">USB Device HID Class</span></span>

<span data-ttu-id="456ca-553">Класс HID USB-устройства позволяет хост-системе USB подключаться к HID-устройству с конкретными возможностями клиента HID.</span><span class="sxs-lookup"><span data-stu-id="456ca-553">The USB device HID class allows for a USB host system to connect to a HID device with specific HID client capabilities.</span></span>

<span data-ttu-id="456ca-554">Класс USBX HID довольно прост в сравнении с узлом.</span><span class="sxs-lookup"><span data-stu-id="456ca-554">USBX HID device class is relatively simple compared to the host side.</span></span> <span data-ttu-id="456ca-555">Он тесно связан с поведением устройства и его дескриптором HID.</span><span class="sxs-lookup"><span data-stu-id="456ca-555">It is closely tied to the behavior of the device and its HID descriptor.</span></span>

<span data-ttu-id="456ca-556">Любой клиент HID сначала должен определить платформу HID-устройства, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="456ca-556">Any HID client requires first to define a HID device framework as the example below.</span></span>

```c
UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0x81, 0x0A, 0x01, 0x01, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x22, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x01, 0x03, 0x00, 0x00, 0x00,

    /* HID descriptor */
    0x09, 0x21, 0x10, 0x01, 0x21, 0x01, 0x22, 0x3f, 0x00,

    /* Endpoint descriptor (Interrupt) */
    0x07, 0x05, 0x81, 0x03, 0x08, 0x00, 0x08

};
```

<span data-ttu-id="456ca-557">Платформа HID содержит дескриптор интерфейса, описывающий класс HID и подкласс HID-устройства.</span><span class="sxs-lookup"><span data-stu-id="456ca-557">The HID framework contains an interface descriptor that describes the HID class and the HID device subclass.</span></span> <span data-ttu-id="456ca-558">Интерфейс HID может быть отдельным классом или частью составного устройства.</span><span class="sxs-lookup"><span data-stu-id="456ca-558">The HID interface can be a standalone class or part of a composite device.</span></span>

<span data-ttu-id="456ca-559">В настоящее время класс USBX HID не поддерживает несколько идентификаторов отчетов, поскольку большинству приложений требуется только один идентификатор (нулевой идентификатор).</span><span class="sxs-lookup"><span data-stu-id="456ca-559">Currently, the USBX HID class does not support multiple report IDs, as most applications only require one ID (ID zero).</span></span> <span data-ttu-id="456ca-560">Если вам требуется использовать несколько идентификаторов отчетов, свяжитесь с нами.</span><span class="sxs-lookup"><span data-stu-id="456ca-560">If multiple report IDs is a feature you are interested in, please contact us.</span></span>

<span data-ttu-id="456ca-561">Инициализация класса HID осуществляется следующим образом. В качестве примера используется USB-клавиатура.</span><span class="sxs-lookup"><span data-stu-id="456ca-561">The initialization of the HID class is as follow, using a USB keyboard as an example.</span></span>

```c
/* Initialize the hid class parameters for a keyboard. */
hid_parameter.ux_device_class_hid_parameter_report_address = hid_keyboard_report;
hid_parameter.ux_device_class_hid_parameter_report_length = HID_KEYBOARD_REPORT_LENGTH;
hid_parameter.ux_device_class_hid_parameter_callback = tx_demo_thread_hid_callback;
hid_parameter.ux_device_class_hid_parameter_report_id = 0;

/* Initialize the device hid class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_hid_name,
    ux_device_class_hid_entry, 1,0,(VOID *)&hid_parameter);
if (status!=UX_SUCCESS)
    return;
```

<span data-ttu-id="456ca-562">Приложению необходимо передать в класс HID дескриптор отчета HID и его длину.</span><span class="sxs-lookup"><span data-stu-id="456ca-562">The application needs to pass to the HID class a HID report descriptor and its length.</span></span> <span data-ttu-id="456ca-563">Дескриптор отчета представляет собой коллекцию элементов, описывающих устройство.</span><span class="sxs-lookup"><span data-stu-id="456ca-563">The report descriptor is a collection of items that describe the device.</span></span> <span data-ttu-id="456ca-564">Дополнительные сведения о грамматике HID см. в спецификации класса HID USB.</span><span class="sxs-lookup"><span data-stu-id="456ca-564">For more information on the HID grammar refer to the HID USB class specification.</span></span>

<span data-ttu-id="456ca-565">Помимо дескриптора отчета, приложение передает обратный вызов при возникновении события HID.</span><span class="sxs-lookup"><span data-stu-id="456ca-565">In addition to the report descriptor, the application passes a call back when a HID event happens.</span></span>

<span data-ttu-id="456ca-566">Класс USBX HID поддерживает следующие стандартные команды HID от узла.</span><span class="sxs-lookup"><span data-stu-id="456ca-566">The USBX HID class supports the following standard HID commands from the host.</span></span>

| <span data-ttu-id="456ca-567">Имя команды</span><span class="sxs-lookup"><span data-stu-id="456ca-567">Command name</span></span>                             | <span data-ttu-id="456ca-568">Значение</span><span class="sxs-lookup"><span data-stu-id="456ca-568">Value</span></span> | <span data-ttu-id="456ca-569">Описание</span><span class="sxs-lookup"><span data-stu-id="456ca-569">Description</span></span>                                      |
| ---------------------------------------- | ----- | ------------------------------------------------ |
| <span data-ttu-id="456ca-570">UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT</span><span class="sxs-lookup"><span data-stu-id="456ca-570">UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT</span></span>   | <span data-ttu-id="456ca-571">0x01</span><span class="sxs-lookup"><span data-stu-id="456ca-571">0x01</span></span>  | <span data-ttu-id="456ca-572">Получение отчета от устройства</span><span class="sxs-lookup"><span data-stu-id="456ca-572">Get a report from the device</span></span>                     |
| <span data-ttu-id="456ca-573">UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE</span><span class="sxs-lookup"><span data-stu-id="456ca-573">UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE</span></span>     | <span data-ttu-id="456ca-574">0x02</span><span class="sxs-lookup"><span data-stu-id="456ca-574">0x02</span></span>  | <span data-ttu-id="456ca-575">Получение частоты простоя конечной точки прерывания</span><span class="sxs-lookup"><span data-stu-id="456ca-575">Get the idle frequency of the interrupt endpoint</span></span> |
| <span data-ttu-id="456ca-576">UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="456ca-576">UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL</span></span> | <span data-ttu-id="456ca-577">0x03</span><span class="sxs-lookup"><span data-stu-id="456ca-577">0x03</span></span>  | <span data-ttu-id="456ca-578">Получение протокола, выполняющегося на устройстве</span><span class="sxs-lookup"><span data-stu-id="456ca-578">Get the protocol running on the device</span></span>           |
| <span data-ttu-id="456ca-579">UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT</span><span class="sxs-lookup"><span data-stu-id="456ca-579">UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT</span></span>   | <span data-ttu-id="456ca-580">0x09</span><span class="sxs-lookup"><span data-stu-id="456ca-580">0x09</span></span>  | <span data-ttu-id="456ca-581">Задание отчета для устройства</span><span class="sxs-lookup"><span data-stu-id="456ca-581">Set a report to the device</span></span>                       |
| <span data-ttu-id="456ca-582">UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE</span><span class="sxs-lookup"><span data-stu-id="456ca-582">UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE</span></span>     | <span data-ttu-id="456ca-583">0x0a</span><span class="sxs-lookup"><span data-stu-id="456ca-583">0x0a</span></span>  | <span data-ttu-id="456ca-584">Задание частоты простоя конечной точки прерывания</span><span class="sxs-lookup"><span data-stu-id="456ca-584">Set the idle frequency of the interrupt endpoint</span></span> |
| <span data-ttu-id="456ca-585">UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="456ca-585">UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL</span></span> | <span data-ttu-id="456ca-586">0x0b</span><span class="sxs-lookup"><span data-stu-id="456ca-586">0x0b</span></span>  | <span data-ttu-id="456ca-587">Получение протокола, выполняющегося на устройстве</span><span class="sxs-lookup"><span data-stu-id="456ca-587">Get the protocol running on the device</span></span>           |

<span data-ttu-id="456ca-588">Получение и задание отчета являются наиболее часто используемыми командами HID для обмена данными между узлом и устройством.</span><span class="sxs-lookup"><span data-stu-id="456ca-588">The Get and Set report are the most commonly used commands by HID to transfer data back and forth between the host and the device.</span></span> <span data-ttu-id="456ca-589">Чаще всего узел отправляет данные в конечную точку управления, но может получать данные либо в конечной точке прерывания, либо с помощью команды GET_REPORT для получения данных в конечной точке управления.</span><span class="sxs-lookup"><span data-stu-id="456ca-589">Most commonly the host sends data on the control endpoint but can receive data either on the interrupt endpoint or by issuing a GET_REPORT command to fetch the data on the control endpoint.</span></span>

<span data-ttu-id="456ca-590">Класс HID может передавать данные обратно на узел в конечной точке прерывания с помощью функции ux_device_class_hid_event_set.</span><span class="sxs-lookup"><span data-stu-id="456ca-590">The HID class can send data back to the host on the interrupt endpoint by using the ux_device_class_hid_event_set function.</span></span>

### <a name="ux_device_class_hid_event_set"></a><span data-ttu-id="456ca-591">ux_device_class_hid_event_set</span><span class="sxs-lookup"><span data-stu-id="456ca-591">ux_device_class_hid_event_set</span></span>

<span data-ttu-id="456ca-592">Задание события для класса HID</span><span class="sxs-lookup"><span data-stu-id="456ca-592">Setting an event to the HID class</span></span>

### <a name="prototype"></a><span data-ttu-id="456ca-593">Прототип</span><span class="sxs-lookup"><span data-stu-id="456ca-593">Prototype</span></span>

```c
UINT ux_device_class_hid_event_set( 
    UX_SLAVE_CLASS_HID *hid,
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a><span data-ttu-id="456ca-594">Описание</span><span class="sxs-lookup"><span data-stu-id="456ca-594">Description</span></span>

<span data-ttu-id="456ca-595">Эта функция вызывается, когда приложению требуется отправить событие HID обратно на узел.</span><span class="sxs-lookup"><span data-stu-id="456ca-595">This function is called when an application needs to send a HID event back to the host.</span></span> <span data-ttu-id="456ca-596">Функция не блокируется, она просто помещает отчет в циклическую очередь и возвращает его в приложение.</span><span class="sxs-lookup"><span data-stu-id="456ca-596">The function is not blocking, it merely puts the report into a circular queue and returns to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="456ca-597">Параметры</span><span class="sxs-lookup"><span data-stu-id="456ca-597">Parameters</span></span>

- <span data-ttu-id="456ca-598">**hid**: указатель на экземпляр класса HID.</span><span class="sxs-lookup"><span data-stu-id="456ca-598">**hid**: Pointer to the hid class instance.</span></span>
- <span data-ttu-id="456ca-599">**hid_event**: указатель на структуру события HID.</span><span class="sxs-lookup"><span data-stu-id="456ca-599">**hid_event**: Pointer to structure of the hid event.</span></span>

### <a name="return-value"></a><span data-ttu-id="456ca-600">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="456ca-600">Return Value</span></span>

- <span data-ttu-id="456ca-601">**UX_SUCCESS** (0x00) — операция успешно выполнена</span><span class="sxs-lookup"><span data-stu-id="456ca-601">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="456ca-602">**UX_ERROR** (0xFF) — ошибка ввиду отсутствия пространства в циклической очереди</span><span class="sxs-lookup"><span data-stu-id="456ca-602">**UX_ERROR** (0xFF) Error no space available in circular queue.</span></span>

### <a name="example"></a><span data-ttu-id="456ca-603">Например, .</span><span class="sxs-lookup"><span data-stu-id="456ca-603">Example</span></span>

```c
/* Insert a key into the keyboard event. Length is fixed to 8. */
hid_event.ux_device_class_hid_event_length = 8;

/* First byte is a modifier byte. */
hid_event.ux_device_class_hid_event_buffer[0] = 0;

/* Second byte is reserved. */
hid_event.ux_device_class_hid_event_buffer[1] = 0;

/* The 6 next bytes are keys. We only have one key here. */
hid_event.ux_device_class_hid_event_buffer[2] = key;

/* Set the keyboard event. */
ux_device_class_hid_event_set(hid, &hid_event);
```

<span data-ttu-id="456ca-604">Обратный вызов, определенный при инициализации класса HID, выполняет действие, противоположное отправке события.</span><span class="sxs-lookup"><span data-stu-id="456ca-604">The callback defined at the initialization of the HID class performs the opposite of sending an event.</span></span> <span data-ttu-id="456ca-605">Он получает в качестве входных данных событие, отправленное узлом.</span><span class="sxs-lookup"><span data-stu-id="456ca-605">It gets as input the event sent by the host.</span></span> <span data-ttu-id="456ca-606">Прототип обратного вызова выглядит следующим образом.</span><span class="sxs-lookup"><span data-stu-id="456ca-606">The prototype of the callback is as follows.</span></span>

### <a name="hid_callback"></a><span data-ttu-id="456ca-607">hid_callback</span><span class="sxs-lookup"><span data-stu-id="456ca-607">hid_callback</span></span>

<span data-ttu-id="456ca-608">Получение события из класса HID</span><span class="sxs-lookup"><span data-stu-id="456ca-608">Getting an event from the HID class</span></span>

### <a name="prototype"></a><span data-ttu-id="456ca-609">Прототип</span><span class="sxs-lookup"><span data-stu-id="456ca-609">Prototype</span></span>

```c
UINT hid_callback(
    UX_SLAVE_CLASS_HID *hid, 
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a><span data-ttu-id="456ca-610">Описание</span><span class="sxs-lookup"><span data-stu-id="456ca-610">Description</span></span>

<span data-ttu-id="456ca-611">Эта функция вызывается, когда узел отправляет отчет HID в приложение.</span><span class="sxs-lookup"><span data-stu-id="456ca-611">This function is called when the host sends a HID report to the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="456ca-612">Параметры</span><span class="sxs-lookup"><span data-stu-id="456ca-612">Parameters</span></span>

- <span data-ttu-id="456ca-613">**hid**: указатель на экземпляр класса HID.</span><span class="sxs-lookup"><span data-stu-id="456ca-613">**hid**: Pointer to the hid class instance.</span></span>
- <span data-ttu-id="456ca-614">**hid_event**: указатель на структуру события HID.</span><span class="sxs-lookup"><span data-stu-id="456ca-614">**hid_event**: Pointer to structure of the hid event.</span></span>

### <a name="example"></a><span data-ttu-id="456ca-615">Например, .</span><span class="sxs-lookup"><span data-stu-id="456ca-615">Example</span></span>

<span data-ttu-id="456ca-616">В следующем примере показано, как интерпретировать событие для клавиатуры HID.</span><span class="sxs-lookup"><span data-stu-id="456ca-616">The following example shows how to interpret an event for a HID keyboard:</span></span>

```c
UINT tx_demo_thread_hid_callback(UX_SLAVE_CLASS_HID *hid, UX_SLAVE_CLASS_HID_EVENT *hid_event
{
/* There was an event. Analyze it. Is it NUM LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_NUM_LOCK_MASK)
    /* Set the Num lock flag. */
    num_lock_flag = UX_TRUE;
else
    /* Reset the Num lock flag. */
    num_lock_flag = UX_FALSE;

/* There was an event. Analyze it. Is it CAPS LOCK ? */

if (hid_event -\ux_device_class_hid_event_buffer[0] & HID_CAPS_LOCK_MASK)
    /* Set the Caps lock flag. */
    caps_lock_flag = UX_TRUE;
else
    /* Reset the Caps lock flag. */
    caps_lock_flag = UX_FALSE;
}
```
