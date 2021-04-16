---
title: Глава 3. Описание служб сервера DHCP для NetX Duo в ОСРВ Azure
description: Эта глава содержит описание всех служб сервера DHCP для NetX Duo, перечисленных ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 33eb0b4bd98f808124b9a6a1f01950639243d612
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814791"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dhcp-server-services"></a><span data-ttu-id="429cb-103">Глава 3. Описание служб сервера DHCP для NetX Duo в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="429cb-103">Chapter 3 - Description of Azure RTOS NetX Duo DHCP Server Services</span></span>

<span data-ttu-id="429cb-104">Эта глава содержит описание всех служб сервера DHCP для NetX Duo, перечисленных ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="429cb-104">This chapter contains a description of all NetX Duo DHCP Server services (listed below) in alphabetic order.</span></span>

> [!NOTE]
> <span data-ttu-id="429cb-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="429cb-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_dhcp_server-create"></a><span data-ttu-id="429cb-106">nx_dhcp_server_create</span><span class="sxs-lookup"><span data-stu-id="429cb-106">nx_dhcp_server create</span></span>

<span data-ttu-id="429cb-107">Создание экземпляра сервера DHCP</span><span class="sxs-lookup"><span data-stu-id="429cb-107">Create a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="429cb-108">Прототип</span><span class="sxs-lookup"><span data-stu-id="429cb-108">Prototype</span></span>

```C
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
    VOID *stack_ptr, ULONG stack_size,
    CHAR *input_address_list, CHAR *name_ptr, NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="429cb-109">Описание</span><span class="sxs-lookup"><span data-stu-id="429cb-109">Description</span></span>

<span data-ttu-id="429cb-110">Эта служба создает экземпляр сервера DHCP, используя ранее созданный экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="429cb-110">This service creates a DHCP Server instance with a previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="429cb-111">Приложению нужно убедиться, что созданный для службы создания IP пул пакетов поддерживает полезные данные размером 548 байт, не считая заголовков UDP, IP и Ethernet.</span><span class="sxs-lookup"><span data-stu-id="429cb-111">The application must make sure the packet pool created for the IP create service has a minimum 548 byte payload, not including the UDP, IP and Ethernet headers.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="429cb-112">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="429cb-112">Input Parameters</span></span>

- <span data-ttu-id="429cb-113">**dhcp_ptr** — указатель на блок управления сервером DHCP.</span><span class="sxs-lookup"><span data-stu-id="429cb-113">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="429cb-114">**ip_ptr** — указатель на экземпляр IP для сервера DHCP.</span><span class="sxs-lookup"><span data-stu-id="429cb-114">**ip_ptr** Pointer to DHCP Server IP instance.</span></span>
- <span data-ttu-id="429cb-115">**stack_ptr** — указатель на расположение стека для сервера DHCP.</span><span class="sxs-lookup"><span data-stu-id="429cb-115">**stack_ptr** Pointer DHCP Server stack location.</span></span>
- <span data-ttu-id="429cb-116">**stack_size** — размер стека для сервера DHCP. input_address_list — указатель на список IP-адресов сервера.</span><span class="sxs-lookup"><span data-stu-id="429cb-116">**stack_size Size of DHCP Server stack** input_address_list Pointer to Server’s list of IP addresses</span></span>
- <span data-ttu-id="429cb-117">**name_ptr** — указатель на имя сервера DHCP. packet_pool_ptr — указатель на пул пакетов для сервера DHCP.</span><span class="sxs-lookup"><span data-stu-id="429cb-117">**name_ptr Pointer to DHCP Server name** packet_pool_ptr Pointer to DHCP Server packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="429cb-118">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="429cb-118">Return Values</span></span>

- <span data-ttu-id="429cb-119">**NX_SUCCESS** (0x00): — сервер DHCP успешно создан.</span><span class="sxs-lookup"><span data-stu-id="429cb-119">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="429cb-120">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD** (0xA9): ошибка: слишком малый размер полезных данных в пакете.</span><span class="sxs-lookup"><span data-stu-id="429cb-120">**NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD** (0xA9) Packet payload too small error</span></span>
- <span data-ttu-id="429cb-121">**NX_DHCP_NO_SERVER_OPTION_LIST** (0x96): список параметров сервера пуст</span><span class="sxs-lookup"><span data-stu-id="429cb-121">**NX_DHCP_NO_SERVER_OPTION_LIST** (0x96) Server option list is empty</span></span>
- <span data-ttu-id="429cb-122">NX_DHCP_PARAMETER_ERROR (0x92): недопустимые входные данные, кроме указателей.</span><span class="sxs-lookup"><span data-stu-id="429cb-122">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="429cb-123">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="429cb-123">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="429cb-124">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="429cb-124">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="429cb-125">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="429cb-125">Allowed From</span></span>

<span data-ttu-id="429cb-126">Приложение</span><span class="sxs-lookup"><span data-stu-id="429cb-126">Application</span></span>

### <a name="example"></a><span data-ttu-id="429cb-127">Например, .</span><span class="sxs-lookup"><span data-stu-id="429cb-127">Example</span></span>

```C
/* Create a DHCP Server instance. */

