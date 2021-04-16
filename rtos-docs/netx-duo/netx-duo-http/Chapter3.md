---
title: Глава 3. Описание служб HTTP для NetX Duo в ОСРВ Azure
description: В этой главе содержится описание всех служб HTTP для NetX Duo в ОСРВ Azure (перечисленных ниже) в алфавитном порядке, за исключением служб для NetX (только IPv4), поскольку эквиваленты одной и той же службы объединяются.
author: philmea
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 703071cd5a1d0677a3e995fccfe35d8b1dbbd9f3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814699"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-http-services"></a><span data-ttu-id="22a86-103">Глава 3. Описание служб HTTP для NetX Duo в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="22a86-103">Chapter 3 - Description of Azure RTOS NetX Duo HTTP Services</span></span>

<span data-ttu-id="22a86-104">В этой главе содержится описание всех служб HTTP для NetX Duo в ОСРВ Azure (перечисленных ниже) в алфавитном порядке, за исключением служб для NetX (только IPv4), поскольку эквиваленты одной и той же службы объединяются.</span><span class="sxs-lookup"><span data-stu-id="22a86-104">This chapter contains a description of all Azure RTOS NetX Duo HTTP services (listed below) in alphabetical order except for the ‘NetX’ (IPv4 only) equivalent of the same service are paired together).</span></span>

<span data-ttu-id="22a86-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, выделенные полужирным шрифтом, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="22a86-105">In the “Return Values” section in the following API descriptions, values in BOLD are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="22a86-106">**Службы HTTP-клиента:**</span><span class="sxs-lookup"><span data-stu-id="22a86-106">**HTTP Client services:**</span></span>

- <span data-ttu-id="22a86-107">**nx_http_client_create** — *создание экземпляра HTTP-клиента*</span><span class="sxs-lookup"><span data-stu-id="22a86-107">**nx_http_client_create** *Create an HTTP Client Instance*</span></span>
- <span data-ttu-id="22a86-108">**nx_http_client_delete** — *удаление экземпляра HTTP-клиента*</span><span class="sxs-lookup"><span data-stu-id="22a86-108">**nx_http_client_delete** *Delete an HTTP Client instance*</span></span>
- <span data-ttu-id="22a86-109">**nx_http_client_get_start** — *запуск HTTP-запроса GET (только IPv4)*</span><span class="sxs-lookup"><span data-stu-id="22a86-109">**nx_http_client_get_start** *Start an HTTP GET request (IPv4 only)*</span></span>
- <span data-ttu-id="22a86-110">**nx_http_client_get_start_extended** — *запуск HTTP-запроса GET (только IPv4)*</span><span class="sxs-lookup"><span data-stu-id="22a86-110">**nx_http_client_get_start_extended** *Start an HTTP GET request (IPv4 only)*</span></span>
- <span data-ttu-id="22a86-111">**nx_http_client_get_start** — *запуск HTTP-запроса GET (IPv4 или IPv6)*</span><span class="sxs-lookup"><span data-stu-id="22a86-111">**nxd_http_client_get_start** *Start an HTTP GET request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="22a86-112">**nx_http_client_get_start_extended** — *запуск HTTP-запроса GET (IPv4 или IPv6)*</span><span class="sxs-lookup"><span data-stu-id="22a86-112">**nxd_http_client_get_start_extended** *Start an HTTP GET request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="22a86-113">**nx_http_client_get_packet** — *получение следующего пакета данных ресурса*</span><span class="sxs-lookup"><span data-stu-id="22a86-113">**nx_http_client_get_packet** *Get next resource data packet*</span></span>
- <span data-ttu-id="22a86-114">**nx_http_client_put_start** — *запуск HTTP-запроса PUT (только IPv4)*</span><span class="sxs-lookup"><span data-stu-id="22a86-114">**nx_http_client_put_start** *Start an HTTP PUT request (IPv4 only)*</span></span>
- <span data-ttu-id="22a86-115">**nx_http_client_put_start_extended** — *запуск HTTP-запроса PUT (только IPv4)*</span><span class="sxs-lookup"><span data-stu-id="22a86-115">**nx_http_client_put_start_extended** *Start an HTTP PUT request (IPv4 only)*</span></span>
- <span data-ttu-id="22a86-116">**nx_http_client_put_start** — *запуск HTTP-запроса PUT (IPv4 или IPv6)*</span><span class="sxs-lookup"><span data-stu-id="22a86-116">**nxd_http_client_put_start** *Start an HTTP PUT request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="22a86-117">**nxd_http_client_put_start_extended** — *запуск HTTP-запроса PUT (IPv4 или IPv6)*</span><span class="sxs-lookup"><span data-stu-id="22a86-117">**nxd_http_client_put_start_extended** *Start an HTTP PUT request (IPv4 or IPv6)*</span></span>
- <span data-ttu-id="22a86-118">**nx_http_client_put_packet** — *отправка следующего пакета данных ресурса*</span><span class="sxs-lookup"><span data-stu-id="22a86-118">**nx_http_client_put_packet** *Send next resource data packet*</span></span>
- <span data-ttu-id="22a86-119">**nx_http_client_set_connect_port** — *изменение порта для подключения к HTTP-серверу*</span><span class="sxs-lookup"><span data-stu-id="22a86-119">**nx_http_client_set_connect_port** *Change the port to connect to the HTTP Server*</span></span>

<span data-ttu-id="22a86-120">**Службы HTTP-сервера:**</span><span class="sxs-lookup"><span data-stu-id="22a86-120">**HTTP server services:**</span></span>

- <span data-ttu-id="22a86-121">**nx_http_server_cache_info_callback_set** — *задание обратного вызова для получения возраста и даты последнего изменения указанного URL-адреса*</span><span class="sxs-lookup"><span data-stu-id="22a86-121">**nx_http_server_cache_info_callback_set** *Set callback to retrieve age and last modified date of specified URL*</span></span>
- <span data-ttu-id="22a86-122">**nx_http_server_callback_data_send** — *отправка данных HTTP из функции обратного вызова*</span><span class="sxs-lookup"><span data-stu-id="22a86-122">**nx_http_server_callback_data_send** *Send HTTP data from callback function*</span></span>
- <span data-ttu-id="22a86-123">**nx_http_server_callback_generate_response_header** — *создание заголовка ответа в функциях обратного вызова*</span><span class="sxs-lookup"><span data-stu-id="22a86-123">**nx_http_server_callback_generate_response_header** *Create response header in callback functions*</span></span>
- <span data-ttu-id="22a86-124">**nx_http_server_callback_generate_response_header_extended** — *создание заголовка ответа в функциях обратного вызова*</span><span class="sxs-lookup"><span data-stu-id="22a86-124">**nx_http_server_callback_generate_response_header_extended** *Create response header in callback functions*</span></span>
- <span data-ttu-id="22a86-125">**nx_http_server_callback_packet_send** — *отправка пакета HTTP из обратного вызова HTTP*</span><span class="sxs-lookup"><span data-stu-id="22a86-125">**nx_http_server_callback_packet_send** *Send an HTTP packet from an HTTP callback*</span></span>
- <span data-ttu-id="22a86-126">**nx_http_server_callback_response_send** — *отправка ответа из функции обратного вызова*</span><span class="sxs-lookup"><span data-stu-id="22a86-126">**nx_http_server_callback_response_send** *Send response from callback function*</span></span>
- <span data-ttu-id="22a86-127">**nx_http_server_callback_response_send_extended** — *отправка ответа из функции обратного вызова*</span><span class="sxs-lookup"><span data-stu-id="22a86-127">**nx_http_server_callback_response_send_extended** *Send response from callback function*</span></span>
- <span data-ttu-id="22a86-128">**nx_http_server_content_get** — *получение содержимого из запроса*</span><span class="sxs-lookup"><span data-stu-id="22a86-128">**nx_http_server_content_get** *Get content from the request*</span></span>
- <span data-ttu-id="22a86-129">**nx_http_server_content_get_extended** — *получение содержимого из запроса; поддерживает пустые запросы (содержимое нулевой длины)*</span><span class="sxs-lookup"><span data-stu-id="22a86-129">**nx_http_server_content_get_extended** *Get content from the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="22a86-130">**nx_http_server_content_length_get** — *получение длины содержимого в запросе*</span><span class="sxs-lookup"><span data-stu-id="22a86-130">**nx_http_server_content_length_get** *Get length of content in the request*</span></span>
- <span data-ttu-id="22a86-131">**nx_http_server_content_length_get_extended** — *получение длины содержимого в запросе; поддерживает пустые запросы (содержимое нулевой длины)*</span><span class="sxs-lookup"><span data-stu-id="22a86-131">**nx_http_server_content_length_get_extended** *Get length of content in the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="22a86-132">**nx_http_server_create** — *создание экземпляра HTTP-сервера*</span><span class="sxs-lookup"><span data-stu-id="22a86-132">**nx_http_server_create** *Create an HTTP Server instance*</span></span>
- <span data-ttu-id="22a86-133">**nx_http_server_delete**  * — удаление экземпляра HTTP-сервера*</span><span class="sxs-lookup"><span data-stu-id="22a86-133">**nx_http_server_delete** \* Delete an HTTP Server instance\*</span></span>
- <span data-ttu-id="22a86-134">**nx_http_server_get_entity_content** — *возврат размера и расположения содержимого сущности в URL-адресе*</span><span class="sxs-lookup"><span data-stu-id="22a86-134">**nx_http_server_get_entity_content** *Return size and location of entity content in URL*</span></span>
- <span data-ttu-id="22a86-135">**nx_http_server_get_entity_header** — *извлечение заголовка сущности URL-адреса в указанный буфер*</span><span class="sxs-lookup"><span data-stu-id="22a86-135">**nx_http_server_get_entity_header** *Extract URL entity header into specified buffer*</span></span>
- <span data-ttu-id="22a86-136">**nx_http_server_gmt_callback_set** — *задание обратного вызова для получения даты и времени по Гринвичу*</span><span class="sxs-lookup"><span data-stu-id="22a86-136">**nx_http_server_gmt_callback_set** *Set callback to retrieve GMT date and time*</span></span>
- <span data-ttu-id="22a86-137">**nx_http_server_invalid_userpassword_notify_set** — *задание обратного вызова, выполняющегося в случае получения в запросе клиента недопустимых имени пользователя и пароля*</span><span class="sxs-lookup"><span data-stu-id="22a86-137">**nx_http_server_invalid_userpassword_notify_set** *Set callback for when invalid username and password is received in a Client request*</span></span>
- <span data-ttu-id="22a86-138">**nx_http_server_mime_maps_additional_set** — *определение дополнительных сопоставлений MIME для HTML*</span><span class="sxs-lookup"><span data-stu-id="22a86-138">**nx_http_server_mime_maps_additional_set** *Define additional mime maps for HTML*</span></span>
- <span data-ttu-id="22a86-139">**nx_http_server_packet_content_find** — *извлечение длины содержимого в заголовке HTTP и установка указателя на начало данных содержимого*</span><span class="sxs-lookup"><span data-stu-id="22a86-139">**nx_http_server_packet_content_find** *Extract content length in HTTP header and set pointer to start of content data*</span></span>
- <span data-ttu-id="22a86-140">**nx_http_server_packet_get** — *прямое получение пакета клиента*</span><span class="sxs-lookup"><span data-stu-id="22a86-140">**nx_http_server_packet_get** *Receive client packet directly*</span></span>
- <span data-ttu-id="22a86-141">**nx_http_server_param_get** — *получение параметра из запроса*</span><span class="sxs-lookup"><span data-stu-id="22a86-141">**nx_http_server_param_get** *Get parameter from the request*</span></span>
- <span data-ttu-id="22a86-142">**nx_http_server_query_get** — *получение параметра из запроса*</span><span class="sxs-lookup"><span data-stu-id="22a86-142">**nx_http_server_query_get** *Get query from the request*</span></span>
- <span data-ttu-id="22a86-143">**nx_http_server_start** — *запуск HTTP-сервера*</span><span class="sxs-lookup"><span data-stu-id="22a86-143">**nx_http_server_start** *Start the HTTP Server*</span></span>
- <span data-ttu-id="22a86-144">**nx_http_server_stop** — *остановка HTTP-сервера*</span><span class="sxs-lookup"><span data-stu-id="22a86-144">**nx_http_server_stop** *Stop the HTTP Server*</span></span>
- <span data-ttu-id="22a86-145">**nx_http_server_type_get (не рекомендуется)**  — *извлечение типа HTTP, например text/plain из заголовка*</span><span class="sxs-lookup"><span data-stu-id="22a86-145">**nx_http_server_type_get (deprecated)** *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="22a86-146">**nx_http_server_type_get_extended** — *извлечение типа HTTP, например text/plain из заголовка*</span><span class="sxs-lookup"><span data-stu-id="22a86-146">**nx_http_server_type_get_extended** *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="22a86-147">**nx_http_server_digest_authenticate_notify_set** — *задание функции обратного вызова дайджест-проверки подлинности*</span><span class="sxs-lookup"><span data-stu-id="22a86-147">**nx_http_server_digest_authenticate_notify_set** *Set digest authenticate callback function*</span></span>
- <span data-ttu-id="22a86-148">**nx_http_server_authentication_check_set** — *задание функции обратного вызова проверки подлинности*</span><span class="sxs-lookup"><span data-stu-id="22a86-148">**nx_http_server_authentication_check_set** *Set authentication checking callback function*</span></span>

## <a name="nx_http_client_create"></a><span data-ttu-id="22a86-149">nx_http_client_create</span><span class="sxs-lookup"><span data-stu-id="22a86-149">nx_http_client_create</span></span>

<span data-ttu-id="22a86-150">Создание экземпляра клиента PPPoE</span><span class="sxs-lookup"><span data-stu-id="22a86-150">Create a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-151">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-151">Prototype</span></span>

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
            CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
            ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="22a86-152">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-152">Description</span></span>

<span data-ttu-id="22a86-153">Эта служба создает экземпляр HTTP-клиента в указанном экземпляре IP.</span><span class="sxs-lookup"><span data-stu-id="22a86-153">This service creates an HTTP Client instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-154">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-154">Input Parameters</span></span>

 - <span data-ttu-id="22a86-155">**client_ptr** — указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="22a86-155">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="22a86-156">**client_name** — имя экземпляра HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-156">**client_name** Name of HTTP Client instance.</span></span>
 - <span data-ttu-id="22a86-157">**ip_ptr** — указатель на экземпляр IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="22a86-157">**ip_ptr** Pointer to IP instance.</span></span>
 - <span data-ttu-id="22a86-158">**pool_ptr** — указатель на пул пакетов по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="22a86-158">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="22a86-159">Обратите внимание, что пакеты в этом пуле должны иметь объем полезных данных, достаточный для работы с полным заголовком ответа.</span><span class="sxs-lookup"><span data-stu-id="22a86-159">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="22a86-160">Это определяется параметром NX_HTTP_CLIENT_MIN_PACKET_SIZE в *nx_http_client.h*.</span><span class="sxs-lookup"><span data-stu-id="22a86-160">This is defined by NX_HTTP_CLIENT_MIN_PACKET_SIZE in *nx_http.h*.</span></span>
 - <span data-ttu-id="22a86-161">**window_size** — размер окна приема сокета TCP клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-161">**window_size** Size of the Client’s TCP socket receive window.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-162">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-162">Return Values</span></span>

 - <span data-ttu-id="22a86-163">**NX_SUCCESS** (0x00) — успешное создание HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-163">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
 - <span data-ttu-id="22a86-164">NX_PTR_ERROR (0x07) — недопустимый указатель на HTTP, ip_ptr или пул пакетов.</span><span class="sxs-lookup"><span data-stu-id="22a86-164">NX_PTR_ERROR (0x07) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
 - <span data-ttu-id="22a86-165">NX_HTTP_POOL_ERROR(0xE9) — недопустимый размер полезных данных в пуле пакетов.</span><span class="sxs-lookup"><span data-stu-id="22a86-165">NX_HTTP_POOL_ERROR (0xE9) Invalid payload size in packet pool</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-166">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-166">Allowed From</span></span>

<span data-ttu-id="22a86-167">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-167">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-168">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-168">Example</span></span>

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status =  nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);

