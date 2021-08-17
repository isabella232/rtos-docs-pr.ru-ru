---
title: Глава 5. Драйверы ввода-вывода для ОСРВ Azure FileX
description: Разработчики могут использовать представленные в этой главе сведения о драйверах ввода-вывода для ОСРВ Azure FileX при написании драйверов для конкретных приложений.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 163893119837a46479b3f346c2bd47d200de2af75232f91a23bbc3f64e20ea50
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116782920"
---
# <a name="chapter-5---io-drivers-for-azure-rtos-filex"></a>Глава 5. Драйверы ввода-вывода для ОСРВ Azure FileX

Разработчики могут использовать представленные в этой главе сведения о драйверах ввода-вывода для ОСРВ Azure FileX при написании драйверов для конкретных приложений.

## <a name="io-driver-introduction"></a>Основные сведения о драйверах ввода-вывода

FileX поддерживает несколько носителей. Структура FX_MEDIA определяет все, что необходимо для управления носителем. Эта структура содержит все сведения о носителе, включая драйвер ввода-вывода для конкретного носителя и связанные параметры для передачи информации и состояния между драйвером и FileX. В большинстве систем имеется уникальный драйвер ввода-вывода для каждого экземпляра носителя FileX.

## <a name="io-driver-entry"></a>Вход в драйвер ввода-вывода

Каждый драйвер ввода-вывода FileX имеет единственную функцию входа, которая определяется вызовом службы ***fx_media_open***. Функция входа драйвера имеет следующий формат:

```c
void my_driver_entry(FX_MEDIA *media_ptr);
```

FileX вызывает функцию входа драйвера ввода-вывода, чтобы запросить полный доступ к физическому носителю, в том числе с помощью инициализации и чтения загрузочного сектора. Запросы к драйверу выполняются последовательно (т. е. FileX ожидает завершения текущего запроса до отправки последующего).

## <a name="io-driver-requests"></a>Запросы драйвера ввода-вывода

Так как каждый драйвер ввода-вывода имеет одну функцию входа, FileX выполняет определенные запросы через блок управления носителем. В частности, для указания точного запроса драйвера используется элемент **fx_media_driver_request** из **FX_MEDIA**. Драйвер ввода-вывода сообщает об успешном или неуспешном выполнении запроса с помощью элемента **fx_media_driver_status** из **FX_MEDIA**. Если запрос драйвера был успешным, **FX_SUCCESS** помещается в это поле перед возвратом драйвера. В противном случае при обнаружении ошибки в это поле помещается FX_IO_ERROR.

### <a name="driver-initialization"></a>Инициализация драйвера

Хотя фактическая обработка инициализации драйвера зависит от приложения, обычно она состоит из инициализации структуры данных и, возможно, предварительной инициализации оборудования. Этот запрос впервые делает FileX. Он выполняется в службе fx_media_open.

Если обнаружена защита от записи на носитель, то элементу драйвера fx_media_driver_write_protect (FX_MEDIA) следует присвоить значение FX_TRUE.

Для запроса инициализации драйвера ввода-вывода используются следующие элементы FX_MEDIA:

|Элемент FX_MEDIA|Значение|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_INIT|

FileX предоставляет механизм для информирования драйвера приложения о том, что секторы больше не используются. Это особенно полезно для диспетчеров FLASH-памяти, которые должны управлять всеми логическими секторами, сопоставляемыми с FLASH-памятью.

Если требуется такое уведомление о свободных секторах, драйвер приложения устанавливает для поля *fx_media_driver_free_sector_update* в связанной структуре **FX_MEDIA** значение **FX_TRUE**. Если задать это поле, FileX вызовет драйвер ввода-вывода **_FX_DRIVER_RELEASE_SECTORS_**, уведомляющий об освобождении одного или нескольких последовательных секторов.

### <a name="boot-sector-read"></a>Чтение загрузочного сектора

Вместо использования стандартного запроса на чтение FileX создает конкретный запрос на чтение загрузочного сектора носителя. Для запроса на чтение загрузочного сектора драйвера ввода-вывода используются следующие элементы **FX_MEDIA**:

|Элемент FX_MEDIA|Значение|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_BOOT_READ|
|fx_media_driver_buffer| Адрес назначения для загрузочного сектора.|

### <a name="boot-sector-write"></a>Запись загрузочного сектора

Вместо использования стандартного запроса на запись FileX создает конкретный запрос на запись загрузочного сектора носителя. Для запроса на запись загрузочного сектора драйвера ввода-вывода используются следующие элементы **FX_MEDIA**:

|Элемент FX_MEDIA|Значение|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_BOOT_WRITE|
|fx_media_driver_buffer| Адрес источника для загрузочного сектора.|

### <a name="sector-read"></a>Чтение сектора

FileX считывает один или несколько секторов в память, отправляя запрос на чтение для драйвера ввода-вывода. Для запроса на чтение драйвера ввода-вывода используются следующие элементы **FX_MEDIA**:

|Элемент FX_MEDIA|Значение|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_READ|
|fx_media_driver_logical_sector|Логический сектор для чтения|
|fx_media_driver_sectors|Число секторов для чтения|
|fx_media_driver_buffer|Буфер назначения для чтения секторов|
|fx_media_driver_data_sector_read|Задайте значение FX_TRUE, если запрашивается сектор данных файла. В противном случае, если запрашивается системный сектор (FAT или сектор каталога), укажите значение FX_FALSE.|
|fx_media_driver_sector_type|Определяет явный тип запрашиваемого сектора, как показано ниже.<br />FX_FAT_SECTOR (2)<br />FX_DIRECTORY_SECTOR (3)<br />FX_DATA_SECTOR (4)|

