---
title: Глава 3. Описание служб клиента ОСРВ Azure NetX Duo MQTT
description: В этой главе приведено описание всех служб клиента NetX Duo MQTT (см. ниже) в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 9cbb65946c45bfbc476091f7c604346e839a42fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814651"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-mqtt-client-services"></a><span data-ttu-id="5a544-103">Глава 3. Описание служб клиента ОСРВ Azure NetX Duo MQTT</span><span class="sxs-lookup"><span data-stu-id="5a544-103">Chapter 3 - Description of Azure RTOS NetX Duo MQTT client services</span></span>

<span data-ttu-id="5a544-104">В этой главе приведено описание всех служб клиента ОСРВ Azure NetX Duo MQTT (см. ниже) в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="5a544-104">This chapter contains a description of all Azure RTOS NetX Duo MQTT client services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="5a544-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, используемым для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="5a544-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="5a544-106">**nxd_mqtt_client_create** *Создание экземпляра клиента MQTT*</span><span class="sxs-lookup"><span data-stu-id="5a544-106">**nxd_mqtt_client_create** *Create MQTT client instance*</span></span>
- <span data-ttu-id="5a544-107">**nxd_mqtt_client_will_message_set** *Установка сообщения LWT*</span><span class="sxs-lookup"><span data-stu-id="5a544-107">**nxd_mqtt_client_will_message_set** *Set the will message*</span></span>
- <span data-ttu-id="5a544-108">**nxd_mqtt_client_client_login_set** *Установка имени пользователя и пароля для доступа к клиенту MQTT*</span><span class="sxs-lookup"><span data-stu-id="5a544-108">**nxd_mqtt_client_client_login_set** *Set MQTT client login username and password*</span></span>
- <span data-ttu-id="5a544-109">**nxd_mqtt_client_connect** *Подключение клиента MQTT к брокеру*</span><span class="sxs-lookup"><span data-stu-id="5a544-109">**nxd_mqtt_client_connect** *Connect MQTT Client to the broker*</span></span>
- <span data-ttu-id="5a544-110">**nxd_mqtt_client_secure_connect** *Подключение клиента MQTT к брокеру по протоколу TLS*</span><span class="sxs-lookup"><span data-stu-id="5a544-110">**nxd_mqtt_client_secure_connect** *Connect MQTT client to the broker with TLS security*</span></span>
- <span data-ttu-id="5a544-111">**nxd_mqtt_client_publish** *Публикация сообщения через брокера.*</span><span class="sxs-lookup"><span data-stu-id="5a544-111">**nxd_mqtt_client_publish** *Publish a message through the broker.*</span></span>
- <span data-ttu-id="5a544-112">**nxd_mqtt_client_subscribe** *Подписка на раздел*</span><span class="sxs-lookup"><span data-stu-id="5a544-112">**nxd_mqtt_client_subscribe** *Subscribe to a topic*</span></span>
- <span data-ttu-id="5a544-113">**nxd_mqtt_client_unsubscribe** *Отписка от раздела*</span><span class="sxs-lookup"><span data-stu-id="5a544-113">**nxd_mqtt_client_unsubscribe** *Unsubscribe from a topic*</span></span>
- <span data-ttu-id="5a544-114">**nxd_mqtt_client_receive_notify_set** *Установка функции обратного вызова для уведомления о сообщении MQTT о получении*</span><span class="sxs-lookup"><span data-stu-id="5a544-114">**nxd_mqtt_client_receive_notify_set** *Set MQTT message receive notify callback function*</span></span>
- <span data-ttu-id="5a544-115">**nxd_mqtt_client_message_get** *Получение сообщения от брокера*</span><span class="sxs-lookup"><span data-stu-id="5a544-115">**nxd_mqtt_client_message_get** *Retrieve a message from the broker*</span></span>
- <span data-ttu-id="5a544-116">**nxd_mqtt_client_disconnect_notify_set** *Установка функции обратного вызова для уведомления о сообщении MQTT об отключении*</span><span class="sxs-lookup"><span data-stu-id="5a544-116">**nxd_mqtt_client_disconnect_notify_set** *Set MQTT message disconnect notify callback function*</span></span>
- <span data-ttu-id="5a544-117">**nxd_mqtt_client_disconnect** *Отключение клиента MQTT от брокера*</span><span class="sxs-lookup"><span data-stu-id="5a544-117">**nxd_mqtt_client_disconnect** *Disconnect MQTT client from the broker*</span></span>
- <span data-ttu-id="5a544-118">**nxd_mqtt_client_delete** *Удаление экземпляра клиента MQTT*</span><span class="sxs-lookup"><span data-stu-id="5a544-118">**nxd_mqtt_client_delete** *Delete the MQTT client instance*</span></span>

## <a name="nxd_mqtt_client_create"></a><span data-ttu-id="5a544-119">nxd_mqtt_client_create</span><span class="sxs-lookup"><span data-stu-id="5a544-119">nxd_mqtt_client_create</span></span>

<span data-ttu-id="5a544-120">Создание экземпляра клиента MQTT</span><span class="sxs-lookup"><span data-stu-id="5a544-120">Create MQTT Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5a544-121">Прототип</span><span class="sxs-lookup"><span data-stu-id="5a544-121">Prototype</span></span>

```c
UINT nxd_mqtt_client_create(NXD_MQTT_CLIENT *client_ptr,
    CHAR *client_name, CHAR *client_id,
    UINT client_id_length, NX_IP *ip_ptr, NX_PACKET_POOL
    *pool_ptr, VOID *stack_ptr, ULONG stack_size, UINT
    mqtt_thread_priority,
    VOID *memory_ptr, ULONG memory_size);
```

### <a name="description"></a><span data-ttu-id="5a544-122">Описание</span><span class="sxs-lookup"><span data-stu-id="5a544-122">Description</span></span>

<span data-ttu-id="5a544-123">Эта служба создает экземпляр клиента MQTT в указанном IP-адресе экземпляра.</span><span class="sxs-lookup"><span data-stu-id="5a544-123">This service creates an MQTT Client instance on the specified IP instance.</span></span> <span data-ttu-id="5a544-124">Строка *client_id* передается на сервер во время фазы подключения MQTT в качестве *идентификатора клиента (ClientId)* .</span><span class="sxs-lookup"><span data-stu-id="5a544-124">The *client_id* string is passed to the server during MQTT connection phase as the *Client Identifier (ClientId)*.</span></span> <span data-ttu-id="5a544-125">Он также создает необходимые ресурсы ThreadX (поток задач клиента MQTT, мьютекс, группу флагов событий и сокет TCP).</span><span class="sxs-lookup"><span data-stu-id="5a544-125">It also creates the necessary ThreadX resources (MQTT Client task thread, mutex, event flag group, and TCP socket).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a544-126">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="5a544-126">Input Parameters</span></span>

- <span data-ttu-id="5a544-127">**client_ptr** Указатель на блок управления клиентом MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-127">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5a544-128">**client_name** Строка имени клиента.</span><span class="sxs-lookup"><span data-stu-id="5a544-128">**client_name** Client name string.</span></span>
- <span data-ttu-id="5a544-129">**client_id** Строка идентификатора клиента, используемая во время фазы подключения.</span><span class="sxs-lookup"><span data-stu-id="5a544-129">**client_id** Client ID string used during connection phase.</span></span> <span data-ttu-id="5a544-130">Брокер MQTT использует client_id для уникальной идентификации клиента.</span><span class="sxs-lookup"><span data-stu-id="5a544-130">MQTT broker uses this client_id to uniquely identify a client.</span></span>
- <span data-ttu-id="5a544-131">**client_id_length** Длина строки идентификатора клиента в байтах.</span><span class="sxs-lookup"><span data-stu-id="5a544-131">**client_id_length** Length of the client ID string, in bytes.</span></span>
- <span data-ttu-id="5a544-132">**ip_ptr** Указатель на экземпляр IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="5a544-132">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="5a544-133">**pool_ptr** Указатель на пул пакетов, который клиент MQTT использует для своей работы.</span><span class="sxs-lookup"><span data-stu-id="5a544-133">**pool_ptr** Pointer to a packet pool MQTT client uses for its operation.</span></span>
- <span data-ttu-id="5a544-134">**stack_ptr** Область стека для потока клиента MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-134">**stack_ptr** Stack area for the MQTT Client thread.</span></span>
- <span data-ttu-id="5a544-135">**stack_size** Размер области стека в байтах.</span><span class="sxs-lookup"><span data-stu-id="5a544-135">**stack_size** Size of the stack area, in bytes.</span></span>
- <span data-ttu-id="5a544-136">**mqtt_thread_priority** Приоритет потока MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-136">**mqtt_thread_priority** The priority of the MQTT Thread.</span></span>
- <span data-ttu-id="5a544-137">**memory_ptr** Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="5a544-137">**memory_ptr** Deprecated.</span></span> <span data-ttu-id="5a544-138">Больше не используется.</span><span class="sxs-lookup"><span data-stu-id="5a544-138">Not used anymore.</span></span>
- <span data-ttu-id="5a544-139">**memory_size** Не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="5a544-139">**memory_size** Deprecated.</span></span> <span data-ttu-id="5a544-140">Больше не используется.</span><span class="sxs-lookup"><span data-stu-id="5a544-140">Not used anymore.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a544-141">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5a544-141">Return Values</span></span>

