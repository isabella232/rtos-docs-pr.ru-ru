---
title: Глава 2. Сведения о классах устройств USBX
description: Класс RNDIS USB-устройства позволяет хост-системе USB обмениваться данными с устройством в качестве устройства Ethernet. Этот класс основан на защищаемой реализации Майкрософт и относится только к платформам Windows.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 035492644a911eba3b1c62a79572bc7d4c55f6dd
ms.sourcegitcommit: 1aeca2f91960856d8cc24fef65f909639e527599
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/31/2021
ms.locfileid: "106082223"
---
# <a name="chapter-2---usbx-device-class-considerations"></a><span data-ttu-id="dcac2-104">Глава 2. Сведения о классах устройств USBX</span><span class="sxs-lookup"><span data-stu-id="dcac2-104">Chapter 2 - USBX Device Class Considerations</span></span>

## <a name="usb-device-rndis-class"></a><span data-ttu-id="dcac2-105">Класс RNDIS USB-устройства</span><span class="sxs-lookup"><span data-stu-id="dcac2-105">USB Device RNDIS Class</span></span>

<span data-ttu-id="dcac2-106">Класс RNDIS USB-устройства позволяет хост-системе USB обмениваться данными с устройством в качестве устройства Ethernet.</span><span class="sxs-lookup"><span data-stu-id="dcac2-106">The USB device RNDIS class allows for a USB host system to communicate with the device as a ethernet device.</span></span> <span data-ttu-id="dcac2-107">Этот класс основан на защищаемой реализации Майкрософт и относится только к платформам Windows.</span><span class="sxs-lookup"><span data-stu-id="dcac2-107">This class is based on the Microsoft proprietary implementation and is specific to Windows platforms.</span></span>

<span data-ttu-id="dcac2-108">В стеке устройств необходимо объявить совместимую с RNDIS платформу устройств.</span><span class="sxs-lookup"><span data-stu-id="dcac2-108">A RNDIS compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="dcac2-109">Пример представлен ниже.</span><span class="sxs-lookup"><span data-stu-id="dcac2-109">An example is found below.</span></span>

```C
unsigned char device_framework_full_speed[] = {
    /* VID: 0x04b4
    PID: 0x1127
    */

    /* Device Descriptor */
    0x12, /* bLength */
    0x01, /* bDescriptorType */
    0x10, 0x01, /* bcdUSB */
    0x02, /* bDeviceClass - CDC */
    0x00, /* bDeviceSubClass */
    0x00, /* bDeviceProtocol */
    0x40, /* bMaxPacketSize0 */
    0xb4, 0x04, /* idVendor */
    0x27, 0x11, /* idProduct */
    0x00, 0x01, /* bcdDevice */
    0x01, /* iManufacturer */
    0x02, /* iProduct */
    0x03, /* iSerialNumber */
    0x01, /* bNumConfigurations */

    /* Configuration Descriptor */
    0x09, /* bLength */
    0x02, /* bDescriptorType */
    0x38, 0x00, /* wTotalLength */
    0x02, /* bNumInterfaces */
    0x01, /* bConfigurationValue */
    0x00, /* iConfiguration */
    0x40, /* bmAttributes - Self-powered */
    0x00, /* bMaxPower */

    /* Interface Association Descriptor */
    0x08, /* bLength */
    0x0b, /* bDescriptorType */
    0x00, /* bFirstInterface */
    0x02, /* bInterfaceCount */
    0x02, /* bFunctionClass - CDC - Communication */
    0xff, /* bFunctionSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bFunctionProtocol - No class specific protocol required */
    0x00, /* iFunction */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x00, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x01, /* bNumEndpoints */
    0x02, /* bInterfaceClass - CDC - Communication */
    0xff, /* bInterfaceSubClass - Vendor Defined – In this case, RNDIS */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x83, /* bEndpointAddress */
    0x03, /* bmAttributes - Interrupt */
    0x08, 0x00, /* wMaxPacketSize */
    0xff, /* bInterval */

    /* Interface Descriptor */
    0x09, /* bLength */
    0x04, /* bDescriptorType */
    0x01, /* bInterfaceNumber */
    0x00, /* bAlternateSetting */
    0x02, /* bNumEndpoints */
    0x0a, /* bInterfaceClass - CDC - Data */
    0x00, /* bInterfaceSubClass - Should be 0x00 */
    0x00, /* bInterfaceProtocol - No class specific protocol required */
    0x00, /* iInterface */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x02, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */

    /* Endpoint Descriptor */
    0x07, /* bLength */
    0x05, /* bDescriptorType */
    0x81, /* bEndpointAddress */
    0x02, /* bmAttributes - Bulk */
    0x40, 0x00, /* wMaxPacketSize */
    0x00, /* bInterval */
};
```

<span data-ttu-id="dcac2-110">Класс RNDIS использует подход, близко схожий с подходом на основе дескриптора устройства CDC-ACM и CDC-ECM, а также требует наличия дескриптора IAD.</span><span class="sxs-lookup"><span data-stu-id="dcac2-110">The RNDIS class uses a very similar device descriptor approach to the CDC-ACM and CDC-ECM and also requires a IAD descriptor.</span></span> <span data-ttu-id="dcac2-111">Определение и требования для дескриптора устройства см. в описании класса CDC-ACM.</span><span class="sxs-lookup"><span data-stu-id="dcac2-111">See the CDC-ACM class for definition and requirements for the device descriptor.</span></span>

<span data-ttu-id="dcac2-112">Активация класса RNDIS выполняется следующим образом.</span><span class="sxs-lookup"><span data-stu-id="dcac2-112">The activation of the RNDIS class is as follows.</span></span>

```C
/* Set the parameters for callback when insertion/extraction of a CDC device. Set to NULL.*/

parameter.ux_slave_class_rndis_instance_activate = UX_NULL;
parameter.ux_slave_class_rndis_instance_deactivate = UX_NULL;

/* Define a local NODE ID. */

parameter.ux_slave_class_rndis_parameter_local_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_local_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_local_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_local_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_local_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_local_node_id[5] = 0x78;

/* Define a remote NODE ID. */

parameter.ux_slave_class_rndis_parameter_remote_node_id[0] = 0x00;
parameter.ux_slave_class_rndis_parameter_remote_node_id[1] = 0x1e;
parameter.ux_slave_class_rndis_parameter_remote_node_id[2] = 0x58;
parameter.ux_slave_class_rndis_parameter_remote_node_id[3] = 0x41;
parameter.ux_slave_class_rndis_parameter_remote_node_id[4] = 0xb8;
parameter.ux_slave_class_rndis_parameter_remote_node_id[5] = 0x79;

/* Set extra parameters used by the RNDIS query command with certain OIDs. */

parameter.ux_slave_class_rndis_parameter_vendor_id = 0x04b4 ;
parameter.ux_slave_class_rndis_parameter_driver_version = 0x1127;
ux_utility_memory_copy(parameter.ux_slave_class_rndis_parameter_vendor_description,
    "ELOGIC RNDIS", 12);

/* Initialize the device rndis class. This class owns both interfaces. */
status = ux_device_stack_class_register(_ux_system_slave_class_rndis_name,
    ux_device_class_rndis_entry, 1,0, &parameter);
```

<span data-ttu-id="dcac2-113">Как и в случае с CDC-ECM, для класса RNDIS требуется 2 узла, один локальный и один удаленный, однако не требуется строковый дескриптор, описывающий удаленный узел.</span><span class="sxs-lookup"><span data-stu-id="dcac2-113">As for the CDC-ECM, the RNDIS class requires 2 nodes, one local and one remote but there is no requirement to have a string descriptor describing the remote node.</span></span>

<span data-ttu-id="dcac2-114">Однако из-за механизма обмена сообщениями корпорации Майкрософт, защищаемого законодательством об интеллектуальной собственности, требуются некоторые дополнительные параметры.</span><span class="sxs-lookup"><span data-stu-id="dcac2-114">However due to Microsoft proprietary messaging mechanism, some extra parameters are required.</span></span> <span data-ttu-id="dcac2-115">Сначала необходимо передать идентификатор поставщика.</span><span class="sxs-lookup"><span data-stu-id="dcac2-115">First the vendor ID has to be passed.</span></span> <span data-ttu-id="dcac2-116">Затем версию драйвера RNDIS.</span><span class="sxs-lookup"><span data-stu-id="dcac2-116">Likewise, the driver version of the RNDIS.</span></span> <span data-ttu-id="dcac2-117">Также задать строку поставщика.</span><span class="sxs-lookup"><span data-stu-id="dcac2-117">A vendor string must also be given.</span></span>

<span data-ttu-id="dcac2-118">Класс RNDIS содержит встроенные API для передачи данных обоими способами, однако они скрыты для приложения, так как пользовательское приложение взаимодействует с USB-устройством Ethernet через NetX.</span><span class="sxs-lookup"><span data-stu-id="dcac2-118">The RNDIS class has built-in APIs for transferring data both ways but they are hidden to the application as the user application will communicate with the USB Ethernet device through NetX.</span></span>

<span data-ttu-id="dcac2-119">Класс USBX RNDIS тесно привязан к сетевому стеку NetX в ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="dcac2-119">The USBX RNDIS class is closely tied to Azure RTOS NetX Network stack.</span></span> <span data-ttu-id="dcac2-120">Приложение, использующее и NetX, и класс USBX RNDIS, активирует сетевой стек NetX обычным образом, но в дополнение необходимо активировать сетевой стек USB, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="dcac2-120">An application using both NetX and USBX RNDIS class will activate the NetX network stack in its usual way but in addition needs to activate the USB network stack as follows.</span></span>

```C
/* Initialize the NetX system. */

nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

<span data-ttu-id="dcac2-121">Сетевой стек USB следует активировать только один раз, и он не зависит от RNDIS, однако необходим для любого класса USB, которому требуются службы NetX.</span><span class="sxs-lookup"><span data-stu-id="dcac2-121">The USB network stack needs to be activated only once and is not specific to RNDIS but is required by any USB class that requires NetX services.</span></span>

<span data-ttu-id="dcac2-122">Класс RNDIS не будет распознан узлами MAC OS и Linux, так как он относится только к операционным системам Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="dcac2-122">The RNDIS class will not be recognized by MAC OS and Linux hosts as it is specific to Microsoft operating systems.</span></span> <span data-ttu-id="dcac2-123">На платформах Windows на узле должен присутствовать INF-файл, соответствующий дескриптору устройства.</span><span class="sxs-lookup"><span data-stu-id="dcac2-123">On windows platforms a .inf file needs to be present on the host that matches the device descriptor.</span></span> <span data-ttu-id="dcac2-124">Корпорация Майкрософт предоставляет для класса RNDIS шаблон, который можно найти в каталоге usbx_windows_host_files.</span><span class="sxs-lookup"><span data-stu-id="dcac2-124">Microsoft supplies a template for the RNDIS class and it can be found in the usbx_windows_host_files directory.</span></span> <span data-ttu-id="dcac2-125">Для более поздней версии Windows следует использовать файл RNDIS_Template.inf.</span><span class="sxs-lookup"><span data-stu-id="dcac2-125">For more recent version of Windows the file RNDIS_Template.inf should be used.</span></span> <span data-ttu-id="dcac2-126">Этот файл необходимо изменить в соответствии с идентификаторами PID/VID, используемыми устройством.</span><span class="sxs-lookup"><span data-stu-id="dcac2-126">This file needs to be modified to reflect the PID/VID used by the device.</span></span> <span data-ttu-id="dcac2-127">PID/VID зависят от клиента, если компания и продукт зарегистрированы с использованием USB-IF.</span><span class="sxs-lookup"><span data-stu-id="dcac2-127">The PID/VID will be specific to the final customer when the company and the product are registered with the USB-IF.</span></span> <span data-ttu-id="dcac2-128">В INF-файле поля для изменения находятся здесь.</span><span class="sxs-lookup"><span data-stu-id="dcac2-128">In the inf file, the fields to modify are located here.</span></span>

```Inf
[DeviceList]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00

