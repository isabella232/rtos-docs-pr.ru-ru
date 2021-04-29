---
title: Глава 3. Описание служб FTP
description: Эта глава содержит описание всех служб NetX FTP, перечисленных ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d721d8bd3e08d8cccdc13011807b4c5017c84173
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814707"
---
# <a name="chapter-3---description-of-ftp-services"></a>Глава 3. Описание служб FTP

В этой главе содержится описание всех служб FTP в NetX, перечисленных ниже в алфавитном порядке (эквивалентные службы IPv4 и IPv6 приводятся вместе).

> [!NOTE]
> В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

## <a name="nx_ftp_client_connect"></a>nx_ftp_client_connect

Подключение к FTP-серверу через IPv4

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG server_ip, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба подключает ранее созданный экземпляр клиента FTP NetX к FTP-серверу по заданному IP-адресу.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом FTP
- **server_ip**: IP-адрес FTP-сервера
- **username**: имя пользователя клиента для проверки подлинности
- **password**: пароль клиента для проверки подлинности
- **wait_option** определяет, как долго служба будет ожидать подключения клиента FTP Параметры ожидания определяются следующим образом.
  - **timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — FTP-подключение успешно создано.
- **NX_TFTP_EXPECTED_22X_CODE** (0xDB) — ответ 22X (OK) не получен.
- **NX_FTP_EXPECTED_23X_CODE** (0xDC) — ответ 23X (OK) не получен.
- **NX_FTP_EXPECTED_33X_CODE** (0xDE) — ответ 33X (OK) не получен.
- **NX_FTP_NOT_DISCONNECTED** (0xD4) — клиент уже подключен.
- NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.
- NX_IP_ADDRESS_ERROR (0x21) — недопустимый IP-адрес.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Connect the FTP Client instance “my_client” to the FTP Server at

IP address 1.2.3.4. */

status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a>См. также:

nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nxd_ftp_client_connect

## <a name="nxd_ftp_client_connect"></a>nxd_ftp_client_connect

Подключение к FTP-серверу с поддержкой IPv6

### <a name="prototype"></a>Прототип

```C
UINT nxd_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    NXD_ADDRESS *server_ipduo, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба подключает ранее созданный экземпляр клиента FTP NetX Duo к FTP-серверу по заданному IP-адресу. Поддерживаются сети IPv4 и IPv6.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом FTP
- **server_ipduo**: IP-адрес FTP-сервера
- **username**: имя пользователя клиента для проверки подлинности
- **password**: пароль клиента для проверки подлинности
- **wait_option** определяет, как долго служба будет ожидать подключения клиента FTP Параметры ожидания определяются следующим образом.
  - **timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — FTP-подключение успешно создано.
- **NX_TFTP_EXPECTED_22X_CODE** (0xDB) — ответ 22X (OK) не получен.
- **NX_FTP_EXPECTED_23X_CODE** (0xDC) — ответ 23X (OK) не получен.
- **NX_FTP_EXPECTED_33X_CODE** (0xDE) — ответ 33X (OK) не получен.
- **NX_FTP_NOT_DISCONNECTED** (0xD4) — клиент уже подключен.
- NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.
- NX_IP_ADDRESS_ERROR (0x21) — недопустимый IP-адрес.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Connect an FTP Client instance to the FTP Server. */

/* Set up an IPv6 address for the server here.
    Note this could also be an IPv4 address as well*/

server_ip_addr.nxd_ip_address.v6[3] = 0x106;
server_ip_addr.nxd_ip_address.v6[2] = 0x0;
server_ip_addr.nxd_ip_address.v6[1] = 0x0000f101;
server_ip_addr.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V6;

status = nxd_ftp_client_connect(&my_client, server_ip_addr, NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a>См. также:

nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nx_ftp_client_connect

## <a name="nx_ftp_client_create"></a>nx_ftp_client_create

Создание экземпляра клиента FTP

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>Описание

Эта служба создает экземпляр клиента FTP.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом FTP
- **ftp_client_name**: имя клиента FTP
- **ip_ptr**: указатель на ранее созданный экземпляр IP
- **window_size**: размер объявленного окна для сокета TCP этого клиента FTP
- **pool_ptr**: указатель на пул пакетов по умолчанию для этого клиента FTP Обратите внимание, что минимальная полезная нагрузка пакета должна быть достаточно большой, чтобы вмещать полный путь и имя файла или каталога.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — клиент FTP успешно создан.
- NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="example"></a>Например, .

```C
/* Create the FTP Client instance “my_client.” */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
    2000, &client_pool);
