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
# <a name="chapter-5---usbx-device-class-considerations"></a>Глава 5. Сведения о классах устройств USBX

## <a name="device-class-registration"></a>Регистрация класса устройства

Принцип регистрации каждого класса устройства один и тот же. Структура, содержащая параметры конкретного класса, передается функции инициализации класса.

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

Каждый класс может зарегистрировать (при необходимости) функцию обратного вызова при активации экземпляра класса. Затем обратный вызов вызывается стеком устройств для информирования приложения о том, что был создан экземпляр.

Приложение будет иметь в своем теле две функции для активации и отключения, как показано в следующем примере.

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

Не рекомендуется выполнять какие-либо действия в этих функциях, кроме запоминания экземпляра класса и его синхронизации с остальной частью приложения.

## <a name="usb-device-storage-class"></a>Класс хранения USB-устройства

Класс хранения USB-устройства позволяет сделать запоминающее устройство, внедренное в систему, видимым для USB-хоста.

Класс хранения USB-устройства сам по себе не предоставляет решение для хранения данных. Он просто принимает и интерпретирует запросы SCSI, поступающие от узла. Если один из этих запросов является командой на чтение или запись, он вызывает предварительно заданный обратный вызов к реальному обработчику запоминающего устройства, например драйверу устройства ATA или драйверу устройства флэш-памяти.

При инициализации класса хранения устройства классу, который содержит всю необходимую информацию, присваивается структура указателя. Ниже приведен пример кода.

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

В этом примере строки хранилища драйвера настраиваются путем присвоения указателей строк соответствующему параметру. Если какой-либо из указателей остается UX_NULL, используется строка ОСРВ Azure по умолчанию.

В этом примере адрес последнего блока диска или LBA указывается как размер логического сектора. LBA — это количество секторов, доступных на носителе (1). На обычном носителе данных длина блока составляет 512. Для дисководов оптических дисков можно задать значение 2048.

Приложению необходимо передать три указателя на функцию обратного вызова, чтобы класс хранения считывал, записывал и получал сведения о состоянии носителя.

Прототипы для функций чтения и записи показаны в примере ниже.

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

Где:

- *storage* — экземпляр класса хранения.
- *lun* — логический номер устройства (LUN), на который отправляется команда.
- *data_pointer* — адрес буфера, используемого для чтения или записи.
- *number_blocks* — количество секторов для чтения и записи.
- *lba* — адрес сектора для чтения.
- *media_status* должен полностью совпадать с возвращаемым значением обратного вызова состояния носителя.

Возвращаемое значение может быть либо UX_SUCCESS, либо UX_ERROR, указывающие на успешную или неудачную операцию. Этим операциям не требуется возвращать другие коды ошибок. Если при выполнении какой-либо операции возникает ошибка, класс хранения вызовет функцию обратного вызова состояния.

Эта функция имеет следующий прототип.

```c
ULONG media_status( 
    VOID *storage,  
    ULONG lun,  
    ULONG media_id,  
    ULONG *media_status);
```

Параметр вызова media_id в настоящее время не используется и всегда должен быть равен нулю. В будущем его можно использовать для различения нескольких запоминающих устройств или запоминающих устройств с несколькими LUN SCSI. Эта версия класса хранения не поддерживает несколько экземпляров класса хранения или запоминающих устройств с несколькими LUN SCSI.

Возвращаемое значение — это код ошибки SCSI, который может иметь следующий формат.

- **Биты 0–7**: смысловой ключ
- **Биты 8–15**: дополнительный смысловой код
- **Биты 16–23**: квалификатор дополнительного смыслового кода

В следующей таблице приведены возможные сочетания смыслового ключа/ASC/ASCQ.