[DeviceList.NTamd64]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00
```

<span data-ttu-id="dcac2-129">В платформе устройств устройства RNDIS идентификаторы PID/VID хранятся в дескрипторе устройства (см. дескриптор устройства, объявленный выше).</span><span class="sxs-lookup"><span data-stu-id="dcac2-129">In the device framework of the RNDIS device, the PID/VID are stored in the device descriptor (see the device descriptor declared above)</span></span>

<span data-ttu-id="dcac2-130">Когда хост-система USB обнаруживает устройство USB RNDIS, она подключает сетевой интерфейс, и устройство может использоваться со стеком сетевых протоколов.</span><span class="sxs-lookup"><span data-stu-id="dcac2-130">When a USB host systems discovers the USB RNDIS device, it will mount a network interface and the device can be used with network protocol stack.</span></span> <span data-ttu-id="dcac2-131">Подробнее см. в разделе "Операционная система узла".</span><span class="sxs-lookup"><span data-stu-id="dcac2-131">See the host Operating System for reference.</span></span>

## <a name="usb-device-dfu-class"></a><span data-ttu-id="dcac2-132">Класс DFU USB-устройства</span><span class="sxs-lookup"><span data-stu-id="dcac2-132">USB Device DFU Class</span></span>

<span data-ttu-id="dcac2-133">Класс DFU USB-устройства позволяет хост-системе USB обновлять встроенное ПО устройства на основе ведущего приложения.</span><span class="sxs-lookup"><span data-stu-id="dcac2-133">The USB device DFU class allows for a USB host system to update the device firmware based on a host application.</span></span> <span data-ttu-id="dcac2-134">Класс DFU — это стандартный класс USB-IF.</span><span class="sxs-lookup"><span data-stu-id="dcac2-134">The DFU class is a USB-IF standard class.</span></span>

<span data-ttu-id="dcac2-135">Класс USBX DFU относительно прост.</span><span class="sxs-lookup"><span data-stu-id="dcac2-135">USBX DFU class is relatively simple.</span></span> <span data-ttu-id="dcac2-136">Дескриптору устройства не требуется ничего, кроме конечной точки управления.</span><span class="sxs-lookup"><span data-stu-id="dcac2-136">It device descriptor does not require anything but a control endpoint.</span></span> <span data-ttu-id="dcac2-137">В большинстве случаев этот класс будет внедрен в составное устройство USB.</span><span class="sxs-lookup"><span data-stu-id="dcac2-137">Most of the time, this class will be embedded into a USB composite device.</span></span> <span data-ttu-id="dcac2-138">Устройство может быть любым, например запоминающим устройством или устройством связи, а добавленный интерфейс DFU может информировать узел о том, что встроенное ПО на устройстве может быть обновлено в режиме реального времени.</span><span class="sxs-lookup"><span data-stu-id="dcac2-138">The device can be anything such as a storage device or a comm device and the added DFU interface can inform the host that the device can have its firmware updated on the fly.</span></span>

<span data-ttu-id="dcac2-139">Работа класса DFU состоит из 3 шагов.</span><span class="sxs-lookup"><span data-stu-id="dcac2-139">The DFU class works in 3 steps.</span></span> <span data-ttu-id="dcac2-140">Сначала устройство подключается как обычное с помощью экспортированного класса.</span><span class="sxs-lookup"><span data-stu-id="dcac2-140">First the device mounts as normal using the class exported.</span></span> <span data-ttu-id="dcac2-141">Приложение на узле (Windows или Linux) будет использовать класс DFU и отправит запрос на сброс устройства в режим DFU.</span><span class="sxs-lookup"><span data-stu-id="dcac2-141">An application on the host (Windows or Linux) will exercise the DFU class and send a request to reset the device into DFU mode.</span></span> <span data-ttu-id="dcac2-142">Устройство ненадолго исчезнет с шины (чтобы узел и устройство обнаружили последовательность сброса RESET), а после перезапуска будет работать исключительно в режиме DFU, ожидая отправки обновления встроенного ПО ведущим приложением.</span><span class="sxs-lookup"><span data-stu-id="dcac2-142">The device will disappear from the bus for a short time (enough for the host and the device to detect a RESET sequence) and upon restarting, the device will be exclusively in DFU mode, waiting for the host application to send a firmware upgrade.</span></span> <span data-ttu-id="dcac2-143">Когда обновление встроенного ПО завершено, ведущее приложение сбрасывает устройство и при повторном перечислении устройство возвращается к нормальной работе с новым встроенным ПО.</span><span class="sxs-lookup"><span data-stu-id="dcac2-143">When the firmware upgrade has been completed, the host application resets the device and upon re-enumeration the device will revert to its normal operation with the new firmware.</span></span>

<span data-ttu-id="dcac2-144">Платформа устройства DFU будет выглядеть указанным ниже образом.</span><span class="sxs-lookup"><span data-stu-id="dcac2-144">A DFU device framework will look like this.</span></span>

```C
UCHAR device_framework_full_speed[] = {

    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x40,
    0x99, 0x99, 0x00, 0x00, 0x00, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x1b, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor for DFU. */
    0x09, 0x04, 0x00, 0x00, 0x00, 0xFE, 0x01, 0x01, 0x00,

    /* Functional descriptor for DFU. */
    0x09, 0x21, 0x0f, 0xE8, 0x03, 0x40, 0x00, 0x00,
    0x01,

};
```

<span data-ttu-id="dcac2-145">В этом примере дескриптор DFU не сопоставлен с другими классами.</span><span class="sxs-lookup"><span data-stu-id="dcac2-145">In this example, the DFU descriptor is not associated with any other classes.</span></span> <span data-ttu-id="dcac2-146">Он имеет простой дескриптор интерфейса и не имеет других подключенных конечных точек.</span><span class="sxs-lookup"><span data-stu-id="dcac2-146">It has a simple interface descriptor and no other endpoints attached to it.</span></span> <span data-ttu-id="dcac2-147">Существует функциональный дескриптор, описывающий особенности возможностей DFU для устройства.</span><span class="sxs-lookup"><span data-stu-id="dcac2-147">There is a Functional descriptor that describes the specifics of the DFU capabilities of the device.</span></span>

<span data-ttu-id="dcac2-148">Ниже приведено описание возможностей DFU.</span><span class="sxs-lookup"><span data-stu-id="dcac2-148">The description of the DFU capabilities are as follows.</span></span>

| <span data-ttu-id="dcac2-149">Имя</span><span class="sxs-lookup"><span data-stu-id="dcac2-149">Name</span></span>             | <span data-ttu-id="dcac2-150">Offset</span><span class="sxs-lookup"><span data-stu-id="dcac2-150">Offset</span></span>  | <span data-ttu-id="dcac2-151">Размер</span><span class="sxs-lookup"><span data-stu-id="dcac2-151">Size</span></span> | <span data-ttu-id="dcac2-152">тип</span><span class="sxs-lookup"><span data-stu-id="dcac2-152">type</span></span>      | <span data-ttu-id="dcac2-153">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-153">Description</span></span> |
|------------------|----------|------|-----------|------------|
| <span data-ttu-id="dcac2-154">bmAttributes</span><span class="sxs-lookup"><span data-stu-id="dcac2-154">bmAttributes</span></span>  | <span data-ttu-id="dcac2-155">2</span><span class="sxs-lookup"><span data-stu-id="dcac2-155">2</span></span>     | <span data-ttu-id="dcac2-156">1</span><span class="sxs-lookup"><span data-stu-id="dcac2-156">1</span></span>   | <span data-ttu-id="dcac2-157">Битовое поле</span><span class="sxs-lookup"><span data-stu-id="dcac2-157">Bit field</span></span> | <span data-ttu-id="dcac2-158">Бит 3: устройство будет выполнять последовательность отсоединения-подсоединения шины при получении запроса DFU_DETACH.</span><span class="sxs-lookup"><span data-stu-id="dcac2-158">Bit 3: device will perform a bus detach-attach sequence when it receives a DFU_DETACH request.</span></span> <span data-ttu-id="dcac2-159">Узел не должен выдавать сброс USB.</span><span class="sxs-lookup"><span data-stu-id="dcac2-159">The host must not issue a USB Reset.</span></span> <span data-ttu-id="dcac2-160">(bitWillDetach) 0 = нет, 1 = да. Бит 2: устройство может взаимодействовать через USB после этапа манифестации.</span><span class="sxs-lookup"><span data-stu-id="dcac2-160">(bitWillDetach) 0 = no 1 = yes Bit 2: device is able to communicate via USB after Manifestation phase.</span></span> <span data-ttu-id="dcac2-161">(bitManifestationTolerant) 0 = нет, должен увидеть сброс шины, 1 = да. Бит 1: поддерживается отправка. (bitCanUpload) 0 = нет, 1 = да. Бит 0: поддерживается скачивание. (bitCanDnload) 0 = нет, 1 = да.</span><span class="sxs-lookup"><span data-stu-id="dcac2-161">(bitManifestationTolerant) 0 = no, must see bus reset 1 = yes Bit 1: upload capable (bitCanUpload) 0 = no 1 = yes Bit 0: download capable (bitCanDnload) 0 = no 1 = yes</span></span>  |
| <span data-ttu-id="dcac2-162">wDetachTimeOut</span><span class="sxs-lookup"><span data-stu-id="dcac2-162">wDetachTimeOut</span></span>  | <span data-ttu-id="dcac2-163">3</span><span class="sxs-lookup"><span data-stu-id="dcac2-163">3</span></span>      | <span data-ttu-id="dcac2-164">2</span><span class="sxs-lookup"><span data-stu-id="dcac2-164">2</span></span>  | <span data-ttu-id="dcac2-165">number</span><span class="sxs-lookup"><span data-stu-id="dcac2-165">number</span></span>    | <span data-ttu-id="dcac2-166">Время в миллисекундах, в течение которого устройство будет ожидать после получения запроса DFU_DETACH.</span><span class="sxs-lookup"><span data-stu-id="dcac2-166">Time, in milliseconds, that the device will wait after receipt of the DFU_DETACH request.</span></span> <span data-ttu-id="dcac2-167">Если это время истекает без сброса USB, устройство завершит этап перенастройки и вернется к нормальной работе.</span><span class="sxs-lookup"><span data-stu-id="dcac2-167">If this time elapses without a USB reset, then the device will terminate the Reconfiguration phase and revert back to normal operation.</span></span> <span data-ttu-id="dcac2-168">Представляет максимальное время ожидания устройства (в зависимости от его таймеров и т. п.).</span><span class="sxs-lookup"><span data-stu-id="dcac2-168">This represents the maximum time that the device can wait (depending on its timers, etc.).</span></span> <span data-ttu-id="dcac2-169">USBX устанавливает это значение равным 1000 мс.</span><span class="sxs-lookup"><span data-stu-id="dcac2-169">USBX sets this value to 1000 ms.</span></span>  |
| <span data-ttu-id="dcac2-170">wTransferSize</span><span class="sxs-lookup"><span data-stu-id="dcac2-170">wTransferSize</span></span>  | <span data-ttu-id="dcac2-171">5</span><span class="sxs-lookup"><span data-stu-id="dcac2-171">5</span></span>      | <span data-ttu-id="dcac2-172">2</span><span class="sxs-lookup"><span data-stu-id="dcac2-172">2</span></span>  | <span data-ttu-id="dcac2-173">number</span><span class="sxs-lookup"><span data-stu-id="dcac2-173">number</span></span>    | <span data-ttu-id="dcac2-174">Максимальное число байтов, которое устройство может принимать на операцию управления\-записи.</span><span class="sxs-lookup"><span data-stu-id="dcac2-174">Maximum number of bytes that the device can accept per control\-write operation.</span></span> <span data-ttu-id="dcac2-175">USBX задает это значение равным 64 байтам.</span><span class="sxs-lookup"><span data-stu-id="dcac2-175">USBX sets this value to 64 bytes.</span></span> |

<span data-ttu-id="dcac2-176">Объявление класса DFU выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="dcac2-176">The declaration of the DFU class is as follows:</span></span>

```C
/* Store the DFU parameters. */

dfu_parameter.ux_slave_class_dfu_parameter_instance_activate =
    tx_demo_thread_dfu_activate;

dfu_parameter.ux_slave_class_dfu_parameter_instance_deactivate =
    tx_demo_thread_dfu_deactivate;

dfu_parameter.ux_slave_class_dfu_parameter_read =
    tx_demo_thread_dfu_read;

dfu_parameter.ux_slave_class_dfu_parameter_write =
    tx_demo_thread_dfu_write;

dfu_parameter.ux_slave_class_dfu_parameter_get_status =
    tx_demo_thread_dfu_get_status;

dfu_parameter.ux_slave_class_dfu_parameter_notify =
    tx_demo_thread_dfu_notify;

dfu_parameter.ux_slave_class_dfu_parameter_framework =
    device_framework_dfu;

dfu_parameter.ux_slave_class_dfu_parameter_framework_length =
    DEVICE_FRAMEWORK_LENGTH_DFU;

/* Initialize the device dfu class. The class is connected with interface
1 on configuration 1. */
status = ux_device_stack_class_register(_ux_system_slave_class_dfu_name,
    ux_device_class_dfu_entry, 1, 0,
    (VOID *)&dfu_parameter);

if (status!=UX_SUCCESS) return;
```

<span data-ttu-id="dcac2-177">Класс DFU должен работать с приложением встроенного ПО устройства, относящимся к целевому объекту.</span><span class="sxs-lookup"><span data-stu-id="dcac2-177">The DFU class needs to work with a device firmware application specific to the target.</span></span> <span data-ttu-id="dcac2-178">Поэтому он определяет несколько обратных вызовов для чтения и записи встроенного ПО и для получения состояния от приложения обновления встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="dcac2-178">Therefore it defines several call back to read and write blocks of firmware and to get status from the firmware update application.</span></span> <span data-ttu-id="dcac2-179">Класс DFU также имеет функцию обратного вызова уведомления для информирования приложения о начале и конце передачи встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="dcac2-179">The DFU class also has a notify callback function to inform the application when a begin and end of transfer of the firmware occur.</span></span>

<span data-ttu-id="dcac2-180">Ниже приведено описание типичной схемы приложения DFU.</span><span class="sxs-lookup"><span data-stu-id="dcac2-180">Following is the description of a typical DFU application flow.</span></span>

![Схема приложения DFU](./media/usbx-device-stack-supplemental/dfu-application-flow.png)

<span data-ttu-id="dcac2-182">Основная сложность при работе с классом DFU заключается в получении правильного приложения на узле для выполнения скачивания встроенного ПО.</span><span class="sxs-lookup"><span data-stu-id="dcac2-182">The major challenge of the DFU class is getting the right application on the host to perform the download the firmware.</span></span> <span data-ttu-id="dcac2-183">Приложения, предоставляемые корпорацией Майкрософт или USB-IF, отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="dcac2-183">There is no application supplied by Microsoft or the USB-IF.</span></span> <span data-ttu-id="dcac2-184">Существует несколько условно бесплатных программ, которые хорошо работают в Linux и немного хуже в Windows.</span><span class="sxs-lookup"><span data-stu-id="dcac2-184">Some shareware exist and they work reasonably well on Linux and to a lesser extent on Windows.</span></span>

<span data-ttu-id="dcac2-185">В Linux можно использовать программы dfu-util, которые можно найти здесь: [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) Множество сведений о dfu-util см. по этой ссылке: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)</span><span class="sxs-lookup"><span data-stu-id="dcac2-185">On Linux, one can use dfu-utils to be found here: [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) A lot of information on dfu utils can also be found on this link: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)</span></span>

<span data-ttu-id="dcac2-186">Реализация DFU в Linux выполняет правильную последовательность сброса между узлом и устройством, и поэтому устройство в этом не нуждается.</span><span class="sxs-lookup"><span data-stu-id="dcac2-186">The Linux implementation of DFU performs correctly the reset sequence between the host and the device and therefore the device does not need to do it.</span></span> <span data-ttu-id="dcac2-187">Linux может принимать для bmAttributes значение *bitWillDetach*, равное 0.</span><span class="sxs-lookup"><span data-stu-id="dcac2-187">Linux can accept for the bmAttributes *bitWillDetach* to be 0.</span></span> <span data-ttu-id="dcac2-188">С другой стороны, Windows требует, чтобы устройство выполнило сброс.</span><span class="sxs-lookup"><span data-stu-id="dcac2-188">Windows on the other side requires the device to perform the reset.</span></span>

<span data-ttu-id="dcac2-189">В Windows реестр USB должен иметь возможность сопоставить USB-устройство с его PID/VID и библиотекой USB, которая, в свою очередь, будет использоваться приложением DFU.</span><span class="sxs-lookup"><span data-stu-id="dcac2-189">On Windows, the USB registry must be able to associate the USB device with its PID/VID and the USB library which will in turn be used by the DFU application.</span></span> <span data-ttu-id="dcac2-190">Это можно легко сделать с помощью бесплатной служебной программы Zadig, которую можно найти здесь: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/).</span><span class="sxs-lookup"><span data-stu-id="dcac2-190">This can be easily done with the free utility Zadig which can be found here: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/).</span></span>

<span data-ttu-id="dcac2-191">При первом запуске Zadig отображается следующий экран:</span><span class="sxs-lookup"><span data-stu-id="dcac2-191">Running Zadig for the first time will show this screen:</span></span>

![Первый запуск Zadig](./media/usbx-device-stack-supplemental/zadig.png)

<span data-ttu-id="dcac2-193">В списке устройств найдите свое устройство и сопоставьте его с драйвером Windows libusb.</span><span class="sxs-lookup"><span data-stu-id="dcac2-193">From the device list, find your device and associate it with the libusb windows driver.</span></span> <span data-ttu-id="dcac2-194">Это приведет к привязке PID/VID устройства к библиотеке USB Windows, используемой служебными программами DFU.</span><span class="sxs-lookup"><span data-stu-id="dcac2-194">This will bind the PID/VID of the device with the Windows USB library used by the DFU utilities.</span></span>

<span data-ttu-id="dcac2-195">Чтобы выполнить команду DFU, просто распакуйте архив со служебными программами DFU в каталог, убедившись, что библиотека DLL libusb также находится в этом каталоге.</span><span class="sxs-lookup"><span data-stu-id="dcac2-195">To operate the DFU command, simply unpack the zipped dfu utilities into a directory, making sure the libusb dll is also present in the same directory.</span></span> <span data-ttu-id="dcac2-196">Служебные программы DFU необходимо запускать из окна DOS в командной строке.</span><span class="sxs-lookup"><span data-stu-id="dcac2-196">The DFU utilities must be run from a DOS box at the command line.</span></span>

<span data-ttu-id="dcac2-197">Сначала введите команду **dfu-util –l**, чтобы определить, отображается ли устройство в списке.</span><span class="sxs-lookup"><span data-stu-id="dcac2-197">First, type the command **dfu-util –l** to determine whether the device is listed.</span></span> <span data-ttu-id="dcac2-198">Если его нет, запустите Zadig, чтобы убедиться, что устройство отображается и связано с библиотекой USB.</span><span class="sxs-lookup"><span data-stu-id="dcac2-198">If not, run Zadig to make sure the device is listed and associated with the USB library.</span></span> <span data-ttu-id="dcac2-199">Вы увидите экран следующего вида:</span><span class="sxs-lookup"><span data-stu-id="dcac2-199">You should see a screen as follows:</span></span>

```Command-line
C:\usb specs\DFU\dfu-util-0.6&gt;dfu-util -l dfu-util 0.6

