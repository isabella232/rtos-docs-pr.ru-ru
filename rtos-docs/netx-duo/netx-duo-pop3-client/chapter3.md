---
title: Глава 3. Описание служб клиента POP3
description: Эта часть содержит описание всех служб клиента POP3 для NetX Duo, которые перечислены ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1f7681c8f3fe161db8a37a82574ab7d5e9bf348e
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814615"
---
# <a name="chapter-3---description-of-pop3-client-services"></a><span data-ttu-id="ff1ff-103">Глава 3. Описание служб клиента POP3</span><span class="sxs-lookup"><span data-stu-id="ff1ff-103">Chapter 3 - Description of POP3 Client Services</span></span>

<span data-ttu-id="ff1ff-104">Эта часть содержит описание всех служб клиента POP3 для NetX Duo, которые перечислены ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-104">This chapter contains a description of all NetX Duo POP3 Client services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="ff1ff-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_pop3_client_create"></a><span data-ttu-id="ff1ff-106">nx_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="ff1ff-106">nx_pop3_client_create</span></span>

<span data-ttu-id="ff1ff-107">Создание экземпляра клиента POP3 для IPv4</span><span class="sxs-lookup"><span data-stu-id="ff1ff-107">Create a POP3 Client instance for IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="ff1ff-108">Прототип</span><span class="sxs-lookup"><span data-stu-id="ff1ff-108">Prototype</span></span>

```C
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    ULONG server_ip_address, ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="ff1ff-109">Описание</span><span class="sxs-lookup"><span data-stu-id="ff1ff-109">Description</span></span>

<span data-ttu-id="ff1ff-110">Эта служба создает экземпляр клиента POP3</span><span class="sxs-lookup"><span data-stu-id="ff1ff-110">This service creates an instance of the POP3 Client.</span></span> <span data-ttu-id="ff1ff-111">Она поддерживает только IPv4-адреса сервера POP3.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-111">It supports only IPv4 POP3 server addresses.</span></span>

<span data-ttu-id="ff1ff-112">Обратите внимание, что приложение должно сначала создать экземпляр IP и пул пакетов, чтобы клиент POP3 мог передавать пакеты.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-112">Note that the device application must first create an IP instance and a packet pool for the POP3 Client to transmit packets.</span></span> <span data-ttu-id="ff1ff-113">Можно создать новый пул пакетов исключительно для задачи клиента POP3 или использовать тот же пул, который применялся для создания экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-113">This packet pool created for use exclusively by the POP3 Client task or the same packet pool used in the IP instance creation.</span></span> <span data-ttu-id="ff1ff-114">Также этот пул пакетов может применяться как пул пакетов для драйвера Ethernet, но у такого подхода есть важный недостаток: крупные пулы пакетов, предназначенные для получения полезных данных потенциально больших пакетов, нерационально использовать для клиента POP3, который отправляет на сервер относительно небольшие пакеты сообщений POP3.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-114">The packet pool may also be shared with the Ethernet driver packet pool but this has the disadvantage of using large packet pools whose payload is intended for receiving potentially large packets payload for the POP3 Client to send relatively small POP3 message packets to the server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ff1ff-115">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ff1ff-115">Input Parameters</span></span>

- <span data-ttu-id="ff1ff-116">**client_ptr** — указатель на создаваемый клиент.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-116">**client_ptr** Pointer to Client to create</span></span>
- <span data-ttu-id="ff1ff-117">**APOP_authentication** — включение проверки подлинности APOP.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-117">**APOP_authentication** Enable APOP authentication</span></span>
- <span data-ttu-id="ff1ff-118">**ip_ptr** — указатель на экземпляр IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-118">**ip_ptr Pointer** to IP instance</span></span>
- <span data-ttu-id="ff1ff-119">**packet_pool_ptr** — указатель на пул пакетов клиента.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-119">**packet_pool_ptr** Pointer to Client packet pool</span></span>
- <span data-ttu-id="ff1ff-120">**server_ip_address** — IPV4-адрес сервера POP3.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-120">**server_ip_address** POP3 server IPv4 address</span></span>
- <span data-ttu-id="ff1ff-121">**server_port** — порт сервера POP3.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-121">**server_port** POP3 server port</span></span>
- <span data-ttu-id="ff1ff-122">**client_name** — указатель на имя клиента.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-122">**client_name** Pointer to Client name</span></span>
- <span data-ttu-id="ff1ff-123">**client_password** — указатель на пароль клиента.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-123">**client_password** Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="ff1ff-124">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ff1ff-124">Return Values</span></span>

- <span data-ttu-id="ff1ff-125">**NX_SUCCESS** (0x00) — клиент успешно создан.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-125">**NX_SUCCESS** (0x00) Client successfully created</span></span>
- <span data-ttu-id="ff1ff-126">**status** — состояние завершения вызовов служб NetX Duo и ThreadX.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-126">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
- <span data-ttu-id="ff1ff-127">NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-127">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="ff1ff-128">NX_POP3_PARAM_ERROR (0xB1) — недопустимые входные данные, отличающиеся от указателя.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-128">NX_POP3_PARAM_ERROR (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff1ff-129">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ff1ff-129">Allowed From</span></span>

<span data-ttu-id="ff1ff-130">Код приложения</span><span class="sxs-lookup"><span data-stu-id="ff1ff-130">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ff1ff-131">Например, .</span><span class="sxs-lookup"><span data-stu-id="ff1ff-131">Example</span></span>

```C
/* Create the POP3 Client. Note that the Client uses its password for its APOP shared
    secret. */

