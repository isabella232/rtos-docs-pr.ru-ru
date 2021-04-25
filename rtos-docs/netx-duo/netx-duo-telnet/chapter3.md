---
title: Глава 3. Описание служб NetX Duo Telnet для ОСРВ Azure
description: В этой главе приведено описание всех служб NetX Duo Telnet для ОСРВ Azure (см. ниже), перечисленных в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 991ec53aaba052b4f42da6e5a541151953121e76
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814528"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-telnet-services"></a><span data-ttu-id="30925-103">Глава 3. Описание служб NetX Duo Telnet для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="30925-103">Chapter 3 - Description of Azure RTOS NetX Duo Telnet services</span></span>

<span data-ttu-id="30925-104">В этой главе приведено описание всех служб NetX Duo Telnet для ОСРВ Azure (см. ниже), перечисленных в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="30925-104">This chapter contains a description of all Azure RTOS NetX Duo Telnet Services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="30925-105">В разделе "Возвращаемые значения" в описаниях API ниже значения, **ВЫДЕЛЕННЫЕ ЖИРНЫМ ШРИФТОМ**, не затрагиваются определением параметра **NX_DISABLE_ERROR_CHECKING**, который используется для отключения проверки ошибок API, в то время как значения, не выделенные жирным шрифтом, полностью отключаются.</span><span class="sxs-lookup"><span data-stu-id="30925-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="30925-106">**nx_telnet_client_connect**: *подключение клиента Telnet с помощью адреса IPv4*</span><span class="sxs-lookup"><span data-stu-id="30925-106">**nx_telnet_client_connect**: *Connect a Telnet Client with IPv4 address*</span></span>
- <span data-ttu-id="30925-107">**nxd_telnet_client_connect**: *подключение клиента Telnet IPv6 с помощью адреса IPv6*</span><span class="sxs-lookup"><span data-stu-id="30925-107">**nxd_telnet_client_connect**: *Connect an IPv6 Telnet Client with IPv6 address*</span></span>
- <span data-ttu-id="30925-108">**nx_telnet_client_create**: *создание клиента Telnet*</span><span class="sxs-lookup"><span data-stu-id="30925-108">**nx_telnet_client_create**: *Create a Telnet Client*</span></span>
- <span data-ttu-id="30925-109">**nx_telnet_client_delete**: *удаление клиента Telnet*</span><span class="sxs-lookup"><span data-stu-id="30925-109">**nx_telnet_client_delete**: *Delete a Telnet Client*</span></span>
- <span data-ttu-id="30925-110">**nx_telnet_client_disconnect**: *отключение клиента Telnet*</span><span class="sxs-lookup"><span data-stu-id="30925-110">**nx_telnet_client_disconnect**: *Disconnect a Telnet Client*</span></span>
- <span data-ttu-id="30925-111">**nx_telnet_client_packet_receive**: *получение пакета через клиент Telnet*</span><span class="sxs-lookup"><span data-stu-id="30925-111">**nx_telnet_client_packet_receive**: *Receive packet via Telnet Client*</span></span>
- <span data-ttu-id="30925-112">**nx_telnet_client_packet_send**: *отправка пакета через клиент Telnet*</span><span class="sxs-lookup"><span data-stu-id="30925-112">**nx_telnet_client_packet_send**: *Send packet via Telnet Client*</span></span>
- <span data-ttu-id="30925-113">**nx_telnet_server_create**: *создание сервера Telnet*</span><span class="sxs-lookup"><span data-stu-id="30925-113">**nx_telnet_server_create**: *Create a Telnet Server*</span></span>
- <span data-ttu-id="30925-114">**nx_telnet_server_delete**: *удаление сервера Telnet*</span><span class="sxs-lookup"><span data-stu-id="30925-114">**nx_telnet_server_delete**: *Delete a Telnet Server*</span></span>
- <span data-ttu-id="30925-115">**nx_telnet_server_disconnect**: *отключение сервера Telnet*</span><span class="sxs-lookup"><span data-stu-id="30925-115">**nx_telnet_server_disconnect**: *Disconnect a Telnet Client*</span></span>
- <span data-ttu-id="30925-116">**nx_telnet_server_get_open_connection_count**: *получение числа открытых соединений*</span><span class="sxs-lookup"><span data-stu-id="30925-116">**nx_telnet_server_get_open_connection_count**: *Retrieve the number of open connections*</span></span>
- <span data-ttu-id="30925-117">**nx_telnet_server_packet_send**: *отправка пакета через клиентское соединение*</span><span class="sxs-lookup"><span data-stu-id="30925-117">**nx_telnet_server_packet_send**: *Send packet through Client connection*</span></span>
- <span data-ttu-id="30925-118">**nx_telnet_server_packet_pool_set**: *задать пул пакетов в качестве пула пакетов сервера Telnet*</span><span class="sxs-lookup"><span data-stu-id="30925-118">**nx_telnet_server_packet_pool_set**: *Set packet pool as Telnet Server packet pool*</span></span>
- <span data-ttu-id="30925-119">**nx_telnet_server_start**: *запуск сервера Telnet*</span><span class="sxs-lookup"><span data-stu-id="30925-119">**nx_telnet_server_start**: *Start a Telnet Server*</span></span>
- <span data-ttu-id="30925-120">**nx_telnet_server_stop**: *остановка сервера Telnet*</span><span class="sxs-lookup"><span data-stu-id="30925-120">**nx_telnet_server_stop**: *Stop a Telnet Server*</span></span>

## <a name="nx_telnet_client_connect"></a><span data-ttu-id="30925-121">nx_telnet_client_connect</span><span class="sxs-lookup"><span data-stu-id="30925-121">nx_telnet_client_connect</span></span>

<span data-ttu-id="30925-122">Подключение клиента Telnet с помощью адреса IPv4</span><span class="sxs-lookup"><span data-stu-id="30925-122">Connect a Telnet Client with IPv4 address</span></span>

### <a name="prototype"></a><span data-ttu-id="30925-123">Прототип</span><span class="sxs-lookup"><span data-stu-id="30925-123">Prototype</span></span>