/* If status is NX_SUCCESS an HTTP Client instance was successfully created. */
```

## <a name="nx_http_client_delete"></a><span data-ttu-id="22a86-169">nx_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="22a86-169">nx_http_client_delete</span></span>

<span data-ttu-id="22a86-170">Удаление экземпляра HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="22a86-170">Delete an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-171">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-171">Prototype</span></span>

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="22a86-172">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-172">Description</span></span>

<span data-ttu-id="22a86-173">Эта служба удаляет ранее созданный экземпляр HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-173">This service deletes a previously created HTTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-174">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-174">Input Parameters</span></span>

 - <span data-ttu-id="22a86-175">**client_ptr** — указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="22a86-175">**client_ptr** Pointer to HTTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-176">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-176">Return Values</span></span>

 - <span data-ttu-id="22a86-177">**NX_SUCCESS** (0x00) — успешное удаление HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-177">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
 - <span data-ttu-id="22a86-178">NX_PTR_ERROR (0x07) — недопустимый указатель на HTTP.</span><span class="sxs-lookup"><span data-stu-id="22a86-178">NX_PTR_ERROR (0x07) Invalid HTTP pointer</span></span>
 - <span data-ttu-id="22a86-179">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="22a86-179">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-180">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-180">Allowed From</span></span>

<span data-ttu-id="22a86-181">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-181">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-182">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-182">Example</span></span>

```c
/* Delete the HTTP Client instance “my_client.”  */
status =  nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully deleted. */
```

## <a name="nx_http_client_get_start"></a><span data-ttu-id="22a86-183">nx_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="22a86-183">nx_http_client_get_start</span></span>

<span data-ttu-id="22a86-184">Запуск HTTP-запроса GET через IPv4</span><span class="sxs-lookup"><span data-stu-id="22a86-184">Start an HTTP GET request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-185">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-185">Prototype</span></span>

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, CHAR *input_ptr,
            UINT input_size, CHAR *username, CHAR *password,
            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="22a86-186">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-186">Description</span></span>

<span data-ttu-id="22a86-187">Эта служба пытается создать и отправить запрос GET к ресурсу, указанному указателем resource, в ранее созданном экземпляре HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-187">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="22a86-188">Если эта подпрограмма возвращает NX_SUCCESS, приложение может выполнить несколько вызовов службы *nx_http_client_get_packet*, чтобы получить пакеты данных, соответствующих содержимому запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-188">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="22a86-189">Строка ресурса может ссылаться на локальный файл, например ``` “/index.htm” ```, или на другой URL-адрес, например ```http://abc.website.com/index.htm```, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.</span><span class="sxs-lookup"><span data-stu-id="22a86-189">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="22a86-190">Эта служба работает только через IPv4.</span><span class="sxs-lookup"><span data-stu-id="22a86-190">This service works only over IPv4 network.</span></span> <span data-ttu-id="22a86-191">Для приложений, которым требуется подключение к сети IPv6, следует использовать *nxd_http_client_get_start_extended ()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-191">For applications that need to connect to IPv6 network, *nxd_http_client_get_start_extended()* should be used.</span></span>

<span data-ttu-id="22a86-192">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="22a86-192">This service is deprecated.</span></span> <span data-ttu-id="22a86-193">Разработчикам рекомендуется перейти на использование *nx_http_client_get_start_extended()* или *nxd_http_client_get_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-193">Developers are encouraged to migrate to *nx_http_client_get_start_extended()* or *nxd_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-194">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-194">Input Parameters</span></span>

 - <span data-ttu-id="22a86-195">**client_ptr** — указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="22a86-195">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="22a86-196">**ip_address** — IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-196">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="22a86-197">**resource** — указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-197">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="22a86-198">**input_ptr** — указатель на дополнительные данные для запроса GET.</span><span class="sxs-lookup"><span data-stu-id="22a86-198">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="22a86-199">Это необязательно.</span><span class="sxs-lookup"><span data-stu-id="22a86-199">This is optional.</span></span> <span data-ttu-id="22a86-200">Если параметр допустим, указанные входные данные помещаются в область содержимого сообщения, а вместо операции GET используется POST.</span><span class="sxs-lookup"><span data-stu-id="22a86-200">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="22a86-201">**input_size** — число байтов в необязательных дополнительных входных данных, на которые указывает ```input_ptr```.</span><span class="sxs-lookup"><span data-stu-id="22a86-201">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="22a86-202">**username** — указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-202">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="22a86-203">**password** — указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-203">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="22a86-204">**wait_option** — определяет, как долго служба будет ожидать запуск запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-204">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="22a86-205">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="22a86-205">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="22a86-206">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="22a86-206">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="22a86-207">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="22a86-207">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="22a86-208">Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="22a86-208">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="22a86-209">Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-209">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-210">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-210">Return Values</span></span>

 - <span data-ttu-id="22a86-211">**NX_SUCCESS** (0x00) — успешная отправка HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="22a86-211">**NX_SUCCESS** (0x00) Successfully sent HTTP Client.</span></span> <span data-ttu-id="22a86-212">ПОЛУЧЕНИЕ сообщения о запуске.</span><span class="sxs-lookup"><span data-stu-id="22a86-212">GET start message.</span></span>
 - <span data-ttu-id="22a86-213">**NX_HTTP_ERROR** (0xE0) — внутренняя ошибка HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-213">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
 - <span data-ttu-id="22a86-214">**NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="22a86-214">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="22a86-215">**NX_HTTP_FAILED** (0xE2) — ошибка HTTP-клиента при взаимодействии с HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="22a86-215">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
 - <span data-ttu-id="22a86-216">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) — недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="22a86-216">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
 - <span data-ttu-id="22a86-217">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-217">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="22a86-218">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="22a86-218">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-219">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-219">Allowed From</span></span>

<span data-ttu-id="22a86-220">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-220">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-221">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-221">Example</span></span>

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

## <a name="nx_http_client_get_start_extended"></a><span data-ttu-id="22a86-222">nx_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="22a86-222">nx_http_client_get_start_extended</span></span>

<span data-ttu-id="22a86-223">Запуск HTTP-запроса GET через IPv4</span><span class="sxs-lookup"><span data-stu-id="22a86-223">Start an HTTP GET request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-224">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-224">Prototype</span></span>

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
            ULONG ip_address, CHAR *resource, UINT resource_length,
            CHAR *input_ptr, UINT input_size, CHAR *username,
            UINT username_length, CHAR *password, UINT password_length,
            ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="22a86-225">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-225">Description</span></span>

<span data-ttu-id="22a86-226">Эта служба пытается создать и отправить запрос GET к ресурсу, указанному указателем resource, в ранее созданном экземпляре HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-226">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="22a86-227">Если эта подпрограмма возвращает NX_SUCCESS, приложение может выполнить несколько вызовов службы *nx_http_client_get_packet*, чтобы получить пакеты данных, соответствующих содержимому запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-227">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="22a86-228">Строка ресурса может ссылаться на локальный файл, например ``` “/index.htm” ```, или на другой URL-адрес, например ```http://abc.website.com/index.htm```, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.</span><span class="sxs-lookup"><span data-stu-id="22a86-228">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="22a86-229">Эта служба работает только через IPv4.</span><span class="sxs-lookup"><span data-stu-id="22a86-229">This service works only over IPv4 network.</span></span> <span data-ttu-id="22a86-230">Для приложений, которым требуется подключение к сети IPv6, следует использовать *nxd_http_client_get_start_extended ()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-230">For applications that need to connect to IPv6 network, *nxd_http_client_get_start_extended()* should be used.</span></span>

<span data-ttu-id="22a86-231">Эта служба заменяет *nx_http_client_get_start()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-231">This service replaces *nx_http_client_get_start()*.</span></span> <span data-ttu-id="22a86-232">Она требует от вызывающей стороны указания длины ресурса, имени пользователя и пароля.</span><span class="sxs-lookup"><span data-stu-id="22a86-232">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-233">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-233">Input Parameters</span></span>

 - <span data-ttu-id="22a86-234">**client_ptr** — указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="22a86-234">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="22a86-235">**ip_address** — IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-235">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="22a86-236">**resource** — указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-236">**resource Pointer** to URL string for requested resource.</span></span>
 - <span data-ttu-id="22a86-237">**resource_length** — длина строки URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-237">**resource_length** Length of URL string for requested resource.</span></span>
 - <span data-ttu-id="22a86-238">**input_ptr** — указатель на дополнительные данные для запроса GET.</span><span class="sxs-lookup"><span data-stu-id="22a86-238">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="22a86-239">Это необязательно.</span><span class="sxs-lookup"><span data-stu-id="22a86-239">This is optional.</span></span> <span data-ttu-id="22a86-240">Если параметр допустим, указанные входные данные помещаются в область содержимого сообщения, а вместо операции GET используется POST.</span><span class="sxs-lookup"><span data-stu-id="22a86-240">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="22a86-241">**input_size** — число байтов в необязательных дополнительных входных данных, на которые указывает ```input_ptr```.</span><span class="sxs-lookup"><span data-stu-id="22a86-241">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="22a86-242">**username** — указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-242">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="22a86-243">**username_length** — длина необязательного имени пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-243">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="22a86-244">**password** — указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-244">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="22a86-245">**password_length** — длина необязательного пароля для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-245">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="22a86-246">**wait_option** — определяет, как долго служба будет ожидать запуск запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-246">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="22a86-247">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="22a86-247">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="22a86-248">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="22a86-248">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="22a86-249">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="22a86-249">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="22a86-250">Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="22a86-250">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="22a86-251">Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-251">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-252">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-252">Return Values</span></span>

 - <span data-ttu-id="22a86-253">**NX_SUCCESS** (0x00) — успешная отправка HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="22a86-253">**NX_SUCCESS** (0x00) Successfully sent HTTP Client.</span></span> <span data-ttu-id="22a86-254">ПОЛУЧЕНИЕ сообщения о запуске</span><span class="sxs-lookup"><span data-stu-id="22a86-254">GET start message</span></span>
 - <span data-ttu-id="22a86-255">**NX_HTTP_ERROR** (0xE0) — внутренняя ошибка HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-255">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
 - <span data-ttu-id="22a86-256">**NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="22a86-256">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="22a86-257">**NX_HTTP_FAILED** (0xE2) — ошибка HTTP-клиента при взаимодействии с HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="22a86-257">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
 - <span data-ttu-id="22a86-258">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) — недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="22a86-258">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
 - <span data-ttu-id="22a86-259">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-259">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="22a86-260">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="22a86-260">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-261">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-261">Allowed From</span></span>

<span data-ttu-id="22a86-262">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-262">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-263">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-263">Example</span></span>

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

## <a name="nxd_http_client_get_start"></a><span data-ttu-id="22a86-264">nxd_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="22a86-264">nxd_http_client_get_start</span></span>

<span data-ttu-id="22a86-265">Отправка HTTP-запроса GET (IPv4 или IPv6)</span><span class="sxs-lookup"><span data-stu-id="22a86-265">Send an HTTP GET request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-266">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-266">Prototype</span></span>

```c
UINT nxd_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                CHAR *input_ptr, UINT input_size, CHAR *username, CHAR *password, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="22a86-267">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-267">Description</span></span>

<span data-ttu-id="22a86-268">Эта служба пытается создать и отправить запрос GET к ресурсу, указанному указателем resource, в ранее созданном экземпляре HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-268">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="22a86-269">Его можно использовать для подключения к сети IPv4 или IPv6.</span><span class="sxs-lookup"><span data-stu-id="22a86-269">It can be used to connect to IPv4 or IPv6 network.</span></span> <span data-ttu-id="22a86-270">Если эта подпрограмма возвращает NX_SUCCESS, приложение может выполнить несколько вызовов службы *nx_http_client_get_packet*, чтобы получить пакеты данных, соответствующих содержимому запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-270">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
><span data-ttu-id="22a86-271">Строка ресурса может ссылаться на локальный файл, например ``` “/index.htm” ```, или на другой URL-адрес, например ```http://abc.website.com/index.htm```, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.</span><span class="sxs-lookup"><span data-stu-id="22a86-271">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="22a86-272">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="22a86-272">This service is deprecated.</span></span> <span data-ttu-id="22a86-273">Разработчикам рекомендуется перейти на использование *nxd_http_client_get_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-273">Developers are encouraged to migrate to *nxd_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-274">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-274">Input Parameters</span></span>

 - <span data-ttu-id="22a86-275">**client_ptr** — указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="22a86-275">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="22a86-276">**Server_ip** — IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-276">**Server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="22a86-277">**resource** — указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-277">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="22a86-278">**input_ptr** — указатель на дополнительные данные для запроса GET.</span><span class="sxs-lookup"><span data-stu-id="22a86-278">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="22a86-279">Это необязательно.</span><span class="sxs-lookup"><span data-stu-id="22a86-279">This is optional.</span></span> <span data-ttu-id="22a86-280">Если параметр допустим, указанные входные данные помещаются в область содержимого сообщения, а вместо операции GET используется POST.</span><span class="sxs-lookup"><span data-stu-id="22a86-280">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="22a86-281">**input_size** — число байтов в необязательных дополнительных входных данных, на которые указывает ```input_ptr```.</span><span class="sxs-lookup"><span data-stu-id="22a86-281">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="22a86-282">**username** — указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-282">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="22a86-283">**username_length** — длина необязательного имени пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-283">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="22a86-284">**password** — указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-284">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="22a86-285">**password_length** — длина необязательного пароля для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-285">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="22a86-286">**wait_option** — определяет, как долго служба будет ожидать запуск запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-286">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="22a86-287">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="22a86-287">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="22a86-288">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="22a86-288">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="22a86-289">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="22a86-289">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="22a86-290">Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="22a86-290">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="22a86-291">Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-291">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-292">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-292">Return Values</span></span>

 - <span data-ttu-id="22a86-293">**NX_SUCCESS** (0x00) — запрос GET успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="22a86-293">**NX_SUCCESS** (0x00) Successfully sent GET request</span></span>
 - <span data-ttu-id="22a86-294">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) — длина пароля превышает размер буфера.</span><span class="sxs-lookup"><span data-stu-id="22a86-294">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Password exceeds buffer size</span></span>
 - <span data-ttu-id="22a86-295">**NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="22a86-295">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="22a86-296">**NX_HTTP_FAILED** (0xE2) — недопустимые параметры пакета.</span><span class="sxs-lookup"><span data-stu-id="22a86-296">**NX_HTTP_FAILED** (0xE2) Invalid packet parameters.</span></span>
 - <span data-ttu-id="22a86-297">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) — недопустимое имя или пароль.</span><span class="sxs-lookup"><span data-stu-id="22a86-297">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name or password</span></span>
 - <span data-ttu-id="22a86-298">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-298">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="22a86-299">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="22a86-299">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-300">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-300">Allowed From</span></span>

<span data-ttu-id="22a86-301">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-302">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-302">Example</span></span>

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

## <a name="nxd_http_client_get_start_extended"></a><span data-ttu-id="22a86-303">nxd_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="22a86-303">nxd_http_client_get_start_extended</span></span>

<span data-ttu-id="22a86-304">Отправка HTTP-запроса GET (IPv4 или IPv6)</span><span class="sxs-lookup"><span data-stu-id="22a86-304">Send an HTTP GET request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-305">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-305">Prototype</span></span>

```c
UINT nxd_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
                NXD_ADDRESS *server_ip, CHAR *resource,
                UINT resource_length, CHAR *input_ptr,
                UINT input_size, CHAR *username, UINT
                username_length, CHAR *password, UINT
                password_length, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="22a86-306">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-306">Description</span></span>

<span data-ttu-id="22a86-307">Эта служба пытается создать и отправить запрос GET к ресурсу, указанному указателем resource, в ранее созданном экземпляре HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-307">This service attempts to create and send a GET request with the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="22a86-308">Его можно использовать для подключения к сети IPv4 или IPv6.</span><span class="sxs-lookup"><span data-stu-id="22a86-308">It can be used to connect to IPv4 or IPv6 network.</span></span> <span data-ttu-id="22a86-309">Если эта подпрограмма возвращает NX_SUCCESS, приложение может выполнить несколько вызовов службы *nx_http_client_get_packet*, чтобы получить пакеты данных, соответствующих содержимому запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-309">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

> [!NOTE]
> <span data-ttu-id="22a86-310">Строка ресурса может ссылаться на локальный файл, например ``` “/index.htm” ```, или на другой URL-адрес, например ```http://abc.website.com/index.htm```, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.</span><span class="sxs-lookup"><span data-stu-id="22a86-310">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="22a86-311">Эта служба заменяет *nxd_http_client_get_start()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-311">This service replaces *nxd_http_client_get_start()*.</span></span> <span data-ttu-id="22a86-312">Она требует от вызывающей стороны указания длины ресурса, имени пользователя и пароля.</span><span class="sxs-lookup"><span data-stu-id="22a86-312">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-313">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-313">Input Parameters</span></span>

 - <span data-ttu-id="22a86-314">**client_ptr** — указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="22a86-314">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="22a86-315">**Server_ip** — IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-315">**Server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="22a86-316">**resource** — указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-316">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="22a86-317">**resource_length** — длина строки URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-317">**resource_length** Length of URL string for requested resource.</span></span>
 - <span data-ttu-id="22a86-318">**input_ptr** — указатель на дополнительные данные для запроса GET.</span><span class="sxs-lookup"><span data-stu-id="22a86-318">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="22a86-319">Это необязательно.</span><span class="sxs-lookup"><span data-stu-id="22a86-319">This is optional.</span></span> <span data-ttu-id="22a86-320">Если параметр допустим, указанные входные данные помещаются в область содержимого сообщения, а вместо операции GET используется POST.</span><span class="sxs-lookup"><span data-stu-id="22a86-320">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
 - <span data-ttu-id="22a86-321">**input_size** — число байтов в необязательных дополнительных входных данных, на которые указывает ```input_ptr```.</span><span class="sxs-lookup"><span data-stu-id="22a86-321">**input_size** Number of bytes in optional additional input pointed to by ```input_ptr```.</span></span>
 - <span data-ttu-id="22a86-322">**username** — указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-322">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="22a86-323">**username_length** — длина необязательного имени пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-323">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="22a86-324">**password** — указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-324">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="22a86-325">**password_length** — длина необязательного пароля для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-325">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="22a86-326">**wait_option** — определяет, как долго служба будет внутренне ожидать обработки запуска запроса get HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-326">**wait_option** Defines how long the service will wait internally to process the HTTP Client get start.</span></span> <span data-ttu-id="22a86-327">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="22a86-327">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="22a86-328">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="22a86-328">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="22a86-329">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="22a86-329">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="22a86-330">Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="22a86-330">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="22a86-331">Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-331">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-332">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-332">Return Values</span></span>

 - <span data-ttu-id="22a86-333">**NX_SUCCESS** (0x00) — запрос GET успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="22a86-333">**NX_SUCCESS** (0x00) Successfully sent GET request</span></span>
 - <span data-ttu-id="22a86-334">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) — длина пароля превышает размер буфера.</span><span class="sxs-lookup"><span data-stu-id="22a86-334">**NX_HTTP_PASSWORD_TOO_LONG** (0xF0) Password exceeds buffer size</span></span>
 - <span data-ttu-id="22a86-335">**NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="22a86-335">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="22a86-336">**NX_HTTP_FAILED** (0xE2) — недопустимые параметры пакета.</span><span class="sxs-lookup"><span data-stu-id="22a86-336">**NX_HTTP_FAILED** (0xE2) Invalid packet parameters.</span></span>
 - <span data-ttu-id="22a86-337">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) — недопустимое имя или пароль.</span><span class="sxs-lookup"><span data-stu-id="22a86-337">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name or password</span></span>
 - <span data-ttu-id="22a86-338">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-338">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="22a86-339">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="22a86-339">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-340">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-340">Allowed From</span></span>

