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
# <a name="chapter-2---usbx-device-class-considerations"></a>Глава 2. Сведения о классах устройств USBX

## <a name="usb-device-rndis-class"></a>Класс RNDIS USB-устройства

Класс RNDIS USB-устройства позволяет хост-системе USB обмениваться данными с устройством в качестве устройства Ethernet. Этот класс основан на защищаемой реализации Майкрософт и относится только к платформам Windows.

В стеке устройств необходимо объявить совместимую с RNDIS платформу устройств. Пример представлен ниже.

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

Класс RNDIS использует подход, близко схожий с подходом на основе дескриптора устройства CDC-ACM и CDC-ECM, а также требует наличия дескриптора IAD. Определение и требования для дескриптора устройства см. в описании класса CDC-ACM.

Активация класса RNDIS выполняется следующим образом.

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

Как и в случае с CDC-ECM, для класса RNDIS требуется 2 узла, один локальный и один удаленный, однако не требуется строковый дескриптор, описывающий удаленный узел.

Однако из-за механизма обмена сообщениями корпорации Майкрософт, защищаемого законодательством об интеллектуальной собственности, требуются некоторые дополнительные параметры. Сначала необходимо передать идентификатор поставщика. Затем версию драйвера RNDIS. Также задать строку поставщика.

Класс RNDIS содержит встроенные API для передачи данных обоими способами, однако они скрыты для приложения, так как пользовательское приложение взаимодействует с USB-устройством Ethernet через NetX.

Класс USBX RNDIS тесно привязан к сетевому стеку NetX в ОСРВ Azure. Приложение, использующее и NetX, и класс USBX RNDIS, активирует сетевой стек NetX обычным образом, но в дополнение необходимо активировать сетевой стек USB, как показано ниже.

```C
/* Initialize the NetX system. */

nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

Сетевой стек USB следует активировать только один раз, и он не зависит от RNDIS, однако необходим для любого класса USB, которому требуются службы NetX.

Класс RNDIS не будет распознан узлами MAC OS и Linux, так как он относится только к операционным системам Майкрософт. На платформах Windows на узле должен присутствовать INF-файл, соответствующий дескриптору устройства. Корпорация Майкрософт предоставляет для класса RNDIS шаблон, который можно найти в каталоге usbx_windows_host_files. Для более поздней версии Windows следует использовать файл RNDIS_Template.inf. Этот файл необходимо изменить в соответствии с идентификаторами PID/VID, используемыми устройством. PID/VID зависят от клиента, если компания и продукт зарегистрированы с использованием USB-IF. В INF-файле поля для изменения находятся здесь.

```Inf
[DeviceList]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00

