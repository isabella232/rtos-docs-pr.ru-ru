---
title: Глава 3. Описание служб NetX Duo Telnet для ОСРВ Azure
description: В этой главе приведено описание всех служб NetX Duo Telnet для ОСРВ Azure (см. ниже), перечисленных в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 991ec53aaba052b4f42da6e5a541151953121e76
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814528"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-telnet-services"></a>Глава 3. Описание служб NetX Duo Telnet для ОСРВ Azure

В этой главе приведено описание всех служб NetX Duo Telnet для ОСРВ Azure (см. ниже), перечисленных в алфавитном порядке.

В разделе "Возвращаемые значения" в описаниях API ниже значения, **ВЫДЕЛЕННЫЕ ЖИРНЫМ ШРИФТОМ**, не затрагиваются определением параметра **NX_DISABLE_ERROR_CHECKING**, который используется для отключения проверки ошибок API, в то время как значения, не выделенные жирным шрифтом, полностью отключаются.

- **nx_telnet_client_connect**: *подключение клиента Telnet с помощью адреса IPv4*
- **nxd_telnet_client_connect**: *подключение клиента Telnet IPv6 с помощью адреса IPv6*
- **nx_telnet_client_create**: *создание клиента Telnet*
- **nx_telnet_client_delete**: *удаление клиента Telnet*
- **nx_telnet_client_disconnect**: *отключение клиента Telnet*
- **nx_telnet_client_packet_receive**: *получение пакета через клиент Telnet*
- **nx_telnet_client_packet_send**: *отправка пакета через клиент Telnet*
- **nx_telnet_server_create**: *создание сервера Telnet*
- **nx_telnet_server_delete**: *удаление сервера Telnet*
- **nx_telnet_server_disconnect**: *отключение сервера Telnet*
- **nx_telnet_server_get_open_connection_count**: *получение числа открытых соединений*
- **nx_telnet_server_packet_send**: *отправка пакета через клиентское соединение*
- **nx_telnet_server_packet_pool_set**: *задать пул пакетов в качестве пула пакетов сервера Telnet*
- **nx_telnet_server_start**: *запуск сервера Telnet*
- **nx_telnet_server_stop**: *остановка сервера Telnet*

## <a name="nx_telnet_client_connect"></a>nx_telnet_client_connect

Подключение клиента Telnet с помощью адреса IPv4

### <a name="prototype"></a>Прототип

```c
UINT nx_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                              ULONG server_ip, UINT server_port, 
                              ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба пытается подключить ранее созданный экземпляр клиента Telnet к серверу по указанному IP-адресу и порту с использованием адреса IPv4 для сервера Telnet. Эта служба фактически вставляет IP-адрес сервера ULONG в блок управления NXD_ADDRESS и устанавливает для версии IP значение 4 перед вызовом службы *nxd_telnet_client_connect*, описанной ниже.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиента Telnet.
- **server_ip**: IPv4-адрес сервера Telnet.
- **server_port**: TCP-порт сервера (сервер Telnet работает на порту 23).
- **wait_option**: определяет, как долго служба будет ожидать подключения клиента Telnet. Параметры ожидания определяются следующим образом:

    - **значение времени ожидания**: (от 0x00000001 до 0xFFFFFFFE). Указание числового значения (1–0xFFFFFFFE) задает максимальное число тактов таймера для приостановки работы при ожидании ответа сервера Telnet.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF). Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер Telnet не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) успешное подключение клиента.
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4) клиент уже подключен.
- NX_PTR_ERROR: (0x07) недопустимый указатель клиента.
- NX_IP_ADDRESS_ERROR: (0x21) недопустимый IP-адрес.
- NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IP address 1.2.3.4 and port 23.  */
status =  nx_telnet_client_connect(&my_client, IP_ADDRESS(1,2,3,4), 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nxd_telnet_client_connect"></a>nxd_telnet_client_connect

Подключение клиента Telnet с помощью адреса IPv6 или IPv4

### <a name="prototype"></a>Прототип

```c
UINT nxd_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                               NXD_ADDRESS *server_ip_address, 
                               UINT server_port, 
                               ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба пытается подключить ранее созданный экземпляр клиента Telnet к серверу по указанному IP-адресу и порту с использованием адреса IPv6 сервера Telnet. Эта служба может принимать адрес IPv4 или IPv6, но он должен содержаться в переменной NXD_ADDRESS *server_ip_address*.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиента Telnet.