status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST, "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a><span data-ttu-id="429cb-128">nx_dhcp_create_server_ip_address_list</span><span class="sxs-lookup"><span data-stu-id="429cb-128">nx_dhcp_create_server_ip_address_list</span></span>

<span data-ttu-id="429cb-129">Создание пула IP-адресов</span><span class="sxs-lookup"><span data-stu-id="429cb-129">Create a IP address pool</span></span>

### <a name="prototype"></a><span data-ttu-id="429cb-130">Прототип</span><span class="sxs-lookup"><span data-stu-id="429cb-130">Prototype</span></span>

```C
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
    UINT iface_index, ULONG start_ip_address,
    ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a><span data-ttu-id="429cb-131">Описание</span><span class="sxs-lookup"><span data-stu-id="429cb-131">Description</span></span>

<span data-ttu-id="429cb-132">Эта служба создает пул доступных IP-адресов для конкретного сетевого интерфейса, которые будут назначены указанному серверу DHCP.</span><span class="sxs-lookup"><span data-stu-id="429cb-132">This service creates a network interface specific pool of available IP addresses for the specified DHCP server to assign.</span></span> <span data-ttu-id="429cb-133">Начальный и конечный IP-адреса должны соответствовать указанному сетевому интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="429cb-133">The start and end IP addresses must match the specified network interface.</span></span> <span data-ttu-id="429cb-134">Реальное число добавленных IP-адресов может оказаться меньше заявленного общего числа адресов, если будет исчерпан список IP-адресов (его размер задается в настраиваемом пользователем параметре *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE*).</span><span class="sxs-lookup"><span data-stu-id="429cb-134">The actual number of IP addresses added may be less than the total addresses if the IP address list is not large enough (which is set in the user configurable *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* parameter).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="429cb-135">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="429cb-135">Input Parameters</span></span>

- <span data-ttu-id="429cb-136">**dhcp_ptr** — указатель на блок управления сервером DHCP.</span><span class="sxs-lookup"><span data-stu-id="429cb-136">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="429cb-137">**iface_index** — индекс, соответствующий сетевому интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="429cb-137">**iface_index** Index corresponding to network interface</span></span>
- <span data-ttu-id="429cb-138">**start_ip_address** — первый доступный IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="429cb-138">**start_ip_address** First available IP address</span></span>
- <span data-ttu-id="429cb-139">**end_ip_address** — последний доступный IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="429cb-139">**end_ip_address** Last of the available IP address</span></span>
- <span data-ttu-id="429cb-140">**addresses_added** — число IP-адресов, добавляемых в список.</span><span class="sxs-lookup"><span data-stu-id="429cb-140">**addresses_added** Number of IP addresses added to list</span></span>

### <a name="return-values"></a><span data-ttu-id="429cb-141">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="429cb-141">Return Values</span></span>

- <span data-ttu-id="429cb-142">**NX_SUCCESS** (0x00): — сервер DHCP успешно создан.</span><span class="sxs-lookup"><span data-stu-id="429cb-142">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="429cb-143">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1): индекс не соответствует адресам.</span><span class="sxs-lookup"><span data-stu-id="429cb-143">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="429cb-144">**NX_DHCP_INVALID_IP_ADDRESS_LIST** (0x99): неправильно введены адреса.</span><span class="sxs-lookup"><span data-stu-id="429cb-144">**NX_DHCP_INVALID_IP_ADDRESS_LIST** (0x99) Invalid address input</span></span>
- <span data-ttu-id="429cb-145">NX_DHCP_INVALID_IP_ADDRESS (0x9B): нарушение логики начального и конечного адресов.</span><span class="sxs-lookup"><span data-stu-id="429cb-145">NX_DHCP_INVALID_IP_ADDRESS (0x9B) Illogical start/end addresses</span></span>
- <span data-ttu-id="429cb-146">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="429cb-146">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="429cb-147">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="429cb-147">Allowed From</span></span>

<span data-ttu-id="429cb-148">Приложение</span><span class="sxs-lookup"><span data-stu-id="429cb-148">Application</span></span>

### <a name="example"></a><span data-ttu-id="429cb-149">Например, .</span><span class="sxs-lookup"><span data-stu-id="429cb-149">Example</span></span>

```C
/* Create a pool of available IP addresses to assign. */