[DeviceList.NTamd64]
%DeviceName%=DriverInstall, USB\\VID_xxxx&PID_yyyy&MI_00
```

В платформе устройств устройства RNDIS идентификаторы PID/VID хранятся в дескрипторе устройства (см. дескриптор устройства, объявленный выше).

Когда хост-система USB обнаруживает устройство USB RNDIS, она подключает сетевой интерфейс, и устройство может использоваться со стеком сетевых протоколов. Подробнее см. в разделе "Операционная система узла".

## <a name="usb-device-dfu-class"></a>Класс DFU USB-устройства

Класс DFU USB-устройства позволяет хост-системе USB обновлять встроенное ПО устройства на основе ведущего приложения. Класс DFU — это стандартный класс USB-IF.

Класс USBX DFU относительно прост. Дескриптору устройства не требуется ничего, кроме конечной точки управления. В большинстве случаев этот класс будет внедрен в составное устройство USB. Устройство может быть любым, например запоминающим устройством или устройством связи, а добавленный интерфейс DFU может информировать узел о том, что встроенное ПО на устройстве может быть обновлено в режиме реального времени.

Работа класса DFU состоит из 3 шагов. Сначала устройство подключается как обычное с помощью экспортированного класса. Приложение на узле (Windows или Linux) будет использовать класс DFU и отправит запрос на сброс устройства в режим DFU. Устройство ненадолго исчезнет с шины (чтобы узел и устройство обнаружили последовательность сброса RESET), а после перезапуска будет работать исключительно в режиме DFU, ожидая отправки обновления встроенного ПО ведущим приложением. Когда обновление встроенного ПО завершено, ведущее приложение сбрасывает устройство и при повторном перечислении устройство возвращается к нормальной работе с новым встроенным ПО.

Платформа устройства DFU будет выглядеть указанным ниже образом.

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

В этом примере дескриптор DFU не сопоставлен с другими классами. Он имеет простой дескриптор интерфейса и не имеет других подключенных конечных точек. Существует функциональный дескриптор, описывающий особенности возможностей DFU для устройства.

Ниже приведено описание возможностей DFU.

| Имя             | Offset  | Размер | тип      | Описание |
|------------------|----------|------|-----------|------------|
| bmAttributes  | 2     | 1   | Битовое поле | Бит 3: устройство будет выполнять последовательность отсоединения-подсоединения шины при получении запроса DFU_DETACH. Узел не должен выдавать сброс USB. (bitWillDetach) 0 = нет, 1 = да. Бит 2: устройство может взаимодействовать через USB после этапа манифестации. (bitManifestationTolerant) 0 = нет, должен увидеть сброс шины, 1 = да. Бит 1: поддерживается отправка. (bitCanUpload) 0 = нет, 1 = да. Бит 0: поддерживается скачивание. (bitCanDnload) 0 = нет, 1 = да.  |
| wDetachTimeOut  | 3      | 2  | number    | Время в миллисекундах, в течение которого устройство будет ожидать после получения запроса DFU_DETACH. Если это время истекает без сброса USB, устройство завершит этап перенастройки и вернется к нормальной работе. Представляет максимальное время ожидания устройства (в зависимости от его таймеров и т. п.). USBX устанавливает это значение равным 1000 мс.  |
| wTransferSize  | 5      | 2  | number    | Максимальное число байтов, которое устройство может принимать на операцию управления\-записи. USBX задает это значение равным 64 байтам. |

Объявление класса DFU выглядит следующим образом:

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

Класс DFU должен работать с приложением встроенного ПО устройства, относящимся к целевому объекту. Поэтому он определяет несколько обратных вызовов для чтения и записи встроенного ПО и для получения состояния от приложения обновления встроенного ПО. Класс DFU также имеет функцию обратного вызова уведомления для информирования приложения о начале и конце передачи встроенного ПО.

Ниже приведено описание типичной схемы приложения DFU.

![Схема приложения DFU](./media/usbx-device-stack-supplemental/dfu-application-flow.png)

Основная сложность при работе с классом DFU заключается в получении правильного приложения на узле для выполнения скачивания встроенного ПО. Приложения, предоставляемые корпорацией Майкрософт или USB-IF, отсутствуют. Существует несколько условно бесплатных программ, которые хорошо работают в Linux и немного хуже в Windows.

В Linux можно использовать программы dfu-util, которые можно найти здесь: [https://wiki.openmoko.org/wiki/Dfu-util](https://wiki.openmoko.org/wiki/Dfu-util) Множество сведений о dfu-util см. по этой ссылке: [https://www.libusb.org/wiki/windows_backend](https://www.libusb.org/wiki/windows_backend)

Реализация DFU в Linux выполняет правильную последовательность сброса между узлом и устройством, и поэтому устройство в этом не нуждается. Linux может принимать для bmAttributes значение *bitWillDetach*, равное 0. С другой стороны, Windows требует, чтобы устройство выполнило сброс.

В Windows реестр USB должен иметь возможность сопоставить USB-устройство с его PID/VID и библиотекой USB, которая, в свою очередь, будет использоваться приложением DFU. Это можно легко сделать с помощью бесплатной служебной программы Zadig, которую можно найти здесь: [https://sourceforge.net/projects/libwdi/files/zadig/](https://sourceforge.net/projects/libwdi/files/zadig/).

При первом запуске Zadig отображается следующий экран:

![Первый запуск Zadig](./media/usbx-device-stack-supplemental/zadig.png)

В списке устройств найдите свое устройство и сопоставьте его с драйвером Windows libusb. Это приведет к привязке PID/VID устройства к библиотеке USB Windows, используемой служебными программами DFU.

Чтобы выполнить команду DFU, просто распакуйте архив со служебными программами DFU в каталог, убедившись, что библиотека DLL libusb также находится в этом каталоге. Служебные программы DFU необходимо запускать из окна DOS в командной строке.

Сначала введите команду **dfu-util –l**, чтобы определить, отображается ли устройство в списке. Если его нет, запустите Zadig, чтобы убедиться, что устройство отображается и связано с библиотекой USB. Вы увидите экран следующего вида:

```Command-line
C:\usb specs\DFU\dfu-util-0.6&gt;dfu-util -l dfu-util 0.6

