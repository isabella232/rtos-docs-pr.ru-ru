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
# <a name="chapter-3---description-of-azure-rtos-netx-pop3-client-services"></a><span data-ttu-id="ad58f-103">Глава 3. Описание служб клиента NetX POP3 для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="ad58f-103">Chapter 3 - Description of Azure RTOS NetX POP3 Client services</span></span>

<span data-ttu-id="ad58f-104">Эта глава содержит описание всех служб клиента NetX POP3 для ОСРВ Azure, перечисленных ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="ad58f-104">This chapter contains a description of all Azure RTOS NetX POP3 Client services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="ad58f-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, используемым для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="ad58f-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="ad58f-106">nx_pop3_client_create: *создание экземпляра клиента POP3*.</span><span class="sxs-lookup"><span data-stu-id="ad58f-106">nx_pop3_client_create: *Create a POP3 Client Instance*</span></span>
- <span data-ttu-id="ad58f-107">nx_pop3_client_delete: *удаление экземпляра клиента POP3*.</span><span class="sxs-lookup"><span data-stu-id="ad58f-107">nx_pop3_client_delete: *Delete a POP3 Client instance*</span></span>
- <span data-ttu-id="ad58f-108">nx_pop3_client_ mail_item_get: *удаление элемента почты клиента из почтового ящика на сервере*.</span><span class="sxs-lookup"><span data-stu-id="ad58f-108">nx_pop3_client_ mail_item_get: *Delete a Client mail item from Server maildrop*</span></span>
- <span data-ttu-id="ad58f-109">nx_pop3_client_mail_item_get: *получение размера указанного почтового сообщения*.</span><span class="sxs-lookup"><span data-stu-id="ad58f-109">nx_pop3_client_mail_item_get: *Retrieve a specific mail message size*</span></span>
- <span data-ttu-id="ad58f-110">nx_pop3_client_mail_items_get: *получение количества элементов в почтовом ящике*.</span><span class="sxs-lookup"><span data-stu-id="ad58f-110">nx_pop3_client_mail_items_get: *Obtain the number of mail items in maildrop*</span></span>
- <span data-ttu-id="ad58f-111">nx_pop3_client_mail_item_message _get: *скачивание указанного почтового сообщения*.</span><span class="sxs-lookup"><span data-stu-id="ad58f-111">nx_pop3_client_mail_item_message _get: *Download a specific mail message*</span></span>
- <span data-ttu-id="ad58f-112">nx_pop3_client_mail_item_size_get: *получение размера указанного элемента почты*.</span><span class="sxs-lookup"><span data-stu-id="ad58f-112">nx_pop3_client_mail_item_size_get: *Obtain the size of a specific mail item*</span></span>

## <a name="nx_pop3_client_create"></a><span data-ttu-id="ad58f-113">nx_pop3_client_create</span><span class="sxs-lookup"><span data-stu-id="ad58f-113">nx_pop3_client_create</span></span>

<span data-ttu-id="ad58f-114">Создание экземпляра клиента POP3</span><span class="sxs-lookup"><span data-stu-id="ad58f-114">Create a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ad58f-115">Прототип</span><span class="sxs-lookup"><span data-stu-id="ad58f-115">Prototype</span></span>

```c
UINT nx_pop3_client_create(NX_POP3_CLIENT *client_ptr,
                        UINT APOP_authentication, NX_IP *ip_ptr,
                        NX_PACKET_POOL *packet_pool_ptr,
                        ULONG server_ip_address,
                        ULONG server_port,
                        CHAR *client_name, CHAR *client_password);
```

### <a name="description"></a><span data-ttu-id="ad58f-116">Описание</span><span class="sxs-lookup"><span data-stu-id="ad58f-116">Description</span></span>

<span data-ttu-id="ad58f-117">Эта служба создает экземпляр клиента POP3 и настраивает для него конфигурацию, используя входные параметры.</span><span class="sxs-lookup"><span data-stu-id="ad58f-117">This service creates an instance of the POP3 Client and sets up its configuration with the input parameters.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ad58f-118">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ad58f-118">Input Parameters</span></span>