- <span data-ttu-id="5a544-142">**NXD_MQTT_SUCCESS** (0x00) – клиент MQTT успешно создан.</span><span class="sxs-lookup"><span data-stu-id="5a544-142">**NXD_MQTT_SUCCESS** (0x00) Successfully created MQTT client.</span></span>
- <span data-ttu-id="5a544-143">**NXD_MQTT_INTERNAL_ERROR** (0x10004) – внутренняя логическая ошибка</span><span class="sxs-lookup"><span data-stu-id="5a544-143">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="5a544-144">NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT, ip_ptr или указатель на пул пакетов.</span><span class="sxs-lookup"><span data-stu-id="5a544-144">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer.</span></span>
- <span data-ttu-id="5a544-145">NXD_MQTT_INVALID_PARAMETER (0x10009) – недопустимая строка раздела сообщений LWT, значение will_retrain_flag или will_QoS.</span><span class="sxs-lookup"><span data-stu-id="5a544-145">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid will topic string, will_retrain_flag, or will_QoS value.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a544-146">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5a544-146">Allowed From</span></span>

<span data-ttu-id="5a544-147">Потоки</span><span class="sxs-lookup"><span data-stu-id="5a544-147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a544-148">Пример</span><span class="sxs-lookup"><span data-stu-id="5a544-148">Example</span></span>

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

## <a name="nxd_mqtt_client_will_message_set"></a><span data-ttu-id="5a544-149">nxd_mqtt_client_will_message_set</span><span class="sxs-lookup"><span data-stu-id="5a544-149">nxd_mqtt_client_will_message_set</span></span>

<span data-ttu-id="5a544-150">Установка сообщения LWT</span><span class="sxs-lookup"><span data-stu-id="5a544-150">Sets the Will message</span></span>

### <a name="prototype"></a><span data-ttu-id="5a544-151">Прототип</span><span class="sxs-lookup"><span data-stu-id="5a544-151">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="5a544-152">Описание</span><span class="sxs-lookup"><span data-stu-id="5a544-152">Description</span></span>

<span data-ttu-id="5a544-153">Эта служба устанавливает необязательный раздел LWT сообщение LWT, прежде чем клиент начнет подключение к серверу.</span><span class="sxs-lookup"><span data-stu-id="5a544-153">This service sets the optional will topic and will message before the client connects to the server.</span></span> <span data-ttu-id="5a544-154">Раздел LWT должен быть строкой в формате UTF-8.</span><span class="sxs-lookup"><span data-stu-id="5a544-154">Will topic must be UTF-8 encoded string.</span></span>

<span data-ttu-id="5a544-155">Сообщение LWT, если оно задано, передается брокеру в составе сообщения CONNECT.</span><span class="sxs-lookup"><span data-stu-id="5a544-155">The will message, if set, is transmitted to the broker as part of the CONNECT message.</span></span> <span data-ttu-id="5a544-156">Поэтому приложение, которое будет использовать сообщение LWT, должно использовать эту службу до подключения MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-156">Therefore application wishing to use will message must use this service before the MQTT connection is make.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a544-157">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="5a544-157">Input Parameters</span></span>

- <span data-ttu-id="5a544-158">**client_ptr** Указатель на блок управления клиентом MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-158">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5a544-159">**will_topic** Строка раздела LWT в формате UTF-8.</span><span class="sxs-lookup"><span data-stu-id="5a544-159">**will_topic** UTF-8 encoded will topic string.</span></span> <span data-ttu-id="5a544-160">Раздел LWT является обязательным.</span><span class="sxs-lookup"><span data-stu-id="5a544-160">Will topic must be present.</span></span> <span data-ttu-id="5a544-161">Пока выполняется вызов *nx_mqtt_client_connect*, вызывающий объект должен считать строку will_topic допустимой.</span><span class="sxs-lookup"><span data-stu-id="5a544-161">Caller must keep the will_topic string valid till the *nx_mqtt_client_connect* call is made.</span></span>
- <span data-ttu-id="5a544-162">**will_topic_length** Число байтов в строке раздела LWT</span><span class="sxs-lookup"><span data-stu-id="5a544-162">**will_topic_length** Number of bytes in the will topic string</span></span>
- <span data-ttu-id="5a544-163">**will_message** Сообщение LWT, заданное приложением.</span><span class="sxs-lookup"><span data-stu-id="5a544-163">**will_message** Application defined will message.</span></span> <span data-ttu-id="5a544-164">Если сообщение LWT не требуется, приложение может задать для этого поля значение *NX_NULL.*</span><span class="sxs-lookup"><span data-stu-id="5a544-164">If will message is not required, application can set this field to *NX_NULL.*</span></span>
- <span data-ttu-id="5a544-165">**will_message_length** Число байтов в строке сообщения LWT.</span><span class="sxs-lookup"><span data-stu-id="5a544-165">**will_message_length** Number of bytes in the will message string.</span></span> <span data-ttu-id="5a544-166">Если will_message имеет значение NULL, для will_message_length должно быть задано значение 0.</span><span class="sxs-lookup"><span data-stu-id="5a544-166">If will_message is set to NULL, will_message_length must be set to 0.</span></span>
- <span data-ttu-id="5a544-167">**will_retain_flag** Включение/отключение публикации сервером сообщения LWT в виде сохраняемого сообщения.</span><span class="sxs-lookup"><span data-stu-id="5a544-167">**will_retain_flag** Whether the server publishes the will message as a retained message.</span></span> <span data-ttu-id="5a544-168">Допустимые значения: *NX_TRUE* или *NX_FALSE.*</span><span class="sxs-lookup"><span data-stu-id="5a544-168">Valid values are *NX_TRUE* or *NX_FALSE.*</span></span>
- <span data-ttu-id="5a544-169">**will_QoS** Значение QoS, используемое сервером при отправке сообщения LWT.</span><span class="sxs-lookup"><span data-stu-id="5a544-169">**will_QoS** QoS value used by the server when sending will message.</span></span> <span data-ttu-id="5a544-170">Допустимы значения 0 или 1.</span><span class="sxs-lookup"><span data-stu-id="5a544-170">Valid values are 0 or 1.</span></span>  

### <a name="return-values"></a><span data-ttu-id="5a544-171">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5a544-171">Return Values</span></span>

- <span data-ttu-id="5a544-172">**NXD_MQTT_SUCCESS** (0X00) – сообщение LWT успешно создано.</span><span class="sxs-lookup"><span data-stu-id="5a544-172">**NXD_MQTT_SUCCESS** (0x00) Successfully sets the will message.</span></span>
- <span data-ttu-id="5a544-173">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) – сообщения QoS уровня 2 не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="5a544-173">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2 messages are not supported.</span></span>
- <span data-ttu-id="5a544-174">NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-174">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>
- <span data-ttu-id="5a544-175">NXD_MQTT_INVALID_PARAMETER (0x10009) – недопустимая строка раздела сообщений LWT, значение will_retrain_flag или will_QoS.</span><span class="sxs-lookup"><span data-stu-id="5a544-175">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid will topic string, will_retrain_flag, or will_QoS value.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a544-176">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5a544-176">Allowed From</span></span>

<span data-ttu-id="5a544-177">Потоки</span><span class="sxs-lookup"><span data-stu-id="5a544-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a544-178">Пример</span><span class="sxs-lookup"><span data-stu-id="5a544-178">Example</span></span>

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

## <a name="nxd_mqtt_client_login_set"></a><span data-ttu-id="5a544-179">nxd_mqtt_client_login_set</span><span class="sxs-lookup"><span data-stu-id="5a544-179">nxd_mqtt_client_login_set</span></span>

<span data-ttu-id="5a544-180">Задает имя пользователя и пароль для доступа к клиенту MQTT</span><span class="sxs-lookup"><span data-stu-id="5a544-180">Sets MQTT client login username and password</span></span>

### <a name="prototype"></a><span data-ttu-id="5a544-181">Прототип</span><span class="sxs-lookup"><span data-stu-id="5a544-181">Prototype</span></span>

```c
UINT nxd_mqtt_client_login_set(NXD_MQTT_CLIENT *client_ptr,
    Const UCHAR *username,
    UINT username_length
    Const UCHAR *password,
    UINT password_length);
```

### <a name="description"></a><span data-ttu-id="5a544-182">Описание</span><span class="sxs-lookup"><span data-stu-id="5a544-182">Description</span></span>

<span data-ttu-id="5a544-183">Эта служба задает имя пользователя и пароль, которые используются на этапе подключения MQTT для проверки подлинности при входе в систему.</span><span class="sxs-lookup"><span data-stu-id="5a544-183">This service sets the username and password, which is used during MQTT connection phase for log in authentication purpose.</span></span>

<span data-ttu-id="5a544-184">Данные для доступа к клиенту MQTT (имя пользователя и пароль) являются необязательными.</span><span class="sxs-lookup"><span data-stu-id="5a544-184">The MQTT client login with username and password is optional.</span></span> <span data-ttu-id="5a544-185">В ситуациях, когда серверу требуется имя пользователя и пароль, их необходимо задать до установки соединения.</span><span class="sxs-lookup"><span data-stu-id="5a544-185">In situations where the server requires a user name and password, the user name and password must be set before the connection is established.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a544-186">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="5a544-186">Input Parameters</span></span>

