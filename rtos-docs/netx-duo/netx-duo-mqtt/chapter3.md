---
title: Глава 3. Описание служб клиента ОСРВ Azure NetX Duo MQTT
description: В этой главе приведено описание всех служб клиента NetX Duo MQTT (см. ниже) в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cc08f7c0dceb84d5843e25384275557d2871e3546d90579aab006119a2d9980c
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797523"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-mqtt-client-services"></a>Глава 3. Описание служб клиента ОСРВ Azure NetX Duo MQTT

В этой главе приведено описание всех служб клиента ОСРВ Azure NetX Duo MQTT (см. ниже) в алфавитном порядке.

В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, используемым для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.

- **nxd_mqtt_client_create** *Создание экземпляра клиента MQTT*
- **nxd_mqtt_client_will_message_set** *Установка сообщения LWT*
- **nxd_mqtt_client_client_login_set** *Установка имени пользователя и пароля для доступа к клиенту MQTT*
- **nxd_mqtt_client_connect** *Подключение клиента MQTT к брокеру*
- **nxd_mqtt_client_secure_connect** *Подключение клиента MQTT к брокеру по протоколу TLS*
- **nxd_mqtt_client_publish** *Публикация сообщения через брокера.*
- **nxd_mqtt_client_subscribe** *Подписка на раздел*
- **nxd_mqtt_client_unsubscribe** *Отписка от раздела*
- **nxd_mqtt_client_receive_notify_set** *Установка функции обратного вызова для уведомления о сообщении MQTT о получении*
- **nxd_mqtt_client_message_get** *Получение сообщения от брокера*
- **nxd_mqtt_client_disconnect_notify_set** *Установка функции обратного вызова для уведомления о сообщении MQTT об отключении*
- **nxd_mqtt_client_disconnect** *Отключение клиента MQTT от брокера*
- **nxd_mqtt_client_delete** *Удаление экземпляра клиента MQTT*

## <a name="nxd_mqtt_client_create"></a>nxd_mqtt_client_create

Создание экземпляра клиента MQTT

### <a name="prototype"></a>Прототип

```c
UINT nxd_mqtt_client_create(NXD_MQTT_CLIENT *client_ptr,
    CHAR *client_name, CHAR *client_id,
    UINT client_id_length, NX_IP *ip_ptr, NX_PACKET_POOL
    *pool_ptr, VOID *stack_ptr, ULONG stack_size, UINT
    mqtt_thread_priority,
    VOID *memory_ptr, ULONG memory_size);
```

### <a name="description"></a>Описание

Эта служба создает экземпляр клиента MQTT в указанном IP-адресе экземпляра. Строка *client_id* передается на сервер во время фазы подключения MQTT в качестве *идентификатора клиента (ClientId)* . Он также создает необходимые ресурсы ThreadX (поток задач клиента MQTT, мьютекс, группу флагов событий и сокет TCP).

### <a name="input-parameters"></a>Входные параметры

- **client_ptr** Указатель на блок управления клиентом MQTT.
- **client_name** Строка имени клиента.
- **client_id** Строка идентификатора клиента, используемая во время фазы подключения. Брокер MQTT использует client_id для уникальной идентификации клиента.
- **client_id_length** Длина строки идентификатора клиента в байтах.
- **ip_ptr** Указатель на экземпляр IP-адреса.
- **pool_ptr** Указатель на пул пакетов, который клиент MQTT использует для своей работы.
- **stack_ptr** Область стека для потока клиента MQTT.
- **stack_size** Размер области стека в байтах.
- **mqtt_thread_priority** Приоритет потока MQTT.
- **memory_ptr** Не рекомендуется. Больше не используется.
- **memory_size** Не рекомендуется. Больше не используется.

### <a name="return-values"></a>Возвращаемые значения