### <a name="sector-write"></a>Операции записи секторов

FileX записывает один или несколько секторов на физический носитель, отправляя запрос на запись в драйвер ввода-вывода. Для запроса на запись драйвера ввода-вывода используются следующие элементы FX_MEDIA:

|Элемент FX_MEDIA| Значение|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_WRITE|
|fx_media_driver_logical_sector|Логический сектор для записи|
|fx_media_driver_sectors|Число секторов для записи|
|fx_media_driver_buffer|Исходный буфер для записи секторов|
|fx_media_driver_system_write| Задайте значение FX_TRUE, если запрашивается системный сектор (FAT или сектор каталога). В противном случае, если запрашивается сектор данных файла, укажите значение FX_FALSE.|
|fx_media_driver_sector_type|Определяет явный тип запрашиваемого сектора, как показано ниже.<br> <br>FX_FAT_SECTOR (2) <br> FX_DIRECTORY_SECTOR (3) <br>FX_DATA_SECTOR (4).|

### <a name="driver-flush"></a>Очистка драйвера

FileX записывает все секторы, находящиеся в кэше секторов драйвера, на физический носитель, отправляя запрос на очистку к драйверу ввода-вывода. Конечно, если драйвер не кэширует секторы, этот запрос не требует обработки драйвера. Для запроса на очистку драйвера ввода-вывода используются следующие элементы FX_MEDIA:

|Элемент FX_MEDIA| Значение|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_FLUSH|

### <a name="driver-abort"></a>Прекращение работы драйвера

FileX информирует драйвер о необходимости прервать все дальнейшие физические операции ввода-вывода с физическим носителем, выполнив запрос прерывания для драйвера ввода-вывода. Драйвер не должен повторно выполнять операции ввода-вывода, пока он не будет инициализирован повторно. Для запроса на прерывание драйвера ввода-вывода используются следующие элементы FX_MEDIA:

|Элемент FX_MEDIA| Значение|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_ABORT|

### <a name="release-sectors"></a>Освобождение секторов

Если в ходе инициализации ранее был выбран драйвер, FileX информирует его о том, что один или несколько последовательных секторов освобождены. Если драйвер на самом деле является диспетчером FLASH-памяти, эти сведения можно использовать, чтобы сообщить диспетчеру, что эти сектора больше не нужны. Для запроса на освобождение драйвера ввода-вывода используются следующие элементы **FX_MEDIA**:

|Элемент FX_MEDIA| Значение|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_RELEASE_SECTORS|
|fx_media_driver_logical_sector|Начало свободного сектора|
|fx_media_driver_sectors|Количество свободных секторов|

### <a name="driver-suspension"></a>Приостановка драйвера

Поскольку выполнение операций ввода-вывода на физических носителях может занять некоторое время, иногда желательно приостанавливать вызывающий поток. Предполагается, что выполнение базовой операции ввода-вывода прерывается. В этом случае приостановка потока легко реализуется с помощью семафора ThreadX. После запуска операции ввода или вывода драйвер ввода-вывода приостанавливает действие с помощью собственного внутреннего семафора ввода-вывода (создается с начальным числом, равным нулю, во время инициализации драйвера). В рамках обработки прерываний ввода-вывода драйвера устанавливается один и тот же семафор ввода-вывода, который, в свою очередь, пробуждает приостановленный поток.

### <a name="sector-translation"></a>Преобразование секторов

Так как FileX просматривает носитель в виде линейных логических секторов, запросы ввода-вывода к драйверу ввода-вывода создаются с помощью логических секторов. Драйвер отвечает за преобразование между логическими секторами и физической геометрией носителя, которая может включать в себя головки, дорожки и физические секторы. Для дисковых носителей FLASH и ОЗУ логические секторы обычно сопоставляют каталог с физическими секторами. Ниже приведены типичные формулы для сопоставления логических и физических секторов в драйвере ввода-вывода.

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

Обратите внимание, что физические секторы начинаются с единицы, а логические — с нуля.

### <a name="hidden-sectors"></a>Скрытые секторы

Скрытые секторы размещаются перед загрузочной записью на носителе. Так как они действительно выходят за рамки структуры файловой системы FAT, их необходимо включить в каждую операцию логического сектора, которую выполняет драйвер.

### <a name="media-write-protect"></a>Защита от записи на носитель

Драйвер FileX может включить защиту от записи, задавая поле fx_media_driver_write_protect в блоке управления носителем. Это приведет к ошибке, которая будет возвращена, если при попытке записи на носитель выполняются какие либо вызовы FileX.

## <a name="sample-ram-driver"></a>Пример драйвера ОЗУ

Демонстрационная система FileX поставляется с драйвером для небольшого диска ОЗУ, который определен в файле fx_ram_driver.c. Драйвер предполагает наличие дискового пространства объемом 32 КБ и создает загрузочную запись для 256 128-байтовых секторов. В этом файле представлен хороший пример реализации драйверов ввода-вывода FileX для конкретного приложения.

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
