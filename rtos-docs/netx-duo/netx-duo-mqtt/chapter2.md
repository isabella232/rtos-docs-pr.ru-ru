---
title: Глава 2. Установка и использование клиента MQTT для NetX Duo (ОСРВ Azure)
description: В этой главе описываются различные вопросы, связанные с установкой, настройкой и использованием клиента MQTT для NetX Duo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4e27a6738456a90f3d708789f51b0471868c6f9e
ms.sourcegitcommit: 4842f4cfe9e31b3ac59059f43e598eb70faebc8f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/20/2021
ms.locfileid: "122601316"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-mqtt-client"></a>Глава 2. Установка и использование клиента MQTT для NetX Duo (ОСРВ Azure)

В этой главе обсуждаются разные вопросы, связанные с установкой, настройкой и использованием клиента MQTT для NetX Duo (ОСРВ Azure).

## <a name="product-distribution"></a>Распространение продукта

Клиент MQTT для NetX Duo доступен по адресу [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo). Этот пакет содержит два исходных файла, один файл включения и PDF-файл, содержащий этот документ:

- **nxd_mqtt_client.h** — файл заголовка для клиента MQTT для NetX Duo;
- **nxd_mqtt_client.c** — исходный файл C для клиента MQTT для NetX Duo;
- **nxd_mqtt_client.pdf** — описание клиента MQTT для NetX Duo;
- **demo_mqtt_client.c** — демонстрационный пример MQTT для NetX Duo.

## <a name="mqtt-client-installation"></a>Установка клиента MQTT

Чтобы использовать клиент MQTT для NetX Duo, упомянутый выше дистрибутив нужно целиком скопировать в каталог с установленным экземпляром NetX Duo. Например, если экземпляр NetX Duo установлен в каталоге *\threadx\arm7\green*, в этот каталог нужно скопировать файлы *nxd_mqtt_client.h* и *nxd_mqtt_client.c* для клиента MQTT для NetX Duo.

## <a name="using-mqtt-client"></a>Использование клиента MQTT

Использование клиента MQTT для NetX Duo не представляет никаких трудностей. В код приложения нужно включить файл *nxd_mqtt_client.h* после включения *tx_api.h* и *nx_api.h*, чтобы использовать ThreadX и NetX Duo соответственно. Включив в код приложения файлы заголовка для клиента MQTT, вы сможете использовать службы MQTT, описанные далее в этом руководстве. В приложение также нужно включить файл *nxd_mqtt_client.c* для процесса сборки. Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а их форма объекта должна быть связана с файлами приложения. Это все, что необходимо для использования клиента MQTT для NetX Duo.

## <a name="using-mqtt-client-with-netx-secure-tls"></a>Использование клиента MQTT с NetX Secure TLS

Чтобы использовать клиент MQTT с модулем NetX Secure TLS, в приложении должен быть установлен модуль NetX Secure TLS и включены файлы *nx_secure_tls_api.h* и *nx_crypto.h*. Библиотека MQTT должна компилироваться с определенным символом ***NX_SECURE_ENABLE***.

## <a name="configuration-options"></a>Параметры конфигурации

Существует ряд параметров конфигурации для использования клиента MQTT для NetX Duo. Ниже приведен список всех параметров с подробным описанием каждого из них. Приведены значения по умолчанию, но их можно переопределить до добавления файла *nxd_mqtt_client.h.* .

- **NX_DISABLE_ERROR_CHECKING**: определен; этот параметр удаляет базовую проверку ошибок клиента MQTT. Обычно он используется после отладки приложения.
- **NX_SECURE_ENABLE**: определен; клиент MQTT компилируется с поддержкой TLS.
Если определен этот символ, необходимо установить модуль NetX Secure TLS.
*NX_SECURE_ENABLE*: по умолчанию отключен.**
- **NXD_MQTT_REQUIRE_TLS**: определен; приложение должно использовать TLS для подключения к брокеру MQTT. Для использования этой возможности нужно определить *NX_SECURE_ENABLE*. По умолчанию этот символ не определен.
- **NXD_MQTT_MAXIMUM_TRANSMIT_QUEUE_DEPTH**: определено, глубина очереди передачи MQTT включена. Значение должно быть положительным целым числом.
- **NXD_MQTT_MAX_TOPIC_NAME_LENGTH**: не рекомендуется использовать.
- **NXD_MQTT_MAX_MESSAGE_LENGTH**: не рекомендуется использовать.
- **NXD_MQTT_KEEPALIVE_TIMER_RATE**: определяет частоту таймера MQTT в тактах таймера ThreadX. Этот таймер используется для контроля за отсчетом времени с момента отправки последнего управляющего сообщения MQTT, чтобы отправить сообщение MQTT PINGREQ до истечения периода активности. Этот таймер активируется, если клиент подключается к брокеру с установленным значением таймера периода активности. По умолчанию используется значение TX_TIMER_TICKS_PER_SECOND, что соответствует длительности таймера в одну секунду.
- **NXD_MQTT_PING_TIMEOUT_DELAY**: определяет время, в течение которого клиент MQTT ожидает ответа PINGRESP от брокера после отправки MQTT PINGREQ. Если ответ PINGRESP не будет получен до истечения этого периода ожидания, клиент определит этот брокер как неработоспособный и отключится от него. По умолчанию для PING используется период ожидания TX_TIMER_TICKS_PER_SECOND, т. е. одна секунда.
- **NXD_MQTT_SOCKET_TIMEOUT**: определяет период ожидания для вызова отключения сокета TCP, когда выполняется отключение от сервера MQTT (в тактах таймера). По умолчанию используется значение NX_WAIT_FOREVER.

