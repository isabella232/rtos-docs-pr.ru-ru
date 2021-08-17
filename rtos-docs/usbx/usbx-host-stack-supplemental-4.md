---
title: Реализация PictBridge в USBX
description: USBX поддерживает полную реализацию PictBridge как на узле, так и на устройстве. С обеих сторон PictBridge размещается поверх класса USBX PIMA.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9f4ba97741d2fc5f93afe6866b9ae6e9dc1e98a977eb3d6050c4a7489804c93c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790725"
---
# <a name="chapter-4-usbx-pictbridge-implementation"></a>Глава 4. Реализация PictBridge в USBX

USBX поддерживает полную реализацию PictBridge как на узле, так и на устройстве. С обеих сторон Pictbridge размещается поверх класса USBX PIMA. 

Стандарты Pictbridge обеспечивают подключение цифровой фотокамеры или смартфона непосредственно к принтеру, без компьютера в качестве посредника, и позволяют напрямую выполнять печатать на принтерах, поддерживающих этот стандарт Pictbridge.

Когда камера или телефон подключаются к принтеру, этот принтер является USB-узлом, а камера — USB-устройством. Но при работе с PictBridge камера отображается как узел и управляет командами для печати. Камера является сервером хранилища, а принтер выполняет роль клиента хранилища. С другой стороны, принтер является сервером печати, а камера подключается к нему как клиент.

PictBridge использует транспортный уровень USB и протокол связи PTP (протокол передачи изображений).

Ниже представлена схема передачи команд и ответов между клиентом DPS и сервером DPS при выполнении задания печати.

![Схема передачи команд и ответов между клиентом DPS и сервером DPS при выполнении задания печати.](./media/usbx-host-stack-supplemental/dps-client-server.png)

## <a name="pictbridge-client-implementation"></a>Реализация клиента PictBridge

Для использования Pictbridge на клиенте нужно сначала запустить стек устройств USBX и класс PIMA.

Платформа устройства описывает класс PIMA следующим образом.

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

Класс PIMA использует значение 0x06 в поле ID (идентификатор), а также подкласс 0x01 для изображения и протокол 0x01 для PIMA 15740.

В этом классе определены три конечные точки, из них две — для отправки и получения данных, а третья — для прерываний по событиям.

В отличие от реализаций других устройств USBX, приложению PictBridge не нужно определять сам класс. Достаточно вызвать функцию ***ux_pictbridge_dpsclient_start***. Пример представлен ниже.

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

Ниже перечислены параметры, которые передаются клиенту PictBridge:

```C
pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_vendor_name
    : String of Vendor name pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_product_name
    : String of product name pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_serial_no,
    : String of serial number pictbridge.ux_pictbridge_dpslocal.ux_pictbridge_devinfo_dpsversions
    : String of version pictbridge.ux_pictbridge_dpslocal. ux_pictbridge_devinfo_vendor_specific_version
    : Value set to 0x0100;
```

После этого требуется синхронизация устройства и узла и переход к состоянию готовности к обмену данными.

Для этого мы ожидаем изменения флага событий, как показано ниже:

```C
/* We should wait for the host and the client to discover one another. */
status = ux_utility_event_flags_get
    (&pictbridge.ux_pictbridge_event_flags_group,
    UX_PICTBRIDGE_EVENT_FLAG_DISCOVERY,TX_AND_CLEAR, &actual_flags,
    UX_PICTBRIDGE_EVENT_TIMEOUT);
```

Когда конечный автомат перейдет в состояние **DISCOVERY_COMPLETE** (Обнаружение завершено), сторона камеры (клиент DPS) будет собирать сведения о принтере и его возможностях.

Когда клиент DPS будет готов принять задание печати, он перейдет в состояние **UX_PICTBRIDGE_NEW_JOB_TRUE**. Это можно проверить в следующем примере:

```C
/* Check if the printer is ready for a print job. */
if (pictbridge.ux_pictbridge_dpsclient.ux_pictbridge_devinfo_newjobok ==
    UX_PICTBRIDGE_NEW_JOB_TRUE)

    /* We can print something … */
```

