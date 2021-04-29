---
title: Глава 3. Описание служб HTTP
description: В этой главе приведено описание всех служб NetX Web HTTP (перечислены ниже) в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 30168ad5a564b0f4c0a8c999046c5103385f4f90
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815376"
---
# <a name="chapter-3---description-of-http-services"></a>Глава 3. Описание служб HTTP

В этой главе приведено описание всех служб NetX Web HTTP (перечислены ниже) в алфавитном порядке.

> [!NOTE]
> В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, используемым для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

## <a name="http-and-https-client-api"></a>API HTTP- и HTTPS-клиентов

## <a name="nx_web_http_client_connect"></a>nx_web_http_client_connect

Открытие сокета без шифрования на HTTP-сервере для пользовательских запросов.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip,
    UINT server_port, ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTP **без шифрования**.

Данная служба открывает сокет TCP без шифрования для HTTP-сервера, но не отправляет запросы. Для создания запросов используется служба *nx_web_http_client_request_initialize()* , а для отправки — служба *nx_web_http_client_request_send()* . Пользовательские заголовки HTTP можно добавить в запрос с помощью службы *nx_web_http_client_request_header_add()* .

С помощью этой службы приложение может добавить в запрос любое количество пользовательских заголовков. **Это позволяет создавать пользовательские HTTP-запросы, предназначенные для конкретных приложений.**