- **NXD_MQTT_SUCCESS** (0x00) – клиент MQTT успешно создан.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) – внутренняя логическая ошибка
- NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT, ip_ptr или указатель на пул пакетов.
- NXD_MQTT_INVALID_PARAMETER (0x10009) – недопустимая строка раздела сообщений LWT, значение will_retrain_flag или will_QoS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
#define CLIENT_ID_STRING "My Test Client"

#define MQTT_THREAD_PRIORITY 2

NXD_MQTT_CLIENT my_client;
NX_IP ip_0; /* Assume ip_0 is created prior to MQTT client creation. */
NX_PACKET_POOL pool_0;/* Assume pool_0 is created prior to MQTT client creation. */
UCHAR mqtt_thread_stack[STACK_SIZE];

/* Create the MQTT Client instance on "ip_0". */
status = **nxd_mqtt_client_create**(&my_client, "my client",
    CLIENT_ID_STRING, stlren(CLIENT_ID_STRING),
    &ip_0, &pool_0, (VOID*)mqtt_thread_stack, STACK_SIZE,
    MQTT_THREAD_PRIORITY, NX_NULL, 0);

/* If status is NXD_MQTT_SUCCESS an MQTT Client instance was successfully created. */
```

## <a name="nxd_mqtt_client_will_message_set"></a>nxd_mqtt_client_will_message_set

Установка сообщения LWT

### <a name="prototype"></a>Прототип

```c
UINT nxd_mqtt_client_will_message_set(NXD_MQTT_CLIENT
    *client_ptr,
    Const UCHAR *will_topic,
    UINT will_topic_length
    Const UCHAR *will_message,
    UINT will_message_length,
    UINT will_retain_flag,
    UINT will_QoS);
```

### <a name="description"></a>Описание

Эта служба устанавливает необязательный раздел LWT сообщение LWT, прежде чем клиент начнет подключение к серверу. Раздел LWT должен быть строкой в формате UTF-8.

Сообщение LWT, если оно задано, передается брокеру в составе сообщения CONNECT. Поэтому приложение, которое будет использовать сообщение LWT, должно использовать эту службу до подключения MQTT.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr** Указатель на блок управления клиентом MQTT.
- **will_topic** Строка раздела LWT в формате UTF-8. Раздел LWT является обязательным. Пока выполняется вызов *nx_mqtt_client_connect*, вызывающий объект должен считать строку will_topic допустимой.
- **will_topic_length** Число байтов в строке раздела LWT
- **will_message** Сообщение LWT, заданное приложением. Если сообщение LWT не требуется, приложение может задать для этого поля значение *NX_NULL.*
- **will_message_length** Число байтов в строке сообщения LWT. Если will_message имеет значение NULL, для will_message_length должно быть задано значение 0.
- **will_retain_flag** Включение/отключение публикации сервером сообщения LWT в виде сохраняемого сообщения. Допустимые значения: *NX_TRUE* или *NX_FALSE.*
- **will_QoS** Значение QoS, используемое сервером при отправке сообщения LWT. Допустимы значения 0 или 1.  

### <a name="return-values"></a>Возвращаемые значения

- **NXD_MQTT_SUCCESS** (0X00) – сообщение LWT успешно создано.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) – сообщения QoS уровня 2 не поддерживаются.
- NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT.
- NXD_MQTT_INVALID_PARAMETER (0x10009) – недопустимая строка раздела сообщений LWT, значение will_retrain_flag или will_QoS.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
#define WILL_TOPIC "my_will_topic"

#define WILL_MESSAGE "my will message"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_will_message_set(&my_client,
    WILL_TOPIC, STRLEN(WILL_TOPIC),
    WILL_MESSAGE, STRLEN(WILL_MESSAGE),
    NX_TRUE, 0);

/* If status is NXD_MQTT_SUCCESS the will message is properly
configured for the session. It will be transmitted to the server
during MQTT connection. */
```

## <a name="nxd_mqtt_client_login_set"></a>nxd_mqtt_client_login_set

Задает имя пользователя и пароль для доступа к клиенту MQTT

### <a name="prototype"></a>Прототип