```c
UINT nx_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                              ULONG server_ip, UINT server_port, 
                              ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="30925-124">Описание</span><span class="sxs-lookup"><span data-stu-id="30925-124">Description</span></span>

<span data-ttu-id="30925-125">Эта служба пытается подключить ранее созданный экземпляр клиента Telnet к серверу по указанному IP-адресу и порту с использованием адреса IPv4 для сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-125">This service attempts to connect the previously created Telnet Client instance to the Server at the specified IP and port using an IPv4 address for the Telnet Server.</span></span> <span data-ttu-id="30925-126">Эта служба фактически вставляет IP-адрес сервера ULONG в блок управления NXD_ADDRESS и устанавливает для версии IP значение 4 перед вызовом службы *nxd_telnet_client_connect*, описанной ниже.</span><span class="sxs-lookup"><span data-stu-id="30925-126">This service actually inserts the ULONG server IP address in an NXD_ADDRESS control block and sets the IP version to 4 before calling the *nxd_telnet_client_connect* service described below.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30925-127">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="30925-127">Input Parameters</span></span>

- <span data-ttu-id="30925-128">**client_ptr**: указатель на блок управления клиента Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-128">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="30925-129">**server_ip**: IPv4-адрес сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-129">**server_ip**: IPv4 Address of the Telnet Server.</span></span>
- <span data-ttu-id="30925-130">**server_port**: TCP-порт сервера (сервер Telnet работает на порту 23).</span><span class="sxs-lookup"><span data-stu-id="30925-130">**server_port**: TCP Port of Server (Telnet Server is port 23).</span></span>
- <span data-ttu-id="30925-131">**wait_option**: определяет, как долго служба будет ожидать подключения клиента Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-131">**wait_option**: Defines how long the service will wait for the Telnet Client connect.</span></span> <span data-ttu-id="30925-132">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="30925-132">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="30925-133">**значение времени ожидания**: (от 0x00000001 до 0xFFFFFFFE). Указание числового значения (1–0xFFFFFFFE) задает максимальное число тактов таймера для приостановки работы при ожидании ответа сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-133">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="30925-134">**TX_WAIT_FOREVER**: (0xFFFFFFFF). Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер Telnet не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="30925-134">**TX_WAIT_FOREVER**: (0xFFFFFFFF)Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="30925-135">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="30925-135">Return Values</span></span>

- <span data-ttu-id="30925-136">**NX_SUCCESS**: (0x00) успешное подключение клиента.</span><span class="sxs-lookup"><span data-stu-id="30925-136">**NX_SUCCESS**: (0x00) Successful Client connect.</span></span>
- <span data-ttu-id="30925-137">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) клиент уже подключен.</span><span class="sxs-lookup"><span data-stu-id="30925-137">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client already connected.</span></span>
- <span data-ttu-id="30925-138">NX_PTR_ERROR: (0x07) недопустимый указатель клиента.</span><span class="sxs-lookup"><span data-stu-id="30925-138">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="30925-139">NX_IP_ADDRESS_ERROR: (0x21) недопустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="30925-139">NX_IP_ADDRESS_ERROR: (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="30925-140">NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="30925-140">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30925-141">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="30925-141">Allowed From</span></span>

<span data-ttu-id="30925-142">Потоки</span><span class="sxs-lookup"><span data-stu-id="30925-142">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30925-143">Например, .</span><span class="sxs-lookup"><span data-stu-id="30925-143">Example</span></span>

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IP address 1.2.3.4 and port 23.  */
status =  nx_telnet_client_connect(&my_client, IP_ADDRESS(1,2,3,4), 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nxd_telnet_client_connect"></a><span data-ttu-id="30925-144">nxd_telnet_client_connect</span><span class="sxs-lookup"><span data-stu-id="30925-144">nxd_telnet_client_connect</span></span>

<span data-ttu-id="30925-145">Подключение клиента Telnet с помощью адреса IPv6 или IPv4</span><span class="sxs-lookup"><span data-stu-id="30925-145">Connect a Telnet Client with IPv6 or IPv4 address</span></span>

### <a name="prototype"></a><span data-ttu-id="30925-146">Прототип</span><span class="sxs-lookup"><span data-stu-id="30925-146">Prototype</span></span>

```c
UINT nxd_telnet_client_connect(NX_TELNET_CLIENT *client_ptr, 
                               NXD_ADDRESS *server_ip_address, 
                               UINT server_port, 
                               ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="30925-147">Описание</span><span class="sxs-lookup"><span data-stu-id="30925-147">Description</span></span>

<span data-ttu-id="30925-148">Эта служба пытается подключить ранее созданный экземпляр клиента Telnet к серверу по указанному IP-адресу и порту с использованием адреса IPv6 сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-148">This service attempts to connect the previously created Telnet Client instance to the Server at the specified IP and port using the Telnet Server’s IPv6 address.</span></span> <span data-ttu-id="30925-149">Эта служба может принимать адрес IPv4 или IPv6, но он должен содержаться в переменной NXD_ADDRESS *server_ip_address*.</span><span class="sxs-lookup"><span data-stu-id="30925-149">This service can take an IPv4 or an IPv6 address but must be contained in the NXD_ADDRESS variable *server_ip_address.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30925-150">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="30925-150">Input Parameters</span></span>

- <span data-ttu-id="30925-151">**client_ptr**: указатель на блок управления клиента Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-151">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="30925-152">**server_ip_address**: IP-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="30925-152">**server_ip_address**: IP Address of Server.</span></span>
- <span data-ttu-id="30925-153">**server_port**: TCP-порт сервера (сервер Telnet работает на порту 23).</span><span class="sxs-lookup"><span data-stu-id="30925-153">**server_port**: TCP Port of Server (Telnet Server is port 23).</span></span>
- <span data-ttu-id="30925-154">**wait_option**: определяет, как долго служба будет ожидать подключения клиента Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-154">**wait_option**: Defines how long the service will wait for the Telnet Client connect.</span></span> <span data-ttu-id="30925-155">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="30925-155">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="30925-156">**значение времени ожидания**: (от 0x00000001 до 0xFFFFFFFE). Указание числового значения (1–0xFFFFFFFE) задает максимальное число тактов таймера для приостановки работы при ожидании ответа сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-156">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="30925-157">**TX_WAIT_FOREVER**: (0xFFFFFFFF). Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер Telnet не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="30925-157">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="30925-158">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="30925-158">Return Values</span></span>

- <span data-ttu-id="30925-159">**NX_SUCCESS**: (0x00) успешное подключение клиента.</span><span class="sxs-lookup"><span data-stu-id="30925-159">**NX_SUCCESS**: (0x00) Successful Client connect.</span></span>
- <span data-ttu-id="30925-160">**NX_TELNET_ERROR**: (0xF0) ошибка подключения клиента.</span><span class="sxs-lookup"><span data-stu-id="30925-160">**NX_TELNET_ERROR**: (0xF0) Client connect error.</span></span>
- <span data-ttu-id="30925-161">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) клиент уже подключен.</span><span class="sxs-lookup"><span data-stu-id="30925-161">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client already connected.</span></span>
- <span data-ttu-id="30925-162">NX_PTR_ERROR: (0x07) недопустимый указатель клиента.</span><span class="sxs-lookup"><span data-stu-id="30925-162">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="30925-163">NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="30925-163">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="30925-164">NX_TELNET_INVALID_PARAMETER: (0xF5) недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="30925-164">NX_TELNET_INVALID_PARAMETER: (0xF5) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30925-165">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="30925-165">Allowed From</span></span>

<span data-ttu-id="30925-166">Потоки</span><span class="sxs-lookup"><span data-stu-id="30925-166">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30925-167">Например, .</span><span class="sxs-lookup"><span data-stu-id="30925-167">Example</span></span>

```c
/* Connect the Telnet Client instance “my_client” to the Server at 
   IPv6 address 20010db1:0:f101::101 and port 23.  */
status =  nxd_telnet_client_connect(&my_client, &server_ip_address, 23, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   connected to the Telnet Server.  */
```