> [!NOTE]
> Методы nx_web_http_client_ *_start предоставляются для удобства (например, *nx_web_http_client_get_start*()) и управляют созданием запросов и подключением к сокетам. Эти службы можно использовать вместо службы *nx_web_http_client_connect()* и связанных подпрограмм, если в запросах не требуются пользовательские заголовки HTTP.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **server_ip**: IP-адрес удаленного HTTP-сервера.
- **server_port**: порт на удаленном HTTP-сервере (например, 80 для HTTP).
- **wait_option**: определяет, как долго служба будет ожидать операций базовой сети. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сокет TCP успешно подключен.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_WEB_HTTP_NOT_READY (0x3000A): уже выполняется другой запрос.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
NXD_ADDRESS server_ip_addr;

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_connect(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="nx_web_http_client_create"></a>nx_web_http_client_create

Создание экземпляра HTTP-клиента.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_create(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
    ULONG window_size);
```

### <a name="description"></a>Описание

Эта служба создает экземпляр HTTP-клиента в указанном экземпляре IP-адреса. Этот экземпляр клиента можно использовать как для протокола HTTP, так и для протокола HTTPS. Дополнительные сведения о запуске экземпляра HTTP или HTTPS см. в описании служб *nx_web_http_client_connect()* и *nx_web_http_client_secure_connect()* . Также ознакомьтесь с интерфейсами API для служб *nx_web_http_client_get_**, *nx_web_http_client_put_** и *nx_web_http_client_post_**, чтобы узнать, как просто вызывать методы GET, WHERE и POST.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **client_name**: имя экземпляра HTTP-клиента.
- **ip_ptr**: указатель на экземпляр IP.
- **pool_ptr**: указатель на пул пакетов по умолчанию. Обратите внимание, что пакеты в этом пуле должны иметь объем полезных данных, достаточный для работы с полным заголовком ответа. Это определяет параметр *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* в файле *nx_web_http_client.h*.
- **window_size**: размер окна приема сокета TCP клиента.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): HTTP-клиент успешно создан.
- NX_PTR_ERROR (0x16): недопустимый указатель на HTTP, ip_ptr или пул пакетов.
- NX_WEB_HTTP_POOL_ERROR (0x30009): недопустимый размер полезных данных в пуле пакетов.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки.

### <a name="example"></a>Например, .

```C
/* Create the HTTP Client instance "my_client" on "ip_0". */
status = nx_web_http_client_create(&my_client, "my client", &ip_0, &pool_0, 8192);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    created. */
```

## <a name="nx_web_http_client_delete"></a>nx_web_http_client_delete

Удаление экземпляра HTTP-клиента.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_delete(NX_WEB_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет созданный ранее экземпляр HTTP-клиента.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): HTTP-клиент успешно удален.
- NX_PTR_ERROR (0x16): недопустимый указатель на HTTP.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Delete the HTTP Client instance "my_client." */
status = nx_web_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    deleted. */
```

## <a name="nx_web_http_client_delete_start"></a>nx_web_http_client_delete_start

Выполнение HTTP-запроса DELETE без шифрования.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_delete_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTP **без шифрования**.

Эта служба пытается отправить запрос DELETE для ресурса, заданного указателем resource, в созданном ранее экземпляре HTTP-клиента. Если эта подпрограмма вернет значение NX_SUCCESS, то приложение сможет вызвать метод *nx_web_http_client_response_body_get()* , чтобы получить ответ сервера.

Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.

Это нерекомендуемый API. Разработчикам рекомендуется использовать службу *nx_web_http_client_delete_start_extended()* .

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: порт на удаленном HTTP-сервере.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **resource**: указатель на строку URL-адреса запрошенного ресурса.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрос DELETE HTTP-клиента успешно отправлен.
- **NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- **NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start(&my_client, &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_start_extended"></a>nx_web_http_client_delete_start_extended

Выполнение HTTP-запроса DELETE без шифрования.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_delete_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTP **без шифрования**.

Эта служба пытается отправить запрос DELETE для ресурса, заданного указателем resource, в созданном ранее экземпляре HTTP-клиента. Если эта подпрограмма вернет значение NX_SUCCESS, то приложение сможет вызвать метод *nx_web_http_client_response_body_get()* , чтобы получить ответ сервера.

Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.

Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.

Эта служба заменяет *nx_web_http_client_delete_start*(). В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса запрошенного ресурса.
- **resource_length**: длина строки для запрошенного ресурса.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **host_length**: длина строки узла.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **username_length**: длина строки имени пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **password_length**: длина строки пароля для проверки подлинности.
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрос DELETE HTTP-клиента успешно отправлен.
- **NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- **NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_start_extended(&my_client,
    &server_ip_address,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_delete_secure_start"></a>nx_web_http_client_delete_secure_start

Выполнение зашифрованного HTTPS-запроса DELETE.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_delete_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.

Эта служба пытается отправить запрос DELETE для ресурса, заданного указателем resource, в созданном ранее экземпляре HTTP-клиента. Если эта подпрограмма вернет значение NX_SUCCESS, то приложение сможет вызвать метод *nx_web_http_client_response_body_get()* , чтобы получить ответ сервера.

Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется использовать службу *nx_web_http_client_delete_secure_start_extended()* .

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса запрошенного ресурса. Это значение должно заканчиваться нулем.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **tls_setup**: обратный вызов, используемый для настройки конфигурации TLS. Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрос DELETE HTTP-клиента успешно отправлен.
- **NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- **NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_delete_secure_start_extended"></a>nx_web_http_client_delete_secure_start_extended

Выполнение зашифрованного HTTPS-запроса DELETE.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_delete_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.

Эта служба пытается отправить запрос DELETE для ресурса, заданного указателем resource, в созданном ранее экземпляре HTTP-клиента. Если эта подпрограмма вернет значение NX_SUCCESS, то приложение сможет вызвать метод *nx_web_http_client_response_body_get()* , чтобы получить ответ сервера.

Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.

Строки ресурса, узла, имени пользователя и пароля должны завершаться нулем, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.

Эта служба заменяет *nx_web_http_client_delete_secure_start()* . В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса запрошенного ресурса. Это значение должно заканчиваться нулем.
- **resource_length**: длина строки для запрошенного ресурса.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **host_length**: длина строки узла.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **username_length**: длина строки имени пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **password_length**: длина строки пароля для проверки подлинности.
- **tls_setup**: обратный вызов, используемый для настройки конфигурации TLS. Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрос DELETE HTTP-клиента успешно отправлен.
- **NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- **NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.


### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the DELETE operation on the HTTP Client "my_client." */
status = nx_web_http_client_delete_secure_start_extended(&my_client,
    &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the DELETE request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_get_start"></a>nx_web_http_client_get_start

Выполнение HTTP-запроса GET без шифрования.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_get_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTP **без шифрования**.

Эта служба пытается выполнить запрос GET к ресурсу, указанному указателем resource, в созданном ранее экземпляре HTTP-клиента. Если эта подпрограмма возвращает NX_SUCCESS, приложение может выполнить несколько вызовов службы *nx_web_http_client_response_body_get()* , чтобы получить пакеты данных, соответствующих содержимому запрошенного ресурса.

Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется использовать службу *nx_web_http_client_get_start_extended()* .

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса запрошенного ресурса.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сообщение о запуске запроса GET HTTP-клиента успешно отправлено.
- **NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- **NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_start_extended"></a>nx_web_http_client_get_start_extended

Выполнение HTTP-запроса GET без шифрования.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_get_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTP **без шифрования**.

Эта служба пытается выполнить запрос GET к ресурсу, указанному указателем resource, в созданном ранее экземпляре HTTP-клиента. Если эта подпрограмма возвращает NX_SUCCESS, приложение может выполнить несколько вызовов службы *nx_web_http_client_response_body_get()* , чтобы получить пакеты данных, соответствующих содержимому запрошенного ресурса.

Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.

Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.

Эта служба заменяет *nx_web_http_client_get_start()* . В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса запрошенного ресурса.
- **resource_length**: длина строки для запрошенного ресурса.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **host_length**: длина строки узла.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **username_length**: длина строки имени пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **password_length**: длина строки пароля для проверки подлинности.
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сообщение о запуске запроса GET HTTP-клиента успешно отправлено.
- **NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- **NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_start_extended(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    multiple times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start"></a>nx_web_http_client_get_secure_start

Выполнение зашифрованного HTTPS-запроса GET.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_get_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
        NX_SECURE_TLS_SESSION *tls_session),
        ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.

Эта служба пытается выполнить запрос GET к ресурсу, указанному указателем resource, в созданном ранее экземпляре HTTP-клиента. Если эта подпрограмма возвращает NX_SUCCESS, приложение может выполнить несколько вызовов службы *nx_web_http_client_response_body_get()* , чтобы получить пакеты данных, соответствующих содержимому запрошенного ресурса.

Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется использовать службу *nx_web_http_client_get_secure_start_extended()* .

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса запрошенного ресурса.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **tls_setup**: обратный вызов, используемый для настройки конфигурации TLS. Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сообщение о запуске запроса GET HTTP-клиента успешно отправлено.
- **NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- **NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started
    and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to
    retrieve the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_get_secure_start_extended"></a>nx_web_http_client_get_secure_start_extended

Выполнение зашифрованного HTTPS-запроса GET.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_get_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.

Эта служба пытается выполнить запрос GET к ресурсу, указанному указателем resource, в созданном ранее экземпляре HTTP-клиента. Если эта подпрограмма возвращает NX_SUCCESS, приложение может выполнить несколько вызовов службы *nx_web_http_client_response_body_get()* , чтобы получить пакеты данных, соответствующих содержимому запрошенного ресурса.

Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.

Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.

Эта служба заменяет *nx_web_http_client_secure_start()* . В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса запрошенного ресурса.
- **resource_length**: длина строки для запрошенного ресурса.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **host_length**: длина строки узла.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **username_length**: длина строки имени пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **password_length**: длина строки пароля для проверки подлинности.
- **tls_setup**: обратный вызов, используемый для настройки конфигурации TLS. Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сообщение о запуске запроса GET HTTP-клиента успешно отправлено.
- **NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- **NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the GET operation on the HTTP Client "my_client." */
status = nx_web_http_client_get_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM
    is started and is so far successful. The client must now call
    *nx_web_http_client_response_body_get()* multiple times to retrieve
    the content associated with TEST.HTM. */
```

## <a name="nx_web_http_client_head_start"></a>nx_web_http_client_head_start

Выполнение HTTP-запроса HEAD без шифрования.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_head_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTP **без шифрования**.

Эта служба пытается получить метаданные HEAD для ресурса, заданного указателем resource, в созданном ранее экземпляре HTTP-клиента. Если эта подпрограмма вернет значение NX_SUCCESS, то приложение сможет вызвать метод *nx_web_http_client_response_body_get()* , чтобы получить ответ.

Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется использовать службу *nx_web_http_client_head_start_extended()* .

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса запрошенного ресурса.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрос HEAD HTTP-клиента успешно отправлен.
- **NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- **NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_start_extended"></a>nx_web_http_client_head_start_extended

Выполнение HTTP-запроса HEAD без шифрования.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_head_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTP **без шифрования**.

Эта служба пытается получить метаданные HEAD для ресурса, заданного указателем resource, в созданном ранее экземпляре HTTP-клиента. Если эта подпрограмма вернет значение NX_SUCCESS, то приложение сможет вызвать метод *nx_web_http_client_response_body_get()* , чтобы получить ответ.

Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.

Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.

Эта служба заменяет *nx_web_http_client_head_start()* . В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса запрошенного ресурса.
- **resource_length**: длина строки для запрошенного ресурса.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **host_length**: длина строки узла.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **username_length**: длина строки имени пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **password_length**: длина строки пароля для проверки подлинности.
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрос HEAD HTTP-клиента успешно отправлен.
- **NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- **NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the response from the server. */
```

## <a name="nx_web_http_client_head_secure_start"></a>nx_web_http_client_head_secure_start

Выполнение зашифрованного HTTPS-запроса HEAD.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.

Эта служба пытается получить метаданные HEAD для ресурса, заданного указателем resource, в созданном ранее экземпляре HTTP-клиента. Если эта подпрограмма возвращает NX_SUCCESS, приложение может вызвать службу *nx_web_http_client_response_body_get()* , чтобы получить ответ сервера, соответствующий содержимому запрошенного ресурса.

Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется использовать службу *nx_web_http_client_head_secure_start_extended()* .

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса запрошенного ресурса.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **tls_setup**: обратный вызов, используемый для настройки конфигурации TLS. Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрос HEAD HTTP-клиента успешно отправлен.
- **NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- **NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword",
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_head_secure_start_extended"></a>nx_web_http_client_head_secure_start_extended

Выполнение зашифрованного HTTPS-запроса HEAD.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.

Эта служба пытается получить метаданные HEAD для ресурса, заданного указателем resource, в созданном ранее экземпляре HTTP-клиента. Если эта подпрограмма возвращает NX_SUCCESS, приложение может вызвать службу *nx_web_http_client_response_body_get()* , чтобы получить ответ сервера, соответствующий содержимому запрошенного ресурса.

Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.

Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.

Эта служба заменяет *nx_web_http_client_head_secure_start()* . В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса запрошенного ресурса.
- **resource_length**: длина строки для запрошенного ресурса.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **host_length**: длина строки узла.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **username_length**: длина строки имени пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **password_length**: длина строки пароля для проверки подлинности.
- **tls_setup**: обратный вызов, используемый для настройки конфигурации TLS. Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрос HEAD HTTP-клиента успешно отправлен.
- **NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- **NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start the HEAD operation on the HTTP Client "my_client." */
status = nx_web_http_client_head_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1,
    my_tls_setup_function, 1000);

/* If status is NX_SUCCESS, the HEAD request for TEST.HTM is started and is so
    far successful. The client must now call *nx_web_http_client_response_body_get*
    to retrieve the server’s response. */
```

## <a name="nx_web_http_client_request_packet_allocate"></a>nx_web_http_client_request_packet_allocate

Выделение пакета HTTP(S).

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_request_packet_allocate(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба пытается выделить пакет для HTTP(S)-клиента.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **packet_ptr**: указатель на выделенный пакет.
- **wait_option**: определяет время ожидания в тактах, если в пуле пакетов нет доступных пакетов. Параметры ожидания определяются следующим образом:
  - **NX_NO_WAIT** (0x00000000);
  - **NX_WAIT_FOREVER** (0xFFFFFFFF);
  - **значение времени ожидания в тактах** (0x00000001–0xFFFFFFFE).

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): пакет выделен успешно.
- **NX_NO_PACKET** (0x01): нет доступных пакетов.
- **NX_WAIT_ABORTED** (0x1A): запрошенная приостановка прервана вызовом *tx_thread_wait_abort*.
- **NX_INVALID_PARAMETERS** (0x4D): размер пакета не поддерживается протоколом.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Allocate a packet for HTTP(S) Client and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_client_request_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_client_post_start"></a>nx_web_http_client_post_start

Выполнение HTTP-запроса POST.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_post_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host,
    CHAR *username, CHAR *password,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTP **без шифрования**.

Эта служба пытается отправить запрос POST с указанным ресурсом на HTTP-сервер по указанному IP-адресу и порту. Если эта подпрограмма выполнена успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_web_http_client_put_packet*, чтобы отправить содержимое ресурса на HTTP-сервер.

Обратите внимание, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется использовать службу *nx_web_http_client_post_start_extended()* .

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: TCP-порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса для ресурса, отправляемого на сервер.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **total_bytes**: общее число отправляемых байтов ресурса. Обратите внимание на то, что совокупная длина всех пакетов, отправленных последующими вызовами *nx_web_http_client_put_packet()* , должна быть равна этому значению.
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрос POST успешно отправлен.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012): слишком длинное имя пользователя для буфера.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_SIZE_ERROR (0x09): недопустимый общий размер ресурса.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_start_extended"></a>nx_web_http_client_post_start_extended

Выполнение HTTP-запроса POST.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_post_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTP **без шифрования**.

Эта служба пытается отправить запрос POST с указанным ресурсом на HTTP-сервер по указанному IP-адресу и порту. Если эта подпрограмма выполнена успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_web_http_client_put_packet*, чтобы отправить содержимое ресурса на HTTP-сервер.

Обратите внимание, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.

Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.

Эта служба заменяет *nx_web_http_client_post_start()* . В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: TCP-порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса запрошенного ресурса.
- **resource_length**: длина строки для запрошенного ресурса.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **host_length**: длина строки узла.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **username_length**: длина строки имени пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **password_length**: длина строки пароля для проверки подлинности.
- **total_bytes**: общее число отправляемых байтов ресурса. Обратите внимание на то, что совокупная длина всех пакетов, отправленных последующими вызовами *nx_web_http_client_put_packet()* , должна быть равна этому значению.
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрос POST успешно отправлен.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012): слишком длинное имя пользователя для буфера.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_SIZE_ERROR (0x09): недопустимый общий размер ресурса.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

/* Start an HTTP POST to post the 20-byte resource "/TEST.HTM" to the HTTP Server
    at IP address 1.2.3.5. */
status = nx_web_http_client_post_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start"></a>nx_web_http_client_post_secure_start

Выполнение зашифрованного HTTPS-запроса POST.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_post_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.

Эта служба пытается отправить запрос POST с указанным ресурсом на HTTPS-сервер по указанному IP-адресу и порту. Если эта подпрограмма выполнена успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_web_http_client_put_packet()* , чтобы отправить содержимое ресурса на HTTP-сервер.

Обратите внимание, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется использовать службу *nx_web_http_client_post_secure_start_extended()* .

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: TCP-порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса для ресурса, отправляемого на сервер.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **total_bytes**: общее число отправляемых байтов ресурса. Обратите внимание на то, что совокупная длина всех пакетов, отправленных последующими вызовами *nx_web_http_client_put_packet()* , должна быть равна этому значению.
- **tls_setup**: обратный вызов, используемый для настройки конфигурации TLS. Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрос POST успешно отправлен.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012): слишком длинное имя пользователя для буфера.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_SIZE_ERROR (0x09): недопустимый общий размер ресурса.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_post_secure_start_extended"></a>nx_web_http_client_delete_secure_start_extended

Выполнение зашифрованного HTTPS-запроса POST.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_post_secure_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.

Эта служба пытается отправить запрос POST с указанным ресурсом на HTTPS-сервер по указанному IP-адресу и порту. Если эта подпрограмма выполнена успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_web_http_client_put_packet()* , чтобы отправить содержимое ресурса на HTTP-сервер.

Обратите внимание, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.

Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.

Эта служба заменяет *nx_web_http_client_post_secure_start()* . В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: TCP-порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса запрошенного ресурса.
- **resource_length**: длина строки для запрошенного ресурса.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **host_length**: длина строки узла.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **username_length**: длина строки имени пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **password_length**: длина строки пароля для проверки подлинности.
- **total_bytes**: общее число отправляемых байтов ресурса. Обратите внимание на то, что совокупная длина всех пакетов, отправленных последующими вызовами *nx_web_http_client_put_packet()* , должна быть равна этому значению.
- **tls_setup**: обратный вызов, используемый для настройки конфигурации TLS. Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрос POST успешно отправлен.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012): слишком длинное имя пользователя для буфера.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_SIZE_ERROR (0x09): недопустимый общий размер ресурса.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the POST operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start"></a>nx_web_http_client_put_start

Выполнение HTTP-запроса PUT.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_put_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTP **без шифрования**.

Эта служба пытается отправить запрос PUT с указанным ресурсом на HTTP-сервер по указанному IP-адресу и порту. Если эта подпрограмма выполнена успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_web_http_client_put_packet()* , чтобы отправить содержимое ресурса на HTTP-сервер.

Обратите внимание, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется использовать службу *nx_web_http_client_put_start_extended()* .

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: TCP-порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса для ресурса, отправляемого на сервер.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **total_bytes**: общее число отправляемых байтов ресурса. Обратите внимание на то, что совокупная длина всех пакетов, отправленных последующими вызовами *nx_web_http_client_put_packet()* , должна быть равна этому значению.
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрос PUT успешно отправлен.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012): слишком длинное имя пользователя для буфера.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_SIZE_ERROR (0x09): недопустимый общий размер ресурса.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start(&my_client, &server_ip_addr,
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_start_extended"></a>nx_web_http_client_put_start_extended

Выполнение HTTP-запроса PUT.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_put_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTP **без шифрования**.

Эта служба пытается отправить запрос PUT с указанным ресурсом на HTTP-сервер по указанному IP-адресу и порту. Если эта подпрограмма выполнена успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_web_http_client_put_packet()* , чтобы отправить содержимое ресурса на HTTP-сервер.

Обратите внимание, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.

Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.

Эта служба заменяет *nx_web_http_client_put_start()* . В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: TCP-порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса запрошенного ресурса.
- **resource_length**: длина строки для запрошенного ресурса.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **host_length**: длина строки узла.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **username_length**: длина строки имени пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **password_length**: длина строки пароля для проверки подлинности.
- **total_bytes**: общее число отправляемых байтов ресурса. Обратите внимание на то, что совокупная длина всех пакетов, отправленных последующими вызовами *nx_web_http_client_put_packet()* , должна быть равна этому значению.
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрос PUT успешно отправлен.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012): слишком длинное имя пользователя для буфера.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_SIZE_ERROR (0x09): недопустимый общий размер ресурса.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTP Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start"></a>nx_web_http_client_put_secure_start

Выполнение зашифрованного HTTPS-запроса PUT.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.

Эта служба пытается отправить запрос PUT с указанным ресурсом на HTTPS-сервер по указанному IP-адресу и порту. Если эта подпрограмма выполнена успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_web_http_client_put_packet()* , чтобы отправить содержимое ресурса на HTTP-сервер.

Обратите внимание, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется использовать службу *nx_web_http_client_put_secure_start_extended()* .

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: TCP-порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса для ресурса, отправляемого на сервер.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **total_bytes**: общее число отправляемых байтов ресурса. Обратите внимание на то, что совокупная длина всех пакетов, отправленных последующими вызовами *nx_web_http_client_put_packet()* , должна быть равна этому значению.
- **tls_setup**: обратный вызов, используемый для настройки конфигурации TLS. Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрос PUT успешно отправлен.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012): слишком длинное имя пользователя для буфера.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_SIZE_ERROR (0x09): недопустимый общий размер ресурса.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, "/TEST.HTM",
    "host.com", "myname", "mypassword", 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_secure_start_extended"></a>nx_web_http_client_put_secure_start_extended

Выполнение зашифрованного HTTPS-запроса PUT.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_put_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length, ULONG total_bytes,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.

Эта служба пытается отправить запрос PUT с указанным ресурсом на HTTPS-сервер по указанному IP-адресу и порту. Если эта подпрограмма выполнена успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_web_http_client_put_packet()* , чтобы отправить содержимое ресурса на HTTP-сервер.

Обратите внимание, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.

Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.

Эта служба заменяет *nx_web_http_client_put_secure_start()* . В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **ip_address**: IP-адрес HTTP-сервера.
- **server_port**: TCP-порт на удаленном HTTP-сервере.
- **resource**: указатель на строку URL-адреса запрошенного ресурса.
- **resource_length**: длина строки для запрошенного ресурса.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **host_length**: длина строки узла.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **username_length**: длина строки имени пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **password_length**: длина строки пароля для проверки подлинности.
- **total_bytes**: общее число отправляемых байтов ресурса. Обратите внимание на то, что совокупная длина всех пакетов, отправленных последующими вызовами *nx_web_http_client_put_packet()* , должна быть равна этому значению.
- **tls_setup**: обратный вызов, используемый для настройки конфигурации TLS. Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрос PUT успешно отправлен.
- **NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012): слишком длинное имя пользователя для буфера.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_SIZE_ERROR (0x09): недопустимый общий размер ресурса.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Start an HTTP PUT to place the 20-byte resource "/TEST.HTM" on the HTTPS Server
    at IP address 1.2.3.5. */

/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

status = nx_web_http_client_put_secure_start_extended(&my_client,
    &server_ip_addr, NX_WEB_HTTPS_SERVER_PORT,
    "/TEST.HTM", sizeof("/TEST.HTM") – 1,
    "host.com", sizeof("host.com") – 1,
    "myname", sizeof("myname") – 1,
    "mypassword", sizeof("mypassword") – 1, 20,
    tls_setup, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
    started. */
```

## <a name="nx_web_http_client_put_packet"></a>nx_web_http_client_put_packet

Отправка следующего пакета данных ресурса.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_put_packet(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба пытается отправить следующий пакет содержимого ресурса на HTTP-сервер для операций PUT и POST. Обратите внимание на то, что эту подпрограмму следует вызывать повторно до тех пор, пока совокупная длина отправленных пакетов не будет равна значению total_bytes, указанному в предшествовавшем вызове службы *nx_web_http_client_put_start()* или *nx_web_http_client_post_start()* (или их соответствующей безопасной версии).

Эта служба также проверяет ответ сервера на случай, если возникла проблема при установлении подключения HTTP (или HTTPS).

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **packet_ptr**: указатель на следующее содержимое ресурса, отправляемого на HTTP-сервер.
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): пакет HTTP-клиента успешно отправлен.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.
- **NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E): получен код ошибки сервера**.
- **NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D): недопустимая длина пакета.
- **NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.
- **NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F): сервер отвечает до завершения запроса PUT.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_INVALID_PACKET (0x12): слишком маленький пакет для заголовка TCP.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Send a 20-byte packet representing the content of the resource
    "/TEST.HTM" to the HTTP Server. */