/* If status is NX_SUCCESS the FTP Client instance was successfully created. */
```

## <a name="nx_ftp_client_delete"></a>nx_ftp_client_delete

Удаление экземпляра клиента FTP

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет экземпляр клиента FTP.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом FTP

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — клиент FTP успешно удален.
- **NX_FTP_NOT_DISCONNECTED** (0xD4) — клиент FTP не отключен.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Delete the FTP Client instance “my_client.” */

status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a>nx_ftp_client_directory_create

Создание каталога на FTP-сервере

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба создает указанный каталог на FTP-сервере, подключенном к указанному клиенту FTP.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом FTP
- **directory_name**: имя создаваемого каталога
- **wait_option** определяет, как долго служба будет ожидать создания каталога FTP Параметры ожидания определяются следующим образом.
  - **timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — каталог FTP успешно создан.
- **NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Create the directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_create(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” was successfully created. */
```

## <a name="nx_ftp_client_directory_default_set"></a>nx_ftp_client_directory_default_set

Задание каталога по умолчанию на FTP-сервере

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба задает каталог по умолчанию на FTP-сервере, подключенном к указанному клиенту FTP. Этот каталог по умолчанию применяется только к подключению этого клиента.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом FTP
- **directory_path**: имя пути к каталогу, который необходимо задать
- **wait_option** определяет, как долго служба будет ожидать задания каталога FTP по умолчанию Параметры ожидания определяются следующим образом.
  - **timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — каталог FTP по умолчанию успешно задан.