Copyright 2005-2008 Weston Schmidt, Harald Welte and OpenMoko Inc.
Copyright 2010-2012 Tormod Volden and Stefan Schmidt
This program is Free Software and has ABSOLUTELY NO WARRANTY
Found Runtime: [0a5c:21bc] devnum=0, cfg=1, intf=3, alt=0, name="UNDEFINED"
```

Следующим шагом будет подготовка файла к скачиванию. Класс USBX DFU не выполняет проверку этого файла и не зависит от его внутреннего формата. Этот файл встроенного ПО сильно зависит для целевого объекта, но не DFU и не USBX.

Затем можно велеть dfu-util отправить файл, введя следующую команду:

```Command-line
dfu-util –R –t 64 -D file_to_download.hex
```

Программа dfu-util должна отобразить процесс скачивания файла, пока встроенное ПО не будет полностью скачано.

## <a name="usb-device-pima-class-ptp-responder"></a>Класс PIMA USB-устройства (ответчик PTP)

Класс USB-устройства PIMA позволяет хост-системе USB (инициатор) подключаться к

устройству PIMA (ответчик) для передачи файлов мультимедиа. Класс USBX PIMA соответствует классу USB-IF PIMA 15740, который также известен как класс PTP (протокол обмена изображениями).

Класс PIMA на стороне устройства USBX поддерживает следующие операции:

| Код операции                                    | Значение | Описание                       |
|---------------------------------------------------|---------|-----------------------------------------------------|
| UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO    | 0x1001  | Получение поддерживаемых устройством операций и событий.                                                         |
| UX_DEVICE_CLASS_PIMA_OC_OPEN_SESSION        | 0x1002  | Открытие сеанса между узлом и устройством.                                                            |
| UX_DEVICE_CLASS_PIMA_OC_CLOSE_SESSION       | 0x1003  | Закрытие сеанса между узлом и устройством.                                                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_IDS    | 0x1004  | Возвращение идентификатора хранилища для устройства. USBX PIMA использует только один идентификатор хранилища. |
| UX_DEVICE_CLASS_PIMA_OC_GET_STORAGE_INFO   | 0x1005  | Возвращение сведений об объекте хранилища, например о максимальной емкости и свободном пространстве.                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_NUM_OBJECTS    | 0x1006  | Возврат числа объектов, содержащихся в запоминающем устройстве.                                              |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_HANDLES | 0x1007  | Возврат массива дескрипторов объектов на запоминающем устройстве.                                           |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT_INFO    | 0x1008  | Возвращение сведений об объекте, таких как имя объекта, дата его создания, дата изменения. |
| UX_DEVICE_CLASS_PIMA_OC_GET_OBJECT          | 0x1009  | Возврат данных, относящихся к определенному объекту.                                                         |
| UX_DEVICE_CLASS_PIMA_OC_GET_THUMB           | 0x100A  | Отправка эскиза, если он доступен для объекта.                                                           |
| UX_DEVICE_CLASS_PIMA_OC_DELETE_OBJECT       | 0x100B  | Удаление объекта на носителе.                                                                             |
| UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT_INFO   | 0x100C  | Отправка на устройство сведения об объекте для его создания на носителе.                              |
| UX_DEVICE_CLASS_PIMA_OC_SEND_OBJECT         | 0x100D  | Отправка данных для объекта на устройство.                                                                     |
| UX_DEVICE_CLASS_PIMA_OC_FORMAT_STORE        | 0x100F  | Очистка носителя устройства.                                                                                    |
| UX_DEVICE_CLASS_PIMA_OC_RESET_DEVICE        | 0x0110  | Сброс целевого устройства.                                                                                   |

| Код операции                                         | Значение | Описание |
|--------------------------------------------------------|-------|-----------------------------------------|
| UX_DEVICE_CLASS_PIMA_EC_CANCEL_TRANSACTION       | 0x4001  | Отмена текущей транзакции.                                                 |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_ADDED             | 0x4002  | Объект был добавлен на носитель устройства и может быть извлечен узлом. |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_REMOVED           | 0x4003  | Объект удален с носителя устройства.                                |
| UX_DEVICE_CLASS_PIMA_EC_STORE_ADDED              | 0x4004  | На устройство добавлен носитель.                                            |
| UX_DEVICE_CLASS_PIMA_EC_STORE_REMOVED            | 0x4005  | Носитель удален с устройства.                                        |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_PROP_CHANGED     | 0x4006  | Свойства устройства изменены.                                                  |
| UX_DEVICE_CLASS_PIMA_EC_OBJECT_INFO_CHANGED     | 0x4007  | Сведения об объекте изменены.                                               |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_INFO_CHANGE      | 0x4008  | Устройство изменилось.                                                            |
| UX_DEVICE_CLASS_PIMA_EC_REQUEST_OBJECT_TRANSFER | 0x4009  | Устройство запрашивает перемещение объекта с узла.                     |
| UX_DEVICE_CLASS_PIMA_EC_STORE_FULL               | 0x400A  | Устройство сообщает, что носитель заполнен.                                                |
| UX_DEVICE_CLASS_PIMA_EC_DEVICE_RESET             | 0x400B  | Устройство сообщает о сбросе.                                                     |
| UX_DEVICE_CLASS_PIMA_EC_STORAGE_INFO_CHANGED    | 0x400C  | На устройстве изменились сведения о хранилище.                                   |
| UX_DEVICE_CLASS_PIMA_EC_CAPTURE_COMPLETE         | 0x400D  | Захват завершен.                                                            |

Класс устройств USBX PIMA использует поток TX для прослушивания команд PIMA с узла.

Команда PIMA состоит из блока команд, блока данных и этапа состояния.

Функция ux_device_class_pima_thread отправляет запрос в стек для получения команды PIMA со стороны узла. Команда PIMA декодируется и проверяется на наличие содержимого. Если блок команд является допустимым, он направляется в соответствующий обработчик команд.

Большинство команд PIMA могут быть выполнены только при открытии сеанса узлом. Единственным исключением является команда **UX_DEVICE_CLASS_PIMA_OC_GET_DEVICE_INFO**. В реализации USBX PIMA между инициатором и ответчиком одновременно можно открыть только один сеанс. Все транзакции в рамках одного сеанса блокируются, и новая транзакция не может начаться до завершения предыдущей.

Транзакции PIMA состоят из 3 этапов — этапа команды, дополнительного этапа данных и этапа ответа. При наличии этапа данных он может присутствовать только для одного направления.

Инициатор всегда определяет поток операций PIMA, но ответчик может инициировать события обратно инициатору, чтобы сообщить об изменениях состояния, произошедших во время сеанса.

На следующей схеме показана передача объекта данных между узлом и классом устройств PIMA.

![Транзакции PIMA](./media/usbx-device-stack-supplemental/pima-transactions.png)

## <a name="initialization-of-the-pima-device-class"></a>Инициализация класса устройств PIMA

Во время инициализации классу устройств PIMA требуются некоторые параметры, предоставляемые приложением.

Приведенные ниже параметры описывают сведения об устройстве и хранилище.

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

Класс PIMA также требует регистрацию обратного вызова в приложении, чтобы информировать приложение об определенных событиях либо извлечь данные с локального носителя или сохранить их там. Эти обратные вызовы указаны ниже.

- `ux_device_class_pima_object_number_get`
- `ux_device_class_pima_object_handles_get`
- `ux_device_class_pima_object_info_get`
- `ux_device_class_pima_object_data_get`
- `ux_device_class_pima_object_info_send`
- `ux_device_class_pima_object_data_send`
- `ux_device_class_pima_object_delete`

В следующем примере показано, как инициализировать клиентскую сторону PIMA. В этом примере используется Pictbridge в качестве клиента для PIMA.

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

## <a name="ux_device_class_pima_object_add"></a>ux_device_class_pima_object_add

Добавление объекта и отправка события на узел.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_pima_object_add(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG object_handle);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда классу PIMA необходимо добавить объект и проинформировать узел.

### <a name="parameters"></a>Параметры

- **pima**: указатель на экземпляр класса PIMA.
- **object_handle**: дескриптор объекта.

### <a name="example"></a>Пример

```C
/* Send the notification to the host that an object has been added. */

