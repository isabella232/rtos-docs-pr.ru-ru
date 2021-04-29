---
title: Глава 3. Описание служб FTP
description: Эта глава содержит описание всех служб NetX FTP, перечисленных ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d721d8bd3e08d8cccdc13011807b4c5017c84173
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814707"
---
# <a name="chapter-3---description-of-ftp-services"></a><span data-ttu-id="ee2db-103">Глава 3. Описание служб FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-103">Chapter 3 - Description of FTP services</span></span>

<span data-ttu-id="ee2db-104">В этой главе содержится описание всех служб FTP в NetX, перечисленных ниже в алфавитном порядке (эквивалентные службы IPv4 и IPv6 приводятся вместе).</span><span class="sxs-lookup"><span data-stu-id="ee2db-104">This chapter contains a description of all NetX FTP services (listed below) in alphabetic order (except where IPv4 and IPv6 equivalents of the same service are paired together).</span></span>

> [!NOTE]
> <span data-ttu-id="ee2db-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="ee2db-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_ftp_client_connect"></a><span data-ttu-id="ee2db-106">nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="ee2db-106">nx_ftp_client_connect</span></span>

<span data-ttu-id="ee2db-107">Подключение к FTP-серверу через IPv4</span><span class="sxs-lookup"><span data-stu-id="ee2db-107">Connect to an FTP Server over IPv4</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-108">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-108">Prototype</span></span>

```C
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG server_ip, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee2db-109">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-109">Description</span></span>

<span data-ttu-id="ee2db-110">Эта служба подключает ранее созданный экземпляр клиента FTP NetX к FTP-серверу по заданному IP-адресу.</span><span class="sxs-lookup"><span data-stu-id="ee2db-110">This service connects the previously created NetX FTP Client instance to the FTP Server at the supplied IP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-111">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-111">Input Parameters</span></span>

- <span data-ttu-id="ee2db-112">**client_ptr**: указатель на блок управления клиентом FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-112">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ee2db-113">**server_ip**: IP-адрес FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-113">**server_ip** IP address of FTP Server.</span></span>
- <span data-ttu-id="ee2db-114">**username**: имя пользователя клиента для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="ee2db-114">**username** Client username for authentication.</span></span>
- <span data-ttu-id="ee2db-115">**password**: пароль клиента для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="ee2db-115">**password** Client password for authentication.</span></span>
- <span data-ttu-id="ee2db-116">**wait_option** определяет, как долго служба будет ожидать подключения клиента FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-116">**wait_option** Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="ee2db-117">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ee2db-117">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ee2db-118">**timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-118">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ee2db-119">**TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос</span><span class="sxs-lookup"><span data-stu-id="ee2db-119">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-120">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-120">Return Values</span></span>

- <span data-ttu-id="ee2db-121">**NX_SUCCESS** (0x00) — FTP-подключение успешно создано.</span><span class="sxs-lookup"><span data-stu-id="ee2db-121">**NX_SUCCESS** (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="ee2db-122">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) — ответ 22X (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-122">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="ee2db-123">**NX_FTP_EXPECTED_23X_CODE** (0xDC) — ответ 23X (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-123">**NX_FTP_EXPECTED_23X_CODE** (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="ee2db-124">**NX_FTP_EXPECTED_33X_CODE** (0xDE) — ответ 33X (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-124">**NX_FTP_EXPECTED_33X_CODE** (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="ee2db-125">**NX_FTP_NOT_DISCONNECTED** (0xD4) — клиент уже подключен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-125">**NX_FTP_NOT_DISCONNECTED** (0xD4) Client is already connected.</span></span>
- <span data-ttu-id="ee2db-126">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ee2db-126">NX_PTR_ERROR (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="ee2db-127">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-127">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ee2db-128">NX_IP_ADDRESS_ERROR (0x21) — недопустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="ee2db-128">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-129">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-129">Allowed From</span></span>

<span data-ttu-id="ee2db-130">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-130">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-131">Пример</span><span class="sxs-lookup"><span data-stu-id="ee2db-131">Example</span></span>

```C
/* Connect the FTP Client instance “my_client” to the FTP Server at

IP address 1.2.3.4. */

status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a><span data-ttu-id="ee2db-132">См. также:</span><span class="sxs-lookup"><span data-stu-id="ee2db-132">See Also</span></span>

<span data-ttu-id="ee2db-133">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nxd_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="ee2db-133">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nxd_ftp_client_connect</span></span>

## <a name="nxd_ftp_client_connect"></a><span data-ttu-id="ee2db-134">nxd_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="ee2db-134">nxd_ftp_client_connect</span></span>

<span data-ttu-id="ee2db-135">Подключение к FTP-серверу с поддержкой IPv6</span><span class="sxs-lookup"><span data-stu-id="ee2db-135">Connect to an FTP Server with IPv6 support</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-136">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-136">Prototype</span></span>

```C
UINT nxd_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
    NXD_ADDRESS *server_ipduo, CHAR *username, CHAR *password,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee2db-137">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-137">Description</span></span>

<span data-ttu-id="ee2db-138">Эта служба подключает ранее созданный экземпляр клиента FTP NetX Duo к FTP-серверу по заданному IP-адресу.</span><span class="sxs-lookup"><span data-stu-id="ee2db-138">This service connects the previously created NetX Duo FTP Client instance to the FTP Server at the supplied IP address.</span></span> <span data-ttu-id="ee2db-139">Поддерживаются сети IPv4 и IPv6.</span><span class="sxs-lookup"><span data-stu-id="ee2db-139">Both IPv4 and IPv6 networks are supported.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-140">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-140">Input Parameters</span></span>

- <span data-ttu-id="ee2db-141">**client_ptr**: указатель на блок управления клиентом FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-141">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ee2db-142">**server_ipduo**: IP-адрес FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-142">**server_ipduo** IP address of the FTP Server.</span></span>
- <span data-ttu-id="ee2db-143">**username**: имя пользователя клиента для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="ee2db-143">**username** Client username for authentication.</span></span>
- <span data-ttu-id="ee2db-144">**password**: пароль клиента для проверки подлинности</span><span class="sxs-lookup"><span data-stu-id="ee2db-144">**password** Client password for authentication.</span></span>
- <span data-ttu-id="ee2db-145">**wait_option** определяет, как долго служба будет ожидать подключения клиента FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-145">**wait_option** Defines how long the service will wait for the FTP Client connection.</span></span> <span data-ttu-id="ee2db-146">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ee2db-146">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ee2db-147">**timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-147">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ee2db-148">**TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос</span><span class="sxs-lookup"><span data-stu-id="ee2db-148">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-149">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-149">Return Values</span></span>

- <span data-ttu-id="ee2db-150">**NX_SUCCESS** (0x00) — FTP-подключение успешно создано.</span><span class="sxs-lookup"><span data-stu-id="ee2db-150">**NX_SUCCESS** (0x00) Successful FTP connection.</span></span>
- <span data-ttu-id="ee2db-151">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) — ответ 22X (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-151">**NX_TFTP_EXPECTED_22X_CODE** (0xDB) Did not get a 22X (ok) response</span></span>
- <span data-ttu-id="ee2db-152">**NX_FTP_EXPECTED_23X_CODE** (0xDC) — ответ 23X (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-152">**NX_FTP_EXPECTED_23X_CODE** (0xDC) Did not get a 23X (ok) response</span></span>
- <span data-ttu-id="ee2db-153">**NX_FTP_EXPECTED_33X_CODE** (0xDE) — ответ 33X (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-153">**NX_FTP_EXPECTED_33X_CODE** (0xDE) Did not get a 33X (ok) response</span></span>
- <span data-ttu-id="ee2db-154">**NX_FTP_NOT_DISCONNECTED** (0xD4) — клиент уже подключен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-154">**NX_FTP_NOT_DISCONNECTED** (0xD4) Client is already connected</span></span>
- <span data-ttu-id="ee2db-155">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ee2db-155">NX_PTR_ERROR (0x07) Invalid pointer inout.</span></span>
- <span data-ttu-id="ee2db-156">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-156">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="ee2db-157">NX_IP_ADDRESS_ERROR (0x21) — недопустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="ee2db-157">NX_IP_ADDRESS_ERROR (0x21) Invalid IP address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-158">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-158">Allowed From</span></span>

<span data-ttu-id="ee2db-159">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-159">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-160">Пример</span><span class="sxs-lookup"><span data-stu-id="ee2db-160">Example</span></span>

```C
/* Connect an FTP Client instance to the FTP Server. */