- <span data-ttu-id="5a544-187">**client_ptr** Указатель на блок управления клиентом MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-187">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5a544-188">**username** Строка имени пользователя в кодировке UTF-8.</span><span class="sxs-lookup"><span data-stu-id="5a544-188">**username** UTF-8 encoded user name string.</span></span> <span data-ttu-id="5a544-189">Пока выполняется вызов *nx_mqtt_client_connect*, вызывающий объект должен считать строку username допустимой.</span><span class="sxs-lookup"><span data-stu-id="5a544-189">Caller must keep the username string valid till the *nx_mqtt_client_connect* call is made.</span></span>
- <span data-ttu-id="5a544-190">**username_length** Число байтов в строке username</span><span class="sxs-lookup"><span data-stu-id="5a544-190">**username_length** Number of bytes in the username string</span></span>
- <span data-ttu-id="5a544-191">**password** Строка пароля.</span><span class="sxs-lookup"><span data-stu-id="5a544-191">**password** Password string.</span></span> <span data-ttu-id="5a544-192">Если пароль не требуется, для этого поля можно установить значение NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="5a544-192">If password is not required, this field may be set to NX_NULL.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a544-193">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5a544-193">Return Values</span></span>

- <span data-ttu-id="5a544-194">**NXD_MQTT_SUCCESS** (0X00) – сообщение LWT успешно создано.</span><span class="sxs-lookup"><span data-stu-id="5a544-194">**NXD_MQTT_SUCCESS** (0x00) Successfully sets the will message.</span></span>
- <span data-ttu-id="5a544-195">NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-195">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>
- <span data-ttu-id="5a544-196">NXD_MQTT_INVALID_PARAMETER (0x10009) – недопустимая строка username или password.</span><span class="sxs-lookup"><span data-stu-id="5a544-196">NXD_MQTT_INVALID_PARAMETER (0x10009) Invalid username string or the password string.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a544-197">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5a544-197">Allowed From</span></span>

<span data-ttu-id="5a544-198">Потоки</span><span class="sxs-lookup"><span data-stu-id="5a544-198">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a544-199">Пример</span><span class="sxs-lookup"><span data-stu-id="5a544-199">Example</span></span>

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

## <a name="nxd_mqtt_client_connect"></a><span data-ttu-id="5a544-200">nxd_mqtt_client_connect</span><span class="sxs-lookup"><span data-stu-id="5a544-200">nxd_mqtt_client_connect</span></span>

<span data-ttu-id="5a544-201">Подключение клиента MQTT к брокеру</span><span class="sxs-lookup"><span data-stu-id="5a544-201">Connect MQTT Client to the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="5a544-202">Прототип</span><span class="sxs-lookup"><span data-stu-id="5a544-202">Prototype</span></span>

```c
UINT nxd_mqtt_client_connect(NXD_MQTT_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT keepalive, UINT clean_session, ULONG wait_option));
```

### <a name="description"></a><span data-ttu-id="5a544-203">Описание</span><span class="sxs-lookup"><span data-stu-id="5a544-203">Description</span></span>

<span data-ttu-id="5a544-204">Эта служба инициирует подключение к брокеру.</span><span class="sxs-lookup"><span data-stu-id="5a544-204">This service initiates a connection to the broker.</span></span> <span data-ttu-id="5a544-205">Сначала она привязывает TCP-сокет, а затем устанавливает соединение по протоколу TCP.</span><span class="sxs-lookup"><span data-stu-id="5a544-205">First it binds a TCP socket, then makes a TCP connection.</span></span> <span data-ttu-id="5a544-206">Затем она создает таймер, если ошибок не возникло и функция проверки активности MQTT включена.</span><span class="sxs-lookup"><span data-stu-id="5a544-206">Assuming that succeeds, it creates a timer if the MQTT keep alive feature is enabled.</span></span> <span data-ttu-id="5a544-207">Затем она подключается к серверу MQTT (брокеру).</span><span class="sxs-lookup"><span data-stu-id="5a544-207">Then it connects with the MQTT server (broker).</span></span>

<span data-ttu-id="5a544-208">Обратите внимание, что эта служба создает соединение с MQTT без защиты по протоколу TLS.</span><span class="sxs-lookup"><span data-stu-id="5a544-208">Note that this service creates an MQTT connection with no TLS protection.</span></span> <span data-ttu-id="5a544-209">Чтобы создать безопасное соединение с MQTT, приложение должно использовать службу ***nxd_mqtt_client_secure_connect ().***</span><span class="sxs-lookup"><span data-stu-id="5a544-209">To create a secure MQTT connection, the application shall use the service ***nxd_mqtt_client_secure_connect().***</span></span>

<span data-ttu-id="5a544-210">Если при подключении клиент задает для *clean_session* значение NX_FALSE, клиент повторно передает все хранящиеся в нем сообщения, которые еще не подтверждены.</span><span class="sxs-lookup"><span data-stu-id="5a544-210">Upon the connection, if the client sets the *clean_session* to NX_FALSE, the client will retransmit any messages stored that have not been acknowledged yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a544-211">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="5a544-211">Input Parameters</span></span>

- <span data-ttu-id="5a544-212">**client_ptr** Указатель на блок управления клиентом MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-212">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5a544-213">**server_ip** IP-адрес брокера.</span><span class="sxs-lookup"><span data-stu-id="5a544-213">**server_ip** Broker IP address.</span></span>
- <span data-ttu-id="5a544-214">**server_port** Номер порта брокера.</span><span class="sxs-lookup"><span data-stu-id="5a544-214">**server_port** Broker port number.</span></span> <span data-ttu-id="5a544-215">Порт по умолчанию для MQTT определяется как **_NXD_MQTT_PORT_** (1883).</span><span class="sxs-lookup"><span data-stu-id="5a544-215">The default port for MQTT is defined as **_NXD_MQTT_PORT_** (1883).</span></span>
- <span data-ttu-id="5a544-216">**keep_alive** Значение проверки активности в секундах, которое будет использоваться во время сеанса.</span><span class="sxs-lookup"><span data-stu-id="5a544-216">**keep_alive** The keep alive value, in seconds, to be used during the session.</span></span> <span data-ttu-id="5a544-217">Значение указывает максимальный временной интервал между двумя сообщениями управления MQTT, отправляемыми брокеру до того, как брокер зафиксирует истечение времени ожидания клиента.</span><span class="sxs-lookup"><span data-stu-id="5a544-217">The value indicates the maximum time between two MQTT control messages being sent to the broker before the broker times out this client.</span></span> <span data-ttu-id="5a544-218">Значение 0 отключает функцию проверки активности.</span><span class="sxs-lookup"><span data-stu-id="5a544-218">The value 0 turns off the keep-alive feature.</span></span>
- <span data-ttu-id="5a544-219">**clean_session** Указывает, должен ли сервер запускать этот сеанс с нуля.</span><span class="sxs-lookup"><span data-stu-id="5a544-219">**clean_session** Whether the server shall start this session clean.</span></span> <span data-ttu-id="5a544-220">Допустимые значения: **_NX_TRUE_ *_ или _* _NX_FALSE._**</span><span class="sxs-lookup"><span data-stu-id="5a544-220">Valid options are **_NX_TRUE_*_ or _*_NX_FALSE._**</span></span>
- <span data-ttu-id="5a544-221">**wait_option** Время ожидания подключения.</span><span class="sxs-lookup"><span data-stu-id="5a544-221">**wait_option** Connection wait time.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a544-222">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5a544-222">Return Values</span></span>

- <span data-ttu-id="5a544-223">**NXD_MQTT_SUCCESS** (0X00) – успешное подключение MQTT</span><span class="sxs-lookup"><span data-stu-id="5a544-223">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT connection</span></span>
- <span data-ttu-id="5a544-224">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) – клиент уже подключен к брокеру.</span><span class="sxs-lookup"><span data-stu-id="5a544-224">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) The client is already connected to the broker.</span></span>
- <span data-ttu-id="5a544-225">**NXD_MQTT_MUTEX_FAILURE** (0X10003) – не удалось получить мьютекс MQTT</span><span class="sxs-lookup"><span data-stu-id="5a544-225">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span> 
- <span data-ttu-id="5a544-226">**NXD_MQTT_INTERNAL_ERROR** (0x10004) – внутренняя логическая ошибка</span><span class="sxs-lookup"><span data-stu-id="5a544-226">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="5a544-227">**NXD_MQTT_CONNECT_FAILURE** (0X10005) – не удалось подключиться к брокеру.</span><span class="sxs-lookup"><span data-stu-id="5a544-227">**NXD_MQTT_CONNECT_FAILURE** (0x10005) Failed to connect to the broker.</span></span>
- <span data-ttu-id="5a544-228">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) – не удалось отправить сообщения брокеру.</span><span class="sxs-lookup"><span data-stu-id="5a544-228">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="5a544-229">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) – сервер ответил с ошибкой</span><span class="sxs-lookup"><span data-stu-id="5a544-229">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Server responded with error</span></span>
- <span data-ttu-id="5a544-230">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) – код отклика сервера</span><span class="sxs-lookup"><span data-stu-id="5a544-230">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Server response code</span></span>
- <span data-ttu-id="5a544-231">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) – код отклика сервера</span><span class="sxs-lookup"><span data-stu-id="5a544-231">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Server response code</span></span>
- <span data-ttu-id="5a544-232">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) – код отклика сервера</span><span class="sxs-lookup"><span data-stu-id="5a544-232">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Server response code</span></span>
- <span data-ttu-id="5a544-233">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) – код отклика сервера</span><span class="sxs-lookup"><span data-stu-id="5a544-233">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Server response code</span></span>
- <span data-ttu-id="5a544-234">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) – код отклика сервера</span><span class="sxs-lookup"><span data-stu-id="5a544-234">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Server response code</span></span>
- <span data-ttu-id="5a544-235">NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT, ip_ptr или указатель на пул пакетов</span><span class="sxs-lookup"><span data-stu-id="5a544-235">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a544-236">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5a544-236">Allowed From</span></span>