Copyright 2005-2008 Weston Schmidt, Harald Welte and OpenMoko Inc.
Copyright 2010-2012 Tormod Volden and Stefan Schmidt
This program is Free Software and has ABSOLUTELY NO WARRANTY
Found Runtime: [0a5c:21bc] devnum=0, cfg=1, intf=3, alt=0, name="UNDEFINED"
```

<span data-ttu-id="dcac2-200">Следующим шагом будет подготовка файла к скачиванию.</span><span class="sxs-lookup"><span data-stu-id="dcac2-200">The next step will be to prepare the file to be downloaded.</span></span> <span data-ttu-id="dcac2-201">Класс USBX DFU не выполняет проверку этого файла и не зависит от его внутреннего формата.</span><span class="sxs-lookup"><span data-stu-id="dcac2-201">The USBX DFU class does not perform any verification on this file and is agnostic of its internal format.</span></span> <span data-ttu-id="dcac2-202">Этот файл встроенного ПО сильно зависит для целевого объекта, но не DFU и не USBX.</span><span class="sxs-lookup"><span data-stu-id="dcac2-202">This firmware file is very specific to the target but not to DFU nor to USBX.</span></span>

<span data-ttu-id="dcac2-203">Затем можно велеть dfu-util отправить файл, введя следующую команду:</span><span class="sxs-lookup"><span data-stu-id="dcac2-203">Then the dfu-util can be instructed to send the file by typing the following command:</span></span>

```Command-line
dfu-util –R –t 64 -D file_to_download.hex
```

<span data-ttu-id="dcac2-204">Программа dfu-util должна отобразить процесс скачивания файла, пока встроенное ПО не будет полностью скачано.</span><span class="sxs-lookup"><span data-stu-id="dcac2-204">The dfu-util should display the file download process until the firmware has been completely downloaded.</span></span>

## <a name="usb-device-pima-class-ptp-responder"></a><span data-ttu-id="dcac2-205">Класс PIMA USB-устройства (ответчик PTP)</span><span class="sxs-lookup"><span data-stu-id="dcac2-205">USB Device PIMA Class (PTP Responder)</span></span>

<span data-ttu-id="dcac2-206">Класс USB-устройства PIMA позволяет хост-системе USB (инициатор) подключаться к</span><span class="sxs-lookup"><span data-stu-id="dcac2-206">The USB device PIMA class allows for a USB host system (Initiator) to connect to a</span></span>

<span data-ttu-id="dcac2-207">устройству PIMA (ответчик) для передачи файлов мультимедиа.</span><span class="sxs-lookup"><span data-stu-id="dcac2-207">PIMA device (Resonder) to transfer media files.</span></span> <span data-ttu-id="dcac2-208">Класс USBX PIMA соответствует классу USB-IF PIMA 15740, который также известен как класс PTP (протокол обмена изображениями).</span><span class="sxs-lookup"><span data-stu-id="dcac2-208">USBX Pima Class is conforming to the USB-IF PIMA 15740 class also known as PTP class (for Picture Transfer Protocol).</span></span>

<span data-ttu-id="dcac2-209">Класс PIMA на стороне устройства USBX поддерживает следующие операции:</span><span class="sxs-lookup"><span data-stu-id="dcac2-209">USBX device side PIMA class supports the following operations.</span></span>

| <span data-ttu-id="dcac2-210">Код операции</span><span class="sxs-lookup"><span data-stu-id="dcac2-210">Operation code</span></span>                                    | <span data-ttu-id="dcac2-211">Значение</span><span class="sxs-lookup"><span data-stu-id="dcac2-211">Value</span></span> | <span data-ttu-id="dcac2-212">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-212">Description</span></span>                       |
|---------------------------------------------------|---------|-----------------------------------------------------|
| <span data-ttu-id="dcac2-213">UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO</span><span class="sxs-lookup"><span data-stu-id="dcac2-213">UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO</span></span>    | <span data-ttu-id="dcac2-214">0x1001</span><span class="sxs-lookup"><span data-stu-id="dcac2-214">0x1001</span></span>  | <span data-ttu-id="dcac2-215">Получение поддерживаемых устройством операций и событий.</span><span class="sxs-lookup"><span data-stu-id="dcac2-215">Obtain the device supported operations and events</span></span>                                                         |
| <span data-ttu-id="dcac2-216">UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION</span><span class="sxs-lookup"><span data-stu-id="dcac2-216">UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION</span></span>        | <span data-ttu-id="dcac2-217">0x1002</span><span class="sxs-lookup"><span data-stu-id="dcac2-217">0x1002</span></span>  | <span data-ttu-id="dcac2-218">Открытие сеанса между узлом и устройством.</span><span class="sxs-lookup"><span data-stu-id="dcac2-218">Open a session between the host and the device</span></span>                                                            |
| <span data-ttu-id="dcac2-219">UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION</span><span class="sxs-lookup"><span data-stu-id="dcac2-219">UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION</span></span>       | <span data-ttu-id="dcac2-220">0x1003</span><span class="sxs-lookup"><span data-stu-id="dcac2-220">0x1003</span></span>  | <span data-ttu-id="dcac2-221">Закрытие сеанса между узлом и устройством.</span><span class="sxs-lookup"><span data-stu-id="dcac2-221">Close a session between the host and the device</span></span>                                                           |
| <span data-ttu-id="dcac2-222">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS</span><span class="sxs-lookup"><span data-stu-id="dcac2-222">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS</span></span>    | <span data-ttu-id="dcac2-223">0x1004</span><span class="sxs-lookup"><span data-stu-id="dcac2-223">0x1004</span></span>  | <span data-ttu-id="dcac2-224">Возвращение идентификатора хранилища для устройства.</span><span class="sxs-lookup"><span data-stu-id="dcac2-224">Returns the storage ID for the device.</span></span> <span data-ttu-id="dcac2-225">USBX PIMA использует только один идентификатор хранилища.</span><span class="sxs-lookup"><span data-stu-id="dcac2-225">USBX PIMA uses one storage ID only</span></span> |
| <span data-ttu-id="dcac2-226">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO</span><span class="sxs-lookup"><span data-stu-id="dcac2-226">UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO</span></span>   | <span data-ttu-id="dcac2-227">0x1005</span><span class="sxs-lookup"><span data-stu-id="dcac2-227">0x1005</span></span>  | <span data-ttu-id="dcac2-228">Возвращение сведений об объекте хранилища, например о максимальной емкости и свободном пространстве.</span><span class="sxs-lookup"><span data-stu-id="dcac2-228">Return information about the storage object such as max capacity and free space</span></span>                           |
| <span data-ttu-id="dcac2-229">UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS</span><span class="sxs-lookup"><span data-stu-id="dcac2-229">UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS</span></span>    | <span data-ttu-id="dcac2-230">0x1006</span><span class="sxs-lookup"><span data-stu-id="dcac2-230">0x1006</span></span>  | <span data-ttu-id="dcac2-231">Возврат числа объектов, содержащихся в запоминающем устройстве.</span><span class="sxs-lookup"><span data-stu-id="dcac2-231">Return the number of objects contained in the storage device</span></span>                                              |
| <span data-ttu-id="dcac2-232">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES</span><span class="sxs-lookup"><span data-stu-id="dcac2-232">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES</span></span> | <span data-ttu-id="dcac2-233">0x1007</span><span class="sxs-lookup"><span data-stu-id="dcac2-233">0x1007</span></span>  | <span data-ttu-id="dcac2-234">Возврат массива дескрипторов объектов на запоминающем устройстве.</span><span class="sxs-lookup"><span data-stu-id="dcac2-234">Return an array of handles of the objects on the storage device</span></span>                                           |
| <span data-ttu-id="dcac2-235">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO</span><span class="sxs-lookup"><span data-stu-id="dcac2-235">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO</span></span>    | <span data-ttu-id="dcac2-236">0x1008</span><span class="sxs-lookup"><span data-stu-id="dcac2-236">0x1008</span></span>  | <span data-ttu-id="dcac2-237">Возвращение сведений об объекте, таких как имя объекта, дата его создания, дата изменения.</span><span class="sxs-lookup"><span data-stu-id="dcac2-237">Return information about an object such as the name of the object, its creation date, modification date</span></span> |
| <span data-ttu-id="dcac2-238">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dcac2-238">UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT</span></span>          | <span data-ttu-id="dcac2-239">0x1009</span><span class="sxs-lookup"><span data-stu-id="dcac2-239">0x1009</span></span>  | <span data-ttu-id="dcac2-240">Возврат данных, относящихся к определенному объекту.</span><span class="sxs-lookup"><span data-stu-id="dcac2-240">Return the data pertaining to a specific object</span></span>                                                         |
| <span data-ttu-id="dcac2-241">UX_DEVICE_CLASS_PIMA_OC_GET_THUMB</span><span class="sxs-lookup"><span data-stu-id="dcac2-241">UX_DEVICE_CLASS_PIMA_OC_GET_THUMB</span></span>           | <span data-ttu-id="dcac2-242">0x100A</span><span class="sxs-lookup"><span data-stu-id="dcac2-242">0x100A</span></span>  | <span data-ttu-id="dcac2-243">Отправка эскиза, если он доступен для объекта.</span><span class="sxs-lookup"><span data-stu-id="dcac2-243">Send the thumbnail if available about an object</span></span>                                                           |
| <span data-ttu-id="dcac2-244">UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dcac2-244">UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT</span></span>       | <span data-ttu-id="dcac2-245">0x100B</span><span class="sxs-lookup"><span data-stu-id="dcac2-245">0x100B</span></span>  | <span data-ttu-id="dcac2-246">Удаление объекта на носителе.</span><span class="sxs-lookup"><span data-stu-id="dcac2-246">Delete an object on the media</span></span>                                                                             |
| <span data-ttu-id="dcac2-247">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO</span><span class="sxs-lookup"><span data-stu-id="dcac2-247">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO</span></span>   | <span data-ttu-id="dcac2-248">0x100C</span><span class="sxs-lookup"><span data-stu-id="dcac2-248">0x100C</span></span>  | <span data-ttu-id="dcac2-249">Отправка на устройство сведения об объекте для его создания на носителе.</span><span class="sxs-lookup"><span data-stu-id="dcac2-249">Send to the device information about an object for its creation on the media</span></span>                              |
| <span data-ttu-id="dcac2-250">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dcac2-250">UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT</span></span>         | <span data-ttu-id="dcac2-251">0x100D</span><span class="sxs-lookup"><span data-stu-id="dcac2-251">0x100D</span></span>  | <span data-ttu-id="dcac2-252">Отправка данных для объекта на устройство.</span><span class="sxs-lookup"><span data-stu-id="dcac2-252">Send data for an object to the device</span></span>                                                                     |
| <span data-ttu-id="dcac2-253">UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE</span><span class="sxs-lookup"><span data-stu-id="dcac2-253">UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE</span></span>        | <span data-ttu-id="dcac2-254">0x100F</span><span class="sxs-lookup"><span data-stu-id="dcac2-254">0x100F</span></span>  | <span data-ttu-id="dcac2-255">Очистка носителя устройства.</span><span class="sxs-lookup"><span data-stu-id="dcac2-255">Clean the device media</span></span>                                                                                    |
| <span data-ttu-id="dcac2-256">UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE</span><span class="sxs-lookup"><span data-stu-id="dcac2-256">UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE</span></span>        | <span data-ttu-id="dcac2-257">0x0110</span><span class="sxs-lookup"><span data-stu-id="dcac2-257">0x0110</span></span>  | <span data-ttu-id="dcac2-258">Сброс целевого устройства.</span><span class="sxs-lookup"><span data-stu-id="dcac2-258">Reset the target device</span></span>                                                                                   |

| <span data-ttu-id="dcac2-259">Код операции</span><span class="sxs-lookup"><span data-stu-id="dcac2-259">Operation Code</span></span>                                         | <span data-ttu-id="dcac2-260">Значение</span><span class="sxs-lookup"><span data-stu-id="dcac2-260">Value</span></span> | <span data-ttu-id="dcac2-261">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-261">Description</span></span> |
|--------------------------------------------------------|-------|-----------------------------------------|
| <span data-ttu-id="dcac2-262">UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="dcac2-262">UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION</span></span>       | <span data-ttu-id="dcac2-263">0x4001</span><span class="sxs-lookup"><span data-stu-id="dcac2-263">0x4001</span></span>  | <span data-ttu-id="dcac2-264">Отмена текущей транзакции.</span><span class="sxs-lookup"><span data-stu-id="dcac2-264">Cancels the current transaction</span></span>                                                 |
| <span data-ttu-id="dcac2-265">UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED</span><span class="sxs-lookup"><span data-stu-id="dcac2-265">UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED</span></span>             | <span data-ttu-id="dcac2-266">0x4002</span><span class="sxs-lookup"><span data-stu-id="dcac2-266">0x4002</span></span>  | <span data-ttu-id="dcac2-267">Объект был добавлен на носитель устройства и может быть извлечен узлом.</span><span class="sxs-lookup"><span data-stu-id="dcac2-267">An object has been added to the device media and can be retrieved by the host\.</span></span> |
| <span data-ttu-id="dcac2-268">UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED</span><span class="sxs-lookup"><span data-stu-id="dcac2-268">UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED</span></span>           | <span data-ttu-id="dcac2-269">0x4003</span><span class="sxs-lookup"><span data-stu-id="dcac2-269">0x4003</span></span>  | <span data-ttu-id="dcac2-270">Объект удален с носителя устройства.</span><span class="sxs-lookup"><span data-stu-id="dcac2-270">An object has been deleted from the device media</span></span>                                |
| <span data-ttu-id="dcac2-271">UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED</span><span class="sxs-lookup"><span data-stu-id="dcac2-271">UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED</span></span>              | <span data-ttu-id="dcac2-272">0x4004</span><span class="sxs-lookup"><span data-stu-id="dcac2-272">0x4004</span></span>  | <span data-ttu-id="dcac2-273">На устройство добавлен носитель.</span><span class="sxs-lookup"><span data-stu-id="dcac2-273">A media has been added to the device</span></span>                                            |
| <span data-ttu-id="dcac2-274">UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED</span><span class="sxs-lookup"><span data-stu-id="dcac2-274">UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED</span></span>            | <span data-ttu-id="dcac2-275">0x4005</span><span class="sxs-lookup"><span data-stu-id="dcac2-275">0x4005</span></span>  | <span data-ttu-id="dcac2-276">Носитель удален с устройства.</span><span class="sxs-lookup"><span data-stu-id="dcac2-276">A media has been deleted from the device</span></span>                                        |
| <span data-ttu-id="dcac2-277">UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED</span><span class="sxs-lookup"><span data-stu-id="dcac2-277">UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED</span></span>     | <span data-ttu-id="dcac2-278">0x4006</span><span class="sxs-lookup"><span data-stu-id="dcac2-278">0x4006</span></span>  | <span data-ttu-id="dcac2-279">Свойства устройства изменены.</span><span class="sxs-lookup"><span data-stu-id="dcac2-279">Device properties have changed</span></span>                                                  |
| <span data-ttu-id="dcac2-280">UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED</span><span class="sxs-lookup"><span data-stu-id="dcac2-280">UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED</span></span>     | <span data-ttu-id="dcac2-281">0x4007</span><span class="sxs-lookup"><span data-stu-id="dcac2-281">0x4007</span></span>  | <span data-ttu-id="dcac2-282">Сведения об объекте изменены.</span><span class="sxs-lookup"><span data-stu-id="dcac2-282">An object information has changed</span></span>                                               |
| <span data-ttu-id="dcac2-283">UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE</span><span class="sxs-lookup"><span data-stu-id="dcac2-283">UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE</span></span>      | <span data-ttu-id="dcac2-284">0x4008</span><span class="sxs-lookup"><span data-stu-id="dcac2-284">0x4008</span></span>  | <span data-ttu-id="dcac2-285">Устройство изменилось.</span><span class="sxs-lookup"><span data-stu-id="dcac2-285">A device has changed</span></span>                                                            |
| <span data-ttu-id="dcac2-286">UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER</span><span class="sxs-lookup"><span data-stu-id="dcac2-286">UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER</span></span> | <span data-ttu-id="dcac2-287">0x4009</span><span class="sxs-lookup"><span data-stu-id="dcac2-287">0x4009</span></span>  | <span data-ttu-id="dcac2-288">Устройство запрашивает перемещение объекта с узла.</span><span class="sxs-lookup"><span data-stu-id="dcac2-288">The device requests the transfer of an object from the host</span></span>                     |
| <span data-ttu-id="dcac2-289">UX_DEVICE_CLASS_PIMA_EC_STORE_FULL</span><span class="sxs-lookup"><span data-stu-id="dcac2-289">UX_DEVICE_CLASS_PIMA_EC_STORE_FULL</span></span>               | <span data-ttu-id="dcac2-290">0x400A</span><span class="sxs-lookup"><span data-stu-id="dcac2-290">0x400A</span></span>  | <span data-ttu-id="dcac2-291">Устройство сообщает, что носитель заполнен.</span><span class="sxs-lookup"><span data-stu-id="dcac2-291">Device reports the media is full</span></span>                                                |
| <span data-ttu-id="dcac2-292">UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET</span><span class="sxs-lookup"><span data-stu-id="dcac2-292">UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET</span></span>             | <span data-ttu-id="dcac2-293">0x400B</span><span class="sxs-lookup"><span data-stu-id="dcac2-293">0x400B</span></span>  | <span data-ttu-id="dcac2-294">Устройство сообщает о сбросе.</span><span class="sxs-lookup"><span data-stu-id="dcac2-294">Device reports it was reset</span></span>                                                     |
| <span data-ttu-id="dcac2-295">UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED</span><span class="sxs-lookup"><span data-stu-id="dcac2-295">UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED</span></span>    | <span data-ttu-id="dcac2-296">0x400C</span><span class="sxs-lookup"><span data-stu-id="dcac2-296">0x400C</span></span>  | <span data-ttu-id="dcac2-297">На устройстве изменились сведения о хранилище.</span><span class="sxs-lookup"><span data-stu-id="dcac2-297">Storage information has changed on the device</span></span>                                   |
| <span data-ttu-id="dcac2-298">UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE</span><span class="sxs-lookup"><span data-stu-id="dcac2-298">UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE</span></span>         | <span data-ttu-id="dcac2-299">0x400D</span><span class="sxs-lookup"><span data-stu-id="dcac2-299">0x400D</span></span>  | <span data-ttu-id="dcac2-300">Захват завершен.</span><span class="sxs-lookup"><span data-stu-id="dcac2-300">Capture is completed</span></span>                                                            |

<span data-ttu-id="dcac2-301">Класс устройств USBX PIMA использует поток TX для прослушивания команд PIMA с узла.</span><span class="sxs-lookup"><span data-stu-id="dcac2-301">The USBX PIMA device class uses a TX Thread to listen to PIMA commands from the host.</span></span>

<span data-ttu-id="dcac2-302">Команда PIMA состоит из блока команд, блока данных и этапа состояния.</span><span class="sxs-lookup"><span data-stu-id="dcac2-302">A PIMA command is composed of a command block, a data block and a status phase.</span></span>

<span data-ttu-id="dcac2-303">Функция ux_device_class_pima_thread отправляет запрос в стек для получения команды PIMA со стороны узла.</span><span class="sxs-lookup"><span data-stu-id="dcac2-303">The function ux_device_class_pima_thread posts a request to the stack to receive a PIMA command from the host side.</span></span> <span data-ttu-id="dcac2-304">Команда PIMA декодируется и проверяется на наличие содержимого.</span><span class="sxs-lookup"><span data-stu-id="dcac2-304">The PIMA command is decoded and verified for content.</span></span> <span data-ttu-id="dcac2-305">Если блок команд является допустимым, он направляется в соответствующий обработчик команд.</span><span class="sxs-lookup"><span data-stu-id="dcac2-305">If the command block is valid, it branches to the appropriate command handler.</span></span>

<span data-ttu-id="dcac2-306">Большинство команд PIMA могут быть выполнены только при открытии сеанса узлом.</span><span class="sxs-lookup"><span data-stu-id="dcac2-306">Most PIMA commands can only be executed when a session has been opened by the host.</span></span> <span data-ttu-id="dcac2-307">Единственным исключением является команда **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO**.</span><span class="sxs-lookup"><span data-stu-id="dcac2-307">The only exception is the command **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO**.</span></span> <span data-ttu-id="dcac2-308">В реализации USBX PIMA между инициатором и ответчиком одновременно можно открыть только один сеанс.</span><span class="sxs-lookup"><span data-stu-id="dcac2-308">With USBX PIMA implementation, only one session can be opened between an Initiator and Responder at any time.</span></span> <span data-ttu-id="dcac2-309">Все транзакции в рамках одного сеанса блокируются, и новая транзакция не может начаться до завершения предыдущей.</span><span class="sxs-lookup"><span data-stu-id="dcac2-309">All transactions within the single session are blocking and no new transaction can begin before the previous one completed.</span></span>

<span data-ttu-id="dcac2-310">Транзакции PIMA состоят из 3 этапов — этапа команды, дополнительного этапа данных и этапа ответа.</span><span class="sxs-lookup"><span data-stu-id="dcac2-310">PIMA transactions are composed of 3 phases, a command phase, an optional data phase and a response phase.</span></span> <span data-ttu-id="dcac2-311">При наличии этапа данных он может присутствовать только для одного направления.</span><span class="sxs-lookup"><span data-stu-id="dcac2-311">If a data phase is present, it can only be in one direction.</span></span>

<span data-ttu-id="dcac2-312">Инициатор всегда определяет поток операций PIMA, но ответчик может инициировать события обратно инициатору, чтобы сообщить об изменениях состояния, произошедших во время сеанса.</span><span class="sxs-lookup"><span data-stu-id="dcac2-312">The Initiator always determines the flow of the PIMA operations but the Responder can initiate events back to the Initiator to inform status changes that happened during a session.</span></span>

<span data-ttu-id="dcac2-313">На следующей схеме показана передача объекта данных между узлом и классом устройств PIMA.</span><span class="sxs-lookup"><span data-stu-id="dcac2-313">The following diagram shows the transfer of a data object between the host and the PIMA device class.</span></span>

![Транзакции PIMA](./media/usbx-device-stack-supplemental/pima-transactions.png)

## <a name="initialization-of-the-pima-device-class"></a><span data-ttu-id="dcac2-315">Инициализация класса устройств PIMA</span><span class="sxs-lookup"><span data-stu-id="dcac2-315">Initialization of the PIMA device class</span></span>

<span data-ttu-id="dcac2-316">Во время инициализации классу устройств PIMA требуются некоторые параметры, предоставляемые приложением.</span><span class="sxs-lookup"><span data-stu-id="dcac2-316">The PIMA device class needs some parameters supplied by the application during the initialization.</span></span>

<span data-ttu-id="dcac2-317">Приведенные ниже параметры описывают сведения об устройстве и хранилище.</span><span class="sxs-lookup"><span data-stu-id="dcac2-317">The following parameters describe the device and storage information.</span></span>

- `ux_device_class_pima_manufacturer`
- `ux_device_class_pima_model`
- `ux_device_class_pima_device_version`
- `ux_device_class_pima_serial_number`
- `ux_device_class_pima_storage_id`
- `ux_device_class_pima_storage_type`
- `ux_device_class_pima_storage_file_system_type`
- `ux_device_class_pima_storage_access_capability`
- `ux_device_class_pima_storage_max_capacity_low`
- `ux_device_class_pima_storage_max_capacity_high`
- `ux_device_class_pima_storage_free_space_low`
- `ux_device_class_pima_storage_free_space_high`
- `ux_device_class_pima_storage_free_space_image`
- `ux_device_class_pima_storage_description`
- `ux_device_class_pima_storage_volume_label`

<span data-ttu-id="dcac2-318">Класс PIMA также требует регистрацию обратного вызова в приложении, чтобы информировать приложение об определенных событиях либо извлечь данные с локального носителя или сохранить их там.</span><span class="sxs-lookup"><span data-stu-id="dcac2-318">The PIMA class also requires the registration of callback into the application to inform the application of certain events or retrieve/store data from/to the local media.</span></span> <span data-ttu-id="dcac2-319">Эти обратные вызовы указаны ниже.</span><span class="sxs-lookup"><span data-stu-id="dcac2-319">The callbacks are as follows.</span></span>

- `ux_device_class_pima_object_number_get`
- `ux_device_class_pima_object_handles_get`
- `ux_device_class_pima_object_info_get`
- `ux_device_class_pima_object_data_get`
- `ux_device_class_pima_object_info_send`
- `ux_device_class_pima_object_data_send`
- `ux_device_class_pima_object_delete`

<span data-ttu-id="dcac2-320">В следующем примере показано, как инициализировать клиентскую сторону PIMA.</span><span class="sxs-lookup"><span data-stu-id="dcac2-320">The following example shows how to initialize the client side of PIMA.</span></span> <span data-ttu-id="dcac2-321">В этом примере используется Pictbridge в качестве клиента для PIMA.</span><span class="sxs-lookup"><span data-stu-id="dcac2-321">This example uses Pictbridge as a client for PIMA.</span></span>

```C
/* Initialize the first XML object valid in the pictbridge instance.

Initialize the handle, type and file name.

The storage handle and the object handle have a fixed value of 1 in our implementation. */

