---
title: Глава 3. Описание служб сервера ОСРВ Azure NetX DHCP
description: В этой главе содержится описание всех служб сервера ОСРВ Azure NetX DHCP.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d24c69cf6b8c2bb84b7155e49a54e8296ee662f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815243"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-server-services"></a><span data-ttu-id="8175a-103">Глава 3. Описание служб сервера ОСРВ Azure NetX DHCP</span><span class="sxs-lookup"><span data-stu-id="8175a-103">Chapter 3 - Description of Azure RTOS NetX DHCP Server services</span></span>

<span data-ttu-id="8175a-104">В этой главе приведено описание всех служб сервера NetX DHCP.</span><span class="sxs-lookup"><span data-stu-id="8175a-104">This chapter contains a description of all NetX DHCP Server services.</span></span>

<span data-ttu-id="8175a-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, используемым для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="8175a-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="8175a-106">**nx_dhcp_server_create**: *создание экземпляра DHCP-сервера*.</span><span class="sxs-lookup"><span data-stu-id="8175a-106">**nx_dhcp_server_create**: *Create a DHCP Server instance*</span></span>
- <span data-ttu-id="8175a-107">**nx_dhcp_set_interface_network_parameters**: *настройка параметров DHCP-сервера для задания критически важных параметров сети для указанного интерфейса*.</span><span class="sxs-lookup"><span data-stu-id="8175a-107">**nx_dhcp_set_interface_network_parameters**: *Set DHCP Server options for critical network parameters for specified interface*</span></span>
- <span data-ttu-id="8175a-108">**nx_dhcp_create_server_ip_address_list**: *создание пула доступных IP-адресов для назначения интерфейсу DHCP-клиентов*.</span><span class="sxs-lookup"><span data-stu-id="8175a-108">**nx_dhcp_create_server_ip_address_list**: *Create pool of available IP addresses to assign to DHCP Clients interface*</span></span>
- <span data-ttu-id="8175a-109">**nx_dhcp_clear_client_record**: *удаление записи клиента из базы данных сервера*.</span><span class="sxs-lookup"><span data-stu-id="8175a-109">**nx_dhcp_clear_client_record**: *Remove Client record in the Server database*</span></span>
- <span data-ttu-id="8175a-110">**nx_dhcp_server_delete**: *удаление экземпляра DHCP-сервера*.</span><span class="sxs-lookup"><span data-stu-id="8175a-110">**nx_dhcp_server_delete**: *Delete a DHCPServer instance*</span></span>
- <span data-ttu-id="8175a-111">**nx_dhcp_server_start**: *запуск или возобновление обработки DHCP-сервера*.</span><span class="sxs-lookup"><span data-stu-id="8175a-111">**nx_dhcp_server_start**: *Start or resume DHCP Server processing*</span></span>
- <span data-ttu-id="8175a-112">**nx_dhcp_server_stop**: *остановка обработки DHCP-сервера*.</span><span class="sxs-lookup"><span data-stu-id="8175a-112">**nx_dhcp_server_stop**: *Stop DHCP server processing*</span></span>

## <a name="nx_dhcp_server_create"></a><span data-ttu-id="8175a-113">nx_dhcp_server_create</span><span class="sxs-lookup"><span data-stu-id="8175a-113">nx_dhcp_server_create</span></span>

<span data-ttu-id="8175a-114">Создание экземпляра DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="8175a-114">Create a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8175a-115">Прототип</span><span class="sxs-lookup"><span data-stu-id="8175a-115">Prototype</span></span>