/* Set up user defined callback services. */
/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD "pass"
#define POP3_SERVER_ADDRESS IP_ADDRESS(192,2,2,92)
#define POP3_SERVER_PORT 110

/* Create a NetX POP3 Client instance. */
status = nx_pop3_client_create(&demo_client,
    NX_FALSE /* disable APOP authentication */,
    &client_ip, &client_packet_pool,
    POP3_SERVER_ADDRESS, POP3_SERVER_PORT,
    LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nxd_pop3_client_create"></a><span data-ttu-id="ff1ff-132">nxd_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="ff1ff-132">nxd_pop3_client_create</span></span>

<span data-ttu-id="ff1ff-133">Создание экземпляра клиента POP3 для IPv4 или IPv6</span><span class="sxs-lookup"><span data-stu-id="ff1ff-133">Create a POP3 Client instance for IPv4 or IPv6</span></span>

### <a name="prototype"></a><span data-ttu-id="ff1ff-134">Прототип</span><span class="sxs-lookup"><span data-stu-id="ff1ff-134">Prototype</span></span>

```C
UINT nxd_pop3_client_create(NX_POP3_CLIENT *client_ptr,
    UINT APOP_authentication, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool_ptr,
    NXD_ADDRESS *server_ip_address,
    ULONG server_port,
    CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="ff1ff-135">Описание</span><span class="sxs-lookup"><span data-stu-id="ff1ff-135">Description</span></span>

<span data-ttu-id="ff1ff-136">Эта служба создает экземпляр клиента POP3</span><span class="sxs-lookup"><span data-stu-id="ff1ff-136">This service creates an instance of the POP3 Client.</span></span> <span data-ttu-id="ff1ff-137">Она поддерживает IPv4- и IPv6-адреса сервера POP3.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-137">It supports both IPv4 and IPv6 POP3 server addresses.</span></span> <span data-ttu-id="ff1ff-138">Дополнительные сведения о процессе создания клиента POP3 см. выше в описании службы *nx_pop3_client_create*.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-138">See the previously described *nx_pop3_client_create* service for more details on POP3 Client create process.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ff1ff-139">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ff1ff-139">Input Parameters</span></span>

- <span data-ttu-id="ff1ff-140">**client_ptr** — указатель на создаваемый клиент.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-140">**client_ptr** Pointer to Client to create</span></span>
- <span data-ttu-id="ff1ff-141">**APOP_authentication** — включение проверки подлинности APOP.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-141">**APOP_authentication** Enable APOP authentication</span></span>
- <span data-ttu-id="ff1ff-142">**ip_ptr** — указатель на экземпляр IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-142">**ip_ptr** Pointer to IP instance</span></span>
- <span data-ttu-id="ff1ff-143">**packet_pool_ptr** — указатель на пул пакетов клиента.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-143">**packet_pool_ptr** Pointer to Client packet pool</span></span>
- <span data-ttu-id="ff1ff-144">**server_ip_address** — IPV4- или IPv6-адрес сервера POP3.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-144">**server_ip_address** POP3 server IPv6 or IPv4 address</span></span>
- <span data-ttu-id="ff1ff-145">**server_port** — порт сервера POP3.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-145">**server_port** POP3 server port</span></span>
- <span data-ttu-id="ff1ff-146">**client_name** — указатель на имя клиента.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-146">**client_name**  Pointer to Client name</span></span>
- <span data-ttu-id="ff1ff-147">**client_password** — указатель на пароль клиента.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-147">**client_password** Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="ff1ff-148">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ff1ff-148">Return Values</span></span>

- <span data-ttu-id="ff1ff-149">**NX_SUCCESS** (0x00) — клиент успешно создан.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-149">**NX_SUCCESS** (0x00) Client successfully created</span></span>
- <span data-ttu-id="ff1ff-150">**status** — состояние завершения вызовов служб NetX Duo и ThreadX.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-150">**status** Status completion of NetX Duo and ThreadX service calls</span></span>
- <span data-ttu-id="ff1ff-151">NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-151">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="ff1ff-152">NX_POP3_PARAM_ERROR (0xB1) — недопустимые входные данные, отличающиеся от указателя.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-152">NX_POP3_PARAM_ERROR (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff1ff-153">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ff1ff-153">Allowed From</span></span>

<span data-ttu-id="ff1ff-154">Код приложения</span><span class="sxs-lookup"><span data-stu-id="ff1ff-154">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ff1ff-155">Например, .</span><span class="sxs-lookup"><span data-stu-id="ff1ff-155">Example</span></span>

```C
/* Create the POP3 Client. */

/* Create username and password for our POP3 Client mail drop. */
#define LOCALHOST "recipient@expresslogic.com"
#define LOCALHOST_PASSWORD "pass"
#define POP3_SERVER_PORT 110

/* Create a NetX POP3 Client instance. Also note the details of IPv6 address validation
    and enabling IPv6 and ICMPv6 services on the IP task are not shown here. See the
    NetX Duo User Guide for more details on this process.
*/
NXD_ADDRESS server_ip_address;

/* Set client IP interface address. */
server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_address.nxd_ip_address.v6[1] = 0xf101;
server_ip_address.nxd_ip_address.v6[2] = 0;
server_ip_address.nxd_ip_address.v6[3] = 0x101;
status = nxd_pop3_client_create(&demo_client,
    NX_FALSE /* disable APOP authentication */,
    &client_ip, &client_packet_pool,
    &server_ip_address, POP3_SERVER_PORT,
    LOCALHOST, LOCALHOST_PASSWORD);

/* If the Client was successfully created, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_delete"></a><span data-ttu-id="ff1ff-156">nx_pop3_client_delete</span><span class="sxs-lookup"><span data-stu-id="ff1ff-156">nx_pop3_client_delete</span></span>

<span data-ttu-id="ff1ff-157">Удаление экземпляра клиента POP3</span><span class="sxs-lookup"><span data-stu-id="ff1ff-157">Delete a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ff1ff-158">Прототип</span><span class="sxs-lookup"><span data-stu-id="ff1ff-158">Prototype</span></span>

```C
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="ff1ff-159">Описание</span><span class="sxs-lookup"><span data-stu-id="ff1ff-159">Description</span></span>

<span data-ttu-id="ff1ff-160">Эта служба удаляет ранее созданный клиент POP3.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-160">This service deletes a previously created POP3 Client.</span></span> <span data-ttu-id="ff1ff-161">Учтите, что эта служба не удаляет пул пакетов для клиента POP3.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-161">Not that this service does not delete the POP3 Client packet pool.</span></span> <span data-ttu-id="ff1ff-162">Приложение устройства должно удалить этот ресурс отдельно, если пул пакетов больше не используется.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-162">The device application must delete this resource separately if it no longer has use for the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ff1ff-163">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ff1ff-163">Input Parameters</span></span>

- <span data-ttu-id="ff1ff-164">**client_ptr** — указатель на удаляемый клиент.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-164">**client_ptr** Pointer to Client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="ff1ff-165">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ff1ff-165">Return Values</span></span>

- <span data-ttu-id="ff1ff-166">**NX_SUCCESS** — (0x00) клиент успешно удален.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-166">**NX_SUCCESS** (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="ff1ff-167">NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-167">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff1ff-168">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ff1ff-168">Allowed From</span></span>

<span data-ttu-id="ff1ff-169">Код приложения</span><span class="sxs-lookup"><span data-stu-id="ff1ff-169">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ff1ff-170">Например, .</span><span class="sxs-lookup"><span data-stu-id="ff1ff-170">Example</span></span>

```C
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a><span data-ttu-id="ff1ff-171">nx_pop3_client_mail_item_delete</span><span class="sxs-lookup"><span data-stu-id="ff1ff-171">nx_pop3_client_mail_item_delete</span></span>

<span data-ttu-id="ff1ff-172">Удаление указанного элемента почты из почтового ящика клиента</span><span class="sxs-lookup"><span data-stu-id="ff1ff-172">Delete a specified mail item from the Client maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="ff1ff-173">Прототип</span><span class="sxs-lookup"><span data-stu-id="ff1ff-173">Prototype</span></span>

```C
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
    UINT mail_index);
```

### <a name="description"></a><span data-ttu-id="ff1ff-174">Описание</span><span class="sxs-lookup"><span data-stu-id="ff1ff-174">Description</span></span>

<span data-ttu-id="ff1ff-175">Эта служба удаляет указанный элемент почты из почтового ящика клиента.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-175">This service deletes the specified mail item from the Client maildrop.</span></span> <span data-ttu-id="ff1ff-176">Она предназначена для удаления уже скачанных элементов почты, хотя некоторые серверы POP3 могут автоматически удалять элементы почты после запрашивания клиентом.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-176">It is intended for after downloading the mail item, although some POP3 servers may automatically delete mail items after being requested by the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ff1ff-177">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ff1ff-177">Input Parameters</span></span>

- <span data-ttu-id="ff1ff-178">**client_ptr** — указатель на экземпляр клиента.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-178">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="ff1ff-179">**mail_index** — порядковый индекс в пределах почтового ящика клиента.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-179">**mail_index** Index into Client maildrop</span></span>

### <a name="return-values"></a><span data-ttu-id="ff1ff-180">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ff1ff-180">Return Values</span></span>

- <span data-ttu-id="ff1ff-181">**NX_SUCCESS** (0x00) — запрос на удаление успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-181">**NX_SUCCESS** (0x00) Delete request successful</span></span>
- <span data-ttu-id="ff1ff-182">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) — недопустимый индекс элемента почты.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-182">**NX_POP3_INVALID_MAIL_ITEM**(0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="ff1ff-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) — слишком короткие полезные данные в пакете для запроса POP3.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**(0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="ff1ff-184">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) — ответ сервера содержит состояние ошибки.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-184">**NX_POP3_SERVER_ERROR_STATUS**(0xB4) Server replies with error status</span></span>
- <span data-ttu-id="ff1ff-185">NX_POP3_CLIENT_INVALID_INDEX (0xB8) — недопустимый входной параметр индекса.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-185">NX_POP3_CLIENT_INVALID_INDEX(0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="ff1ff-186">NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-186">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff1ff-187">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ff1ff-187">Allowed From</span></span>

<span data-ttu-id="ff1ff-188">Код приложения</span><span class="sxs-lookup"><span data-stu-id="ff1ff-188">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ff1ff-189">Например, .</span><span class="sxs-lookup"><span data-stu-id="ff1ff-189">Example</span></span>

```C
ULONG item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status =
    NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a><span data-ttu-id="ff1ff-190">nx_pop3_client_mail_item_get</span><span class="sxs-lookup"><span data-stu-id="ff1ff-190">nx_pop3_client_mail_item_get</span></span>

<span data-ttu-id="ff1ff-191">Получение указанного элемента почты</span><span class="sxs-lookup"><span data-stu-id="ff1ff-191">Retrieve a specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="ff1ff-192">Прототип</span><span class="sxs-lookup"><span data-stu-id="ff1ff-192">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *item_size);
```

### <a name="description"></a><span data-ttu-id="ff1ff-193">Описание</span><span class="sxs-lookup"><span data-stu-id="ff1ff-193">Description</span></span>

<span data-ttu-id="ff1ff-194">Эта служба создает запрос RETR для получения из почтового ящика клиента элемента почты с индексом mail_item.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-194">This service makes a RETR request to retrieve a mail item from the Client maildrop specified by the index mail_item.</span></span> <span data-ttu-id="ff1ff-195">После выполнения запроса RETR и получения положительного ответа от сервера клиент может начать скачивание почтового сообщения с помощью службы *nx_pop3_client_mail_item_message_get*.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-195">After making a RETR request, and receiving a positive response from the Server, the Client can start downloading the mail message using the *nx_pop3_client_mail_item_message_get* service.</span></span> <span data-ttu-id="ff1ff-196">Обратите внимание, что эта служба также предоставляет размер элемента почты, извлеченного из ответа сервера.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-196">Note that the service also supplies the size of the requested mail item extracted from the Server reply.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ff1ff-197">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ff1ff-197">Input Parameters</span></span>

- <span data-ttu-id="ff1ff-198">**client_ptr** — указатель на экземпляр клиента.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-198">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="ff1ff-199">**mail_item** — порядковый индекс в пределах почтового ящика клиента.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-199">**mail_item** Index into Client maildrop</span></span>
- <span data-ttu-id="ff1ff-200">**item_size** — указатель на размер почтового сообщения.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-200">**item_size** Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="ff1ff-201">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ff1ff-201">Return Values</span></span>

- <span data-ttu-id="ff1ff-202">**NX_SUCCESS** (0x00) — элемент почты успешно получен.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-202">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="ff1ff-203">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) — недопустимый индекс элемента почты.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-203">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="ff1ff-204">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) — слишком короткие полезные данные в пакете для запроса POP3.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-204">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="ff1ff-205">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) — ответ сервера содержит состояние ошибки.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-205">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="ff1ff-206">NX_POP3_CLIENT_INVALID_INDEX (0xB8) — недопустимый входной параметр индекса.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-206">NX_POP3_CLIENT_INVALID_INDEX (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="ff1ff-207">NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-207">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff1ff-208">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ff1ff-208">Allowed From</span></span>

<span data-ttu-id="ff1ff-209">Код приложения</span><span class="sxs-lookup"><span data-stu-id="ff1ff-209">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ff1ff-210">Например, .</span><span class="sxs-lookup"><span data-stu-id="ff1ff-210">Example</span></span>

```C
ULONG item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a><span data-ttu-id="ff1ff-211">nx_pop3_client_mail_items_get</span><span class="sxs-lookup"><span data-stu-id="ff1ff-211">nx_pop3_client_mail_items_get</span></span>

<span data-ttu-id="ff1ff-212">Получение количества элементов в почтовом ящике</span><span class="sxs-lookup"><span data-stu-id="ff1ff-212">Retrieve the number of mail items in maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="ff1ff-213">Прототип</span><span class="sxs-lookup"><span data-stu-id="ff1ff-213">Prototype</span></span>

```C
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
    UINT *number_mail_items,
    ULONG *maildrop_total_size);
```

### <a name="description"></a><span data-ttu-id="ff1ff-214">Описание</span><span class="sxs-lookup"><span data-stu-id="ff1ff-214">Description</span></span>

<span data-ttu-id="ff1ff-215">Эта служба выполняет запрос STAT для получения количества элементов почты и общего объема данных почтовых сообщений в почтовом ящике клиента.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-215">This service makes a STAT request to retrieve the number of mail items and total size of mail message data from the Client maildrop.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ff1ff-216">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ff1ff-216">Input Parameters</span></span>

- <span data-ttu-id="ff1ff-217">**client_ptr** — указатель на экземпляр клиента.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-217">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="ff1ff-218">**number_mail_item** — количество писем в почтовом ящике клиента.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-218">**number_mail_item** Number of mail in Client maildrop</span></span>
- <span data-ttu-id="ff1ff-219">**maildrop_total_size** — указатель на общий размер всех почтовых сообщений.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-219">**maildrop_total_size** Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="ff1ff-220">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ff1ff-220">Return Values</span></span>

- <span data-ttu-id="ff1ff-221">**NX_SUCCESS** (0x00) — элемент почты успешно получен.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-221">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="ff1ff-222">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) — недопустимый индекс элемента почты.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-222">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="ff1ff-223">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) — слишком короткие полезные данные в пакете для запроса POP3.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-223">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="ff1ff-224">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) — ответ сервера содержит состояние ошибки.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-224">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="ff1ff-225">NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-225">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff1ff-226">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ff1ff-226">Allowed From</span></span>

<span data-ttu-id="ff1ff-227">Код приложения</span><span class="sxs-lookup"><span data-stu-id="ff1ff-227">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ff1ff-228">Например, .</span><span class="sxs-lookup"><span data-stu-id="ff1ff-228">Example</span></span>

```C
UINT number_mail_items;

ULONG maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
    &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a><span data-ttu-id="ff1ff-229">nx_pop3_client_mail_item_message_get</span><span class="sxs-lookup"><span data-stu-id="ff1ff-229">nx_pop3_client_mail_item_message_get</span></span>

<span data-ttu-id="ff1ff-230">Получение сообщения из указанного элемента почты</span><span class="sxs-lookup"><span data-stu-id="ff1ff-230">Retrieve the specified mail item message</span></span>

### <a name="prototype"></a><span data-ttu-id="ff1ff-231">Прототип</span><span class="sxs-lookup"><span data-stu-id="ff1ff-231">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_message_get(
    NX_POP3_CLIENT *client_ptr,
    NX_PACKET **recv_packet_ptr,
    ULONG *bytes_retrieved,
    UINT *final_packet);
```

### <a name="description"></a><span data-ttu-id="ff1ff-232">Описание</span><span class="sxs-lookup"><span data-stu-id="ff1ff-232">Description</span></span>

<span data-ttu-id="ff1ff-233">Эта служба извлекает сообщение из элемента почты, размер почтового сообщения и сведения о том, является ли пакет в почтовом сообщении последним.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-233">This service retrieves the mail item message, size of the mail message, and if it is the last packet in the mail message.</span></span> <span data-ttu-id="ff1ff-234">Если final_packet имеет значение NX_TRUE, пакет, на который ссылается recv_packet_ptr, является последним пакетом сообщения в элементе почты.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-234">If final_packet is NX_TRUE the packet pointed to by recv_packet_ptr is the final packet in the mail item message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ff1ff-235">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ff1ff-235">Input Parameters</span></span>

- <span data-ttu-id="ff1ff-236">**client_ptr** — указатель на экземпляр клиента.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-236">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="ff1ff-237">**recv_packet_ptr** — полученный пакет данных сообщения.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-237">**recv_packet_ptr** Received packet of message data</span></span>
- <span data-ttu-id="ff1ff-238">**number_mail_item** — количество писем в почтовом ящике клиента.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-238">**number_mail_item** Number of mail in Client maildrop</span></span>
- <span data-ttu-id="ff1ff-239">**maildrop_total_size** — указатель на общий размер всех почтовых сообщений.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-239">**maildrop_total_size** Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="ff1ff-240">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ff1ff-240">Return Values</span></span>

- <span data-ttu-id="ff1ff-241">**NX_SUCCESS** (0x00) — элемент почты успешно получен.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-241">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="ff1ff-242">**NX_POP3_CLIENT_INVALID_STATE** (0xB7) — слишком короткие полезные данные в пакете для запроса POP3.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-242">**NX_POP3_CLIENT_INVALID_STATE** (0xB7) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="ff1ff-243">NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-243">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff1ff-244">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ff1ff-244">Allowed From</span></span>

<span data-ttu-id="ff1ff-245">Код приложения</span><span class="sxs-lookup"><span data-stu-id="ff1ff-245">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ff1ff-246">Например, .</span><span class="sxs-lookup"><span data-stu-id="ff1ff-246">Example</span></span>

```C
NX_PACKET *recv_packet_ptr;

ULONG bytes_retrieved;

UINT final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
    bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a><span data-ttu-id="ff1ff-247">nx_pop3_client_mail_item_size_get</span><span class="sxs-lookup"><span data-stu-id="ff1ff-247">nx_pop3_client_mail_item_size_get</span></span>

<span data-ttu-id="ff1ff-248">Получение размера указанного элемента почты</span><span class="sxs-lookup"><span data-stu-id="ff1ff-248">Retrieve the size of the specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="ff1ff-249">Прототип</span><span class="sxs-lookup"><span data-stu-id="ff1ff-249">Prototype</span></span>

```C
UINT nx_pop3_client_mail_item_size_get(
    NX_POP3_CLIENT *client_ptr,
    UINT mail_item, ULONG *size);
```

### <a name="description"></a><span data-ttu-id="ff1ff-250">Описание</span><span class="sxs-lookup"><span data-stu-id="ff1ff-250">Description</span></span>

<span data-ttu-id="ff1ff-251">Эта служба создает запрос LIST для получения размера указанного элемента почты.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-251">This service makes a LIST request to obtain the size of the specified mail item.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ff1ff-252">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ff1ff-252">Input Parameters</span></span>

- <span data-ttu-id="ff1ff-253">**client_ptr** — указатель на экземпляр клиента.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-253">**client_ptr** Pointer to Client instance</span></span>
- <span data-ttu-id="ff1ff-254">**mail_item** — порядковый индекс в пределах почтового ящика клиента.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-254">**mail_item** Index into Client maildrop</span></span>
- <span data-ttu-id="ff1ff-255">**size** — указатель на размер почтового сообщения.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-255">**size** Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="ff1ff-256">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ff1ff-256">Return Values</span></span>

- <span data-ttu-id="ff1ff-257">**NX_SUCCESS** (0x00) — элемент почты успешно получен.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-257">**NX_SUCCESS** (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="ff1ff-258">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) — недопустимый индекс элемента почты.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-258">**NX_POP3_INVALID_MAIL_ITEM** (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="ff1ff-259">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) — слишком короткие полезные данные в пакете для запроса POP3.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-259">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD** (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="ff1ff-260">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) — ответ сервера содержит состояние ошибки.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-260">**NX_POP3_SERVER_ERROR_STATUS** (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="ff1ff-261">NX_POP3_CLIENT_INVALID_INDEX (0xB8) — недопустимый входной параметр индекса.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-261">NX_POP3_CLIENT_INVALID_INDEX (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="ff1ff-262">NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="ff1ff-262">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ff1ff-263">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ff1ff-263">Allowed From</span></span>

<span data-ttu-id="ff1ff-264">Код приложения</span><span class="sxs-lookup"><span data-stu-id="ff1ff-264">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ff1ff-265">Пример</span><span class="sxs-lookup"><span data-stu-id="ff1ff-265">Example</span></span>

```C
ULONG size;

UINT mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */

status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
