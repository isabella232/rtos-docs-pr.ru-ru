---
title: Глава 3. Описание служб HTTP для NetX Duo в ОСРВ Azure
description: В этой главе содержится описание всех служб HTTP для NetX Duo в ОСРВ Azure (перечисленных ниже) в алфавитном порядке, за исключением служб для NetX (только IPv4), поскольку эквиваленты одной и той же службы объединяются.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 09add7bb20a8e104ba41583c0dbf4d574b8e6c9e6b3a3deed71d8fa8c8942ce2
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796486"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-http-services"></a>Глава 3. Описание служб HTTP для NetX Duo в ОСРВ Azure

В этой главе содержится описание всех служб HTTP для NetX Duo в ОСРВ Azure (перечисленных ниже) в алфавитном порядке, за исключением служб для NetX (только IPv4), поскольку эквиваленты одной и той же службы объединяются.

В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, выделенные полужирным шрифтом, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

**Службы HTTP-клиента:**

- **nx_http_client_create** — *создание экземпляра HTTP-клиента*
- **nx_http_client_delete** — *удаление экземпляра HTTP-клиента*
- **nx_http_client_get_start** — *запуск HTTP-запроса GET (только IPv4)*
- **nx_http_client_get_start_extended** — *запуск HTTP-запроса GET (только IPv4)*
- **nx_http_client_get_start** — *запуск HTTP-запроса GET (IPv4 или IPv6)*
- **nx_http_client_get_start_extended** — *запуск HTTP-запроса GET (IPv4 или IPv6)*
- **nx_http_client_get_packet** — *получение следующего пакета данных ресурса*
- **nx_http_client_put_start** — *запуск HTTP-запроса PUT (только IPv4)*
- **nx_http_client_put_start_extended** — *запуск HTTP-запроса PUT (только IPv4)*
- **nx_http_client_put_start** — *запуск HTTP-запроса PUT (IPv4 или IPv6)*
- **nxd_http_client_put_start_extended** — *запуск HTTP-запроса PUT (IPv4 или IPv6)*
- **nx_http_client_put_packet** — *отправка следующего пакета данных ресурса*
- **nx_http_client_set_connect_port** — *изменение порта для подключения к HTTP-серверу*

**Службы HTTP-сервера:**

- **nx_http_server_cache_info_callback_set** — *задание обратного вызова для получения возраста и даты последнего изменения указанного URL-адреса*
- **nx_http_server_callback_data_send** — *отправка данных HTTP из функции обратного вызова*
- **nx_http_server_callback_generate_response_header** — *создание заголовка ответа в функциях обратного вызова*
- **nx_http_server_callback_generate_response_header_extended** — *создание заголовка ответа в функциях обратного вызова*
- **nx_http_server_callback_packet_send** — *отправка пакета HTTP из обратного вызова HTTP*
- **nx_http_server_callback_response_send** — *отправка ответа из функции обратного вызова*
- **nx_http_server_callback_response_send_extended** — *отправка ответа из функции обратного вызова*
- **nx_http_server_content_get** — *получение содержимого из запроса*
- **nx_http_server_content_get_extended** — *получение содержимого из запроса; поддерживает пустые запросы (содержимое нулевой длины)*
- **nx_http_server_content_length_get** — *получение длины содержимого в запросе*
- **nx_http_server_content_length_get_extended** — *получение длины содержимого в запросе; поддерживает пустые запросы (содержимое нулевой длины)*
- **nx_http_server_create** — *создание экземпляра HTTP-сервера*
- **nx_http_server_delete**  * — удаление экземпляра HTTP-сервера*
- **nx_http_server_get_entity_content** — *возврат размера и расположения содержимого сущности в URL-адресе*
- **nx_http_server_get_entity_header** — *извлечение заголовка сущности URL-адреса в указанный буфер*
- **nx_http_server_gmt_callback_set** — *задание обратного вызова для получения даты и времени по Гринвичу*
- **nx_http_server_invalid_userpassword_notify_set** — *задание обратного вызова, выполняющегося в случае получения в запросе клиента недопустимых имени пользователя и пароля*
- **nx_http_server_mime_maps_additional_set** — *определение дополнительных сопоставлений MIME для HTML*
- **nx_http_server_packet_content_find** — *извлечение длины содержимого в заголовке HTTP и установка указателя на начало данных содержимого*
- **nx_http_server_packet_get** — *прямое получение пакета клиента*
- **nx_http_server_param_get** — *получение параметра из запроса*
- **nx_http_server_query_get** — *получение параметра из запроса*
- **nx_http_server_start** — *запуск HTTP-сервера*
- **nx_http_server_stop** — *остановка HTTP-сервера*
- **nx_http_server_type_get (не рекомендуется)**  — *извлечение типа HTTP, например text/plain из заголовка*
- **nx_http_server_type_get_extended** — *извлечение типа HTTP, например text/plain из заголовка*
- **nx_http_server_digest_authenticate_notify_set** — *задание функции обратного вызова дайджест-проверки подлинности*
- **nx_http_server_authentication_check_set** — *задание функции обратного вызова проверки подлинности*

## <a name="nx_http_client_create"></a>nx_http_client_create

Создание экземпляра клиента PPPoE

### <a name="prototype"></a>Прототип

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
            CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
            ULONG window_size);
```

### <a name="description"></a>Описание

Эта служба создает экземпляр HTTP-клиента в указанном экземпляре IP.

### <a name="input-parameters"></a>Входные параметры

 - **client_ptr**: указатель на блок управления HTTP-клиентом.
 - **client_name**: имя экземпляра HTTP-клиента
 - **ip_ptr**: указатель на экземпляр IP
 - **pool_ptr**: указатель на пул пакетов по умолчанию Обратите внимание, что пакеты в этом пуле должны иметь объем полезных данных, достаточный для работы с полным заголовком ответа. Это определяется параметром NX_HTTP_CLIENT_MIN_PACKET_SIZE в *nx_http_client.h*.
 - **window_size** — размер окна приема сокета TCP клиента.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — успешное создание HTTP-клиента.
 - NX_PTR_ERROR (0x07) — недопустимый указатель на HTTP, ip_ptr или пул пакетов.
 - NX_HTTP_POOL_ERROR(0xE9) — недопустимый размер полезных данных в пуле пакетов.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status =  nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);

/* If status is NX_SUCCESS an HTTP Client instance was successfully created. */
```

## <a name="nx_http_client_delete"></a>nx_http_client_delete

Удаление экземпляра HTTP-клиента

### <a name="prototype"></a>Прототип

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет ранее созданный экземпляр HTTP-клиента.

### <a name="input-parameters"></a>Входные параметры

 - **client_ptr**: указатель на блок управления HTTP-клиентом.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — успешное удаление HTTP-клиента.
 - NX_PTR_ERROR (0x07) — недопустимый указатель на HTTP.
 - NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Delete the HTTP Client instance “my_client.”  */
status =  nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully deleted. */
```

## <a name="nx_http_client_get_start"></a>nx_http_client_get_start

Запуск HTTP-запроса GET через IPv4

### <a name="prototype"></a>Прототип

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, CHAR *input_ptr,
            UINT input_size, CHAR *username, CHAR *password,
            ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба пытается создать и отправить запрос GET к ресурсу, указанному указателем resource, в ранее созданном экземпляре HTTP-клиента. Если эта подпрограмма возвращает NX_SUCCESS, приложение может выполнить несколько вызовов службы *nx_http_client_get_packet*, чтобы получить пакеты данных, соответствующих содержимому запрошенного ресурса.

> [!NOTE]
> Строка ресурса может ссылаться на локальный файл, например ``` “/index.htm” ```, или на другой URL-адрес, например ```http://abc.website.com/index.htm```, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.

Эта служба работает только через IPv4. Для приложений, которым требуется подключение к сети IPv6, следует использовать *nxd_http_client_get_start_extended ()* .

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется перейти на использование *nx_http_client_get_start_extended()* или *nxd_http_client_get_start_extended()* .

### <a name="input-parameters"></a>Входные параметры

 - **client_ptr**: указатель на блок управления HTTP-клиентом.
 - **ip_address**: IP-адрес HTTP-сервера
 - **resource**: указатель на строку URL-адреса запрошенного ресурса
 - **input_ptr**: указатель на дополнительные данные для запроса GET Это необязательно. Если параметр допустим, указанные входные данные помещаются в область содержимого сообщения, а вместо операции GET используется POST.
 - **input_size** — число байтов в необязательных дополнительных входных данных, на которые указывает ```input_ptr```.
 - **username** — указатель на необязательное имя пользователя для проверки подлинности.
 - **password**: указатель на необязательный пароль для проверки подлинности.
 - **wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента. Параметры ожидания определяются следующим образом:

    - **Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Выбор параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.

    Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — успешная отправка HTTP-клиентом. ПОЛУЧЕНИЕ сообщения о запуске.
 - **NX_HTTP_ERROR** (0xE0) — внутренняя ошибка HTTP-клиента.
 - **NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.
 - **NX_HTTP_FAILED** (0xE2) — ошибка HTTP-клиента при взаимодействии с HTTP-сервером.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) — недопустимое имя и (или) пароль.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
 - NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                           NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                            POST_MESSAGE, sizeof(POST_MESSAGE),
                            “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_start_extended"></a>nx_http_client_get_start_extended

