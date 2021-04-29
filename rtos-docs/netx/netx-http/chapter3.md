---
title: Глава 3. Описание служб HTTP для NetX
description: В этой главе приводится описание всех служб HTTP для NetX (перечислены ниже) в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c58d0e3d7eca86816a9d656bf2b92a896ffb96fc
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815195"
---
# <a name="chapter-3---description-of-netx-http-services"></a><span data-ttu-id="c4da6-103">Глава 3. Описание служб HTTP для NetX</span><span class="sxs-lookup"><span data-stu-id="c4da6-103">Chapter 3 - Description of NetX HTTP services</span></span>

<span data-ttu-id="c4da6-104">В этой главе приводится описание всех служб HTTP для NetX (перечислены ниже) в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="c4da6-104">This chapter contains a description of all NetX HTTP services (listed below) in alphabetical order.</span></span>

<span data-ttu-id="c4da6-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="c4da6-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

<span data-ttu-id="c4da6-106">**Службы HTTP-клиента**</span><span class="sxs-lookup"><span data-stu-id="c4da6-106">**HTTP Client services:**</span></span>

- <span data-ttu-id="c4da6-107">nx_http_client_create: *создание экземпляра HTTP-клиента*</span><span class="sxs-lookup"><span data-stu-id="c4da6-107">nx_http_client_create *Create an HTTP Client Instance*</span></span>
- <span data-ttu-id="c4da6-108">nx_http_client_delete: *удаление экземпляра HTTP-клиента*</span><span class="sxs-lookup"><span data-stu-id="c4da6-108">nx_http_client_delete *Delete an HTTP Client instance*</span></span>
- <span data-ttu-id="c4da6-109">nx_http_client_get_start: *запуск HTTP-запроса GET*</span><span class="sxs-lookup"><span data-stu-id="c4da6-109">nx_http_client_get_start *Start an HTTP GET request*</span></span>
- <span data-ttu-id="c4da6-110">nx_http_client_get_start_extended: *запуск HTTP-запроса GET*</span><span class="sxs-lookup"><span data-stu-id="c4da6-110">nx_http_client_get_start_extended *Start an HTTP GET request*</span></span>
- <span data-ttu-id="c4da6-111">nx_http_client_get_packet: *получение следующего пакета данных ресурса*</span><span class="sxs-lookup"><span data-stu-id="c4da6-111">nx_http_client_get_packet *Get next resource data packet*</span></span>
- <span data-ttu-id="c4da6-112">nx_http_client_put_start: *запуск HTTP-запроса PUT*</span><span class="sxs-lookup"><span data-stu-id="c4da6-112">nx_http_client_put_start *Start an HTTP PUT request*</span></span>
- <span data-ttu-id="c4da6-113">nx_http_client_put_start_extended: *запуск HTTP-запроса PUT*</span><span class="sxs-lookup"><span data-stu-id="c4da6-113">nx_http_client_put_start_extended *Start an HTTP PUT request*</span></span>
- <span data-ttu-id="c4da6-114">nx_http_client_put_packet: *отправка следующего пакета данных ресурса*</span><span class="sxs-lookup"><span data-stu-id="c4da6-114">nx_http_client_put_packet *Send next resource data packet*</span></span>
- <span data-ttu-id="c4da6-115">*nx_http_client_set_connect_port:* *изменение порта для подключения к HTTP-серверу*</span><span class="sxs-lookup"><span data-stu-id="c4da6-115">*nx_http_client_set_connect_port* *Change the port to connect to the HTTP Server*</span></span>

<span data-ttu-id="c4da6-116">**Службы HTTP-сервера**</span><span class="sxs-lookup"><span data-stu-id="c4da6-116">**HTTP Server services:**</span></span>

- <span data-ttu-id="c4da6-117">nx_http_server_cache_info_callback_set: *задание обратного вызова для получения возраста и даты последнего изменения указанного URL-адреса*</span><span class="sxs-lookup"><span data-stu-id="c4da6-117">nx_http_server_cache_info_callback_set *Set callback to retrieve age and last modified date of specified URL*</span></span>
- <span data-ttu-id="c4da6-118">nx_http_server_callback_data_send: *отправка данных HTTP из функции обратного вызова*</span><span class="sxs-lookup"><span data-stu-id="c4da6-118">nx_http_server_callback_data_send *Send HTTP data from callback function*</span></span>
- <span data-ttu-id="c4da6-119">nx_http_server_callback_generate_response_header: *создание заголовка ответа в функциях обратного вызова*</span><span class="sxs-lookup"><span data-stu-id="c4da6-119">nx_http_server_callback_generate_response_header *Create response header in callback functions*</span></span>
- <span data-ttu-id="c4da6-120">nx_http_server_callback_generate_response_header_extended: *создание заголовка ответа в функциях обратного вызова*</span><span class="sxs-lookup"><span data-stu-id="c4da6-120">nx_http_server_callback_generate_response_header_extended *Create response header in callback functions*</span></span>
- <span data-ttu-id="c4da6-121">nx_http_server_callback_packet_send: *отправка пакета HTTP из обратного вызова HTTP*</span><span class="sxs-lookup"><span data-stu-id="c4da6-121">nx_http_server_callback_packet_send *Send an HTTP packet from an HTTP callback*</span></span>
- <span data-ttu-id="c4da6-122">nx_http_server_callback_response_send: *отправка ответа из функции обратного вызова*</span><span class="sxs-lookup"><span data-stu-id="c4da6-122">nx_http_server_callback_response_send *Send response from callback function*</span></span>
- <span data-ttu-id="c4da6-123">nx_http_server_callback_response_send_extended: *отправка ответа из функции обратного вызова*</span><span class="sxs-lookup"><span data-stu-id="c4da6-123">nx_http_server_callback_response_send_extended *Send response from callback function*</span></span>
- <span data-ttu-id="c4da6-124">nx_http_server_content_get: *получение содержимого из запроса*</span><span class="sxs-lookup"><span data-stu-id="c4da6-124">nx_http_server_content_get *Get content from the request*</span></span>
- <span data-ttu-id="c4da6-125">nx_http_server_content_get_extended: *получение содержимого из запроса; поддерживает пустые запросы (содержимое нулевой длины)*</span><span class="sxs-lookup"><span data-stu-id="c4da6-125">nx_http_server_content_get_extended *Get content from the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="c4da6-126">nx_http_server_content_length_get: *получение длины содержимого в запросе*</span><span class="sxs-lookup"><span data-stu-id="c4da6-126">nx_http_server_content_length_get *Get length of content in the request*</span></span>
- <span data-ttu-id="c4da6-127">nx_http_server_content_length_get_extended: *получение длины содержимого в запросе; поддерживает пустые запросы (содержимое нулевой длины)*</span><span class="sxs-lookup"><span data-stu-id="c4da6-127">nx_http_server_content_length_get_extended *Get length of content in the request; supports empty (zero Content Length) requests*</span></span>
- <span data-ttu-id="c4da6-128">nx_http_server_create: *создание экземпляра HTTP-сервера*</span><span class="sxs-lookup"><span data-stu-id="c4da6-128">nx_http_server_create *Create an HTTP Server instance*</span></span>
- <span data-ttu-id="c4da6-129">nx_http_server_delete: *удаление экземпляра HTTP-сервера*</span><span class="sxs-lookup"><span data-stu-id="c4da6-129">nx_http_server_delete *Delete an HTTP Server instance*</span></span>
- <span data-ttu-id="c4da6-130">nx_http_server_get_entity_content: *возврат размера и расположения содержимого сущности в URL-адресе*</span><span class="sxs-lookup"><span data-stu-id="c4da6-130">nx_http_server_get_entity_content *Return size and location of entity content in URL*</span></span>
- <span data-ttu-id="c4da6-131">nx_http_server_get_entity_header: *извлечение заголовка сущности URL-адреса в указанный буфер*</span><span class="sxs-lookup"><span data-stu-id="c4da6-131">nx_http_server_get_entity_header *Extract URL entity header into specified buffer*</span></span>
- <span data-ttu-id="c4da6-132">nx_http_server_gmt_callback_set: *задание обратного вызова для получения даты и времени по Гринвичу*</span><span class="sxs-lookup"><span data-stu-id="c4da6-132">nx_http_server_gmt_callback_set *Set callback to retrieve GMT date and time*</span></span>
- <span data-ttu-id="c4da6-133">nx_http_server_invalid_userpassword_notify_set: *задание обратного вызова, выполняющегося, когда в запросе клиента получены недопустимые имя пользователя и пароль*</span><span class="sxs-lookup"><span data-stu-id="c4da6-133">nx_http_server_invalid_userpassword_notify_set *Set callback for when invalid username and password is received in a Client request*</span></span>
- <span data-ttu-id="c4da6-134">nx_http_server_mime_maps_additional_set: *определение дополнительных сопоставлений MIME для HTML*</span><span class="sxs-lookup"><span data-stu-id="c4da6-134">nx_http_server_mime_maps_additional_set *Define additional mime maps for HTML*</span></span>
- <span data-ttu-id="c4da6-135">nx_http_server_packet_content_find: *извлечение длины содержимого в заголовке HTTP и установка указателя на начало данных содержимого*</span><span class="sxs-lookup"><span data-stu-id="c4da6-135">nx_http_server_packet_content_find *Extract content length in HTTP header and set pointer to start of content data*</span></span>
- <span data-ttu-id="c4da6-136">nx_http_server_packet_get: *прямое получение пакета клиента*</span><span class="sxs-lookup"><span data-stu-id="c4da6-136">nx_http_server_packet_get *Receive client packet directly*</span></span>
- <span data-ttu-id="c4da6-137">nx_http_server_param_get: *получение параметра из запроса*</span><span class="sxs-lookup"><span data-stu-id="c4da6-137">nx_http_server_param_get *Get parameter from the request*</span></span>
- <span data-ttu-id="c4da6-138">nx_http_server_query_get: *получение запроса из запроса*</span><span class="sxs-lookup"><span data-stu-id="c4da6-138">nx_http_server_query_get *Get query from the request*</span></span>
- <span data-ttu-id="c4da6-139">nx_http_server_start: *запуск HTTP-сервера*</span><span class="sxs-lookup"><span data-stu-id="c4da6-139">nx_http_server_start *Start the HTTP Server*</span></span>
- <span data-ttu-id="c4da6-140">nx_http_server_stop: *остановка HTTP-сервера*</span><span class="sxs-lookup"><span data-stu-id="c4da6-140">nx_http_server_stop *Stop the HTTP Server*</span></span>
- <span data-ttu-id="c4da6-141">nx_http_server_type_get: *извлечение типа HTTP, например text/plain из заголовка*</span><span class="sxs-lookup"><span data-stu-id="c4da6-141">nx_http_server_type_get *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="c4da6-142">nx_http_server_type_get_extended: *извлечение типа HTTP, например text/plain из заголовка*</span><span class="sxs-lookup"><span data-stu-id="c4da6-142">nx_http_server_type_get_extended *Extract HTTP type e.g. text/plain from header*</span></span>
- <span data-ttu-id="c4da6-143">nx_http_server_digest_authenticate_notify_set: *задание функции обратного вызова дайджест-проверки подлинности*</span><span class="sxs-lookup"><span data-stu-id="c4da6-143">nx_http_server_digest_authenticate_notify_set *Set digest authenticate callback function*</span></span>
- <span data-ttu-id="c4da6-144">nx_http_server_authentication_check_set: *задание функции обратного вызова проверки для проверки подлинности*</span><span class="sxs-lookup"><span data-stu-id="c4da6-144">nx_http_server_authentication_check_set *Set authentication checking callback function*</span></span>

## <a name="nx_http_client_create"></a><span data-ttu-id="c4da6-145">nx_http_client_create</span><span class="sxs-lookup"><span data-stu-id="c4da6-145">nx_http_client_create</span></span>

### <a name="create-an-http-client-instance"></a><span data-ttu-id="c4da6-146">Создание экземпляра HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="c4da6-146">Create an HTTP Client Instance</span></span>

<span data-ttu-id="c4da6-147">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-147">**Prototype**</span></span>

```c
UINT nx_http_client_create(NX_HTTP_CLIENT *client_ptr,
                          CHAR *client_name, NX_IP *ip_ptr, 
                          NX_PACKET_POOL *pool_ptr,
                          ULONG window_size);
```

<span data-ttu-id="c4da6-148">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-148">**Description**</span></span>

<span data-ttu-id="c4da6-149">Эта служба создает экземпляр HTTP-клиента в указанном экземпляре IP.</span><span class="sxs-lookup"><span data-stu-id="c4da6-149">This service creates an HTTP Client instance on the specified IP instance.</span></span>

<span data-ttu-id="c4da6-150">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-150">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-151">**client_ptr**: указатель на блок управления HTTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="c4da6-151">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="c4da6-152">**client_name**: имя экземпляра HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="c4da6-152">**client_name** Name of HTTP Client instance.</span></span>
- <span data-ttu-id="c4da6-153">**ip_ptr**: указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="c4da6-153">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="c4da6-154">**pool_ptr**: указатель на пул пакетов по умолчанию</span><span class="sxs-lookup"><span data-stu-id="c4da6-154">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="c4da6-155">Обратите внимание, что пакеты в этом пуле должны иметь объем полезных данных, достаточный для работы с полным заголовком ответа.</span><span class="sxs-lookup"><span data-stu-id="c4da6-155">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="c4da6-156">Это определяется параметром NX_HTTP_CLIENT_MIN_PACKET_SIZE в *nx_http_client.h*.</span><span class="sxs-lookup"><span data-stu-id="c4da6-156">This is defined by NX_HTTP_CLIENT_MIN_PACKET_SIZE in *nx_http_client.h*.</span></span>
- <span data-ttu-id="c4da6-157">**window_size** Размер окна приема TCP-сокета клиента.</span><span class="sxs-lookup"><span data-stu-id="c4da6-157">**window_size** Size of the Client’s TCP socket receive window.</span></span>

<span data-ttu-id="c4da6-158">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-158">**Return Values**</span></span>

- <span data-ttu-id="c4da6-159">**NX_SUCCESS** (0x00) — HTTP-клиент успешно создан.</span><span class="sxs-lookup"><span data-stu-id="c4da6-159">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
- <span data-ttu-id="c4da6-160">NX_PTR_ERROR (0x16) — недопустимый указатель на HTTP, ip_ptr или пул пакетов.</span><span class="sxs-lookup"><span data-stu-id="c4da6-160">NX_PTR_ERROR (0x16) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="c4da6-161">NX_HTTP_POOL_ERROR (0xE9) — недопустимый размер полезных данных в пуле пакетов.</span><span class="sxs-lookup"><span data-stu-id="c4da6-161">NX_HTTP_POOL_ERROR(0xE9) Invalid payload size in packet pool</span></span>

<span data-ttu-id="c4da6-162">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-162">**Allowed From**</span></span>

<span data-ttu-id="c4da6-163">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-163">Initialization, Threads</span></span>

<span data-ttu-id="c4da6-164">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-164">**Example**</span></span>

```c
/* Create the HTTP Client instance “my_client” on “ip_0”. */
status = nx_http_client_create(&my_client, “my client”, &ip_0, &pool_0, 100);
  
/* If status is NX_SUCCESS an HTTP Client instance was successfully  created. */
```

## <a name="nx_http_client_delete"></a><span data-ttu-id="c4da6-165">nx_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="c4da6-165">nx_http_client_delete</span></span>

### <a name="delete-an-http-client-instance"></a><span data-ttu-id="c4da6-166">Удаление экземпляра HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="c4da6-166">Delete an HTTP Client Instance</span></span>

<span data-ttu-id="c4da6-167">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-167">**Prototype**</span></span>

```c
UINT nx_http_client_delete(NX_HTTP_CLIENT *client_ptr);
```

<span data-ttu-id="c4da6-168">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-168">**Description**</span></span>

<span data-ttu-id="c4da6-169">Эта служба удаляет ранее созданный экземпляр HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="c4da6-169">This service deletes a previously created HTTP Client instance.</span></span>

<span data-ttu-id="c4da6-170">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-170">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-171">**client_ptr**: указатель на блок управления HTTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="c4da6-171">**client_ptr** Pointer to HTTP Client control block.</span></span>

<span data-ttu-id="c4da6-172">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-172">**Return Values**</span></span>

- <span data-ttu-id="c4da6-173">**NX_SUCCESS** (0x00) — HTTP-клиент успешно удален.</span><span class="sxs-lookup"><span data-stu-id="c4da6-173">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
- <span data-ttu-id="c4da6-174">NX_PTR_ERROR (0x16) — недопустимый указатель на HTTP.</span><span class="sxs-lookup"><span data-stu-id="c4da6-174">NX_PTR_ERROR (0x16) Invalid HTTP pointer</span></span>
- <span data-ttu-id="c4da6-175">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="c4da6-175">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="c4da6-176">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-176">**Allowed From**</span></span>

<span data-ttu-id="c4da6-177">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-177">Threads</span></span>

<span data-ttu-id="c4da6-178">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-178">**Example**</span></span>

```c
/* Delete the HTTP Client instance “my_client.” */
status = nx_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully  deleted. */
```

## <a name="nx_http_client_get_start"></a><span data-ttu-id="c4da6-179">nx_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="c4da6-179">nx_http_client_get_start</span></span>

### <a name="start-an-http-get-request"></a><span data-ttu-id="c4da6-180">Запуск HTTP-запроса GET</span><span class="sxs-lookup"><span data-stu-id="c4da6-180">Start an HTTP GET request</span></span>

<span data-ttu-id="c4da6-181">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-181">**Prototype**</span></span>

```c
UINT nx_http_client_get_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource, CHAR *input_ptr,
                             UINT input_size, CHAR *username, CHAR *password,
                             ULONG wait_option);
```

<span data-ttu-id="c4da6-182">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-182">**Description**</span></span>

<span data-ttu-id="c4da6-183">Эта служба пытается выполнить запрос GET к ресурсу, указанному указателем resource, в ранее созданном экземпляре HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="c4da6-183">This service attempts to GET the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="c4da6-184">Если эта подпрограмма возвращает NX_SUCCESS, приложение может выполнить несколько вызовов службы *nx_http_client_get_packet*, чтобы получить пакеты данных, соответствующие содержимому запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="c4da6-184">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="c4da6-185">Обратите внимание, что строка ресурса может ссылаться на локальный файл, например /index.htm, или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.</span><span class="sxs-lookup"><span data-stu-id="c4da6-185">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="c4da6-186">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="c4da6-186">This service is deprecated.</span></span> <span data-ttu-id="c4da6-187">Разработчикам рекомендуется перейти на использование *nx_http_client_get_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="c4da6-187">Developers are encouraged to migrate to *nx_http_client_get_start_extended()*</span></span>

