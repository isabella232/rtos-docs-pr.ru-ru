---
title: Глава 3. Описание служб клиента NetX POP3 для ОСРВ Azure
description: Эта глава содержит описание всех служб клиента NetX POP3 для ОСРВ Azure, перечисленных ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1a0ab96a454bea9f56ced0d7aa8de5d481b284e9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815160"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pop3-client-services"></a>Глава 3. Описание служб клиента NetX POP3 для ОСРВ Azure

Эта глава содержит описание всех служб клиента NetX POP3 для ОСРВ Azure, перечисленных ниже в алфавитном порядке.

В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, используемым для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

- nx_pop3_client_create: *создание экземпляра клиента POP3*.
- nx_pop3_client_delete: *удаление экземпляра клиента POP3*.
- nx_pop3_client_ mail_item_get: *удаление элемента почты клиента из почтового ящика на сервере*.
- nx_pop3_client_mail_item_get: *получение размера указанного почтового сообщения*.
- nx_pop3_client_mail_items_get: *получение количества элементов в почтовом ящике*.
- nx_pop3_client_mail_item_message _get: *скачивание указанного почтового сообщения*.
- nx_pop3_client_mail_item_size_get: *получение размера указанного элемента почты*.

## <a name="nx_pop3_client_create"></a>nx_pop3_client_create

Создание экземпляра клиента POP3

### <a name="prototype"></a>Прототип

```c
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                        UINT APOP_authentication, NX_IP *ip_ptr,
                        NX_PACKET_POOL *packet_pool_ptr,
                        ULONG server_ip_address,
                        ULONG server_port,
                        CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a>Описание

Эта служба создает экземпляр клиента POP3 и настраивает для него конфигурацию, используя входные параметры.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на создаваемый клиент.
- **APOP_authentication**: включение проверки подлинности APOP.
- **ip_ptr**: указатель на экземпляр IP-адреса.
- **packet_pool_ptr**: указатель на пул пакетов клиента.
- **server_ip_address**: адрес сервера POP3.
- **server_port**: порт сервера POP3.
- **client_name**: указатель на имя клиента.
- **client_password**: указатель на пароль клиента.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) клиент успешно создан.
- **status**: состояние завершения вызовов служб NetX и ThreadX.
- NX_PTR_ERROR: (0x07) недопустимый параметр указателя во входных данных.
- NX_POP3_PARAM_ERROR: (0xB1) недопустимые входные данные, кроме указателей.

### <a name="allowed-from"></a>Допустимые источники

Код приложения

### <a name="example"></a>Например, .

```c
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST                   "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD          "pass"
#define POP3_SERVER_ADDRESS         IP_ADDRESS(192,2,2,92
#define POP3_SERVER_PORT            110

/* Create a NetX POP3 Client instance. */
ULONG server_ip_address = IP_ADDRESS(1,2,3,4);
status = nx_pop3_client_create(&demo_client,
        NX_FALSE /* disable APOP authentication */,
        &client_ip, &client_packet_pool,
        server_ip_address, POP3_SERVER_PORT,
        LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a>nx_pop3_client_delete

Удаление экземпляра клиента POP3

### <a name="prototype"></a>Прототип

```c
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr)
```

### <a name="description"></a>Описание

Эта служба удаляет ранее созданный клиент POP3. Учтите, что эта служба не удаляет пул пакетов для клиента POP3. Приложение устройства должно удалить этот ресурс отдельно, если пул пакетов больше не используется.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на удаляемый клиент.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) клиент успешно удален
- NX_PTR_ERROR: (0x07) недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники

Код приложения

### <a name="example"></a>Например, .

```c
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a>nx_pop3_client_mail_item_delete

Удаление указанного элемента почты из почтового ящика клиента

### <a name="prototype"></a>Прототип

```c
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
                                    UINT mail_index)
```

### <a name="description"></a>Описание

Эта служба удаляет указанный элемент почты из почтового ящика клиента. Она предназначена для удаления уже скачанных элементов почты, хотя некоторые серверы POP3 могут автоматически удалять элементы почты после запрашивания клиентом.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на экземпляр клиента.
- **mail_index**: порядковый индекс в пределах почтового ящика клиента.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) запрос на удаление успешно выполнен.
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) недопустимый индекс элемента почты.
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) слишком короткие полезные данные в пакете для запроса POP3.
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) ответ сервера содержит состояние ошибки.
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) недопустимый входной параметр индекса.
- NX_PTR_ERROR: (0x07) недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники

Код приложения

### <a name="example"></a>Например, .

```c
ULONG     item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status = 
   NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a>nx_pop3_client_mail_item_get

