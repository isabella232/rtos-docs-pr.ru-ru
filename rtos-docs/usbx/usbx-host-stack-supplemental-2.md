---
title: API классов узлов USBX
description: В этой главе рассматриваются все предоставляемые API классов узлов USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 28e733e37b06da7053f238e23e2b8b8046df2dd9940e50cd0321ccf15c27ec47
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116802113"
---
# <a name="chapter-2-usbx-host-classes-api"></a>Глава 2. API классов узлов USBX

В этой главе рассматриваются все предоставляемые API классов узлов USBX. Ниже подробно описаны следующие интерфейсы API для каждого класса.

- Класс Printer.
- Класс Audio.
- Класс Asix.
- Класс Pima/PTP.
- Класс Prolific.
- Класс Generic Serial.

## <a name="ux_host_class_printer_read"></a>ux_host_class_printer_read

Чтение из интерфейса принтера.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_printer_read(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Описание

Эта функция считывает данные из интерфейса принтера. Вызов блокируется и возвращается только в случае ошибки или завершения передачи. Чтение разрешено только на двунаправленных принтерах.

### <a name="parameters"></a>Параметры

- **printer** — указатель на экземпляр класса Printer.
- **data_pointer** — указатель на адрес буфера полезных данных.
- **requested_length** — длина для получения.
- **actual_length** — фактическая полученная длина.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) — функция не поддерживается, так как принтер не является двунаправленным.
- **UX_TRANSFER_TIMEOUT**: (0x5c) — превышение времени ожидания передачи, чтение не завершено.