<span data-ttu-id="22a86-341">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-341">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-342">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-342">Example</span></span>

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

## <a name="nx_http_client_get_packet"></a><span data-ttu-id="22a86-343">nx_http_client_get_packet</span><span class="sxs-lookup"><span data-stu-id="22a86-343">nx_http_client_get_packet</span></span>

<span data-ttu-id="22a86-344">Получение следующего пакета данных ресурса</span><span class="sxs-lookup"><span data-stu-id="22a86-344">Get next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-345">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-345">Prototype</span></span>

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET **packet_ptr, ULONG
                               wait_option);
```

### <a name="description"></a><span data-ttu-id="22a86-346">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-346">Description</span></span>

<span data-ttu-id="22a86-347">Эта служба извлекает следующий пакет содержимого ресурса, запрошенного предыдущим вызовом *nx_http_client_get_start*.</span><span class="sxs-lookup"><span data-stu-id="22a86-347">This service retrieves the next packet of content of the resource requested by the previous *nx_http_client_get_start* call.</span></span> <span data-ttu-id="22a86-348">Последовательные вызовы этой подпрограммы должны выполняться до получения состояния возврата NX_HTTP_GET_DONE.</span><span class="sxs-lookup"><span data-stu-id="22a86-348">Successive calls to this routine should be made until the return status of NX_HTTP_GET_DONE is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-349">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-349">Input Parameters</span></span>

 - <span data-ttu-id="22a86-350">**client_ptr** — указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="22a86-350">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="22a86-351">**packet_ptr** — назначение для указателя пакета, содержащего частичное содержимое ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-351">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
 - <span data-ttu-id="22a86-352">**wait_option** — определяет, как долго служба будет ожидать получение пакета HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="22a86-352">**wait_option** Defines how long the service will wait for the HTTP Client get packet.</span></span> <span data-ttu-id="22a86-353">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="22a86-353">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="22a86-354">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="22a86-354">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="22a86-355">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="22a86-355">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="22a86-356">Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="22a86-356">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="22a86-357">Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-357">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-358">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-358">Return Values</span></span>

 - <span data-ttu-id="22a86-359">**NX_SUCCESS** (0x00) — пакет получен HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="22a86-359">**NX_SUCCESS** (0x00) Successful HTTP Client get packet.</span></span>
 - <span data-ttu-id="22a86-360">**NX_HTTP_GET_DONE** (0xEC) — получение пакета HTTP-клиентом выполнено.</span><span class="sxs-lookup"><span data-stu-id="22a86-360">**NX_HTTP_GET_DONE** (0xEC) HTTP Client get packet is done</span></span>
 - <span data-ttu-id="22a86-361">**NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не находится в режиме получения.</span><span class="sxs-lookup"><span data-stu-id="22a86-361">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not in get mode.</span></span>
 - <span data-ttu-id="22a86-362">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) — недопустимая длина пакета.</span><span class="sxs-lookup"><span data-stu-id="22a86-362">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
 - <span data-ttu-id="22a86-363">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-363">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="22a86-364">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="22a86-364">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-365">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-365">Allowed From</span></span>

<span data-ttu-id="22a86-366">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-366">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-367">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-367">Example</span></span>

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
   Note that the nx_http_client_get_start routine must have been called
   previously. */
status =  nx_http_client_get_packet(&my_client, &next_packet, 1000);


/* If status is NX_SUCCESS, the next packet of content is pointed to
   by “next_packet”. */
```

## <a name="nx_http_client_put_start"></a><span data-ttu-id="22a86-368">nx_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="22a86-368">nx_http_client_put_start</span></span>

<span data-ttu-id="22a86-369">Запуск HTTP-запроса PUT через IPv4</span><span class="sxs-lookup"><span data-stu-id="22a86-369">Start an HTTP PUT request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-370">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-370">Prototype</span></span>

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               ULONG ip_address, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="22a86-371">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-371">Description</span></span>

<span data-ttu-id="22a86-372">Эта служба пытается отправить запрос PUT с указанным ресурсом к HTTP-серверу по указанному IP-адресу.</span><span class="sxs-lookup"><span data-stu-id="22a86-372">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="22a86-373">Если эта подпрограмма выполняется успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_http_client_put_packet()* , чтобы фактически отправить содержимое ресурса на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="22a86-373">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="22a86-374">Строка ресурса может ссылаться на локальный файл, например ``` “/index.htm” ```, или на другой URL-адрес, например ```http://abc.website.com/index.htm```, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.</span><span class="sxs-lookup"><span data-stu-id="22a86-374">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="22a86-375">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="22a86-375">This service is deprecated.</span></span> <span data-ttu-id="22a86-376">Разработчикам рекомендуется перейти на использование *nx_http_client_put_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-376">Developers are encouraged to migrate to *nxd_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-377">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-377">Input Parameters</span></span>

 - <span data-ttu-id="22a86-378">**client_ptr** — указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="22a86-378">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="22a86-379">**ip_address** — IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-379">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="22a86-380">**resource** — указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-380">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="22a86-381">**username** — указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-381">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="22a86-382">**password** — указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-382">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="22a86-383">**total_bytes** — общее число отправляемых байтов ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-383">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="22a86-384">Обратите внимание, что совокупная длина всех пакетов, отправленных через последующие вызовы *nx_http_client_put_packet*, должна равняться этому значению.</span><span class="sxs-lookup"><span data-stu-id="22a86-384">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="22a86-385">**wait_option** — определяет, как долго служба будет ожидать запуск запроса PUT HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-385">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="22a86-386">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="22a86-386">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="22a86-387">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="22a86-387">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="22a86-388">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="22a86-388">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="22a86-389">Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="22a86-389">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="22a86-390">Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="22a86-390">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-391">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-391">Return Values</span></span>

 - <span data-ttu-id="22a86-392">**NX_SUCCESS** (0x00) — запрос PUT успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="22a86-392">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
 - <span data-ttu-id="22a86-393">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) — слишком длинное имя пользователя для буфера.</span><span class="sxs-lookup"><span data-stu-id="22a86-393">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
 - <span data-ttu-id="22a86-394">**NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="22a86-394">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="22a86-395">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-395">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="22a86-396">NX_SIZE_ERROR (0x09) — недопустимый общий размер ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-396">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="22a86-397">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="22a86-397">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-398">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-398">Allowed From</span></span>

<span data-ttu-id="22a86-399">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-400">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-400">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, “myname”, “mypassword”, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nx_http_client_put_start_extended"></a><span data-ttu-id="22a86-401">nx_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="22a86-401">nx_http_client_put_start_extended</span></span>

<span data-ttu-id="22a86-402">Запуск HTTP-запроса PUT через IPv4</span><span class="sxs-lookup"><span data-stu-id="22a86-402">Start an HTTP PUT request over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-403">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-403">Prototype</span></span>

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
           ULONG ip_address, CHAR *resource, UINT resource_length,
           CHAR *username,UINT username_length, CHAR *password,
           UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="22a86-404">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-404">Description</span></span>

<span data-ttu-id="22a86-405">Эта служба пытается отправить запрос PUT с указанным ресурсом к HTTP-серверу по указанному IP-адресу.</span><span class="sxs-lookup"><span data-stu-id="22a86-405">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="22a86-406">Если эта подпрограмма выполняется успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_http_client_put_packet()* , чтобы фактически отправить содержимое ресурса на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="22a86-406">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="22a86-407">Строка ресурса может ссылаться на локальный файл, например ``` “/index.htm” ```, или на другой URL-адрес, например ```http://abc.website.com/index.htm```, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.</span><span class="sxs-lookup"><span data-stu-id="22a86-407">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="22a86-408">Эта служба заменяет *nx_http_client_put_start()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-408">This service replaces *nx_http_client_put_start()*.</span></span> <span data-ttu-id="22a86-409">Она требует от вызывающей стороны указания длины ресурса, имени пользователя и пароля.</span><span class="sxs-lookup"><span data-stu-id="22a86-409">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-410">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-410">Input Parameters</span></span>

 - <span data-ttu-id="22a86-411">**client_ptr** — указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="22a86-411">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="22a86-412">**ip_address** — IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-412">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="22a86-413">**resource** — указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-413">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="22a86-414">**resource_length** — длина строки URL-адреса для ресурса, отправляемого на сервер.</span><span class="sxs-lookup"><span data-stu-id="22a86-414">**resource_length** Length of URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="22a86-415">**username** — указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-415">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="22a86-416">**username_length** — длина необязательного имени пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-416">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="22a86-417">**password** — указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-417">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="22a86-418">**password_length** — длина необязательного пароля для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-418">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="22a86-419">**total_bytes** — общее число отправляемых байтов ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-419">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="22a86-420">Обратите внимание, что совокупная длина всех пакетов, отправленных через последующие вызовы *nx_http_client_put_packet*, должна равняться этому значению.</span><span class="sxs-lookup"><span data-stu-id="22a86-420">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="22a86-421">**wait_option** — определяет, как долго служба будет ожидать запуск запроса PUT HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-421">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="22a86-422">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="22a86-422">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="22a86-423">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="22a86-423">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="22a86-424">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="22a86-424">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="22a86-425">Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="22a86-425">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="22a86-426">Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-426">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-427">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-427">Return Values</span></span>

 - <span data-ttu-id="22a86-428">**NX_SUCCESS** (0x00) — запрос PUT успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="22a86-428">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
 - <span data-ttu-id="22a86-429">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) — слишком длинное имя пользователя для буфера.</span><span class="sxs-lookup"><span data-stu-id="22a86-429">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
 - <span data-ttu-id="22a86-430">**NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="22a86-430">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="22a86-431">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-431">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="22a86-432">NX_SIZE_ERROR (0x09) — недопустимый общий размер ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-432">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="22a86-433">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="22a86-433">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-434">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-434">Allowed From</span></span>

<span data-ttu-id="22a86-435">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-435">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-436">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-436">Example</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP Server
   at IP address 1.2.3.5. */
status =  nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
“/TEST.HTM”, 9, “myname”, 6, “mypassword”, 10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully been
   started. */
```

## <a name="nxd_http_client_put_start"></a><span data-ttu-id="22a86-437">nxd_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="22a86-437">nxd_http_client_put_start</span></span>

<span data-ttu-id="22a86-438">Запуск HTTP-запроса PUT (IPv4 или IPv6)</span><span class="sxs-lookup"><span data-stu-id="22a86-438">Start an HTTP PUT request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-439">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-439">Prototype</span></span>

```c
UINT nxd_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                               NXD_ADDRESS *server_ip, CHAR *resource,
                               CHAR *username, CHAR *password,
                               ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="22a86-440">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-440">Description</span></span>

<span data-ttu-id="22a86-441">Эта служба пытается отправить запрос PUT (на отправку) с указанным ресурсом к HTTP-серверу по указанному IP-адресу через IPv6.</span><span class="sxs-lookup"><span data-stu-id="22a86-441">This service attempts to PUT (send) the specified resource on the HTTP Server at the supplied IP address over IPv6.</span></span> <span data-ttu-id="22a86-442">Если эта подпрограмма выполняется успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_http_client_put_packet()* , чтобы фактически отправить содержимое ресурса на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="22a86-442">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="22a86-443">Строка ресурса может ссылаться на локальный файл, например ``` “/index.htm” ```, или на другой URL-адрес, например ```http://abc.website.com/index.htm```, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.</span><span class="sxs-lookup"><span data-stu-id="22a86-443">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="22a86-444">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="22a86-444">This service is deprecated.</span></span> <span data-ttu-id="22a86-445">Разработчикам рекомендуется перейти на использование *nx_http_client_put_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-445">Developers are encouraged to migrate to *nxd_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-446">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-446">Input Parameters</span></span>

 - <span data-ttu-id="22a86-447">**client_ptr** — указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="22a86-447">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="22a86-448">**server_ip** — IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-448">**server_ip** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="22a86-449">**resource** — указатель на строку URL-адреса для ресурса, отправляемого на сервер.</span><span class="sxs-lookup"><span data-stu-id="22a86-449">**resource** Pointer to URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="22a86-450">**username** — указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-450">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="22a86-451">**password** — указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-451">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="22a86-452">**total_bytes** — общее число отправляемых байтов ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-452">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="22a86-453">Обратите внимание, что совокупная длина всех пакетов, отправленных через последующие вызовы *nx_http_client_put_packet*, должна равняться этому значению.</span><span class="sxs-lookup"><span data-stu-id="22a86-453">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="22a86-454">**wait_option** — определяет, как долго служба будет ожидать запуск запроса PUT HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-454">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="22a86-455">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="22a86-455">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="22a86-456">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="22a86-456">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="22a86-457">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="22a86-457">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="22a86-458">Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="22a86-458">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="22a86-459">Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-459">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-460">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-460">Return Values</span></span>

 - <span data-ttu-id="22a86-461">**NX_SUCCESS** (0x00) — запрос PUT HTTP-клиента успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="22a86-461">**NX_SUCCESS** (0x00) Successfully sent HTTP Client PUT request</span></span>
 - <span data-ttu-id="22a86-462">**NX_HTTP_ERROR** (0xE0) — внутренняя ошибка HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-462">**NX_HTTP_ERROR** (0xE0) HTTP Client internal error</span></span>
 - <span data-ttu-id="22a86-463">**NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="22a86-463">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="22a86-464">**NX_HTTP_FAILED** (0xE2) — ошибка HTTP-клиента при взаимодействии с HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="22a86-464">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server</span></span>
 - <span data-ttu-id="22a86-465">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-465">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="22a86-466">NX_SIZE_ERROR (0x09) — недопустимый общий размер ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-466">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="22a86-467">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="22a86-467">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-468">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-468">Allowed From</span></span>

<span data-ttu-id="22a86-469">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-469">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-470">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-470">Example</span></span>

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

## <a name="nxd_http_client_put_start_extended"></a><span data-ttu-id="22a86-471">nxd_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="22a86-471">nxd_http_client_put_start_extended</span></span>

<span data-ttu-id="22a86-472">Запуск HTTP-запроса PUT (IPv4 или IPv6)</span><span class="sxs-lookup"><span data-stu-id="22a86-472">Start an HTTP PUT request (IPv4 or IPv6)</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-473">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-473">Prototype</span></span>

```c
UINT nxd_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
          NXD_ADDRESS *server_ip, CHAR *resource, UINT resource_length,
          CHAR *username, UINT username_length, CHAR *password,
          UINT password_length, ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="22a86-474">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-474">Description</span></span>

<span data-ttu-id="22a86-475">Эта служба пытается отправить запрос PUT (на отправку) с указанным ресурсом к HTTP-серверу по указанному IP-адресу через IPv6.</span><span class="sxs-lookup"><span data-stu-id="22a86-475">This service attempts to PUT (send) the specified resource on the HTTP Server at the supplied IP address over IPv6.</span></span> <span data-ttu-id="22a86-476">Если эта подпрограмма выполняется успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_http_client_put_packet()* , чтобы фактически отправить содержимое ресурса на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="22a86-476">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet()* routine to actually send the resource contents to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="22a86-477">Строка ресурса может ссылаться на локальный файл, например ``` “/index.htm” ```, или на другой URL-адрес, например ```http://abc.website.com/index.htm```, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.</span><span class="sxs-lookup"><span data-stu-id="22a86-477">The resource string can refer to a local file e.g. ``` “/index.htm” ``` or it can refer to another URL e.g. ```http://abc.website.com/index.htm``` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="22a86-478">Эта служба заменяет *nxd_http_client_put_start()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-478">This service replaces *nxd_http_client_put_start()*.</span></span> <span data-ttu-id="22a86-479">Она требует от вызывающей стороны указания длины ресурса, имени пользователя и пароля.</span><span class="sxs-lookup"><span data-stu-id="22a86-479">It requires caller to specify the length of the resource, username and password.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-480">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-480">Input Parameters</span></span>

 - <span data-ttu-id="22a86-481">**client_ptr** — указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="22a86-481">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="22a86-482">**ip_address** — IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-482">**ip_address** IP address of the HTTP Server.</span></span>
 - <span data-ttu-id="22a86-483">**resource** — указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-483">**resource** Pointer to URL string for requested resource.</span></span>
 - <span data-ttu-id="22a86-484">**resource_length** — длина строки URL-адреса для ресурса, отправляемого на сервер.</span><span class="sxs-lookup"><span data-stu-id="22a86-484">**resource_length** Length of URL string for resource to send to Server.</span></span>
 - <span data-ttu-id="22a86-485">**username** — указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-485">**username** Pointer to optional user name for authentication.</span></span>
 - <span data-ttu-id="22a86-486">**username_length** — длина необязательного имени пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-486">**username_length** Length of optional user name for authentication.</span></span>
 - <span data-ttu-id="22a86-487">**password** — указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-487">**password** Pointer to optional password for authentication.</span></span>
 - <span data-ttu-id="22a86-488">**password_length** — длина необязательного пароля для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-488">**password_length** Length of optional password for authentication.</span></span>
 - <span data-ttu-id="22a86-489">**total_bytes** — общее число отправляемых байтов ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-489">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="22a86-490">Обратите внимание, что совокупная длина всех пакетов, отправленных через последующие вызовы *nx_http_client_put_packet*, должна равняться этому значению.</span><span class="sxs-lookup"><span data-stu-id="22a86-490">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
 - <span data-ttu-id="22a86-491">**wait_option** — определяет, как долго служба будет ожидать запуск запроса PUT HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-491">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="22a86-492">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="22a86-492">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="22a86-493">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="22a86-493">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="22a86-494">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="22a86-494">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="22a86-495">Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="22a86-495">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="22a86-496">Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-496">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-497">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-497">Return Values</span></span>

 - <span data-ttu-id="22a86-498">**NX_SUCCESS** (0x00) — запрос PUT HTTP-клиента успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="22a86-498">**NX_SUCCESS** (0x00) Successfully sent HTTP Client PUT request</span></span>
 - <span data-ttu-id="22a86-499">**NX_HTTP_ERROR** (0xE0) — внутренняя ошибка HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-499">**NX_HTTP_ERROR** (0xE0) HTTP Client internal error</span></span>
 - <span data-ttu-id="22a86-500">**NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="22a86-500">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="22a86-501">NX_HTTP_FAILED (0xE2) — ошибка HTTP-клиента при взаимодействии с HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="22a86-501">NX_HTTP_FAILED (0xE2) HTTP Client error communicating with the HTTP Server</span></span>
 - <span data-ttu-id="22a86-502">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-502">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="22a86-503">NX_SIZE_ERROR (0x09) — недопустимый общий размер ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-503">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
 - <span data-ttu-id="22a86-504">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="22a86-504">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-505">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-505">Allowed From</span></span>