object_info = pictbridge -> ux_pictbridge_object_client;

object_info -> ux_device_class_pima_object_format = UX_DEVICE_CLASS_PIMA_OFC_SCRIPT;
object_info -> ux_device_class_pima_object_storage_id = 1;
object_info -> ux_device_class_pima_object_handle_id = 2;

ux_utility_string_to_unicode(_ux_pictbridge_ddiscovery_name,
    object_info -> ux_device_class_pima_object_filename);

/* Initialize the head and tail of the notification round robin buffers.
   At first, the head and tail are pointing to the beginning of the array.
*/

pictbridge -> ux_pictbridge_event_array_head =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_tail =
    pictbridge -> ux_pictbridge_event_array;

pictbridge -> ux_pictbridge_event_array_end =
    pictbridge -> ux_pictbridge_event_array +
    UX_PICTBRIDGE_MAX_EVENT_NUMBER;

/* Initialialize the pima device parameter. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_manufacturer =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_model =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_serial_number =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_id = 1;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_type =
    UX_DEVICE_CLASS_PIMA_STC_FIXED_RAM;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_file_system_type =
    UX_DEVICE_CLASS_PIMA_FSTC_GENERIC_FLAT;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_access_capability =
    UX_DEVICE_CLASS_PIMA_AC_READ_WRITE;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_max_capacity_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_low =
    pictbridge -> ux_pictbridge_dpslocal.ux_pictbridge_devinfo_storage_size;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_high = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_free_space_image = 0;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_description =
    _ux_pictbridge_volume_description;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_storage_volume_label =
    _ux_pictbridge_volume_label;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_number_get =
    ux_pictbridge_dpsclient_object_number_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_handles_get =
    ux_pictbridge_dpsclient_object_handles_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_get =
    ux_pictbridge_dpsclient_object_info_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_get =
    ux_pictbridge_dpsclient_object_data_get;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_info_send =
    ux_pictbridge_dpsclient_object_info_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_data_send =
    ux_pictbridge_dpsclient_object_data_send;

pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_object_delete =
    ux_pictbridge_dpsclient_object_delete;

/* Store the instance owner. */
pictbridge -> ux_pictbridge_pima_parameter.ux_device_class_pima_parameter_application =
    (VOID *) pictbridge;

/* Initialize the device pima class. The class is connected with interface 0 */

status = ux_device_stack_class_register(_ux_system_slave_class_pima_name,
    ux_device_class_pima_entry, 1, 0, (VOID *)&pictbridge -> ux_pictbridge_pima_parameter);

/* Check status. */
if (status != UX_SUCCESS)
```

## <a name="ux_device_class_pima_object_add"></a><span data-ttu-id="dcac2-322">ux_device_class_pima_object_add</span><span class="sxs-lookup"><span data-stu-id="dcac2-322">ux_device_class_pima_object_add</span></span>

<span data-ttu-id="dcac2-323">Добавление объекта и отправка события на узел.</span><span class="sxs-lookup"><span data-stu-id="dcac2-323">Adding an object and sending the event to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-324">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-324">Prototype</span></span>

```C
UINT ux_device_class_pima_object_add(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG object_handle);
```

### <a name="description"></a><span data-ttu-id="dcac2-325">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-325">Description</span></span>

<span data-ttu-id="dcac2-326">Эта функция вызывается, когда классу PIMA необходимо добавить объект и проинформировать узел.</span><span class="sxs-lookup"><span data-stu-id="dcac2-326">This function is called when the PIMA class needs to add an object and inform the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-327">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-327">Parameters</span></span>

- <span data-ttu-id="dcac2-328">**pima**: указатель на экземпляр класса PIMA.</span><span class="sxs-lookup"><span data-stu-id="dcac2-328">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="dcac2-329">**object_handle**: дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="dcac2-329">**object_handle**: Handle of the object.</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-330">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-330">Example</span></span>

```C
/* Send the notification to the host that an object has been added. */

status = ux_device_class_pima_object_add(pima, UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST);
```

## <a name="ux_device_class_pima_object_number_get"></a><span data-ttu-id="dcac2-331">ux_device_class_pima_object_number_get</span><span class="sxs-lookup"><span data-stu-id="dcac2-331">ux_device_class_pima_object_number_get</span></span>

<span data-ttu-id="dcac2-332">Получение количества объектов из приложения.</span><span class="sxs-lookup"><span data-stu-id="dcac2-332">Getting the object number from the application</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-333">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-333">Prototype</span></span>

```C
UINT ux_device_class_pima_object_number_get(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG *object_number);
```

### <a name="description"></a><span data-ttu-id="dcac2-334">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-334">Description</span></span>

<span data-ttu-id="dcac2-335">Эта функция вызывается, когда классу PIMA требуется получить количество объектов в локальной системе и отправить его обратно на узел.</span><span class="sxs-lookup"><span data-stu-id="dcac2-335">This function is called when the PIMA class needs to retrieve the number of objects in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-336">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-336">Parameters</span></span>

- <span data-ttu-id="dcac2-337">**pima**: указатель на экземпляр класса PIMA.</span><span class="sxs-lookup"><span data-stu-id="dcac2-337">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="dcac2-338">**object_number**: адрес возвращаемого числа объектов.</span><span class="sxs-lookup"><span data-stu-id="dcac2-338">**object_number**: Address of the number of objects to be returned</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-339">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-339">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_number_get(UX_SLAVE_CLASS_PIMA *pima, ULONG *number_objects)
{
    /* We force the number of objects to be 1 only here. This will be the XML scripts. */
    *number_objects = 1;
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_handles_get"></a><span data-ttu-id="dcac2-340">ux_device_class_pima_object_handles_get</span><span class="sxs-lookup"><span data-stu-id="dcac2-340">ux_device_class_pima_object_handles_get</span></span>

<span data-ttu-id="dcac2-341">Возврат массива обработчиков объектов.</span><span class="sxs-lookup"><span data-stu-id="dcac2-341">Return the object handle array</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-342">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-342">Prototype</span></span>

```C
UINT **ux_device_class_pima_object_handles_get**(
    UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number);
```

### <a name="description"></a><span data-ttu-id="dcac2-343">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-343">Description</span></span>

<span data-ttu-id="dcac2-344">Эта функция вызывается, когда классу PIMA требуется получить массив дескрипторов объекта в локальной системе и отправить его обратно на узел.</span><span class="sxs-lookup"><span data-stu-id="dcac2-344">This function is called when the PIMA class needs to retrieve the object handles array in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-345">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-345">Parameters</span></span>

- <span data-ttu-id="dcac2-346">**pima**: указатель на экземпляр класса PIMA.</span><span class="sxs-lookup"><span data-stu-id="dcac2-346">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="dcac2-347">**object_handles_format_code**: код формата для дескрипторов.</span><span class="sxs-lookup"><span data-stu-id="dcac2-347">**object_handles_format_code**: Format code for the handles</span></span>
- <span data-ttu-id="dcac2-348">**object_handles_association**: код сопоставления объектов.</span><span class="sxs-lookup"><span data-stu-id="dcac2-348">**object_handles_association**: Object association code</span></span>
- <span data-ttu-id="dcac2-349">**object_handle_array**: адрес для хранения дескрипторов.</span><span class="sxs-lookup"><span data-stu-id="dcac2-349">**object_handle_array**: Address where to store the handles</span></span>
- <span data-ttu-id="dcac2-350">**object_handles_max_number**: максимальное число дескрипторов в массиве.</span><span class="sxs-lookup"><span data-stu-id="dcac2-350">**object_handles_max_number**: Maximum number of handles in the array</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-351">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-351">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_handles_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *) pima -> ux_device_class_pima_application;

    /* Set the pima pointer to the pictbridge instance. */
    pictbridge -> ux_pictbridge_pima = (VOID *) pima;

    /* We say we have one object but the caller might specify different format code and associations. */
    object_info = pictbridge -> ux_pictbridge_object_client;

    /* Insert in the array the number of found handles so far: 0. */
    ux_utility_long_put((UCHAR *)object_handles_array, 0);

    /* Check the type demanded. */

    if (object_handles_format_code == 0 || object_handles_format_code ==
        0xFFFFFFFF || object_info -> ux_device_class_pima_object_format ==
        object_handles_format_code)
    {
        /* Insert in the array the number of found handles. This handle is for the client XML script. */
        ux_utility_long_put((UCHAR *)object_handles_array, 1);

        /* Adjust the array to point after the number of elements. */
        object_handles_array++;

        /* We have a candicate. Store the handle. */
        ux_utility_long_put((UCHAR *)object_handles_array, object_info ->
            ux_device_class_pima_object_handle_id);
    }

    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_info_get"></a><span data-ttu-id="dcac2-352">ux_device_class_pima_object_info_get</span><span class="sxs-lookup"><span data-stu-id="dcac2-352">ux_device_class_pima_object_info_get</span></span>

<span data-ttu-id="dcac2-353">Возврат сведений об объекте.</span><span class="sxs-lookup"><span data-stu-id="dcac2-353">Return the object information</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-354">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-354">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_get(
    struct UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handle, 
    UX_SLAVE_CLASS_PIMA_OBJECT **object);
```

### <a name="description"></a><span data-ttu-id="dcac2-355">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-355">Description</span></span>

<span data-ttu-id="dcac2-356">Эта функция вызывается, когда классу PIMA требуется получить массив дескрипторов объекта в локальной системе и отправить его обратно на узел.</span><span class="sxs-lookup"><span data-stu-id="dcac2-356">This function is called when the PIMA class needs to retrieve the object handles array in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-357">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-357">Parameters</span></span>