<span data-ttu-id="5a544-237">Потоки</span><span class="sxs-lookup"><span data-stu-id="5a544-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a544-238">Пример</span><span class="sxs-lookup"><span data-stu-id="5a544-238">Example</span></span>

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

## <a name="nxd_mqtt_client_secure_connect"></a><span data-ttu-id="5a544-239">nxd_mqtt_client_secure_connect</span><span class="sxs-lookup"><span data-stu-id="5a544-239">nxd_mqtt_client_secure_connect</span></span>

<span data-ttu-id="5a544-240">Подключение клиента MQTT к брокеру по протоколу защиты TLS</span><span class="sxs-lookup"><span data-stu-id="5a544-240">Connect MQTT client to the broker with TLS security</span></span>

### <a name="prototype"></a><span data-ttu-id="5a544-241">Прототип</span><span class="sxs-lookup"><span data-stu-id="5a544-241">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="5a544-242">Описание</span><span class="sxs-lookup"><span data-stu-id="5a544-242">Description</span></span>

<span data-ttu-id="5a544-243">Эта служба идентична службе ***nxd_mqtt_client_connect*** за исключением того, что соединение проходит через уровень TLS, а не TCP.</span><span class="sxs-lookup"><span data-stu-id="5a544-243">This service is identical to ***nxd_mqtt_client_connect*** except that the connection goes through TLS layer instead of TCP.</span></span> <span data-ttu-id="5a544-244">Таким образом, обеспечивается защита связи между клиентом и брокером.</span><span class="sxs-lookup"><span data-stu-id="5a544-244">Therefore, communication between the client and the broker is secured.</span></span>

<span data-ttu-id="5a544-245">*tls_setup* — это определяемая пользователем функция обратного вызова, которую клиент MQTT использует перед созданием соединения с клиентом MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-245">The user-defined *tls_setup* is a callback function that the MQTT client uses prior to making a MQTT client connection.</span></span> <span data-ttu-id="5a544-246">Приложение должно инициализировать NetX Secure TLS, настроить параметры безопасности и загрузить соответствующие сертификаты для использования при подтверждении TLS.</span><span class="sxs-lookup"><span data-stu-id="5a544-246">The application shall initialize NetX Secure TLS, configure security parameters, and load relevant certificates to be used during TLS handshake.</span></span> <span data-ttu-id="5a544-247">Фактическое подтверждение TLS происходит после установки соединения с портом MQTT TLS брокера по протоколу TCP (порт TCP по умолчанию: 8883).</span><span class="sxs-lookup"><span data-stu-id="5a544-247">The actual TLS handshake happens after a TCP connection is established on the broker's MQTT TLS port (default TCP port 8883).</span></span> <span data-ttu-id="5a544-248">После успешного подтверждения TLS пакет управления MQTT CONNECT отправляется по протоколу TLS.</span><span class="sxs-lookup"><span data-stu-id="5a544-248">Once the TLS handshake is successful, the MQTT CONNECT control packet is sent via TLS.</span></span>

<span data-ttu-id="5a544-249">Чтобы обеспечить безопасное подключение, должна быть доступна библиотека NetX Secure TLS, а клиент NetX Duo MQTT должен быть создан с использованием службы ***NX_SECURE_ENABLE***.</span><span class="sxs-lookup"><span data-stu-id="5a544-249">To make secure connections, the NetX Secure TLS library must be available, and the NetX Duo MQTT client must be built with ***NX_SECURE_ENABLE*** defined.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a544-250">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="5a544-250">Input Parameters</span></span>

- <span data-ttu-id="5a544-251">**client_ptr** Указатель на блок управления клиентом MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-251">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5a544-252">**server_ip** IP-адрес брокера.</span><span class="sxs-lookup"><span data-stu-id="5a544-252">**server_ip** Broker IP address.</span></span>
- <span data-ttu-id="5a544-253">**server_port** Номер порта брокера.</span><span class="sxs-lookup"><span data-stu-id="5a544-253">**server_port** Broker port number.</span></span> <span data-ttu-id="5a544-254">Порт по умолчанию для MQTT определяется как **_NXD_MQTT_TLS_PORT_** (8883).</span><span class="sxs-lookup"><span data-stu-id="5a544-254">The default port for MQTT isdefined as **_NXD_MQTT_TLS_PORT_** (8883).</span></span>
- <span data-ttu-id="5a544-255">**tls_setup** Предоставляемая пользователем функция обратного вызова для настройки TLS.</span><span class="sxs-lookup"><span data-stu-id="5a544-255">**tls_setup** User-provided TLS Setup callback function.</span></span> <span data-ttu-id="5a544-256">Эта функция обратного вызова вызывается для настройки параметров подключения клиента TLS.</span><span class="sxs-lookup"><span data-stu-id="5a544-256">This callback function is invoked to set up TLS client connection parameters.</span></span>
- <span data-ttu-id="5a544-257">**keep_alive** Значение проверки активности, которое будет использоваться во время сеанса.</span><span class="sxs-lookup"><span data-stu-id="5a544-257">**keep_alive** The keep-alive value to be used during the session.</span></span> <span data-ttu-id="5a544-258">Значение 0 отключает функцию проверки активности.</span><span class="sxs-lookup"><span data-stu-id="5a544-258">The value 0 turns off the keep-alive feature.</span></span>
- <span data-ttu-id="5a544-259">**clean_session** Указывает, должен ли сервер запускать этот сеанс с нуля.</span><span class="sxs-lookup"><span data-stu-id="5a544-259">**clean_session** Whether or not the server shall start this session clean.</span></span> <span data-ttu-id="5a544-260">Допустимые значения: **_NX_TRUE_ *_ или _* _NX_FALSE._**</span><span class="sxs-lookup"><span data-stu-id="5a544-260">Valid options are **_NX_TRUE_*_ or _*_NX_FALSE._**</span></span>
- <span data-ttu-id="5a544-261">**wait_option** Время ожидания подключения.</span><span class="sxs-lookup"><span data-stu-id="5a544-261">**wait_option** Connection wait time.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a544-262">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5a544-262">Return Values</span></span>

- <span data-ttu-id="5a544-263">**NXD_MQTT_SUCCESS** (0X00) – успешное подключение клиента MQTT по протоколу TLS.</span><span class="sxs-lookup"><span data-stu-id="5a544-263">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT client connection established via TLS.</span></span>
- <span data-ttu-id="5a544-264">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) – клиент уже подключен к брокеру.</span><span class="sxs-lookup"><span data-stu-id="5a544-264">**NXD_MQTT_ALREADY_CONNECTED** (0x10001) The client is already connected to the broker.</span></span>
- <span data-ttu-id="5a544-265">**NXD_MQTT_MUTEX_FAILURE** (0X10003) – не удалось получить мьютекс MQTT</span><span class="sxs-lookup"><span data-stu-id="5a544-265">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span> 
- <span data-ttu-id="5a544-266">**NXD_MQTT_INTERNAL_ERROR** (0x10004) – внутренняя логическая ошибка</span><span class="sxs-lookup"><span data-stu-id="5a544-266">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="5a544-267">**NXD_MQTT_CONNECT_FAILURE** (0X10005) – не удалось подключиться к брокеру.</span><span class="sxs-lookup"><span data-stu-id="5a544-267">**NXD_MQTT_CONNECT_FAILURE** (0x10005) Failed to connect to the broker.</span></span>
- <span data-ttu-id="5a544-268">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) – не удалось отправить сообщения брокеру.</span><span class="sxs-lookup"><span data-stu-id="5a544-268">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="5a544-269">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) – сервер ответил с сообщением об ошибке.</span><span class="sxs-lookup"><span data-stu-id="5a544-269">**NXD_MQTT_SERVER_MESSAGE_FAILURE** (0x10008) Server responded with error message.</span></span>
- <span data-ttu-id="5a544-270">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) – код отклика сервера</span><span class="sxs-lookup"><span data-stu-id="5a544-270">**NXD_MQTT_ERROR_UNACCEPTABLE_PROTOCOL** (0x10081) Server response code</span></span>
- <span data-ttu-id="5a544-271">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) – код отклика сервера</span><span class="sxs-lookup"><span data-stu-id="5a544-271">**NXD_MQTT_ERROR_IDENTIFYIER_REJECTED** (0x10082) Server response code</span></span>
- <span data-ttu-id="5a544-272">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) – код отклика сервера</span><span class="sxs-lookup"><span data-stu-id="5a544-272">**NXD_MQTT_ERROR_SERVER_UNAVAILABLE** (0x10083) Server response code</span></span>
- <span data-ttu-id="5a544-273">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) – код отклика сервера</span><span class="sxs-lookup"><span data-stu-id="5a544-273">**NXD_MQTT_ERROR_BAD_USERNAME_PASSWORD** (0x10084) Server response code</span></span>
- <span data-ttu-id="5a544-274">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) – код отклика сервера</span><span class="sxs-lookup"><span data-stu-id="5a544-274">**NXD_MQTT_ERROR_NOT_AUTHORIZED** (0x10085) Server response code</span></span>
- <span data-ttu-id="5a544-275">NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT или структура адреса сервера.</span><span class="sxs-lookup"><span data-stu-id="5a544-275">NX_PTR_ERROR (0x07) Invalid MQTT control block or sever address structure.</span></span>
- <span data-ttu-id="5a544-276">NX_INVALID_PORT (0x46) – значение порта сервера не может быть нулевым.</span><span class="sxs-lookup"><span data-stu-id="5a544-276">NX_INVALID_PORT (0x46) Server port cannot be 0.</span></span>
- <span data-ttu-id="5a544-277">NXD_MQTT_INVALID_PARAMETER (0x10009) – ошибка входного параметра</span><span class="sxs-lookup"><span data-stu-id="5a544-277">NXD_MQTT_INVALID_PARAMETER (0x10009) Input parameter error</span></span>
- <span data-ttu-id="5a544-278">NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT – поток MQTT еще не запущен.</span><span class="sxs-lookup"><span data-stu-id="5a544-278">NXD_MQTT_CLIENT_NOT_RUNNING (0x1000E) MQTT Thread has not started running yet.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a544-279">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5a544-279">Allowed From</span></span>