<span data-ttu-id="22a86-506">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-506">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-507">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-507">Example</span></span>

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

## <a name="nx_http_client_put_packet"></a><span data-ttu-id="22a86-508">nx_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="22a86-508">nx_http_client_put_packet</span></span>

<span data-ttu-id="22a86-509">Отправка следующего пакета данных ресурса</span><span class="sxs-lookup"><span data-stu-id="22a86-509">Send next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-510">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-510">Prototype</span></span>

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                               NX_PACKET *packet_ptr,
                               ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="22a86-511">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-511">Description</span></span>

<span data-ttu-id="22a86-512">Эта служба пытается отправить следующий пакет содержимого ресурса на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="22a86-512">This service attempts to send the next packet of resource content to the HTTP Server.</span></span>

> [!NOTE]
> <span data-ttu-id="22a86-513">Эту подпрограмму следует вызывать несколько раз до тех пор, пока суммарная длина отправляемых пакетов не будет равна значению total_bytes, указанному в предыдущем вызове *nx_http_client_put_start()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-513">This routine should be called repetitively until the combined length of the packets sent equals the “total_bytes” specified in the previous *nx_http_client_put_start* call.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-514">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-514">Input Parameters</span></span>

 - <span data-ttu-id="22a86-515">**client_ptr** — указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="22a86-515">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="22a86-516">**packet_ptr** — указатель на следующее содержимое ресурса, отправляемого на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="22a86-516">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
 - <span data-ttu-id="22a86-517">**wait_option** — определяет, как долго служба будет внутренне ожидать обработки пакета PUT HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-517">**wait_option** Defines how long the service will wait internally to process the HTTP Client PUT packet.</span></span> <span data-ttu-id="22a86-518">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="22a86-518">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="22a86-519">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="22a86-519">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
    - <span data-ttu-id="22a86-520">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="22a86-520">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>

    <span data-ttu-id="22a86-521">Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="22a86-521">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

    <span data-ttu-id="22a86-522">Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-522">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-523">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-523">Return Values</span></span>

 - <span data-ttu-id="22a86-524">**NX_SUCCESS** (0x00) — пакет HTTP-клиента успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="22a86-524">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
 - <span data-ttu-id="22a86-525">**NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="22a86-525">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
 - <span data-ttu-id="22a86-526">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) — получен код ошибки сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-526">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Received Server error code</span></span>
 - <span data-ttu-id="22a86-527">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) — недопустимая длина пакета.</span><span class="sxs-lookup"><span data-stu-id="22a86-527">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
 - <span data-ttu-id="22a86-528">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) — недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="22a86-528">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or Password</span></span>
 - <span data-ttu-id="22a86-529">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) — сервер отвечает до завершения запроса PUT.</span><span class="sxs-lookup"><span data-stu-id="22a86-529">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Server responds before PUT Is complete</span></span>
 - <span data-ttu-id="22a86-530">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-530">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="22a86-531">NX_INVALID_PACKET (0x12) — слишком маленький пакет для заголовка TCP.</span><span class="sxs-lookup"><span data-stu-id="22a86-531">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
 - <span data-ttu-id="22a86-532">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="22a86-532">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-533">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-533">Allowed From</span></span>

<span data-ttu-id="22a86-534">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-534">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-535">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-535">Example</span></span>

```c
/* Send a 20-byte packet representing the content of the resource
   “/TEST.HTM” to the HTTP Server. */
status =  nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr, NX_PACKET *packet_ptr, ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
   successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a><span data-ttu-id="22a86-536">nx_http_client_set_connect_port</span><span class="sxs-lookup"><span data-stu-id="22a86-536">nx_http_client_set_connect_port</span></span>

<span data-ttu-id="22a86-537">Задание порта подключения к серверу</span><span class="sxs-lookup"><span data-stu-id="22a86-537">Set the connection port to the Server</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-538">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-538">Prototype</span></span>

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                      UINT port);
```

### <a name="description"></a><span data-ttu-id="22a86-539">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-539">Description</span></span>

<span data-ttu-id="22a86-540">При подключении к HTTP-серверу эта служба изменяет порт подключения на указанный порт во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="22a86-540">This service changes the connect port when connecting to the HTTP Server to the specified port at runtime.</span></span> <span data-ttu-id="22a86-541">В противном случае по умолчанию используется порт 80.</span><span class="sxs-lookup"><span data-stu-id="22a86-541">Otherwise the connect port defaults to 80.</span></span> <span data-ttu-id="22a86-542">Эту службу необходимо вызвать до *nx_http_client_get_start()* и *nx_http_client_put_start()* , например, когда HTTP-клиент подключается к серверу.</span><span class="sxs-lookup"><span data-stu-id="22a86-542">This must be called before *nx_http_client_get_start()* and *nx_http_client_put_start()* e.g. when the HTTP Client connects with the Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-543">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-543">Input Parameters</span></span>

 - <span data-ttu-id="22a86-544">**client_ptr** — указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="22a86-544">**client_ptr** Pointer to HTTP Client control block.</span></span>
 - <span data-ttu-id="22a86-545">**port** — порт для подключения к серверу.</span><span class="sxs-lookup"><span data-stu-id="22a86-545">**port** Port for connecting to the Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-546">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-546">Return Values</span></span>

 - <span data-ttu-id="22a86-547">Порт **NX_SUCCESS** (0X00) — порт успешно изменен.</span><span class="sxs-lookup"><span data-stu-id="22a86-547">**NX_SUCCESS** (0x00) Successfully change port</span></span>
 - <span data-ttu-id="22a86-548">NX_INVALID_PORT (0x46) — превышено максимальное значение номера порта (0xFFFF), или номер равен нулю.</span><span class="sxs-lookup"><span data-stu-id="22a86-548">NX_INVALID_PORT (0x46) Port exceeds the maximum (0xFFFF) or is zero</span></span>
 - <span data-ttu-id="22a86-549">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-549">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-550">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-550">Allowed From</span></span>

<span data-ttu-id="22a86-551">Потоки, инициализация</span><span class="sxs-lookup"><span data-stu-id="22a86-551">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="22a86-552">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-552">Example</span></span>

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status =  nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a><span data-ttu-id="22a86-553">nx_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="22a86-553">nx_http_server_cache_info_callback_set</span></span>

<span data-ttu-id="22a86-554">Задание обратного вызова для получения максимального возраста и даты URL-адреса</span><span class="sxs-lookup"><span data-stu-id="22a86-554">Set the callback to retrieve URL max age and date</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-555">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-555">Prototype</span></span>

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                         UINT (*cache_info_get)(CHAR *resource,
                                                 UINT *max_age,
                                                 NX_HTTP_SERVER_DATE
                                                      *date));
```

### <a name="description"></a><span data-ttu-id="22a86-556">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-556">Description</span></span>

<span data-ttu-id="22a86-557">Эта служба задает службу обратного вызова, вызываемую для получения максимального возраста и даты последнего изменения указанного ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-557">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-558">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-558">Input Parameters</span></span>

 - <span data-ttu-id="22a86-559">**server_ptr** — указатель на управляющий блок HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-559">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="22a86-560">**cache_info_get** — указатель на обратный вызов.</span><span class="sxs-lookup"><span data-stu-id="22a86-560">**cache_info_get** Pointer to the callback</span></span>
 - <span data-ttu-id="22a86-561">**max_age** — указатель на максимальный возраст ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-561">**max_age** Pointer to maximum age of a resource</span></span>
 - <span data-ttu-id="22a86-562">**data** — указатель на возвращенную дату последнего изменения.</span><span class="sxs-lookup"><span data-stu-id="22a86-562">**data** Pointer to last modified date returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-563">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-563">Return Values</span></span>

 - <span data-ttu-id="22a86-564">**NX_SUCCESS** (0x00) — обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="22a86-564">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="22a86-565">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-565">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-566">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-566">Allowed From</span></span>

<span data-ttu-id="22a86-567">Инициализация</span><span class="sxs-lookup"><span data-stu-id="22a86-567">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="22a86-568">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-568">Example</span></span>

```c
NX_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
                           NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP  
   server is set by nx_http_server_start(), set the cache info callback: */

status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);


/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a><span data-ttu-id="22a86-569">nx_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="22a86-569">nx_http_server_callback_data_send</span></span>

<span data-ttu-id="22a86-570">Отправка данных из функции обратного вызова</span><span class="sxs-lookup"><span data-stu-id="22a86-570">Send data from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-571">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-571">Prototype</span></span>

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                       VOID *data_ptr,
                                       ULONG data_length);
```

### <a name="description"></a><span data-ttu-id="22a86-572">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-572">Description</span></span>

<span data-ttu-id="22a86-573">Эта служба отправляет данные в предоставленном пакете из подпрограммы обратного вызова приложения.</span><span class="sxs-lookup"><span data-stu-id="22a86-573">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="22a86-574">Обычно она используется для отправки динамических данных, связанных с запросами GET/POST.</span><span class="sxs-lookup"><span data-stu-id="22a86-574">This is typically used to send dynamic data associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="22a86-575">Если используется эта функция, подпрограмма обратного вызова отвечает за отправку всего ответа в правильном формате.</span><span class="sxs-lookup"><span data-stu-id="22a86-575">If this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="22a86-576">Кроме того, подпрограмма обратного вызова должна возвращать состояние NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="22a86-576">In addition, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-577">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-577">Input Parameters</span></span>

 - <span data-ttu-id="22a86-578">**server_ptr** — указатель на управляющий блок HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-578">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="22a86-579">**data_ptr** — указатель на данные для отправки.</span><span class="sxs-lookup"><span data-stu-id="22a86-579">**data_ptr** Pointer to the data to send.</span></span>
 - <span data-ttu-id="22a86-580">**data_length** — число отправляемых байтов.</span><span class="sxs-lookup"><span data-stu-id="22a86-580">**data_length**  Number of bytes to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-581">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-581">Return Values</span></span>

 - <span data-ttu-id="22a86-582">**NX_SUCCESS** (0x00) — данные сервера успешно отправлены.</span><span class="sxs-lookup"><span data-stu-id="22a86-582">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
 - <span data-ttu-id="22a86-583">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-583">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-584">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-584">Allowed From</span></span>

<span data-ttu-id="22a86-585">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-585">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-586">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-586">Example</span></span>

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

## <a name="nx_http_server_callback_generate_response_header"></a><span data-ttu-id="22a86-587">nx_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="22a86-587">nx_http_server_callback_generate_response_header</span></span>

<span data-ttu-id="22a86-588">Создание заголовка ответа в функции обратного вызова</span><span class="sxs-lookup"><span data-stu-id="22a86-588">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-589">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-589">Prototype</span></span>

```c
UINT nx_http_server_callback_generate_response_header(
                        NX_HTTP_SERVER *server_ptr,
                        NX_PACKET **packet_pptr,
                        CHAR *status_code, UINT content_length,
                        CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a><span data-ttu-id="22a86-590">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-590">Description</span></span>

<span data-ttu-id="22a86-591">Эта служба вызывает внутреннюю функцию *_nx_http_server_generate_response_header*, когда HTTP-сервер отвечает на запросы GET, PUT и DELETE клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-591">This service calls the internal function *_nx_http_server_generate_response_header* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="22a86-592">Ее нужно использовать в функциях обратного вызова HTTP-сервера, когда приложение HTTP-сервера формирует ответ клиенту.</span><span class="sxs-lookup"><span data-stu-id="22a86-592">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="22a86-593">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="22a86-593">This service is deprecated.</span></span> <span data-ttu-id="22a86-594">Разработчикам рекомендуется перейти на использование *nxd_http_server_callback_generate_response_header_extended()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-594">Developers are encouraged to migrate to *nxd_http_server_callback_generate_response_header_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-595">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-595">Input Parameters</span></span>

 - <span data-ttu-id="22a86-596">**server_ptr** — указатель на управляющий блок HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-596">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="22a86-597">**packet_pptr** — указатель на указатель пакета, выделенный для сообщения.</span><span class="sxs-lookup"><span data-stu-id="22a86-597">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
 - <span data-ttu-id="22a86-598">**status_code** — указывает на состояние ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-598">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="22a86-599">Примеры:</span><span class="sxs-lookup"><span data-stu-id="22a86-599">Examples:</span></span>
    - <span data-ttu-id="22a86-600">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="22a86-600">**NX_HTTP_STATUS_OK**</span></span>
    - <span data-ttu-id="22a86-601">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="22a86-601">**NX_HTTP_STATUS_MODIFIED**</span></span>
    - <span data-ttu-id="22a86-602">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="22a86-602">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
 - <span data-ttu-id="22a86-603">**content_length** — размер содержимого в байтах.</span><span class="sxs-lookup"><span data-stu-id="22a86-603">**content_length** Size of content in bytes</span></span>
 - <span data-ttu-id="22a86-604">**content_type** — тип HTTP, например text/plain.</span><span class="sxs-lookup"><span data-stu-id="22a86-604">**content_type** Type of HTTP e.g. “text/plain”</span></span>
 - <span data-ttu-id="22a86-605">**additional_header** — указатель на дополнительный текст заголовка.</span><span class="sxs-lookup"><span data-stu-id="22a86-605">**additional_header** Pointer to additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-606">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-606">Return Values</span></span>

 - <span data-ttu-id="22a86-607">**NX_SUCCESS** (0x00) — заголовок успешно создан.</span><span class="sxs-lookup"><span data-stu-id="22a86-607">**NX_SUCCESS** (0x00) Successfully created header</span></span>
 - <span data-ttu-id="22a86-608">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-608">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-609">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-609">Allowed From</span></span>

<span data-ttu-id="22a86-610">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-610">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-611">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-611">Example</span></span>

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

## <a name="nx_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="22a86-612">nx_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="22a86-612">nx_http_server_callback_generate_response_header_extended</span></span>

<span data-ttu-id="22a86-613">Создание заголовка ответа в функции обратного вызова</span><span class="sxs-lookup"><span data-stu-id="22a86-613">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-614">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-614">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="22a86-615">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-615">Description</span></span>

<span data-ttu-id="22a86-616">Эта служба вызывает внутреннюю функцию *_nx_http_server_generate_response_header()* , когда HTTP-сервер отвечает на запросы GET, PUT и DELETE клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-616">This service calls the internal function *_nx_http_server_generate_response_header()* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="22a86-617">Ее нужно использовать в функциях обратного вызова HTTP-сервера, когда приложение HTTP-сервера формирует ответ клиенту.</span><span class="sxs-lookup"><span data-stu-id="22a86-617">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="22a86-618">Эта служба заменяет *nx_http_server_callback_generate_response_header()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-618">This service replaces *nx_http_server_callback_generate_response_header()*.</span></span> <span data-ttu-id="22a86-619">Эта версия предоставляет дополнительные сведения о длине функции обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="22a86-619">This version supplies additional length information to the callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-620">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-620">Input Parameters</span></span>

 - <span data-ttu-id="22a86-621">**server_ptr** — указатель на управляющий блок HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-621">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="22a86-622">**packet_pptr** — указатель на указатель пакета, выделенный для сообщения.</span><span class="sxs-lookup"><span data-stu-id="22a86-622">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
 - <span data-ttu-id="22a86-623">**status_code** — указывает на состояние ресурса.</span><span class="sxs-lookup"><span data-stu-id="22a86-623">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="22a86-624">Примеры:</span><span class="sxs-lookup"><span data-stu-id="22a86-624">Examples:</span></span>
    - <span data-ttu-id="22a86-625">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="22a86-625">**NX_HTTP_STATUS_OK**</span></span>
    - <span data-ttu-id="22a86-626">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="22a86-626">**NX_HTTP_STATUS_MODIFIED**</span></span>
    - <span data-ttu-id="22a86-627">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="22a86-627">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
 - <span data-ttu-id="22a86-628">**status_code** — длина кода состояния.</span><span class="sxs-lookup"><span data-stu-id="22a86-628">**status_code** Length of status code</span></span>
 - <span data-ttu-id="22a86-629">**content_length** — размер содержимого в байтах.</span><span class="sxs-lookup"><span data-stu-id="22a86-629">**content_length** Size of content in bytes</span></span>
 - <span data-ttu-id="22a86-630">**content_type** — тип HTTP, например text/plain.</span><span class="sxs-lookup"><span data-stu-id="22a86-630">**content_type** Type of HTTP e.g. “text/plain”</span></span>
 - <span data-ttu-id="22a86-631">**content_type_length** — длина типа HTTP.</span><span class="sxs-lookup"><span data-stu-id="22a86-631">**content_type_length** Length of HTTP type</span></span>
 - <span data-ttu-id="22a86-632">**additional_header** — указатель на дополнительный текст заголовка.</span><span class="sxs-lookup"><span data-stu-id="22a86-632">**additional_header** Pointer to additional header text</span></span>
 - <span data-ttu-id="22a86-633">**additional_header_length** — длина дополнительного текста заголовка.</span><span class="sxs-lookup"><span data-stu-id="22a86-633">**additional_header_length** Length of additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-634">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-634">Return Values</span></span>

 - <span data-ttu-id="22a86-635">**NX_SUCCESS** (0x00) — заголовок успешно создан.</span><span class="sxs-lookup"><span data-stu-id="22a86-635">**NX_SUCCESS** (0x00) Successfully created header</span></span>
 - <span data-ttu-id="22a86-636">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-636">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-637">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-637">Allowed From</span></span>

<span data-ttu-id="22a86-638">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-638">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-639">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-639">Example</span></span>

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

## <a name="nx_http_server_callback_packet_send"></a><span data-ttu-id="22a86-640">nx_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="22a86-640">nx_http_server_callback_packet_send</span></span>

<span data-ttu-id="22a86-641">Отправка пакета HTTP из функции обратного вызова</span><span class="sxs-lookup"><span data-stu-id="22a86-641">Send an HTTP packet from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-642">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-642">Prototype</span></span>

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="22a86-643">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-643">Description</span></span>

<span data-ttu-id="22a86-644">Эта служба отправляет полный ответ HTTP-сервера из обратного вызова HTTP.</span><span class="sxs-lookup"><span data-stu-id="22a86-644">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="22a86-645">HTTP-сервер отправит пакет с NX_HTTP_SERVER_TIMEOUT_SEND.</span><span class="sxs-lookup"><span data-stu-id="22a86-645">HTTP server will send the packet with the NX_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="22a86-646">К пакету должны быть добавлены заголовок и данные HTTP.</span><span class="sxs-lookup"><span data-stu-id="22a86-646">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="22a86-647">Если возвращаемое состояние указывает на ошибку, приложение HTTP должно освободить пакет.</span><span class="sxs-lookup"><span data-stu-id="22a86-647">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="22a86-648">Обратный вызов должен возвращать NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="22a86-648">The callback should return NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="22a86-649">Более подробный пример см. в описании *nx_http_server_callback_generate_response_header()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-649">See *nx_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-650">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-650">Input Parameters</span></span>

 - <span data-ttu-id="22a86-651">**server_ptr** — указатель на управляющий блок HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-651">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="22a86-652">**packet_ptr** — указатель на пакет для отправки.</span><span class="sxs-lookup"><span data-stu-id="22a86-652">**packet_ptr** Pointer to the packet to send</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-653">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-653">Return Values</span></span>

 - <span data-ttu-id="22a86-654">**NX_SUCCESS** (0x00) — пакет сервера успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="22a86-654">**NX_SUCCESS** (0x00) Successfully sent Server packet</span></span>
 - <span data-ttu-id="22a86-655">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-655">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-656">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-656">Allowed From</span></span>

<span data-ttu-id="22a86-657">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-657">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-658">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-658">Example</span></span>

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

## <a name="nx_http_server_callback_response_send"></a><span data-ttu-id="22a86-659">nx_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="22a86-659">nx_http_server_callback_response_send</span></span>

<span data-ttu-id="22a86-660">Отправка ответа из функции обратного вызова</span><span class="sxs-lookup"><span data-stu-id="22a86-660">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-661">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-661">Prototype</span></span>

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
                                           CHAR *header,
                                           CHAR *information,
                                           CHAR additional_info);