- **server_ip_address**: IP-адрес сервера.
- **server_port**: TCP-порт сервера (сервер Telnet работает на порту 23).
- **wait_option**: определяет, как долго служба будет ожидать подключения клиента Telnet. Параметры ожидания определяются следующим образом:

    - **значение времени ожидания**: (от 0x00000001 до 0xFFFFFFFE). Указание числового значения (1–0xFFFFFFFE) задает максимальное число тактов таймера для приостановки работы при ожидании ответа сервера Telnet.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF). Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер Telnet не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) успешное подключение клиента.
- **NX_TELNET_ERROR**: (0xF0) ошибка подключения клиента.
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4) клиент уже подключен.
- NX_PTR_ERROR: (0x07) недопустимый указатель клиента.
- NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект службы.
- NX_TELNET_INVALID_PARAMETER: (0xF5) недопустимые входные данные без указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IPv6 address 20010db1:0:f101::101 and port 23.  */
status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nx_telnet_client_create"></a>nx_telnet_client_create

Создание клиента Telnet

### <a name="prototype"></a>Прототип

```c
UINT nx_telnet_client_create(NX_TELNET_CLIENT *client_ptr, 
                             CHAR *client_name, NX_IP *ip_ptr, 
                             ULONG window_size);
```

### <a name="description"></a>Описание

Эта служба создает экземпляр клиента Telnet.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиента Telnet.
- **client_name**: имя экземпляра клиента.
- **ip_ptr**: указатель на экземпляр IP.
- **window_size**: размер окна приема TCP для этого клиента.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) успешное создание клиента.
- **NX_TELNET_ERROR**: (0xF0) ошибка при создании сокета.
- NX_PTR_ERROR: (0x07) недопустимый указатель клиента или IP.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, Потоки

### <a name="example"></a>Например, .

```c
/* Create the Telnet Client instance “my_client” on the IP instance “ip_0”.  */
status =  nx_telnet_client_create(&my_client, “My Telnet Client”, &ip_0, 2048);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   created.  */
```
## <a name="nx_telnet_client_delete"></a>nx_telnet_client_delete

Удаление клиента Telnet

### <a name="prototype"></a>Прототип

```c
UINT nx_telnet_client_delete(NX_TELNET_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет ранее созданный экземпляр клиента Telnet.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиента Telnet.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) успешное удаление клиента.
- **NX_TELNET_NOT_DISCONNECTED**: (0xF4) клиент все еще подключен.
- NX_PTR_ERROR: (0x07) недопустимый указатель клиента.
- NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Delete the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_delete(&my_client);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   deleted.  */
```

## <a name="nx_telnet_client_disconnect"></a>nx_telnet_client_disconnect

Отключение клиента Telnet

### <a name="prototype"></a>Прототип

```c
UINT nx_telnet_client_disconnect(NX_TELNET_CLIENT *client_ptr, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба отключает ранее подключенный экземпляр клиента Telnet.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиента Telnet.
- **wait_option**: определяет, как долго служба будет ожидать отключения клиента Telnet. Параметры ожидания определяются следующим образом:

    - **значение времени ожидания**: (от 0x00000001 до 0xFFFFFFFE). Указание числового значения (1–0xFFFFFFFE) задает максимальное число тактов таймера для приостановки работы при ожидании ответа сервера Telnet.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF). Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер Telnet не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) успешное отключение клиента.
- **NX_TELNET_NOT_CONNECTED**: (0xF3) клиент не подключен.
- NX_PTR_ERROR: (0x07) недопустимый указатель клиента.
- NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект этой службы.


### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c

/* Disconnect the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_disconnect(&my_client, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   disconnected.  */
```

## <a name="nx_telnet_client_packet_receive"></a>nx_telnet_client_packet_receive

