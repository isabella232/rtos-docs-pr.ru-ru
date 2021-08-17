---
title: Глава 3. Описание служб клиента SMTP
description: Эта глава содержит описание всех служб клиента NetX Duo SMTP (перечисленных ниже) в порядке использования в типичном клиентском приложении SMTP.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bc54e7763c4a3977ef4d760bc92025b1cda792b979d741fc7b82f8f1a3f2901b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797812"
---
# <a name="chapter-3---client-description-of-smtp-client-services"></a>Глава 3. Описание служб клиента SMTP

Эта глава содержит описание всех служб клиента NetX Duo SMTP (перечисленных ниже) в порядке использования в типичном клиентском приложении SMTP.

> [!NOTE]
> В разделе "Возвращаемые значения" в приведенных ниже описаниях API значения, выделенные **полужирным шрифтом**, не зависят от определения параметра **_NX_DISABLE_ERROR_CHECKING_**, который используется для отключения проверки на ошибки API, а значения, не выделенные полужирным шрифтом, полностью отключены.

## <a name="nxd_smtp_client_create"></a>nxd_smtp_client_create

Создание экземпляра клиента SMTP.

### <a name="prototype"></a>Прототип

```C
UINT nxd_smtp_client_create(NX_SMTP_CLIENT *client_ptr,
    NX_IP *ip_ptr, NX_PACKET_POOL
    *client_packet_pool_ptr,
    CHAR *username, CHAR *password,
    CHAR *from_address,
    CHAR *client_domain,
    UINT authentication_type, NXD_ADDRESS *server_address,
    UINT port);
```

### <a name="description"></a>Описание

Эта служба создает экземпляр клиента SMTP в указанном экземпляре IP.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления клиентом SMTP.
- **ip_ptr**: указатель на экземпляр IP.
- **packet_pool_ptr**: указатель на пул пакетов клиента.
- **username**: имя пользователя для проверки подлинности, оканчивающееся нулевым символом**.
- **password**: пароль для проверки подлинности, оканчивающийся нулевым символом.
- **from_address**: адрес отправителя, оканчивающийся нулевым символом.
- **client_domain**: доменное имя, заканчивающееся нулевым символом.
- **authentication_type**: тип проверки подлинности. Поддерживаемые типы:
  - NX_SMTP_CLIENT_AUTH_LOGIN
  - NX_SMTP_CLIENT_AUTH_PLAIN
  - NX_SMTP_CLIENT_AUTH_NONE
- **server_address**: указатель на IP-адрес сервера SMTP.
- **server_port**: TCP-порт сервера SMTP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): клиент SMTP успешно создан. Состояние создания сокета TCP
- NX_SMTP_INVALID_PARAM (0xA5): недопустимые входные данные, отличные от указателя.
- NX_IP_ADDRESS_ERROR (0x21): недопустимый тип IP-адреса.
- NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники

Код приложения

### <a name="example"></a>Например, .

```C
/* Create the SMTP Client instance. */
NX_PACKET_POOL client_packet_pool;
NX_IP client_ip;
NX_SMTP_CLIENT demo_client;

#define USERNAME “myusername”
#define PASSWORD “mypassword”
#define FROM_ADDRESS “<myname@mycompany.com>”
#define LOCAL_DOMAIN “mycompany.com”
#define SERVER_PORT 25

/* Define client authentication type as LOGIN. 
    If not specified or unknown the SMTP Client will set it to PLAIN. */
#define CLIENT_AUTHENTICATION_TYPE NX_SMTP_CLIENT_AUTH_LOGIN

NXD_ADDRESS server_ip_address;

#ifdef USE_IPV6
    /* Set up the Server IPv6 address. */
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
    server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    server_ip_address.nxd_ip_address.v6[1] = 0xf101;
    server_ip_address.nxd_ip_address.v6[2] = 0;
    server_ip_address.nxd_ip_address.v6[3] = 0x106;
#else
    server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip_address.nxd_ip_address.v4 = SERVER_IP_ADDRESS;
#endif

status = nxd_smtp_client_create(&demo_client, &client_ip, &client_packet_pool,
    USERNAME, PASSWORD, FROM_ADDRESS,
    LOCAL_DOMAIN, CLIENT_AUTHENTICATION_TYPE,
    &server_ip_address, SERVER_PORT);

/* If an SMTP Client instance was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_smtp_client_delete"></a>nx_smtp_client_delete

Удаление экземпляра клиента SMTP.

### <a name="prototype"></a>Прототип

```C
UINT nx_smtp_client_delete(NX_SMTP_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет созданный ранее экземпляр клиента SMTP.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на экземпляр клиента SMTP.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): клиент успешно удален.
- NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Delete the SMTP Client instance “my_client.” */

NX_SMTP_CLIENT demo_client;

status = nx_smtp_client_delete(&demo_client);

/* If an SMTP Client instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_smtp_mail_send"></a>nx_smtp_mail_send

Создание и отправка почтового элемента SMTP.

### <a name="prototype"></a>Прототип

```C
UINT nx_smtp_mail_send(NX_SMTP_CLIENT *client_ptr,
    CHAR *recipient_address,
    UINT priority, CHAR *subject,
    CHAR *mail_body,
    UINT mail_body_length);
```

### <a name="description"></a>Описание

Эта служба создает и отправляет почтовый элемент SMTP. Клиент SMTP устанавливает TCP-подключение к серверу SMTP и отправляет серию команд SMTP. Если ошибки не обнаружены, он передает почтовое сообщение на сервер. Независимо от того, было ли успешно отправлено сообщение, TCP-подключение разрывается и возвращается состояние, указывающее на результат передачи почты. Приложение может вызывать эту службу для любого количества почтовых сообщений, которые необходимо отправить.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на клиент SMTP.
- **recipient_address**: адрес получателя, оканчивающийся нулевым символом.
- **subject**: текст строки темы, оканчивающийся нулевым символом.
- **priority**: уровень приоритета доставки почты.
- **mail_body**: указатель на почтовое сообщение.
- **mail_body_length**: размер почтового сообщения.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): почта успешно отправлена.
- **NX_SMTP_CLIENT_NOT_INITIALIZED** (0xB2): экземпляр клиента SMTP не инициализирован для состояния сеанса SMTP, соответствующего результату сеанса SMTP.
- NX_PTR_ERROR (0x07): недопустимый параметр указателя.
- NX_SMTP_INVALID_PARAM (0xA5): недопустимые входные данные, отличные от указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```C
/* Create and send a Client mail item. */

#define RECIPIENT_ADDRESS “<your@yourcompany.com>”
#define SUBJECT “NetX Duo SMTP Client Demo”
#define MAIL_BODY "NetX Duo SMTP client is an SMTP client ” \
    “implementation for embedded devices \r\n” \
    "to send email to SMTP servers.\r\n"

status = nx_smtp_mail_send(&demo_client, RECIPIENT_ADDRESS,
    NX_SMTP_MAIL_PRIORITY_NORMAL,
    SUBJECT_LINE, MAIL_BODY,
    sizeof(MAIL_BODY) - 1);

/* Return status being NX_SUCCESS indicates the mail has been
    successfully sent. */
```