| Смысловой ключ | ASC | ASCQ | Описание                                       |
| --------- | --- | ---- | ------------------------------------------------- |
| 00        | 00  | 00   | НЕТ СМЫСЛА                                          |
| 01        | 17  | 01   | ВОССТАНОВЛЕННЫЕ ДАННЫЕ С ПОВТОРНЫМИ ПОПЫТКАМИ                       |
| 01        | 18  | 00   | ВОССТАНОВЛЕННЫЕ ДАННЫЕ С ECC                           |
| 02        | 04  | 01   | ЛОГИЧЕСКИЙ ДИСК НЕ ГОТОВ — ГОТОВИТСЯ К РАБОТЕ          |
| 02        | 04  | 02   | ЛОГИЧЕСКИЙ ДИСК НЕ ГОТОВ — ТРЕБУЕТСЯ ИНИЦИАЛИЗАЦИЯ |
| 02        | 04  | 04   | ЛОГИЧЕСКОЕ УСТРОЙСТВО НЕ ГОТОВО — ВЫПОЛНЯЕТСЯ ФОРМАТИРОВАНИЕ       |
| 02        | 04  | FF   | ЛОГИЧЕСКИЙ ДИСК НЕ ГОТОВ — УСТРОЙСТВО ЗАНЯТО          |
| 02        | 06  | 00   | ИСХОДНОЕ ПОЛОЖЕНИЕ НЕ НАЙДЕНО                       |
| 02        | 08  | 00   | СБОЙ СВЯЗИ С ЛОГИЧЕСКИМ УСТРОЙСТВОМ                |
| 02        | 08  | 01   | ВРЕМЯ ОЖИДАНИЯ СВЯЗИ С ЛОГИЧЕСКИМ УСТРОЙСТВОМ ИСТЕКЛО               |
| 02        | 08  | 80   | ПЕРЕПОЛНЕНИЕ СВЯЗИ С ЛОГИЧЕСКИМ УСТРОЙСТВОМ                |
| 02        | 3A  | 00   | НОСИТЕЛЬ ОТСУТСТВУЕТ                                |
| 02        | 54  | 00   | СБОЙ ИНТЕРФЕЙСА МЕЖДУ USB И ХОСТ-СИСТЕМОЙ              |
| 02        | 80  | 00   | НЕДОСТАТОЧНО РЕСУРСОВ                            |
| 02        | FF  | FF   | НЕИЗВЕСТНАЯ ОШИБКА                                     |
| 03        | 02  | 00   | ПОИСК НЕ ЗАВЕРШЕН                                  |
| 03        | 03  | 00   | ОШИБКА ЗАПИСИ                                       |
| 03        | 10  | 00   | ОШИБКА CRC ИДЕНТИФИКАТОРА                                      |
| 03        | 11  | 00   | НЕУСТРАНЕННАЯ ОШИБКА ЧТЕНИЯ                            |
| 03        | 12  | 00   | НЕ УДАЛОСЬ НАЙТИ МЕТКУ АДРЕСА ДЛЯ ПОЛЯ ИДЕНТИФИКАТОРА               |
| 03        | 13  | 00   | НЕ УДАЛОСЬ НАЙТИ МЕТКУ АДРЕСА ДЛЯ ПОЛЯ ДАННЫХ             |
| 03        | 14  | 00   | ЗАРЕГИСТРИРОВАННАЯ СУЩНОСТЬ НЕ НАЙДЕНА                         |
| 03        | 30  | 01   | НЕ УДАЕТСЯ СЧИТАТЬ ДАННЫЕ С НОСИТЕЛЯ — НЕИЗВЕСТНЫЙ ФОРМАТ               |
| 03        | 31  | 01   | СБОЙ КОМАНДЫ ФОРМАТИРОВАНИЯ                             |
| 04        | 40  | NN   | СБОЙ ДИАГНОСТИКИ В КОМПОНЕНТЕ NN (80H-FFH)      |
| 05        | 1A  | 00   | ОШИБКА ДЛИНЫ СПИСКА ПАРАМЕТРОВ                       |
| 05        | 20  | 00   | НЕДОПУСТИМЫЙ КОД ОПЕРАЦИИ КОМАНДЫ                    |
| 05        | 21  | 00   | АДРЕС ЛОГИЧЕСКОГО БЛОКА ВНЕ ДОПУСТИМОГО ДИАПАЗОНА                |
| 05        | 24  | 00   | НЕДОПУСТИМОЕ ПОЛЕ В КОМАНДНОМ ПАКЕТЕ                   |
| 05        | 25  | 00   | ЛОГИЧЕСКОЕ УСТРОЙСТВО НЕ ПОДДЕРЖИВАЕТСЯ                        |
| 05        | 26  | 00   | НЕДОПУСТИМОЕ ПОЛЕ В СПИСКЕ ПАРАМЕТРОВ                   |
| 05        | 26  | 01   | НЕПОДДЕРЖИВАЕМЫЙ ПАРАМЕТР                           |
| 05        | 26  | 02   | НЕДОПУСТИМОЕ ЗНАЧЕНИЕ ПАРАМЕТРА                           |
| 05        | 39  | 00   | СОХРАНЕНИЕ ПАРАМЕТРОВ НЕ ПОДДЕРЖИВАЕТСЯ                     |
| 06        | 28  | 00   | НЕ ГОТОВО К ПЕРЕХОДУ В СОСТОЯНИЕ ГОТОВНОСТИ — НОСИТЕЛЬ ИЗМЕНЕН     |
| 06        | 29  | 00   | ПРОИЗОШЕЛ СБРОС ПИТАНИЯ ИЛИ СБРОС УСТРОЙСТВА ШИНЫ       |
| 06        | 2F  | 00   | КОМАНДЫ УДАЛЕНЫ ДРУГИМ ИНИЦИАТОРОМ             |
| 07        | 27  | 00   | НОСИТЕЛЬ С ЗАЩИТОЙ ОТ ЗАПИСИ                             |
| 0B        | 4E  | 00   | ПОПЫТКА ВЫПОЛНЕНИЯ ПЕРЕКРЫВАЮЩЕЙ КОМАНДЫ                      |