status = nx_web_http_client_put_packet(&client_ptr, packet_ptr, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
    successfully been sent. */
```

## <a name="nx_web_http_client_request_chunked_set"></a>nx_web_http_client_request_chunked_set

Настройка поблочной передачи для HTTP(S)-запроса.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_request_chunked_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Описание

Эта служба использует поблочное кодирование для передачи пользовательских HTTP(S)-запросов на сервер, указанный в вызове службы *nx_web_http_client_connect()* или *nx_web_http_client_secure_connect()* , который ранее установил подключение через сокет к удаленному узлу.

> [!NOTE]
> Если приложение использует поблочное кодирование для передачи пакета данных запроса, то оно должно вызвать эту службу после вызова службы *nx_web_http_client_request_packet_allocate()* и перед вызовом службы *nx_web_http_client_reqeust_packet_send()* .

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **chunk_size**: размер блока данных в октетах.
- **packet_ptr**: указатель на пакет данных HTTP(S)-запроса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): режим поблочной передачи успешно задан.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTPS server. */

nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT, "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_TRUE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_client_request_chunked_set(&my_client, 128, my_packet);

/* At this point, user can fill the data into my_packet. *./
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
nx_web_http_client_request_packet_send(&my_client, my_packet,
    0, NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_header_add"></a>nx_web_http_client_request_header_add

Добавление пользовательского заголовка в пользовательский HTTP-запрос.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_request_header_add(
    NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT name_length,
    CHAR *field_value, UINT value_length,
    UINT wait_option);
```

### <a name="description"></a>Описание

Эта служба добавляет пользовательский заголовок (в виде имени поля и значения) в пользовательский HTTP-запрос, созданный с помощью службы *nx_web_http_client_request_initialize()* .

С помощью этой службы приложение может добавить в запрос любое количество пользовательских заголовков. **Это позволяет создавать пользовательские HTTP-запросы, предназначенные для конкретных приложений.**

> [!NOTE]
> Методы nx_web_http_client_\*_start предоставляются для удобства. Во всех этих функциях данная подпрограмма используется (как и служба *nx_web_http_client_request_initialize())* для создания и отправки HTTP-запросов.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **field_name**: строка имени поля (например, "Content-Type").
- **name_length**: длина строки имени поля в байтах.
- **field_value**: строка значения поля (например, "application/octet-stream").
- **value_length**: длина строки значения в байтах.
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): заголовок успешно добавлен в запрос.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */

nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server
    by repeatedly calling *nx_web_http_client_response_body_get()*
    until the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize"></a>nx_web_http_client_request_initialize

Инициализация пользовательского HTTP-запроса.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a>Описание

Эта служба создает пользовательский HTTP-запрос и связывает его с экземпляром HTTP-клиента. В отличие от более простой службы *nx_web_http_client_get_start()* (наряду с методами PUT, POST и связанными защищенными версиями этих API), пользовательский запрос не отправляется, пока не вызвана служба *nx_web_http_client_request_send()* .

Использование этой службы позволяет приложению добавить любое количество пользовательских заголовков в запрос с помощью службы ***nx_web_http_client_request_header_add()***. Это позволяет создавать пользовательские HTTP-запросы, предназначенные для конкретных приложений.

> [!NOTE]
> Методы nx_web_http_client_\*_start предоставляются для удобства. Во всех этих функциях данная подпрограмма используется (как и служба *nx_web_http_client_request_send())* для создания и отправки HTTP-запросов.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется использовать службу *nx_web_http_client_request_initialize_extended()* .

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **method**: используемый метод HTTP-запроса. Параметры определяются следующим образом:
  - **NX_WEB_HTTP_METHOD_NONE (0x0)**
  - **NX_WEB_HTTP_METHOD_GET (0x1)**
  - **NX_WEB_HTTP_METHOD_PUT (0x2)**
  - **NX_WEB_HTTP_METHOD_POST (0x3)**
  - **NX_WEB_HTTP_METHOD_DELETE (0x4)**
  - **NX_WEB_HTTP_METHOD_HEAD (0x5)**
- **resource**: имя передаваемого ресурса.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **input_size**: размер входных данных для операций PUT и POST. Для других операций следует передавать 0.
- **transfer_encoding_trunked**: зарезервированный параметр для будущей поддержки транкинговой передачи.
- **username**: имя пользователя для защищенных ресурсов.
- **password**: пароль для защищенных ресурсов.
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00): запрос успешно инициализирован.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_WEB_HTTP_METHOD_ERROR (0x30014): отсутствует необходимая информация (например, input_size для операции PUT или POST).

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */

status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. *./
get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize_extended"></a>nx_web_http_client_request_initialize_extended

Инициализация пользовательского HTTP-запроса.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a>Описание

Эта служба создает пользовательский HTTP-запрос и связывает его с экземпляром HTTP-клиента. В отличие от более простой службы *nx_web_http_client_get_start()* (наряду с методами PUT, POST и связанными защищенными версиями этих API), пользовательский запрос не отправляется, пока не вызвана служба *nx_web_http_client_request_send()* .

Использование этой службы позволяет приложению добавить любое количество пользовательских заголовков в запрос с помощью службы ***nx_web_http_client_request_header_add()***. Это позволяет создавать пользовательские HTTP-запросы, предназначенные для конкретных приложений.

> [!NOTE]
> Методы nx_web_http_client_\*_start предоставляются для удобства. Во всех этих функциях данная подпрограмма используется (как и служба *nx_web_http_client_request_send())* для создания и отправки HTTP-запросов.

Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.

Эта служба заменяет *nx_web_http_client_request_initialize()* . В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **method**: используемый метод HTTP-запроса. Параметры определяются следующим образом:
  - **NX_WEB_HTTP_METHOD_NONE (0x0)**
  - **NX_WEB_HTTP_METHOD_GET (0x1)**
  - **NX_WEB_HTTP_METHOD_PUT (0x2)**
  - **NX_WEB_HTTP_METHOD_POST (0x3)**
  - **NX_WEB_HTTP_METHOD_DELETE (0x4)**
  - **NX_WEB_HTTP_METHOD_HEAD (0x5)**
- **resource**: имя передаваемого ресурса.
- **resource_length**: длина строки для запрошенного ресурса.
- **host**: строка доменного имени сервера, оканчивающаяся нулевым символом. Эта строка передается в поле заголовка узла HTTP. Строка узла не может иметь значение NULL.
- **host_length**: длина строки узла.
- **input_size**: размер входных данных для операций PUT и POST. Для других операций следует передавать 0.
- **transfer_encoding_trunked**: зарезервированный параметр для будущей поддержки транкинговой передачи.
- **username**: указатель на необязательное имя пользователя для проверки подлинности.
- **username_length**: длина строки имени пользователя для проверки подлинности.
- **password**: указатель на необязательный пароль для проверки подлинности.
- **password_length**: длина строки пароля для проверки подлинности.
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00): запрос успешно инициализирован.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_WEB_HTTP_METHOD_ERROR (0x30014): отсутствует необходимая информация (например, input_size для операции PUT или POST).

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize_extended(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "test.txt ", sizeof("test.txt ") – 1,
    "host.com", sizeof("host.com") – 1,
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    0,
    NX_NULL, /* password */
    0,
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);


/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. *./
get_status = NX_SUCCESS;
while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_packet_send"></a>nx_web_http_client_request_packet_send

Отправка удаленному серверу пакета данных HTTP(S)-запроса.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_request_packet_send(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, UINT more_date,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба отправляет пакет данных пользовательского HTTP(S)-запроса, созданный с помощью службы *nx_web_http_client_request_packet_allocate()* , на сервер, указанный в вызове службы *nx_web_http_client_connect()* или *nx_web_http_client_secure_connect(* ), который ранее установил подключение через сокет к удаленному узлу.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **packet_ptr**: указатель на пакет данных HTTP(S)-запроса.
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): пакет данных запроса успешно отправлен.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ",
    128, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the PUT operation. */
nx_web_http_client_request_send(&my_client, 1000);

/* Create a new data packet request on the HTTP(S) client instance. */
nx_web_http_client_request_packet_allocate(&my_client,
    &my_packet,
    NX_WAIT_FOREVER);