### <a name="example"></a>Пример

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_read(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_write"></a>ux_host_class_printer_write

Запись в интерфейс принтера.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_printer_write(
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *data_pointer,  
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Описание

Эта функция записывает данные в интерфейс принтера. Вызов блокируется и возвращается только в случае ошибки или завершения передачи.

### <a name="parameters"></a>Параметры

- **printer** — указатель на экземпляр класса Printer.
- **data_pointer** — указатель на адрес буфера полезных данных.
- **requested_length** — длина для отправки.
- **actual_length** — фактическая отправленная длина.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена.
- **UX_TRANSFER_TIMEOUT**: (0x5c) — превышение времени ожидания передачи, запись не завершена.

### <a name="example"></a>Пример

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_write(printer, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_soft_reset"></a>ux_host_class_printer_soft_reset

Выполнение программного сброса принтера.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_printer_soft_reset(UX_HOST_CLASS_PRINTER *printer)
```

### <a name="description"></a>Описание

Эта функция выполняет программный сброс принтера.

### <a name="input-parameter"></a>Входной параметр

- **printer** — указатель на экземпляр класса Printer.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — сброс завершен.
- **UX_TRANSFER_TIMEOUT**: (0x5c) — превышение времени ожидания передачи, сброс не завершен.

### <a name="example"></a>Пример

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_soft_reset(printer);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_status_get"></a>ux_host_class_printer_status_get

Получение состояния принтера

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_printer_status_get( 
    UX_HOST_CLASS_PRINTER *printer,
    ULONG *printer_status)
```

### <a name="description"></a>Описание

Эта функция получает состояние принтера. Состояние принтера похоже на состояние LPT (стандарт 1284).

### <a name="parameters"></a>Параметры

- **printer** — указатель на экземпляр класса Printer.
- **printer_status** — адрес возвращаемого состояния.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) — сброс завершен.
- **UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для выполнения этой операции.
- **UX_TRANSFER_TIMEOUT**: (0x5c) — превышение времени ожидания передачи, сброс не завершен

### <a name="example"></a>Пример

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_status_get(printer, printer_status);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_printer_device_id_get"></a>ux_host_class_printer_device_id_get

Получение кода устройства принтера.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_printer_device_id_get( 
    UX_HOST_CLASS_PRINTER *printer,
    UCHAR *descriptor_buffer, 
    ULONG length)
```

### <a name="description"></a>Описание

Эта функция получает строку кода устройства принтера IEEE 1284 (включая длину первых двух байтов в формате с обратным порядком байтов).

### <a name="parameters"></a>Параметры

- **printer** — указатель на экземпляр класса Printer.
- **descriptor_buffer** — указатель на буфер для заполнения строки кода устройства IEEE 1284 (включая длину первых двух байтов в формате с обратным порядком байтов). 
- **length** — длина буфера в байтах.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) — операция успешно выполнена.
- **UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для выполнения этой операции.
- **UX_TRANSFER_TIMEOUT**: (0x5c) — превышение времени ожидания передачи, запрос не завершен.
- **UX_TRANSFER_NOT_READY**: (0x25) — устройство находилось в недопустимом состоянии (допустимые состояния: ATTACHED, ADDRESSED или CONFIGURED).
- **UX_TRANSFER_STALL**: (0x21) — передача остановлена.
- **TX_WAIT_ABORTED** (0x1A) — приостановка была прервана другим потоком, таймером или ISR.
- **TX_SEMAPHORE_ERROR** (0x0C) — недопустимый указатель на семафор со счетчиком.
- **TX_WAIT_ERROR** (0x04) — в вызове из непотокового запроса был указан параметр ожидания, отличный от TX_NO_WAIT.

### <a name="example"></a>Пример

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_printer_device_id_get(printer, descriptor_buffer, length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_audio_read"></a>ux_host_class_audio_read

Чтение из интерфейса аудио.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_audio_read(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST
    *audio_transfer_request)
```

### <a name="description"></a>Описание

Эта функция считывает данные из интерфейса аудио. Этот вызов не блокируется. Приложение должно убедиться, что для интерфейса потоковой передачи аудио выбран соответствующий альтернативный параметр.

### <a name="parameters"></a>Параметры

- **audio** — указатель на экземпляр класса Audio.
- **audio_transfer_request** — указатель на структуру передачи аудио.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) — функция не поддерживается

### <a name="example"></a>Пример

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

## <a name="ux_host_class_audio_write"></a>ux_host_class_audio_write

Запись в интерфейс аудио.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_audio_write(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_TRANSFER_REQUEST *audio_transfer_request)
```

### <a name="description"></a>Описание

Эта функция записывает данные в интерфейс аудио. Этот вызов не блокируется. Приложение должно убедиться, что для интерфейса потоковой передачи аудио выбран соответствующий альтернативный параметр.

### <a name="parameters"></a>Параметры

- **audio** — указатель на экземпляр класса Audio
- **audio_transfer_request** — указатель на структуру передачи аудио

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) — функция не поддерживается.
- **ux_host_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) — недопустимый интерфейс.

### <a name="example"></a>Пример

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

## <a name="ux_host_class_audio_control_get"></a>ux_host_class_audio_control_get

Получение конкретного элемента управления из интерфейса управления звуком.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_audio_control_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

### <a name="description"></a>Описание

Эта функция считывает конкретный элемент управления из интерфейса управления звуком.

### <a name="parameters"></a>Параметры

- **audio** — указатель на экземпляр класса Audio
- **audio_control** — указатель на структуру управления аудио.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) — функция не поддерживается
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) — недопустимый интерфейс

### <a name="example"></a>Пример

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

## <a name="ux_host_class_audio_control_value_set"></a>ux_host_class_audio_control_value_set

Указание конкретного элемента управления для интерфейса управления аудио.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_audio_control_value_set(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_CONTROL *audio_control)
```

**Описание **

Эта функция задает конкретный элемент управления для интерфейса управления аудио.

### <a name="parameters"></a>Параметры

- **audio** — указатель на экземпляр класса Audio
- **audio_control** — указатель на структуру управления аудио.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) — функция не поддерживается
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) — недопустимый интерфейс

### <a name="example"></a>Пример

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

## <a name="ux_host_class_audio_streaming_sampling_set"></a>ux_host_class_audio_streaming_sampling_set

Указание альтернативного параметра для интерфейса потоковой передачи аудио.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_audio_streaming_sampling_set
    (UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING *audio_sampling)
```

### <a name="description"></a>Описание

Эта функция задает подходящий альтернативный параметр для интерфейса потоковой передачи аудио в соответствии с определенной структурой выборки.

### <a name="parameters"></a>Параметры

- **audio** — указатель на экземпляр класса Audio.
- **audio_sampling** — указатель на структуру выборки аудио.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) — функция не поддерживается
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) — недопустимый интерфейс
- **UX_NO_ALTERNATE_SETTING**: (0x5e) — отсутствует альтернативный параметр для значений выборки.

### <a name="example"></a>Пример

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

## <a name="ux_host_class_audio_streaming_sampling_get"></a>ux_host_class_audio_streaming_sampling_get

Получение возможных параметров выборки для интерфейса потоковой передачи аудио.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_audio_streaming_sampling_get(
    UX_HOST_CLASS_AUDIO *audio,
    UX_HOST_CLASS_AUDIO_SAMPLING_CHARACTERISTICS *audio_sampling)
```