Существует два дополнительных необязательных обратных вызова, которые может реализовать приложение. Один предназначен для реагирования на команду **GET_STATUS_NOTIFICATION**, а другой — для ответа на команду **SYNCHRONIZE_CACHE**.

Если приложение должно обработать команду GET_STATUS_NOTIFICATION от узла, оно должно реализовать обратный вызов со следующим прототипом.

```c
UINT ux_slave_class_storage_media_notification( 
    VOID *storage,  
    ULONG lun,
    ULONG media_id,  
    ULONG notification_class,
    UCHAR **media_notification,  
    ULONG *media_notification_length);
```

Где:

- *storage* — экземпляр класса хранения.
- *media_id* — в настоящее время не используется. notification_class указывает класс уведомления.
- *media_notification* задается приложением для буфера, содержащего ответ для уведомления.
- *media_notification_length* задается приложением для хранения длины буфера ответа.

Возвращаемое значение указывает, была ли команда успешной: должно быть либо **UX_SUCCESS**, либо **UX_ERROR**.

Если приложение не реализует этот обратный вызов, то после получения команды **GET_STATUS_NOTIFICATION** USBX будет уведомлять узел о том, что команда не реализована.

Команда **SYNCHRONIZE_CACHE** должна быть обработана, если приложение использует кэш для записи с узла. Узел может отправить эту команду, если известно, что запоминающее устройство будет отключено. Например, если в ОС Windows щелкнуть значок устройства флэш-памяти на панели инструментов правой кнопкой мыши и выбрать команду "Извлечь \[имя запоминающего устройства\]", Windows выдаст этому устройству команду **SYNCHRONIZE_CACHE**.

Если приложение должно обработать команду **GET_STATUS_NOTIFICATION** от узла, оно должно реализовать обратный вызов со следующим прототипом.

```c
UINT ux_slave_class_storage_media_flush(
    VOID *storage, 
    ULONG lun,
    ULONG number_blocks, 
    ULONG lba, 
    ULONG *media_status);
```

Где:

- *storage* — экземпляр класса хранения.
- *lun* указывает, к какому LUN направлена команда.
- *number_blocks* — количество синхронизируемых блоков.
- *lba* — адрес сектора первого блока для синхронизации.
- *media_status* должен полностью совпадать с возвращаемым значением обратного вызова состояния носителя.

Возвращаемое значение указывает, была ли команда успешной: должно быть либо **UX_SUCCESS**, либо **UX_ERROR**.

### <a name="multiple-scsi-lun"></a>Несколько LUN SCSI

Класс хранения устройства USBX поддерживает несколько LUN. Поэтому можно создать запоминающее устройство, которое будет одновременно работать как компакт-диск и устройство флэш-памяти. В этом случае инициализация будет немного отличаться. Ниже приведен пример для устройства флэш-памяти и компакт-диска.

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