/* At this point, user can fill the data into my_packet. *./
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
status = nx_web_http_client_request_packet_send(&my_client,
    my_packet,
    0,
    NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_send"></a>nx_web_http_client_request_send

Отправка пользовательского HTTP-запроса.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_request_send(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT wait_option);
```

### <a name="description"></a>Описание

Эта служба отправляет пользовательский HTTP-запрос, созданный с помощью службы *nx_web_http_client_request_initialize()* , на сервер, указанный в вызове службы *nx_web_http_client_connect()* или *nx_web_http_client_secure_connect(* ), который ранее установил подключение через сокет к удаленному узлу.

Использование этой службы позволяет приложению добавить любое количество пользовательских заголовков в запрос с помощью службы ***nx_web_http_client_request_header_add()***. Это позволяет создавать пользовательские HTTP-запросы, предназначенные для конкретных приложений.

> [!NOTE]
> Методы nx_web_http_client_\*_start предоставляются для удобства. Во всех этих функциях данная подпрограмма используется (как и служба *nx_web_http_client_request_initialize())* для создания и отправки HTTP-запросов.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): запрос успешно отправлен.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by
    repeatedly calling *nx_web_http_client_response_body_get* until
    the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_response_body_get"></a>nx_web_http_client_response_body_get

Получение следующего пакета данных ресурса.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_response_body_get(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr, ULONG
    wait_option);
```

### <a name="description"></a>Описание

Эта служба извлекает следующий пакет содержимого ресурса, запрошенного предшествовавшим вызовом службы *nx_web_http_client_get_start()* или *nx_web_http_client_get_secure_start()* . Последовательные вызовы этой подпрограммы должны выполняться до получения состояния возврата NX_WEB_HTTP_GET_DONE.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **packet_ptr**: назначение для указателя пакета, содержащего частичное содержимое ресурса.
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): пакет HTTP-клиента успешно отправлен.
- **NX_WEB_HTTP_GET_DONE** (0x3000C): пакет HTTP-клиента получен.
- **NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не в режиме получения.
- **NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D): недопустимая длина пакета.
- **NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A): код состояния HTTP "100 Continue" (100: продолжение).
- **NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B): код состояния HTTP "101 Switching Protocols" (101: переключение протоколов).
- **NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C): код состояния HTTP "201 Created" (201: создано).
- **NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001C): код состояния HTTP "202 Accepted" (202: принято).
- **NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E): код состояния HTTP "203 Non-Authoritative Information" (203: не заслуживающая доверия информация).
- **NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F): код состояния HTTP "204 No Content" (204: содержимое отсутствует).
- **NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020): код состояния HTTP "205 Reset Content" (205: сброс содержимого).
- **NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021): код состояния HTTP "206 Partial Content" (206: неполное содержимое).
- **NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022): код состояния HTTP "300 Multiple Choices" (300: несколько вариантов).
- **NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023): код состояния HTTP "301 Moved Permanently" (301: окончательно перемещено).
- **NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024): код состояния HTTP "302 Found" (302: найдено).
- **NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025): код состояния HTTP "303 See Other" (303: перенаправление).
- **NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026): код состояния HTTP "304 Not Modified" (304: не изменено).
- **NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027): код состояния HTTP "305 Use Proxy" (305: использование прокси-сервера).
- **NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028): код состояния HTTP "307 Temporary Redirect" (307: временное перенаправление).
- **NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029): код состояния HTTP "400 Bad Request" (400: недействительный запрос).
- **NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A): код состояния HTTP "401 Unauthorized" (401: не авторизовано).
- **NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B): код состояния HTTP "402 Payment Required" (402: требуется оплата).
- **NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C): код состояния HTTP "403 Forbidden" (403: запрещено).
- **NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D): код состояния HTTP "404 Not Found" (404: не найдено).
- **NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E): код состояния HTTP "405 Method Not Allowed" (405: метод запрещен).
- **NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F): код состояния HTTP "406 Not Acceptable" (406: неприемлемо).
- **NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030): код состояния HTTP "407 Proxy Authentication Required" (407: требуется проверка подлинности прокси-сервера).
- **NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031): код состояния HTTP "408 Request Time-out" (408: превышено время ожидания запроса).
- **NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032): код состояния HTTP "409 Conflict" (409: конфликт).
- **NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033): код состояния HTTP "410 Gone" (401: отсутствует).
- **NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034): код состояния HTTP "411 Length Required" (411: требуется указать длину).
- **NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035): код состояния HTTP "412 Precondition Failed" (412: необходимое условие не выполнено).
- **NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036): код состояния HTTP "413 Request Entity Too Large" (413: слишком большой объект запроса).
- **NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037): код состояния HTTP "414 Request URL Too Large" (414: слишком длинный URL-адрес запроса).
- **NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038): код состояния HTTP "415 Unsupported Media Type" (415: неподдерживаемый тип носителя).
- **NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039): код состояния HTTP "416 Requested range not satisfiable" (416: запрошенный диапазон невыполним).
- **NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A): код состояния HTTP "417 Expectation Failed" (417: ошибка ожидания).
- **NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B): код состояния HTTP "500 Internal Server Error" (500: внутренняя ошибка сервера).
- **NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C): код состояния HTTP "501 Not Implemented" (501: не реализовано).
- **NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D): код состояния HTTP "502 Bad Gateway" (502: недопустимый шлюз).
- **NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E): код состояния HTTP "503 Service Unavailable" (503: служба недоступна).
- **NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F): код состояния HTTP "504 Gateway Time-out" (504: превышено время ожидания шлюза).
- **NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040): код состояния HTTP "505 HTTP Version not supported" (505: версия протокола HTTP не поддерживается).
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Get the next packet of resource content on the HTTP Client "my_client."
    Note that the nx_web_http_client_get_start() routine must have been called
    previously. */
status = nx_web_http_client_response_body_get(&my_client, &next_packet, 1000);

/* If status is NX_SUCCESS, the next packet of content is pointed to
    by "next_packet". */
```

## <a name="nx_web_http_client_response_header_callback_set"></a>nx_web_http_client_response_header_callback_set

Задание обратного вызова для выполнения при обработке заголовков HTTP.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_response_header_callback_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    VOID (*callback_function)(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT field_name_length,
    CHAR *field_value, UINT field_value_length));
```

### <a name="description"></a>Описание

Эта служба назначает обратный вызов, который будет вызываться каждый раз, когда клиент NetX Web HTTP обрабатывает заголовок HTTP во входящем ответе от удаленного HTTP-сервера. При обработке обратный вызов выполняется один раз для каждого заголовка в ответе. Обратный вызов позволяет приложению HTTP-клиента получить доступ к каждому из заголовков в ответе HTTP-сервера, чтобы выполнять все необходимые действия, помимо базовой обработки, выполняемой клиентом NetX Web HTTP.

### <a name="input-parameters"></a>Входные параметры

**client_ptr**: указатель на блок управления HTTP-клиентом.

**callback_function**: функция обратного вызова, вызываемая во время обработки заголовка ответа. Обратный вызов выполняется со строковыми значениями имени и значения поля (и их длиной). Например, заголовок "Content-Length: 100" приведет к вызову функции со строкой "Content-Length" для параметра *field_name* и строкой "100" для параметра *field_value*.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): функция обратного вызова успешно назначена.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Setup a callback to print out header information as it is processed. */
VOID http_response_callback(NX_WEB_HTTP_CLIENT *client_ptr, CHAR *field_name,
    UINT field_name_length, CHAR *field_value,
    UINT field_value_length)
{
    CHAR name[100];
    CHAR value[100];
    memset(name, 0, sizeof(name));

    memset(value, 0, sizeof(value));

    strncpy(name, field_name, field_name_length);
    strncpy(value, field_value, field_value_length);

    printf("Received header: \n");
    printf("\tField name: %s (%d bytes)\n", name, field_name_length);
    printf("\tValue: %s (%d bytes)\n\n", value, field_value_length);
}

/* Assign the callback to the HTTP client instance. */
nx_web_http_client_response_header_callback_set(&my_client,
    http_response_callback);

/* Start a GET operation to get a response from the HTTP server. */
status = nx_web_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTP_SERVER_PORT, "/TEST.HTM",
    "myname", "mypassword", 1000);

/* When the HTTP server returns a response to the GET request, NetX Web HTTP
    Client will invoke the http_response_callback function for each header
    processed in the HTTP response. */
```

## <a name="nx_web_http_client_secure_connect"></a>nx_web_http_client_secure_connect

Открытие сеанса TLS с HTTPS-сервером для обработки пользовательских запросов.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_client_secure_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls),
    ULONG wait_option);
```

### <a name="description"></a>Описание

Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.

Эта служба открывает защищенный сеанс TLS с HTTPS-сервером, но не отправляет запросы. Для создания запросов используется служба *nx_web_http_client_request_initialize()* , а для отправки — служба *nx_web_http_client_request_send()* . Пользовательские заголовки HTTP можно добавить в запрос с помощью службы *nx_web_http_client_request_header_add()* .

С помощью этой службы приложение может добавить в запрос любое количество пользовательских заголовков. **Это позволяет создавать пользовательские HTTP-запросы, предназначенные для конкретных приложений.**

> [!NOTE]
> Методы nx_web_http_client_\*_start предоставляются для удобства. Во всех этих функциях данная подпрограмма используется (как и служба *nx_web_http_client_request_initialize())* для создания и отправки HTTP-запросов.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **server_ip**: IP-адрес удаленного HTTPS-сервера.
- **server_port**: порт на удаленном HTTPS-сервере (например, 443 для HTTPS).
- **tls_setup**: обратный вызов, используемый для настройки конфигурации TLS. Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).
- **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): сеанс TCP успешно подключен.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_WEB_HTTP_NOT_READY (0x3000A): уже выполняется другой запрос.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Connect to a remote HTTPS server. */
/* Connect to a remote HTTP server. */
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_addr.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,5);

nx_web_http_client_secure_connect(&my_client, &server_ip_addr,
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Add a custom header to the GET request we just created. */
status = nx_web_http_client_request_header_add(&my_client, "Server", 6,
    "NetX Web HTTPS Server", 21, NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by repeatedly
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. *./

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="http-and-https-server-api"></a>Интерфейсы API HTTP- и HTTPS-сервера

## <a name="nx_web_http_server_cache_info_callback_set"></a>nx_web_http_server_cache_info_callback_set

Задание обратного вызова для получения максимального возраста и даты URL-адреса.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)(CHAR *resource,
    UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *date));
```

### <a name="description"></a>Описание

Эта служба задает службу обратного вызова, вызываемую для получения максимального возраста и даты последнего изменения указанного ресурса.

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на блок управления HTTP-сервером.
- **cache_info_get**: указатель на обратный вызов.
- **max_age**: указатель на максимальный возраст ресурса.
- **data**: указатель на возвращенную дату последнего изменения.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): обратный вызов успешно задан.
- **NX_PTR_ERROR** (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Инициализация

### <a name="example"></a>Например, .

```C
NX_WEB_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_web_http_server_create and before the HTTP
    server is set by nx_web_http_server_start(), set the cache info callback: */
status = nx_web_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_web_http_server_callback_data_send"></a>nx_web_http_server_callback_data_send