```

### <a name="description"></a><span data-ttu-id="22a86-662">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-662">Description</span></span>

<span data-ttu-id="22a86-663">Эта служба отправляет указанные сведения об ответе из подпрограммы обратного вызова приложения.</span><span class="sxs-lookup"><span data-stu-id="22a86-663">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="22a86-664">Обычно она используется для отправки пользовательских ответов, связанных с запросами GET/POST.</span><span class="sxs-lookup"><span data-stu-id="22a86-664">This is typically used to send custom responses associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="22a86-665">Если используется эта функция, подпрограмма обратного вызова должна возвращать состояние NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="22a86-665">If this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="22a86-666">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="22a86-666">This service is deprecated.</span></span> <span data-ttu-id="22a86-667">Разработчикам рекомендуется перейти на использование *nxd_http_server_callback_response_send_extended()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-667">Developers are encouraged to migrate to *nxd_http_server_callback_response_send_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-668">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-668">Input Parameters</span></span>

 - <span data-ttu-id="22a86-669">**server_ptr** — указатель на управляющий блок HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-669">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="22a86-670">**header** — указатель на строку заголовка ответа.</span><span class="sxs-lookup"><span data-stu-id="22a86-670">**header** Pointer to the response header string.</span></span>
 - <span data-ttu-id="22a86-671">**information** — указатель на строку информации.</span><span class="sxs-lookup"><span data-stu-id="22a86-671">**information** Pointer to the information string.</span></span>
 - <span data-ttu-id="22a86-672">**additional_info** — указатель на строку дополнительной информации.</span><span class="sxs-lookup"><span data-stu-id="22a86-672">**additional_info** Pointer to the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-673">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-673">Return Values</span></span>

 - <span data-ttu-id="22a86-674">**NX_SUCCESS** (0x00) — ответ сервера успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="22a86-674">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-675">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-675">Allowed From</span></span>

<span data-ttu-id="22a86-676">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-676">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-677">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-677">Example</span></span>

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

## <a name="nx_http_server_callback_response_send_extended"></a><span data-ttu-id="22a86-678">nx_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="22a86-678">nx_http_server_callback_response_send_extended</span></span>

<span data-ttu-id="22a86-679">Отправка ответа из функции обратного вызова</span><span class="sxs-lookup"><span data-stu-id="22a86-679">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-680">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-680">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="22a86-681">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-681">Description</span></span>

<span data-ttu-id="22a86-682">Эта служба отправляет указанные сведения об ответе из подпрограммы обратного вызова приложения.</span><span class="sxs-lookup"><span data-stu-id="22a86-682">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="22a86-683">Обычно она используется для отправки пользовательских ответов, связанных с запросами GET/POST.</span><span class="sxs-lookup"><span data-stu-id="22a86-683">This is typically used to send custom responses associated with GET/POST requests.</span></span>

> [!NOTE]
> <span data-ttu-id="22a86-684">Если используется эта функция, подпрограмма обратного вызова должна возвращать состояние NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="22a86-684">If this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="22a86-685">Эта служба заменяет *nx_http_server_callback_response_send()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-685">This service replaces *nx_http_server_callback_response_send()*.</span></span> <span data-ttu-id="22a86-686">Эта версия принимает дополнительные сведения о длине в качестве аргументов.</span><span class="sxs-lookup"><span data-stu-id="22a86-686">This version takes additional length information as arguments.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-687">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-687">Input Parameters</span></span>

 - <span data-ttu-id="22a86-688">**server_ptr** — указатель на управляющий блок HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-688">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="22a86-689">**header** — указатель на строку заголовка ответа.</span><span class="sxs-lookup"><span data-stu-id="22a86-689">**header** Pointer to the response header string.</span></span>
 - <span data-ttu-id="22a86-690">**header_length** — длина строки заголовка ответа.</span><span class="sxs-lookup"><span data-stu-id="22a86-690">**header_length** Length of the response header string.</span></span>
 - <span data-ttu-id="22a86-691">**information** — указатель на строку информации.</span><span class="sxs-lookup"><span data-stu-id="22a86-691">**information** Pointer to the information string.</span></span>
 - <span data-ttu-id="22a86-692">**information_length** — длина строки информации.</span><span class="sxs-lookup"><span data-stu-id="22a86-692">**information_length** Length of the information string.</span></span>
 - <span data-ttu-id="22a86-693">**additional_info** — указатель на строку дополнительной информации.</span><span class="sxs-lookup"><span data-stu-id="22a86-693">**additional_info** Pointer to the additional information string.</span></span>
 - <span data-ttu-id="22a86-694">**additional_info_length** — длина строки дополнительной информации.</span><span class="sxs-lookup"><span data-stu-id="22a86-694">**additional_info_length** Length of the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-695">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-695">Return Values</span></span>

 - <span data-ttu-id="22a86-696">**NX_SUCCESS** (0x00) — ответ сервера успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="22a86-696">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-697">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-697">Allowed From</span></span>

<span data-ttu-id="22a86-698">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-698">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-699">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-699">Example</span></span>

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

## <a name="nx_http_server_content_get"></a><span data-ttu-id="22a86-700">nx_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="22a86-700">nx_http_server_content_get</span></span>

<span data-ttu-id="22a86-701">Получение содержимого из запроса</span><span class="sxs-lookup"><span data-stu-id="22a86-701">Get content from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-702">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-702">Prototype</span></span>

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="22a86-703">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-703">Description</span></span>

<span data-ttu-id="22a86-704">Эта служба пытается получить указанный объем содержимого из запроса POST или PUT HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-704">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="22a86-705">Ее следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_http_server_create*).</span><span class="sxs-lookup"><span data-stu-id="22a86-705">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

<span data-ttu-id="22a86-706">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="22a86-706">This service is deprecated.</span></span> <span data-ttu-id="22a86-707">Разработчикам рекомендуется перейти на использование *nx_http_server_content_get_extended()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-707">Developers are encouraged to migrate to *nx_http_server_content_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-708">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-708">Input Parameters</span></span>

 - <span data-ttu-id="22a86-709">**server_ptr** — указатель на управляющий блок HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-709">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="22a86-710">**packet_ptr** — указатель на пакет запроса HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-710">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="22a86-711">Обратите внимание, что этот пакет не должен быть освобожден обратным вызовом уведомления о запросе.</span><span class="sxs-lookup"><span data-stu-id="22a86-711">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="22a86-712">**byte_offset** — число байтов для смещения в область содержимого.</span><span class="sxs-lookup"><span data-stu-id="22a86-712">**byte_offset** Number of bytes to offset into the content area.</span></span>
 - <span data-ttu-id="22a86-713">**destination_ptr** — указатель на область назначения для содержимого.</span><span class="sxs-lookup"><span data-stu-id="22a86-713">**destination_ptr** Pointer to the destination area for the content.</span></span>
 - <span data-ttu-id="22a86-714">**destination_size** — максимальное число байтов, доступных в области назначения.</span><span class="sxs-lookup"><span data-stu-id="22a86-714">**destination_size** Maximum number of bytes available in the destination area.</span></span>
 - <span data-ttu-id="22a86-715">**actual_size** — указатель на переменную назначения, в качестве значения которой будет задан фактический размер копируемого содержимого.</span><span class="sxs-lookup"><span data-stu-id="22a86-715">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-716">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-716">Return Values</span></span>

 - <span data-ttu-id="22a86-717">**NX_SUCCESS** (0x00) — содержимое HTTP-сервера успешно получено.</span><span class="sxs-lookup"><span data-stu-id="22a86-717">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
 - <span data-ttu-id="22a86-718">**NX_HTTP_ERROR** (0xE0) — внутренняя ошибка HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-718">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
 - <span data-ttu-id="22a86-719">**NX_HTTP_DATA_END** (0xE7) — конец содержимого запроса.</span><span class="sxs-lookup"><span data-stu-id="22a86-719">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
 - <span data-ttu-id="22a86-720">**NX_HTTP_TIMEOUT** (0xE1) — время ожидания HTTP-сервера в получении следующего пакета содержимого.</span><span class="sxs-lookup"><span data-stu-id="22a86-720">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet of content</span></span>
 - <span data-ttu-id="22a86-721">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-721">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="22a86-722">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="22a86-722">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-723">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-723">Allowed From</span></span>

<span data-ttu-id="22a86-724">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-724">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-725">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-725">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get(&my_server, packet_ptr,
                      0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_get_extended"></a><span data-ttu-id="22a86-726">nx_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="22a86-726">nx_http_server_content_get_extended</span></span>

<span data-ttu-id="22a86-727">Получение содержимого из запроса или поддержка содержимого нулевой длины</span><span class="sxs-lookup"><span data-stu-id="22a86-727">Get content from the request/supports zero length Content Length</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-728">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-728">Prototype</span></span>

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                         NX_PACKET *packet_ptr,
                                         ULONG byte_offset,
                                         CHAR *destination_ptr,
                                         UINT destination_size,
                                         UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="22a86-729">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-729">Description</span></span>

<span data-ttu-id="22a86-730">Эта служба почти идентична службе *nx_http_server_content_get()* . Она пытается получить указанный объем содержимого из запроса POST или PUT HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-730">This service is almost identical to *nx_http_server_content_get();* it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="22a86-731">Однако она обрабатывает запросы с содержимым нулевой длины (пустые запросы) как допустимые.</span><span class="sxs-lookup"><span data-stu-id="22a86-731">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="22a86-732">Ее следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="22a86-732">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="22a86-733">Эта служба заменяет *nx_http_server_content_get()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-733">This service replaces *nx_http_server_content_get()*.</span></span> <span data-ttu-id="22a86-734">Эта версия требует, чтобы вызывающий объект указал дополнительные сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="22a86-734">This version requires caller to supply additional length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-735">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-735">Input Parameters</span></span>

 - <span data-ttu-id="22a86-736">**server_ptr** — указатель на управляющий блок HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-736">**server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="22a86-737">**packet_ptr** — указатель на пакет запроса HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-737">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="22a86-738">Обратите внимание, что этот пакет не должен быть освобожден обратным вызовом уведомления о запросе.</span><span class="sxs-lookup"><span data-stu-id="22a86-738">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="22a86-739">**byte_offset** — число байтов для смещения в область содержимого.</span><span class="sxs-lookup"><span data-stu-id="22a86-739">**byte_offset** Number of bytes to offset into the content area.</span></span>
 - <span data-ttu-id="22a86-740">**destination_ptr** — указатель на область назначения для содержимого.</span><span class="sxs-lookup"><span data-stu-id="22a86-740">**destination_ptr** Pointer to the destination area for the content.</span></span>
 - <span data-ttu-id="22a86-741">**destination_size** — максимальное число байтов, доступных в области назначения.</span><span class="sxs-lookup"><span data-stu-id="22a86-741">**destination_size** Maximum number of bytes available in the destination area.</span></span>
 - <span data-ttu-id="22a86-742">**actual_size** — указатель на переменную назначения, в качестве значения которой будет задан фактический размер копируемого содержимого.</span><span class="sxs-lookup"><span data-stu-id="22a86-742">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-743">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-743">Return Values</span></span>

 - <span data-ttu-id="22a86-744">**NX_SUCCESS** (0x00) — содержимое HTTP-запроса успешно получено.</span><span class="sxs-lookup"><span data-stu-id="22a86-744">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
 - <span data-ttu-id="22a86-745">**NX_HTTP_ERROR** (0xE0) — внутренняя ошибка HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-745">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
 - <span data-ttu-id="22a86-746">**NX_HTTP_DATA_END** (0xE7) — конец содержимого запроса.</span><span class="sxs-lookup"><span data-stu-id="22a86-746">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
 - <span data-ttu-id="22a86-747">**NX_HTTP_TIMEOUT** (0xE1) — время ожидания HTTP-сервера в получении следующего пакета.</span><span class="sxs-lookup"><span data-stu-id="22a86-747">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet</span></span>
 - <span data-ttu-id="22a86-748">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-748">NX_PTR_ERROR (0x07) Invalid  pointer input</span></span>
 - <span data-ttu-id="22a86-749">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="22a86-749">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-750">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-750">Allowed From</span></span>

<span data-ttu-id="22a86-751">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-751">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-752">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-752">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, retrieve up to 100 bytes of content starting at offset
   0. */
status =  nx_http_server_content_get_extended(&my_server, packet_ptr,
                               0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
   request content. */
```

## <a name="nx_http_server_content_length_get"></a><span data-ttu-id="22a86-753">nx_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="22a86-753">nx_http_server_content_length_get</span></span>

<span data-ttu-id="22a86-754">Получение длины содержимого в запросе</span><span class="sxs-lookup"><span data-stu-id="22a86-754">Get length of content in the request</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-755">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-755">Prototype</span></span>

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="22a86-756">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-756">Description</span></span>