## <a name="usb-device-cdc-acm-class"></a>Класс CDC-ACM USB-устройства

Класс CDC-ACM USB-устройства позволяет хост-системе USB обмениваться данными с устройством как с устройством с последовательным интерфейсом. Этот класс основан на стандарте USB и является подмножеством стандарта CDC.

В стеке устройств необходимо объявить совместимую с CDC-ACM платформу устройств. Ниже приведен пример этого.

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

Класс CDC-ACM использует составную платформу устройств для группирования интерфейсов (элементов управления и данных). В результате при определении дескриптора устройства следует проявлять осторожность. USBX использует дескриптор IAD для определения внутреннего порядка привязки интерфейсов. Дескриптор IAD должен быть объявлен перед интерфейсами. Он должен содержать первый интерфейс класса CDC-ACM и количество присоединенных интерфейсов.

Класс CDC-ACM также использует функциональный дескриптор объединения, который выполняет ту же функцию, что и новый дескриптор IAD. Несмотря на то что функциональный дескриптор объединения должен быть объявлен по историческим причинам и для обеспечения совместимости на стороне узла, он не используется USBX.

При инициализации класса CDC-ACM требуются следующие параметры.

```c
/* Set the parameters for callback when insertion/extraction of a CDC device. */

parameter.ux_slave_class_cdc_acm_instance_activate = tx_demo_cdc_instance_activate;

parameter.ux_slave_class_cdc_acm_instance_deactivate = tx_demo_cdc_instance_deactivate;

parameter.ux_slave_class_cdc_acm_parameter_change = tx_demo_cdc_instance_parameter_change;

/* Initialize the device cdc class. This class owns both interfaces starting with 0. */
status = ux_device_stack_class_register(_ux_system_slave_class_cdc_acm_name,ux_device_class_cdc_acm_entry,
    1,0, &parameter);
```

Два определенных параметра — это указатели обратного вызова в пользовательские приложения, которые будут вызываться при активации или отключении этого класса стеком.

Третий параметр — это указатель обратного вызова в пользовательское приложение, которое будет вызываться при изменении параметра кода строки или состояния строки. Например, при получении от узла запроса на изменение состояния DTR на **TRUE** вызывается обратный вызов. В пользовательском приложении можно проверить состояние строки с помощью функции IOCTL, чтобы знать, что узел готов к обмену данными.

CDC-ACM основан на стандарте USB-IF, и он автоматически распознается операционными системами MacOs и Linux. В платформах Windows, предшествующих версии 10, для этого класса требуется INF-файл. В Windows 10 не требуется никаких INF-файлов. Мы предоставляем шаблон для класса CDC-ACM, который находится в каталоге ***usbx_windows_host_files***. Для более поздней версии Windows следует использовать файл CDC_ACM_Template_Win7_64bit.INF (кроме Win10). Этот файл необходимо изменить в соответствии с идентификатором PID/VID, используемым устройством. PID/VID зависит от клиента, если компания и продукт зарегистрированы с использованием USB-IF. В INF-файле поля для изменения находятся здесь.

```INF
[DeviceList]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000

[DeviceList.NTamd64]
%DESCRIPTION%=DriverInstall, USB\VID_8484&PID_0000
```

В платформе устройств устройства CDC-ACM идентификатор PID/VID хранится в дескрипторе устройства (см. дескриптор устройства, объявленный выше).

Когда хост-системы USB обнаруживают устройство USB CDC-ACM, они подключают последовательный класс и устройство можно использовать с любой последовательной терминальной программой. Подробнее см. в разделе "Операционная система узла".

Функции API класса CDC-ACM определены ниже.

### <a name="ux_device_class_cdc_acm_ioctl"></a>ux_device_class_cdc_acm_ioctl

Выполнение IOCTL в интерфейсе CDC-ACM

### <a name="prototype"></a>Прототип

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm, 
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда приложению требуется выполнить различные вызовы IOCTL в интерфейс CDC ACM.

### <a name="parameters"></a>Параметры

- **cdc_acm**: указатель на экземпляр класса CDC.
- **ioctl_function**: функция IOCTL для выполнения.
- **parameter**: указатель на параметр, относящийся к вызову IOCTL.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) — операция успешно выполнена
- **UX_ERROR** (0xFF) — ошибка в функции