- <span data-ttu-id="ad58f-119">**client_ptr**: указатель на создаваемый клиент.</span><span class="sxs-lookup"><span data-stu-id="ad58f-119">**client_ptr**: Pointer to Client to create</span></span>
- <span data-ttu-id="ad58f-120">**APOP_authentication**: включение проверки подлинности APOP.</span><span class="sxs-lookup"><span data-stu-id="ad58f-120">**APOP_authentication**: Enable APOP authentication</span></span>
- <span data-ttu-id="ad58f-121">**ip_ptr**: указатель на экземпляр IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="ad58f-121">**ip_ptr**: Pointer to IP instance</span></span>
- <span data-ttu-id="ad58f-122">**packet_pool_ptr**: указатель на пул пакетов клиента.</span><span class="sxs-lookup"><span data-stu-id="ad58f-122">**packet_pool_ptr**: Pointer to Client packet pool</span></span>
- <span data-ttu-id="ad58f-123">**server_ip_address**: адрес сервера POP3.</span><span class="sxs-lookup"><span data-stu-id="ad58f-123">**server_ip_address**: POP3 server address</span></span>
- <span data-ttu-id="ad58f-124">**server_port**: порт сервера POP3.</span><span class="sxs-lookup"><span data-stu-id="ad58f-124">**server_port**: POP3 server port</span></span>
- <span data-ttu-id="ad58f-125">**client_name**: указатель на имя клиента.</span><span class="sxs-lookup"><span data-stu-id="ad58f-125">**client_name**: Pointer to Client name</span></span>
- <span data-ttu-id="ad58f-126">**client_password**: указатель на пароль клиента.</span><span class="sxs-lookup"><span data-stu-id="ad58f-126">**client_password**: Pointer to Client password</span></span>

### <a name="return-values"></a><span data-ttu-id="ad58f-127">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ad58f-127">Return Values</span></span>

- <span data-ttu-id="ad58f-128">**NX_SUCCESS**: (0x00) клиент успешно создан.</span><span class="sxs-lookup"><span data-stu-id="ad58f-128">**NX_SUCCESS**: (0x00) Client successfully created</span></span>
- <span data-ttu-id="ad58f-129">**status**: состояние завершения вызовов служб NetX и ThreadX.</span><span class="sxs-lookup"><span data-stu-id="ad58f-129">**status**: Status completion of NetX and ThreadX service calls</span></span>
- <span data-ttu-id="ad58f-130">NX_PTR_ERROR: (0x07) недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="ad58f-130">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="ad58f-131">NX_POP3_PARAM_ERROR: (0xB1) недопустимые входные данные, кроме указателей.</span><span class="sxs-lookup"><span data-stu-id="ad58f-131">NX_POP3_PARAM_ERROR: (0xB1) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ad58f-132">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ad58f-132">Allowed From</span></span>

<span data-ttu-id="ad58f-133">Код приложения</span><span class="sxs-lookup"><span data-stu-id="ad58f-133">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ad58f-134">Например, .</span><span class="sxs-lookup"><span data-stu-id="ad58f-134">Example</span></span>

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

## <a name="nx_pop3_client_delete"></a><span data-ttu-id="ad58f-135">nx_pop3_client_delete</span><span class="sxs-lookup"><span data-stu-id="ad58f-135">nx_pop3_client_delete</span></span>

<span data-ttu-id="ad58f-136">Удаление экземпляра клиента POP3</span><span class="sxs-lookup"><span data-stu-id="ad58f-136">Delete a POP3 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ad58f-137">Прототип</span><span class="sxs-lookup"><span data-stu-id="ad58f-137">Prototype</span></span>

```c
UINT nx_pop3_client_delete(NX_POP3_CLIENT *client_ptr)
```

### <a name="description"></a><span data-ttu-id="ad58f-138">Описание</span><span class="sxs-lookup"><span data-stu-id="ad58f-138">Description</span></span>