Отправка данных из функции обратного вызова.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_callback_data_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID *data_ptr, ULONG data_length);
```

### <a name="description"></a>Описание

Эта служба отправляет данные в предоставленном пакете из подпрограммы обратного вызова приложения. Обычно она используется для отправки динамических данных, связанных с запросами GET или POST. Обратите внимание, что, если используется эта функция, то подпрограмма обратного вызова отвечает за отправку всего ответа в правильном формате. Кроме того, подпрограмма обратного вызова должна возвращать состояние NX_WEB_HTTP_CALLBACK_COMPLETED.

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на блок управления HTTP-сервером.
- **data_ptr**: указатель на данные для отправки.
- **data_length**: число отправляемых байтов.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): данные сервера успешно отправлены.
- **NX_PTR_ERROR** (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
            contents directly. */
        nx_web_http_server_callback_data_send(server_ptr,
            "HTTP/1.0 200 \r\nContent-Length:" "103\r\nContent-Type: text/html\r\n\r\n",
            63);

        nx_web_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX"
            "HTTP Test </TITLE></HEAD>\r\n"
            :<BODY>\r\n<H1>NetX Test Page"
            "</H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_generate_response_header"></a>nx_web_http_server_callback_generate_response_header

Создание заголовка ответа в функции обратного вызова.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_callback_generate_response_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT content_length,
    CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a>Описание

Эта служба используется в подпрограмме обратного вызова HTTP(S)-сервера (определяется приложением) для создания заголовка ответа HTTP. Подпрограмма обратного вызова сервера вызывается, когда HTTP-сервер отвечает на запросы GET, PUT и DELETE клиента, требующие ответа HTTP. Эта функция принимает из приложения данные ответа и создает соответствующий заголовок ответа. Дополнительные сведения о подпрограмме обратного вызова для запросов сервера см. в описании службы *nx_web_http_server_create()* .

Это нерекомендуемый API. Разработчикам рекомендуется использовать службу *nx_web_http_server_callback_generate_response_header_extended()* .

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на блок управления HTTP-сервером.
- **packet_pptr**: указатель на указатель пакета, выделенного для сообщения.
- **status_code**: указывает на состояние ресурса. Примеры:
  - **NX_WEB_HTTP_STATUS_OK**
  - **NX_WEB_HTTP_STATUS_MODIFIED**
  - **NX_WEB_HTTP_STATUS_INTERNAL_ERROR**
- **content_length**: размер содержимого в байтах.
- **content_type**: тип HTTP, например "text/plain".
- **additional_header**: указатель на дополнительный текст заголовка.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): заголовок HTML успешно создан.
- **NX_PTR_ERROR** (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback registered
    with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        length, temp_string, NX_NULL);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}
```

## <a name="nx_web_http_server_callback_generate_response_header_extended"></a>nx_web_http_server_callback_generate_response_header_extended

Создание заголовка ответа в функции обратного вызова.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_callback_generate_response_header_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT status_code_length,
    UINT content_length, CHAR *content_type,
    UINT content_type_length,
    CHAR* additional_header,
    UINT additional_header_length);
```

### <a name="description"></a>Описание

Эта служба используется в подпрограмме обратного вызова HTTP(S)-сервера (определяется приложением) для создания заголовка ответа HTTP. Подпрограмма обратного вызова сервера вызывается, когда HTTP-сервер отвечает на запросы GET, PUT и DELETE клиента, требующие ответа HTTP. Эта функция принимает из приложения данные ответа и создает соответствующий заголовок ответа. Дополнительные сведения о подпрограмме обратного вызова для запросов сервера см. в описании службы *nx_web_http_server_create()* .

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на блок управления HTTP-сервером.
- **packet_pptr**: указатель на указатель пакета, выделенного для сообщения.
- **status_code**: указывает на состояние ресурса. Примеры:
  - **NX_WEB_HTTP_STATUS_OK**
  - **NX_WEB_HTTP_STATUS_MODIFIED**
  - **NX_WEB_HTTP_STATUS_INTERNAL_ERROR**
- **status_code**: длина строки кода состояния.
- **content_length**: размер содержимого в байтах.
- **content_type**: тип HTTP, например "text/plain".
- **content_type_length**: длина строки типа содержимого.
- **additional_header**: указатель на дополнительный текст заголовка.
- **additional_header_length**: длина дополнительного текста заголовка.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): заголовок HTML успешно создан.
- **NX_PTR_ERROR** (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
CHAR demotestbuffer[] = "<html>> r\n\r\n<head>> r\n\r\n<title>Main \
    Window</title>> r\n</head>> r\n\r\n<body>Test message\r\n \ </body>> r\n</html>> r\n";

/* my_request_notify* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create*,
    creates a response to the received Client request. */

UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET *resp_packet_ptr;
    ULONG string_length;
    CHAR temp_string[30];
    ULONG length = 0;
    length = strlen(&demotestbuffer[0]);

    /* Derive the client request type from the client request. */
    nx_web_http_server_type_extract(server_ptr,
        server_ptr -> nx_web_http_server_request_resource,
        temp_string, sizeof(temp_string), &string_length);

    /* Null terminate the string. */
    temp_string[string_length] = 0;

    /* Now build a response header with server status is OK and no additional header info. */
    status = nx_web_http_server_callback_generate_response_header_extended(http_server_ptr,
        &resp_packet_ptr, NX_WEB_HTTP_STATUS_OK,
        sizeof(NX_WEB_HTTP_STATUS_OK) – 1,
        length, temp_string, string_length NX_NULL, 0);

    /* If status is NX_SUCCESS, the header was successfully appended. */

    /* Now add data to the packet. */
    status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
        strlen(&demotestbuffer[0]), server_ptr >>
        nx_web_http_server_packet_pool_ptr, NX_WAIT_FOREVER);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Now send the packet! */
    status = nx_web_http_server_callback_packet_send(
        &(server_ptr -> nx_web_http_server_socket),
        resp_packet_ptr);

    if (status != NX_SUCCESS)
    {
        nx_packet_release(resp_packet_ptr);
        return status;
    }

    /* Let HTTP server know the response has been sent. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);

}
```

## <a name="nx_web_http_server_callback_packet_send"></a>nx_web_http_server_callback_packet_send

Отправка пакета HTTP из функции обратного вызова.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_callback_packet_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr);
```

### <a name="description"></a>Описание

Эта служба отправляет полный ответ HTTP-сервера из обратного вызова HTTP. HTTP-сервер отправит пакет с NX_WEB_HTTP_SERVER_TIMEOUT_SEND. В пакет должны быть добавлены заголовок и данные HTTP. Если возвращаемое состояние указывает на ошибку, приложение HTTP должно освободить пакет.

Обратный вызов должен возвращать NX_WEB_HTTP_CALLBACK_COMPLETED.

Более подробный пример: *nx_http_server_callback_generate_response_header()* .

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на управляющий блок HTTP-сервера.
- **packet_ptr**: указатель на пакет для отправки.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): пакет HTTP-сервера успешно отправлен.
- **NX_PTR_ERROR** (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* The packet is appended with HTTP header and data
    and is ready to send to the Client directly. */
status = nx_web_http_server_callback_packet_send(server_ptr, packet_ptr);

if (status != NX_SUCCESS)
{
    nx_packet_release(packet_ptr);
}

return(NX_WEB_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_web_http_server_callback_response_send"></a>nx_web_http_server_callback_response_send

Отправка ответа из функции обратного вызова.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_callback_response_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header,
    CHAR *information,
    CHAR additional_info);
```

### <a name="description"></a>Описание

Эта служба отправляет указанные сведения об ответе из подпрограммы обратного вызова приложения. Обычно она используется для отправки пользовательских ответов, связанных с запросами GET и POST. Обратите внимание, что, если используется эта функция, то подпрограмма обратного вызова должна возвращать состояние NX_WEB_HTTP_CALLBACK_COMPLETED.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется использовать службу *nx_web_http_server_callback_response_send_extended()* .

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на блок управления HTTP-сервером.
- **header**: указатель на строку заголовка ответа.
- **information**: указатель на строку информации.
- **additional_info**: указатель на строку дополнительной информации.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): ответ HTTP-сервера успешно отправлен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send(server_ptr,
            "HTTP/1.0 404 ",
            "NetX HTTP Server unable to find file: ",
            resource);

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_callback_response_send_extended"></a>nx_web_http_server_callback_response_send_extended

Отправка ответа из функции обратного вызова.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_callback_response_send_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header, UINT header_length,
    CHAR *information,
    UINT information_length,
    CHAR additional_info,
    UINT additional_info_length);
```

### <a name="description"></a>Описание

Эта служба отправляет указанные сведения об ответе из подпрограммы обратного вызова приложения. Обычно она используется для отправки пользовательских ответов, связанных с запросами GET и POST. Обратите внимание, что, если используется эта функция, то подпрограмма обратного вызова должна возвращать состояние NX_WEB_HTTP_CALLBACK_COMPLETED.

Строки header, information и additional_info должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.

Эта служба заменяет *nx_web_http_server_callback_response_send()* . В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на блок управления HTTP-сервером.
- **header**: указатель на строку заголовка ответа.
- **header_length**: длина строки заголовка ответа.
- **information**: указатель на строку информации.
- **information_length**: длина строки информации.
- **additional_info**: указатель на строку дополнительной информации.
- **additional_info_length**: длина строки дополнительной информации.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): ответ HTTP-сервера успешно отправлен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    /* Look for the test resource! */
    if ((request_type == NX_WEB_HTTP_SERVER_GET_REQUEST) &&
        (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
            a resource not found response. */
        nx_web_http_server_callback_response_send_extended(server_ptr,
            "HTTP/1.0 404 ",
            sizeof("HTTP/1.0 404 ") – 1,
            "NetX HTTP Server unable to find file: ",
            sizeof("NetX HTTP Server unable to find file: ") – 1,
            resource, strlen(resource));

        /* Return completion status. */
        return(NX_WEB_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_web_http_server_content_get"></a>nx_web_http_server_content_get

Получение содержимого из запроса.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_content_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a>Описание

Эта служба пытается получить указанный объем содержимого из запроса POST или PUT HTTP-клиента. Ее следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_web_http_server_create()* ).

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на блок управления HTTP-сервером.
- **packet_ptr**: указатель на пакет запроса HTTP-клиента. Обратите внимание, что этот пакет не должен быть освобожден обратным вызовом уведомления о запросе.
- **byte_offset**: число байтов для смещения в область содержимого.
- **destination_ptr**: указатель на область назначения для содержимого.
- **destination_size**: максимальное число байтов, доступных в области назначения.
- **actual_size**: указатель на переменную назначения, в качестве значения которой будет задан фактический размер копируемого содержимого.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): содержимое HTTP-сервера успешно получено.
- **NX_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-сервера.
- **NX_WEB_HTTP_DATA_END** (0X30007): конец содержимого запроса.
- **NX_WEB_HTTP_TIMEOUT** (0x30001): время ожидания HTTP-сервера при получении следующего пакета содержимого.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_get_extended"></a>nx_web_http_server_content_get_extended

Получение содержимого из запроса или поддержка содержимого нулевой длины.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_content_get_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a>Описание

Эта служба почти идентична службе *nx_web_http_server_content_get()* . Она пытается получить указанный объем содержимого из запроса POST или PUT HTTP-клиента. Однако она обрабатывает запросы с содержимым нулевой длины (пустые запросы) как допустимые. Ее следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_web_http_server_create()* ).

Эта служба заменяет *nx_web_http_server_content_get()* . В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на блок управления HTTP-сервером.
- **packet_ptr**: указатель на пакет запроса HTTP-клиента. Обратите внимание, что этот пакет не должен быть освобожден обратным вызовом уведомления о запросе.
- **byte_offset**: число байтов для смещения в область содержимого.
- **destination_ptr**: указатель на область назначения для содержимого.
- **destination_size**: максимальное число байтов, доступных в области назначения.
- **actual_size**: указатель на переменную назначения, в качестве значения которой будет задан фактический размер копируемого содержимого.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): содержимое HTTP-запроса успешно получено.
- **NX_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-сервера.
- **NX_WEB_HTTP_DATA_END** (0X30007): конец содержимого запроса.
- **NX_WEB_HTTP_TIMEOUT** (0x30001): время ожидания HTTP-сервера при получении следующего пакета.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get_extended(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_length_get"></a>nx_web_http_server_content_length_get

Получение длины содержимого в запросе или поддержка содержимого нулевой длины.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_content_length_get(
    NX_PACKET *packet_ptr,
    UINT *content_length);
```

### <a name="description"></a>Описание

Эта служба пытается получить длину содержимого HTTP в указанном пакете. Возвращаемое значение указывает на состояние успешного завершения, а фактическое значение длины возвращается в параметре content_length входного указателя. Если содержимого HTTP нет или длина содержимого равна нулю, эта подпрограмма по-прежнему возвращает состояние выполнения, а указатель ввода content_length указывает на допустимую длину (ноль). Ее следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_web_http_server_create()* ).