### <a name="example"></a>Например, .

```c
/* Start cdc acm callback transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START, &callback);

if(status != UX_SUCCESS)
    return;
```

### <a name="ioctl-functions"></a>Функции IOCTL

| Функция                                        | Значение |
| ----------------------------------------------- | - |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING    | 1 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING    | 2 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE     | 3 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE         | 4 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE     | 5 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START | 6 |
| UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP  | 7 |

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_coding"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING

Выполнение IOCTL: настройка кодирования строк в интерфейсе CDC-ACM

### <a name="prototype"></a>Прототип

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда приложению необходимо задать параметры кодирования строк.

### <a name="parameters"></a>Параметры

- **cdc_acm**: указатель на экземпляр класса CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_CODING.
- **parameter**: указатель на структуру параметров строки.

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a>Возвращаемое значение

**UX_SUCCESS** (0x00) — операция успешно выполнена

### <a name="example"></a>Например, .

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

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_coding"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_CODING

Выполнение IOCTL: получение кода строки для интерфейса CDC-ACM

### <a name="prototype"></a>Прототип

```c
device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда приложению требуется получить параметры кодирования строки.

### <a name="parameters"></a>Параметры

- **cdc_acm**: указатель на экземпляр класса CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_ LINE_CODING.
- **parameter**: указатель на структуру параметров строки.

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER_STRUCT
{
    ULONG ux_slave_class_cdc_acm_parameter_baudrate;
    UCHAR ux_slave_class_cdc_acm_parameter_stop_bit;
    UCHAR ux_slave_class_cdc_acm_parameter_parity;
    UCHAR ux_slave_class_cdc_acm_parameter_data_bit;
} UX_SLAVE_CLASS_CDC_ACM_LINE_CODING_PARAMETER;
```

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) — операция успешно выполнена

### <a name="example"></a>Например, .

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

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_get_line_state"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE

Выполнение IOCTL: получение состояния строки в интерфейсе CDC-ACM

## <a name="prototype"></a>Прототип

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM*cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда приложению требуется получить параметры состояния строки.

### <a name="parameters"></a>Параметры

- **cdc_acm**: указатель на экземпляр класса CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_GET_LINE_STATE.
- **parameter**: указатель на структуру параметров строки.

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) — операция успешно выполнена

### <a name="example"></a>Например, .

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

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_set_line_state"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE

Выполнение IOCTL: задание состояния строки в интерфейсе CDC-ACM

### <a name="prototype"></a>Прототип

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда приложению требуется получить параметры состояния строки.

### <a name="parameters"></a>Параметры

- **cdc_acm**: указатель на экземпляр класса CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE.
- **parameter**: указатель на структуру параметров строки.

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER_STRUCT
{
    UCHAR ux_slave_class_cdc_acm_parameter_rts;
    UCHAR ux_slave_class_cdc_acm_parameter_dtr;
} UX_SLAVE_CLASS_CDC_ACM_LINE_STATE_PARAMETER;
```

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) — операция успешно выполнена

### <a name="example"></a>Например, .

```c
/* This is to set RTS state. */

line_state.ux_slave_class_cdc_acm_parameter_rts = UX_TRUE;
status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_SET_LINE_STATE, &line_state);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_abort_pipe"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE

Выполнение IOCTL: прерывание канала в интерфейсе CDC-ACM

### <a name="prototype"></a>Прототип

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда приложению требуется прервать канал. Например, чтобы прервать текущую операцию записи, в качестве параметра следует передать UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT.

### <a name="parameters"></a>Параметры

- **cdc_acm**: указатель на экземпляр класса CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE.
- **parameter**: направление канала.

```c
UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT 1

UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_RCV 2
```

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) — операция успешно выполнена
- **UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) — недопустимое направление канала

### <a name="example"></a>Например, .