<span data-ttu-id="c4da6-188">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-188">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-189">**client_ptr**: указатель на блок управления HTTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="c4da6-189">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="c4da6-190">**ip_address**: IP-адрес HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-190">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="c4da6-191">**resource**: указатель на строку URL-адреса запрошенного ресурса</span><span class="sxs-lookup"><span data-stu-id="c4da6-191">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="c4da6-192">**input_ptr**: указатель на дополнительные данные для запроса GET</span><span class="sxs-lookup"><span data-stu-id="c4da6-192">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="c4da6-193">Это необязательно.</span><span class="sxs-lookup"><span data-stu-id="c4da6-193">This is optional.</span></span> <span data-ttu-id="c4da6-194">Если параметр допустим, указанные входные данные помещаются в область содержимого сообщения, а вместо операции GET используется POST.</span><span class="sxs-lookup"><span data-stu-id="c4da6-194">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
- <span data-ttu-id="c4da6-195">**input_size**: число байтов в необязательных дополнительных входных данных, на которые указывает input_ptr</span><span class="sxs-lookup"><span data-stu-id="c4da6-195">**input_size** Number of bytes in optional additional input pointed to by input_ptr.</span></span>
- <span data-ttu-id="c4da6-196">**username**: указатель на необязательное имя пользователя для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="c4da6-196">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="c4da6-197">**password**: указатель на необязательный пароль для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="c4da6-197">**password** Pointer to optional password for authentication.</span></span><span data-ttu-id="c4da6-198">
-\*\*wait_option*\* определяет, как долго служба будет ожидать запуск запроса GET HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="c4da6-198">
-\*\*wait_option*\* Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="c4da6-199">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="c4da6-199">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c4da6-200">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c4da6-200">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c4da6-201">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="c4da6-201">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="c4da6-202">Выбор параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="c4da6-202">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="c4da6-203">Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c4da6-203">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="c4da6-204">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-204">**Return Values**</span></span>

- <span data-ttu-id="c4da6-205">**NX_SUCCESS** (0x00) — сообщение о запуске запроса GET HTTP-клиента успешно отправлено.</span><span class="sxs-lookup"><span data-stu-id="c4da6-205">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="c4da6-206">**NX_HTTP_ERROR** (0xE0) — внутренняя ошибка HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="c4da6-206">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
- <span data-ttu-id="c4da6-207">**NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="c4da6-207">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="c4da6-208">**NX_HTTP_FAILED** (0xE2) — ошибка HTTP-клиента при взаимодействии с HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="c4da6-208">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="c4da6-209">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) — недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="c4da6-209">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
- <span data-ttu-id="c4da6-210">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-210">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="c4da6-211">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="c4da6-211">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

<span data-ttu-id="c4da6-212">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-212">**Allowed From**</span></span>

<span data-ttu-id="c4da6-213">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-213">Threads</span></span>

<span data-ttu-id="c4da6-214">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-214">**Example**</span></span>

```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                  NX_NULL, 0, “myname”, “mypassword”, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
far successful. The client must now call *nx_http_client_get_packet* multiple
times to retrieve the content associated with TEST.HTM. */

#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start(&my_client, IP_ADDRESS(1,2,3,5), “/TEST.HTM”,
                                  POST_MESSAGE, sizeof(POST_MESSAGE),
                                  “myname”, “mypassword”, 1000);
 
/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST 
request for TEST.HTM and successfully sent. */
```


## <a name="nx_http_client_get_start_extended"></a><span data-ttu-id="c4da6-215">nx_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="c4da6-215">nx_http_client_get_start_extended</span></span>

### <a name="start-an-http-get-request"></a><span data-ttu-id="c4da6-216">Запуск HTTP-запроса GET</span><span class="sxs-lookup"><span data-stu-id="c4da6-216">Start an HTTP GET request</span></span>

<span data-ttu-id="c4da6-217">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-217">**Prototype**</span></span>

```c
UINT nx_http_client_get_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *input_ptr, UINT input_size, CHAR *username,
     UINT username_length, CHAR *password, UINT password_length,
     ULONG wait_option);
```

<span data-ttu-id="c4da6-218">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-218">**Description**</span></span>

<span data-ttu-id="c4da6-219">Эта служба пытается выполнить запрос GET к ресурсу, указанному указателем resource, в ранее созданном экземпляре HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="c4da6-219">This service attempts to GET the resource specified by “resource” pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="c4da6-220">Если эта подпрограмма возвращает NX_SUCCESS, приложение может выполнить несколько вызовов службы *nx_http_client_get_packet*, чтобы получить пакеты данных, соответствующие содержимому запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="c4da6-220">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_http_client_get_packet* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="c4da6-221">Обратите внимание, что строка ресурса может ссылаться на локальный файл, например /index.htm, или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.</span><span class="sxs-lookup"><span data-stu-id="c4da6-221">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="c4da6-222">Эта служба заменяет *nx_http_client_get_start()* .</span><span class="sxs-lookup"><span data-stu-id="c4da6-222">This service replaces *nx_http_client_get_start()*.</span></span> <span data-ttu-id="c4da6-223">Она требует от вызывающей стороны указания длины ресурса, имени пользователя и пароля.</span><span class="sxs-lookup"><span data-stu-id="c4da6-223">It requires caller to specify the length of the resource, username and password.</span></span>

<span data-ttu-id="c4da6-224">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-224">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-225">**client_ptr**: указатель на блок управления HTTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="c4da6-225">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="c4da6-226">**ip_address**: IP-адрес HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-226">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="c4da6-227">**resource**: указатель на строку URL-адреса запрошенного ресурса</span><span class="sxs-lookup"><span data-stu-id="c4da6-227">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="c4da6-228">**resource_length**: длина строки URL-адреса запрошенного ресурса</span><span class="sxs-lookup"><span data-stu-id="c4da6-228">**resource_length** Length of URL string for requested resource.</span></span>
- <span data-ttu-id="c4da6-229">**input_ptr**: указатель на дополнительные данные для запроса GET</span><span class="sxs-lookup"><span data-stu-id="c4da6-229">**input_ptr** Pointer to additional data for the GET request.</span></span> <span data-ttu-id="c4da6-230">Это необязательно.</span><span class="sxs-lookup"><span data-stu-id="c4da6-230">This is optional.</span></span> <span data-ttu-id="c4da6-231">Если параметр допустим, указанные входные данные помещаются в область содержимого сообщения, а вместо операции GET используется POST.</span><span class="sxs-lookup"><span data-stu-id="c4da6-231">If valid, the specified input is placed in the content area of the message and a POST is used instead of a GET operation.</span></span>
- <span data-ttu-id="c4da6-232">**input_size**: число байтов в необязательных дополнительных входных данных, на которые указывает input_ptr</span><span class="sxs-lookup"><span data-stu-id="c4da6-232">**input_size** Number of bytes in optional additional input pointed to by input_ptr.</span></span>
- <span data-ttu-id="c4da6-233">**username**: указатель на необязательное имя пользователя для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="c4da6-233">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="c4da6-234">**username_length**: длина необязательного имени пользователя для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="c4da6-234">**username_length** Length of optional user name for authentication.</span></span>
- <span data-ttu-id="c4da6-235">**password**: указатель на необязательный пароль для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="c4da6-235">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="c4da6-236">**password_length**: длина необязательного пароля для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="c4da6-236">**password_length** Length of optional password for authentication.</span></span>
- <span data-ttu-id="c4da6-237">**wait_option** определяет, как долго служба будет ожидать запуск запроса GET HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="c4da6-237">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="c4da6-238">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="c4da6-238">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c4da6-239">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c4da6-239">**time out value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c4da6-240">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="c4da6-240">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="c4da6-241">Выбор параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="c4da6-241">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="c4da6-242">Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c4da6-242">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="c4da6-243">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-243">**Return Values**</span></span>

- <span data-ttu-id="c4da6-244">**NX_SUCCESS** (0x00) — сообщение о запуске запроса GET HTTP-клиента успешно отправлено.</span><span class="sxs-lookup"><span data-stu-id="c4da6-244">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="c4da6-245">**NX_HTTP_ERROR** (0xE0) — внутренняя ошибка HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="c4da6-245">**NX_HTTP_ERROR** (0xE0) Internal HTTP Client error</span></span>
- <span data-ttu-id="c4da6-246">**NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="c4da6-246">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="c4da6-247">**NX_HTTP_FAILED** (0xE2) — ошибка HTTP-клиента при взаимодействии с HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="c4da6-247">**NX_HTTP_FAILED** (0xE2) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="c4da6-248">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) — недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="c4da6-248">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or password.</span></span>
- <span data-ttu-id="c4da6-249">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-249">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="c4da6-250">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="c4da6-250">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

<span data-ttu-id="c4da6-251">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-251">**Allowed From**</span></span>

<span data-ttu-id="c4da6-252">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-252">Threads</span></span>

<span data-ttu-id="c4da6-253">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-253">**Example**</span></span>
            
```c
/* Start the GET operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5),
                                           “/TEST.HTM”,
                                           9, NX_NULL, 0, “myname”, 6,
                                           “mypassword”, 10, 1000);

/* If status is NX_SUCCESS, the GET request for TEST.HTM is started and is so
far successful. The client must now call *nx_http_client_get_packet* multiple
times to retrieve the content associated with TEST.HTM. */

#define POST_MESSAGE   “Add this data to the message content”

/* Start the POST operation on the HTTP Client “my_client.”  */
status =  nx_http_client_get_start_extended(&my_client, IP_ADDRESS(1,2,3,5), 
                                           “/TEST.HTM”,
                                           9, POST_MESSAGE, sizeof(POST_MESSAGE),
                                           “myname”, 6, “mypassword”, 10, 1000);

/* If status is NX_SUCCESS, the POST_MESSAGE is added to the message in the POST 
request for TEST.HTM and successfully sent. */
```

## <a name="nx_http_client_get_packet"></a><span data-ttu-id="c4da6-254">nx_http_client_get_packet</span><span class="sxs-lookup"><span data-stu-id="c4da6-254">nx_http_client_get_packet</span></span>

### <a name="get-next-resource-data-packet"></a><span data-ttu-id="c4da6-255">Получение следующего пакета данных ресурса</span><span class="sxs-lookup"><span data-stu-id="c4da6-255">Get next resource data packet</span></span>

<span data-ttu-id="c4da6-256">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-256">**Prototype**</span></span>

```c
UINT nx_http_client_get_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET **packet_ptr,
                              ULONG wait_option);
```

<span data-ttu-id="c4da6-257">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-257">**Description**</span></span>

<span data-ttu-id="c4da6-258">Эта служба извлекает следующий пакет содержимого ресурса, запрошенного предыдущим вызовом *nx_http_client_get_start*.</span><span class="sxs-lookup"><span data-stu-id="c4da6-258">This service retrieves the next packet of content of the resource requested by the previous *nx_http_client_get_start* call.</span></span> <span data-ttu-id="c4da6-259">Последовательные вызовы этой подпрограммы должны выполняться до получения состояния возврата NX_HTTP_GET_DONE.</span><span class="sxs-lookup"><span data-stu-id="c4da6-259">Successive calls to this routine should be made until the return status of NX_HTTP_GET_DONE is received.</span></span>

<span data-ttu-id="c4da6-260">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-260">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-261">**client_ptr**: указатель на блок управления HTTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="c4da6-261">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="c4da6-262">**packet_ptr**: назначение для указателя пакета, содержащего частичное содержимое ресурса</span><span class="sxs-lookup"><span data-stu-id="c4da6-262">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
- <span data-ttu-id="c4da6-263">**wait_option** определяет, как долго служба будет ожидать получение пакета HTTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="c4da6-263">**wait_option** Defines how long the service will wait for the HTTP Client get packet.</span></span> <span data-ttu-id="c4da6-264">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="c4da6-264">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c4da6-265">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c4da6-265">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c4da6-266">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="c4da6-266">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="c4da6-267">Выбор параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="c4da6-267">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="c4da6-268">Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c4da6-268">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="c4da6-269">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-269">**Return Values**</span></span>

- <span data-ttu-id="c4da6-270">**NX_SUCCESS** (0x00) — пакет получен HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="c4da6-270">**NX_SUCCESS** (0x00) Successful HTTP Client get packet.</span></span>
- <span data-ttu-id="c4da6-271">**NX_HTTP_GET_DONE** (0xEC) — получение пакета HTTP-клиентом выполнено.</span><span class="sxs-lookup"><span data-stu-id="c4da6-271">**NX_HTTP_GET_DONE** (0xEC) HTTP Client get packet is done</span></span>
- <span data-ttu-id="c4da6-272">**NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не находится в режиме получения.</span><span class="sxs-lookup"><span data-stu-id="c4da6-272">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not in get mode.</span></span>
- <span data-ttu-id="c4da6-273">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) — недопустимая длина пакета.</span><span class="sxs-lookup"><span data-stu-id="c4da6-273">**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
- <span data-ttu-id="c4da6-274">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-274">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="c4da6-275">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="c4da6-275">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="c4da6-276">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-276">**Allowed From**</span></span>

<span data-ttu-id="c4da6-277">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-277">Threads</span></span>

<span data-ttu-id="c4da6-278">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-278">**Example**</span></span>

```c
/* Get the next packet of resource content on the HTTP Client “my_client.”
Note that the nx_http_client_get_start routine must have been called
previously. */
status = nx_http_client_get_packet(&my_client, &next_packet, 1000);
 
/* If status is NX_SUCCESS, the next packet of content is pointed to by 
“next_packet”. */
```

## <a name="nx_http_client_put_start"></a><span data-ttu-id="c4da6-279">nx_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="c4da6-279">nx_http_client_put_start</span></span>

### <a name="start-an-http-put-request"></a><span data-ttu-id="c4da6-280">Запуск HTTP-запроса PUT</span><span class="sxs-lookup"><span data-stu-id="c4da6-280">Start an HTTP PUT request</span></span> 

<span data-ttu-id="c4da6-281">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-281">**Prototype**</span></span>

```c
UINT nx_http_client_put_start(NX_HTTP_CLIENT *client_ptr,
                             ULONG ip_address, CHAR *resource,
                             CHAR *username, CHAR *password,
                             ULONG total_bytes, ULONG wait_option);
```

<span data-ttu-id="c4da6-282">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-282">**Description**</span></span>

<span data-ttu-id="c4da6-283">Эта служба пытается отправить запрос PUT с указанным ресурсом к HTTP-серверу по указанному IP-адресу.</span><span class="sxs-lookup"><span data-stu-id="c4da6-283">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="c4da6-284">Если эта подпрограмма выполняется успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_http_client_put_packet*, чтобы фактически отправить содержимое ресурса на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="c4da6-284">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet* routine to actually send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="c4da6-285">Обратите внимание, что строка ресурса может ссылаться на локальный файл, например /index.htm, или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.</span><span class="sxs-lookup"><span data-stu-id="c4da6-285">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="c4da6-286">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="c4da6-286">This service is deprecated.</span></span> <span data-ttu-id="c4da6-287">Разработчикам рекомендуется перейти на использование *nx_http_client_put_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="c4da6-287">Developers are encouraged to migrate to *nx_http_client_put_start_extended()*.</span></span>

<span data-ttu-id="c4da6-288">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-288">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-289">**client_ptr**: указатель на блок управления HTTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="c4da6-289">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="c4da6-290">**ip_address**: IP-адрес HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-290">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="c4da6-291">**resource**: указатель на строку URL-адреса для ресурса, отправляемого на сервер</span><span class="sxs-lookup"><span data-stu-id="c4da6-291">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="c4da6-292">**username**: указатель на необязательное имя пользователя для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="c4da6-292">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="c4da6-293">**password**: указатель на необязательный пароль для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="c4da6-293">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="c4da6-294">**total_bytes**: общее число отправляемых байтов ресурса</span><span class="sxs-lookup"><span data-stu-id="c4da6-294">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="c4da6-295">Обратите внимание, что совокупная длина всех пакетов, отправленных через последующие вызовы *nx_http_client_put_packet*, должна равняться этому значению.</span><span class="sxs-lookup"><span data-stu-id="c4da6-295">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
- <span data-ttu-id="c4da6-296">**wait_option** определяет, как долго служба будет ожидать запуск запроса PUT HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="c4da6-296">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="c4da6-297">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="c4da6-297">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c4da6-298">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c4da6-298">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c4da6-299">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="c4da6-299">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="c4da6-300">Выбор параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="c4da6-300">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="c4da6-301">Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c4da6-301">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="c4da6-302">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-302">**Return Values**</span></span>

- <span data-ttu-id="c4da6-303">**NX_SUCCESS** (0x00) — запрос PUT успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="c4da6-303">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="c4da6-304">**NX_HTTP_USERNAME_TOO_LONG**</span><span class="sxs-lookup"><span data-stu-id="c4da6-304">**NX_HTTP_USERNAME_TOO_LONG**</span></span>
- <span data-ttu-id="c4da6-305">**(0xF1) — слишком длинное имя пользователя для буфера**.</span><span class="sxs-lookup"><span data-stu-id="c4da6-305">**(0xF1) Username too large for buffer**</span></span>
- <span data-ttu-id="c4da6-306">**NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="c4da6-306">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="c4da6-307">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-307">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="c4da6-308">NX_SIZE_ERROR (0x09) — недопустимый общий размер ресурса.</span><span class="sxs-lookup"><span data-stu-id="c4da6-308">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="c4da6-309">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="c4da6-309">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="c4da6-310">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-310">**Allowed From**</span></span>

<span data-ttu-id="c4da6-311">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-311">Threads</span></span>