status = nx_dhcp_create_server_ip_list(&dhcp_server, iface_index,
    START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS a IP address list was successfully created.
    addresses_added indicates how many IP addresses were actually added to the
    list. */
```

## <a name="nx_dhcp_clear_client_record"></a><span data-ttu-id="429cb-150">nx_dhcp_clear_client_record</span><span class="sxs-lookup"><span data-stu-id="429cb-150">nx_dhcp_clear_client_record</span></span>

<span data-ttu-id="429cb-151">Удаление записи клиента из базы данных сервера</span><span class="sxs-lookup"><span data-stu-id="429cb-151">Remove Client record from Server database</span></span>

### <a name="prototype"></a><span data-ttu-id="429cb-152">Прототип</span><span class="sxs-lookup"><span data-stu-id="429cb-152">Prototype</span></span>

```C
UINT nx_dhcp_clear_client_record(NX_DHCP_SERVER *dhcp_ptr,
    NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a><span data-ttu-id="429cb-153">Описание</span><span class="sxs-lookup"><span data-stu-id="429cb-153">Description</span></span>

<span data-ttu-id="429cb-154">Эта служба очищает запись клиента из базы данных сервера.</span><span class="sxs-lookup"><span data-stu-id="429cb-154">This service clears the Client record from the Server database.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="429cb-155">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="429cb-155">Input Parameters</span></span>

- <span data-ttu-id="429cb-156">**dhcp_ptr** — указатель на блок управления сервером DHCP.</span><span class="sxs-lookup"><span data-stu-id="429cb-156">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="429cb-157">**dhcp_client_ptr** — указатель на клиент DHCP, который нужно удалить.</span><span class="sxs-lookup"><span data-stu-id="429cb-157">**dhcp_client_ptr Pointer to DHCP Client to remove**</span></span>

### <a name="return-values"></a><span data-ttu-id="429cb-158">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="429cb-158">Return Values</span></span>

- <span data-ttu-id="429cb-159">**NX_SUCCESS** (0x00): — сервер DHCP успешно создан.</span><span class="sxs-lookup"><span data-stu-id="429cb-159">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="429cb-160">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="429cb-160">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="429cb-161">NX_CALLER_ERROR (0x11): вызов службы не из потока</span><span class="sxs-lookup"><span data-stu-id="429cb-161">NX_CALLER_ERROR (0x11) Non thread caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="429cb-162">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="429cb-162">Allowed From</span></span>

<span data-ttu-id="429cb-163">Приложение</span><span class="sxs-lookup"><span data-stu-id="429cb-163">Application</span></span>

### <a name="example"></a><span data-ttu-id="429cb-164">Например, .</span><span class="sxs-lookup"><span data-stu-id="429cb-164">Example</span></span>

```C
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record(&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a><span data-ttu-id="429cb-165">nx_dhcp_set_interface_network_parameters</span><span class="sxs-lookup"><span data-stu-id="429cb-165">nx_dhcp_set_interface_network_parameters</span></span>

<span data-ttu-id="429cb-166">Настройка параметров сети в конфигурации DHCP</span><span class="sxs-lookup"><span data-stu-id="429cb-166">Set network parameters for DHCP options</span></span>

### <a name="prototype"></a><span data-ttu-id="429cb-167">Прототип</span><span class="sxs-lookup"><span data-stu-id="429cb-167">Prototype</span></span>

```C
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
    UINT iface_index, ULONG subnet_mask,
    ULONG default_gateway_address,
    ULONG dns_server_address);
```

### <a name="description"></a><span data-ttu-id="429cb-168">Описание</span><span class="sxs-lookup"><span data-stu-id="429cb-168">Description</span></span>

<span data-ttu-id="429cb-169">Эта служба задает значения по умолчанию для критически важных сетевых параметров указанного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="429cb-169">This service sets default values for network critical parameters for the specified interface.</span></span> <span data-ttu-id="429cb-170">Сервер DHCP будет включать эти параметры в ответы OFFER и ACK, возвращаемые в клиент DHCP.</span><span class="sxs-lookup"><span data-stu-id="429cb-170">The DHCP server will include these options in its OFFER and ACK replies to the DHCP Client.</span></span> <span data-ttu-id="429cb-171">Если параметры интерфейса устанавливает узел, в котором выполняется сервер DHCP, будут использоваться следующие значения по умолчанию: в качестве основного шлюза для интерфейса задается адрес самого сервера DHCP, в качестве адреса DNS-сервера также задается адрес самого сервера DHCP, а в качестве маски подсети задается значение, настроенное для интерфейса сервера DHCP.</span><span class="sxs-lookup"><span data-stu-id="429cb-171">If the host set interface parameters on which a DHCP server is running, the parameters will defaulted as follows: the router set to the primary interface gateway for the DHCP server itself, the DNS server address to the DHCP server itself, and the subnet mask to the same as the DHCP server interface is configured with.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="429cb-172">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="429cb-172">Input Parameters</span></span>

- <span data-ttu-id="429cb-173">**dhcp_ptr** — указатель на блок управления сервером DHCP.</span><span class="sxs-lookup"><span data-stu-id="429cb-173">**dhcp_ptr** Pointer to DHCP Server control block.</span></span>
- <span data-ttu-id="429cb-174">**iface_index** — индекс, соответствующий сетевому интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="429cb-174">**iface_index** Index corresponding to network interface</span></span>
- <span data-ttu-id="429cb-175">**subnet_mask** — маска подсети для сети клиента.</span><span class="sxs-lookup"><span data-stu-id="429cb-175">**subnet_mask** Subnet mask for Client network</span></span>
- <span data-ttu-id="429cb-176">**default_gateway_address** — IP-адрес маршрутизатора клиента.</span><span class="sxs-lookup"><span data-stu-id="429cb-176">**default_gateway_address** Client’s router IP address</span></span>
- <span data-ttu-id="429cb-177">**dns_server_address** — DNS-сервер для сети клиента.</span><span class="sxs-lookup"><span data-stu-id="429cb-177">**dns_server_address** DNS server for Client’s network</span></span>

### <a name="return-values"></a><span data-ttu-id="429cb-178">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="429cb-178">Return Values</span></span>

- <span data-ttu-id="429cb-179">**NX_SUCCESS** (0x00): — сервер DHCP успешно создан.</span><span class="sxs-lookup"><span data-stu-id="429cb-179">**NX_SUCCESS** (0x00) Successful DHCP Server create.</span></span>
- <span data-ttu-id="429cb-180">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1): индекс не соответствует адресам.</span><span class="sxs-lookup"><span data-stu-id="429cb-180">**NX_DHCP_SERVER_BAD_INTERFACE_INDEX** (0xA1) Index does not match addresses</span></span>
- <span data-ttu-id="429cb-181">**NX_DHCP_INVALID_NETWORK_PARAMETERS** (0xA3): недопустимые параметры сети</span><span class="sxs-lookup"><span data-stu-id="429cb-181">**NX_DHCP_INVALID_NETWORK_PARAMETERS** (0xA3) Invalid network parameters</span></span>
- <span data-ttu-id="429cb-182">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="429cb-182">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="429cb-183">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="429cb-183">Allowed From</span></span>

<span data-ttu-id="429cb-184">Приложение</span><span class="sxs-lookup"><span data-stu-id="429cb-184">Application</span></span>

### <a name="example"></a><span data-ttu-id="429cb-185">Например, .</span><span class="sxs-lookup"><span data-stu-id="429cb-185">Example</span></span>

```C
/* Set network parameters for a specific interface. */

status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
    NX_DHCP_SUBNET_MASK, NX_DHCP_DEFAULT_GATEWAY,
    NX_DHCP_DNS_SERVER);

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a><span data-ttu-id="429cb-186">nx_dhcp_server_delete</span><span class="sxs-lookup"><span data-stu-id="429cb-186">nx_dhcp_server_delete</span></span>