Запуск HTTP-запроса GET через IPv4

### <a name="prototype"></a>Прототип

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, UINT resource_length,
            CHAR *input_ptr, UINT input_size, CHAR *username,
            UINT username_length, CHAR *password, UINT password_length,
            ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба пытается создать и отправить запрос GET к ресурсу, указанному указателем resource, в ранее созданном экземпляре HTTP-клиента. Если эта подпрограмма возвращает NX_SUCCESS, приложение может выполнить несколько вызовов службы *nx_http_client_get_packet*, чтобы получить пакеты данных, соответствующих содержимому запрошенного ресурса.

> [!NOTE]
> Строка ресурса может ссылаться на локальный файл, например ``` “/index.htm” ```, или на другой URL-адрес, например ```http://abc.website.com/index.htm```, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.

Эта служба работает только через IPv4. Для приложений, которым требуется подключение к сети IPv6, следует использовать *nxd_http_client_get_start_extended ()* .

Эта служба заменяет *nx_http_client_get_start()* . Она требует от вызывающей стороны указания длины ресурса, имени пользователя и пароля.

### <a name="input-parameters"></a>Входные параметры

 - **client_ptr**: указатель на блок управления HTTP-клиентом.
 - **ip_address** — IP-адрес HTTP-сервера.
 - **resource** — указатель на строку URL-адреса запрошенного ресурса.
 - **resource_length** — длина строки URL-адреса запрошенного ресурса.
 - **input_ptr**: указатель на дополнительные данные для запроса GET Это необязательно. Если параметр допустим, указанные входные данные помещаются в область содержимого сообщения, а вместо операции GET используется POST.
 - **input_size** — число байтов в необязательных дополнительных входных данных, на которые указывает ```input_ptr```.
 - **username** — указатель на необязательное имя пользователя для проверки подлинности.
 - **username_length**: длина необязательного имени пользователя для проверки подлинности
 - **password**: указатель на необязательный пароль для проверки подлинности
 - **password_length**: длина необязательного пароля для проверки подлинности
 - **wait_option** определяет, как долго служба будет ожидать запуск запроса GET HTTP-клиента Параметры ожидания определяются следующим образом:
    - **Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Выбор параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.

    Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — успешная отправка HTTP-клиентом. ПОЛУЧЕНИЕ сообщения о запуске
 - **NX_HTTP_ERROR** (0xE0) — внутренняя ошибка HTTP-клиента.
 - **NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.
 - **NX_HTTP_FAILED** (0xE2) — ошибка HTTP-клиента при взаимодействии с HTTP-сервером.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) — недопустимое имя и (или) пароль.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
 - NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */


#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                     9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                     “myname”, 6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST request
   for TEST.HTM and successfully sent. */
```

## <a name="nxd_http_client_get_start"></a>nxd_http_client_get_start

Отправка HTTP-запроса GET (IPv4 или IPv6)

### <a name="prototype"></a>Прототип

```c
UINT nxd_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                CHAR *input_ptr, UINT input_size, CHAR *username, CHAR *password, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба пытается создать и отправить запрос GET к ресурсу, указанному указателем resource, в ранее созданном экземпляре HTTP-клиента. Его можно использовать для подключения к сети IPv4 или IPv6. Если эта подпрограмма возвращает NX_SUCCESS, приложение может выполнить несколько вызовов службы *nx_http_client_get_packet*, чтобы получить пакеты данных, соответствующих содержимому запрошенного ресурса.

> [!NOTE]
>Строка ресурса может ссылаться на локальный файл, например ``` “/index.htm” ```, или на другой URL-адрес, например ```http://abc.website.com/index.htm```, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется перейти на использование *nxd_http_client_get_start_extended()* .

### <a name="input-parameters"></a>Входные параметры

 - **client_ptr** — указатель на блок управления HTTP-клиентом.
 - **Server_ip** — IP-адрес HTTP-сервера.
 - **resource** — указатель на строку URL-адреса запрошенного ресурса.
 - **input_ptr**: указатель на дополнительные данные для запроса GET Это необязательно. Если параметр допустим, указанные входные данные помещаются в область содержимого сообщения, а вместо операции GET используется POST.
 - **input_size** — число байтов в необязательных дополнительных входных данных, на которые указывает ```input_ptr```.
 - **username** — указатель на необязательное имя пользователя для проверки подлинности.
 - **username_length**: длина необязательного имени пользователя для проверки подлинности
 - **password**: указатель на необязательный пароль для проверки подлинности
 - **password_length**: длина необязательного пароля для проверки подлинности
 - **wait_option** определяет, как долго служба будет ожидать запуск запроса GET HTTP-клиента Параметры ожидания определяются следующим образом:
    - **Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Выбор параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.

    Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — запрос GET успешно отправлен.
 - **NX_HTTP_PASSWORD_TOO_LONG** (0xF0) — длина пароля превышает размер буфера.
 - **NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.
 - **NX_HTTP_FAILED** (0xE2) — недопустимые параметры пакета.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) — недопустимое имя или пароль.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
 - NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start(&my_client, server_ip_address, “/TEST.HTM”,
NX_NULL, 0, “myname”, “mypassword”, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nxd_http_client_get_start_extended"></a>nxd_http_client_get_start_extended

Отправка HTTP-запроса GET (IPv4 или IPv6)

### <a name="prototype"></a>Прототип

```c
UINT nxd_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                UINT resource_length, CHAR *input_ptr,
                UINT input_size, CHAR *username, UINT
                username_length, CHAR *password, UINT
                password_length, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба пытается создать и отправить запрос GET к ресурсу, указанному указателем resource, в ранее созданном экземпляре HTTP-клиента. Его можно использовать для подключения к сети IPv4 или IPv6. Если эта подпрограмма возвращает NX_SUCCESS, приложение может выполнить несколько вызовов службы *nx_http_client_get_packet*, чтобы получить пакеты данных, соответствующих содержимому запрошенного ресурса.

> [!NOTE]
> Строка ресурса может ссылаться на локальный файл, например ``` “/index.htm” ```, или на другой URL-адрес, например ```http://abc.website.com/index.htm```, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.

Эта служба заменяет *nxd_http_client_get_start()* . Она требует от вызывающей стороны указания длины ресурса, имени пользователя и пароля.

### <a name="input-parameters"></a>Входные параметры

 - **client_ptr** — указатель на блок управления HTTP-клиентом.
 - **Server_ip** — IP-адрес HTTP-сервера.
 - **resource** — указатель на строку URL-адреса запрошенного ресурса.
 - **resource_length**: длина строки URL-адреса запрошенного ресурса
 - **input_ptr**: указатель на дополнительные данные для запроса GET Это необязательно. Если параметр допустим, указанные входные данные помещаются в область содержимого сообщения, а вместо операции GET используется POST.
 - **input_size** — число байтов в необязательных дополнительных входных данных, на которые указывает ```input_ptr```.
 - **username** — указатель на необязательное имя пользователя для проверки подлинности.
 - **username_length**: длина необязательного имени пользователя для проверки подлинности
 - **password**: указатель на необязательный пароль для проверки подлинности
 - **password_length** — длина необязательного пароля для проверки подлинности.
 - **wait_option** — определяет, как долго служба будет внутренне ожидать обработки запуска запроса get HTTP-клиента. Параметры ожидания определяются следующим образом:
    - **Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Выбор параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.

    Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — запрос GET успешно отправлен.
 - **NX_HTTP_PASSWORD_TOO_LONG** (0xF0) — длина пароля превышает размер буфера.
 - **NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.
 - **NX_HTTP_FAILED** (0xE2) — недопустимые параметры пакета.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) — недопустимое имя или пароль.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
 - NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;


/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nxd_http_client_get_start_extended(&my_client, server_ip_address,
                                             “/TEST.HTM”, 9, NX_NULL, 0, “myname”,
        6, “mypassword”, 10, 1000);


/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
   far successful. The client must now call nx_http_client_get_packet multiple
   times to retrieve the content associated with TEST.HTM. */
```

## <a name="nx_http_client_get_packet"></a>nx_http_client_get_packet

Получение следующего пакета данных ресурса

### <a name="prototype"></a>Прототип

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET **packet_ptr, ULONG
                               wait_option);
```

### <a name="description"></a>Описание

Эта служба извлекает следующий пакет содержимого ресурса, запрошенного предыдущим вызовом *nx_http_client_get_start*. Последовательные вызовы этой подпрограммы должны выполняться до получения состояния возврата NX_HTTP_GET_DONE.

