---
title: Глава 3. Описание служб HTTP
description: В этой главе приведено описание всех служб NetX Web HTTP (перечислены ниже) в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6bb2743f05c5b56331d1c0e948601ad23bf340d1
ms.sourcegitcommit: 95f4ae0842a486fec8f10d1480203695faa9592d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2021
ms.locfileid: "111875278"
---
# <a name="chapter-3---description-of-http-services"></a><span data-ttu-id="34cb8-103">Глава 3. Описание служб HTTP</span><span class="sxs-lookup"><span data-stu-id="34cb8-103">Chapter 3 - Description of HTTP services</span></span>

<span data-ttu-id="34cb8-104">В этой главе приведено описание всех служб NetX Web HTTP (перечислены ниже) в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="34cb8-104">This chapter contains a description of all NetX Web HTTP services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="34cb8-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, используемым для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="34cb8-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="http-and-https-client-api"></a><span data-ttu-id="34cb8-106">API HTTP- и HTTPS-клиентов</span><span class="sxs-lookup"><span data-stu-id="34cb8-106">HTTP and HTTPS Client API</span></span>

## <a name="nx_web_http_client_connect"></a><span data-ttu-id="34cb8-107">nx_web_http_client_connect</span><span class="sxs-lookup"><span data-stu-id="34cb8-107">nx_web_http_client_connect</span></span>

<span data-ttu-id="34cb8-108">Открытие сокета без шифрования на HTTP-сервере для пользовательских запросов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-108">Open a plaintext socket to an HTTP server for custom requests</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-109">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-109">Prototype</span></span>

```C
UINT nx_web_http_client_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip,
    UINT server_port, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-110">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-110">Description</span></span>

<span data-ttu-id="34cb8-111">Этот метод предназначен для протокола HTTP **без шифрования**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-111">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="34cb8-112">Данная служба открывает сокет TCP без шифрования для HTTP-сервера, но не отправляет запросы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-112">This service opens a plaintext TCP socket to an HTTP server but does not send any requests.</span></span> <span data-ttu-id="34cb8-113">Для создания запросов используется служба *nx_web_http_client_request_initialize()* , а для отправки — служба *nx_web_http_client_request_send()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-113">Requests are created with n *x_web_http_client_request_initialize()* and sent using *nx_web_http_client_request_send()*.</span></span> <span data-ttu-id="34cb8-114">Пользовательские заголовки HTTP можно добавить в запрос с помощью службы *nx_web_http_client_request_header_add()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-114">Custom HTTP headers may be added to the request using *nx_web_http_client_request_header_add()*.</span></span>

<span data-ttu-id="34cb8-115">С помощью этой службы приложение может добавить в запрос любое количество пользовательских заголовков.</span><span class="sxs-lookup"><span data-stu-id="34cb8-115">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="34cb8-116">**Это позволяет создавать пользовательские HTTP-запросы, предназначенные для конкретных приложений.**</span><span class="sxs-lookup"><span data-stu-id="34cb8-116">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="34cb8-117">Методы nx_web_http_client_ \*_start предоставляются для удобства (например, *nx_web_http_client_get_start*()) и управляют созданием запросов и подключением к сокетам.</span><span class="sxs-lookup"><span data-stu-id="34cb8-117">The nx_web_http_client_\*_start methods are provided for convenience (e.g. *nx_web_http_client_get_start*()) and handle the request generation and socket connection.</span></span> <span data-ttu-id="34cb8-118">Эти службы можно использовать вместо службы *nx_web_http_client_connect()* и связанных подпрограмм, если в запросах не требуются пользовательские заголовки HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-118">You can use those services instead of *nx_web_http_client_connect()* and the related routines if you do not need custom HTTP headers in your requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-119">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-119">Input Parameters</span></span>

- <span data-ttu-id="34cb8-120">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-120">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-121">**server_ip**: IP-адрес удаленного HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-121">**server_ip** IP address of remote HTTP server.</span></span>
- <span data-ttu-id="34cb8-122">**server_port**: порт на удаленном HTTP-сервере (например, 80 для HTTP).</span><span class="sxs-lookup"><span data-stu-id="34cb8-122">**server_port** Port on remote HTTP server (e.g. 80 for HTTP).</span></span>
- <span data-ttu-id="34cb8-123">**wait_option**: определяет, как долго служба будет ожидать операций базовой сети.</span><span class="sxs-lookup"><span data-stu-id="34cb8-123">**wait_option** Defines how long the service will wait for underlying network operations.</span></span> <span data-ttu-id="34cb8-124">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-124">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-125">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-125">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-126">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-126">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-127">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-127">Return Values</span></span>

- <span data-ttu-id="34cb8-128">**NX_SUCCESS** (0X00): сокет TCP успешно подключен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-128">**NX_SUCCESS** (0x00) Successful connection of TCP socket.</span></span>
- <span data-ttu-id="34cb8-129">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-129">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-130">NX_WEB_HTTP_NOT_READY (0x3000A): уже выполняется другой запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-130">NX_WEB_HTTP_NOT_READY (0x3000A) Another request is already in progress.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-131">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-131">Allowed From</span></span>

<span data-ttu-id="34cb8-132">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-132">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-133">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-133">Example</span></span>

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
    "https://192.168.1.150/test.txt ", "host.com",
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
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="nx_web_http_client_create"></a><span data-ttu-id="34cb8-134">nx_web_http_client_create</span><span class="sxs-lookup"><span data-stu-id="34cb8-134">nx_web_http_client_create</span></span>

<span data-ttu-id="34cb8-135">Создание экземпляра HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-135">Create an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-136">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-136">Prototype</span></span>

```C
UINT nx_web_http_client_create(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr,
    ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="34cb8-137">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-137">Description</span></span>

<span data-ttu-id="34cb8-138">Эта служба создает экземпляр HTTP-клиента в указанном экземпляре IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-138">This service creates an HTTP Client instance on the specified IP instance.</span></span> <span data-ttu-id="34cb8-139">Этот экземпляр клиента можно использовать как для протокола HTTP, так и для протокола HTTPS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-139">The Client instance can be used for either HTTP or HTTPS.</span></span> <span data-ttu-id="34cb8-140">Дополнительные сведения о запуске экземпляра HTTP или HTTPS см. в описании служб *nx_web_http_client_connect()* и *nx_web_http_client_secure_connect()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-140">See the services *nx_web_http_client_connect()* and *nx_web_http_client_secure_connect()* for more information on starting an HTTP or HTTPS instance.</span></span> <span data-ttu-id="34cb8-141">Также ознакомьтесь с интерфейсами API для служб *nx_web_http_client_get_\*\*, *nx_web_http_client_put_** и \*nx_web_http_client_post_\*\*, чтобы узнать, как просто вызывать методы GET, WHERE и POST.</span><span class="sxs-lookup"><span data-stu-id="34cb8-141">Also refer to the API for \*nx_web_http_client_get_\*\*, *nx_web_http_client_put_\*\*, *nx_web_http_client_post_** for simple invocations of GET, PUT, and POST methods.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-142">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-142">Input Parameters</span></span>

- <span data-ttu-id="34cb8-143">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-143">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-144">**client_name**: имя экземпляра HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="34cb8-144">**client_name** Name of HTTP Client instance.</span></span>
- <span data-ttu-id="34cb8-145">**ip_ptr**: указатель на экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="34cb8-145">**ip_ptr** Pointer to IP instance.</span></span>
- <span data-ttu-id="34cb8-146">**pool_ptr**: указатель на пул пакетов по умолчанию</span><span class="sxs-lookup"><span data-stu-id="34cb8-146">**pool_ptr** Pointer to default packet pool.</span></span> <span data-ttu-id="34cb8-147">Обратите внимание, что пакеты в этом пуле должны иметь объем полезных данных, достаточный для работы с полным заголовком ответа.</span><span class="sxs-lookup"><span data-stu-id="34cb8-147">Note that the packets in this pool must have a payload large enough to handle the complete response header.</span></span> <span data-ttu-id="34cb8-148">Это определяет параметр *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* в файле *nx_web_http_client.h*.</span><span class="sxs-lookup"><span data-stu-id="34cb8-148">This is defined by *NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE* in *nx_web_http_client.h*.</span></span>
- <span data-ttu-id="34cb8-149">**window_size**: размер окна приема сокета TCP клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-149">**window_size** Size of the Client’s TCP socket receive window.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-150">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-150">Return Values</span></span>

- <span data-ttu-id="34cb8-151">**NX_SUCCESS** (0x00): HTTP-клиент успешно создан.</span><span class="sxs-lookup"><span data-stu-id="34cb8-151">**NX_SUCCESS** (0x00) Successful HTTP Client create</span></span>
- <span data-ttu-id="34cb8-152">NX_PTR_ERROR (0x16): недопустимый указатель на HTTP, ip_ptr или пул пакетов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-152">NX_PTR_ERROR (0x16) Invalid HTTP, ip_ptr, or packet pool pointer</span></span>
- <span data-ttu-id="34cb8-153">NX_WEB_HTTP_POOL_ERROR (0x30009): недопустимый размер полезных данных в пуле пакетов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-153">NX_WEB_HTTP_POOL_ERROR (0x30009) Invalid payload size in packet pool</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-154">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-154">Allowed From</span></span>

<span data-ttu-id="34cb8-155">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-155">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-156">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-156">Example</span></span>

```C
/* Create the HTTP Client instance "my_client" on "ip_0". */
status = nx_web_http_client_create(&my_client, "my client", &ip_0, &pool_0, 8192);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    created. */
```

## <a name="nx_web_http_client_delete"></a><span data-ttu-id="34cb8-157">nx_web_http_client_delete</span><span class="sxs-lookup"><span data-stu-id="34cb8-157">nx_web_http_client_delete</span></span>

<span data-ttu-id="34cb8-158">Удаление экземпляра HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-158">Delete an HTTP Client Instance</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-159">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-159">Prototype</span></span>

```C
UINT nx_web_http_client_delete(NX_WEB_HTTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="34cb8-160">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-160">Description</span></span>

<span data-ttu-id="34cb8-161">Эта служба удаляет ранее созданный экземпляр HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-161">This service deletes a previously created HTTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-162">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-162">Input Parameters</span></span>

- <span data-ttu-id="34cb8-163">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-163">**client_ptr** Pointer to HTTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-164">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-164">Return Values</span></span>

- <span data-ttu-id="34cb8-165">**NX_SUCCESS** (0x00): HTTP-клиент успешно удален.</span><span class="sxs-lookup"><span data-stu-id="34cb8-165">**NX_SUCCESS** (0x00) Successful HTTP Client delete</span></span>
- <span data-ttu-id="34cb8-166">NX_PTR_ERROR (0x16) — недопустимый указатель на HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-166">NX_PTR_ERROR (0x16) Invalid HTTP pointer</span></span>
- <span data-ttu-id="34cb8-167">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-167">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-168">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-168">Allowed From</span></span>

<span data-ttu-id="34cb8-169">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-169">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-170">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-170">Example</span></span>

```C
/* Delete the HTTP Client instance "my_client." */
status = nx_web_http_client_delete(&my_client);

/* If status is NX_SUCCESS an HTTP Client instance was successfully
    deleted. */
```

## <a name="nx_web_http_client_delete_start"></a><span data-ttu-id="34cb8-171">nx_web_http_client_delete_start</span><span class="sxs-lookup"><span data-stu-id="34cb8-171">nx_web_http_client_delete_start</span></span>

<span data-ttu-id="34cb8-172">Выполнение HTTP-запроса DELETE без шифрования.</span><span class="sxs-lookup"><span data-stu-id="34cb8-172">Start a plaintext HTTP DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-173">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-173">Prototype</span></span>

```C
UINT nx_web_http_client_delete_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-174">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-174">Description</span></span>

<span data-ttu-id="34cb8-175">Этот метод предназначен для протокола HTTP **без шифрования**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-175">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="34cb8-176">Эта служба пытается отправить запрос DELETE для ресурса, заданного указателем resource, в созданном ранее экземпляре HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-176">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="34cb8-177">Если эта подпрограмма вернет значение NX_SUCCESS, то приложение сможет вызвать метод *nx_web_http_client_response_body_get()* , чтобы получить ответ сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-177">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="34cb8-178">Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.</span><span class="sxs-lookup"><span data-stu-id="34cb8-178">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="34cb8-179">Это нерекомендуемый API.</span><span class="sxs-lookup"><span data-stu-id="34cb8-179">This API is deprecated.</span></span> <span data-ttu-id="34cb8-180">Разработчикам рекомендуется использовать службу *nx_web_http_client_delete_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-180">Developers are encouraged to use *nx_web_http_client_delete_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-181">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-181">Input Parameters</span></span>

- <span data-ttu-id="34cb8-182">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-182">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-183">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-183">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-184">**server_port**: порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-184">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-185">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-185">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-186">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-186">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-187">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-187">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-188">**resource**: указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-188">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="34cb8-189">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-189">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-190">**password**: указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-190">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-191">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-191">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-192">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-192">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-193">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-193">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-194">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-194">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-195">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-195">Return Values</span></span>

- <span data-ttu-id="34cb8-196">**NX_SUCCESS** (0x00): запрос DELETE HTTP-клиента успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-196">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="34cb8-197">**NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-197">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="34cb8-198">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-198">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-199">**NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-199">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-200">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="34cb8-200">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="34cb8-201">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-201">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-202">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-202">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-203">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-203">Allowed From</span></span>

<span data-ttu-id="34cb8-204">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-204">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-205">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-205">Example</span></span>

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

## <a name="nx_web_http_client_delete_start_extended"></a><span data-ttu-id="34cb8-206">nx_web_http_client_delete_start_extended</span><span class="sxs-lookup"><span data-stu-id="34cb8-206">nx_web_http_client_delete_start_extended</span></span>

<span data-ttu-id="34cb8-207">Выполнение HTTP-запроса DELETE без шифрования.</span><span class="sxs-lookup"><span data-stu-id="34cb8-207">Start a plaintext HTTP DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-208">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-208">Prototype</span></span>

```C
UINT nx_web_http_client_delete_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-209">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-209">Description</span></span>

<span data-ttu-id="34cb8-210">Этот метод предназначен для протокола HTTP **без шифрования**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-210">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="34cb8-211">Эта служба пытается отправить запрос DELETE для ресурса, заданного указателем resource, в созданном ранее экземпляре HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-211">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="34cb8-212">Если эта подпрограмма вернет значение NX_SUCCESS, то приложение сможет вызвать метод *nx_web_http_client_response_body_get()* , чтобы получить ответ сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-212">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="34cb8-213">Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.</span><span class="sxs-lookup"><span data-stu-id="34cb8-213">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="34cb8-214">Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-214">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="34cb8-215">Эта служба заменяет *nx_web_http_client_delete_start*().</span><span class="sxs-lookup"><span data-stu-id="34cb8-215">This service replaces *nx_web_http_client_delete_start* ().</span></span> <span data-ttu-id="34cb8-216">В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="34cb8-216">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-217">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-217">Input Parameters</span></span>

- <span data-ttu-id="34cb8-218">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-218">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-219">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-219">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-220">**server_port**: порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-220">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-221">**resource**: указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-221">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="34cb8-222">**resource_length**: длина строки для запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-222">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="34cb8-223">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-223">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-224">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-224">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-225">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-225">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-226">**host_length**: длина строки узла.</span><span class="sxs-lookup"><span data-stu-id="34cb8-226">**host_length** String length of host.</span></span>
- <span data-ttu-id="34cb8-227">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-227">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-228">**username_length**: длина строки имени пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-228">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="34cb8-229">**password**: указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-229">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-230">**password_length**: длина строки пароля для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-230">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="34cb8-231">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-231">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-232">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-232">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-233">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-233">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-234">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-234">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-235">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-235">Return Values</span></span>

- <span data-ttu-id="34cb8-236">**NX_SUCCESS** (0x00): запрос DELETE HTTP-клиента успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-236">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="34cb8-237">**NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-237">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="34cb8-238">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-238">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-239">**NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-239">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-240">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="34cb8-240">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="34cb8-241">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-241">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-242">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-242">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-243">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-243">Allowed From</span></span>

<span data-ttu-id="34cb8-244">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-244">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-245">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-245">Example</span></span>

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

## <a name="nx_web_http_client_delete_secure_start"></a><span data-ttu-id="34cb8-246">nx_web_http_client_delete_secure_start</span><span class="sxs-lookup"><span data-stu-id="34cb8-246">nx_web_http_client_delete_secure_start</span></span>

<span data-ttu-id="34cb8-247">Выполнение зашифрованного HTTPS-запроса DELETE.</span><span class="sxs-lookup"><span data-stu-id="34cb8-247">Start an encrypted HTTPS DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-248">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-248">Prototype</span></span>

```C
UINT nx_web_http_client_delete_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-249">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-249">Description</span></span>

<span data-ttu-id="34cb8-250">Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-250">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="34cb8-251">Эта служба пытается отправить запрос DELETE для ресурса, заданного указателем resource, в созданном ранее экземпляре HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-251">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="34cb8-252">Если эта подпрограмма вернет значение NX_SUCCESS, то приложение сможет вызвать метод *nx_web_http_client_response_body_get()* , чтобы получить ответ сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-252">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="34cb8-253">Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.</span><span class="sxs-lookup"><span data-stu-id="34cb8-253">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="34cb8-254">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="34cb8-254">This service is deprecated.</span></span> <span data-ttu-id="34cb8-255">Разработчикам рекомендуется использовать службу *nx_web_http_client_delete_secure_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-255">Developers are encouraged to use *nx_web_http_client_delete_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-256">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-256">Input Parameters</span></span>

- <span data-ttu-id="34cb8-257">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-257">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-258">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-258">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-259">**server_port**: порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-259">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-260">**resource**: указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-260">**resource** Pointer to URL string for requested resource.</span></span> <span data-ttu-id="34cb8-261">Это значение должно заканчиваться нулем.</span><span class="sxs-lookup"><span data-stu-id="34cb8-261">resource must be NULL-terminated.</span></span>
- <span data-ttu-id="34cb8-262">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-262">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-263">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-263">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-264">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-264">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-265">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-265">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-266">**password**: указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-266">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-267">**tls_setup**: обратный вызов, используемый для настройки конфигурации TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-267">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="34cb8-268">Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).</span><span class="sxs-lookup"><span data-stu-id="34cb8-268">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="34cb8-269">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-269">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-270">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-270">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-271">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-271">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-272">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-272">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-273">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-273">Return Values</span></span>

- <span data-ttu-id="34cb8-274">**NX_SUCCESS** (0x00): запрос DELETE HTTP-клиента успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-274">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="34cb8-275">**NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-275">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="34cb8-276">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-276">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-277">**NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-277">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-278">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="34cb8-278">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="34cb8-279">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-279">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-280">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-280">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-281">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-281">Allowed From</span></span>

<span data-ttu-id="34cb8-282">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-282">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-283">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-283">Example</span></span>

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

## <a name="nx_web_http_client_delete_secure_start_extended"></a><span data-ttu-id="34cb8-284">nx_web_http_client_delete_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="34cb8-284">nx_web_http_client_delete_secure_start_extended</span></span>

<span data-ttu-id="34cb8-285">Выполнение зашифрованного HTTPS-запроса DELETE.</span><span class="sxs-lookup"><span data-stu-id="34cb8-285">Start an encrypted HTTPS DELETE request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-286">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-286">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="34cb8-287">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-287">Description</span></span>

<span data-ttu-id="34cb8-288">Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-288">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="34cb8-289">Эта служба пытается отправить запрос DELETE для ресурса, заданного указателем resource, в созданном ранее экземпляре HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-289">This service attempts to send a DELETE request for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="34cb8-290">Если эта подпрограмма вернет значение NX_SUCCESS, то приложение сможет вызвать метод *nx_web_http_client_response_body_get()* , чтобы получить ответ сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-290">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response.</span></span>

<span data-ttu-id="34cb8-291">Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.</span><span class="sxs-lookup"><span data-stu-id="34cb8-291">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="34cb8-292">Строки ресурса, узла, имени пользователя и пароля должны завершаться нулем, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-292">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="34cb8-293">Эта служба заменяет *nx_web_http_client_delete_secure_start()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-293">This service replaces *nx_web_http_client_delete_secure_start*().</span></span> <span data-ttu-id="34cb8-294">В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="34cb8-294">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-295">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-295">Input Parameters</span></span>

- <span data-ttu-id="34cb8-296">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-296">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-297">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-297">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-298">**server_port**: порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-298">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-299">**resource**: указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-299">**resource** Pointer to URL string for requested resource.</span></span> <span data-ttu-id="34cb8-300">Это значение должно заканчиваться нулем.</span><span class="sxs-lookup"><span data-stu-id="34cb8-300">resource must be NULL-terminated.</span></span>
- <span data-ttu-id="34cb8-301">**resource_length**: длина строки для запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-301">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="34cb8-302">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-302">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-303">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-303">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-304">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-304">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-305">**host_length**: длина строки узла.</span><span class="sxs-lookup"><span data-stu-id="34cb8-305">**host_length** String length of host.</span></span>
- <span data-ttu-id="34cb8-306">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-306">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-307">**username_length**: длина строки имени пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-307">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="34cb8-308">**password**: указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-308">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-309">**password_length**: длина строки пароля для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-309">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="34cb8-310">**tls_setup**: обратный вызов, используемый для настройки конфигурации TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-310">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="34cb8-311">Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).</span><span class="sxs-lookup"><span data-stu-id="34cb8-311">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="34cb8-312">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-312">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-313">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-313">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-314">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-314">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-315">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-315">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-316">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-316">Return Values</span></span>

- <span data-ttu-id="34cb8-317">**NX_SUCCESS** (0x00): запрос DELETE HTTP-клиента успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-317">**NX_SUCCESS** (0x00) Successfully sent HTTP Client DELETE request message</span></span>
- <span data-ttu-id="34cb8-318">**NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-318">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="34cb8-319">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-319">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-320">**NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-320">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-321">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="34cb8-321">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="34cb8-322">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-322">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-323">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-323">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="34cb8-324">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-324">Allowed From</span></span>

<span data-ttu-id="34cb8-325">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-325">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-326">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-326">Example</span></span>

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

## <a name="nx_web_http_client_get_start"></a><span data-ttu-id="34cb8-327">nx_web_http_client_get_start</span><span class="sxs-lookup"><span data-stu-id="34cb8-327">nx_web_http_client_get_start</span></span>

<span data-ttu-id="34cb8-328">Выполнение HTTP-запроса GET без шифрования.</span><span class="sxs-lookup"><span data-stu-id="34cb8-328">Start a plaintext HTTP GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-329">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-329">Prototype</span></span>

```C
UINT nx_web_http_client_get_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-330">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-330">Description</span></span>

<span data-ttu-id="34cb8-331">Этот метод предназначен для протокола HTTP **без шифрования**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-331">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="34cb8-332">Эта служба пытается выполнить запрос GET к ресурсу, указанному указателем resource, в созданном ранее экземпляре HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-332">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="34cb8-333">Если эта подпрограмма возвращает NX_SUCCESS, приложение может выполнить несколько вызовов службы *nx_web_http_client_response_body_get()* , чтобы получить пакеты данных, соответствующих содержимому запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-333">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="34cb8-334">Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.</span><span class="sxs-lookup"><span data-stu-id="34cb8-334">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="34cb8-335">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="34cb8-335">This service is deprecated.</span></span> <span data-ttu-id="34cb8-336">Разработчикам рекомендуется использовать службу *nx_web_http_client_get_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-336">Developers are encouraged to use *nx_web_http_client_get_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-337">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-337">Input Parameters</span></span>

- <span data-ttu-id="34cb8-338">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-338">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-339">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-339">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-340">**server_port**: порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-340">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-341">**resource**: указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-341">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="34cb8-342">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-342">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-343">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-343">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-344">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-344">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-345">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-345">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-346">**password**: указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-346">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-347">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-347">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-348">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-348">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-349">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-349">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-350">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-350">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-351">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-351">Return Values</span></span>

- <span data-ttu-id="34cb8-352">**NX_SUCCESS** (0X00): сообщение о запуске запроса GET HTTP-клиента успешно отправлено.</span><span class="sxs-lookup"><span data-stu-id="34cb8-352">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="34cb8-353">**NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-353">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="34cb8-354">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-354">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-355">**NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-355">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-356">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="34cb8-356">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="34cb8-357">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-357">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-358">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-358">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-359">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-359">Allowed From</span></span>

<span data-ttu-id="34cb8-360">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-360">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-361">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-361">Example</span></span>

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

## <a name="nx_web_http_client_get_start_extended"></a><span data-ttu-id="34cb8-362">nx_web_http_client_get_start_extended</span><span class="sxs-lookup"><span data-stu-id="34cb8-362">nx_web_http_client_get_start_extended</span></span>

<span data-ttu-id="34cb8-363">Выполнение HTTP-запроса GET без шифрования.</span><span class="sxs-lookup"><span data-stu-id="34cb8-363">Start a plaintext HTTP GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-364">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-364">Prototype</span></span>

```C
UINT nx_web_http_client_get_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-365">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-365">Description</span></span>

<span data-ttu-id="34cb8-366">Этот метод предназначен для протокола HTTP **без шифрования**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-366">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="34cb8-367">Эта служба пытается выполнить запрос GET к ресурсу, указанному указателем resource, в созданном ранее экземпляре HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-367">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="34cb8-368">Если эта подпрограмма возвращает NX_SUCCESS, приложение может выполнить несколько вызовов службы *nx_web_http_client_response_body_get()* , чтобы получить пакеты данных, соответствующих содержимому запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-368">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="34cb8-369">Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.</span><span class="sxs-lookup"><span data-stu-id="34cb8-369">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="34cb8-370">Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-370">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="34cb8-371">Эта служба заменяет *nx_web_http_client_get_start()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-371">This service replaces *nx_web_http_client_get_start*().</span></span> <span data-ttu-id="34cb8-372">В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="34cb8-372">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-373">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-373">Input Parameters</span></span>

- <span data-ttu-id="34cb8-374">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-374">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-375">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-375">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-376">**server_port**: порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-376">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-377">**resource**: указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-377">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="34cb8-378">**resource_length**: длина строки для запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-378">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="34cb8-379">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-379">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-380">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-380">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-381">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-381">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-382">**host_length**: длина строки узла.</span><span class="sxs-lookup"><span data-stu-id="34cb8-382">**host_length** String length of host.</span></span>
- <span data-ttu-id="34cb8-383">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-383">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-384">**username_length**: длина строки имени пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-384">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="34cb8-385">**password**: указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-385">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-386">**password_length**: длина строки пароля для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-386">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="34cb8-387">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-387">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-388">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-388">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-389">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-389">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-390">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-390">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-391">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-391">Return Values</span></span>

- <span data-ttu-id="34cb8-392">**NX_SUCCESS** (0X00): сообщение о запуске запроса GET HTTP-клиента успешно отправлено.</span><span class="sxs-lookup"><span data-stu-id="34cb8-392">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="34cb8-393">**NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-393">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="34cb8-394">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-394">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-395">**NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-395">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-396">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="34cb8-396">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="34cb8-397">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-397">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-398">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-398">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-399">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-399">Allowed From</span></span>

<span data-ttu-id="34cb8-400">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-401">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-401">Example</span></span>

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

## <a name="nx_web_http_client_get_secure_start"></a><span data-ttu-id="34cb8-402">nx_web_http_client_get_secure_start</span><span class="sxs-lookup"><span data-stu-id="34cb8-402">nx_web_http_client_get_secure_start</span></span>

<span data-ttu-id="34cb8-403">Выполнение зашифрованного HTTPS-запроса GET.</span><span class="sxs-lookup"><span data-stu-id="34cb8-403">Start an encrypted HTTPS GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-404">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-404">Prototype</span></span>

```C
UINT nx_web_http_client_get_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
        NX_SECURE_TLS_SESSION *tls_session),
        ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-405">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-405">Description</span></span>

<span data-ttu-id="34cb8-406">Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-406">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="34cb8-407">Эта служба пытается выполнить запрос GET к ресурсу, указанному указателем resource, в созданном ранее экземпляре HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-407">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="34cb8-408">Если эта подпрограмма возвращает NX_SUCCESS, приложение может выполнить несколько вызовов службы *nx_web_http_client_response_body_get()* , чтобы получить пакеты данных, соответствующих содержимому запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-408">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="34cb8-409">Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.</span><span class="sxs-lookup"><span data-stu-id="34cb8-409">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="34cb8-410">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="34cb8-410">This service is deprecated.</span></span> <span data-ttu-id="34cb8-411">Разработчикам рекомендуется использовать службу *nx_web_http_client_get_secure_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-411">Developers are encouraged to use *nx_web_http_client_get_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-412">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-412">Input Parameters</span></span>

- <span data-ttu-id="34cb8-413">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-413">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-414">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-414">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-415">**server_port**: порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-415">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-416">**resource**: указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-416">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="34cb8-417">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-417">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-418">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-418">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-419">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-419">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-420">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-420">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-421">**password**: указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-421">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-422">**tls_setup**: обратный вызов, используемый для настройки конфигурации TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-422">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="34cb8-423">Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).</span><span class="sxs-lookup"><span data-stu-id="34cb8-423">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="34cb8-424">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-424">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-425">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-425">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-426">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-426">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-427">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-427">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-428">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-428">Return Values</span></span>

- <span data-ttu-id="34cb8-429">**NX_SUCCESS** (0X00): сообщение о запуске запроса GET HTTP-клиента успешно отправлено.</span><span class="sxs-lookup"><span data-stu-id="34cb8-429">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="34cb8-430">**NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-430">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="34cb8-431">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-431">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-432">**NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-432">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-433">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="34cb8-433">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="34cb8-434">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-434">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-435">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-435">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-436">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-436">Allowed From</span></span>

<span data-ttu-id="34cb8-437">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-437">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-438">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-438">Example</span></span>

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

## <a name="nx_web_http_client_get_secure_start_extended"></a><span data-ttu-id="34cb8-439">nx_web_http_client_get_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="34cb8-439">nx_web_http_client_get_secure_start_extended</span></span>

<span data-ttu-id="34cb8-440">Выполнение зашифрованного HTTPS-запроса GET.</span><span class="sxs-lookup"><span data-stu-id="34cb8-440">Start an encrypted HTTPS GET request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-441">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-441">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="34cb8-442">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-442">Description</span></span>

<span data-ttu-id="34cb8-443">Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-443">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="34cb8-444">Эта служба пытается выполнить запрос GET к ресурсу, указанному указателем resource, в созданном ранее экземпляре HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-444">This service attempts to GET the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="34cb8-445">Если эта подпрограмма возвращает NX_SUCCESS, приложение может выполнить несколько вызовов службы *nx_web_http_client_response_body_get()* , чтобы получить пакеты данных, соответствующих содержимому запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-445">If this routine returns NX_SUCCESS, the application can then make multiple calls to *nx_web_http_client_response_body_get()* to retrieve packets of data corresponding to the requested resource content.</span></span>

<span data-ttu-id="34cb8-446">Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.</span><span class="sxs-lookup"><span data-stu-id="34cb8-446">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="34cb8-447">Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-447">The strings of resource, host, username and password must be NULL-terminated, and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="34cb8-448">Эта служба заменяет *nx_web_http_client_secure_start()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-448">This service replaces *nx_web_http_client_secure_start*().</span></span> <span data-ttu-id="34cb8-449">В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="34cb8-449">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-450">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-450">Input Parameters</span></span>

- <span data-ttu-id="34cb8-451">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-451">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-452">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-452">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-453">**server_port**: порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-453">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-454">**resource**: указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-454">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="34cb8-455">**resource_length**: длина строки для запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-455">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="34cb8-456">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-456">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-457">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-457">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-458">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-458">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-459">**host_length**: длина строки узла.</span><span class="sxs-lookup"><span data-stu-id="34cb8-459">**host_length** String length of host.</span></span>
- <span data-ttu-id="34cb8-460">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-460">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-461">**username_length**: длина строки имени пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-461">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="34cb8-462">**password**: указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-462">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-463">**password_length**: длина строки пароля для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-463">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="34cb8-464">**tls_setup**: обратный вызов, используемый для настройки конфигурации TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-464">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="34cb8-465">Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).</span><span class="sxs-lookup"><span data-stu-id="34cb8-465">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="34cb8-466">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-466">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-467">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-467">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-468">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-468">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-469">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-469">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-470">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-470">Return Values</span></span>

- <span data-ttu-id="34cb8-471">**NX_SUCCESS** (0X00): сообщение о запуске запроса GET HTTP-клиента успешно отправлено.</span><span class="sxs-lookup"><span data-stu-id="34cb8-471">**NX_SUCCESS** (0x00) Successfully sent HTTP Client GET start message</span></span>
- <span data-ttu-id="34cb8-472">**NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-472">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="34cb8-473">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-473">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-474">**NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-474">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-475">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="34cb8-475">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="34cb8-476">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-476">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-477">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-477">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-478">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-478">Allowed From</span></span>

<span data-ttu-id="34cb8-479">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-480">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-480">Example</span></span>

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

## <a name="nx_web_http_client_head_start"></a><span data-ttu-id="34cb8-481">nx_web_http_client_head_start</span><span class="sxs-lookup"><span data-stu-id="34cb8-481">nx_web_http_client_head_start</span></span>

<span data-ttu-id="34cb8-482">Выполнение HTTP-запроса HEAD без шифрования.</span><span class="sxs-lookup"><span data-stu-id="34cb8-482">Start a plaintext HTTP HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-483">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-483">Prototype</span></span>

```C
UINT nx_web_http_client_head_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-484">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-484">Description</span></span>

<span data-ttu-id="34cb8-485">Этот метод предназначен для протокола HTTP **без шифрования**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-485">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="34cb8-486">Эта служба пытается получить метаданные HEAD для ресурса, заданного указателем resource, в созданном ранее экземпляре HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-486">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="34cb8-487">Если эта подпрограмма вернет значение NX_SUCCESS, то приложение сможет вызвать метод *nx_web_http_client_response_body_get()* , чтобы получить ответ.</span><span class="sxs-lookup"><span data-stu-id="34cb8-487">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the response.</span></span>

<span data-ttu-id="34cb8-488">Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.</span><span class="sxs-lookup"><span data-stu-id="34cb8-488">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="34cb8-489">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="34cb8-489">This service is deprecated.</span></span> <span data-ttu-id="34cb8-490">Разработчикам рекомендуется использовать службу *nx_web_http_client_head_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-490">Developers are encouraged to use *nx_web_http_client_head_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-491">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-491">Input Parameters</span></span>

- <span data-ttu-id="34cb8-492">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-492">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-493">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-493">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-494">**server_port**: порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-494">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-495">**resource**: указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-495">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="34cb8-496">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-496">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-497">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-497">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-498">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-498">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-499">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-499">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-500">**password**: указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-500">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-501">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-501">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-502">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-502">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-503">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-503">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-504">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-504">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-505">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-505">Return Values</span></span>

- <span data-ttu-id="34cb8-506">**NX_SUCCESS** (0x00): запрос HEAD HTTP-клиента успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-506">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="34cb8-507">**NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-507">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="34cb8-508">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-508">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-509">**NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-509">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-510">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="34cb8-510">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="34cb8-511">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-511">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-512">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-512">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-513">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-513">Allowed From</span></span>

<span data-ttu-id="34cb8-514">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-514">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-515">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-515">Example</span></span>

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

## <a name="nx_web_http_client_head_start_extended"></a><span data-ttu-id="34cb8-516">nx_web_http_client_head_start_extended</span><span class="sxs-lookup"><span data-stu-id="34cb8-516">nx_web_http_client_head_start_extended</span></span>

<span data-ttu-id="34cb8-517">Выполнение HTTP-запроса HEAD без шифрования.</span><span class="sxs-lookup"><span data-stu-id="34cb8-517">Start a plaintext HTTP HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-518">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-518">Prototype</span></span>

```C
UINT nx_web_http_client_head_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-519">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-519">Description</span></span>

<span data-ttu-id="34cb8-520">Этот метод предназначен для протокола HTTP **без шифрования**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-520">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="34cb8-521">Эта служба пытается получить метаданные HEAD для ресурса, заданного указателем resource, в созданном ранее экземпляре HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-521">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="34cb8-522">Если эта подпрограмма вернет значение NX_SUCCESS, то приложение сможет вызвать метод *nx_web_http_client_response_body_get()* , чтобы получить ответ.</span><span class="sxs-lookup"><span data-stu-id="34cb8-522">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the response.</span></span>

<span data-ttu-id="34cb8-523">Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.</span><span class="sxs-lookup"><span data-stu-id="34cb8-523">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="34cb8-524">Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-524">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="34cb8-525">Эта служба заменяет *nx_web_http_client_head_start()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-525">This service replaces *nx_web_http_client_head_start*().</span></span> <span data-ttu-id="34cb8-526">В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="34cb8-526">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-527">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-527">Input Parameters</span></span>

- <span data-ttu-id="34cb8-528">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-528">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-529">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-529">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-530">**server_port**: порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-530">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-531">**resource**: указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-531">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="34cb8-532">**resource_length**: длина строки для запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-532">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="34cb8-533">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-533">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-534">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-534">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-535">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-535">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-536">**host_length**: длина строки узла.</span><span class="sxs-lookup"><span data-stu-id="34cb8-536">**host_length** String length of host.</span></span>
- <span data-ttu-id="34cb8-537">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-537">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-538">**username_length**: длина строки имени пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-538">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="34cb8-539">**password**: указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-539">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-540">**password_length**: длина строки пароля для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-540">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="34cb8-541">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-541">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-542">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-542">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-543">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-543">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-544">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-544">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-545">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-545">Return Values</span></span>

- <span data-ttu-id="34cb8-546">**NX_SUCCESS** (0x00): запрос HEAD HTTP-клиента успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-546">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="34cb8-547">**NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-547">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="34cb8-548">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-548">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-549">**NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-549">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-550">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="34cb8-550">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="34cb8-551">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-551">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-552">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-552">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-553">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-553">Allowed From</span></span>

<span data-ttu-id="34cb8-554">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-555">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-555">Example</span></span>

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

## <a name="nx_web_http_client_head_secure_start"></a><span data-ttu-id="34cb8-556">nx_web_http_client_head_secure_start</span><span class="sxs-lookup"><span data-stu-id="34cb8-556">nx_web_http_client_head_secure_start</span></span>

<span data-ttu-id="34cb8-557">Выполнение зашифрованного HTTPS-запроса HEAD.</span><span class="sxs-lookup"><span data-stu-id="34cb8-557">Start an encrypted HTTPS HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-558">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-558">Prototype</span></span>

```C
UINT nx_web_http_client_head_secure_start(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port, CHAR *resource,
    CHAR *host, CHAR *username, CHAR *password,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls_session),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-559">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-559">Description</span></span>

<span data-ttu-id="34cb8-560">Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-560">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="34cb8-561">Эта служба пытается получить метаданные HEAD для ресурса, заданного указателем resource, в созданном ранее экземпляре HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-561">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="34cb8-562">Если эта подпрограмма возвращает NX_SUCCESS, приложение может вызвать службу *nx_web_http_client_response_body_get()* , чтобы получить ответ сервера, соответствующий содержимому запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-562">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response corresponding to the requested resource content.</span></span>

<span data-ttu-id="34cb8-563">Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.</span><span class="sxs-lookup"><span data-stu-id="34cb8-563">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="34cb8-564">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="34cb8-564">This service is deprecated.</span></span> <span data-ttu-id="34cb8-565">Разработчикам рекомендуется использовать службу *nx_web_http_client_head_secure_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-565">Developers are encouraged to use *nx_web_http_client_head_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-566">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-566">Input Parameters</span></span>

- <span data-ttu-id="34cb8-567">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-567">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-568">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-568">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-569">**server_port**: порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-569">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-570">**resource**: указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-570">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="34cb8-571">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-571">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-572">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-572">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-573">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-573">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-574">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-574">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-575">**password**: указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-575">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-576">**tls_setup**: обратный вызов, используемый для настройки конфигурации TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-576">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="34cb8-577">Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).</span><span class="sxs-lookup"><span data-stu-id="34cb8-577">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="34cb8-578">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-578">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-579">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-579">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-580">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-580">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-581">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-581">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-582">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-582">Return Values</span></span>