- **NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Set the default directory to “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_default_set(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a>nx_ftp_client_directory_delete

Удаление каталога на FTP-сервере

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба удаляет указанный каталог на FTP-сервере, подключенном к указанному клиенту FTP.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом FTP
- **directory_name**: имя удаляемого каталога
- **wait_option** определяет, как долго служба будет ожидать удаления каталога FTP Параметры ожидания определяются следующим образом.
  - **timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — каталог FTP успешно удален.
- **NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Delete directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_delete(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a>nx_ftp_client_directory_listing_get

Получение содержимого каталога с FTP-сервера

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба получает содержимое указанного каталога на FTP-сервере, подключенном к указанному клиенту FTP. Приведенный указатель пакета будет содержать одну запись каталога или несколько. Каждая запись отделяется комбинацией символов \<cr/lf\>. Для завершения операции получения каталога необходимо вызвать службу ***nx_ftp_client_directory_listing_continue***.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом FTP
- **directory_name**: имя каталога, содержимое которого нужно получить
- **packet_ptr**: указатель на указатель пакета назначения В случае успешного выполнения полезная нагрузка пакета будет содержать одну запись каталога или несколько.
- **wait_option** определяет, как долго служба будет ожидать получения содержимого каталога FTP Параметры ожидания определяются следующим образом.
  - **timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — содержимое каталога FTP успешно получено.
- **NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.
- **NX_NOT_ENABLED** (0x14) — служба (IPv6) не включена.
- **NX_FTP_EXPECTED_1XX_CODE** (0xD9) — ответ 1XX (OK) не получен.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Get the contents of directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_get(&my_client, “my_dir”, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_directory_listing_continue"></a>nx_ftp_client_directory_listing_continue

Продолжение получения содержимого каталога с FTP-сервера

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба продолжает получать содержимое указанного каталога на FTP-сервере, подключенном к указанному клиенту FTP. Перед ней должен быть выполнен вызов службы ***nx_ftp_client_directory_listing_get***. В случае успеха заданный указатель пакета будет содержать одну запись каталога или несколько. Эту подпрограмму следует вызывать до получения состояния NX_FTP_END_OF_LISTING.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом FTP
- **packet_ptr**: указатель на указатель пакета назначения В случае успешного выполнения полезная нагрузка пакета будет содержать одну запись каталога или несколько записей, разделенных комбинацией символов <cr/lf>.
- **wait_option** определяет, как долго служба будет ожидать получения содержимого каталога FTP Параметры ожидания определяются следующим образом.
  - **timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — содержимое каталога FTP успешно получено.
- **NX_FTP_END_OF_LISTING** (0xD8) — в этом каталоге больше нет записей.
- **NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Continue getting the contents of directory “my_dir” on the FTP Server
    connected to the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_disconnect"></a>nx_ftp_client_disconnect

Отключение от FTP-сервера

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба отключает ранее установленное подключение FTP-сервера к указанному клиенту FTP.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом FTP
- **wait_option** определяет, как долго служба будет ожидать отключения клиента FTP Параметры ожидания определяются следующим образом.
  - **timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — FTP-подключение завершено.
- **NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Disconnect “my_client” from the FTP Server. */

status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, “my_client” has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a>nx_ftp_client_file_close

Закрытие файла клиента

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба закрывает ранее открытый файл на FTP-сервере.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом FTP
- **wait_option** определяет, как долго служба будет ожидать закрытия файла клиента FTP Параметры ожидания определяются следующим образом.
  - **timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — FTP-файл успешно закрыт.
- **NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.
- **NX_FTP_NOT_OPEN** (0xD5) — файл не открыт; его невозможно закрыть.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Close previously opened file of client “my_client” on the FTP Server. */

status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the “my_client” FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a>nx_ftp_client_file_delete

Удаление файла на FTP-сервере

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба удаляет указанный файл на FTP-сервере.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом FTP
- **file_name**: имя файла для удаления
- **wait_option** определяет, как долго служба будет ожидать удаления файла клиента FTP Параметры ожидания определяются следующим образом.
  - **timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — FTP-файл успешно удален.
- **NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Delete the file “my_file.txt” on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_delete(&my_client, “my_file.txt”, 200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a>nx_ftp_client_file_open

Открытие файла на FTP-сервере

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба открывает указанный файл для чтения или записи на FTP-сервере, ранее подключенном к указанному экземпляру клиента.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом FTP
- **file_name**: имя файла для открытия
- **open_type**: **NX_FTP_OPEN_FOR_READ** или **NX_FTP_OPEN_FOR_WRITE**
- **wait_option** определяет, как долго служба будет ожидать открытия файла клиента FTP Параметры ожидания определяются следующим образом.
  - **timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — FTP-файл успешно открыт.
- **NX_OPTION_ERROR** (0x0A) — недопустимый тип операции открытия.
- **NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.
- **NX_FTP_NOT_CLOSED** (0xD6) — клиент FTP уже открыт.
- **NX_NO_FREE_PORTS** (0x45) — нет доступных TCP-портов для назначения.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Open the file “my_file.txt” for reading on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_open(&my_client, “my_file.txt”, NX_FTP_OPEN_FOR_READ,
    200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a>nx_ftp_client_file_read

Чтение из файла

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба считывает пакет из ранее открытого файла. Ее следует вызывать повторно, пока не будет получено состояние NX_FTP_END_OF_FILE.

Обратите внимание, что вызывающий объект не выделяет пакет для этой службы.  Он должен предоставлять только указатель на указатель пакета. Эта служба обновит указатель на пакет так, чтобы он указывал на пакет, полученный из очереди получения сокета.  Если возвращено успешное состояние, это означает, что пакет доступен, а вызывающий объект отвечает за освобождение пакета после завершения работы с ним.

Если возвращается ненулевое состояние (состояние ошибки или NX_FTP_END_OF_FILE), вызывающий объект не освобождает пакет. Если указатель пакета имеет значение NULL, возникает ошибка.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом FTP
- **packet_ptr**: указатель на место назначения для сохраняемого указателя пакета данных В случае успеха данные пакета будут содержать часть файла или файл полностью.
- **wait_option** определяет, как долго служба будет ожидать чтения файла клиента FTP Параметры ожидания определяются следующим образом.
  - **timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — FTP-файл успешно считан.
- **NX_FTP_NOT_OPEN** (0xD5) — клиент FTP не открыт.
- **NX_FTP_END_OF_FILE** (0xD7) — конец условия файла.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
NX_PACKET   *my_packet;

/* Read a packet of data from the file “my_file.txt” that was previously opened
    from the client “my_client.” */

status = nx_ftp_client_file_read(&my_client, &my_packet, 200);

/* Check status.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else
{
    /* Release packet when done with it. */
    nx_packet_release(my_packet);
}

/* If status is NX_SUCCESS, the packet pointer, “my_packet” points to the packet
    that contains the next bytes from the file. If the file is completely
    downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a>nx_ftp_client_file_rename

Переименование файла на FTP-сервере

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
    CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба переименовывает файл на FTP-сервере.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом FTP
- **filename**: текущее имя файла
- **new_filename**: новое имя файла
- **wait_option** определяет, как долго служба будет ожидать переименования файла клиента FTP Параметры ожидания определяются следующим образом.
  - **timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — FTP-файл успешно переименован.
- **NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.
- **NX_FTP_EXPECTED_3XX_CODE** (0XDD) — ответ 3XX (OK) не получен.
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Rename file “my_file.txt” to “new_file.txt” on the previously connected
    Client instance “my_client.” */

status = nx_ftp_client_file_rename(&my_client, “my_file.txt”, “new_file.txt”,
    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a>nx_ftp_client_file_write

Запись в файл

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба записывает пакет данных в ранее открытый файл на FTP-сервере.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом FTP
- **packet_ptr**: указатель пакета, содержащий данные для записи
- **wait_option** определяет, как долго служба будет ожидать записи в файл клиента FTP Параметры ожидания определяются следующим образом.
  - **timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера
  - **TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — запись в FTP-файл успешно выполнена.
- **NX_FTP_NOT_OPEN** (0xD5) — клиент FTP не открыт.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Write the data contained in “my_packet” to the previously opened file
    “my_file.txt”. */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a>nx_ftp_client_passive_mode_set

Включение или отключение пассивного режима передачи

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
    UINT passive_mode_enabled);
```

### <a name="description"></a>Описание

Эта служба включает пассивный режим передачи, если для входных данных passive_mode_enabled задано NX_TRUE в ранее созданном экземпляре клиента FTP, так что последующие вызовы для чтения или записи файлов (RETR, STOR) или скачивания содержимого каталога (NLST) выполняются в режиме передачи. Чтобы отключить пассивный режим передачи и вернуться к заданному по умолчанию активному режиму передачи, вызовите эту функцию, для входных данных passive_mode_enabled которой задано NX_FALSE.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом FTP
- **passive_mode_enabled**: если задано значение NX_TRUE, пассивный режим включен<br />Если задано значение NX_FALSE, пассивный режим отключен.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — пассивный режим успешно задан.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.
- NX_INVALID_PARAMETERS (0x4D) — недопустимые входные данные без указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a>nx_ftp_server_create

Создание FTP-сервера

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address,
        UINT client_port, CHAR *name, CHAR *password,
        CHAR *extra_info),
    UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address, UINT client_port,
         CHAR *name, CHAR *password, CHAR *extra_info));
```

### <a name="description"></a>Описание

Эта служба создает экземпляр FTP-сервера в указанном и ранее созданном экземпляре IP для NetX. Обратите внимание, что для начала работы FTP-сервер должен быть запущен с помощью вызова службы ***nx_ftp_server_start***.

### <a name="input-parameters"></a>Входные параметры

- **ftp_server_ptr**: указатель на блок управления FTP-сервера
- **ftp_server_name**: имя FTP-сервера
- **ip_ptr**: указатель на связанный экземпляр IP для NetX Обратите внимание, что для экземпляра IP может существовать только один FTP-сервер.
- **media_ptr**: указатель на связанный экземпляр носителя FileX
- **stack_ptr**: указатель на память области стека внутреннего потока FTP-сервера
- **stack_size**: размер области стека, заданный параметром *stack_ptr*
- **pool_ptr**: указатель на пул пакетов NetX по умолчанию Обратите внимание, что размер полезных данных пакетов в пуле должен быть достаточно большим, чтобы вмещать максимально длинное имя файла или путь.
- **ftp_login**: указатель функции для функции входа в приложение Эта функция предоставляет имя пользователя и пароль от клиента, запросившего подключение, а также адрес клиента в типе данных ULONG. Если они являются допустимыми, функция входа в приложение должна вернуть NX_SUCCESS.
- **ftp_logout**: указатель функции на функцию выхода из приложения Эта функция предоставляет имя пользователя и пароль от клиента, запросившего отключение, а также адрес клиента в типе данных ULONG. Если они являются допустимыми, функция входа в приложение должна вернуть NX_SUCCESS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — FTP-сервер успешно создан.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="example"></a>Например, .

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nx_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nxd_ftp_server_create"></a>nxd_ftp_server_create

Создание FTP-сервера с поддержкой IPv4 и IPv6

### <a name="prototype"></a>Прототип

```C
UINT nxd_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info),
    UINT (*ftp_logout_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info));
```

### <a name="description"></a>Описание

Эта служба создает экземпляр FTP-сервера в указанном и ранее созданном экземпляре IP для NetX. Обратите внимание, что после создания FTP-сервера его все равно необходимо запустить с помощью вызова ***nx_ftp_server_start***, чтобы он начал работать.

### <a name="input-parameters"></a>Входные параметры

- **ftp_server_ptr**: указатель на блок управления FTP-сервера
- **ftp_server_name**: имя FTP-сервера
- **ip_ptr**: указатель на связанный экземпляр IP для NetX Обратите внимание, что для экземпляра IP может существовать только один FTP-сервер.
- **media_ptr**: указатель на связанный экземпляр носителя FileX
- **stack_ptr**: указатель на память области стека внутреннего потока FTP-сервера
- **stack_size**: размер области стека, заданный параметром *stack_ptr*
- **pool_ptr**: указатель на пул пакетов NetX по умолчанию Обратите внимание, что размер полезных данных пакетов в пуле должен быть достаточно большим, чтобы вмещать максимально длинное имя файла или путь.
- **ftp_login_duo**: указатель функции на функцию входа в приложение Эта функция предоставляет имя пользователя и пароль от клиента, запросившего подключение, а также указатель на адрес клиента в типе данных NXD_ADDRESS. Если они являются допустимыми, функция входа в приложение должна вернуть NX_SUCCESS.
- **ftp_logout_duo**: указатель функции на функцию выхода из приложения Эта функция предоставляет имя пользователя и пароль от клиента, запросившего отключение, а также указатель на адрес клиента в типе данных NXD_ADDRESS. Если они являются допустимыми, функция входа в приложение должна вернуть NX_SUCCESS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — FTP-сервер успешно создан.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Инициализация и потоки

### <a name="example"></a>Например, .

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nxd_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_duo_login, my_duo_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a>nx_ftp_server_delete

Удаление FTP-сервера

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет ранее созданный экземпляр FTP-сервера.

### <a name="input-parameters"></a>Входные параметры

- **ftp_server_ptr**: указатель на блок управления FTP-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — FTP-сервер успешно удален.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Delete the FTP Server “my_server”. */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a>nx_ftp_server_start

Запуск FTP-сервера

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Описание

Эта служба запускает ранее созданный экземпляр FTP-сервера.

### <a name="input-parameters"></a>Входные параметры

- **ftp_server_ptr**: указатель на блок управления FTP-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — FTP-сервер успешно запущен.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Start the FTP Server “my_server”. */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a>nx_ftp_server_stop

Остановка FTP-сервера

### <a name="prototype"></a>Прототип

```C
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>Описание

Эта служба останавливает ранее созданный и запущенный экземпляр FTP-сервера.

### <a name="input-parameters"></a>Входные параметры

- **ftp_server_ptr**: указатель на блок управления FTP-сервера

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) — FTP-сервер успешно остановлен.
- NX_PTR_ERROR (0x07) — недопустимый указатель FTP.
- NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Stop the FTP Server “my_server”. */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