<span data-ttu-id="5a544-280">Потоки</span><span class="sxs-lookup"><span data-stu-id="5a544-280">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a544-281">Пример</span><span class="sxs-lookup"><span data-stu-id="5a544-281">Example</span></span>

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

## <a name="nxd_mqtt_client_publish"></a><span data-ttu-id="5a544-282">nxd_mqtt_client_publish</span><span class="sxs-lookup"><span data-stu-id="5a544-282">nxd_mqtt_client_publish</span></span>

<span data-ttu-id="5a544-283">Публикация сообщения через брокер</span><span class="sxs-lookup"><span data-stu-id="5a544-283">Publish a message through the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="5a544-284">Прототип</span><span class="sxs-lookup"><span data-stu-id="5a544-284">Prototype</span></span>

```c
UINT nxd_mqtt_client_publish(NXD_MQTT_CLIENT *client_ptr,
    CHAR *topic_name, UINT topic_name_length, CHAR *message, UINT
    message_length,
    UINT retain, UINT QoS, ULONG timeout);
```

### <a name="description"></a><span data-ttu-id="5a544-285">Описание</span><span class="sxs-lookup"><span data-stu-id="5a544-285">Description</span></span>

<span data-ttu-id="5a544-286">Эта служба публикует сообщение через брокер.</span><span class="sxs-lookup"><span data-stu-id="5a544-286">This service publishes a message through the broker.</span></span> <span data-ttu-id="5a544-287">Публикация сообщений QoS уровня 2 пока не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="5a544-287">Publishing QoS level 2 messages is not supported yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a544-288">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="5a544-288">Input Parameters</span></span>

- <span data-ttu-id="5a544-289">**client_ptr** Указатель на блок управления клиентом MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-289">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5a544-290">**topic_name** Раздел для публикации.</span><span class="sxs-lookup"><span data-stu-id="5a544-290">**topic_name** Topic to publish to.</span></span>
- <span data-ttu-id="5a544-291">**topic_name_length** Длина раздела в байтах.</span><span class="sxs-lookup"><span data-stu-id="5a544-291">**topic_name_length** Length of the topic, in bytes.</span></span>
- <span data-ttu-id="5a544-292">**message** Указатель на буфер сообщений.</span><span class="sxs-lookup"><span data-stu-id="5a544-292">**message** Pointer to the message buffer.</span></span>
- <span data-ttu-id="5a544-293">**message_length** Размер сообщения в байтах</span><span class="sxs-lookup"><span data-stu-id="5a544-293">**message_length** Size of the message, in bytes</span></span>
- <span data-ttu-id="5a544-294">**retain** Определяет, должен ли брокер хранить сообщение.</span><span class="sxs-lookup"><span data-stu-id="5a544-294">**retain** Determines if the broker shall retain the message.</span></span>
- <span data-ttu-id="5a544-295">**QoS** Рекомендуемое значение качества обслуживания: 0 или 1.</span><span class="sxs-lookup"><span data-stu-id="5a544-295">**QoS** The desired QoS value: 0 or 1.</span></span>
- <span data-ttu-id="5a544-296">**timeout** Значение времени ожидания</span><span class="sxs-lookup"><span data-stu-id="5a544-296">**timeout** Timeout value</span></span>

### <a name="return-values"></a><span data-ttu-id="5a544-297">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5a544-297">Return Values</span></span>

- <span data-ttu-id="5a544-298">**NXD_MQTT_SUCCESS** (0x00) – клиент MQTT успешно создан</span><span class="sxs-lookup"><span data-stu-id="5a544-298">**NXD_MQTT_SUCCESS** (0x00) Successful MQTT Client create</span></span>
- <span data-ttu-id="5a544-299">**NXD_MQTT_INTERNAL_ERROR** (0x10004) – внутренняя логическая ошибка.</span><span class="sxs-lookup"><span data-stu-id="5a544-299">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error.</span></span>
- <span data-ttu-id="5a544-300">**NXD_MQTT_PACKET_POOL_FAILURE** (0x10006) – не удалось получить пакет из пула пакетов.</span><span class="sxs-lookup"><span data-stu-id="5a544-300">**NXD_MQTT_PACKET_POOL_FAILURE** (0x10006) Failed to obtain packet from the packet pool.</span></span>
- <span data-ttu-id="5a544-301">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) – не удалось связаться с брокером.</span><span class="sxs-lookup"><span data-stu-id="5a544-301">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Failed to communication with the broker.</span></span>
- <span data-ttu-id="5a544-302">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) – сообщения QoS уровня 2 не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="5a544-302">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2 messages are not supported.</span></span>
- <span data-ttu-id="5a544-303">NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT, ip_ptr или указатель на пул пакетов</span><span class="sxs-lookup"><span data-stu-id="5a544-303">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="5a544-304">NXD_MQTT_INVALID_PARAMETER (0x10009) – ошибка входного параметра</span><span class="sxs-lookup"><span data-stu-id="5a544-304">NXD_MQTT_INVALID_PARAMETER (0x10009) Input parameter error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a544-305">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5a544-305">Allowed From</span></span>

<span data-ttu-id="5a544-306">Потоки</span><span class="sxs-lookup"><span data-stu-id="5a544-306">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a544-307">Пример</span><span class="sxs-lookup"><span data-stu-id="5a544-307">Example</span></span>

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

## <a name="nxd_mqtt_client_subscribe"></a><span data-ttu-id="5a544-308">nxd_mqtt_client_subscribe</span><span class="sxs-lookup"><span data-stu-id="5a544-308">nxd_mqtt_client_subscribe</span></span>

<span data-ttu-id="5a544-309">Оформление подписки на тему</span><span class="sxs-lookup"><span data-stu-id="5a544-309">Subscribe to a topic</span></span>

### <a name="prototype"></a><span data-ttu-id="5a544-310">Прототип</span><span class="sxs-lookup"><span data-stu-id="5a544-310">Prototype</span></span>

```c
UINT nxd_mqtt_client_subscribe(NXD_MQTT_CLIENT
    *mqtt_client_ptr, CHAR *topic_name,
    UINT topic_name_length, UINT QoS);
```

### <a name="description"></a><span data-ttu-id="5a544-311">Описание</span><span class="sxs-lookup"><span data-stu-id="5a544-311">Description</span></span>

<span data-ttu-id="5a544-312">Эта служба подписывается на конкретный раздел.</span><span class="sxs-lookup"><span data-stu-id="5a544-312">This service subscribes to a specific topic.</span></span> <span data-ttu-id="5a544-313">Подписка на сообщения QoS уровня 2 пока не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="5a544-313">Subscribing to QoS level 2 messages is not supported yet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a544-314">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="5a544-314">Input Parameters</span></span>

- <span data-ttu-id="5a544-315">**client_ptr** Указатель на блок управления клиентом MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-315">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5a544-316">**topic_name** Раздел для публикации.</span><span class="sxs-lookup"><span data-stu-id="5a544-316">**topic_name** Topic to publish to.</span></span>
- <span data-ttu-id="5a544-317">**topic_name_length** Длина раздела в байтах.</span><span class="sxs-lookup"><span data-stu-id="5a544-317">**topic_name_length** Length of the topic, in bytes.</span></span>
- <span data-ttu-id="5a544-318">**QoS Рекомендуемый уровень качества обслуживания:** 0 или 1.</span><span class="sxs-lookup"><span data-stu-id="5a544-318">**QoS The desired QoS level:** 0 or 1.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a544-319">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5a544-319">Return Values</span></span>

- <span data-ttu-id="5a544-320">**NXD_MQTT_SUCCESS** (0x00) – подписка на раздел успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="5a544-320">**NXD_MQTT_SUCCESS** (0x00) Successfully subscribed to the topic.</span></span>
- <span data-ttu-id="5a544-321">**NXD_MQTT_NOT_CONNECTED** (0x10002) – клиент не подключен к брокеру.</span><span class="sxs-lookup"><span data-stu-id="5a544-321">**NXD_MQTT_NOT_CONNECTED** (0x10002) The client is not connected to the broker.</span></span>
- <span data-ttu-id="5a544-322">**NXD_MQTT_MUTEX_FAILURE** (0X10003) – не удалось получить мьютекс MQTT</span><span class="sxs-lookup"><span data-stu-id="5a544-322">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex</span></span>
- <span data-ttu-id="5a544-323">**NXD_MQTT_INTERNAL_ERROR** (0x10004) – внутренняя логическая ошибка</span><span class="sxs-lookup"><span data-stu-id="5a544-323">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="5a544-324">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) – не удалось отправить сообщения брокеру.</span><span class="sxs-lookup"><span data-stu-id="5a544-324">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="5a544-325">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) – сообщения QoS уровня 2 не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="5a544-325">**NXD_MQTT_QOS2_NOT_SUPPORTED** (0x1000C) QoS level 2messages are not supported.</span></span>
- <span data-ttu-id="5a544-326">NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT, ip_ptr или указатель на пул пакетов</span><span class="sxs-lookup"><span data-stu-id="5a544-326">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="5a544-327">NXD_MQTT_INVALID_PARAMETER (0x10009) – значение topic_name не задано, значение topic_name_length равно нулю либо значение качества обслуживания недопустимо.</span><span class="sxs-lookup"><span data-stu-id="5a544-327">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name is not set, or topic_name_length is zero, or QoS is value is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a544-328">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5a544-328">Allowed From</span></span>

