---
title: Глава 3. Описание служб ОСРВ Azure NetX Duo TFTP
description: Эта глава содержит описание всех служб NetX Duo TFTP, перечисленных ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: db7b7469bda02597db6428ecbf080b37a095413411eef2abefb1c4804d7bb1d3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799069"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-tftp-services"></a>Глава 3. Описание служб ОСРВ Azure NetX Duo TFTP

Эта глава содержит описание всех служб NetX Duo TFTP, перечисленных ниже в алфавитном порядке. Если не указано иное, все службы поддерживают взаимодействие по протоколам IPv6 и IPv4.

В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

- **nxd_tftp_client_file_open**: *открытие файла клиента TFTP*.

- **nxd_tftp_client_create**: *создание экземпляра клиента TFTP*.

- **nxd_tftp_client_delete**: *удаление экземпляра клиента TFTP*.

- **nxd_tftp_client_error_info_get**: *получение сведений об ошибке клиента*.

- **nxd_tftp_client_file_close**: *закрытие файла клиента*.

- **nxd_tftp_client_file_open**: *открытие файла клиента*.

- **nxd_tftp_client_file_read**: *чтение блока из файла клиента*.

- **nxd_tftp_client_file_write**: *запись блока в файл клиента*.

- **nxd_tftp_client_packet_allocate**: *выделение пакета для записи в файл клиента*.

- **nxd_tftp_client_set_interface**: *настройка физического интерфейса для запросов TFTP*.

- **nxd_tftp_server_create**: *создание сервера TFTP*.

- **nxd_tftp_server_delete**: *удаление сервера TFTP*.

- **nxd_tftp_server_start**: *запуск сервера TFTP*.

- **nxd_tftp_server_stop**: *остановка сервера TFTP*.

> [!NOTE] 
> Эквиваленты всех перечисленных выше служб для протокола IPv4 доступны в клиенте и сервере NetX Duo TFTP, например *nx_tftp_server_create* и *nx_tftp_client_file_open*. На следующих страницах приведено только описание интерфейсов API для Duo (например, службы, начинающиеся с *nxd_* ). Если указаны входные данные NXD_ADDRESS\*, это означает эквивалентный вызов интерфейсов API IPv4 для входных данных типа ULONG. В противном случае разницы в использовании API нет.

## <a name="nxd_tftp_client_create"></a>nxd_tftp_client_create

Создание экземпляра клиента TFTP.

### <a name="prototype"></a>Прототип

```C
UINT nxd_tftp_client_create(NX_TFTP_CLIENT *tftp_client_ptr,  
     CHAR *tftp_client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Описание

Эта служба создает экземпляр клиента TFTP для созданного ранее экземпляра IP.

> [!IMPORTANT]
> Приложение должно гарантировать, что указанный экземпляр IP и пул пакетов уже созданы. Кроме того, перед вызовом этой службы необходимо включить протокол UDP для экземпляра IP.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом TFTP.

- **tftp_client_name**: имя этого экземпляра клиента TFTP.

- **ip_ptr**: указатель на созданный ранее экземпляр IP.

- **pool_ptr**: указатель на пул пакетов экземпляра клиента TFTP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): экземпляр TFTP успешно создан.

- **NX_TFTP_INVALID_IP_VERSION** (0X0C): недопустимая или неподдерживаемая версия протокола IP.

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08): получен недопустимый IP-адрес сервера.

- **NX_TFTP_NO_ACK_RECEIVED** (0x09): сообщение ACK от сервера не получено.

- NX_PTR_ERROR (0x16): недопустимый указатель на IP-адрес, пул или экземпляр TFTP.

- NX_INVALID_PARAMETERS (0x4D): недопустимые входные данные, отличные от указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="example"></a>Например, .

```C
/* Create a TFTP Client instance. */
status =  nxd_tftp_client_create(&my_tftp_client, “My TFTP Client”, 
                                                    &my_ip, &pool_ptr);

/* If status is NX_SUCCESS a TFTP Client instance was successfully
   created. */
```

## <a name="nxd_tftp_client_delete"></a>nxd_tftp_client_delete

Удаление экземпляра клиента TFTP.

### <a name="prototype"></a>Прототип

```C
UINT nxd_tftp_client_delete(NX_TFTP_CLIENT *tftp_client_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет созданный ранее экземпляр клиента TFTP.

### <a name="input-parameters"></a>Входные параметры

- **tftp_client_ptr**: указатель на созданный ранее экземпляр клиента TFTP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): клиент TFTP успешно удален.

- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Delete a TFTP Client instance. */
status =  nxd_tftp_client_delete(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP Client instance was successfully
   deleted. */
```

## <a name="nxd_tftp_client_error_info_get"></a>nxd_tftp_client_error_info_get

Получение сведений об ошибке клиента.

### <a name="prototype"></a>Прототип

```C
UINT nxd_tftp_client_error_info_get(NX_TFTP_CLIENT *tftp_client_ptr,
                        UINT *error_code, CHAR **error_string);
```

### <a name="description"></a>Описание

Эта служба возвращает последний полученный код ошибки и задает указатель на внутреннюю строку ошибки клиента. В описании ошибки пользователь может просмотреть последнюю ошибку, отправленную сервером. Строка ошибки со значением NULL указывает на отсутствие ошибки.

### <a name="input-parameters"></a>Входные параметры

- **tftp_client_ptr**: указатель на созданный ранее экземпляр клиента TFTP.

- **error_code**: указатель на область назначения для кода ошибки.

- **error_string**: указатель на место назначения для строки ошибки.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сведения об ошибке TFTP успешно получены.  

- NX_PTR_ERROR (0x16): недопустимый указатель на клиент TFTP.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Get error information for client. */
status =  nxd_tftp_client_error_info_get(&my_tftp_client, &error_code,
                    &error_string_ptr);

/* If status is NX_SUCCESS the error code and error string are available. */
```

## <a name="nxd_tftp_client_file_close"></a>nxd_tftp_client_file_close

Закрытие файла клиента.

### <a name="prototype"></a>Прототип

```C
UINT nxd_tftp_client_file_close(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT ip_type);
```

### <a name="description"></a>Описание

Эта служба закрывает файл, открытый ранее этим экземпляром клиента TFTP. Экземпляр клиента TFTP может одновременно открыть только один файл.

### <a name="input-parameters"></a>Входные параметры

- **tftp_client_ptr**: указатель на созданный ранее экземпляр клиента TFTP.

- **ip_type**: позволяет указать, какой протокол IP использовать. Допустимые значения: IPv4 (4) или IPv6 (6).

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): файл TFTP успешно закрыт.

- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

- NX_INVALID_PARAMETERS (0x4D): недопустимые входные данные, отличные от указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Close the previously opened file associated with “my_client”. */
status =  nxd_tftp_client_file_close(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP file is closed. */
```

## <a name="nx_tftp_client_file_open"></a>nx_tftp_client_file_open

Открытие файла клиента TFTP.

### <a name="prototype"></a>Прототип

```C
UINT nx_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr, 
            CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
            open_type, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба пытается открыть указанный файл на сервере TFTP по заданному IP-адресу. Файл будет открыт для чтения или записи. 

> [!NOTE] 
> Это ограничение относится только к пакетам IPv4 и предназначено для поддержки приложений NetX TFTP. Разработчикам рекомендуется перенести свои приложения для использование эквивалентной службы Duo, *nxd_tftp_client_file_open*.

### <a name="input-parameters"></a>Входные параметры

- **tftp_client_ptr**: указатель на блок управления TFTP.

- **file_name**: имя файла ASCII, оканчивающееся нулевым символом, и соответствующие сведения о пути.

- **server_ip_address**: адрес сервера TFTP.

- **open_type**: тип запроса на открытие:

  **NX_TFTP_OPEN_FOR_READ** (0x01)

  **NX_TFTP_OPEN_FOR_WRITE** (0x02)

- **wait_option**: определяет, как долго служба будет ожидать открытия файла клиента TFTP. Параметры ожидания определяются следующим образом:

  **Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF). 
  
  Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер TFTP не ответит на запрос. 
  
  Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа сервера TFTP.

- **ip_type**: позволяет указать, какой протокол IP использовать. Допустимые значения: IPv4 (4) или IPv6 (6).

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): файл клиента успешно открыт.

- **NX_TFTP_NOT_CLOSED** (0xC3): клиент уже открыл файл.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08): получен недопустимый адрес сервера.

- **NX_TFTP_NO_ACK_RECEIVED** (0x09): не получено сообщение ACK от сервера.

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08): получен недопустимый IP-адрес сервера.

- **NX_TFTP_CODE_ERROR** (0X05): получен код ошибки.

- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

- NX_IP_ADDRESS_ERROR (0x21): недопустимый IP-адрес сервера.