### <a name="input-parameters"></a>Входные параметры

 - **client_ptr**: указатель на блок управления HTTP-клиентом.
 - **packet_ptr**: назначение для указателя пакета, содержащего частичное содержимое ресурса
 - **wait_option** определяет, как долго служба будет ожидать получение пакета HTTP-клиентом Параметры ожидания определяются следующим образом:
    - **Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Выбор параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.

    Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — пакет получен HTTP-клиентом.
 - **NX_HTTP_GET_DONE** (0xEC) — получение пакета HTTP-клиентом выполнено.
 - **NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не находится в режиме получения.
 - **NX_HTTP_BAD_PACKET_LENGTH** (0xED) — недопустимая длина пакета.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
 - NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
   Note that the nx_http_client_get_start routine must have been called
   previously. */
status =  nx_http_client_get_packet(&my_client, &next_packet, 1000);


/* If status is NX_SUCCESS, the next packet of content is pointed to
   by “next_packet”. */
```

## <a name="nx_http_client_put_start"></a>nx_http_client_put_start

Запуск HTTP-запроса PUT через IPv4

### <a name="prototype"></a>Прототип

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               ULONG ip_address, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба пытается отправить запрос PUT с указанным ресурсом к HTTP-серверу по указанному IP-адресу. Если эта подпрограмма выполняется успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_http_client_put_packet()* , чтобы фактически отправить содержимое ресурса на HTTP-сервер.

> [!NOTE]
> Строка ресурса может ссылаться на локальный файл, например ``` “/index.htm” ```, или на другой URL-адрес, например ```http://abc.website.com/index.htm```, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется перейти на использование *nx_http_client_put_start_extended()* .

### <a name="input-parameters"></a>Входные параметры

 - **client_ptr**: указатель на блок управления HTTP-клиентом.
 - **ip_address**: IP-адрес HTTP-сервера
 - **resource** — указатель на строку URL-адреса запрошенного ресурса.
 - **username**: указатель на необязательное имя пользователя для проверки подлинности.
 - **password**: указатель на необязательный пароль для проверки подлинности.
 - **total_bytes**: общее число отправляемых байтов ресурса Обратите внимание, что совокупная длина всех пакетов, отправленных через последующие вызовы *nx_http_client_put_packet*, должна равняться этому значению.
 - **wait_option** определяет, как долго служба будет ожидать запуск запроса PUT HTTP-клиента Параметры ожидания определяются следующим образом:
    - **Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.

    Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — запрос PUT успешно отправлен.
 - **NX_HTTP_USERNAME_TOO_LONG** (0xF1) — слишком длинное имя пользователя для буфера
 - **NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
 - NX_SIZE_ERROR (0x09) — недопустимый общий размер ресурса.
 - NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, “myname”, “mypassword”, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nx_http_client_put_start_extended"></a>nx_http_client_put_start_extended

Запуск HTTP-запроса PUT через IPv4

### <a name="prototype"></a>Прототип

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
           ULONG ip_address, CHAR *resource, UINT resource_length,
           CHAR *username,UINT username_length, CHAR *password,
           UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба пытается отправить запрос PUT с указанным ресурсом к HTTP-серверу по указанному IP-адресу. Если эта подпрограмма выполняется успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_http_client_put_packet()* , чтобы фактически отправить содержимое ресурса на HTTP-сервер.

> [!NOTE]
> Строка ресурса может ссылаться на локальный файл, например ``` “/index.htm” ```, или на другой URL-адрес, например ```http://abc.website.com/index.htm```, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.

Эта служба заменяет *nx_http_client_put_start()* . Она требует от вызывающей стороны указания длины ресурса, имени пользователя и пароля.

### <a name="input-parameters"></a>Входные параметры

 - **client_ptr**: указатель на блок управления HTTP-клиентом.
 - **ip_address**: IP-адрес HTTP-сервера
 - **resource** — указатель на строку URL-адреса запрошенного ресурса.
 - **resource_length** — длина строки URL-адреса для ресурса, отправляемого на сервер.
 - **username**: указатель на необязательное имя пользователя для проверки подлинности
 - **username_length**: длина необязательного имени пользователя для проверки подлинности
 - **password**: указатель на необязательный пароль для проверки подлинности
 - **password_length**: длина необязательного пароля для проверки подлинности
 - **total_bytes**: общее число отправляемых байтов ресурса Обратите внимание, что совокупная длина всех пакетов, отправленных через последующие вызовы *nx_http_client_put_packet*, должна равняться этому значению.
 - **wait_option** определяет, как долго служба будет ожидать запуск запроса PUT HTTP-клиента Параметры ожидания определяются следующим образом:
    - **Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Выбор параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.

    Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — запрос PUT успешно отправлен.
 - **NX_HTTP_USERNAME_TOO_LONG** (0xF1) — слишком длинное имя пользователя для буфера
 - **NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
 - NX_SIZE_ERROR (0x09) — недопустимый общий размер ресурса.
 - NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, 9, “myname”, 6, “mypassword”, 10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nxd_http_client_put_start"></a>nxd_http_client_put_start

Запуск HTTP-запроса PUT (IPv4 или IPv6)

### <a name="prototype"></a>Прототип

```c
UINT nxd_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               NXD_ADDRESS *server_ip, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба пытается отправить запрос PUT (на отправку) с указанным ресурсом к HTTP-серверу по указанному IP-адресу через IPv6. Если эта подпрограмма выполняется успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_http_client_put_packet()* , чтобы фактически отправить содержимое ресурса на HTTP-сервер.

> [!NOTE]
> Строка ресурса может ссылаться на локальный файл, например ``` “/index.htm” ```, или на другой URL-адрес, например ```http://abc.website.com/index.htm```, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется перейти на использование *nx_http_client_put_start_extended()* .

### <a name="input-parameters"></a>Входные параметры

 - **client_ptr** — указатель на блок управления HTTP-клиентом.
 - **server_ip** — IP-адрес HTTP-сервера.
 - **resource** — указатель на строку URL-адреса для ресурса, отправляемого на сервер.
 - **username**: указатель на необязательное имя пользователя для проверки подлинности
 - **password**: указатель на необязательный пароль для проверки подлинности.
 - **total_bytes**: общее число отправляемых байтов ресурса Обратите внимание, что совокупная длина всех пакетов, отправленных через последующие вызовы *nx_http_client_put_packet*, должна равняться этому значению.
 - **wait_option** определяет, как долго служба будет ожидать запуск запроса PUT HTTP-клиента Параметры ожидания определяются следующим образом:
    - **Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Выбор параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.

    Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — запрос PUT HTTP-клиента успешно отправлен.
 - **NX_HTTP_ERROR** (0xE0) — внутренняя ошибка HTTP-клиента.
 - **NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.
 - **NX_HTTP_FAILED** (0xE2) — ошибка HTTP-клиента при взаимодействии с HTTP-сервером.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
 - NX_SIZE_ERROR (0x09) — недопустимый общий размер ресурса.
 - NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start(&my_client, &server_ip_address,
                                    "/client_test.htm", "name", "password", 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nxd_http_client_put_start_extended"></a>nxd_http_client_put_start_extended

Запуск HTTP-запроса PUT (IPv4 или IPv6)

### <a name="prototype"></a>Прототип

```c
UINT nxd_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
          NXD_ADDRESS *server_ip, CHAR *resource, UINT resource_length,
          CHAR *username, UINT username_length, CHAR *password,
          UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба пытается отправить запрос PUT (на отправку) с указанным ресурсом к HTTP-серверу по указанному IP-адресу через IPv6. Если эта подпрограмма выполняется успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_http_client_put_packet()* , чтобы фактически отправить содержимое ресурса на HTTP-сервер.

> [!NOTE]
> Строка ресурса может ссылаться на локальный файл, например ``` “/index.htm” ```, или на другой URL-адрес, например ```http://abc.website.com/index.htm```, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.

Эта служба заменяет *nxd_http_client_put_start()* . Она требует от вызывающей стороны указания длины ресурса, имени пользователя и пароля.

### <a name="input-parameters"></a>Входные параметры

 - **client_ptr**: указатель на блок управления HTTP-клиентом.
 - **ip_address**: IP-адрес HTTP-сервера
 - **resource** — указатель на строку URL-адреса запрошенного ресурса.
 - **resource_length** — длина строки URL-адреса для ресурса, отправляемого на сервер.
 - **username**: указатель на необязательное имя пользователя для проверки подлинности
 - **username_length**: длина необязательного имени пользователя для проверки подлинности
 - **password**: указатель на необязательный пароль для проверки подлинности
 - **password_length**: длина необязательного пароля для проверки подлинности
 - **total_bytes**: общее число отправляемых байтов ресурса Обратите внимание, что совокупная длина всех пакетов, отправленных через последующие вызовы *nx_http_client_put_packet*, должна равняться этому значению.
 - **wait_option** определяет, как долго служба будет ожидать запуск запроса PUT HTTP-клиента Параметры ожидания определяются следующим образом:
    - **Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Выбор параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.

    Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — запрос PUT HTTP-клиента успешно отправлен.
 - **NX_HTTP_ERROR** (0xE0) — внутренняя ошибка HTTP-клиента.
 - **NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.
 - NX_HTTP_FAILED (0xE2) — ошибка HTTP-клиента при взаимодействии с HTTP-сервером.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
 - NX_SIZE_ERROR (0x09) — недопустимый общий размер ресурса.
 - NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NXD_ADDRESS server_ip_address;

/* for an IPv4 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V4;
server_ip_address.nxd_ip_address.v4 = IP_ADDRESS(1,2,3,4);

/* for an IPv6 address, define as follows: */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0x0;
server_ip_address.nxd_ip_address.v6[2] = 0xf101;
server_ip_address.nxd_ip_address.v6[3] = 0x106;

/* Start an HTTP PUT to place the 20-byte resource Client_test.HTM” on the HTTPv6  
   Server. */
status =  nxd_http_client_put_start_extended(&my_client, &server_ip_address,
                                            "/client_test.htm", 16, "name", 4, "password", 8, 103, 50);

/* If status is NX_SUCCESS, the PUT operation for Client_test.HTM has successfully
   been started. */
```

## <a name="nx_http_client_put_packet"></a>nx_http_client_put_packet

Отправка следующего пакета данных ресурса

### <a name="prototype"></a>Прототип

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET *packet_ptr,
                               ULONG wait_option);
```

### <a name="description"></a>Описание

Эта служба пытается отправить следующий пакет содержимого ресурса на HTTP-сервер.

> [!NOTE]
> Эту подпрограмму следует вызывать несколько раз до тех пор, пока суммарная длина отправляемых пакетов не будет равна значению total_bytes, указанному в предыдущем вызове *nx_http_client_put_start()* .

### <a name="input-parameters"></a>Входные параметры

 - **client_ptr**: указатель на блок управления HTTP-клиентом.
 - **packet_ptr**: указатель на следующее содержимое ресурса, отправляемого на HTTP-сервер
 - **wait_option** определяет, как долго служба будет внутренне ожидать обработки пакета PUT HTTP-клиента Параметры ожидания определяются следующим образом:
    - **Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)
    - **TX_WAIT_FOREVER** (0xFFFFFFFF)

    Выбор параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.

    Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — пакет HTTP-клиента успешно отправлен.
 - **NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.
 - **NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) — получен код ошибки сервера.
 - **NX_HTTP_BAD_PACKET_LENGTH** (0xED) — недопустимая длина пакета.
 - **NX_HTTP_AUTHENTICATION_ERROR** (0xEB) — недопустимое имя и (или) пароль.
 - **NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) — сервер отвечает до завершения запроса PUT.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
 - NX_INVALID_PACKET (0x12) — слишком маленький пакет для заголовка TCP
 - NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Send a 20-byte packet representing the content of the resource
   “/TEST.HTM” to the HTTP Server. */