```c
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
                        VOID *stack_ptr, ULONG stack_size,
                        CHAR *input_address_list, CHAR *name_ptr,
                        NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="8175a-116">Описание</span><span class="sxs-lookup"><span data-stu-id="8175a-116">Description</span></span>

<span data-ttu-id="8175a-117">Эта служба создает экземпляр DHCP-сервера, используя созданный ранее экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="8175a-117">This service creates a DHCP Server instance with a previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8175a-118">Приложение должно обеспечить, чтобы созданный для службы создания экземпляров IP пул пакетов поддерживал полезные данные размером в 548 байт, не считая заголовков UDP, IP и Ethernet.</span><span class="sxs-lookup"><span data-stu-id="8175a-118">The application must make sure the packet pool created for the IP create service has a minimum548 byte payload, not including the UDP, IP and Ethernet headers.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8175a-119">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="8175a-119">Input Parameters</span></span>

- <span data-ttu-id="8175a-120">**dhcp_ptr**: указатель на блок управления DHCP-сервером.</span><span class="sxs-lookup"><span data-stu-id="8175a-120">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="8175a-121">**ip_ptr**: указатель на экземпляр IP для DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="8175a-121">**ip_ptr**: Pointer to DHCP Server IP instance.</span></span>
- <span data-ttu-id="8175a-122">**stack_ptr**: указатель на расположение стека для DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="8175a-122">**stack_ptr**: Pointer DHCP Server stack location.</span></span>
- <span data-ttu-id="8175a-123">**stack_size**: размер стека DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="8175a-123">**stack_size**: Size of DHCP Server stack</span></span>
- <span data-ttu-id="8175a-124">**input_address_list**: указатель на список IP-адресов сервера.</span><span class="sxs-lookup"><span data-stu-id="8175a-124">**input_address_list**: Pointer to Server's list of IP addresses</span></span>
- <span data-ttu-id="8175a-125">**name_ptr**: указатель на имя DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="8175a-125">**name_ptr**: Pointer to DHCP Server name</span></span>
- <span data-ttu-id="8175a-126">**packet_pool_ptr**: указатель на пул пакетов DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="8175a-126">**packet_pool_ptr**: Pointer to DHCP Server packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="8175a-127">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="8175a-127">Return Values</span></span>

- <span data-ttu-id="8175a-128">**NX_SUCCESS** (0x00): DHCP-сервер успешно создан.</span><span class="sxs-lookup"><span data-stu-id="8175a-128">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="8175a-129">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD** (0xA9): ошибка из-за слишком маленького размера полезных данных в пакете.</span><span class="sxs-lookup"><span data-stu-id="8175a-129">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0xA9) Packet payload too small error</span></span>
- <span data-ttu-id="8175a-130">**NX_DHCP_NO_SERVER_OPTION_LIST** (0x96): список параметров сервера пустой.</span><span class="sxs-lookup"><span data-stu-id="8175a-130">**NX_DHCP_NO_SERVER_OPTION_LIST**: (0x96) Server option list is empty</span></span>
- <span data-ttu-id="8175a-131">NX_DHCP_PARAMETER_ERROR (0x92): недопустимые входные данные, отличные от указателя.</span><span class="sxs-lookup"><span data-stu-id="8175a-131">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="8175a-132">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="8175a-132">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="8175a-133">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="8175a-133">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8175a-134">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="8175a-134">Allowed From</span></span>

<span data-ttu-id="8175a-135">Приложение</span><span class="sxs-lookup"><span data-stu-id="8175a-135">Application</span></span>

### <a name="example"></a><span data-ttu-id="8175a-136">Например, .</span><span class="sxs-lookup"><span data-stu-id="8175a-136">Example</span></span>

```c
/* Create a DHCP Server instance. */
status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST,
                    "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a><span data-ttu-id="8175a-137">nx_dhcp_create_server_ip_address_list</span><span class="sxs-lookup"><span data-stu-id="8175a-137">nx_dhcp_create_server_ip_address_list</span></span>

<span data-ttu-id="8175a-138">Создание пула IP-адресов.</span><span class="sxs-lookup"><span data-stu-id="8175a-138">Create a IP address pool</span></span>

### <a name="prototype"></a><span data-ttu-id="8175a-139">Прототип</span><span class="sxs-lookup"><span data-stu-id="8175a-139">Prototype</span></span>