Получение пакета через клиент Telnet

### <a name="prototype"></a>Прототип

```c
UINT nx_telnet_client_packet_receive(NX_TELNET_CLIENT *client_ptr, 
                                     NX_PACKET **packet_ptr, 
                                     ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба получает пакет из ранее подключенного экземпляра клиента Telnet.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиента Telnet.
- **packet_ptr**: указатель на место назначения для полученного пакета.
- **wait_option**: определяет, как долго служба будет ожидать получения пакета от клиента Telnet. Параметры ожидания определяются следующим образом:
    - **значение времени ожидания**: (от 0x00000001 до 0xFFFFFFFE). Указание числового значения (1–0xFFFFFFFE) задает максимальное число тактов таймера для приостановки работы при ожидании ответа сервера Telnet.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF). Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер Telnet не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) получение пакета от клиента успешно выполнено.
- NX_PTR_ERROR: (0x07) Недопустимые входные данные указателя.
- NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c

/* Receive a packet from the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 100);

/* If status is NX_SUCCESS the “my_packet” pointer contains data received from
   the Telnet Client connection.  */
```
## <a name="nx_telnet_client_packet_send"></a>nx_telnet_client_packet_send

Отправка пакета через клиент Telnet

### <a name="prototype"></a>Прототип

```c
UINT nx_telnet_client_packet_send(NX_TELNET_CLIENT *client_ptr, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба отправляет пакет через ранее подключенный экземпляра клиента Telnet.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиента Telnet.
- **packet_ptr**: указатель на пакет для отправки.
- **wait_option**: определяет, как долго служба будет ожидать отправки пакета в клиент Telnet. Параметры ожидания определяются следующим образом:
    - **значение времени ожидания**: (от 0x00000001 до 0xFFFFFFFE). Указание числового значения (1–0xFFFFFFFE) задает максимальное число тактов таймера для приостановки работы при ожидании ответа сервера Telnet.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF). Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер Telnet не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) отправка пакета в клиент успешно выполнено.
- **NX_TELNET_ERROR**: (0xF0) не удалось отправить пакет, вызывающий объект отвечает за освобождение пакета.
- NX_PTR_ERROR: (0x07) Недопустимые входные данные указателя.
- NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Send a packet via the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_send(&my_client, my_packet, 100);
/* If status is NX_SUCCESS the packet was successfully sent.  */

```

## <a name="nx_telnet_server_create"></a>nx_telnet_server_create

Создание сервера Telnet

### <a name="prototype"></a>Прототип

```c
UINT nx_telnet_server_create(NX_TELNET_SERVER *server_ptr, CHAR *server_name, NX_IP *ip_ptr, 
                             VOID *stack_ptr, ULONG stack_size, 
                             void (*new_connection)(struct NX_TELNET_SERVER_STRUCT*telnet_server_ptr, 
                                                    UINT logical_connection), 
                             void (*receive_data)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                  UINT logical_connection, NX_PACKET *packet_ptr), 
                             void (*connection_end)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                    UINT logical_connection));

```

### <a name="description"></a>Описание

Эта служба создает экземпляр сервера Telnet в указанном экземпляре IP.

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на управляющий блок сервера Telnet.
- **server_name**: имя экземпляра сервера Telnet.
- **ip_ptr**: указатель на связанный экземпляр IP.
- **stack_ptr**: указатель на стек для внутреннего потока сервера.
- **sack_size**: размер стека в байтах.
- **new_connection**: указатель функции подпрограммы обратного вызова приложения. Эта подпрограмма вызывается всякий раз, когда сервер обнаруживает новый запрос на подключение клиента Telnet.
- **receive_data**: указатель функции подпрограммы обратного вызова приложения. Эта подпрограмма вызывается при наличии в соединении новых данных клиента Telnet. Эта подпрограмма отвечает за освобождение пакета.
- **end_connection**: указатель функции подпрограммы обратного вызова приложения. Эта подпрограмма вызывается при каждом отключении клиента Telnet, инициализированном клиентом, или истечении времени ожидания подключения клиента (истекло время ожидания действий). Сервер также может отключиться через службу *nx_telnet_server_disconnect*, описанную ниже.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) успешное создание сервера.
- NX_PTR_ERROR: (0x07) недопустимые указатели сервера, IP, стека или обратного вызова приложения.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, Потоки