- <span data-ttu-id="dcac2-358">**pima**: указатель на экземпляр класса PIMA.</span><span class="sxs-lookup"><span data-stu-id="dcac2-358">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="dcac2-359">**object_handles** — дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="dcac2-359">**object_handles**: Handle of the object</span></span>
- <span data-ttu-id="dcac2-360">**object**: адрес указателя объекта.</span><span class="sxs-lookup"><span data-stu-id="dcac2-360">**object**: Object pointer address</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-361">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-361">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_info_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UX_SLAVE_CLASS_PIMA_OBJECT **object)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST)) {

        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge -> ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;
    } else
        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;
    /* Return the pointer to this object. */
    *object = object_info;

    /* We are done. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_get"></a><span data-ttu-id="dcac2-362">ux_device_class_pima_object_data_get</span><span class="sxs-lookup"><span data-stu-id="dcac2-362">ux_device_class_pima_object_data_get</span></span>

<span data-ttu-id="dcac2-363">Возврат данных объекта.</span><span class="sxs-lookup"><span data-stu-id="dcac2-363">Return the object data</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-364">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-364">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_get(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length_requested,
    ULONG *object_actual_length);
```

### <a name="description"></a><span data-ttu-id="dcac2-365">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-365">Description</span></span>

<span data-ttu-id="dcac2-366">Эта функция вызывается, когда классу PIMA требуется получить данные объекта в локальной системе и отправить их обратно на узел.</span><span class="sxs-lookup"><span data-stu-id="dcac2-366">This function is called when the PIMA class needs to retrieve the object data in the local system and send it back to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-367">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-367">Parameters</span></span>

- <span data-ttu-id="dcac2-368">**pima**: указатель на экземпляр класса PIMA.</span><span class="sxs-lookup"><span data-stu-id="dcac2-368">**pima**: Pointer to the pima class instance.</span></span>
- <span data-ttu-id="dcac2-369">**object_handle**: дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="dcac2-369">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="dcac2-370">**object_buffer**: адрес буфера объектов.</span><span class="sxs-lookup"><span data-stu-id="dcac2-370">**object_buffer**: Object buffer address</span></span>
- <span data-ttu-id="dcac2-371">**object_length_requested**: длина данных объекта, запрошенная клиентом для приложения.</span><span class="sxs-lookup"><span data-stu-id="dcac2-371">**object_length_requested**: Object data length requested by the client to the application</span></span>
- <span data-ttu-id="dcac2-372">**object_actual_length**: длина данных объекта, возвращенная приложением.</span><span class="sxs-lookup"><span data-stu-id="dcac2-372">**object_actual_length**: Object data length returned by the application</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-373">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-373">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_data_get(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, UCHAR *object_buffer, ULONG object_offset,
    ULONG object_length_requested, ULONG *object_actual_length)
{

    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    UCHAR *pima_object_buffer;
    ULONG actual_length;
    UINT status;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Check the object handle. If this is handle 1 or 2 , we need to return the XML script object.
       If the handle is not 1 or 2, this is a JPEG picture or other object to be printed. */
    if ((object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE) ||
        (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST))
    {
        /* Check what XML object is requested. It is either a request script or a response. */
        if (object_handle == UX_PICTBRIDGE_OBJECT_HANDLE_HOST_RESPONSE)
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_host;
        else
            object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
                ux_pictbridge_object_client;

       /* Is this the corrent handle ? */
       if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
       {
           /* Get the pointer to the object buffer. */
           pima_object_buffer = object_info -> ux_device_class_pima_object_buffer;

           /* Copy the demanded object data portion. */
           ux_utility_memory_copy(object_buffer, pima_object_buffer +
               object_offset, object_length_requested);

           /* Update the length requested. for a demo, we do not do any checking. */
           *object_actual_length = object_length_requested;

           /* What cycle are we in ? */
           if (pictbridge -> ux_pictbridge_host_client_state_machine &
               UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST)
            {
                /* Check if we are blocking for a client request. */
                if (pictbridge -> ux_pictbridge_host_client_state_machine &
                    UX_PICTBRIDGE_STATE_MACHINE_CLIENT_REQUEST_PENDING)

                    /* Yes we are pending, send an event to release the pending request. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_STATE_MACHINE_READY, TX_OR);

               /* Since we are in host request, this indicates we are done with the cycle. */
               pictbridge -> ux_pictbridge_host_client_state_machine =
                   UX_PICTBRIDGE_STATE_MACHINE_IDLE;

            }

            /* We have copied the requested data. Return OK. */
            return(UX_SUCCESS);

        }
    }
    else
    {

        /* Get the object info from the job info structure. */
        object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
            ux_pictbridge_jobinfo.ux_pictbridge_jobinfo_object;

        /* Obtain the data from the application jobinfo callback. */
        status = pictbridge -> ux_pictbridge_jobinfo.
            ux_pictbridge_jobinfo_object_data_read(pictbridge, object_buffer, object_offset,
            object_length_requested, &actual_length);

        /* Save the length returned. */
        *object_actual_length = actual_length;

        /* Return the application status. */
        return(status);

    }

    /* Could not find the handle. */

    return(UX_DEVICE_CLASS_PIMA_RC_INVALID_OBJECT_HANDLE);
}
```

## <a name="ux_device_class_pima_object_info_send"></a><span data-ttu-id="dcac2-374">ux_device_class_pima_object_info_send</span><span class="sxs-lookup"><span data-stu-id="dcac2-374">ux_device_class_pima_object_info_send</span></span>

<span data-ttu-id="dcac2-375">Узел отправляет сведения об объекте.</span><span class="sxs-lookup"><span data-stu-id="dcac2-375">Host sends the object information</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-376">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-376">Prototype</span></span>

```C
UINT ux_device_class_pima_object_info_send(
    UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, 
    ULONG *object_handle);
```

### <a name="description"></a><span data-ttu-id="dcac2-377">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-377">Description</span></span>

<span data-ttu-id="dcac2-378">Эта функция вызывается, когда классу PIMA требуется получить сведения об объекте в локальной системе для хранения в будущем.</span><span class="sxs-lookup"><span data-stu-id="dcac2-378">This function is called when the PIMA class needs to receive the object information in the local system for future storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-379">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-379">Parameters</span></span>

- <span data-ttu-id="dcac2-380">**pima**: указатель на экземпляр класса PIMA.</span><span class="sxs-lookup"><span data-stu-id="dcac2-380">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="dcac2-381">**object**: указатель на объект.</span><span class="sxs-lookup"><span data-stu-id="dcac2-381">**object**:  Pointer to the object</span></span>
- <span data-ttu-id="dcac2-382">**object_handle**: дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="dcac2-382">**object_handle**: Handle of the object</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-383">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-383">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_info_send(UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, ULONG *object_handle)
{
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info; UCHAR
    string_discovery_name[UX_PICTBRIDGE_MAX_FILE_NAME_SIZE];

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* We only have one object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Copy the demanded object info set. */
    ux_utility_memory_copy(object_info, object,
        UX_SLAVE_CLASS_PIMA_OBJECT_DATA_LENGTH);

    /* Store the object handle. In Pictbridge we only receive XML scripts so the handle is hardwired to 1. */
    object_info -> ux_device_class_pima_object_handle_id = 1;
    *object_handle = 1;

    /* Check state machine. If we are in discovery pending mode, check file name of this object. */
    if (pictbridge -> ux_pictbridge_discovery_state ==
        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_PENDING)
    {
        /* We are in the discovery mode. Check for file name. It must match
           HDISCVRY.DPS in Unicode mode. */

        /* Check if this is a script. */
        if (object_info -> ux_device_class_pima_object_format ==
            UX_DEVICE_CLASS_PIMA_OFC_SCRIPT)
        {

            /* Yes this is a script. We need to search for the HDISCVRY.DPS file name. Get the file name in a ascii format. */
            ux_utility_unicode_to_string(object_info ->
                ux_device_class_pima_object_filename,
                string_discovery_name);

            /* Now, compare it to the HDISCVRY.DPS file name. Check length first. */
            if (ux_utility_string_length_get(_ux_pictbridge_hdiscovery_name)
                == ux_utility_string_length_get(string_discovery_name))
            {

                /* So far, the length of name of the files are the same. Compare names now. */
                if(ux_utility_memory_compare(_ux_pictbridge_hdiscovery_name,
                    string_discovery_name,
                    ux_utility_string_length_get(string_discovery_name)) == UX_SUCCESS)
                {
                    /* We are done with discovery of the printer. We can now send notifications when the camera wants to print an object. */
                    pictbridge -> ux_pictbridge_discovery_state =
                        UX_PICTBRIDGE_DPSCLIENT_DISCOVERY_COMPLETE;

                    /* Set an event flag if the application is listening. */
                    ux_utility_event_flags_set(&pictbridge ->
                        ux_pictbridge_event_flags_group,
                        UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY, TX_OR);

                    /* There is no object during th discovery cycle. */
                    return(UX_SUCCESS);
                }
            }
        }
    }
    /* What cycle are we in ? */
    if (pictbridge -> ux_pictbridge_host_client_state_machine ==
        UX_PICTBRIDGE_STATE_MACHINE_IDLE)

        /* Since we are in idle state, we must have received a request from the host. */
        pictbridge -> ux_pictbridge_host_client_state_machine =
            UX_PICTBRIDGE_STATE_MACHINE_HOST_REQUEST;

    /* We have copied the requested data. Return OK. */
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_data_send"></a><span data-ttu-id="dcac2-384">ux_device_class_pima_object_data_send</span><span class="sxs-lookup"><span data-stu-id="dcac2-384">ux_device_class_pima_object_data_send</span></span>

<span data-ttu-id="dcac2-385">Узел отправляет данные объекта.</span><span class="sxs-lookup"><span data-stu-id="dcac2-385">Host sends the object data</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-386">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-386">Prototype</span></span>

```C
UINT ux_device_class_pima_object_data_send(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, 
    ULONG phase, 
    UCHAR *object_buffer,
    ULONG object_offset, 
    ULONG object_length);
```

### <a name="description"></a><span data-ttu-id="dcac2-387">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-387">Description</span></span>

<span data-ttu-id="dcac2-388">Эта функция вызывается, когда классу PIMA требуется получить данные объекта в локальной системе для хранения.</span><span class="sxs-lookup"><span data-stu-id="dcac2-388">This function is called when the PIMA class needs to receive the object data in the local system for storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-389">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-389">Parameters</span></span>

- <span data-ttu-id="dcac2-390">**pima**: указатель на экземпляр класса PIMA.</span><span class="sxs-lookup"><span data-stu-id="dcac2-390">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="dcac2-391">**object_handle**: дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="dcac2-391">**object_handle**: Handle of the object</span></span>
- <span data-ttu-id="dcac2-392">**phase**: этап передачи (активный или полный).</span><span class="sxs-lookup"><span data-stu-id="dcac2-392">**phase**: phase of the transfer (active or complete)</span></span>
- <span data-ttu-id="dcac2-393">**object_buffer**: адрес буфера объектов.</span><span class="sxs-lookup"><span data-stu-id="dcac2-393">**object_buffer**: Object buffer address</span></span>
- <span data-ttu-id="dcac2-394">**object_offset**: адрес данных.</span><span class="sxs-lookup"><span data-stu-id="dcac2-394">**object_offset**: Address of data</span></span>
- <span data-ttu-id="dcac2-395">**object_length**: длина данных объекта, отправленная приложением.</span><span class="sxs-lookup"><span data-stu-id="dcac2-395">**object_length**: Object data length sent by application</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-396">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-396">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_data_send(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    ULONG phase,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length)
{
    UINT status;
    UX_PICTBRIDGE *pictbridge;
    UX_SLAVE_CLASS_PIMA_OBJECT *object_info;
    ULONG event_flag;
    UCHAR *pima_object_buffer;

    /* Get the pointer to the Pictbridge instance. */
    pictbridge = (UX_PICTBRIDGE *)pima -> ux_device_class_pima_application;

    /* Get the pointer to the pima object. */
    object_info = (UX_SLAVE_CLASS_PIMA_OBJECT *) pictbridge ->
        ux_pictbridge_object_host;

    /* Is this the corrent handle ? */
    if (object_info -> ux_device_class_pima_object_handle_id == object_handle)
    {
        /* Get the pointer to the object buffer. */
        pima_object_buffer = object_info ->
            ux_device_class_pima_object_buffer;

        /* Check the phase. We should wait for the object to be completed and the response sent back before parsing the object. */
        if (phase == UX_DEVICE_CLASS_PIMA_OBJECT_TRANSFER_PHASE_ACTIVE)
        {
            /* Copy the demanded object data portion. */
            ux_utility_memory_copy(pima_object_buffer + object_offset,
                object_buffer, object_length);

            /* Save the length of this object. */
            object_info -> ux_device_class_pima_object_length = object_length;

            /* We are not done yet. */
            return(UX_SUCCESS);
        }
        else
        {
            /* Completion of transfer. We are done. */
            return(UX_SUCCESS);
        }
    }
}
```

## <a name="ux_device_class_pima_object_delete"></a><span data-ttu-id="dcac2-397">ux_device_class_pima_object_delete</span><span class="sxs-lookup"><span data-stu-id="dcac2-397">ux_device_class_pima_object_delete</span></span>

<span data-ttu-id="dcac2-398">Удаление локального объекта.</span><span class="sxs-lookup"><span data-stu-id="dcac2-398">Delete a local object</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-399">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-399">Prototype</span></span>

```C
UINT ux_device_class_pima_object_delete(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle);
```

### <a name="description"></a><span data-ttu-id="dcac2-400">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-400">Description</span></span>

<span data-ttu-id="dcac2-401">Эта функция вызывается, когда классу PIMA требуется удалить объект в локальном хранилище.</span><span class="sxs-lookup"><span data-stu-id="dcac2-401">This function is called when the PIMA class needs to delete an object on the local storage.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-402">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-402">Parameters</span></span>

- <span data-ttu-id="dcac2-403">**pima**: указатель на экземпляр класса PIMA.</span><span class="sxs-lookup"><span data-stu-id="dcac2-403">**pima**: Pointer to the pima class instance</span></span>
- <span data-ttu-id="dcac2-404">**object_handle**: дескриптор объекта.</span><span class="sxs-lookup"><span data-stu-id="dcac2-404">**object_handle**: Handle of the object</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-405">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-405">Example</span></span>

```C
UINT ux_pictbridge_dpsclient_object_delete(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle)
{
    /* Delete the object pointer by the handle. */

}
```

## <a name="usb-device-audio-class"></a><span data-ttu-id="dcac2-406">Класс Audio USB-устройства</span><span class="sxs-lookup"><span data-stu-id="dcac2-406">USB Device Audio Class</span></span>

<span data-ttu-id="dcac2-407">Класс Audio USB-устройства позволяет хост-системе USB обмениваться данными с устройством в качестве звукового устройства.</span><span class="sxs-lookup"><span data-stu-id="dcac2-407">The USB device Audio class allows for a USB host system to communicate with the device as an audio device.</span></span> <span data-ttu-id="dcac2-408">Этот класс основан на стандарте USB и стандарте USB Audio Class 1.0 или 2.0.</span><span class="sxs-lookup"><span data-stu-id="dcac2-408">This class is based on the USB standard and USB Audio Class 1.0 or 2.0 standard.</span></span>

<span data-ttu-id="dcac2-409">В стеке устройств необходимо объявить совместимую с USB Audio платформу устройств.</span><span class="sxs-lookup"><span data-stu-id="dcac2-409">A USB audio compliant device framework needs to be declared by the device stack.</span></span> <span data-ttu-id="dcac2-410">Ниже приведен пример динамика Audio 2.0.</span><span class="sxs-lookup"><span data-stu-id="dcac2-410">An example of an Audio 2.0 speaker follows:</span></span>