```c
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
                            UINT iface_index, ULONG start_ip_address,
                            ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a><span data-ttu-id="8175a-140">Описание</span><span class="sxs-lookup"><span data-stu-id="8175a-140">Description</span></span>

<span data-ttu-id="8175a-141">Эта служба создает пул доступных IP-адресов для конкретного сетевого интерфейса, которые будут назначаться указанным DHCP-сервером.</span><span class="sxs-lookup"><span data-stu-id="8175a-141">This service creates a networkinterface specific pool of available IP addresses for the specified DHCP server to assign.</span></span> <span data-ttu-id="8175a-142">Начальный и конечный IP-адреса должны соответствовать указанному сетевому интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="8175a-142">The start and end IP addresses must match the specified network interface.</span></span> <span data-ttu-id="8175a-143">Реальное число добавленных IP-адресов может оказаться меньше заявленного общего числа адресов, если будет исчерпан список IP-адресов (его размер задается в настраиваемом пользователем параметре *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE*).</span><span class="sxs-lookup"><span data-stu-id="8175a-143">The actual number of IP addresses added may be less than the total addresses if the IP address list is not large enough (which is set in the user configurable *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parameter).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8175a-144">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="8175a-144">Input Parameters</span></span>

- <span data-ttu-id="8175a-145">**dhcp_ptr**: указатель на блок управления DHCP-сервером.</span><span class="sxs-lookup"><span data-stu-id="8175a-145">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="8175a-146">**iface_index**: индекс, соответствующий сетевому интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="8175a-146">**iface_index**: Index corresponding to network interface</span></span>
- <span data-ttu-id="8175a-147">**start_ip_address**: первый доступный IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="8175a-147">**start_ip_address**: First available IP address</span></span>
- <span data-ttu-id="8175a-148">**end_ip_address**: последний доступный IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="8175a-148">**end_ip_address**: Last of the available IP address</span></span>
- <span data-ttu-id="8175a-149">**addresses_added**: число IP-адресов, добавляемых в список.</span><span class="sxs-lookup"><span data-stu-id="8175a-149">**addresses_added**: Number of IP addresses added to list</span></span>

### <a name="return-values"></a><span data-ttu-id="8175a-150">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="8175a-150">Return Values</span></span>

- <span data-ttu-id="8175a-151">**NX_SUCCESS** (0x00): DHCP-сервер успешно создан.</span><span class="sxs-lookup"><span data-stu-id="8175a-151">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="8175a-152">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1): индекс не соответствует адресам.</span><span class="sxs-lookup"><span data-stu-id="8175a-152">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="8175a-153">**NX_DHCP_INVALID_IP_ADDRESS_LIST** (0x99): недопустимые входные данные адреса.</span><span class="sxs-lookup"><span data-stu-id="8175a-153">**NX_DHCP_INVALID_IP_ADDRESS_LIST**: (0x99) Invalid address input</span></span>
- <span data-ttu-id="8175a-154">NX_DHCP_INVALID_IP_ADDRESS (0x9B): нарушение логики начального и конечного адресов.</span><span class="sxs-lookup"><span data-stu-id="8175a-154">NX_DHCP_INVALID_IP_ADDRESS: (0x9B) Illogical start/end addresses</span></span>
- <span data-ttu-id="8175a-155">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="8175a-155">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8175a-156">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="8175a-156">Allowed From</span></span>

<span data-ttu-id="8175a-157">Приложение</span><span class="sxs-lookup"><span data-stu-id="8175a-157">Application</span></span>

### <a name="example"></a><span data-ttu-id="8175a-158">Например, .</span><span class="sxs-lookup"><span data-stu-id="8175a-158">Example</span></span>

```c
/* Create a pool of available IP addresses to assign. */
status = nx_dhcp_create_server_ip_list (&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS aIP address list was successfully created. 
addresses_added indicates how many IP addresses were actually added to the list. */
```

## <a name="nx_dhcp_clear_client_record"></a><span data-ttu-id="8175a-159">nx_dhcp_clear_client_record</span><span class="sxs-lookup"><span data-stu-id="8175a-159">nx_dhcp_clear_client_record</span></span>

<span data-ttu-id="8175a-160">Удаление записи клиента из базы данных сервера.</span><span class="sxs-lookup"><span data-stu-id="8175a-160">Remove Client record from Server database</span></span>

### <a name="prototype"></a><span data-ttu-id="8175a-161">Прототип</span><span class="sxs-lookup"><span data-stu-id="8175a-161">Prototype</span></span>

```c
UINT nx_dhcp_clear_client_record (NX_DHCP_SERVER *dhcp_ptr,
                                NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="8175a-162">Описание</span><span class="sxs-lookup"><span data-stu-id="8175a-162">Description</span></span>

<span data-ttu-id="8175a-163">Эта служба удаляет запись клиента из базы данных сервера.</span><span class="sxs-lookup"><span data-stu-id="8175a-163">This service clears the Client record from the Server database.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8175a-164">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="8175a-164">Input Parameters</span></span>

- <span data-ttu-id="8175a-165">**dhcp_ptr**: указатель на блок управления DHCP-сервером.</span><span class="sxs-lookup"><span data-stu-id="8175a-165">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="8175a-166">**dhcp_client_ptr**: указатель на DHCP-клиент, который нужно удалить.</span><span class="sxs-lookup"><span data-stu-id="8175a-166">**dhcp_client_ptr**: Pointer to DHCP Client to remove</span></span>

### <a name="return-values"></a><span data-ttu-id="8175a-167">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="8175a-167">Return Values</span></span>

- <span data-ttu-id="8175a-168">**NX_SUCCESS** (0x00): DHCP-сервер успешно создан.</span><span class="sxs-lookup"><span data-stu-id="8175a-168">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="8175a-169">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="8175a-169">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="8175a-170">NX_CALLER_ERROR (0x11): вызов службы не из потока.</span><span class="sxs-lookup"><span data-stu-id="8175a-170">NX_CALLER_ERROR: (0x11) Non thread caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8175a-171">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="8175a-171">Allowed From</span></span>

<span data-ttu-id="8175a-172">Приложение</span><span class="sxs-lookup"><span data-stu-id="8175a-172">Application</span></span>

### <a name="example"></a><span data-ttu-id="8175a-173">Например, .</span><span class="sxs-lookup"><span data-stu-id="8175a-173">Example</span></span>

```c
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record (&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a><span data-ttu-id="8175a-174">nx_dhcp_set_interface_network_parameters</span><span class="sxs-lookup"><span data-stu-id="8175a-174">nx_dhcp_set_interface_network_parameters</span></span>

<span data-ttu-id="8175a-175">Настройка параметров сети в конфигурации DHCP.</span><span class="sxs-lookup"><span data-stu-id="8175a-175">Set network parameters for DHCP options</span></span>

### <a name="prototype"></a><span data-ttu-id="8175a-176">Прототип</span><span class="sxs-lookup"><span data-stu-id="8175a-176">Prototype</span></span>

```c
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
                                    UINT iface_index, ULONG subnet_mask,
                                    ULONG default_gateway_address,
                                    ULONG dns_server_address);
```

### <a name="description"></a><span data-ttu-id="8175a-177">Описание</span><span class="sxs-lookup"><span data-stu-id="8175a-177">Description</span></span>

<span data-ttu-id="8175a-178">Эта служба задает значения по умолчанию для критически важных параметров сети для указанного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="8175a-178">This service sets default values for network critical parameters for the specified interface.</span></span> <span data-ttu-id="8175a-179">DHCP-сервер будет включать эти параметры в ответы OFFER и ACK, возвращаемые в DHCP-клиент.</span><span class="sxs-lookup"><span data-stu-id="8175a-179">The DHCP server will include these options in its OFFER and ACK replies to the DHCP Client.</span></span> <span data-ttu-id="8175a-180">Если параметры интерфейса устанавливает узел, на котором выполняется DHCP-сервер, то будут использоваться следующие значения по умолчанию: в качестве основного шлюза для интерфейса задается адрес самого DHCP-сервера, в качестве адреса DNS-сервера также задается адрес самого DHCP-сервера, а в качестве маски подсети задается значение, настроенное для интерфейса DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="8175a-180">If the host set interface parameters on which a DHCP server is running, the parameters will defaulted as follows: the router set to the primary interface gateway for the DHCP server itself, the DNS server address to the DHCP server itself, and the subnet mask to the same as the DHCP server interface is configured with.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8175a-181">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="8175a-181">Input Parameters</span></span>

- <span data-ttu-id="8175a-182">**dhcp_ptr**: указатель на блок управления DHCP-сервером.</span><span class="sxs-lookup"><span data-stu-id="8175a-182">**dhcp_ptr**: Pointer to DHCP Server control block.</span></span>  
- <span data-ttu-id="8175a-183">**iface_index**: индекс, соответствующий сетевому интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="8175a-183">**iface_index**: Index corresponding to network interface</span></span>
- <span data-ttu-id="8175a-184">**subnet_mask**: маска подсети для сети клиента.</span><span class="sxs-lookup"><span data-stu-id="8175a-184">**subnet_mask**: Subnet mask for Client network</span></span>
- <span data-ttu-id="8175a-185">**default_gateway_address**: IP-адрес маршрутизатора клиента.</span><span class="sxs-lookup"><span data-stu-id="8175a-185">**default_gateway_address**: Client's router IP address</span></span>
- <span data-ttu-id="8175a-186">**dns_server_address**: DNS-сервер для сети клиента.</span><span class="sxs-lookup"><span data-stu-id="8175a-186">**dns_server_address**: DNS server for Client's network</span></span>

### <a name="return-values"></a><span data-ttu-id="8175a-187">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="8175a-187">Return Values</span></span>

- <span data-ttu-id="8175a-188">**NX_SUCCESS** (0x00): DHCP-сервер успешно создан.</span><span class="sxs-lookup"><span data-stu-id="8175a-188">**NX_SUCCESS**: (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="8175a-189">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1): индекс не соответствует адресам.</span><span class="sxs-lookup"><span data-stu-id="8175a-189">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="8175a-190">**NX_DHCP_INVALID_NETWORK_PARAMETERS** (0xA3): недопустимые параметры сети.</span><span class="sxs-lookup"><span data-stu-id="8175a-190">**NX_DHCP_INVALID_NETWORK_PARAMETERS**: (0xA3) Invalid network parameters</span></span>
- <span data-ttu-id="8175a-191">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="8175a-191">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8175a-192">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="8175a-192">Allowed From</span></span>

<span data-ttu-id="8175a-193">Приложение</span><span class="sxs-lookup"><span data-stu-id="8175a-193">Application</span></span>

### <a name="example"></a><span data-ttu-id="8175a-194">Например, .</span><span class="sxs-lookup"><span data-stu-id="8175a-194">Example</span></span>

```c
/* Set network parameters for a specific interface. */
status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                    NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                    IP_ADDRESS(10,0,0,1));

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a><span data-ttu-id="8175a-195">nx_dhcp_server_delete</span><span class="sxs-lookup"><span data-stu-id="8175a-195">nx_dhcp_server_delete</span></span>