<span data-ttu-id="22a86-757">Эта служба пытается получить длину содержимого HTTP в указанном пакете.</span><span class="sxs-lookup"><span data-stu-id="22a86-757">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="22a86-758">Если содержимое HTTP отсутствует, эта подпрограмма возвращает нулевое значение.</span><span class="sxs-lookup"><span data-stu-id="22a86-758">If there is no HTTP content, this routine returns a value of zero.</span></span> <span data-ttu-id="22a86-759">Ее следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="22a86-759">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="22a86-760">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="22a86-760">This service is deprecated.</span></span> <span data-ttu-id="22a86-761">Разработчикам рекомендуется перейти на использование *nx_http_server_content_length_get_extended()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-761">Developers are encouraged to migrate to *nx_http_server_content_length_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-762">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-762">Input Parameters</span></span>

 - <span data-ttu-id="22a86-763">**packet_ptr** — указатель на пакет запроса HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-763">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="22a86-764">Обратите внимание, что этот пакет не должен быть освобожден обратным вызовом уведомления о запросе.</span><span class="sxs-lookup"><span data-stu-id="22a86-764">Note that this packet must not be released by the request notify callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-765">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-765">Return Values</span></span>

 - <span data-ttu-id="22a86-766">**content_length** — при возникновении ошибки возвращается нулевое значение.</span><span class="sxs-lookup"><span data-stu-id="22a86-766">**content length** On error, a value of zero is returned</span></span>  

### <a name="allowed-from"></a><span data-ttu-id="22a86-767">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-767">Allowed From</span></span>

<span data-ttu-id="22a86-768">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-768">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-769">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-769">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
length =  nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
   request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a><span data-ttu-id="22a86-770">nx_http_server_content_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="22a86-770">nx_http_server_content_length_get_extended</span></span>

<span data-ttu-id="22a86-771">Получение длины содержимого в запросе или поддержка содержимого нулевой длины</span><span class="sxs-lookup"><span data-stu-id="22a86-771">Get length of content in the request/supports Content Length of zero value</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-772">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-772">Prototype</span></span>

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                                UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="22a86-773">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-773">Description</span></span>

<span data-ttu-id="22a86-774">Эта служба аналогична службе *nx_http_server_content_length_get;* . Она пытается получить длину содержимого HTTP в указанном пакете.</span><span class="sxs-lookup"><span data-stu-id="22a86-774">This service is similar to *nx_http_server_content_length_get;* attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="22a86-775">Однако возвращаемое значение указывает на состояние успешного завершения, а фактическое значение длины возвращается в параметре```content_length``` входного указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-775">However, the return value indicates successful completion status, and the actual length value is returned in the input pointer ```content_length```.</span></span> <span data-ttu-id="22a86-776">Если содержимого HTTP нет или длина содержимого равна нулю, эта подпрограмма по-прежнему возвращает состояние выполнения, а указатель ввода content_length указывает на допустимую длину (ноль).</span><span class="sxs-lookup"><span data-stu-id="22a86-776">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="22a86-777">Ее следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_http_server_create*).</span><span class="sxs-lookup"><span data-stu-id="22a86-777">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

<span data-ttu-id="22a86-778">Эта служба заменяет *nx_http_server_content_length_get()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-778">This service replaces *nx_http_server_content_length_get()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-779">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-779">Input Parameters</span></span>

 - <span data-ttu-id="22a86-780">**packet_ptr** — указатель на пакет запроса HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-780">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="22a86-781">Обратите внимание, что этот пакет не должен быть освобожден обратным вызовом уведомления о запросе.</span><span class="sxs-lookup"><span data-stu-id="22a86-781">Note that this packet must not be released by the request notify callback.</span></span>
 - <span data-ttu-id="22a86-782">**content_length** — указатель на значение, полученное из поля длины содержимого.</span><span class="sxs-lookup"><span data-stu-id="22a86-782">**content_length** Pointer to value retrieved from Content Length field</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-783">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-783">Return Values</span></span>

 - <span data-ttu-id="22a86-784">**NX_SUCCESS** (0x00) — содержимое сервера успешно получено.</span><span class="sxs-lookup"><span data-stu-id="22a86-784">**NX_SUCCESS** (0x00) Successful Server content get</span></span>
 - <span data-ttu-id="22a86-785">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) — недопустимый формат заголовка HTTP.</span><span class="sxs-lookup"><span data-stu-id="22a86-785">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Improper HTTP header format</span></span>
 - <span data-ttu-id="22a86-786">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-786">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-787">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-787">Allowed From</span></span>

<span data-ttu-id="22a86-788">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-788">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-789">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-789">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the content length of the HTTP Client request. */
ULONG content_length;

status =  nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
   contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a><span data-ttu-id="22a86-790">nx_http_server_create</span><span class="sxs-lookup"><span data-stu-id="22a86-790">nx_http_server_create</span></span>

<span data-ttu-id="22a86-791">Создание экземпляра HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="22a86-791">Create an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-792">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-792">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="22a86-793">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-793">Description</span></span>

<span data-ttu-id="22a86-794">Эта служба создает экземпляр HTTP-сервера, который выполняется в контексте собственного потока ThreadX.</span><span class="sxs-lookup"><span data-stu-id="22a86-794">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="22a86-795">Необязательные подпрограммы обратного вызова приложений *authentication_check* и request_notify позволяют программному обеспечению приложения управлять основными операциями HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-795">The optional *authentication_check* and request_notify application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-796">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-796">Input Parameters</span></span>

 - <span data-ttu-id="22a86-797">**http_server_ptr** — указатель на управляющий блок HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-797">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
 - <span data-ttu-id="22a86-798">**http_server_name** — указатель на имя HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-798">**http_server_name** Pointer to HTTP Server’s name.</span></span>
 - <span data-ttu-id="22a86-799">**ip_ptr** — указатель на ранее созданный IP-экземпляр.</span><span class="sxs-lookup"><span data-stu-id="22a86-799">**ip_ptr** Pointer to previously created IP instance.</span></span>
 - <span data-ttu-id="22a86-800">**media_ptr** — указатель на ранее созданный экземпляр носителя FileX.</span><span class="sxs-lookup"><span data-stu-id="22a86-800">**media_ptr** Pointer to previously created FileX media instance.</span></span>
 - <span data-ttu-id="22a86-801">**stack_ptr** — указатель на область стека потока HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-801">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
 - <span data-ttu-id="22a86-802">**stack_size** — указатель на размер стека потока HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-802">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
 - <span data-ttu-id="22a86-803">**authentication_check** — указатель функции на подпрограмму проверки подлинности приложения.</span><span class="sxs-lookup"><span data-stu-id="22a86-803">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="22a86-804">Если параметр указан, эта подпрограмма вызывается для каждого запроса HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-804">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="22a86-805">Если этот параметр имеет значение NULL, проверка подлинности выполняться не будет.</span><span class="sxs-lookup"><span data-stu-id="22a86-805">If this parameter is NULL, no authentication will be performed.</span></span>
 - <span data-ttu-id="22a86-806">**request_notify** — указатель функции на подпрограмму уведомления о запросе приложения.</span><span class="sxs-lookup"><span data-stu-id="22a86-806">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="22a86-807">Если параметр указан, подпрограмма вызывается перед обработкой запроса HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="22a86-807">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="22a86-808">Это позволяет перенаправлять имя ресурса или обновлять поля в самом ресурсе до завершения запроса HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-808">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-809">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-809">Return Values</span></span>

 - <span data-ttu-id="22a86-810">**NX_SUCCESS** (0x00) — HTTP-сервер успешно создан.</span><span class="sxs-lookup"><span data-stu-id="22a86-810">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
 - <span data-ttu-id="22a86-811">NX_PTR_ERROR (0x07) — недопустимый указатель на HTTP-сервер, IP-адрес, носитель, стек или пул пакетов.</span><span class="sxs-lookup"><span data-stu-id="22a86-811">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
 - <span data-ttu-id="22a86-812">NX_HTTP_POOL_ERROR (0xE9) — полезные данные пакета пула недостаточно велики, чтобы содержать полный HTTP-запрос.</span><span class="sxs-lookup"><span data-stu-id="22a86-812">NX_HTTP_POOL_ERROR (0xE9) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-813">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-813">Allowed From</span></span>

<span data-ttu-id="22a86-814">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-814">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-815">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-815">Example</span></span>

```c
/* Create an HTTP Server instance called “my_server.”  */
status =  nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
              stack_ptr, stack_size, &pool_0,
              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a><span data-ttu-id="22a86-816">nx_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="22a86-816">nx_http_server_delete</span></span>

<span data-ttu-id="22a86-817">Удаление экземпляра HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="22a86-817">Delete an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-818">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-818">Prototype</span></span>

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="22a86-819">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-819">Description</span></span>

<span data-ttu-id="22a86-820">Эта служба удаляет ранее созданный экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-820">This service deletes a previously created HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-821">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-821">Input Parameters</span></span>

 - <span data-ttu-id="22a86-822">**http_server_ptr** — указатель на управляющий блок HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-822">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-823">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-823">Return Values</span></span>

 - <span data-ttu-id="22a86-824">**NX_SUCCESS** (0x00) — HTTP-сервер успешно удален.</span><span class="sxs-lookup"><span data-stu-id="22a86-824">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
 - <span data-ttu-id="22a86-825">NX_PTR_ERROR (0x07) — недопустимый указатель на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="22a86-825">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
 - <span data-ttu-id="22a86-826">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="22a86-826">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-827">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-827">Allowed From</span></span>

<span data-ttu-id="22a86-828">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-828">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-829">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-829">Example</span></span>

```c
/* Delete the HTTP Server instance called “my_server.”  */
status =  nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a><span data-ttu-id="22a86-830">nx_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="22a86-830">nx_http_server_get_entity_content</span></span>

<span data-ttu-id="22a86-831">Получение расположения и длины данных сущности</span><span class="sxs-lookup"><span data-stu-id="22a86-831">Retrieve the location and length of entity data</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-832">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-832">Prototype</span></span>

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_pptr,
                                       ULONG *available_offset,
                                       ULONG *available_length);
```

### <a name="description"></a><span data-ttu-id="22a86-833">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-833">Description</span></span>

<span data-ttu-id="22a86-834">Эта служба определяет расположение начала данных в текущем составном объекте в полученных сообщениях клиента, а также длину данных, не включая граничную строку.</span><span class="sxs-lookup"><span data-stu-id="22a86-834">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="22a86-835">HTTP-сервер внутренне обновляет собственные смещения, чтобы эту функцию можно было повторно вызывать в той же клиентской датаграмме для сообщений с несколькими сущностями.</span><span class="sxs-lookup"><span data-stu-id="22a86-835">Internally HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="22a86-836">Указатель пакета обновляется до следующего пакета, где сообщение клиента является датаграммой с несколькими пакетами.</span><span class="sxs-lookup"><span data-stu-id="22a86-836">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

> [!NOTE]
> <span data-ttu-id="22a86-837">Для использования этой службы необходимо включить NX_HTTP_MULTIPART_ENABLE.</span><span class="sxs-lookup"><span data-stu-id="22a86-837">NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="22a86-838">Дополнительные сведения см. в описании [*nx_http_server_get_entity_header*](#nx_http_server_get_entity_header).</span><span class="sxs-lookup"><span data-stu-id="22a86-838">See [*nx_http_server_get_entity_header*](#nx_http_server_get_entity_header) for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-839">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-839">Input Parameters</span></span>

 - <span data-ttu-id="22a86-840">**server_ptr** — указатель на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="22a86-840">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="22a86-841">**packet_pptr** — указатель на расположение указателя пакета.</span><span class="sxs-lookup"><span data-stu-id="22a86-841">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="22a86-842">Обратите внимание, что приложение не должно освобождать этот пакет.</span><span class="sxs-lookup"><span data-stu-id="22a86-842">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="22a86-843">**available_offset** — указатель на смещение данных сущности от указателя начала пакета.</span><span class="sxs-lookup"><span data-stu-id="22a86-843">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
 - <span data-ttu-id="22a86-844">**available_length** — указатель на длину данных сущности.</span><span class="sxs-lookup"><span data-stu-id="22a86-844">**available_length** Pointer to length of entity data</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-845">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-845">Return Values</span></span>

 - <span data-ttu-id="22a86-846">**NX_SUCCESS** (0x00) — размер и расположение содержимого сущности успешно получены.</span><span class="sxs-lookup"><span data-stu-id="22a86-846">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
 - <span data-ttu-id="22a86-847">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) — содержимое для внутренних многокомпонентных маркеров HTTP-сервера уже найдено.</span><span class="sxs-lookup"><span data-stu-id="22a86-847">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Content for the HTTP server  internal multipart markers is already found</span></span>
 - <span data-ttu-id="22a86-848">NX_HTTP_ERROR (0xE0) — внутренняя ошибка HTTP.</span><span class="sxs-lookup"><span data-stu-id="22a86-848">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>
 - <span data-ttu-id="22a86-849">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-849">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-850">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-850">Allowed From</span></span>

<span data-ttu-id="22a86-851">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-851">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-852">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-852">Example</span></span>

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

## <a name="nx_http_server_get_entity_header"></a><span data-ttu-id="22a86-853">nx_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="22a86-853">nx_http_server_get_entity_header</span></span>

<span data-ttu-id="22a86-854">Получение содержимого заголовка сущности</span><span class="sxs-lookup"><span data-stu-id="22a86-854">Retrieve the contents of entity header</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-855">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-855">Prototype</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      UCHAR *entity_header_buffer,
                                      ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="22a86-856">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-856">Description</span></span>

<span data-ttu-id="22a86-857">Эта служба извлекает заголовок сущности в указанный буфер.</span><span class="sxs-lookup"><span data-stu-id="22a86-857">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="22a86-858">HTTP-сервер внутренне обновляет собственные указатели для поиска следующей составной сущности в датаграмме клиента с несколькими заголовками сущностей.</span><span class="sxs-lookup"><span data-stu-id="22a86-858">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="22a86-859">Указатель пакета обновляется до следующего пакета, где сообщение клиента является датаграммой с несколькими пакетами.</span><span class="sxs-lookup"><span data-stu-id="22a86-859">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

> [!NOTE]
> <span data-ttu-id="22a86-860">Для использования этой службы необходимо включить NX_HTTP_MULTIPART_ENABLE.</span><span class="sxs-lookup"><span data-stu-id="22a86-860">NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-861">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-861">Input Parameters</span></span>

 - <span data-ttu-id="22a86-862">**server_ptr** — указатель на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="22a86-862">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="22a86-863">**packet_pptr** — указатель на расположение указателя пакета.</span><span class="sxs-lookup"><span data-stu-id="22a86-863">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="22a86-864">Обратите внимание, что приложение не должно освобождать этот пакет.</span><span class="sxs-lookup"><span data-stu-id="22a86-864">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="22a86-865">**entity_header_buffer** — указатель на расположение для хранения заголовка сущности.</span><span class="sxs-lookup"><span data-stu-id="22a86-865">**entity_header_buffer** Pointer to location to store entity header</span></span>
 - <span data-ttu-id="22a86-866">**buffer_size** — размер входного буфера.</span><span class="sxs-lookup"><span data-stu-id="22a86-866">**buffer_size** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-867">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-867">Return Values</span></span>

 - <span data-ttu-id="22a86-868">**NX_SUCCESS** (0x00) — заголовок сущности успешно получен.</span><span class="sxs-lookup"><span data-stu-id="22a86-868">**NX_SUCCESS** (0x00) Successfully retrieved entity heade</span></span>
 - <span data-ttu-id="22a86-869">**NX_HTTP_NOT_FOUND** **(0xE6)**  — поле заголовка сущности не найдено.</span><span class="sxs-lookup"><span data-stu-id="22a86-869">**NX_HTTP_NOT_FOUND** **(0xE6)** Entity header field not found</span></span>
 - <span data-ttu-id="22a86-870">**NX_HTTP_TIMEOUT** **(0xE1)**  — истекло время для получения следующего пакета для сообщения клиента с несколькими пакетами.</span><span class="sxs-lookup"><span data-stu-id="22a86-870">**NX_HTTP_TIMEOUT** **(0xE1)** Time expired to receive next packet for multipacket client message</span></span>
 - <span data-ttu-id="22a86-871">NX_HTTP_ERROR (0xE0) — внутренняя ошибка HTTP.</span><span class="sxs-lookup"><span data-stu-id="22a86-871">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>
 - <span data-ttu-id="22a86-872">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-872">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="22a86-873">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="22a86-873">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-874">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-874">Allowed From</span></span>

<span data-ttu-id="22a86-875">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-875">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-876">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-876">Example</span></span>

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

## <a name="nx_http_server_gmt_callback_set"></a><span data-ttu-id="22a86-877">nx_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="22a86-877">nx_http_server_gmt_callback_set</span></span>

<span data-ttu-id="22a86-878">Задание обратного вызова для получения даты и времени по Гринвичу</span><span class="sxs-lookup"><span data-stu-id="22a86-878">Set the callback to obtain GMT date and time</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-879">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-879">Prototype</span></span>

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

### <a name="description"></a><span data-ttu-id="22a86-880">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-880">Description</span></span>

<span data-ttu-id="22a86-881">Эта служба задает обратный вызов для получения даты и времени в формате GMT с помощью ранее созданного HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-881">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="22a86-882">Эта служба вызывается HTTP-сервером и создает заголовок в ответах HTTP-сервера для клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-882">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-883">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-883">Input Parameters</span></span>

 - <span data-ttu-id="22a86-884">**server_ptr** — указатель на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="22a86-884">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="22a86-885">**gmt_getv** — указатель на обратный вызов GMT.</span><span class="sxs-lookup"><span data-stu-id="22a86-885">**gmt_getv** Pointer to GMT callback</span></span>
 - <span data-ttu-id="22a86-886">**datev** — указатель на полученную дату.</span><span class="sxs-lookup"><span data-stu-id="22a86-886">**datev** Pointer to the date retrieved</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-887">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-887">Return Values</span></span>

 - <span data-ttu-id="22a86-888">**NX_SUCCESS** (0x00) — обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="22a86-888">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="22a86-889">NX_PTR_ERROR (0x07) — недопустимый указатель на пакет или параметр.</span><span class="sxs-lookup"><span data-stu-id="22a86-889">NX_PTR_ERROR (0x07)  Invalid packet or parameter pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-890">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-890">Allowed From</span></span>

<span data-ttu-id="22a86-891">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-891">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-892">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-892">Example</span></span>

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

## <a name="nx_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="22a86-893">nx_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="22a86-893">nx_http_server_invalid_userpassword_notify_set</span></span>

<span data-ttu-id="22a86-894">Задание обратного вызова для обработки недопустимого имени пользователя и пароля</span><span class="sxs-lookup"><span data-stu-id="22a86-894">Set the callback to to handle invalid user/password</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-895">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-895">Prototype</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set(
            NX_HTTP_SERVER *http_server_ptr,
            UINT (*invalid_username_password_callback)
                        (CHAR *resource,
                        NXD_ADDRESS *client_address,
                        UINT request_type));
```