```c
/* This is to abort the Xmit pipe. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_ABORT_PIPE,
    UX_SLAVE_CLASS_CDC_ACM_ENDPOINT_XMIT);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_start"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START

Выполнение IOCTL: запуск передачи в интерфейсе CDC-ACM

### <a name="prototype"></a>Прототип

```c
UINT ux_device_class_cdc_acm_ioctl ( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда приложению требуется использовать передачу с обратным вызовом.

### <a name="parameters"></a>Параметры

- **cdc_acm**: указатель на экземпляр класса CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.
- **parameter**: указатель на структуру параметров запуска передачи.

```c
typedef struct UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER_STRUCT
{
    UINT (*ux_device_class_cdc_acm_parameter_write_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, ULONG length);
    UINT (*ux_device_class_cdc_acm_parameter_read_callback)(struct UX_SLAVE_CLASS_CDC_ACM_STRUCT *cdc_acm,
        UINT status, UCHAR *data_pointer, ULONG length);
} UX_SLAVE_CLASS_CDC_ACM_CALLBACK_PARAMETER;
```

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) — операция успешно выполнена
- **UX_ERROR** (0xFF) — передача уже запущена
- **UX_MEMORY_INSUFFICIENT** (0x12) — сбой выделения памяти

### <a name="example"></a>Например, .

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

### <a name="ux_device_class_cdc_acm_ioctl-ux_slave_class_cdc_acm_ioctl_transmission_stop"></a>ux_device_class_cdc_acm_ioctl: UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP

Выполнение IOCTL: остановка передачи в интерфейсе CDC-ACM

### <a name="prototype"></a>Прототип

```c
UINT ux_device_class_cdc_acm_ioctl( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    ULONG ioctl_function,  
    VOID *parameter);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда приложению требуется отключить передачу с помощью обратного вызова.

### <a name="parameters"></a>Параметры

- **cdc_acm**: указатель на экземпляр класса CDC.
- **ioctl_function**: ux_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSI ON_STOP.
- **parameter**: не используется.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) — операция успешно выполнена
- **UX_ERROR** (0xFF) — нет текущих передач.

### <a name="example"></a>Например, .

```c
/* Program the stop of transmission. */

status = _ux_device_class_cdc_acm_ioctl(cdc_acm_slave,
    UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_STOP, UX_NULL);

/* If status is UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_class_cdc_acm_read"></a>ux_device_class_cdc_acm_read

Чтение из канала CDC-ACM

### <a name="prototype"></a>Прототип

```c
UINT ux_device_class_cdc_acm_read( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда приложению требуется выполнить чтение из канала данных OUT (OUT — с узла, IN —с устройства). Он блокируется.

### <a name="parameters"></a>Параметры

- **cdc_acm**: указатель на экземпляр класса CDC.
- **buffer**: адрес буфера, где будут храниться данные.
- **requested_length**: максимально допустимая длина.
- **actual_length**: длина, возвращаемая в буфер.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) — операция успешно выполнена
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) — устройство больше не находится в настроенном состоянии
- **UX_TRANSFER_NO_ANSWER** (0x22) — нет ответа от устройства Возможно, устройство было отключено, пока ожидалась передача.

### <a name="example"></a>Например, .

```c
/* Read from the CDC class. */

status = ux_device_class_cdc_acm_read(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS) return;
```

### <a name="ux_device_class_cdc_acm_write"></a>ux_device_class_cdc_acm_write

Запись в канал CDC-ACM

### <a name="prototype"></a>Прототип

```c
UINT ux_device_class_cdc_acm_write( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length,  
    ULONG *actual_length);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда приложению требуется выполнить запись в канал данных IN (IN — с узла, OUT — с устройства). Он блокируется.

### <a name="parameters"></a>Параметры

- **cdc_acm**: указатель на экземпляр класса CDC.
- **buffer**: адрес буфера, где хранятся данные.
- **requested_length**: длина буфера для записи.
- **actual_length**: длина, возвращенная в буфер после выполнения операции записи.

### <a name="return-value"></a>Возвращаемое значение
- **UX_SUCCESS** (0x00) — операция успешно выполнена
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) — устройство больше не находится в настроенном состоянии
- **UX_TRANSFER_NO_ANSWER** (0x22) — нет ответа от устройства Возможно, устройство было отключено, пока ожидалась передача.

### <a name="example"></a>Например, .

```c
/* Write to the CDC class bulk in pipe. */

status = ux_device_class_cdc_acm_write(cdc, buffer, UX_DEMO_BUFFER_SIZE, &actual_length);

if(status != UX_SUCCESS)
    return;
```

### <a name="ux_device_class_cdc_acm_write_with_callback"></a>ux_device_class_cdc_acm_write_with_callback