### <a name="input-parameters"></a>Входные параметры

- **packet_ptr**: указатель на пакет запроса HTTP-клиента. Обратите внимание, что этот пакет не должен быть освобожден обратным вызовом уведомления о запросе.
- **content_length**: указатель на значение, полученное из поля длины содержимого.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): длина содержимого HTTP-сервера успешно получена.
- **NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F): недопустимый формат заголовка HTTP.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Assuming we are in the application’s request notify callback
    routine, get the content length of the HTTP Client request. */

ULONG content_length;
status = nx_web_http_server_content_length_get(packet_ptr, &content_length);

/* If the "status" variable indicates successful completion, the "length"
    Variable contains the length of the HTTP Client request content area. */
```

## <a name="nx_web_http_server_create"></a>nx_web_http_server_create

Создание экземпляра HTTP-сервера.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_create(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *http_server_name, NX_IP *ip_ptr, UINT server_port,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*authentication_check)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, CHAR **name,
        CHAR **password, CHAR **realm),
    UINT (*request_notify)(NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a>Описание

Эта служба создает экземпляр HTTP-сервера, который выполняется в контексте собственного потока ThreadX. Необязательные подпрограммы обратного вызова приложений *authentication_check* и *request_notify* позволяют программному обеспечению приложения управлять основными операциями HTTP-сервера.

Эта служба используется для создания как HTTP-серверов без шифрования, так и HTTPS-серверов с шифрованием TLS. Чтобы включить протокол HTTPS с шифрованием TLS, ознакомьтесь с описанием службы *nx_web_http_server_secure_configure()* .

### <a name="input-parameters"></a>Входные параметры

- **http_server_ptr**: указатель на блок управления HTTP-сервером.
- **http_server_name**: указатель на имя HTTP-сервера.
- **ip_ptr**: указатель на созданный ранее экземпляр IP.
- **server_port**: TCP-порт ожидания передачи данных для экземпляра сервера.
- **media_ptr**: указатель на созданный ранее экземпляр носителя FileX.
- **stack_ptr**: указатель на область стека потоков HTTP-сервера.
- **stack_size**: указатель на размер стека потоков HTTP-сервера.
- **authentication_check**: указатель функции на подпрограмму проверки подлинности приложения. Если этот параметр указан, данная подпрограмма вызывается для каждого запроса HTTP-клиента. Если этот параметр имеет значение NULL, то проверка подлинности выполняться не будет. Этот параметр является нерекомендуемым. Вместо этого используйте вызов *nx_web_http_server_authenticate_check_set()* .
- **request_notify**: указатель функции на подпрограмму уведомления о запросе приложения. Если этот параметр указан, подпрограмма вызывается перед обработкой запроса HTTP-сервером. Это позволяет перенаправлять имя ресурса или обновлять поля в самом ресурсе до завершения запроса HTTP-клиента.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): HTTP-сервер успешно создан.
- NX_PTR_ERROR (0x07): недопустимый указатель на HTTP-сервер, IP-адрес, носитель, стек или пул пакетов.
- NX_WEB_HTTP_POOL_ERROR (0x30009): полезные данные пакета пула недостаточно велики, чтобы вместить полный HTTP-запрос.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки.

### <a name="example"></a>Например, .

```C
/* Create an HTTP Server instance called "my_server." */
status = nx_web_http_server_create(&my_server, "my server", &ip_0,
    NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_web_http_server_delete"></a>nx_web_http_server_delete

Удаление экземпляра HTTP-сервера.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_delete(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет созданный ранее экземпляр HTTP-сервера.

### <a name="input-parameters"></a>Входные параметры

- **http_server_ptr**: указатель на блок управления HTTP-сервером.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): HTTP-сервер успешно удален.
- NX_PTR_ERROR (0x07): недопустимый указатель на HTTP-сервер.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Delete the HTTP Server instance called "my_server." */
status = nx_web_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_web_http_server_get_entity_content"></a>nx_web_http_server_get_entity_content

Получение расположения и длины данных сущности.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_get_entity_content(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

### <a name="description"></a>Описание

Эта служба определяет расположение начала данных в текущем составном объекте в полученных сообщениях клиента, а также длину данных, не включая граничную строку. HTTP-сервер обновляет собственные смещения, чтобы эту функцию можно было повторно вызывать для той же датаграмме клиента в случае сообщений с несколькими сущностями. Указатель пакета обновляется до следующего пакета, где сообщением клиента является датаграмма с несколькими пакетами.

Обратите внимание на то, что для использования этой службы необходимо включить NX_WEB_HTTP_MULTIPART_ENABLE. Также обратите внимание, что приложение не должно освобождать пакет, на который указывает packet_pptr. Это выполняет HTTP-сервер.

Дополнительные сведения см. в описании *nx_web_http_server_get_entity_header()* .

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на HTTP-сервер.
- **packet_pptr**: указатель на расположение указателя пакета. Обратите внимание на то, что приложение не должно освобождать этот пакет.
- **available_offset**: указатель на смещение данных сущности от указателя начала пакета.
- **available_length**: указатель на длину данных сущности.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): размер и расположение содержимого сущности успешно получены.
- **NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016): содержимое внутренних составных маркеров HTTP-сервера уже найдено.
- NX_HTTP_ERROR (0x30000): внутренняя ошибка HTTP-сервера.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
NX_WEB_HTTP_SERVER my_server;
UINT offset, length;
NX_PACKET *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
    the entity header to determine details about the multipart data. If
    successful, it then calls this service to get the location of entity data: */
status = nx_web_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
    &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
    entity data. */
```

## <a name="nx_web_http_server_get_entity_header"></a>nx_web_http_server_get_entity_header

Получение содержимого заголовка сущности.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_get_entity_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);
```

### <a name="description"></a>Описание

Эта служба извлекает заголовок сущности в указанный буфер. HTTP-сервер обновляет собственные указатели для поиска следующей составной сущности в датаграмме клиента с несколькими заголовками сущностей. Указатель пакета обновляется до следующего пакета, где сообщением клиента является датаграмма с несколькими пакетами.

Обратите внимание на то, что для использования этой службы необходимо включить NX_WEB_HTTP_MULTIPART_ENABLE. Также обратите внимание, что приложение не должно освобождать пакет, на который указывает packet_pptr.

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на HTTP-сервер.
- **packet_pptr**: указатель на расположение указателя пакета. Обратите внимание на то, что приложение не должно освобождать этот пакет.
- **entity_header_buffer**: указатель на расположение для хранения заголовка сущности.
- **buffer_size**: размер входного буфера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): заголовок сущности успешно получен.
- **NX_WEB_HTTP_NOT_FOUND** (0x30006): поле заголовка сущности не найдено.
- **NX_WEB_HTTP_TIMEOUT** (0x30001): истекло время ожидания получения следующего пакета для сообщения клиента с несколькими пакетами.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.
- NX_WEB_HTTP_ERROR (0x30000): внутренняя ошибка HTTP.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Buffer to hold data we are extracting from the request. */
UCHAR buffer[1440];

/* *my_request_notify()* is the application request notify callback
    registered with the HTTP server in *nx_web_http_server_create()*,
    creates a response to the received Client request. */
UINT my_request_notify(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
    CHAR *resource, NX_PACKET *packet_ptr)
{
    UINT offset, length;
    NX_PACKET *response_pkt;

    /* Process multipart data. */
    if(request_type == NX_WEB_HTTP_SERVER_POST_REQUEST)
    {
        /* Get the content header. */
        while(nx_web_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
            sizeof(buffer)) == NX_SUCCESS)
        {
            /* Header obtained successfully. Get the content data location. */
            while(nx_web_http_server_get_entity_content(server_ptr,
                &packet_ptr, &offset, &length) == NX_SUCCESS)
            {
                /* Write content data to buffer. */
                nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                    &length);
                buffer[length] = 0;
            }
        }

        /* Generate HTTP header. */
        status = nx_web_http_server_callback_generate_response_header(server_ptr,
            &response_pkt, NX_WEB_HTTP_STATUS_OK, 800, "text/html",
            "Server: NetX WEB HTTP 5.10\r\n");

        if(status == NX_SUCCESS)
        {
            if(nx_web_http_server_callback_packet_send(server_ptr, response_pkt) !=
                NX_SUCCESS)
            {
                nx_packet_release(response_pkt);
            }
        }
    }
    else
    {
        /* Indicate we have not processed the response to client yet.*/
        return(NX_SUCCESS);
    }

    /* Indicate the response to client is transmitted. */
    return(NX_WEB_HTTP_CALLBACK_COMPLETED);
}

```

## <a name="nx_web_http_server_gmt_callback_set"></a>nx_web_http_server_gmt_callback_set

Задание обратного вызова для получения даты и времени по Гринвичу.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

### <a name="description"></a>Описание

Эта служба задает обратный вызов для получения даты и времени в формате GMT с помощью созданного ранее HTTP-сервера. Эта служба вызывается HTTP-сервером и создает заголовок в ответах HTTP-сервера для клиента.

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на HTTP-сервер.
- **gmt_getv**: указатель на обратный вызов для получения даты и времени по Гринвичу.
- **date**: указатель на полученную дату.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): обратный вызов успешно задан.
- NX_PTR_ERROR (0x07): недопустимый указатель на пакет или параметр.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
NX_WEB_HTTP_SERVER my_server;

VOID get_gmt(NX_WEB_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_web_http_server_create(),
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the GMT retrieve callback: */
status = nx_web_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
    response header date. */
```

## <a name="nx_web_http_server_invalid_userpassword_notify_set"></a>nx_web_http_server_invalid_userpassword_notify_set

Задание обратного вызова для обработки недопустимого имени пользователя или пароля.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource,
        ULONG client_address,
        UINT request_type));
```

### <a name="description"></a>Описание

Эта служба задает обратный вызов, вызываемый при получении недопустимого имени пользователя и пароля в запросе GET, PUT или DELETE клиента в результате дайджест-проверки подлинности или обычной проверки подлинности. HTTP-сервер должен быть уже создан.

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на HTTP-сервер.
- **invalid_username_password_callback**: указатель на недопустимый обратный вызов для имени пользователя или пароля.
- **resource**: указатель на ресурс, указанный клиентом.
- **client_address**: адрес клиента.
- **request_type**: указывает тип запроса клиента. Может иметь следующие значения:
  - *NX_WEB_HTTP_SERVER_GET_REQUEST*
  - *NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*
  - *NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): обратный вызов успешно задан.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
NX_WEB_HTTP_SERVER my_server;

VOID invalid_username_password_callback(NX_CHAR *resource,
    ULONG client_address,
    UINT request_type);

/* After the HTTP server is created by calling nx_web_http_server_create,
    and before starting HTTP services when nx_web_http_server_start() is called,
    set the invalid username password callback: */

status = nx_web_http_server_invalid_userpassword_notify_set( (&my_server,
    invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
    will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_web_http_server_mime_maps_additional_set"></a>nx_web_http_server_mime_maps_additional_set

Задание дополнительных сопоставлений MIME для HTML.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_mime_maps_additional_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_WEB_HTTP_SERVER_MIME_MAP *mime_maps,
    UINT mime_maps_num);
```

### <a name="description"></a>Описание

Эта служба позволяет разработчику приложения HTTP добавлять дополнительные типы MIME из типов MIME по умолчанию, предоставляемых сервером NetX Web HTTP. Список определенных типов см. в описании *nx_web_http_server_get_type ()* .

Если получен запрос клиента, например запрос GET, HTTP-сервер анализирует запрошенный тип файла из заголовка HTTP с помощью дополнительно заданного сопоставления MIME и, если совпадения не найдены, ищет соответствие с сопоставлением MIME по умолчанию HTTP-сервера. Если совпадения не найдены, по умолчанию используется тип MIME "text/plain".