status = ux_device_class_pima_object_add(pima, UX_PICTBRIDGE_OBJECT_HANDLE_CLIENT_REQUEST);
```

## <a name="ux_device_class_pima_object_number_get"></a>ux_device_class_pima_object_number_get

Получение количества объектов из приложения.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_pima_object_number_get(
    UX_SLAVE_CLASS_PIMA *pima, 
    ULONG *object_number);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда классу PIMA требуется получить количество объектов в локальной системе и отправить его обратно на узел.

### <a name="parameters"></a>Параметры

- **pima**: указатель на экземпляр класса PIMA.
- **object_number**: адрес возвращаемого числа объектов.

### <a name="example"></a>Пример

```C
UINT ux_pictbridge_dpsclient_object_number_get(UX_SLAVE_CLASS_PIMA *pima, ULONG *number_objects)
{
    /* We force the number of objects to be 1 only here. This will be the XML scripts. */
    *number_objects = 1;
    return(UX_SUCCESS);
}
```

## <a name="ux_device_class_pima_object_handles_get"></a>ux_device_class_pima_object_handles_get

Возврат массива обработчиков объектов.

### <a name="prototype"></a>Прототип

```C
UINT **ux_device_class_pima_object_handles_get**(
    UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handles_format_code,
    ULONG object_handles_association,
    ULONG *object_handles_array,
    ULONG object_handles_max_number);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда классу PIMA требуется получить массив дескрипторов объекта в локальной системе и отправить его обратно на узел.

### <a name="parameters"></a>Параметры

- **pima**: указатель на экземпляр класса PIMA.
- **object_handles_format_code**: код формата для дескрипторов.
- **object_handles_association**: код сопоставления объектов.
- **object_handle_array**: адрес для хранения дескрипторов.
- **object_handles_max_number**: максимальное число дескрипторов в массиве.

### <a name="example"></a>Пример

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

## <a name="ux_device_class_pima_object_info_get"></a>ux_device_class_pima_object_info_get

Возврат сведений об объекте.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_pima_object_info_get(
    struct UX_SLAVE_CLASS_PIMA_STRUCT *pima,
    ULONG object_handle, 
    UX_SLAVE_CLASS_PIMA_OBJECT **object);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда классу PIMA требуется получить массив дескрипторов объекта в локальной системе и отправить его обратно на узел.

### <a name="parameters"></a>Параметры

- **pima**: указатель на экземпляр класса PIMA.
- **object_handles** — дескриптор объекта.
- **object**: адрес указателя объекта.

### <a name="example"></a>Пример

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

## <a name="ux_device_class_pima_object_data_get"></a>ux_device_class_pima_object_data_get

Возврат данных объекта.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_pima_object_info_get(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length_requested,
    ULONG *object_actual_length);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда классу PIMA требуется получить данные объекта в локальной системе и отправить их обратно на узел.

### <a name="parameters"></a>Параметры