/* Set up an IPv6 address for the server here.
    Note this could also be an IPv4 address as well*/

server_ip_addr.nxd_ip_address.v6[3] = 0x106;
server_ip_addr.nxd_ip_address.v6[2] = 0x0;
server_ip_addr.nxd_ip_address.v6[1] = 0x0000f101;
server_ip_addr.nxd_ip_address.v6[0] = 0x20010db8;
server_ip_addr.nxd_ip_version = NX_IP_VERSION_V6;

status = nxd_ftp_client_connect(&my_client, server_ip_addr, NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
    connected to the FTP Server. */
```

### <a name="see-also"></a><span data-ttu-id="ee2db-161">См. также:</span><span class="sxs-lookup"><span data-stu-id="ee2db-161">See Also</span></span>

<span data-ttu-id="ee2db-162">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nx_ftp_client_connect</span><span class="sxs-lookup"><span data-stu-id="ee2db-162">nx_ftp_client_create, nx_ftp_client_delete, nx_ftp_client_directory_create, nx_ftp_client_disconnect, nx_ftp_client_connect</span></span>

## <a name="nx_ftp_client_create"></a><span data-ttu-id="ee2db-163">nx_ftp_client_create</span><span class="sxs-lookup"><span data-stu-id="ee2db-163">nx_ftp_client_create</span></span>

<span data-ttu-id="ee2db-164">Создание экземпляра клиента FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-164">Create an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-165">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-165">Prototype</span></span>

```C
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="ee2db-166">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-166">Description</span></span>

<span data-ttu-id="ee2db-167">Эта служба создает экземпляр клиента FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-167">This service creates an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-168">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-168">Input Parameters</span></span>

- <span data-ttu-id="ee2db-169">**client_ptr**: указатель на блок управления клиентом FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-169">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ee2db-170">**ftp_client_name**: имя клиента FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-170">**ftp_client_name** Name of FTP Client.</span></span>
- <span data-ttu-id="ee2db-171">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="ee2db-171">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="ee2db-172">**window_size**: размер объявленного окна для сокета TCP этого клиента FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-172">**window_size** Advertised window size for TCP sockets of this FTP Client.</span></span>
- <span data-ttu-id="ee2db-173">**pool_ptr**: указатель на пул пакетов по умолчанию для этого клиента FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-173">**pool_ptr** Pointer to the default packet pool for this FTP Client.</span></span> <span data-ttu-id="ee2db-174">Обратите внимание, что минимальная полезная нагрузка пакета должна быть достаточно большой, чтобы вмещать полный путь и имя файла или каталога.</span><span class="sxs-lookup"><span data-stu-id="ee2db-174">Note that the minimum packet payload must be large enough to hold  complete path and the file or directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-175">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-175">Return Values</span></span>

- <span data-ttu-id="ee2db-176">**NX_SUCCESS** (0x00) — клиент FTP успешно создан.</span><span class="sxs-lookup"><span data-stu-id="ee2db-176">**NX_SUCCESS** (0x00) Successful FTP Client create.</span></span>
- <span data-ttu-id="ee2db-177">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ee2db-177">NX_PTR_ERROR (0x07) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-178">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-178">Allowed From</span></span>

<span data-ttu-id="ee2db-179">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-179">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-180">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-180">Example</span></span>

```C
/* Create the FTP Client instance “my_client.” */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
    2000, &client_pool);
/* If status is NX_SUCCESS the FTP Client instance was successfully created. */
```

## <a name="nx_ftp_client_delete"></a><span data-ttu-id="ee2db-181">nx_ftp_client_delete</span><span class="sxs-lookup"><span data-stu-id="ee2db-181">nx_ftp_client_delete</span></span>

<span data-ttu-id="ee2db-182">Удаление экземпляра клиента FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-182">Delete an FTP Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-183">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-183">Prototype</span></span>

```C
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="ee2db-184">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-184">Description</span></span>

<span data-ttu-id="ee2db-185">Эта служба удаляет экземпляр клиента FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-185">This service deletes an FTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-186">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-186">Input Parameters</span></span>

- <span data-ttu-id="ee2db-187">**client_ptr**: указатель на блок управления клиентом FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-187">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-188">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-188">Return Values</span></span>

- <span data-ttu-id="ee2db-189">**NX_SUCCESS** (0x00) — клиент FTP успешно удален.</span><span class="sxs-lookup"><span data-stu-id="ee2db-189">**NX_SUCCESS** (0x00) Successful FTP Client delete.</span></span>
- <span data-ttu-id="ee2db-190">**NX_FTP_NOT_DISCONNECTED** (0xD4) — клиент FTP не отключен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-190">**NX_FTP_NOT_DISCONNECTED** (0xD4) FTP client not disconnected</span></span>
- <span data-ttu-id="ee2db-191">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-191">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ee2db-192">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-192">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-193">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-193">Allowed From</span></span>

<span data-ttu-id="ee2db-194">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-194">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-195">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-195">Example</span></span>

```C
/* Delete the FTP Client instance “my_client.” */

status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a><span data-ttu-id="ee2db-196">nx_ftp_client_directory_create</span><span class="sxs-lookup"><span data-stu-id="ee2db-196">nx_ftp_client_directory_create</span></span>

<span data-ttu-id="ee2db-197">Создание каталога на FTP-сервере</span><span class="sxs-lookup"><span data-stu-id="ee2db-197">Create a directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-198">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-198">Prototype</span></span>

```C
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee2db-199">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-199">Description</span></span>

<span data-ttu-id="ee2db-200">Эта служба создает указанный каталог на FTP-сервере, подключенном к указанному клиенту FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-200">This service creates the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-201">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-201">Input Parameters</span></span>

- <span data-ttu-id="ee2db-202">**client_ptr**: указатель на блок управления клиентом FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-202">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ee2db-203">**directory_name**: имя создаваемого каталога</span><span class="sxs-lookup"><span data-stu-id="ee2db-203">**directory_name** Name of directory to create.</span></span>
- <span data-ttu-id="ee2db-204">**wait_option** определяет, как долго служба будет ожидать создания каталога FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-204">**wait_option** Defines how long the service will wait for the FTP directory create.</span></span> <span data-ttu-id="ee2db-205">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ee2db-205">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ee2db-206">**timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-206">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ee2db-207">**TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос</span><span class="sxs-lookup"><span data-stu-id="ee2db-207">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-208">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-208">Return Values</span></span>

- <span data-ttu-id="ee2db-209">**NX_SUCCESS** (0x00) — каталог FTP успешно создан.</span><span class="sxs-lookup"><span data-stu-id="ee2db-209">**NX_SUCCESS** (0x00) Successful FTP directory create.</span></span>
- <span data-ttu-id="ee2db-210">**NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-210">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ee2db-211">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-211">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="ee2db-212">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-212">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ee2db-213">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-213">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-214">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-214">Allowed From</span></span>

<span data-ttu-id="ee2db-215">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-216">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-216">Example</span></span>

```C
/* Create the directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_create(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” was successfully created. */
```

## <a name="nx_ftp_client_directory_default_set"></a><span data-ttu-id="ee2db-217">nx_ftp_client_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="ee2db-217">nx_ftp_client_directory_default_set</span></span>

<span data-ttu-id="ee2db-218">Задание каталога по умолчанию на FTP-сервере</span><span class="sxs-lookup"><span data-stu-id="ee2db-218">Set default directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-219">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-219">Prototype</span></span>

```C
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee2db-220">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-220">Description</span></span>

<span data-ttu-id="ee2db-221">Эта служба задает каталог по умолчанию на FTP-сервере, подключенном к указанному клиенту FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-221">This service sets the default directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="ee2db-222">Этот каталог по умолчанию применяется только к подключению этого клиента.</span><span class="sxs-lookup"><span data-stu-id="ee2db-222">This default directory applies only to this client’s connection.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-223">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-223">Input Parameters</span></span>

- <span data-ttu-id="ee2db-224">**client_ptr**: указатель на блок управления клиентом FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-224">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ee2db-225">**directory_path**: имя пути к каталогу, который необходимо задать</span><span class="sxs-lookup"><span data-stu-id="ee2db-225">**directory_path** Name of directory path to set.</span></span>
- <span data-ttu-id="ee2db-226">**wait_option** определяет, как долго служба будет ожидать задания каталога FTP по умолчанию</span><span class="sxs-lookup"><span data-stu-id="ee2db-226">**wait_option** Defines how long the service will wait for the FTP default directory set.</span></span> <span data-ttu-id="ee2db-227">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ee2db-227">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ee2db-228">**timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-228">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ee2db-229">**TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос</span><span class="sxs-lookup"><span data-stu-id="ee2db-229">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-230">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-230">Return Values</span></span>

- <span data-ttu-id="ee2db-231">**NX_SUCCESS** (0x00) — каталог FTP по умолчанию успешно задан.</span><span class="sxs-lookup"><span data-stu-id="ee2db-231">**NX_SUCCESS** (0x00) Successful FTP default set.</span></span>
- <span data-ttu-id="ee2db-232">**NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-232">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ee2db-233">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-233">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="ee2db-234">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-234">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ee2db-235">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-235">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-236">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-236">Allowed From</span></span>

<span data-ttu-id="ee2db-237">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-238">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-238">Example</span></span>

```C
/* Set the default directory to “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_default_set(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a><span data-ttu-id="ee2db-239">nx_ftp_client_directory_delete</span><span class="sxs-lookup"><span data-stu-id="ee2db-239">nx_ftp_client_directory_delete</span></span>

<span data-ttu-id="ee2db-240">Удаление каталога на FTP-сервере</span><span class="sxs-lookup"><span data-stu-id="ee2db-240">Delete directory on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-241">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-241">Prototype</span></span>

```C
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee2db-242">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-242">Description</span></span>

<span data-ttu-id="ee2db-243">Эта служба удаляет указанный каталог на FTP-сервере, подключенном к указанному клиенту FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-243">This service deletes the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-244">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-244">Input Parameters</span></span>

- <span data-ttu-id="ee2db-245">**client_ptr**: указатель на блок управления клиентом FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-245">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ee2db-246">**directory_name**: имя удаляемого каталога</span><span class="sxs-lookup"><span data-stu-id="ee2db-246">**directory_name** Name of directory to delete.</span></span>
- <span data-ttu-id="ee2db-247">**wait_option** определяет, как долго служба будет ожидать удаления каталога FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-247">**wait_option** Defines how long the service will wait for the FTP directory delete.</span></span> <span data-ttu-id="ee2db-248">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ee2db-248">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ee2db-249">**timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-249">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ee2db-250">**TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос</span><span class="sxs-lookup"><span data-stu-id="ee2db-250">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-251">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-251">Return Values</span></span>

- <span data-ttu-id="ee2db-252">**NX_SUCCESS** (0x00) — каталог FTP успешно удален.</span><span class="sxs-lookup"><span data-stu-id="ee2db-252">**NX_SUCCESS** (0x00) Successful FTP directory delete.</span></span>
- <span data-ttu-id="ee2db-253">**NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-253">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ee2db-254">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-254">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="ee2db-255">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-255">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ee2db-256">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-256">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-257">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-257">Allowed From</span></span>

<span data-ttu-id="ee2db-258">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-258">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-259">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-259">Example</span></span>

```C
/* Delete directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_delete(&my_client, “my_dir”, 200);

/* If status is NX_SUCCESS the directory “my_dir” is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a><span data-ttu-id="ee2db-260">nx_ftp_client_directory_listing_get</span><span class="sxs-lookup"><span data-stu-id="ee2db-260">nx_ftp_client_directory_listing_get</span></span>

<span data-ttu-id="ee2db-261">Получение содержимого каталога с FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-261">Get directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-262">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-262">Prototype</span></span>

```C
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *directory_name, NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee2db-263">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-263">Description</span></span>

<span data-ttu-id="ee2db-264">Эта служба получает содержимое указанного каталога на FTP-сервере, подключенном к указанному клиенту FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-264">This service gets the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="ee2db-265">Приведенный указатель пакета будет содержать одну запись каталога или несколько.</span><span class="sxs-lookup"><span data-stu-id="ee2db-265">The supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="ee2db-266">Каждая запись отделяется комбинацией символов \<cr/lf\>.</span><span class="sxs-lookup"><span data-stu-id="ee2db-266">Each entry is separated by a \<cr/lf\> combination.</span></span> <span data-ttu-id="ee2db-267">Для завершения операции получения каталога необходимо вызвать службу ***nx_ftp_client_directory_listing_continue***.</span><span class="sxs-lookup"><span data-stu-id="ee2db-267">The ***nx_ftp_client_directory_listing_continue*** should be called to complete the directory get operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-268">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-268">Input Parameters</span></span>

- <span data-ttu-id="ee2db-269">**client_ptr**: указатель на блок управления клиентом FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-269">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ee2db-270">**directory_name**: имя каталога, содержимое которого нужно получить</span><span class="sxs-lookup"><span data-stu-id="ee2db-270">**directory_name** Name of directory to get contents of.</span></span>
- <span data-ttu-id="ee2db-271">**packet_ptr**: указатель на указатель пакета назначения</span><span class="sxs-lookup"><span data-stu-id="ee2db-271">**packet_ptr** Pointer to destination packet pointer.</span></span> <span data-ttu-id="ee2db-272">В случае успешного выполнения полезная нагрузка пакета будет содержать одну запись каталога или несколько.</span><span class="sxs-lookup"><span data-stu-id="ee2db-272">If successful, the packet payload will contain one or more directory entries.</span></span>
- <span data-ttu-id="ee2db-273">**wait_option** определяет, как долго служба будет ожидать получения содержимого каталога FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-273">**wait_option** Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="ee2db-274">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ee2db-274">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ee2db-275">**timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-275">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ee2db-276">**TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос</span><span class="sxs-lookup"><span data-stu-id="ee2db-276">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-277">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-277">Return Values</span></span>

- <span data-ttu-id="ee2db-278">**NX_SUCCESS** (0x00) — содержимое каталога FTP успешно получено.</span><span class="sxs-lookup"><span data-stu-id="ee2db-278">**NX_SUCCESS** (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="ee2db-279">**NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-279">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ee2db-280">**NX_NOT_ENABLED** (0x14) — служба (IPv6) не включена.</span><span class="sxs-lookup"><span data-stu-id="ee2db-280">**NX_NOT_ENABLED** (0x14) Service (IPv6) not enabled</span></span>
- <span data-ttu-id="ee2db-281">**NX_FTP_EXPECTED_1XX_CODE** (0xD9) — ответ 1XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-281">**NX_FTP_EXPECTED_1XX_CODE** (0xD9) Did not get a 1XX (ok) response</span></span>
- <span data-ttu-id="ee2db-282">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-282">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="ee2db-283">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-283">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ee2db-284">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-284">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-285">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-285">Allowed From</span></span>

<span data-ttu-id="ee2db-286">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-286">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-287">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-287">Example</span></span>

```C
/* Get the contents of directory “my_dir” on the FTP Server connected to
    the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_get(&my_client, “my_dir”, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_directory_listing_continue"></a><span data-ttu-id="ee2db-288">nx_ftp_client_directory_listing_continue</span><span class="sxs-lookup"><span data-stu-id="ee2db-288">nx_ftp_client_directory_listing_continue</span></span>

<span data-ttu-id="ee2db-289">Продолжение получения содержимого каталога с FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-289">Continue directory listing from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-290">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-290">Prototype</span></span>

```C
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee2db-291">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-291">Description</span></span>

<span data-ttu-id="ee2db-292">Эта служба продолжает получать содержимое указанного каталога на FTP-сервере, подключенном к указанному клиенту FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-292">This service continues getting the contents of the specified directory on the FTP Server that is connected to the specified FTP Client.</span></span> <span data-ttu-id="ee2db-293">Перед ней должен быть выполнен вызов службы ***nx_ftp_client_directory_listing_get***.</span><span class="sxs-lookup"><span data-stu-id="ee2db-293">It should have been immediately preceded by a call to ***nx_ftp_client_directory_listing_get***.</span></span> <span data-ttu-id="ee2db-294">В случае успеха заданный указатель пакета будет содержать одну запись каталога или несколько.</span><span class="sxs-lookup"><span data-stu-id="ee2db-294">If successful, the supplied packet pointer will contain one or more directory entries.</span></span> <span data-ttu-id="ee2db-295">Эту подпрограмму следует вызывать до получения состояния NX_FTP_END_OF_LISTING.</span><span class="sxs-lookup"><span data-stu-id="ee2db-295">This routine should be called until an NX_FTP_END_OF_LISTING status is received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-296">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-296">Input Parameters</span></span>

- <span data-ttu-id="ee2db-297">**client_ptr**: указатель на блок управления клиентом FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-297">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ee2db-298">**packet_ptr**: указатель на указатель пакета назначения</span><span class="sxs-lookup"><span data-stu-id="ee2db-298">**packet_ptr** Pointer to destination packet pointer.</span></span> <span data-ttu-id="ee2db-299">В случае успешного выполнения полезная нагрузка пакета будет содержать одну запись каталога или несколько записей, разделенных комбинацией символов <cr/lf>.</span><span class="sxs-lookup"><span data-stu-id="ee2db-299">If successful, the packet payload will contain one or more directory entries, separated by a <cr/lf>.</span></span>
- <span data-ttu-id="ee2db-300">**wait_option** определяет, как долго служба будет ожидать получения содержимого каталога FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-300">**wait_option** Defines how long the service will wait for the FTP directory listing.</span></span> <span data-ttu-id="ee2db-301">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ee2db-301">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ee2db-302">**timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-302">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ee2db-303">**TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос</span><span class="sxs-lookup"><span data-stu-id="ee2db-303">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-304">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-304">Return Values</span></span>

- <span data-ttu-id="ee2db-305">**NX_SUCCESS** (0x00) — содержимое каталога FTP успешно получено.</span><span class="sxs-lookup"><span data-stu-id="ee2db-305">**NX_SUCCESS** (0x00) Successful FTP directory listing.</span></span>
- <span data-ttu-id="ee2db-306">**NX_FTP_END_OF_LISTING** (0xD8) — в этом каталоге больше нет записей.</span><span class="sxs-lookup"><span data-stu-id="ee2db-306">**NX_FTP_END_OF_LISTING** (0xD8) No more entries in this directory.</span></span>
- <span data-ttu-id="ee2db-307">**NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-307">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ee2db-308">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-308">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="ee2db-309">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-309">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ee2db-310">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-310">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-311">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-311">Allowed From</span></span>

<span data-ttu-id="ee2db-312">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-312">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-313">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-313">Example</span></span>

```C
/* Continue getting the contents of directory “my_dir” on the FTP Server
    connected to the FTP Client instance “my_client.” */

status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
    200);

/* If status is NX_SUCCESS, one or more entries of the directory “my_dir”
    can be found in “my_packet”. */
```

## <a name="nx_ftp_client_disconnect"></a><span data-ttu-id="ee2db-314">nx_ftp_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="ee2db-314">nx_ftp_client_disconnect</span></span>

<span data-ttu-id="ee2db-315">Отключение от FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-315">Disconnect from FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-316">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-316">Prototype</span></span>

```C
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee2db-317">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-317">Description</span></span>

<span data-ttu-id="ee2db-318">Эта служба отключает ранее установленное подключение FTP-сервера к указанному клиенту FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-318">This service disconnects a previously established FTP Server connection with the specified FTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-319">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-319">Input Parameters</span></span>

- <span data-ttu-id="ee2db-320">**client_ptr**: указатель на блок управления клиентом FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-320">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ee2db-321">**wait_option** определяет, как долго служба будет ожидать отключения клиента FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-321">**wait_option** Defines how long the service will wait for the FTP Client disconnect.</span></span> <span data-ttu-id="ee2db-322">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ee2db-322">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ee2db-323">**timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-323">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ee2db-324">**TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос</span><span class="sxs-lookup"><span data-stu-id="ee2db-324">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-325">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-325">Return Values</span></span>

- <span data-ttu-id="ee2db-326">**NX_SUCCESS** (0x00) — FTP-подключение завершено.</span><span class="sxs-lookup"><span data-stu-id="ee2db-326">**NX_SUCCESS** (0x00) Successful FTP disconnect.</span></span>
- <span data-ttu-id="ee2db-327">**NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-327">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ee2db-328">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-328">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="ee2db-329">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-329">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ee2db-330">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-330">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-331">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-331">Allowed From</span></span>

<span data-ttu-id="ee2db-332">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-332">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-333">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-333">Example</span></span>

```C
/* Disconnect “my_client” from the FTP Server. */

status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, “my_client” has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a><span data-ttu-id="ee2db-334">nx_ftp_client_file_close</span><span class="sxs-lookup"><span data-stu-id="ee2db-334">nx_ftp_client_file_close</span></span>

<span data-ttu-id="ee2db-335">Закрытие файла клиента</span><span class="sxs-lookup"><span data-stu-id="ee2db-335">Close Client file</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-336">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-336">Prototype</span></span>

```C
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee2db-337">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-337">Description</span></span>

<span data-ttu-id="ee2db-338">Эта служба закрывает ранее открытый файл на FTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="ee2db-338">This service closes a previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-339">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-339">Input Parameters</span></span>

- <span data-ttu-id="ee2db-340">**client_ptr**: указатель на блок управления клиентом FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-340">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ee2db-341">**wait_option** определяет, как долго служба будет ожидать закрытия файла клиента FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-341">**wait_option** Defines how long the service will wait for the FTP Client file close.</span></span> <span data-ttu-id="ee2db-342">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ee2db-342">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ee2db-343">**timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-343">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ee2db-344">**TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос</span><span class="sxs-lookup"><span data-stu-id="ee2db-344">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-345">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-345">Return Values</span></span>

- <span data-ttu-id="ee2db-346">**NX_SUCCESS** (0x00) — FTP-файл успешно закрыт.</span><span class="sxs-lookup"><span data-stu-id="ee2db-346">**NX_SUCCESS** (0x00) Successful FTP file close.</span></span>
- <span data-ttu-id="ee2db-347">**NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-347">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ee2db-348">**NX_FTP_NOT_OPEN** (0xD5) — файл не открыт; его невозможно закрыть.</span><span class="sxs-lookup"><span data-stu-id="ee2db-348">**NX_FTP_NOT_OPEN (0xD5)** File not open; cannot close it</span></span>
- <span data-ttu-id="ee2db-349">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-349">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="ee2db-350">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-350">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ee2db-351">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-351">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-352">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-352">Allowed From</span></span>

<span data-ttu-id="ee2db-353">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-353">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-354">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-354">Example</span></span>

```C
/* Close previously opened file of client “my_client” on the FTP Server. */

status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the “my_client” FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a><span data-ttu-id="ee2db-355">nx_ftp_client_file_delete</span><span class="sxs-lookup"><span data-stu-id="ee2db-355">nx_ftp_client_file_delete</span></span>

<span data-ttu-id="ee2db-356">Удаление файла на FTP-сервере</span><span class="sxs-lookup"><span data-stu-id="ee2db-356">Delete file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-357">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-357">Prototype</span></span>

```C
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee2db-358">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-358">Description</span></span>

<span data-ttu-id="ee2db-359">Эта служба удаляет указанный файл на FTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="ee2db-359">This service deletes the specified file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-360">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-360">Input Parameters</span></span>

- <span data-ttu-id="ee2db-361">**client_ptr**: указатель на блок управления клиентом FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-361">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ee2db-362">**file_name**: имя файла для удаления</span><span class="sxs-lookup"><span data-stu-id="ee2db-362">**file_name** Name of file to delete.</span></span>
- <span data-ttu-id="ee2db-363">**wait_option** определяет, как долго служба будет ожидать удаления файла клиента FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-363">**wait_option** Defines how long the service will wait for the FTP Client file delete.</span></span> <span data-ttu-id="ee2db-364">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ee2db-364">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ee2db-365">**timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-365">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ee2db-366">**TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос</span><span class="sxs-lookup"><span data-stu-id="ee2db-366">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-367">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-367">Return Values</span></span>

- <span data-ttu-id="ee2db-368">**NX_SUCCESS** (0x00) — FTP-файл успешно удален.</span><span class="sxs-lookup"><span data-stu-id="ee2db-368">**NX_SUCCESS** (0x00) Successful FTP file delete.</span></span>
- <span data-ttu-id="ee2db-369">**NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-369">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ee2db-370">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-370">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="ee2db-371">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-371">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ee2db-372">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-372">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-373">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-373">Allowed From</span></span>

<span data-ttu-id="ee2db-374">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-374">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-375">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-375">Example</span></span>

```C
/* Delete the file “my_file.txt” on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_delete(&my_client, “my_file.txt”, 200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a><span data-ttu-id="ee2db-376">nx_ftp_client_file_open</span><span class="sxs-lookup"><span data-stu-id="ee2db-376">nx_ftp_client_file_open</span></span>

<span data-ttu-id="ee2db-377">Открытие файла на FTP-сервере</span><span class="sxs-lookup"><span data-stu-id="ee2db-377">Opens file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-378">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-378">Prototype</span></span>

```C
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee2db-379">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-379">Description</span></span>

<span data-ttu-id="ee2db-380">Эта служба открывает указанный файл для чтения или записи на FTP-сервере, ранее подключенном к указанному экземпляру клиента.</span><span class="sxs-lookup"><span data-stu-id="ee2db-380">This service opens the specified file – for reading or writing – on the FTP Server previously connected to the specified Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-381">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-381">Input Parameters</span></span>

- <span data-ttu-id="ee2db-382">**client_ptr**: указатель на блок управления клиентом FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-382">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ee2db-383">**file_name**: имя файла для открытия</span><span class="sxs-lookup"><span data-stu-id="ee2db-383">**file_name** Name of file to open.</span></span>
- <span data-ttu-id="ee2db-384">**open_type**: **NX_FTP_OPEN_FOR_READ** или **NX_FTP_OPEN_FOR_WRITE**</span><span class="sxs-lookup"><span data-stu-id="ee2db-384">**open_type** Either **NX_FTP_OPEN_FOR_READ** or **NX_FTP_OPEN_FOR_WRITE**.</span></span>
- <span data-ttu-id="ee2db-385">**wait_option** определяет, как долго служба будет ожидать открытия файла клиента FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-385">**wait_option** Defines how long the service will wait for the FTP Client file open.</span></span> <span data-ttu-id="ee2db-386">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ee2db-386">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ee2db-387">**timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-387">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ee2db-388">**TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос</span><span class="sxs-lookup"><span data-stu-id="ee2db-388">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-389">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-389">Return Values</span></span>

- <span data-ttu-id="ee2db-390">**NX_SUCCESS** (0x00) — FTP-файл успешно открыт.</span><span class="sxs-lookup"><span data-stu-id="ee2db-390">**NX_SUCCESS** (0x00) Successful FTP file open.</span></span>
- <span data-ttu-id="ee2db-391">**NX_OPTION_ERROR** (0x0A) — недопустимый тип операции открытия.</span><span class="sxs-lookup"><span data-stu-id="ee2db-391">**NX_OPTION_ERROR** (0x0A) Invalid open type.</span></span>
- <span data-ttu-id="ee2db-392">**NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-392">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ee2db-393">**NX_FTP_NOT_CLOSED** (0xD6) — клиент FTP уже открыт.</span><span class="sxs-lookup"><span data-stu-id="ee2db-393">**NX_FTP_NOT_CLOSED** (0xD6) FTP Client is already opened.</span></span>
- <span data-ttu-id="ee2db-394">**NX_NO_FREE_PORTS** (0x45) — нет доступных TCP-портов для назначения.</span><span class="sxs-lookup"><span data-stu-id="ee2db-394">**NX_NO_FREE_PORTS** (0x45) No TCP ports available to assign</span></span>
- <span data-ttu-id="ee2db-395">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-395">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ee2db-396">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-396">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-397">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-397">Allowed From</span></span>

<span data-ttu-id="ee2db-398">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-398">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-399">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-399">Example</span></span>

```C
/* Open the file “my_file.txt” for reading on the FTP Server using the previously
    connected client “my_client.” */

status = nx_ftp_client_file_open(&my_client, “my_file.txt”, NX_FTP_OPEN_FOR_READ,
    200);

/* If status is NX_SUCCESS, the file “my_file.txt” on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a><span data-ttu-id="ee2db-400">nx_ftp_client_file_read</span><span class="sxs-lookup"><span data-stu-id="ee2db-400">nx_ftp_client_file_read</span></span>

<span data-ttu-id="ee2db-401">Чтение из файла</span><span class="sxs-lookup"><span data-stu-id="ee2db-401">Read from file</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-402">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-402">Prototype</span></span>

```C
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee2db-403">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-403">Description</span></span>

<span data-ttu-id="ee2db-404">Эта служба считывает пакет из ранее открытого файла.</span><span class="sxs-lookup"><span data-stu-id="ee2db-404">This service reads a packet from a previously opened file.</span></span> <span data-ttu-id="ee2db-405">Ее следует вызывать повторно, пока не будет получено состояние NX_FTP_END_OF_FILE.</span><span class="sxs-lookup"><span data-stu-id="ee2db-405">It should be called repetitively until a status of NX_FTP_END_OF_FILE is received.</span></span>

<span data-ttu-id="ee2db-406">Обратите внимание, что вызывающий объект не выделяет пакет для этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-406">Note that the caller does not allocate a packet for this service.</span></span>  <span data-ttu-id="ee2db-407">Он должен предоставлять только указатель на указатель пакета.</span><span class="sxs-lookup"><span data-stu-id="ee2db-407">It need only supply a pointer to a packet pointer.</span></span> <span data-ttu-id="ee2db-408">Эта служба обновит указатель на пакет так, чтобы он указывал на пакет, полученный из очереди получения сокета.</span><span class="sxs-lookup"><span data-stu-id="ee2db-408">This service will update that packet pointer to point to a packet retrieved from the socket receive queue.</span></span>  <span data-ttu-id="ee2db-409">Если возвращено успешное состояние, это означает, что пакет доступен, а вызывающий объект отвечает за освобождение пакета после завершения работы с ним.</span><span class="sxs-lookup"><span data-stu-id="ee2db-409">If a successful status is returned, that means there was a packet available, and it is the caller’s responsibility to release the packet when it is done with it.</span></span>

<span data-ttu-id="ee2db-410">Если возвращается ненулевое состояние (состояние ошибки или NX_FTP_END_OF_FILE), вызывающий объект не освобождает пакет.</span><span class="sxs-lookup"><span data-stu-id="ee2db-410">If a non-zero status (either an error status or NX_FTP_END_OF_FILE) is returned, the caller does not release the packet.</span></span> <span data-ttu-id="ee2db-411">Если указатель пакета имеет значение NULL, возникает ошибка.</span><span class="sxs-lookup"><span data-stu-id="ee2db-411">Otherwise, an error is generated when if the packet pointer is NULL.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-412">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-412">Input Parameters</span></span>

- <span data-ttu-id="ee2db-413">**client_ptr**: указатель на блок управления клиентом FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-413">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ee2db-414">**packet_ptr**: указатель на место назначения для сохраняемого указателя пакета данных</span><span class="sxs-lookup"><span data-stu-id="ee2db-414">**packet_ptr** Pointer to destination for the data packet pointer to be stored.</span></span> <span data-ttu-id="ee2db-415">В случае успеха данные пакета будут содержать часть файла или файл полностью.</span><span class="sxs-lookup"><span data-stu-id="ee2db-415">If successful, the packet some or all the contains of the file.</span></span>
- <span data-ttu-id="ee2db-416">**wait_option** определяет, как долго служба будет ожидать чтения файла клиента FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-416">**wait_option** Defines how long the service will wait for the FTP Client file read.</span></span> <span data-ttu-id="ee2db-417">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ee2db-417">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ee2db-418">**timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-418">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ee2db-419">**TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос</span><span class="sxs-lookup"><span data-stu-id="ee2db-419">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-420">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-420">Return Values</span></span>

- <span data-ttu-id="ee2db-421">**NX_SUCCESS** (0x00) — FTP-файл успешно считан.</span><span class="sxs-lookup"><span data-stu-id="ee2db-421">**NX_SUCCESS** (0x00) Successful FTP file read.</span></span>
- <span data-ttu-id="ee2db-422">**NX_FTP_NOT_OPEN** (0xD5) — клиент FTP не открыт.</span><span class="sxs-lookup"><span data-stu-id="ee2db-422">**NX_FTP_NOT_OPEN** (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="ee2db-423">**NX_FTP_END_OF_FILE** (0xD7) — конец условия файла.</span><span class="sxs-lookup"><span data-stu-id="ee2db-423">**NX_FTP_END_OF_FILE** (0xD7) End of file condition.</span></span>
- <span data-ttu-id="ee2db-424">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-424">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ee2db-425">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-425">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-426">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-426">Allowed From</span></span>

<span data-ttu-id="ee2db-427">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-427">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-428">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-428">Example</span></span>

```C
NX_PACKET   *my_packet;

/* Read a packet of data from the file “my_file.txt” that was previously opened
    from the client “my_client.” */

status = nx_ftp_client_file_read(&my_client, &my_packet, 200);

/* Check status.  */
if (status != NX_SUCCESS)
{
    error_counter++;
}
else
{
    /* Release packet when done with it. */
    nx_packet_release(my_packet);
}

/* If status is NX_SUCCESS, the packet pointer, “my_packet” points to the packet
    that contains the next bytes from the file. If the file is completely
    downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a><span data-ttu-id="ee2db-429">nx_ftp_client_file_rename</span><span class="sxs-lookup"><span data-stu-id="ee2db-429">nx_ftp_client_file_rename</span></span>

<span data-ttu-id="ee2db-430">Переименование файла на FTP-сервере</span><span class="sxs-lookup"><span data-stu-id="ee2db-430">Rename file on FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-431">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-431">Prototype</span></span>

```C
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
    CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee2db-432">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-432">Description</span></span>

<span data-ttu-id="ee2db-433">Эта служба переименовывает файл на FTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="ee2db-433">This service renames a file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-434">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-434">Input Parameters</span></span>

- <span data-ttu-id="ee2db-435">**client_ptr**: указатель на блок управления клиентом FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-435">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ee2db-436">**filename**: текущее имя файла</span><span class="sxs-lookup"><span data-stu-id="ee2db-436">**filename** Current name of file.</span></span>
- <span data-ttu-id="ee2db-437">**new_filename**: новое имя файла</span><span class="sxs-lookup"><span data-stu-id="ee2db-437">**new_filename** New name for file.</span></span>
- <span data-ttu-id="ee2db-438">**wait_option** определяет, как долго служба будет ожидать переименования файла клиента FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-438">**wait_option** Defines how long the service will wait for the FTP Client file rename.</span></span> <span data-ttu-id="ee2db-439">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ee2db-439">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ee2db-440">**timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-440">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ee2db-441">**TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос</span><span class="sxs-lookup"><span data-stu-id="ee2db-441">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-442">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-442">Return Values</span></span>

- <span data-ttu-id="ee2db-443">**NX_SUCCESS** (0x00) — FTP-файл успешно переименован.</span><span class="sxs-lookup"><span data-stu-id="ee2db-443">**NX_SUCCESS** (0x00) Successful FTP file rename.</span></span>
- <span data-ttu-id="ee2db-444">**NX_FTP_NOT_CONNECTED** (0xD3) — клиент FTP не подключен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-444">**NX_FTP_NOT_CONNECTED** (0xD3) FTP Client is not connected.</span></span>
- <span data-ttu-id="ee2db-445">**NX_FTP_EXPECTED_3XX_CODE** (0XDD) — ответ 3XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-445">**NX_FTP_EXPECTED_3XX_CODE** (0XDD) Did not receive 3XX (ok) response</span></span>
- <span data-ttu-id="ee2db-446">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) — ответ 2XX (OK) не получен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-446">**NX_FTP_EXPECTED_2XX_CODE** (0xDA) Did not get a 2XX (ok) response</span></span>
- <span data-ttu-id="ee2db-447">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-447">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ee2db-448">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-448">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-449">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-449">Allowed From</span></span>

<span data-ttu-id="ee2db-450">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-450">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-451">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-451">Example</span></span>

```C
/* Rename file “my_file.txt” to “new_file.txt” on the previously connected
    Client instance “my_client.” */

status = nx_ftp_client_file_rename(&my_client, “my_file.txt”, “new_file.txt”,
    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a><span data-ttu-id="ee2db-452">nx_ftp_client_file_write</span><span class="sxs-lookup"><span data-stu-id="ee2db-452">nx_ftp_client_file_write</span></span>

<span data-ttu-id="ee2db-453">Запись в файл</span><span class="sxs-lookup"><span data-stu-id="ee2db-453">Write to file</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-454">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-454">Prototype</span></span>

```C
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="ee2db-455">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-455">Description</span></span>

<span data-ttu-id="ee2db-456">Эта служба записывает пакет данных в ранее открытый файл на FTP-сервере.</span><span class="sxs-lookup"><span data-stu-id="ee2db-456">This service writes a packet of data to the previously opened file on the FTP Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-457">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-457">Input Parameters</span></span>

- <span data-ttu-id="ee2db-458">**client_ptr**: указатель на блок управления клиентом FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-458">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ee2db-459">**packet_ptr**: указатель пакета, содержащий данные для записи</span><span class="sxs-lookup"><span data-stu-id="ee2db-459">**packet_ptr** Packet pointer containing data to write.</span></span>
- <span data-ttu-id="ee2db-460">**wait_option** определяет, как долго служба будет ожидать записи в файл клиента FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-460">**wait_option** Defines how long the service will wait for the FTP Client file write.</span></span> <span data-ttu-id="ee2db-461">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="ee2db-461">The wait options are defined as follows:</span></span>
  - <span data-ttu-id="ee2db-462">**timeout value** (от 0x00000001 до 0xFFFFFFFE): числовое значение (1–0xFFFFFFFE), которое задает максимальное число тактов таймера для приостановки работы при ожидании ответа от FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-462">**timeout value** (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the FTP Server response.</span></span>
  - <span data-ttu-id="ee2db-463">**TX_WAIT_FOREVER** (0xFFFFFFFF): указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока FTP-сервер не ответит на запрос</span><span class="sxs-lookup"><span data-stu-id="ee2db-463">**TX_WAIT_FOREVER** (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a FTP Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-464">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-464">Return Values</span></span>

- <span data-ttu-id="ee2db-465">**NX_SUCCESS** (0x00) — запись в FTP-файл успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="ee2db-465">**NX_SUCCESS** (0x00) Successful FTP file write.</span></span>
- <span data-ttu-id="ee2db-466">**NX_FTP_NOT_OPEN** (0xD5) — клиент FTP не открыт.</span><span class="sxs-lookup"><span data-stu-id="ee2db-466">**NX_FTP_NOT_OPEN** (0xD5) FTP Client is not opened.</span></span>
- <span data-ttu-id="ee2db-467">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-467">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ee2db-468">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-468">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-469">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-469">Allowed From</span></span>

<span data-ttu-id="ee2db-470">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-470">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-471">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-471">Example</span></span>

```C
/* Write the data contained in “my_packet” to the previously opened file
    “my_file.txt”. */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a><span data-ttu-id="ee2db-472">nx_ftp_client_passive_mode_set</span><span class="sxs-lookup"><span data-stu-id="ee2db-472">nx_ftp_client_passive_mode_set</span></span>

<span data-ttu-id="ee2db-473">Включение или отключение пассивного режима передачи</span><span class="sxs-lookup"><span data-stu-id="ee2db-473">Enable or disable passive transfer mode</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-474">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-474">Prototype</span></span>

```C
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
    UINT passive_mode_enabled);
```

### <a name="description"></a><span data-ttu-id="ee2db-475">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-475">Description</span></span>

<span data-ttu-id="ee2db-476">Эта служба включает пассивный режим передачи, если для входных данных passive_mode_enabled задано NX_TRUE в ранее созданном экземпляре клиента FTP, так что последующие вызовы для чтения или записи файлов (RETR, STOR) или скачивания содержимого каталога (NLST) выполняются в режиме передачи.</span><span class="sxs-lookup"><span data-stu-id="ee2db-476">This service enables passive transfer mode if the passive_mode_enabled input is set to NX_TRUE on a previously created FTP Client instance such that subsequent calls to read or write files (RETR, STOR) or download a directory listing (NLST) are done in transfer mode.</span></span> <span data-ttu-id="ee2db-477">Чтобы отключить пассивный режим передачи и вернуться к заданному по умолчанию активному режиму передачи, вызовите эту функцию, для входных данных passive_mode_enabled которой задано NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="ee2db-477">To disable passive mode transfer and return to the default behavior of active transfer mode, call this function with the passive_mode_enabled input set to NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-478">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-478">Input Parameters</span></span>

- <span data-ttu-id="ee2db-479">**client_ptr**: указатель на блок управления клиентом FTP</span><span class="sxs-lookup"><span data-stu-id="ee2db-479">**ftp_client_ptr** Pointer to FTP Client control block.</span></span>
- <span data-ttu-id="ee2db-480">**passive_mode_enabled**: если задано значение NX_TRUE, пассивный режим включен</span><span class="sxs-lookup"><span data-stu-id="ee2db-480">**passive_mode_enabled** If set to NX_TRUE, passive mode is enabled.</span></span><br /><span data-ttu-id="ee2db-481">Если задано значение NX_FALSE, пассивный режим отключен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-481">If set to NX_FALSE, passive mode is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-482">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-482">Return Values</span></span>

- <span data-ttu-id="ee2db-483">**NX_SUCCESS** (0x00) — пассивный режим успешно задан.</span><span class="sxs-lookup"><span data-stu-id="ee2db-483">**NX_SUCCESS** (0x00) Successful passive mode set.</span></span>
- <span data-ttu-id="ee2db-484">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-484">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ee2db-485">NX_INVALID_PARAMETERS (0x4D) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="ee2db-485">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-486">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-486">Allowed From</span></span>

<span data-ttu-id="ee2db-487">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-487">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-488">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-488">Example</span></span>

```C
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a><span data-ttu-id="ee2db-489">nx_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="ee2db-489">nx_ftp_server_create</span></span>

<span data-ttu-id="ee2db-490">Создание FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-490">Create FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-491">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-491">Prototype</span></span>

```C
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address,
        UINT client_port, CHAR *name, CHAR *password,
        CHAR *extra_info),
    UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        ULONG client_ip_address, UINT client_port,
         CHAR *name, CHAR *password, CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="ee2db-492">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-492">Description</span></span>

<span data-ttu-id="ee2db-493">Эта служба создает экземпляр FTP-сервера в указанном и ранее созданном экземпляре IP для NetX.</span><span class="sxs-lookup"><span data-stu-id="ee2db-493">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="ee2db-494">Обратите внимание, что для начала работы FTP-сервер должен быть запущен с помощью вызова службы ***nx_ftp_server_start***.</span><span class="sxs-lookup"><span data-stu-id="ee2db-494">Note the FTP Server needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-495">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-495">Input Parameters</span></span>

- <span data-ttu-id="ee2db-496">**ftp_server_ptr**: указатель на блок управления FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-496">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="ee2db-497">**ftp_server_name**: имя FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-497">**ftp_server_name** Name of FTP Server.</span></span>
- <span data-ttu-id="ee2db-498">**ip_ptr**: указатель на связанный экземпляр IP для NetX</span><span class="sxs-lookup"><span data-stu-id="ee2db-498">**ip_ptr** Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="ee2db-499">Обратите внимание, что для экземпляра IP может существовать только один FTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="ee2db-499">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="ee2db-500">**media_ptr**: указатель на связанный экземпляр носителя FileX</span><span class="sxs-lookup"><span data-stu-id="ee2db-500">**media_ptr** Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="ee2db-501">**stack_ptr**: указатель на память области стека внутреннего потока FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-501">**stack_ptr** Pointer to memory for the internal FTP Server thread’s stack area.</span></span>
- <span data-ttu-id="ee2db-502">**stack_size**: размер области стека, заданный параметром *stack_ptr*</span><span class="sxs-lookup"><span data-stu-id="ee2db-502">**stack_size** Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="ee2db-503">**pool_ptr**: указатель на пул пакетов NetX по умолчанию</span><span class="sxs-lookup"><span data-stu-id="ee2db-503">**pool_ptr** Pointer to default NetX packet pool.</span></span> <span data-ttu-id="ee2db-504">Обратите внимание, что размер полезных данных пакетов в пуле должен быть достаточно большим, чтобы вмещать максимально длинное имя файла или путь.</span><span class="sxs-lookup"><span data-stu-id="ee2db-504">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="ee2db-505">**ftp_login**: указатель функции для функции входа в приложение</span><span class="sxs-lookup"><span data-stu-id="ee2db-505">**ftp_login** Function pointer to application’s login function.</span></span> <span data-ttu-id="ee2db-506">Эта функция предоставляет имя пользователя и пароль от клиента, запросившего подключение, а также адрес клиента в типе данных ULONG.</span><span class="sxs-lookup"><span data-stu-id="ee2db-506">This function is supplied the username and password from the Client requesting a connection, and the Client address in the ULONG data type.</span></span> <span data-ttu-id="ee2db-507">Если они являются допустимыми, функция входа в приложение должна вернуть NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="ee2db-507">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="ee2db-508">**ftp_logout**: указатель функции на функцию выхода из приложения</span><span class="sxs-lookup"><span data-stu-id="ee2db-508">**ftp_logout** Function pointer to application’s logout function.</span></span> <span data-ttu-id="ee2db-509">Эта функция предоставляет имя пользователя и пароль от клиента, запросившего отключение, а также адрес клиента в типе данных ULONG.</span><span class="sxs-lookup"><span data-stu-id="ee2db-509">This function is supplied the username and password from the Client requesting a disconnection, and the Client address in the ULONG data type.</span></span> <span data-ttu-id="ee2db-510">Если они являются допустимыми, функция входа в приложение должна вернуть NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="ee2db-510">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-511">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-511">Return Values</span></span>

- <span data-ttu-id="ee2db-512">**NX_SUCCESS** (0x00) — FTP-сервер успешно создан.</span><span class="sxs-lookup"><span data-stu-id="ee2db-512">**NX_SUCCESS** (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="ee2db-513">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-513">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-514">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-514">Allowed From</span></span>

<span data-ttu-id="ee2db-515">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-515">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-516">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-516">Example</span></span>

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nx_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nxd_ftp_server_create"></a><span data-ttu-id="ee2db-517">nxd_ftp_server_create</span><span class="sxs-lookup"><span data-stu-id="ee2db-517">nxd_ftp_server_create</span></span>

<span data-ttu-id="ee2db-518">Создание FTP-сервера с поддержкой IPv4 и IPv6</span><span class="sxs-lookup"><span data-stu-id="ee2db-518">Create FTP Server with IPv4 and IPv6 support</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-519">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-519">Prototype</span></span>

```C
UINT nxd_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
    CHAR *ftp_server_name, NX_IP *ip_ptr,
    FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
    NX_PACKET_POOL *pool_ptr,
    UINT (*ftp_login_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info),
    UINT (*ftp_logout_duo)(struct NX_FTP_SERVER_STRUCT *ftp_server_ptr,
        NXD_ADDRESS *client_ip_address, UINT client_port, CHAR *name,
        CHAR *password, CHAR *extra_info));
```

### <a name="description"></a><span data-ttu-id="ee2db-520">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-520">Description</span></span>

<span data-ttu-id="ee2db-521">Эта служба создает экземпляр FTP-сервера в указанном и ранее созданном экземпляре IP для NetX.</span><span class="sxs-lookup"><span data-stu-id="ee2db-521">This service creates an FTP Server instance on the specified and previously created NetX IP instance.</span></span> <span data-ttu-id="ee2db-522">Обратите внимание, что после создания FTP-сервера его все равно необходимо запустить с помощью вызова ***nx_ftp_server_start***, чтобы он начал работать.</span><span class="sxs-lookup"><span data-stu-id="ee2db-522">Note the FTP Server still needs to be started with a call to ***nx_ftp_server_start*** for it to begin operation after the Server is created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-523">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-523">Input Parameters</span></span>

- <span data-ttu-id="ee2db-524">**ftp_server_ptr**: указатель на блок управления FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-524">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>
- <span data-ttu-id="ee2db-525">**ftp_server_name**: имя FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-525">**ftp_server_name** Name of FTP Server.</span></span>
- <span data-ttu-id="ee2db-526">**ip_ptr**: указатель на связанный экземпляр IP для NetX</span><span class="sxs-lookup"><span data-stu-id="ee2db-526">**ip_ptr** Pointer to associated NetX IP instance.</span></span> <span data-ttu-id="ee2db-527">Обратите внимание, что для экземпляра IP может существовать только один FTP-сервер.</span><span class="sxs-lookup"><span data-stu-id="ee2db-527">Note there can only be one FTP Server for an IP instance.</span></span>
- <span data-ttu-id="ee2db-528">**media_ptr**: указатель на связанный экземпляр носителя FileX</span><span class="sxs-lookup"><span data-stu-id="ee2db-528">**media_ptr** Pointer to associated FileX media instance.</span></span>
- <span data-ttu-id="ee2db-529">**stack_ptr**: указатель на память области стека внутреннего потока FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-529">**stack_ptr** Pointer to memory for the internal FTP Server thread’s stack area.</span></span>
- <span data-ttu-id="ee2db-530">**stack_size**: размер области стека, заданный параметром *stack_ptr*</span><span class="sxs-lookup"><span data-stu-id="ee2db-530">**stack_size** Size of stack area specified by *stack_ptr*.</span></span>
- <span data-ttu-id="ee2db-531">**pool_ptr**: указатель на пул пакетов NetX по умолчанию</span><span class="sxs-lookup"><span data-stu-id="ee2db-531">**pool_ptr** Pointer to default NetX packet pool.</span></span> <span data-ttu-id="ee2db-532">Обратите внимание, что размер полезных данных пакетов в пуле должен быть достаточно большим, чтобы вмещать максимально длинное имя файла или путь.</span><span class="sxs-lookup"><span data-stu-id="ee2db-532">Note the payload size of packets in the pool must be large enough to accommodate the largest filename/path.</span></span>
- <span data-ttu-id="ee2db-533">**ftp_login_duo**: указатель функции на функцию входа в приложение</span><span class="sxs-lookup"><span data-stu-id="ee2db-533">**ftp_login_duo** Function pointer to application’s login function.</span></span> <span data-ttu-id="ee2db-534">Эта функция предоставляет имя пользователя и пароль от клиента, запросившего подключение, а также указатель на адрес клиента в типе данных NXD_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="ee2db-534">This function is supplied the username and password from the Client requesting a connection, and a pointer to the Client address in the NXD_ADDRESS data type.</span></span> <span data-ttu-id="ee2db-535">Если они являются допустимыми, функция входа в приложение должна вернуть NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="ee2db-535">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>
- <span data-ttu-id="ee2db-536">**ftp_logout_duo**: указатель функции на функцию выхода из приложения</span><span class="sxs-lookup"><span data-stu-id="ee2db-536">**ftp_logout_duo** Function pointer to application’s logout function.</span></span> <span data-ttu-id="ee2db-537">Эта функция предоставляет имя пользователя и пароль от клиента, запросившего отключение, а также указатель на адрес клиента в типе данных NXD_ADDRESS.</span><span class="sxs-lookup"><span data-stu-id="ee2db-537">This function is supplied the username and password from the Client requesting a disconnection, and a pointer to the Client address in the NXD_ADDRESS data type.</span></span> <span data-ttu-id="ee2db-538">Если они являются допустимыми, функция входа в приложение должна вернуть NX_SUCCESS.</span><span class="sxs-lookup"><span data-stu-id="ee2db-538">If this is valid, the application’s login function should return NX_SUCCESS.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-539">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-539">Return Values</span></span>

- <span data-ttu-id="ee2db-540">**NX_SUCCESS** (0x00) — FTP-сервер успешно создан.</span><span class="sxs-lookup"><span data-stu-id="ee2db-540">**NX_SUCCESS** (0x00) Successful FTP Server create.</span></span>
- <span data-ttu-id="ee2db-541">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-541">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ee2db-542">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-542">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-543">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-543">Allowed From</span></span>

<span data-ttu-id="ee2db-544">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-544">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-545">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-545">Example</span></span>

```C
/* Create the FTP Server “my_server” on the IP instance “ip_0” using the
    “ram_disk” media. */

status = nxd_ftp_server_create(&my_server, “My Server Name”, &ip_0, &ram_disk,
    stack_ptr, stack_size, &pool_0,
    my_duo_login, my_duo_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a><span data-ttu-id="ee2db-546">nx_ftp_server_delete</span><span class="sxs-lookup"><span data-stu-id="ee2db-546">nx_ftp_server_delete</span></span>

<span data-ttu-id="ee2db-547">Удаление FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-547">Delete FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-548">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-548">Prototype</span></span>

```C
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="ee2db-549">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-549">Description</span></span>

<span data-ttu-id="ee2db-550">Эта служба удаляет ранее созданный экземпляр FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="ee2db-550">This service deletes a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-551">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-551">Input Parameters</span></span>

- <span data-ttu-id="ee2db-552">**ftp_server_ptr**: указатель на блок управления FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-552">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-553">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-553">Return Values</span></span>

- <span data-ttu-id="ee2db-554">**NX_SUCCESS** (0x00) — FTP-сервер успешно удален.</span><span class="sxs-lookup"><span data-stu-id="ee2db-554">**NX_SUCCESS** (0x00) Successful FTP Server delete.</span></span>
- <span data-ttu-id="ee2db-555">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-555">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ee2db-556">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-556">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-557">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-557">Allowed From</span></span>

<span data-ttu-id="ee2db-558">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-558">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-559">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-559">Example</span></span>

```C
/* Delete the FTP Server “my_server”. */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a><span data-ttu-id="ee2db-560">nx_ftp_server_start</span><span class="sxs-lookup"><span data-stu-id="ee2db-560">nx_ftp_server_start</span></span>

<span data-ttu-id="ee2db-561">Запуск FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-561">Start FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-562">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-562">Prototype</span></span>

```C
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="ee2db-563">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-563">Description</span></span>

<span data-ttu-id="ee2db-564">Эта служба запускает ранее созданный экземпляр FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="ee2db-564">This service starts a previously created FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-565">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-565">Input Parameters</span></span>

- <span data-ttu-id="ee2db-566">**ftp_server_ptr**: указатель на блок управления FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-566">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-567">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-567">Return Values</span></span>

- <span data-ttu-id="ee2db-568">**NX_SUCCESS** (0x00) — FTP-сервер успешно запущен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-568">**NX_SUCCESS** (0x00) Successful FTP Server start.</span></span>
- <span data-ttu-id="ee2db-569">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-569">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-570">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-570">Allowed From</span></span>

<span data-ttu-id="ee2db-571">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-571">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-572">Например, .</span><span class="sxs-lookup"><span data-stu-id="ee2db-572">Example</span></span>

```C
/* Start the FTP Server “my_server”. */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a><span data-ttu-id="ee2db-573">nx_ftp_server_stop</span><span class="sxs-lookup"><span data-stu-id="ee2db-573">nx_ftp_server_stop</span></span>

<span data-ttu-id="ee2db-574">Остановка FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-574">Stop FTP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ee2db-575">Прототип</span><span class="sxs-lookup"><span data-stu-id="ee2db-575">Prototype</span></span>

```C
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a><span data-ttu-id="ee2db-576">Описание</span><span class="sxs-lookup"><span data-stu-id="ee2db-576">Description</span></span>

<span data-ttu-id="ee2db-577">Эта служба останавливает ранее созданный и запущенный экземпляр FTP-сервера.</span><span class="sxs-lookup"><span data-stu-id="ee2db-577">This service stops a previously created and started FTP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ee2db-578">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ee2db-578">Input Parameters</span></span>

- <span data-ttu-id="ee2db-579">**ftp_server_ptr**: указатель на блок управления FTP-сервера</span><span class="sxs-lookup"><span data-stu-id="ee2db-579">**ftp_server_ptr** Pointer to FTP Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="ee2db-580">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ee2db-580">Return Values</span></span>

- <span data-ttu-id="ee2db-581">**NX_SUCCESS** (0x00) — FTP-сервер успешно остановлен.</span><span class="sxs-lookup"><span data-stu-id="ee2db-581">**NX_SUCCESS** (0x00) Successful FTP Server stop.</span></span>
- <span data-ttu-id="ee2db-582">NX_PTR_ERROR (0x07) — недопустимый указатель FTP.</span><span class="sxs-lookup"><span data-stu-id="ee2db-582">NX_PTR_ERROR (0x07) Invalid FTP pointer.</span></span>
- <span data-ttu-id="ee2db-583">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ee2db-583">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ee2db-584">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ee2db-584">Allowed From</span></span>

<span data-ttu-id="ee2db-585">Потоки</span><span class="sxs-lookup"><span data-stu-id="ee2db-585">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ee2db-586">Пример</span><span class="sxs-lookup"><span data-stu-id="ee2db-586">Example</span></span>

```C
/* Stop the FTP Server “my_server”. */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