<span data-ttu-id="c4da6-312">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-312">**Example**</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP 
Server at IP address 1.2.3.5. */
status = nx_http_client_put_start(&my_client, IP_ADDRESS(1, 2, 3, 5),
                                 “/TEST.HTM”, “myname”, “mypassword”, 20, 
                                 NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully 
been started. */
```

## <a name="nx_http_client_put_start_extended"></a><span data-ttu-id="c4da6-313">nx_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="c4da6-313">nx_http_client_put_start_extended</span></span>

### <a name="start-an-http-put-request"></a><span data-ttu-id="c4da6-314">Запуск HTTP-запроса PUT</span><span class="sxs-lookup"><span data-stu-id="c4da6-314">Start an HTTP PUT request</span></span>

<span data-ttu-id="c4da6-315">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-315">**Prototype**</span></span>

```c
UINT nx_http_client_put_start_extended(NX_HTTP_CLIENT *client_ptr,
     ULONG ip_address, CHAR *resource, UINT resource_length,
     CHAR *username,UINT username_length, CHAR *password,
     UINT password_length, ULONG total_bytes, ULONG wait_option);
```

<span data-ttu-id="c4da6-316">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-316">**Description**</span></span>

<span data-ttu-id="c4da6-317">Эта служба пытается отправить запрос PUT с указанным ресурсом к HTTP-серверу по указанному IP-адресу.</span><span class="sxs-lookup"><span data-stu-id="c4da6-317">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address.</span></span> <span data-ttu-id="c4da6-318">Если эта подпрограмма выполняется успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_http_client_put_packet*, чтобы фактически отправить содержимое ресурса на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="c4da6-318">If this routine is successful, the application code should make successive calls to the *nx_http_client_put_packet* routine to actually send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="c4da6-319">Обратите внимание, что строка ресурса может ссылаться на локальный файл, например /index.htm, или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.</span><span class="sxs-lookup"><span data-stu-id="c4da6-319">Note that the resource string can refer to a local file e.g. “/index.htm” or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="c4da6-320">Эта служба заменяет *nx_http_client_put_start()* .</span><span class="sxs-lookup"><span data-stu-id="c4da6-320">This service replaces *nx_http_client_put_start()*.</span></span> <span data-ttu-id="c4da6-321">Она требует от вызывающей стороны указания длины ресурса, имени пользователя и пароля.</span><span class="sxs-lookup"><span data-stu-id="c4da6-321">It requires caller to specify the length of the resource, username and password.</span></span>

<span data-ttu-id="c4da6-322">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-322">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-323">**client_ptr**: указатель на блок управления HTTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="c4da6-323">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="c4da6-324">**ip_address**: IP-адрес HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-324">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="c4da6-325">**resource**: указатель на строку URL-адреса для ресурса, отправляемого на сервер</span><span class="sxs-lookup"><span data-stu-id="c4da6-325">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="c4da6-326">**resource_length** Длина строки URL-адреса для ресурса, отправляемого на сервер.</span><span class="sxs-lookup"><span data-stu-id="c4da6-326">**resource_length** Length of URL string for resource to send to Server.</span></span>
- <span data-ttu-id="c4da6-327">**username**: указатель на необязательное имя пользователя для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="c4da6-327">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="c4da6-328">**username_length**: длина необязательного имени пользователя для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="c4da6-328">**username_length** Length of optional user name for authentication.</span></span>
- <span data-ttu-id="c4da6-329">**password**: указатель на необязательный пароль для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="c4da6-329">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="c4da6-330">**password_length**: длина необязательного пароля для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="c4da6-330">**password_length** Length of optional password for authentication.</span></span>
- <span data-ttu-id="c4da6-331">**total_bytes**: общее число отправляемых байтов ресурса</span><span class="sxs-lookup"><span data-stu-id="c4da6-331">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="c4da6-332">Обратите внимание, что совокупная длина всех пакетов, отправленных через последующие вызовы *nx_http_client_put_packet*, должна равняться этому значению.</span><span class="sxs-lookup"><span data-stu-id="c4da6-332">Note that the combined length of all packets sent via subsequent calls to *nx_http_client_put_packet* must equal this value.</span></span>
- <span data-ttu-id="c4da6-333">**wait_option** определяет, как долго служба будет ожидать запуск запроса PUT HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="c4da6-333">**wait_option** Defines how long the service will wait for the HTTP Client PUT start.</span></span> <span data-ttu-id="c4da6-334">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="c4da6-334">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c4da6-335">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c4da6-335">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c4da6-336">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="c4da6-336">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="c4da6-337">Выбор параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="c4da6-337">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /><span data-ttu-id="c4da6-338">Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c4da6-338">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="c4da6-339">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-339">**Return Values**</span></span>

- <span data-ttu-id="c4da6-340">**NX_SUCCESS** (0x00) — запрос PUT успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="c4da6-340">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="c4da6-341">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) — слишком длинное имя пользователя для буфера</span><span class="sxs-lookup"><span data-stu-id="c4da6-341">**NX_HTTP_USERNAME_TOO_LONG** (0xF1) Username too large for buffer</span></span>
- <span data-ttu-id="c4da6-342">**NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="c4da6-342">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="c4da6-343">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-343">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="c4da6-344">NX_SIZE_ERROR (0x09) — недопустимый общий размер ресурса.</span><span class="sxs-lookup"><span data-stu-id="c4da6-344">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="c4da6-345">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="c4da6-345">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="c4da6-346">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-346">**Allowed From**</span></span>

<span data-ttu-id="c4da6-347">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-347">Threads</span></span>

<span data-ttu-id="c4da6-348">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-348">**Example**</span></span>

```c
/* Start an HTTP PUT to place the 20-byte resource “/TEST.HTM” on the HTTP 
Server at IP address 1.2.3.5. */
status = nx_http_client_put_start_extended(&my_client, IP_ADDRESS(1, 2, 3, 5),
                                          “/TEST.HTM”, 9, “myname”, 6, 
                                          “mypassword”, 
                                          10, 20, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the PUT operation for TEST.HTM has successfully 
been started. */
```

## <a name="nx_http_client_put_packet"></a><span data-ttu-id="c4da6-349">nx_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="c4da6-349">nx_http_client_put_packet</span></span>

### <a name="send-next-resource-data-packet"></a><span data-ttu-id="c4da6-350">Отправка следующего пакета данных ресурса</span><span class="sxs-lookup"><span data-stu-id="c4da6-350">Send next resource data packet</span></span>

<span data-ttu-id="c4da6-351">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-351">**Prototype**</span></span>

```c
UINT nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                              NX_PACKET *packet_ptr,
                              ULONG wait_option);
```

<span data-ttu-id="c4da6-352">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-352">**Description**</span></span>

<span data-ttu-id="c4da6-353">Эта служба пытается отправить следующий пакет содержимого ресурса на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="c4da6-353">This service attempts to send the next packet of resource content to the HTTP Server.</span></span> <span data-ttu-id="c4da6-354">Обратите внимание, что эту подпрограмму следует вызывать несколько раз до тех пор, пока суммарная длина отправляемых пакетов не будет равна значению total_bytes, указанному в предыдущем вызове *nx_http_client_put_start()* .</span><span class="sxs-lookup"><span data-stu-id="c4da6-354">Note that this routine should be called repetitively until the combined length of the packets sent equals the “total_bytes” specified in the previous *nx_http_client_put_start()* call.</span></span>

<span data-ttu-id="c4da6-355">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-355">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-356">**client_ptr**: указатель на блок управления HTTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="c4da6-356">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="c4da6-357">**packet_ptr**: указатель на следующее содержимое ресурса, отправляемого на HTTP-сервер</span><span class="sxs-lookup"><span data-stu-id="c4da6-357">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
- <span data-ttu-id="c4da6-358">**wait_option** определяет, как долго служба будет внутренне ожидать обработки пакета PUT HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="c4da6-358">**wait_option** Defines how long the service will wait internally to process the HTTP Client PUT packet.</span></span> <span data-ttu-id="c4da6-359">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="c4da6-359">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="c4da6-360">**Значение времени ожидания** (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="c4da6-360">**timeout value** (0x00000001 through 0xFFFFFFFE)</span></span>
  - <span data-ttu-id="c4da6-361">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="c4da6-361">**TX_WAIT_FOREVER** (0xFFFFFFFF)</span></span><br /><span data-ttu-id="c4da6-362">Выбор параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="c4da6-362">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span><br /> <span data-ttu-id="c4da6-363">Числовое значение (0x1–0xFFFFFFFE) задает максимальное количество тактов таймера для нахождения в состоянии приостановки при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c4da6-363">Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

<span data-ttu-id="c4da6-364">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-364">**Return Values**</span></span>

- <span data-ttu-id="c4da6-365">**NX_SUCCESS** (0x00) — пакет HTTP-клиента успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="c4da6-365">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
- <span data-ttu-id="c4da6-366">**NX_HTTP_NOT_READY** (0xEA) — HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="c4da6-366">**NX_HTTP_NOT_READY** (0xEA) HTTP Client not ready</span></span>
- <span data-ttu-id="c4da6-367">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) — получен код ошибки сервера **-**NX_HTTP_BAD_PACKET_LENGTH\*\* (0xED) — недопустимая длина пакета.</span><span class="sxs-lookup"><span data-stu-id="c4da6-367">**NX_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0xEE) Received Server error code\*\* -**NX_HTTP_BAD_PACKET_LENGTH** (0xED) Invalid packet length</span></span>
- <span data-ttu-id="c4da6-368">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) — недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="c4da6-368">**NX_HTTP_AUTHENTICATION_ERROR** (0xEB) Invalid name and/or Password</span></span>
- <span data-ttu-id="c4da6-369">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) — сервер отвечает до завершения запроса PUT.</span><span class="sxs-lookup"><span data-stu-id="c4da6-369">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Server responds before PUT Is complete</span></span>
- <span data-ttu-id="c4da6-370">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-370">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="c4da6-371">NX_INVALID_PACKET (0x12) — слишком маленький пакет для заголовка TCP</span><span class="sxs-lookup"><span data-stu-id="c4da6-371">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
- <span data-ttu-id="c4da6-372">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="c4da6-372">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="c4da6-373">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-373">**Allowed From**</span></span>

<span data-ttu-id="c4da6-374">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-374">Threads</span></span>

<span data-ttu-id="c4da6-375">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-375">**Example**</span></span>

```c
/* Send a 20-byte packet representing the content of the resource
“/TEST.HTM” to the HTTP Server. */
status = nx_http_client_put_packet(NX_HTTP_CLIENT *client_ptr,
                                  NX_PACKET *packet_ptr,
                                  ULONG wait_option);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM
has successfully been sent. */
```

## <a name="nx_http_client_set_connect_port"></a><span data-ttu-id="c4da6-376">nx_http_client_set_connect_port</span><span class="sxs-lookup"><span data-stu-id="c4da6-376">nx_http_client_set_connect_port</span></span>

### <a name="set-the-connection-port-to-the-server"></a><span data-ttu-id="c4da6-377">Задание порта подключения к серверу</span><span class="sxs-lookup"><span data-stu-id="c4da6-377">Set the connection port to the Server</span></span>

<span data-ttu-id="c4da6-378">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-378">**Prototype**</span></span>

```c
UINT nx_http_client_set_connect_port(NX_HTTP_CLIENT *client_ptr,
                                    UINT port);
```

<span data-ttu-id="c4da6-379">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-379">**Description**</span></span>

<span data-ttu-id="c4da6-380">Эта служба изменяет порт подключения при подключении к HTTP-серверу на указанный порт во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="c4da6-380">This service changes the connect port when connecting to the HTTP Server to the specified port at runtime.</span></span> <span data-ttu-id="c4da6-381">В противном случае по умолчанию используется порт 80.</span><span class="sxs-lookup"><span data-stu-id="c4da6-381">Otherwise the connect port defaults to 80.</span></span> <span data-ttu-id="c4da6-382">Эту службу необходимо вызвать до *nx_http_client_get_start*() и *nx_http_client_put_start*(), например когда HTTP-клиент подключается к серверу.</span><span class="sxs-lookup"><span data-stu-id="c4da6-382">This must be called before *nx_http_client_get_start*() and *nx_http_client_put_start*() e.g. when the HTTP Client connects with the Server.</span></span>

<span data-ttu-id="c4da6-383">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-383">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-384">**client_ptr**: указатель на блок управления HTTP-клиентом</span><span class="sxs-lookup"><span data-stu-id="c4da6-384">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="c4da6-385">**port**: порт для подключения к серверу</span><span class="sxs-lookup"><span data-stu-id="c4da6-385">**port** Port for connecting to the Server.</span></span>

<span data-ttu-id="c4da6-386">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-386">**Return Values**</span></span>

- <span data-ttu-id="c4da6-387">**NX_SUCCESS** (0x00) — порт подключения успешно изменен.</span><span class="sxs-lookup"><span data-stu-id="c4da6-387">**NX_SUCCESS** (0x00) Successfully changed the connect port</span></span>
- <span data-ttu-id="c4da6-388">**NX_INVALID_PORT** (0x46) — превышено максимальное значение номера порта (0xFFFF), или номер равен нулю.</span><span class="sxs-lookup"><span data-stu-id="c4da6-388">**NX_INVALID_PORT** (0x46) Port exceeds the maximum (0xFFFF) or is zero.</span></span>
- <span data-ttu-id="c4da6-389">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-389">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="c4da6-390">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-390">**Allowed From**</span></span>

<span data-ttu-id="c4da6-391">Потоки, инициализация</span><span class="sxs-lookup"><span data-stu-id="c4da6-391">Threads, Initialization</span></span>

<span data-ttu-id="c4da6-392">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-392">**Example**</span></span>

```c
NX_HTTP_CLIENT *client_ptr;

/* Change the connect port to 114. */
status = nx_http_client_set_connect_port(client_ptr, 114);

/* If status is NX_SUCCESS, the connect port is successfully changed. */
```

## <a name="nx_http_server_cache_info_callback_set"></a><span data-ttu-id="c4da6-393">nx_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="c4da6-393">nx_http_server_cache_info_callback_set</span></span>

### <a name="set-the-callback-to-retrieve-url-max-age-and-date"></a><span data-ttu-id="c4da6-394">Задание обратного вызова для получения максимального возраста и даты последнего изменения URL-адреса</span><span class="sxs-lookup"><span data-stu-id="c4da6-394">Set the callback to retrieve URL max age and date</span></span>

<span data-ttu-id="c4da6-395">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-395">**Prototype**</span></span>

```c
UINT nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                           UINT (*cache_info_get)(CHAR *resource,
                                           UINT *max_age,
                                           NX_HTTP_SERVER_DATE *date));
```

<span data-ttu-id="c4da6-396">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-396">**Description**</span></span>

<span data-ttu-id="c4da6-397">Эта служба задает службу обратного вызова, вызываемую для получения максимального возраста и даты последнего изменения указанного ресурса.</span><span class="sxs-lookup"><span data-stu-id="c4da6-397">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

<span data-ttu-id="c4da6-398">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-398">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-399">**server_ptr**: указатель на управляющий блок HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-399">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="c4da6-400">**cache_info_get**: указатель на обратный вызов</span><span class="sxs-lookup"><span data-stu-id="c4da6-400">**cache_info_get** Pointer to the callback</span></span>
- <span data-ttu-id="c4da6-401">**max_age**: указатель на максимальный возраст ресурса</span><span class="sxs-lookup"><span data-stu-id="c4da6-401">**max_age** Pointer to maximum age of a resource</span></span>
- <span data-ttu-id="c4da6-402">**data**: указатель на возвращенную дату последнего изменения</span><span class="sxs-lookup"><span data-stu-id="c4da6-402">**data** Pointer to last modified date returned.</span></span>

<span data-ttu-id="c4da6-403">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-403">**Return Values**</span></span>

- <span data-ttu-id="c4da6-404">**NX_SUCCESS** (0x00) — обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="c4da6-404">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="c4da6-405">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-405">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="c4da6-406">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-406">**Allowed From**</span></span>

<span data-ttu-id="c4da6-407">Инициализация</span><span class="sxs-lookup"><span data-stu-id="c4da6-407">Initialization</span></span>

<span data-ttu-id="c4da6-408">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-408">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;
UINT cache_info_get(CHAR *resource, UINT *max_age,
                   NX_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_http_server_create and before the HTTP
server is set by nx_http_server_start(), set the cache info callback: */
status = nx_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_http_server_callback_data_send"></a><span data-ttu-id="c4da6-409">nx_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="c4da6-409">nx_http_server_callback_data_send</span></span>

### <a name="send-data-from-callback-function"></a><span data-ttu-id="c4da6-410">Отправка данных из функции обратного вызова</span><span class="sxs-lookup"><span data-stu-id="c4da6-410">Send data from callback function</span></span>

<span data-ttu-id="c4da6-411">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-411">**Prototype**</span></span>

```c
UINT nx_http_server_callback_data_send(NX_HTTP_SERVER *server_ptr,
                                      VOID *data_ptr,
                                      ULONG data_length);
```

<span data-ttu-id="c4da6-412">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-412">**Description**</span></span>

<span data-ttu-id="c4da6-413">Эта служба отправляет данные в предоставленном пакете из подпрограммы обратного вызова приложения.</span><span class="sxs-lookup"><span data-stu-id="c4da6-413">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="c4da6-414">Обычно она используется для отправки динамических данных, связанных с запросами GET/POST.</span><span class="sxs-lookup"><span data-stu-id="c4da6-414">This is typically used to send dynamic data associated with GET/POST requests.</span></span> <span data-ttu-id="c4da6-415">Обратите внимание, что, если используется эта функция, подпрограмма обратного вызова отвечает за отправку всего ответа в правильном формате.</span><span class="sxs-lookup"><span data-stu-id="c4da6-415">Note that if this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="c4da6-416">Кроме того, подпрограмма обратного вызова должна возвращать состояние NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="c4da6-416">In addition, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="c4da6-417">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-417">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-418">**server_ptr**: указатель на управляющий блок HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-418">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="c4da6-419">**data_ptr**: указатель на данные для отправки</span><span class="sxs-lookup"><span data-stu-id="c4da6-419">**data_ptr** Pointer to the data to send.</span></span>
- <span data-ttu-id="c4da6-420">**data_length**: число отправляемых байтов</span><span class="sxs-lookup"><span data-stu-id="c4da6-420">**data_length** Number of bytes to send.</span></span>

<span data-ttu-id="c4da6-421">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-421">**Return Values**</span></span>

- <span data-ttu-id="c4da6-422">**NX_SUCCESS** (0x00) — данные сервера успешно отправлены.</span><span class="sxs-lookup"><span data-stu-id="c4da6-422">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
- <span data-ttu-id="c4da6-423">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-423">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="c4da6-424">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-424">**Allowed From**</span></span>

<span data-ttu-id="c4da6-425">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-425">Threads</span></span>

<span data-ttu-id="c4da6-426">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-426">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
    if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
       (strcmp(resource, "/test.htm") == 0))
    {
        /* Found it, override the GET processing by sending the resource
        contents directly. */

        nx_http_server_callback_data_send(server_ptr,
                                         "HTTP/1.0 200 \r\nContent-Length:
                                         103\r\nContent-Type: text/html\r\n\r\n",
                                         63);
        nx_http_server_callback_data_send(server_ptr, "<HTML>> r\n<HEAD><TITLE>NetX
                                         HTTP Test </TITLE></HEAD>\r\n
                                         <BODY>\r\n<H1>NetX Test Page
                                         </H1>\r\n</BODY>> r\n</HTML>\r\n", 103);
        /* Return completion status. */
        return(NX_HTTP_CALLBACK_COMPLETED);
    }
    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_callback_generate_response_header"></a><span data-ttu-id="c4da6-427">nx_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="c4da6-427">nx_http_server_callback_generate_response_header</span></span>

### <a name="create-a-response-header-in-a-callback-function"></a><span data-ttu-id="c4da6-428">Создание заголовка ответа в функции обратного вызова</span><span class="sxs-lookup"><span data-stu-id="c4da6-428">Create a response header in a callback function</span></span>

<span data-ttu-id="c4da6-429">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-429">**Prototype**</span></span>

```c
UINT nx_http_server_callback_generate_response_header(NX_HTTP_SERVER *server_ptr,
     NX_PACKET **packet_pptr, CHAR *status_code, UINT content_length,
     CHAR *content_type, CHAR* additional_header);