```C
unsigned char device_framework_high_speed[] = {

    /* --- Device Descriptor 18 bytes
    0x00 bDeviceClass: Refer to interface
    0x00 bDeviceSubclass: Refer to interface
    0x00 bDeviceProtocol: Refer to interface

    idVendor & idProduct - https://www.linux-usb.org/usb.ids
    */

    /* 0 bLength, bDescriptorType */ 18, 0x01,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00, 0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 0x08,
    /* 8 idVendor, idProduct */ 0x84, 0x84, 0x03, 0x00,
    /* 12 bcdDevice */ 0x00, 0x02,
    /* 14 iManufacturer, iProduct, iSerialNumber */ 0, 0, 0,
    /* 17 bNumConfigurations */ 1,
    /* ---------------- Device Qualifier Descriptor */
    /* 0 bLength, bDescriptorType */ 10, 0x06,
    /* 2 bcdUSB : 0x200 (2.00) */ 0x00,0x02,
    /* 4 bDeviceClass : 0x00 (see interface) */ 0x00,
    /* 5 bDeviceSubClass : 0x00 (see interface) */ 0x00,
    /* 6 bDeviceProtocol : 0x00 (see interface) */ 0x00,
    /* 7 bMaxPacketSize0 */ 8,
    /* 8 bNumConfigurations */ 1,
    /* 9 bReserved */ 0,
    /* --- Configuration Descriptor (9+8+73+55=145, 0x91) */
    /* 0 bLength, bDescriptorType */ 9, 0x02,
    /* 2 wTotalLength */ 145, 0,
    /* 4 bNumInterfaces, bConfigurationValue */ 2, 1,
    /* 6 iConfiguration */ 0,
    /* 7 bmAttributes, bMaxPower */ 0x80, 50,
    /* ----------- Interface Association Descriptor */
    /* 0 bLength, bDescriptorType */ 8, 0x0B,
    /* 2 bFirstInterface, bInterfaceCount */ 0, 2,
    /* 4 bFunctionClass : 0x01 (Audio) */ 0x01,
    /* 5 bFunctionSubClass : 0x00 (UNDEFINED) */ 0x00,
    /* 6 bFunctionProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 7 iFunction */ 0,
    /* --- Interface Descriptor #0: Control (9+64=73) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 0, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioControl) */ 0x01,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* --- Audio 2.0 AC Interface Header Descriptor (9+8+17+18+12=64, 0x40) */
    /* 0 bLength */ 9,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bcdADC */ 0x00, 0x02,
    /* 5 bCategory : 0x08 (IO Box) */ 0x08,
    /* 6 wTotalLength */ 64, 0,
    /* 8 bmControls */ 0x00,
    /* -------- Audio 2.0 AC Clock Source Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x0A,
    /* 3 bClockID */ 0x10,
    /* 4 bmAttributes : 0x05 (Sync|InternalFixedClk) */ 0x05,
    /* 5 bmControls : 0x01 (FreqReadOnly) */ 0x01,
    /* 6 bAssocTerminal, iClockSource */ 0x00, 0,
    /* ------ Audio 2.0 AC Input Terminal Descriptor */
    /* 0 bLength */ 17,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02, /* 3 bTerminalID */ 0x04,
    /* 4 wTerminalType : 0x0101 (USB Streaming) */ 0x01, 0x01,
    /* 6 bAssocTerminal, bCSourceID */ 0x00, 0x10,
    /* 8 bNrChannels */ 2,
    /* 9 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 13 iChannelNames, bmControls, iTerminal */ 0, 0x00, 0x00, 0,
    /* -------- Audio 2.0 AC Feature Unit Descriptor */
    /* 0 bLength */ 18,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x06,
    /* 3 bUnitID, bSourceID */ 0x05, 0x04,
    /* 5 bmaControls(0) : 0x0F (VolumeRW|MuteRW) */ 0x0F, 0x00, 0x00, 0x00,
    /* 9 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* 13 bmaControls(1) : 0x00000000 */ 0x00, 0x00, 0x00, 0x00,
    /* . iFeature */ 0,
    /* ----- Audio 2.0 AC Output Terminal Descriptor */
    /* 0 bLength */ 12,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x03, /* 3 bTerminalID */ 0x06,
    /* 4 wTerminalType : 0x0301 (Speaker) */ 0x01, 0x03,
    /* 6 bAssocTerminal, bSourceID, bCSourceID */ 0x00, 0x05, 0x10,
    /* 9 bmControls, iTerminal */ 0x00, 0x00, 0,
    /* --- Interface Descriptor #1: Stream OUT (9+9+16+6+7+8=55) */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 0,
    /* 4 bNumEndpoints */ 0,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------------------- Interface Descriptor */
    /* 0 bLength, bDescriptorType */ 9, 0x04,
    /* 2 bInterfaceNumber, bAlternateSetting */ 1, 1,
    /* 4 bNumEndpoints */ 1,
    /* 5 bInterfaceClass : 0x01 (Audio) */ 0x01,
    /* 6 bInterfaceSubClass : 0x01 (AudioStream) */ 0x02,
    /* 7 bInterfaceProtocol : 0x20 (VERSION_02_00) */ 0x20,
    /* 8 iInterface */ 0,
    /* ----------- Audio 2.0 AS Interface Descriptor */
    /* 0 bLength */ 16,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x01,
    /* 3 bTerminalLink, bmControls */ 0x04, 0x00,
    /* 5 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 6 bmFormats : 0x000000001 (PCM) */ 0x01, 0x00, 0x00, 0x00, /* 10 bNrChannels */ 2,
    /* 11 bmChannelConfig */ 0x00, 0x00, 0x00, 0x00,
    /* 15 iChannelNames */ 0, /* --------- Audio 2.0 AS Format Type Descriptor */
    /* 0 bLength */ 6,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x24, 0x02,
    /* 3 bFormatType : 0x01 (FORMAT_TYPE_I) */ 0x01,
    /* 4 bSubslotSize, bBitResolution */ 2, 16,
    /* ------------------------- Endpoint Descriptor */
    /* 0 bLength, bDescriptorType */ 7, 0x05,
    /* 2 bEndpointAddress */ 0x02,
    /* 3 bmAttributes : 0x0D (Sync|ISO) */ 0x0D,
    /* 4 wMaxPacketSize : 0x0100 (256) */ 0x00, 0x01,
    /* 6 bInterval : 0x04 (1ms) */ 4,
    /* - Audio 2.0 AS ISO Audio Data Endpoint Descriptor */
    /* 0 bLength */ 8,
    /* 1 bDescriptorType, bDescriptorSubtype */ 0x25, 0x01,
    /* 3 bmAttributes, bmControls */ 0x00, 0x00,
    /* 5 bLockDelayUnits, wLockDelay */ 0x00, 0x00, 0x00,
};
```

<span data-ttu-id="dcac2-411">Класс Audio использует составную платформу устройств для группирования интерфейсов (для управления и потоковой передачи).</span><span class="sxs-lookup"><span data-stu-id="dcac2-411">The Audio class uses a composite device framework to group interfaces (control and streaming).</span></span> <span data-ttu-id="dcac2-412">В результате при определении дескриптора устройства следует проявлять осторожность.</span><span class="sxs-lookup"><span data-stu-id="dcac2-412">As a result care should be taken when defining the device descriptor.</span></span> <span data-ttu-id="dcac2-413">USBX использует дескриптор IAD для определения внутреннего порядка привязки интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="dcac2-413">USBX relies on the IAD descriptor to know internally how to bind interfaces.</span></span> <span data-ttu-id="dcac2-414">Дескриптор IAD должен быть объявлен перед интерфейсами (интерфейс AudioControl, за которым следует один или несколько интерфейсов AudioStreaming) и содержать первый интерфейс класса Audio (интерфейс AudioControl) и число подключенных интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="dcac2-414">The IAD descriptor should be declared before the interfaces (an AudioControl interface followed by one or more AudioStreaming interfaces) and contain the first interface of the Audio class (the AudioControl interface) and how many interfaces are attached.</span></span>

<span data-ttu-id="dcac2-415">Способ работы класса Audio зависит от того, отправляет или принимает устройство звук, но в обоих случаях используется FIFO для хранения буферов аудиокадров: если устройство отправляет звук на узел, приложение добавляет в FIFO буферы аудиокадров, которые позже отправляются USBX на узел; если устройство принимает звук с узла, USBX добавляет в FIFO буферы аудиокадров, полученные от узла, которые позже считываются приложением.</span><span class="sxs-lookup"><span data-stu-id="dcac2-415">The way the audio class works depends on whether the device is sending or receiving audio, but both cases use a FIFO for storing audio frame buffers: if the device is sending audio to the host, then the application adds audio frame buffers to the FIFO which are later sent to the host by USBX; if the device is receiving audio from the host, then USBX adds the audio frame buffers received from the host to the FIFO which are later read by the application.</span></span> <span data-ttu-id="dcac2-416">Каждый аудиопоток имеет собственный FIFO, а каждый буфер аудиокадров состоит из нескольких выборок.</span><span class="sxs-lookup"><span data-stu-id="dcac2-416">Each audio stream has its own FIFO, and each audio frame buffer consists of multiple samples.</span></span>

<span data-ttu-id="dcac2-417">При инициализации класса Audio ожидаются следующие компоненты.</span><span class="sxs-lookup"><span data-stu-id="dcac2-417">The initialization of the Audio class expects the following parts.</span></span>

1. <span data-ttu-id="dcac2-418">Класс Audio ожидает следующие параметры потоковой передачи:</span><span class="sxs-lookup"><span data-stu-id="dcac2-418">Audio class expects the following streaming parameters:</span></span>

   ```C
   /* Set the parameters for Audio streams. */
   /* Set the application-defined callback that is invoked when the
      host requests a change to the alternate setting. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_change = demo_audio_read_change;

   /* Set the application-defined callback that is invoked whenever
      a USB packet (audio frame) is sent to or received from the host. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_callbacks
       .ux_device_class_audio_stream_frame_done = demo_audio_read_done;

   /* Set the number of audio frame buffers in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_nb = UX_DEMO_FRAME_BUFFER_NB;

   /* Set the maximum size of each audio frame buffer in the FIFO. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_max_frame _buffer_size = UX_DEMO_MAX_FRAME_SIZE;

   /* Set the internally-defined audio processing thread entry pointer. If the application wishes to receive audio from the host
      (which is the case in this example), ux_device_class_audio_read_thread_entry should be used;
      if the application wishes to send data to the host, ux_device_class_audio_write_thread_entry should be used. */
   audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry = ux_device_class_audio_read_thread_entry;
   ```

2. <span data-ttu-id="dcac2-419">Класс Audio ожидает следующие параметры функций:</span><span class="sxs-lookup"><span data-stu-id="dcac2-419">Audio class expects the following function parameters.</span></span>

   ```C
   /* Set the parameters for Audio device. */

   /* Set the number of streams. */
   audio_parameter.ux_device_class_audio_parameter_streams_nb = 1;

   /* Set the pointer to the first audio stream parameter.
      Note that we initialized this parameter in the previous section.
      Also note that for more than one streams, this should be an array. */
   audio_parameter.ux_device_class_audio_parameter_streams = audio_stream_parameter;

   /* Set the application-defined callback that is invoked when the audio class
      is activated i.e. device is connected to host. */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_activate = demo_audio_instance_activate;

   /* Set the application-defined callback that is invoked when the audio class
      is deactivated i.e. device is disconnected from host. */

   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_slave_class_audio_instance_deactivate = demo_audio_instance_deactivate;

   /* Set the application-defined callback that is invoked when the stack receives a control request from the host.
      See below for more details.
   */
   audio_parameter.ux_device_class_audio_parameter_callbacks
       .ux_device_class_audio_control_process = demo_audio20_request_process;

   /* Initialize the device Audio class. This class owns interfaces starting with 0. */
   status = ux_device_stack_class_register(_ux_system_slave_class_audio_name,
       ux_device_class_audio_entry, 1, 0, &audio_parameter);
   if(status!=UX_SUCCESS)
       return;
   ```

   <span data-ttu-id="dcac2-420">Определяемый приложением обратный вызов запроса управления (***ux_device_class_audio_control_process***, заданный в предыдущем примере) выполняется, когда стек получает запрос управления от узла.</span><span class="sxs-lookup"><span data-stu-id="dcac2-420">The application-defined control request callback (***ux_device_class_audio_control_process***; set in the previous example) is invoked when the stack receives a control request from the host.</span></span> <span data-ttu-id="dcac2-421">Если запрос принят и обработан (подтвержден или остановлен), обратный вызов должен вернуть данные об успешном выполнении, в противном случае должна возвращаться ошибка.</span><span class="sxs-lookup"><span data-stu-id="dcac2-421">If the request is accepted and handled (acknowledged or stalled) the callback must return success, otherwise error should be returned.</span></span>

   <span data-ttu-id="dcac2-422">Процесс запроса управления, относящегося к классу, определяется как определяемый приложением обратный вызов, так как запросы управления сильно различаются между версиями USB Audio и большая часть процесса запроса связана с платформой устройств.</span><span class="sxs-lookup"><span data-stu-id="dcac2-422">The class-specific control request process is defined as an application-defined callback because the control requests are very different between USB Audio versions and a large part of the request process relates to the device framework.</span></span> <span data-ttu-id="dcac2-423">Чтобы устройство функционировало, приложение должно правильно обрабатывать запросы.</span><span class="sxs-lookup"><span data-stu-id="dcac2-423">The application should handle requests correctly to make the device functional.</span></span>

   <span data-ttu-id="dcac2-424">Так как для звукового устройства громкость, отключение звука и частота выборки относятся к типичным запросам управления, в последующих разделах представлены простые внутренние обратные вызовы для различных версий USB Audio, которые могут использовать приложения.</span><span class="sxs-lookup"><span data-stu-id="dcac2-424">Since for an audio device, volume, mute and sampling frequency are common control requests, simple, internally-defined callbacks for different USB audio versions are introduced in later sections for applications to use.</span></span> <span data-ttu-id="dcac2-425">Дополнительные сведения см. в описании \***ux_device_class_audio10_control_process** _ и _ \*_ux_device_class_audio_control_request_\*\*.</span><span class="sxs-lookup"><span data-stu-id="dcac2-425">Refer to ***ux_device_class_audio10_control_process** _ and _ *_ux_device_class_audio_control_request_** for more details.</span></span>

<span data-ttu-id="dcac2-426">В платформе устройств устройства Audio идентификаторы PID/VID хранятся в дескрипторе устройства (см. дескриптор устройства, объявленный выше).</span><span class="sxs-lookup"><span data-stu-id="dcac2-426">In the device framework of the Audio device, the PID/VID are stored in the device descriptor (see the device descriptor declared above).</span></span>

<span data-ttu-id="dcac2-427">Когда хост-система USB обнаруживает устройство USB Audio и подключает класс Audio, устройство можно использовать с любым проигрывателем или устройством записи (в зависимости от платформы).</span><span class="sxs-lookup"><span data-stu-id="dcac2-427">When a USB host system discovers the USB Audio device and mounts the audio class, the device can be used with any audio player or recorder (depending on the framework).</span></span> <span data-ttu-id="dcac2-428">Подробнее см. в разделе "Операционная система узла".</span><span class="sxs-lookup"><span data-stu-id="dcac2-428">See the host Operating System for reference.</span></span>

<span data-ttu-id="dcac2-429">Интерфейсы API класса Audio определены ниже.</span><span class="sxs-lookup"><span data-stu-id="dcac2-429">The Audio class APIs are defined below.</span></span>

## <a name="ux_device_class_audio_read_thread_entry"></a><span data-ttu-id="dcac2-430">ux_device_class_audio_read_thread_entry</span><span class="sxs-lookup"><span data-stu-id="dcac2-430">ux_device_class_audio_read_thread_entry</span></span>

<span data-ttu-id="dcac2-431">Запись потока для чтения данных для функции Audio.</span><span class="sxs-lookup"><span data-stu-id="dcac2-431">Thread entry for reading data for the Audio function.</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-432">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-432">Prototype</span></span>

```C
VOID ux_device_class_audio_read_thread_entry(ULONG audio_stream);
```

### <a name="description"></a><span data-ttu-id="dcac2-433">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-433">Description</span></span>

<span data-ttu-id="dcac2-434">Эта функция передается в параметр инициализации аудиопотока, если требуется считывание звука с узла.</span><span class="sxs-lookup"><span data-stu-id="dcac2-434">This function is passed to the audio stream initialization parameter if reading audio from the host is desired.</span></span> <span data-ttu-id="dcac2-435">На внутреннем уровне создается поток с этой функцией в качестве входной функции, он сам считывает звуковые данные через изохронную конечную точку OUT в функции Audio.</span><span class="sxs-lookup"><span data-stu-id="dcac2-435">Internally, a thread is created with this function as its entry function; the thread itself reads audio data through the isochronous OUT endpoint in the Audio function.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-436">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-436">Parameters</span></span>

- <span data-ttu-id="dcac2-437">**audio_stream**: указатель на экземпляр аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-437">**audio_stream**: Pointer to the audio stream instance.</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-438">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-438">Example</span></span>

```C
/* Set parameter to initialize a stream for reading. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry
     = ux_device_class_audio_read_thread_entry;
```

## <a name="ux_device_class_audio_write_thread_entry"></a><span data-ttu-id="dcac2-439">ux_device_class_audio_write_thread_entry</span><span class="sxs-lookup"><span data-stu-id="dcac2-439">ux_device_class_audio_write_thread_entry</span></span>

<span data-ttu-id="dcac2-440">Запись потока для записи данных для функции Audio.</span><span class="sxs-lookup"><span data-stu-id="dcac2-440">Thread entry for writing data for the Audio function</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-441">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-441">Prototype</span></span>

```C
VOID ux_device_class_audio_write_thread_entry(ULONG audio_stream);
```

### <a name="description"></a><span data-ttu-id="dcac2-442">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-442">Description</span></span>

<span data-ttu-id="dcac2-443">Эта функция передается в параметр инициализации аудиопотока, если требуется запись звука на узел.</span><span class="sxs-lookup"><span data-stu-id="dcac2-443">This function is passed to the audio stream initialization parameter if writing audio to the host is desired.</span></span> <span data-ttu-id="dcac2-444">На внутреннем уровне создается поток с этой функцией в качестве входной функции, он сам записывает звуковые данные через изохронную конечную точку IN в функции Audio.</span><span class="sxs-lookup"><span data-stu-id="dcac2-444">Internally, a thread is created with this function as its entry function; the thread itself writes audio data through the isochronous IN endpoint in the Audio function.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-445">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-445">Parameters</span></span>

- <span data-ttu-id="dcac2-446">**audio_stream**: указатель на экземпляр аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-446">**audio_stream**: Pointer to the audio stream instance.</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-447">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-447">Example</span></span>