```c
UINT nxd_mqtt_client_login_set(NXD_MQTT_CLIENT *client_ptr,
    Const UCHAR *username,
    UINT username_length
    Const UCHAR *password,
    UINT password_length);
```

### <a name="description"></a>Описание

Эта служба задает имя пользователя и пароль, которые используются на этапе подключения MQTT для проверки подлинности при входе в систему.

Данные для доступа к клиенту MQTT (имя пользователя и пароль) являются необязательными. В ситуациях, когда серверу требуется имя пользователя и пароль, их необходимо задать до установки соединения.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr** Указатель на блок управления клиентом MQTT.
- **username** Строка имени пользователя в кодировке UTF-8. Пока выполняется вызов *nx_mqtt_client_connect*, вызывающий объект должен считать строку username допустимой.
- **username_length** Число байтов в строке username
- **password** Строка пароля. Если пароль не требуется, для этого поля можно установить значение NX_NULL.

### <a name="return-values"></a>Возвращаемые значения

- **NXD_MQTT_SUCCESS** (0X00) – сообщение LWT успешно создано.
- NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT.
- NXD_MQTT_INVALID_PARAMETER (0x10009) – недопустимая строка username или password.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
#define USERNAME "MY_NAME"

#define PASSWORD "MY_LOGIN_SECRET"

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_login_set(&my_client,
    USERNAME, STRLEN(USERNAME),
    PASSWORD, STRLEN(PASSWORD));

/* If status is NXD_MQTT_SUCCESS the username and the password 
are set for the session. This information will be 
transmitted to the server during MQTT connection. */
```

## <a name="nxd_mqtt_client_connect"></a>nxd_mqtt_client_connect

Подключение клиента MQTT к брокеру

### <a name="prototype"></a>Прототип

```c
UINT nxd_mqtt_client_connect(NXD_MQTT_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT keepalive, UINT clean_session, ULONG wait_option));
```

### <a name="description"></a>Описание

Эта служба инициирует подключение к брокеру. Сначала она привязывает TCP-сокет, а затем устанавливает соединение по протоколу TCP. Затем она создает таймер, если ошибок не возникло и функция проверки активности MQTT включена. Затем она подключается к серверу MQTT (брокеру).

Обратите внимание, что эта служба создает соединение с MQTT без защиты по протоколу TLS. Чтобы создать безопасное соединение с MQTT, приложение должно использовать службу ***nxd_mqtt_client_secure_connect ().***

Если при подключении клиент задает для *clean_session* значение NX_FALSE, клиент повторно передает все хранящиеся в нем сообщения, которые еще не подтверждены.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr** Указатель на блок управления клиентом MQTT.
- **server_ip** IP-адрес брокера.
- **server_port** Номер порта брокера. Порт по умолчанию для MQTT определяется как **_NXD_MQTT_PORT_** (1883).
- **keep_alive** Значение проверки активности в секундах, которое будет использоваться во время сеанса. Значение указывает максимальный временной интервал между двумя сообщениями управления MQTT, отправляемыми брокеру до того, как брокер зафиксирует истечение времени ожидания клиента. Значение 0 отключает функцию проверки активности.
- **clean_session** Указывает, должен ли сервер запускать этот сеанс с нуля. Допустимые значения: **_NX_TRUE_ *_ или _* _NX_FALSE._**
- **wait_option** Время ожидания подключения.

### <a name="return-values"></a>Возвращаемые значения

- **NXD_MQTT_SUCCESS** (0X00) – успешное подключение MQTT
- **NXD_MQTT_ALREADY_CONNECTED** (0x10001) – клиент уже подключен к брокеру.
- **NXD_MQTT_MUTEX_FAILURE** (0X10003) – не удалось получить мьютекс MQTT 
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) – внутренняя логическая ошибка
- **NXD_MQTT_CONNECT_FAILURE** (0X10005) – не удалось подключиться к брокеру.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) – не удалось отправить сообщения брокеру.
- **NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) – сервер ответил с ошибкой
- **NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) – код отклика сервера
- **NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) – код отклика сервера
- **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) – код отклика сервера
- **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) – код отклика сервера
- **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) – код отклика сервера
- NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT, ip_ptr или указатель на пул пакетов

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_connect(&my_client, &broker_address,
    NXD_MQTT_PORT,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session flag set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS a connection to the broker is successfully established. */
```