- <span data-ttu-id="34cb8-583">**NX_SUCCESS** (0x00): запрос HEAD HTTP-клиента успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-583">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="34cb8-584">**NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-584">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="34cb8-585">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-585">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-586">**NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-586">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-587">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="34cb8-587">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="34cb8-588">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-588">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-589">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-589">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-590">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-590">Allowed From</span></span>

<span data-ttu-id="34cb8-591">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-591">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-592">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-592">Example</span></span>

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

## <a name="nx_web_http_client_head_secure_start_extended"></a><span data-ttu-id="34cb8-593">nx_web_http_client_head_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="34cb8-593">nx_web_http_client_head_secure_start_extended</span></span>

<span data-ttu-id="34cb8-594">Выполнение зашифрованного HTTPS-запроса HEAD.</span><span class="sxs-lookup"><span data-stu-id="34cb8-594">Start an encrypted HTTPS HEAD request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-595">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-595">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="34cb8-596">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-596">Description</span></span>

<span data-ttu-id="34cb8-597">Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-597">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="34cb8-598">Эта служба пытается получить метаданные HEAD для ресурса, заданного указателем resource, в созданном ранее экземпляре HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-598">This service attempts to retrieve the HEAD metadata for the resource specified by "resource" pointer on the previously created HTTP Client instance.</span></span> <span data-ttu-id="34cb8-599">Если эта подпрограмма возвращает NX_SUCCESS, приложение может вызвать службу *nx_web_http_client_response_body_get()* , чтобы получить ответ сервера, соответствующий содержимому запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-599">If this routine returns NX_SUCCESS, the application can then call *nx_web_http_client_response_body_get()* to retrieve the server’s response corresponding to the requested resource content.</span></span>

<span data-ttu-id="34cb8-600">Обратите внимание на то, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы GET.</span><span class="sxs-lookup"><span data-stu-id="34cb8-600">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring GET requests.</span></span>

<span data-ttu-id="34cb8-601">Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-601">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="34cb8-602">Эта служба заменяет *nx_web_http_client_head_secure_start()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-602">This service replaces *nx_web_http_client_head_secure_start*().</span></span> <span data-ttu-id="34cb8-603">В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="34cb8-603">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-604">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-604">Input Parameters</span></span>

- <span data-ttu-id="34cb8-605">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-605">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-606">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-606">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-607">**server_port**: порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-607">**server_port** Port on remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-608">**resource**: указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-608">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="34cb8-609">**resource_length**: длина строки для запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-609">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="34cb8-610">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-610">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-611">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-611">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-612">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-612">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-613">**host_length**: длина строки узла.</span><span class="sxs-lookup"><span data-stu-id="34cb8-613">**host_length** String length of host.</span></span>
- <span data-ttu-id="34cb8-614">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-614">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-615">**username_length**: длина строки имени пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-615">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="34cb8-616">**password**: указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-616">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-617">**password_length**: длина строки пароля для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-617">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="34cb8-618">**tls_setup**: обратный вызов, используемый для настройки конфигурации TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-618">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="34cb8-619">Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).</span><span class="sxs-lookup"><span data-stu-id="34cb8-619">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="34cb8-620">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-620">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-621">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-621">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-622">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-622">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-623">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-623">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-624">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-624">Return Values</span></span>

- <span data-ttu-id="34cb8-625">**NX_SUCCESS** (0x00): запрос HEAD HTTP-клиента успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-625">**NX_SUCCESS** (0x00) Successfully sent HTTP Client HEAD request message</span></span>
- <span data-ttu-id="34cb8-626">**NX_WEB_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-626">**NX_WEB_HTTP_ERROR** (0x30000) Internal HTTP Client error</span></span>
- <span data-ttu-id="34cb8-627">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-627">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-628">**NX_WEB_HTTP_FAILED** (0x30002): ошибка HTTP-клиента при взаимодействии с HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-628">**NX_WEB_HTTP_FAILED** (0x30002) HTTP Client error communicating with the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-629">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="34cb8-629">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or password.</span></span>
- <span data-ttu-id="34cb8-630">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-630">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-631">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-631">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-632">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-632">Allowed From</span></span>

<span data-ttu-id="34cb8-633">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-633">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-634">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-634">Example</span></span>

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

## <a name="nx_web_http_client_request_packet_allocate"></a><span data-ttu-id="34cb8-635">nx_web_http_client_request_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="34cb8-635">nx_web_http_client_request_packet_allocate</span></span>

<span data-ttu-id="34cb8-636">Выделение пакета HTTP(S).</span><span class="sxs-lookup"><span data-stu-id="34cb8-636">Allocate a HTTP(S) packet</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-637">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-637">Prototype</span></span>