Запись в канал CDC-ACM с обратным вызовом

### <a name="prototype"></a>Прототип

```c
UINT ux_device_class_cdc_acm_write_with_callback( 
    UX_SLAVE_CLASS_CDC_ACM *cdc_acm,
    UCHAR *buffer,  
    ULONG requested_length);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда приложению требуется выполнить запись в канал данных IN (IN — с узла, OUT — с устройства). Эта функция не блокируется, и она выполняется через обратный вызов, заданный в UX_SLAVE_CLASS_CDC_ACM_IOCTL_TRANSMISSION_START.

### <a name="parameters"></a>Параметры

- **cdc_acm**: указатель на экземпляр класса CDC.
- **buffer**: адрес буфера, где хранятся данные.
- **requested_length**: длина буфера для записи.
- **actual_length**: длина, возвращенная в буфер после выполнения операции записи.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) — операция успешно выполнена
- **UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) — устройство больше не находится в настроенном состоянии
- **UX_TRANSFER_NO_ANSWER** (0x22) — нет ответа от устройства Возможно, устройство было отключено, пока ожидалась передача.

### <a name="example"></a>Например, .

```c
/* Write to the CDC class bulk in pipe non blocking mode. */
status = ux_device_class_cdc_acm_write_with_callback(cdc, buffer, UX_DEMO_BUFFER_SIZE);

if(status != UX_SUCCESS)
    return;
```

### <a name="usb-device-cdc-ecm-class"></a>Класс CDC-ECM USB-устройства

Класс CDC-ECM USB-устройства позволяет хост-системе USB обмениваться данными с устройством как с устройством Ethernet. Этот класс основан на стандарте USB и является подмножеством стандарта CDC.

В стеке устройств необходимо объявить совместимую с CDC-ACM платформу устройств. Ниже приведен пример этого.

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

Класс CDC-ECM использует подход, близко схожий с подходом на основе дескриптора устройства CDC-ACM, а также требует наличия дескриптора IAD. Определение см. в описании класса CDC-ACM.

Помимо обычной платформы устройств, CDC-ECM требует специальных дескрипторов строк. Ниже приведен пример кода.

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

Дескриптор строки MAC-адреса используется классом CDC ECM для ответа на запросы к узлу в соответствии с MAC-адресом устройства, отвечающего по протоколу TCP/IP. Его можно задать в соответствии с выбранным устройством, однако его необходимо определить здесь.

Инициализация класса CDC-ECM выполняется следующим образом.

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

Инициализация этого класса ожидает один и тот же обратный вызов функции для активации и отключения, однако здесь в качестве упражнения задано значение NULL, поэтому обратный вызов не выполняется.

Следующие параметры предназначены для определения идентификаторов узлов. Для репликации CDC-ECM требуется два узла: локальный узел и удаленный узел. Локальный узел задает MAC-адрес устройства, а удаленный узел — MAC-адрес узла. Удаленный узел должен быть таким же, как тот, который объявлен в дескрипторе строки платформы устройства.

Класс CDC-ECM содержит встроенные API для передачи данных обоими способами, однако они скрыты для приложения, поскольку пользовательское приложение взаимодействует с USB-устройством Ethernet через NetX.

Класс USBX CDC-ECM тесно привязан к сетевому стеку NetX ОСРВ Azure. Приложение, использующее и NetX, и класс USBX CDC-ECM, активирует сетевой стек NetX обычным образом, но в дополнение необходимо активировать сетевой стек USB, как показано ниже.

```c
/* Initialize the NetX system. */
nx_system_initialize();