<span data-ttu-id="5a544-329">Потоки</span><span class="sxs-lookup"><span data-stu-id="5a544-329">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a544-330">Пример</span><span class="sxs-lookup"><span data-stu-id="5a544-330">Example</span></span>

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_subscribe(&my_client, topic,
    STRLEN(topic), 0);

/* If status is NXD_MQTT_SUCCESS, the client successfully
subscribes to the topic "temperate". At this point the client
is ready for receiving messages from the broker. */
```

## <a name="nxd_mqtt_client_unsubscribe"></a><span data-ttu-id="5a544-331">nxd_mqtt_client_unsubscribe</span><span class="sxs-lookup"><span data-stu-id="5a544-331">nxd_mqtt_client_unsubscribe</span></span>

<span data-ttu-id="5a544-332">Отмена подписки на раздел</span><span class="sxs-lookup"><span data-stu-id="5a544-332">Unsubscribe from a topic</span></span>

### <a name="prototype"></a><span data-ttu-id="5a544-333">Прототип</span><span class="sxs-lookup"><span data-stu-id="5a544-333">Prototype</span></span>

```c
UINT nxd_mqtt_client_unsubscribe(NXD_MQTT_CLIENT
    *mqtt_client_pr,
    CHAR *topic_name,
    UINT topic_name_length);
```

### <a name="description"></a><span data-ttu-id="5a544-334">Описание</span><span class="sxs-lookup"><span data-stu-id="5a544-334">Description</span></span>

<span data-ttu-id="5a544-335">Эта служба отменяет подписку на раздел.</span><span class="sxs-lookup"><span data-stu-id="5a544-335">This service unsubscribes from a topic.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a544-336">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="5a544-336">Input Parameters</span></span>

- <span data-ttu-id="5a544-337">**client_ptr** Указатель на блок управления клиентом MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-337">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5a544-338">**topic_name** Раздел, от которого необходимо отписаться.</span><span class="sxs-lookup"><span data-stu-id="5a544-338">**topic_name** Topic to unsubscribe from.</span></span>
- <span data-ttu-id="5a544-339">**topic_name_length** Длина раздела в байтах.</span><span class="sxs-lookup"><span data-stu-id="5a544-339">**topic_name_length** Length of the topic, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a544-340">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5a544-340">Return Values</span></span>

- <span data-ttu-id="5a544-341">**NXD_MQTT_SUCCESS** (0x00) – подписка на раздел успешно отменена.</span><span class="sxs-lookup"><span data-stu-id="5a544-341">**NXD_MQTT_SUCCESS** (0x00) Successfully unsubscribed from the topic.</span></span>
- <span data-ttu-id="5a544-342">**NXD_MQTT_NOT_CONNECTED** (0x10002) – клиент не подключен к брокеру.</span><span class="sxs-lookup"><span data-stu-id="5a544-342">**NXD_MQTT_NOT_CONNECTED** (0x10002) The client is not connected to the broker.</span></span>
- <span data-ttu-id="5a544-343">**NXD_MQTT_MUTEX_FAILURE** (0x10003) – не удалось получить мьютекс MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-343">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex.</span></span>
- <span data-ttu-id="5a544-344">**NXD_MQTT_INTERNAL_ERROR** (0x10004) – внутренняя логическая ошибка</span><span class="sxs-lookup"><span data-stu-id="5a544-344">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="5a544-345">**NXD_MQTT_COMMUNICATION_FAILURE** (0X10007) – не удалось отправить сообщения брокеру.</span><span class="sxs-lookup"><span data-stu-id="5a544-345">**NXD_MQTT_COMMUNICATION_FAILURE** (0x10007) Unable to send messages to the broker.</span></span>
- <span data-ttu-id="5a544-346">NX_PTR_ERROR (0x07) – недопустимый указатель на блок управления MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-346">NX_PTR_ERROR (0x07) Invalid MQTT control block pointer</span></span>
- <span data-ttu-id="5a544-347">NXD_MQTT_INVALID_PARAMETER (0x10009) – значение topic_name не задано или значение topic_name_length равно нулю.</span><span class="sxs-lookup"><span data-stu-id="5a544-347">NXD_MQTT_INVALID_PARAMETER (0x10009) topic_name is not set, or topic_name_length is zero.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a544-348">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5a544-348">Allowed From</span></span>

<span data-ttu-id="5a544-349">Потоки</span><span class="sxs-lookup"><span data-stu-id="5a544-349">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a544-350">Пример</span><span class="sxs-lookup"><span data-stu-id="5a544-350">Example</span></span>

```c
/* Subscribe to the topic "temperature" with QoS level 0 */
CHAR *topic = "temperature";

status = nxd_mqtt_client_unsubscribe(&my_client, topic,
    STRLEN(topic));

/* If status is NXD_MQTT_SUCCESS, the client successfully
unsubscribes the topic "temperate". */
```

## <a name="nxd_mqtt_client_receive_notify_set"></a><span data-ttu-id="5a544-351">nxd_mqtt_client_receive_notify_set</span><span class="sxs-lookup"><span data-stu-id="5a544-351">nxd_mqtt_client_receive_notify_set</span></span>

<span data-ttu-id="5a544-352">Установка функции обратного вызова для уведомления о сообщении MQTT о получении</span><span class="sxs-lookup"><span data-stu-id="5a544-352">Set MQTT message receive notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="5a544-353">Прототип</span><span class="sxs-lookup"><span data-stu-id="5a544-353">Prototype</span></span>

```c
UINT nxd_mqtt_client_receive_notify_set(NXD_MQTT_CLIENT
    *client_ptr,
    VOID(*receive_notify)(NXD_MQTT_CLIENT* client_ptr,
    UINT message_count));
```

### <a name="description"></a><span data-ttu-id="5a544-354">Описание</span><span class="sxs-lookup"><span data-stu-id="5a544-354">Description</span></span>

<span data-ttu-id="5a544-355">Эта служба регистрирует функцию обратного вызова с клиентом MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-355">This service registers a callback function with the MQTT client.</span></span> <span data-ttu-id="5a544-356">При получении сообщения, опубликованного брокером, клиент MQTT сохраняет сообщение в очередь получения.</span><span class="sxs-lookup"><span data-stu-id="5a544-356">Upon receiving a message published by the broker, MQTT client stores the message in the receive queue.</span></span> <span data-ttu-id="5a544-357">Если функция обратного вызова задана, она активируется, чтобы уведомить приложение о том, что сообщение готово к извлечению.</span><span class="sxs-lookup"><span data-stu-id="5a544-357">If the callback function is set, the callback function is invoked to notify the application that a message is ready to be retrieved.</span></span> <span data-ttu-id="5a544-358">Функция уведомления о получении принимает указатель на блок управления клиентом MQTT и значение *message_count*, указывающее количество сообщений, доступных в очереди получения.</span><span class="sxs-lookup"><span data-stu-id="5a544-358">The receive notify function takes a pointer to the MQTT client control block, and a *message_count* indicating the number of messages available in the receive queue.</span></span> <span data-ttu-id="5a544-359">Обратите внимание, что в период с момента уведомления о получении до момента, когда приложение извлекает эти сообщения, количество сообщений может измениться, поскольку в этот период могут поступить новые сообщения.</span><span class="sxs-lookup"><span data-stu-id="5a544-359">Note that the number may change between the receive notification and when the application retrieves these messages, as new messages may have arrived in the interval.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a544-360">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="5a544-360">Input Parameters</span></span>

- <span data-ttu-id="5a544-361">**client_ptr** Указатель на блок управления клиентом MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-361">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5a544-362">**receive_notify** Задаваемая пользователем функция обратного вызова будет активирована при получении сообщения.</span><span class="sxs-lookup"><span data-stu-id="5a544-362">**receive_notify** User supplied callback function to be invoked on receiving a message.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a544-363">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5a544-363">Return Values</span></span>

- <span data-ttu-id="5a544-364">**NXD_MQTT_SUCCESS** (0x00) – функция уведомления о получении сообщений успешно задана.</span><span class="sxs-lookup"><span data-stu-id="5a544-364">**NXD_MQTT_SUCCESS** (0x00) Successfully set the receive notify function.</span></span>
- <span data-ttu-id="5a544-365">NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-365">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a544-366">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5a544-366">Allowed From</span></span>

<span data-ttu-id="5a544-367">Потоки</span><span class="sxs-lookup"><span data-stu-id="5a544-367">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a544-368">Пример</span><span class="sxs-lookup"><span data-stu-id="5a544-368">Example</span></span>

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

## <a name="nxd_mqtt_client_message_get"></a><span data-ttu-id="5a544-369">nxd_mqtt_client_message_get</span><span class="sxs-lookup"><span data-stu-id="5a544-369">nxd_mqtt_client_message_get</span></span>

<span data-ttu-id="5a544-370">Извлечение сообщения из брокера</span><span class="sxs-lookup"><span data-stu-id="5a544-370">Retrieve a message from the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="5a544-371">Прототип</span><span class="sxs-lookup"><span data-stu-id="5a544-371">Prototype</span></span>

```c
UINT nxd_mqtt_client_message_get(NXD_MQTT_CLIENT
    *client_ptr,
    UCHAR *topic_buffer, UINT topic_buffer_size,
    UINT *actual_topic_length, UCHAR *message_buffer,
    UINT message_buffer_size, UINT *actual_message_length);