```C
UINT nx_web_http_client_request_packet_allocate(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-638">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-638">Description</span></span>

<span data-ttu-id="34cb8-639">Эта служба пытается выделить пакет для HTTP(S)-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-639">This service attempts to allocates a packet for Client HTTP(S).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-640">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-640">Input Parameters</span></span>

- <span data-ttu-id="34cb8-641">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-641">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-642">**packet_ptr**: указатель на выделенный пакет.</span><span class="sxs-lookup"><span data-stu-id="34cb8-642">**packet_ptr** Pointer to allocated packet.</span></span>
- <span data-ttu-id="34cb8-643">**wait_option**: определяет время ожидания в тактах, если в пуле пакетов нет доступных пакетов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-643">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="34cb8-644">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-644">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-645">**NX_NO_WAIT** (0x00000000);</span><span class="sxs-lookup"><span data-stu-id="34cb8-645">**NX_NO_WAIT** (0x00000000)</span></span>
  - <span data-ttu-id="34cb8-646">**NX_WAIT_FOREVER** (0xFFFFFFFF);</span><span class="sxs-lookup"><span data-stu-id="34cb8-646">**NX_WAIT_FOREVER** (0xFFFFFFFF)</span></span>
  - <span data-ttu-id="34cb8-647">**значение времени ожидания в тактах** (0x00000001–0xFFFFFFFE).</span><span class="sxs-lookup"><span data-stu-id="34cb8-647">**timeout in ticks** (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-648">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-648">Return Values</span></span>

- <span data-ttu-id="34cb8-649">**NX_SUCCESS** (0x00): пакет выделен успешно.</span><span class="sxs-lookup"><span data-stu-id="34cb8-649">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>
- <span data-ttu-id="34cb8-650">**NX_NO_PACKET** (0x01): нет доступных пакетов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-650">**NX_NO_PACKET** (0x01) No packet available</span></span>
- <span data-ttu-id="34cb8-651">**NX_WAIT_ABORTED** (0x1A): запрошенная приостановка прервана вызовом *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="34cb8-651">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="34cb8-652">**NX_INVALID_PARAMETERS** (0x4D): размер пакета не поддерживается протоколом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-652">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="34cb8-653">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-653">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-654">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-654">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-655">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-655">Allowed From</span></span>

<span data-ttu-id="34cb8-656">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-656">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-657">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-657">Example</span></span>

```C
/* Allocate a packet for HTTP(S) Client and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_client_request_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_client_post_start"></a><span data-ttu-id="34cb8-658">nx_web_http_client_post_start</span><span class="sxs-lookup"><span data-stu-id="34cb8-658">nx_web_http_client_post_start</span></span>

<span data-ttu-id="34cb8-659">Выполнение HTTP-запроса POST.</span><span class="sxs-lookup"><span data-stu-id="34cb8-659">Start an HTTP POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-660">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-660">Prototype</span></span>

```C
UINT nx_web_http_client_post_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host,
    CHAR *username, CHAR *password,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-661">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-661">Description</span></span>

<span data-ttu-id="34cb8-662">Этот метод предназначен для протокола HTTP **без шифрования**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-662">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="34cb8-663">Эта служба пытается отправить запрос POST с указанным ресурсом на HTTP-сервер по указанному IP-адресу и порту.</span><span class="sxs-lookup"><span data-stu-id="34cb8-663">This service attempts to send a POST request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="34cb8-664">Если эта подпрограмма выполнена успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_web_http_client_put_packet*, чтобы отправить содержимое ресурса на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-664">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="34cb8-665">Обратите внимание, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.</span><span class="sxs-lookup"><span data-stu-id="34cb8-665">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="34cb8-666">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="34cb8-666">This service is deprecated.</span></span> <span data-ttu-id="34cb8-667">Разработчикам рекомендуется использовать службу *nx_web_http_client_post_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-667">Developers are encouraged to use *nx_web_http_client_post_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-668">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-668">Input Parameters</span></span>

- <span data-ttu-id="34cb8-669">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-669">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-670">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-670">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-671">**server_port**: TCP-порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-671">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-672">**resource**: указатель на строку URL-адреса для ресурса, отправляемого на сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-672">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="34cb8-673">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-673">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-674">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-674">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-675">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-675">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-676">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-676">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-677">**password**: указатель на необязательный пароль для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="34cb8-677">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-678">**total_bytes**: общее число отправляемых байтов ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-678">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="34cb8-679">Обратите внимание на то, что совокупная длина всех пакетов, отправленных последующими вызовами *nx_web_http_client_put_packet()* , должна быть равна этому значению.</span><span class="sxs-lookup"><span data-stu-id="34cb8-679">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="34cb8-680">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-680">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-681">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-681">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-682">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-682">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-683">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-683">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-684">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-684">Return Values</span></span>

- <span data-ttu-id="34cb8-685">**NX_SUCCESS** (0x00): запрос POST успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-685">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="34cb8-686">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012): слишком длинное имя пользователя для буфера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-686">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="34cb8-687">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-687">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-688">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-688">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-689">NX_SIZE_ERROR (0x09) — недопустимый общий размер ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-689">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="34cb8-690">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-690">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-691">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-691">Allowed From</span></span>

<span data-ttu-id="34cb8-692">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-693">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-693">Example</span></span>

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

## <a name="nx_web_http_client_post_start_extended"></a><span data-ttu-id="34cb8-694">nx_web_http_client_post_start_extended</span><span class="sxs-lookup"><span data-stu-id="34cb8-694">nx_web_http_client_post_start_extended</span></span>

<span data-ttu-id="34cb8-695">Выполнение HTTP-запроса POST.</span><span class="sxs-lookup"><span data-stu-id="34cb8-695">Start an HTTP POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-696">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-696">Prototype</span></span>

```C
UINT nx_web_http_client_post_start_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-697">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-697">Description</span></span>

<span data-ttu-id="34cb8-698">Этот метод предназначен для протокола HTTP **без шифрования**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-698">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="34cb8-699">Эта служба пытается отправить запрос POST с указанным ресурсом на HTTP-сервер по указанному IP-адресу и порту.</span><span class="sxs-lookup"><span data-stu-id="34cb8-699">This service attempts to send a POST request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="34cb8-700">Если эта подпрограмма выполнена успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_web_http_client_put_packet*, чтобы отправить содержимое ресурса на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-700">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="34cb8-701">Обратите внимание, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.</span><span class="sxs-lookup"><span data-stu-id="34cb8-701">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="34cb8-702">Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-702">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="34cb8-703">Эта служба заменяет *nx_web_http_client_post_start()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-703">This service replaces *nx_web_http_client_post_start* ().</span></span> <span data-ttu-id="34cb8-704">В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="34cb8-704">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-705">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-705">Input Parameters</span></span>

- <span data-ttu-id="34cb8-706">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-706">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-707">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-707">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-708">**server_port**: TCP-порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-708">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-709">**resource**: указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-709">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="34cb8-710">**resource_length**: длина строки для запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-710">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="34cb8-711">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-711">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-712">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-712">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-713">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-713">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-714">**host_length**: длина строки узла.</span><span class="sxs-lookup"><span data-stu-id="34cb8-714">**host_length** String length of host.</span></span>
- <span data-ttu-id="34cb8-715">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-715">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-716">**username_length**: длина строки имени пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-716">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="34cb8-717">**password**: указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-717">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-718">**password_length**: длина строки пароля для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-718">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="34cb8-719">**total_bytes**: общее число отправляемых байтов ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-719">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="34cb8-720">Обратите внимание на то, что совокупная длина всех пакетов, отправленных последующими вызовами *nx_web_http_client_put_packet()* , должна быть равна этому значению.</span><span class="sxs-lookup"><span data-stu-id="34cb8-720">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="34cb8-721">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-721">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-722">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-722">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-723">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-723">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-724">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-724">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-725">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-725">Return Values</span></span>

- <span data-ttu-id="34cb8-726">**NX_SUCCESS** (0x00): запрос POST успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-726">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="34cb8-727">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012): слишком длинное имя пользователя для буфера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-727">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="34cb8-728">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-728">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-729">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-729">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-730">NX_SIZE_ERROR (0x09) — недопустимый общий размер ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-730">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="34cb8-731">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-731">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-732">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-732">Allowed From</span></span>

<span data-ttu-id="34cb8-733">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-734">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-734">Example</span></span>

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

## <a name="nx_web_http_client_post_secure_start"></a><span data-ttu-id="34cb8-735">nx_web_http_client_post_secure_start</span><span class="sxs-lookup"><span data-stu-id="34cb8-735">nx_web_http_client_post_secure_start</span></span>

<span data-ttu-id="34cb8-736">Выполнение зашифрованного HTTPS-запроса POST.</span><span class="sxs-lookup"><span data-stu-id="34cb8-736">Start an encrypted HTTPS POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-737">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-737">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="34cb8-738">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-738">Description</span></span>

<span data-ttu-id="34cb8-739">Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-739">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="34cb8-740">Эта служба пытается отправить запрос POST с указанным ресурсом на HTTPS-сервер по указанному IP-адресу и порту.</span><span class="sxs-lookup"><span data-stu-id="34cb8-740">This service attempts to send a POST request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="34cb8-741">Если эта подпрограмма выполнена успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_web_http_client_put_packet()* , чтобы отправить содержимое ресурса на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-741">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="34cb8-742">Обратите внимание, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.</span><span class="sxs-lookup"><span data-stu-id="34cb8-742">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="34cb8-743">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="34cb8-743">This service is deprecated.</span></span> <span data-ttu-id="34cb8-744">Разработчикам рекомендуется использовать службу *nx_web_http_client_post_secure_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-744">Developers are encouraged to use *nx_web_http_client_post_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-745">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-745">Input Parameters</span></span>

- <span data-ttu-id="34cb8-746">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-746">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-747">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-747">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-748">**server_port**: TCP-порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-748">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-749">**resource**: указатель на строку URL-адреса для ресурса, отправляемого на сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-749">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="34cb8-750">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-750">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-751">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-751">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-752">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-752">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-753">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-753">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-754">**password**: указатель на необязательный пароль для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="34cb8-754">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-755">**total_bytes**: общее число отправляемых байтов ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-755">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="34cb8-756">Обратите внимание на то, что совокупная длина всех пакетов, отправленных последующими вызовами *nx_web_http_client_put_packet()* , должна быть равна этому значению.</span><span class="sxs-lookup"><span data-stu-id="34cb8-756">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="34cb8-757">**tls_setup**: обратный вызов, используемый для настройки конфигурации TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-757">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="34cb8-758">Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).</span><span class="sxs-lookup"><span data-stu-id="34cb8-758">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="34cb8-759">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-759">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-760">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-760">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-761">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-761">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-762">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-762">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-763">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-763">Return Values</span></span>

- <span data-ttu-id="34cb8-764">**NX_SUCCESS** (0x00): запрос POST успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-764">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="34cb8-765">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012): слишком длинное имя пользователя для буфера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-765">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="34cb8-766">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-766">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-767">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-767">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-768">NX_SIZE_ERROR (0x09) — недопустимый общий размер ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-768">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="34cb8-769">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-769">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-770">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-770">Allowed From</span></span>

<span data-ttu-id="34cb8-771">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-771">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-772">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-772">Example</span></span>

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

## <a name="nx_web_http_client_post_secure_start_extended"></a><span data-ttu-id="34cb8-773">nx_web_http_client_delete_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="34cb8-773">nx_web_http_client_post_secure_start_extended</span></span>

<span data-ttu-id="34cb8-774">Выполнение зашифрованного HTTPS-запроса POST.</span><span class="sxs-lookup"><span data-stu-id="34cb8-774">Start an encrypted HTTPS POST request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-775">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-775">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="34cb8-776">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-776">Description</span></span>

<span data-ttu-id="34cb8-777">Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-777">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="34cb8-778">Эта служба пытается отправить запрос POST с указанным ресурсом на HTTPS-сервер по указанному IP-адресу и порту.</span><span class="sxs-lookup"><span data-stu-id="34cb8-778">This service attempts to send a POST request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="34cb8-779">Если эта подпрограмма выполнена успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_web_http_client_put_packet()* , чтобы отправить содержимое ресурса на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-779">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="34cb8-780">Обратите внимание, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.</span><span class="sxs-lookup"><span data-stu-id="34cb8-780">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="34cb8-781">Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-781">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="34cb8-782">Эта служба заменяет *nx_web_http_client_post_secure_start()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-782">This service replaces *nx_web_http_client_post_secure_start* ().</span></span> <span data-ttu-id="34cb8-783">В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="34cb8-783">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-784">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-784">Input Parameters</span></span>

- <span data-ttu-id="34cb8-785">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-785">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-786">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-786">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-787">**server_port**: TCP-порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-787">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-788">**resource**: указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-788">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="34cb8-789">**resource_length**: длина строки для запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-789">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="34cb8-790">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-790">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-791">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-791">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-792">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-792">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-793">**host_length**: длина строки узла.</span><span class="sxs-lookup"><span data-stu-id="34cb8-793">**host_length** String length of host.</span></span>
- <span data-ttu-id="34cb8-794">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-794">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-795">**username_length**: длина строки имени пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-795">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="34cb8-796">**password**: указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-796">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-797">**password_length**: длина строки пароля для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-797">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="34cb8-798">**total_bytes**: общее число отправляемых байтов ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-798">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="34cb8-799">Обратите внимание на то, что совокупная длина всех пакетов, отправленных последующими вызовами *nx_web_http_client_put_packet()* , должна быть равна этому значению.</span><span class="sxs-lookup"><span data-stu-id="34cb8-799">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="34cb8-800">**tls_setup**: обратный вызов, используемый для настройки конфигурации TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-800">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="34cb8-801">Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).</span><span class="sxs-lookup"><span data-stu-id="34cb8-801">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="34cb8-802">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-802">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-803">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-803">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-804">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-804">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-805">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-805">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-806">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-806">Return Values</span></span>

- <span data-ttu-id="34cb8-807">**NX_SUCCESS** (0x00): запрос POST успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-807">**NX_SUCCESS** (0x00) Successfully sent POST request</span></span>
- <span data-ttu-id="34cb8-808">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012): слишком длинное имя пользователя для буфера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-808">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="34cb8-809">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-809">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-810">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-810">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-811">NX_SIZE_ERROR (0x09) — недопустимый общий размер ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-811">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="34cb8-812">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-812">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-813">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-813">Allowed From</span></span>

<span data-ttu-id="34cb8-814">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-814">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-815">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-815">Example</span></span>

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

## <a name="nx_web_http_client_put_start"></a><span data-ttu-id="34cb8-816">nx_web_http_client_put_start</span><span class="sxs-lookup"><span data-stu-id="34cb8-816">nx_web_http_client_put_start</span></span>

<span data-ttu-id="34cb8-817">Выполнение HTTP-запроса PUT.</span><span class="sxs-lookup"><span data-stu-id="34cb8-817">Start an HTTP PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-818">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-818">Prototype</span></span>

```C
UINT nx_web_http_client_put_start(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS ip_address, UINT server_port,
    CHAR *resource, CHAR *host, CHAR *username,
    CHAR *password, ULONG total_bytes,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-819">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-819">Description</span></span>

<span data-ttu-id="34cb8-820">Этот метод предназначен для протокола HTTP **без шифрования**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-820">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="34cb8-821">Эта служба пытается отправить запрос PUT с указанным ресурсом на HTTP-сервер по указанному IP-адресу и порту.</span><span class="sxs-lookup"><span data-stu-id="34cb8-821">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="34cb8-822">Если эта подпрограмма выполнена успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_web_http_client_put_packet()* , чтобы отправить содержимое ресурса на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-822">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="34cb8-823">Обратите внимание, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.</span><span class="sxs-lookup"><span data-stu-id="34cb8-823">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="34cb8-824">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="34cb8-824">This service is deprecated.</span></span> <span data-ttu-id="34cb8-825">Разработчикам рекомендуется использовать службу *nx_web_http_client_put_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-825">Developers are encouraged to use *nx_web_http_client_put_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-826">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-826">Input Parameters</span></span>

- <span data-ttu-id="34cb8-827">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-827">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-828">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-828">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-829">**server_port**: TCP-порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-829">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-830">**resource**: указатель на строку URL-адреса для ресурса, отправляемого на сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-830">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="34cb8-831">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-831">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-832">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-832">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-833">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-833">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-834">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-834">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-835">**password**: указатель на необязательный пароль для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="34cb8-835">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-836">**total_bytes**: общее число отправляемых байтов ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-836">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="34cb8-837">Обратите внимание на то, что совокупная длина всех пакетов, отправленных последующими вызовами *nx_web_http_client_put_packet()* , должна быть равна этому значению.</span><span class="sxs-lookup"><span data-stu-id="34cb8-837">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="34cb8-838">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-838">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-839">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-839">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-840">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-840">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-841">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-841">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-842">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-842">Return Values</span></span>

- <span data-ttu-id="34cb8-843">**NX_SUCCESS** (0x00): запрос PUT успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-843">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="34cb8-844">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012): слишком длинное имя пользователя для буфера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-844">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="34cb8-845">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-845">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-846">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-846">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-847">NX_SIZE_ERROR (0x09) — недопустимый общий размер ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-847">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="34cb8-848">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-848">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-849">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-849">Allowed From</span></span>

<span data-ttu-id="34cb8-850">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-850">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-851">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-851">Example</span></span>

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

## <a name="nx_web_http_client_put_start_extended"></a><span data-ttu-id="34cb8-852">nx_web_http_client_put_start_extended</span><span class="sxs-lookup"><span data-stu-id="34cb8-852">nx_web_http_client_put_start_extended</span></span>

<span data-ttu-id="34cb8-853">Выполнение HTTP-запроса PUT.</span><span class="sxs-lookup"><span data-stu-id="34cb8-853">Start an HTTP PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-854">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-854">Prototype</span></span>

```C
UINT nx_web_http_client_put_start(
    NX_WEB_HTTP_CLIENT *client_ptr, NXD_ADDRESS ip_address,
    UINT server_port, CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length, CHAR *username,
    UINT username_length, CHAR *password, UINT password_length,
    ULONG total_bytes, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-855">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-855">Description</span></span>

<span data-ttu-id="34cb8-856">Этот метод предназначен для протокола HTTP **без шифрования**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-856">This method is for **plaintext** HTTP.</span></span>

<span data-ttu-id="34cb8-857">Эта служба пытается отправить запрос PUT с указанным ресурсом на HTTP-сервер по указанному IP-адресу и порту.</span><span class="sxs-lookup"><span data-stu-id="34cb8-857">This service attempts to send a PUT request with the specified resource to the HTTP Server at the supplied IP address and port.</span></span> <span data-ttu-id="34cb8-858">Если эта подпрограмма выполнена успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_web_http_client_put_packet()* , чтобы отправить содержимое ресурса на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-858">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="34cb8-859">Обратите внимание, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.</span><span class="sxs-lookup"><span data-stu-id="34cb8-859">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="34cb8-860">Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-860">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="34cb8-861">Эта служба заменяет *nx_web_http_client_put_start()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-861">This service replaces *nx_web_http_client_put_start* ().</span></span> <span data-ttu-id="34cb8-862">В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="34cb8-862">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-863">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-863">Input Parameters</span></span>

- <span data-ttu-id="34cb8-864">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-864">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-865">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-865">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-866">**server_port**: TCP-порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-866">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-867">**resource**: указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-867">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="34cb8-868">**resource_length**: длина строки для запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-868">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="34cb8-869">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-869">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-870">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-870">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-871">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-871">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-872">**host_length**: длина строки узла.</span><span class="sxs-lookup"><span data-stu-id="34cb8-872">**host_length** String length of host.</span></span>
- <span data-ttu-id="34cb8-873">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-873">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-874">**username_length**: длина строки имени пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-874">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="34cb8-875">**password**: указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-875">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-876">**password_length**: длина строки пароля для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-876">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="34cb8-877">**total_bytes**: общее число отправляемых байтов ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-877">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="34cb8-878">Обратите внимание на то, что совокупная длина всех пакетов, отправленных последующими вызовами *nx_web_http_client_put_packet()* , должна быть равна этому значению.</span><span class="sxs-lookup"><span data-stu-id="34cb8-878">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="34cb8-879">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-879">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-880">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-880">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-881">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-881">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-882">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-882">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-883">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-883">Return Values</span></span>

- <span data-ttu-id="34cb8-884">**NX_SUCCESS** (0x00): запрос PUT успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-884">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="34cb8-885">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012): слишком длинное имя пользователя для буфера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-885">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="34cb8-886">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-886">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-887">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-887">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-888">NX_SIZE_ERROR (0x09) — недопустимый общий размер ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-888">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="34cb8-889">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-889">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-890">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-890">Allowed From</span></span>

<span data-ttu-id="34cb8-891">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-891">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-892">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-892">Example</span></span>

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

## <a name="nx_web_http_client_put_secure_start"></a><span data-ttu-id="34cb8-893">nx_web_http_client_put_secure_start</span><span class="sxs-lookup"><span data-stu-id="34cb8-893">nx_web_http_client_put_secure_start</span></span>

<span data-ttu-id="34cb8-894">Выполнение зашифрованного HTTPS-запроса PUT.</span><span class="sxs-lookup"><span data-stu-id="34cb8-894">Start an encrypted HTTPS PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-895">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-895">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="34cb8-896">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-896">Description</span></span>

<span data-ttu-id="34cb8-897">Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-897">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="34cb8-898">Эта служба пытается отправить запрос PUT с указанным ресурсом на HTTPS-сервер по указанному IP-адресу и порту.</span><span class="sxs-lookup"><span data-stu-id="34cb8-898">This service attempts to send a PUT request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="34cb8-899">Если эта подпрограмма выполнена успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_web_http_client_put_packet()* , чтобы отправить содержимое ресурса на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-899">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="34cb8-900">Обратите внимание, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.</span><span class="sxs-lookup"><span data-stu-id="34cb8-900">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="34cb8-901">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="34cb8-901">This service is deprecated.</span></span> <span data-ttu-id="34cb8-902">Разработчикам рекомендуется использовать службу *nx_web_http_client_put_secure_start_extended()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-902">Developers are encouraged to use *nx_web_http_client_put_secure_start_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-903">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-903">Input Parameters</span></span>

- <span data-ttu-id="34cb8-904">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-904">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-905">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-905">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-906">**server_port**: TCP-порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-906">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-907">**resource**: указатель на строку URL-адреса для ресурса, отправляемого на сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-907">**resource** Pointer to URL string for resource to send to Server.</span></span>
- <span data-ttu-id="34cb8-908">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-908">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-909">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-909">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-910">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-910">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-911">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-911">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-912">**password**: указатель на необязательный пароль для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="34cb8-912">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-913">**total_bytes**: общее число отправляемых байтов ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-913">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="34cb8-914">Обратите внимание на то, что совокупная длина всех пакетов, отправленных последующими вызовами *nx_web_http_client_put_packet()* , должна быть равна этому значению.</span><span class="sxs-lookup"><span data-stu-id="34cb8-914">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="34cb8-915">**tls_setup**: обратный вызов, используемый для настройки конфигурации TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-915">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="34cb8-916">Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).</span><span class="sxs-lookup"><span data-stu-id="34cb8-916">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="34cb8-917">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-917">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-918">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-918">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-919">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-919">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-920">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-920">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-921">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-921">Return Values</span></span>

- <span data-ttu-id="34cb8-922">**NX_SUCCESS** (0x00): запрос PUT успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-922">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="34cb8-923">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012): слишком длинное имя пользователя для буфера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-923">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="34cb8-924">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-924">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-925">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-925">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-926">NX_SIZE_ERROR (0x09) — недопустимый общий размер ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-926">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="34cb8-927">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-927">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-928">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-928">Allowed From</span></span>

<span data-ttu-id="34cb8-929">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-929">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-930">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-930">Example</span></span>

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

## <a name="nx_web_http_client_put_secure_start_extended"></a><span data-ttu-id="34cb8-931">nx_web_http_client_put_secure_start_extended</span><span class="sxs-lookup"><span data-stu-id="34cb8-931">nx_web_http_client_put_secure_start_extended</span></span>

<span data-ttu-id="34cb8-932">Выполнение зашифрованного HTTPS-запроса PUT.</span><span class="sxs-lookup"><span data-stu-id="34cb8-932">Start an encrypted HTTPS PUT request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-933">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-933">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="34cb8-934">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-934">Description</span></span>

<span data-ttu-id="34cb8-935">Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-935">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="34cb8-936">Эта служба пытается отправить запрос PUT с указанным ресурсом на HTTPS-сервер по указанному IP-адресу и порту.</span><span class="sxs-lookup"><span data-stu-id="34cb8-936">This service attempts to send a PUT request with the specified resource to the HTTPS Server at the supplied IP address and port.</span></span> <span data-ttu-id="34cb8-937">Если эта подпрограмма выполнена успешно, код приложения должен выполнить последовательные вызовы подпрограммы *nx_web_http_client_put_packet()* , чтобы отправить содержимое ресурса на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-937">If this routine is successful, the application code should make successive calls to the *nx_web_http_client_put_packet()* routine to send the resource contents to the HTTP Server.</span></span>

<span data-ttu-id="34cb8-938">Обратите внимание, что строка ресурса может ссылаться на локальный файл, например "/index.htm", или на другой URL-адрес, например `http://abc.website.com/index.htm`, если HTTP-сервер указывает, что он поддерживает ссылки на запросы PUT.</span><span class="sxs-lookup"><span data-stu-id="34cb8-938">Note that the resource string can refer to a local file e.g. "/index.htm" or it can refer to another URL e.g. `http://abc.website.com/index.htm` if the HTTP Server indicates it supports referring PUT requests.</span></span>

<span data-ttu-id="34cb8-939">Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-939">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="34cb8-940">Эта служба заменяет *nx_web_http_client_put_secure_start()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-940">This service replaces *nx_web_http_client_put_secure_start*().</span></span> <span data-ttu-id="34cb8-941">В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="34cb8-941">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-942">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-942">Input Parameters</span></span>

- <span data-ttu-id="34cb8-943">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-943">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-944">**ip_address**: IP-адрес HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-944">**ip_address** IP address of the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-945">**server_port**: TCP-порт на удаленном HTTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-945">**server_port** TCP port on the remote HTTP Server.</span></span>
- <span data-ttu-id="34cb8-946">**resource**: указатель на строку URL-адреса запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-946">**resource** Pointer to URL string for requested resource.</span></span>
- <span data-ttu-id="34cb8-947">**resource_length**: длина строки для запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-947">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="34cb8-948">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-948">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-949">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-949">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-950">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-950">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-951">**host_length**: длина строки узла.</span><span class="sxs-lookup"><span data-stu-id="34cb8-951">**host_length** String length of host.</span></span>
- <span data-ttu-id="34cb8-952">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-952">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-953">**username_length**: длина строки имени пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-953">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="34cb8-954">**password**: указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-954">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-955">**password_length**: длина строки пароля для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-955">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="34cb8-956">**total_bytes**: общее число отправляемых байтов ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-956">**total_bytes** Total bytes of resource being sent.</span></span> <span data-ttu-id="34cb8-957">Обратите внимание на то, что совокупная длина всех пакетов, отправленных последующими вызовами *nx_web_http_client_put_packet()* , должна быть равна этому значению.</span><span class="sxs-lookup"><span data-stu-id="34cb8-957">Note that the combined length of all packets sent via subsequent calls to *nx_web_http_client_put_packet()* must equal this value.</span></span>
- <span data-ttu-id="34cb8-958">**tls_setup**: обратный вызов, используемый для настройки конфигурации TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-958">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="34cb8-959">Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).</span><span class="sxs-lookup"><span data-stu-id="34cb8-959">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="34cb8-960">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-960">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-961">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-961">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-962">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-962">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-963">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-963">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-964">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-964">Return Values</span></span>

- <span data-ttu-id="34cb8-965">**NX_SUCCESS** (0x00): запрос PUT успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-965">**NX_SUCCESS** (0x00) Successfully sent PUT request</span></span>
- <span data-ttu-id="34cb8-966">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012): слишком длинное имя пользователя для буфера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-966">**NX_WEB_HTTP_USERNAME_TOO_LONG** (0x30012) Username too large for buffer</span></span>
- <span data-ttu-id="34cb8-967">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-967">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-968">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-968">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-969">NX_SIZE_ERROR (0x09) — недопустимый общий размер ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-969">NX_SIZE_ERROR (0x09) Invalid total size of resource</span></span>
- <span data-ttu-id="34cb8-970">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-970">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-971">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-971">Allowed From</span></span>

<span data-ttu-id="34cb8-972">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-972">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-973">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-973">Example</span></span>

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

## <a name="nx_web_http_client_put_packet"></a><span data-ttu-id="34cb8-974">nx_web_http_client_put_packet</span><span class="sxs-lookup"><span data-stu-id="34cb8-974">nx_web_http_client_put_packet</span></span>

<span data-ttu-id="34cb8-975">Отправка следующего пакета данных ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-975">Send next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-976">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-976">Prototype</span></span>

```C
UINT nx_web_http_client_put_packet(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-977">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-977">Description</span></span>

<span data-ttu-id="34cb8-978">Эта служба пытается отправить следующий пакет содержимого ресурса на HTTP-сервер для операций PUT и POST.</span><span class="sxs-lookup"><span data-stu-id="34cb8-978">This service attempts to send the next packet of resource content to the HTTP Server for both PUT and POST operations.</span></span> <span data-ttu-id="34cb8-979">Обратите внимание на то, что эту подпрограмму следует вызывать повторно до тех пор, пока совокупная длина отправленных пакетов не будет равна значению total_bytes, указанному в предшествовавшем вызове службы *nx_web_http_client_put_start()* или *nx_web_http_client_post_start()* (или их соответствующей безопасной версии).</span><span class="sxs-lookup"><span data-stu-id="34cb8-979">Note that this routine should be called repetitively until the combined length of the packets sent equals the "total_bytes" specified in the previous *nx_web_http_client_put_start()* or *nx_web_http_client_post_start()* call (or their corresponding secure versions).</span></span>

<span data-ttu-id="34cb8-980">Эта служба также проверяет ответ сервера на случай, если возникла проблема при установлении подключения HTTP (или HTTPS).</span><span class="sxs-lookup"><span data-stu-id="34cb8-980">This service also checks for a response from the server in case there was a problem establishing the HTTP (or HTTPS) connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-981">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-981">Input Parameters</span></span>

- <span data-ttu-id="34cb8-982">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-982">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-983">**packet_ptr**: указатель на следующее содержимое ресурса, отправляемого на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-983">**packet_ptr** Pointer to next content of the resource to being sent to the HTTP Server.</span></span>
- <span data-ttu-id="34cb8-984">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-984">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-985">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-985">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-986">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-986">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-987">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-987">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-988">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-988">Return Values</span></span>

- <span data-ttu-id="34cb8-989">**NX_SUCCESS** (0x00): пакет HTTP-клиента успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-989">**NX_SUCCESS** (0x00) Successfully sent HTTP Client packet.</span></span>
- <span data-ttu-id="34cb8-990">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не готов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-990">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not ready</span></span>
- <span data-ttu-id="34cb8-991">**NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E): получен код ошибки сервера\*\*.</span><span class="sxs-lookup"><span data-stu-id="34cb8-991">**NX_WEB_HTTP_REQUEST_UNSUCCESSFUL_CODE** (0x3000E) Received Server error code\*\*</span></span>
- <span data-ttu-id="34cb8-992">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D): недопустимая длина пакета.</span><span class="sxs-lookup"><span data-stu-id="34cb8-992">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Invalid packet length</span></span>
- <span data-ttu-id="34cb8-993">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B): недопустимое имя и (или) пароль.</span><span class="sxs-lookup"><span data-stu-id="34cb8-993">**NX_WEB_HTTP_AUTHENTICATION_ERROR** (0x3000B) Invalid name and/or Password</span></span>
- <span data-ttu-id="34cb8-994">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F): сервер отвечает до завершения запроса PUT.</span><span class="sxs-lookup"><span data-stu-id="34cb8-994">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Server responds before PUT is complete</span></span>
- <span data-ttu-id="34cb8-995">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-995">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-996">NX_INVALID_PACKET (0x12) — слишком маленький пакет для заголовка TCP</span><span class="sxs-lookup"><span data-stu-id="34cb8-996">NX_INVALID_PACKET (0x12) Packet too small for TCP header</span></span>
- <span data-ttu-id="34cb8-997">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-997">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-998">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-998">Allowed From</span></span>

<span data-ttu-id="34cb8-999">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-999">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1000">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1000">Example</span></span>

```C
/* Send a 20-byte packet representing the content of the resource
    "/TEST.HTM" to the HTTP Server. */