<span data-ttu-id="429cb-187">Удаление экземпляра сервера DHCP</span><span class="sxs-lookup"><span data-stu-id="429cb-187">Delete a DHCP Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="429cb-188">Прототип</span><span class="sxs-lookup"><span data-stu-id="429cb-188">Prototype</span></span>

```C
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="429cb-189">Описание</span><span class="sxs-lookup"><span data-stu-id="429cb-189">Description</span></span>

<span data-ttu-id="429cb-190">Эта служба удаляет ранее созданный экземпляр сервера DHCP.</span><span class="sxs-lookup"><span data-stu-id="429cb-190">This service deletes a previously created DHCP Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="429cb-191">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="429cb-191">Input Parameters</span></span>

- <span data-ttu-id="429cb-192">**dhcp_ptr** — указатель на экземпляр сервера DHCP.</span><span class="sxs-lookup"><span data-stu-id="429cb-192">**dhcp_ptr** Pointer to a DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="429cb-193">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="429cb-193">Return Values</span></span>

- <span data-ttu-id="429cb-194">**NX_SUCCESS** (0x00): сервер DHCP успешно удален.</span><span class="sxs-lookup"><span data-stu-id="429cb-194">**NX_SUCCESS** (0x00) Successful DHCP Server delete.</span></span>
- <span data-ttu-id="429cb-195">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="429cb-195">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="429cb-196">NX_DHCP_PARAMETER_ERROR (0x92): недопустимые входные данные, кроме указателей.</span><span class="sxs-lookup"><span data-stu-id="429cb-196">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>
- <span data-ttu-id="429cb-197">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="429cb-197">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="429cb-198">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="429cb-198">Allowed From</span></span>

<span data-ttu-id="429cb-199">Потоки</span><span class="sxs-lookup"><span data-stu-id="429cb-199">Threads</span></span>

### <a name="example"></a><span data-ttu-id="429cb-200">Например, .</span><span class="sxs-lookup"><span data-stu-id="429cb-200">Example</span></span>

```C
/* Delete a DHCP Server instance. */