### <a name="description"></a><span data-ttu-id="22a86-896">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-896">Description</span></span>

<span data-ttu-id="22a86-897">Эта служба задает обратный вызов, вызываемый при получении недопустимого имени пользователя и пароля в запросе GET, PUT или DELETE клиента в результате дайджест- или обычной проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-897">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="22a86-898">HTTP-сервер должен быть создан ранее.</span><span class="sxs-lookup"><span data-stu-id="22a86-898">The HTTP server must be previously created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-899">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-899">Input Parameters</span></span>

 - <span data-ttu-id="22a86-900">**server_ptr** — указатель на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="22a86-900">**server_ptr** Pointer to HTTP Server</span></span>
 - <span data-ttu-id="22a86-901">**invalid_username_password_callback** — указатель на недопустимый обратный вызов имени пользователя или пароля.</span><span class="sxs-lookup"><span data-stu-id="22a86-901">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
 - <span data-ttu-id="22a86-902">**resource** — указатель на ресурс, указанный клиентом.</span><span class="sxs-lookup"><span data-stu-id="22a86-902">**resource** Pointer to the resource specified by the client</span></span>
 - <span data-ttu-id="22a86-903">**client_address** — указатель на адрес клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-903">**client_address** Pointer to client address.</span></span> <span data-ttu-id="22a86-904">Разрешено использовать IPv4 или IPv6.</span><span class="sxs-lookup"><span data-stu-id="22a86-904">Can be IPv4 or IPv6</span></span>
 - <span data-ttu-id="22a86-905">**request_type** — указывает на тип запроса клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-905">**request_type** Indicates client request type.</span></span> <span data-ttu-id="22a86-906">Может иметь следующие значения:</span><span class="sxs-lookup"><span data-stu-id="22a86-906">May be:</span></span>
    - <span data-ttu-id="22a86-907">NX_HTTP_SERVER_GET_REQUEST</span><span class="sxs-lookup"><span data-stu-id="22a86-907">NX_HTTP_SERVER_GET_REQUEST</span></span>
    - <span data-ttu-id="22a86-908">NX_HTTP_SERVER_POST_REQUEST</span><span class="sxs-lookup"><span data-stu-id="22a86-908">NX_HTTP_SERVER_POST_REQUEST</span></span>
    - <span data-ttu-id="22a86-909">NX_HTTP_SERVER_HEAD_REQUEST</span><span class="sxs-lookup"><span data-stu-id="22a86-909">NX_HTTP_SERVER_HEAD_REQUEST</span></span>
    - <span data-ttu-id="22a86-910">NX_HTTP_SERVER_PUT_REQUEST</span><span class="sxs-lookup"><span data-stu-id="22a86-910">NX_HTTP_SERVER_PUT_REQUEST</span></span>
    - <span data-ttu-id="22a86-911">NX_HTTP_SERVER_DELETE_REQUEST</span><span class="sxs-lookup"><span data-stu-id="22a86-911">NX_HTTP_SERVER_DELETE_REQUEST</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-912">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-912">Return Values</span></span>

 - <span data-ttu-id="22a86-913">**NX_SUCCESS** (0x00) — обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="22a86-913">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="22a86-914">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-914">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-915">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-915">Allowed From</span></span>

<span data-ttu-id="22a86-916">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-916">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-917">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-917">Example</span></span>

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

## <a name="nx_http_server_mime_maps_additional_set"></a><span data-ttu-id="22a86-918">nx_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="22a86-918">nx_http_server_mime_maps_additional_set</span></span>

<span data-ttu-id="22a86-919">Задание дополнительных сопоставлений MIME для HTML</span><span class="sxs-lookup"><span data-stu-id="22a86-919">Set additional MIME maps for HTML</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-920">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-920">Prototype</span></span>

```c
UINT nx_http_server_mime_maps_additional_set(
                        NX_HTTP_SERVER *server_ptr,
                        NX_HTTP_SERVER_MIME_MAP *mime_maps,
                        UINT mime_maps_num);
```

### <a name="description"></a><span data-ttu-id="22a86-921">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-921">Description</span></span>

<span data-ttu-id="22a86-922">Эта служба позволяет разработчику приложений HTTP добавлять дополнительные типы MIME из типов MIME по умолчанию, предоставляемых HTTP-сервером NetX Duo (см. *nx_http_server_get_type*, чтобы получить сведения о списке определенных типов).</span><span class="sxs-lookup"><span data-stu-id="22a86-922">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by NetX Duo HTTP Server (see *nx_http_server_get_type* for list of defined types).</span></span>

<span data-ttu-id="22a86-923">Если получен запрос клиента, например запрос GET, HTTP-сервер анализирует запрошенный тип файла из заголовка HTTP с помощью дополнительно заданного сопоставления MIME и, если совпадений не найдено, ищет соответствие в сопоставлении MIME по умолчанию HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-923">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="22a86-924">Если совпадений не найдено, по умолчанию используется тип MIME text/plain.</span><span class="sxs-lookup"><span data-stu-id="22a86-924">If no match is found, the MIME type defaults to “text/plain”.</span></span>

<span data-ttu-id="22a86-925">Если функция уведомления о запросе зарегистрирована на HTTP-сервере, обратный вызов уведомления о запросе может вызвать *nx_http_server_type_retrieve()* для анализа типа файла.</span><span class="sxs-lookup"><span data-stu-id="22a86-925">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_http_server_type_retrieve()* to parse the file type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-926">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-926">Input Parameters</span></span>

 - <span data-ttu-id="22a86-927">**server_ptr** — указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-927">**server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="22a86-928">**mime_maps** — указатель на массив сопоставлений MIME.</span><span class="sxs-lookup"><span data-stu-id="22a86-928">**mime_maps** Pointer to a MIME map array</span></span>
 - <span data-ttu-id="22a86-929">**mime_map_num** — число сопоставлений MIME в массиве.</span><span class="sxs-lookup"><span data-stu-id="22a86-929">**mime_map_num** Number of MIME maps in array</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-930">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-930">Return Values</span></span>

 - <span data-ttu-id="22a86-931">**NX_SUCCESS** (0x00) — сопоставление MIME HTTP-сервера успешно задано.</span><span class="sxs-lookup"><span data-stu-id="22a86-931">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
 - <span data-ttu-id="22a86-932">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-932">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-933">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-933">Allowed From</span></span>

<span data-ttu-id="22a86-934">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-934">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-935">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-935">Example</span></span>

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

## <a name="nx_http_server_packet_content_find"></a><span data-ttu-id="22a86-936">nx_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="22a86-936">nx_http_server_packet_content_find</span></span>

<span data-ttu-id="22a86-937">Извлечение длины содержимого и установка указателя на начало данных</span><span class="sxs-lookup"><span data-stu-id="22a86-937">Extract content length and set pointer to start of data</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-938">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-938">Prototype</span></span>

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET **packet_ptr,
                                        UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="22a86-939">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-939">Description</span></span>

<span data-ttu-id="22a86-940">Эта служба извлекает длину содержимого из заголовка HTTP.</span><span class="sxs-lookup"><span data-stu-id="22a86-940">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="22a86-941">Она также обновляет указанный пакет следующим образом: перед указателем начала пакета (начало расположения буфера пакета для записи) задается содержимое HTTP (данные), только что переданное заголовком HTTP.</span><span class="sxs-lookup"><span data-stu-id="22a86-941">It also  updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="22a86-942">Если в текущем пакете не найдено начало содержимого, функция ожидает получения следующего пакета с помощью параметра ожидания NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="22a86-942">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

> [!NOTE]
> <span data-ttu-id="22a86-943">Этот параметр не следует вызывать перед вызовом *nx_http_server_get_entity_header*, поскольку он изменяет указатель в начале после заголовка сущности.</span><span class="sxs-lookup"><span data-stu-id="22a86-943">This should not be called before calling *nx_http_server_get_entity_header* because it modifies the prepend pointer past the entity header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-944">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-944">Input Parameters</span></span>

 - <span data-ttu-id="22a86-945">**server_ptr** — указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-945">**server_ptr** Pointer to HTTP server instance</span></span>
 - <span data-ttu-id="22a86-946">**packet_ptr** — указатель на указатель пакета для возврата пакета с обновленным указателем начала.</span><span class="sxs-lookup"><span data-stu-id="22a86-946">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
 - <span data-ttu-id="22a86-947">**content_length** — указатель на извлеченный параметр ```content_length```.</span><span class="sxs-lookup"><span data-stu-id="22a86-947">**content_length** Pointer to extracted ```content_length```</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-948">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-948">Return Values</span></span>

 - <span data-ttu-id="22a86-949">**NX_SUCCESS** (0x00) — длина содержимого HTTP обнаружена, и пакет успешно обновлен.</span><span class="sxs-lookup"><span data-stu-id="22a86-949">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
 - <span data-ttu-id="22a86-950">**NX_HTTP_TIMEOUT** (0xE1) — истекло время ожидания следующего пакета.</span><span class="sxs-lookup"><span data-stu-id="22a86-950">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
 - <span data-ttu-id="22a86-951">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-951">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-952">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-952">Allowed From</span></span>

<span data-ttu-id="22a86-953">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-953">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-954">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-954">Example</span></span>

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

## <a name="nx_http_server_packet_get"></a><span data-ttu-id="22a86-955">nx_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="22a86-955">nx_http_server_packet_get</span></span>

<span data-ttu-id="22a86-956">Получение следующего пакета HTTP</span><span class="sxs-lookup"><span data-stu-id="22a86-956">Receive the next HTTP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-957">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-957">Prototype</span></span>

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

### <a name="description"></a><span data-ttu-id="22a86-958">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-958">Description</span></span>

<span data-ttu-id="22a86-959">Эта служба возвращает следующий пакет, полученный через сокет HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-959">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="22a86-960">Для получения пакета используется параметр ожидания NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="22a86-960">The wait option to receive a packet is NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-961">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-961">Input Parameters</span></span>

 - <span data-ttu-id="22a86-962">**server_ptr** — указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-962">**server_ptr** Pointer to HTTP server instance</span></span>
 - <span data-ttu-id="22a86-963">**packet_ptr** — указатель на полученный пакет.</span><span class="sxs-lookup"><span data-stu-id="22a86-963">**packet_ptr** Pointer to received packet</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-964">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-964">Return Values</span></span>

 - <span data-ttu-id="22a86-965">**NX_SUCCESS** (0x00) — следующий пакет успешно получен.</span><span class="sxs-lookup"><span data-stu-id="22a86-965">**NX_SUCCESS** (0x00) Successfully received next packet</span></span>
 - <span data-ttu-id="22a86-966">**NX_HTTP_TIMEOUT** (0xE1) — истекло время ожидания следующего пакета.</span><span class="sxs-lookup"><span data-stu-id="22a86-966">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
 - <span data-ttu-id="22a86-967">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-967">NX_PTR_ERROR (0x07)  Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-968">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-968">Allowed From</span></span>

<span data-ttu-id="22a86-969">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-969">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-970">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-970">Example</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status =  nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a><span data-ttu-id="22a86-971">nx_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="22a86-971">nx_http_server_param_get</span></span>

<span data-ttu-id="22a86-972">Получение параметра из запроса</span><span class="sxs-lookup"><span data-stu-id="22a86-972">Get parameter from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-973">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-973">Prototype</span></span>

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                              UINT param_number, CHAR *param_ptr,
                              UINT max_param_size);
```

### <a name="description"></a><span data-ttu-id="22a86-974">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-974">Description</span></span>

<span data-ttu-id="22a86-975">Эта служба пытается получить указанный параметр URL-адреса HTTP в указанном пакете запроса.</span><span class="sxs-lookup"><span data-stu-id="22a86-975">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="22a86-976">Если запрашиваемый параметр HTTP отсутствует, подпрограмма возвращает состояние NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="22a86-976">If the requested HTTP parameter is not present,  this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="22a86-977">Эту подпрограмму следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_http_server_create*).</span><span class="sxs-lookup"><span data-stu-id="22a86-977">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-978">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-978">Input Parameters</span></span>

 - <span data-ttu-id="22a86-979">**packet_ptr** — указатель на пакет запроса HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-979">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="22a86-980">Обратите внимание, что приложение не должно освобождать этот пакет.</span><span class="sxs-lookup"><span data-stu-id="22a86-980">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="22a86-981">**param_number** — логический номер параметра, начинающийся с нуля, слева направо в списке параметров.</span><span class="sxs-lookup"><span data-stu-id="22a86-981">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
 - <span data-ttu-id="22a86-982">**param_ptr** — область назначения для копирования параметра.</span><span class="sxs-lookup"><span data-stu-id="22a86-982">**param_ptr** Destination area to copy the parameter.</span></span>
 - <span data-ttu-id="22a86-983">**max_param_size** — максимальный размер области назначения параметра.</span><span class="sxs-lookup"><span data-stu-id="22a86-983">**max_param_size** Maximum size of the parameter destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-984">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-984">Return Values</span></span>

 - <span data-ttu-id="22a86-985">**NX_SUCCESS** (0x00) — параметр HTTP-сервера успешно получен.</span><span class="sxs-lookup"><span data-stu-id="22a86-985">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
 - <span data-ttu-id="22a86-986">**NX_HTTP_NOT_FOUND** (0xE6) — указанный параметр не найден.</span><span class="sxs-lookup"><span data-stu-id="22a86-986">**NX_HTTP_NOT_FOUND** (0xE6) Specified parameter not found</span></span>
 - <span data-ttu-id="22a86-987">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) — неправильное завершение параметра запроса.</span><span class="sxs-lookup"><span data-stu-id="22a86-987">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Request parameter not properly terminated</span></span>
 - <span data-ttu-id="22a86-988">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-988">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="22a86-989">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="22a86-989">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-990">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-990">Allowed From</span></span>

<span data-ttu-id="22a86-991">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-991">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-992">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-992">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first parameter of the HTTP Client request. */

status =  nx_http_server_param_get(request_packet_ptr, 0, param_destination,
               30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
   in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a><span data-ttu-id="22a86-993">nx_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="22a86-993">nx_http_server_query_get</span></span>

<span data-ttu-id="22a86-994">Получение запроса из запроса</span><span class="sxs-lookup"><span data-stu-id="22a86-994">Get query from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-995">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-995">Prototype</span></span>

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                   CHAR *query_ptr, UINT max_query_size);
```

### <a name="description"></a><span data-ttu-id="22a86-996">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-996">Description</span></span>

<span data-ttu-id="22a86-997">Эта служба пытается получить указанный HTTP-запрос URL-адреса в указанном пакете запроса.</span><span class="sxs-lookup"><span data-stu-id="22a86-997">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="22a86-998">Если запрашиваемый HTTP-запрос отсутствует, подпрограмма возвращает состояние NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="22a86-998">If the requested HTTP query is not present,  this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="22a86-999">Эту подпрограмму следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_http_server_create*).</span><span class="sxs-lookup"><span data-stu-id="22a86-999">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-1000">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-1000">Input Parameters</span></span>

 - <span data-ttu-id="22a86-1001">**packet_ptr** — указатель на пакет запроса HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-1001">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="22a86-1002">Обратите внимание, что приложение не должно освобождать этот пакет.</span><span class="sxs-lookup"><span data-stu-id="22a86-1002">Note that the application should not release this packet.</span></span>
 - <span data-ttu-id="22a86-1003">**query_number** — логический номер параметра, начинающийся с нуля, слева направо в списке запросов.</span><span class="sxs-lookup"><span data-stu-id="22a86-1003">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
 - <span data-ttu-id="22a86-1004">**query_ptr** — область назначения для копирования запроса.</span><span class="sxs-lookup"><span data-stu-id="22a86-1004">**query_ptr** Destination area to copy the query.</span></span>
 - <span data-ttu-id="22a86-1005">**max_query_size** — максимальный размер области назначения запроса.</span><span class="sxs-lookup"><span data-stu-id="22a86-1005">**max_query_size** Maximum size of the query destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-1006">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-1006">Return Values</span></span>

 - <span data-ttu-id="22a86-1007">**NX_SUCCESS** (0x00) — запрос HTTP-сервера успешно получен.</span><span class="sxs-lookup"><span data-stu-id="22a86-1007">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
 - <span data-ttu-id="22a86-1008">**NX_HTTP_FAILED** (0xE2) — слишком маленький размер запроса.</span><span class="sxs-lookup"><span data-stu-id="22a86-1008">**NX_HTTP_FAILED** (0xE2) Query size too small.</span></span>
 - <span data-ttu-id="22a86-1009">**NX_HTTP_NOT_FOUND** (0xE6) — указанный запрос не найден.</span><span class="sxs-lookup"><span data-stu-id="22a86-1009">**NX_HTTP_NOT_FOUND** (0xE6) Specified query not found</span></span>
 - <span data-ttu-id="22a86-1010">**NX_HTTP_NO_QUERY_PARSED** (0xF2) — нет запроса в запросе клиента.</span><span class="sxs-lookup"><span data-stu-id="22a86-1010">**NX_HTTP_NO_QUERY_PARSED** (0xF2) No query in Client request</span></span>
 - <span data-ttu-id="22a86-1011">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-1011">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="22a86-1012">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="22a86-1012">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-1013">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-1013">Allowed From</span></span>