status = nx_web_http_client_put_packet(&client_ptr, packet_ptr, NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the 20-byte resource contents of TEST.HTM has
    successfully been sent. */
```

## <a name="nx_web_http_client_request_chunked_set"></a><span data-ttu-id="34cb8-1001">nx_web_http_client_request_chunked_set</span><span class="sxs-lookup"><span data-stu-id="34cb8-1001">nx_web_http_client_request_chunked_set</span></span>

<span data-ttu-id="34cb8-1002">Настройка поблочной передачи для HTTP(S)-запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1002">Set chunked transfer for HTTP(S) request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1003">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1003">Prototype</span></span>

```C
UINT nx_web_http_client_request_chunked_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="34cb8-1004">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1004">Description</span></span>

<span data-ttu-id="34cb8-1005">Эта служба использует поблочное кодирование для передачи пользовательских HTTP(S)-запросов на сервер, указанный в вызове службы *nx_web_http_client_connect()* или *nx_web_http_client_secure_connect()* , который ранее установил подключение через сокет к удаленному узлу.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1005">This service uses chunked transfer coding to send a custom HTTP(S) request to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect()* call which has previously established the socket connection to the remote host.</span></span>

> [!NOTE]
> <span data-ttu-id="34cb8-1006">Если приложение использует поблочное кодирование для передачи пакета данных запроса, то оно должно вызвать эту службу после вызова службы *nx_web_http_client_request_packet_allocate()* и перед вызовом службы *nx_web_http_client_reqeust_packet_send()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1006">If the application uses chunked transfer coding to send a request data packet, it must call this service after calling *nx_web_http_client_request_packet_allocate*(), and before call *nx_web_http_client_reqeust_packet_send* ().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1007">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1007">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1008">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1008">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-1009">**chunk_size**: размер блока данных в октетах.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1009">**chunk_size** Size of the chunk-data in octets.</span></span>
- <span data-ttu-id="34cb8-1010">**packet_ptr**: указатель на пакет данных HTTP(S)-запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1010">**packet_ptr** HTTP(S) request data packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1011">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1011">Return Values</span></span>

- <span data-ttu-id="34cb8-1012">**NX_SUCCESS** (0X00): режим поблочной передачи успешно задан.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1012">**NX_SUCCESS** (0x00) Successfully set chunked.</span></span>
- <span data-ttu-id="34cb8-1013">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1013">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1014">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1014">Allowed From</span></span>

<span data-ttu-id="34cb8-1015">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1015">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1016">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1016">Example</span></span>

```C
/* Connect to a remote HTTPS server. */

nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
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

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
nx_web_http_client_request_packet_send(&my_client, my_packet,
    0, NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_header_add"></a><span data-ttu-id="34cb8-1017">nx_web_http_client_request_header_add</span><span class="sxs-lookup"><span data-stu-id="34cb8-1017">nx_web_http_client_request_header_add</span></span>

<span data-ttu-id="34cb8-1018">Добавление пользовательского заголовка в пользовательский HTTP-запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1018">Add a custom header to a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1019">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1019">Prototype</span></span>

```C
UINT nx_web_http_client_request_header_add(
    NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT name_length,
    CHAR *field_value, UINT value_length,
    UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-1020">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1020">Description</span></span>

<span data-ttu-id="34cb8-1021">Эта служба добавляет пользовательский заголовок (в виде имени поля и значения) в пользовательский HTTP-запрос, созданный с помощью службы *nx_web_http_client_request_initialize()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1021">This service adds a custom header (in the form of a field name and value) to a custom HTTP request created with n *x_web_http_client_request_initialize()*.</span></span>

<span data-ttu-id="34cb8-1022">С помощью этой службы приложение может добавить в запрос любое количество пользовательских заголовков.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1022">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="34cb8-1023">**Это позволяет создавать пользовательские HTTP-запросы, предназначенные для конкретных приложений.**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1023">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="34cb8-1024">Методы nx_web_http_client_\*_start предоставляются для удобства.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1024">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="34cb8-1025">Во всех этих функциях данная подпрограмма используется (как и служба *nx_web_http_client_request_initialize())* для создания и отправки HTTP-запросов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1025">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1026">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1026">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1027">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1027">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-1028">**field_name**: строка имени поля (например, "Content-Type").</span><span class="sxs-lookup"><span data-stu-id="34cb8-1028">**field_name** Field name string (e.g. "Content-Type").</span></span>
- <span data-ttu-id="34cb8-1029">**name_length**: длина строки имени поля в байтах.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1029">**name_length** Length of field name string in bytes.</span></span>
- <span data-ttu-id="34cb8-1030">**field_value**: строка значения поля (например, "application/octet-stream").</span><span class="sxs-lookup"><span data-stu-id="34cb8-1030">**field_value** Field value string (e.g. "application/octet-stream").</span></span>
- <span data-ttu-id="34cb8-1031">**value_length**: длина строки значения в байтах.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1031">**value_length** Length of value string in bytes.</span></span>
- <span data-ttu-id="34cb8-1032">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1032">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-1033">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-1033">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-1034">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1034">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-1035">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1035">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1036">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1036">Return Values</span></span>

- <span data-ttu-id="34cb8-1037">**NX_SUCCESS** (0X00): заголовок успешно добавлен в запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1037">**NX_SUCCESS** (0x00) Successful addition of header to request.</span></span>
- <span data-ttu-id="34cb8-1038">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1038">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1039">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1039">Allowed From</span></span>

<span data-ttu-id="34cb8-1040">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1040">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1041">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1041">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */

nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
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
    until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize"></a><span data-ttu-id="34cb8-1042">nx_web_http_client_request_initialize</span><span class="sxs-lookup"><span data-stu-id="34cb8-1042">nx_web_http_client_request_initialize</span></span>

<span data-ttu-id="34cb8-1043">Инициализация пользовательского HTTP-запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1043">Initialize a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1044">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1044">Prototype</span></span>

```C
UINT nx_web_http_client_request_initialize(
    NX_WEB_HTTP_CLIENT *client_ptr,
    UINT method, CHAR *resource, CHAR *host,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, CHAR *password, UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-1045">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1045">Description</span></span>

<span data-ttu-id="34cb8-1046">Эта служба создает пользовательский HTTP-запрос и связывает его с экземпляром HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1046">This service creates a custom HTTP request and associates it with the HTTP Client instance.</span></span> <span data-ttu-id="34cb8-1047">В отличие от более простой службы *nx_web_http_client_get_start()* (наряду с методами PUT, POST и связанными защищенными версиями этих API), пользовательский запрос не отправляется, пока не вызвана служба *nx_web_http_client_request_send()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1047">Unlike the simpler *nx_web_http_client_get_start()* (along with the methods for PUT, POST, and the associated secure versions of those API), the custom request is not sent until the *nx_web_http_client_request_send()* service is called.</span></span>

<span data-ttu-id="34cb8-1048">Использование этой службы позволяет приложению добавить любое количество пользовательских заголовков в запрос с помощью службы ***nx_web_http_client_request_header_add()***.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1048">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="34cb8-1049">Это позволяет создавать пользовательские HTTP-запросы, предназначенные для конкретных приложений.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1049">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="34cb8-1050">Методы nx_web_http_client_\*_start предоставляются для удобства.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1050">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="34cb8-1051">Во всех этих функциях данная подпрограмма используется (как и служба *nx_web_http_client_request_send())* для создания и отправки HTTP-запросов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1051">These functions all use this routine internally (along with *nx_web_http_client_request_send())* to create and send HTTP requests.</span></span>

<span data-ttu-id="34cb8-1052">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1052">This service is deprecated.</span></span> <span data-ttu-id="34cb8-1053">Разработчикам рекомендуется использовать службу *nx_web_http_client_request_initialize_extended()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1053">Developers are encouraged to use *nx_web_http_client_request_initialize_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1054">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1054">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1055">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1055">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-1056">**method**: используемый метод HTTP-запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1056">**method** The HTTP request method to use.</span></span> <span data-ttu-id="34cb8-1057">Параметры определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-1057">The options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-1058">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1058">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span></span>
  - <span data-ttu-id="34cb8-1059">**NX_WEB_HTTP_METHOD_GET (0x1)**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1059">**NX_WEB_HTTP_METHOD_GET (0x1)**</span></span>
  - <span data-ttu-id="34cb8-1060">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1060">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span></span>
  - <span data-ttu-id="34cb8-1061">**NX_WEB_HTTP_METHOD_POST (0x3)**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1061">**NX_WEB_HTTP_METHOD_POST (0x3)**</span></span>
  - <span data-ttu-id="34cb8-1062">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1062">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span></span>
  - <span data-ttu-id="34cb8-1063">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1063">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span></span>
- <span data-ttu-id="34cb8-1064">**resource**: имя передаваемого ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1064">**resource** Name of resource being transferred.</span></span>
- <span data-ttu-id="34cb8-1065">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1065">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-1066">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1066">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-1067">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1067">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-1068">**input_size**: размер входных данных для операций PUT и POST.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1068">**input_size** Size of input data for PUT and POST.</span></span> <span data-ttu-id="34cb8-1069">Для других операций следует передавать 0.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1069">Pass 0 for other operations.</span></span>
- <span data-ttu-id="34cb8-1070">**transfer_encoding_trunked**: зарезервированный параметр для будущей поддержки транкинговой передачи.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1070">**transfer_encoding_trunked** Reserved parameter for future trunked transfer support.</span></span>
- <span data-ttu-id="34cb8-1071">**username**: имя пользователя для защищенных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1071">**username** Username for protected resources.</span></span>
- <span data-ttu-id="34cb8-1072">**password**: пароль для защищенных ресурсов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1072">**password** Password for protected resources.</span></span>
- <span data-ttu-id="34cb8-1073">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1073">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-1074">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-1074">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-1075">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1075">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-1076">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1076">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1077">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1077">Return Values</span></span>

- <span data-ttu-id="34cb8-1078">**TX_SUCCESS** (0x00): запрос успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1078">**NX_SUCCESS** (0x00) Successful initialization of request.</span></span>
- <span data-ttu-id="34cb8-1079">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1079">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-1080">NX_WEB_HTTP_METHOD_ERROR (0x30014): отсутствует необходимая информация (например, input_size для операции PUT или POST).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1080">NX_WEB_HTTP_METHOD_ERROR (0x30014) Some required information was missing (e.g. input_size for PUT or POST).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1081">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1081">Allowed From</span></span>

<span data-ttu-id="34cb8-1082">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1082">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1083">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1083">Example</span></span>

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
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_initialize_extended"></a><span data-ttu-id="34cb8-1084">nx_web_http_client_request_initialize_extended</span><span class="sxs-lookup"><span data-stu-id="34cb8-1084">nx_web_http_client_request_initialize_extended</span></span>

<span data-ttu-id="34cb8-1085">Инициализация пользовательского HTTP-запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1085">Initialize a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1086">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1086">Prototype</span></span>

```C
UINT nx_web_http_client_request_initialize_extended(
    NX_WEB_HTTP_CLIENT *client_ptr, UINT method,
    CHAR *resource, UINT resource_length,
    CHAR *host, UINT host_length,
    UINT input_size, UINT transfer_encoding_trunked,
    CHAR *username, UINT username_length,
    CHAR *password, UINT password_length, UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-1087">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1087">Description</span></span>

<span data-ttu-id="34cb8-1088">Эта служба создает пользовательский HTTP-запрос и связывает его с экземпляром HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1088">This service creates a custom HTTP request and associates it with the HTTP Client instance.</span></span> <span data-ttu-id="34cb8-1089">В отличие от более простой службы *nx_web_http_client_get_start()* (наряду с методами PUT, POST и связанными защищенными версиями этих API), пользовательский запрос не отправляется, пока не вызвана служба *nx_web_http_client_request_send()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1089">Unlike the simpler *nx_web_http_client_get_start()* (along with the methods for PUT, POST, and the associated secure versions of those API), the custom request is not sent until the *nx_web_http_client_request_send()* service is called.</span></span>

<span data-ttu-id="34cb8-1090">Использование этой службы позволяет приложению добавить любое количество пользовательских заголовков в запрос с помощью службы ***nx_web_http_client_request_header_add()***.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1090">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="34cb8-1091">Это позволяет создавать пользовательские HTTP-запросы, предназначенные для конкретных приложений.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1091">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="34cb8-1092">Методы nx_web_http_client_\*_start предоставляются для удобства.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1092">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="34cb8-1093">Во всех этих функциях данная подпрограмма используется (как и служба *nx_web_http_client_request_send())* для создания и отправки HTTP-запросов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1093">These functions all use this routine internally (along with *nx_web_http_client_request_send())* to create and send HTTP requests.</span></span>

<span data-ttu-id="34cb8-1094">Строки resource, host, username и password должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1094">The strings of resource, host, username and password must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="34cb8-1095">Эта служба заменяет *nx_web_http_client_request_initialize()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1095">This service replaces *nx_web_http_client_request_initialize*().</span></span> <span data-ttu-id="34cb8-1096">В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1096">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1097">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1097">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1098">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1098">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-1099">**method**: используемый метод HTTP-запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1099">**method** The HTTP request method to use.</span></span> <span data-ttu-id="34cb8-1100">Параметры определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-1100">The options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-1101">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1101">**NX_WEB_HTTP_METHOD_NONE (0x0)**</span></span>
  - <span data-ttu-id="34cb8-1102">**NX_WEB_HTTP_METHOD_GET (0x1)**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1102">**NX_WEB_HTTP_METHOD_GET (0x1)**</span></span>
  - <span data-ttu-id="34cb8-1103">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1103">**NX_WEB_HTTP_METHOD_PUT (0x2)**</span></span>
  - <span data-ttu-id="34cb8-1104">**NX_WEB_HTTP_METHOD_POST (0x3)**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1104">**NX_WEB_HTTP_METHOD_POST (0x3)**</span></span>
  - <span data-ttu-id="34cb8-1105">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1105">**NX_WEB_HTTP_METHOD_DELETE (0x4)**</span></span>
  - <span data-ttu-id="34cb8-1106">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1106">**NX_WEB_HTTP_METHOD_HEAD (0x5)**</span></span>
- <span data-ttu-id="34cb8-1107">**resource**: имя передаваемого ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1107">**resource** Name of resource being transferred.</span></span>
- <span data-ttu-id="34cb8-1108">**resource_length**: длина строки для запрошенного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1108">**resource_length** String length of requested resource.</span></span>
- <span data-ttu-id="34cb8-1109">**host**: строка доменного имени сервера, оканчивающаяся нулевым символом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1109">**host** Null-terminated string of the server’s domain name.</span></span> <span data-ttu-id="34cb8-1110">Эта строка передается в поле заголовка узла HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1110">This string is transmitted in the HTTP Host header field.</span></span> <span data-ttu-id="34cb8-1111">Строка узла не может иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1111">The host string cannot be NULL.</span></span>
- <span data-ttu-id="34cb8-1112">**host_length**: длина строки узла.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1112">**host_length** String length of host.</span></span>
- <span data-ttu-id="34cb8-1113">**input_size**: размер входных данных для операций PUT и POST.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1113">**input_size** Size of input data for PUT and POST.</span></span> <span data-ttu-id="34cb8-1114">Для других операций следует передавать 0.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1114">Pass 0 for other operations.</span></span>
- <span data-ttu-id="34cb8-1115">**transfer_encoding_trunked**: зарезервированный параметр для будущей поддержки транкинговой передачи.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1115">**transfer_encoding_trunked** Reserved parameter for future trunked transfer support.</span></span>
- <span data-ttu-id="34cb8-1116">**username**: указатель на необязательное имя пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1116">**username** Pointer to optional user name for authentication.</span></span>
- <span data-ttu-id="34cb8-1117">**username_length**: длина строки имени пользователя для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1117">**username_length** String length of user name for authentication.</span></span>
- <span data-ttu-id="34cb8-1118">**password**: указатель на необязательный пароль для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1118">**password** Pointer to optional password for authentication.</span></span>
- <span data-ttu-id="34cb8-1119">**password_length**: длина строки пароля для проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1119">**password_length** String length of password for authentication.</span></span>
- <span data-ttu-id="34cb8-1120">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1120">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-1121">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-1121">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-1122">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1122">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-1123">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1123">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1124">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1124">Return Values</span></span>

- <span data-ttu-id="34cb8-1125">**TX_SUCCESS** (0x00): запрос успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1125">**NX_SUCCESS** (0x00) Successful initialization of request.</span></span>
- <span data-ttu-id="34cb8-1126">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1126">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-1127">NX_WEB_HTTP_METHOD_ERROR (0x30014): отсутствует необходимая информация (например, input_size для операции PUT или POST).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1127">NX_WEB_HTTP_METHOD_ERROR (0x30014) Some required information was missing (e.g. input_size for PUT or POST).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1128">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1128">Allowed From</span></span>

<span data-ttu-id="34cb8-1129">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1129">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1130">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1130">Example</span></span>

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
    calling *nx_web_http_client_response_body_get()* until the entire response is retrieved. */
get_status = NX_SUCCESS;
while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_request_packet_send"></a><span data-ttu-id="34cb8-1131">nx_web_http_client_request_packet_send</span><span class="sxs-lookup"><span data-stu-id="34cb8-1131">nx_web_http_client_request_packet_send</span></span>

<span data-ttu-id="34cb8-1132">Отправка удаленному серверу пакета данных HTTP(S)-запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1132">Send HTTP(S) request data packet to remote server</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1133">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1133">Prototype</span></span>

```C
UINT nx_web_http_client_request_packet_send(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET *packet_ptr, UINT more_date,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-1134">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1134">Description</span></span>

<span data-ttu-id="34cb8-1135">Эта служба отправляет пакет данных пользовательского HTTP(S)-запроса, созданный с помощью службы *nx_web_http_client_request_packet_allocate()* , на сервер, указанный в вызове службы *nx_web_http_client_connect()* или *nx_web_http_client_secure_connect(* ), который ранее установил подключение через сокет к удаленному узлу.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1135">This service sends a custom HTTP(S) request data packet created with *nx_web_http_client_request_packet_allocate* () to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect(*) call which has previously established the socket connection to the remote host.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1136">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1136">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1137">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1137">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-1138">**packet_ptr**: указатель на пакет данных HTTP(S)-запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1138">**packet_ptr** HTTP(S) request data packet pointer.</span></span>
- <span data-ttu-id="34cb8-1139">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1139">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-1140">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-1140">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-1141">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1141">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-1142">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1142">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1143">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1143">Return Values</span></span>

- <span data-ttu-id="34cb8-1144">**NX_SUCCESS** (0X00): пакет данных запроса успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1144">**NX_SUCCESS** (0x00) Successful send of request data packet.</span></span>
- <span data-ttu-id="34cb8-1145">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1145">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1146">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1146">Allowed From</span></span>

<span data-ttu-id="34cb8-1147">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1148">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1148">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a PUT request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_PUT,
    "https://192.168.1.150/test.txt ", "host.com",
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

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet request to server. */
status = nx_web_http_client_request_packet_send(&my_client,
    my_packet,
    0,
    NX_WAIT_FOREVER);
```

## <a name="nx_web_http_client_request_send"></a><span data-ttu-id="34cb8-1149">nx_web_http_client_request_send</span><span class="sxs-lookup"><span data-stu-id="34cb8-1149">nx_web_http_client_request_send</span></span>

<span data-ttu-id="34cb8-1150">Отправка пользовательского HTTP-запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1150">Send a custom HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1151">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1151">Prototype</span></span>

```C
UINT nx_web_http_client_request_send(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-1152">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1152">Description</span></span>

<span data-ttu-id="34cb8-1153">Эта служба отправляет пользовательский HTTP-запрос, созданный с помощью службы *nx_web_http_client_request_initialize()* , на сервер, указанный в вызове службы *nx_web_http_client_connect()* или *nx_web_http_client_secure_connect(* ), который ранее установил подключение через сокет к удаленному узлу.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1153">This service sends a custom HTTP request created with *nx_web_http_client_request_initialize()* to the server specified in the *nx_web_http_client_connect()* or *nx_web_http_client_secure_connect()* both of which have previously established the socket connection to the remote host.</span></span>

<span data-ttu-id="34cb8-1154">Использование этой службы позволяет приложению добавить любое количество пользовательских заголовков в запрос с помощью службы ***nx_web_http_client_request_header_add()***.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1154">Use of this service enables an application to add any number of custom headers to the request using the ***nx_web_http_client_request_header_add()*** service.</span></span> <span data-ttu-id="34cb8-1155">Это позволяет создавать пользовательские HTTP-запросы, предназначенные для конкретных приложений.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1155">This allows for customized HTTP requests intended for specific applications.</span></span>

> [!NOTE]
> <span data-ttu-id="34cb8-1156">Методы nx_web_http_client_\*_start предоставляются для удобства.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1156">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="34cb8-1157">Во всех этих функциях данная подпрограмма используется (как и служба *nx_web_http_client_request_initialize())* для создания и отправки HTTP-запросов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1157">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1158">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1158">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1159">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1159">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-1160">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1160">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-1161">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-1161">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-1162">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1162">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-1163">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1163">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1164">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1164">Return Values</span></span>

- <span data-ttu-id="34cb8-1165">**NX_SUCCESS** (0X00): запрос успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1165">**NX_SUCCESS** (0x00) Successful send of request.</span></span>
- <span data-ttu-id="34cb8-1166">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1166">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1167">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1167">Allowed From</span></span>

<span data-ttu-id="34cb8-1168">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1168">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1169">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1169">Example</span></span>

```C
/* Connect to a remote HTTPS server. */
nx_web_http_client_secure_connect(&my_client, IP_ADDRESS(1,2,3,5),
    NX_WEB_HTTPS_SERVER_PORT, tls_setup_callback,
    NX_WAIT_FOREVER);

/* Create a new GET request on the HTTP client instance. */
nx_web_http_client_request_initialize(&my_client,
    NX_WEB_HTTP_METHOD_GET,
    "https://192.168.1.150/test.txt ", "host.com",
    0, /* Used by PUT and POST only */
    NX_FALSE,
    NX_NULL, /* username */
    NX_NULL, /* password */
    NX_WAIT_FOREVER);

/* Start the GET operation to get a response from the HTTPS server. */
status = nx_web_http_client_request_send(&my_client, 1000);

/* At this point, we need to handle the response from the server by
    repeatedly calling *nx_web_http_client_response_body_get* until
    the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);

    /* Process response packets… */
}
```

## <a name="nx_web_http_client_response_body_get"></a><span data-ttu-id="34cb8-1170">nx_web_http_client_response_body_get</span><span class="sxs-lookup"><span data-stu-id="34cb8-1170">nx_web_http_client_response_body_get</span></span>

<span data-ttu-id="34cb8-1171">Получение следующего пакета данных ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1171">Get next resource data packet</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1172">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1172">Prototype</span></span>

```C
UINT nx_web_http_client_response_body_get(
    NX_WEB_HTTP_CLIENT *client_ptr,
    NX_PACKET **packet_ptr, ULONG
    wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-1173">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1173">Description</span></span>

<span data-ttu-id="34cb8-1174">Эта служба извлекает следующий пакет содержимого ресурса, запрошенного предшествовавшим вызовом службы *nx_web_http_client_get_start()* или *nx_web_http_client_get_secure_start()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1174">This service retrieves the next packet of content of the resource requested by the previous *nx_web_http_client_get_start()* or *nx_web_http_client_get_secure_start()* call.</span></span> <span data-ttu-id="34cb8-1175">Последовательные вызовы этой подпрограммы должны выполняться до получения состояния возврата NX_WEB_HTTP_GET_DONE.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1175">Successive calls to this routine should be made until the return status of NX_WEB_HTTP_GET_DONE is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1176">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1176">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1177">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1177">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-1178">**packet_ptr**: назначение для указателя пакета, содержащего частичное содержимое ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1178">**packet_ptr** Destination for packet pointer containing partial resource content.</span></span>
- <span data-ttu-id="34cb8-1179">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1179">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-1180">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-1180">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-1181">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1181">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-1182">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1182">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1183">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1183">Return Values</span></span>

- <span data-ttu-id="34cb8-1184">**NX_SUCCESS** (0x00): пакет HTTP-клиента успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1184">**NX_SUCCESS** (0x00) Successful get of HTTP Client packet.</span></span>
- <span data-ttu-id="34cb8-1185">**NX_WEB_HTTP_GET_DONE** (0x3000C): пакет HTTP-клиента получен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1185">**NX_WEB_HTTP_GET_DONE** (0x3000C) HTTP Client get packet is done</span></span>
- <span data-ttu-id="34cb8-1186">**NX_WEB_HTTP_NOT_READY** (0x3000A): HTTP-клиент не в режиме получения.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1186">**NX_WEB_HTTP_NOT_READY** (0x3000A) HTTP Client not in get mode.</span></span>
- <span data-ttu-id="34cb8-1187">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D): недопустимая длина пакета.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1187">**NX_WEB_HTTP_BAD_PACKET_LENGTH** (0x3000D) Invalid packet length</span></span>
- <span data-ttu-id="34cb8-1188">**NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A): код состояния HTTP "100 Continue" (100: продолжение).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1188">**NX_WEB_HTTP_STATUS_CODE_CONTINUE** (0x3001A) HTTP status code 100 Continue</span></span>
- <span data-ttu-id="34cb8-1189">**NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B): код состояния HTTP "101 Switching Protocols" (101: переключение протоколов).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1189">**NX_WEB_HTTP_STATUS_CODE_SWITCHING_PROTOCOLS** (0x3001B) HTTP status code 101 Switching Protocols</span></span>
- <span data-ttu-id="34cb8-1190">**NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C): код состояния HTTP "201 Created" (201: создано).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1190">**NX_WEB_HTTP_STATUS_CODE_CREATED** (0x3001C) HTTP status code 201 Created</span></span>
- <span data-ttu-id="34cb8-1191">**NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001C): код состояния HTTP "202 Accepted" (202: принято).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1191">**NX_WEB_HTTP_STATUS_CODE_ACCEPTED** (0x3001D) HTTP status code 202 Accepted</span></span>
- <span data-ttu-id="34cb8-1192">**NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E): код состояния HTTP "203 Non-Authoritative Information" (203: не заслуживающая доверия информация).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1192">**NX_WEB_HTTP_STATUS_CODE_NON_AUTH_INFO** (0x3001E) HTTP status code 203 Non-Authoritative Information</span></span>
- <span data-ttu-id="34cb8-1193">**NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F): код состояния HTTP "204 No Content" (204: содержимое отсутствует).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1193">**NX_WEB_HTTP_STATUS_CODE_NO_CONTENT** (0x3001F) HTTP status code 204 No Content</span></span>
- <span data-ttu-id="34cb8-1194">**NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020): код состояния HTTP "205 Reset Content" (205: сброс содержимого).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1194">**NX_WEB_HTTP_STATUS_CODE_RESET_CONTENT** (0x30020) HTTP status code 205 Reset Content</span></span>
- <span data-ttu-id="34cb8-1195">**NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021): код состояния HTTP "206 Partial Content" (206: неполное содержимое).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1195">**NX_WEB_HTTP_STATUS_CODE_PARTIAL_CONTENT** (0x30021) HTTP status code 206 Partial Content</span></span>
- <span data-ttu-id="34cb8-1196">**NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022): код состояния HTTP "300 Multiple Choices" (300: несколько вариантов).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1196">**NX_WEB_HTTP_STATUS_CODE_MULTIPLE_CHOICES** (0x30022) HTTP status code 300 Multiple Choices</span></span>
- <span data-ttu-id="34cb8-1197">**NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023): код состояния HTTP "301 Moved Permanently" (301: окончательно перемещено).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1197">**NX_WEB_HTTP_STATUS_CODE_MOVED_PERMANETLY** (0x30023) HTTP status code 301 Moved Permanently</span></span>
- <span data-ttu-id="34cb8-1198">**NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024): код состояния HTTP "302 Found" (302: найдено).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1198">**NX_WEB_HTTP_STATUS_CODE_FOUND** (0x30024) HTTP status code 302 Found</span></span>
- <span data-ttu-id="34cb8-1199">**NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025): код состояния HTTP "303 See Other" (303: перенаправление).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1199">**NX_WEB_HTTP_STATUS_CODE_SEE_OTHER** (0x30025) HTTP status code 303 See Other</span></span>
- <span data-ttu-id="34cb8-1200">**NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026): код состояния HTTP "304 Not Modified" (304: не изменено).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1200">**NX_WEB_HTTP_STATUS_CODE_NOT_MODIFIED** (0x30026) HTTP status code 304 Not Modified</span></span>
- <span data-ttu-id="34cb8-1201">**NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027): код состояния HTTP "305 Use Proxy" (305: использование прокси-сервера).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1201">**NX_WEB_HTTP_STATUS_CODE_USE_PROXY** (0x30027) HTTP status code 305 Use Proxy</span></span>
- <span data-ttu-id="34cb8-1202">**NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028): код состояния HTTP "307 Temporary Redirect" (307: временное перенаправление).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1202">**NX_WEB_HTTP_STATUS_CODE_TEMPORARY_REDIRECT** (0x30028) HTTP status code 307 Temporary Redirect</span></span>
- <span data-ttu-id="34cb8-1203">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029): код состояния HTTP "400 Bad Request" (400: недействительный запрос).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1203">**NX_WEB_HTTP_STATUS_CODE_BAD_REQUEST** (0x30029) HTTP status code 400 Bad Request</span></span>
- <span data-ttu-id="34cb8-1204">**NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A): код состояния HTTP "401 Unauthorized" (401: не авторизовано).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1204">**NX_WEB_HTTP_STATUS_CODE_UNAUTHORIZED** (0x3002A) HTTP status code 401 Unauthorized</span></span>
- <span data-ttu-id="34cb8-1205">**NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B): код состояния HTTP "402 Payment Required" (402: требуется оплата).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1205">**NX_WEB_HTTP_STATUS_CODE_PAYMENT_REQUIRED** (0x3002B) HTTP status code 402 Payment Required</span></span>
- <span data-ttu-id="34cb8-1206">**NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C): код состояния HTTP "403 Forbidden" (403: запрещено).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1206">**NX_WEB_HTTP_STATUS_CODE_FORBIDDEN** (0x3002C) HTTP status code 403 Forbidden</span></span>
- <span data-ttu-id="34cb8-1207">**NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D): код состояния HTTP "404 Not Found" (404: не найдено).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1207">**NX_WEB_HTTP_STATUS_CODE_NOT_FOUND** (0x3002D) HTTP status code 404 Not Found</span></span>
- <span data-ttu-id="34cb8-1208">**NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E): код состояния HTTP "405 Method Not Allowed" (405: метод запрещен).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1208">**NX_WEB_HTTP_STATUS_CODE_METHOD_NOT_ALLOWED** (0x3002E) HTTP status code 405 Method Not Allowed</span></span>
- <span data-ttu-id="34cb8-1209">**NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F): код состояния HTTP "406 Not Acceptable" (406: неприемлемо).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1209">**NX_WEB_HTTP_STATUS_CODE_NOT_ACCEPTABLE** (0x3002F) HTTP status code 406 Not Acceptable</span></span>
- <span data-ttu-id="34cb8-1210">**NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030): код состояния HTTP "407 Proxy Authentication Required" (407: требуется проверка подлинности прокси-сервера).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1210">**NX_WEB_HTTP_STATUS_CODE_PROXY_AUTH_REQUIRED** (0x30030) HTTP status code 407 Proxy Authentication Required</span></span>
- <span data-ttu-id="34cb8-1211">**NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031): код состояния HTTP "408 Request Time-out" (408: превышено время ожидания запроса).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1211">**NX_WEB_HTTP_STATUS_CODE_REQUEST_TIMEOUT** (0x30031) HTTP status code 408 Request Time-out</span></span>
- <span data-ttu-id="34cb8-1212">**NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032): код состояния HTTP "409 Conflict" (409: конфликт).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1212">**NX_WEB_HTTP_STATUS_CODE_CONFLICT** (0x30032) HTTP status code 409 Conflict</span></span>
- <span data-ttu-id="34cb8-1213">**NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033): код состояния HTTP "410 Gone" (401: отсутствует).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1213">**NX_WEB_HTTP_STATUS_CODE_GONE** (0x30033) HTTP status code 410 Gone</span></span>
- <span data-ttu-id="34cb8-1214">**NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034): код состояния HTTP "411 Length Required" (411: требуется указать длину).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1214">**NX_WEB_HTTP_STATUS_CODE_LENGTH_REQUIRED** (0x30034) HTTP status code 411 Length Required</span></span>
- <span data-ttu-id="34cb8-1215">**NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035): код состояния HTTP "412 Precondition Failed" (412: необходимое условие не выполнено).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1215">**NX_WEB_HTTP_STATUS_CODE_PRECONDITION_FAILED** (0x30035) HTTP status code 412 Precondition Failed</span></span>
- <span data-ttu-id="34cb8-1216">**NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036): код состояния HTTP "413 Request Entity Too Large" (413: слишком большой объект запроса).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1216">**NX_WEB_HTTP_STATUS_CODE_ENTITY_TOO_LARGE** (0x30036) HTTP status code 413 Request Entity Too Large</span></span>
- <span data-ttu-id="34cb8-1217">**NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037): код состояния HTTP "414 Request URL Too Large" (414: слишком длинный URL-адрес запроса).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1217">**NX_WEB_HTTP_STATUS_CODE_URL_TOO_LARGE** (0x30037) HTTP status code 414 Request URL Too Large</span></span>
- <span data-ttu-id="34cb8-1218">**NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038): код состояния HTTP "415 Unsupported Media Type" (415: неподдерживаемый тип носителя).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1218">**NX_WEB_HTTP_STATUS_CODE_UNSUPPORTED_MEDIA** (0x30038) HTTP status code 415 Unsupported Media Type</span></span>
- <span data-ttu-id="34cb8-1219">**NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039): код состояния HTTP "416 Requested range not satisfiable" (416: запрошенный диапазон невыполним).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1219">**NX_WEB_HTTP_STATUS_CODE_RANGE_NOT_SATISFY** (0x30039) HTTP status code 416 Requested range not satisfiable</span></span>
- <span data-ttu-id="34cb8-1220">**NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A): код состояния HTTP "417 Expectation Failed" (417: ошибка ожидания).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1220">**NX_WEB_HTTP_STATUS_CODE_EXPECTATION_FAILED** (0x3003A) HTTP status code 417 Expectation Failed</span></span>
- <span data-ttu-id="34cb8-1221">**NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B): код состояния HTTP "500 Internal Server Error" (500: внутренняя ошибка сервера).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1221">**NX_WEB_HTTP_STATUS_CODE_INTERNAL_ERROR** (0x3003B) HTTP status code 500 Internal Server Error</span></span>
- <span data-ttu-id="34cb8-1222">**NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C): код состояния HTTP "501 Not Implemented" (501: не реализовано).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1222">**NX_WEB_HTTP_STATUS_CODE_NOT_IMPLEMENTED** (0x3003C) HTTP status code 501 Not Implemented</span></span>
- <span data-ttu-id="34cb8-1223">**NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D): код состояния HTTP "502 Bad Gateway" (502: недопустимый шлюз).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1223">**NX_WEB_HTTP_STATUS_CODE_BAD_GATEWAY** (0x3003D) HTTP status code 502 Bad Gateway</span></span>
- <span data-ttu-id="34cb8-1224">**NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E): код состояния HTTP "503 Service Unavailable" (503: служба недоступна).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1224">**NX_WEB_HTTP_STATUS_CODE_SERVICE_UNAVAILABLE** (0x3003E) HTTP status code 503 Service Unavailable</span></span>
- <span data-ttu-id="34cb8-1225">**NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F): код состояния HTTP "504 Gateway Time-out" (504: превышено время ожидания шлюза).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1225">**NX_WEB_HTTP_STATUS_CODE_GATEWAY_TIMEOUT** (0x3003F) HTTP status code 504 Gateway Time-out</span></span>
- <span data-ttu-id="34cb8-1226">**NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040): код состояния HTTP "505 HTTP Version not supported" (505: версия протокола HTTP не поддерживается).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1226">**NX_WEB_HTTP_STATUS_CODE_VERSION_ERROR** (0x30040) HTTP status code 505 HTTP Version not supported</span></span>
- <span data-ttu-id="34cb8-1227">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1227">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-1228">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1228">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1229">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1229">Allowed From</span></span>