<span data-ttu-id="ad58f-139">Эта служба удаляет ранее созданный клиент POP3.</span><span class="sxs-lookup"><span data-stu-id="ad58f-139">This service deletes a previously created POP3 Client.</span></span> <span data-ttu-id="ad58f-140">Учтите, что эта служба не удаляет пул пакетов для клиента POP3.</span><span class="sxs-lookup"><span data-stu-id="ad58f-140">Not that this service does not delete the POP3 Client packet pool.</span></span> <span data-ttu-id="ad58f-141">Приложение устройства должно удалить этот ресурс отдельно, если пул пакетов больше не используется.</span><span class="sxs-lookup"><span data-stu-id="ad58f-141">The device application must delete this resource separately if it no longer has use for the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ad58f-142">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ad58f-142">Input Parameters</span></span>

- <span data-ttu-id="ad58f-143">**client_ptr**: указатель на удаляемый клиент.</span><span class="sxs-lookup"><span data-stu-id="ad58f-143">**client_ptr**: Pointer to Client to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="ad58f-144">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ad58f-144">Return Values</span></span>

- <span data-ttu-id="ad58f-145">**NX_SUCCESS**: (0x00) клиент успешно удален</span><span class="sxs-lookup"><span data-stu-id="ad58f-145">**NX_SUCCESS**: (0x00) Client successfully deleted</span></span>
- <span data-ttu-id="ad58f-146">NX_PTR_ERROR: (0x07) недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="ad58f-146">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ad58f-147">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ad58f-147">Allowed From</span></span>

<span data-ttu-id="ad58f-148">Код приложения</span><span class="sxs-lookup"><span data-stu-id="ad58f-148">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ad58f-149">Например, .</span><span class="sxs-lookup"><span data-stu-id="ad58f-149">Example</span></span>

```c
/* Delete the POP3 Client. */
status = nx_pop3_client_delete (&demo_client);

/* If the Client was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_delete"></a><span data-ttu-id="ad58f-150">nx_pop3_client_mail_item_delete</span><span class="sxs-lookup"><span data-stu-id="ad58f-150">nx_pop3_client_mail_item_delete</span></span>

<span data-ttu-id="ad58f-151">Удаление указанного элемента почты из почтового ящика клиента</span><span class="sxs-lookup"><span data-stu-id="ad58f-151">Delete a specified mail item from the Client maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="ad58f-152">Прототип</span><span class="sxs-lookup"><span data-stu-id="ad58f-152">Prototype</span></span>

```c
UINT nx_pop3_client_mail_items_delete(NX_POP3_CLIENT *client_ptr,
                                    UINT mail_index)
```

### <a name="description"></a><span data-ttu-id="ad58f-153">Описание</span><span class="sxs-lookup"><span data-stu-id="ad58f-153">Description</span></span>

<span data-ttu-id="ad58f-154">Эта служба удаляет указанный элемент почты из почтового ящика клиента.</span><span class="sxs-lookup"><span data-stu-id="ad58f-154">This service deletes the specified mail item from the Client maildrop.</span></span> <span data-ttu-id="ad58f-155">Она предназначена для удаления уже скачанных элементов почты, хотя некоторые серверы POP3 могут автоматически удалять элементы почты после запрашивания клиентом.</span><span class="sxs-lookup"><span data-stu-id="ad58f-155">It is intended for after downloading the mail item, although some POP3 servers may automatically delete mail items after being requested by the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ad58f-156">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ad58f-156">Input Parameters</span></span>

- <span data-ttu-id="ad58f-157">**client_ptr**: указатель на экземпляр клиента.</span><span class="sxs-lookup"><span data-stu-id="ad58f-157">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="ad58f-158">**mail_index**: порядковый индекс в пределах почтового ящика клиента.</span><span class="sxs-lookup"><span data-stu-id="ad58f-158">**mail_index**: Index into Client maildrop</span></span>

### <a name="return-values"></a><span data-ttu-id="ad58f-159">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ad58f-159">Return Values</span></span>

- <span data-ttu-id="ad58f-160">**NX_SUCCESS**: (0x00) запрос на удаление успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="ad58f-160">**NX_SUCCESS**: (0x00) Delete request successful</span></span>
- <span data-ttu-id="ad58f-161">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) недопустимый индекс элемента почты.</span><span class="sxs-lookup"><span data-stu-id="ad58f-161">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="ad58f-162">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) слишком короткие полезные данные в пакете для запроса POP3.</span><span class="sxs-lookup"><span data-stu-id="ad58f-162">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="ad58f-163">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) ответ сервера содержит состояние ошибки.</span><span class="sxs-lookup"><span data-stu-id="ad58f-163">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="ad58f-164">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) недопустимый входной параметр индекса.</span><span class="sxs-lookup"><span data-stu-id="ad58f-164">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="ad58f-165">NX_PTR_ERROR: (0x07) недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="ad58f-165">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ad58f-166">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ad58f-166">Allowed From</span></span>

<span data-ttu-id="ad58f-167">Код приложения</span><span class="sxs-lookup"><span data-stu-id="ad58f-167">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ad58f-168">Например, .</span><span class="sxs-lookup"><span data-stu-id="ad58f-168">Example</span></span>

```c
ULONG     item_index;