<span data-ttu-id="22a86-1014">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-1014">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-1015">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-1015">Example</span></span>

```c
/* Assuming we are in the application’s request notify callback
   routine, get the first query of the HTTP Client request. */
status =  nx_http_server_query_get(request_packet_ptr, 0, query_destination,
                30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
   in “query_destination.” */
```

## <a name="nx_http_server_start"></a><span data-ttu-id="22a86-1016">nx_http_server_start</span><span class="sxs-lookup"><span data-stu-id="22a86-1016">nx_http_server_start</span></span>

<span data-ttu-id="22a86-1017">Запуск HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="22a86-1017">Start the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-1018">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-1018">Prototype</span></span>

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="22a86-1019">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-1019">Description</span></span>

<span data-ttu-id="22a86-1020">Эта служба запускает ранее созданный экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-1020">This service starts the previously create HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-1021">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-1021">Input Parameters</span></span>

 - <span data-ttu-id="22a86-1022">**http_server_ptr** — указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-1022">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-1023">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-1023">Return Values</span></span>

 - <span data-ttu-id="22a86-1024">**NX_SUCCESS** (0x00) — сервер успешно запущен.</span><span class="sxs-lookup"><span data-stu-id="22a86-1024">**NX_SUCCESS** (0x00) Successful Server start</span></span>
 - <span data-ttu-id="22a86-1025">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-1025">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-1026">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-1026">Allowed From</span></span>

<span data-ttu-id="22a86-1027">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-1027">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-1028">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-1028">Example</span></span>

```c
/* Start the HTTP Server instance “my_server.”  */
status =  nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a><span data-ttu-id="22a86-1029">nx_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="22a86-1029">nx_http_server_stop</span></span>

<span data-ttu-id="22a86-1030">Остановка HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="22a86-1030">Stop the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-1031">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-1031">Prototype</span></span>

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="22a86-1032">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-1032">Description</span></span>

<span data-ttu-id="22a86-1033">Эта служба останавливает ранее созданный экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-1033">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="22a86-1034">Эту подпрограмму следует вызывать до удаления экземпляра HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-1034">This routine should be called prior to deleting an HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-1035">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-1035">Input Parameters</span></span>

 - <span data-ttu-id="22a86-1036">**http_server_ptr** — указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-1036">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-1037">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-1037">Return Values</span></span>

 - <span data-ttu-id="22a86-1038">**NX_SUCCESS** (0x00) — сервер успешно остановлен.</span><span class="sxs-lookup"><span data-stu-id="22a86-1038">**NX_SUCCESS** (0x00) Successful Server stop</span></span>
 - <span data-ttu-id="22a86-1039">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-1039">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="22a86-1040">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="22a86-1040">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-1041">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-1041">Allowed From</span></span>

<span data-ttu-id="22a86-1042">Потоки</span><span class="sxs-lookup"><span data-stu-id="22a86-1042">Threads</span></span>

### <a name="example"></a><span data-ttu-id="22a86-1043">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-1043">Example</span></span>

```c
/* Stop the HTTP Server instance “my_server.”  */
status =  nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a><span data-ttu-id="22a86-1044">nx_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="22a86-1044">nx_http_server_type_get</span></span>

<span data-ttu-id="22a86-1045">Извлечение типа файла из HTTP-запроса клиента</span><span class="sxs-lookup"><span data-stu-id="22a86-1045">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-1046">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-1046">Prototype</span></span>

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                             CHAR *name, CHAR *http_type_string);
```

### <a name="description"></a><span data-ttu-id="22a86-1047">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-1047">Description</span></span>

> [!NOTE]
> <span data-ttu-id="22a86-1048">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="22a86-1048">This service is deprecated.</span></span> <span data-ttu-id="22a86-1049">Пользователям рекомендуется использовать службу *nx_http_server_type_retrieve()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-1049">Users are encouraged to use the service *nx_http_server_type_retrieve()*.</span></span>

<span data-ttu-id="22a86-1050">Эта служба извлекает тип HTTP-запроса в буфере http_type_string и его длину в возвращаемом значении из имени входного буфера (обычно это URL-адрес).</span><span class="sxs-lookup"><span data-stu-id="22a86-1050">This service extracts the HTTP request type in the buffer http_type_string and its length in the return value from the input buffer name, usually the URL.</span></span> <span data-ttu-id="22a86-1051">Если сопоставление MIME не найдено, по умолчанию используется тип text/plain.</span><span class="sxs-lookup"><span data-stu-id="22a86-1051">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="22a86-1052">В противном случае извлеченный тип сравнивается с сопоставлениями MIME HTTP-сервера по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="22a86-1052">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="22a86-1053">Сопоставления MIME по умолчанию в HTTP-сервере NetX Duo:</span><span class="sxs-lookup"><span data-stu-id="22a86-1053">The default MIME maps in NetX Duo HTTP Server are:</span></span>

 - <span data-ttu-id="22a86-1054">**HTML** — текст или HTML.</span><span class="sxs-lookup"><span data-stu-id="22a86-1054">**html** text/html</span></span>
 - <span data-ttu-id="22a86-1055">**HTM** — текст или HTML.</span><span class="sxs-lookup"><span data-stu-id="22a86-1055">**htm** text/html</span></span>
 - <span data-ttu-id="22a86-1056">**TXT** — текст или обычный текст.</span><span class="sxs-lookup"><span data-stu-id="22a86-1056">**txt** text/plain</span></span>
 - <span data-ttu-id="22a86-1057">**GIF** — изображение или GIF.</span><span class="sxs-lookup"><span data-stu-id="22a86-1057">**gif** image/gif</span></span>
 - <span data-ttu-id="22a86-1058">**JPEG** — изображение или JPEG.</span><span class="sxs-lookup"><span data-stu-id="22a86-1058">**jpg** image/jpeg</span></span>
 - <span data-ttu-id="22a86-1059">**ICO** — изображение или x-icon.</span><span class="sxs-lookup"><span data-stu-id="22a86-1059">**ico** image/x-icon</span></span>

<span data-ttu-id="22a86-1060">Если задать, оно также будет искать определенный пользователем набор дополнительных сопоставлений MIME.</span><span class="sxs-lookup"><span data-stu-id="22a86-1060">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="22a86-1061">Дополнительные сведения об определяемых пользователем сопоставлениях см. в описании *nx_http_server_mime_maps_addtional_set()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-1061">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="22a86-1062">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="22a86-1062">This service is deprecated.</span></span> <span data-ttu-id="22a86-1063">Разработчикам рекомендуется перейти на использование *nx_http_server_type_get_extended()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-1063">Developers are encouraged to migrate to *nx_http_server_type_get_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-1064">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-1064">Input Parameters</span></span>

 - <span data-ttu-id="22a86-1065">**http_server_ptr** — указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-1065">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="22a86-1066">**name** — указатель на буфер для поиска.</span><span class="sxs-lookup"><span data-stu-id="22a86-1066">**name Pointer** to buffer to search</span></span>
 - <span data-ttu-id="22a86-1067">**http_type_string** — указатель на извлеченный тип HTML.</span><span class="sxs-lookup"><span data-stu-id="22a86-1067">**http_type_string** (Pointer to extracted HTML type)</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-1068">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-1068">Return Values</span></span>

 - <span data-ttu-id="22a86-1069">**Длина строки в байтах** — ненулевое значение означает успешную операцию.</span><span class="sxs-lookup"><span data-stu-id="22a86-1069">**Length of string in bytes** Non zero value is success.</span></span> <span data-ttu-id="22a86-1070">Нуль означает ошибку.</span><span class="sxs-lookup"><span data-stu-id="22a86-1070">Zero indicates error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-1071">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-1071">Allowed From</span></span>

<span data-ttu-id="22a86-1072">Приложение</span><span class="sxs-lookup"><span data-stu-id="22a86-1072">Application</span></span>

### <a name="example"></a><span data-ttu-id="22a86-1073">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-1073">Example</span></span>

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

## <a name="nx_http_server_type_get_extended"></a><span data-ttu-id="22a86-1074">nx_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="22a86-1074">nx_http_server_type_get_extended</span></span>

<span data-ttu-id="22a86-1075">Извлечение типа файла из HTTP-запроса клиента</span><span class="sxs-lookup"><span data-stu-id="22a86-1075">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-1076">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-1076">Prototype</span></span>

```c
UINT nx_http_server_type_get_extended(
                                    NX_HTTP_SERVER *http_server_ptr,
                                    CHAR *name, CHAR *http_type_string,
                                    UINT http_type_string_max_size);
```

### <a name="description"></a><span data-ttu-id="22a86-1077">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-1077">Description</span></span>

<span data-ttu-id="22a86-1078">Эта служба извлекает тип HTTP-запроса в буфере *http_type_string* и его длину в возвращаемом значении из *имени* входного буфера (обычно это URL-адрес).</span><span class="sxs-lookup"><span data-stu-id="22a86-1078">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="22a86-1079">Если сопоставление MIME не найдено, по умолчанию используется тип text/plain.</span><span class="sxs-lookup"><span data-stu-id="22a86-1079">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="22a86-1080">В противном случае извлеченный тип сравнивается с сопоставлениями MIME HTTP-сервера по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="22a86-1080">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="22a86-1081">Сопоставления MIME по умолчанию в HTTP-сервере NetX Duo:</span><span class="sxs-lookup"><span data-stu-id="22a86-1081">The default MIME maps in NetX Duo HTTP Server are:</span></span>

 - <span data-ttu-id="22a86-1082">**HTML** — текст или HTML.</span><span class="sxs-lookup"><span data-stu-id="22a86-1082">**html** text/html</span></span>
 - <span data-ttu-id="22a86-1083">**HTM** — текст или HTML.</span><span class="sxs-lookup"><span data-stu-id="22a86-1083">**htm** text/html</span></span>
 - <span data-ttu-id="22a86-1084">**TXT** — текст или обычный текст.</span><span class="sxs-lookup"><span data-stu-id="22a86-1084">**txt** text/plain</span></span>
 - <span data-ttu-id="22a86-1085">**GIF** — изображение или GIF.</span><span class="sxs-lookup"><span data-stu-id="22a86-1085">**gif** image/gif</span></span>
 - <span data-ttu-id="22a86-1086">**JPEG** — изображение или JPEG.</span><span class="sxs-lookup"><span data-stu-id="22a86-1086">**jpg** image/jpeg</span></span>
 - <span data-ttu-id="22a86-1087">**ICO** — изображение или x-icon.</span><span class="sxs-lookup"><span data-stu-id="22a86-1087">**ico** image/x-icon</span></span>

<span data-ttu-id="22a86-1088">Если задать, оно также будет искать определенный пользователем набор дополнительных сопоставлений MIME.</span><span class="sxs-lookup"><span data-stu-id="22a86-1088">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="22a86-1089">Дополнительные сведения об определяемых пользователем сопоставлениях см. в описании *nx_http_server_mime_maps_addtional_set()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-1089">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="22a86-1090">Эта служба заменяет *nx_http_server_type_get ()* .</span><span class="sxs-lookup"><span data-stu-id="22a86-1090">This service replaces *nx_http_server_type_get()*.</span></span> <span data-ttu-id="22a86-1091">Эта версия предоставляет дополнительные сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="22a86-1091">This version supplies additional length information.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-1092">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-1092">Input Parameters</span></span>

 - <span data-ttu-id="22a86-1093">**http_server_ptr** — указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-1093">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="22a86-1094">**name** — указатель на буфер для поиска.</span><span class="sxs-lookup"><span data-stu-id="22a86-1094">**name** Pointer to buffer to search</span></span>
 - <span data-ttu-id="22a86-1095">**name_length** — длина буфера для поиска.</span><span class="sxs-lookup"><span data-stu-id="22a86-1095">**name_length** Length of buffer to search</span></span>
 - <span data-ttu-id="22a86-1096">**http_type_string** — указатель на извлеченный тип HTML.</span><span class="sxs-lookup"><span data-stu-id="22a86-1096">**http_type_string** (Pointer to extracted HTML type)</span></span>
 - <span data-ttu-id="22a86-1097">**http_type_string_max_size** — размер буфера http_type_string.</span><span class="sxs-lookup"><span data-stu-id="22a86-1097">**http_type_string_max_size** Size of the http_type_string buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-1098">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-1098">Return Values</span></span>

 - <span data-ttu-id="22a86-1099">**Длина строки в байтах** — ненулевое значение означает успешную операцию.</span><span class="sxs-lookup"><span data-stu-id="22a86-1099">**Length of string in bytes** Non zero value is success.</span></span> <span data-ttu-id="22a86-1100">Нуль означает ошибку.</span><span class="sxs-lookup"><span data-stu-id="22a86-1100">Zero indicates error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-1101">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-1101">Allowed From</span></span>

<span data-ttu-id="22a86-1102">Приложение</span><span class="sxs-lookup"><span data-stu-id="22a86-1102">Application</span></span>

### <a name="example"></a><span data-ttu-id="22a86-1103">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-1103">Example</span></span>

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

<span data-ttu-id="22a86-1104">Более подробный пример см. в описании для [*nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header).</span><span class="sxs-lookup"><span data-stu-id="22a86-1104">For a more detailed example, see the description for [*nx_http_server_callback_generate_response_header*](#nx_http_server_callback_generate_response_header).</span></span>

## <a name="nx_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="22a86-1105">nx_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="22a86-1105">nx_http_server_digest_authenticate_notify_set</span></span>

<span data-ttu-id="22a86-1106">Задание функции обратного вызова дайджест-проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="22a86-1106">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-1107">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-1107">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="22a86-1108">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-1108">Description</span></span>

<span data-ttu-id="22a86-1109">Эта служба задает обратный вызов, вызываемый при выполнении дайджест-проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-1109">This service sets the callback invoked when digest authenticate is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-1110">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-1110">Input Parameters</span></span>

 - <span data-ttu-id="22a86-1111">**http_server_ptr** — указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-1111">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="22a86-1112">**digest_authenticate_callback** — указатель на обратный вызов дайджест-проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-1112">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-1113">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-1113">Return Values</span></span>

 - <span data-ttu-id="22a86-1114">**NX_SUCCESS** (0x00) — обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="22a86-1114">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="22a86-1115">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-1115">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
 - <span data-ttu-id="22a86-1116">NX_NOT_SUPPORTED (0x4B) — дайджест-проверка подлинности не включена.</span><span class="sxs-lookup"><span data-stu-id="22a86-1116">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-1117">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-1117">Allowed From</span></span>

<span data-ttu-id="22a86-1118">Приложение</span><span class="sxs-lookup"><span data-stu-id="22a86-1118">Application</span></span>

### <a name="example"></a><span data-ttu-id="22a86-1119">Например, .</span><span class="sxs-lookup"><span data-stu-id="22a86-1119">Example</span></span>

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

## <a name="nx_http_server_authentication_check_set"></a><span data-ttu-id="22a86-1120">nx_http_server_authentication_check_set</span><span class="sxs-lookup"><span data-stu-id="22a86-1120">nx_http_server_authentication_check_set</span></span>

<span data-ttu-id="22a86-1121">Задание функции обратного вызова проверки для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="22a86-1121">Set authentication checking callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="22a86-1122">Прототип</span><span class="sxs-lookup"><span data-stu-id="22a86-1122">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="22a86-1123">Описание</span><span class="sxs-lookup"><span data-stu-id="22a86-1123">Description</span></span>

<span data-ttu-id="22a86-1124">Эта служба задает функцию обратного вызова проверки для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="22a86-1124">This service sets the callback function of authentication checking.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="22a86-1125">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="22a86-1125">Input Parameters</span></span>

 - <span data-ttu-id="22a86-1126">**http_server_ptr** — указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="22a86-1126">**http_server_ptr** Pointer to HTTP Server instance</span></span>
 - <span data-ttu-id="22a86-1127">**authentication_check_extended** — указатель на проверку для проверки подлинности приложения.</span><span class="sxs-lookup"><span data-stu-id="22a86-1127">**authentication_check_extended** Pointer to application’s authentication checking</span></span>

### <a name="return-values"></a><span data-ttu-id="22a86-1128">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="22a86-1128">Return Values</span></span>

 - <span data-ttu-id="22a86-1129">**NX_SUCCESS** (0x00) — обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="22a86-1129">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
 - <span data-ttu-id="22a86-1130">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="22a86-1130">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="22a86-1131">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="22a86-1131">Allowed From</span></span>

<span data-ttu-id="22a86-1132">Приложение</span><span class="sxs-lookup"><span data-stu-id="22a86-1132">Application</span></span>

### <a name="example"></a><span data-ttu-id="22a86-1133">Пример</span><span class="sxs-lookup"><span data-stu-id="22a86-1133">Example</span></span>

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