status =  nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr, NX_PACKET *packet_ptr, ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
   successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a>nx_http_client_set_connect_port

Задание порта подключения к серверу

### <a name="prototype"></a>Прототип

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                      UINT port);
```

### <a name="description"></a>Описание

При подключении к HTTP-серверу эта служба изменяет порт подключения на указанный порт во время выполнения. В противном случае по умолчанию используется порт 80. Эту службу необходимо вызвать до *nx_http_client_get_start()* и *nx_http_client_put_start()* , например, когда HTTP-клиент подключается к серверу.

### <a name="input-parameters"></a>Входные параметры

 - **client_ptr** — указатель на блок управления HTTP-клиентом.
 - **port** — порт для подключения к серверу.

### <a name="return-values"></a>Возвращаемые значения

 - Порт **NX_SUCCESS** (0X00) — порт успешно изменен.
 - NX_INVALID_PORT (0x46) — превышено максимальное значение номера порта (0xFFFF), или номер равен нулю.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки, инициализация

### <a name="example"></a>Например, .

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status =  nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a>nx_http_server_cache_info_callback_set

Задание обратного вызова для получения максимального возраста и даты URL-адреса

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                         UINT (*cache_info_get)(CHAR *resource,
                                                 UINT *max_age,
                                                 NX_HTTP_SERVER_DATE
                                                      *date));
```

### <a name="description"></a>Описание

Эта служба задает службу обратного вызова, вызываемую для получения максимального возраста и даты последнего изменения указанного ресурса.

### <a name="input-parameters"></a>Входные параметры

 - **server_ptr**: указатель на блок управления HTTP-сервером.
 - **cache_info_get**: указатель на обратный вызов
 - **max_age**: указатель на максимальный возраст ресурса
 - **data**: указатель на возвращенную дату последнего изменения.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — обратный вызов успешно задан.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Инициализация

### <a name="example"></a>Например, .

```c
NX_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
                           NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP  
   server is set by nx_http_server_start(), set the cache info callback: */

status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);


/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a>nx_http_server_callback_data_send

Отправка данных из функции обратного вызова

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                       VOID *data_ptr,
                                       ULONG data_length);
```

### <a name="description"></a>Описание

Эта служба отправляет данные в предоставленном пакете из подпрограммы обратного вызова приложения. Обычно она используется для отправки динамических данных, связанных с запросами GET/POST.

> [!NOTE]
> Если используется эта функция, подпрограмма обратного вызова отвечает за отправку всего ответа в правильном формате. Кроме того, подпрограмма обратного вызова должна возвращать состояние NX_HTTP_CALLBACK_COMPLETED.

### <a name="input-parameters"></a>Входные параметры

 - **server_ptr**: указатель на блок управления HTTP-сервером.
 - **data_ptr** — указатель на данные для отправки.
 - **data_length** — число отправляемых байтов.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — данные сервера успешно отправлены.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
  CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
                (strcmp(resource, "/test.htm") == 0))
    {

        /* Found it, override the GET processing by sending the resource
    contents directly. */

        nx_http_server_callback_data_send(server_ptr,
    "HTTP/1.0 200 \r\nContent-Length:
    103\r\nContent-Type: text/html\r\n\r\n",
    63);

        nx_http_server_callback_data_send(server_ptr, "<HTML>\r\n<HEAD><TITLE>NetX
    HTTP Test </TITLE></HEAD>\r\n
    <BODY>\r\n<H1>NetX Test Page
    </H1>\r\n</BODY>\r\n</HTML>\r\n", 103);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a>nx_http_server_callback_generate_response_header

Создание заголовка ответа в функции обратного вызова

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_callback_generate_response_header(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT content_length,
                        CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a>Описание

Эта служба вызывает внутреннюю функцию *_nx_http_server_generate_response_header*, когда HTTP-сервер отвечает на запросы GET, PUT и DELETE клиента. Ее нужно использовать в функциях обратного вызова HTTP-сервера, когда приложение HTTP-сервера формирует ответ клиенту.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется перейти на использование *nxd_http_server_callback_generate_response_header_extended()* .

### <a name="input-parameters"></a>Входные параметры

 - **server_ptr**: указатель на блок управления HTTP-сервером.
 - **packet_pptr**: указатель на указатель пакета, выделенный для сообщения
 - **status_code**: указывает состояние ресурса Примеры:
    - **NX_HTTP_STATUS_OK**
    - **NX_HTTP_STATUS_MODIFIED**
    - **NX_HTTP_STATUS_INTERNAL_ERROR**
 - **content_length**: размер содержимого в байтах
 - **content_type**: тип HTTP, например text/plain
 - **additional_header** — указатель на дополнительный текст заголовка.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — заголовок успешно создан.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
            Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
                  &resp_packet_ptr, NX_HTTP_STATUS_OK,
                  length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
                 nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
       nx_packet_release(resp_packet_ptr);
       return status;
   }



/* Now send the packet! */
           status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                      resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
      nx_packet_release(resp_packet_ptr);

      return status;
   }

/* Let HTTP server know the response has been sent. */
  return NX_HTTP_CALLBACK_COMPLETED;

     }
```

## <a name="nx_http_server_callback_generate_response_header_extended"></a>nx_http_server_callback_generate_response_header_extended

Создание заголовка ответа в функции обратного вызова

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_callback_generate_response_header_extended(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT status_code_length,
                        UINT content_length,
                        CHAR *content_type, UINT content_type_length,
                        CHAR *additional_header,
                        UINT additional_header_length);
```

### <a name="description"></a>Описание

Эта служба вызывает внутреннюю функцию *_nx_http_server_generate_response_header()* , когда HTTP-сервер отвечает на запросы GET, PUT и DELETE клиента. Ее нужно использовать в функциях обратного вызова HTTP-сервера, когда приложение HTTP-сервера формирует ответ клиенту.

Эта служба заменяет *nx_http_server_callback_generate_response_header()* . Эта версия предоставляет дополнительные сведения о длине функции обратного вызова.