/* Delete the POP3 Client mail item. */
status = nx_pop3_client_mail_item_delete(&demo_client, item_index);

/* If the server accepts the DELE request (and deletes the mail item), status = 
   NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_get"></a><span data-ttu-id="ad58f-169">nx_pop3_client_mail_item_get</span><span class="sxs-lookup"><span data-stu-id="ad58f-169">nx_pop3_client_mail_item_get</span></span>

<span data-ttu-id="ad58f-170">Получение указанного элемента почты</span><span class="sxs-lookup"><span data-stu-id="ad58f-170">Retrieve a specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="ad58f-171">Прототип</span><span class="sxs-lookup"><span data-stu-id="ad58f-171">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_get(NX_POP3_CLIENT *client_ptr,
                                UINT mail_item, ULONG *item_size)
```

### <a name="description"></a><span data-ttu-id="ad58f-172">Описание</span><span class="sxs-lookup"><span data-stu-id="ad58f-172">Description</span></span>

<span data-ttu-id="ad58f-173">Эта служба создает запрос RETR для получения из почтового ящика клиента элемента почты с индексом mail_item.</span><span class="sxs-lookup"><span data-stu-id="ad58f-173">This service makes a RETR request to retrieve a mail item from the Client maildrop specified by the index mail_item.</span></span> <span data-ttu-id="ad58f-174">После выполнения запроса RETR и получения положительного ответа от сервера клиент может начать скачивание почтового сообщения с помощью службы *nx_pop3_client_mail_item_message_get*.</span><span class="sxs-lookup"><span data-stu-id="ad58f-174">After making a RETR request, and receiving a positive response from the Server, the Client can start downloading the mail message using the *nx_pop3_client_mail_item_message_get* service.</span></span> <span data-ttu-id="ad58f-175">Обратите внимание, что эта служба также предоставляет размер элемента почты, извлеченного из ответа сервера.</span><span class="sxs-lookup"><span data-stu-id="ad58f-175">Note that the service also supplies the size of the requested mail item extracted from the Server reply.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ad58f-176">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ad58f-176">Input Parameters</span></span>

- <span data-ttu-id="ad58f-177">**client_ptr**: указатель на экземпляр клиента.</span><span class="sxs-lookup"><span data-stu-id="ad58f-177">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="ad58f-178">**mail_item**: порядковый индекс в пределах почтового ящика клиента.</span><span class="sxs-lookup"><span data-stu-id="ad58f-178">**mail_item**: Index into Client maildrop</span></span>
- <span data-ttu-id="ad58f-179">**item_size**: указатель на размер почтового сообщения.</span><span class="sxs-lookup"><span data-stu-id="ad58f-179">**item_size**: Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="ad58f-180">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ad58f-180">Return Values</span></span>

- <span data-ttu-id="ad58f-181">**NX_SUCCESS**: (0x00) элемент почты успешно получен.</span><span class="sxs-lookup"><span data-stu-id="ad58f-181">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="ad58f-182">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) недопустимый индекс элемента почты.</span><span class="sxs-lookup"><span data-stu-id="ad58f-182">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="ad58f-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) слишком короткие полезные данные в пакете для запроса POP3.</span><span class="sxs-lookup"><span data-stu-id="ad58f-183">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="ad58f-184">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) ответ сервера содержит состояние ошибки.</span><span class="sxs-lookup"><span data-stu-id="ad58f-184">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="ad58f-185">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) недопустимый входной параметр индекса.</span><span class="sxs-lookup"><span data-stu-id="ad58f-185">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="ad58f-186">NX_PTR_ERROR: (0x07) недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="ad58f-186">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ad58f-187">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ad58f-187">Allowed From</span></span>

<span data-ttu-id="ad58f-188">Код приложения</span><span class="sxs-lookup"><span data-stu-id="ad58f-188">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ad58f-189">Например, .</span><span class="sxs-lookup"><span data-stu-id="ad58f-189">Example</span></span>

```c
ULONG     item_size;

/* Retrieve the POP3 Client mail item. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &item_size);

/* If the mail item was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_items_get"></a><span data-ttu-id="ad58f-190">nx_pop3_client_mail_items_get</span><span class="sxs-lookup"><span data-stu-id="ad58f-190">nx_pop3_client_mail_items_get</span></span>

<span data-ttu-id="ad58f-191">Получение количества элементов в почтовом ящике</span><span class="sxs-lookup"><span data-stu-id="ad58f-191">Retrieve the number of mail items in maildrop</span></span>

### <a name="prototype"></a><span data-ttu-id="ad58f-192">Прототип</span><span class="sxs-lookup"><span data-stu-id="ad58f-192">Prototype</span></span>

```c
UINT nx_pop3_client_mail_items_get(NX_POP3_CLIENT *client_ptr,
                                UINT *number_mail_items,
                                ULONG *maildrop_total_size)
```

### <a name="description"></a><span data-ttu-id="ad58f-193">Описание</span><span class="sxs-lookup"><span data-stu-id="ad58f-193">Description</span></span>

<span data-ttu-id="ad58f-194">Эта служба выполняет запрос STAT для получения количества элементов почты и общего объема данных почтовых сообщений в почтовом ящике клиента.</span><span class="sxs-lookup"><span data-stu-id="ad58f-194">This service makes a STAT request to retrieve the number of mail items and total size of mail message data from the Client maildrop.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ad58f-195">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ad58f-195">Input Parameters</span></span>

- <span data-ttu-id="ad58f-196">**client_ptr**: указатель на экземпляр клиента.</span><span class="sxs-lookup"><span data-stu-id="ad58f-196">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="ad58f-197">**number_mail_item**: количество писем в почтовом ящике клиента.</span><span class="sxs-lookup"><span data-stu-id="ad58f-197">**number_mail_item**: Number of mail in Client maildrop</span></span>
- <span data-ttu-id="ad58f-198">**maildrop_total_size**: указатель на общий размер всех почтовых сообщений.</span><span class="sxs-lookup"><span data-stu-id="ad58f-198">**maildrop_total_size**: Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="ad58f-199">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ad58f-199">Return Values</span></span>

- <span data-ttu-id="ad58f-200">**NX_SUCCESS**: (0x00) элемент почты успешно получен.</span><span class="sxs-lookup"><span data-stu-id="ad58f-200">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="ad58f-201">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) недопустимый индекс элемента почты.</span><span class="sxs-lookup"><span data-stu-id="ad58f-201">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="ad58f-202">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) слишком короткие полезные данные в пакете для запроса POP3.</span><span class="sxs-lookup"><span data-stu-id="ad58f-202">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="ad58f-203">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) ответ сервера содержит состояние ошибки.</span><span class="sxs-lookup"><span data-stu-id="ad58f-203">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span> 
- <span data-ttu-id="ad58f-204">NX_PTR_ERROR: (0x07) недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="ad58f-204">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ad58f-205">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ad58f-205">Allowed From</span></span>

<span data-ttu-id="ad58f-206">Код приложения</span><span class="sxs-lookup"><span data-stu-id="ad58f-206">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ad58f-207">Например, .</span><span class="sxs-lookup"><span data-stu-id="ad58f-207">Example</span></span>

```c
UINT      number_mail_items;
ULONG     maildrop_total_size;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_get (&demo_client, 1, &number_mail_items,
                                        &maildrop_total_size);

/* If the maildrop data was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_message_get"></a><span data-ttu-id="ad58f-208">nx_pop3_client_mail_item_message_get</span><span class="sxs-lookup"><span data-stu-id="ad58f-208">nx_pop3_client_mail_item_message_get</span></span>

<span data-ttu-id="ad58f-209">Получение сообщения из указанного элемента почты</span><span class="sxs-lookup"><span data-stu-id="ad58f-209">Retrieve the specified mail item message</span></span>

### <a name="prototype"></a><span data-ttu-id="ad58f-210">Прототип</span><span class="sxs-lookup"><span data-stu-id="ad58f-210">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_message_get(
                NX_POP3_CLIENT *client_ptr,
                NX_PACKET **recv_packet_ptr,
                ULONG *bytes_retrieved,
                UINT *final_packet)
```

### <a name="description"></a><span data-ttu-id="ad58f-211">Описание</span><span class="sxs-lookup"><span data-stu-id="ad58f-211">Description</span></span>

<span data-ttu-id="ad58f-212">Эта служба извлекает сообщение из элемента почты, размер почтового сообщения и сведения о том, является ли пакет в почтовом сообщении последним.</span><span class="sxs-lookup"><span data-stu-id="ad58f-212">This service retrieves the mail item message, size of the mail message, and if it is the last packet in the mail message.</span></span> <span data-ttu-id="ad58f-213">Если параметр `final_packet` имеет значение NX_TRUE, то предоставленный в `recv_packet_ptr` пакет является последним в сообщении этого почтового элемента.</span><span class="sxs-lookup"><span data-stu-id="ad58f-213">If `final_packet` is NX_TRUE the packet pointed to by `recv_packet_ptr` is the final packet in the mail item message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ad58f-214">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ad58f-214">Input Parameters</span></span>

- <span data-ttu-id="ad58f-215">**client_ptr**: указатель на экземпляр клиента.</span><span class="sxs-lookup"><span data-stu-id="ad58f-215">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="ad58f-216">**recv_packet_ptr**: полученный пакет данных из сообщения.</span><span class="sxs-lookup"><span data-stu-id="ad58f-216">**recv_packet_ptr**: Received packet of message data</span></span>
- <span data-ttu-id="ad58f-217">**number_mail_item**: количество писем в почтовом ящике клиента.</span><span class="sxs-lookup"><span data-stu-id="ad58f-217">**number_mail_item**: Number of mail in Client maildrop</span></span>
- <span data-ttu-id="ad58f-218">**maildrop_total_size**: указатель на общий размер всех почтовых сообщений.</span><span class="sxs-lookup"><span data-stu-id="ad58f-218">**maildrop_total_size**: Pointer to size of all mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="ad58f-219">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ad58f-219">Return Values</span></span>

- <span data-ttu-id="ad58f-220">**NX_SUCCESS**: (0x00) элемент почты успешно получен.</span><span class="sxs-lookup"><span data-stu-id="ad58f-220">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="ad58f-221">**NX_POP3_CLIENT_INVALID_STATE**: (0xB7) слишком короткие полезные данные в пакете для запроса POP3.</span><span class="sxs-lookup"><span data-stu-id="ad58f-221">**NX_POP3_CLIENT_INVALID_STATE**: (0xB7) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="ad58f-222">NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="ad58f-222">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ad58f-223">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ad58f-223">Allowed From</span></span>

<span data-ttu-id="ad58f-224">Код приложения</span><span class="sxs-lookup"><span data-stu-id="ad58f-224">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ad58f-225">Например, .</span><span class="sxs-lookup"><span data-stu-id="ad58f-225">Example</span></span>

```c
NX_PACKET     *recv_packet_ptr;
ULONG         bytes_retrieved;
UINT          final_packet;

/* Retrieve the size and number of items in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_message_get (&demo_client, &recv_packet_ptr,
                                                bytes_retrieved, final_packet);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```

## <a name="nx_pop3_client_mail_item_size_get"></a><span data-ttu-id="ad58f-226">nx_pop3_client_mail_item_size_get</span><span class="sxs-lookup"><span data-stu-id="ad58f-226">nx_pop3_client_mail_item_size_get</span></span>

<span data-ttu-id="ad58f-227">Получение размера указанного элемента почты</span><span class="sxs-lookup"><span data-stu-id="ad58f-227">Retrieve the size of the specified mail item</span></span>

### <a name="prototype"></a><span data-ttu-id="ad58f-228">Прототип</span><span class="sxs-lookup"><span data-stu-id="ad58f-228">Prototype</span></span>

```c
UINT nx_pop3_client_mail_item_size_get(
                NX_POP3_CLIENT *client_ptr,
                UINT mail_item, ULONG *size)
```

### <a name="description"></a><span data-ttu-id="ad58f-229">Описание</span><span class="sxs-lookup"><span data-stu-id="ad58f-229">Description</span></span>

<span data-ttu-id="ad58f-230">Эта служба создает запрос LIST для получения размера указанного элемента почты.</span><span class="sxs-lookup"><span data-stu-id="ad58f-230">This service makes a LIST request to obtain the size of the specified mail item.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ad58f-231">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ad58f-231">Input Parameters</span></span>

- <span data-ttu-id="ad58f-232">**client_ptr**: указатель на экземпляр клиента.</span><span class="sxs-lookup"><span data-stu-id="ad58f-232">**client_ptr**: Pointer to Client instance</span></span>
- <span data-ttu-id="ad58f-233">**mail_item**: порядковый индекс в пределах почтового ящика клиента.</span><span class="sxs-lookup"><span data-stu-id="ad58f-233">**mail_item**: Index into Client maildrop</span></span>
- <span data-ttu-id="ad58f-234">**size**: указатель на размер почтового сообщения.</span><span class="sxs-lookup"><span data-stu-id="ad58f-234">**size**: Pointer to size of mail message</span></span>

### <a name="return-values"></a><span data-ttu-id="ad58f-235">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ad58f-235">Return Values</span></span>

- <span data-ttu-id="ad58f-236">**NX_SUCCESS**: (0x00) элемент почты успешно получен.</span><span class="sxs-lookup"><span data-stu-id="ad58f-236">**NX_SUCCESS**: (0x00) Mail item successfully retrieved</span></span>
- <span data-ttu-id="ad58f-237">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) недопустимый индекс элемента почты.</span><span class="sxs-lookup"><span data-stu-id="ad58f-237">**NX_POP3_INVALID_MAIL_ITEM**: (0xB2) Invalid mail item index</span></span>
- <span data-ttu-id="ad58f-238">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) слишком короткие полезные данные в пакете для запроса POP3.</span><span class="sxs-lookup"><span data-stu-id="ad58f-238">**NX_POP3_INSUFFICIENT_PACKET_PAYLOAD**: (0xB6) Client packet payload too small for POP3 request.</span></span>
- <span data-ttu-id="ad58f-239">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) ответ сервера содержит состояние ошибки.</span><span class="sxs-lookup"><span data-stu-id="ad58f-239">**NX_POP3_SERVER_ERROR_STATUS**: (0xB4) Server replies with error status</span></span>
- <span data-ttu-id="ad58f-240">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) недопустимый входной параметр индекса.</span><span class="sxs-lookup"><span data-stu-id="ad58f-240">NX_POP3_CLIENT_INVALID_INDEX: (0xB8) Invalid mail index input</span></span>
- <span data-ttu-id="ad58f-241">NX_PTR_ERROR: (0x07) недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="ad58f-241">NX_PTR_ERROR: (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ad58f-242">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ad58f-242">Allowed From</span></span>

<span data-ttu-id="ad58f-243">Код приложения</span><span class="sxs-lookup"><span data-stu-id="ad58f-243">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ad58f-244">Пример</span><span class="sxs-lookup"><span data-stu-id="ad58f-244">Example</span></span>

```c
ULONG     size;
UINT      mail_item;

/* Retrieve the size of the specified mail item in POP3 Client maildrop. */
status = nx_pop3_client_mail_item_size_get (&demo_client, mail_item, &size);

/* If the maildrop message packet was successfully obtained, status = NX_SUCCESS. */
```