/* Perform the initialization of the network driver. This will initialize the USBX network layer.*/
ux_network_driver_init();
```

Сетевой стек USB следует активировать только один раз, и он не зависит от CDCECM, однако он необходим для любого класса USB, которому требуются службы NetX.

Класс CDC-ECM распознается узлами MAC OS и Linux. Однако в Microsoft Windows отсутствует собственный драйвер для распознавания CDC-ECM. Для платформ Windows существуют некоторые коммерческие продукты, которые предоставляют собственный INF-файл. Этот файл потребуется изменить так же, как шаблон CDC-ACM INF, чтобы он соответствовал идентификатору PID/VID сетевого USB-устройства.

## <a name="usb-device-hid-class"></a>Класс HID USB-устройства

Класс HID USB-устройства позволяет хост-системе USB подключаться к HID-устройству с конкретными возможностями клиента HID.

Класс USBX HID довольно прост в сравнении с узлом. Он тесно связан с поведением устройства и его дескриптором HID.

Любой клиент HID сначала должен определить платформу HID-устройства, как показано ниже.

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

Платформа HID содержит дескриптор интерфейса, описывающий класс HID и подкласс HID-устройства. Интерфейс HID может быть отдельным классом или частью составного устройства.

В настоящее время класс USBX HID не поддерживает несколько идентификаторов отчетов, поскольку большинству приложений требуется только один идентификатор (нулевой идентификатор). Если вам требуется использовать несколько идентификаторов отчетов, свяжитесь с нами.

Инициализация класса HID осуществляется следующим образом. В качестве примера используется USB-клавиатура.

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

Приложению необходимо передать в класс HID дескриптор отчета HID и его длину. Дескриптор отчета представляет собой коллекцию элементов, описывающих устройство. Дополнительные сведения о грамматике HID см. в спецификации класса HID USB.

Помимо дескриптора отчета, приложение передает обратный вызов при возникновении события HID.

Класс USBX HID поддерживает следующие стандартные команды HID от узла.

| Имя команды                             | Значение | Описание                                      |
| ---------------------------------------- | ----- | ------------------------------------------------ |
| UX_DEVICE_CLASS_HID_COMMAND_GET_REPORT   | 0x01  | Получение отчета от устройства                     |
| UX_DEVICE_CLASS_HID_COMMAND_GET_IDLE     | 0x02  | Получение частоты простоя конечной точки прерывания |
| UX_DEVICE_CLASS_HID_COMMAND_GET_PROTOCOL | 0x03  | Получение протокола, выполняющегося на устройстве           |
| UX_DEVICE_CLASS_HID_COMMAND_SET_REPORT   | 0x09  | Задание отчета для устройства                       |
| UX_DEVICE_CLASS_HID_COMMAND_SET_IDLE     | 0x0a  | Задание частоты простоя конечной точки прерывания |
| UX_DEVICE_CLASS_HID_COMMAND_SET_PROTOCOL | 0x0b  | Получение протокола, выполняющегося на устройстве           |

Получение и задание отчета являются наиболее часто используемыми командами HID для обмена данными между узлом и устройством. Чаще всего узел отправляет данные в конечную точку управления, но может получать данные либо в конечной точке прерывания, либо с помощью команды GET_REPORT для получения данных в конечной точке управления.

Класс HID может передавать данные обратно на узел в конечной точке прерывания с помощью функции ux_device_class_hid_event_set.

### <a name="ux_device_class_hid_event_set"></a>ux_device_class_hid_event_set

Задание события для класса HID

### <a name="prototype"></a>Прототип

```c
UINT ux_device_class_hid_event_set( 
    UX_SLAVE_CLASS_HID *hid,
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда приложению требуется отправить событие HID обратно на узел. Функция не блокируется, она просто помещает отчет в циклическую очередь и возвращает его в приложение.

### <a name="parameters"></a>Параметры

- **hid**: указатель на экземпляр класса HID.
- **hid_event**: указатель на структуру события HID.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) — операция успешно выполнена
- **UX_ERROR** (0xFF) — ошибка ввиду отсутствия пространства в циклической очереди

### <a name="example"></a>Например, .

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

Обратный вызов, определенный при инициализации класса HID, выполняет действие, противоположное отправке события. Он получает в качестве входных данных событие, отправленное узлом. Прототип обратного вызова выглядит следующим образом.

### <a name="hid_callback"></a>hid_callback

Получение события из класса HID

### <a name="prototype"></a>Прототип

```c
UINT hid_callback(
    UX_SLAVE_CLASS_HID *hid, 
    UX_SLAVE_CLASS_HID_EVENT *hid_event);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда узел отправляет отчет HID в приложение.

### <a name="parameters"></a>Параметры

- **hid**: указатель на экземпляр класса HID.
- **hid_event**: указатель на структуру события HID.

### <a name="example"></a>Например, .

В следующем примере показано, как интерпретировать событие для клавиатуры HID.

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