<span data-ttu-id="8175a-196">Удаление экземпляра DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="8175a-196">Delete a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="8175a-197">Прототип</span><span class="sxs-lookup"><span data-stu-id="8175a-197">Prototype</span></span>

```c
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="8175a-198">Описание</span><span class="sxs-lookup"><span data-stu-id="8175a-198">Description</span></span>

<span data-ttu-id="8175a-199">Эта служба удаляет созданный ранее экземпляр DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="8175a-199">This service deletes a previously created DHCP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8175a-200">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="8175a-200">Input Parameters</span></span>

- <span data-ttu-id="8175a-201">**dhcp_ptr**: указатель на экземпляр DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="8175a-201">**dhcp_ptr**: Pointer to a DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8175a-202">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="8175a-202">Return Values</span></span>

- <span data-ttu-id="8175a-203">**NX_SUCCESS** (0x00): DHCP-сервер успешно удален.</span><span class="sxs-lookup"><span data-stu-id="8175a-203">**NX_SUCCESS**: (0x00) Successful DHCP Server delete.</span></span>
- <span data-ttu-id="8175a-204">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="8175a-204">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="8175a-205">NX_DHCP_PARAMETER_ERROR (0x92): недопустимые входные данные, отличные от указателя.</span><span class="sxs-lookup"><span data-stu-id="8175a-205">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="8175a-206">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="8175a-206">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8175a-207">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="8175a-207">Allowed From</span></span>

<span data-ttu-id="8175a-208">Потоки</span><span class="sxs-lookup"><span data-stu-id="8175a-208">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8175a-209">Например, .</span><span class="sxs-lookup"><span data-stu-id="8175a-209">Example</span></span>

```c
/* Delete a DHCP Server instance. */
status = nx_dhcp_server_delete(&dhcp_server);  
  