## <a name="nx_telnet_client_create"></a><span data-ttu-id="30925-168">nx_telnet_client_create</span><span class="sxs-lookup"><span data-stu-id="30925-168">nx_telnet_client_create</span></span>

<span data-ttu-id="30925-169">Создание клиента Telnet</span><span class="sxs-lookup"><span data-stu-id="30925-169">Create a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="30925-170">Прототип</span><span class="sxs-lookup"><span data-stu-id="30925-170">Prototype</span></span>

```c
UINT nx_telnet_client_create(NX_TELNET_CLIENT *client_ptr, 
                             CHAR *client_name, NX_IP *ip_ptr, 
                             ULONG window_size);
```

### <a name="description"></a><span data-ttu-id="30925-171">Описание</span><span class="sxs-lookup"><span data-stu-id="30925-171">Description</span></span>

<span data-ttu-id="30925-172">Эта служба создает экземпляр клиента Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-172">This service creates a Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30925-173">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="30925-173">Input Parameters</span></span>

- <span data-ttu-id="30925-174">**client_ptr**: указатель на блок управления клиента Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-174">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="30925-175">**client_name**: имя экземпляра клиента.</span><span class="sxs-lookup"><span data-stu-id="30925-175">**client_name**: Name of Client instance.</span></span>
- <span data-ttu-id="30925-176">**ip_ptr**: указатель на экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="30925-176">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="30925-177">**window_size**: размер окна приема TCP для этого клиента.</span><span class="sxs-lookup"><span data-stu-id="30925-177">**window_size**: Size of TCP receive window for this Client.</span></span>

### <a name="return-values"></a><span data-ttu-id="30925-178">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="30925-178">Return Values</span></span>

- <span data-ttu-id="30925-179">**NX_SUCCESS**: (0x00) успешное создание клиента.</span><span class="sxs-lookup"><span data-stu-id="30925-179">**NX_SUCCESS**: (0x00) Successful Client create.</span></span>
- <span data-ttu-id="30925-180">**NX_TELNET_ERROR**: (0xF0) ошибка при создании сокета.</span><span class="sxs-lookup"><span data-stu-id="30925-180">**NX_TELNET_ERROR**: (0xF0) Socket create error.</span></span>
- <span data-ttu-id="30925-181">NX_PTR_ERROR: (0x07) недопустимый указатель клиента или IP.</span><span class="sxs-lookup"><span data-stu-id="30925-181">NX_PTR_ERROR: (0x07) Invalid Client or IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30925-182">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="30925-182">Allowed From</span></span>

<span data-ttu-id="30925-183">Инициализация, Потоки</span><span class="sxs-lookup"><span data-stu-id="30925-183">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="30925-184">Например, .</span><span class="sxs-lookup"><span data-stu-id="30925-184">Example</span></span>

```c
/* Create the Telnet Client instance “my_client” on the IP instance “ip_0”.  */
status =  nx_telnet_client_create(&my_client, “My Telnet Client”, &ip_0, 2048);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   created.  */
```
## <a name="nx_telnet_client_delete"></a><span data-ttu-id="30925-185">nx_telnet_client_delete</span><span class="sxs-lookup"><span data-stu-id="30925-185">nx_telnet_client_delete</span></span>

<span data-ttu-id="30925-186">Удаление клиента Telnet</span><span class="sxs-lookup"><span data-stu-id="30925-186">Delete a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="30925-187">Прототип</span><span class="sxs-lookup"><span data-stu-id="30925-187">Prototype</span></span>

