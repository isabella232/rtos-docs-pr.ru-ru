---
title: Глава 2. Установка и использование клиента MQTT для NetX Duo (ОСРВ Azure)
description: В этой главе описываются различные вопросы, связанные с установкой, настройкой и использованием клиента MQTT для NetX Duo.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cde19a0e84f369f1199ea4027fa09e6bd038e837
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814659"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-duo-mqtt-client"></a><span data-ttu-id="fa55b-103">Глава 2. Установка и использование клиента MQTT для NetX Duo (ОСРВ Azure)</span><span class="sxs-lookup"><span data-stu-id="fa55b-103">Chapter 2 - Installation and use of Azure RTOS NetX Duo MQTT client</span></span>

<span data-ttu-id="fa55b-104">В этой главе обсуждаются разные вопросы, связанные с установкой, настройкой и использованием клиента MQTT для NetX Duo (ОСРВ Azure).</span><span class="sxs-lookup"><span data-stu-id="fa55b-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX Duo MQTT client component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="fa55b-105">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="fa55b-105">Product Distribution</span></span>

<span data-ttu-id="fa55b-106">Клиент MQTT для NetX Duo доступен по адресу [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span><span class="sxs-lookup"><span data-stu-id="fa55b-106">MQTT Client for NetX Duo is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="fa55b-107">Этот пакет содержит два исходных файла, один файл включения и PDF-файл, содержащий этот документ:</span><span class="sxs-lookup"><span data-stu-id="fa55b-107">The package includes two source files, one include file, and a file that contains this document, as follows:</span></span>

- <span data-ttu-id="fa55b-108">**nxd_mqtt_client.h** — файл заголовка для клиента MQTT для NetX Duo;</span><span class="sxs-lookup"><span data-stu-id="fa55b-108">**nxd_mqtt_client.h** Header file for MQTT Client for NetX Duo</span></span>
- <span data-ttu-id="fa55b-109">**nxd_mqtt_client.c** — исходный файл C для клиента MQTT для NetX Duo;</span><span class="sxs-lookup"><span data-stu-id="fa55b-109">**nxd_mqtt_client.c** C Source file for MQTT Client for NetX Duo</span></span>
- <span data-ttu-id="fa55b-110">**nxd_mqtt_client.pdf** — описание клиента MQTT для NetX Duo;</span><span class="sxs-lookup"><span data-stu-id="fa55b-110">**nxd_mqtt_client.pdf** Description of MQTT Client for NetX Duo</span></span>
- <span data-ttu-id="fa55b-111">**demo_mqtt_client.c** — демонстрационный пример MQTT для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="fa55b-111">**demo_mqtt_client.c** NetX Duo MQTT demonstration</span></span>

## <a name="mqtt-client-installation"></a><span data-ttu-id="fa55b-112">Установка клиента MQTT</span><span class="sxs-lookup"><span data-stu-id="fa55b-112">MQTT Client Installation</span></span>

<span data-ttu-id="fa55b-113">Чтобы использовать клиент MQTT для NetX Duo, упомянутый выше дистрибутив нужно целиком скопировать в каталог с установленным экземпляром NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="fa55b-113">In order to use MQTT Client for NetX Duo, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="fa55b-114">Например, если экземпляр NetX Duo установлен в каталоге *\threadx\arm7\green*, в этот каталог нужно скопировать файлы *nxd_mqtt_client.h* и *nxd_mqtt_client.c* для клиента MQTT для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="fa55b-114">For example, if NetX Duo is installed in the directory "*\threadx\arm7\green*" then the *nxd_mqtt_client.h* and *nxd_mqtt_client.c* for NetX Duo MQTT Client need to be copied into this directory.</span></span>

## <a name="using-mqtt-client"></a><span data-ttu-id="fa55b-115">Использование клиента MQTT</span><span class="sxs-lookup"><span data-stu-id="fa55b-115">Using MQTT Client</span></span>

<span data-ttu-id="fa55b-116">Использование клиента MQTT для NetX Duo не представляет никаких трудностей.</span><span class="sxs-lookup"><span data-stu-id="fa55b-116">Using MQTT Client for NetX Duo is easy.</span></span> <span data-ttu-id="fa55b-117">В код приложения нужно включить файл *nxd_mqtt_client.h* после включения *tx_api.h* и *nx_api.h*, чтобы использовать ThreadX и NetX Duo соответственно.</span><span class="sxs-lookup"><span data-stu-id="fa55b-117">Basically, the application code must include *nxd_mqtt_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX, and NetX Duo, respectively.</span></span> <span data-ttu-id="fa55b-118">Включив в код приложения файлы заголовка для клиента MQTT, вы сможете использовать службы MQTT, описанные далее в этом руководстве.</span><span class="sxs-lookup"><span data-stu-id="fa55b-118">Once the MQTT Client header files are included, the application code is then able to use the MQTT services described later in this guide.</span></span> <span data-ttu-id="fa55b-119">В приложение также нужно включить файл *nxd_mqtt_client.c* для процесса сборки.</span><span class="sxs-lookup"><span data-stu-id="fa55b-119">The application must also include *nxd_mqtt_client.c* in the build process.</span></span> <span data-ttu-id="fa55b-120">Эти файлы должны быть скомпилированы так же, как и другие файлы приложения, а их форма объекта должна быть связана с файлами приложения.</span><span class="sxs-lookup"><span data-stu-id="fa55b-120">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="fa55b-121">Это все, что необходимо для использования клиента MQTT для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="fa55b-121">This is all that is required to use NetX Duo MQTT Client.</span></span>

## <a name="using-mqtt-client-with-netx-secure-tls"></a><span data-ttu-id="fa55b-122">Использование клиента MQTT с NetX Secure TLS</span><span class="sxs-lookup"><span data-stu-id="fa55b-122">Using MQTT Client with NetX Secure TLS</span></span>

<span data-ttu-id="fa55b-123">Чтобы использовать клиент MQTT с модулем NetX Secure TLS, в приложении должен быть установлен модуль NetX Secure TLS и включены файлы *nx_secure_tls_api.h* и *nx_crypto.h*.</span><span class="sxs-lookup"><span data-stu-id="fa55b-123">To use MQTT client with NetX Secure TLS module, application must have NetX Secure TLS module installed, and include *nx_secure_tls_api.h* and *nx_crypto.h*.</span></span> <span data-ttu-id="fa55b-124">Библиотека MQTT должна компилироваться с определенным символом ***NX_SECURE_ENABLE***.</span><span class="sxs-lookup"><span data-stu-id="fa55b-124">The MQTT library must be built with the symbol ***NX_SECURE_ENABLE*** defined.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="fa55b-125">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="fa55b-125">Configuration Options</span></span>

<span data-ttu-id="fa55b-126">Существует ряд параметров конфигурации для использования клиента MQTT для NetX Duo.</span><span class="sxs-lookup"><span data-stu-id="fa55b-126">There are several configuration options for building MQTT client for NetX Duo.</span></span> <span data-ttu-id="fa55b-127">Ниже приведен список всех параметров с подробным описанием каждого из них.</span><span class="sxs-lookup"><span data-stu-id="fa55b-127">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="fa55b-128">Приведены значения по умолчанию, но их можно переопределить до добавления файла *nxd_mqtt_client.h.* .</span><span class="sxs-lookup"><span data-stu-id="fa55b-128">The default values are listed, but can be redefined prior to inclusion of *nxd_mqtt_client.h.*</span></span>

- <span data-ttu-id="fa55b-129">**NX_DISABLE_ERROR_CHECKING**: определен; этот параметр удаляет базовую проверку ошибок клиента MQTT.</span><span class="sxs-lookup"><span data-stu-id="fa55b-129">**NX_DISABLE_ERROR_CHECKING**: Defined, this option removes the basic MQTT client error checking.</span></span> <span data-ttu-id="fa55b-130">Обычно он используется после отладки приложения.</span><span class="sxs-lookup"><span data-stu-id="fa55b-130">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="fa55b-131">**NX_SECURE_ENABLE**: определен; клиент MQTT компилируется с поддержкой TLS.</span><span class="sxs-lookup"><span data-stu-id="fa55b-131">**NX_SECURE_ENABLE**: Defined, MQTT Client is built with TLS support.</span></span>
<span data-ttu-id="fa55b-132">Если определен этот символ, необходимо установить модуль NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="fa55b-132">Defining this symbol requires NetX Secure TLS module to be installed.</span></span>
<span data-ttu-id="fa55b-133">*NX_SECURE_ENABLE*: по умолчанию отключен.\*\*</span><span class="sxs-lookup"><span data-stu-id="fa55b-133">*NX_SECURE_ENABLE* is not enabled by default.\*\*</span></span>
- <span data-ttu-id="fa55b-134">**NXD_MQTT_REQUIRE_TLS**: определен; приложение должно использовать TLS для подключения к брокеру MQTT.</span><span class="sxs-lookup"><span data-stu-id="fa55b-134">**NXD_MQTT_REQUIRE_TLS**: Defined, application must use TLS to connect to MQTT broker.</span></span> <span data-ttu-id="fa55b-135">Для использования этой возможности нужно определить *NX_SECURE_ENABLE*.</span><span class="sxs-lookup"><span data-stu-id="fa55b-135">This feature requires *NX_SECURE_ENABLE* defined.</span></span> <span data-ttu-id="fa55b-136">По умолчанию этот символ не определен.</span><span class="sxs-lookup"><span data-stu-id="fa55b-136">By default, this symbol is not defined.</span></span>
- <span data-ttu-id="fa55b-137">**NXD_MQTT_MAX_TOPIC_NAME_LENGTH**: не рекомендуется использовать.</span><span class="sxs-lookup"><span data-stu-id="fa55b-137">**NXD_MQTT_MAX_TOPIC_NAME_LENGTH**: Deprecated.</span></span>
- <span data-ttu-id="fa55b-138">**NXD_MQTT_MAX_MESSAGE_LENGTH**: не рекомендуется использовать.</span><span class="sxs-lookup"><span data-stu-id="fa55b-138">**NXD_MQTT_MAX_MESSAGE_LENGTH**: Deprecated.</span></span>
- <span data-ttu-id="fa55b-139">**NXD_MQTT_KEEPALIVE_TIMER_RATE**: определяет частоту таймера MQTT в тактах таймера ThreadX.</span><span class="sxs-lookup"><span data-stu-id="fa55b-139">**NXD_MQTT_KEEPALIVE_TIMER_RATE**: Defines the MQTT timer rate, in ThreadX timer ticks.</span></span> <span data-ttu-id="fa55b-140">Этот таймер используется для контроля за отсчетом времени с момента отправки последнего управляющего сообщения MQTT, чтобы отправить сообщение MQTT PINGREQ до истечения периода активности.</span><span class="sxs-lookup"><span data-stu-id="fa55b-140">This timer is used to keep track of the time since last MQTT control message was sent, and sends out an MQTT PINGREQ message before the keep-alive time expires.</span></span> <span data-ttu-id="fa55b-141">Этот таймер активируется, если клиент подключается к брокеру с установленным значением таймера периода активности.</span><span class="sxs-lookup"><span data-stu-id="fa55b-141">This timer is activated if the client connects to the broker with a keep-alive timer value set.</span></span> <span data-ttu-id="fa55b-142">По умолчанию используется значение TX_TIMER_TICKS_PER_SECOND, что соответствует длительности таймера в одну секунду.</span><span class="sxs-lookup"><span data-stu-id="fa55b-142">The default value is TX_TIMER_TICKS_PER_SECOND, which is a one-second timer.</span></span>
- <span data-ttu-id="fa55b-143">**NXD_MQTT_PING_TIMEOUT_DELAY**: определяет время, в течение которого клиент MQTT ожидает ответа PINGRESP от брокера после отправки MQTT PINGREQ.</span><span class="sxs-lookup"><span data-stu-id="fa55b-143">**NXD_MQTT_PING_TIMEOUT_DELAY**: Defines the time the MQTT client waits for PINGRESP from the broker after it sends out MQTT PINGREQ.</span></span> <span data-ttu-id="fa55b-144">Если ответ PINGRESP не будет получен до истечения этого периода ожидания, клиент определит этот брокер как неработоспособный и отключится от него.</span><span class="sxs-lookup"><span data-stu-id="fa55b-144">If no PINGRESP is received after this timeout delay, the client treats the broker as non-responsive and disconnects itself from the broker.</span></span> <span data-ttu-id="fa55b-145">По умолчанию для PING используется период ожидания TX_TIMER_TICKS_PER_SECOND, т. е. одна секунда.</span><span class="sxs-lookup"><span data-stu-id="fa55b-145">The default PING timeout delay is TX_TIMER_TICKS_PER_SECOND, which is one second.</span></span>
- <span data-ttu-id="fa55b-146">**NXD_MQTT_SOCKET_TIMEOUT**: определяет период ожидания для вызова отключения сокета TCP, когда выполняется отключение от сервера MQTT (в тактах таймера).</span><span class="sxs-lookup"><span data-stu-id="fa55b-146">**NXD_MQTT_SOCKET_TIMEOUT**: Defines the time out in the TCP socket disconnect call when disconnecting from the MQTT server in timer ticks.</span></span> <span data-ttu-id="fa55b-147">По умолчанию используется значение NX_WAIT_FOREVER.</span><span class="sxs-lookup"><span data-stu-id="fa55b-147">The default value is NX_WAIT_FOREVER.</span></span>

## <a name="sample-mqtt-program"></a><span data-ttu-id="fa55b-148">Пример программы MQTT</span><span class="sxs-lookup"><span data-stu-id="fa55b-148">Sample MQTT program</span></span>

<span data-ttu-id="fa55b-149">В следующей программе представлен простой пример приложения MQTT.</span><span class="sxs-lookup"><span data-stu-id="fa55b-149">The following program illustrates a simple MQTT application.</span></span> <span data-ttu-id="fa55b-150">Для простоты предполагается, что все операции выполняются успешно, поэтому проверка кодов ошибок не выполняется.</span><span class="sxs-lookup"><span data-stu-id="fa55b-150">For simplicity, the return codes are assumed to be successful, therefore no further error checking is done.</span></span>

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