- **pima**: указатель на экземпляр класса PIMA.
- **object_handle**: дескриптор объекта.
- **object_buffer**: адрес буфера объектов.
- **object_length_requested**: длина данных объекта, запрошенная клиентом для приложения.
- **object_actual_length**: длина данных объекта, возвращенная приложением.

### <a name="example"></a>Пример

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

## <a name="ux_device_class_pima_object_info_send"></a>ux_device_class_pima_object_info_send

Узел отправляет сведения об объекте.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_pima_object_info_send(
    UX_SLAVE_CLASS_PIMA *pima,
    UX_SLAVE_CLASS_PIMA_OBJECT *object, 
    ULONG *object_handle);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда классу PIMA требуется получить сведения об объекте в локальной системе для хранения в будущем.

### <a name="parameters"></a>Параметры

- **pima**: указатель на экземпляр класса PIMA.
- **object**: указатель на объект.
- **object_handle**: дескриптор объекта.

### <a name="example"></a>Пример

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

## <a name="ux_device_class_pima_object_data_send"></a>ux_device_class_pima_object_data_send

Узел отправляет данные объекта.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_pima_object_data_send(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle, 
    ULONG phase, 
    UCHAR *object_buffer,
    ULONG object_offset, 
    ULONG object_length);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда классу PIMA требуется получить данные объекта в локальной системе для хранения.

### <a name="parameters"></a>Параметры

- **pima**: указатель на экземпляр класса PIMA.
- **object_handle**: дескриптор объекта.
- **phase**: этап передачи (активный или полный).
- **object_buffer**: адрес буфера объектов.
- **object_offset**: адрес данных.
- **object_length**: длина данных объекта, отправленная приложением.

### <a name="example"></a>Пример

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

## <a name="ux_device_class_pima_object_delete"></a>ux_device_class_pima_object_delete