## <a name="nxd_mqtt_client_secure_connect"></a>nxd_mqtt_client_secure_connect

Подключение клиента MQTT к брокеру по протоколу защиты TLS

### <a name="prototype"></a>Прототип

```c
UINT nxd_mqtt_client_secure_connect(NXD_MQTT_CLIENT
    *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NXD_MQTT_CLIENT *,
        NX_SECURE_TLS_SESISON *,
        NX_SECURE_TLS_CERTIFICATE *,
        NX_SECURE_TLS_CERTIFICATE *),
    UINT keepalive, UINT connection_flag,
    UINT clean_session, ULONG wait_option));
```

### <a name="description"></a>Описание

Эта служба идентична службе ***nxd_mqtt_client_connect*** за исключением того, что соединение проходит через уровень TLS, а не TCP. Таким образом, обеспечивается защита связи между клиентом и брокером.

*tls_setup* — это определяемая пользователем функция обратного вызова, которую клиент MQTT использует перед созданием соединения с клиентом MQTT. Приложение должно инициализировать NetX Secure TLS, настроить параметры безопасности и загрузить соответствующие сертификаты для использования при подтверждении TLS. Фактическое подтверждение TLS происходит после установки соединения с портом MQTT TLS брокера по протоколу TCP (порт TCP по умолчанию: 8883). После успешного подтверждения TLS пакет управления MQTT CONNECT отправляется по протоколу TLS.

Чтобы обеспечить безопасное подключение, должна быть доступна библиотека NetX Secure TLS, а клиент NetX Duo MQTT должен быть создан с использованием службы ***NX_SECURE_ENABLE***.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr** Указатель на блок управления клиентом MQTT.
- **server_ip** IP-адрес брокера.
- **server_port** Номер порта брокера. Порт по умолчанию для MQTT определяется как **_NXD_MQTT_TLS_PORT_** (8883).
- **tls_setup** Предоставляемая пользователем функция обратного вызова для настройки TLS. Эта функция обратного вызова вызывается для настройки параметров подключения клиента TLS.
- **keep_alive** Значение проверки активности, которое будет использоваться во время сеанса. Значение 0 отключает функцию проверки активности.
- **clean_session** Указывает, должен ли сервер запускать этот сеанс с нуля. Допустимые значения: **_NX_TRUE_ *_ или _* _NX_FALSE._**
- **wait_option** Время ожидания подключения.

### <a name="return-values"></a>Возвращаемые значения

- **NXD_MQTT_SUCCESS** (0X00) – успешное подключение клиента MQTT по протоколу TLS.
- **NXD_MQTT_ALREADY_CONNECTED** (0x10001) – клиент уже подключен к брокеру.
- **NXD_MQTT_MUTEX_FAILURE** (0X10003) – не удалось получить мьютекс MQTT 
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) – внутренняя логическая ошибка
- **NXD_MQTT_CONNECT_FAILURE** (0X10005) – не удалось подключиться к брокеру.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) – не удалось отправить сообщения брокеру.
- **NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) – сервер ответил с сообщением об ошибке.
- **NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) – код отклика сервера
- **NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) – код отклика сервера
- **NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) – код отклика сервера
- **NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) – код отклика сервера
- **NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) – код отклика сервера
- NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT или структура адреса сервера.
- NX_INVALID_PORT (0x46) – значение порта сервера не может быть нулевым.
- NXD_MQTT_INVALID_PARAMETER (0x10009) – ошибка входного параметра
- NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT – поток MQTT еще не запущен.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* TLS setup routine. This function is responsible for setting up TLS parameters.*/
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate,
    UINT timeout)
{
/* Note this routine is simplified to highlight the
necessary steps to setup a TLS session. Each
application may employ different procedures suitable for
its TLS settings, such as cipher suite, certificates. */

/* Create a TLS session for the MQTT connection, and pass
in various crypto methods this session can use for the
initial TLS handshake. */

/* Load appropriate certificates, or set up session key for Pre-share key operation. */

/* Start the TLS session */

/* Return NX_SUCCESS if the TLS session is established. */
    return(NX_SUCCESS);
}