Если функция уведомления о запросе зарегистрирована на HTTP-сервере, обратный вызов уведомления о запросе может вызвать *nx_web_http_server_type_get_extended* для анализа типа файла.

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на экземпляр HTTP-сервера.
- **mime_maps**: указатель на массив сопоставлений MIME.
- **mime_map_num**: число сопоставлений MIME в массиве.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): сопоставление MIME HTTP-сервера успешно задано.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки.

### <a name="example"></a>Например, .

```C
/* my_server is an NX_WEB_HTTP_SERVER previously created. */
static NX_WEB_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_web_http_server_mime_maps_additional_set(&my_server,
    &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
    server MIME map set." */
```

## <a name="nx_web_http_server_response_packet_allocate"></a>nx_web_http_server_response_packet_allocate

Выделение пакета HTTP(S).

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_response_packet_allocate(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба пытается выделить пакет для HTTP(S)-сервера.

Обратите внимание на то, что в случае **сбоя** последующего вызова API NetX или HTTP-сервера, использующего этот пакет в качестве входных данных, например nx_packet_data_append или **nx_web_http_server_callback_packet_send, за освобождение этого пакета отвечает приложение. **

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на блок управления HTTP-сервером.
- **packet_ptr**: указатель на выделенный пакет.
- **wait_option**: определяет время ожидания в тактах, если в пуле пакетов нет доступных пакетов. Параметры ожидания определяются следующим образом:
  - **NX_NO_WAIT** (0X00000000): выбор NX_NO_WAIT приведет к немедленному возвращению вызывающего потока, если запрос не может быть выполнен.
  - **NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.
  - **значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): пакет выделен успешно.
- **NX_NO_PACKET** (0x01): нет доступных пакетов.
- **NX_WAIT_ABORTED** (0x1A): запрошенная приостановка прервана вызовом *tx_thread_wait_abort*.
- **NX_INVALID_PARAMETERS** (0x4D): размер пакета не поддерживается протоколом.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Allocate a packet for HTTP(S) Server and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_server_response_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_server_packet_content_find"></a>nx_web_http_server_packet_content_find

Извлечение длины содержимого и установка указателя на начало данных.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_packet_content_find(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    UINT *content_length);
```

### <a name="description"></a>Описание

Эта служба извлекает длину содержимого из заголовка HTTP. Она также обновляет указанный пакет следующим образом: перед указателем начала пакета (начало расположения буфера пакета для записи) задается содержимое HTTP (данные), только что переданное заголовком HTTP.

Если в текущем пакете не найдено начало содержимого, функция ожидает получения следующего пакета с помощью параметра ожидания NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.

Обратите внимание, что эту службу не следует вызывать перед вызовом *nx_web_http_server_get_entity_header()* , так как она изменяет зависящий от пакета указатель в начале после заголовка сущности.

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на экземпляр HTTP-сервера.
- **packet_ptr**: указатель на указатель пакета для возврата пакета с обновленным указателем начала.
- **content_length**: указатель на извлеченный параметр content_length.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): длина содержимого HTTP обнаружена, и пакет успешно обновлен.
- **NX_HTTP_TIMEOUT** (0x30001): истекло время ожидания следующего пакета.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
    The server has received a Client request packet, recv_packet_ptr,
    and the packet content find service is called from the request notify callback
    function registered with the HTTP server. */

UINT content_length;

status = nx_web_http_server_packet_content_find(server_ptr, recv_packet_ptr,
    &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
    and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_web_http_server_packet_get"></a>nx_web_http_server_packet_get

Получение следующего пакета HTTP.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_packet_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr);
```

### <a name="description"></a>Описание

Эта служба возвращает следующий пакет, полученный через сокет HTTP-сервера. Для получения пакета используется параметр ожидания NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.

Обратите внимание на то, что в случае успешного выполнения именно приложение отвечает за освобождение пакета.

### <a name="input-parameters"></a>Входные параметры

- **server_ptr**: указатель на экземпляр HTTP-сервера.
- **packet_ptr**: указатель на полученный пакет.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): следующий пакет HTTP успешно получен.
- **NX_HTTP_TIMEOUT** (0x30001): истекло время ожидания следующего пакета.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* The HTTP server pointed to by server_ptr is previously created and started. */
UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_web_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_web_http_server_param_get"></a>nx_web_http_server_param_get

Получение параметра из запроса.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_param_get(NX_PACKET *packet_ptr,
    UINT param_number, CHAR *param_ptr,
    UINT *param_size, UINT max_param_size);
```

### <a name="description"></a>Описание

Эта служба пытается получить указанный параметр URL-адреса HTTP из указанного пакета запроса. Если запрашиваемый параметр HTTP отсутствует, подпрограмма возвращает состояние NX_WEB_HTTP_NOT_FOUND. Эту подпрограмму следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_web_http_server_create()* ).

### <a name="input-parameters"></a>Входные параметры

- **packet_ptr**: указатель на пакет запроса HTTP-клиента. Обратите внимание на то, что приложение не должно освобождать этот пакет.
- **param_number**: логический номер параметра, начинающийся с нуля, слева направо в списке параметров.
- **param_ptr**: область назначения для копирования параметра.
- **param_size**: возвращает общий размер данных параметра (в байтах).
- **max_param_size**: максимальный размер области назначения параметра.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): параметр HTTP-сервера успешно получен.
- **NX_WEB_HTTP_NOT_FOUND** (0x30006): указанный параметр не найден.
- **NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015): неправильное завершение параметра запроса.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first parameter of the HTTP Client request. */

status = nx_web_http_server_param_get(request_packet_ptr, 0, param_destination,
    &param_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
    in "param_destination" and the size of that string can be found
    in the variable "param_size." */
```

## <a name="nx_web_http_server_query_get"></a>nx_web_http_server_query_get

Получение запроса из запроса.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_query_get(NX_PACKET *packet_ptr,
    UINT query_number,
    CHAR *query_ptr,
    CHAR *query_size,
    UINT max_query_size);
```

### <a name="description"></a>Описание

Эта служба пытается получить указанный HTTP-запрос URL-адреса из указанного пакета запроса. Если запрашиваемый HTTP-запрос отсутствует, подпрограмма возвращает состояние NX_WEB_HTTP_NOT_FOUND. Эту подпрограмму следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_web_http_server_create()* ).

### <a name="input-parameters"></a>Входные параметры

- **packet_ptr**: указатель на пакет запроса HTTP-клиента. Обратите внимание на то, что приложение не должно освобождать этот пакет.
- **query_number**: логический номер параметра, начинающийся с нуля, слева направо в списке запросов.
- **query_ptr**: область назначения для копирования запроса.
- **query_size**: размер возвращаемых данных запроса (в байтах).
- **max_query_size**: максимальный размер области назначения запроса.

.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): запрос HTTP-сервера успешно получен.
- **NX_WEB_HTTP_FAILED** (0x30002): слишком маленький размер запроса.
- **NX_WEB_HTTP_NOT_FOUND** (0x30006): указанный запрос не найден.
- **NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013): запрос отсутствует в запросе клиента.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first query of the HTTP Client request. */

status = nx_web_http_server_query_get(request_packet_ptr, 0,
    query_destination, &query_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
    in "query_destination" and the length of that string can be found in the
    variable "query_size". */
```

## <a name="nx_web_http_server_response_chunked_set"></a>nx_web_http_server_response_chunked_set

Настройка поблочной передачи для ответа HTTP(S).

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_response_chunked_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a>Описание

Эта служба использует поблочное кодирование для передачи клиенту пользовательского пакета данных ответа HTTP(S), созданного с помощью службы *nx_web_http_server_response_packet_allocate()* .

> [!NOTE]
> Если приложение использует поблочное кодирование для передачи пакета данных ответа, то оно должно вызвать эту службу после вызова службы *nx_web_http_server_response_packet_allocate()* и перед вызовом службы *nx_web_http_server_callback_packet_send()* .

### <a name="input-parameters"></a>Входные параметры

- **client_ptr**: указатель на блок управления HTTP-клиентом.
- **chunk_size**: размер блока данных в октетах.
- **packet_ptr**: указатель на пакет данных HTTP(S)-запроса.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): режим поблочной передачи успешно задан.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Generate HTTP header. */
nx_web_http_server_callback_generate_response_header(server_ptr,
    &response_pkt, NX_WEB_HTTP_STATUS_OK, 0, "text/html",
    "Transfer-Encoding: chunked\r\n");

/* Create a new data packet response on the HTTP(S) Server instance. */
nx_web_http_server_response_packet_allocate(&my_server, &my_packet, NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_server_response_chunked_set(&my_server, 128, my_packet)

/* At this point, user can fill the data into my_packet. *./
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet response to client. */
nx_web_http_server_callback_packet_send(&my_server, my_packet);
```

## <a name="nx_web_http_server_secure_configure"></a>nx_web_http_server_secure_configure

Настройка шифрования TLS на HTTP-сервере для использования защищенного протокола HTTPS.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_secure_configure(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    const NX_SECURE_TLS_CRYPTO *crypto_table,
    VOID *metadata_buffer, ULONG metadata_size,
    UCHAR* packet_buffer, UINT packet_buffer_size,
    NX_SECURE_X509_CERT *identity_certificate,
    NX_SECURE_X509_CERT *trusted_certificates[],
    UINT trusted_certs_num,
    NX_SECURE_X509_CERT *remote_certificates[],
    UINT remote_certs_num,
    UCHAR *remote_certificate_buffer,
    UINT remote_cert_buffer_size);
```

### <a name="description"></a>Описание

Эта служба настраивает шифрование TLS на созданном ранее экземпляре сервера NetX Web HTTP для безопасного обмена данными по протоколу HTTPS. Используются параметры для настройки всех возможных сеансов TLS с одинаковым состоянием, чтобы обеспечить согласованное поведение всех входящих HTTPS-клиентов. Количеством сеансов TLS управляет макрос NX_WEB_HTTP_SESSION_MAX.

Таблица подпрограмм шифрования (таблица комплектов шифров) является общей для всех сеансов TLS, так как она содержит только указатели функций.

Буферы повторной сборки метаданных и пакетов равномерно распределяются между всеми сеансами TLS. Если размер буфера не делится нацело на число сеансов, то полученный остаток не используется.

Переданный сертификат удостоверения используется всеми сеансами. Во время операции TLS сертификат удостоверения сервера только считывается, поэтому его не требуется копировать для каждого сеанса.

Доверенные сертификаты добавляются в каждый сеанс TLS на HTTPS-сервере. Они используются для проверки подлинности на основе сертификата клиента, которая автоматически включается, когда предоставляется удаленное хранилище сертификатов.

Удаленный массив и буфер сертификатов по умолчанию являются общими для всех сеансов TLS. Удаленные сертификаты используются для проверки подлинности на основе сертификата клиента, которая автоматически включается, когда число удаленных сертификатов не равно нулю. Ввиду совместного использования буфера некоторые сеансы могут блокироваться во время проверки сертификата.

Чтобы отключить проверку подлинности на основе сертификата клиента, передайте значение NX_NULL для параметра remote_certificates и значение 0 для параметра remote_certs_num.

Возвращаемые значения будут содержать все коды ошибок TLS, полученные в результате проблем в конфигурации сеансов TLS.

### <a name="input-parameters"></a>Входные параметры

- **http_server_ptr**: указатель на экземпляр HTTP-сервера.
- **crypto_table**: указатель на таблицу комплектов шифров TLS.
- **metadata_buffer**: указатель на буфер криптографических метаданных.
- **metadata_size**: размер буфера криптографических метаданных.
- **packet_buffer**: буфер повторной сборки пакетов TLS.
- **packet_buffer**: размер буфера пакетов TLS, он должен быть равен <требуемый размер буфера TLS> * NX_WEB_HTTP_SESSION_MAX.
- **identity_certificate**: сертификат удостоверения сервера TLS, который будет использоваться для всех сеансов HTTPS-сервера.
- **trusted_certificates**: указатель на массив объектов NX_SECURE_X509_CERT, используемый для проверки входящих сертификатов клиента, если проверка подлинности на основе сертификата клиента включена путем передачи ненулевого значения для параметра *remote_certs_num*.
- **trusted_certs_num**: количество доверенных сертификатов в массиве *trusted_certificates*.
- **remote_certificates**: указатель на массив объектов NX_SECURE_X509_CERT, используемых для входящих сертификатов клиента.
- **remote_certs_num**: число удаленных сертификатов. Должно быть равно максимальному числу ожидаемых сертификатов от клиентов. Проверка подлинности на основе сертификата клиента включается автоматически, если это значение не равно нулю.
- **remote_certificate_buffer**: буфер для хранения входящих удаленных сертификатов от клиентов, если включена проверка подлинности на основе сертификата клиента. remote_cert_buffer_size: размер буфера удаленных сертификатов. Должен быть равен <максимальный ожидаемый размер сертификата> \* remote_certs_num.


### <a name="return-values"></a>Возвращаемые значения

- **TX_SUCCESS** (0x00): сеанс TLS успешно инициализирован.
- **NX_NOT_CONNECTED** (0x38): базовый сокет TCP больше не подключен.
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102): получен неправильный тип сообщения TLS.
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106): шифр, предоставленный удаленным узлом, не поддерживается.
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107): не удалось обработать сообщение во время подтверждения TLS.
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108): не удалось проверить хэш MAC во входящем сообщении.
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109): не удалось отправить данные через базовый сокет TCP.
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A): входящее сообщение содержало недопустимое поле длины.
- **NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B): неправильное входящее сообщение ChangeCipherSpec.
- **NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C): входящий сертификат TLS невозможно использовать для идентификации удаленного сервера TLS.
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D): шифр с открытым ключом, предоставленный удаленным узлом, не поддерживается.
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0X10E): на удаленном узле нет ни одного комплекта шифров, поддерживаемого стеком NetX Secure TLS.
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F): в заголовке полученного сообщения TLS указана неизвестная версия TLS.
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110): в заголовке полученного сообщения TLS указана неподдерживаемая версия TLS.
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111): не удалось выделить внутренний пакет TLS.
- **NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112): удаленный узел предоставил недопустимый сертификат.
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114): удаленный узел отправил оповещение об ошибке и завершает сеанс TLS.
- **NX_PTR_ERROR** (0x07): попытка использовать недопустимый указатель.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки.