<span data-ttu-id="34cb8-1230">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1230">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1231">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1231">Example</span></span>

```C
/* Get the next packet of resource content on the HTTP Client "my_client."
    Note that the nx_web_http_client_get_start() routine must have been called
    previously. */
status = nx_web_http_client_response_body_get(&my_client, &next_packet, 1000);

/* If status is NX_SUCCESS, the next packet of content is pointed to
    by "next_packet". */
```

## <a name="nx_web_http_client_response_header_callback_set"></a><span data-ttu-id="34cb8-1232">nx_web_http_client_response_header_callback_set</span><span class="sxs-lookup"><span data-stu-id="34cb8-1232">nx_web_http_client_response_header_callback_set</span></span>

<span data-ttu-id="34cb8-1233">Задание обратного вызова для выполнения при обработке заголовков HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1233">Set callback to invoke when processing HTTP headers</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1234">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1234">Prototype</span></span>

```C
UINT nx_web_http_client_response_header_callback_set(
    NX_WEB_HTTP_CLIENT *client_ptr,
    VOID (*callback_function)(NX_WEB_HTTP_CLIENT *client_ptr,
    CHAR *field_name, UINT field_name_length,
    CHAR *field_value, UINT field_value_length));
```

### <a name="description"></a><span data-ttu-id="34cb8-1235">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1235">Description</span></span>

<span data-ttu-id="34cb8-1236">Эта служба назначает обратный вызов, который будет вызываться каждый раз, когда клиент NetX Web HTTP обрабатывает заголовок HTTP во входящем ответе от удаленного HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1236">This service assigns a callback that will be invoked whenever NetX Web HTTP Client processes an HTTP header in an incoming response from a remote HTTP server.</span></span> <span data-ttu-id="34cb8-1237">При обработке обратный вызов выполняется один раз для каждого заголовка в ответе.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1237">The callback is invoked once for each header in the response as it is processed.</span></span> <span data-ttu-id="34cb8-1238">Обратный вызов позволяет приложению HTTP-клиента получить доступ к каждому из заголовков в ответе HTTP-сервера, чтобы выполнять все необходимые действия, помимо базовой обработки, выполняемой клиентом NetX Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1238">The callback allows an HTTP Client application to access each of the headers in the HTTP server response to take any desired actions beyond the basic processing that NetX Web HTTP Client does.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1239">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1239">Input Parameters</span></span>

<span data-ttu-id="34cb8-1240">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1240">**client_ptr** Pointer to HTTP Client control block.</span></span>

<span data-ttu-id="34cb8-1241">**callback_function**: функция обратного вызова, вызываемая во время обработки заголовка ответа.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1241">**callback_function** Callback invoked during response header processing.</span></span> <span data-ttu-id="34cb8-1242">Обратный вызов выполняется со строковыми значениями имени и значения поля (и их длиной).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1242">The callback is invoked with the field name and value as strings (and their lengths).</span></span> <span data-ttu-id="34cb8-1243">Например, заголовок "Content-Length: 100" приведет к вызову функции со строкой "Content-Length" для параметра *field_name* и строкой "100" для параметра *field_value*.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1243">For example, the header "Content-Length: 100" would cause the function to be invoked with "Content-Length" for *field_name* and the string "100" for *field_value*.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1244">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1244">Return Values</span></span>

- <span data-ttu-id="34cb8-1245">**NX_SUCCESS** (0X00): функция обратного вызова успешно назначена.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1245">**NX_SUCCESS** (0x00) Successful assignment of callback.</span></span>
- <span data-ttu-id="34cb8-1246">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1246">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1247">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1247">Allowed From</span></span>

<span data-ttu-id="34cb8-1248">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1248">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1249">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1249">Example</span></span>

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

## <a name="nx_web_http_client_secure_connect"></a><span data-ttu-id="34cb8-1250">nx_web_http_client_secure_connect</span><span class="sxs-lookup"><span data-stu-id="34cb8-1250">nx_web_http_client_secure_connect</span></span>

<span data-ttu-id="34cb8-1251">Открытие сеанса TLS с HTTPS-сервером для обработки пользовательских запросов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1251">Open a TLS session to an HTTPS server for custom requests</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1252">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1252">Prototype</span></span>

```C
UINT nx_web_http_client_secure_connect(NX_WEB_HTTP_CLIENT *client_ptr,
    NXD_ADDRESS *server_ip, UINT server_port,
    UINT (*tls_setup)(NX_WEB_HTTP_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *tls),
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-1253">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1253">Description</span></span>

<span data-ttu-id="34cb8-1254">Этот метод предназначен для протокола HTTPS **с шифрованием TLS**.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1254">This method is for **TLS-secured** HTTPS.</span></span>

<span data-ttu-id="34cb8-1255">Эта служба открывает защищенный сеанс TLS с HTTPS-сервером, но не отправляет запросы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1255">This service opens a secured TLS session to an HTTPS server but does not send any requests.</span></span> <span data-ttu-id="34cb8-1256">Для создания запросов используется служба *nx_web_http_client_request_initialize()* , а для отправки — служба *nx_web_http_client_request_send()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1256">Requests are created with n *x_web_http_client_request_initialize()* and sent using *nx_web_http_client_request_send()*.</span></span> <span data-ttu-id="34cb8-1257">Пользовательские заголовки HTTP можно добавить в запрос с помощью службы *nx_web_http_client_request_header_add()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1257">Custom HTTP headers may be added to the request using *nx_web_http_client_request_header_add()*.</span></span>

<span data-ttu-id="34cb8-1258">С помощью этой службы приложение может добавить в запрос любое количество пользовательских заголовков.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1258">Use of this service enables an application to add any number of custom headers to the request.</span></span> <span data-ttu-id="34cb8-1259">**Это позволяет создавать пользовательские HTTP-запросы, предназначенные для конкретных приложений.**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1259">**This allows for customized HTTP requests intended for specific applications.**</span></span>

> [!NOTE]
> <span data-ttu-id="34cb8-1260">Методы nx_web_http_client_\*_start предоставляются для удобства.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1260">The nx_web_http_client_\*_start methods are provided for convenience.</span></span> <span data-ttu-id="34cb8-1261">Во всех этих функциях данная подпрограмма используется (как и служба *nx_web_http_client_request_initialize())* для создания и отправки HTTP-запросов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1261">These functions all use this routine internally (along with *nx_web_http_client_request_initialize())* to create and send HTTP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1262">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1262">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1263">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1263">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-1264">**server_ip**: IP-адрес удаленного HTTPS-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1264">**server_ip** IP address of remote HTTPS server.</span></span>
- <span data-ttu-id="34cb8-1265">**server_port**: порт на удаленном HTTPS-сервере (например, 443 для HTTPS).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1265">**server_port** Port on remote HTTPS server (e.g. 443 for HTTPS).</span></span>
- <span data-ttu-id="34cb8-1266">**tls_setup**: обратный вызов, используемый для настройки конфигурации TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1266">**tls_setup** Callback used to setup TLS configuration.</span></span> <span data-ttu-id="34cb8-1267">Приложение определяет этот обратный вызов для инициализации шифрования и учетных данных TLS (например, сертификатов).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1267">The application defines this callback to initialize TLS cryptography and credentials (e.g. certificates).</span></span>
- <span data-ttu-id="34cb8-1268">**wait_option**: определяет, как долго служба будет ожидать запуска запроса GET HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1268">**wait_option** Defines how long the service will wait for the HTTP Client get start request.</span></span> <span data-ttu-id="34cb8-1269">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-1269">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-1270">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1270">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>
  - <span data-ttu-id="34cb8-1271">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1271">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1272">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1272">Return Values</span></span>

- <span data-ttu-id="34cb8-1273">**NX_SUCCESS** (0X00): сеанс TCP успешно подключен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1273">**NX_SUCCESS** (0x00) Successful connection of TLS session.</span></span>
- <span data-ttu-id="34cb8-1274">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1274">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-1275">NX_WEB_HTTP_NOT_READY (0x3000A): уже выполняется другой запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1275">NX_WEB_HTTP_NOT_READY (0x3000A) Another request is already in progress.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1276">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1276">Allowed From</span></span>

<span data-ttu-id="34cb8-1277">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1278">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1278">Example</span></span>

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
    "https://192.168.1.150/test.txt ", "host.com",
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
    calling *nx_web_http_client_response_body_get* until the entire response is retrieved. */

get_status = NX_SUCCESS;

while(get_status != NX_WEB_HTTP_GET_DONE)
{
    get_status = nx_web_http_client_response_body_get(&my_client, &receive_packet,
        NX_WAIT_FOREVER);
    /* Process response packets… */
}
```

## <a name="http-and-https-server-api"></a><span data-ttu-id="34cb8-1279">Интерфейсы API HTTP- и HTTPS-сервера</span><span class="sxs-lookup"><span data-stu-id="34cb8-1279">HTTP and HTTPS Server API</span></span>

## <a name="nx_web_http_server_cache_info_callback_set"></a><span data-ttu-id="34cb8-1280">nx_web_http_server_cache_info_callback_set</span><span class="sxs-lookup"><span data-stu-id="34cb8-1280">nx_web_http_server_cache_info_callback_set</span></span>

<span data-ttu-id="34cb8-1281">Задание обратного вызова для получения максимального возраста и даты URL-адреса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1281">Set the callback to retrieve URL max age and date</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1282">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1282">Prototype</span></span>

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)(CHAR *resource,
    UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *date));
```

### <a name="description"></a><span data-ttu-id="34cb8-1283">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1283">Description</span></span>

<span data-ttu-id="34cb8-1284">Эта служба задает службу обратного вызова, вызываемую для получения максимального возраста и даты последнего изменения указанного ресурса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1284">This service sets the callback service invoked to obtain the maximum age and last modified date of the specified resource.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1285">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1285">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1286">**server_ptr**: указатель на блок управления HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1286">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="34cb8-1287">**cache_info_get**: указатель на обратный вызов</span><span class="sxs-lookup"><span data-stu-id="34cb8-1287">**cache_info_get** Pointer to the callback</span></span>
- <span data-ttu-id="34cb8-1288">**max_age**: указатель на максимальный возраст ресурса</span><span class="sxs-lookup"><span data-stu-id="34cb8-1288">**max_age** Pointer to maximum age of a resource</span></span>
- <span data-ttu-id="34cb8-1289">**data**: указатель на возвращенную дату последнего изменения.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1289">**data** Pointer to last modified date returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1290">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1290">Return Values</span></span>

- <span data-ttu-id="34cb8-1291">**NX_SUCCESS** (0x00) — обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1291">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="34cb8-1292">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1292">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1293">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1293">Allowed From</span></span>

<span data-ttu-id="34cb8-1294">Инициализация</span><span class="sxs-lookup"><span data-stu-id="34cb8-1294">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1295">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1295">Example</span></span>

```C
NX_WEB_HTTP_SERVER my_server;

UINT cache_info_get(CHAR *resource, UINT *max_age,
    NX_WEB_HTTP_SERVER_DATE *last_modified);

/* After my_server is created with nx_web_http_server_create and before the HTTP
    server is set by nx_web_http_server_start(), set the cache info callback: */
status = nx_web_http_server_cache_info_callback_set(&my_server, cache_info_get);

/* If status is NX_SUCCESS, the callback was successfully sent. */
```

## <a name="nx_web_http_server_callback_data_send"></a><span data-ttu-id="34cb8-1296">nx_web_http_server_callback_data_send</span><span class="sxs-lookup"><span data-stu-id="34cb8-1296">nx_web_http_server_callback_data_send</span></span>

<span data-ttu-id="34cb8-1297">Отправка данных из функции обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1297">Send data from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1298">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1298">Prototype</span></span>

```C
UINT nx_web_http_server_callback_data_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID *data_ptr, ULONG data_length);
```

### <a name="description"></a><span data-ttu-id="34cb8-1299">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1299">Description</span></span>

<span data-ttu-id="34cb8-1300">Эта служба отправляет данные в предоставленном пакете из подпрограммы обратного вызова приложения.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1300">This service sends the data in the supplied packet from the application’s callback routine.</span></span> <span data-ttu-id="34cb8-1301">Обычно она используется для отправки динамических данных, связанных с запросами GET/POST.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1301">This is typically used to send dynamic data associated with GET/POST requests.</span></span> <span data-ttu-id="34cb8-1302">Обратите внимание, что, если используется эта функция, то подпрограмма обратного вызова отвечает за отправку всего ответа в правильном формате.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1302">Note that if this function is used, the callback routine is responsible for sending the entire response in the proper format.</span></span> <span data-ttu-id="34cb8-1303">Кроме того, подпрограмма обратного вызова должна возвращать состояние NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1303">In addition, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1304">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1304">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1305">**server_ptr**: указатель на блок управления HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1305">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="34cb8-1306">**data_ptr**: указатель на данные для отправки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1306">**data_ptr** Pointer to the data to send.</span></span>
- <span data-ttu-id="34cb8-1307">**data_length**: число отправляемых байтов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1307">**data_length** Number of bytes to send.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1308">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1308">Return Values</span></span>

- <span data-ttu-id="34cb8-1309">**NX_SUCCESS** (0x00) — данные сервера успешно отправлены.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1309">**NX_SUCCESS** (0x00) Successfully sent Server data</span></span>
- <span data-ttu-id="34cb8-1310">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1310">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1311">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1311">Allowed From</span></span>

<span data-ttu-id="34cb8-1312">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1312">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1313">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1313">Example</span></span>

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

## <a name="nx_web_http_server_callback_generate_response_header"></a><span data-ttu-id="34cb8-1314">nx_web_http_server_callback_generate_response_header</span><span class="sxs-lookup"><span data-stu-id="34cb8-1314">nx_web_http_server_callback_generate_response_header</span></span>

<span data-ttu-id="34cb8-1315">Создание заголовка ответа в функции обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1315">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1316">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1316">Prototype</span></span>

```C
UINT nx_web_http_server_callback_generate_response_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    CHAR *status_code, UINT content_length,
    CHAR *content_type, CHAR* additional_header);
```

### <a name="description"></a><span data-ttu-id="34cb8-1317">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1317">Description</span></span>

<span data-ttu-id="34cb8-1318">Эта служба используется в подпрограмме обратного вызова HTTP(S)-сервера (определяется приложением) для создания заголовка ответа HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1318">This service is used in the HTTP(S) server callback routine (defined by the application) to generate an HTTP response header.</span></span> <span data-ttu-id="34cb8-1319">Подпрограмма обратного вызова сервера вызывается, когда HTTP-сервер отвечает на запросы GET, PUT и DELETE клиента, требующие ответа HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1319">The server callback routine is invoked when the HTTP server responds to Client GET, PUT and DELETE requests which require an HTTP response.</span></span> <span data-ttu-id="34cb8-1320">Эта функция принимает из приложения данные ответа и создает соответствующий заголовок ответа.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1320">This function takes the response information from the application and generates the appropriate response header.</span></span> <span data-ttu-id="34cb8-1321">Дополнительные сведения о подпрограмме обратного вызова для запросов сервера см. в описании службы *nx_web_http_server_create()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1321">See the service *nx_web_http_server_create()* for more information on the server request callback routine.</span></span>

<span data-ttu-id="34cb8-1322">Это нерекомендуемый API.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1322">This API is deprecated.</span></span> <span data-ttu-id="34cb8-1323">Разработчикам рекомендуется использовать службу *nx_web_http_server_callback_generate_response_header_extended()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1323">Developers are encouraged to use *nx_web_http_server_callback_generate_response_header_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1324">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1324">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1325">**server_ptr**: указатель на блок управления HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1325">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="34cb8-1326">**packet_pptr**: указатель на указатель пакета, выделенный для сообщения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1326">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="34cb8-1327">**status_code**: указывает состояние ресурса</span><span class="sxs-lookup"><span data-stu-id="34cb8-1327">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="34cb8-1328">Примеры:</span><span class="sxs-lookup"><span data-stu-id="34cb8-1328">Examples:</span></span>
  - <span data-ttu-id="34cb8-1329">**NX_WEB_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1329">**NX_WEB_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="34cb8-1330">**NX_WEB_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1330">**NX_WEB_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="34cb8-1331">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1331">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="34cb8-1332">**content_length**: размер содержимого в байтах.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1332">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="34cb8-1333">**content_type**: тип HTTP, например "text/plain".</span><span class="sxs-lookup"><span data-stu-id="34cb8-1333">**content_type** Type of HTTP e.g. "text/plain"</span></span>
- <span data-ttu-id="34cb8-1334">**additional_header**: указатель на дополнительный текст заголовка.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1334">**additional_header** Pointer to additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1335">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1335">Return Values</span></span>

- <span data-ttu-id="34cb8-1336">**NX_SUCCESS** (0X00): заголовок HTML успешно создан.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1336">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="34cb8-1337">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1337">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1338">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1338">Allowed From</span></span>

<span data-ttu-id="34cb8-1339">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1339">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1340">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1340">Example</span></span>

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

## <a name="nx_web_http_server_callback_generate_response_header_extended"></a><span data-ttu-id="34cb8-1341">nx_web_http_server_callback_generate_response_header_extended</span><span class="sxs-lookup"><span data-stu-id="34cb8-1341">nx_web_http_server_callback_generate_response_header_extended</span></span>

<span data-ttu-id="34cb8-1342">Создание заголовка ответа в функции обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1342">Create a response header in a callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1343">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1343">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="34cb8-1344">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1344">Description</span></span>

<span data-ttu-id="34cb8-1345">Эта служба используется в подпрограмме обратного вызова HTTP(S)-сервера (определяется приложением) для создания заголовка ответа HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1345">This service is used in the HTTP(S) server callback routine (defined by the application) to generate an HTTP response header.</span></span> <span data-ttu-id="34cb8-1346">Подпрограмма обратного вызова сервера вызывается, когда HTTP-сервер отвечает на запросы GET, PUT и DELETE клиента, требующие ответа HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1346">The server callback routine is invoked when the HTTP server responds to Client GET, PUT and DELETE requests which require an HTTP response.</span></span> <span data-ttu-id="34cb8-1347">Эта функция принимает из приложения данные ответа и создает соответствующий заголовок ответа.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1347">This function takes the response information from the application and generates the appropriate response header.</span></span> <span data-ttu-id="34cb8-1348">Дополнительные сведения о подпрограмме обратного вызова для запросов сервера см. в описании службы *nx_web_http_server_create()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1348">See the service *nx_web_http_server_create()* for more information on the server request callback routine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1349">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1349">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1350">**server_ptr**: указатель на блок управления HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1350">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="34cb8-1351">**packet_pptr**: указатель на указатель пакета, выделенный для сообщения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1351">**packet_pptr** Pointer a packet pointer allocated for message</span></span>
- <span data-ttu-id="34cb8-1352">**status_code**: указывает состояние ресурса</span><span class="sxs-lookup"><span data-stu-id="34cb8-1352">**status_code** Indicate status of resource.</span></span> <span data-ttu-id="34cb8-1353">Примеры:</span><span class="sxs-lookup"><span data-stu-id="34cb8-1353">Examples:</span></span>
  - <span data-ttu-id="34cb8-1354">**NX_WEB_HTTP_STATUS_OK**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1354">**NX_WEB_HTTP_STATUS_OK**</span></span>
  - <span data-ttu-id="34cb8-1355">**NX_WEB_HTTP_STATUS_MODIFIED**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1355">**NX_WEB_HTTP_STATUS_MODIFIED**</span></span>
  - <span data-ttu-id="34cb8-1356">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span><span class="sxs-lookup"><span data-stu-id="34cb8-1356">**NX_WEB_HTTP_STATUS_INTERNAL_ERROR**</span></span>
- <span data-ttu-id="34cb8-1357">**status_code**: длина строки кода состояния.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1357">**status_code_length** String length of status code</span></span>
- <span data-ttu-id="34cb8-1358">**content_length**: размер содержимого в байтах.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1358">**content_length** Size of content in bytes</span></span>
- <span data-ttu-id="34cb8-1359">**content_type**: тип HTTP, например "text/plain".</span><span class="sxs-lookup"><span data-stu-id="34cb8-1359">**content_type** Type of HTTP e.g. "text/plain"</span></span>
- <span data-ttu-id="34cb8-1360">**content_type_length**: длина строки типа содержимого.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1360">**content_type_length** String length of content type</span></span>
- <span data-ttu-id="34cb8-1361">**additional_header**: указатель на дополнительный текст заголовка.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1361">**additional_header** Pointer to additional header text</span></span>
- <span data-ttu-id="34cb8-1362">**additional_header_length**: длина дополнительного текста заголовка.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1362">**additional_header_length** Length of additional header text</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1363">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1363">Return Values</span></span>

- <span data-ttu-id="34cb8-1364">**NX_SUCCESS** (0X00): заголовок HTML успешно создан.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1364">**NX_SUCCESS** (0x00) Successfully created HTML header</span></span>
- <span data-ttu-id="34cb8-1365">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1365">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1366">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1366">Allowed From</span></span>

<span data-ttu-id="34cb8-1367">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1367">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1368">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1368">Example</span></span>

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

## <a name="nx_web_http_server_callback_packet_send"></a><span data-ttu-id="34cb8-1369">nx_web_http_server_callback_packet_send</span><span class="sxs-lookup"><span data-stu-id="34cb8-1369">nx_web_http_server_callback_packet_send</span></span>

<span data-ttu-id="34cb8-1370">Отправка пакета HTTP из функции обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1370">Send an HTTP packet from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1371">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1371">Prototype</span></span>

```C
UINT nx_web_http_server_callback_packet_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="34cb8-1372">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1372">Description</span></span>

<span data-ttu-id="34cb8-1373">Эта служба отправляет полный ответ HTTP-сервера из обратного вызова HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1373">This service sends a complete HTTP server response from an HTTP callback.</span></span> <span data-ttu-id="34cb8-1374">HTTP-сервер отправит пакет с NX_WEB_HTTP_SERVER_TIMEOUT_SEND.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1374">HTTP server will send the packet with the NX_WEB_HTTP_SERVER _TIMEOUT_SEND.</span></span> <span data-ttu-id="34cb8-1375">В пакет должны быть добавлены заголовок и данные HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1375">The HTTP header and data must be appended to the packet.</span></span> <span data-ttu-id="34cb8-1376">Если возвращаемое состояние указывает на ошибку, приложение HTTP должно освободить пакет.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1376">If the return status indicates an error, the HTTP application must release the packet.</span></span>

<span data-ttu-id="34cb8-1377">Обратный вызов должен возвращать NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1377">The callback should return NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="34cb8-1378">Более подробный пример: *nx_http_server_callback_generate_response_header()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1378">See *nx_web_http_server_callback_generate_response_header()* for a more detailed example.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1379">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1379">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1380">**server_ptr**: указатель на управляющий блок HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1380">**server_ptr** Pointer to HTTP Server control block</span></span>
- <span data-ttu-id="34cb8-1381">**packet_ptr**: указатель на пакет для отправки.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1381">**packet_ptr** Pointer to the packet to send</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1382">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1382">Return Values</span></span>

- <span data-ttu-id="34cb8-1383">**NX_SUCCESS** (0X00): пакет HTTP-сервера успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1383">**NX_SUCCESS** (0x00) Successfully sent HTTP Server packet</span></span>
- <span data-ttu-id="34cb8-1384">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1384">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1385">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1385">Allowed From</span></span>

<span data-ttu-id="34cb8-1386">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1386">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1387">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1387">Example</span></span>

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

## <a name="nx_web_http_server_callback_response_send"></a><span data-ttu-id="34cb8-1388">nx_web_http_server_callback_response_send</span><span class="sxs-lookup"><span data-stu-id="34cb8-1388">nx_web_http_server_callback_response_send</span></span>

<span data-ttu-id="34cb8-1389">Отправка ответа из функции обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1389">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1390">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1390">Prototype</span></span>

```C
UINT nx_web_http_server_callback_response_send(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header,
    CHAR *information,
    CHAR additional_info);
```

### <a name="description"></a><span data-ttu-id="34cb8-1391">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1391">Description</span></span>

<span data-ttu-id="34cb8-1392">Эта служба отправляет указанные сведения об ответе из подпрограммы обратного вызова приложения.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1392">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="34cb8-1393">Обычно она используется для отправки пользовательских ответов, связанных с запросами GET и POST.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1393">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="34cb8-1394">Обратите внимание, что, если используется эта функция, то подпрограмма обратного вызова должна возвращать состояние NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1394">Note that if this function is used, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="34cb8-1395">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1395">This service is deprecated.</span></span> <span data-ttu-id="34cb8-1396">Разработчикам рекомендуется использовать службу *nx_web_http_server_callback_response_send_extended()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1396">Developers are encouraged to use *nx_web_http_server_callback_response_send_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1397">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1397">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1398">**server_ptr**: указатель на блок управления HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1398">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="34cb8-1399">**header**: указатель на строку заголовка ответа</span><span class="sxs-lookup"><span data-stu-id="34cb8-1399">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="34cb8-1400">**information**: указатель на строку информации</span><span class="sxs-lookup"><span data-stu-id="34cb8-1400">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="34cb8-1401">**additional_info**: указатель на строку дополнительной информации.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1401">**additional_info** Pointer to the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1402">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1402">Return Values</span></span>

- <span data-ttu-id="34cb8-1403">**NX_SUCCESS** (0X00): ответ HTTP-сервера успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1403">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1404">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1404">Allowed From</span></span>

<span data-ttu-id="34cb8-1405">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1405">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1406">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1406">Example</span></span>

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

## <a name="nx_web_http_server_callback_response_send_extended"></a><span data-ttu-id="34cb8-1407">nx_web_http_server_callback_response_send_extended</span><span class="sxs-lookup"><span data-stu-id="34cb8-1407">nx_web_http_server_callback_response_send_extended</span></span>

<span data-ttu-id="34cb8-1408">Отправка ответа из функции обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1408">Send response from callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1409">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1409">Prototype</span></span>

```C
UINT nx_web_http_server_callback_response_send_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    CHAR *header, UINT header_length,
    CHAR *information,
    UINT information_length,
    CHAR additional_info,
    UINT additional_info_length);
```

### <a name="description"></a><span data-ttu-id="34cb8-1410">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1410">Description</span></span>