Удаление локального объекта.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_pima_object_delete(
    UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда классу PIMA требуется удалить объект в локальном хранилище.

### <a name="parameters"></a>Параметры

- **pima**: указатель на экземпляр класса PIMA.
- **object_handle**: дескриптор объекта.

### <a name="example"></a>Пример

```C
UINT ux_pictbridge_dpsclient_object_delete(UX_SLAVE_CLASS_PIMA *pima,
    ULONG object_handle)
{
    /* Delete the object pointer by the handle. */

}
```

## <a name="usb-device-audio-class"></a>Класс Audio USB-устройства

Класс Audio USB-устройства позволяет хост-системе USB обмениваться данными с устройством в качестве звукового устройства. Этот класс основан на стандарте USB и стандарте USB Audio Class 1.0 или 2.0.

В стеке устройств необходимо объявить совместимую с USB Audio платформу устройств. Ниже приведен пример динамика Audio 2.0.

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

Класс Audio использует составную платформу устройств для группирования интерфейсов (для управления и потоковой передачи). В результате при определении дескриптора устройства следует проявлять осторожность. USBX использует дескриптор IAD для определения внутреннего порядка привязки интерфейсов. Дескриптор IAD должен быть объявлен перед интерфейсами (интерфейс AudioControl, за которым следует один или несколько интерфейсов AudioStreaming) и содержать первый интерфейс класса Audio (интерфейс AudioControl) и число подключенных интерфейсов.

Способ работы класса Audio зависит от того, отправляет или принимает устройство звук, но в обоих случаях используется FIFO для хранения буферов аудиокадров: если устройство отправляет звук на узел, приложение добавляет в FIFO буферы аудиокадров, которые позже отправляются USBX на узел; если устройство принимает звук с узла, USBX добавляет в FIFO буферы аудиокадров, полученные от узла, которые позже считываются приложением. Каждый аудиопоток имеет собственный FIFO, а каждый буфер аудиокадров состоит из нескольких выборок.

При инициализации класса Audio ожидаются следующие компоненты.

1. Класс Audio ожидает следующие параметры потоковой передачи:

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

2. Класс Audio ожидает следующие параметры функций:

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

   Определяемый приложением обратный вызов запроса управления (***ux_device_class_audio_control_process***, заданный в предыдущем примере) выполняется, когда стек получает запрос управления от узла. Если запрос принят и обработан (подтвержден или остановлен), обратный вызов должен вернуть данные об успешном выполнении, в противном случае должна возвращаться ошибка.

   Процесс запроса управления, относящегося к классу, определяется как определяемый приложением обратный вызов, так как запросы управления сильно различаются между версиями USB Audio и большая часть процесса запроса связана с платформой устройств. Чтобы устройство функционировало, приложение должно правильно обрабатывать запросы.

   Так как для звукового устройства громкость, отключение звука и частота выборки относятся к типичным запросам управления, в последующих разделах представлены простые внутренние обратные вызовы для различных версий USB Audio, которые могут использовать приложения. Дополнительные сведения см. в описании ***ux_device_class_audio10_control_process** _ и _ *_ux_device_class_audio_control_request_**.

В платформе устройств устройства Audio идентификаторы PID/VID хранятся в дескрипторе устройства (см. дескриптор устройства, объявленный выше).

Когда хост-система USB обнаруживает устройство USB Audio и подключает класс Audio, устройство можно использовать с любым проигрывателем или устройством записи (в зависимости от платформы). Подробнее см. в разделе "Операционная система узла".

Интерфейсы API класса Audio определены ниже.

## <a name="ux_device_class_audio_read_thread_entry"></a>ux_device_class_audio_read_thread_entry

Запись потока для чтения данных для функции Audio.

### <a name="prototype"></a>Прототип

```C
VOID ux_device_class_audio_read_thread_entry(ULONG audio_stream);
```

### <a name="description"></a>Описание

Эта функция передается в параметр инициализации аудиопотока, если требуется считывание звука с узла. На внутреннем уровне создается поток с этой функцией в качестве входной функции, он сам считывает звуковые данные через изохронную конечную точку OUT в функции Audio.

### <a name="parameters"></a>Параметры

- **audio_stream**: указатель на экземпляр аудиопотока.

### <a name="example"></a>Пример

```C
/* Set parameter to initialize a stream for reading. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_entry
     = ux_device_class_audio_read_thread_entry;
```

## <a name="ux_device_class_audio_write_thread_entry"></a>ux_device_class_audio_write_thread_entry

Запись потока для записи данных для функции Audio.

### <a name="prototype"></a>Прототип

```C
VOID ux_device_class_audio_write_thread_entry(ULONG audio_stream);
```

### <a name="description"></a>Описание

Эта функция передается в параметр инициализации аудиопотока, если требуется запись звука на узел. На внутреннем уровне создается поток с этой функцией в качестве входной функции, он сам записывает звуковые данные через изохронную конечную точку IN в функции Audio.

### <a name="parameters"></a>Параметры

- **audio_stream**: указатель на экземпляр аудиопотока.

### <a name="example"></a>Пример

```C
/* Set parameter to initialize as stream for writing. */
audio_stream_parameter[0].ux_device_class_audio_stream_parameter_thread_en
    try = ux_device_class_audio_write_thread_entry;
```

## <a name="ux_device_class_audio_stream_get"></a>ux_device_class_audio_stream_get

Получение конкретного экземпляра потока для функции Audio.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_audio_stream_get(
    UX_DEVICE_CLASS_AUDIO *audio,
    ULONG stream_index, 
    UX_DEVICE_CLASS_AUDIO_STREAM **stream);
```

### <a name="description"></a>Описание

Эта функция используется для получения экземпляра потока класса Audio.

### <a name="parameters"></a>Параметры

- **audio**: указатель на экземпляр звука.
- **stream_index**: индекс экземпляра потока, отчитываемый от 0.
- **stream**: указатель на буфер для хранения указателя экземпляра аудиопотока.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00): операция успешно выполнена.
- **UX_ERROR** (0xFF): ошибка в функции.

### <a name="example"></a>Пример

```C
/* Get audio stream instance. */
status = ux_device_class_audio_stream_get(audio, 0, &stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_reception_start"></a>ux_device_class_audio_reception_start

Запуск получения звуковых данных для аудиопотока.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_audio_reception_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Описание

Эта функция используется для запуска чтения звуковых данных в аудиопотоках.

### <a name="parameters"></a>Параметры

- **stream**: указатель на экземпляр аудиопотока.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00): операция успешно выполнена.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.
- **UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO заполнен.
- **UX_ERROR** (0xFF): ошибка в функции.

### <a name="example"></a>Пример

```C
/* Start stream data reception. */
status = ux_device_class_audio_reception_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read8"></a>ux_device_class_audio_sample_read8

Чтение 8-разрядной выборки из аудиопотока.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_audio_sample_read8(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    UCHAR *buffer);
```

### <a name="description"></a>Описание

Эта функция считывает данные 8-разрядной аудиовыборки из указанного потока.

В частности, она считывает данные выборки из текущего буфера аудиокадров в FIFO. После чтения последней выборки в аудиокадре он будет автоматически освобожден, чтобы его можно было использовать для приема дополнительных данных от узла.

### <a name="parameters"></a>Параметры

- **stream**: указатель на экземпляр аудиопотока.
- **buffer**: указатель на буфер для сохранения байта выборки.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00): операция успешно выполнена.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.
- **UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO имеет значение NULL.
- **UX_ERROR** (0xFF): ошибка в функции.

### <a name="example"></a>Пример

```C
/* Read a byte in audio FIFO. */

status = ux_device_class_audio_sample_read8(stream, &sample_byte);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read16"></a>ux_device_class_audio_sample_read16

Чтение 16-разрядной выборки из аудиопотока.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_audio_sample_read16(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    USHORT *buffer);
```

### <a name="description"></a>Описание

Эта функция считывает данные 16-разрядной аудиовыборки из указанного потока.

В частности, она считывает данные выборки из текущего буфера аудиокадров в FIFO. После чтения последней выборки в аудиокадре он будет автоматически освобожден, чтобы его можно было использовать для приема дополнительных данных от узла.

### <a name="parameters"></a>Параметры