```

<span data-ttu-id="c4da6-430">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-430">**Description**</span></span>

<span data-ttu-id="c4da6-431">Эта служба вызывает внутреннюю функцию _ *nx_http_server_generate_response_header*, когда HTTP-сервер отвечает на запросы GET, PUT и DELETE клиента.</span><span class="sxs-lookup"><span data-stu-id="c4da6-431">This service calls the internal function _ *nx_http_server_generate_response_header* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="c4da6-432">Она предназначена для использования в функциях обратного вызова HTTP-сервера, когда приложение HTTP-сервера формирует ответ клиенту.</span><span class="sxs-lookup"><span data-stu-id="c4da6-432">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="c4da6-433">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="c4da6-433">This service is deprecated.</span></span> <span data-ttu-id="c4da6-434">Разработчикам рекомендуется перейти на *nxd_http_server_callback_generate_response_header_extended()* .</span><span class="sxs-lookup"><span data-stu-id="c4da6-434">Developers are encouraged to migrate to *nxd_http_server_callback_generate_response_header_extended()*.</span></span>

<span data-ttu-id="c4da6-435">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-435">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-436">**server_ptr**: указатель на управляющий блок HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-436">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="c4da6-437">**packet_pptr**: указатель на указатель пакета, выделенный для сообщения</span><span class="sxs-lookup"><span data-stu-id="c4da6-437">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="c4da6-438">**status_code**: указывает состояние ресурса</span><span class="sxs-lookup"><span data-stu-id="c4da6-438">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="c4da6-439">Примеры:</span><span class="sxs-lookup"><span data-stu-id="c4da6-439">Examples:</span></span>
- <span data-ttu-id="c4da6-440">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="c4da6-440">**NX_HTTP_STATUS_OK**</span></span>
- <span data-ttu-id="c4da6-441">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="c4da6-441">**NX_HTTP_STATUS_MODIFIED**</span></span>
- <span data-ttu-id="c4da6-442">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="c4da6-442">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="c4da6-443">**content_length**: размер содержимого в байтах</span><span class="sxs-lookup"><span data-stu-id="c4da6-443">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="c4da6-444">**content_type**: тип HTTP, например text/plain</span><span class="sxs-lookup"><span data-stu-id="c4da6-444">**content_type** Type of HTTP e.g. “text/plain”</span></span>
- <span data-ttu-id="c4da6-445">**additional_header**: указатель на дополнительный текст заголовка</span><span class="sxs-lookup"><span data-stu-id="c4da6-445">**additional_header** Pointer to additional header text</span></span>

<span data-ttu-id="c4da6-446">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-446">**Return Values**</span></span>

- <span data-ttu-id="c4da6-447">**NX_SUCCESS** (0x00) — заголовок HTML успешно создан.</span><span class="sxs-lookup"><span data-stu-id="c4da6-447">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="c4da6-448">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-448">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="c4da6-449">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-449">**Allowed From**</span></span>

<span data-ttu-id="c4da6-450">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-450">Threads</span></span>

<span data-ttu-id="c4da6-451">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-451">**Example**</span></span>

```c
CHAR demotestbuffer[] = “<html>\r\n\r\n<head> r\n\r\n<title>Main                 \
                        Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n  \ 
                        </body>\r\n</html>\r\n";

/* my_request_notify is the application request notify callback registered with
the HTTP server in nx_http_server_create, creates a response to the received
Client request. */

UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *recv_packet_ptr)
{
    NX_PACKET     *sresp_packet_ptr;
    ULONG         string_length;
    CHAR          temp_string[30];
    ULONG         length = 0;

        length = sizeof(demotestbuffer) - 1;

/* Derive the client request type from the client request. */
   string_length = (ULONG) nx_http_server_type_get(server_ptr, server_ptr ->
                   nx_http_server_request_resource, temp_string);

/* Null terminate the string. */
   temp_string[temp] = 0;

/* Now build a response header with server status is OK and no additional header info. */
   status = nx_http_server_callback_generate_response_header(http_server_ptr,
            &resp_packet_ptr, NX_HTTP_STATUS_OK,
            length, temp_string, NX_NULL);

/* If status is NX_SUCCESS, the header was successfully appended. */

/* Now add data to the packet. */
   status = nx_packet_data_append(resp_packet_ptr, &demotestbuffer[0],
            length, server_ptr >>
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

## <a name="nx_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="c4da6-452">nx_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="c4da6-452">nx_http_server_callback_generate_response_header_extended</span></span>

### <a name="create-a-response-header-in-a-callback-function"></a><span data-ttu-id="c4da6-453">Создание заголовка ответа в функции обратного вызова</span><span class="sxs-lookup"><span data-stu-id="c4da6-453">Create a response header in a callback function</span></span>

<span data-ttu-id="c4da6-454">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-454">**Prototype**</span></span>

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

<span data-ttu-id="c4da6-455">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-455">**Description**</span></span>

<span data-ttu-id="c4da6-456">Эта служба вызывает внутреннюю функцию _ *nx_http_server_generate_response_header()* , когда HTTP-сервер отвечает на запросы GET, PUT и DELETE клиента.</span><span class="sxs-lookup"><span data-stu-id="c4da6-456">This service calls the internal function _ *nx_http_server_generate_response_header()* when the HTTP server responds to Client get, put and delete requests.</span></span> <span data-ttu-id="c4da6-457">Она предназначена для использования в функциях обратного вызова HTTP-сервера, когда приложение HTTP-сервера формирует ответ клиенту.</span><span class="sxs-lookup"><span data-stu-id="c4da6-457">It is intended for use in HTTP server callback functions when the HTTP server application is designing its response to the Client.</span></span>

<span data-ttu-id="c4da6-458">Эта служба заменяет *nx_http_server_callback_generate_response_header()* .</span><span class="sxs-lookup"><span data-stu-id="c4da6-458">This service replaces *nx_http_server_callback_generate_response_header()*.</span></span> <span data-ttu-id="c4da6-459">Эта версия предоставляет дополнительные сведения о длине функции обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="c4da6-459">This version supplies additional length information to the callback function.</span></span>

<span data-ttu-id="c4da6-460">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-460">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-461">**server_ptr**: указатель на управляющий блок HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-461">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="c4da6-462">**packet_pptr**: указатель на указатель пакета, выделенный для сообщения</span><span class="sxs-lookup"><span data-stu-id="c4da6-462">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="c4da6-463">**status_code**: указывает состояние ресурса</span><span class="sxs-lookup"><span data-stu-id="c4da6-463">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="c4da6-464">Примеры:</span><span class="sxs-lookup"><span data-stu-id="c4da6-464">Examples:</span></span>
  - <span data-ttu-id="c4da6-465">**NX_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="c4da6-465">**NX_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="c4da6-466">**NX_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="c4da6-466">**NX_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="c4da6-467">**NX_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="c4da6-467">**NX_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="c4da6-468">**status_code** Длина кода состояния.</span><span class="sxs-lookup"><span data-stu-id="c4da6-468">**status_code** Length of status code</span></span>
- <span data-ttu-id="c4da6-469">**content_length**: размер содержимого в байтах</span><span class="sxs-lookup"><span data-stu-id="c4da6-469">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="c4da6-470">**content_type**: тип HTTP, например text/plain</span><span class="sxs-lookup"><span data-stu-id="c4da6-470">**content_type** Type of HTTP e.g. “text/plain”</span></span>
- <span data-ttu-id="c4da6-471">**content_type_length**: длина типа HTTP</span><span class="sxs-lookup"><span data-stu-id="c4da6-471">**content_type_length** Length of HTTP type</span></span>
- <span data-ttu-id="c4da6-472">**additional_header**: указатель на дополнительный текст заголовка</span><span class="sxs-lookup"><span data-stu-id="c4da6-472">**additional_header** Pointer to additional header text</span></span>
- <span data-ttu-id="c4da6-473">**additional_header_length**: длина дополнительного текста заголовка</span><span class="sxs-lookup"><span data-stu-id="c4da6-473">**additional_header_length** Length of additional header text</span></span>

<span data-ttu-id="c4da6-474">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-474">**Return Values**</span></span>

- <span data-ttu-id="c4da6-475">**NX_SUCCESS** (0x00) — заголовок успешно создан.</span><span class="sxs-lookup"><span data-stu-id="c4da6-475">**NX_SUCCESS** (0x00) Successfully created header</span></span>
- <span data-ttu-id="c4da6-476">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-476">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="c4da6-477">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-477">**Allowed From**</span></span>

<span data-ttu-id="c4da6-478">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-478">Threads</span></span>

<span data-ttu-id="c4da6-479">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-479">**Example**</span></span>

```c
  CHAR demotestbuffer[] = “<html>\r\n\r\n<head>\r\n\r\n<title>Main                    \
                          Window</title>\r\n</head>\r\n\r\n<body>Test message\r\n     \
                          </body>\r\n</html>\r\n";

/* my_request_notify is the application request notify callback registered with
   the HTTP server in nx_http_server_create, creates a response to the received
   Client request. */

   UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                         CHAR *resource, NX_PACKET *recv_packet_ptr)
   {
     NX_PACKET *sresp_packet_ptr;
     ULONG string_length;
     CHAR temp_string[30];
     ULONG length = 0;

     length = sizeof(demotestbuffer) - 1;

    /* Derive the client request type from the client request. */
       string_length = (ULONG) nx_http_server_type_retrieve(server_ptr, server_ptr >>
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
                length, server_ptr ->
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

## <a name="nx_http_server_callback_packet_send"></a><span data-ttu-id="c4da6-480">nx_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="c4da6-480">nx_http_server_callback_packet_send</span></span>

### <a name="send-an-http-packet-from-callback-function"></a><span data-ttu-id="c4da6-481">Отправка пакета HTTP из функции обратного вызова</span><span class="sxs-lookup"><span data-stu-id="c4da6-481">Send an HTTP packet from callback function</span></span>

<span data-ttu-id="c4da6-482">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-482">**Prototype**</span></span>

```c
UINT nx_http_server_callback_packet_send(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr);
```

<span data-ttu-id="c4da6-483">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-483">**Description**</span></span>

<span data-ttu-id="c4da6-484">Эта служба отправляет полный ответ HTTP-сервера из обратного вызова HTTP.</span><span class="sxs-lookup"><span data-stu-id="c4da6-484">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="c4da6-485">HTTP-сервер отправит пакет с NX_HTTP_SERVER_TIMEOUT_SEND.</span><span class="sxs-lookup"><span data-stu-id="c4da6-485">HTTP server will send the packet with the NX_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="c4da6-486">К пакету должны быть добавлены заголовок и данные HTTP.</span><span class="sxs-lookup"><span data-stu-id="c4da6-486">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="c4da6-487">Если возвращаемое состояние указывает на ошибку, приложение HTTP должно освободить пакет.</span><span class="sxs-lookup"><span data-stu-id="c4da6-487">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="c4da6-488">Обратный вызов должен возвращать NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="c4da6-488">The callback should return NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="c4da6-489">Более подробный пример см. в разделе *nx_http_server_callback_generate_response_header()* .</span><span class="sxs-lookup"><span data-stu-id="c4da6-489">See *nx_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

<span data-ttu-id="c4da6-490">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-490">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-491">**server_ptr**: указатель на управляющий блок HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-491">**server_ptr** Pointer to HTTP Server control block</span></span>
- <span data-ttu-id="c4da6-492">**packet_ptr**: указатель на пакет для отправки</span><span class="sxs-lookup"><span data-stu-id="c4da6-492">**packet_ptr** Pointer to the packet to send</span></span>

<span data-ttu-id="c4da6-493">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-493">**Return Values**</span></span>

- <span data-ttu-id="c4da6-494">**NX_SUCCESS** (0x00) — пакет HTTP-сервера успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="c4da6-494">**NX_SUCCESS** (0x00) Successfully sent HTTP Server packet</span></span>
- <span data-ttu-id="c4da6-495">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-495">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

<span data-ttu-id="c4da6-496">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-496">**Allowed From**</span></span>

<span data-ttu-id="c4da6-497">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-497">Threads</span></span>

<span data-ttu-id="c4da6-498">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-498">**Example**</span></span>

```c
/* The packet is appended with HTTP header and data and is ready to send to the
Client directly. */

   status = nx_http_server_callback_response_send**(server_ptr, packet_ptr);
   
   if (status != NX_SUCCESS)
   {
        nx_packet_release(packet_ptr);
   }
    return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_callback_response_send"></a><span data-ttu-id="c4da6-499">nx_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="c4da6-499">nx_http_server_callback_response_send</span></span>

### <a name="send-response-from-callback-function"></a><span data-ttu-id="c4da6-500">Отправка ответа из функции обратного вызова</span><span class="sxs-lookup"><span data-stu-id="c4da6-500">Send response from callback function</span></span>

<span data-ttu-id="c4da6-501">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-501">**Prototype**</span></span>

```c
UINT nx_http_server_callback_response_send(NX_HTTP_SERVER *server_ptr,
     CHAR *header, CHAR *information, CHAR additional_info);
```

<span data-ttu-id="c4da6-502">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-502">**Description**</span></span>

<span data-ttu-id="c4da6-503">Эта служба отправляет указанные сведения об ответе из подпрограммы обратного вызова приложения.</span><span class="sxs-lookup"><span data-stu-id="c4da6-503">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="c4da6-504">Обычно она используется для отправки пользовательских ответов, связанных с запросами GET/POST.</span><span class="sxs-lookup"><span data-stu-id="c4da6-504">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="c4da6-505">Обратите внимание, что, если используется эта функция, подпрограмма обратного вызова должна возвращать состояние NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="c4da6-505">Note that if this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="c4da6-506">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="c4da6-506">This service is deprecated.</span></span> <span data-ttu-id="c4da6-507">Разработчикам рекомендуется перейти на *nx_http_server_callback_response_send_extended()* .</span><span class="sxs-lookup"><span data-stu-id="c4da6-507">Developers are encouraged to migrate to *nx_http_server_callback_response_send_extended().*</span></span>

<span data-ttu-id="c4da6-508">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-508">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-509">**server_ptr**: указатель на управляющий блок HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-509">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="c4da6-510">**header**: указатель на строку заголовка ответа</span><span class="sxs-lookup"><span data-stu-id="c4da6-510">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="c4da6-511">**information**: указатель на строку информации</span><span class="sxs-lookup"><span data-stu-id="c4da6-511">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="c4da6-512">**additional_info**: указатель на строку дополнительной информации</span><span class="sxs-lookup"><span data-stu-id="c4da6-512">**additional_info** Pointer to the additional information string.</span></span>

<span data-ttu-id="c4da6-513">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-513">**Return Values**</span></span>

- <span data-ttu-id="c4da6-514">**NX_SUCCESS** (0x00) — ответ HTTP-сервера успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="c4da6-514">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

<span data-ttu-id="c4da6-515">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-515">**Allowed From**</span></span>

<span data-ttu-id="c4da6-516">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-516">Threads</span></span>

<span data-ttu-id="c4da6-517">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-517">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
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

## <a name="nx_http_server_callback_response_send_extended"></a><span data-ttu-id="c4da6-518">nx_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="c4da6-518">nx_http_server_callback_response_send_extended</span></span>

### <a name="send-response-from-callback-function"></a><span data-ttu-id="c4da6-519">Отправка ответа из функции обратного вызова</span><span class="sxs-lookup"><span data-stu-id="c4da6-519">Send response from callback function</span></span>

<span data-ttu-id="c4da6-520">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-520">**Prototype**</span></span>

```c
UINT nx_http_server_callback_response_send_extended(
     NX_HTTP_SERVER *server_ptr, CHAR *heade
     UINT header_length, CHAR *information,
     UINT information_length, CHAR *additional_info,
     UINT additional_info_length);
```

<span data-ttu-id="c4da6-521">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-521">**Description**</span></span>

<span data-ttu-id="c4da6-522">Эта служба отправляет указанные сведения об ответе из подпрограммы обратного вызова приложения.</span><span class="sxs-lookup"><span data-stu-id="c4da6-522">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="c4da6-523">Обычно она используется для отправки пользовательских ответов, связанных с запросами GET/POST.</span><span class="sxs-lookup"><span data-stu-id="c4da6-523">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="c4da6-524">Обратите внимание, что, если используется эта функция, подпрограмма обратного вызова должна возвращать состояние NX_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="c4da6-524">Note that if this function is used, the callback routine must return the status of NX_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="c4da6-525">Эта служба заменяет *nx_http_server_callback_response_send()* .</span><span class="sxs-lookup"><span data-stu-id="c4da6-525">This service replaces *nx_http_server_callback_response_send().*</span></span> <span data-ttu-id="c4da6-526">Эта версия принимает сведения о длине в качестве входного аргумента.</span><span class="sxs-lookup"><span data-stu-id="c4da6-526">This version takes length information as input argument.</span></span>

<span data-ttu-id="c4da6-527">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-527">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-528">**server_ptr**: указатель на управляющий блок HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-528">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="c4da6-529">**header**: указатель на строку заголовка ответа</span><span class="sxs-lookup"><span data-stu-id="c4da6-529">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="c4da6-530">**header_length**: длина строки заголовка ответа.</span><span class="sxs-lookup"><span data-stu-id="c4da6-530">**header_length** Length of the response header string.</span></span>
- <span data-ttu-id="c4da6-531">**information**: указатель на строку информации</span><span class="sxs-lookup"><span data-stu-id="c4da6-531">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="c4da6-532">**information_length**: длина строки информации</span><span class="sxs-lookup"><span data-stu-id="c4da6-532">**information_length** Length of the information string.</span></span>
- <span data-ttu-id="c4da6-533">**additional_info**: указатель на строку дополнительной информации</span><span class="sxs-lookup"><span data-stu-id="c4da6-533">**additional_info** Pointer to the additional information string.</span></span>
- <span data-ttu-id="c4da6-534">**additional_info_length**: длина строки дополнительной информации</span><span class="sxs-lookup"><span data-stu-id="c4da6-534">**additional_info_length** Length of the additional information string.</span></span>

<span data-ttu-id="c4da6-535">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-535">**Return Values**</span></span>

- <span data-ttu-id="c4da6-536">**NX_SUCCESS** (0x00) — ответ сервера успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="c4da6-536">**NX_SUCCESS** (0x00) Successfully sent Server response</span></span>

<span data-ttu-id="c4da6-537">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-537">**Allowed From**</span></span>

<span data-ttu-id="c4da6-538">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-538">Threads</span></span>

<span data-ttu-id="c4da6-539">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-539">**Example**</span></span>

```c
UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

    /* Look for the test resource! */
       if ((request_type == NX_HTTP_SERVER_GET_REQUEST) &&
          (strcmp(resource, "/test.htm") == 0))
    {
        /* In this example, we will complete the GET processing with
           a resource not found response. */
           nx_http_server_callback_response_send_extended(server_ptr,
                                                         "HTTP/1.0 404 ", 12,
                                                         "NetX HTTP Server unable to find
                                                         file: ", 38, resource, 9);
        /* Return completion status. */
           return(NX_HTTP_CALLBACK_COMPLETED);
    }
    return(NX_SUCCESS);
}
```

## <a name="nx_http_server_content_get"></a><span data-ttu-id="c4da6-540">nx_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="c4da6-540">nx_http_server_content_get</span></span>

### <a name="get-content-from-the-request"></a><span data-ttu-id="c4da6-541">Получение содержимого из запроса</span><span class="sxs-lookup"><span data-stu-id="c4da6-541">Get content from the request</span></span>

<span data-ttu-id="c4da6-542">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-542">**Prototype**</span></span>

```c
UINT nx_http_server_content_get(NX_HTTP_SERVER *server_ptr,
                                NX_PACKET *packet_ptr,
                                ULONG byte_offset,
                                CHAR *destination_ptr,
                                UINT destination_size,
                                UINT *actual_size);
```

<span data-ttu-id="c4da6-543">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-543">**Description**</span></span>

<span data-ttu-id="c4da6-544">Эта служба пытается получить указанный объем содержимого из запроса POST или PUT HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="c4da6-544">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="c4da6-545">Ее следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="c4da6-545">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="c4da6-546">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="c4da6-546">This service is deprecated.</span></span> <span data-ttu-id="c4da6-547">Разработчикам рекомендуется перейти на использование nx_http_server_content_get_extended().</span><span class="sxs-lookup"><span data-stu-id="c4da6-547">Developers are encouraged to migrate to nx_http_server_content_get_extended().</span></span>

<span data-ttu-id="c4da6-548">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-548">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-549">**server_ptr**: указатель на управляющий блок HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-549">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="c4da6-550">**packet_ptr**: указатель на пакет запроса HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="c4da6-550">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="c4da6-551">Обратите внимание, что этот пакет не должен быть освобожден обратным вызовом уведомления о запросе.</span><span class="sxs-lookup"><span data-stu-id="c4da6-551">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="c4da6-552">**byte_offset**: число байтов для смещения в область содержимого</span><span class="sxs-lookup"><span data-stu-id="c4da6-552">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="c4da6-553">**destination_ptr**: указатель на область назначения для содержимого</span><span class="sxs-lookup"><span data-stu-id="c4da6-553">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="c4da6-554">**destination_size**: максимальное число байтов, доступных в области назначения</span><span class="sxs-lookup"><span data-stu-id="c4da6-554">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="c4da6-555">**actual_size**: указатель на переменную назначения, в качестве значения которой будет задан фактический размер копируемого содержимого</span><span class="sxs-lookup"><span data-stu-id="c4da6-555">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

<span data-ttu-id="c4da6-556">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-556">**Return Values**</span></span>

- <span data-ttu-id="c4da6-557">**NX_SUCCESS** (0x00) — содержимое HTTP-сервера успешно получено.</span><span class="sxs-lookup"><span data-stu-id="c4da6-557">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
- <span data-ttu-id="c4da6-558">**NX_HTTP_ERROR** (0xE0) — внутренняя ошибка HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c4da6-558">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="c4da6-559">**NX_HTTP_DATA_END** (0xE7) — конец содержимого запроса.</span><span class="sxs-lookup"><span data-stu-id="c4da6-559">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
- <span data-ttu-id="c4da6-560">**NX_HTTP_TIMEOUT** (0xE1) — время ожидания HTTP-сервера в получении следующего пакета содержимого.</span><span class="sxs-lookup"><span data-stu-id="c4da6-560">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet of content</span></span>
- <span data-ttu-id="c4da6-561">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-561">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="c4da6-562">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="c4da6-562">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="c4da6-563">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-563">**Allowed From**</span></span>

<span data-ttu-id="c4da6-564">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-564">Threads</span></span>

<span data-ttu-id="c4da6-565">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-565">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, retrieve up to 100 bytes of content starting at offset 0. */
status = nx_http_server_content_get(&my_server, packet_ptr,
                                   0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
request content. */
```

## <a name="nx_http_server_content_get_extended"></a><span data-ttu-id="c4da6-566">nx_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="c4da6-566">nx_http_server_content_get_extended</span></span>

### <a name="get-content-from-the-requestsupports-zero-length-content-length"></a><span data-ttu-id="c4da6-567">Получение содержимого из запроса или поддержка содержимого нулевой длины</span><span class="sxs-lookup"><span data-stu-id="c4da6-567">Get content from the request/supports zero length Content Length</span></span>

<span data-ttu-id="c4da6-568">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-568">**Prototype**</span></span>

```c
UINT nx_http_server_content_get_extended(NX_HTTP_SERVER *server_ptr,
                                        NX_PACKET *packet_ptr,
                                        ULONG byte_offset,
                                        CHAR *destination_ptr,
                                        UINT destination_size,
                                        UINT *actual_size);
```

<span data-ttu-id="c4da6-569">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-569">**Description**</span></span>

<span data-ttu-id="c4da6-570">Эта служба почти идентична службе *nx_http_server_content_get()* . Она пытается получить указанный объем содержимого из запроса POST или PUT HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="c4da6-570">This service is almost identical to *nx_http_server_content_get()*; it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="c4da6-571">Однако она обрабатывает запросы с содержимым нулевой длины (пустые запросы) как допустимые.</span><span class="sxs-lookup"><span data-stu-id="c4da6-571">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="c4da6-572">Ее следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="c4da6-572">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="c4da6-573">Эта служба заменяет *nx_http_server_content_get()* .</span><span class="sxs-lookup"><span data-stu-id="c4da6-573">This service replaces *nx_http_server_content_get().*</span></span> <span data-ttu-id="c4da6-574">Эта версия требует, чтобы вызывающий объект указал дополнительные сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="c4da6-574">This version requires caller to supply additional length information.</span></span>

<span data-ttu-id="c4da6-575">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-575">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-576">**server_ptr**: указатель на управляющий блок HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-576">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="c4da6-577">**packet_ptr**: указатель на пакет запроса HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="c4da6-577">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="c4da6-578">Обратите внимание, что этот пакет не должен быть освобожден обратным вызовом уведомления о запросе.</span><span class="sxs-lookup"><span data-stu-id="c4da6-578">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="c4da6-579">**byte_offset**: число байтов для смещения в область содержимого</span><span class="sxs-lookup"><span data-stu-id="c4da6-579">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="c4da6-580">**destination_ptr**: указатель на область назначения для содержимого</span><span class="sxs-lookup"><span data-stu-id="c4da6-580">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="c4da6-581">**destination_size**: максимальное число байтов, доступных в области назначения</span><span class="sxs-lookup"><span data-stu-id="c4da6-581">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="c4da6-582">**actual_size**: указатель на переменную назначения, в качестве значения которой будет задан фактический размер копируемого содержимого</span><span class="sxs-lookup"><span data-stu-id="c4da6-582">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

<span data-ttu-id="c4da6-583">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-583">**Return Values**</span></span>

- <span data-ttu-id="c4da6-584">**NX_SUCCESS** (0x00) — содержимое HTTP-запроса успешно получено.</span><span class="sxs-lookup"><span data-stu-id="c4da6-584">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
- <span data-ttu-id="c4da6-585">**NX_HTTP_ERROR** (0xE0) — внутренняя ошибка HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c4da6-585">**NX_HTTP_ERROR** (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="c4da6-586">**NX_HTTP_DATA_END** (0xE7) — конец содержимого запроса.</span><span class="sxs-lookup"><span data-stu-id="c4da6-586">**NX_HTTP_DATA_END** (0xE7) End of request content</span></span>
- <span data-ttu-id="c4da6-587">**NX_HTTP_TIMEOUT** (0xE1) — время ожидания HTTP-сервера в получении следующего пакета</span><span class="sxs-lookup"><span data-stu-id="c4da6-587">**NX_HTTP_TIMEOUT** (0xE1) HTTP Server timeout in getting next packet</span></span>
- <span data-ttu-id="c4da6-588">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-588">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="c4da6-589">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="c4da6-589">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="c4da6-590">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-590">**Allowed From**</span></span>

<span data-ttu-id="c4da6-591">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-591">Threads</span></span>

<span data-ttu-id="c4da6-592">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-592">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, retrieve up to 100 bytes of content starting at offset 0. */
status = nx_http_server_content_get_extended(&my_server, packet_ptr,
                                            0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, “my_buffer” contains “actual_size” bytes of
request content. */
```

## <a name="nx_http_server_content_length_get"></a><span data-ttu-id="c4da6-593">nx_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="c4da6-593">nx_http_server_content_length_get</span></span>

### <a name="get-length-of-content-in-the-request"></a><span data-ttu-id="c4da6-594">Получение длины содержимого в запросе</span><span class="sxs-lookup"><span data-stu-id="c4da6-594">Get length of content in the request</span></span>

<span data-ttu-id="c4da6-595">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-595">**Prototype**</span></span>

```c
UINT nx_http_server_content_length_get(NX_PACKET *packet_ptr);
```
<span data-ttu-id="c4da6-596">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-596">**Description**</span></span>

<span data-ttu-id="c4da6-597">Эта служба пытается получить длину содержимого HTTP в указанном пакете.</span><span class="sxs-lookup"><span data-stu-id="c4da6-597">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="c4da6-598">Если содержимое HTTP отсутствует, эта подпрограмма возвращает нулевое значение.</span><span class="sxs-lookup"><span data-stu-id="c4da6-598">If there is no HTTP content, this routine returns a value of zero.</span></span> <span data-ttu-id="c4da6-599">Ее следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="c4da6-599">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="c4da6-600">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="c4da6-600">This service is deprecated.</span></span> <span data-ttu-id="c4da6-601">Разработчикам рекомендуется перейти на использование nx_http_server_content_length_get_extended().</span><span class="sxs-lookup"><span data-stu-id="c4da6-601">Developers are encouraged to migrate to nx_http_server_content_length_get_extended().</span></span>

<span data-ttu-id="c4da6-602">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-602">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-603">**packet_ptr**: указатель на пакет запроса HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="c4da6-603">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="c4da6-604">Обратите внимание, что этот пакет не должен быть освобожден обратным вызовом уведомления о запросе.</span><span class="sxs-lookup"><span data-stu-id="c4da6-604">Note that this packet must not be released by the request notify callback.</span></span>

<span data-ttu-id="c4da6-605">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-605">**Return Values**</span></span>

- <span data-ttu-id="c4da6-606">**content_length** — при возникновении ошибки возвращается нулевое значение.</span><span class="sxs-lookup"><span data-stu-id="c4da6-606">**content length** On error, a value of zero is returned</span></span>

<span data-ttu-id="c4da6-607">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-607">**Allowed From**</span></span>

<span data-ttu-id="c4da6-608">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-608">Threads</span></span>

<span data-ttu-id="c4da6-609">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-609">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the content length of the HTTP Client request. */
length = nx_http_server_content_length_get(packet_ptr);

/* The “length” variable now contains the length of the HTTP Client
request content area. */
```

## <a name="nx_http_server_content_length_get_extended"></a><span data-ttu-id="c4da6-610">nx_http_server_content_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="c4da6-610">nx_http_server_content_length_get_extended</span></span>

### <a name="get-length-of-content-in-the-requestsupports-content-length-of-zero-value"></a><span data-ttu-id="c4da6-611">Получение длины содержимого в запросе или поддержка содержимого нулевой длины</span><span class="sxs-lookup"><span data-stu-id="c4da6-611">Get length of content in the request/supports Content Length of zero value</span></span>

<span data-ttu-id="c4da6-612">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-612">**Prototype**</span></span>

```c
UINT nx_http_server_content_length_get_extended(NX_PACKET *packet_ptr,
                                               UINT *content_length);
```

<span data-ttu-id="c4da6-613">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-613">**Description**</span></span>

<span data-ttu-id="c4da6-614">Эта служба аналогична службе *nx_http_server_content_length_get()* . Она пытается получить длину содержимого HTTP в указанном пакете.</span><span class="sxs-lookup"><span data-stu-id="c4da6-614">This service is similar to *nx_http_server_content_length_get()*; attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="c4da6-615">Однако возвращаемое значение указывает на состояние успешного завершения, а фактическое значение длины возвращается в параметре content_length входного указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-615">However, the return value indicates successful completion status, and the actual length value is returned in the input pointer content_length.</span></span> <span data-ttu-id="c4da6-616">Если нет содержимого HTTP или длина содержимого равна нулю, эта подпрограмма по-прежнему возвращает состояние выполнения, а указатель ввода content_length указывает на допустимую длину (ноль).</span><span class="sxs-lookup"><span data-stu-id="c4da6-616">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="c4da6-617">Ее следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="c4da6-617">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="c4da6-618">Эта служба заменяет *nx_http_server_content_length_get()* .</span><span class="sxs-lookup"><span data-stu-id="c4da6-618">This service replaces *nx_http_server_content_length_get*().</span></span>

<span data-ttu-id="c4da6-619">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-619">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-620">**packet_ptr**: указатель на пакет запроса HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="c4da6-620">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="c4da6-621">Обратите внимание, что этот пакет не должен быть освобожден обратным вызовом уведомления о запросе.</span><span class="sxs-lookup"><span data-stu-id="c4da6-621">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="c4da6-622">**content_length** Указатель на значение, полученное из поля длины содержимого.</span><span class="sxs-lookup"><span data-stu-id="c4da6-622">**content_length** Pointer to value retrieved from Content Length field</span></span>

<span data-ttu-id="c4da6-623">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-623">**Return Values**</span></span>

- <span data-ttu-id="c4da6-624">**NX_SUCCESS** (0x00) — содержимое HTTP-сервера успешно получено.</span><span class="sxs-lookup"><span data-stu-id="c4da6-624">**NX_SUCCESS** (0x00) Successful HTTP Server content get</span></span>
- <span data-ttu-id="c4da6-625">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) — недопустимый формат заголовка HTTP</span><span class="sxs-lookup"><span data-stu-id="c4da6-625">**NX_HTTP_INCOMPLETE_PUT_ERROR** (0xEF) Improper HTTP header format</span></span>
- <span data-ttu-id="c4da6-626">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-626">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="c4da6-627">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-627">**Allowed From**</span></span>

<span data-ttu-id="c4da6-628">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-628">Threads</span></span>

<span data-ttu-id="c4da6-629">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-629">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the content length of the HTTP Client request. */
ULONG content_length;

status = nx_http_server_content_length_get_extended(packet_ptr, &content_length);

/* If the “status” variable indicates successful completion, the“length” variable
contains the length of the HTTP Client request content area. */
```

## <a name="nx_http_server_create"></a><span data-ttu-id="c4da6-630">nx_http_server_create</span><span class="sxs-lookup"><span data-stu-id="c4da6-630">nx_http_server_create</span></span>

### <a name="create-an-http-server-instance"></a><span data-ttu-id="c4da6-631">Создание экземпляра HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-631">Create an HTTP Server instance</span></span>

<span data-ttu-id="c4da6-632">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-632">**Prototype**</span></span>

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

<span data-ttu-id="c4da6-633">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-633">**Description**</span></span>

<span data-ttu-id="c4da6-634">Эта служба создает экземпляр HTTP-сервера, который выполняется в контексте собственного потока ThreadX.</span><span class="sxs-lookup"><span data-stu-id="c4da6-634">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="c4da6-635">Необязательные подпрограммы обратного вызова приложений *authentication_check* и *request_notify* позволяют программному обеспечению приложения управлять основными операциями HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c4da6-635">The optional *authentication_check* and *request_notify* application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

<span data-ttu-id="c4da6-636">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-636">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-637">**http_server_ptr**: указатель на управляющий блок HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-637">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="c4da6-638">**http_server_name**: указатель на имя HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-638">**http_server_name** Pointer to HTTP Server’s name.</span></span>
- <span data-ttu-id="c4da6-639">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="c4da6-639">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="c4da6-640">**media_ptr**: указатель на ранее созданный экземпляр носителя FileX</span><span class="sxs-lookup"><span data-stu-id="c4da6-640">**media_ptr** Pointer to previously created FileX media instance.</span></span>
- <span data-ttu-id="c4da6-641">**stack_ptr**: указатель на область стека потока HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-641">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
- <span data-ttu-id="c4da6-642">**stack_ptr**: указатель на размер стека потока HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-642">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
- <span data-ttu-id="c4da6-643">**authentication_check**: указатель функции на подпрограмму проверки подлинности приложения</span><span class="sxs-lookup"><span data-stu-id="c4da6-643">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="c4da6-644">Если параметр указан, эта подпрограмма вызывается для каждого запроса HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="c4da6-644">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="c4da6-645">Если этот параметр имеет значение NULL, проверка подлинности выполняться не будет.</span><span class="sxs-lookup"><span data-stu-id="c4da6-645">If this parameter is NULL no authentication will be performed.</span></span>
- <span data-ttu-id="c4da6-646">**request_notify**: указатель функции в подпрограмме уведомления о запросе приложения</span><span class="sxs-lookup"><span data-stu-id="c4da6-646">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="c4da6-647">Если параметр указан, подпрограмма вызывается перед обработкой запроса HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="c4da6-647">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="c4da6-648">Это позволяет перенаправлять имя ресурса или обновлять поля в самом ресурсе до завершения запроса HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="c4da6-648">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

<span data-ttu-id="c4da6-649">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-649">**Return Values**</span></span>

- <span data-ttu-id="c4da6-650">**NX_SUCCESS** (0x00) — HTTP-сервера успешно создан.</span><span class="sxs-lookup"><span data-stu-id="c4da6-650">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
- <span data-ttu-id="c4da6-651">NX_PTR_ERROR (0x07) — недопустимый указатель на HTTP-сервер, IP-адрес, носитель, стек или пул пакетов</span><span class="sxs-lookup"><span data-stu-id="c4da6-651">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
- <span data-ttu-id="c4da6-652">NX_HTTP_POOL_ERROR (0xE9) — полезные данные пула недостаточно велики, чтобы содержать полный HTTP-запрос</span><span class="sxs-lookup"><span data-stu-id="c4da6-652">NX_HTTP_POOL_ERROR (0xE9) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

<span data-ttu-id="c4da6-653">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-653">**Allowed From**</span></span>

<span data-ttu-id="c4da6-654">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-654">Initialization, Threads</span></span>

<span data-ttu-id="c4da6-655">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-655">**Example**</span></span>

```c
/* Create an HTTP Server instance called “my_server.” */
status = nx_http_server_create(&my_server, “my server”, &ip_0, &ram_disk,
                              stack_ptr, stack_size, &pool_0,
                              my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_http_server_delete"></a><span data-ttu-id="c4da6-656">nx_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="c4da6-656">nx_http_server_delete</span></span>

### <a name="delete-an-http-server-instance"></a><span data-ttu-id="c4da6-657">Удаление экземпляра HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-657">Delete an HTTP Server instance</span></span>

<span data-ttu-id="c4da6-658">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-658">**Prototype**</span></span>

```c
UINT nx_http_server_delete(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="c4da6-659">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-659">**Description**</span></span>

<span data-ttu-id="c4da6-660">Эта служба удаляет ранее созданный экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c4da6-660">This service deletes a previously created HTTP Server instance.</span></span>

<span data-ttu-id="c4da6-661">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-661">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-662">**http_server_ptr**: указатель на управляющий блок HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-662">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

<span data-ttu-id="c4da6-663">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-663">**Return Values**</span></span>

- <span data-ttu-id="c4da6-664">**NX_SUCCESS** (0x00) — HTTP-сервер успешно удален.</span><span class="sxs-lookup"><span data-stu-id="c4da6-664">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
- <span data-ttu-id="c4da6-665">NX_PTR_ERROR (0x07) — недопустимый указатель на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="c4da6-665">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
- <span data-ttu-id="c4da6-666">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="c4da6-666">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="c4da6-667">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-667">**Allowed From**</span></span>

<span data-ttu-id="c4da6-668">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-668">Threads</span></span>

<span data-ttu-id="c4da6-669">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-669">**Example**</span></span>

```c
/* Delete the HTTP Server instance called “my_server.” */
status = nx_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_http_server_get_entity_content"></a><span data-ttu-id="c4da6-670">nx_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="c4da6-670">nx_http_server_get_entity_content</span></span>

### <a name="retrieve-the-location-and-length-of-entity-data"></a><span data-ttu-id="c4da6-671">Получение расположения и длины данных сущности</span><span class="sxs-lookup"><span data-stu-id="c4da6-671">Retrieve the location and length of entity data</span></span>

<span data-ttu-id="c4da6-672">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-672">**Prototype**</span></span>

```c
UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

<span data-ttu-id="c4da6-673">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-673">**Description**</span></span>

<span data-ttu-id="c4da6-674">Эта служба определяет расположение начала данных в текущем составном объекте в полученных сообщениях клиента, а также длину данных, не включая граничную строку.</span><span class="sxs-lookup"><span data-stu-id="c4da6-674">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="c4da6-675">HTTP-сервер внутренне обновляет собственные смещения, чтобы эту функцию можно было повторно вызывать в той же клиентской датаграмме для сообщений с несколькими сущностями.</span><span class="sxs-lookup"><span data-stu-id="c4da6-675">Internally HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="c4da6-676">Указатель пакета обновляется до следующего пакета, где сообщение клиента является датаграммой с несколькими пакетами.</span><span class="sxs-lookup"><span data-stu-id="c4da6-676">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="c4da6-677">Обратите внимание, что для использования этой службы необходимо включить NX_HTTP_MULTIPART_ENABLE.</span><span class="sxs-lookup"><span data-stu-id="c4da6-677">Note that NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="c4da6-678">Дополнительные сведения см. в разделе *nx_http_server_get_entity_header*.</span><span class="sxs-lookup"><span data-stu-id="c4da6-678">See *nx_http_server_get_entity_header* for more details.</span></span>

<span data-ttu-id="c4da6-679">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-679">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-680">**server_ptr**: указатель на HTTP-сервер</span><span class="sxs-lookup"><span data-stu-id="c4da6-680">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="c4da6-681">**packet_pptr**: указатель на расположение указателя пакета</span><span class="sxs-lookup"><span data-stu-id="c4da6-681">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="c4da6-682">Обратите внимание, что приложение не должно освобождать этот пакет.</span><span class="sxs-lookup"><span data-stu-id="c4da6-682">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="c4da6-683">**available_offset**: указатель на смещение данных сущности от указателя начала пакета</span><span class="sxs-lookup"><span data-stu-id="c4da6-683">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
- <span data-ttu-id="c4da6-684">**available_length**: указатель на длину данных сущности</span><span class="sxs-lookup"><span data-stu-id="c4da6-684">**available_length** Pointer to length of entity data</span></span>

<span data-ttu-id="c4da6-685">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-685">**Return Values**</span></span>

- <span data-ttu-id="c4da6-686">**NX_SUCCESS** (0x00) — размер и расположение содержимого сущности успешно получены.</span><span class="sxs-lookup"><span data-stu-id="c4da6-686">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
- <span data-ttu-id="c4da6-687">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) — содержимое для внутренних многокомпонентных маркеров HTTP-сервера уже найдено.</span><span class="sxs-lookup"><span data-stu-id="c4da6-687">**NX_HTTP_BOUNDARY_ALREADY_FOUND** (0xF4) Content for the HTTP server internal multipart markers is already found</span></span>
- <span data-ttu-id="c4da6-688">NX_HTTP_ERROR (0xE0) — внутренняя ошибка HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c4da6-688">NX_HTTP_ERROR (0xE0) HTTP Server internal error</span></span>
- <span data-ttu-id="c4da6-689">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-689">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="c4da6-690">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-690">**Allowed From**</span></span>

<span data-ttu-id="c4da6-691">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-691">Threads</span></span>

<span data-ttu-id="c4da6-692">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-692">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;

UINT         offset, length;
NX_PACKET    *packet_ptr;

/* Inside the request notify callback, the HTTP server application first obtains
the entity header to determine details about the multipart data. If
successful, it then calls this service to get the location of entity data: */
status = nx_http_server_get_entity_content(&my_server, &packet_ptr, *offset,
                                          &length);

/* If status equals NX_SUCCESS, offset and location determine the location of the
entity data. */
```

## <a name="nx_http_server_get_entity_header"></a><span data-ttu-id="c4da6-693">nx_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="c4da6-693">nx_http_server_get_entity_header</span></span>

### <a name="retrieve-the-contents-of-entity-header"></a><span data-ttu-id="c4da6-694">Получение содержимого заголовка сущности</span><span class="sxs-lookup"><span data-stu-id="c4da6-694">Retrieve the contents of entity header</span></span>

<span data-ttu-id="c4da6-695">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-695">**Prototype**</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);
```

<span data-ttu-id="c4da6-696">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-696">**Description**</span></span>

<span data-ttu-id="c4da6-697">Эта служба извлекает заголовок сущности в указанный буфер.</span><span class="sxs-lookup"><span data-stu-id="c4da6-697">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="c4da6-698">HTTP-сервер внутренне обновляет собственные указатели для поиска следующей составной сущности в датаграмме клиента с несколькими заголовками сущностей.</span><span class="sxs-lookup"><span data-stu-id="c4da6-698">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="c4da6-699">Указатель пакета обновляется до следующего пакета, где сообщение клиента является датаграммой с несколькими пакетами.</span><span class="sxs-lookup"><span data-stu-id="c4da6-699">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="c4da6-700">Обратите внимание, что для использования этой службы необходимо включить NX_HTTP_MULTIPART_ENABLE.</span><span class="sxs-lookup"><span data-stu-id="c4da6-700">Note that NX_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span>

<span data-ttu-id="c4da6-701">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-701">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-702">**server_ptr**: указатель на HTTP-сервер</span><span class="sxs-lookup"><span data-stu-id="c4da6-702">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="c4da6-703">**packet_pptr**: указатель на расположение указателя пакета</span><span class="sxs-lookup"><span data-stu-id="c4da6-703">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="c4da6-704">Обратите внимание, что приложение не должно освобождать этот пакет.</span><span class="sxs-lookup"><span data-stu-id="c4da6-704">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="c4da6-705">**entity_header_buffer**: указатель на расположение для хранения заголовка сущности</span><span class="sxs-lookup"><span data-stu-id="c4da6-705">**entity_header_buffer** Pointer to location to store entity header</span></span>
- <span data-ttu-id="c4da6-706">**buffer_size**: размер входного буфера</span><span class="sxs-lookup"><span data-stu-id="c4da6-706">**buffer_size** Size of input buffer</span></span>

<span data-ttu-id="c4da6-707">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-707">**Return Values**</span></span>

- <span data-ttu-id="c4da6-708">**NX_SUCCESS** (0x00) — заголовок сущности успешно получен.</span><span class="sxs-lookup"><span data-stu-id="c4da6-708">**NX_SUCCESS** (0x00) Successfully retrieved entity heade</span></span>
- <span data-ttu-id="c4da6-709">**NX_HTTP_NOT_FOUND (0xE6)**  — поле заголовка сущности не найдено.</span><span class="sxs-lookup"><span data-stu-id="c4da6-709">**NX_HTTP_NOT_FOUND (0xE6)** Entity header field not found</span></span>
- <span data-ttu-id="c4da6-710">**NX_HTTP_TIMEOUT (0xE1)**  — истекло время для получения следующего пакета для сообщения клиента с несколькими пакетами.</span><span class="sxs-lookup"><span data-stu-id="c4da6-710">**NX_HTTP_TIMEOUT (0xE1)** Time expired to receive next packet for multipacket client message</span></span> 
- <span data-ttu-id="c4da6-711">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-711">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="c4da6-712">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="c4da6-712">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="c4da6-713">NX_HTTP_ERROR (0xE0) — внутренняя ошибка HTTP.</span><span class="sxs-lookup"><span data-stu-id="c4da6-713">NX_HTTP_ERROR (0xE0) Internal HTTP error</span></span>

<span data-ttu-id="c4da6-714">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-714">**Allowed From**</span></span>

<span data-ttu-id="c4da6-715">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-715">Threads</span></span>

<span data-ttu-id="c4da6-716">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-716">**Example**</span></span>

```c
/* my_request_notify* is the application request notify callback registered with
the HTTP server in *nx_http_server_create,* creates a response to the received
Client request. */

UINT my_request_notify(NX_HTTP_SERVER *server_ptr, UINT request_type,
                      CHAR *resource, NX_PACKET *packet_ptr)
{

NX_PACKET     *sresp_packet_ptr;
UINT          offset, length;**
NX_PACKET     *response_pkt;
UCHAR         buffer[1440];

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
             "Server: NetX HTTP 5.3\r\n");

    if(status == NX_SUCCESS)
    {
        if(nx_http_server_callback_packet_send(server_ptr, response_pkt) !=
                                              NX_SUCCESS)
        {
            nx_packet_release(response_pkt);
        }
    }
}
Else
{

        /* Indicate we have not processed the response to client yet.*/        
        return(NX_SUCCESS);
}

/* Indicate the response to client is transmitted. */
return(NX_HTTP_CALLBACK_COMPLETED);
```

## <a name="nx_http_server_gmt_callback_set"></a><span data-ttu-id="c4da6-717">nx_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="c4da6-717">nx_http_server_gmt_callback_set</span></span>

### <a name="set-the-callback-to-obtain-gmt-date-and-time"></a><span data-ttu-id="c4da6-718">Задание обратного вызова для получения даты и времени по Гринвичу</span><span class="sxs-lookup"><span data-stu-id="c4da6-718">Set the callback to obtain GMT date and time</span></span>

<span data-ttu-id="c4da6-719">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-719">**Prototype**</span></span>

```c
UINT nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                    VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

<span data-ttu-id="c4da6-720">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-720">**Description**</span></span>

<span data-ttu-id="c4da6-721">Эта служба задает обратный вызов для получения даты и времени в формате GMT с помощью ранее созданного HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c4da6-721">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="c4da6-722">Эта служба вызывается HTTP-сервером и создает заголовок в ответах HTTP-сервера для клиента.</span><span class="sxs-lookup"><span data-stu-id="c4da6-722">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

<span data-ttu-id="c4da6-723">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-723">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-724">**server_ptr**: указатель на HTTP-сервер</span><span class="sxs-lookup"><span data-stu-id="c4da6-724">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="c4da6-725">**gmt_getv**: указатель на обратный вызов для получения даты и времени по Гринвичу</span><span class="sxs-lookup"><span data-stu-id="c4da6-725">**gmt_get** Pointer to GMT callback</span></span>
- <span data-ttu-id="c4da6-726">**date**: указатель на полученную дату</span><span class="sxs-lookup"><span data-stu-id="c4da6-726">**date** Pointer to the date retrieved</span></span>

<span data-ttu-id="c4da6-727">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-727">**Return Values**</span></span>

- <span data-ttu-id="c4da6-728">**NX_SUCCESS** (0x00) — обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="c4da6-728">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="c4da6-729">NX_PTR_ERROR (0x07) — недопустимый указатель на пакет или параметр.</span><span class="sxs-lookup"><span data-stu-id="c4da6-729">NX_PTR_ERROR (0x07) Invalid packet or parameter pointer.</span></span>

<span data-ttu-id="c4da6-730">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-730">**Allowed From**</span></span>

<span data-ttu-id="c4da6-731">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-731">Threads</span></span>

<span data-ttu-id="c4da6-732">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-732">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;

VOID get_gmt(NX_HTTP_SERVER_DATE *now);

/* After the HTTP server is created by calling nx_http_server_create, and before
starting HTTP services when nx_http_server_start is called, set the GMT
retrieve callback: */

status = nx_http_server_gmt_callback_set(&my_server, gmt_get);

/* If status equals NX_SUCCESS, the gmt_get will be called to set the HTTP server
response header date. */
```

## <a name="nx_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="c4da6-733">nx_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="c4da6-733">nx_http_server_invalid_userpassword_notify_set</span></span>

### <a name="set-the-callback-to-to-handle-invalid-userpassword"></a><span data-ttu-id="c4da6-734">Задание обратного вызова для обработки недопустимого имени пользователя и пароля</span><span class="sxs-lookup"><span data-stu-id="c4da6-734">Set the callback to to handle invalid user/password</span></span>

<span data-ttu-id="c4da6-735">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-735">**Prototype**</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set(
     NX_HTTP_SERVER *http_server_ptr,
     UINT (*invalid_username_password_callback)
     (CHAR *resource,
     ULONG client_address,
     UINT request_type));
```

<span data-ttu-id="c4da6-736">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-736">**Description**</span></span>

<span data-ttu-id="c4da6-737">Эта служба задает обратный вызов, вызываемый при получении недопустимого имени пользователя и пароля в запросе GET, PUT или DELETE клиента в результате дайджест- или обычной проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="c4da6-737">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="c4da6-738">HTTP-сервер должен быть создан ранее.</span><span class="sxs-lookup"><span data-stu-id="c4da6-738">The HTTP server must be previously created.</span></span>

<span data-ttu-id="c4da6-739">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-739">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-740">**server_ptr**: указатель на HTTP-сервер</span><span class="sxs-lookup"><span data-stu-id="c4da6-740">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="c4da6-741">**invalid_username_password_callback**: указатель на недопустимый обратный вызов имени пользователя или пароля</span><span class="sxs-lookup"><span data-stu-id="c4da6-741">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
- <span data-ttu-id="c4da6-742">**resource**: указатель на ресурс, указанный клиентом</span><span class="sxs-lookup"><span data-stu-id="c4da6-742">**resource** Pointer to the resource specified by the client</span></span>
- <span data-ttu-id="c4da6-743">**client_address**: адрес клиента</span><span class="sxs-lookup"><span data-stu-id="c4da6-743">**client_address** Client address</span></span>
- <span data-ttu-id="c4da6-744">**request_type** указывает тип запроса клиента</span><span class="sxs-lookup"><span data-stu-id="c4da6-744">**request_type** Indicates client request type.</span></span> <span data-ttu-id="c4da6-745">Может иметь следующие значения.</span><span class="sxs-lookup"><span data-stu-id="c4da6-745">May be:</span></span>
  - <span data-ttu-id="c4da6-746">NX_HTTP_SERVER_GET_REQUEST</span><span class="sxs-lookup"><span data-stu-id="c4da6-746">NX_HTTP_SERVER_GET_REQUEST</span></span>
  - <span data-ttu-id="c4da6-747">NX_HTTP_SERVER_POST_REQUEST NX_HTTP_SERVER_HEAD_REQUEST</span><span class="sxs-lookup"><span data-stu-id="c4da6-747">NX_HTTP_SERVER_POST_REQUEST NX_HTTP_SERVER_HEAD_REQUEST</span></span>
  - <span data-ttu-id="c4da6-748">NX_HTTP_SERVER_PUT_REQUEST NX_HTTP_SERVER_DELETE_REQUEST</span><span class="sxs-lookup"><span data-stu-id="c4da6-748">NX_HTTP_SERVER_PUT_REQUEST NX_HTTP_SERVER_DELETE_REQUEST</span></span>

<span data-ttu-id="c4da6-749">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-749">**Return Values**</span></span>

- <span data-ttu-id="c4da6-750">**NX_SUCCESS** (0x00) — обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="c4da6-750">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="c4da6-751">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-751">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="c4da6-752">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-752">**Allowed From**</span></span>

<span data-ttu-id="c4da6-753">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-753">Threads</span></span>

<span data-ttu-id="c4da6-754">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-754">**Example**</span></span>

```c
NX_HTTP_SERVER my_server;
VOID invalid_username_password_callback (NX_ CHAR *resource,
                                        ULONG client_address,
                                        UINT request_type);

/* After the HTTP server is created by calling nx_http_server_create, and before
starting HTTP services when nx_http_server_start is called, set the invalid
username password callback: */

status = nx_http_server_gmt_callback_set(&my_server,
                                        invalid_username_password_callback);

/* If status equals NX_SUCCESS, the invalid_username_password_callback function
will be called when the HTTP server receives an invalid username/password. */
```

## <a name="nx_http_server_mime_maps_additional_set"></a><span data-ttu-id="c4da6-755">nx_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="c4da6-755">nx_http_server_mime_maps_additional_set</span></span>

### <a name="set-additional-mime-maps-for-html"></a><span data-ttu-id="c4da6-756">Задание дополнительных сопоставлений MIME для HTML</span><span class="sxs-lookup"><span data-stu-id="c4da6-756">Set additional MIME maps for HTML</span></span> 

<span data-ttu-id="c4da6-757">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-757">**Prototype**</span></span>

```c
UINT nx_http_server_mime_maps_additional_set(
     NX_HTTP_SERVER *server_ptr,
     NX_HTTP_SERVER_MIME_MAP *mime_maps,
     UINT mime_maps_num);
```

<span data-ttu-id="c4da6-758">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-758">**Description**</span></span>

<span data-ttu-id="c4da6-759">Эта служба позволяет разработчику приложений HTTP добавлять дополнительные типы MIME из типов MIME по умолчанию, предоставляемых HTTP-сервером NetX (см. *nx_http_server_get_type* для получения списка определенных типов).</span><span class="sxs-lookup"><span data-stu-id="c4da6-759">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by NetX HTTP Server (see *nx_http_server_get_type* for list of defined types).</span></span>

<span data-ttu-id="c4da6-760">Если получен запрос клиента, например запрос GET, HTTP-сервер анализирует запрошенный тип файла из заголовка HTTP с помощью дополнительного заданного сопоставления MIME и, если совпадений не найдено, ищет соответствие в сопоставлении MIME по умолчанию HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c4da6-760">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="c4da6-761">Если совпадений не найдено, по умолчанию используется тип MIME text/plain.</span><span class="sxs-lookup"><span data-stu-id="c4da6-761">If no match is found, the MIME type defaults to “text/plain”.</span></span>

<span data-ttu-id="c4da6-762">Если функция уведомления о запросе зарегистрирована на HTTP-сервере, обратный вызов уведомления о запросе может вызвать *nx_http_server_type_get* для анализа типа файла.</span><span class="sxs-lookup"><span data-stu-id="c4da6-762">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_http_server_type_get* to parse the file type.</span></span>

<span data-ttu-id="c4da6-763">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-763">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-764">**server_ptr**: указатель на экземпляр HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-764">**server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="c4da6-765">**mime_maps**: указатель на массив сопоставлений MIME</span><span class="sxs-lookup"><span data-stu-id="c4da6-765">**mime_maps** Pointer to a MIME map array</span></span>
- <span data-ttu-id="c4da6-766">**mime_map_num**: число сопоставлений MIME в массиве</span><span class="sxs-lookup"><span data-stu-id="c4da6-766">**mime_map_num** Number of MIME maps in array</span></span>

<span data-ttu-id="c4da6-767">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-767">**Return Values**</span></span>

- <span data-ttu-id="c4da6-768">**NX_SUCCESS** (0x00) — сопоставление MIME HTTP-сервера успешно задано.</span><span class="sxs-lookup"><span data-stu-id="c4da6-768">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
- <span data-ttu-id="c4da6-769">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-769">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="c4da6-770">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-770">**Allowed From**</span></span>

<span data-ttu-id="c4da6-771">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-771">Initialization, Threads</span></span>

<span data-ttu-id="c4da6-772">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-772">**Example**</span></span>

```c
/* my_server is an NX_HTTP_SERVER previously created. */

NX_HTTP_SERVER_MIME_MAP my_mime_maps [2];

static NX_HTTP_SERVER_MIME_MAP my_mime_maps[] =
{
    {"abc", "yourtype/abc"},
    {"xyz", "mytype/xyz"},
};

status = nx_http_server_mime_maps_additional_set(&my_server,
                                                &my_mime_maps[0], 2);

/* If status equals NX_SUCCESS, two additional MIME types are added to the HTTP
server MIME map set.” */
```

## <a name="nx_http_server_packet_content_find"></a><span data-ttu-id="c4da6-773">nx_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="c4da6-773">nx_http_server_packet_content_find</span></span>

### <a name="extract-content-length-and-set-pointer-to-start-of-data"></a><span data-ttu-id="c4da6-774">Извлечение длины содержимого и установка указателя на начало данных</span><span class="sxs-lookup"><span data-stu-id="c4da6-774">Extract content length and set pointer to start of data</span></span>

<span data-ttu-id="c4da6-775">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-775">**Prototype**</span></span>

```c
UINT nx_http_server_packet_content_find(NX_HTTP_SERVER *server_ptr,
                                       NX_PACKET **packet_ptr,
                                       UINT *content_length);
```

<span data-ttu-id="c4da6-776">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-776">**Description**</span></span>

<span data-ttu-id="c4da6-777">Эта служба извлекает длину содержимого из заголовка HTTP.</span><span class="sxs-lookup"><span data-stu-id="c4da6-777">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="c4da6-778">Она также обновляет указанный пакет следующим образом: перед указателем начала пакета (начало расположения буфера пакета для записи) задается содержимое HTTP (данные), только что переданное заголовком HTTP.</span><span class="sxs-lookup"><span data-stu-id="c4da6-778">It also updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="c4da6-779">Если в текущем пакете не найдено начало содержимого, функция ожидает получения следующего пакета с помощью параметра ожидания NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="c4da6-779">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

<span data-ttu-id="c4da6-780">Обратите внимание, что эту службу не следует вызывать перед вызовом *nx_http_server_get_entity_header()* , поскольку она изменяет указатель в начале после заголовка сущности.</span><span class="sxs-lookup"><span data-stu-id="c4da6-780">Note this should not be called before calling *nx_http_server_get_entity_header()* because it modifies the prepend pointer past the entity header.</span></span>

<span data-ttu-id="c4da6-781">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-781">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-782">**server_ptr**: указатель на экземпляр HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-782">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="c4da6-783">**packet_ptr**: указатель на указатель пакета для возврата пакета с обновленным указателем начала</span><span class="sxs-lookup"><span data-stu-id="c4da6-783">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
- <span data-ttu-id="c4da6-784">**content_length**: указатель на извлеченный параметр content_length</span><span class="sxs-lookup"><span data-stu-id="c4da6-784">**content_length** Pointer to extracted content_length</span></span>

<span data-ttu-id="c4da6-785">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-785">**Return Values**</span></span>

- <span data-ttu-id="c4da6-786">**NX_SUCCESS** (0x00) — длина содержимого HTTP обнаружена, и пакет успешно обновлен.</span><span class="sxs-lookup"><span data-stu-id="c4da6-786">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
- <span data-ttu-id="c4da6-787">**NX_HTTP_TIMEOUT** (0xE1) — истекло время ожидания следующего пакета.</span><span class="sxs-lookup"><span data-stu-id="c4da6-787">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
- <span data-ttu-id="c4da6-788">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-788">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="c4da6-789">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-789">**Allowed From**</span></span>

<span data-ttu-id="c4da6-790">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-790">Threads</span></span>

<span data-ttu-id="c4da6-791">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-791">**Example**</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started.
The server has received a Client request packet, recv_packet_ptr, and the packet
content find service is called from the request notify callback function 
registere with the HTTP server. */

UINT content_length;

status = nx_http_server_packet_content_find(server_ptr, recv_packet_ptr,
                                           &content_length);

/* If status equals NX_SUCCESS, the content length specifies the content length
and the packet pointer prepend pointer is set to the HTTP content (data). */
```

## <a name="nx_http_server_packet_get"></a><span data-ttu-id="c4da6-792">nx_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="c4da6-792">nx_http_server_packet_get</span></span>

### <a name="receive-the-next-http-packet"></a><span data-ttu-id="c4da6-793">Получение следующего пакета HTTP</span><span class="sxs-lookup"><span data-stu-id="c4da6-793">Receive the next HTTP packet</span></span>

<span data-ttu-id="c4da6-794">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-794">**Prototype**</span></span>

```c
UINT nx_http_server_packet_get(NX_HTTP_SERVER *server_ptr,
                              NX_PACKET **packet_ptr);
```

<span data-ttu-id="c4da6-795">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-795">**Description**</span></span>

<span data-ttu-id="c4da6-796">Эта служба возвращает следующий пакет, полученный через сокет HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c4da6-796">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="c4da6-797">Для получения пакета используется параметр ожидания NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="c4da6-797">The wait option to receive a packet is NX_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

<span data-ttu-id="c4da6-798">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-798">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-799">**server_ptr**: указатель на экземпляр HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-799">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="c4da6-800">**packet_ptr**: указатель на полученный пакет</span><span class="sxs-lookup"><span data-stu-id="c4da6-800">**packet_ptr** Pointer to received packet</span></span>

<span data-ttu-id="c4da6-801">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-801">**Return Values**</span></span>

- <span data-ttu-id="c4da6-802">**NX_SUCCESS** (0x00) — следующий пакет HTTP успешно получен.</span><span class="sxs-lookup"><span data-stu-id="c4da6-802">**NX_SUCCESS** (0x00) Successfully received next HTTP packet</span></span>
- <span data-ttu-id="c4da6-803">**NX_HTTP_TIMEOUT** (0xE1) — истекло время ожидания следующего пакета.</span><span class="sxs-lookup"><span data-stu-id="c4da6-803">**NX_HTTP_TIMEOUT** (0xE1) Time expired waiting on next packet</span></span>
- <span data-ttu-id="c4da6-804">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-804">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="c4da6-805">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-805">**Allowed From**</span></span>

<span data-ttu-id="c4da6-806">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-806">Threads</span></span>

<span data-ttu-id="c4da6-807">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-807">**Example**</span></span>

```c
/* The HTTP server pointed to by server_ptr is previously created and started. */

UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_http_server_param_get"></a><span data-ttu-id="c4da6-808">nx_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="c4da6-808">nx_http_server_param_get</span></span>

### <a name="get-parameter-from-the-request"></a><span data-ttu-id="c4da6-809">Получение параметра из запроса</span><span class="sxs-lookup"><span data-stu-id="c4da6-809">Get parameter from the request</span></span>

<span data-ttu-id="c4da6-810">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-810">**Prototype**</span></span>

```c
UINT nx_http_server_param_get(NX_PACKET *packet_ptr,
                             UINT param_number, CHAR *param_ptr,
                             UINT max_param_size);
```

<span data-ttu-id="c4da6-811">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-811">**Description**</span></span>

<span data-ttu-id="c4da6-812">Эта служба пытается получить указанный параметр URL-адреса HTTP в указанном пакете запроса.</span><span class="sxs-lookup"><span data-stu-id="c4da6-812">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="c4da6-813">Если запрашиваемый параметр HTTP отсутствует, подпрограмма возвращает состояние NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="c4da6-813">If the requested HTTP parameter is not present, this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="c4da6-814">Эту подпрограмму следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="c4da6-814">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="c4da6-815">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-815">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-816">**packet_ptr**: указатель на пакет запроса HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="c4da6-816">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="c4da6-817">Обратите внимание, что приложение не должно освобождать этот пакет.</span><span class="sxs-lookup"><span data-stu-id="c4da6-817">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="c4da6-818">**param_number**: логический номер параметра, начинающийся с нуля, слева направо в списке параметров</span><span class="sxs-lookup"><span data-stu-id="c4da6-818">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
- <span data-ttu-id="c4da6-819">**param_ptr**: область назначения для копирования параметра</span><span class="sxs-lookup"><span data-stu-id="c4da6-819">**param_ptr** Destination area to copy the parameter.</span></span>
- <span data-ttu-id="c4da6-820">**max_param_size**: максимальный размер области назначения параметра</span><span class="sxs-lookup"><span data-stu-id="c4da6-820">**max_param_size** Maximum size of the parameter destination area.</span></span>

<span data-ttu-id="c4da6-821">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-821">**Return Values**</span></span>

- <span data-ttu-id="c4da6-822">**NX_SUCCESS** (0x00) — параметр HTTP-сервера успешно получен</span><span class="sxs-lookup"><span data-stu-id="c4da6-822">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
- <span data-ttu-id="c4da6-823">**NX_HTTP_NOT_FOUND** (0xE6) — указанный параметр не найден</span><span class="sxs-lookup"><span data-stu-id="c4da6-823">**NX_HTTP_NOT_FOUND** (0xE6) Specified parameter not found</span></span>
- <span data-ttu-id="c4da6-824">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) — неправильное завершение параметра запроса</span><span class="sxs-lookup"><span data-stu-id="c4da6-824">**NX_HTTP_IMPROPERLY_TERMINATED_PARAM** (0xF3) Request parameter not properly terminated</span></span>
- <span data-ttu-id="c4da6-825">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-825">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="c4da6-826">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="c4da6-826">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="c4da6-827">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-827">**Allowed From**</span></span>

<span data-ttu-id="c4da6-828">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-828">Threads</span></span>

<span data-ttu-id="c4da6-829">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-829">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the first parameter of the HTTP Client request. */

status = nx_http_server_param_get(request_packet_ptr, 0, param_destination, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
in “param_destination.” */
```

## <a name="nx_http_server_query_get"></a><span data-ttu-id="c4da6-830">nx_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="c4da6-830">nx_http_server_query_get</span></span>

### <a name="get-query-from-the-request"></a><span data-ttu-id="c4da6-831">Получение запроса из запроса</span><span class="sxs-lookup"><span data-stu-id="c4da6-831">Get query from the request</span></span>

<span data-ttu-id="c4da6-832">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-832">**Prototype**</span></span>

```c
UINT nx_http_server_query_get(NX_PACKET *packet_ptr, UINT query_number,
                             CHAR *query_ptr, UINT max_query_size);
```

<span data-ttu-id="c4da6-833">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-833">**Description**</span></span>

<span data-ttu-id="c4da6-834">Эта служба пытается получить указанный HTTP-запрос URL-адреса в указанном пакете запроса.</span><span class="sxs-lookup"><span data-stu-id="c4da6-834">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="c4da6-835">Если запрашиваемый HTTP-запрос отсутствует, подпрограмма возвращает состояние NX_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="c4da6-835">If the requested HTTP query is not present, this routine returns a status of NX_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="c4da6-836">Эту подпрограмму следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="c4da6-836">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_http_server_create()*).</span></span>

<span data-ttu-id="c4da6-837">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-837">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-838">**packet_ptr**: указатель на пакет запроса HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="c4da6-838">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="c4da6-839">Обратите внимание, что приложение не должно освобождать этот пакет.</span><span class="sxs-lookup"><span data-stu-id="c4da6-839">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="c4da6-840">**query_number**: логический номер параметра, начинающийся с нуля, слева направо в списке запросов</span><span class="sxs-lookup"><span data-stu-id="c4da6-840">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
- <span data-ttu-id="c4da6-841">**query_ptr**: область назначения для копирования запроса</span><span class="sxs-lookup"><span data-stu-id="c4da6-841">**query_ptr** Destination area to copy the query.</span></span>
- <span data-ttu-id="c4da6-842">**max_query_size**: максимальный размер области назначения запроса</span><span class="sxs-lookup"><span data-stu-id="c4da6-842">**max_query_size** Maximum size of the query destination area.</span></span>

<span data-ttu-id="c4da6-843">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-843">**Return Values**</span></span>

- <span data-ttu-id="c4da6-844">**NX_SUCCESS** (0x00) — запрос HTTP-сервера успешно получен.</span><span class="sxs-lookup"><span data-stu-id="c4da6-844">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
- <span data-ttu-id="c4da6-845">**NX_HTTP_FAILED** (0xE2) — слишком маленький размер запроса.</span><span class="sxs-lookup"><span data-stu-id="c4da6-845">**NX_HTTP_FAILED** (0xE2) Query size too small.</span></span>
- <span data-ttu-id="c4da6-846">**NX_HTTP_NOT_FOUND** (0xE6) — указанный запрос не найден.</span><span class="sxs-lookup"><span data-stu-id="c4da6-846">**NX_HTTP_NOT_FOUND** (0xE6) Specified query not found</span></span>
- <span data-ttu-id="c4da6-847">**NX_HTTP_NO_QUERY_PARSED** (0xF2) — нет запроса в запросе клиента.</span><span class="sxs-lookup"><span data-stu-id="c4da6-847">**NX_HTTP_NO_QUERY_PARSED** (0xF2) No query in Client request</span></span>
- <span data-ttu-id="c4da6-848">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-848">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="c4da6-849">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="c4da6-849">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="c4da6-850">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-850">**Allowed From**</span></span>

<span data-ttu-id="c4da6-851">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-851">Threads</span></span>

<span data-ttu-id="c4da6-852">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-852">**Example**</span></span>

```c
/* Assuming we are in the application’s request notify callback
routine, get the first query of the HTTP Client request. */
status = nx_http_server_query_get(request_packet_ptr, 0, query_destination, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
in “query_destination.” */
```

##   
<span data-ttu-id="c4da6-853">nx_http_server_start</span><span class="sxs-lookup"><span data-stu-id="c4da6-853">nx_http_server_start</span></span>

### <a name="start-the-http-server"></a><span data-ttu-id="c4da6-854">Запуск HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-854">Start the HTTP Server</span></span>

<span data-ttu-id="c4da6-855">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-855">**Prototype**</span></span>

```c
UINT nx_http_server_start(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="c4da6-856">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-856">**Description**</span></span>

<span data-ttu-id="c4da6-857">Эта служба запускает ранее созданный экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c4da6-857">This service starts the previously create HTTP Server instance.</span></span>

<span data-ttu-id="c4da6-858">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-858">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-859">**http_server_ptr**: указатель на экземпляр HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-859">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

<span data-ttu-id="c4da6-860">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-860">**Return Values**</span></span>

- <span data-ttu-id="c4da6-861">**NX_SUCCESS** (0x00) — HTTP-сервер успешно запущен.</span><span class="sxs-lookup"><span data-stu-id="c4da6-861">**NX_SUCCESS** (0x00) Successful HTTP Server start</span></span>
- <span data-ttu-id="c4da6-862">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-862">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="c4da6-863">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-863">**Allowed From**</span></span>

<span data-ttu-id="c4da6-864">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-864">Initialization, Threads</span></span>

<span data-ttu-id="c4da6-865">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-865">**Example**</span></span>

```c
/* Start the HTTP Server instance “my_server.” */
status = nx_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_http_server_stop"></a><span data-ttu-id="c4da6-866">nx_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="c4da6-866">nx_http_server_stop</span></span>

### <a name="stop-the-http-server"></a><span data-ttu-id="c4da6-867">Остановка HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-867">Stop the HTTP Server</span></span>

<span data-ttu-id="c4da6-868">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-868">**Prototype**</span></span>

```c
UINT nx_http_server_stop(NX_HTTP_SERVER *http_server_ptr);
```

<span data-ttu-id="c4da6-869">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-869">**Description**</span></span>

<span data-ttu-id="c4da6-870">Эта служба останавливает ранее созданный экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c4da6-870">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="c4da6-871">Эту подпрограмму следует вызывать до удаления экземпляра HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="c4da6-871">This routine should be called prior to deleting an HTTP Server instance.</span></span>

<span data-ttu-id="c4da6-872">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-872">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-873">**http_server_ptr**: указатель на экземпляр HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-873">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

<span data-ttu-id="c4da6-874">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-874">**Return Values**</span></span>

- <span data-ttu-id="c4da6-875">**NX_SUCCESS** (0x00) — HTTP-сервер успешно остановлен.</span><span class="sxs-lookup"><span data-stu-id="c4da6-875">**NX_SUCCESS** (0x00) Successful HTTP Server stop</span></span>
- <span data-ttu-id="c4da6-876">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-876">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="c4da6-877">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="c4da6-877">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

<span data-ttu-id="c4da6-878">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-878">**Allowed From**</span></span>

<span data-ttu-id="c4da6-879">Потоки</span><span class="sxs-lookup"><span data-stu-id="c4da6-879">Threads</span></span>

<span data-ttu-id="c4da6-880">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-880">**Example**</span></span>

```c
/* Stop the HTTP Server instance “my_server.” */

status = nx_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_http_server_type_get"></a><span data-ttu-id="c4da6-881">nx_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="c4da6-881">nx_http_server_type_get</span></span>

### <a name="extract-file-type-from-client-http-request"></a><span data-ttu-id="c4da6-882">Извлечение типа файла из HTTP-запроса клиента</span><span class="sxs-lookup"><span data-stu-id="c4da6-882">Extract file type from Client HTTP request</span></span>

<span data-ttu-id="c4da6-883">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-883">**Prototype**</span></span>

```c
UINT nx_http_server_type_get(NX_HTTP_SERVER *http_server_ptr,
                            CHAR *name, CHAR *http_type_string);
```

<span data-ttu-id="c4da6-884">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-884">**Description**</span></span>

<span data-ttu-id="c4da6-885">Эта служба извлекает тип HTTP-запроса в буфере *http_type_string* и его длину в возвращаемом значении из *имени* входного буфера (обычно это URL-адрес).</span><span class="sxs-lookup"><span data-stu-id="c4da6-885">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="c4da6-886">Если сопоставление MIME не найдено, по умолчанию используется тип text/plain.</span><span class="sxs-lookup"><span data-stu-id="c4da6-886">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="c4da6-887">В противном случае извлеченный тип сравнивается с сопоставлениями MIME HTTP-сервера по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c4da6-887">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="c4da6-888">Сопоставления MIME по умолчанию в HTTP-сервере NetX</span><span class="sxs-lookup"><span data-stu-id="c4da6-888">The default MIME maps in NetX HTTP Server are:</span></span>

- <span data-ttu-id="c4da6-889">HTML — текст или HTML</span><span class="sxs-lookup"><span data-stu-id="c4da6-889">html text/html</span></span>
- <span data-ttu-id="c4da6-890">HTM — текст или HTML</span><span class="sxs-lookup"><span data-stu-id="c4da6-890">htm text/html</span></span>
- <span data-ttu-id="c4da6-891">TXT — текст или обычный текст</span><span class="sxs-lookup"><span data-stu-id="c4da6-891">txt text/plain</span></span>
- <span data-ttu-id="c4da6-892">GIF — изображение или GIF</span><span class="sxs-lookup"><span data-stu-id="c4da6-892">gif image/gif</span></span>
- <span data-ttu-id="c4da6-893">JPEG — изображение или JPEG</span><span class="sxs-lookup"><span data-stu-id="c4da6-893">jpg image/jpeg</span></span>
- <span data-ttu-id="c4da6-894">ICO — изображение или x-icon</span><span class="sxs-lookup"><span data-stu-id="c4da6-894">ico image/x-icon</span></span>

<span data-ttu-id="c4da6-895">Если оно задано, оно также будет искать определенный пользователем набор дополнительных сопоставлений MIME.</span><span class="sxs-lookup"><span data-stu-id="c4da6-895">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="c4da6-896">Дополнительные сведения об определяемых пользователем сопоставлениях см. в описании *nx_http_server_mime_maps_addtional_set()* .</span><span class="sxs-lookup"><span data-stu-id="c4da6-896">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="c4da6-897">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="c4da6-897">This service is deprecated.</span></span> <span data-ttu-id="c4da6-898">Разработчикам рекомендуется перейти на использование *nx_http_server_type_get_extended()* .</span><span class="sxs-lookup"><span data-stu-id="c4da6-898">Developers are encouraged to migrate to *nx_http_server_type_get_extended().*</span></span>

<span data-ttu-id="c4da6-899">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-899">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-900">**http_server_pt**: указатель на экземпляр HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-900">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="c4da6-901">**name**: указатель на буфер для поиска</span><span class="sxs-lookup"><span data-stu-id="c4da6-901">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="c4da6-902">**http_type_string**: указатель на извлеченный тип HTML</span><span class="sxs-lookup"><span data-stu-id="c4da6-902">**http_type_string** (Pointer to extracted HTML type)</span></span>

<span data-ttu-id="c4da6-903">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-903">**Return Values**</span></span>

- <span data-ttu-id="c4da6-904">**Длина строки в байтах** — значение, отличное от нуля, означает успех.</span><span class="sxs-lookup"><span data-stu-id="c4da6-904">**Length of string in bytes** Non zero value is success</span></span>
- <span data-ttu-id="c4da6-905">**Нуль означает ошибку**</span><span class="sxs-lookup"><span data-stu-id="c4da6-905">**Zero indicates error**</span></span>

<span data-ttu-id="c4da6-906">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-906">**Allowed From**</span></span>

<span data-ttu-id="c4da6-907">Приложение</span><span class="sxs-lookup"><span data-stu-id="c4da6-907">Application</span></span>

<span data-ttu-id="c4da6-908">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-908">**Example**</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting 
client requests when *nx_http_server_start* is called*/

CHAR temp_string[20];
UINT string_length;

/* Extract the HTTP type. */
string_length = nx_http_server_type_get(&my_server_ptr,
                my_server.nx_http_server_request_resource, temp_string);

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="c4da6-909">Более подробный пример см. в описании</span><span class="sxs-lookup"><span data-stu-id="c4da6-909">For a more detailed example, see the description for</span></span>

<span data-ttu-id="c4da6-910">*nx_http_server_callback_generate_response_header*.</span><span class="sxs-lookup"><span data-stu-id="c4da6-910">*nx_http_server_callback_generate_response_header.*</span></span>

## <a name="nx_http_server_type_get_extended"></a><span data-ttu-id="c4da6-911">nx_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="c4da6-911">nx_http_server_type_get_extended</span></span>

### <a name="extract-file-type-from-client-http-request"></a><span data-ttu-id="c4da6-912">Извлечение типа файла из HTTP-запроса клиента</span><span class="sxs-lookup"><span data-stu-id="c4da6-912">Extract file type from Client HTTP request</span></span>

<span data-ttu-id="c4da6-913">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-913">**Prototype**</span></span>

```c
UINT nx_http_server_type_get_extended(
     NX_HTTP_SERVER *http_server_ptr,
     CHAR *name, CHAR *http_type_string,
     UINT http_type_string_max_size);
```

<span data-ttu-id="c4da6-914">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-914">**Description**</span></span>

<span data-ttu-id="c4da6-915">Эта служба извлекает тип HTTP-запроса в буфере *http_type_string* и его длину в возвращаемом значении из *имени* входного буфера (обычно это URL-адрес).</span><span class="sxs-lookup"><span data-stu-id="c4da6-915">This service extracts the HTTP request type in the buffer *http_type_string* and its length in the return value from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="c4da6-916">Если сопоставление MIME не найдено, по умолчанию используется тип text/plain.</span><span class="sxs-lookup"><span data-stu-id="c4da6-916">If no MIME map is found, it defaults to the “text/plain” type.</span></span> <span data-ttu-id="c4da6-917">В противном случае извлеченный тип сравнивается с сопоставлениями MIME HTTP-сервера по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="c4da6-917">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="c4da6-918">Сопоставления MIME по умолчанию в HTTP-сервере NetX Duo</span><span class="sxs-lookup"><span data-stu-id="c4da6-918">The default MIME maps in NetX Duo HTTP Server are:</span></span>

- <span data-ttu-id="c4da6-919">HTML — текст или HTML</span><span class="sxs-lookup"><span data-stu-id="c4da6-919">html text/html</span></span>
- <span data-ttu-id="c4da6-920">HTM — текст или HTML</span><span class="sxs-lookup"><span data-stu-id="c4da6-920">htm text/html</span></span>
- <span data-ttu-id="c4da6-921">TXT — текст или обычный текст</span><span class="sxs-lookup"><span data-stu-id="c4da6-921">txt text/plain</span></span>
- <span data-ttu-id="c4da6-922">GIF — изображение или GIF</span><span class="sxs-lookup"><span data-stu-id="c4da6-922">gif image/gif</span></span>
- <span data-ttu-id="c4da6-923">JPEG — изображение или JPEG</span><span class="sxs-lookup"><span data-stu-id="c4da6-923">jpg image/jpeg</span></span>
- <span data-ttu-id="c4da6-924">ICO — изображение или x-icon</span><span class="sxs-lookup"><span data-stu-id="c4da6-924">ico image/x-icon</span></span>

<span data-ttu-id="c4da6-925">Если оно задано, оно также будет искать определенный пользователем набор дополнительных сопоставлений MIME.</span><span class="sxs-lookup"><span data-stu-id="c4da6-925">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="c4da6-926">Дополнительные сведения об определяемых пользователем сопоставлениях см. в описании *nx_http_server_mime_maps_addtional_set()* .</span><span class="sxs-lookup"><span data-stu-id="c4da6-926">See *nx_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="c4da6-927">Эта служба заменяет *nx_http_server_type_get()* .</span><span class="sxs-lookup"><span data-stu-id="c4da6-927">This service replaces *nx_http_server_type_get().*</span></span> <span data-ttu-id="c4da6-928">Эта версия предоставляет дополнительные сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="c4da6-928">This version supplies additional length information.</span></span>

<span data-ttu-id="c4da6-929">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-929">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-930">**http_server_pt**: указатель на экземпляр HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-930">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="c4da6-931">**name**: указатель на буфер для поиска</span><span class="sxs-lookup"><span data-stu-id="c4da6-931">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="c4da6-932">**name_length**: длина буфера для поиска</span><span class="sxs-lookup"><span data-stu-id="c4da6-932">**name_length** Length of buffer to search</span></span>
- <span data-ttu-id="c4da6-933">**http_type_string**: указатель на извлеченный тип HTML</span><span class="sxs-lookup"><span data-stu-id="c4da6-933">**http_type_string** (Pointer to extracted HTML type)</span></span>
- <span data-ttu-id="c4da6-934">**http_type_string_max_size**</span><span class="sxs-lookup"><span data-stu-id="c4da6-934">**http_type_string_max_size**</span></span>

<span data-ttu-id="c4da6-935">Размер буфера *http_type_string*</span><span class="sxs-lookup"><span data-stu-id="c4da6-935">Size of the *http_type_string* buffer</span></span>

<span data-ttu-id="c4da6-936">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-936">**Return Values**</span></span>

- <span data-ttu-id="c4da6-937">**Длина строки в байтах** — значение, отличное от нуля, означает успех.</span><span class="sxs-lookup"><span data-stu-id="c4da6-937">**Length of string in bytes** Non zero value is success</span></span><br /><span data-ttu-id="c4da6-938">Нуль означает ошибку</span><span class="sxs-lookup"><span data-stu-id="c4da6-938">Zero indicates error</span></span>

<span data-ttu-id="c4da6-939">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-939">**Allowed From**</span></span>

<span data-ttu-id="c4da6-940">Приложение</span><span class="sxs-lookup"><span data-stu-id="c4da6-940">Application</span></span>

<span data-ttu-id="c4da6-941">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-941">**Example**</span></span>

```c
/* my_server is a previously created HTTP server, which starts accepting 
client requests when *nx_http_server_start* is called*/

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
string_length = nx_http_server_type_get_extended(&my_server,
                my_server.nx_http_server_request_resource, resource_length,
                temp_string, sizeof(temp_string));

/* If string_length is non zero, the HTTP string is extracted. */
```

<span data-ttu-id="c4da6-942">Более подробный пример см. в описании</span><span class="sxs-lookup"><span data-stu-id="c4da6-942">For a more detailed example, see the description for</span></span>

<span data-ttu-id="c4da6-943">*nx_http_server_callback_generate_response_header*.</span><span class="sxs-lookup"><span data-stu-id="c4da6-943">*nx_http_server_callback_generate_response_header.*</span></span>

## <a name="nx_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="c4da6-944">nx_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="c4da6-944">nx_http_server_digest_authenticate_notify_set</span></span>

### <a name="set-digest-authenticate-callback-function"></a><span data-ttu-id="c4da6-945">Задание функции обратного вызова дайджест-проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="c4da6-945">Set digest authenticate callback function</span></span>

<span data-ttu-id="c4da6-946">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-946">**Prototype**</span></span>

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

<span data-ttu-id="c4da6-947">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-947">**Description**</span></span>

<span data-ttu-id="c4da6-948">Эта служба задает обратный вызов, вызываемый при выполнении дайджест-проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="c4da6-948">This service sets the callback invoked when digest authenticate is performed.</span></span>

<span data-ttu-id="c4da6-949">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-949">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-950">**http_server_pt**: указатель на экземпляр HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-950">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="c4da6-951">**digest_authenticate_callback**: указатель на обратный вызов дайджест-проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="c4da6-951">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

<span data-ttu-id="c4da6-952">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-952">**Return Values**</span></span>

- <span data-ttu-id="c4da6-953">**NX_SUCCESS** (0x00) — обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="c4da6-953">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="c4da6-954">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-954">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="c4da6-955">NX_NOT_SUPPORTED (0x4B) — дайджест-проверка подлинности не включена.</span><span class="sxs-lookup"><span data-stu-id="c4da6-955">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

<span data-ttu-id="c4da6-956">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-956">**Allowed From**</span></span>

<span data-ttu-id="c4da6-957">Приложение</span><span class="sxs-lookup"><span data-stu-id="c4da6-957">Application</span></span>

<span data-ttu-id="c4da6-958">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-958">**Example**</span></span>

```c
UINT digest_authenticate_callback(NX_HTTP_SERVER *server_ptr, CHAR *name_ptr,
                                 CHAR *realm_ptr, CHAR *password_ptr,
                                 CHAR *method,CHAR *authorization_uri,
                                 CHAR *authorization_nc,
                                 CHAR *authorization_cnonce)
{
    return(NX_SUCCESS);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and
before starting HTTP services when nx_http_server_start is called, set the
digest authenticate callback: */

status = nx_http_server_digest_authenticate_notify_set (&my_server,
                                                       digest_authenticate_callback);

/* If status equals NX_SUCCESS, the digest_authenticate_callback function
will be called when the HTTP server performs digest authenticate. */
```

## <a name="nx_http_server_authentication_check_set"></a><span data-ttu-id="c4da6-959">nx_http_server_authentication_check_set</span><span class="sxs-lookup"><span data-stu-id="c4da6-959">nx_http_server_authentication_check_set</span></span>

### <a name="set-authentication-checking-callback-function"></a><span data-ttu-id="c4da6-960">Задание функции обратного вызова проверки для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="c4da6-960">Set authentication checking callback function</span></span>

<span data-ttu-id="c4da6-961">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="c4da6-961">**Prototype**</span></span>

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

<span data-ttu-id="c4da6-962">**Описание**</span><span class="sxs-lookup"><span data-stu-id="c4da6-962">**Description**</span></span>

<span data-ttu-id="c4da6-963">Эта служба задает функцию обратного вызова проверки для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="c4da6-963">This service sets the callback function of authentication checking.</span></span>

<span data-ttu-id="c4da6-964">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="c4da6-964">**Input Parameters**</span></span>

- <span data-ttu-id="c4da6-965">**http_server_pt**: указатель на экземпляр HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="c4da6-965">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="c4da6-966">**authentication_check_extended**: указатель на проверку для проверки подлинности приложения</span><span class="sxs-lookup"><span data-stu-id="c4da6-966">**authentication_check_extended** Pointer to application’s authentication checking</span></span>

<span data-ttu-id="c4da6-967">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="c4da6-967">**Return Values**</span></span>

- <span data-ttu-id="c4da6-968">**NX_SUCCESS** (0x00) — обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="c4da6-968">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="c4da6-969">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="c4da6-969">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

<span data-ttu-id="c4da6-970">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="c4da6-970">**Allowed From**</span></span>

<span data-ttu-id="c4da6-971">Приложение</span><span class="sxs-lookup"><span data-stu-id="c4da6-971">Application</span></span>

<span data-ttu-id="c4da6-972">**Пример**</span><span class="sxs-lookup"><span data-stu-id="c4da6-972">**Example**</span></span>

```c
static UINT authentication_check_extended(NX_HTTP_SERVER *server_ptr,
                                         UINT request_type, CHAR *resource,
                                         CHAR **name, UINT *name_length,
                                         CHAR **password, 
                                         UINT *password_length,
                                         CHAR **realm, UINT *realm_length)
{

    /* Just use a simple name, password, and realm for all
    requests and resources. */

    *name = "name";
    *password = "password";
    *realm = "NetX Duo HTTP demo";
    *name_length = 4;
    *password_length = 8;
    *realm_length = 18;

    /* Request basic authentication. */
    return(NX_HTTP_BASIC_AUTHENTICATE);
}

NX_HTTP_SERVER my_server;

/* After the HTTP server is created by calling nx_http_server_create, and
before starting HTTP services when nx_http_server_start is called, set 
the authentication checking callback: */

nx_http_server_authentication_check_set (&my_server,
                                        authentication_check_extended);
```