```C
/* Set parameter to initialize as stream for writing. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_en
    try = ux_device_class_audio_write_thread_entry;
```

## <a name="ux_device_class_audio_stream_get"></a><span data-ttu-id="dcac2-448">ux_device_class_audio_stream_get</span><span class="sxs-lookup"><span data-stu-id="dcac2-448">ux_device_class_audio_stream_get</span></span>

<span data-ttu-id="dcac2-449">Получение конкретного экземпляра потока для функции Audio.</span><span class="sxs-lookup"><span data-stu-id="dcac2-449">Get specific stream instance for the Audio function</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-450">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-450">Prototype</span></span>

```C
UINT ux_device_class_audio_stream_get(
    UX_DEVICE_CLASS_AUDIO *audio,
    ULONG stream_index, 
    UX_DEVICE_CLASS_AUDIO_STREAM **stream);
```

### <a name="description"></a><span data-ttu-id="dcac2-451">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-451">Description</span></span>

<span data-ttu-id="dcac2-452">Эта функция используется для получения экземпляра потока класса Audio.</span><span class="sxs-lookup"><span data-stu-id="dcac2-452">This function is used to get a stream instance of audio class.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-453">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-453">Parameters</span></span>

- <span data-ttu-id="dcac2-454">**audio**: указатель на экземпляр звука.</span><span class="sxs-lookup"><span data-stu-id="dcac2-454">**audio**: Pointer to the audio instance</span></span>
- <span data-ttu-id="dcac2-455">**stream_index**: индекс экземпляра потока, отчитываемый от 0.</span><span class="sxs-lookup"><span data-stu-id="dcac2-455">**stream_index**: Stream instance index based on 0</span></span>
- <span data-ttu-id="dcac2-456">**stream**: указатель на буфер для хранения указателя экземпляра аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-456">**stream**: Pointer to buffer to store the audio stream instance pointer</span></span>

### <a name="return-value"></a><span data-ttu-id="dcac2-457">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dcac2-457">Return Value</span></span>

- <span data-ttu-id="dcac2-458">**UX_SUCCESS** (0x00): операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="dcac2-458">**UX_SUCCESS** (0x00) This operation was successful</span></span>
- <span data-ttu-id="dcac2-459">**UX_ERROR** (0xFF): ошибка в функции.</span><span class="sxs-lookup"><span data-stu-id="dcac2-459">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-460">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-460">Example</span></span>

```C
/* Get audio stream instance. */
status = ux_device_class_audio_stream_get(audio, 0, &stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_reception_start"></a><span data-ttu-id="dcac2-461">ux_device_class_audio_reception_start</span><span class="sxs-lookup"><span data-stu-id="dcac2-461">ux_device_class_audio_reception_start</span></span>

<span data-ttu-id="dcac2-462">Запуск получения звуковых данных для аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-462">Start audio data reception for the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-463">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-463">Prototype</span></span>

```C
UINT ux_device_class_audio_reception_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="dcac2-464">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-464">Description</span></span>

<span data-ttu-id="dcac2-465">Эта функция используется для запуска чтения звуковых данных в аудиопотоках.</span><span class="sxs-lookup"><span data-stu-id="dcac2-465">This function is used to start audio data reading in audio streams.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-466">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-466">Parameters</span></span>

- <span data-ttu-id="dcac2-467">**stream**: указатель на экземпляр аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-467">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="dcac2-468">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dcac2-468">Return Value</span></span>

- <span data-ttu-id="dcac2-469">**UX_SUCCESS** (0x00): операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="dcac2-469">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="dcac2-470">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.</span><span class="sxs-lookup"><span data-stu-id="dcac2-470">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="dcac2-471">**UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO заполнен.</span><span class="sxs-lookup"><span data-stu-id="dcac2-471">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="dcac2-472">**UX_ERROR** (0xFF): ошибка в функции.</span><span class="sxs-lookup"><span data-stu-id="dcac2-472">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-473">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-473">Example</span></span>

```C
/* Start stream data reception. */
status = ux_device_class_audio_reception_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read8"></a><span data-ttu-id="dcac2-474">ux_device_class_audio_sample_read8</span><span class="sxs-lookup"><span data-stu-id="dcac2-474">ux_device_class_audio_sample_read8</span></span>

<span data-ttu-id="dcac2-475">Чтение 8-разрядной выборки из аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-475">Read 8-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-476">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-476">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read8(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    UCHAR *buffer);
```

### <a name="description"></a><span data-ttu-id="dcac2-477">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-477">Description</span></span>

<span data-ttu-id="dcac2-478">Эта функция считывает данные 8-разрядной аудиовыборки из указанного потока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-478">This function reads 8-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="dcac2-479">В частности, она считывает данные выборки из текущего буфера аудиокадров в FIFO.</span><span class="sxs-lookup"><span data-stu-id="dcac2-479">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="dcac2-480">После чтения последней выборки в аудиокадре он будет автоматически освобожден, чтобы его можно было использовать для приема дополнительных данных от узла.</span><span class="sxs-lookup"><span data-stu-id="dcac2-480">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-481">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-481">Parameters</span></span>

- <span data-ttu-id="dcac2-482">**stream**: указатель на экземпляр аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-482">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="dcac2-483">**buffer**: указатель на буфер для сохранения байта выборки.</span><span class="sxs-lookup"><span data-stu-id="dcac2-483">**buffer**: Pointer to the buffer to save sample byte.</span></span>

### <a name="return-value"></a><span data-ttu-id="dcac2-484">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dcac2-484">Return Value</span></span>

- <span data-ttu-id="dcac2-485">**UX_SUCCESS** (0x00): операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="dcac2-485">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="dcac2-486">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.</span><span class="sxs-lookup"><span data-stu-id="dcac2-486">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="dcac2-487">**UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="dcac2-487">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="dcac2-488">**UX_ERROR** (0xFF): ошибка в функции.</span><span class="sxs-lookup"><span data-stu-id="dcac2-488">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-489">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-489">Example</span></span>

```C
/* Read a byte in audio FIFO. */

status = ux_device_class_audio_sample_read8(stream, &sample_byte);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read16"></a><span data-ttu-id="dcac2-490">ux_device_class_audio_sample_read16</span><span class="sxs-lookup"><span data-stu-id="dcac2-490">ux_device_class_audio_sample_read16</span></span>

<span data-ttu-id="dcac2-491">Чтение 16-разрядной выборки из аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-491">Read 16-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-492">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-492">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read16(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    USHORT *buffer);
```

### <a name="description"></a><span data-ttu-id="dcac2-493">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-493">Description</span></span>

<span data-ttu-id="dcac2-494">Эта функция считывает данные 16-разрядной аудиовыборки из указанного потока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-494">This function reads 16-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="dcac2-495">В частности, она считывает данные выборки из текущего буфера аудиокадров в FIFO.</span><span class="sxs-lookup"><span data-stu-id="dcac2-495">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="dcac2-496">После чтения последней выборки в аудиокадре он будет автоматически освобожден, чтобы его можно было использовать для приема дополнительных данных от узла.</span><span class="sxs-lookup"><span data-stu-id="dcac2-496">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-497">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-497">Parameters</span></span>

- <span data-ttu-id="dcac2-498">**stream**: указатель на экземпляр аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-498">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="dcac2-499">**buffer**: указатель на буфер для сохранения 16-разрядной выборки.</span><span class="sxs-lookup"><span data-stu-id="dcac2-499">**buffer**: Pointer to the buffer to save the 16-bit sample.</span></span>

### <a name="return-value"></a><span data-ttu-id="dcac2-500">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dcac2-500">Return Value</span></span>

- <span data-ttu-id="dcac2-501">**UX_SUCCESS** (0x00): операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="dcac2-501">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="dcac2-502">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.</span><span class="sxs-lookup"><span data-stu-id="dcac2-502">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="dcac2-503">**UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="dcac2-503">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="dcac2-504">**UX_ERROR** (0xFF): ошибка в функции.</span><span class="sxs-lookup"><span data-stu-id="dcac2-504">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-505">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-505">Example</span></span>

```C
/* Read a 16-bit sample in audio FIFO. */

status = ux_device_class_audio_sample_read16(stream, &sample_word);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read24"></a><span data-ttu-id="dcac2-506">ux_device_class_audio_sample_read24</span><span class="sxs-lookup"><span data-stu-id="dcac2-506">ux_device_class_audio_sample_read24</span></span>

<span data-ttu-id="dcac2-507">Чтение 24-разрядной выборки из аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-507">Read 24-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-508">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-508">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read24(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a><span data-ttu-id="dcac2-509">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-509">Description</span></span>

<span data-ttu-id="dcac2-510">Эта функция считывает данные 24-разрядной аудиовыборки из указанного потока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-510">This function reads 24-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="dcac2-511">В частности, она считывает данные выборки из текущего буфера аудиокадров в FIFO.</span><span class="sxs-lookup"><span data-stu-id="dcac2-511">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="dcac2-512">После чтения последней выборки в аудиокадре он будет автоматически освобожден, чтобы его можно было использовать для приема дополнительных данных от узла.</span><span class="sxs-lookup"><span data-stu-id="dcac2-512">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-513">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-513">Parameters</span></span>

- <span data-ttu-id="dcac2-514">**stream**: указатель на экземпляр аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-514">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="dcac2-515">**buffer**: указатель на буфер для сохранения 3-байтовой выборки.</span><span class="sxs-lookup"><span data-stu-id="dcac2-515">**buffer**: Pointer to the buffer to save the 3-byte sample.</span></span>

### <a name="return-value"></a><span data-ttu-id="dcac2-516">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dcac2-516">Return Value</span></span>

- <span data-ttu-id="dcac2-517">**UX_SUCCESS** (0x00): операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="dcac2-517">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="dcac2-518">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.</span><span class="sxs-lookup"><span data-stu-id="dcac2-518">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="dcac2-519">**UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="dcac2-519">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="dcac2-520">**UX_ERROR** (0xFF): ошибка в функции.</span><span class="sxs-lookup"><span data-stu-id="dcac2-520">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-521">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-521">Example</span></span>

```C
/* Read 3 bytes to in audio FIFO. */