<span data-ttu-id="34cb8-1411">Эта служба отправляет указанные сведения об ответе из подпрограммы обратного вызова приложения.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1411">This service sends the supplied response information from the application’s callback routine.</span></span> <span data-ttu-id="34cb8-1412">Обычно она используется для отправки пользовательских ответов, связанных с запросами GET и POST.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1412">This is typically used to send custom responses associated with GET/POST requests.</span></span> <span data-ttu-id="34cb8-1413">Обратите внимание, что, если используется эта функция, то подпрограмма обратного вызова должна возвращать состояние NX_WEB_HTTP_CALLBACK_COMPLETED.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1413">Note that if this function is used, the callback routine must return the status of NX_WEB_HTTP_CALLBACK_COMPLETED.</span></span>

<span data-ttu-id="34cb8-1414">Строки header, information и additional_info должны оканчиваться нулевым символом, а длина каждой строки должна соответствовать длине, указанной в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1414">The strings of header, information and additional_info must be NULL-terminated and length of each string matches the length specified in the argument list.</span></span>

<span data-ttu-id="34cb8-1415">Эта служба заменяет *nx_web_http_server_callback_response_send()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1415">This service replaces *nx_web_http_server_callback_response_send*().</span></span> <span data-ttu-id="34cb8-1416">В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1416">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1417">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1417">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1418">**server_ptr**: указатель на блок управления HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1418">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="34cb8-1419">**header**: указатель на строку заголовка ответа</span><span class="sxs-lookup"><span data-stu-id="34cb8-1419">**header** Pointer to the response header string.</span></span>
- <span data-ttu-id="34cb8-1420">**header_length**: длина строки заголовка ответа.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1420">**header_length** Length of the response header string.</span></span>
- <span data-ttu-id="34cb8-1421">**information**: указатель на строку информации.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1421">**information** Pointer to the information string.</span></span>
- <span data-ttu-id="34cb8-1422">**information_length**: длина строки информации.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1422">**Information_length** Length of the information string.</span></span>
- <span data-ttu-id="34cb8-1423">**additional_info**: указатель на строку дополнительной информации.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1423">**additional_info** Pointer to the additional information string.</span></span>
- <span data-ttu-id="34cb8-1424">**additional_info_length**: длина строки дополнительной информации.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1424">**additional_info_length** Length of the additional information string.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1425">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1425">Return Values</span></span>

- <span data-ttu-id="34cb8-1426">**NX_SUCCESS** (0X00): ответ HTTP-сервера успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1426">**NX_SUCCESS** (0x00) Successfully sent HTTP Server response</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1427">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1427">Allowed From</span></span>

<span data-ttu-id="34cb8-1428">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1428">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1429">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1429">Example</span></span>

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

## <a name="nx_web_http_server_content_get"></a><span data-ttu-id="34cb8-1430">nx_web_http_server_content_get</span><span class="sxs-lookup"><span data-stu-id="34cb8-1430">nx_web_http_server_content_get</span></span>

<span data-ttu-id="34cb8-1431">Получение содержимого из запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1431">Get content from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1432">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1432">Prototype</span></span>

```C
UINT nx_web_http_server_content_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="34cb8-1433">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1433">Description</span></span>

<span data-ttu-id="34cb8-1434">Эта служба пытается получить указанный объем содержимого из запроса POST или PUT HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1434">This service attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="34cb8-1435">Ее следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_web_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1435">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1436">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1436">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1437">**server_ptr**: указатель на блок управления HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1437">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="34cb8-1438">**packet_ptr**: указатель на пакет запроса HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="34cb8-1438">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="34cb8-1439">Обратите внимание, что этот пакет не должен быть освобожден обратным вызовом уведомления о запросе.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1439">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="34cb8-1440">**byte_offset**: число байтов для смещения в область содержимого</span><span class="sxs-lookup"><span data-stu-id="34cb8-1440">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="34cb8-1441">**destination_ptr**: указатель на область назначения для содержимого</span><span class="sxs-lookup"><span data-stu-id="34cb8-1441">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="34cb8-1442">**destination_size**: максимальное число байтов, доступных в области назначения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1442">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="34cb8-1443">**actual_size**: указатель на переменную назначения, в качестве значения которой будет задан фактический размер копируемого содержимого.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1443">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1444">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1444">Return Values</span></span>

- <span data-ttu-id="34cb8-1445">**NX_SUCCESS** (0x00): содержимое HTTP-сервера успешно получено.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1445">**NX_SUCCESS** (0x00) Successful HTTP Server content Get</span></span>
- <span data-ttu-id="34cb8-1446">**NX_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1446">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="34cb8-1447">**NX_WEB_HTTP_DATA_END** (0X30007): конец содержимого запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1447">**NX_WEB_HTTP_DATA_END** (0x30007) End of request content</span></span>
- <span data-ttu-id="34cb8-1448">**NX_WEB_HTTP_TIMEOUT** (0x30001): время ожидания HTTP-сервера при получении следующего пакета содержимого.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1448">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Server timeout in getting next packet of content</span></span>
- <span data-ttu-id="34cb8-1449">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1449">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-1450">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1450">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1451">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1451">Allowed From</span></span>

<span data-ttu-id="34cb8-1452">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1452">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1453">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1453">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_get_extended"></a><span data-ttu-id="34cb8-1454">nx_web_http_server_content_get_extended</span><span class="sxs-lookup"><span data-stu-id="34cb8-1454">nx_web_http_server_content_get_extended</span></span>

<span data-ttu-id="34cb8-1455">Получение содержимого из запроса или поддержка содержимого нулевой длины.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1455">Get content from the request/supports zero length Content Length</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1456">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1456">Prototype</span></span>

```C
UINT nx_web_http_server_content_get_extended(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET *packet_ptr,
    ULONG byte_offset,
    CHAR *destination_ptr,
    UINT destination_size,
    UINT *actual_size);
```

### <a name="description"></a><span data-ttu-id="34cb8-1457">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1457">Description</span></span>

<span data-ttu-id="34cb8-1458">Эта служба почти идентична службе *nx_web_http_server_content_get()* . Она пытается получить указанный объем содержимого из запроса POST или PUT HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1458">This service is almost identical to *nx_web_http_server_content_get()*; it attempts to retrieve the specified amount of content from the POST or PUT HTTP Client request.</span></span> <span data-ttu-id="34cb8-1459">Однако она обрабатывает запросы с содержимым нулевой длины (пустые запросы) как допустимые.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1459">However it handles requests with Content Length of zero value (‘empty request’) as a valid request.</span></span> <span data-ttu-id="34cb8-1460">Ее следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_web_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1460">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

<span data-ttu-id="34cb8-1461">Эта служба заменяет *nx_web_http_server_content_get()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1461">This service replaces *nx_web_http_server_content_get*().</span></span> <span data-ttu-id="34cb8-1462">В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1462">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1463">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1463">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1464">**server_ptr**: указатель на блок управления HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1464">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="34cb8-1465">**packet_ptr**: указатель на пакет запроса HTTP-клиента</span><span class="sxs-lookup"><span data-stu-id="34cb8-1465">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="34cb8-1466">Обратите внимание, что этот пакет не должен быть освобожден обратным вызовом уведомления о запросе.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1466">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="34cb8-1467">**byte_offset**: число байтов для смещения в область содержимого</span><span class="sxs-lookup"><span data-stu-id="34cb8-1467">**byte_offset** Number of bytes to offset into the content area.</span></span>
- <span data-ttu-id="34cb8-1468">**destination_ptr**: указатель на область назначения для содержимого</span><span class="sxs-lookup"><span data-stu-id="34cb8-1468">**destination_ptr** Pointer to the destination area for the content.</span></span>
- <span data-ttu-id="34cb8-1469">**destination_size**: максимальное число байтов, доступных в области назначения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1469">**destination_size** Maximum number of bytes available in the destination area.</span></span>
- <span data-ttu-id="34cb8-1470">**actual_size**: указатель на переменную назначения, в качестве значения которой будет задан фактический размер копируемого содержимого.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1470">**actual_size** Pointer to the destination variable that will be set to the actual size of the content copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1471">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1471">Return Values</span></span>

- <span data-ttu-id="34cb8-1472">**NX_SUCCESS** (0x00): содержимое HTTP-запроса успешно получено.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1472">**NX_SUCCESS** (0x00) Successful HTTP content get</span></span>
- <span data-ttu-id="34cb8-1473">**NX_HTTP_ERROR** (0x30000): внутренняя ошибка HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1473">**NX_WEB_HTTP_ERROR** (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="34cb8-1474">**NX_WEB_HTTP_DATA_END** (0X30007): конец содержимого запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1474">**NX_WEB_HTTP_DATA_END** (0x30007) End of request content</span></span>
- <span data-ttu-id="34cb8-1475">**NX_WEB_HTTP_TIMEOUT** (0x30001): время ожидания HTTP-сервера при получении следующего пакета.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1475">**NX_WEB_HTTP_TIMEOUT** (0x30001) HTTP Server timeout in getting next packet</span></span>
- <span data-ttu-id="34cb8-1476">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1476">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-1477">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1477">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1478">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1478">Allowed From</span></span>

<span data-ttu-id="34cb8-1479">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1479">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1480">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1480">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, retrieve up to 100 bytes of content starting at offset
    0. */
status = nx_web_http_server_content_get_extended(&my_server, packet_ptr,
    0, my_buffer, 100, &actual_size);

/* If status is NX_SUCCESS, "my_buffer" contains "actual_size" bytes of
    request content. */
```

## <a name="nx_web_http_server_content_length_get"></a><span data-ttu-id="34cb8-1481">nx_web_http_server_content_length_get</span><span class="sxs-lookup"><span data-stu-id="34cb8-1481">nx_web_http_server_content_length_get</span></span>

<span data-ttu-id="34cb8-1482">Получение длины содержимого в запросе или поддержка содержимого нулевой длины.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1482">Get length of content in the request/supports Content Length of zero value</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1483">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1483">Prototype</span></span>

```C
UINT nx_web_http_server_content_length_get(
    NX_PACKET *packet_ptr,
    UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="34cb8-1484">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1484">Description</span></span>

<span data-ttu-id="34cb8-1485">Эта служба пытается получить длину содержимого HTTP в указанном пакете.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1485">This service attempts to retrieve the HTTP content length in the supplied packet.</span></span> <span data-ttu-id="34cb8-1486">Возвращаемое значение указывает на состояние успешного завершения, а фактическое значение длины возвращается в параметре content_length входного указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1486">The return value indicates successful completion status and the actual length value is returned in the input pointer content_length.</span></span> <span data-ttu-id="34cb8-1487">Если содержимого HTTP нет или длина содержимого равна нулю, эта подпрограмма по-прежнему возвращает состояние выполнения, а указатель ввода content_length указывает на допустимую длину (ноль).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1487">If there is no HTTP content/Content Length = 0, this routine still returns a successful completion status and the content_length input pointer points to a valid length (zero).</span></span> <span data-ttu-id="34cb8-1488">Ее следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_web_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1488">It should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1489">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1489">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1490">**packet_ptr**: указатель на пакет запроса HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1490">**packet_ptr** Pointer to the HTTP Client request packet.</span></span> <span data-ttu-id="34cb8-1491">Обратите внимание, что этот пакет не должен быть освобожден обратным вызовом уведомления о запросе.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1491">Note that this packet must not be released by the request notify callback.</span></span>
- <span data-ttu-id="34cb8-1492">**content_length**: указатель на значение, полученное из поля длины содержимого.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1492">**content_length** Pointer to value retrieved from Content Length field</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1493">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1493">Return Values</span></span>

- <span data-ttu-id="34cb8-1494">**NX_SUCCESS** (0x00): длина содержимого HTTP-сервера успешно получена.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1494">**NX_SUCCESS** (0x00) Successful HTTP Server Content Length Get</span></span>
- <span data-ttu-id="34cb8-1495">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F): недопустимый формат заголовка HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1495">**NX_WEB_HTTP_INCOMPLETE_PUT_ERROR** (0x3000F) Improper HTTP header format</span></span>
- <span data-ttu-id="34cb8-1496">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1496">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1497">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1497">Allowed From</span></span>

<span data-ttu-id="34cb8-1498">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1498">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1499">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1499">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the content length of the HTTP Client request. */

ULONG content_length;
status = nx_web_http_server_content_length_get(packet_ptr, &content_length);

/* If the "status" variable indicates successful completion, the "length"
    Variable contains the length of the HTTP Client request content area. */
```

## <a name="nx_web_http_server_create"></a><span data-ttu-id="34cb8-1500">nx_web_http_server_create</span><span class="sxs-lookup"><span data-stu-id="34cb8-1500">nx_web_http_server_create</span></span>

<span data-ttu-id="34cb8-1501">Создание экземпляра HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1501">Create an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1502">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1502">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="34cb8-1503">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1503">Description</span></span>

<span data-ttu-id="34cb8-1504">Эта служба создает экземпляр HTTP-сервера, который выполняется в контексте собственного потока ThreadX.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1504">This service creates an HTTP Server instance, which runs in the context of its own ThreadX thread.</span></span> <span data-ttu-id="34cb8-1505">Необязательные подпрограммы обратного вызова приложений *authentication_check* и *request_notify* позволяют программному обеспечению приложения управлять основными операциями HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1505">The optional *authentication_check* and *request_notify* application callback routines give the application software control over the basic operations of the HTTP Server.</span></span>

<span data-ttu-id="34cb8-1506">Эта служба используется для создания как HTTP-серверов без шифрования, так и HTTPS-серверов с шифрованием TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1506">This service is used to create both plaintext HTTP servers and TLS-secured HTTPS servers.</span></span> <span data-ttu-id="34cb8-1507">Чтобы включить протокол HTTPS с шифрованием TLS, ознакомьтесь с описанием службы *nx_web_http_server_secure_configure()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1507">To enable HTTPS using TLS, see the service *nx_web_http_server_secure_configure()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1508">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1508">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1509">**http_server_ptr**: указатель на блок управления HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1509">**http_server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="34cb8-1510">**http_server_name**: указатель на имя HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="34cb8-1510">**http_server_name** Pointer to HTTP Server’s name.</span></span>
- <span data-ttu-id="34cb8-1511">**ip_ptr**: указатель на созданный ранее экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1511">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="34cb8-1512">**server_port**: TCP-порт ожидания передачи данных для экземпляра сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1512">**server_port** TCP listening port for server instance.</span></span>
- <span data-ttu-id="34cb8-1513">**media_ptr**: указатель на созданный ранее экземпляр носителя FileX.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1513">**media_ptr** Pointer to previously created FileX media instance.</span></span>
- <span data-ttu-id="34cb8-1514">**stack_ptr**: указатель на область стека потока HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="34cb8-1514">**stack_ptr** Pointer to HTTP Server thread stack area.</span></span>
- <span data-ttu-id="34cb8-1515">**stack_ptr**: указатель на размер стека потока HTTP-сервера</span><span class="sxs-lookup"><span data-stu-id="34cb8-1515">**stack_size** Pointer to HTTP Server thread stack size.</span></span>
- <span data-ttu-id="34cb8-1516">**authentication_check**: указатель функции на подпрограмму проверки подлинности приложения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1516">**authentication_check** Function pointer to application’s authentication checking routine.</span></span> <span data-ttu-id="34cb8-1517">Если параметр указан, эта подпрограмма вызывается для каждого запроса HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1517">If specified, this routine is called for each HTTP Client request.</span></span> <span data-ttu-id="34cb8-1518">Если этот параметр имеет значение NULL, то проверка подлинности выполняться не будет.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1518">If this parameter is NULL, no authentication will be performed.</span></span> <span data-ttu-id="34cb8-1519">Этот параметр является нерекомендуемым.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1519">This parameter is deprecated.</span></span> <span data-ttu-id="34cb8-1520">Вместо этого используйте вызов *nx_web_http_server_authenticate_check_set()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1520">Call *nx_web_http_server_authenticate_check_set*() instead.</span></span>
- <span data-ttu-id="34cb8-1521">**request_notify**: указатель функции на подпрограмму уведомления о запросе приложения.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1521">**request_notify** Function pointer to application’s request notify routine.</span></span> <span data-ttu-id="34cb8-1522">Если параметр указан, подпрограмма вызывается перед обработкой запроса HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1522">If specified, this routine is called prior to the HTTP server processing of the request.</span></span> <span data-ttu-id="34cb8-1523">Это позволяет перенаправлять имя ресурса или обновлять поля в самом ресурсе до завершения запроса HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1523">This allows the resource name to be redirected or fields within a resource to be updated prior to completing the HTTP Client request.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1524">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1524">Return Values</span></span>

- <span data-ttu-id="34cb8-1525">**NX_SUCCESS** (0x00): HTTP-сервер успешно создан.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1525">**NX_SUCCESS** (0x00) Successful HTTP Server create.</span></span>
- <span data-ttu-id="34cb8-1526">NX_PTR_ERROR (0x07): недопустимый указатель на HTTP-сервер, IP-адрес, носитель, стек или пул пакетов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1526">NX_PTR_ERROR (0x07) Invalid HTTP Server, IP, media, stack, or packet pool pointer.</span></span>
- <span data-ttu-id="34cb8-1527">NX_WEB_HTTP_POOL_ERROR (0x30009): полезные данные пакета пула недостаточно велики, чтобы вместить полный HTTP-запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1527">NX_WEB_HTTP_POOL_ERROR (0x30009) Packet payload of pool is not large enough to contain complete HTTP request.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1528">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1528">Allowed From</span></span>

<span data-ttu-id="34cb8-1529">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1529">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1530">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1530">Example</span></span>

```C
/* Create an HTTP Server instance called "my_server." */
status = nx_web_http_server_create(&my_server, "my server", &ip_0,
    NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_authentication_check, my_request_notify);

/* If status equals NX_SUCCESS, the HTTP Server creation was successful. */
```

## <a name="nx_web_http_server_delete"></a><span data-ttu-id="34cb8-1531">nx_web_http_server_delete</span><span class="sxs-lookup"><span data-stu-id="34cb8-1531">nx_web_http_server_delete</span></span>

<span data-ttu-id="34cb8-1532">Удаление экземпляра HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1532">Delete an HTTP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1533">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1533">Prototype</span></span>

```C
UINT nx_web_http_server_delete(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="34cb8-1534">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1534">Description</span></span>

<span data-ttu-id="34cb8-1535">Эта служба удаляет ранее созданный экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1535">This service deletes a previously created HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1536">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1536">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1537">**http_server_ptr**: указатель на блок управления HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1537">**http_server_ptr** Pointer to HTTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1538">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1538">Return Values</span></span>

- <span data-ttu-id="34cb8-1539">**NX_SUCCESS** (0x00) — HTTP-сервер успешно удален.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1539">**NX_SUCCESS** (0x00) Successful HTTP Server delete</span></span>
- <span data-ttu-id="34cb8-1540">NX_PTR_ERROR (0x07) — недопустимый указатель на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1540">NX_PTR_ERROR (0x07) Invalid HTTP Server pointer</span></span>
- <span data-ttu-id="34cb8-1541">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1541">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1542">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1542">Allowed From</span></span>

<span data-ttu-id="34cb8-1543">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1543">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1544">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1544">Example</span></span>

```C
/* Delete the HTTP Server instance called "my_server." */
status = nx_web_http_server_delete(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server delete was successful. */
```

## <a name="nx_web_http_server_get_entity_content"></a><span data-ttu-id="34cb8-1545">nx_web_http_server_get_entity_content</span><span class="sxs-lookup"><span data-stu-id="34cb8-1545">nx_web_http_server_get_entity_content</span></span>

<span data-ttu-id="34cb8-1546">Получение расположения и длины данных сущности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1546">Retrieve the location and length of entity data</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1547">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1547">Prototype</span></span>

```C
UINT nx_web_http_server_get_entity_content(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

### <a name="description"></a><span data-ttu-id="34cb8-1548">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1548">Description</span></span>

<span data-ttu-id="34cb8-1549">Эта служба определяет расположение начала данных в текущем составном объекте в полученных сообщениях клиента, а также длину данных, не включая граничную строку.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1549">This service determines the location of the start of data within the current multipart entity in the received Client messages, and the length of data not including the boundary string.</span></span> <span data-ttu-id="34cb8-1550">HTTP-сервер обновляет собственные смещения, чтобы эту функцию можно было повторно вызывать для той же датаграмме клиента в случае сообщений с несколькими сущностями.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1550">Internally, the HTTP server updates its own offsets so that this function can be called again on the same Client datagram for messages with multiple entities.</span></span> <span data-ttu-id="34cb8-1551">Указатель пакета обновляется до следующего пакета, где сообщением клиента является датаграмма с несколькими пакетами.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1551">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="34cb8-1552">Обратите внимание на то, что для использования этой службы необходимо включить NX_WEB_HTTP_MULTIPART_ENABLE.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1552">Note that NX_WEB_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span> <span data-ttu-id="34cb8-1553">Также обратите внимание, что приложение не должно освобождать пакет, на который указывает packet_pptr.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1553">Also note that the application should not release the packet pointed to by packet_pptr.</span></span> <span data-ttu-id="34cb8-1554">Это выполняет HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1554">This is done internally by the HTTP server.</span></span>

<span data-ttu-id="34cb8-1555">Дополнительные сведения см. в описании *nx_web_http_server_get_entity_header()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1555">See *nx_web_http_server_get_entity_header()* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1556">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1556">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1557">**server_ptr**: указатель на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1557">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="34cb8-1558">**packet_pptr**: указатель на расположение указателя пакета.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1558">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="34cb8-1559">Обратите внимание на то, что приложение не должно освобождать этот пакет.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1559">Note that the application should not release this packet</span></span>
- <span data-ttu-id="34cb8-1560">**available_offset**: указатель на смещение данных сущности от указателя начала пакета.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1560">**available_offset** Pointer to offset of entity data from the packet prepend pointer</span></span>
- <span data-ttu-id="34cb8-1561">**available_length**: указатель на длину данных сущности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1561">**available_length** Pointer to length of entity data</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1562">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1562">Return Values</span></span>

- <span data-ttu-id="34cb8-1563">**NX_SUCCESS** (0x00): размер и расположение содержимого сущности успешно получены.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1563">**NX_SUCCESS** (0x00) Successfully retrieved size and location of entity content</span></span>
- <span data-ttu-id="34cb8-1564">**NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016): содержимое внутренних составных маркеров HTTP-сервера уже найдено.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1564">**NX_WEB_HTTP_BOUNDARY_ALREADY_FOUND** (0x30016) Content for the HTTP server internal multipart markers is already found</span></span>
- <span data-ttu-id="34cb8-1565">NX_HTTP_ERROR (0x30000): внутренняя ошибка HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1565">NX_WEB_HTTP_ERROR (0x30000) HTTP Server internal error</span></span>
- <span data-ttu-id="34cb8-1566">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1566">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1567">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1567">Allowed From</span></span>

<span data-ttu-id="34cb8-1568">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1568">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1569">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1569">Example</span></span>

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

## <a name="nx_web_http_server_get_entity_header"></a><span data-ttu-id="34cb8-1570">nx_web_http_server_get_entity_header</span><span class="sxs-lookup"><span data-stu-id="34cb8-1570">nx_web_http_server_get_entity_header</span></span>

<span data-ttu-id="34cb8-1571">Получение содержимого заголовка сущности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1571">Retrieve the contents of entity header</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1572">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1572">Prototype</span></span>

```C
UINT nx_web_http_server_get_entity_header(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);
```

### <a name="description"></a><span data-ttu-id="34cb8-1573">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1573">Description</span></span>

<span data-ttu-id="34cb8-1574">Эта служба извлекает заголовок сущности в указанный буфер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1574">This service retrieves the entity header into the specified buffer.</span></span> <span data-ttu-id="34cb8-1575">HTTP-сервер внутренне обновляет собственные указатели для поиска следующей составной сущности в датаграмме клиента с несколькими заголовками сущностей.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1575">Internally HTTP Server updates its own pointers to locate the next multipart entity in a Client datagram with multiple entity headers.</span></span> <span data-ttu-id="34cb8-1576">Указатель пакета обновляется до следующего пакета, где сообщением клиента является датаграмма с несколькими пакетами.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1576">The packet pointer is updated to the next packet where the Client message is a multi-packet datagram.</span></span>

<span data-ttu-id="34cb8-1577">Обратите внимание на то, что для использования этой службы необходимо включить NX_WEB_HTTP_MULTIPART_ENABLE.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1577">Note that NX_WEB_HTTP_MULTIPART_ENABLE must be enabled to use this service.</span></span> <span data-ttu-id="34cb8-1578">Также обратите внимание, что приложение не должно освобождать пакет, на который указывает packet_pptr.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1578">Note also that the application should not release the packet pointed to by packet_pptr.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1579">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1579">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1580">**server_ptr**: указатель на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1580">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="34cb8-1581">**packet_pptr**: указатель на расположение указателя пакета.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1581">**packet_pptr** Pointer to location of packet pointer.</span></span> <span data-ttu-id="34cb8-1582">Обратите внимание на то, что приложение не должно освобождать этот пакет.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1582">Note that the application should not release this packet</span></span>
- <span data-ttu-id="34cb8-1583">**entity_header_buffer**: указатель на расположение для хранения заголовка сущности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1583">**entity_header_buffer** Pointer to location to store entity header</span></span>
- <span data-ttu-id="34cb8-1584">**buffer_size**: размер входного буфера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1584">**buffer_size** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1585">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1585">Return Values</span></span>

- <span data-ttu-id="34cb8-1586">**NX_SUCCESS** (0x00): заголовок сущности успешно получен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1586">**NX_SUCCESS** (0x00) Successfully retrieved entity Header</span></span>
- <span data-ttu-id="34cb8-1587">**NX_WEB_HTTP_NOT_FOUND** (0x30006): поле заголовка сущности не найдено.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1587">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Entity header field not found</span></span>
- <span data-ttu-id="34cb8-1588">**NX_WEB_HTTP_TIMEOUT** (0x30001): истекло время ожидания получения следующего пакета для сообщения клиента с несколькими пакетами.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1588">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired to receive next packet for multipacket client message</span></span>
- <span data-ttu-id="34cb8-1589">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1589">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-1590">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1590">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="34cb8-1591">NX_WEB_HTTP_ERROR (0x30000): внутренняя ошибка HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1591">NX_WEB_HTTP_ERROR (0x30000) Internal HTTP error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1592">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1592">Allowed From</span></span>

<span data-ttu-id="34cb8-1593">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1593">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1594">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1594">Example</span></span>

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

## <a name="nx_web_http_server_gmt_callback_set"></a><span data-ttu-id="34cb8-1595">nx_web_http_server_gmt_callback_set</span><span class="sxs-lookup"><span data-stu-id="34cb8-1595">nx_web_http_server_gmt_callback_set</span></span>

<span data-ttu-id="34cb8-1596">Задание обратного вызова для получения даты и времени по Гринвичу.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1596">Set the callback to obtain GMT date and time</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1597">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1597">Prototype</span></span>

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

### <a name="description"></a><span data-ttu-id="34cb8-1598">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1598">Description</span></span>

<span data-ttu-id="34cb8-1599">Эта служба задает обратный вызов для получения даты и времени в формате GMT с помощью ранее созданного HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1599">This service sets the callback to obtain GMT date and time with a previously created HTTP server.</span></span> <span data-ttu-id="34cb8-1600">Эта служба вызывается HTTP-сервером и создает заголовок в ответах HTTP-сервера для клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1600">This service is invoked with the HTTP server is creating a header in HTTP server responses to the Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1601">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1601">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1602">**server_ptr**: указатель на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1602">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="34cb8-1603">**gmt_getv**: указатель на обратный вызов для получения даты и времени по Гринвичу</span><span class="sxs-lookup"><span data-stu-id="34cb8-1603">**gmt_get** Pointer to GMT callback</span></span>
- <span data-ttu-id="34cb8-1604">**date**: указатель на полученную дату.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1604">**date** Pointer to the date retrieved</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1605">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1605">Return Values</span></span>

- <span data-ttu-id="34cb8-1606">**NX_SUCCESS** (0x00) — обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1606">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="34cb8-1607">NX_PTR_ERROR (0x07): недопустимый указатель на пакет или параметр.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1607">NX_PTR_ERROR (0x07) Invalid packet or parameter pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1608">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1608">Allowed From</span></span>

<span data-ttu-id="34cb8-1609">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1609">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1610">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1610">Example</span></span>

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

## <a name="nx_web_http_server_invalid_userpassword_notify_set"></a><span data-ttu-id="34cb8-1611">nx_web_http_server_invalid_userpassword_notify_set</span><span class="sxs-lookup"><span data-stu-id="34cb8-1611">nx_web_http_server_invalid_userpassword_notify_set</span></span>

<span data-ttu-id="34cb8-1612">Задание обратного вызова для обработки недопустимого имени пользователя или пароля.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1612">Set the callback to handle invalid user/password</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1613">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1613">Prototype</span></span>

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource,
        ULONG client_address,
        UINT request_type));