Теперь нужно заполнить дескрипторы задания печати, как показано ниже:

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

Теперь клиент PictBridge получил задание для печати и будет постепенно получать блоки изображений от приложения через обратный вызов, определенный в соответствующем поле.

```C
jobinfo ->ux_pictbridge_jobinfo_object_data_read
```

Прототип этой функции определяется следующим образом.

## <a name="ux_pictbridge_jobinfo_object_data_read"></a>ux_pictbridge_jobinfo_object_data_read

Копирование блока данных для печати из пользовательского пространства.

### <a name="prototype"></a>Прототип

```C
UINT **ux_pictbridge_jobinfo_object_data_read(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG object_offset,
    ULONG object_length,
    ULONG *actual_length)
```

### <a name="description"></a>Описание

Эта функция вызывается, когда клиенту DPS требуется получить блок данных для печати на целевом принтере Pictbridge.

### <a name="parameters"></a>Параметры

- **pictbridge** — указатель на экземпляр класса pictbridge;
- **object_buffer** — указатель на буфер объектов;
- **object_offset** — позиция для начала чтения блока данных;
- **object_length** — требуемая длина ответа;
- **actual_length** — длина фактически полученного ответа.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00): операция успешно выполнена.
- **UX_ERROR** (0x01): приложению не удалось извлечь данные.

### <a name="example"></a>Например, .

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

## <a name="pictbridge-host-implementation"></a>Реализация узла Pictbridge

Реализация узла Pictbridge довольно сильно отличается от реализации клиента.

Первое, что нужно сделать в среде размещения PictBridge, — зарегистрировать класс PIMA, как показано в примере ниже.

```C
status = ux_host_stack_class_register(ux_system_host_class_pima_name,
    ux_host_class_pima_entry);
if(status != UX_SUCCESS)
    return;
```

Этот класс реализует универсальный слой PTP, размещенный между стеком узла USB и слоем PictBridge.

Следующим этапом мы инициализируем значения по умолчанию для служб печати PictBridge, как показано ниже.