- NX_OPTION_ERROR (0x0A): недопустимый тип операции открытия.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
        & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_open"></a>nxd_tftp_client_file_open

Открытие файла клиента TFTP.

### <a name="prototype"></a>Прототип

```C
UINT nxd_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr,
        CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
        open_type, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a>Описание

Эта служба пытается открыть указанный файл на сервере TFTP по заданному IPv6-адресу. Файл будет открыт для чтения или записи.

### <a name="input-parameters"></a>Входные параметры

- **tftp_client_ptr**: указатель на блок управления TFTP.

- **file_name**: имя файла ASCII, оканчивающееся нулевым символом, и соответствующие сведения о пути.

- **server_ip_address**: адрес сервера TFTP.

- **open_type**: тип запроса на открытие:

  **NX_TFTP_OPEN_FOR_READ** (0x01)

  **NX_TFTP_OPEN_FOR_WRITE** (0x02)

- **wait_option**: определяет, как долго служба будет ожидать открытия файла клиента TFTP. Параметры ожидания определяются следующим образом:

  **Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF).

  Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер TFTP не ответит на запрос.

  Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа сервера TFTP.

- **ip_type**: позволяет указать, какой протокол IP использовать. Допустимые значения: IPv4 (4) или IPv6 (6).

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): файл клиента успешно открыт.

- **NX_TFTP_NOT_CLOSED** (0xC3): клиент уже открыл файл.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08): получен недопустимый адрес сервера.

- **NX_TFTP_NO_ACK_RECEIVED** (0x09): не получено сообщение ACK от сервера.

- **NX_TFTP_INVALID_IP_VERSION** (0X0C): недопустимая версия протокола IP.

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08): получен недопустимый IP-адрес сервера.

- **NX_TFTP_CODE_ERROR** (0X05): получен код ошибки.

- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

- NX_IP_ADDRESS_ERROR (0x21): недопустимый IP-адрес сервера.

- NX_OPTION_ERROR (0x0A): недопустимый тип операции открытия.

- NX_INVALID_PARAMETERS (0x4D): недопустимые входные данные, отличные от указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
                & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_read"></a>nxd_tftp_client_file_read

Чтение блока из файла клиента.

### <a name="prototype"></a>Прототип

```C
UINT nxd_tftp_client_file_read(NX_TFTP_CLIENT *tftp_client_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a>Описание

Эта служба считывает блок размером в 512 байт из открытого ранее файла клиента TFTP. Блок, содержащий менее 512 байт, означает конец файла.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом TFTP.

- **packet_ptr**: место назначения для пакета, содержащего блок, считанный из файла.

- **wait_option**: определяет, как долго служба будет ожидать завершения чтения. Параметры ожидания определяются следующим образом:

  **Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF).

  Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер TFTP не ответит на запрос.

  Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для ожидания в состоянии приостановки, пока сервер TFTP не отправит блок из файла.

- **ip_type**: позволяет указать, какой протокол IP использовать. Допустимые значения: IPv4 (4) или IPv6 (6).

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): блок успешно считан из файла клиента.

- **NX_TFTP_NOT_OPEN** (0xC3): указанный файл клиента не открыт для чтения.

- **NX_NO_PACKET** (0X01): сервер не передал какие-либо пакеты.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08): получен недопустимый адрес сервера.

- **NX_TFTP_NO_ACK_RECEIVED** (0x09): не получено сообщение ACK от сервера.

- **NX_TFTP_END_OF_FILE** (0xC5): обнаружен конец файла (не ошибка).

- **NX_TFTP_INVALID_IP_VERSION** (0X0C): недопустимая версия протокола IP.

- **NX_TFTP_CODE_ERROR** (0X05): получен код ошибки.

- **NX_TFTP_FAILED** (0xC2): получен неизвестный код TFTP.

- **NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A): получен недопустимый номер блока.

- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

- NX_INVALID_PARAMETERS (0x4D): недопустимые входные данные, отличные от указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Read a block from a previously opened file of “my_client”. */
status =  nxd_tftp_client_file_read(&my_tftp_client, &return_packet_ptr, 200);

/* If status is NX_SUCCESS a block of the TFTP file is in the payload of
   “return_packet_ptr”. */