```

### <a name="description"></a><span data-ttu-id="34cb8-1614">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1614">Description</span></span>

<span data-ttu-id="34cb8-1615">Эта служба задает обратный вызов, вызываемый при получении недопустимого имени пользователя и пароля в запросе GET, PUT или DELETE клиента в результате дайджест- или обычной проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1615">This service sets the callback invoked when an invalid username and password is received in a Client get, put or delete request, either by digest or basic authentication.</span></span> <span data-ttu-id="34cb8-1616">HTTP-сервер должен быть создан ранее.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1616">The HTTP server must be previously created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1617">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1617">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1618">**server_ptr**: указатель на HTTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1618">**server_ptr** Pointer to HTTP Server</span></span>
- <span data-ttu-id="34cb8-1619">**invalid_username_password_callback**: указатель на недопустимый обратный вызов имени пользователя или пароля</span><span class="sxs-lookup"><span data-stu-id="34cb8-1619">**invalid_username_password_callback** Pointer to invalid user/pass callback</span></span>
- <span data-ttu-id="34cb8-1620">**resource**: указатель на ресурс, указанный клиентом</span><span class="sxs-lookup"><span data-stu-id="34cb8-1620">**resource** Pointer to the resource specified by the client</span></span>
- <span data-ttu-id="34cb8-1621">**client_address**: адрес клиента</span><span class="sxs-lookup"><span data-stu-id="34cb8-1621">**client_address** Client address</span></span>
- <span data-ttu-id="34cb8-1622">**request_type** указывает тип запроса клиента</span><span class="sxs-lookup"><span data-stu-id="34cb8-1622">**request_type** Indicates client request type.</span></span> <span data-ttu-id="34cb8-1623">Может иметь следующие значения:</span><span class="sxs-lookup"><span data-stu-id="34cb8-1623">May be:</span></span>
  - <span data-ttu-id="34cb8-1624">*NX_WEB_HTTP_SERVER_GET_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="34cb8-1624">*NX_WEB_HTTP_SERVER_GET_REQUEST*</span></span>
  - <span data-ttu-id="34cb8-1625">*NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="34cb8-1625">*NX_WEB_HTTP_SERVER_POST_REQUEST NX_WEB_HTTP_SERVER_HEAD_REQUEST*</span></span>
  - <span data-ttu-id="34cb8-1626">*NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*</span><span class="sxs-lookup"><span data-stu-id="34cb8-1626">*NX_WEB_HTTP_SERVER_PUT_REQUEST NX_WEB_HTTP_SERVER_DELETE_REQUEST*</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1627">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1627">Return Values</span></span>

- <span data-ttu-id="34cb8-1628">**NX_SUCCESS** (0x00) — обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1628">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="34cb8-1629">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1629">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1630">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1630">Allowed From</span></span>

<span data-ttu-id="34cb8-1631">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1631">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1632">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1632">Example</span></span>

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

## <a name="nx_web_http_server_mime_maps_additional_set"></a><span data-ttu-id="34cb8-1633">nx_web_http_server_mime_maps_additional_set</span><span class="sxs-lookup"><span data-stu-id="34cb8-1633">nx_web_http_server_mime_maps_additional_set</span></span>

<span data-ttu-id="34cb8-1634">Задание дополнительных сопоставлений MIME для HTML.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1634">Set additional MIME maps for HTML</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1635">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1635">Prototype</span></span>

```C
UINT nx_web_http_server_mime_maps_additional_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_WEB_HTTP_SERVER_MIME_MAP *mime_maps,
    UINT mime_maps_num);
```

### <a name="description"></a><span data-ttu-id="34cb8-1636">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1636">Description</span></span>

<span data-ttu-id="34cb8-1637">Эта служба позволяет разработчику приложения HTTP добавлять дополнительные типы MIME из типов MIME по умолчанию, предоставляемых сервером NetX Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1637">This service allows the HTTP application developer to add additional MIME types from the default MIME types supplied by the NetX Web HTTP Server.</span></span> <span data-ttu-id="34cb8-1638">Список определенных типов см. в описании *nx_web_http_server_get_type ()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1638">See *nx_web_http_server_get_type()* for list of defined types.</span></span>

<span data-ttu-id="34cb8-1639">Если получен запрос клиента, например запрос GET, HTTP-сервер анализирует запрошенный тип файла из заголовка HTTP с помощью дополнительно заданного сопоставления MIME и, если совпадения не найдены, ищет соответствие с сопоставлением MIME по умолчанию HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1639">When a client request is received, e.g. a GET request, HTTP server parses the requested file type from the HTTP header using preferentially the additional MIME map set and if no match if found, it looks for a match in the default MIME map of the HTTP server.</span></span> <span data-ttu-id="34cb8-1640">Если совпадения не найдены, по умолчанию используется тип MIME "text/plain".</span><span class="sxs-lookup"><span data-stu-id="34cb8-1640">If no match is found, the MIME type defaults to "text/plain".</span></span>

<span data-ttu-id="34cb8-1641">Если функция уведомления о запросе зарегистрирована на HTTP-сервере, обратный вызов уведомления о запросе может вызвать *nx_web_http_server_type_get_extended* для анализа типа файла.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1641">If the request notify function is registered with the HTTP server, the request notify callback can call *nx_web_http_server_type_get_extended()* to parse the file type.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1642">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1642">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1643">**server_ptr**: указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1643">**server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="34cb8-1644">**mime_maps**: указатель на массив сопоставлений MIME</span><span class="sxs-lookup"><span data-stu-id="34cb8-1644">**mime_maps** Pointer to a MIME map array</span></span>
- <span data-ttu-id="34cb8-1645">**mime_map_num**: число сопоставлений MIME в массиве.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1645">**mime_map_num** Number of MIME maps in array</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1646">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1646">Return Values</span></span>

- <span data-ttu-id="34cb8-1647">**NX_SUCCESS** (0x00) — сопоставление MIME HTTP-сервера успешно задано.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1647">**NX_SUCCESS** (0x00) Successful HTTP Server MIME map set</span></span>
- <span data-ttu-id="34cb8-1648">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1648">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1649">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1649">Allowed From</span></span>

<span data-ttu-id="34cb8-1650">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1650">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1651">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1651">Example</span></span>

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

## <a name="nx_web_http_server_response_packet_allocate"></a><span data-ttu-id="34cb8-1652">nx_web_http_server_response_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="34cb8-1652">nx_web_http_server_response_packet_allocate</span></span>

<span data-ttu-id="34cb8-1653">Выделение пакета HTTP(S).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1653">Allocate an HTTP(S) packet</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1654">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1654">Prototype</span></span>

```C
UINT nx_web_http_server_response_packet_allocate(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="34cb8-1655">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1655">Description</span></span>

<span data-ttu-id="34cb8-1656">Эта служба пытается выделить пакет для HTTP(S)-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1656">This service attempts to allocates a packet for the HTTP(S) server.</span></span>

<span data-ttu-id="34cb8-1657">Обратите внимание на то, что в случае **сбоя** последующего вызова API NetX или HTTP-сервера, использующего этот пакет в качестве входных данных, например nx_packet_data_append или \*\*nx_web_http_server_callback_packet_send, за освобождение этого пакета отвечает приложение.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1657">Note that if a subsequent NetX or HTTP Server API using this packet as input **fails**, such as nx_packet_data_append or \*\*nx_web_http_server_callback_packet_send, the application is responsible for releasing the packet.</span></span> **

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1658">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1658">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1659">**server_ptr**: указатель на блок управления HTTP-сервером.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1659">**server_ptr** Pointer to HTTP Server control block.</span></span>
- <span data-ttu-id="34cb8-1660">**packet_ptr**: указатель на выделенный пакет.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1660">**packet_ptr** Pointer to allocated packet.</span></span>
- <span data-ttu-id="34cb8-1661">**wait_option**: определяет время ожидания в тактах, если в пуле пакетов нет доступных пакетов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1661">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="34cb8-1662">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="34cb8-1662">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="34cb8-1663">**NX_NO_WAIT** (0X00000000): выбор NX_NO_WAIT приведет к немедленному возвращению вызывающего потока, если запрос не может быть выполнен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1663">**NX_NO_WAIT** (0x00000000) Selecting NX_NO_WAIT causes the calling thread to return immediately if the request cannot be fulfilled.</span></span>
  - <span data-ttu-id="34cb8-1664">**NX_WAIT_FOREVER** (0xFFFFFFFF): если указан параметр NX_WAIT_FOREVER, то вызывающий поток будет приостановлен на неограниченное время, пока HTTP-сервер не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1664">**NX_WAIT_FOREVER** (0xFFFFFFFF) Selecting NX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the HTTP Server responds to the request.</span></span>
  - <span data-ttu-id="34cb8-1665">**значение времени ожидания** (0x00000001–0xFFFFFFFE): если указано числовое значение (0x1–0xFFFFFFFE), то оно задает максимальное число тактов таймера для приостановки работы при ожидании ответа HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1665">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (0x1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the HTTP Server response.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1666">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1666">Return Values</span></span>

- <span data-ttu-id="34cb8-1667">**NX_SUCCESS** (0x00): пакет выделен успешно.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1667">**NX_SUCCESS** (0x00) Successful packet allocate</span></span>
- <span data-ttu-id="34cb8-1668">**NX_NO_PACKET** (0x01): нет доступных пакетов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1668">**NX_NO_PACKET** (0x01) No packet available</span></span>
- <span data-ttu-id="34cb8-1669">**NX_WAIT_ABORTED** (0x1A): запрошенная приостановка прервана вызовом *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1669">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="34cb8-1670">**NX_INVALID_PARAMETERS** (0x4D): размер пакета не поддерживается протоколом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1670">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="34cb8-1671">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1671">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-1672">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1672">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1673">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1673">Allowed From</span></span>

<span data-ttu-id="34cb8-1674">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1674">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1675">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1675">Example</span></span>

```C
/* Allocate a packet for HTTP(S) Server and suspend for a maximum of 5 timer
    ticks if the pool is empty. */
status = nx_web_http_server_response_packet_allocate(&my_client, &packet_ptr, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
    variable packet_ptr. */
```

## <a name="nx_web_http_server_packet_content_find"></a><span data-ttu-id="34cb8-1676">nx_web_http_server_packet_content_find</span><span class="sxs-lookup"><span data-stu-id="34cb8-1676">nx_web_http_server_packet_content_find</span></span>

<span data-ttu-id="34cb8-1677">Извлечение длины содержимого и установка указателя на начало данных.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1677">Extract content length and set pointer to start of data</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1678">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1678">Prototype</span></span>

```C
UINT nx_web_http_server_packet_content_find(
    NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr,
    UINT *content_length);
```

### <a name="description"></a><span data-ttu-id="34cb8-1679">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1679">Description</span></span>

<span data-ttu-id="34cb8-1680">Эта служба извлекает длину содержимого из заголовка HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1680">This service extracts the content length from the HTTP header.</span></span> <span data-ttu-id="34cb8-1681">Она также обновляет указанный пакет следующим образом: перед указателем начала пакета (начало расположения буфера пакета для записи) задается содержимое HTTP (данные), только что переданное заголовком HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1681">It also updates the supplied packet as follows: the packet prepend pointer (start of location of packet buffer to write to) is set to the HTTP content (data) just passed the HTTP header.</span></span>

<span data-ttu-id="34cb8-1682">Если в текущем пакете не найдено начало содержимого, функция ожидает получения следующего пакета с помощью параметра ожидания NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1682">If the beginning of content is not found in the current packet, the function waits for the next packet to be received using the NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE wait option.</span></span>

<span data-ttu-id="34cb8-1683">Обратите внимание, что эту службу не следует вызывать перед вызовом *nx_web_http_server_get_entity_header()* , так как она изменяет зависящий от пакета указатель в начале после заголовка сущности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1683">Note this should not be called before calling *nx_web_http_server_get_entity_header()* because it modifies the packet prepend pointer past the entity header.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1684">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1684">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1685">**server_ptr**: указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1685">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="34cb8-1686">**packet_ptr**: указатель на указатель пакета для возврата пакета с обновленным указателем начала</span><span class="sxs-lookup"><span data-stu-id="34cb8-1686">**packet_ptr** Pointer to packet pointer for returning the packet with updated prepend pointer</span></span>
- <span data-ttu-id="34cb8-1687">**content_length**: указатель на извлеченный параметр content_length.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1687">**content_length** Pointer to extracted content_length</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1688">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1688">Return Values</span></span>

- <span data-ttu-id="34cb8-1689">**NX_SUCCESS** (0x00): длина содержимого HTTP обнаружена, и пакет успешно обновлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1689">**NX_SUCCESS** (0x00) HTTP content length found and packet successfully updated</span></span>
- <span data-ttu-id="34cb8-1690">**NX_HTTP_TIMEOUT** (0x30001): истекло время ожидания следующего пакета.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1690">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired waiting on next Packet</span></span>
- <span data-ttu-id="34cb8-1691">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1691">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1692">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1692">Allowed From</span></span>

<span data-ttu-id="34cb8-1693">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1693">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1694">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1694">Example</span></span>

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

## <a name="nx_web_http_server_packet_get"></a><span data-ttu-id="34cb8-1695">nx_web_http_server_packet_get</span><span class="sxs-lookup"><span data-stu-id="34cb8-1695">nx_web_http_server_packet_get</span></span>

<span data-ttu-id="34cb8-1696">Получение следующего пакета HTTP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1696">Receive the next HTTP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1697">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1697">Prototype</span></span>

```C
UINT nx_web_http_server_packet_get(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_ptr);
```

### <a name="description"></a><span data-ttu-id="34cb8-1698">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1698">Description</span></span>

<span data-ttu-id="34cb8-1699">Эта служба возвращает следующий пакет, полученный через сокет HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1699">This service returns the next packet received on the HTTP server socket.</span></span> <span data-ttu-id="34cb8-1700">Для получения пакета используется параметр ожидания NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1700">The wait option to receive a packet is NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE.</span></span>

<span data-ttu-id="34cb8-1701">Обратите внимание на то, что в случае успешного выполнения именно приложение отвечает за освобождение пакета.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1701">Note that if successful the application is responsible for releasing the packet.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1702">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1702">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1703">**server_ptr**: указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1703">**server_ptr** Pointer to HTTP server instance</span></span>
- <span data-ttu-id="34cb8-1704">**packet_ptr**: указатель на полученный пакет.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1704">**packet_ptr** Pointer to received packet</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1705">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1705">Return Values</span></span>

- <span data-ttu-id="34cb8-1706">**NX_SUCCESS** (0x00): следующий пакет HTTP успешно получен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1706">**NX_SUCCESS** (0x00) Successfully received next HTTP packet</span></span>
- <span data-ttu-id="34cb8-1707">**NX_HTTP_TIMEOUT** (0x30001): истекло время ожидания следующего пакета.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1707">**NX_WEB_HTTP_TIMEOUT** (0x30001) Time expired waiting on next Packet</span></span>
- <span data-ttu-id="34cb8-1708">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1708">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1709">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1709">Allowed From</span></span>

<span data-ttu-id="34cb8-1710">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1710">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1711">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1711">Example</span></span>

```C
/* The HTTP server pointed to by server_ptr is previously created and started. */
UINT content_length;
NX_PACKET *recv_packet_ptr;

status = nx_web_http_server_packet_get(server_ptr, &recv_packet_ptr);

/* If status equals NX_SUCCESS, a Client packet is obtained. */
```

## <a name="nx_web_http_server_param_get"></a><span data-ttu-id="34cb8-1712">nx_web_http_server_param_get</span><span class="sxs-lookup"><span data-stu-id="34cb8-1712">nx_web_http_server_param_get</span></span>

<span data-ttu-id="34cb8-1713">Получение параметра из запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1713">Get parameter from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1714">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1714">Prototype</span></span>

```C
UINT nx_web_http_server_param_get(NX_PACKET *packet_ptr,
    UINT param_number, CHAR *param_ptr,
    UINT *param_size, UINT max_param_size);
```

### <a name="description"></a><span data-ttu-id="34cb8-1715">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1715">Description</span></span>

<span data-ttu-id="34cb8-1716">Эта служба пытается получить указанный параметр URL-адреса HTTP из указанного пакета запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1716">This service attempts to retrieve the specified HTTP URL parameter in the supplied request packet.</span></span> <span data-ttu-id="34cb8-1717">Если запрашиваемый параметр HTTP отсутствует, подпрограмма возвращает состояние NX_WEB_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1717">If the requested HTTP parameter is not present, this routine returns a status of NX_WEB_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="34cb8-1718">Эту подпрограмму следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_web_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1718">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1719">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1719">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1720">**packet_ptr**: указатель на пакет запроса HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1720">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="34cb8-1721">Обратите внимание, что приложение не должно освобождать этот пакет.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1721">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="34cb8-1722">**param_number**: логический номер параметра, начинающийся с нуля, слева направо в списке параметров</span><span class="sxs-lookup"><span data-stu-id="34cb8-1722">**param_number** Logical number of the parameter starting at zero, from left to right in the parameter list.</span></span>
- <span data-ttu-id="34cb8-1723">**param_ptr**: область назначения для копирования параметра.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1723">**param_ptr** Destination area to copy the parameter.</span></span>
- <span data-ttu-id="34cb8-1724">**param_size**: возвращает общий размер данных параметра (в байтах).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1724">**param_size** Return the total parameter data length (in bytes).</span></span>
- <span data-ttu-id="34cb8-1725">**max_param_size**: максимальный размер области назначения параметра.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1725">**max_param_size** Maximum size of the parameter destination area.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1726">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1726">Return Values</span></span>

- <span data-ttu-id="34cb8-1727">**NX_SUCCESS** (0x00): параметр HTTP-сервера успешно получен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1727">**NX_SUCCESS** (0x00) Successful HTTP Server parameter get</span></span>
- <span data-ttu-id="34cb8-1728">**NX_WEB_HTTP_NOT_FOUND** (0x30006): указанный параметр не найден.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1728">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Specified parameter not found</span></span>
- <span data-ttu-id="34cb8-1729">**NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015): неправильное завершение параметра запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1729">**NX_WEB_HTTP_IMPROPERLY_TERMINATED_PARAM** (0x30015) Request parameter not properly terminated</span></span>
- <span data-ttu-id="34cb8-1730">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1730">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-1731">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1731">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1732">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1732">Allowed From</span></span>

<span data-ttu-id="34cb8-1733">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1734">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1734">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first parameter of the HTTP Client request. */