### <a name="example"></a>Например, .

```c
/* Create a Telnet Server instance “my_server”.  */
status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_0, 
                                   pointer, 2048, telnet_new_connection, 
                                   telnet_receive_data, telnet_connection_end);


/* If status is NX_SUCCESS the Telnet Server was successfully created.  */
```
## <a name="nx_telnet_server_delete"></a>nx_telnet_server_delete

Удаление сервера Telnet

### <a name="prototype"></a>Прототип

```c
UINT nx_telnet_server_delete(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет ранее созданный экземпляр сервера Telnet.

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на управляющий блок сервера Telnet.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) успешное удаление сервера.
- NX_PTR_ERROR: (0x07) недопустимый указатель сервера.
- NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Delete the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_delete(&my_server);

/* If status is NX_SUCCESS the Telnet Server was successfully deleted.  */
```

## <a name="nx_telnet_server_disconnect"></a>nx_telnet_server_disconnect

Отключение клиента Telnet

### <a name="prototype"></a>Прототип

```c
UINT nx_telnet_server_disconnect(NX_TELNET_SERVER *server_ptr, UINT logical_connection);
```

### <a name="description"></a>Описание

Эта служба отключает ранее подключенный клиент на данном экземпляре сервера Telnet. Эта подпрограмма обычно вызывается из функции обратного вызова получения данных приложения в ответ на условие, обнаруженное в полученных данных.

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на управляющий блок сервера Telnet.
- **logical_connection**: логическое подключение, соответствующее клиентскому подключению к этому серверу. Диапазон допустимых значений — от 0 до NX_TELENET_MAX_CLIENTS.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) успешное отключение сервера.
- **NX_TELNET_ERROR**: (0xF0) сбой отключения сервера.
- NX_OPTION_ERROR: (0x0A) недопустимое логическое подключение.
- NX_PTR_ERROR: (0x07) недопустимый указатель сервера.
- NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c

/* Disconnect the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_disconnect(&my_server, 2);

/* If status is NX_SUCCESS the Client on logical connection 2 was 
   disconnected.  */
```

## <a name="nx_telnet_server_get_open_connection_count"></a>nx_telnet_server_get_open_connection_count

Возвращает число открытых соединений

### <a name="prototype"></a>Прототип

```c
UINT nx_telnet_server_get_open_connection_count(NX_TELNET_SERVER *server_ptr, UINT *connection_count);
```

### <a name="description"></a>Описание

Эта служба возвращает число подключенных в настоящее время клиентов Telnet.

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на управляющий блок сервера Telnet.
- **Connection_count**: указатель на память для хранения числа подключений.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00) успешное выполнение.
- NX_PTR_ERROR: (0x07) недопустимый указатель сервера.
- NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Get the number of Telnet Clients connected to the Server. */

status =  nx_telnet_server_get_open_connection_count(&my_server, &conn_count);

/* If status is NX_SUCCESS the conn_count holds the number of open connections.  */

```

## <a name="nx_telnet_server_packet_send"></a>nx_telnet_server_packet_send

Отправка пакета через клиентское соединение

### <a name="prototype"></a>Прототип