Получение указанного элемента почты

### <a name="prototype"></a>Прототип

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item, ULONG *item_size)
```

### <a name="description"></a>Описание

Эта служба создает запрос RETR для получения из почтового ящика клиента элемента почты с индексом mail_item. После выполнения запроса RETR и получения положительного ответа от сервера клиент может начать скачивание почтового сообщения с помощью службы *nx_pop3_client_mail_item_message_get*. Обратите внимание, что эта служба также предоставляет размер элемента почты, извлеченного из ответа сервера.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на экземпляр клиента.
- **mail_item**: порядковый индекс в пределах почтового ящика клиента.
- **item_size**: указатель на размер почтового сообщения.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) элемент почты успешно получен.
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) недопустимый индекс элемента почты.
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) слишком короткие полезные данные в пакете для запроса POP3.
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) ответ сервера содержит состояние ошибки.
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) недопустимый входной параметр индекса.
- NX_PTR_ERROR: (0x07) недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники

Код приложения

### <a name="example"></a>Например, .

```c
ULONG     item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a>nx_pop3_client_mail_items_get

Получение количества элементов в почтовом ящике

### <a name="prototype"></a>Прототип

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

### <a name="description"></a>Описание

Эта служба выполняет запрос STAT для получения количества элементов почты и общего объема данных почтовых сообщений в почтовом ящике клиента.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на экземпляр клиента.
- **number_mail_item**: количество писем в почтовом ящике клиента.
- **maildrop_total_size**: указатель на общий размер всех почтовых сообщений.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) элемент почты успешно получен.
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) недопустимый индекс элемента почты.
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) слишком короткие полезные данные в пакете для запроса POP3.
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) ответ сервера содержит состояние ошибки. 
- NX_PTR_ERROR: (0x07) недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники

Код приложения

### <a name="example"></a>Например, .

```c
UINT      number_mail_items;
ULONG     maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
                                        &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a>nx_pop3_client_mail_item_message_get

Получение сообщения из указанного элемента почты

### <a name="prototype"></a>Прототип

```c
UINT nx_pop3_client_mail_item_message_get(
                NX_POP3_CLIENT *client_ptr,
                NX_PACKET **recv_packet_ptr,
                ULONG *bytes_retrieved,
                UINT *final_packet)
```

### <a name="description"></a>Описание

Эта служба извлекает сообщение из элемента почты, размер почтового сообщения и сведения о том, является ли пакет в почтовом сообщении последним. Если параметр `final_packet` имеет значение NX_TRUE, то предоставленный в `recv_packet_ptr` пакет является последним в сообщении этого почтового элемента.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на экземпляр клиента.
- **recv_packet_ptr**: полученный пакет данных из сообщения.
- **number_mail_item**: количество писем в почтовом ящике клиента.
- **maildrop_total_size**: указатель на общий размер всех почтовых сообщений.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) элемент почты успешно получен.
- **NX_POP3_CLIENT_INVALID_STATE**: (0xB7) слишком короткие полезные данные в пакете для запроса POP3.
- NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники

Код приложения

### <a name="example"></a>Например, .

```c
NX_PACKET     *recv_packet_ptr;
ULONG         bytes_retrieved;
UINT          final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
                                                bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a>nx_pop3_client_mail_item_size_get

Получение размера указанного элемента почты

### <a name="prototype"></a>Прототип

```c
UINT nx_pop3_client_mail_item_size_get(
                NX_POP3_CLIENT *client_ptr,
                UINT mail_item, ULONG *size)
```

### <a name="description"></a>Описание

Эта служба создает запрос LIST для получения размера указанного элемента почты.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на экземпляр клиента.
- **mail_item**: порядковый индекс в пределах почтового ящика клиента.
- **size**: указатель на размер почтового сообщения.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS**: (0x00) элемент почты успешно получен.
- **NX_POP3_INVALID_MAIL_ITEM**: (0xB2) недопустимый индекс элемента почты.
- **NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) слишком короткие полезные данные в пакете для запроса POP3.
- **NX_POP3_SERVER_ERROR_STATUS**: (0xB4) ответ сервера содержит состояние ошибки.
- NX_POP3_CLIENT_INVALID_INDEX: (0xB8) недопустимый входной параметр индекса.
- NX_PTR_ERROR: (0x07) недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники

Код приложения

### <a name="example"></a>Пример

```c
ULONG     size;
UINT      mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