```

### <a name="description"></a><span data-ttu-id="5a544-372">Описание</span><span class="sxs-lookup"><span data-stu-id="5a544-372">Description</span></span>

<span data-ttu-id="5a544-373">Эта служба извлекает сообщение, опубликованное брокером.</span><span class="sxs-lookup"><span data-stu-id="5a544-373">This service retrieves a message published by the broker.</span></span> <span data-ttu-id="5a544-374">Все входящие сообщения хранятся в очереди получения.</span><span class="sxs-lookup"><span data-stu-id="5a544-374">All incoming messages are stored in the receive queue.</span></span> <span data-ttu-id="5a544-375">Приложение использует эту службу для извлечения этих сообщений.</span><span class="sxs-lookup"><span data-stu-id="5a544-375">The application uses this service to retrieve these messages.</span></span> <span data-ttu-id="5a544-376">Этот вызов не блокируется.</span><span class="sxs-lookup"><span data-stu-id="5a544-376">This call is non-blocking.</span></span> <span data-ttu-id="5a544-377">Если очередь получения пуста, эта служба возвращает \***NXD_MQTT_NO_MESSAGE** _.</span><span class="sxs-lookup"><span data-stu-id="5a544-377">If the receive queue is empty, this service returns \***NXD_MQTT_NO_MESSAGE** _.</span></span> <span data-ttu-id="5a544-378">Приложение, которое должно получать уведомление о входящем сообщении, может вызвать службу _ *_nxd_mqtt_client_receive_notify_set_*\* для регистрации функции обратного вызова для получения.</span><span class="sxs-lookup"><span data-stu-id="5a544-378">An application wishing to be notified of incoming message can call the service _ *_nxd_mqtt_client_receive_notify_set_*\* to register a receive callback function.</span></span>

<span data-ttu-id="5a544-379">Вызывающий объект должен предоставить место для сохранения строки раздела и текста сообщения.</span><span class="sxs-lookup"><span data-stu-id="5a544-379">The caller needs to provide memory space for the topic string and the message body.</span></span> <span data-ttu-id="5a544-380">Размеры этих двух буферов передаются с помощью служб *topic_buffer_size* и *message_buffer_size*.</span><span class="sxs-lookup"><span data-stu-id="5a544-380">The sizes of these two buffers are passed in using *topic_buffer_size* and *message_buffer_size*.</span></span> <span data-ttu-id="5a544-381">Фактическое число байтов в строке раздела и тексте сообщения возвращаются с помощью *actual_topic_length* и *actual_message_length*.</span><span class="sxs-lookup"><span data-stu-id="5a544-381">The actual number of bytes in the topic string and the message body are returned in *actual_topic_length* and *actual_message_length*.</span></span> <span data-ttu-id="5a544-382">Если длина раздела или сообщения превышает выделенный объем буфера, эта служба возвращает код ошибки *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.</span><span class="sxs-lookup"><span data-stu-id="5a544-382">If topic length or massage length is greater than the buffer space provided, this service returns error code *NXD_MQTT_INSUFFICIENT_BUFFER_SIZE*.</span></span>

<span data-ttu-id="5a544-383">Приложение должно выделить буфер большего размера и повторить попытку.</span><span class="sxs-lookup"><span data-stu-id="5a544-383">The application shall allocate a bigger buffer and try again.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a544-384">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="5a544-384">Input Parameters</span></span>

- <span data-ttu-id="5a544-385">**client_ptr** Указатель на блок управления клиентом MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-385">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5a544-386">**topic_buffer** Указатель на место в памяти для копирования строки раздела.</span><span class="sxs-lookup"><span data-stu-id="5a544-386">**topic_buffer** Pointer to the memory location where the topic string is copied into.</span></span>
- <span data-ttu-id="5a544-387">**topic_buffer_size** Размер буфера раздела.</span><span class="sxs-lookup"><span data-stu-id="5a544-387">**topic_buffer_size** Size of the topic buffer.</span></span>
- <span data-ttu-id="5a544-388">**actual_topic_length** Указатель на место в памяти для возвращаемого значения фактической длины раздела.</span><span class="sxs-lookup"><span data-stu-id="5a544-388">**actual_topic_length** Pointer to the memory location where the actual topic length is returned.</span></span>
- <span data-ttu-id="5a544-389">**topic_buffer** Указатель на место в памяти для копирования строки сообщения.</span><span class="sxs-lookup"><span data-stu-id="5a544-389">**message_buffer** Pointer to the memory location where the message string is copied into.</span></span>
- <span data-ttu-id="5a544-390">**message_buffer_size** Размер буфера сообщений.</span><span class="sxs-lookup"><span data-stu-id="5a544-390">**message_buffer_size** Size of the message buffer.</span></span>
- <span data-ttu-id="5a544-391">**actual_message_length** Указатель на место в памяти для возвращаемого значения длины сообщения.</span><span class="sxs-lookup"><span data-stu-id="5a544-391">**actual_message_length** Pointer to the memory location where the message length is returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a544-392">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5a544-392">Return Values</span></span>

- <span data-ttu-id="5a544-393">**NXD_MQTT_SUCCESS** (0x00) – сообщение успешно извлечено.</span><span class="sxs-lookup"><span data-stu-id="5a544-393">**NXD_MQTT_SUCCESS** (0x00) Successfully retrieved message.</span></span>
- <span data-ttu-id="5a544-394">**NXD_MQTT_INTERNAL_ERROR** (0x10004) – внутренняя логическая ошибка</span><span class="sxs-lookup"><span data-stu-id="5a544-394">**NXD_MQTT_INTERNAL_ERROR** (0x10004) Internal logic error</span></span>
- <span data-ttu-id="5a544-395">**NXD_MQTT_NO_MESSAGE** (0x1000A) – очередь получения пуста.</span><span class="sxs-lookup"><span data-stu-id="5a544-395">**NXD_MQTT_NO_MESSAGE** (0x1000A) The receive queue is empty.</span></span>
- <span data-ttu-id="5a544-396">**NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) – размер буфера раздела или сообщения слишком мал для раздела или сообщения.</span><span class="sxs-lookup"><span data-stu-id="5a544-396">**NXD_MQTT_INSUFFICIENT_BUFFER_SIZE** (0x1000D) Topic buffer or message buffer is too small for the topic or the message.</span></span>
- <span data-ttu-id="5a544-397">NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT, ip_ptr или указатель на пул пакетов</span><span class="sxs-lookup"><span data-stu-id="5a544-397">NX_PTR_ERROR (0x07) Invalid MQTT control block, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="5a544-398">NXD_MQTT_INVALID_PARAMETER (0x10009) – указатель message_buffer или topic_buffer имеет значение NULL</span><span class="sxs-lookup"><span data-stu-id="5a544-398">NXD_MQTT_INVALID_PARAMETER (0x10009) message_buffer or topic_buffer pointer is NULL</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a544-399">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5a544-399">Allowed From</span></span>

<span data-ttu-id="5a544-400">Потоки</span><span class="sxs-lookup"><span data-stu-id="5a544-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a544-401">Пример</span><span class="sxs-lookup"><span data-stu-id="5a544-401">Example</span></span>

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

## <a name="nxd_mqtt_client_disconnect_notify_set"></a><span data-ttu-id="5a544-402">nxd_mqtt_client_disconnect_notify_set</span><span class="sxs-lookup"><span data-stu-id="5a544-402">nxd_mqtt_client_disconnect_notify_set</span></span>

<span data-ttu-id="5a544-403">Установка функции обратного вызова для уведомления о сообщении MQTT об отключении</span><span class="sxs-lookup"><span data-stu-id="5a544-403">Set MQTT message disconnect notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="5a544-404">Прототип</span><span class="sxs-lookup"><span data-stu-id="5a544-404">Prototype</span></span>

```c
UINT nxd_mqtt_client_disconnect_notify_set(
    NXD_MQTT_CLIENT *client_ptr,
    VOID(*disconnect_notify)(NXD_MQTT_CLIENT* client_ptr));