```

## <a name="nxd_tftp_client_file_write"></a>nxd_tftp_client_file_write

Запись блока в файл клиента.

### <a name="prototype"></a>Прототип

```C
UINT nxd_tftp_client_file_write(NX_TFTP_CLIENT *tftp_client_ptr,
            NX_PACKET *packet_ptr, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a>Описание

Эта служба записывает блок размером в 512 байт в открытый ранее файл клиента TFTP. Если указан блок, содержащий менее 512 байт, это означает конец файла.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом TFTP.

- **packet_ptr**: пакет, содержащий блок для записи в файл.

- **wait_option**: определяет, как долго служба будет ожидать завершения записи. Параметры ожидания определяются следующим образом:

  **Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF).

  Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер TFTP не ответит на запрос.
 
  Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для ожидания в состоянии приостановки, пока сервер TFTP не отправит сообщение ACK для запроса на запись.

- **ip_type**: позволяет указать, какой протокол IP использовать. Допустимые значения: IPv4 (4) или IPv6 (6).

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): блок успешно записан в файл клиента.

- **NX_TFTP_NOT_OPEN** (0xC3): указанный файл клиента не открыт для записи.

- **NX_TFTP_TIMEOUT** (0XC1): время ожидания сообщения ACK от сервера.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08): получен недопустимый адрес сервера.

- **NX_TFTP_NO_ACK_RECEIVED** (0x09): не получено сообщение ACK от сервера.

- **NX_TFTP_INVALID_IP_VERSION** (0X0C): недопустимая версия протокола IP.

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08): получен недопустимый адрес сервера.

- **NX_TFTP_CODE_ERROR** (0X05): получен код ошибки.

- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

- NX_INVALID_PARAMETERS (0x4D): недопустимые входные данные, отличные от указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Write a block to the previously opened file of “my_client”. */
status =  nxd_tftp_client_file_write(&my_tftp_client, packet_ptr, 200);

/* If status is NX_SUCCESS the block in the payload of “packet_ptr” was 
   written to the TFTP file opened by “my_client”. */
```

## <a name="nxd_tftp_client_packet_allocate"></a>nxd_tftp_client_packet_allocate

Выделение пакета для записи в файл клиента.

### <a name="prototype"></a>Прототип

```C
UINT nxd_tftp_client_packet_allocate(NX_PACKET_POOL *pool_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a>Описание

Эта служба выделяет пакет UDP из указанного пула пакетов и освобождает пространство для 4-байтового заголовка TFTP перед возвращением пакета вызывающему объекту. После этого вызывающий объект может создать буфер для записи в файл клиента.

### <a name="input-parameters"></a>Входные параметры

- **pool_ptr**: указатель на пул пакетов.

- **packet_ptr**: место назначения для указателя на выделенный пакет.

- **wait_option**: определяет, как долго служба будет ожидать завершения выделения пакета. Параметры ожидания определяются следующим образом:

  **Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF).

  В случае выбора TX_WAIT_FOREVER вызывающий поток приостанавливается на неопределенное время, пока пакет не будет выделен.

  Числовое значение (от 1 до 0xFFFFFFFE) указывает максимальное количество тактов таймера для ожидания выделения пакета в состоянии приостановки.

- **ip_type**: позволяет указать, какой протокол IP использовать. Допустимые значения: IPv4 (4) или IPv6 (6).

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): пакет выделен успешно.

- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

- NX_INVALID_PARAMETERS (0x4D): недопустимые входные данные, отличные от указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Allocate a packet for TFTP file write. */
status =  nxd_tftp_client_packet_allocate(&my_pool, &packet_ptr, 200);

/* If status is NX_SUCCESS “packet_ptr” contains the new packet. */
```

## <a name="nxd_tftp_client_set_interface"></a>nxd_tftp_client_set_interface

Настройка физического интерфейса для запросов TFTP.

### <a name="prototype"></a>Прототип

```C
UINT nxd_tftp_client_set_interface(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT if_index);
```

### <a name="description"></a>Описание

Эта служба использует входной индекс интерфейса, чтобы задать физический интерфейс клиента TFTP для отправки и получения пакетов TFTP. Значение по умолчанию равно нулю, что соответствует основному интерфейсу.

> [!NOTE]
> Для использования этой службы версия NetX Duo должна поддерживать множественную адресацию (версия 5.6 или более поздняя версия).

### <a name="input-parameters"></a>Входные параметры

- **tftp_client_ptr**: указатель на экземпляр клиента TFTP.

- **if_index**: индекс используемого физического интерфейса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): интерфейс успешно задан; (0x0B): недопустимые входные данные интерфейса.

- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

- NX_TFTP_INVALID_INTERFACE (0x0B): недопустимые входные данные интерфейса.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Specify the primary interface for TFTP requests. */
status =  nxd_tftp_client_set_interface(&client, 0);

/* If status is NX_SUCCESS the primary interface will be use for TFTP communications. */
```