NXD_ADDRESS broker_address;

/* Set up broker IP address */
broker_address.nxd_ip_version = 4;
broker_address.nxd_ip_address.v4 = MQTT_BROKER_ADDRESS;

/* Create the MQTT Client instance "my_client" on "ip_0". */
status = nxd_mqtt_client_secure_connect(&my_client,
    &server_address, NXD_MQTT_TLS_PORT, tls_setup_callback,
    0, /* Turn off keepalive */
    NX_TRUE, /* Clean session set */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the MQTT Client was successfully connected to the broker via TLS. */
```

## <a name="nxd_mqtt_client_publish"></a>nxd_mqtt_client_publish

Публикация сообщения через брокер

### <a name="prototype"></a>Прототип

```c
UINT nxd_mqtt_client_publish(NXD_MQTT_CLIENT *client_ptr,
    CHAR *topic_name, UINT topic_name_length, CHAR *message, UINT
    message_length,
    UINT retain, UINT QoS, ULONG timeout);
```

### <a name="description"></a>Описание

Эта служба публикует сообщение через брокер. Публикация сообщений QoS уровня 2 пока не поддерживается.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr** Указатель на блок управления клиентом MQTT.
- **topic_name** Раздел для публикации.
- **topic_name_length** Длина раздела в байтах.
- **message** Указатель на буфер сообщений.
- **message_length** Размер сообщения в байтах
- **retain** Определяет, должен ли брокер хранить сообщение.
- **QoS** Рекомендуемое значение качества обслуживания: 0 или 1.
- **timeout** Значение времени ожидания

### <a name="return-values"></a>Возвращаемые значения

- **NXD_MQTT_SUCCESS** (0x00) – клиент MQTT успешно создан
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) – внутренняя логическая ошибка.
- **NXD_MQTT_PACKET_POOL_FAILURE** (0x10006) – не удалось получить пакет из пула пакетов.
- **NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) – не удалось связаться с брокером.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) – сообщения QoS уровня 2 не поддерживаются.
- NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT, ip_ptr или указатель на пул пакетов
- NXD_MQTT_INVALID_PARAMETER (0x10009) – ошибка входного параметра

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
CHAR *topic = "temperature";
CHAR *message = "100";

/* Publish the temperature value. */
status = nxd_mqtt_client_publish(&my_client,
    topic, STRLEN(topic),
    message, STRLEN(message),
    NX_TRUE, /* Server retains message. */);
    0, /* QOS */
    NX_WAIT_FOREVER);

/* If status is NXD_MQTT_SUCCESS the message has been 
successfully sent to the broker. */
```

## <a name="nxd_mqtt_client_subscribe"></a>nxd_mqtt_client_subscribe

Оформление подписки на тему

### <a name="prototype"></a>Прототип

```c
UINT nxd_mqtt_client_subscribe(NXD_MQTT_CLIENT
    *mqtt_client_ptr, CHAR *topic_name,
    UINT topic_name_length, UINT QoS);
```

### <a name="description"></a>Описание

Эта служба подписывается на конкретный раздел. Подписка на сообщения QoS уровня 2 пока не поддерживается.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr** Указатель на блок управления клиентом MQTT.
- **topic_name** Раздел для публикации.
- **topic_name_length** Длина раздела в байтах.
- **QoS Рекомендуемый уровень качества обслуживания:** 0 или 1.

### <a name="return-values"></a>Возвращаемые значения

- **NXD_MQTT_SUCCESS** (0x00) – подписка на раздел успешно выполнена.
- **NXD_MQTT_NOT_CONNECTED** (0x10002) – клиент не подключен к брокеру.
- **NXD_MQTT_MUTEX_FAILURE** (0X10003) – не удалось получить мьютекс MQTT
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) – внутренняя логическая ошибка
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) – не удалось отправить сообщения брокеру.
- **NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) – сообщения QoS уровня 2 не поддерживаются.
- NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT, ip_ptr или указатель на пул пакетов
- NXD_MQTT_INVALID_PARAMETER (0x10009) – значение topic_name не задано, значение topic_name_length равно нулю либо значение качества обслуживания недопустимо.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_subscribe(&my_client, topic,
    STRLEN(topic), 0);