### <a name="example"></a>Например, .

```C
/* Create the HTTPS Server. */

status = nx_web_http_server_create(&my_server, "My HTTP Server",
    &ip_0, &ram_disk, &server_stack, sizeof(server_stack),
    &pool_0, authentication_check, server_request_callback);

/* Initialize device certificate (used for all sessions in HTTPS server). */
nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
    device_cert_der_len, NX_NULL, 0,
    device_cert_key_der, device_cert_key_der_len,
    NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

/* Setup TLS session for the HTTPS server.
    Note that since the remote_certs_num parameter is 0,
    no trusted certificates are needed, and Client certificate authentication is disabled. */
status = nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
    crypto_metadata,
    sizeof(crypto_metadata),
    tls_packet_buffer, sizeof(tls_packet_buffer),
    &certificate, NX_NULL, 0, NX_NULL, 0, NX_NULL, 0);

/* Start an HTTPS Server with TLS. */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_start"></a>nx_web_http_server_start

Запуск HTTP-сервера.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_start(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Описание

Эта служба запускает созданный ранее экземпляр HTTP или HTTPS-сервера.

HTTPS-серверы используют те же API, что и HTTP-серверы. Чтобы включить протокол HTTPS с шифрованием TLS на HTTP-сервере, ознакомьтесь с описанием службы *nx_web_http_server_secure_configure()* .

### <a name="input-parameters"></a>Входные параметры

- **http_server_ptr**: указатель на экземпляр HTTP-сервера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): HTTP-сервер успешно запущен.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки.

### <a name="example"></a>Например, .

```C
/* Start the HTTP Server instance "my_server." */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_stop"></a>nx_web_http_server_stop

Остановка HTTP-сервера.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_stop(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Описание

Эта служба останавливает созданный ранее экземпляр HTTP-сервера. Эту подпрограмму следует вызывать до удаления экземпляра HTTP-сервера.

### <a name="input-parameters"></a>Входные параметры

- **http_server_ptr**: указатель на экземпляр HTTP-сервера.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): HTTP-сервер успешно остановлен.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```C
/* Stop the HTTP Server instance "my_server." */
status = nx_web_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_web_http_server_type_get"></a>nx_web_http_server_type_get

Извлечение типа файла из HTTP-запроса клиента.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_type_get(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, CHAR *http_type_string,
    UINT *string_size);
```

### <a name="description"></a>Описание

> [!NOTE]
> использовать эту службу больше не рекомендуется. Пользователям рекомендуется использовать службу *nx_web_http_server_type_get_extended()* .

Эта служба извлекает тип HTTP-запроса из *http_type_string* и его длину из *string_size* из входного буфера *name* (обычно это URL-адрес). Если сопоставление MIME не найдено, по умолчанию используется тип "text/plain". В противном случае извлеченный тип сравнивается с сопоставлениями MIME HTTP-сервера по умолчанию. Сопоставления MIME по умолчанию на сервере NetX Duo HTTP:

- html — "text/html";
- htm — "text/html";
- txt — "text/plain";
- gif — "image/gif";
- jpg — "image/jpeg";
- ico — "image/x-icon".

Если этот параметр задан, также будет выполнен поиск определенного пользователем набора дополнительных сопоставлений MIME. Дополнительные сведения об определяемых пользователем сопоставлениях см. в описании службы *nx_web_http_server_mime_maps_addtional_set()* .

### <a name="input-parameters"></a>Входные параметры

- **http_server_ptr**: указатель на экземпляр HTTP-сервера.
- **name**: указатель на буфер для поиска.
- **http_type_string**: указатель на извлеченный тип HTML.
- **string_size**: указатель на возвращаемую длину строки типа HTML.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): тип успешно извлечен.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- **NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019): возвращен тип по умолчанию (text/plain).

### <a name="allowed-from"></a>Допустимые источники

Приложение

### <a name="example"></a>Например, .

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_web_http_server_type_get(&my_server_ptr,
    my_server.nx_web_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_type_get_extended"></a>nx_web_http_server_type_get_extended

Извлечение типа файла из HTTP-запроса клиента.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_type_get_extended(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, UINT name_length,
    CHAR *http_type_string,
    UINT http_type_string_max_size,
    UINT *string_size);
```

### <a name="description"></a>Описание

Эта служба извлекает тип HTTP-запроса из *http_type_string* и его длину из *string_size* из входного буфера *name* (обычно это URL-адрес). Если сопоставление MIME не найдено, по умолчанию используется тип "text/plain". В противном случае извлеченный тип сравнивается с сопоставлениями MIME HTTP-сервера по умолчанию. Сопоставления MIME по умолчанию на сервере NetX Duo HTTP:

- html — "text/html";
- htm — "text/html";
- txt — "text/plain";
- gif — "image/gif";
- jpg — "image/jpeg";
- ico — "image/x-icon".

Если этот параметр задан, также будет выполнен поиск определенного пользователем набора дополнительных сопоставлений MIME. Дополнительные сведения об определяемых пользователем сопоставлениях см. в описании службы *nx_web_http_server_mime_maps_addtional_set()* .

Эта служба заменяет *nx_web_http_server_type_get()* . В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.

### <a name="input-parameters"></a>Входные параметры

- **http_server_ptr**: указатель на экземпляр HTTP-сервера.
- **name**: указатель на буфер для поиска.
- **name_length**: длина имени.
- **http_type_string**: указатель на извлеченный тип HTML.
- **http_type_string_max_size**: размер буфера http_type_string.
- **string_size**: указатель на возвращаемую длину строки типа HTML

.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0X00): тип успешно извлечен.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- **NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019): возвращен тип по умолчанию (text/plain).

### <a name="allowed-from"></a>Допустимые источники

Приложение

### <a name="example"></a>Например, .

```C
/* my_server is a previously created HTTP server, which starts accepting client
    requests when *nx_web_http_server_start* is called */

CHAR temp_string[20];
UINT string_length;
UINT ret;

/* Extract the HTTP type. */
ret = nx_web_http_server_type_get_extended(&my_server_ptr,
    my_server.nx_web_http_server_request_resource,
    strlen(my_server.nx_web_http_server_request_resource),
    temp_string,sizeof(temp_string), &string_length);

/* If string_length is non zero, the HTTP string is extracted. */
    For a more detailed example, see the description for
    *nx_web_http_server_callback_generate_response_header().*
```

## <a name="nx_web_http_server_digest_authenticate_notify_set"></a>nx_web_http_server_digest_authenticate_notify_set

Задание функции обратного вызова дайджест-проверки подлинности.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*digest_authenticate_callback)(NX_WEB_HTTP_SERVER *server_ptr,
        CHAR *name_ptr,
        CHAR *realm_ptr,
        CHAR *password_ptr,
        CHAR *method,
        CHAR *authorization_uri,
        CHAR *authorization_nc,
        CHAR *authorization_cnonce));
```

### <a name="description"></a>Описание

Эта служба задает обратный вызов, вызываемый при выполнении дайджест-проверки подлинности.

### <a name="input-parameters"></a>Входные параметры

- **http_server_ptr**: указатель на экземпляр HTTP-сервера.
- **digest_authenticate_callback**: указатель на обратный вызов дайджест-проверки подлинности.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): обратный вызов успешно задан.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
- NX_NOT_SUPPORTED (0x4B): дайджест-проверка подлинности не включена.

### <a name="allowed-from"></a>Допустимые источники

Приложение

### <a name="example"></a>Например, .

```C
UINT digest_authenticate_callback(NX_WEB_HTTP_SERVER *server_ptr, CHAR *name_ptr,
    CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
    CHAR *authorization_uri, CHAR *authorization_nc,
    CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the digest authenticate callback: */
status = nx_web_http_server_digest_authenticate_notify_set(&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
    will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_web_http_server_authenticate_check_set"></a>nx_web_http_server_authenticate_check_set

Задание функции обратного вызова дайджест-проверки подлинности.

### <a name="prototype"></a>Прототип

```C
UINT nx_web_http_server_digest_authenticate_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*authentication_check_extended)(
        NX_WEB_HTTP_SERVER *server_ptr,
        UINT request_type,
        CHAR *resource,
        CHAR **name,
        UINT *name_length,
        CHAR **password,
        UINT password_length,
        CHAR **realm,
        UINT *realm_length));
```

### <a name="description"></a>Описание

Эта служба задает обратный вызов, выполняемый при проверке подлинности.

### <a name="input-parameters"></a>Входные параметры

- **http_server_ptr**: указатель на экземпляр HTTP-сервера.
- **authenticate_check_externded**: указатель на обратный вызов проверки подлинности.

### <a name="return-values"></a>Возвращаемые значения

- **NX_SUCCESS** (0x00): обратный вызов успешно задан.
- NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Приложение

### <a name="example"></a>Пример

```C
UINT authenticate_check_callback(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type,
    CHAR *name_ptr, UCHAR *resource, UCHAR **name,
    UINT *name_length, UCHAR **password,
    UINT *password_length, UCHAR **realm,
    UINT *realm_length)
{
    *name = "name";
    *name_length = 4;
    *password = "password";
    *password_length = 8;
    *realm = "realm";
    *realm_length = 5;
    return(NX_SUCCESS);
}

NX_WEB_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_web_http_server_create, and
    before starting HTTP services when nx_web_http_server_start is called, set the authenticate check callback: */

status = nx_web_http_digest_authenticate_check_set (&my_server,
    authenticate_check_callback);

/* If status equals NX_SUCCESS, the authenticate_check_callback function
    will be called when the HTTP server performs authenticate check. */
```