### <a name="input-parameters"></a>Входные параметры

 - **server_ptr**: указатель на блок управления HTTP-сервером.
 - **packet_pptr**: указатель на указатель пакета, выделенный для сообщения
 - **status_code**: указывает состояние ресурса Примеры:
    - **NX_HTTP_STATUS_OK**
    - **NX_HTTP_STATUS_MODIFIED**
    - **NX_HTTP_STATUS_INTERNAL_ERROR**
 - **status_code** Длина кода состояния.
 - **content_length**: размер содержимого в байтах
 - **content_type**: тип HTTP, например text/plain
 - **content_type_length**: длина типа HTTP
 - **additional_header**: указатель на дополнительный текст заголовка
 - **additional_header_length**: длина дополнительного текста заголовка.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — заголовок успешно создан.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
CHAR demotestbuffer[] = "<html>\r\n\r\n<head>\r\n\r\n<title>Main   \
     Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n   \  </body>\r\n</html>\r\n";

     /* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
 CHAR *resource, NX_PACKET *recv_packet_ptr)
      {

NX_PACKET   *sresp_packet_ptr;
ULONG       string_length;
CHAR        temp_string[30];
ULONG       length = 0;


   length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length =  (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr ->
nx_http_server_request_resource, temp_string,
sizeof(temp_string));

       /* Null terminate the string. */
   temp_string[temp] = 0;

       /* Now build a response header with server status is OK and no additional header  
          info. */
   status = nx_http_server_callback_generate_response_header_extended(
                             http_server_ptr, &resp_packet_ptr, NX_HTTP_STATUS_OK,
              sizeof(NX_HTTP_STATUS_OK) - 1, length,
              temp_string, string_length, NX_NULL, 0);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
                 length,  server_ptr ->
                 nx_http_server_packet_pool_ptr, NX_WAIT_FOREVER);
   if (status != NX_SUCCESS)
   {
       nx_packet_release(resp_packet_ptr);
       return status;
   }



/* Now send the packet! */
           status = nx_tcp_socket_send(&(server_ptr -> nx_http_server_socket),
                                      resp_packet_ptr, NX_HTTP_SERVER_TIMEOUT_SEND);

   if (status != NX_SUCCESS)
   {
      nx_packet_release(resp_packet_ptr);

      return status;
   }

/* Let HTTP server know the response has been sent. */
  return NX_HTTP_CALLBACK_COMPLETED;

     }
```

## <a name="nx_http_server_callback_packet_send"></a>nx_http_server_callback_packet_send

Отправка пакета HTTP из функции обратного вызова

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr);
```

### <a name="description"></a>Описание

Эта служба отправляет полный ответ HTTP-сервера из обратного вызова HTTP. HTTP-сервер отправит пакет с NX_HTTP_SERVER_TIMEOUT_SEND. К пакету должны быть добавлены заголовок и данные HTTP. Если возвращаемое состояние указывает на ошибку, приложение HTTP должно освободить пакет.

Обратный вызов должен возвращать NX_HTTP_CALLBACK_COMPLETED.

Более подробный пример см. в описании *nx_http_server_callback_generate_response_header()* .

### <a name="input-parameters"></a>Входные параметры

 - **server_ptr** — указатель на управляющий блок HTTP-сервера.
 - **packet_ptr** — указатель на пакет для отправки.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — пакет сервера успешно отправлен.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* The packet is appended with HTTP header and data and is ready to send to the
   Client directly. */

   status = nx_http_server_callback_response_send(server_ptr, packet_ptr);

   if (status != NX_SUCCESS)
   {

    nx_packet_release(packet_ptr);
   }

    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a>nx_http_server_callback_response_send

Отправка ответа из функции обратного вызова

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
                                           CHAR *header,
                                           CHAR *information,
                                           CHAR additional_info);
```

### <a name="description"></a>Описание

Эта служба отправляет указанные сведения об ответе из подпрограммы обратного вызова приложения. Обычно она используется для отправки пользовательских ответов, связанных с запросами GET/POST.

> [!NOTE]
> Если используется эта функция, подпрограмма обратного вызова должна возвращать состояние NX_HTTP_CALLBACK_COMPLETED.

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется перейти на использование *nxd_http_server_callback_response_send_extended()* .

### <a name="input-parameters"></a>Входные параметры

 - **server_ptr**: указатель на блок управления HTTP-сервером.
 - **header**: указатель на строку заголовка ответа
 - **information**: указатель на строку информации.
 - **additional_info**: указатель на строку дополнительной информации.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — ответ сервера успешно отправлен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send(server_ptr,
                      "HTTP/1.0 404 ",
                      "NetX HTTP Server unable to find  
                       file: ", resource);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_response_send_extended"></a>nx_http_server_callback_response_send_extended

Отправка ответа из функции обратного вызова

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_callback_response_send_extended(
                                          NX_HTTP_SERVER *server_ptr,
                                          CHAR *header,
                                          UINT header_length,
                                          CHAR *information,
                                          UINT information_length,
                                          CHAR *additional_info,
                                          UINT additional_info_length);
```

### <a name="description"></a>Описание

Эта служба отправляет указанные сведения об ответе из подпрограммы обратного вызова приложения. Обычно она используется для отправки пользовательских ответов, связанных с запросами GET/POST.

> [!NOTE]
> Если используется эта функция, подпрограмма обратного вызова должна возвращать состояние NX_HTTP_CALLBACK_COMPLETED.

Эта служба заменяет *nx_http_server_callback_response_send()* . Эта версия принимает дополнительные сведения о длине в качестве аргументов.

### <a name="input-parameters"></a>Входные параметры

 - **server_ptr**: указатель на блок управления HTTP-сервером.
 - **header**: указатель на строку заголовка ответа
 - **header_length**: длина строки заголовка ответа.
 - **information**: указатель на строку информации
 - **information_length**: длина строки информации
 - **additional_info**: указатель на строку дополнительной информации
 - **additional_info_length**: длина строки дополнительной информации.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — ответ сервера успешно отправлен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                        CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource!  */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
               (strcmp(resource, "/test.htm") == 0))
    {

        /* In this example, we will complete the GET processing with
           a resource not found response. */
     nx_http_server_callback_response_send_extended(
                                             server_ptr,
                      "HTTP/1.0 404 ", 12,
                      "NetX HTTP Server unable to find  
                       file: ", 38, resource, 9);

        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }

    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a>nx_http_server_content_get

Получение содержимого из запроса

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

### <a name="description"></a>Описание

Эта служба пытается получить указанный объем содержимого из запроса POST или PUT HTTP-клиента. Ее следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_http_server_create*).

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется перейти на использование *nx_http_server_content_get_extended()* .

### <a name="input-parameters"></a>Входные параметры

 - **server_ptr**: указатель на блок управления HTTP-сервером.
 - **packet_ptr**: указатель на пакет запроса HTTP-клиента. Обратите внимание, что этот пакет не должен быть освобожден обратным вызовом уведомления о запросе.
 - **byte_offset**: число байтов для смещения в область содержимого
 - **destination_ptr**: указатель на область назначения для содержимого
 - **destination_size**: максимальное число байтов, доступных в области назначения
 - **actual_size**: указатель на переменную назначения, в качестве значения которой будет задан фактический размер копируемого содержимого.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — содержимое HTTP-сервера успешно получено.
 - **NX_HTTP_ERROR** (0xE0) — внутренняя ошибка HTTP-сервера.
 - **NX_HTTP_DATA_END** (0xE7) — конец содержимого запроса.
 - **NX_HTTP_TIMEOUT** (0xE1) — время ожидания HTTP-сервера в получении следующего пакета содержимого.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
 - NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get(&my_server, packet_ptr,
                      0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_get_extended"></a>nx_http_server_content_get_extended

Получение содержимого из запроса или поддержка содержимого нулевой длины

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr,
                                         ULONG byte_offset,
                                         CHAR *destination_ptr,
                                         UINT destination_size,
                                         UINT *actual_size);
```

### <a name="description"></a>Описание

Эта служба почти идентична службе *nx_http_server_content_get()* . Она пытается получить указанный объем содержимого из запроса POST или PUT HTTP-клиента. Однако она обрабатывает запросы с содержимым нулевой длины (пустые запросы) как допустимые. Ее следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_http_server_create()* ).

Эта служба заменяет *nx_http_server_content_get()* . Эта версия требует, чтобы вызывающий объект указал дополнительные сведения о длине.

### <a name="input-parameters"></a>Входные параметры

 - **server_ptr**: указатель на блок управления HTTP-сервером.
 - **packet_ptr**: указатель на пакет запроса HTTP-клиента. Обратите внимание, что этот пакет не должен быть освобожден обратным вызовом уведомления о запросе.
 - **byte_offset**: число байтов для смещения в область содержимого
 - **destination_ptr**: указатель на область назначения для содержимого
 - **destination_size**: максимальное число байтов, доступных в области назначения
 - **actual_size**: указатель на переменную назначения, в качестве значения которой будет задан фактический размер копируемого содержимого.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — содержимое HTTP-запроса успешно получено.
 - **NX_HTTP_ERROR** (0xE0) — внутренняя ошибка HTTP-сервера.
 - **NX_HTTP_DATA_END** (0xE7) — конец содержимого запроса.
 - **NX_HTTP_TIMEOUT** (0xE1) — время ожидания HTTP-сервера в получении следующего пакета.
 - NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.
 - NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get_extended(&my_server, packet_ptr,
                               0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_length_get"></a>nx_http_server_content_length_get

Получение длины содержимого в запросе

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```