/* If status is NXD_MQTT_SUCCESS, the client successfully
subscribes to the topic "temperate". At this point the client
is ready for receiving messages from the broker. */
```

## <a name="nxd_mqtt_client_unsubscribe"></a>nxd_mqtt_client_unsubscribe

Отмена подписки на раздел

### <a name="prototype"></a>Прототип

```c
UINT nxd_mqtt_client_unsubscribe(NXD_MQTT_CLIENT
    *mqtt_client_pr,
    CHAR *topic_name,
    UINT topic_name_length);
```

### <a name="description"></a>Описание

Эта служба отменяет подписку на раздел.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr** Указатель на блок управления клиентом MQTT.
- **topic_name** Раздел, от которого необходимо отписаться.
- **topic_name_length** Длина раздела в байтах.

### <a name="return-values"></a>Возвращаемые значения

- **NXD_MQTT_SUCCESS** (0x00) – подписка на раздел успешно отменена.
- **NXD_MQTT_NOT_CONNECTED** (0x10002) – клиент не подключен к брокеру.
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) – не удалось получить мьютекс MQTT.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) – внутренняя логическая ошибка
- **NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) – не удалось отправить сообщения брокеру.
- NX_PTR_ERROR (0x07) – недопустимый указатель на блок управления MQTT.
- NXD_MQTT_INVALID_PARAMETER (0x10009) – значение topic_name не задано или значение topic_name_length равно нулю.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_unsubscribe(&my_client, topic,
    STRLEN(topic));

/* If status is NXD_MQTT_SUCCESS, the client successfully
unsubscribes the topic "temperate". */
```

## <a name="nxd_mqtt_client_receive_notify_set"></a>nxd_mqtt_client_receive_notify_set

Установка функции обратного вызова для уведомления о сообщении MQTT о получении

### <a name="prototype"></a>Прототип

```c
UINT nxd_mqtt_client_receive_notify_set(NXD_MQTT_CLIENT
    *client_ptr,
    VOID(*receive_notify)(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count));
```

### <a name="description"></a>Описание

Эта служба регистрирует функцию обратного вызова с клиентом MQTT. При получении сообщения, опубликованного брокером, клиент MQTT сохраняет сообщение в очередь получения. Если функция обратного вызова задана, она активируется, чтобы уведомить приложение о том, что сообщение готово к извлечению. Функция уведомления о получении принимает указатель на блок управления клиентом MQTT и значение *message_count*, указывающее количество сообщений, доступных в очереди получения. Обратите внимание, что в период с момента уведомления о получении до момента, когда приложение извлекает эти сообщения, количество сообщений может измениться, поскольку в этот период могут поступить новые сообщения.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr** Указатель на блок управления клиентом MQTT.
- **receive_notify** Задаваемая пользователем функция обратного вызова будет активирована при получении сообщения.

### <a name="return-values"></a>Возвращаемые значения

- **NXD_MQTT_SUCCESS** (0x00) – функция уведомления о получении сообщений успешно задана.
- NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Sample MQTT receive notify function. */

VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count)
{

/* On receiving a message, set an event flag to wake up the
application thread. The message will be received and
processed in the application thread. */
tx_event_flags_set(&mqtt_app_flag,
    MESSAGE_RECEIVED_EVENT, TX_OR);

/* All done. Return to the caller. */
    return;
}