### <a name="description"></a>Описание

Эта функция получает по очереди все возможные параметры выборки, доступные в каждом из альтернативных параметров интерфейса потоковой передачи звука. При первом использовании функции все поля в указателе структуры вызовов должны быть сброшены. Функция будет возвращать конкретный набор значений потоковой передачи при возврате, если не достигнут конец альтернативных параметров. При повторном использовании этой функции для поиска следующих значений выборки будут использоваться ее предыдущие значения.

### <a name="parameters"></a>Параметры

- **audio** — указатель на экземпляр класса Audio.
- **audio_sampling** — указатель на структуру выборки аудио.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) — функция не поддерживается
- **UX_HOST_CLASS_AUDIO_WRONG_INTERFACE**: (0x81) — недопустимый интерфейс
- **UX_NO_ALTERNATE_SETTING**: (0x5e) — отсутствует альтернативный параметр для значений выборки.

### <a name="example"></a>Пример

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

## <a name="ux_host_class_asix_read"></a>ux_host_class_asix_read

Чтение из интерфейса asix.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_asix_read(
    UX_HOST_CLASS_ASIX *asix,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Описание

Эта функция считывает данные из интерфейса asix. Вызов блокируется и возвращается только в случае ошибки или завершения передачи.

### <a name="parameters"></a>Параметры

- **asix** — указатель на экземпляр класса Asix.
- **data_pointer** — указатель на адрес буфера полезных данных.
- **requested_length** — длина для получения.
- **actual_length** — фактическая полученная длина.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена.
- **UX_TRANSFER_TIMEOUT**: (0x5c) — превышение времени ожидания передачи, чтение не завершено.

### <a name="example"></a>Пример

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_read(asix, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_asix_write"></a>ux_host_class_asix_write

Запись в интерфейс asix.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_asix_write(
    VOID *asix_class,
    NX_PACKET *packet)
```

### <a name="description"></a>Описание

Эта функция записывает данные в интерфейс asix. Этот вызов не блокируется.

### <a name="parameters"></a>Параметры

- **asix** — указатель на экземпляр класса Asix.
- **packet** — пакет данных Netx.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена.
- **UX_ERROR**: (0xFF) — невозможно запросить передачу.

### <a name="example"></a>Пример

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_asix_write(asix, packet);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_pima_session_open"></a>ux_host_class_pima_session_open

Открытие сеанса между инициатором и отвечающим устройством.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_pima_session_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a>Описание

Эта функция открывает сеанс между инициатором PIMA и отвечающим устройством PIMA. После успешного открытия сеанса можно выполнить большинство команд PIMA.

### <a name="parameters"></a>Параметры

- **pima** — указатель на экземпляр класса Pima.
- **pima_session** — указатель на сеанс PIMA<

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0X00) — сеанс успешно открыт.
- **UX_HOST_CLASS_PIMA_RC_SESSION_ALREADY_OPENED**: (0x201E) — сеанс уже открыт.

### <a name="example"></a>Пример

```C
/* Open a pima session. */

status = ux_host_class_pima_session_open(pima, pima_session);

if (status != UX_SUCCESS)
    return(UX_PICTBRIDGE_ERROR_SESSION_NOT_OPEN);
```

## <a name="ux_host_class_pima_session_close"></a>ux_host_class_pima_session_close

Закрытие сеанса между инициатором и отвечающим устройством.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_pima_session_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session)
```

### <a name="description"></a>Описание

Эта функция закрывает сеанс, который ранее открывался между инициатором PIMA и отвечающим устройством PIMA. После закрытия сеанса большинство команд PIMA больше не будут выполняться.

### <a name="parameters"></a>Параметры

- **pima** — указатель на экземпляр класса Pima.
- **pima_session** — указатель на сеанс PIMA.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — сеанс закрыт.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт.

### <a name="example"></a>Пример

```C
/* Close the pima session. */

status = ux_host_class_pima_session_close(pima, pima_session);
```

## <a name="ux_host_class_pima_storage_ids_get"></a>ux_host_class_pima_storage_ids_get

Получение массива идентификаторов хранилища из отвечающего устройства.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_pima_storage_ids_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG *storage_ids_array,
    ULONG storage_id_length)
```

### <a name="description"></a>Описание

Эта функция получает массив идентификаторов хранилища из отвечающего устройства.

### <a name="parameters"></a>Параметры

- **pima** — указатель на экземпляр класса Pima.
- **pima_session** — указатель на сеанс PIMA
- **storage_ids_array** — массив, в который будут возвращены идентификаторы хранилища.
- **storage_id_length** — длина массива хранения.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — массив идентификаторов хранилища заполнен.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт
- **UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.

### <a name="example"></a>Пример

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

## <a name="ux_host_class_pima_storage_info_get"></a>ux_host_class_pima_storage_info_get

Получение сведений о хранилище из отвечающего устройства.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_pima_storage_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    UX_HOST_CLASS_PIMA_STORAGE *storage)
```

### <a name="description"></a>Описание

Эта функция получает сведения о хранилище для контейнера хранилища со значением *storage_id*.

### <a name="parameters"></a>Параметры

- **pima** — указатель на экземпляр класса Pima.
- **pima_session** — указатель на сеанс PIMA
- **storage_id** — идентификатор контейнера хранилища.
- **storage** — указатель на контейнер сведений о хранилище.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — сведения о хранилище получены.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт
- **UX_MEMORY_INSUFFICIENT** (0x12) — недостаточно памяти для создания команды PIMA.

### <a name="example"></a>Пример

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

## <a name="ux_host_class_pima_num_objects_get"></a>ux_host_class_pima_num_objects_get

Получение количества объектов в контейнере хранилища из отвечающего устройства.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_pima_num_objects_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG object_format_code)
```

### <a name="description"></a>Описание

Эта функция получает количество объектов, хранящихся в определенном контейнере хранилища со значением storage_id, соответствующим определенному коду формата. Количество объектов возвращается в поле: ux_host_class_pima_session_nb_objects структуры pima_session.

### <a name="parameters"></a>Параметры

- **pima** — указатель на экземпляр класса Pima.
- **pima_session** — указатель на сеанс PIMA
- **storage_id** — идентификатор контейнера хранилища.
- **object_format_code** — фильтр кода формата объектов.

Эти коды формата объекта могут иметь одно из приведенных ниже значений.

| Код формата объекта               | Описание   |     Код USBX                          |
|----------------------------------|---------------|------------------------------------------|
| 0x3000                           | Не определено. Неопределенный объект, не являющийся изображением | UX_HOST_CLASS_PIMA_OFC_UNDEFINED   |
| 0x3001                           | Связь. Связь (например, папка) | UX_HOST_CLASS_PIMA_OFC_ASSOCIATION |
| 0x3002                           | Скрипт. Скрипт конкретной модели устройства | UX_HOST_CLASS_PIMA_OFC_SCRIPT      |
| 0x3003                           | Исполняемый файл. Двоичный исполняемый файл конкретной модели устройства | UX_HOST_CLASS_PIMA_OFC_EXECUTABLE  |
| 0x3004                           | Текст. Текстовый файл  |   UX_HOST_CLASS_PIMA_OFC_TEXT        |
| 0x3005                           | HTML. Файл языка гипертекстовой разметки (текст) | UX_HOST_CLASS_PIMA_OFC_HTML        |
| 0x3006                           | DPOF. Файл цифрового формата управления печатью (текст) | UX_HOST_CLASS_PIMA_OFC_DPOF        |
| 0x3007                           | AIFF. Аудиоклип  |  UX_HOST_CLASS_PIMA_OFC_AIFF        |
| 0x3008                           | WAV. Аудиоклип   |  UX_HOST_CLASS_PIMA_OFC_WAV         |
| 0x3009                           | MP3. Аудиоклип   |  UX_HOST_CLASS_PIMA_OFC_MP3         |
| 0x300A                           | AVI. Видеоролик   |  UX_HOST_CLASS_PIMA_OFC_AVI         |
| 0x300B                           | MPEG. Видеоролик  |  UX_HOST_CLASS_PIMA_OFC_MPEG        |
| 0x300C                           | ASF. Формат Microsoft Advanced Streaming Format (видео) | UX_HOST_CLASS_PIMA_OFC_ASF         |
| 0x3800                           | Не определено. Неизвестный объект изображения | UX_HOST_CLASS_PIMA_OFC_QT          |
| 0x3801                           | EXIF/JPEG. Формат Exchangeable File Format, стандарт JEIDA | UX_HOST_CLASS_PIMA_OFC_EXIF_JPEG   |
| 0x3802                           | TIFF/EP. Формат файла Tag Image File Format для электронной фотографии | UX_HOST_CLASS_PIMA_OFC_TIFF_EP     |
| 0x3803                           | FlashPix. Формат Structured Storage Image Format | UX_HOST_CLASS_PIMA_OFC_FLASHPIX    |
| 0x3804                           | BMP. Файл в формате Microsoft Windows Bitmap | UX_HOST_CLASS_PIMA_OFC_BMP         |
| 0x3805                           | CIFF. Формат файла Canon Camera Image File Format | UX_HOST_CLASS_PIMA_OFC_CIFF        |
| 0x3806                           | Не определено. Зарезервировано |  |
| 0x3807                           | GIF. Формат Graphics Interchange Format | UX_HOST_CLASS_PIMA_OFC_GIF         |
| 0x3808                           | JFIF. Формат обмена файлами JPEG | UX_HOST_CLASS_PIMA_OFC_JFIF        |
| 0x3809                           | PCD. Формат PhotoCD Image Pac | UX_HOST_CLASS_PIMA_OFC_PCD         |
| 0x380A                           | PICT. Формат Quickdraw Image Format | UX_HOST_CLASS_PIMA_OFC_PICT        |
| 0x380B                           | PNG. Формат Portable Network Graphics | UX_HOST_CLASS_PIMA_OFC_PNG         |
| 0x380C                           | Не определено. Зарезервировано |   |
| 0x380D                           | TIFF. Формат Tag Image File Format | UX_HOST_CLASS_PIMA_OFC_TIFF        |
| 0x380E                           | TIFF/IT. Формат Tag Image File Format for Information Technology (графика) | UX_HOST_CLASS_PIMA_OFC_TIFF_IT     |
| 0x380F                           | JP2. Базовый формат файла JPEG2000 | UX_HOST_CLASS_PIMA_OFC_JP2         |
| 0x3810                           | JPX. Расширенный формат файла JPEG2000 | UX_HOST_CLASS_PIMA_OFC_JPX         |
| Все остальные коды с MSN 0011 | Не определено (любые). Зарезервировано для будущего использования |                                    |
| Все остальные коды с MSN 1011 | Любой определенный поставщиком. Определенный поставщиком тип: изображение |                                    |

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт
- **UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.

### <a name="example"></a>Пример

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

## <a name="ux_host_class_pima_object_handles_get"></a>ux_host_class_pima_object_handles_get

Получение дескрипторов объектов из отвечающего устройства.

### <a name="prototype"></a>Прототип

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

### <a name="description"></a>Описание

Возвращает массив дескрипторов объектов, имеющихся в контейнере хранилища, указанном параметром storage_id. Если требуется агрегированный список по всем хранилищам, это значение должно быть 0xFFFFFFFF.

### <a name="parameters"></a>Параметры

- **pima** — указатель на экземпляр класса Pima.
- **pima_session** — указатель на сеанс PIMA
- **object_handes_array** — массив, в который возвращаются дескрипторы.
- **object_handles_length** — длина массива.
- **storage_id** — идентификатор контейнера хранилища.
- **object_format_code** — код формата для объекта (см. таблицу для функции ux_host_class_pima_num_objects_get).
- **object_handle_association** — необязательное значение связи объекта.

Связь дескриптора объекта может быть одним из значений из следующей таблицы:

| AssociationCode                        | AssociationType      | Интерпретация       |
|----------------------------------------|----------------------|----------------------|
| 0x0000                                 | Не определено            | Не определено            |
| 0x0001                                 | GenericFolder        | Не используется               |
| 0x0002                                 | Album                | Зарезервировано             |
| 0x0003                                 | TimeSequence         | DefaultPlaybackDelta |
| 0x0004                                 | HorizontalPanoramic  | Не используется               |
| 0x0005                                 | VerticalPanoramic    | Не используется               |
| 0x0006                                 | 2DPanoramic          | ImagesPerRow         |
| 0x0007                                 | AncillaryData        | Не определено.            |
| Все остальные значения с битом 15 равным 0  | Зарезервировано             | Не определено.            |
| Все остальные значения с битом 15 равным 1        | Определяется поставщиком       | Определяется поставщиком       |

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт
- **UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.

### <a name="example"></a>Пример

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

## <a name="ux_host_class_pima_object_info_get"></a>ux_host_class_pima_object_info_get

Получение сведений об объекте из отвечающего устройства.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_pima_object_info_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Описание

Эта функция получает сведения об объекте для дескриптора объекта.

### <a name="parameters"></a>Параметры

- **pima** — указатель на экземпляр класса Pima.
- **pima_session** — указатель на сеанс PIMA
- **object_handle** — дескриптор объекта
- **object** — указатель на контейнер сведений об объекте

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт
- **UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.

### <a name="example"></a>Пример

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

## <a name="ux_host_class_pima_object_info_send"></a>ux_host_class_pima_object_info_send

Отправка сведений об объекте в отвечающее устройство.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_pima_object_info_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG storage_id,
    ULONG parent_object_id,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Описание

Эта функция отправляет сведения о хранилище для контейнера хранилища со значением storage_id. Инициатор должен использовать эту команду перед отправкой объекта в отвечающее устройство.

### <a name="parameters"></a>Параметры

- **pima** — указатель на экземпляр класса Pima.
- **pima_session** — указатель на сеанс PIMA.
- **storage_id** — идентификатор целевого хранилища.
- **parent_object_id** — родительский ObjectHandle в отвечающем устройстве, в котором следует разместить объект.
- **object** — указатель на контейнер сведений об объекте.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт
- **UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.

### <a name="example"></a>Пример

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

## <a name="ux_host_class_pima_object_open"></a>ux_host_class_pima_object_open

Открытие объекта, хранящегося в отвечающем устройстве.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_pima_object_open(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Описание

Эта функция открывает объект на стороне отвечающего устройства перед чтением или записью.

### <a name="parameters"></a>Параметры

- **pima** — указатель на экземпляр класса Pima.
- **pima_session** — указатель на сеанс PIMA.
- **object_handle** — дескриптор объекта.
- **object** — указатель на контейнер сведений об объекте.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт
- **UX_HOST_CLASS_PIMA_RC_OBJECT_ALREADY_OPENED**: (0x2021) — объект уже открыт.
- **UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.

### <a name="example"></a>Пример

```C
/* Open the object. */