/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a><span data-ttu-id="8175a-210">nx_dhcp_server_start</span><span class="sxs-lookup"><span data-stu-id="8175a-210">nx_dhcp_server_start</span></span>

<span data-ttu-id="8175a-211">Запуск обработки DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="8175a-211">Start DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="8175a-212">Прототип</span><span class="sxs-lookup"><span data-stu-id="8175a-212">Prototype</span></span>

```c
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="8175a-213">Описание</span><span class="sxs-lookup"><span data-stu-id="8175a-213">Description</span></span>

<span data-ttu-id="8175a-214">Эта служба запускает работу DHCP-сервера, в том числе создает для сервера сокет UDP, привязывает порт DHCP и ожидает получения запросов от DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="8175a-214">This service starts DHCP Server processing, which includes creating a server UDP socket, binding the DHCP port and waiting to receive Client DHCP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8175a-215">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="8175a-215">Input Parameters</span></span>

- <span data-ttu-id="8175a-216">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="8175a-216">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8175a-217">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="8175a-217">Return Values</span></span>

- <span data-ttu-id="8175a-218">**NX_SUCCESS** (0x00): сервер успешно запущен.</span><span class="sxs-lookup"><span data-stu-id="8175a-218">**NX_SUCCESS**: (0x00) Successful Server start.</span></span>  
- <span data-ttu-id="8175a-219">**NX_DHCP_ALREADY_STARTED** (0x93): экземпляр DHCP уже запущен.</span><span class="sxs-lookup"><span data-stu-id="8175a-219">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="8175a-220">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="8175a-220">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="8175a-221">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="8175a-221">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="8175a-222">NX_DHCP_PARAMETER_ERROR (0x92): недопустимые входные данные, отличные от указателя.</span><span class="sxs-lookup"><span data-stu-id="8175a-222">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8175a-223">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="8175a-223">Allowed From</span></span>

<span data-ttu-id="8175a-224">Потоки</span><span class="sxs-lookup"><span data-stu-id="8175a-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8175a-225">Пример</span><span class="sxs-lookup"><span data-stu-id="8175a-225">Example</span></span>

```c
/* Start the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_start(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="8175a-226">См. также:</span><span class="sxs-lookup"><span data-stu-id="8175a-226">See Also</span></span>

<span data-ttu-id="8175a-227">nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve, nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="8175a-227">nx_dhcp_create, nx_dhcp_delete, nx_dhcp_release, nx_dhcp_state_change_notify, nx_dhcp_stop, nx_dhcp_user_option_retrieve, nx_dhcp_user_option_convert</span></span>

## <a name="nx_dhcp_server_stop"></a><span data-ttu-id="8175a-228">nx_dhcp_server_stop</span><span class="sxs-lookup"><span data-stu-id="8175a-228">nx_dhcp_server_stop</span></span>

<span data-ttu-id="8175a-229">Остановка обработки DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="8175a-229">Stops DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="8175a-230">Прототип</span><span class="sxs-lookup"><span data-stu-id="8175a-230">Prototype</span></span>

```c
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="8175a-231">Описание</span><span class="sxs-lookup"><span data-stu-id="8175a-231">Description</span></span>

<span data-ttu-id="8175a-232">Эта служба останавливает работу DHCP-сервера, в том числе получение запросов от DHCP-клиентов.</span><span class="sxs-lookup"><span data-stu-id="8175a-232">This service stops DHCP Server processing, which includes of receiving DHCP Client requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="8175a-233">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="8175a-233">Input Parameters</span></span>

- <span data-ttu-id="8175a-234">**dhcp_ptr**: указатель на экземпляр DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="8175a-234">**dhcp_ptr**: Pointer to DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="8175a-235">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="8175a-235">Return Values</span></span>

- <span data-ttu-id="8175a-236">**NX_SUCCESS** (0x00): экземпляр DHCP успешно остановлен.</span><span class="sxs-lookup"><span data-stu-id="8175a-236">**NX_SUCCESS**: (0x00) Successful DHCP stop.</span></span>
- <span data-ttu-id="8175a-237">**NX_DHCP_ALREADY_STARTED** (0x93): экземпляр DHCP уже запущен.</span><span class="sxs-lookup"><span data-stu-id="8175a-237">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="8175a-238">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="8175a-238">NX_PTR_ERROR: (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="8175a-239">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="8175a-239">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="8175a-240">NX_DHCP_PARAMETER_ERROR (0x92): недопустимые входные данные, отличные от указателя.</span><span class="sxs-lookup"><span data-stu-id="8175a-240">NX_DHCP_PARAMETER_ERROR: (0x92) Invalid non pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="8175a-241">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="8175a-241">Allowed From</span></span>

<span data-ttu-id="8175a-242">Потоки</span><span class="sxs-lookup"><span data-stu-id="8175a-242">Threads</span></span>

### <a name="example"></a><span data-ttu-id="8175a-243">Пример</span><span class="sxs-lookup"><span data-stu-id="8175a-243">Example</span></span>

```c
/* Stop the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_stop(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