### <a name="description"></a>Описание

Эта служба пытается получить длину содержимого HTTP в указанном пакете. Если содержимое HTTP отсутствует, эта подпрограмма возвращает нулевое значение. Ее следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_http_server_create()* ).

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется перейти на использование *nx_http_server_content_length_get_extended()* .

### <a name="input-parameters"></a>Входные параметры

 - **packet_ptr**: указатель на пакет запроса HTTP-клиента. Обратите внимание, что этот пакет не должен быть освобожден обратным вызовом уведомления о запросе.

### <a name="return-values"></a>Возвращаемые значения

 - **content_length** — при возникновении ошибки возвращается нулевое значение.  

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
length =  nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
   request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a>nx_http_server_content_length_get_extended

Получение длины содержимого в запросе или поддержка содержимого нулевой длины

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                                UINT *content_length);
```

### <a name="description"></a>Описание

Эта служба аналогична службе *nx_http_server_content_length_get;* . Она пытается получить длину содержимого HTTP в указанном пакете. Однако возвращаемое значение указывает на состояние успешного завершения, а фактическое значение длины возвращается в параметре```content_length``` входного указателя. Если содержимого HTTP нет или длина содержимого равна нулю, эта подпрограмма по-прежнему возвращает состояние выполнения, а указатель ввода content_length указывает на допустимую длину (ноль). Ее следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_http_server_create*).

Эта служба заменяет *nx_http_server_content_length_get()* .

### <a name="input-parameters"></a>Входные параметры

 - **packet_ptr**: указатель на пакет запроса HTTP-клиента. Обратите внимание, что этот пакет не должен быть освобожден обратным вызовом уведомления о запросе.
 - **content_length**: указатель на значение, полученное из поля длины содержимого.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — содержимое сервера успешно получено.
 - **NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) — недопустимый формат заголовка HTTP.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
ULONG content_length;

status =  nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
   contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a>nx_http_server_create

Создание экземпляра HTTP-сервера

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_create(NX_HTTP_SERVER *http_server_ptr,
      CHAR *http_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr,
      VOID *stack_ptr, ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*authentication_check)(NX_HTTP_SERVER *server_ptr,
            UINT request_type, CHAR *resource, CHAR **name,
            CHAR **password, CHAR **realm),
      UINT (*request_notify)(NX_HTTP_SERVER *server_ptr,
            UINT request_type, CHAR *resource, NX_PACKET *packet_ptr));
```

### <a name="description"></a>Описание

Эта служба создает экземпляр HTTP-сервера, который выполняется в контексте собственного потока ThreadX. Необязательные подпрограммы обратного вызова приложений *authentication_check* и request_notify позволяют программному обеспечению приложения управлять основными операциями HTTP-сервера.

### <a name="input-parameters"></a>Входные параметры

 - **http_server_ptr**: указатель на блок управления HTTP-сервером.
 - **http_server_name**: указатель на имя HTTP-сервера
 - **ip_ptr**: указатель на ранее созданный экземпляр IP
 - **media_ptr**: указатель на ранее созданный экземпляр носителя FileX
 - **stack_ptr**: указатель на область стека потока HTTP-сервера
 - **stack_ptr**: указатель на размер стека потока HTTP-сервера
 - **authentication_check**: указатель функции на подпрограмму проверки подлинности приложения Если параметр указан, эта подпрограмма вызывается для каждого запроса HTTP-клиента. Если этот параметр имеет значение NULL, проверка подлинности выполняться не будет.
 - **request_notify** — указатель функции на подпрограмму уведомления о запросе приложения. Если параметр указан, подпрограмма вызывается перед обработкой запроса HTTP-сервером. Это позволяет перенаправлять имя ресурса или обновлять поля в самом ресурсе до завершения запроса HTTP-клиента.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00): HTTP-сервер успешно создан.
 - NX_PTR_ERROR (0x07) — недопустимый указатель на HTTP-сервер, IP-адрес, носитель, стек или пул пакетов
 - NX_HTTP_POOL_ERROR (0xE9) — полезные данные пакета пула недостаточно велики, чтобы содержать полный HTTP-запрос.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Create an HTTP Server instance called “my_server.”  */
status =  nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
              stack_ptr, stack_size, &pool_0,
              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a>nx_http_server_delete

Удаление экземпляра HTTP-сервера

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет ранее созданный экземпляр HTTP-сервера.

### <a name="input-parameters"></a>Входные параметры

 - **http_server_ptr**: указатель на блок управления HTTP-сервером.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — HTTP-сервер успешно удален.
 - NX_PTR_ERROR (0x07) — недопустимый указатель на HTTP-сервер.
 - NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Delete the HTTP Server instance called “my_server.”  */
status =  nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a>nx_http_server_get_entity_content

Получение расположения и длины данных сущности

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_pptr,
                                       ULONG *available_offset,
                                       ULONG *available_length);
```

### <a name="description"></a>Описание

Эта служба определяет расположение начала данных в текущем составном объекте в полученных сообщениях клиента, а также длину данных, не включая граничную строку. HTTP-сервер внутренне обновляет собственные смещения, чтобы эту функцию можно было повторно вызывать в той же клиентской датаграмме для сообщений с несколькими сущностями. Указатель пакета обновляется до следующего пакета, где сообщение клиента является датаграммой с несколькими пакетами.

> [!NOTE]
> Для использования этой службы необходимо включить NX_HTTP_MULTIPART_ENABLE.

Дополнительные сведения см. в описании [*nx_http_server_get_entity_header*](#nx_http_server_get_entity_header).

### <a name="input-parameters"></a>Входные параметры

 - **server_ptr**: указатель на HTTP-сервер.
 - **packet_pptr**: указатель на расположение указателя пакета Обратите внимание, что приложение не должно освобождать этот пакет.
 - **available_offset**: указатель на смещение данных сущности от указателя начала пакета
 - **available_length**: указатель на длину данных сущности.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — размер и расположение содержимого сущности успешно получены.
 - **NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) — содержимое для внутренних многокомпонентных маркеров HTTP-сервера уже найдено.
 - NX_HTTP_ERROR (0xE0) — внутренняя ошибка HTTP.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NX_HTTP_SERVER my_server;

UINT        offset, length;
NX_PACKET  *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
   the entity header to determine details about the multipart data. If
   successful, it then calls this service to get the location of entity data: */

status =  nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
&length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
   entity data. */
```

## <a name="nx_http_server_get_entity_header"></a>nx_http_server_get_entity_header

Получение содержимого заголовка сущности

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      UCHAR *entity_header_buffer,
                                      ULONG buffer_size);