status = ux_host_class_pima_object_open(pima, pima_session,
    object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_get"></a>ux_host_class_pima_object_get

Получение объекта, хранящегося в отвечающем устройстве.

### <a name="prototype"></a>Прототип

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

### <a name="description"></a>Описание

Эта функция получает объект на стороне отвечающего устройства.

### <a name="parameters"></a>Параметры

- **pima** — указатель на экземпляр класса Pima.
- **pima_session** — указатель на сеанс PIMA
- **object_handle** — дескриптор объекта
- **object** — указатель на контейнер сведений об объекте
- **object_buffer** — адрес данных объекта.
- **object_buffer_length** — запрошенная длина объекта.
- **object_actual_length** — длина возвращаемого объекта.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — объект передан.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) — объект не открыт.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) — отказано в доступе к объекту
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) — передача не завершена
- **UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.
- **UX_TRANSFER_ERROR**: (0x23) — ошибка передачи при чтении объекта

### <a name="example"></a>Пример

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

## <a name="ux_host_class_pima_object_send"></a>ux_host_class_pima_object_send

Отправка объекта, хранящегося в отвечающем устройстве.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_pima_object_send(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *object_buffer, ULONG object_buffer_length)
```

### <a name="description"></a>Описание

Эта функция отправляет объект в отвечающее устройство.

### <a name="parameters"></a>Параметры

- **pima** — указатель на экземпляр класса Pima.
- **pima_session** — указатель на сеанс PIMA
- **object_handle** — дескриптор объекта
- **object** — указатель на контейнер сведений об объекте
- **object_buffer** — адрес данных объекта.
- **object_buffer_length** — запрошенная длина объекта.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) — объект не открыт.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) — отказано в доступе к объекту
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) — передача не завершена
- **UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.
- **UX_TRANSFER_ERROR**: (0x23) — ошибка передачи при записи объекта.

### <a name="example"></a>Пример

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

## <a name="ux_host_class_pima_thumb_get"></a>ux_host_class_pima_thumb_get

Получение объекта Thumb, хранящегося в отвечающем устройстве.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_pima_thumb_get(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle,
    UX_HOST_CLASS_PIMA_OBJECT *object,
    UCHAR *thumb_buffer, ULONG thumb_buffer_length,
    ULONG *thumb_actual_length)
```