| Поле PictBridge       | Значение                                  |
|------------------------|----------------------------------------|
| DpsVersion[0]          | 0x00010000                             |
| DpsVersion[1]          | 0x00010001                             |
| DpsVersion[2]          | 0x00000000                             |
| VendorSpecificVersion  | 0x00010000                             |
| PrintServiceAvailable  | 0x30010000                             |
| Qualities[0]           | UX_PICTBRIDGE_QUALITIES_DEFAULT        |
| Qualities[1]           | UX_PICTBRIDGE_QUALITIES_NORMAL         |
| Qualities[2]           | UX_PICTBRIDGE_QUALITIES_DRAFT          |
| Qualities[3]           | UX_PICTBRIDGE_QUALITIES_FINE           |
| PaperSizes[0]          | UX_PICTBRIDGE_PAPER_SIZES_DEFAULT      |
| PaperSizes[1]          | UX_PICTBRIDGE_PAPER_SIZES_4IX6I        |
| PaperSizes[2]          | UX_PICTBRIDGE_PAPER_SIZES_L            |
| PaperSizes[3]          | UX_PICTBRIDGE_PAPER_SIZES_2L           |
| PaperSizes[4]          | UX_PICTBRIDGE_PAPER_SIZES_LETTER       |
| PaperTypes[0]          | UX_PICTBRIDGE_PAPER_TYPES_DEFAULT      |
| PaperTypes[1]          | UX_PICTBRIDGE_PAPER_TYPES_PLAIN        |
| PaperTypes[2]          | UX_PICTBRIDGE_PAPER_TYPES_PHOTO        |
| FileTypes[0]           | UX_PICTBRIDGE_FILE_TYPES_DEFAULT       |
| FileTypes[1]           | UX_PICTBRIDGE_FILE_TYPES_EXIF_JPEG     |
| FileTypes[2]           | UX_PICTBRIDGE_FILE_TYPES_JFIF          |
| FileTypes[3]           | UX_PICTBRIDGE_FILE_TYPES_DPOF          |
| DatePrints[0]          | UX_PICTBRIDGE_DATE_PRINTS_DEFAULT      |
| DatePrints[1]          | UX_PICTBRIDGE_DATE_PRINTS_OFF          |
| DatePrints[2]          | UX_PICTBRIDGE_DATE_PRINTS_ON           |
| FileNamePrints[0]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_DEFAULT |
| FileNamePrints[1]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_OFF     |
| FileNamePrints[2]      | UX_PICTBRIDGE_FILE_NAME_PRINTS_ON      |
| ImageOptimizes[0]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_DEFAULT  |
| ImageOptimizes[1]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_OFF      |
| ImageOptimizes[2]      | UX_PICTBRIDGE_IMAGE_OPTIMIZES_ON       |
| Layouts[0]             | UX_PICTBRIDGE_LAYOUTS_DEFAULT          |
| Layouts[1]             | UX_PICTBRIDGE_LAYOUTS_1_UP_BORDER      |
| Layouts[2]             | UX_PICTBRIDGE_LAYOUTS_INDEX_PRINT      |
| Layouts[3]             | UX_PICTBRIDGE_LAYOUTS_1_UP_BORDERLESS  |
| FixedSizes[0]          | UX_PICTBRIDGE_FIXED_SIZE_DEFAULT       |
| FixedSizes[1]          | UX_PICTBRIDGE_FIXED_SIZE_35IX5I        |
| FixedSizes[2]          | UX_PICTBRIDGE_FIXED_SIZE_4IX6I         |
| FixedSizes[3]          | UX_PICTBRIDGE_FIXED_SIZE_5IX7I         |
| FixedSizes[4]          | UX_PICTBRIDGE_FIXED_SIZE_7CMX10CM      |
| FixedSizes[5]          | UX_PICTBRIDGE_FIXED_SIZE_LETTER        |
| FixedSizes[6]          | UX_PICTBRIDGE_FIXED_SIZE_A4            |
| Croppings[0]           | UX_PICTBRIDGE_CROPPINGS_DEFAULT        |
| Croppings[1]           | UX_PICTBRIDGE_CROPPINGS_OFF            |
| Croppings[2]           | UX_PICTBRIDGE_CROPPINGS_ON             |

Конечный автомат узла DPS перейдет состояние бездействия и будет ожидать новое задание для печати.

Теперь вы можете запустить PictBridge на стороне узла, как показано в примере ниже.

```C
/* Activate the pictbridge dpshost. */

status = ux_pictbridge_dpshost_start(&pictbridge, pima);
if (status != UX_SUCCESS)
    return;
```

Для работы узла PictBridge нужен обратный вызов, информирующий о готовности данных к печати. Для реализации этого в структуре узла PictBridge передается указатель функции, как показано ниже.

```C
/* Set a callback when an object is being received. */

pictbridge.ux_pictbridge_application_object_data_write =
    tx_demo_object_data_write;
```

Эта функция имеет следующие свойства.

## <a name="ux_pictbridge_application_object_data_write"></a>ux_pictbridge_application_object_data_write

Запись блока данных для печати.

### <a name="prototype"></a>Прототип

```C
UINT **ux_pictbridge_application_object_data_write(
    UX_PICTBRIDGE *pictbridge,
    UCHAR *object_buffer,
    ULONG offset,
    ULONG total_length,
    ULONG length);
```

### <a name="description"></a>Описание

Эта функция вызывается, когда серверу DPS нужно получить блок данных от клиента DPS для печати на локальном принтере.

### <a name="parameters"></a>Параметры

- **pictbridge** — указатель на экземпляр класса pictbridge;
- **object_buffer** — указатель на буфер объектов;
- **object_offset** — позиция для начала чтения блока данных;
- **total_length** — полная длина объекта;
- **length** — длина этого буфера.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00): операция успешно выполнена.
- **UX_ERROR** (0x01): приложению не удалось распечатать данные.

### <a name="example"></a>Пример

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