/* Set the receive callback function. */
status = **nxd_mqtt_client_receive_notify_set**(&my_client,
    my_notify_func);

/* If status is NXD_MQTT_SUCCESS the notify function is properly set. */
```

## <a name="nxd_mqtt_client_message_get"></a>nxd_mqtt_client_message_get

Извлечение сообщения из брокера

### <a name="prototype"></a>Прототип

```c
UINT nxd_mqtt_client_message_get(NXD_MQTT_CLIENT
    *client_ptr,
    UCHAR *topic_buffer, UINT topic_buffer_size,
    UINT *actual_topic_length, UCHAR *message_buffer,
    UINT message_buffer_size, UINT *actual_message_length);
```

### <a name="description"></a>Описание

Эта служба извлекает сообщение, опубликованное брокером. Все входящие сообщения хранятся в очереди получения. Приложение использует эту службу для извлечения этих сообщений. Этот вызов не блокируется. Если очередь получения пуста, эта служба возвращает ***NXD_MQTT_NO_MESSAGE** _. Приложение, которое должно получать уведомление о входящем сообщении, может вызвать службу _ *_nxd_mqtt_client_receive_notify_set_** для регистрации функции обратного вызова для получения.

Вызывающий объект должен предоставить место для сохранения строки раздела и текста сообщения. Размеры этих двух буферов передаются с помощью служб *topic_buffer_size* и *message_buffer_size*. Фактическое число байтов в строке раздела и тексте сообщения возвращаются с помощью *actual_topic_length* и *actual_message_length*. Если длина раздела или сообщения превышает выделенный объем буфера, эта служба возвращает код ошибки *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.

Приложение должно выделить буфер большего размера и повторить попытку.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr** Указатель на блок управления клиентом MQTT.
- **topic_buffer** Указатель на место в памяти для копирования строки раздела.
- **topic_buffer_size** Размер буфера раздела.
- **actual_topic_length** Указатель на место в памяти для возвращаемого значения фактической длины раздела.
- **topic_buffer** Указатель на место в памяти для копирования строки сообщения.
- **message_buffer_size** Размер буфера сообщений.
- **actual_message_length** Указатель на место в памяти для возвращаемого значения длины сообщения.

### <a name="return-values"></a>Возвращаемые значения

- **NXD_MQTT_SUCCESS** (0x00) – сообщение успешно извлечено.
- **NXD_MQTT_INTERNAL_ERROR** (0x10004) – внутренняя логическая ошибка
- **NXD_MQTT_NO_MESSAGE** (0x1000A) – очередь получения пуста.
- **NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) – размер буфера раздела или сообщения слишком мал для раздела или сообщения.
- NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT, ip_ptr или указатель на пул пакетов
- NXD_MQTT_INVALID_PARAMETER (0x10009) – указатель message_buffer или topic_buffer имеет значение NULL

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
UCHAR topic[MAX_TOPIC_SIZE];
UCHAR message[MAX_TOPIC_SIZE];
UINT topic_length;
UINT message_length;

/* Retrieve a message from MQTT client receive queue. */
status = nxd_mqtt_client_message_get(&my_client, topic,
    sizeof(topic), &topic_length, message, sizeof(message),
    &message_length);

/* Check the return value. */
if(status == NXD_MQTT_SUCCESS)
{
/* A message is received. All done. */
}
else if (status == NXD_MQTT_NO_MESSAGE)
{
/* No more messages in the receive queue. All done. */
}
else
{
/* Receive error. */
}
```

## <a name="nxd_mqtt_client_disconnect_notify_set"></a>nxd_mqtt_client_disconnect_notify_set

Установка функции обратного вызова для уведомления о сообщении MQTT об отключении

### <a name="prototype"></a>Прототип

```c
UINT nxd_mqtt_client_disconnect_notify_set(
    NXD_MQTT_CLIENT *client_ptr,
    VOID(*disconnect_notify)(NXD_MQTT_CLIENT* client_ptr));
```