## <a name="sample-mqtt-program"></a>Пример программы MQTT

В следующей программе представлен простой пример приложения MQTT. Для простоты предполагается, что все операции выполняются успешно, поэтому проверка кодов ошибок не выполняется.

```c
#define LOCAL_SERVER_ADDRESS (IP_ADDRESS(192, 168, 1, 81))

/*******************************************************/
/* IOT MQTT Client Example                             */
/*******************************************************/
#define DEMO_STACK_SIZE 2048
#define CLIENT_ID_STRING "mytestclient"
#define MQTT_CLIENT_STACK_SIZE 4096
#define STRLEN(p) (sizeof(p) - 1)

/* Declare the MQTT thread stack space. */
static ULONG mqtt_client_stack[MQTT_CLIENT_STACK_SIZE / sizeof(ULONG)];

/* Declare the MQTT client control block. */
static NXD_MQTT_CLIENT mqtt_client;

/* Define the symbol for signaling a received message. */

/* Define the test threads. */

#define TOPIC_NAME "topic"

#define MESSAGE_STRING "This is a message. "

/* Define the priority of the MQTT internal thread. */
#define MQTT_THREAD_PRIORTY 2

/* Define the MQTT keep alive timer for 5 minutes */
#define MQTT_KEEP_ALIVE_TIMER 300
#define QOS0 0
#define QOS1 1

/* Declare event flag, which is used in this demo. */
TX_EVENT_FLAGS_GROUP mqtt_app_flag;
#define DEMO_MESSAGE_EVENT 1
#define DEMO_ALL_EVENTS 3

/* Declare buffers to hold message and topic. */
static UCHAR message_buffer[NXD_MQTT_MAX_MESSAGE_LENGTH];
static UCHAR topic_buffer[NXD_MQTT_MAX_TOPIC_NAME_LENGTH];

/* Declare the disconnect notify function. */
static VOID my_disconnect_func(NXD_MQTT_CLIENT *client_ptr)
{
    printf("client disconnected from server\n");
}

static VOID my_notify_func(NXD_MQTT_CLIENT* client_ptr, UINT number_of_messages)
{
    tx_event_flags_set(&mqtt_app_flag, DEMO_MESSAGE_EVENT, TX_OR);
    return;
}

static ULONG error_counter;
void demo_mqtt_client_local(NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr)
{
    UINT status;
    NXD_ADDRESS server_ip;
    ULONG events;
    UINT topic_length, message_length;

    /* Create MQTT client instance. */
    nxd_mqtt_client_create(&mqtt_client, "my_client",
        CLIENT_ID_STRING, STRLEN(CLIENT_ID_STRING), ip_ptr, pool_ptr,
        (VOID*)mqtt_client_stack, sizeof(mqtt_client_stack),
        MQTT_THREAD_PRIORTY, NX_NULL, 0);

    /* Register the disconnect notification function. */
    nxd_mqtt_client_disconnect_notify_set(&mqtt_client, my_disconnect_func);

    /* Create an event flag for this demo. */
    status = tx_event_flags_create(&mqtt_app_flag, "my app event");
    server_ip.nxd_ip_version = 4;
    server_ip.nxd_ip_address.v4 = LOCAL_SERVER_ADDRESS;

    /* Start the connection to the server. */
    nxd_mqtt_client_connect(&mqtt_client, &server_ip, NXD_MQTT_PORT, 
        MQTT_KEEP_ALIVE_TIMER, 0, NX_WAIT_FOREVER);

    /* Subscribe to the topic with QoS level 0. */
    nxd_mqtt_client_subscribe(&mqtt_client, TOPIC_NAME, STRLEN(TOPIC_NAME),
        QOS0);

    /* Set the receive notify function. */
    nxd_mqtt_client_receive_notify_set(&mqtt_client, my_notify_func);

    /* Publish a message with QoS Level 1. */
    nxd_mqtt_client_publish(&mqtt_client, TOPIC_NAME,
        STRLEN(TOPIC_NAME), (CHAR*)MESSAGE_STRING, 
        STRLEN(MESSAGE_STRING), 0, QOS1, NX_WAIT_FOREVER);

    /* Now wait for the broker to publish the message. */
    tx_event_flags_get(&mqtt_app_flag, DEMO_ALL_EVENTS,
        TX_OR_CLEAR, &events, TX_WAIT_FOREVER);

    if(events & DEMO_MESSAGE_EVENT)
    {
        nxd_mqtt_client_message_get(&mqtt_client, topic_buffer,
            sizeof(topic_buffer), &topic_length, message_buffer,
            sizeof(message_buffer), &message_length);

        topic_buffer[topic_length] = 0;

        message_buffer[message_length] = 0;

        printf("topic = %s, message = %s\n", topic_buffer, message_buffer);
    }

    /* Now unsubscribe the topic. */
    nxd_mqtt_client_unsubscribe(&mqtt_client, TOPIC_NAME,
        STRLEN(TOPIC_NAME));

    /* Disconnect from the broker. */
    nxd_mqtt_client_disconnect(&mqtt_client);

    /* Delete the client instance, release all the resources. */
    nxd_mqtt_client_delete(&mqtt_client);
    return;
}
```