status = nx_web_http_server_param_get(request_packet_ptr, 0, param_destination,
    &param_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first parameter can be found
    in "param_destination" and the size of that string can be found
    in the variable "param_size." */
```

## <a name="nx_web_http_server_query_get"></a><span data-ttu-id="34cb8-1735">nx_web_http_server_query_get</span><span class="sxs-lookup"><span data-stu-id="34cb8-1735">nx_web_http_server_query_get</span></span>

<span data-ttu-id="34cb8-1736">Получение запроса из запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1736">Get query from the request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1737">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1737">Prototype</span></span>

```C
UINT nx_web_http_server_query_get(NX_PACKET *packet_ptr,
    UINT query_number,
    CHAR *query_ptr,
    CHAR *query_size,
    UINT max_query_size);
```

### <a name="description"></a><span data-ttu-id="34cb8-1738">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1738">Description</span></span>

<span data-ttu-id="34cb8-1739">Эта служба пытается получить указанный HTTP-запрос URL-адреса из указанного пакета запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1739">This service attempts to retrieve the specified HTTP URL query in the supplied request packet.</span></span> <span data-ttu-id="34cb8-1740">Если запрашиваемый HTTP-запрос отсутствует, подпрограмма возвращает состояние NX_WEB_HTTP_NOT_FOUND.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1740">If the requested HTTP query is not present, this routine returns a status of NX_WEB_HTTP_NOT_FOUND.</span></span> <span data-ttu-id="34cb8-1741">Эту подпрограмму следует вызывать из обратного вызова уведомления о запросе приложения, указанного во время создания HTTP-сервера (*nx_web_http_server_create()* ).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1741">This routine should be called from the application’s request notify callback specified during HTTP Server creation (*nx_web_http_server_create()*).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1742">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1742">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1743">**packet_ptr**: указатель на пакет запроса HTTP-клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1743">**packet_ptr** Pointer to HTTP Client request packet.</span></span> <span data-ttu-id="34cb8-1744">Обратите внимание, что приложение не должно освобождать этот пакет.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1744">Note that the application should not release this packet.</span></span>
- <span data-ttu-id="34cb8-1745">**query_number**: логический номер параметра, начинающийся с нуля, слева направо в списке запросов</span><span class="sxs-lookup"><span data-stu-id="34cb8-1745">**query_number** Logical number of the parameter starting at zero, from left to right in the query list.</span></span>
- <span data-ttu-id="34cb8-1746">**query_ptr**: область назначения для копирования запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1746">**query_ptr** Destination area to copy the query.</span></span>
- <span data-ttu-id="34cb8-1747">**query_size**: размер возвращаемых данных запроса (в байтах).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1747">**query_size** Return query data size (in bytes).</span></span>
- <span data-ttu-id="34cb8-1748">**max_query_size**: максимальный размер области назначения запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1748">**max_query_size** Maximum size of the query destination</span></span>

<span data-ttu-id="34cb8-1749">.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1749">area.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1750">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1750">Return Values</span></span>

- <span data-ttu-id="34cb8-1751">**NX_SUCCESS** (0x00): запрос HTTP-сервера успешно получен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1751">**NX_SUCCESS** (0x00) Successful HTTP Server query get</span></span>
- <span data-ttu-id="34cb8-1752">**NX_WEB_HTTP_FAILED** (0x30002): слишком маленький размер запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1752">**NX_WEB_HTTP_FAILED** (0x30002) Query size too small.</span></span>
- <span data-ttu-id="34cb8-1753">**NX_WEB_HTTP_NOT_FOUND** (0x30006): указанный запрос не найден.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1753">**NX_WEB_HTTP_NOT_FOUND** (0x30006) Specified query not found</span></span>
- <span data-ttu-id="34cb8-1754">**NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013): запрос отсутствует в запросе клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1754">**NX_WEB_HTTP_NO_QUERY_PARSED** (0x30013) No query in Client request</span></span>
- <span data-ttu-id="34cb8-1755">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1755">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-1756">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1756">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1757">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1757">Allowed From</span></span>

<span data-ttu-id="34cb8-1758">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1758">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1759">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1759">Example</span></span>

```C
/* Assuming we are in the application’s request notify callback
    routine, get the first query of the HTTP Client request. */

status = nx_web_http_server_query_get(request_packet_ptr, 0,
    query_destination, &query_size, 30);

/* If status equals NX_SUCCESS, the NULL-terminated first query can be found
    in "query_destination" and the length of that string can be found in the
    variable "query_size". */
```

## <a name="nx_web_http_server_response_chunked_set"></a><span data-ttu-id="34cb8-1760">nx_web_http_server_response_chunked_set</span><span class="sxs-lookup"><span data-stu-id="34cb8-1760">nx_web_http_server_response_chunked_set</span></span>

<span data-ttu-id="34cb8-1761">Настройка поблочной передачи для ответа HTTP(S).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1761">Set chunked transfer for HTTP(S) response</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1762">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1762">Prototype</span></span>

```C
UINT nx_web_http_server_response_chunked_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="34cb8-1763">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1763">Description</span></span>

<span data-ttu-id="34cb8-1764">Эта служба использует поблочное кодирование для передачи клиенту пользовательского пакета данных ответа HTTP(S), созданного с помощью службы *nx_web_http_server_response_packet_allocate()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1764">This service uses chunked transfer coding to send a custom HTTP(S) response data packet created with *nx_web_http_server_response_packet_allocate*() to the client.</span></span>

> [!NOTE]
> <span data-ttu-id="34cb8-1765">Если приложение использует поблочное кодирование для передачи пакета данных ответа, то оно должно вызвать эту службу после вызова службы *nx_web_http_server_response_packet_allocate()* и перед вызовом службы *nx_web_http_server_callback_packet_send()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1765">If the application uses chunked transfer coding to send a response data packet, it must call this service after calling *nx_web_http_server_response_packet_allocate*(), and before calling *nx_web_http_server_callback_packet_send*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1766">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1766">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1767">**client_ptr**: указатель на блок управления HTTP-клиентом.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1767">**client_ptr** Pointer to HTTP Client control block.</span></span>
- <span data-ttu-id="34cb8-1768">**chunk_size**: размер блока данных в октетах.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1768">**chunk_size** Size of the chunk-data in octets.</span></span>
- <span data-ttu-id="34cb8-1769">**packet_ptr**: указатель на пакет данных HTTP(S)-запроса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1769">**packet_ptr** HTTP(S) request data packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1770">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1770">Return Values</span></span>

- <span data-ttu-id="34cb8-1771">**NX_SUCCESS** (0X00): режим поблочной передачи успешно задан.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1771">**NX_SUCCESS** (0x00) Successful set chunked.</span></span>
- <span data-ttu-id="34cb8-1772">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1772">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1773">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1773">Allowed From</span></span>

<span data-ttu-id="34cb8-1774">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1774">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1775">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1775">Example</span></span>

```C
/* Generate HTTP header. */
nx_web_http_server_callback_generate_response_header(server_ptr,
    &response_pkt, NX_WEB_HTTP_STATUS_OK, 0, "text/html",
    "Transfer-Encoding: chunked\r\n");

/* Create a new data packet response on the HTTP(S) Server instance. */
nx_web_http_server_response_packet_allocate(&my_server, &my_packet, NX_WAIT_FOREVER);

/* Set the chunked transfer. */
status = nx_web_http_server_response_chunked_set(&my_server, 128, my_packet)

/* At this point, user can fill the data into my_packet. */
nx_packet_data_append(my_packet, data_ptr, data_size,
    packet_pool, NX_WAIT_FOREVER);

/* Send data packet response to client. */
nx_web_http_server_callback_packet_send(&my_server, my_packet);
```

## <a name="nx_web_http_server_secure_configure"></a><span data-ttu-id="34cb8-1776">nx_web_http_server_secure_configure</span><span class="sxs-lookup"><span data-stu-id="34cb8-1776">nx_web_http_server_secure_configure</span></span>

<span data-ttu-id="34cb8-1777">Настройка шифрования TLS на HTTP-сервере для использования защищенного протокола HTTPS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1777">Configure an HTTP Server to use TLS for secure HTTPS</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1778">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1778">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="34cb8-1779">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1779">Description</span></span>

<span data-ttu-id="34cb8-1780">Эта служба настраивает шифрование TLS на созданном ранее экземпляре сервера NetX Web HTTP для безопасного обмена данными по протоколу HTTPS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1780">This service configures a previously created NetX Web HTTP server instance to use TLS for secure HTTPS communications.</span></span> <span data-ttu-id="34cb8-1781">Используются параметры для настройки всех возможных сеансов TLS с одинаковым состоянием, чтобы обеспечить согласованное поведение всех входящих HTTPS-клиентов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1781">The parameters are used to configure all the possible TLS sessions with identical state so that each incoming HTTPS Client experiences consistent behavior.</span></span> <span data-ttu-id="34cb8-1782">Количеством сеансов TLS управляет макрос NX_WEB_HTTP_SESSION_MAX.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1782">The number of TLS sessions is controlled using the macro NX_WEB_HTTP_SESSION_MAX.</span></span>

<span data-ttu-id="34cb8-1783">Таблица подпрограмм шифрования (таблица комплектов шифров) является общей для всех сеансов TLS, так как она содержит только указатели функций.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1783">The cryptographic routine table (ciphersuite table) is shared between all TLS sessions as it just contains function pointers.</span></span>

<span data-ttu-id="34cb8-1784">Буферы повторной сборки метаданных и пакетов равномерно распределяются между всеми сеансами TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1784">The metadata and packet reassembly buffers are each divided equally between all TLS sessions.</span></span> <span data-ttu-id="34cb8-1785">Если размер буфера не делится нацело на число сеансов, то полученный остаток не используется.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1785">If the buffer size is not evenly divisible by the number of sessions the remainder will be unused.</span></span>

<span data-ttu-id="34cb8-1786">Переданный сертификат удостоверения используется всеми сеансами.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1786">The passed-in identity certificate is used by all sessions.</span></span> <span data-ttu-id="34cb8-1787">Во время операции TLS сертификат удостоверения сервера только считывается, поэтому его не требуется копировать для каждого сеанса.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1787">During TLS operation the server identity certificate is only read from so copies are not needed for each session.</span></span>

<span data-ttu-id="34cb8-1788">Доверенные сертификаты добавляются в каждый сеанс TLS на HTTPS-сервере.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1788">The trusted certificates are added to each TLS session in the HTTPS Server.</span></span> <span data-ttu-id="34cb8-1789">Они используются для проверки подлинности на основе сертификата клиента, которая автоматически включается, когда предоставляется удаленное хранилище сертификатов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1789">These are used for Client certificate authentication which is automatically enabled when remote certificate space is provided.</span></span>

<span data-ttu-id="34cb8-1790">Удаленный массив и буфер сертификатов по умолчанию являются общими для всех сеансов TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1790">The remote certificate array and buffer is shared by default between all TLS sessions.</span></span> <span data-ttu-id="34cb8-1791">Удаленные сертификаты используются для проверки подлинности на основе сертификата клиента, которая автоматически включается, когда число удаленных сертификатов не равно нулю.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1791">The remote certificates are used for Client certificate authentication which is automatically enabled when the remote certificate count is nonzero.</span></span> <span data-ttu-id="34cb8-1792">Ввиду совместного использования буфера некоторые сеансы могут блокироваться во время проверки сертификата.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1792">Due to the buffer being shared some sessions may block during certificate validation.</span></span>

<span data-ttu-id="34cb8-1793">Чтобы отключить проверку подлинности на основе сертификата клиента, передайте значение NX_NULL для параметра remote_certificates и значение 0 для параметра remote_certs_num.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1793">To disable client certificate authentication, pass NX_NULL for the remote_certificates parameter and a value of 0 for the remote_certs_num parameter.</span></span>

<span data-ttu-id="34cb8-1794">Возвращаемые значения будут содержать все коды ошибок TLS, полученные в результате проблем в конфигурации сеансов TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1794">Return values will include any TLS error codes resulting from issues in the configuration of the TLS sessions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1795">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1795">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1796">**http_server_ptr**: указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1796">**http_server_ptr** Pointer to HTTP Server instance.</span></span>
- <span data-ttu-id="34cb8-1797">**crypto_table**: указатель на таблицу комплектов шифров TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1797">**crypto_table** Pointer to TLS ciphersuite table.</span></span>
- <span data-ttu-id="34cb8-1798">**metadata_buffer**: указатель на буфер криптографических метаданных.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1798">**metadata_buffer** Pointer to cryptographic metadata buffer.</span></span>
- <span data-ttu-id="34cb8-1799">**metadata_size**: размер буфера криптографических метаданных.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1799">**metadata_size** Size of cryptographic metadata buffer.</span></span>
- <span data-ttu-id="34cb8-1800">**packet_buffer**: буфер повторной сборки пакетов TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1800">**packet_buffer** TLS packet reassembly buffer.</span></span>
- <span data-ttu-id="34cb8-1801">**packet_buffer**: размер буфера пакетов TLS, он должен быть равен <требуемый размер буфера TLS> \* NX_WEB_HTTP_SESSION_MAX.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1801">**packet_buffer** Size of TLS packet buffer – should be equal to (<desired TLS buffer size\* NX_WEB_HTTP_SESSION_MAX).</span></span>
- <span data-ttu-id="34cb8-1802">**identity_certificate**: сертификат удостоверения сервера TLS, который будет использоваться для всех сеансов HTTPS-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1802">**identity_certificate** TLS server identity certificate – will be used for all HTTPS server sessions.</span></span>
- <span data-ttu-id="34cb8-1803">**trusted_certificates**: указатель на массив объектов NX_SECURE_X509_CERT, используемый для проверки входящих сертификатов клиента, если проверка подлинности на основе сертификата клиента включена путем передачи ненулевого значения для параметра *remote_certs_num*.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1803">**trusted_certificates** Pointer to array of NX_SECURE_X509_CERT objects, used to validate incoming client certificates if client certificate authentication is enabled by passing a non-zero value for the *remote_certs_num* parameter.</span></span>
- <span data-ttu-id="34cb8-1804">**trusted_certs_num**: количество доверенных сертификатов в массиве *trusted_certificates*.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1804">**trusted_certs_num** Number of trusted certificates in the *trusted_certificates* array.</span></span>
- <span data-ttu-id="34cb8-1805">**remote_certificates**: указатель на массив объектов NX_SECURE_X509_CERT, используемых для входящих сертификатов клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1805">**remote_certificates** Pointer to array of NX_SECURE_X509_CERT objects, used for incoming client certificates.</span></span>
- <span data-ttu-id="34cb8-1806">**remote_certs_num**: число удаленных сертификатов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1806">**remote_certs_num** Number of remote certificates.</span></span> <span data-ttu-id="34cb8-1807">Должно быть равно максимальному числу ожидаемых сертификатов от клиентов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1807">Should be the maximum number of expected certificates from clients.</span></span> <span data-ttu-id="34cb8-1808">Проверка подлинности на основе сертификата клиента включается автоматически, если это значение не равно нулю.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1808">Client certificate authentication is enabled automatically when this is non-zero.</span></span>
- <span data-ttu-id="34cb8-1809">**remote_certificate_buffer**: буфер для хранения входящих удаленных сертификатов от клиентов, если включена проверка подлинности на основе сертификата клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1809">**remote_certificate_buffer** Buffer to contain incoming remote certificates from clients if client certificate authentication is enabled.</span></span> <span data-ttu-id="34cb8-1810">remote_cert_buffer_size: размер буфера удаленных сертификатов.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1810">remote_cert_buffer_size Size of remote certificates buffer.</span></span> <span data-ttu-id="34cb8-1811">Должен быть равен <максимальный ожидаемый размер сертификата> \* remote_certs_num.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1811">Should be equal to (<maximum expected certificate size \* remote_certs_num).</span></span>


### <a name="return-values"></a><span data-ttu-id="34cb8-1812">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1812">Return Values</span></span>

- <span data-ttu-id="34cb8-1813">**NX_SUCCESS** (0x00) — сеанс TLS успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1813">**NX_SUCCESS** (0x00) Successful initialization of the TLS session.</span></span>
- <span data-ttu-id="34cb8-1814">**NX_NOT_CONNECTED** (0x38): базовый сокет TCP больше не подключен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1814">**NX_NOT_CONNECTED** (0x38) The underlying TCP socket is no longer connected.</span></span>
- <span data-ttu-id="34cb8-1815">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102): получен неправильный тип сообщения TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1815">**NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) A received TLS message type is incorrect.</span></span>
- <span data-ttu-id="34cb8-1816">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106): шифр, предоставленный удаленным узлом, не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1816">**NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) A cipher provided by the remote host is not supported.</span></span>
- <span data-ttu-id="34cb8-1817">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107): не удалось обработать сообщение во время подтверждения TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1817">**NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) Message processing during the TLS handshake has failed.</span></span>
- <span data-ttu-id="34cb8-1818">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0X108): не удалось проверить хэш MAC во входящем сообщении.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1818">**NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) An incoming message failed a  hash MAC check.</span></span>
- <span data-ttu-id="34cb8-1819">**NX_SECURE_TLS_TCP_SEND_FAILED** (0x109): не удалось отправить данные через базовый сокет TCP.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1819">**NX_SECURE_TLS_TCP_SEND_FAILE** (0x109) An underlying TCP socket send failed.</span></span>
- <span data-ttu-id="34cb8-1820">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A): входящее сообщение содержало недопустимое поле длины.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1820">**NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) An incoming message had an invalid length field.</span></span>
- <span data-ttu-id="34cb8-1821">**NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B): неправильное входящее сообщение ChangeCipherSpec.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1821">**NX_SECURE_TLS_BAD_CIPHERSPE** (0x10B) An incoming ChangeCipherSpec message was incorrect.</span></span>
- <span data-ttu-id="34cb8-1822">**NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C): входящий сертификат TLS невозможно использовать для идентификации удаленного сервера TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1822">**NX_SECURE_TLS_INVALID_SERVER_CER** (0x10C) An incoming TLS certificate is unusable for identifying the remote TLS server.</span></span>
- <span data-ttu-id="34cb8-1823">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D): шифр с открытым ключом, предоставленный удаленным узлом, не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1823">**NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) The public-key cipher provided by the remote host is unsupported.</span></span>
- <span data-ttu-id="34cb8-1824">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0X10E): на удаленном узле нет ни одного комплекта шифров, поддерживаемого стеком NetX Secure TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1824">**NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) The remote host has indicated no ciphersuites that are supported by the NetX Secure TLS stack.</span></span>
- <span data-ttu-id="34cb8-1825">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F): в заголовке полученного сообщения TLS указана неизвестная версия TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1825">**NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) A received TLS message had an unknown TLS version in its header.</span></span>
- <span data-ttu-id="34cb8-1826">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110): в заголовке полученного сообщения TLS указана неподдерживаемая версия TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1826">**NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) A received TLS message had a known but unsupported TLS version in its header.</span></span>
- <span data-ttu-id="34cb8-1827">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111): не удалось выделить внутренний пакет TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1827">**NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) An internal TLS packet allocation failed.</span></span>
- <span data-ttu-id="34cb8-1828">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112): удаленный узел предоставил недопустимый сертификат.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1828">**NX_SECURE_TLS_INVALID_CERTIFICATE** (0x112) The remote host provided an invalid certificate.</span></span>
- <span data-ttu-id="34cb8-1829">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114): удаленный узел отправил оповещение об ошибке и завершает сеанс TLS.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1829">**NX_SECURE_TLS_ALERT_RECEIVED** (0x114) The remote host sent an alert indicating an error and ending the TLS session.</span></span>
- <span data-ttu-id="34cb8-1830">**NX_PTR_ERROR** (0x07): попытка использовать недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1830">**NX_PTR_ERROR** (0x07) Tried to use an invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1831">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1831">Allowed From</span></span>

<span data-ttu-id="34cb8-1832">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1832">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1833">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1833">Example</span></span>

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

## <a name="nx_web_http_server_start"></a><span data-ttu-id="34cb8-1834">nx_web_http_server_start</span><span class="sxs-lookup"><span data-stu-id="34cb8-1834">nx_web_http_server_start</span></span>

<span data-ttu-id="34cb8-1835">Запуск HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1835">Start the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1836">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1836">Prototype</span></span>

```C
UINT nx_web_http_server_start(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="34cb8-1837">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1837">Description</span></span>

<span data-ttu-id="34cb8-1838">Эта служба запускает созданный ранее экземпляр HTTP или HTTPS-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1838">This service starts a previously created HTTP or HTTPS Server instance.</span></span>

<span data-ttu-id="34cb8-1839">HTTPS-серверы используют те же API, что и HTTP-серверы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1839">HTTPS servers share the same API as HTTP.</span></span> <span data-ttu-id="34cb8-1840">Чтобы включить протокол HTTPS с шифрованием TLS на HTTP-сервере, ознакомьтесь с описанием службы *nx_web_http_server_secure_configure()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1840">To enable HTTPS using TLS on an HTTP server, see the service *nx_web_http_server_secure_configure().*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1841">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1841">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1842">**http_server_ptr**: указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1842">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1843">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1843">Return Values</span></span>

- <span data-ttu-id="34cb8-1844">**NX_SUCCESS** (0X00): HTTP-сервер успешно запущен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1844">**NX_SUCCESS** (0x00) Successful HTTP Server Start</span></span>
- <span data-ttu-id="34cb8-1845">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1845">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1846">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1846">Allowed From</span></span>

<span data-ttu-id="34cb8-1847">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1847">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1848">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1848">Example</span></span>

```C
/* Start the HTTP Server instance "my_server." */
status = nx_web_http_server_start(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been started. */
```

## <a name="nx_web_http_server_stop"></a><span data-ttu-id="34cb8-1849">nx_web_http_server_stop</span><span class="sxs-lookup"><span data-stu-id="34cb8-1849">nx_web_http_server_stop</span></span>

<span data-ttu-id="34cb8-1850">Остановка HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1850">Stop the HTTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1851">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1851">Prototype</span></span>

```C
UINT nx_web_http_server_stop(NX_WEB_HTTP_SERVER *http_server_ptr);
```

### <a name="description"></a><span data-ttu-id="34cb8-1852">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1852">Description</span></span>

<span data-ttu-id="34cb8-1853">Эта служба останавливает ранее созданный экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1853">This service stops the previously create HTTP Server instance.</span></span> <span data-ttu-id="34cb8-1854">Эту подпрограмму следует вызывать до удаления экземпляра HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1854">This routine should be called prior to deleting an HTTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1855">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1855">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1856">**http_server_ptr**: указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1856">**http_server_ptr** Pointer to HTTP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1857">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1857">Return Values</span></span>

- <span data-ttu-id="34cb8-1858">**NX_SUCCESS** (0X00): HTTP-сервер успешно остановлен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1858">**NX_SUCCESS** (0x00) Successful HTTP Server Stop</span></span>
- <span data-ttu-id="34cb8-1859">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1859">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-1860">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1860">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1861">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1861">Allowed From</span></span>

<span data-ttu-id="34cb8-1862">Потоки</span><span class="sxs-lookup"><span data-stu-id="34cb8-1862">Threads</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1863">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1863">Example</span></span>

```C
/* Stop the HTTP Server instance "my_server." */
status = nx_web_http_server_stop(&my_server);

/* If status equals NX_SUCCESS, the HTTP Server has been stopped. */
```

## <a name="nx_web_http_server_type_get"></a><span data-ttu-id="34cb8-1864">nx_web_http_server_type_get</span><span class="sxs-lookup"><span data-stu-id="34cb8-1864">nx_web_http_server_type_get</span></span>

<span data-ttu-id="34cb8-1865">Извлечение типа файла из HTTP-запроса клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1865">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1866">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1866">Prototype</span></span>

```C
UINT nx_web_http_server_type_get(NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, CHAR *http_type_string,
    UINT *string_size);
```

### <a name="description"></a><span data-ttu-id="34cb8-1867">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1867">Description</span></span>

> [!NOTE]
> <span data-ttu-id="34cb8-1868">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1868">This service is deprecated.</span></span> <span data-ttu-id="34cb8-1869">Пользователям рекомендуется использовать службу *nx_web_http_server_type_get_extended()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1869">Users are encouraged to use the service *nx_web_http_server_type_get_extended()*.</span></span>

<span data-ttu-id="34cb8-1870">Эта служба извлекает тип HTTP-запроса из *http_type_string* и его длину из *string_size* из входного буфера *name* (обычно это URL-адрес).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1870">This service extracts the HTTP request type in the buffer *http_type_string* and its length in *string_size* from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="34cb8-1871">Если сопоставление MIME не найдено, по умолчанию используется тип "text/plain".</span><span class="sxs-lookup"><span data-stu-id="34cb8-1871">If no MIME map is found, it defaults to the "text/plain" type.</span></span> <span data-ttu-id="34cb8-1872">В противном случае извлеченный тип сравнивается с сопоставлениями MIME HTTP-сервера по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1872">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="34cb8-1873">Сопоставления MIME по умолчанию на сервере NetX Duo HTTP:</span><span class="sxs-lookup"><span data-stu-id="34cb8-1873">The default MIME maps in NetX Web HTTP Server are:</span></span>

- <span data-ttu-id="34cb8-1874">html — "text/html";</span><span class="sxs-lookup"><span data-stu-id="34cb8-1874">html text/html</span></span>
- <span data-ttu-id="34cb8-1875">HTM — текст или HTML</span><span class="sxs-lookup"><span data-stu-id="34cb8-1875">htm text/html</span></span>
- <span data-ttu-id="34cb8-1876">TXT — текст или обычный текст</span><span class="sxs-lookup"><span data-stu-id="34cb8-1876">txt text/plain</span></span>
- <span data-ttu-id="34cb8-1877">GIF — изображение или GIF</span><span class="sxs-lookup"><span data-stu-id="34cb8-1877">gif image/gif</span></span>
- <span data-ttu-id="34cb8-1878">JPEG — изображение или JPEG</span><span class="sxs-lookup"><span data-stu-id="34cb8-1878">jpg image/jpeg</span></span>
- <span data-ttu-id="34cb8-1879">ICO — изображение или x-icon</span><span class="sxs-lookup"><span data-stu-id="34cb8-1879">ico image/x-icon</span></span>

<span data-ttu-id="34cb8-1880">Если этот параметр задан, также будет выполнен поиск определенного пользователем набора дополнительных сопоставлений MIME.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1880">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="34cb8-1881">Дополнительные сведения об определяемых пользователем сопоставлениях см. в описании службы *nx_web_http_server_mime_maps_addtional_set()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1881">See *nx_web_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1882">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1882">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1883">**http_server_ptr**: указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1883">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="34cb8-1884">**name**: указатель на буфер для поиска.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1884">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="34cb8-1885">**http_type_string**: указатель на извлеченный тип HTML.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1885">**http_type_string** Pointer to extracted HTML type string</span></span>
- <span data-ttu-id="34cb8-1886">**string_size**: указатель на возвращаемую длину строки типа HTML.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1886">**string_size** Pointer to return extracted HTML type string length.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1887">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1887">Return Values</span></span>

- <span data-ttu-id="34cb8-1888">**NX_SUCCESS** (0X00): тип успешно извлечен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1888">**NX_SUCCESS** (0x00) Successful extraction of type</span></span>
- <span data-ttu-id="34cb8-1889">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1889">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-1890">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019): возвращен тип по умолчанию (text/plain).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1890">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Default "text/plain" returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1891">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1891">Allowed From</span></span>

<span data-ttu-id="34cb8-1892">Приложение</span><span class="sxs-lookup"><span data-stu-id="34cb8-1892">Application</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1893">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1893">Example</span></span>

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

## <a name="nx_web_http_server_type_get_extended"></a><span data-ttu-id="34cb8-1894">nx_web_http_server_type_get_extended</span><span class="sxs-lookup"><span data-stu-id="34cb8-1894">nx_web_http_server_type_get_extended</span></span>

<span data-ttu-id="34cb8-1895">Извлечение типа файла из HTTP-запроса клиента.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1895">Extract file type from Client HTTP request</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1896">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1896">Prototype</span></span>

```C
UINT nx_web_http_server_type_get_extended(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    CHAR *name, UINT name_length,
    CHAR *http_type_string,
    UINT http_type_string_max_size,
    UINT *string_size);
```

### <a name="description"></a><span data-ttu-id="34cb8-1897">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1897">Description</span></span>

<span data-ttu-id="34cb8-1898">Эта служба извлекает тип HTTP-запроса из *http_type_string* и его длину из *string_size* из входного буфера *name* (обычно это URL-адрес).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1898">This service extracts the HTTP request type in the buffer *http_type_string* and its length in *string_size* from the input buffer *name*, usually the URL.</span></span> <span data-ttu-id="34cb8-1899">Если сопоставление MIME не найдено, по умолчанию используется тип "text/plain".</span><span class="sxs-lookup"><span data-stu-id="34cb8-1899">If no MIME map is found, it defaults to the "text/plain" type.</span></span> <span data-ttu-id="34cb8-1900">В противном случае извлеченный тип сравнивается с сопоставлениями MIME HTTP-сервера по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1900">Otherwise it compares the extracted type against the HTTP Server default MIME maps for a match.</span></span> <span data-ttu-id="34cb8-1901">Сопоставления MIME по умолчанию на сервере NetX Duo HTTP:</span><span class="sxs-lookup"><span data-stu-id="34cb8-1901">The default MIME maps in NetX Web HTTP Server are:</span></span>

- <span data-ttu-id="34cb8-1902">html — "text/html";</span><span class="sxs-lookup"><span data-stu-id="34cb8-1902">html text/html</span></span>
- <span data-ttu-id="34cb8-1903">HTM — текст или HTML</span><span class="sxs-lookup"><span data-stu-id="34cb8-1903">htm text/html</span></span>
- <span data-ttu-id="34cb8-1904">TXT — текст или обычный текст</span><span class="sxs-lookup"><span data-stu-id="34cb8-1904">txt text/plain</span></span>
- <span data-ttu-id="34cb8-1905">GIF — изображение или GIF</span><span class="sxs-lookup"><span data-stu-id="34cb8-1905">gif image/gif</span></span>
- <span data-ttu-id="34cb8-1906">JPEG — изображение или JPEG</span><span class="sxs-lookup"><span data-stu-id="34cb8-1906">jpg image/jpeg</span></span>
- <span data-ttu-id="34cb8-1907">ICO — изображение или x-icon</span><span class="sxs-lookup"><span data-stu-id="34cb8-1907">ico image/x-icon</span></span>

<span data-ttu-id="34cb8-1908">Если этот параметр задан, также будет выполнен поиск определенного пользователем набора дополнительных сопоставлений MIME.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1908">If supplied, it will also search a user defined set of additional MIME maps.</span></span> <span data-ttu-id="34cb8-1909">Дополнительные сведения об определяемых пользователем сопоставлениях см. в описании службы *nx_web_http_server_mime_maps_addtional_set()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1909">See *nx_web_http_server_mime_maps_addtional_set()* for more details on user defined maps.</span></span>

<span data-ttu-id="34cb8-1910">Эта служба заменяет *nx_web_http_server_type_get()* .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1910">This service replaces *nx_web_http_server_type_get*().</span></span> <span data-ttu-id="34cb8-1911">В этой версии требуется, чтобы вызывающие объекты предоставляли функции сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1911">This version requires callers to supply length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1912">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1912">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1913">**http_server_ptr**: указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1913">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="34cb8-1914">**name**: указатель на буфер для поиска.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1914">**name** Pointer to buffer to search</span></span>
- <span data-ttu-id="34cb8-1915">**name_length**: длина имени.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1915">**name_length** Length of name</span></span>
- <span data-ttu-id="34cb8-1916">**http_type_string**: указатель на извлеченный тип HTML.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1916">**http_type_string** Pointer to extracted HTML type string</span></span>
- <span data-ttu-id="34cb8-1917">**http_type_string_max_size**: размер буфера http_type_string.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1917">**http_type_string_max_size** Size of the http_type_string buffer size</span></span>
- <span data-ttu-id="34cb8-1918">**string_size**: указатель на возвращаемую длину строки типа HTML</span><span class="sxs-lookup"><span data-stu-id="34cb8-1918">**string_size** Pointer to return extracted HTML type string</span></span>

<span data-ttu-id="34cb8-1919">.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1919">length.</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1920">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1920">Return Values</span></span>

- <span data-ttu-id="34cb8-1921">**NX_SUCCESS** (0X00): тип успешно извлечен.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1921">**NX_SUCCESS** (0x00) Successful extraction of type</span></span>
- <span data-ttu-id="34cb8-1922">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1922">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-1923">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019): возвращен тип по умолчанию (text/plain).</span><span class="sxs-lookup"><span data-stu-id="34cb8-1923">**NX_WEB_HTTP_EXTENSION_MIME_DEFAULT** (0x30019) Default "text/plain" returned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1924">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1924">Allowed From</span></span>

<span data-ttu-id="34cb8-1925">Приложение</span><span class="sxs-lookup"><span data-stu-id="34cb8-1925">Application</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1926">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1926">Example</span></span>

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

## <a name="nx_web_http_server_digest_authenticate_notify_set"></a><span data-ttu-id="34cb8-1927">nx_web_http_server_digest_authenticate_notify_set</span><span class="sxs-lookup"><span data-stu-id="34cb8-1927">nx_web_http_server_digest_authenticate_notify_set</span></span>

<span data-ttu-id="34cb8-1928">Задание функции обратного вызова дайджест-проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1928">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1929">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1929">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="34cb8-1930">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1930">Description</span></span>

<span data-ttu-id="34cb8-1931">Эта служба задает обратный вызов, вызываемый при выполнении дайджест-проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1931">This service sets the callback invoked when digest authenticate is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1932">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1932">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1933">**http_server_ptr**: указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1933">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="34cb8-1934">**digest_authenticate_callback**: указатель на обратный вызов дайджест-проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1934">**digest_authenticate_callback** Pointer to digest authenticate callback</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1935">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1935">Return Values</span></span>

- <span data-ttu-id="34cb8-1936">**NX_SUCCESS** (0x00) — обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1936">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="34cb8-1937">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1937">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="34cb8-1938">NX_NOT_SUPPORTED (0x4B) — дайджест-проверка подлинности не включена.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1938">NX_NOT_SUPPORTED (0x4B) Digest authenticate not enabled</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1939">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1939">Allowed From</span></span>

<span data-ttu-id="34cb8-1940">Приложение</span><span class="sxs-lookup"><span data-stu-id="34cb8-1940">Application</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1941">Например, .</span><span class="sxs-lookup"><span data-stu-id="34cb8-1941">Example</span></span>

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

## <a name="nx_web_http_server_authenticate_check_set"></a><span data-ttu-id="34cb8-1942">nx_web_http_server_authenticate_check_set</span><span class="sxs-lookup"><span data-stu-id="34cb8-1942">nx_web_http_server_authenticate_check_set</span></span>

<span data-ttu-id="34cb8-1943">Задание функции обратного вызова дайджест-проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1943">Set digest authenticate callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="34cb8-1944">Прототип</span><span class="sxs-lookup"><span data-stu-id="34cb8-1944">Prototype</span></span>

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

### <a name="description"></a><span data-ttu-id="34cb8-1945">Описание</span><span class="sxs-lookup"><span data-stu-id="34cb8-1945">Description</span></span>

<span data-ttu-id="34cb8-1946">Эта служба задает обратный вызов, выполняемый при проверке подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1946">This service sets the callback invoked when authenticate check is performed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="34cb8-1947">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="34cb8-1947">Input Parameters</span></span>

- <span data-ttu-id="34cb8-1948">**http_server_ptr**: указатель на экземпляр HTTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1948">**http_server_ptr** Pointer to HTTP Server instance</span></span>
- <span data-ttu-id="34cb8-1949">**authenticate_check_externded**: указатель на обратный вызов проверки подлинности.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1949">**authenticate_check_externded** Pointer to authenticate check callback</span></span>

### <a name="return-values"></a><span data-ttu-id="34cb8-1950">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="34cb8-1950">Return Values</span></span>

- <span data-ttu-id="34cb8-1951">**NX_SUCCESS** (0x00) — обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1951">**NX_SUCCESS** (0x00) Successfully set the callback</span></span>
- <span data-ttu-id="34cb8-1952">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="34cb8-1952">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="34cb8-1953">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="34cb8-1953">Allowed From</span></span>

<span data-ttu-id="34cb8-1954">Приложение</span><span class="sxs-lookup"><span data-stu-id="34cb8-1954">Application</span></span>

### <a name="example"></a><span data-ttu-id="34cb8-1955">Пример</span><span class="sxs-lookup"><span data-stu-id="34cb8-1955">Example</span></span>

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