```

### <a name="description"></a>Описание

Эта служба извлекает заголовок сущности в указанный буфер. HTTP-сервер внутренне обновляет собственные указатели для поиска следующей составной сущности в датаграмме клиента с несколькими заголовками сущностей. Указатель пакета обновляется до следующего пакета, где сообщение клиента является датаграммой с несколькими пакетами.

> [!NOTE]
> Для использования этой службы необходимо включить NX_HTTP_MULTIPART_ENABLE.

### <a name="input-parameters"></a>Входные параметры

 - **server_ptr**: указатель на HTTP-сервер.
 - **packet_pptr**: указатель на расположение указателя пакета Обратите внимание, что приложение не должно освобождать этот пакет.
 - **entity_header_buffer**: указатель на расположение для хранения заголовка сущности
 - **buffer_size**: размер входного буфера.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — заголовок сущности успешно получен.
 - **NX_HTTP_NOT_FOUND** **(0xE6)**  — поле заголовка сущности не найдено.
 - **NX_HTTP_TIMEOUT** **(0xE1)**  — истекло время для получения следующего пакета для сообщения клиента с несколькими пакетами.
 - NX_HTTP_ERROR (0xE0) — внутренняя ошибка HTTP.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
 - NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* my_request_notify is the application request notify callback registered with
      the HTTP server in nx_http_server_create, creates a response to the received  
      Client request. */

      UINT  my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                              CHAR *resource, NX_PACKET *packet_ptr)
      {

        NX_PACKET   *sresp_packet_ptr;
        UINT        offset, length;
        NX_PACKET   *response_pkt;
        UCHAR       buffer[1440];

        /* Process multipart data. */
        if(request_type == NX_HTTP_SERVER_POST_REQUEST)
        {

       /* Get the content header. */
       while(nx_http_server_get_entity_header(server_ptr, &packet_ptr, buffer,
                                         sizeof(buffer)) == NX_SUCCESS)
   {

      /* Header obtained successfully. Get the content data location. */
      while(nx_http_server_get_entity_content(server_ptr, &packet_ptr, &offset,
                                              &length) == NX_SUCCESS)
      {
           /* Write content data to buffer. */
           nx_packet_data_extract_offset(packet_ptr, offset, buffer, length,
                                         &length);
           buffer[length] = 0;
      }

    }

    /* Generate HTTP header. */
    status = nx_http_server_callback_generate_response_header(server_ptr,
                         &response_pkt, NX_HTTP_STATUS_OK, 800, "text/html",
                         "Server: NetXDuo HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
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
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a>nx_http_server_gmt_callback_set

Задание обратного вызова для получения даты и времени по Гринвичу

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

### <a name="description"></a>Описание

Эта служба задает обратный вызов для получения даты и времени в формате GMT с помощью ранее созданного HTTP-сервера. Эта служба вызывается HTTP-сервером и создает заголовок в ответах HTTP-сервера для клиента.

### <a name="input-parameters"></a>Входные параметры

 - **server_ptr** — указатель на HTTP-сервер.
 - **gmt_getv** — указатель на обратный вызов GMT.
 - **datev** — указатель на полученную дату.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — обратный вызов успешно задан.
 - NX_PTR_ERROR (0x07) — недопустимый указатель на пакет или параметр.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the GMT
   retrieve callback: */

status =  nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
   response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a>nx_http_server_invalid_userpassword_notify_set

Задание обратного вызова для обработки недопустимого имени пользователя и пароля

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_invalid_userpassword_notify_set(
            NX_HTTP_SERVER *http_server_ptr,
            UINT (*invalid_username_password_callback)
                        (CHAR *resource,
                        NXD_ADDRESS *client_address,
                        UINT request_type));
```

### <a name="description"></a>Описание

Эта служба задает обратный вызов, вызываемый при получении недопустимого имени пользователя и пароля в запросе GET, PUT или DELETE клиента в результате дайджест- или обычной проверки подлинности. HTTP-сервер должен быть создан ранее.

### <a name="input-parameters"></a>Входные параметры

 - **server_ptr**: указатель на HTTP-сервер.
 - **invalid_username_password_callback**: указатель на недопустимый обратный вызов имени пользователя или пароля
 - **resource** — указатель на ресурс, указанный клиентом.
 - **client_address** — указатель на адрес клиента. Разрешено использовать IPv4 или IPv6.
 - **request_type** — указывает на тип запроса клиента. Может иметь следующие значения:
    - NX_HTTP_SERVER_GET_REQUEST
    - NX_HTTP_SERVER_POST_REQUEST
    - NX_HTTP_SERVER_HEAD_REQUEST
    - NX_HTTP_SERVER_PUT_REQUEST
    - NX_HTTP_SERVER_DELETE_REQUEST

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — обратный вызов успешно задан.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                         NXD_ADDRESS *client_address,
                                         UINT   request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the invalid
   username password callback: */

status =  nx_http_server_gmt_callback_set(&my_server,
                                          invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
   will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a>nx_http_server_mime_maps_additional_set

Задание дополнительных сопоставлений MIME для HTML

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_mime_maps_additional_set(
                        NX_HTTP_SERVER *server_ptr,
                        NX_HTTP_SERVER_MIME_MAP *mime_maps,
                        UINT mime_maps_num);
```

### <a name="description"></a>Описание

Эта служба позволяет разработчику приложений HTTP добавлять дополнительные типы MIME из типов MIME по умолчанию, предоставляемых HTTP-сервером NetX Duo (см. *nx_http_server_get_type*, чтобы получить сведения о списке определенных типов).

Если получен запрос клиента, например запрос GET, HTTP-сервер анализирует запрошенный тип файла из заголовка HTTP с помощью дополнительно заданного сопоставления MIME и, если совпадений не найдено, ищет соответствие в сопоставлении MIME по умолчанию HTTP-сервера. Если совпадений не найдено, по умолчанию используется тип MIME text/plain.

Если функция уведомления о запросе зарегистрирована на HTTP-сервере, обратный вызов уведомления о запросе может вызвать *nx_http_server_type_retrieve()* для анализа типа файла.

### <a name="input-parameters"></a>Входные параметры

 - **server_ptr**: указатель на экземпляр HTTP-сервера.
 - **mime_maps**: указатель на массив сопоставлений MIME
 - **mime_map_num**: число сопоставлений MIME в массиве.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — сопоставление MIME HTTP-сервера успешно задано.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc",      "yourtype/abc"},
    {"xyz",      "mytype/xyz"},
};

status =  nx_http_server_mime_maps_additional_set(&my_server,
                                                  &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP  
  server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a>nx_http_server_packet_content_find

Извлечение длины содержимого и установка указателя на начало данных

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET **packet_ptr,
                                        UINT *content_length);
```

### <a name="description"></a>Описание

Эта служба извлекает длину содержимого из заголовка HTTP. Она также обновляет указанный пакет следующим образом: перед указателем начала пакета (начало расположения буфера пакета для записи) задается содержимое HTTP (данные), только что переданное заголовком HTTP.

Если в текущем пакете не найдено начало содержимого, функция ожидает получения следующего пакета с помощью параметра ожидания NX_HTTP_SERVER_TIMEOUT_RECEIVE.

> [!NOTE]
> Этот параметр не следует вызывать перед вызовом *nx_http_server_get_entity_header*, поскольку он изменяет указатель в начале после заголовка сущности.

### <a name="input-parameters"></a>Входные параметры

 - **server_ptr**: указатель на экземпляр HTTP-сервера.
 - **packet_ptr** — указатель на указатель пакета для возврата пакета с обновленным указателем начала.
 - **content_length** — указатель на извлеченный параметр ```content_length```.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — длина содержимого HTTP обнаружена, и пакет успешно обновлен.
 - **NX_HTTP_TIMEOUT** (0xE1) — истекло время ожидания следующего пакета.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function
registered with the HTTP server. */

UINT content_length;

status =  nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                             &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
   and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a>nx_http_server_packet_get

Получение следующего пакета HTTP

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

### <a name="description"></a>Описание

Эта служба возвращает следующий пакет, полученный через сокет HTTP-сервера. Для получения пакета используется параметр ожидания NX_HTTP_SERVER_TIMEOUT_RECEIVE.

### <a name="input-parameters"></a>Входные параметры

 - **server_ptr**: указатель на экземпляр HTTP-сервера.
 - **packet_ptr**: указатель на полученный пакет.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — следующий пакет успешно получен.
 - **NX_HTTP_TIMEOUT** (0xE1) — истекло время ожидания следующего пакета.
 - NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status =  nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a>nx_http_server_param_get

Получение параметра из запроса

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                              UINT param_number, CHAR *param_ptr,
                              UINT max_param_size);
```

### <a name="description"></a>Описание

Эта служба пытается получить указанный параметр URL-адреса HTTP в указанном пакете запроса. Если запрашиваемый параметр HTTP отсутствует, подпрограмма возвращает состояние NX_HTTP_NOT_FOUND. Эту подпрограмму следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_http_server_create*).

### <a name="input-parameters"></a>Входные параметры

 - **packet_ptr**: указатель на пакет запроса HTTP-клиента. Обратите внимание, что приложение не должно освобождать этот пакет.
 - **param_number**: логический номер параметра, начинающийся с нуля, слева направо в списке параметров
 - **param_ptr**: область назначения для копирования параметра
 - **max_param_size** — максимальный размер области назначения параметра.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — параметр HTTP-сервера успешно получен.
 - **NX_HTTP_NOT_FOUND** (0xE6) — указанный параметр не найден
 - **NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) — неправильное завершение параметра запроса
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
 - NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first parameter of the HTTP Client request. */

status =  nx_http_server_param_get(request_packet_ptr, 0, param_destination,
               30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
   in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a>nx_http_server_query_get

Получение запроса из запроса

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                   CHAR *query_ptr, UINT max_query_size);
```

### <a name="description"></a>Описание

Эта служба пытается получить указанный HTTP-запрос URL-адреса в указанном пакете запроса. Если запрашиваемый HTTP-запрос отсутствует, подпрограмма возвращает состояние NX_HTTP_NOT_FOUND. Эту подпрограмму следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_http_server_create*).

### <a name="input-parameters"></a>Входные параметры

 - **packet_ptr**: указатель на пакет запроса HTTP-клиента. Обратите внимание, что приложение не должно освобождать этот пакет.
 - **query_number**: логический номер параметра, начинающийся с нуля, слева направо в списке запросов
 - **query_ptr**: область назначения для копирования запроса
 - **max_query_size** — максимальный размер области назначения запроса.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — запрос HTTP-сервера успешно получен.
 - **NX_HTTP_FAILED** (0xE2) — слишком маленький размер запроса.
 - **NX_HTTP_NOT_FOUND** (0xE6) — указанный запрос не найден.
 - **NX_HTTP_NO_QUERY_PARSED** (0xF2) — нет запроса в запросе клиента.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
 - NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first query of the HTTP Client request. */