status = ux_device_class_audio_sample_read24(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read32"></a><span data-ttu-id="dcac2-522">ux_device_class_audio_sample_read32</span><span class="sxs-lookup"><span data-stu-id="dcac2-522">ux_device_class_audio_sample_read32</span></span>

<span data-ttu-id="dcac2-523">Чтение 32-разрядной выборки из аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-523">Read 32-bit sample from the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-524">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-524">Prototype</span></span>

```C
UINT ux_device_class_audio_sample_read32(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a><span data-ttu-id="dcac2-525">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-525">Description</span></span>

<span data-ttu-id="dcac2-526">Эта функция считывает данные 32-разрядной аудиовыборки из указанного потока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-526">This function reads 32-bit audio sample data from the specified stream.</span></span>

<span data-ttu-id="dcac2-527">В частности, она считывает данные выборки из текущего буфера аудиокадров в FIFO.</span><span class="sxs-lookup"><span data-stu-id="dcac2-527">Specifically, it reads the sample data from the current audio frame buffer in the FIFO.</span></span> <span data-ttu-id="dcac2-528">После чтения последней выборки в аудиокадре он будет автоматически освобожден, чтобы его можно было использовать для приема дополнительных данных от узла.</span><span class="sxs-lookup"><span data-stu-id="dcac2-528">Upon reading the last sample in an audio frame, the frame will be automatically freed so that it can be used to accept more data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-529">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-529">Parameters</span></span>

- <span data-ttu-id="dcac2-530">**stream**: указатель на экземпляр аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-530">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="dcac2-531">**buffer**: указатель на буфер для сохранения 4-байтовых данных.</span><span class="sxs-lookup"><span data-stu-id="dcac2-531">**buffer**: Pointer to the buffer to save the 4-byte data.</span></span>

### <a name="return-value"></a><span data-ttu-id="dcac2-532">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dcac2-532">Return Value</span></span>

- <span data-ttu-id="dcac2-533">**UX_SUCCESS** (0x00): операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="dcac2-533">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="dcac2-534">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.</span><span class="sxs-lookup"><span data-stu-id="dcac2-534">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="dcac2-535">**UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="dcac2-535">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="dcac2-536">**UX_ERROR** (0xFF): ошибка в функции.</span><span class="sxs-lookup"><span data-stu-id="dcac2-536">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-537">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-537">Example</span></span>

```C
/* Read 4 bytes in audio FIFO. */

status = ux_device_class_audio_sample_read32(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_get"></a><span data-ttu-id="dcac2-538">ux_device_class_audio_read_frame_get</span><span class="sxs-lookup"><span data-stu-id="dcac2-538">ux_device_class_audio_read_frame_get</span></span>

<span data-ttu-id="dcac2-539">Получение доступа к аудиокадру в аудиопотоке.</span><span class="sxs-lookup"><span data-stu-id="dcac2-539">Get access to audio frame in the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-540">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-540">Prototype</span></span>

```C
UINT ux_device_class_audio_read_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a><span data-ttu-id="dcac2-541">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-541">Description</span></span>

<span data-ttu-id="dcac2-542">Эта функция возвращает первый буфер аудиокадров и его длину в FIFO указанного потока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-542">This function returns the first audio frame buffer and its length in the specified stream's FIFO.</span></span> <span data-ttu-id="dcac2-543">Когда приложение завершает обработку данных, необходимо использовать ux_device_class_audio_read_frame_free для освобождения буфера кадров в FIFO.</span><span class="sxs-lookup"><span data-stu-id="dcac2-543">When the application is done processing the data, ux_device_class_audio_read_frame_free must be used to free the frame buffer in the FIFO.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-544">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-544">Parameters</span></span>

- <span data-ttu-id="dcac2-545">**stream**: указатель на экземпляр аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-545">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="dcac2-546">**frame_data**: указатель на указатель данных, куда требуется возвратить указатель данных.</span><span class="sxs-lookup"><span data-stu-id="dcac2-546">**frame_data**: Pointer to data pointer to return the data pointer in.</span></span>
- <span data-ttu-id="dcac2-547">**frame_length**: указатель на буфер для сохранения длины кадра в виде количества байтов.</span><span class="sxs-lookup"><span data-stu-id="dcac2-547">**frame_length**: Pointer to buffer to save the frame length in number of bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="dcac2-548">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dcac2-548">Return Value</span></span>

- <span data-ttu-id="dcac2-549">**UX_SUCCESS** (0x00): операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="dcac2-549">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="dcac2-550">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.</span><span class="sxs-lookup"><span data-stu-id="dcac2-550">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="dcac2-551">**UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="dcac2-551">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="dcac2-552">**UX_ERROR** (0xFF): ошибка в функции.</span><span class="sxs-lookup"><span data-stu-id="dcac2-552">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-553">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-553">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_read_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_free"></a><span data-ttu-id="dcac2-554">ux_device_class_audio_read_frame_free</span><span class="sxs-lookup"><span data-stu-id="dcac2-554">ux_device_class_audio_read_frame_free</span></span>

<span data-ttu-id="dcac2-555">Освобождение буфера аудиокадров в аудиопотоке.</span><span class="sxs-lookup"><span data-stu-id="dcac2-555">Free an audio frame buffer in Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-556">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-556">Prototype</span></span>

```C
UINT ux_device_class_audio_read_frame_free(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="dcac2-557">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-557">Description</span></span>

<span data-ttu-id="dcac2-558">Эта функция освобождает буфер аудиокадров в начале буфера FIFO указанного потока, чтобы он мог принять данные с узла.</span><span class="sxs-lookup"><span data-stu-id="dcac2-558">This function frees the audio frame buffer at the front of the specified stream's FIFO so that it can receive data from the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-559">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-559">Parameters</span></span>

- <span data-ttu-id="dcac2-560">**stream**: указатель на экземпляр аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-560">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="dcac2-561">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dcac2-561">Return Value</span></span>

- <span data-ttu-id="dcac2-562">**UX_SUCCESS** (0x00): операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="dcac2-562">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="dcac2-563">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.</span><span class="sxs-lookup"><span data-stu-id="dcac2-563">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="dcac2-564">**UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="dcac2-564">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="dcac2-565">**UX_ERROR** (0xFF): ошибка в функции.</span><span class="sxs-lookup"><span data-stu-id="dcac2-565">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-566">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-566">Example</span></span>

```C
/* Refree a frame buffer in FIFO. */

status = ux_device_class_audio_read_frame_free(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_transmission_start"></a><span data-ttu-id="dcac2-567">ux_device_class_audio_transmission_start</span><span class="sxs-lookup"><span data-stu-id="dcac2-567">ux_device_class_audio_transmission_start</span></span>

<span data-ttu-id="dcac2-568">Запуск передачи звуковых данных для аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-568">Start audio data transmission for the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-569">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-569">Prototype</span></span>

```C
UINT ux_device_class_audio_transmission_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a><span data-ttu-id="dcac2-570">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-570">Description</span></span>

<span data-ttu-id="dcac2-571">Эта функция используется для запуска отправки звуковых данных, записанных в FIFO в классе Audio.</span><span class="sxs-lookup"><span data-stu-id="dcac2-571">This function is used to start sending audio data written to the FIFO in the audio class.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-572">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-572">Parameters</span></span>

- <span data-ttu-id="dcac2-573">**stream**: указатель на экземпляр аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-573">**stream**: Pointer to the audio stream instance.</span></span>

### <a name="return-value"></a><span data-ttu-id="dcac2-574">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dcac2-574">Return Value</span></span>

- <span data-ttu-id="dcac2-575">**UX_SUCCESS** (0x00): операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="dcac2-575">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="dcac2-576">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.</span><span class="sxs-lookup"><span data-stu-id="dcac2-576">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="dcac2-577">**UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="dcac2-577">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is null.</span></span>
- <span data-ttu-id="dcac2-578">**UX_ERROR** (0xFF): ошибка в функции.</span><span class="sxs-lookup"><span data-stu-id="dcac2-578">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-579">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-579">Example</span></span>

```C
/* Start stream data transmission. */

status = ux_device_class_audio_transmission_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_frame_write"></a><span data-ttu-id="dcac2-580">ux_device_class_audio_frame_write</span><span class="sxs-lookup"><span data-stu-id="dcac2-580">ux_device_class_audio_frame_write</span></span>

<span data-ttu-id="dcac2-581">Запись аудиокадра в аудиопоток.</span><span class="sxs-lookup"><span data-stu-id="dcac2-581">Write an audio frame into the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-582">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-582">Prototype</span></span>

```C
UINT ux_device_class_audio_frame_write(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR *frame,
    ULONG frame_length);
```

### <a name="description"></a><span data-ttu-id="dcac2-583">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-583">Description</span></span>

<span data-ttu-id="dcac2-584">Эта функция записывает кадр в FIFO аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-584">This function writes a frame to the audio stream's FIFO.</span></span> <span data-ttu-id="dcac2-585">Данные кадра копируются в доступный буфер в FIFO, чтобы их можно было отправить на узел.</span><span class="sxs-lookup"><span data-stu-id="dcac2-585">The frame data is copied to the available buffer in the FIFO so that it can be sent to the host.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-586">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-586">Parameters</span></span>

- <span data-ttu-id="dcac2-587">**stream**: указатель на экземпляр аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-587">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="dcac2-588">**frame**: указатель на данные кадра.</span><span class="sxs-lookup"><span data-stu-id="dcac2-588">**frame**: Pointer to frame data.</span></span>
- <span data-ttu-id="dcac2-589">**frame_length**: длина кадра в виде количества байтов.</span><span class="sxs-lookup"><span data-stu-id="dcac2-589">**frame_length** Frame length in number of bytes.</span></span>

### <a name="return-value"></a><span data-ttu-id="dcac2-590">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dcac2-590">Return Value</span></span>

- <span data-ttu-id="dcac2-591">**UX_SUCCESS** (0x00): операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="dcac2-591">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="dcac2-592">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.</span><span class="sxs-lookup"><span data-stu-id="dcac2-592">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="dcac2-593">**UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO заполнен.</span><span class="sxs-lookup"><span data-stu-id="dcac2-593">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="dcac2-594">**UX_ERROR** (0xFF): ошибка в функции.</span><span class="sxs-lookup"><span data-stu-id="dcac2-594">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-595">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-595">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_frame_write(stream, frame, frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_write_frame_get"></a><span data-ttu-id="dcac2-596">ux_device_class_audio_write_frame_get</span><span class="sxs-lookup"><span data-stu-id="dcac2-596">ux_device_class_audio_write_frame_get</span></span>

<span data-ttu-id="dcac2-597">Получение доступа к аудиокадру в аудиопотоке.</span><span class="sxs-lookup"><span data-stu-id="dcac2-597">Get access to audio frame in the Audio stream</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-598">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-598">Prototype</span></span>

```C
UINT ux_device_class_audio_write_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a><span data-ttu-id="dcac2-599">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-599">Description</span></span>

<span data-ttu-id="dcac2-600">Эта функция получает адрес последнего буфера аудиокадров FIFO; она также получает длину буфера аудиокадров.</span><span class="sxs-lookup"><span data-stu-id="dcac2-600">This function retrieves the address of the last audio frame buffer of the FIFO; it also retrieves the length of the audio frame buffer.</span></span> <span data-ttu-id="dcac2-601">После того как приложение заполнит буфер аудиокадров своими необходимыми данными, необходимо использовать ***ux_device_class_audio_write_frame_commit*** для добавления или фиксации буфера кадров в FIFO.</span><span class="sxs-lookup"><span data-stu-id="dcac2-601">After the application fills the audio frame buffer with its desired data, ***ux_device_class_audio_write_frame_commit*** must be used to add/commit the frame buffer to the FIFO.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-602">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-602">Parameters</span></span>

- <span data-ttu-id="dcac2-603">**stream**: указатель на экземпляр аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-603">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="dcac2-604">**frame_data**: указатель на указатель данных кадра, куда требуется возвратить указатель данных кадра.</span><span class="sxs-lookup"><span data-stu-id="dcac2-604">**frame_data**: Pointer to frame data pointer to return the frame data pointer in.</span></span>
- <span data-ttu-id="dcac2-605">**frame_length**: указатель на буфер для сохранения длины кадра в виде количества байтов.</span><span class="sxs-lookup"><span data-stu-id="dcac2-605">**frame_length** Pointer to the buffer to save frame length in number of bytes .</span></span>

### <a name="return-value"></a><span data-ttu-id="dcac2-606">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dcac2-606">Return Value</span></span>

- <span data-ttu-id="dcac2-607">**UX_SUCCESS** (0x00): операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="dcac2-607">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="dcac2-608">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.</span><span class="sxs-lookup"><span data-stu-id="dcac2-608">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="dcac2-609">**UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO заполнен.</span><span class="sxs-lookup"><span data-stu-id="dcac2-609">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is full.</span></span>
- <span data-ttu-id="dcac2-610">**UX_ERROR** (0xFF): ошибка в функции.</span><span class="sxs-lookup"><span data-stu-id="dcac2-610">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-611">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-611">Example</span></span>

```C
/* Get frame access. */

status = ux_device_class_audio_write_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
     return;
```

## <a name="ux_device_class_audio_write_frame_commit"></a><span data-ttu-id="dcac2-612">ux_device_class_audio_write_frame_commit</span><span class="sxs-lookup"><span data-stu-id="dcac2-612">ux_device_class_audio_write_frame_commit</span></span>

<span data-ttu-id="dcac2-613">Фиксация буфера аудиокадров в аудиопотоке.</span><span class="sxs-lookup"><span data-stu-id="dcac2-613">Commit an audio frame buffer in Audio stream.</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-614">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-614">Prototype</span></span>

```C
UINT ux_device_class_audio_write_frame_commit(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG length);
```

### <a name="description"></a><span data-ttu-id="dcac2-615">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-615">Description</span></span>

<span data-ttu-id="dcac2-616">Эта функция добавляет или фиксирует последний буфер аудиокадров в FIFO, чтобы буфер был готов к передаче на узел. Обратите внимание, что последний буфер аудиокадров должен быть заполнен с помощью ux_device_class_write_frame_get.</span><span class="sxs-lookup"><span data-stu-id="dcac2-616">This function adds/commits the last audio frame buffer to the FIFO so the buffer is ready to be transferred to host; note the last audio frame buffer should have been filled out via ux_device_class_write_frame_get.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-617">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-617">Parameters</span></span>

- <span data-ttu-id="dcac2-618">**stream**: указатель на экземпляр аудиопотока.</span><span class="sxs-lookup"><span data-stu-id="dcac2-618">**stream**: Pointer to the audio stream instance.</span></span>
- <span data-ttu-id="dcac2-619">**length**: число готовых байтов в буфере.</span><span class="sxs-lookup"><span data-stu-id="dcac2-619">**length**: Number of bytes ready in the buffer.</span></span>

### <a name="return-value"></a><span data-ttu-id="dcac2-620">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dcac2-620">Return Value</span></span>

- <span data-ttu-id="dcac2-621">**UX_SUCCESS** (0x00): операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="dcac2-621">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="dcac2-622">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.</span><span class="sxs-lookup"><span data-stu-id="dcac2-622">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The interface is down.</span></span>
- <span data-ttu-id="dcac2-623">**UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO заполнен.</span><span class="sxs-lookup"><span data-stu-id="dcac2-623">**UX_BUFFER_OVERFLOW** (0x5d) FIFO buffer is fssull.</span></span>
- <span data-ttu-id="dcac2-624">**UX_ERROR** (0xFF): ошибка в функции.</span><span class="sxs-lookup"><span data-stu-id="dcac2-624">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-625">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-625">Example</span></span>

```C
/* Commit a frame after fill values in buffer. */

status = ux_device_class_audio_write_frame_commit(stream, 192);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio10_control_process"></a><span data-ttu-id="dcac2-626">ux_device_class_audio10_control_process</span><span class="sxs-lookup"><span data-stu-id="dcac2-626">ux_device_class_audio10_control_process</span></span>

<span data-ttu-id="dcac2-627">Обработка запросов управления USB Audio 1.0.</span><span class="sxs-lookup"><span data-stu-id="dcac2-627">Process USB Audio 1.0 control requests</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-628">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-628">Prototype</span></span>

```C
UINT ux_device_class_audio10_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO10_CONTROL_GROUP *group);
```

### <a name="description"></a><span data-ttu-id="dcac2-629">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-629">Description</span></span>

<span data-ttu-id="dcac2-630">Эта функция управляет базовыми запросами, отправленными узлом в конечной точке управления, с конкретным типом USB Audio 1.0.</span><span class="sxs-lookup"><span data-stu-id="dcac2-630">This function manages basic requests sent by the host on the control endpoint with a USB Audio 1.0 specific type.</span></span>

<span data-ttu-id="dcac2-631">Функции Audio 1.0 для запросов громкости и отключения звука обрабатываются внутри функции.</span><span class="sxs-lookup"><span data-stu-id="dcac2-631">Audio 1.0 features of volume and mute requests are processed in the function.</span></span> <span data-ttu-id="dcac2-632">При обработке запросов предварительно определенные данные, передаваемые последним параметром (group), используются для ответа на запросы и сохранения изменений управления.</span><span class="sxs-lookup"><span data-stu-id="dcac2-632">When processing the requests, pre-defined data passed by the last parameter (group) is used to answer requests and store control changes.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-633">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-633">Parameters</span></span>

- <span data-ttu-id="dcac2-634">**audio**: указатель на экземпляр звука.</span><span class="sxs-lookup"><span data-stu-id="dcac2-634">**audio**: Pointer to the audio instance.</span></span>
- <span data-ttu-id="dcac2-635">**transfer**: указатель на экземпляр запроса на передачу.</span><span class="sxs-lookup"><span data-stu-id="dcac2-635">**transfer**: Pointer to the transfer request instance.</span></span>
- <span data-ttu-id="dcac2-636">**group**: группа данных для процесса запроса.</span><span class="sxs-lookup"><span data-stu-id="dcac2-636">**group**: Data group for request process.</span></span>

### <a name="return-value"></a><span data-ttu-id="dcac2-637">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dcac2-637">Return Value</span></span>

- <span data-ttu-id="dcac2-638">**UX_SUCCESS** (0x00): операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="dcac2-638">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="dcac2-639">**UX_ERROR** (0xFF): ошибка в функции.</span><span class="sxs-lookup"><span data-stu-id="dcac2-639">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-640">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-640">Example</span></span>

```C
/* Initialize audio 1.0 control values. */

audio_control[0].ux_device_class_audio10_control_fu_id = 2;
audio_control[0].ux_device_class_audio10_control_mute[0] = 0;
audio_control[0].ux_device_class_audio10_control_volume[0] = 0;
audio_control[1].ux_device_class_audio10_control_fu_id = 5;
audio_control[1].ux_device_class_audio10_control_mute[0] = 0;
audio_control[1].ux_device_class_audio10_control_volume[0] = 0;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio10_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio10_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO10_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```

## <a name="ux_device_class_audio20_control_process"></a><span data-ttu-id="dcac2-641">ux_device_class_audio20_control_process</span><span class="sxs-lookup"><span data-stu-id="dcac2-641">ux_device_class_audio20_control_process</span></span>

<span data-ttu-id="dcac2-642">Обработка запросов управления USB Audio 1.0.</span><span class="sxs-lookup"><span data-stu-id="dcac2-642">Process USB Audio 1.0 control requests</span></span>

### <a name="prototype"></a><span data-ttu-id="dcac2-643">Прототип</span><span class="sxs-lookup"><span data-stu-id="dcac2-643">Prototype</span></span>
```C
UINT ux_device_class_audio20_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO20_CONTROL_GROUP *group);
```

### <a name="description"></a><span data-ttu-id="dcac2-644">Описание</span><span class="sxs-lookup"><span data-stu-id="dcac2-644">Description</span></span>

<span data-ttu-id="dcac2-645">Эта функция управляет базовыми запросами, отправленными узлом в конечной точке управления, с конкретным типом USB Audio 2.0.</span><span class="sxs-lookup"><span data-stu-id="dcac2-645">This function manages basic requests sent by the host on the control endpoint with a USB Audio 2.0 specific type.</span></span>

<span data-ttu-id="dcac2-646">Частота выборки Audio 2.0 (предполагается одна фиксированная частота), функции запросов громкости и отключения звука, которые обрабатываются внутри функции.</span><span class="sxs-lookup"><span data-stu-id="dcac2-646">Audio 2.0 sampling rate (assumed single fixed frequency), features of volume and mute requests are processed in the function.</span></span> <span data-ttu-id="dcac2-647">При обработке запросов предварительно определенные данные, передаваемые последним параметром (group), используются для ответа на запросы и сохранения изменений управления.</span><span class="sxs-lookup"><span data-stu-id="dcac2-647">When processing the requests, pre-defined data passed by the last parameter (group) is used to answer requests and store control changes.</span></span>

### <a name="parameters"></a><span data-ttu-id="dcac2-648">Параметры</span><span class="sxs-lookup"><span data-stu-id="dcac2-648">Parameters</span></span>

- <span data-ttu-id="dcac2-649">**audio**: указатель на экземпляр звука.</span><span class="sxs-lookup"><span data-stu-id="dcac2-649">**audio**: Pointer to the audio instance.</span></span>
- <span data-ttu-id="dcac2-650">**transfer**: указатель на экземпляр запроса на передачу.</span><span class="sxs-lookup"><span data-stu-id="dcac2-650">**transfer**: Pointer to the transfer request instance.</span></span>
- <span data-ttu-id="dcac2-651">**group**: группа данных для процесса запроса.</span><span class="sxs-lookup"><span data-stu-id="dcac2-651">**group**: Data group for request process.</span></span>

### <a name="return-value"></a><span data-ttu-id="dcac2-652">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dcac2-652">Return Value</span></span>

- <span data-ttu-id="dcac2-653">**UX_SUCCESS** (0x00): операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="dcac2-653">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="dcac2-654">**UX_ERROR** (0xFF): ошибка в функции.</span><span class="sxs-lookup"><span data-stu-id="dcac2-654">**UX_ERROR** (0xFF) Error from function</span></span>

### <a name="example"></a><span data-ttu-id="dcac2-655">Пример</span><span class="sxs-lookup"><span data-stu-id="dcac2-655">Example</span></span>

```C
/* Initialize audio 2.0 control values. */

audio_control[0].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[0].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[0].ux_device_class_audio20_control_fu_id = 2;
audio_control[0].ux_device_class_audio20_control_mute[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[0].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[0].ux_device_class_audio20_control_volume[0] = 50;
audio_control[1].ux_device_class_audio20_control_cs_id = 0x10;
audio_control[1].ux_device_class_audio20_control_sampling_frequency = 48000;
audio_control[1].ux_device_class_audio20_control_fu_id = 5;
audio_control[1].ux_device_class_audio20_control_mute[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_min[0] = 0;
audio_control[1].ux_device_class_audio20_control_volume_max[0] = 100;
audio_control[1].ux_device_class_audio20_control_volume[0] = 50;

/* Handle request and update control values.
Note here only mute and volume for master channel is supported.
*/

status = ux_device_class_audio20_control_process(audio, transfer, &group);
if (status == UX_SUCCESS)
{
    /* Request handled, check changes */
    switch(audio_control[0].ux_device_class_audio20_control_changed)
    {
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_MUTE_CHANGED:
        case UX_DEVICE_CLASS_AUDIO20_CONTROL_VOLUME_CHANGED:
        default: break;
    }
}
```