```c
UINT nx_telnet_client_delete(NX_TELNET_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="30925-188">Описание</span><span class="sxs-lookup"><span data-stu-id="30925-188">Description</span></span>

<span data-ttu-id="30925-189">Эта служба удаляет ранее созданный экземпляр клиента Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-189">This service deletes a previously created Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30925-190">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="30925-190">Input Parameters</span></span>

- <span data-ttu-id="30925-191">**client_ptr**: указатель на блок управления клиента Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-191">**client_ptr**: Pointer to Telnet Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="30925-192">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="30925-192">Return Values</span></span>

- <span data-ttu-id="30925-193">**NX_SUCCESS**: (0x00) успешное удаление клиента.</span><span class="sxs-lookup"><span data-stu-id="30925-193">**NX_SUCCESS**: (0x00) Successful Client delete.</span></span>
- <span data-ttu-id="30925-194">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) клиент все еще подключен.</span><span class="sxs-lookup"><span data-stu-id="30925-194">**NX_TELNET_NOT_DISCONNECTED**: (0xF4) Client still connected.</span></span>
- <span data-ttu-id="30925-195">NX_PTR_ERROR: (0x07) недопустимый указатель клиента.</span><span class="sxs-lookup"><span data-stu-id="30925-195">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="30925-196">NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="30925-196">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30925-197">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="30925-197">Allowed From</span></span>

<span data-ttu-id="30925-198">Потоки</span><span class="sxs-lookup"><span data-stu-id="30925-198">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30925-199">Например, .</span><span class="sxs-lookup"><span data-stu-id="30925-199">Example</span></span>

```c
/* Delete the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_delete(&my_client);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   deleted.  */
```

## <a name="nx_telnet_client_disconnect"></a><span data-ttu-id="30925-200">nx_telnet_client_disconnect</span><span class="sxs-lookup"><span data-stu-id="30925-200">nx_telnet_client_disconnect</span></span>

<span data-ttu-id="30925-201">Отключение клиента Telnet</span><span class="sxs-lookup"><span data-stu-id="30925-201">Disconnect a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="30925-202">Прототип</span><span class="sxs-lookup"><span data-stu-id="30925-202">Prototype</span></span>

```c
UINT nx_telnet_client_disconnect(NX_TELNET_CLIENT *client_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="30925-203">Описание</span><span class="sxs-lookup"><span data-stu-id="30925-203">Description</span></span>

<span data-ttu-id="30925-204">Эта служба отключает ранее подключенный экземпляр клиента Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-204">This service disconnects a previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30925-205">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="30925-205">Input Parameters</span></span>

- <span data-ttu-id="30925-206">**client_ptr**: указатель на блок управления клиента Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-206">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="30925-207">**wait_option**: определяет, как долго служба будет ожидать отключения клиента Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-207">**wait_option**: Defines how long the service will wait for the Telnet Client disconnect.</span></span> <span data-ttu-id="30925-208">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="30925-208">The wait options are defined as follows:</span></span>

    - <span data-ttu-id="30925-209">**значение времени ожидания**: (от 0x00000001 до 0xFFFFFFFE). Указание числового значения (1–0xFFFFFFFE) задает максимальное число тактов таймера для приостановки работы при ожидании ответа сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-209">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="30925-210">**TX_WAIT_FOREVER**: (0xFFFFFFFF). Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер Telnet не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="30925-210">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="30925-211">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="30925-211">Return Values</span></span>

- <span data-ttu-id="30925-212">**NX_SUCCESS**: (0x00) успешное отключение клиента.</span><span class="sxs-lookup"><span data-stu-id="30925-212">**NX_SUCCESS**: (0x00) Successful Client disconnect.</span></span>
- <span data-ttu-id="30925-213">**NX_TELNET_NOT_CONNECTED**: (0xF3) клиент не подключен.</span><span class="sxs-lookup"><span data-stu-id="30925-213">**NX_TELNET_NOT_CONNECTED**: (0xF3) Client not connected.</span></span>
- <span data-ttu-id="30925-214">NX_PTR_ERROR: (0x07) недопустимый указатель клиента.</span><span class="sxs-lookup"><span data-stu-id="30925-214">NX_PTR_ERROR: (0x07) Invalid Client pointer.</span></span>
- <span data-ttu-id="30925-215">NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="30925-215">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="30925-216">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="30925-216">Allowed From</span></span>

<span data-ttu-id="30925-217">Потоки</span><span class="sxs-lookup"><span data-stu-id="30925-217">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30925-218">Например, .</span><span class="sxs-lookup"><span data-stu-id="30925-218">Example</span></span>

```c

/* Disconnect the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_disconnect(&my_client, 100);

/* If status is NX_SUCCESS the Telnet Client instance was successfully
   disconnected.  */
```

## <a name="nx_telnet_client_packet_receive"></a><span data-ttu-id="30925-219">nx_telnet_client_packet_receive</span><span class="sxs-lookup"><span data-stu-id="30925-219">nx_telnet_client_packet_receive</span></span>

<span data-ttu-id="30925-220">Получение пакета через клиент Telnet</span><span class="sxs-lookup"><span data-stu-id="30925-220">Receive packet via Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="30925-221">Прототип</span><span class="sxs-lookup"><span data-stu-id="30925-221">Prototype</span></span>

```c
UINT nx_telnet_client_packet_receive(NX_TELNET_CLIENT *client_ptr, 
                                     NX_PACKET **packet_ptr, 
                                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="30925-222">Описание</span><span class="sxs-lookup"><span data-stu-id="30925-222">Description</span></span>

<span data-ttu-id="30925-223">Эта служба получает пакет из ранее подключенного экземпляра клиента Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-223">This service receives a packet from the previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30925-224">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="30925-224">Input Parameters</span></span>

- <span data-ttu-id="30925-225">**client_ptr**: указатель на блок управления клиента Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-225">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="30925-226">**packet_ptr**: указатель на место назначения для полученного пакета.</span><span class="sxs-lookup"><span data-stu-id="30925-226">**packet_ptr**: Pointer to the destination for the received packet.</span></span>
- <span data-ttu-id="30925-227">**wait_option**: определяет, как долго служба будет ожидать получения пакета от клиента Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-227">**wait_option**: Defines how long the service will wait for the Telnet Client packet receive.</span></span> <span data-ttu-id="30925-228">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="30925-228">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="30925-229">**значение времени ожидания**: (от 0x00000001 до 0xFFFFFFFE). Указание числового значения (1–0xFFFFFFFE) задает максимальное число тактов таймера для приостановки работы при ожидании ответа сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-229">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="30925-230">**TX_WAIT_FOREVER**: (0xFFFFFFFF). Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер Telnet не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="30925-230">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="30925-231">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="30925-231">Return Values</span></span>

- <span data-ttu-id="30925-232">**NX_SUCCESS**: (0x00) получение пакета от клиента успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="30925-232">**NX_SUCCESS**: (0x00) Successful Client packet receive.</span></span>
- <span data-ttu-id="30925-233">NX_PTR_ERROR: (0x07) Недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="30925-233">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="30925-234">NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="30925-234">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30925-235">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="30925-235">Allowed From</span></span>

<span data-ttu-id="30925-236">Потоки</span><span class="sxs-lookup"><span data-stu-id="30925-236">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30925-237">Например, .</span><span class="sxs-lookup"><span data-stu-id="30925-237">Example</span></span>

```c

/* Receive a packet from the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_receive(&my_client, &my_packet, 100);

/* If status is NX_SUCCESS the “my_packet” pointer contains data received from
   the Telnet Client connection.  */
```
## <a name="nx_telnet_client_packet_send"></a><span data-ttu-id="30925-238">nx_telnet_client_packet_send</span><span class="sxs-lookup"><span data-stu-id="30925-238">nx_telnet_client_packet_send</span></span>

<span data-ttu-id="30925-239">Отправка пакета через клиент Telnet</span><span class="sxs-lookup"><span data-stu-id="30925-239">Send packet via Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="30925-240">Прототип</span><span class="sxs-lookup"><span data-stu-id="30925-240">Prototype</span></span>

```c
UINT nx_telnet_client_packet_send(NX_TELNET_CLIENT *client_ptr, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="30925-241">Описание</span><span class="sxs-lookup"><span data-stu-id="30925-241">Description</span></span>

<span data-ttu-id="30925-242">Эта служба отправляет пакет через ранее подключенный экземпляра клиента Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-242">This service sends a packet through the previously connected Telnet Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30925-243">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="30925-243">Input Parameters</span></span>

- <span data-ttu-id="30925-244">**client_ptr**: указатель на блок управления клиента Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-244">**client_ptr**: Pointer to Telnet Client control block.</span></span>
- <span data-ttu-id="30925-245">**packet_ptr**: указатель на пакет для отправки.</span><span class="sxs-lookup"><span data-stu-id="30925-245">**packet_ptr**: Pointer to the packet to send.</span></span>
- <span data-ttu-id="30925-246">**wait_option**: определяет, как долго служба будет ожидать отправки пакета в клиент Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-246">**wait_option**: Defines how long the service will wait for the Telnet Client packet send.</span></span> <span data-ttu-id="30925-247">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="30925-247">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="30925-248">**значение времени ожидания**: (от 0x00000001 до 0xFFFFFFFE). Указание числового значения (1–0xFFFFFFFE) задает максимальное число тактов таймера для приостановки работы при ожидании ответа сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-248">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="30925-249">**TX_WAIT_FOREVER**: (0xFFFFFFFF). Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер Telnet не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="30925-249">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span>

### <a name="return-values"></a><span data-ttu-id="30925-250">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="30925-250">Return Values</span></span>

- <span data-ttu-id="30925-251">**NX_SUCCESS**: (0x00) отправка пакета в клиент успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="30925-251">**NX_SUCCESS**: (0x00) Successful Client packet send.</span></span>
- <span data-ttu-id="30925-252">**NX_TELNET_ERROR**: (0xF0) не удалось отправить пакет, вызывающий объект отвечает за освобождение пакета.</span><span class="sxs-lookup"><span data-stu-id="30925-252">**NX_TELNET_ERROR**: (0xF0) Send packet failed – caller is responsible for releasing the packet.</span></span>
- <span data-ttu-id="30925-253">NX_PTR_ERROR: (0x07) Недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="30925-253">NX_PTR_ERROR: (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="30925-254">NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="30925-254">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30925-255">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="30925-255">Allowed From</span></span>

<span data-ttu-id="30925-256">Потоки</span><span class="sxs-lookup"><span data-stu-id="30925-256">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30925-257">Например, .</span><span class="sxs-lookup"><span data-stu-id="30925-257">Example</span></span>

```c
/* Send a packet via the Telnet Client instance “my_client”.  */
status =  nx_telnet_client_packet_send(&my_client, my_packet, 100);
/* If status is NX_SUCCESS the packet was successfully sent.  */

```

## <a name="nx_telnet_server_create"></a><span data-ttu-id="30925-258">nx_telnet_server_create</span><span class="sxs-lookup"><span data-stu-id="30925-258">nx_telnet_server_create</span></span>

<span data-ttu-id="30925-259">Создание сервера Telnet</span><span class="sxs-lookup"><span data-stu-id="30925-259">Create a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="30925-260">Прототип</span><span class="sxs-lookup"><span data-stu-id="30925-260">Prototype</span></span>

```c
UINT nx_telnet_server_create(NX_TELNET_SERVER *server_ptr, CHAR *server_name, NX_IP *ip_ptr, 
                             VOID *stack_ptr, ULONG stack_size, 
                             void (*new_connection)(struct NX_TELNET_SERVER_STRUCT*telnet_server_ptr, 
                                                    UINT logical_connection), 
                             void (*receive_data)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                  UINT logical_connection, NX_PACKET *packet_ptr), 
                             void (*connection_end)(struct NX_TELNET_SERVER_STRUCT *telnet_server_ptr, 
                                                    UINT logical_connection));

```

### <a name="description"></a><span data-ttu-id="30925-261">Описание</span><span class="sxs-lookup"><span data-stu-id="30925-261">Description</span></span>

<span data-ttu-id="30925-262">Эта служба создает экземпляр сервера Telnet в указанном экземпляре IP.</span><span class="sxs-lookup"><span data-stu-id="30925-262">This service creates a Telnet Server instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30925-263">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="30925-263">Input Parameters</span></span>

- <span data-ttu-id="30925-264">**server_ptr**: указатель на управляющий блок сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-264">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="30925-265">**server_name**: имя экземпляра сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-265">**server_name**: Name of Telnet Server instance.</span></span>
- <span data-ttu-id="30925-266">**ip_ptr**: указатель на связанный экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="30925-266">**ip_ptr**: Pointer to associated IP instance.</span></span>
- <span data-ttu-id="30925-267">**stack_ptr**: указатель на стек для внутреннего потока сервера.</span><span class="sxs-lookup"><span data-stu-id="30925-267">**stack_ptr**: Pointer to stack for the internal Server thread.</span></span>
- <span data-ttu-id="30925-268">**sack_size**: размер стека в байтах.</span><span class="sxs-lookup"><span data-stu-id="30925-268">**sack_size**: Size of the stack, in bytes.</span></span>
- <span data-ttu-id="30925-269">**new_connection**: указатель функции подпрограммы обратного вызова приложения.</span><span class="sxs-lookup"><span data-stu-id="30925-269">**new_connection**: Application callback routine function pointer.</span></span> <span data-ttu-id="30925-270">Эта подпрограмма вызывается всякий раз, когда сервер обнаруживает новый запрос на подключение клиента Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-270">This routine is called whenever a new Telnet Client connection request is detected by the Server.</span></span>
- <span data-ttu-id="30925-271">**receive_data**: указатель функции подпрограммы обратного вызова приложения.</span><span class="sxs-lookup"><span data-stu-id="30925-271">**receive_data**: Application callback routine function pointer.</span></span> <span data-ttu-id="30925-272">Эта подпрограмма вызывается при наличии в соединении новых данных клиента Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-272">This routine is called whenever a new Telnet Client data is present on the connection.</span></span> <span data-ttu-id="30925-273">Эта подпрограмма отвечает за освобождение пакета.</span><span class="sxs-lookup"><span data-stu-id="30925-273">This routine is responsible for releasing the packet.</span></span>
- <span data-ttu-id="30925-274">**end_connection**: указатель функции подпрограммы обратного вызова приложения.</span><span class="sxs-lookup"><span data-stu-id="30925-274">**end_connection**: Application callback routine function pointer.</span></span> <span data-ttu-id="30925-275">Эта подпрограмма вызывается при каждом отключении клиента Telnet, инициализированном клиентом, или истечении времени ожидания подключения клиента (истекло время ожидания действий).</span><span class="sxs-lookup"><span data-stu-id="30925-275">This routine is called whenever a Telnet Client connection is disconnected by the Client or the Client connection times out (“activity timeout” expires).</span></span> <span data-ttu-id="30925-276">Сервер также может отключиться через службу *nx_telnet_server_disconnect*, описанную ниже.</span><span class="sxs-lookup"><span data-stu-id="30925-276">The Server can also disconnect via the *nx_telnet_server_disconnect* service described below.</span></span>

### <a name="return-values"></a><span data-ttu-id="30925-277">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="30925-277">Return Values</span></span>

- <span data-ttu-id="30925-278">**NX_SUCCESS**: (0x00) успешное создание сервера.</span><span class="sxs-lookup"><span data-stu-id="30925-278">**NX_SUCCESS**: (0x00) Successful Server create.</span></span>
- <span data-ttu-id="30925-279">NX_PTR_ERROR: (0x07) недопустимые указатели сервера, IP, стека или обратного вызова приложения.</span><span class="sxs-lookup"><span data-stu-id="30925-279">NX_PTR_ERROR: (0x07) Invalid Server, IP, stack, or application callback pointers.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30925-280">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="30925-280">Allowed From</span></span>

<span data-ttu-id="30925-281">Инициализация, Потоки</span><span class="sxs-lookup"><span data-stu-id="30925-281">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="30925-282">Например, .</span><span class="sxs-lookup"><span data-stu-id="30925-282">Example</span></span>

```c
/* Create a Telnet Server instance “my_server”.  */
status =  nx_telnet_server_create(&my_server, "Telnet Server", &ip_0, 
                                   pointer, 2048, telnet_new_connection, 
                                   telnet_receive_data, telnet_connection_end);


/* If status is NX_SUCCESS the Telnet Server was successfully created.  */
```
## <a name="nx_telnet_server_delete"></a><span data-ttu-id="30925-283">nx_telnet_server_delete</span><span class="sxs-lookup"><span data-stu-id="30925-283">nx_telnet_server_delete</span></span>

<span data-ttu-id="30925-284">Удаление сервера Telnet</span><span class="sxs-lookup"><span data-stu-id="30925-284">Delete a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="30925-285">Прототип</span><span class="sxs-lookup"><span data-stu-id="30925-285">Prototype</span></span>

```c
UINT nx_telnet_server_delete(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="30925-286">Описание</span><span class="sxs-lookup"><span data-stu-id="30925-286">Description</span></span>

<span data-ttu-id="30925-287">Эта служба удаляет ранее созданный экземпляр сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-287">This service deletes a previously created Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30925-288">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="30925-288">Input Parameters</span></span>

- <span data-ttu-id="30925-289">**server_ptr**: указатель на управляющий блок сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-289">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="30925-290">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="30925-290">Return Values</span></span>

- <span data-ttu-id="30925-291">**NX_SUCCESS**: (0x00) успешное удаление сервера.</span><span class="sxs-lookup"><span data-stu-id="30925-291">**NX_SUCCESS**: (0x00) Successful Server delete.</span></span>
- <span data-ttu-id="30925-292">NX_PTR_ERROR: (0x07) недопустимый указатель сервера.</span><span class="sxs-lookup"><span data-stu-id="30925-292">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="30925-293">NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="30925-293">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30925-294">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="30925-294">Allowed From</span></span>

<span data-ttu-id="30925-295">Потоки</span><span class="sxs-lookup"><span data-stu-id="30925-295">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30925-296">Например, .</span><span class="sxs-lookup"><span data-stu-id="30925-296">Example</span></span>

```c
/* Delete the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_delete(&my_server);

/* If status is NX_SUCCESS the Telnet Server was successfully deleted.  */
```

## <a name="nx_telnet_server_disconnect"></a><span data-ttu-id="30925-297">nx_telnet_server_disconnect</span><span class="sxs-lookup"><span data-stu-id="30925-297">nx_telnet_server_disconnect</span></span>

<span data-ttu-id="30925-298">Отключение клиента Telnet</span><span class="sxs-lookup"><span data-stu-id="30925-298">Disconnect a Telnet Client</span></span>

### <a name="prototype"></a><span data-ttu-id="30925-299">Прототип</span><span class="sxs-lookup"><span data-stu-id="30925-299">Prototype</span></span>

```c
UINT nx_telnet_server_disconnect(NX_TELNET_SERVER *server_ptr, UINT logical_connection);
```

### <a name="description"></a><span data-ttu-id="30925-300">Описание</span><span class="sxs-lookup"><span data-stu-id="30925-300">Description</span></span>

<span data-ttu-id="30925-301">Эта служба отключает ранее подключенный клиент на данном экземпляре сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-301">This service disconnects a previously connected Client on this Telnet Server instance.</span></span> <span data-ttu-id="30925-302">Эта подпрограмма обычно вызывается из функции обратного вызова получения данных приложения в ответ на условие, обнаруженное в полученных данных.</span><span class="sxs-lookup"><span data-stu-id="30925-302">This routine is typically called from the application’s receive data callback function in response to a condition detected in the data received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30925-303">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="30925-303">Input Parameters</span></span>

- <span data-ttu-id="30925-304">**server_ptr**: указатель на управляющий блок сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-304">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="30925-305">**logical_connection**: логическое подключение, соответствующее клиентскому подключению к этому серверу.</span><span class="sxs-lookup"><span data-stu-id="30925-305">**logical_connection**: Logical connection corresponding the Client connection on this Server.</span></span> <span data-ttu-id="30925-306">Диапазон допустимых значений — от 0 до NX_TELENET_MAX_CLIENTS.</span><span class="sxs-lookup"><span data-stu-id="30925-306">Valid value range from 0 through NX_TELENET_MAX_CLIENTS.</span></span>

### <a name="return-values"></a><span data-ttu-id="30925-307">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="30925-307">Return Values</span></span>

- <span data-ttu-id="30925-308">**NX_SUCCESS**: (0x00) успешное отключение сервера.</span><span class="sxs-lookup"><span data-stu-id="30925-308">**NX_SUCCESS**: (0x00) Successful Server disconnect.</span></span>
- <span data-ttu-id="30925-309">**NX_TELNET_ERROR**: (0xF0) сбой отключения сервера.</span><span class="sxs-lookup"><span data-stu-id="30925-309">**NX_TELNET_ERROR**: (0xF0) Server disconnect failed.</span></span>
- <span data-ttu-id="30925-310">NX_OPTION_ERROR: (0x0A) недопустимое логическое подключение.</span><span class="sxs-lookup"><span data-stu-id="30925-310">NX_OPTION_ERROR: (0x0A) Invalid logical connection.</span></span>
- <span data-ttu-id="30925-311">NX_PTR_ERROR: (0x07) недопустимый указатель сервера.</span><span class="sxs-lookup"><span data-stu-id="30925-311">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="30925-312">NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="30925-312">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30925-313">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="30925-313">Allowed From</span></span>

<span data-ttu-id="30925-314">Потоки</span><span class="sxs-lookup"><span data-stu-id="30925-314">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30925-315">Например, .</span><span class="sxs-lookup"><span data-stu-id="30925-315">Example</span></span>

```c

/* Disconnect the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_disconnect(&my_server, 2);

/* If status is NX_SUCCESS the Client on logical connection 2 was 
   disconnected.  */
```

## <a name="nx_telnet_server_get_open_connection_count"></a><span data-ttu-id="30925-316">nx_telnet_server_get_open_connection_count</span><span class="sxs-lookup"><span data-stu-id="30925-316">nx_telnet_server_get_open_connection_count</span></span>

<span data-ttu-id="30925-317">Возвращает число открытых соединений</span><span class="sxs-lookup"><span data-stu-id="30925-317">Return number of currently open connections</span></span>

### <a name="prototype"></a><span data-ttu-id="30925-318">Прототип</span><span class="sxs-lookup"><span data-stu-id="30925-318">Prototype</span></span>

```c
UINT nx_telnet_server_get_open_connection_count(NX_TELNET_SERVER *server_ptr, UINT *connection_count);
```

### <a name="description"></a><span data-ttu-id="30925-319">Описание</span><span class="sxs-lookup"><span data-stu-id="30925-319">Description</span></span>

<span data-ttu-id="30925-320">Эта служба возвращает число подключенных в настоящее время клиентов Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-320">This service returns the number of currently connected Telnet Clients.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30925-321">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="30925-321">Input Parameters</span></span>

- <span data-ttu-id="30925-322">**server_ptr**: указатель на управляющий блок сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-322">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="30925-323">**Connection_count**: указатель на память для хранения числа подключений.</span><span class="sxs-lookup"><span data-stu-id="30925-323">**Connection_count**: Pointer to memory to store connection count</span></span>

### <a name="return-values"></a><span data-ttu-id="30925-324">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="30925-324">Return Values</span></span>

- <span data-ttu-id="30925-325">**NX_SUCCESS** (0x00) успешное выполнение.</span><span class="sxs-lookup"><span data-stu-id="30925-325">**NX_SUCCESS**: (0x00) Successful completion.</span></span>
- <span data-ttu-id="30925-326">NX_PTR_ERROR: (0x07) недопустимый указатель сервера.</span><span class="sxs-lookup"><span data-stu-id="30925-326">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="30925-327">NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="30925-327">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30925-328">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="30925-328">Allowed From</span></span>

<span data-ttu-id="30925-329">Потоки</span><span class="sxs-lookup"><span data-stu-id="30925-329">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30925-330">Например, .</span><span class="sxs-lookup"><span data-stu-id="30925-330">Example</span></span>

```c
/* Get the number of Telnet Clients connected to the Server. */

status =  nx_telnet_server_get_open_connection_count(&my_server, &conn_count);

/* If status is NX_SUCCESS the conn_count holds the number of open connections.  */

```

## <a name="nx_telnet_server_packet_send"></a><span data-ttu-id="30925-331">nx_telnet_server_packet_send</span><span class="sxs-lookup"><span data-stu-id="30925-331">nx_telnet_server_packet_send</span></span>

<span data-ttu-id="30925-332">Отправка пакета через клиентское соединение</span><span class="sxs-lookup"><span data-stu-id="30925-332">Send packet through Client connection</span></span>

### <a name="prototype"></a><span data-ttu-id="30925-333">Прототип</span><span class="sxs-lookup"><span data-stu-id="30925-333">Prototype</span></span>

```c
UINT nx_telnet_server_packet_send(NX_TELNET_SERVER *server_ptr, 
                                  UINT logical_connection, 
                                  NX_PACKET *packet_ptr, 
                                  ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="30925-334">Описание</span><span class="sxs-lookup"><span data-stu-id="30925-334">Description</span></span>

<span data-ttu-id="30925-335">Эта служба отправляет пакет клиентскому подключению к данному экземпляру сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-335">This service sends a packet to the Client connection on this Telnet Server instance.</span></span> <span data-ttu-id="30925-336">Эта подпрограмма обычно вызывается из функции обратного вызова получения данных приложения в ответ на условие, обнаруженное в полученных данных.</span><span class="sxs-lookup"><span data-stu-id="30925-336">This routine is typically called from the application’s receive data callback function in response to a condition detected in the data received.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30925-337">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="30925-337">Input Parameters</span></span>

- <span data-ttu-id="30925-338">**server_ptr**: указатель на управляющий блок сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-338">**server_ptr**: Pointer to Telnet Server control block.</span></span>
- <span data-ttu-id="30925-339">**logical_connection**: логическое подключение, соответствующее клиентскому подключению к этому серверу.</span><span class="sxs-lookup"><span data-stu-id="30925-339">**logical_connection**: Logical connection corresponding the Client connection on this Server.</span></span> <span data-ttu-id="30925-340">Диапазон допустимых значений — от 0 до NX_TELENET_MAX_CLIENTS.</span><span class="sxs-lookup"><span data-stu-id="30925-340">Valid value range from 0 through NX_TELENET_MAX_CLIENTS.</span></span>
- <span data-ttu-id="30925-341">**packet_ptr**: указатель на полученный пакет.</span><span class="sxs-lookup"><span data-stu-id="30925-341">**packet_ptr**: Pointer to the received packet.</span></span>
- <span data-ttu-id="30925-342">**wait_option**: определяет, как долго служба будет ожидать отправки пакета сервером Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-342">**wait_option**: Defines how long the service will wait for the Telnet Server packet send.</span></span> <span data-ttu-id="30925-343">Параметры ожидания определяются следующим образом:</span><span class="sxs-lookup"><span data-stu-id="30925-343">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="30925-344">**значение времени ожидания**: (от 0x00000001 до 0xFFFFFFFE). Указание числового значения (1–0xFFFFFFFE) задает максимальное число тактов таймера для приостановки работы при ожидании ответа сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-344">**timeout value**: (0x00000001 through 0xFFFFFFFE) Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the Telnet Server response.</span></span>
    - <span data-ttu-id="30925-345">**TX_WAIT_FOREVER**: (0xFFFFFFFF). Указание параметра TX_WAIT_FOREVER приведет к приостановке вызывающего потока на неограниченное время, пока сервер Telnet не ответит на запрос.</span><span class="sxs-lookup"><span data-stu-id="30925-345">**TX_WAIT_FOREVER**: (0xFFFFFFFF) Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until the Telnet Server responds to the request.</span></span> 

### <a name="return-values"></a><span data-ttu-id="30925-346">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="30925-346">Return Values</span></span>

- <span data-ttu-id="30925-347">**NX_SUCCESS**: (0x00) пакет успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="30925-347">**NX_SUCCESS**: (0x00) Successful packet send.</span></span>
- <span data-ttu-id="30925-348">**NX_TELNET_FAILED**: (0xF2) ошибка отправки сокета TCP.</span><span class="sxs-lookup"><span data-stu-id="30925-348">**NX_TELNET_FAILED**: (0xF2) TCP socket send failed.</span></span>
- <span data-ttu-id="30925-349">NX_OPTION_ERROR: (0x0A) недопустимое логическое подключение.</span><span class="sxs-lookup"><span data-stu-id="30925-349">NX_OPTION_ERROR: (0x0A) Invalid logical connection.</span></span>
- <span data-ttu-id="30925-350">NX_PTR_ERROR: (0x07) недопустимый указатель сервера.</span><span class="sxs-lookup"><span data-stu-id="30925-350">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="30925-351">NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="30925-351">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30925-352">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="30925-352">Allowed From</span></span>

<span data-ttu-id="30925-353">Потоки</span><span class="sxs-lookup"><span data-stu-id="30925-353">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30925-354">Например, .</span><span class="sxs-lookup"><span data-stu-id="30925-354">Example</span></span>

```c
/* Send a packet to the Telnet Client associated with logical connection 2 on 
   the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_packet_send(&my_server, 2, my_packet, 100);

/* If status is NX_SUCCESS the packet was sent to the Client on logical 
   connection 2.  */
```

## <a name="nx_telnet_server_packet_pool_set"></a><span data-ttu-id="30925-355">nx_telnet_server_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="30925-355">nx_telnet_server_packet_pool_set</span></span>

<span data-ttu-id="30925-356">Задает ранее созданный пул пакетов в качестве пула сервера Telnet</span><span class="sxs-lookup"><span data-stu-id="30925-356">Set previously created packet pool as Telnet Server pool</span></span>

### <a name="prototype"></a><span data-ttu-id="30925-357">Прототип</span><span class="sxs-lookup"><span data-stu-id="30925-357">Prototype</span></span>

```c
UINT nx_telnet_server_packet_pool_set(NX_TELNET_SERVER *server_ptr, NX_PACKET_POOL *packet_pool_ptr);

```

### <a name="description"></a><span data-ttu-id="30925-358">Описание</span><span class="sxs-lookup"><span data-stu-id="30925-358">Description</span></span>

<span data-ttu-id="30925-359">Эта служба задает ранее созданный пул пакетов в качестве пула пакетов сервера Telnet, если определен параметр NX_TELNET_SERVER_USER_CREATE_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="30925-359">This service sets a previously created packet pool as the Telnet Server packet pool if NX_TELNET_SERVER_USER_CREATE_PACKET_POOL is defined.</span></span> <span data-ttu-id="30925-360">Также требуется, чтобы не был определен параметр NX_TELNET_SERVER_OPTION_DISABLE, чтобы серверу Telnet требовался пул пакетов для передачи параметров Telnet клиентам Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-360">It also requires that NX_TELNET_SERVER_OPTION_DISABLE not be defined such that the Telnet Server needs a packet pool to transmit Telnet options to Telnet clients.</span></span>

<span data-ttu-id="30925-361">Это позволяет приложениям создавать пул пакетов в памяти, отличной от стека сервера Telnet, например без кэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="30925-361">This permits applications to create the packet pool in different memory e.g. no cache memory, than the Telnet Server stack.</span></span> <span data-ttu-id="30925-362">Обратите внимание, проверяет ли эта функция, установлен или нет пул пакетов сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-362">Note that if this function does not check if the Telnet Server packet pool is already set.</span></span> <span data-ttu-id="30925-363">Если она вызывается для указателя пула пакетов сервера Telnet, отличного от NULL, она перезапишет его и заменит существующий пул пакетов на пул пакетов, на который указывает указатель из входных данных.</span><span class="sxs-lookup"><span data-stu-id="30925-363">If it is called on a non null Telnet Server packet pool pointer, it will overwrite it and replace the existing packet pool with packet pool pointed to by the input pointer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30925-364">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="30925-364">Input Parameters</span></span>

- <span data-ttu-id="30925-365">**server_ptr**: указатель на управляющий блок сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-365">**server_ptr**: Pointer to Telnet Server control block</span></span>
- <span data-ttu-id="30925-366">**packet_pool_ptr**: указатель на ранее созданный пул пакетов.</span><span class="sxs-lookup"><span data-stu-id="30925-366">**packet_pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="30925-367">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="30925-367">Return Values</span></span>

- <span data-ttu-id="30925-368">**NX_SUCCESS**: (0x00) пул успешно задан.</span><span class="sxs-lookup"><span data-stu-id="30925-368">**NX_SUCCESS**: (0x00) Successfully set pool.</span></span>
- <span data-ttu-id="30925-369">NX_PTR_ERROR: (0x07) недопустимый указатель сервера.</span><span class="sxs-lookup"><span data-stu-id="30925-369">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30925-370">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="30925-370">Allowed From</span></span>

<span data-ttu-id="30925-371">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="30925-371">Init, Threads</span></span>

### <a name="example"></a><span data-ttu-id="30925-372">Например, .</span><span class="sxs-lookup"><span data-stu-id="30925-372">Example</span></span>

```c
status =  nx_packet_pool_create(&telnet_server_packet_pool, 
                                "Telnet Server Packet Pool", 
                                telnet_server_pool_area, 600*10);

/* Set the packet pool as the Telnet Server packet pool.   */
status =  nx_telnet_server_packet_pool_set(&my_server, &telnet_server_packet_pool);

/* If status is NX_SUCCESS the packet pool is set as Telnet Server pool.  */
```
## <a name="nx_telnet_server_start"></a><span data-ttu-id="30925-373">nx_telnet_server_start</span><span class="sxs-lookup"><span data-stu-id="30925-373">nx_telnet_server_start</span></span>

<span data-ttu-id="30925-374">Запуск сервера Telnet</span><span class="sxs-lookup"><span data-stu-id="30925-374">Start a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="30925-375">Прототип</span><span class="sxs-lookup"><span data-stu-id="30925-375">Prototype</span></span>

```c
UINT nx_telnet_server_start(NX_TELNET_SERVER *server_ptr);

```

### <a name="description"></a><span data-ttu-id="30925-376">Описание</span><span class="sxs-lookup"><span data-stu-id="30925-376">Description</span></span>

<span data-ttu-id="30925-377">Эта служба запускает ранее созданный экземпляр сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-377">This service starts a previously created Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30925-378">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="30925-378">Input Parameters</span></span>

- <span data-ttu-id="30925-379">**server_ptr**: указатель на управляющий блок сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-379">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="30925-380">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="30925-380">Return Values</span></span>

- <span data-ttu-id="30925-381">**NX_SUCCESS**: (0x00) запущено успешно.</span><span class="sxs-lookup"><span data-stu-id="30925-381">**NX_SUCCESS**: (0x00) Successfully started.</span></span>
- <span data-ttu-id="30925-382">**NX_TELNET_NO_PACKET_POOL**: (0xF6) не задан пул пакетов.</span><span class="sxs-lookup"><span data-stu-id="30925-382">**NX_TELNET_NO_PACKET_POOL**: (0xF6) No packet pool set</span></span>
- <span data-ttu-id="30925-383">NX_PTR_ERROR: (0x07) недопустимый указатель сервера.</span><span class="sxs-lookup"><span data-stu-id="30925-383">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30925-384">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="30925-384">Allowed From</span></span>

<span data-ttu-id="30925-385">Инициализация, Потоки</span><span class="sxs-lookup"><span data-stu-id="30925-385">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="30925-386">Например, .</span><span class="sxs-lookup"><span data-stu-id="30925-386">Example</span></span>

```c
/* Start the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_start(&my_server);

/* If status is NX_SUCCESS the Server was started.  */
```

## <a name="nx_telnet_server_stop"></a><span data-ttu-id="30925-387">nx_telnet_server_stop</span><span class="sxs-lookup"><span data-stu-id="30925-387">nx_telnet_server_stop</span></span>

<span data-ttu-id="30925-388">Остановка сервера Telnet</span><span class="sxs-lookup"><span data-stu-id="30925-388">Stop a Telnet Server</span></span>

### <a name="prototype"></a><span data-ttu-id="30925-389">Прототип</span><span class="sxs-lookup"><span data-stu-id="30925-389">Prototype</span></span>

```c
UINT nx_telnet_server_stop(NX_TELNET_SERVER *server_ptr);
```

### <a name="description"></a><span data-ttu-id="30925-390">Описание</span><span class="sxs-lookup"><span data-stu-id="30925-390">Description</span></span>

<span data-ttu-id="30925-391">Эта служба завершает работу ранее созданного и запущенного экземпляра сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-391">This service stops a previously created and started Telnet Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="30925-392">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="30925-392">Input Parameters</span></span>

- <span data-ttu-id="30925-393">**server_ptr**: указатель на управляющий блок сервера Telnet.</span><span class="sxs-lookup"><span data-stu-id="30925-393">**server_ptr**: Pointer to Telnet Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="30925-394">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="30925-394">Return Values</span></span>

- <span data-ttu-id="30925-395">**NX_SUCCESS**: (0x00) остановлено успешно.</span><span class="sxs-lookup"><span data-stu-id="30925-395">**NX_SUCCESS**: (0x00) Successfully stopped</span></span>
- <span data-ttu-id="30925-396">NX_PTR_ERROR: (0x07) недопустимый указатель сервера.</span><span class="sxs-lookup"><span data-stu-id="30925-396">NX_PTR_ERROR: (0x07) Invalid Server pointer.</span></span>
- <span data-ttu-id="30925-397">NX_CALLER_ERROR: (0x11) недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="30925-397">NX_CALLER_ERROR: (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="30925-398">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="30925-398">Allowed From</span></span>

<span data-ttu-id="30925-399">Потоки</span><span class="sxs-lookup"><span data-stu-id="30925-399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="30925-400">Пример</span><span class="sxs-lookup"><span data-stu-id="30925-400">Example</span></span>

```c
/* Stop the Telnet Server instance “my_server”.  */
status =  nx_telnet_server_stop(&my_server);

/* If status is NX_SUCCESS the Server was stopped.  */
```