### <a name="description"></a>Описание

Эта служба регистрирует функцию обратного вызова с клиентом MQTT. Когда MQTT обнаруживает, что соединение с брокером прервано, он вызывает эту функцию для оповещения приложения. Таким образом, приложение может использовать эту функцию обратного вызова для обнаружения прерванного соединения и для восстановления подключения к брокеру.

```c
VOID callback_func(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="input-parameters"></a>Входные параметры

- **client_ptr** Указатель на блок управления клиентом MQTT.
- **disconnect_notify** Задаваемая пользователем функция обратного вызова, которая активируется, когда MQTT обнаруживает, что соединение с брокером прервано.

### <a name="return-values"></a>Возвращаемые значения

- **NXD_MQTT_SUCCESS** (0x00) – функция уведомления об отключении успешно задана.
- NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT.

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
VOID disconnect_notify(NXD_MQTT_CLIENT *client_ptr)
{
/* MQTT client is disconnected from the broker. Notify the application so it can re-connect to the broker. */
}

status = nxd_mqtt_client_disconnect_notify_set(client_ptr,
    disconnect_notify);
```

## <a name="nxd_mqtt_client_disconnect"></a>nxd_mqtt_client_disconnect

Отключение клиента MQTT от брокера

### <a name="prototype"></a>Прототип

```c
UINT nxd_mqtt_client_disconnect(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Эта служба отключает клиент от брокера. Обратите внимание, что сообщения в очереди получения освобождаются. Сообщения с QoS 1 в очереди передачи не освобождаются. После повторного подключения клиента к серверу можно обработать сообщения QoS 1, если клиент не подключится к серверу с флагом *clean_session*, для которого установлено значение ***NX_TRUE***.

Если установлено подключение с защитой TLS, эта служба перед отключением соединения по TCP закроет сеанс TLS.

Фактический вызов отключения сокета TCP имеет параметр ожидания, задаваемый с помощью службы NXD_MQTT_SOCKET_TIMEOUT (такты таймера). По умолчанию используется значение NX_WAIT_FOREVER. Чтобы избежать неограниченной приостановки в случае прерывания сетевого соединения или отсутствия ответа от сервера, установите для этого параметра конечное значение.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr** Указатель на блок управления клиентом MQTT.

### <a name="return-values"></a>Возвращаемые значения

- **NXD_MQTT_SUCCESS** (0x00) – успешное отключение от брокера
- **NXD_MQTT_MUTEX_FAILURE** (0x10003) – не удалось получить мьютекс MQTT.
- NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Disconnect from the broker. */
status = nxd_mqtt_client_disconnect(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
disconnected from the broker. */
```

## <a name="nxd_mqtt_client_delete"></a>nxd_mqtt_client_delete

Удаление экземпляра клиента MQTT

### <a name="prototype"></a>Прототип

```c
UINT nxd_mqtt_client_delete(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a>Описание

Эта служба удаляет экземпляр клиента MQTT и освобождает внутренние ресурсы. Эта служба автоматически отключает клиент от брокера, если он по-прежнему подключен. Сообщения, которые еще не были отправлены или не подтверждены, освобождаются. Также освобождаются сообщения, полученные, но не извлеченные приложением.

Если установлено подключение с защитой TLS, эта служба перед отключением соединения по TCP закрывает сеанс TLS.

После удаления клиента приложение, желающее использовать службу MQTT, должно создать новый экземпляр.

### <a name="input-parameters"></a>Входные параметры

- **client_ptr** Указатель на блок управления клиентом MQTT.

### <a name="return-values"></a>Возвращаемые значения

- **NXD_MQTT_SUCCESS** (0x00) – клиент MQTT успешно удален.
- NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT

### <a name="allowed-from"></a>Допустимые источники

Потоки

### <a name="example"></a>Пример

```c
/* Delete the MQTT client instance. */
status = nxd_mqtt_client_delete(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
deleted from the system. */
```