status =  nx_http_server_query_get(request_packet_ptr, 0, query_destination,
                30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
   in “query_destination.” */
```

## <a name="nx_http_server_start"></a>nx_http_server_start

Запуск HTTP-сервера

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Описание

Эта служба запускает ранее созданный экземпляр HTTP-сервера.

### <a name="input-parameters"></a>Входные параметры

 - **http_server_ptr**: указатель на экземпляр HTTP-сервера.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — сервер успешно запущен.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Инициализация, потоки

### <a name="example"></a>Например, .

```c
/* Start the HTTP Server instance “my_server.”  */
status =  nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a>nx_http_server_stop

Остановка HTTP-сервера

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a>Описание

Эта служба останавливает ранее созданный экземпляр HTTP-сервера. Эту подпрограмму следует вызывать до удаления экземпляра HTTP-сервера.

### <a name="input-parameters"></a>Входные параметры

 - **http_server_ptr**: указатель на экземпляр HTTP-сервера.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — сервер успешно остановлен.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
 - NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Например, .

```c
/* Stop the HTTP Server instance “my_server.”  */
status =  nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a>nx_http_server_type_get

Извлечение типа файла из HTTP-запроса клиента

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                             CHAR *name, CHAR *http_type_string);
```

### <a name="description"></a>Описание

> [!NOTE]
> использовать эту службу больше не рекомендуется. Пользователям рекомендуется использовать службу *nx_http_server_type_retrieve()* .

Эта служба извлекает тип HTTP-запроса в буфере http_type_string и его длину в возвращаемом значении из имени входного буфера (обычно это URL-адрес). Если сопоставление MIME не найдено, по умолчанию используется тип text/plain. В противном случае извлеченный тип сравнивается с сопоставлениями MIME HTTP-сервера по умолчанию. Сопоставления MIME по умолчанию в HTTP-сервере NetX Duo:

 - **HTML** — текст или HTML.
 - **HTM** — текст или HTML.
 - **TXT** — текст или обычный текст.
 - **GIF** — изображение или GIF.
 - **JPEG** — изображение или JPEG.
 - **ICO** — изображение или x-icon.

Если задать, оно также будет искать определенный пользователем набор дополнительных сопоставлений MIME. Дополнительные сведения об определяемых пользователем сопоставлениях см. в описании *nx_http_server_mime_maps_addtional_set()* .

использовать эту службу больше не рекомендуется. Разработчикам рекомендуется перейти на использование *nx_http_server_type_get_extended()* .

### <a name="input-parameters"></a>Входные параметры

 - **http_server_ptr** — указатель на экземпляр HTTP-сервера.
 - **name** — указатель на буфер для поиска.
 - **http_type_string** — указатель на извлеченный тип HTML.

### <a name="return-values"></a>Возвращаемые значения

 - **Длина строки в байтах** — ненулевое значение означает успешную операцию. Нуль означает ошибку.

### <a name="allowed-from"></a>Допустимые источники

Приложение

### <a name="example"></a>Например, .

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

## <a name="nx_http_server_type_get_extended"></a>nx_http_server_type_get_extended

Извлечение типа файла из HTTP-запроса клиента

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_type_get_extended(
                                    NX_HTTP_SERVER *http_server_ptr,
                                    CHAR *name, CHAR *http_type_string,
                                    UINT http_type_string_max_size);
```

### <a name="description"></a>Описание

Эта служба извлекает тип HTTP-запроса в буфере *http_type_string* и его длину в возвращаемом значении из *имени* входного буфера (обычно это URL-адрес). Если сопоставление MIME не найдено, по умолчанию используется тип text/plain. В противном случае извлеченный тип сравнивается с сопоставлениями MIME HTTP-сервера по умолчанию. Сопоставления MIME по умолчанию в HTTP-сервере NetX Duo:

 - **HTML** — текст или HTML.
 - **HTM** — текст или HTML.
 - **TXT** — текст или обычный текст.
 - **GIF** — изображение или GIF.
 - **JPEG** — изображение или JPEG.
 - **ICO** — изображение или x-icon.

Если задать, оно также будет искать определенный пользователем набор дополнительных сопоставлений MIME. Дополнительные сведения об определяемых пользователем сопоставлениях см. в описании *nx_http_server_mime_maps_addtional_set()* .

Эта служба заменяет *nx_http_server_type_get ()* . Эта версия предоставляет дополнительные сведения о длине.

### <a name="input-parameters"></a>Входные параметры

 - **http_server_ptr**: указатель на экземпляр HTTP-сервера.
 - **name**: указатель на буфер для поиска
 - **name_length**: длина буфера для поиска
 - **http_type_string** — указатель на извлеченный тип HTML.
 - **http_type_string_max_size** — размер буфера http_type_string.

### <a name="return-values"></a>Возвращаемые значения

 - **Длина строки в байтах** — ненулевое значение означает успешную операцию. Нуль означает ошибку.

### <a name="allowed-from"></a>Допустимые источники

Приложение

### <a name="example"></a>Например, .

```c
/* my_server is a previously created HTTP server, which starts accepting client
   requests when nx_http_server_start is called*/

CHAR temp_string[20];
UINT string_length;

/* Get the length of request resource. */
    if (_nx_utility_string_length_check(
                    my_server.nx_http_server_request_resource, &resource_length,
                    sizeof(my_server.nx_http_server_request_resource) - 1))
           {
               return;
           }

/* Extract the HTTP type. */
    string_length =  nx_http_server_type_get_extended(&my_server,
               my_server.nx_http_server_request_resource, resource_length,
               temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

Более подробный пример см. в описании для [*nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header).

## <a name="nx_http_server_digest_authenticate_notify_set"></a>nx_http_server_digest_authenticate_notify_set

Задание функции обратного вызова дайджест-проверки подлинности

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_digest_authenticate_notify_set(
       NX_HTTP_SERVER *http_server_ptr,
       UINT (*digest_authenticate_callback)(NX_HTTP_SERVER *server_ptr,
                                            CHAR *name_ptr,
                                            CHAR *realm_ptr,
                                            CHAR *password_ptr,
                                            CHAR *method,
                                            CHAR *authorization_uri,
                                            CHAR *authorization_nc,
                                            CHAR *authorization_cnonce
                                           ));
```

### <a name="description"></a>Описание

Эта служба задает обратный вызов, вызываемый при выполнении дайджест-проверки подлинности.

### <a name="input-parameters"></a>Входные параметры

 - **http_server_ptr**: указатель на экземпляр HTTP-сервера.
 - **digest_authenticate_callback**: указатель на обратный вызов дайджест-проверки подлинности.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — обратный вызов успешно задан.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.
 - NX_NOT_SUPPORTED (0x4B) — дайджест-проверка подлинности не включена.

### <a name="allowed-from"></a>Допустимые источники

Приложение

### <a name="example"></a>Например, .

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                  CHAR *realm_ptr, CHAR *password_ptr, CHAR *method,
                                  CHAR *authorization_uri, CHAR *authorization_nc,
                                  CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the digest authenticate callback: */

status =  nx_http_server_digest_authenticate_notify_set (&my_server,
    digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
   will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a>nx_http_server_authentication_check_set

Задание функции обратного вызова проверки для проверки подлинности

### <a name="prototype"></a>Прототип

```c
UINT nx_http_server_authentication_check_set(
       NX_HTTP_SERVER *http_server_ptr,
       UINT (*authentication_check_extended)(
                                            NX_HTTP_SERVER *server_ptr,
                                            UINT request_type,
                                            CHAR *resource,
                                            CHAR **name,
                                            UINT *name_length,
                                            CHAR **password,
                                            UINT *password_length,
                                            CHAR **realm,
                                            UINT *realm_length
                                            ));
```

### <a name="description"></a>Описание

Эта служба задает функцию обратного вызова проверки для проверки подлинности.

### <a name="input-parameters"></a>Входные параметры

 - **http_server_ptr** — указатель на экземпляр HTTP-сервера.
 - **authentication_check_extended** — указатель на проверку для проверки подлинности приложения.

### <a name="return-values"></a>Возвращаемые значения

 - **NX_SUCCESS** (0x00) — обратный вызов успешно задан.
 - NX_PTR_ERROR (0x07): недопустимые входные данные указателя.

### <a name="allowed-from"></a>Допустимые источники

Приложение

### <a name="example"></a>Пример

```c
static UINT  authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                           UINT request_type, CHAR *resource,
                                           CHAR **name, UINT *name_length,
                                           CHAR **password, UINT *password_length,
                                           CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
       requests and resources. */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and before
   starting HTTP services when nx_http_server_start is called, set the
   authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                         authentication_check_extended);
```