- **stream**: указатель на экземпляр аудиопотока.
- **buffer**: указатель на буфер для сохранения 16-разрядной выборки.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00): операция успешно выполнена.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.
- **UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO имеет значение NULL.
- **UX_ERROR** (0xFF): ошибка в функции.

### <a name="example"></a>Пример

```C
/* Read a 16-bit sample in audio FIFO. */

status = ux_device_class_audio_sample_read16(stream, &sample_word);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read24"></a>ux_device_class_audio_sample_read24

Чтение 24-разрядной выборки из аудиопотока.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_audio_sample_read24(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a>Описание

Эта функция считывает данные 24-разрядной аудиовыборки из указанного потока.

В частности, она считывает данные выборки из текущего буфера аудиокадров в FIFO. После чтения последней выборки в аудиокадре он будет автоматически освобожден, чтобы его можно было использовать для приема дополнительных данных от узла.

### <a name="parameters"></a>Параметры

- **stream**: указатель на экземпляр аудиопотока.
- **buffer**: указатель на буфер для сохранения 3-байтовой выборки.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00): операция успешно выполнена.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.
- **UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO имеет значение NULL.
- **UX_ERROR** (0xFF): ошибка в функции.

### <a name="example"></a>Пример

```C
/* Read 3 bytes to in audio FIFO. */

status = ux_device_class_audio_sample_read24(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_sample_read32"></a>ux_device_class_audio_sample_read32

Чтение 32-разрядной выборки из аудиопотока.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_audio_sample_read32(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG *buffer);
```

### <a name="description"></a>Описание

Эта функция считывает данные 32-разрядной аудиовыборки из указанного потока.

В частности, она считывает данные выборки из текущего буфера аудиокадров в FIFO. После чтения последней выборки в аудиокадре он будет автоматически освобожден, чтобы его можно было использовать для приема дополнительных данных от узла.

### <a name="parameters"></a>Параметры

- **stream**: указатель на экземпляр аудиопотока.
- **buffer**: указатель на буфер для сохранения 4-байтовых данных.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00): операция успешно выполнена.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.
- **UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO имеет значение NULL.
- **UX_ERROR** (0xFF): ошибка в функции.

### <a name="example"></a>Пример

```C
/* Read 4 bytes in audio FIFO. */

status = ux_device_class_audio_sample_read32(stream, &sample_bytes);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_get"></a>ux_device_class_audio_read_frame_get

Получение доступа к аудиокадру в аудиопотоке.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_audio_read_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a>Описание

Эта функция возвращает первый буфер аудиокадров и его длину в FIFO указанного потока. Когда приложение завершает обработку данных, необходимо использовать ux_device_class_audio_read_frame_free для освобождения буфера кадров в FIFO.

### <a name="parameters"></a>Параметры

- **stream**: указатель на экземпляр аудиопотока.
- **frame_data**: указатель на указатель данных, куда требуется возвратить указатель данных.
- **frame_length**: указатель на буфер для сохранения длины кадра в виде количества байтов.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00): операция успешно выполнена.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.
- **UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO имеет значение NULL.
- **UX_ERROR** (0xFF): ошибка в функции.

### <a name="example"></a>Пример

```C
/* Get frame access. */

status = ux_device_class_audio_read_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_read_frame_free"></a>ux_device_class_audio_read_frame_free

Освобождение буфера аудиокадров в аудиопотоке.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_audio_read_frame_free(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Описание

Эта функция освобождает буфер аудиокадров в начале буфера FIFO указанного потока, чтобы он мог принять данные с узла.

### <a name="parameters"></a>Параметры

- **stream**: указатель на экземпляр аудиопотока.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00): операция успешно выполнена.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.
- **UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO имеет значение NULL.
- **UX_ERROR** (0xFF): ошибка в функции.

### <a name="example"></a>Пример

```C
/* Refree a frame buffer in FIFO. */