### <a name="description"></a>Описание

Эта функция получает объект Thumb на стороне отвечающего устройства.

### <a name="parameters"></a>Параметры

- **pima** — указатель на экземпляр класса Pima.
- **pima_session** — указатель на сеанс PIMA.
- **object_handle** — дескриптор объекта.
- **object** — указатель на контейнер сведений об объекте.
- **thumb_buffer** — адрес данных объекта Thumb.
- **thumb_buffer_length** — запрошенная длина объекта Thumb.
- **thumb_actual_length** — длина возвращаемого объекта Thumb.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) — объект не открыт.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0x200f) — отказано в доступе к объекту.
- **UX_HOST_CLASS_PIMA_RC_INCOMPLETE_TRANSFER**: (0x2007) — передача не завершена.
- **UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.
- **UX_TRANSFER_ERROR**: (0x23) — ошибка передачи при чтении объекта.

### <a name="example"></a>Пример

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

## <a name="ux_host_class_pima_object_delete"></a>ux_host_class_pima_object_delete

Удаление объекта, хранящегося в отвечающем устройстве.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_pima_object_delete(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle)
```

### <a name="description"></a>Описание

Эта функция удаляет объект на стороне отвечающего устройства.

### <a name="parameters"></a>Параметры

- **pima** — указатель на экземпляр класса Pima.
- **pima_session** — указатель на сеанс PIMA
- **object_handle** — дескриптор объекта

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — объект удален.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт.
- **UX_HOST_CLASS_PIMA_RC_ACCESS_DENIED**: (0X200f) — не удается удалить объект.
- **UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.

### <a name="example"></a>Пример

```C
/* Delete the object. */
status = ux_host_class_pima_object_delete(pima, pima_session, object_handle, pima_object);