status = nx_dhcp_server_delete(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a><span data-ttu-id="429cb-201">nx_dhcp_server_start</span><span class="sxs-lookup"><span data-stu-id="429cb-201">nx_dhcp_server_start</span></span>

<span data-ttu-id="429cb-202">Запуск работы сервера DHCP.</span><span class="sxs-lookup"><span data-stu-id="429cb-202">Start DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="429cb-203">Прототип</span><span class="sxs-lookup"><span data-stu-id="429cb-203">Prototype</span></span>

```C
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="429cb-204">Описание</span><span class="sxs-lookup"><span data-stu-id="429cb-204">Description</span></span>

<span data-ttu-id="429cb-205">Эта служба запускает работу сервера DHCP, в том числе создает для сервера сокет UDP, привязывает порт DHCP и ожидает получения запросов от клиента DHCP.</span><span class="sxs-lookup"><span data-stu-id="429cb-205">This service starts DHCP Server processing, which includes creating a server UDP socket, binding the DHCP port and waiting to receive Client DHCP requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="429cb-206">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="429cb-206">Input Parameters</span></span>

- <span data-ttu-id="429cb-207">**dhcp_ptr** — указатель на ранее созданный экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="429cb-207">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="429cb-208">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="429cb-208">Return Values</span></span>

- <span data-ttu-id="429cb-209">**NX_SUCCESS** (0X00): сервер успешно запущен.</span><span class="sxs-lookup"><span data-stu-id="429cb-209">**NX_SUCCESS** (0x00) Successful Server start.</span></span>
- <span data-ttu-id="429cb-210">**NX_DHCP_ALREADY_STARTED** (0x93): сервер DHCP уже запущен.</span><span class="sxs-lookup"><span data-stu-id="429cb-210">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>
- <span data-ttu-id="429cb-211">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="429cb-211">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="429cb-212">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="429cb-212">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="429cb-213">NX_DHCP_PARAMETER_ERROR (0x92): недопустимые входные данные, кроме указателей.</span><span class="sxs-lookup"><span data-stu-id="429cb-213">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="429cb-214">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="429cb-214">Allowed From</span></span>

<span data-ttu-id="429cb-215">Потоки</span><span class="sxs-lookup"><span data-stu-id="429cb-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="429cb-216">Например, .</span><span class="sxs-lookup"><span data-stu-id="429cb-216">Example</span></span>

```C
/* Start the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_start(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

## <a name="nx_dhcp_server_stop"></a><span data-ttu-id="429cb-217">nx_dhcp_server_stop</span><span class="sxs-lookup"><span data-stu-id="429cb-217">nx_dhcp_server_stop</span></span>

<span data-ttu-id="429cb-218">Остановка работы сервера DHCP</span><span class="sxs-lookup"><span data-stu-id="429cb-218">Stops DHCP Server processing</span></span>

### <a name="prototype"></a><span data-ttu-id="429cb-219">Прототип</span><span class="sxs-lookup"><span data-stu-id="429cb-219">Prototype</span></span>

```C
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="429cb-220">Описание</span><span class="sxs-lookup"><span data-stu-id="429cb-220">Description</span></span>

<span data-ttu-id="429cb-221">Эта служба останавливает работу сервера DHCP, в том числе получение запросов от клиента DHCP.</span><span class="sxs-lookup"><span data-stu-id="429cb-221">This service stops DHCP Server processing, which includes of receiving DHCP Client requests.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="429cb-222">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="429cb-222">Input Parameters</span></span>

- <span data-ttu-id="429cb-223">**dhcp_ptr** — указатель на экземпляр сервера DHCP.</span><span class="sxs-lookup"><span data-stu-id="429cb-223">**dhcp_ptr** Pointer to DHCP Server instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="429cb-224">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="429cb-224">Return Values</span></span>

- <span data-ttu-id="429cb-225">**NX_SUCCESS** (0x00): сервер DHCP успешно остановлен.</span><span class="sxs-lookup"><span data-stu-id="429cb-225">**NX_SUCCESS** (0x00) Successful DHCP stop.</span></span>
- <span data-ttu-id="429cb-226">**NX_DHCP_ALREADY_STARTED** (0x93): сервер DHCP уже запущен.</span><span class="sxs-lookup"><span data-stu-id="429cb-226">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>
- <span data-ttu-id="429cb-227">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="429cb-227">NX_PTR_ERROR (0x16) Invalid pointer input.</span></span>
- <span data-ttu-id="429cb-228">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="429cb-228">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="429cb-229">NX_DHCP_PARAMETER_ERROR (0x92): недопустимые входные данные, кроме указателей.</span><span class="sxs-lookup"><span data-stu-id="429cb-229">NX_DHCP_PARAMETER_ERROR (0x92) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="429cb-230">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="429cb-230">Allowed From</span></span>

<span data-ttu-id="429cb-231">Потоки</span><span class="sxs-lookup"><span data-stu-id="429cb-231">Threads</span></span>

### <a name="example"></a><span data-ttu-id="429cb-232">Пример</span><span class="sxs-lookup"><span data-stu-id="429cb-232">Example</span></span>

```C
/* Stop the DHCP Server processing for this IP instance. */

status = nx_dhcp_server_stop(&dhcp_server);

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