status = ux_device_class_audio_read_frame_free(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_transmission_start"></a>ux_device_class_audio_transmission_start

Запуск передачи звуковых данных для аудиопотока.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_audio_transmission_start(UX_DEVICE_CLASS_AUDIO_STREAM *stream);
```

### <a name="description"></a>Описание

Эта функция используется для запуска отправки звуковых данных, записанных в FIFO в классе Audio.

### <a name="parameters"></a>Параметры

- **stream**: указатель на экземпляр аудиопотока.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00): операция успешно выполнена.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.
- **UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO имеет значение NULL.
- **UX_ERROR** (0xFF): ошибка в функции.

### <a name="example"></a>Пример

```C
/* Start stream data transmission. */

status = ux_device_class_audio_transmission_start(stream);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_frame_write"></a>ux_device_class_audio_frame_write

Запись аудиокадра в аудиопоток.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_audio_frame_write(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR *frame,
    ULONG frame_length);
```

### <a name="description"></a>Описание

Эта функция записывает кадр в FIFO аудиопотока. Данные кадра копируются в доступный буфер в FIFO, чтобы их можно было отправить на узел.

### <a name="parameters"></a>Параметры

- **stream**: указатель на экземпляр аудиопотока.
- **frame**: указатель на данные кадра.
- **frame_length**: длина кадра в виде количества байтов.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00): операция успешно выполнена.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.
- **UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO заполнен.
- **UX_ERROR** (0xFF): ошибка в функции.

### <a name="example"></a>Пример

```C
/* Get frame access. */

status = ux_device_class_audio_frame_write(stream, frame, frame_length);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio_write_frame_get"></a>ux_device_class_audio_write_frame_get

Получение доступа к аудиокадру в аудиопотоке.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_audio_write_frame_get(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream,
    UCHAR **frame_data, 
    ULONG *frame_length);
```

### <a name="description"></a>Описание

Эта функция получает адрес последнего буфера аудиокадров FIFO; она также получает длину буфера аудиокадров. После того как приложение заполнит буфер аудиокадров своими необходимыми данными, необходимо использовать ***ux_device_class_audio_write_frame_commit*** для добавления или фиксации буфера кадров в FIFO.

### <a name="parameters"></a>Параметры

- **stream**: указатель на экземпляр аудиопотока.
- **frame_data**: указатель на указатель данных кадра, куда требуется возвратить указатель данных кадра.
- **frame_length**: указатель на буфер для сохранения длины кадра в виде количества байтов.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00): операция успешно выполнена.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.
- **UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO заполнен.
- **UX_ERROR** (0xFF): ошибка в функции.

### <a name="example"></a>Пример

```C
/* Get frame access. */

status = ux_device_class_audio_write_frame_get(stream, &frame, &frame_length);

if(status != UX_SUCCESS)
     return;
```

## <a name="ux_device_class_audio_write_frame_commit"></a>ux_device_class_audio_write_frame_commit

Фиксация буфера аудиокадров в аудиопотоке.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_audio_write_frame_commit(
    UX_DEVICE_CLASS_AUDIO_STREAM *stream, 
    ULONG length);
```

### <a name="description"></a>Описание

Эта функция добавляет или фиксирует последний буфер аудиокадров в FIFO, чтобы буфер был готов к передаче на узел. Обратите внимание, что последний буфер аудиокадров должен быть заполнен с помощью ux_device_class_write_frame_get.

### <a name="parameters"></a>Параметры

- **stream**: указатель на экземпляр аудиопотока.
- **length**: число готовых байтов в буфере.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00): операция успешно выполнена.
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51): интерфейс не работает.
- **UX_BUFFER_OVERFLOW** (0x5d): буфер FIFO заполнен.
- **UX_ERROR** (0xFF): ошибка в функции.

### <a name="example"></a>Пример

```C
/* Commit a frame after fill values in buffer. */

status = ux_device_class_audio_write_frame_commit(stream, 192);

if(status != UX_SUCCESS)
    return;
```

## <a name="ux_device_class_audio10_control_process"></a>ux_device_class_audio10_control_process

Обработка запросов управления USB Audio 1.0.

### <a name="prototype"></a>Прототип

```C
UINT ux_device_class_audio10_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO10_CONTROL_GROUP *group);
```

### <a name="description"></a>Описание

Эта функция управляет базовыми запросами, отправленными узлом в конечной точке управления, с конкретным типом USB Audio 1.0.

Функции Audio 1.0 для запросов громкости и отключения звука обрабатываются внутри функции. При обработке запросов предварительно определенные данные, передаваемые последним параметром (group), используются для ответа на запросы и сохранения изменений управления.

### <a name="parameters"></a>Параметры

- **audio**: указатель на экземпляр звука.
- **transfer**: указатель на экземпляр запроса на передачу.
- **group**: группа данных для процесса запроса.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00): операция успешно выполнена.
- **UX_ERROR** (0xFF): ошибка в функции.

### <a name="example"></a>Пример

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

## <a name="ux_device_class_audio20_control_process"></a>ux_device_class_audio20_control_process

Обработка запросов управления USB Audio 1.0.

### <a name="prototype"></a>Прототип
```C
UINT ux_device_class_audio20_control_process(
    UX_DEVICE_CLASS_AUDIO *audio,
    UX_SLAVE_TRANSFER *transfer_request,
    UX_DEVICE_CLASS_AUDIO20_CONTROL_GROUP *group);
```

### <a name="description"></a>Описание

Эта функция управляет базовыми запросами, отправленными узлом в конечной точке управления, с конкретным типом USB Audio 2.0.

Частота выборки Audio 2.0 (предполагается одна фиксированная частота), функции запросов громкости и отключения звука, которые обрабатываются внутри функции. При обработке запросов предварительно определенные данные, передаваемые последним параметром (group), используются для ответа на запросы и сохранения изменений управления.

### <a name="parameters"></a>Параметры

- **audio**: указатель на экземпляр звука.
- **transfer**: указатель на экземпляр запроса на передачу.
- **group**: группа данных для процесса запроса.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00): операция успешно выполнена.
- **UX_ERROR** (0xFF): ошибка в функции.

### <a name="example"></a>Пример

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