/* Check status. */
if (status != UX_SUCCESS)
    return(status);
```

## <a name="ux_host_class_pima_object_close"></a>ux_host_class_pima_object_close

Закрытие объекта, хранящегося в отвечающем устройстве.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_pima_object_close(
    UX_HOST_CLASS_PIMA *pima,
    UX_HOST_CLASS_PIMA_SESSION *pima_session,
    ULONG object_handle, UX_HOST_CLASS_PIMA_OBJECT *object)
```

### <a name="description"></a>Описание

Эта функция закрывает объект на стороне отвечающего устройства.

### <a name="parameters"></a>Параметры

- **pima** — указатель на экземпляр класса Pima.
- **pima_session** — указатель на сеанс PIMA.
- **object_handle** — дескриптор объекта.
- **object** — указатель на объект.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — объект закрыт.
- **UX_HOST_CLASS_PIMA_RC_SESSION_NOT_OPEN**: (0x2003) — сеанс не открыт.
- **UX_HOST_CLASS_PIMA_RC_OBJECT_NOT_OPENED**: (0x2023) — объект не открыт.
- **UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти для создания команды PIMA.

### <a name="example"></a>Пример

```C
/* Close the object. */
status = ux_host_class_pima_object_close(pima, pima_session, object_handle, object);
```