## <a name="nxd_tftp_server_create"></a>nxd_tftp_server_create

Создание сервера TFTP.

### <a name="prototype"></a>Прототип

```C
UINT nxd_tftp_server_create(NX_TFTP_SERVER *tftp_server_ptr,
            CHAR *tftp_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr, 
            VOID *stack_ptr, ULONG stack_size,
            NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Описание

Эта служба создает сервер TFTP, отвечающий на запросы клиентов TFTP через порт 69. Данный сервер должен быть запущен последующим вызовом *nxd_tftp_server_start*.

> [!IMPORTANT]
> Приложение должно обеспечить предварительное создание указанного экземпляра IP, пула пакетов и экземпляра носителя FileX. Кроме того, перед вызовом этой службы необходимо включить протокол UDP для экземпляра IP.

### <a name="input-parameters"></a>Входные параметры

- **tftp_server_ptr**: указатель на блок управления сервером TFTP.

- **tftp_server_name**: имя этого экземпляра сервера TFTP.

- **ip_ptr**: указатель на созданный ранее экземпляр IP.

- **media_ptr**: указатель на экземпляр носителя FileX.

- **stack_ptr**: указатель на область стека сервера TFTP.

- **stack_size**: число байтов в стеке сервера TFTP.

- **pool_ptr**: указатель на пул пакетов TFTP. 

> [!NOTE]
> Указанный пул должен вмещать полезные данные пакетов размером не менее 580 байт.<sup>1</sup>

<sup>1</sup> Сами данные пакета занимают ровно 512 байт, но размер полезных данных пакета должен составлять не менее 572 байт. Оставшиеся байты используются для заголовков UDP, IPv6 и Ethernet и потенциальных младших байтов, необходимых драйверу для выравнивания.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) сервер успешно создан.

- **NX_TFTP_POOL_ERROR** (0xC6): размер пакета в пуле пакетов меньше 560 байт.

- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```C
/* Create a TFTP Server called “my_server”. */
status =  nxd_tftp_server_create(&my_server, “My TFTP Server”, &server_ip, 
                &ram_disk, stack_ptr, 2048, pool_ptr);

/* If status is NX_SUCCESS the TFTP Server is created. */
```

## <a name="nxd_tftp_server_delete"></a>nxd_tftp_server_delete

Удаление сервера TFTP.

### <a name="prototype"></a>Прототип

```C
UINT nxd_tftp_server_delete(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет созданный ранее сервер TFTP.

### <a name="input-parameters"></a>Входные параметры

- **tftp_server_ptr**: указатель на блок управления сервером TFTP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): сервер успешно удален.

- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Delete the TFTP Server called “my_server”. */
status =  nxd_tftp_server_delete(&my_server);

/* If status is NX_SUCCESS the TFTP Server is deleted. */
```

## <a name="nxd_tftp_server_start"></a>nxd_tftp_server_start

Запуск сервера TFTP.

### <a name="prototype"></a>Прототип

```C
UINT nxd_tftp_server_start(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Описание

Эта служба запускает созданный ранее сервер TFTP.

### <a name="input-parameters"></a>Входные параметры

- **tftp_server_ptr**: указатель на блок управления сервером TFTP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): сервер успешно запущен.

- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.
 
### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```C
/* Start the TFTP Server called “my_server”. */
status =  nxd_tftp_server_start(&my_server);

/* If status is NX_SUCCESS the TFTP Server is started. */
```

## <a name="nxd_tftp_server_stop"></a>nxd_tftp_server_stop

Остановка сервера TFTP.

### <a name="prototype"></a>Прототип

```C
UINT nxd_tftp_server_stop(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>Описание

Эта служба останавливает созданный ранее сервер TFTP.

### <a name="input-parameters"></a>Входные параметры

- **tftp_server_ptr**: указатель на блок управления сервером TFTP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): сервер успешно остановлен.

- NX_PTR_ERROR (0x16): недопустимые входные данные указателя.

- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Stop the TFTP Server called “my_server”. */
status =  nxd_tftp_server_stop(&my_server);

/* If status is NX_SUCCESS the TFTP Server is stopped. */
```