```

### <a name="description"></a><span data-ttu-id="5a544-405">Описание</span><span class="sxs-lookup"><span data-stu-id="5a544-405">Description</span></span>

<span data-ttu-id="5a544-406">Эта служба регистрирует функцию обратного вызова с клиентом MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-406">This service registers a callback function with the MQTT client.</span></span> <span data-ttu-id="5a544-407">Когда MQTT обнаруживает, что соединение с брокером прервано, он вызывает эту функцию для оповещения приложения.</span><span class="sxs-lookup"><span data-stu-id="5a544-407">When MQTT detects the connection to the broker is lost, it calls this notify function to alert the application.</span></span> <span data-ttu-id="5a544-408">Таким образом, приложение может использовать эту функцию обратного вызова для обнаружения прерванного соединения и для восстановления подключения к брокеру.</span><span class="sxs-lookup"><span data-stu-id="5a544-408">Therefore, the application can use this callback function to detect a lost connection, and to be able to re-establish connection to the broker.</span></span>

```c
VOID callback_func(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="input-parameters"></a><span data-ttu-id="5a544-409">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="5a544-409">Input Parameters</span></span>

- <span data-ttu-id="5a544-410">**client_ptr** Указатель на блок управления клиентом MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-410">**client_ptr** Pointer to MQTT Client control block.</span></span>
- <span data-ttu-id="5a544-411">**disconnect_notify** Задаваемая пользователем функция обратного вызова, которая активируется, когда MQTT обнаруживает, что соединение с брокером прервано.</span><span class="sxs-lookup"><span data-stu-id="5a544-411">**disconnect_notify** User supplied callback function to be invoked when MQTT detects the connection to the broker is lost.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a544-412">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5a544-412">Return Values</span></span>

- <span data-ttu-id="5a544-413">**NXD_MQTT_SUCCESS** (0x00) – функция уведомления об отключении успешно задана.</span><span class="sxs-lookup"><span data-stu-id="5a544-413">**NXD_MQTT_SUCCESS** (0x00) Successfully set the disconnect notify function.</span></span>
- <span data-ttu-id="5a544-414">NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-414">NX_PTR_ERROR (0x07) Invalid MQTT control block.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a544-415">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5a544-415">Allowed From</span></span>

<span data-ttu-id="5a544-416">Потоки</span><span class="sxs-lookup"><span data-stu-id="5a544-416">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a544-417">Пример</span><span class="sxs-lookup"><span data-stu-id="5a544-417">Example</span></span>

```c
VOID disconnect_notify(NXD_MQTT_CLIENT *client_ptr)
{
/* MQTT client is disconnected from the broker. Notify the application so it can re-connect to the broker. */
}

status = nxd_mqtt_client_disconnect_notify_set(client_ptr,
    disconnect_notify);
```

## <a name="nxd_mqtt_client_disconnect"></a><span data-ttu-id="5a544-418">nxd_mqtt_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="5a544-418">nxd_mqtt_client_disconnect</span></span>

<span data-ttu-id="5a544-419">Отключение клиента MQTT от брокера</span><span class="sxs-lookup"><span data-stu-id="5a544-419">Disconnect MQTT client from the broker</span></span>

### <a name="prototype"></a><span data-ttu-id="5a544-420">Прототип</span><span class="sxs-lookup"><span data-stu-id="5a544-420">Prototype</span></span>

```c
UINT nxd_mqtt_client_disconnect(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="5a544-421">Описание</span><span class="sxs-lookup"><span data-stu-id="5a544-421">Description</span></span>

<span data-ttu-id="5a544-422">Эта служба отключает клиент от брокера.</span><span class="sxs-lookup"><span data-stu-id="5a544-422">This service disconnects the client from the broker.</span></span> <span data-ttu-id="5a544-423">Обратите внимание, что сообщения в очереди получения освобождаются.</span><span class="sxs-lookup"><span data-stu-id="5a544-423">Note that messages on the receive queue are released.</span></span> <span data-ttu-id="5a544-424">Сообщения с QoS 1 в очереди передачи не освобождаются.</span><span class="sxs-lookup"><span data-stu-id="5a544-424">Messages with QoS 1 in the transmit queue are not released.</span></span> <span data-ttu-id="5a544-425">После повторного подключения клиента к серверу можно обработать сообщения QoS 1, если клиент не подключится к серверу с флагом *clean_session*, для которого установлено значение ***NX_TRUE***.</span><span class="sxs-lookup"><span data-stu-id="5a544-425">After the client reconnects to the server, QoS 1 messages can be processed, unless the client reconnects to the server with *clean_session* flag set to ***NX_TRUE***.</span></span>

<span data-ttu-id="5a544-426">Если установлено подключение с защитой TLS, эта служба перед отключением соединения по TCP закроет сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="5a544-426">If the connection was made with TLS security protection, this service will close the TLS session before disconnecting the TCP connection.</span></span>

<span data-ttu-id="5a544-427">Фактический вызов отключения сокета TCP имеет параметр ожидания, задаваемый с помощью службы NXD_MQTT_SOCKET_TIMEOUT (такты таймера).</span><span class="sxs-lookup"><span data-stu-id="5a544-427">The actual TCP socket disconnect call has a wait option defined by NXD_MQTT_SOCKET_TIMEOUT (timer ticks).</span></span> <span data-ttu-id="5a544-428">По умолчанию используется значение NX_WAIT_FOREVER.</span><span class="sxs-lookup"><span data-stu-id="5a544-428">The default value is NX_WAIT_FOREVER.</span></span> <span data-ttu-id="5a544-429">Чтобы избежать неограниченной приостановки в случае прерывания сетевого соединения или отсутствия ответа от сервера, установите для этого параметра конечное значение.</span><span class="sxs-lookup"><span data-stu-id="5a544-429">To avoid indefinite suspension in the event that the network connection is lost or the server is not responding, set this option to a finite value.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a544-430">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="5a544-430">Input Parameters</span></span>

- <span data-ttu-id="5a544-431">**client_ptr** Указатель на блок управления клиентом MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-431">**client_ptr** Pointer to MQTT Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a544-432">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5a544-432">Return Values</span></span>

- <span data-ttu-id="5a544-433">**NXD_MQTT_SUCCESS** (0x00) – успешное отключение от брокера</span><span class="sxs-lookup"><span data-stu-id="5a544-433">**NXD_MQTT_SUCCESS** (0x00) Successfully disconnected from broker</span></span>
- <span data-ttu-id="5a544-434">**NXD_MQTT_MUTEX_FAILURE** (0x10003) – не удалось получить мьютекс MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-434">**NXD_MQTT_MUTEX_FAILURE** (0x10003) Failed to obtain MQTT mutex.</span></span>
- <span data-ttu-id="5a544-435">NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT</span><span class="sxs-lookup"><span data-stu-id="5a544-435">NX_PTR_ERROR (0x07) Invalid MQTT control block</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a544-436">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5a544-436">Allowed From</span></span>

<span data-ttu-id="5a544-437">Потоки</span><span class="sxs-lookup"><span data-stu-id="5a544-437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a544-438">Пример</span><span class="sxs-lookup"><span data-stu-id="5a544-438">Example</span></span>

```c
/* Disconnect from the broker. */
status = nxd_mqtt_client_disconnect(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
disconnected from the broker. */
```

## <a name="nxd_mqtt_client_delete"></a><span data-ttu-id="5a544-439">nxd_mqtt_client_delete</span><span class="sxs-lookup"><span data-stu-id="5a544-439">nxd_mqtt_client_delete</span></span>

<span data-ttu-id="5a544-440">Удаление экземпляра клиента MQTT</span><span class="sxs-lookup"><span data-stu-id="5a544-440">Delete the MQTT client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5a544-441">Прототип</span><span class="sxs-lookup"><span data-stu-id="5a544-441">Prototype</span></span>

```c
UINT nxd_mqtt_client_delete(NXD_MQTT_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="5a544-442">Описание</span><span class="sxs-lookup"><span data-stu-id="5a544-442">Description</span></span>

<span data-ttu-id="5a544-443">Эта служба удаляет экземпляр клиента MQTT и освобождает внутренние ресурсы.</span><span class="sxs-lookup"><span data-stu-id="5a544-443">This service deletes the MQTT client instance and releases internal resources.</span></span> <span data-ttu-id="5a544-444">Эта служба автоматически отключает клиент от брокера, если он по-прежнему подключен.</span><span class="sxs-lookup"><span data-stu-id="5a544-444">This service automatically disconnects the client from the broker if it is still connected.</span></span> <span data-ttu-id="5a544-445">Сообщения, которые еще не были отправлены или не подтверждены, освобождаются.</span><span class="sxs-lookup"><span data-stu-id="5a544-445">Messages not yet transmitted or not been acknowledged are released.</span></span> <span data-ttu-id="5a544-446">Также освобождаются сообщения, полученные, но не извлеченные приложением.</span><span class="sxs-lookup"><span data-stu-id="5a544-446">Messages received but not retrieved by the application are also released.</span></span>

<span data-ttu-id="5a544-447">Если установлено подключение с защитой TLS, эта служба перед отключением соединения по TCP закрывает сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="5a544-447">If the connection was made with TLS security protection, this service closes the TLS session before disconnecting the TCP connection.</span></span>

<span data-ttu-id="5a544-448">После удаления клиента приложение, желающее использовать службу MQTT, должно создать новый экземпляр.</span><span class="sxs-lookup"><span data-stu-id="5a544-448">After the client is deleted, an application wishing to use MQTT service needs to create a new instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5a544-449">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="5a544-449">Input Parameters</span></span>

- <span data-ttu-id="5a544-450">**client_ptr** Указатель на блок управления клиентом MQTT.</span><span class="sxs-lookup"><span data-stu-id="5a544-450">**client_ptr** Pointer to MQTT Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5a544-451">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5a544-451">Return Values</span></span>

- <span data-ttu-id="5a544-452">**NXD_MQTT_SUCCESS** (0x00) – клиент MQTT успешно удален.</span><span class="sxs-lookup"><span data-stu-id="5a544-452">**NXD_MQTT_SUCCESS** (0x00) Successfully deleted MQTT client.</span></span>
- <span data-ttu-id="5a544-453">NX_PTR_ERROR (0x07) – недопустимый блок управления MQTT</span><span class="sxs-lookup"><span data-stu-id="5a544-453">NX_PTR_ERROR (0x07) Invalid MQTT control block</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5a544-454">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5a544-454">Allowed From</span></span>

<span data-ttu-id="5a544-455">Потоки</span><span class="sxs-lookup"><span data-stu-id="5a544-455">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5a544-456">Пример</span><span class="sxs-lookup"><span data-stu-id="5a544-456">Example</span></span>

```c
/* Delete the MQTT client instance. */
status = nxd_mqtt_client_delete(&my_client);

/* If status is NXD_MQTT_SUCCESS the client is successfully
deleted from the system. */
```