## <a name="ux_host_class_gser_read"></a>ux_host_class_gser_read

Чтение из универсального последовательного интерфейса.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_gser_read(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Описание

Эта функция считывает данные из универсального последовательного интерфейса. Вызов блокируется и возвращается только в случае ошибки или завершения передачи.

### <a name="parameters"></a>Параметры

- **gser** — указатель на экземпляр класса gser.
- **interface_index** — индекс интерфейса для считывания.
- **data_pointer** — указатель на адрес буфера полезных данных.
- **requested_length** — длина для получения.
- **actual_length** — фактическая полученная длина.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена.
- **UX_TRANSFER_TIMEOUT**: (0x5c) — превышение времени ожидания передачи, чтение не завершено.

### <a name="example"></a>Пример

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_gser_read(cdc_acm, interface_index,data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_write"></a>ux_host_class_gser_write

Запись в универсальный последовательный интерфейс.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_gser_write(
    UX_HOST_CLASS_GSER *gser,
    ULONG interface_index,
    UCHAR *data_pointer,
    ULONG requested_length,
    ULONG *actual_length)
```

### <a name="description"></a>Описание

Эта функция выполняет запись в универсальный последовательный интерфейс. Вызов блокируется и возвращается только в случае ошибки или завершения передачи.

### <a name="parameters"></a>Параметры

- **gser** — указатель на экземпляр класса gser.
- **interface_index** — интерфейс для записи.
- **data_pointer** — указатель на адрес буфера полезных данных.
- **requested_length** — длина для отправки.
- **actual_length** — фактическая отправленная длина.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена.
- **UX_TRANSFER_TIMEOUT**: (0x5c) — превышение времени ожидания передачи, запись не завершена.

### <a name="example"></a>Пример

```C
UINT status;

/* The following example illustrates this service. */
status = ux_host_class_cdc_acm_write(gser, data_pointer, requested_length, &actual_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_ioctl"></a>ux_host_class_gser_ioctl

Выполнение функции IOCTL для универсального последовательного интерфейса.

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_gser_ioctl(
    UX_HOST_CLASS_GSER *gser,
    ULONG ioctl_function,
    VOID *parameter)
```

### <a name="description"></a>Описание

Эта функция выполняет конкретную функцию IOCTL в интерфейсе gser. Вызов блокируется и возвращается только в случае ошибки или после завершения выполнения команды.

### <a name="parameters"></a>Параметры

- **gser** — указатель на экземпляр класса gser.
- **ioctl_function** — функция IOCTL для выполнения. Допустимые функции IOCTL см. в приведенной ниже таблице.
- **parameter** — указатель на параметр, относящийся к IOCTL

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS**: (0x00) — передача данных завершена.
- **UX_MEMORY_INSUFFICIENT**: (0x12) — недостаточно памяти.
- **UX_HOST_CLASS_UNKNOWN**: (0X59) — неправильный экземпляр класса.
- **UX_FUNCTION_NOT_SUPPORTED**: (0x54) — неизвестная функция IOCTL.

### <a name="ioctl-functions"></a>Функции IOCTL

- UX_HOST_CLASS_GSER_IOCTL_SET_LINE_CODING
- UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING
- UX_HOST_CLASS_GSER_IOCTL_SET_LINE_STATE
- UX_HOST_CLASS_GSER_IOCTL_SEND_BREAK
- UX_HOST_CLASS_GSER_IOCTL_ABORT_IN_PIPE
- UX_HOST_CLASS_GSER_IOCTL_ABORT_OUT_PIPE
- UX_HOST_CLASS_GSER_IOCTL_NOTIFICATION_CALLBACK
- UX_HOST_CLASS_GSER_IOCTL_GET_DEVICE_STATUS

### <a name="example"></a>Пример

```C
UINT status;

/* The following example illustrates this service. */

status = ux_host_class_gser_ioctl(gser,
    UX_HOST_CLASS_GSER_IOCTL_GET_LINE_CODING,
    (VOID *)&line_coding);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_class_gser_reception_start"></a>ux_host_class_gser_reception_start

Начало приема в универсальном последовательном интерфейсе

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_gser_reception_start(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a>Описание

Эта функция запускает прием в универсальном последовательном интерфейсе класса. Эта функция разрешает прием без блокировки. После получения буфера в приложении выполняется обратный вызов.

### <a name="parameters"></a>Параметры

- **gser** — указатель на экземпляр класса gser.
- **gser_reception** — структура, содержащая параметры приема.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) — передача данных завершена.
- **UX_HOST_CLASS_UNKNOWN** (0X59) — неправильный экземпляр класса.
- **UX_ERROR** (0x01) — ошибка.

### <a name="example"></a>Пример

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

## <a name="ux_host_class_gser_reception_stop"></a>ux_host_class_gser_reception_stop

Остановка приема на универсальном последовательном интерфейсе

### <a name="prototype"></a>Прототип

```C
UINT ux_host_class_gser_reception_stop(
    UX_HOST_CLASS_GSER *gser,
    UX_HOST_CLASS_GSER_RECEPTION *gser_reception)
```

### <a name="description"></a>Описание

Эта функция останавливает прием на интерфейсе универсального последовательного класса.

### <a name="parameters"></a>Параметры

- **gser** — указатель на экземпляр класса gser.
- **gser_reception** — структура, содержащая параметры приема.

### <a name="return-value"></a>Возвращаемое значение

- **UX_SUCCESS** (0x00) — передача данных завершена.
- **UX_HOST_CLASS_UNKNOWN** (0X59) — неправильный экземпляр класса.
- **UX_ERROR** (0x01) — ошибка.

### <a name="example"></a>Пример

```C
/* Stops the reception for gser. */
ux_host_class_gser_reception_stop(gser, &gser_reception);
```