```c
UINT nx_telnet_server_packet_send(NX_TELNET_SERVER *server_ptr, 
                                  UINT logical_connection, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба отправляет пакет клиентскому подключению к данному экземпляру сервера Telnet. Эта подпрограмма обычно вызывается из функции обратного вызова получения данных приложения в ответ на условие, обнаруженное в полученных данных.

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на управляющий блок сервера Telnet.
- **logical_connection**: логическое подключение, соответствующее клиентскому подключению к этому серверу. Диапазон допустимых значений — от 0 до NX_TELENET_MAX_CLIENTS.
- **packet_ptr**: указатель на полученный пакет.
- **wait_option**: определяет, как долго служба будет ожидать отправки пакета сервером Telnet. Параметры ожидания определяются следующим образом:
    - **значение времени ожидания**: (от 0x00000001 до 0xFFFFFFFE). Указание числового значения (1–0xFFFFFFFE) задает максимальное число тактов таймера для приостановки работы при ожидании ответа сервера Telnet.
    - **TX_WAIT_FOREVER**: (0xFFFFFFFF). Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер Telnet не ответит на запрос. 

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) пакет успешно отправлен.
- **NX_TELNET_FAILED**: (0xF2) ошибка отправки сокета TCP.
- NX_OPTION_ERROR: (0x0A) недопустимое логическое подключение.
- NX_PTR_ERROR: (0x07) недопустимый указатель сервера.
- NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Send a packet to the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_packet_send(&my_server, 2, my_packet, 100);

/* If status is NX_SUCCESS the packet was sent to the Client on logical 
   connection 2.  */
```

## <a name="nx_telnet_server_packet_pool_set"></a>nx_telnet_server_packet_pool_set

Задает ранее созданный пул пакетов в качестве пула сервера Telnet

### <a name="prototype"></a>Прототип

```c
UINT nx_telnet_server_packet_pool_set(NX_TELNET_SERVER *server_ptr, NX_PACKET_POOL *packet_pool_ptr);

```

### <a name="description"></a>Описание

Эта служба задает ранее созданный пул пакетов в качестве пула пакетов сервера Telnet, если определен параметр NX_TELNET_SERVER_USER_CREATE_PACKET_POOL. Также требуется, чтобы не был определен параметр NX_TELNET_SERVER_OPTION_DISABLE, чтобы серверу Telnet требовался пул пакетов для передачи параметров Telnet клиентам Telnet.

Это позволяет приложениям создавать пул пакетов в памяти, отличной от стека сервера Telnet, например без кэш-памяти. Обратите внимание, проверяет ли эта функция, установлен или нет пул пакетов сервера Telnet. Если она вызывается для указателя пула пакетов сервера Telnet, отличного от NULL, она перезапишет его и заменит существующий пул пакетов на пул пакетов, на который указывает указатель из входных данных.

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на управляющий блок сервера Telnet.
- **packet_pool_ptr**: указатель на ранее созданный пул пакетов.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) пул успешно задан.
- NX_PTR_ERROR: (0x07) недопустимый указатель сервера.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
status =  nx_packet_pool_create(&telnet_server_packet_pool, 
                                "Telnet Server Packet Pool", 
                                telnet_server_pool_area, 600*10);

/* Set the packet pool as the Telnet Server packet pool.   */
status =  nx_telnet_server_packet_pool_set(&my_server, &telnet_server_packet_pool);

/* If status is NX_SUCCESS the packet pool is set as Telnet Server pool.  */
```
## <a name="nx_telnet_server_start"></a>nx_telnet_server_start

Запуск сервера Telnet

### <a name="prototype"></a>Прототип

```c
UINT nx_telnet_server_start(NX_TELNET_SERVER *server_ptr);

```

### <a name="description"></a>Описание

Эта служба запускает ранее созданный экземпляр сервера Telnet.

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на управляющий блок сервера Telnet.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) запущено успешно.
- **NX_TELNET_NO_PACKET_POOL**: (0xF6) не задан пул пакетов.
- NX_PTR_ERROR: (0x07) недопустимый указатель сервера.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, Потоки

### <a name="example"></a>Например, .

```c
/* Start the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_start(&my_server);

/* If status is NX_SUCCESS the Server was started.  */
```

## <a name="nx_telnet_server_stop"></a>nx_telnet_server_stop

Остановка сервера Telnet

### <a name="prototype"></a>Прототип

```c
UINT nx_telnet_server_stop(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a>Описание

Эта служба завершает работу ранее созданного и запущенного экземпляра сервера Telnet.

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на управляющий блок сервера Telnet.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) остановлено успешно.
- NX_PTR_ERROR: (0x07) недопустимый указатель сервера.
- NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Stop the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_stop(&my_server);

/* If status is NX_SUCCESS the Server was stopped.  */
```