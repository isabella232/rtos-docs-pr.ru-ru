---
title: Глава 4. Службы сервера ОСРВ Azure NetX Duo DHCPv6
description: В этой главе приведено описание всех служб NetX Duo DHCPv6Server
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1d45139031b5a687baacf86c7a2e0a53c90533be
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814739"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-server-services"></a><span data-ttu-id="73073-103">Глава 4. Службы сервера ОСРВ Azure NetX Duo DHCPv6</span><span class="sxs-lookup"><span data-stu-id="73073-103">Chapter 4 - Azure RTOS NetX Duo DHCPv6 server services</span></span>

<span data-ttu-id="73073-104">В этой главе приведено описание всех служб NetX Duo DHCPv6Server (см. список ниже).</span><span class="sxs-lookup"><span data-stu-id="73073-104">This chapter contains a description of all NetX Duo DHCPv6Server services (listed below).</span></span>

<span data-ttu-id="73073-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="73073-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="73073-106">nx_dhcpv6_server_create *Создание DHCPv6 serverinstance*</span><span class="sxs-lookup"><span data-stu-id="73073-106">nx_dhcpv6_server_create *Create a DHCPv6 serverinstance*</span></span>
- <span data-ttu-id="73073-107">nx_dhcpv6_server_delete *Удаление DHCPv6 serverinstance*</span><span class="sxs-lookup"><span data-stu-id="73073-107">nx_dhcpv6_server_delete *Delete a DHCPv6 serverinstance*</span></span>
- <span data-ttu-id="73073-108">nx_dhcpv6_server_start *Запуск задачи DHCPv6-сервера*</span><span class="sxs-lookup"><span data-stu-id="73073-108">nx_dhcpv6_server_start *Start the DHCPv6 server task*</span></span>
- <span data-ttu-id="73073-109">nx_dhcpv6_server_suspend *Приостановка задачи DHCPv6-сервера*</span><span class="sxs-lookup"><span data-stu-id="73073-109">nx_dhcpv6_server_suspend *Suspend the DHCPv6 server task*</span></span>
- <span data-ttu-id="73073-110">nx_dhcpv6_server_resume *Возобновление клиентской обработки DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="73073-110">nx_dhcpv6_server_resume *Resume DHCPv6 client processing*</span></span>
- <span data-ttu-id="73073-111">nx_dhcpv6_server_suspend *Приостановка клиентской обработки DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="73073-111">nx_dhcpv6_server_suspend *Suspend DHCPv6 client processing*</span></span>
- <span data-ttu-id="73073-112">nx_dhcpv6_create_dns_address *Установка DNS-сервера для запросов параметров*</span><span class="sxs-lookup"><span data-stu-id="73073-112">nx_dhcpv6_create_dns_address *Set the DNS server for option requests*</span></span>
- <span data-ttu-id="73073-113">nx_dhcpv6_create_ip_address_range *Создание диапазона IP-адресов для аренды*</span><span class="sxs-lookup"><span data-stu-id="73073-113">nx_dhcpv6_create_ip_address_range *Create the range of IP addresses to lease*</span></span>
- <span data-ttu-id="73073-114">nx_dhcpv6_reserve_ip_address_range *Резервирование диапазона IP-адресов в списке сервера*</span><span class="sxs-lookup"><span data-stu-id="73073-114">nx_dhcpv6_reserve_ip_address_range *Reserve range of IP addresses in server list*</span></span>
- <span data-ttu-id="73073-115">nx_dhcpv6_set_server_duid *Установка DUID сервера для пакетов DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="73073-115">nx_dhcpv6_set_server_duid *Set the Server DUID for DHCPv6 packets*</span></span>
- <span data-ttu-id="73073-116">nx_dhcpv6_add_ip_address_lease *Добавление записи аренды в таблицу DHCPv6-сервера*</span><span class="sxs-lookup"><span data-stu-id="73073-116">nx_dhcpv6_add_ip_address_lease *Add a lease record to the DHCPv6 server table*</span></span>
- <span data-ttu-id="73073-117">Nx_dhcpv6_retrieve_ip_address_lease *Получение записи IP-аренды из таблицы сервера*</span><span class="sxs-lookup"><span data-stu-id="73073-117">Nx_dhcpv6_retrieve_ip_address_lease *Retrieve an IP lease record from the Server table*</span></span>
- <span data-ttu-id="73073-118">nx_dhcpv6_add_client_record *Добавление записи DHCPv6-клиента в таблицу сервера*</span><span class="sxs-lookup"><span data-stu-id="73073-118">nx_dhcpv6_add_client_record *Add a DHCPv6 Client record to the Server table*</span></span>
- <span data-ttu-id="73073-119">nx_dhcpv6_retrieve_client_record *Получение записи клиента из таблицы сервера*</span><span class="sxs-lookup"><span data-stu-id="73073-119">nx_dhcpv6_retrieve_client_record *Retrieve a client record from the Server table*</span></span>
- <span data-ttu-id="73073-120">nx_dhcpv6_server_interface_set *Установка индекса интерфейса для служб DHCPv6-сервера*</span><span class="sxs-lookup"><span data-stu-id="73073-120">nx_dhcpv6_server_interface_set *Set the interface index for Server DHCPv6 services*</span></span>
- <span data-ttu-id="73073-121">nx_dhcpv6_server_option_request_handler_set *Установка обработчика запроса параметра*</span><span class="sxs-lookup"><span data-stu-id="73073-121">nx_dhcpv6_server_option_request_handler_set *Set the option request handler*</span></span>

## <a name="nx_dhcpv6_create_dns_address"></a><span data-ttu-id="73073-122">nx_dhcpv6_create_dns_address</span><span class="sxs-lookup"><span data-stu-id="73073-122">nx_dhcpv6_create_dns_address</span></span>

### <a name="set-the-network-dns-server"></a><span data-ttu-id="73073-123">Установка сетевого DNS-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-123">Set the network DNS server</span></span>

<span data-ttu-id="73073-124">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="73073-124">**Prototype**</span></span>

```
UINT nx_dhcpv6_create_dns_address(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *dns_ipv6_address);
```

<span data-ttu-id="73073-125">**Описание**</span><span class="sxs-lookup"><span data-stu-id="73073-125">**Description**</span></span>

<span data-ttu-id="73073-126">Эта служба загружает DHCPv6-сервер с адресом DNS-сервера для сетевого интерфейса DHCPv6 сервера.</span><span class="sxs-lookup"><span data-stu-id="73073-126">This service loads the DHCPv6 Server with the DNS server address for the Server DHCPv6 network interface.</span></span>

<span data-ttu-id="73073-127">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="73073-127">**Input Parameters**</span></span>

- <span data-ttu-id="73073-128">**dhcpv6_server_ptr** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-128">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="73073-129">**dns_ipv6_address** Указатель на DNS-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-129">**dns_ipv6_address** Pointer to the DNS server</span></span>

<span data-ttu-id="73073-130">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="73073-130">**Return Values**</span></span>

- <span data-ttu-id="73073-131">**NX_SUCCESS** (0x00) DNS-сервер сохранен в экземпляре DHCPv6-сервера</span><span class="sxs-lookup"><span data-stu-id="73073-131">**NX_SUCCESS** (0x00) DNS Serversaved to DHCPv6 Server instance</span></span>
- <span data-ttu-id="73073-132">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) – указан недопустимый адрес</span><span class="sxs-lookup"><span data-stu-id="73073-132">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="73073-133">NX_PTR_ERROR (0x16) – недопустимые входные данные указателя</span><span class="sxs-lookup"><span data-stu-id="73073-133">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="73073-134">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="73073-134">**Allowed From**</span></span>

<span data-ttu-id="73073-135">Код приложения</span><span class="sxs-lookup"><span data-stu-id="73073-135">Application Code</span></span>

<span data-ttu-id="73073-136">**Пример**</span><span class="sxs-lookup"><span data-stu-id="73073-136">**Example**</span></span>

```
/* Set the network DNS server with the input address for the Server DHCPv6interface. */
status = nx_dhcpv6_create__dns_address(&dhcp_server_0, &dns_ipv6_address);
/* If this service returns NX_SUCCESS the DNS server data was accepted. */
```

## <a name="nx_dhcpv6_create_ip_address_range"></a><span data-ttu-id="73073-137">nx_dhcpv6_create_ip_address_range</span><span class="sxs-lookup"><span data-stu-id="73073-137">nx_dhcpv6_create_ip_address_range</span></span>

### <a name="create-the-server-ip-address-list"></a><span data-ttu-id="73073-138">Создание списка IP-адресов сервера</span><span class="sxs-lookup"><span data-stu-id="73073-138">Create the Server IP address list</span></span>

<span data-ttu-id="73073-139">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="73073-139">**Prototype**</span></span>

```
UINT _nx_dhcpv6_create_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_added)
```

<span data-ttu-id="73073-140">**Описание**</span><span class="sxs-lookup"><span data-stu-id="73073-140">**Description**</span></span>

<span data-ttu-id="73073-141">Эта служба создает список IP-адресов, определяемый начальным и конечным адресом диапазона назначаемых адресов сервера.</span><span class="sxs-lookup"><span data-stu-id="73073-141">This service creates the IP address list specified by the start and end addresses of the Server’s assignable address range.</span></span> <span data-ttu-id="73073-142">Начальный и конечный адреса должны совпадать с префиксом адреса интерфейса сервера (должны находиться по той же ссылке, что и интерфейс DHCPv6 сервера).</span><span class="sxs-lookup"><span data-stu-id="73073-142">The start and end addresses must match the Server interface address prefix (must be on the same link as the Server DHCPv6 interface).</span></span> <span data-ttu-id="73073-143">Возвращается число фактически добавленных адресов.</span><span class="sxs-lookup"><span data-stu-id="73073-143">The number of addresses actually added is returned.</span></span>

<span data-ttu-id="73073-144">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="73073-144">**Input Parameters**</span></span>

- <span data-ttu-id="73073-145">**dhcpv6_server_ptr** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-145">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="73073-146">**start_ipv6_address** Первый добавляемый адрес</span><span class="sxs-lookup"><span data-stu-id="73073-146">**start_ipv6_address** Start of addresses to add</span></span>
- <span data-ttu-id="73073-147">**end_ipv6_address** Последний добавляемый адрес</span><span class="sxs-lookup"><span data-stu-id="73073-147">**end_ipv6_address** End of addresses to add</span></span>
- <span data-ttu-id="73073-148">\***addresses_added** Результат добавления адресов</span><span class="sxs-lookup"><span data-stu-id="73073-148">\***addresses_added** Output of addresses added</span></span>

<span data-ttu-id="73073-149">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="73073-149">**Return Values**</span></span>

- <span data-ttu-id="73073-150">**NX_SUCCESS** (0x00) – список IP-адресов успешно создан</span><span class="sxs-lookup"><span data-stu-id="73073-150">**NX_SUCCESS** (0x00) IP address list successfully created</span></span>
- <span data-ttu-id="73073-151">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) – указан недопустимый адрес</span><span class="sxs-lookup"><span data-stu-id="73073-151">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="73073-152">NX_PTR_ERROR (0x16) – недопустимые входные данные указателя</span><span class="sxs-lookup"><span data-stu-id="73073-152">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="73073-153">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="73073-153">**Allowed From**</span></span>

<span data-ttu-id="73073-154">Код приложения</span><span class="sxs-lookup"><span data-stu-id="73073-154">Application Code</span></span>

<span data-ttu-id="73073-155">**Пример**</span><span class="sxs-lookup"><span data-stu-id="73073-155">**Example**</span></span>

```
/* Create the Server IP address list for the server DHCPv6 interface. */
status = nx_dhcpv6_create_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);
/* If status is NX_SUCCESS one or more addresses were successfully added. */
```

## <a name="nx_dhcpv6_reserve_ip_address_range"></a><span data-ttu-id="73073-156">nx_dhcpv6_reserve_ip_address_range</span><span class="sxs-lookup"><span data-stu-id="73073-156">nx_dhcpv6_reserve_ip_address_range</span></span>

### <a name="reserve-specified-range-of-ip-addresses"></a><span data-ttu-id="73073-157">Резервирование указанного диапазона IP-адресов</span><span class="sxs-lookup"><span data-stu-id="73073-157">Reserve specified range of IP addresses</span></span>

<span data-ttu-id="73073-158">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="73073-158">**Prototype**</span></span>

```
UINT _nx_dhcpv6_reserve_ip_address_range(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     NXD_ADDRESS *start_ipv6_address, NXD_ADDRESS *end_ipv6_address, 
     UINT *addresses_reserved)
```

<span data-ttu-id="73073-159">**Описание**</span><span class="sxs-lookup"><span data-stu-id="73073-159">**Description**</span></span>

<span data-ttu-id="73073-160">Эта служба резервирует диапазон IP-адресов, заданный начальным и конечным адресами.</span><span class="sxs-lookup"><span data-stu-id="73073-160">This service reserves the IP address range specified by the start and end addresses.</span></span> <span data-ttu-id="73073-161">Эти адреса должны находиться в пределах ранее созданного диапазона IP-адресов сервера.</span><span class="sxs-lookup"><span data-stu-id="73073-161">These addresses must be within in the previously created server IP address range.</span></span> <span data-ttu-id="73073-162">DHCPv6-сервер не будет назначать эти адреса клиентам.</span><span class="sxs-lookup"><span data-stu-id="73073-162">These addresses will not be assigned to any Clients by the DHCPv6 Server.</span></span> <span data-ttu-id="73073-163">Начальный и конечный адреса должны совпадать с префиксом адреса интерфейса сервера (должны находиться по той же ссылке, что и сетевой интерфейс DHCPv6 сервера).</span><span class="sxs-lookup"><span data-stu-id="73073-163">The start and end addresses must match the Server interface address prefix (must be on the same link as the Server DHCPv6 network interface).</span></span> <span data-ttu-id="73073-164">Возвращается число фактически зарезервированных адресов.</span><span class="sxs-lookup"><span data-stu-id="73073-164">The number of addresses actually reserved is returned.</span></span>

<span data-ttu-id="73073-165">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="73073-165">**Input Parameters**</span></span>

- <span data-ttu-id="73073-166">**dhcpv6_server_ptr** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-166">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="73073-167">**start_ipv6_address** Первый резервируемый адрес</span><span class="sxs-lookup"><span data-stu-id="73073-167">**start_ipv6_address** Start of addresses to reserve</span></span>
- <span data-ttu-id="73073-168">**end_ipv6_address** Последний резервируемый адрес</span><span class="sxs-lookup"><span data-stu-id="73073-168">**end_ipv6_address** End of addresses to reserve</span></span>
- <span data-ttu-id="73073-169">\***addresses_reserved** Число зарезервированных адресов</span><span class="sxs-lookup"><span data-stu-id="73073-169">\***addresses_reserved** Number of addresses reserved</span></span>

<span data-ttu-id="73073-170">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="73073-170">**Return Values**</span></span>

- <span data-ttu-id="73073-171">**NX_SUCCESS** (0x00) RELEASE – сообщение успешно создано и обработано</span><span class="sxs-lookup"><span data-stu-id="73073-171">**NX_SUCCESS** (0x00) RELEASE message successfully created and processed</span></span>
- <span data-ttu-id="73073-172">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) – указан недопустимый адрес</span><span class="sxs-lookup"><span data-stu-id="73073-172">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) An invalid address is supplied</span></span>
- <span data-ttu-id="73073-173">**NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) – начальный адрес не найден в списке адресов сервера.</span><span class="sxs-lookup"><span data-stu-id="73073-173">**NX_DHCPV6_INVALID_IP_ADDRESS** (0xED1) Starting address not found in Server address list.</span></span>
- <span data-ttu-id="73073-174">NX_PTR_ERROR (0x16) – недопустимые входные данные указателя</span><span class="sxs-lookup"><span data-stu-id="73073-174">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="73073-175">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="73073-175">**Allowed From**</span></span>

<span data-ttu-id="73073-176">Код приложения</span><span class="sxs-lookup"><span data-stu-id="73073-176">Application Code</span></span>

<span data-ttu-id="73073-177">**Пример**</span><span class="sxs-lookup"><span data-stu-id="73073-177">**Example**</span></span>

```
/* Reserve a range of ip addresses in the Server address table for the server DHCPv6 
network interface. */

status = nx_dhcpv6_reserve_ip_address_range(&dhcp_server_0,
         &start_ipv6_address, &end_ipv6_address, &addresses_reserved);

/* If status is NX_SUCCESS one or more addresses were successfully reserved. */
```

## <a name="nx_dhcpv6_server_create"></a><span data-ttu-id="73073-178">nx_dhcpv6_server_create</span><span class="sxs-lookup"><span data-stu-id="73073-178">nx_dhcpv6_server_create</span></span>

### <a name="create-the-dhcpv6-server-instance"></a><span data-ttu-id="73073-179">Создание экземпляра DHCPv6-сервера</span><span class="sxs-lookup"><span data-stu-id="73073-179">Create the DHCPv6 Server instance</span></span> 

<span data-ttu-id="73073-180">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="73073-180">**Prototype**</span></span>

```
UINT nx_dhcpv6_server_create(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
        NX_IP *ip_ptr, CHAR *name_ptr, 
        NX_PACKET_POOL *packet_pool_ptr, 
        VOID *stack_ptr,ULONG stack_size,
    VOID (*dhcpv6_address_declined_handler)(struct 
        NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        NX_DHCPV6_CLIENT *dhcpv6_client_ptr, 
        UINT message),
    VOID (*dhcpv6_option_request_handler)(
        struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
        UINT option_request, UCHAR *buffer_ptr, UINT *index));
```

<span data-ttu-id="73073-181">**Описание**</span><span class="sxs-lookup"><span data-stu-id="73073-181">**Description**</span></span>

<span data-ttu-id="73073-182">Эта служба создает задачу DHCPv6-сервера с указанными входными данными.</span><span class="sxs-lookup"><span data-stu-id="73073-182">This service creates the DHCPv6 Server task with the specified input.</span></span> <span data-ttu-id="73073-183">Обработчики обратного вызова являются необязательными входными данными.</span><span class="sxs-lookup"><span data-stu-id="73073-183">The callback handlers are optional input.</span></span> <span data-ttu-id="73073-184">Необходимо ввести указатель стека, IP-адрес экземпляра и входные данные пула пакетов.</span><span class="sxs-lookup"><span data-stu-id="73073-184">The stack pointer, IP instance and packet pool input are required.</span></span> <span data-ttu-id="73073-185">IP-адрес экземпляра и пул пакетов необходимо создать заранее.</span><span class="sxs-lookup"><span data-stu-id="73073-185">The IP instance and packet pool must already be created.</span></span>

<span data-ttu-id="73073-186">Пользователю рекомендуется вызвать nx_dhcpv6_server_option_request_handler_set, чтобы задать обработчик запросов параметров.</span><span class="sxs-lookup"><span data-stu-id="73073-186">User is encouraged to call nx_dhcpv6_server_option_request_handler_set to set the option request handler.</span></span>

<span data-ttu-id="73073-187">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="73073-187">**Input Parameters**</span></span>

- <span data-ttu-id="73073-188">**dhcpv6_server_ptr** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-188">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="73073-189">**ip_ptr** Указатель на IP-адрес экземпляра</span><span class="sxs-lookup"><span data-stu-id="73073-189">**ip_ptr** Pointer to the IP instance</span></span>
- <span data-ttu-id="73073-190">**name_str** Указатель на имя сервера</span><span class="sxs-lookup"><span data-stu-id="73073-190">**name_str** Pointer to Server name</span></span>
- <span data-ttu-id="73073-191">**packet_pool_ptr** Указатель на пул пакетов сервера</span><span class="sxs-lookup"><span data-stu-id="73073-191">**packet_pool_ptr** Pointer to Server packet pool</span></span>
- <span data-ttu-id="73073-192">**stack_ptr** Указатель на память стека сервера</span><span class="sxs-lookup"><span data-stu-id="73073-192">**stack_ptr** Pointer to Server stack memory</span></span>
- <span data-ttu-id="73073-193">**stack_size** Размер памяти стека сервера</span><span class="sxs-lookup"><span data-stu-id="73073-193">**stack_size** Size of Server stack memory</span></span>
- <span data-ttu-id="73073-194">**dhcpv6_address_declined_handler** Указатель на обработчик сообщений об отклонении или выпуске клиента</span><span class="sxs-lookup"><span data-stu-id="73073-194">**dhcpv6_address_declined_handler** Pointer to Client Decline or Release message handler</span></span>
- <span data-ttu-id="73073-195">**dhcpv6_option_request_handler** Указатель на обработчик параметров запросов параметров</span><span class="sxs-lookup"><span data-stu-id="73073-195">**dhcpv6_option_request_handler** Pointer to options request option handler</span></span>

<span data-ttu-id="73073-196">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="73073-196">**Return Values**</span></span>

- <span data-ttu-id="73073-197">**NX_SUCCESS** (0x00) – работа сервера успешно возобновлена</span><span class="sxs-lookup"><span data-stu-id="73073-197">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="73073-198">NX_PTR_ERROR (0x16) – недопустимые входные данные указателя</span><span class="sxs-lookup"><span data-stu-id="73073-198">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>
- <span data-ttu-id="73073-199">NX_DHCPV6_PARAM_ERROR – недопустимые входные данные без указателя</span><span class="sxs-lookup"><span data-stu-id="73073-199">NX_DHCPV6_PARAM_ERROR Invalid non pointer input</span></span>

<span data-ttu-id="73073-200">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="73073-200">**Allowed From**</span></span>

<span data-ttu-id="73073-201">Код приложения</span><span class="sxs-lookup"><span data-stu-id="73073-201">Application Code</span></span>

<span data-ttu-id="73073-202">**Пример**</span><span class="sxs-lookup"><span data-stu-id="73073-202">**Example**</span></span>

```
/* Create the DHCPv6 Server. */
status = nx_dhcpv6_server_create(&dhcp_server_0, &ip_0, "DHCPv6 Server",
         &pool_0, stack_pointer,2048, dhcpv6_decline_handler,
         dhcpv6_get_time_handler);
/* If status is NX_SUCCESS the Server successfully created. */
```

## <a name="nx_dhcpv6_server_delete"></a><span data-ttu-id="73073-203">nx_dhcpv6_server_delete</span><span class="sxs-lookup"><span data-stu-id="73073-203">nx_dhcpv6_server_delete</span></span>

### <a name="delete-the-dhcpv6-server"></a><span data-ttu-id="73073-204">Удаление DHCPv6-сервера</span><span class="sxs-lookup"><span data-stu-id="73073-204">Delete the DHCPv6 Server</span></span>

<span data-ttu-id="73073-205">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="73073-205">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_delee(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="73073-206">**Описание**</span><span class="sxs-lookup"><span data-stu-id="73073-206">**Description**</span></span>

<span data-ttu-id="73073-207">Эта служба удаляет задачу DHCPv6-сервера и все запросы, выполняемые сервером.</span><span class="sxs-lookup"><span data-stu-id="73073-207">This service deletes the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="73073-208">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="73073-208">**Input Parameters**</span></span>

- <span data-ttu-id="73073-209">**dhcpv6_server_ptr** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-209">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="73073-210">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="73073-210">**Return Values**</span></span>

- <span data-ttu-id="73073-211">**NX_SUCCESS** (0x00) – сервер успешно удален</span><span class="sxs-lookup"><span data-stu-id="73073-211">**NX_SUCCESS** (0x00) Server successfully deleted</span></span>
- <span data-ttu-id="73073-212">NX_PTR_ERROR (0x16) – недопустимые входные данные указателя</span><span class="sxs-lookup"><span data-stu-id="73073-212">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="73073-213">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="73073-213">**Allowed From**</span></span>

<span data-ttu-id="73073-214">Потоки</span><span class="sxs-lookup"><span data-stu-id="73073-214">Threads</span></span>

<span data-ttu-id="73073-215">**Пример**</span><span class="sxs-lookup"><span data-stu-id="73073-215">**Example**</span></span>

```
/* Delete the DHCPv6 Serve. */
status = nx_dhcpv6_server_delete(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully deleted. */
```

## <a name="nx_dhcpv6_server_resume"></a><span data-ttu-id="73073-216">nx_dhcpv6_server_resume</span><span class="sxs-lookup"><span data-stu-id="73073-216">nx_dhcpv6_server_resume</span></span>

### <a name="resume-dhcpv6-server-task"></a><span data-ttu-id="73073-217">Возобновление задачи DHCPv6-сервера</span><span class="sxs-lookup"><span data-stu-id="73073-217">Resume DHCPv6 Server task</span></span> 

<span data-ttu-id="73073-218">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="73073-218">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_resume(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="73073-219">**Описание**</span><span class="sxs-lookup"><span data-stu-id="73073-219">**Description**</span></span>

<span data-ttu-id="73073-220">Эта служба возобновляет задачу DHCPv6-сервера и все запросы, выполнявшиеся сервером.</span><span class="sxs-lookup"><span data-stu-id="73073-220">This service resumes the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="73073-221">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="73073-221">**Input Parameters**</span></span>

- <span data-ttu-id="73073-222">**dhcpv6_server_ptr** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-222">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="73073-223">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="73073-223">**Return Values**</span></span>

- <span data-ttu-id="73073-224">**NX_SUCCESS** (0x00) – работа сервера успешно возобновлена</span><span class="sxs-lookup"><span data-stu-id="73073-224">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="73073-225">**NX_DHCPV6_ALREADY_STARTED** (0xE91) – сервер уже запущен</span><span class="sxs-lookup"><span data-stu-id="73073-225">**NX_DHCPV6_ALREADY_STARTED** (0xE91) Server is running already</span></span>
- <span data-ttu-id="73073-226">**состояние** (переменная) – состояние ошибки ThreadX и NetX Duo</span><span class="sxs-lookup"><span data-stu-id="73073-226">**status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="73073-227">NX_PTR_ERROR (0x16) – недопустимые входные данные указателя</span><span class="sxs-lookup"><span data-stu-id="73073-227">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="73073-228">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="73073-228">**Allowed From**</span></span>

<span data-ttu-id="73073-229">Потоки</span><span class="sxs-lookup"><span data-stu-id="73073-229">Threads</span></span>

<span data-ttu-id="73073-230">**Пример**</span><span class="sxs-lookup"><span data-stu-id="73073-230">**Example**</span></span>

```
/* Resume the DHCPv6 Server task. */
status = nx_dhcpv6_server_resume(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully resumed. */
```

## <a name="nx_dhcpv6_server_suspend"></a><span data-ttu-id="73073-231">nx_dhcpv6_server_suspend</span><span class="sxs-lookup"><span data-stu-id="73073-231">nx_dhcpv6_server_suspend</span></span>

### <a name="suspend-dhcpv6-server-task"></a><span data-ttu-id="73073-232">Приостановка задачи DHCPv6-сервера</span><span class="sxs-lookup"><span data-stu-id="73073-232">Suspend DHCPv6 Server task</span></span> 

<span data-ttu-id="73073-233">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="73073-233">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_suspend(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="73073-234">**Описание**</span><span class="sxs-lookup"><span data-stu-id="73073-234">**Description**</span></span>

<span data-ttu-id="73073-235">Эта служба приостанавливает задачу DHCPv6-сервера и все запросы, выполняемые сервером.</span><span class="sxs-lookup"><span data-stu-id="73073-235">This service suspends the DHCPv6 Server task and any request that the Server was processing.</span></span>

<span data-ttu-id="73073-236">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="73073-236">**Input Parameters**</span></span>

- <span data-ttu-id="73073-237">**dhcpv6_server_ptr** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-237">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="73073-238">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="73073-238">**Return Values**</span></span>

- <span data-ttu-id="73073-239">**NX_SUCCESS** (0x00) – работа сервера успешно возобновлена</span><span class="sxs-lookup"><span data-stu-id="73073-239">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="73073-240">**NX_DHCPV6_NOT_STARTED** (0xE92) – сервер не запущен</span><span class="sxs-lookup"><span data-stu-id="73073-240">**NX_DHCPV6_NOT_STARTED** (0xE92) Server is not started</span></span> 
- <span data-ttu-id="73073-241">**состояние** (переменная) – состояние ошибки ThreadX и NetX Duo</span><span class="sxs-lookup"><span data-stu-id="73073-241">**Status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="73073-242">NX_PTR_ERROR (0x16) – недопустимые входные данные указателя</span><span class="sxs-lookup"><span data-stu-id="73073-242">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="73073-243">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="73073-243">**Allowed From**</span></span>

<span data-ttu-id="73073-244">Потоки</span><span class="sxs-lookup"><span data-stu-id="73073-244">Threads</span></span>

<span data-ttu-id="73073-245">**Пример**</span><span class="sxs-lookup"><span data-stu-id="73073-245">**Example**</span></span>

```
/* Suspend the DHCPv6 Server task. */
status = nx_dhcpv6_server_suspend(&dhcp_server_0);

/* If status is NX_SUCCESS the Server successfully suspended. */
```

## <a name="nx_dhcpv6_server_start"></a><span data-ttu-id="73073-246">nx_dhcpv6_server_start</span><span class="sxs-lookup"><span data-stu-id="73073-246">nx_dhcpv6_server_start</span></span>

### <a name="start-the-dhcpv6-server-task"></a><span data-ttu-id="73073-247">Запуск задачи DHCPv6-сервера</span><span class="sxs-lookup"><span data-stu-id="73073-247">Start the DHCPv6 Server task</span></span> 

<span data-ttu-id="73073-248">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="73073-248">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_start(NX_DHCPV6_SERVER *dhcpv6_server_ptr)
```

<span data-ttu-id="73073-249">**Описание**</span><span class="sxs-lookup"><span data-stu-id="73073-249">**Description**</span></span>

<span data-ttu-id="73073-250">Эта служба запускает задачу DHCPv6-сервера и готовит сервер к обработке запросов приложений на получение сообщений клиента DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="73073-250">This service starts the DHCPv6 Server task and readies the Server to process application requests for receiving DHCPv6 Client messages.</span></span> <span data-ttu-id="73073-251">Она проверяет, имеет ли экземпляр сервера достаточно информации (DUID сервера), создает и привязывает UDP-сокет для отправки и получения сообщений DHCPv6, а также активирует таймеры для отслеживания времени сеанса и истечения срока действия IP-аренды.</span><span class="sxs-lookup"><span data-stu-id="73073-251">It verifies the Server instance has sufficient information (Server DUID), creates and binds the UDP socket for sending and receiving DHCPv6 messages, and activates timers for keeping track of session time and IP lease expiration.</span></span>

>[!NOTE] 
> <span data-ttu-id="73073-252">Перед запуском DHCPv6-сервера ведущее приложение должно создать диапазон IP-адресов, из которого сервер будет назначать адреса.</span><span class="sxs-lookup"><span data-stu-id="73073-252">Before the DHCPv6 Server can run, the host application is responsible for creating the IP address range from which the Server can assign IP addresses.</span></span> <span data-ttu-id="73073-253">Оно также настраивает DUID сервера и интерфейса DHCPv6 (см. *nx_dhcpv6_server_duid_set* и *nx_dhcpv6_server_interface_set* соответственно.</span><span class="sxs-lookup"><span data-stu-id="73073-253">It is also responsible for setting the Server DUID and DHCPv6 interface (see *nx_dhcpv6_server_duid_set* and *nx_dhcpv6_server_interface_set* respectively.</span></span>

<span data-ttu-id="73073-254">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="73073-254">**Input Parameters**</span></span>

- <span data-ttu-id="73073-255">**dhcpv6_server_ptr** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-255">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="73073-256">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="73073-256">**Return Values**</span></span>

- <span data-ttu-id="73073-257">**NX_SUCCESS** (0x00) – сервер успешно запущен</span><span class="sxs-lookup"><span data-stu-id="73073-257">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="73073-258">**NX_DHCPV6_ALREADY_STARTED** (0xE91) – сервер уже запущен</span><span class="sxs-lookup"><span data-stu-id="73073-258">**NX_DHCPV6_ALREADY_STARTED** (0xE91) Server is running already</span></span>
- <span data-ttu-id="73073-259">**NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) – для сервера не заданы назначаемые адреса для аренды</span><span class="sxs-lookup"><span data-stu-id="73073-259">**NX_DHCPV6_NO_ASSIGNABLE_ADDRESSES** (0xEA7) Server has no assignable addresses to lease</span></span>
- <span data-ttu-id="73073-260">**NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) – глобальный индекс адреса не задан</span><span class="sxs-lookup"><span data-stu-id="73073-260">**NX_DHCPV6_INVALID_GLOBAL_INDEX** (0xE97) Global address index not set</span></span>
- <span data-ttu-id="73073-261">**NX_DHCPV6_NO_SERVER_DUID** (0xE92) – DUID сервера не создан</span><span class="sxs-lookup"><span data-stu-id="73073-261">**NX_DHCPV6_NO_SERVER_DUID** (0xE92) No Server DUID created</span></span> 
- <span data-ttu-id="73073-262">**состояние** (переменная) – состояние ошибки ThreadX и NetX Duo</span><span class="sxs-lookup"><span data-stu-id="73073-262">**status** (variable) ThreadX and NetX Duo error status</span></span>
- <span data-ttu-id="73073-263">NX_PTR_ERROR (0x16) – недопустимые входные данные указателя</span><span class="sxs-lookup"><span data-stu-id="73073-263">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="73073-264">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="73073-264">**Allowed From**</span></span>

<span data-ttu-id="73073-265">Потоки</span><span class="sxs-lookup"><span data-stu-id="73073-265">Threads</span></span>

<span data-ttu-id="73073-266">**Пример**</span><span class="sxs-lookup"><span data-stu-id="73073-266">**Example**</span></span>

```
/* Start the DHCPv6 Server task. */
status = nx_dhcpv6_server_start(&dhcp_server_0);
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_retrieve_ip_address_lease"></a><span data-ttu-id="73073-267">nx_dhcpv6_retrieve_ip_address_lease</span><span class="sxs-lookup"><span data-stu-id="73073-267">nx_dhcpv6_retrieve_ip_address_lease</span></span>

### <a name="get-an-ip-address-lease-from-the-server-table"></a><span data-ttu-id="73073-268">Получение IP-адреса для аренды из таблицы сервера</span><span class="sxs-lookup"><span data-stu-id="73073-268">Get an IP address lease from the Server table</span></span>

<span data-ttu-id="73073-269">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="73073-269">**Prototype**</span></span>

```
UINT _nx_dhcpv6_retrieve_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, 
     NXD_ADDRESS *lease_IP_address, ULONG *T1, ULONG *T2, 
     ULONG *valid_lifetime, ULONG *preferred_lifetime)
```

<span data-ttu-id="73073-270">**Описание**</span><span class="sxs-lookup"><span data-stu-id="73073-270">**Description**</span></span>

<span data-ttu-id="73073-271">Эта служба получает запись аренды IP-адреса из таблицы сервера в указанном месте таблицы по индексу.</span><span class="sxs-lookup"><span data-stu-id="73073-271">This service retrieves an IP address lease record from the Server table at the specified table index location.</span></span> <span data-ttu-id="73073-272">Это можно сделать до или после получения данных записи клиента.</span><span class="sxs-lookup"><span data-stu-id="73073-272">This can be done before or after retrieving Client record data.</span></span>

<span data-ttu-id="73073-273">Возможность хранения и извлечения данных между DHCPv6-сервером и энергонезависимой памятью является обязательным условием работы по протоколу DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="73073-273">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span> <span data-ttu-id="73073-274">Это не влияет на порядок сохранения данных IP-аренды и данных записи клиента в энергонезависимой памяти.</span><span class="sxs-lookup"><span data-stu-id="73073-274">It makes no difference in what order IP lease data and Client record data is saved to nonvolatile memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="73073-275">Не рекомендуется копировать данные в таблицах сервера без предварительной остановки или приостановки DHCPv6-сервера.</span><span class="sxs-lookup"><span data-stu-id="73073-275">It is not recommended to copy data to or from Server tables without stopping or suspending the DHCPv6 Server first.</span></span>

<span data-ttu-id="73073-276">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="73073-276">**Input Parameters**</span></span>

- <span data-ttu-id="73073-277">**dhcpv6_server_ptr** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-277">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="73073-278">**table_index** – индекс таблицы для хранения данных аренды</span><span class="sxs-lookup"><span data-stu-id="73073-278">**table_index** Table index to store lease at</span></span>
- <span data-ttu-id="73073-279">**lease_IP_address** – указатель на IP-адрес, предоставленный в аренду клиенту</span><span class="sxs-lookup"><span data-stu-id="73073-279">**lease_IP_address** Pointer to IP address leased to the Client</span></span>
- <span data-ttu-id="73073-280">**T1** – время на возобновление, запрошенное клиентом</span><span class="sxs-lookup"><span data-stu-id="73073-280">**T1** Client requested renew time</span></span>
- <span data-ttu-id="73073-281">**T2** – время на восстановление соединений, запрошенное клиентом</span><span class="sxs-lookup"><span data-stu-id="73073-281">**T2** Client requested rebind time</span></span>
- <span data-ttu-id="73073-282">**valid_lifetime** – срок аренды для клиента становится нерекомендуемым</span><span class="sxs-lookup"><span data-stu-id="73073-282">**valid_lifetime** Client lease becomes deprecated</span></span>
- <span data-ttu-id="73073-283">**preferred_lifetime** – срок аренды для клиента истекает</span><span class="sxs-lookup"><span data-stu-id="73073-283">**preferred_lifetime** Client lease becomes invalid</span></span>

<span data-ttu-id="73073-284">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="73073-284">**Return Values**</span></span>

- <span data-ttu-id="73073-285">**NX_SUCCESS** (0x00) – сервер успешно запущен</span><span class="sxs-lookup"><span data-stu-id="73073-285">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="73073-286">**NX_DHCPV6_PARAMETER_ERROR** (0xE93) – введены недопустимые входные данные IP-аренды</span><span class="sxs-lookup"><span data-stu-id="73073-286">**NX_DHCPV6_PARAMETER_ERROR** (0xE93) Invalid IP lease data input</span></span>
- <span data-ttu-id="73073-287">NX_PTR_ERROR (0x16) – недопустимые входные данные указателя</span><span class="sxs-lookup"><span data-stu-id="73073-287">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="73073-288">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="73073-288">**Allowed From**</span></span>

<span data-ttu-id="73073-289">Код приложения</span><span class="sxs-lookup"><span data-stu-id="73073-289">Application code</span></span>

<span data-ttu-id="73073-290">**Пример**</span><span class="sxs-lookup"><span data-stu-id="73073-290">**Example**</span></span>

```
/* Retrieve the DHCPv6 Server lease data. */
For (I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
{
    /* Get the next lease record. */
    status = nx_dhcpv6_server_startdhcpv6_server_ptr, i, &next_ipv6_address, &T1,
             &T2, &preferred_lifetime, &valid_lifetime);
    /* The host application then saves this record to memory.
}
/* If status is NX_SUCCESS the Server data is successfully downloaded. */
```

## <a name="nx_dhcpv6_add_ip_address_lease"></a><span data-ttu-id="73073-291">nx_dhcpv6_add_ip_address_lease</span><span class="sxs-lookup"><span data-stu-id="73073-291">nx_dhcpv6_add_ip_address_lease</span></span>

### <a name="add-an-ip-address-lease-to-the-server-table"></a><span data-ttu-id="73073-292">Добавление IP-адреса для аренды в таблицу сервера</span><span class="sxs-lookup"><span data-stu-id="73073-292">Add an IP address lease to the Server table</span></span>

<span data-ttu-id="73073-293">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="73073-293">**Prototype**</span></span>

```
UINT _nx_dhcpv6_add_ip_address_lease(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, UINT table_index, NXD_ADDRESS *lease_IP_address, ULONG T1, ULONG T2, 
     ULONG valid_lifetime, ULONG preferred_lifetime)
```

<span data-ttu-id="73073-294">**Описание**</span><span class="sxs-lookup"><span data-stu-id="73073-294">**Description**</span></span>

<span data-ttu-id="73073-295">Эта служба загружает данные об аренде IP-адреса из предыдущего сеанса сервера DHCPv6, сохраненного в энергонезависимой памяти, в таблицу аренды сервера.</span><span class="sxs-lookup"><span data-stu-id="73073-295">This service loads IP lease data from a previous DHCPv6 Server session from non volatile memory to the Server lease table.</span></span> <span data-ttu-id="73073-296">Это необязательно, если сервер запускается в первый раз и предыдущих данных аренды нет.</span><span class="sxs-lookup"><span data-stu-id="73073-296">This is not necessary if the Server is running for the first time and has no previous lease data.</span></span> <span data-ttu-id="73073-297">В этом случае ведущее приложение должно создать диапазон IP-адресов для назначения с помощью службы *nx_dhcpv6_create_ip_address_range*.</span><span class="sxs-lookup"><span data-stu-id="73073-297">If this is the case the host application must create an IP address range for assigning IP addresses, using the *nx_dhcpv6_create_ip_address_range* service.</span></span> <span data-ttu-id="73073-298">Этих данных будет достаточно для воссоздания записи аренды DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="73073-298">The data is sufficient to reconstruct a DHCPv6 lease record.</span></span> <span data-ttu-id="73073-299">Индекс таблицы указывать не нужно.</span><span class="sxs-lookup"><span data-stu-id="73073-299">The table index need not be specified.</span></span> <span data-ttu-id="73073-300">Если задано значение 0xFFFFFFFF (бесконечность), DHCPv6-сервер скопирует данные в ближайший доступный слот.</span><span class="sxs-lookup"><span data-stu-id="73073-300">If set to 0xFFFFFFFF (infinity) the DHCPv6 Server will find the next available slot to copy the data to.</span></span>

>[!NOTE] 
> <span data-ttu-id="73073-301">Перед отправкой записей клиентов необходимо выполнить отправку данных об аренде IP-адреса. Обе операции необходимо выполнить до (повторного) запуска DHCPv6-сервера.</span><span class="sxs-lookup"><span data-stu-id="73073-301">Uploading IP lease data MUST be done before uploading Client records; both MUST be done before (re)starting the DHCPv6 Server.</span></span>

<span data-ttu-id="73073-302">Возможность хранения и извлечения данных между DHCPv6-сервером и энергонезависимой памятью является обязательным условием работы по протоколу DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="73073-302">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span>

<span data-ttu-id="73073-303">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="73073-303">**Input Parameters**</span></span>

- <span data-ttu-id="73073-304">**dhcpv6_server_ptr** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-304">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="73073-305">**table_index** – индекс таблицы для хранения данных аренды</span><span class="sxs-lookup"><span data-stu-id="73073-305">**table_index** Table index to store lease at</span></span>
- <span data-ttu-id="73073-306">**lease_IP_address** – указатель на IP-адрес, предоставленный в аренду клиенту</span><span class="sxs-lookup"><span data-stu-id="73073-306">**lease_IP_address** Pointer to IP address leased to the Client</span></span>
- <span data-ttu-id="73073-307">**T1** – время на возобновление, запрошенное клиентом</span><span class="sxs-lookup"><span data-stu-id="73073-307">**T1** Client requested renew time</span></span>
- <span data-ttu-id="73073-308">**T2** – время на восстановление соединений, запрошенное клиентом</span><span class="sxs-lookup"><span data-stu-id="73073-308">**T2** Client requested rebind time</span></span>
- <span data-ttu-id="73073-309">**valid_lifetime** – срок аренды для клиента становится нерекомендуемым</span><span class="sxs-lookup"><span data-stu-id="73073-309">**valid_lifetime** Client lease becomes deprecated</span></span>
- <span data-ttu-id="73073-310">**preferred_lifetime** – срок аренды для клиента истекает</span><span class="sxs-lookup"><span data-stu-id="73073-310">**preferred_lifetime** Client lease becomes invalid</span></span>

<span data-ttu-id="73073-311">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="73073-311">**Return Values**</span></span>

- <span data-ttu-id="73073-312">**NX_SUCCESS** (0x00) – сервер успешно запущен</span><span class="sxs-lookup"><span data-stu-id="73073-312">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="73073-313">**NX_DHCPV6_TABLE_FULL** (0xEC4) – нет места для добавления данных об аренде\*\*</span><span class="sxs-lookup"><span data-stu-id="73073-313">**NX_DHCPV6_TABLE_FULL** (0xEC4) No room for more lease data\*\*</span></span>
- <span data-ttu-id="73073-314">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) – вероятно, данные аренды не связаны с интерфейсом сервера DHCPv6</span><span class="sxs-lookup"><span data-stu-id="73073-314">**NX_DHCPV6_INVALID_INTERFACE_IP_ADDRESS** (0xE95) Lease data does not appear to be on link with Server DHCPv6 interface</span></span>
- <span data-ttu-id="73073-315">**NX_DHCPV6_PARAM_ERROR** (0xE93) – недопустимые входные данные об аренде IP-адресов</span><span class="sxs-lookup"><span data-stu-id="73073-315">**NX_DHCPV6_PARAM_ERROR** (0xE93) Invalid IP lease data input</span></span>
- <span data-ttu-id="73073-316">NX_PTR_ERROR (0x16) – недопустимые входные данные указателя</span><span class="sxs-lookup"><span data-stu-id="73073-316">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="73073-317">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="73073-317">**Allowed From**</span></span>

<span data-ttu-id="73073-318">Код приложения</span><span class="sxs-lookup"><span data-stu-id="73073-318">Application code</span></span>

<span data-ttu-id="73073-319">**Пример**</span><span class="sxs-lookup"><span data-stu-id="73073-319">**Example**</span></span>

```
/* Copy the IP lease data to the Server address table. Note that the table index
is defaulted to 0xFFFFFFFF meaning the DHCPv6 Server will find an empty slot 
for each lease. */

    For(I = 0; I < NX_DHCPV6_MAX_LEASES; i++)
    {
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr, 0xFFFFFFFF,
                 &next_ipv6_address, &T1, &T2, &preferred_lifetime, &valid_lifetime);
        /* Get the next lease address from memory… */
    }
    
    /* If status is NX_SUCCESS the lease data was successfully uploaded. It is opk
    to add the Client records to the Server table now. */
```

## <a name="nx_dhcpv6_add_client_record"></a><span data-ttu-id="73073-320">nx_dhcpv6_add_client_record</span><span class="sxs-lookup"><span data-stu-id="73073-320">nx_dhcpv6_add_client_record</span></span>

### <a name="add-a-client-record-to-the-server-table"></a><span data-ttu-id="73073-321">Добавление записи клиента в таблицу сервера</span><span class="sxs-lookup"><span data-stu-id="73073-321">Add a Client record to the Server table</span></span>

<span data-ttu-id="73073-322">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="73073-322">**Prototype**</span></span>

```
UINT _nx_dhcpv6_add_client_record(NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG message_xid, 
     NXD_ADDRESS *client_address, UINT client_state, 
     ULONG IP_lease_time_accrued, ULONG valid_lifetime, UINT duid_type, UINTduid_hardware, 
     ULONG physical_address_msw, ULONG physical_address_lsw, ULONG duid_time, 
     ULONG duid_vendor_number, UCHAR *duid_vendor_private, UINT duid_private_length)
```

<span data-ttu-id="73073-323">**Описание**</span><span class="sxs-lookup"><span data-stu-id="73073-323">**Description**</span></span>

<span data-ttu-id="73073-324">Эта служба копирует данные клиента из энергонезависимой памяти в таблицу сервера по одной записи за раз.</span><span class="sxs-lookup"><span data-stu-id="73073-324">This service copies Client data from non volatile memory to the Server table one record at a time.</span></span> <span data-ttu-id="73073-325">Это необходимо только при перезагрузке сервера и при наличии в памяти данных клиента из предыдущего сеанса для восстановления.</span><span class="sxs-lookup"><span data-stu-id="73073-325">This is only necessary if the Server is being rebooted and has Client data from a previous session to restore from memory.</span></span> <span data-ttu-id="73073-326">Если на сервере нет данных из предыдущего сеанса, DHCPv6-сервер инициализирует таблицу клиента для добавления записей клиента.</span><span class="sxs-lookup"><span data-stu-id="73073-326">If a Server has no previous data, the DHCPv6 Server will initialize the Client table to be able for adding Client records.</span></span>

<span data-ttu-id="73073-327">Указывать индекс таблицы необязательно.</span><span class="sxs-lookup"><span data-stu-id="73073-327">It is not necessary to specify the table index.</span></span> <span data-ttu-id="73073-328">Если задано значение 0xFFFFFFFF (бесконечность), DHCPv6-сервер будет использовать ближайший доступный слот.</span><span class="sxs-lookup"><span data-stu-id="73073-328">If set to 0xFFFFFFFF (infinity) the DHCPv6 Server will locate the next available slot.</span></span> <span data-ttu-id="73073-329">На основе этих данных DHCPv6-сервер может воссоздать запись клиента.</span><span class="sxs-lookup"><span data-stu-id="73073-329">The DHCPv6 Server can reconstruct a Client record from this data.</span></span>

>[!NOTE] 
> <span data-ttu-id="73073-330">Ведущее приложение ДОЛЖНО передать данные об аренде IP-адресов ПЕРЕД передачей данных записи клиента.</span><span class="sxs-lookup"><span data-stu-id="73073-330">The host application MUST upload the IP lease data BEFORE the Client record data.</span></span> <span data-ttu-id="73073-331">Это позволяет внутреннему серверу DHCPv6 связывать таблицы, т.е. соединять записи клиента с записями аренды IP-адреса в соответствующих таблицах.</span><span class="sxs-lookup"><span data-stu-id="73073-331">This is so that internally the DHCPv6 Server can cross link the tables so that each Client record is joined with its corresponding IP lease record in their respective tables.</span></span> <span data-ttu-id="73073-332">Дополнительную информацию о передаче данных об аренде IP-адресов см. в разделе *nx_dhcpv6_add_ip_address_lease*.</span><span class="sxs-lookup"><span data-stu-id="73073-332">See *nx_dhcpv6_add_ip_address_lease* for details on uploading IP lease data from memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="73073-333">В зависимости от типа DUID некоторые данные можно не указывать.</span><span class="sxs-lookup"><span data-stu-id="73073-333">Depending on DUID type, not all data must be supplied.</span></span> <span data-ttu-id="73073-334">Например, если у клиента есть назначенный поставщиком тип DUID, он может отправить нулевое значение для параметров канального уровня DUID (MAC-адрес, тип оборудования, время DUID).</span><span class="sxs-lookup"><span data-stu-id="73073-334">For example if a Client has a vendor assigned DUID type, it can send in zero for DUID Link Layer parameters (MAC address, hardware type, DUID time).</span></span>

<span data-ttu-id="73073-335">Возможность хранения и извлечения данных между DHCPv6-сервером и энергонезависимой памятью является обязательным условием работы по протоколу DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="73073-335">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span>

<span data-ttu-id="73073-336">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="73073-336">**Input Parameters**</span></span>

- <span data-ttu-id="73073-337">**dhcpv6_server_ptr** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-337">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="73073-338">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="73073-338">**Return Values**</span></span>

- <span data-ttu-id="73073-339">**NX_SUCCESS** (0x00) – сервер успешно запущен</span><span class="sxs-lookup"><span data-stu-id="73073-339">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="73073-340">**NX_ INVALID_PARAMETERS** (0x4D) – недопустимые входные данные без указателя\*\*</span><span class="sxs-lookup"><span data-stu-id="73073-340">**NX_ INVALID_PARAMETERS** (0x4D) Invalid non pointer input\*\*</span></span>
- <span data-ttu-id="73073-341">**NX_DHCPV6_TABLE_FULL** (0xEC4) – нет свободных слотов для добавления записи клиента</span><span class="sxs-lookup"><span data-stu-id="73073-341">**NX_DHCPV6_TABLE_FULL** (0xEC4) No empty slots left for adding another Client record</span></span>
- <span data-ttu-id="73073-342">**NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) – адрес, назначенный клиенту, не найден в таблице данных сервера об аренде.</span><span class="sxs-lookup"><span data-stu-id="73073-342">**NX_DHCPV6_ADDRESS_NOT_FOUND** (0xEA8) Client assigned address not found in Server lease table.</span></span>
- <span data-ttu-id="73073-343">NX_PTR_ERROR (0x16) – недопустимые входные данные указателя</span><span class="sxs-lookup"><span data-stu-id="73073-343">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="73073-344">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="73073-344">**Allowed From**</span></span>

<span data-ttu-id="73073-345">Код приложения</span><span class="sxs-lookup"><span data-stu-id="73073-345">Application code</span></span>

<span data-ttu-id="73073-346">**Пример**</span><span class="sxs-lookup"><span data-stu-id="73073-346">**Example**</span></span>

```
/*Add the IP lease data and Client records back to the server before starting
theServer. */
    /* Copy the 'lease data' to the server table FIRST. */
for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {

        /* Add the next lease record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_ip_address_lease(dhcpv6_server_ptr,
                 0xFFFFFFFF,,&next_ipv6_address, NX_DHCPV6_DEFAULT_T1_TIME, 
                 NX_DHCPV6_DEFAULT_T2_TIME, NX_DHCPV6_DEFAULT_PREFERRED_TIME, 
                 NX_DHCPV6_DEFAULT_VALID_TIME);
if (status != NX_SUCCESS)
return status;
        /* Get the next IP lease record from memory. */
        …
    }
    /* Copy the client records to the Server table NEXT.
    for (i = 0; i< NX_DHCPV6_MAX_LEASES; i++)
    {
        /* Add the next client record. Let the server find the next
        available slot. */
        status = nx_dhcpv6_add_client_record(dhcpv6_server_ptr, 0xFFFFFFFF,
                 message_xid, &client_ipv6_address, NX_DHCPV6_STATE_BOUND,
                 IP_lifetime_time_accrued, valid_lifetime, duid_type, 
                 duid_hardware, physical_address_msw, physical_address_lsw, 
                 duid_time, 0, NX_NULL, 0);
if (status != NX_SUCCESS)
return status;
        /* Get the next Client record from memory. */
        …
    }

/* If status is NX_SUCCESS the Server data was successfully restored and 
it is ok to start the DHCPv6 server now. */
```

## <a name="nx_dhcpv6_retrieve_client_record"></a><span data-ttu-id="73073-347">nx_dhcpv6_retrieve_client_record</span><span class="sxs-lookup"><span data-stu-id="73073-347">nx_dhcpv6_retrieve_client_record</span></span>

### <a name="retrieve-a-client-record-from-the-server-table"></a><span data-ttu-id="73073-348">Получение записи клиента из таблицы сервера</span><span class="sxs-lookup"><span data-stu-id="73073-348">Retrieve a Client record from the Server table</span></span>

<span data-ttu-id="73073-349">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="73073-349">**Prototype**</span></span>

```
UINT _nx_dhcpv6_retrieve_client_record(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT table_index, ULONG *message_xid, 
     NXD_ADDRESS *client_address, UINT *client_state, 
     ULONG IP_lease_time_accrued, 
     ULONG *valid_lifetime, UINT *duid_type, 
     UINT *duid_hardware, ULONG *physical_address_msw, 
     ULONG *physical_address_lsw, ULONG *duid_time, 
     ULONG *duid_vendor_number, 
     UCHAR *duid_vendor_private, 
     UINT *duid_private_length)
```

<span data-ttu-id="73073-350">**Описание**</span><span class="sxs-lookup"><span data-stu-id="73073-350">**Description**</span></span>

<span data-ttu-id="73073-351">Эта служба копирует основные данные из таблицы записей клиентов сервера для хранения в энергонезависимой памяти.</span><span class="sxs-lookup"><span data-stu-id="73073-351">This service copies the essential data from the Server’s Client record table for storage to non-volatile memory.</span></span> <span data-ttu-id="73073-352">Сервер может воссоздать соответствующую запись клиента из таких данных в обратном процессе (отправка данных в таблицу сервера).</span><span class="sxs-lookup"><span data-stu-id="73073-352">The Server can reconstruct an adequate Client record from such data in the reverse process (uploading data to the Server table).</span></span> <span data-ttu-id="73073-353">Независимо от типа DUID указатель не может быть нулевым значением; при инициализации для всех параметров будут установлены нулевые значения.</span><span class="sxs-lookup"><span data-stu-id="73073-353">Regardless of the DUID type, none of the pointers can be NULL pointers; data is initialized to zero for all parameters.</span></span> <span data-ttu-id="73073-354">Например, если тип DUID клиента — канальный слой и время, возвращается нулевое значение поставщика и пустая строка вместо частного идентификатора.</span><span class="sxs-lookup"><span data-stu-id="73073-354">For example, if the Client DUID type is Link Layer Plus Time, the vendor number is returned as zero and the private ID is an empty string.</span></span>

<span data-ttu-id="73073-355">Возможность хранения и извлечения данных между DHCPv6-сервером и энергонезависимой памятью является обязательным условием работы по протоколу DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="73073-355">The capability of storing and retrieving data between the DHCPv6 Server and non volatile memory is a requirement of the DHCPv6 protocol.</span></span> <span data-ttu-id="73073-356">Это не влияет на порядок сохранения данных IP-аренды и данных записи клиента в энергонезависимой памяти.</span><span class="sxs-lookup"><span data-stu-id="73073-356">It makes no difference in what order IP lease data and Client record data is saved to nonvolatile memory.</span></span>

>[!NOTE] 
> <span data-ttu-id="73073-357">Не рекомендуется копировать данные в таблицах сервера без предварительной остановки или приостановки DHCPv6-сервера.</span><span class="sxs-lookup"><span data-stu-id="73073-357">It is not recommended to copy data to or from Server tables without stopping or suspending the DHCPv6 Server first.</span></span>

<span data-ttu-id="73073-358">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="73073-358">**Input Parameters**</span></span>

- <span data-ttu-id="73073-359">**dhcpv6_server_ptr** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-359">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="73073-360">**table_index** Индекс для таблицы данных клиентов сервера</span><span class="sxs-lookup"><span data-stu-id="73073-360">**table_index** Index into Server’s client table</span></span>
- <span data-ttu-id="73073-361">**message_xid** Идентификатор транзакции клиентского сервера</span><span class="sxs-lookup"><span data-stu-id="73073-361">**message_xid** Client Server Transaction ID</span></span>
- <span data-ttu-id="73073-362">**client_address** IPv6-адрес, предоставленный клиенту в аренду</span><span class="sxs-lookup"><span data-stu-id="73073-362">**client_address** IPv6 address leased to Client</span></span>
- <span data-ttu-id="73073-363">**client_state** Состояние DHCPv6 клиента (например, "ограниченный")</span><span class="sxs-lookup"><span data-stu-id="73073-363">**client_state** Client DHCPv6 state (e.g. bound)</span></span>
- <span data-ttu-id="73073-364">**IP_lease_time_accrued** Текущий срок аренды **dhcpv6_server_ptr** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-364">**IP_lease_time_accrued** Time expired on lease already **dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="73073-365">**dhcpv6_server_ptr** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-365">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>

<span data-ttu-id="73073-366">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="73073-366">**Return Values**</span></span>

- <span data-ttu-id="73073-367">**NX_SUCCESS** (0x00) – сервер успешно запущен</span><span class="sxs-lookup"><span data-stu-id="73073-367">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="73073-368">**NX_DHCPV6_INVALID_DUID** (0xECC) – недопустимые или противоречивые данные DUID</span><span class="sxs-lookup"><span data-stu-id="73073-368">**NX_DHCPV6_INVALID_DUID** (0xECC) Invalid or inconsistent DUID data</span></span>
- <span data-ttu-id="73073-369">**NX_PTR_ERROR** (0x16) – недопустимые входные данные указателя</span><span class="sxs-lookup"><span data-stu-id="73073-369">**NX_PTR_ERROR** (0x16) Invalid pointer input</span></span>
- <span data-ttu-id="73073-370">NX_INVALID_PARAMETERS (0x4D) – недопустимые входные данные без указателя</span><span class="sxs-lookup"><span data-stu-id="73073-370">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

<span data-ttu-id="73073-371">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="73073-371">**Allowed From**</span></span>

<span data-ttu-id="73073-372">Код приложения</span><span class="sxs-lookup"><span data-stu-id="73073-372">Application code</span></span>

<span data-ttu-id="73073-373">**Пример**</span><span class="sxs-lookup"><span data-stu-id="73073-373">**Example**</span></span>

```
/* Retrieve the Client records from the DHCPv6 Server table. */
For (i = 0; i< NX_MAX_DHCPV6_CLIENTS; i++)
{
    status = nx_dhcpv6_retrieve_client_recorddhcpv6_server_ptr, i, &message_xid,
             &client_ipv6_address, &client_state, &IP_lifetime_time_accrued, 
             valid_lifetime, &duid_type, &duid_hardware, &physical_address_msw,
             &physical_address_lsw, &duid_time, &duid_vendor_number, &private_id[0], 
             &length);
    /* The host application can save this data to memory now.
}
/* If status is NX_SUCCESS the Server successfully started. */
```

## <a name="nx_dhcpv6_server_interface_set"></a><span data-ttu-id="73073-374">nx_dhcpv6_server_interface_set</span><span class="sxs-lookup"><span data-stu-id="73073-374">nx_dhcpv6_server_interface_set</span></span>

### <a name="setthe-interface-index-for-server-dhcpv6-interface"></a><span data-ttu-id="73073-375">Установка индекса интерфейса для DHCPv6-сервера</span><span class="sxs-lookup"><span data-stu-id="73073-375">Setthe interface index for Server DHCPv6 interface</span></span>

<span data-ttu-id="73073-376">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="73073-376">**Prototype**</span></span>

```
UINT _nx_dhcpv6_server_interface_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     UINT iface_index, UINT ga_address_index)
```

<span data-ttu-id="73073-377">**Описание**</span><span class="sxs-lookup"><span data-stu-id="73073-377">**Description**</span></span>

<span data-ttu-id="73073-378">Эта служба задает сетевой интерфейс, на котором DHCPv6-сервер обрабатывает запросы клиента DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="73073-378">This service sets the network interface on which the DHCPv6 Server handles DHCPv6 Client requests.</span></span> <span data-ttu-id="73073-379">Это не распространяется на версии NetX Duo, которые не поддерживают множественную адресацию, значение интерфейса будет сброшено на нуль.</span><span class="sxs-lookup"><span data-stu-id="73073-379">Not that for versions of NetX Duo that do not support multihome, the interface value is defaulted to zero.</span></span> <span data-ttu-id="73073-380">Индекс глобального адреса необходим для получения глобального адреса сервера в интерфейсе DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="73073-380">The global address index is necessary to obtain the Server global address on its DHCPv6 interface.</span></span> <span data-ttu-id="73073-381">В логике DHCPv6 он подтверждает наличие связи между адресами аренды и другими данными DHCPv6 и сервером DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="73073-381">This is used by the DHCPv6 logic to ensure that lease addresses and other DHCPv6 data is on link with the DHCPv6 Server.</span></span>

<span data-ttu-id="73073-382">Этот вызов должен быть выполнен перед запуском DHCPv6-сервера, даже для приложений на отдельных сетевых устройствах или без поддержки множественной адресации.</span><span class="sxs-lookup"><span data-stu-id="73073-382">This must be called before the DHCPv6 server is started, even for applications on single homed devices or without multihome support.</span></span>

<span data-ttu-id="73073-383">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="73073-383">**Input Parameters**</span></span>

- <span data-ttu-id="73073-384">**dhcpv6_server_ptr** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-384">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="73073-385">**iface_index** Интерфейс DHCPv6-сервера</span><span class="sxs-lookup"><span data-stu-id="73073-385">**iface_index** Server DHCPv6 Server interface</span></span>
- <span data-ttu-id="73073-386">**ga_address_index** Индекс глобального адреса сервера в таблице IP-адресов экземпляров сервера</span><span class="sxs-lookup"><span data-stu-id="73073-386">**ga_address_index** Index of Server global address in the Server IP instance address table</span></span>

<span data-ttu-id="73073-387">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="73073-387">**Return Values**</span></span>

- <span data-ttu-id="73073-388">**NX_SUCCESS** (0x00) – сервер успешно запущен</span><span class="sxs-lookup"><span data-stu-id="73073-388">**NX_SUCCESS** (0x00) Server successfully started</span></span>
- <span data-ttu-id="73073-389">**NX_INVALID_INTERFACE** (0x4C) – интерфейс не существует</span><span class="sxs-lookup"><span data-stu-id="73073-389">**NX_INVALID_INTERFACE** (0x4C) Interface does not exist</span></span>
- <span data-ttu-id="73073-390">NX_NO_INTERFACE_ADDRESS (0x50) – глобальный индекс превышает максимальное число IPv6-адресов для IP-адреса экземпляра (NX_MAX_IPV6_ADDRESSES)</span><span class="sxs-lookup"><span data-stu-id="73073-390">NX_NO_INTERFACE_ADDRESS (0x50) Global index exceeds the IP instance maximum IPv6 addresses (NX_MAX_IPV6_ADDRESSES)</span></span>
- <span data-ttu-id="73073-391">NX_PTR_ERROR (0x16) – недопустимые входные данные указателя</span><span class="sxs-lookup"><span data-stu-id="73073-391">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="73073-392">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="73073-392">**Allowed From**</span></span>

<span data-ttu-id="73073-393">Код приложения</span><span class="sxs-lookup"><span data-stu-id="73073-393">Application code</span></span>

<span data-ttu-id="73073-394">**Пример**</span><span class="sxs-lookup"><span data-stu-id="73073-394">**Example**</span></span>

```
/* Set the Server DHCPv6 interface to the primary interface. The global IP 
address is at the index 1 in the IP address table. */
status = nx_dhcpv6_server_interface_set(&dhcp_server_0, 0, 1);

/* If status is NX_SUCCESS the Server interface is successfully set. */
```
## <a name="nx_dhcpv6_set_server_duid"></a><span data-ttu-id="73073-395">nx_dhcpv6_set_server_duid</span><span class="sxs-lookup"><span data-stu-id="73073-395">nx_dhcpv6_set_server_duid</span></span>

### <a name="set-the-server-duid-for-dhcpv6-packets"></a><span data-ttu-id="73073-396">Установка DUID сервера для пакетов DHCPv6</span><span class="sxs-lookup"><span data-stu-id="73073-396">Set the Server DUID for DHCPv6 packets</span></span>

<span data-ttu-id="73073-397">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="73073-397">**Prototype**</span></span>

```
UINT _nx_dhcpv6_set_server_duid(NX_DHCPV6_SERVER *dhcpv6_server_ptr,
     UINT duid_type, UINT hardware_type, 
     ULONG mac_address_msw, ULONG mac_address_lsw, 
     ULONG time)
```

<span data-ttu-id="73073-398">**Описание**</span><span class="sxs-lookup"><span data-stu-id="73073-398">**Description**</span></span>

<span data-ttu-id="73073-399">Эта служба задает DUID сервера, и ее необходимо вызвать до того, как ведущее приложение запустит сервер.</span><span class="sxs-lookup"><span data-stu-id="73073-399">This service sets the Server DUID and must be called before the host application starts the Server.</span></span> <span data-ttu-id="73073-400">Для типов DUID канального уровня и времени канального уровня ведущее приложение должно предоставить данные о типе оборудования и MAC-адрес.</span><span class="sxs-lookup"><span data-stu-id="73073-400">For link layer and link layer time DUID types, the host application must supply the hardware type and MAC address data.</span></span> <span data-ttu-id="73073-401">Для DUID времени на канальном уровне указатель времени должен указывать на допустимое время.</span><span class="sxs-lookup"><span data-stu-id="73073-401">For link layer time DUIDs, the time pointer must point to a valid time.</span></span> <span data-ttu-id="73073-402">Обычно в качестве исходного значения используется количество секунд с 1 января 2000 года.</span><span class="sxs-lookup"><span data-stu-id="73073-402">The number of seconds since Jan 1, 2000 is a typical seed value.</span></span> <span data-ttu-id="73073-403">Если тип DUID для сервера — предприятие и назначен поставщиком, то DUID будет создан на основе настраиваемых параметров пользователя, NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID и NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, а значения времени и MAC-адреса могут быть нулевыми.</span><span class="sxs-lookup"><span data-stu-id="73073-403">If the Server DUID type is the enterprise, vendor assigned type, the DUID will be created from the user configurable options NX_DHCPV6_SERVER_DUID_VENDOR_PRIVATE_ID and NX_DHCPV6_SERVER_DUID_VENDOR_ASSIGNED_ID, and the time and MAC address values can be set to NULL.</span></span>

>[!NOTE] 
> <span data-ttu-id="73073-404">Ведущее приложение должно сохранить параметры DUID сервера в энергонезависимой памяти, чтобы между перезагрузками использовать одинаковые DUID в сообщениях для клиентов.</span><span class="sxs-lookup"><span data-stu-id="73073-404">It is the host application’s responsibility to save the Server DUID parameters to nonvolatile memory such that it uses the same DUID in messages to Clients between reboots.</span></span> <span data-ttu-id="73073-405">Это необходимое условие работы по протоколу DHCPv6 (RFC 3315).</span><span class="sxs-lookup"><span data-stu-id="73073-405">This is a requirement of the DHCPv6 protocol (RFC 3315).</span></span>

<span data-ttu-id="73073-406">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="73073-406">**Input Parameters**</span></span>

- <span data-ttu-id="73073-407">**dhcpv6_server_ptr** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-407">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="73073-408">**duid_type** Тип DUID DHCPv6-сервера</span><span class="sxs-lookup"><span data-stu-id="73073-408">**duid_type** DHCPv6 Server DUID type</span></span>
- <span data-ttu-id="73073-409">**hardware_type** Тип оборудования (например, Ethernet)</span><span class="sxs-lookup"><span data-stu-id="73073-409">**hardware_type** Hardware type (e.g. Ethernet)</span></span>
- <span data-ttu-id="73073-410">**mac_address_msw** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-410">**mac_address_msw** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="73073-411">**mac_address_lsw** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-411">**mac_address_lsw** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="73073-412">**time** Значение времени для DUID</span><span class="sxs-lookup"><span data-stu-id="73073-412">**time** Time value for DUID</span></span>

<span data-ttu-id="73073-413">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="73073-413">**Return Values**</span></span>

- <span data-ttu-id="73073-414">**NX_SUCCESS** (0x00) – сервер успешно приостановлен</span><span class="sxs-lookup"><span data-stu-id="73073-414">**NX_SUCCESS** (0x00) Server successfully suspended</span></span>
- <span data-ttu-id="73073-415">**NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) – неизвестный или неподдерживаемый тип DUID</span><span class="sxs-lookup"><span data-stu-id="73073-415">**NX_DHCPV6_INVALID_SERVER_DUID** (0XE98) Unknown or unsupported DUID type</span></span>
- <span data-ttu-id="73073-416">**NX_INVALID_PARAMETERS** (0x4D) – недопустимые входные данные без указателя</span><span class="sxs-lookup"><span data-stu-id="73073-416">**NX_INVALID_PARAMETERS** (0x4D) Invalid non pointer input</span></span>
- <span data-ttu-id="73073-417">NX_PTR_ERROR (0x16) – недопустимые входные данные указателя</span><span class="sxs-lookup"><span data-stu-id="73073-417">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="73073-418">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="73073-418">**Allowed From**</span></span>

<span data-ttu-id="73073-419">Код приложения</span><span class="sxs-lookup"><span data-stu-id="73073-419">Application code</span></span>

<span data-ttu-id="73073-420">**Пример**</span><span class="sxs-lookup"><span data-stu-id="73073-420">**Example**</span></span>

```
/* Set the DHCPv6 ServerDUID as Link layer plus time, over Ethernet hardware. */
duid_time = SECONDS_SINCE_JAN_1_2000_MOD_32 + rand();

status = nx_dhcpv6_set_server_duid(&dhcp_server_0,1, 0x6,
         physical_address_msw,physical_address_lsw,duid_time);

/* If status is NX_SUCCESS the ServerDUID is successfully set. */
```

## <a name="nx_dhcpv6_server_option_request_handler_set"></a><span data-ttu-id="73073-421">nx_dhcpv6_server_option_request_handler_set</span><span class="sxs-lookup"><span data-stu-id="73073-421">nx_dhcpv6_server_option_request_handler_set</span></span>

### <a name="set-the-option-request-handler-for-dhcpv6-server-instance"></a><span data-ttu-id="73073-422">Установка обработчика запросов параметров для экземпляра DHCPv6-сервера</span><span class="sxs-lookup"><span data-stu-id="73073-422">Set the option request handler for DHCPv6 Server instance</span></span> 

<span data-ttu-id="73073-423">**Прототип**</span><span class="sxs-lookup"><span data-stu-id="73073-423">**Prototype**</span></span>

```
UINT nx_dhcpv6_server_option_request_handler_set(
     NX_DHCPV6_SERVER *dhcpv6_server_ptr, 
     VOID (*dhcpv6_option_request_handler_extended)(
          struct NX_DHCPV6_SERVER_STRUCT *dhcpv6_server_ptr, 
          UINT option_request, UCHAR *buffer_ptr, 
          UINT *index, UINT available_payload));
```

<span data-ttu-id="73073-424">**Описание**</span><span class="sxs-lookup"><span data-stu-id="73073-424">**Description**</span></span>

<span data-ttu-id="73073-425">Эта служба задает расширенный обработчик запросов параметров DHCPv6-сервера.</span><span class="sxs-lookup"><span data-stu-id="73073-425">This service sets the DHCPv6 Server extended option request handler.</span></span>

<span data-ttu-id="73073-426">**Входные параметры**</span><span class="sxs-lookup"><span data-stu-id="73073-426">**Input Parameters**</span></span>

- <span data-ttu-id="73073-427">**dhcpv6_server_ptr** Указатель на DHCPv6-сервер</span><span class="sxs-lookup"><span data-stu-id="73073-427">**dhcpv6_server_ptr** Pointer to DHCPv6 Server</span></span>
- <span data-ttu-id="73073-428">**dhcpv6_option_request_handler_extended** Указатель на расширенный обработчик запросов параметров</span><span class="sxs-lookup"><span data-stu-id="73073-428">**dhcpv6_option_request_handler_extended** Pointer to extended options request handler</span></span>

<span data-ttu-id="73073-429">**Возвращаемые значения**</span><span class="sxs-lookup"><span data-stu-id="73073-429">**Return Values**</span></span>

- <span data-ttu-id="73073-430">**NX_SUCCESS** (0x00) – работа сервера успешно возобновлена</span><span class="sxs-lookup"><span data-stu-id="73073-430">**NX_SUCCESS** (0x00) Server successfully resumed</span></span>
- <span data-ttu-id="73073-431">NX_PTR_ERROR (0x16) – недопустимые входные данные указателя</span><span class="sxs-lookup"><span data-stu-id="73073-431">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

<span data-ttu-id="73073-432">**Допустимые источники**</span><span class="sxs-lookup"><span data-stu-id="73073-432">**Allowed From**</span></span>

<span data-ttu-id="73073-433">Код приложения</span><span class="sxs-lookup"><span data-stu-id="73073-433">Application Code</span></span>

<span data-ttu-id="73073-434">**Пример**</span><span class="sxs-lookup"><span data-stu-id="73073-434">**Example**</span></span>

```
/* Set the option request handler for DHCPv6 Server. */
status = nx_dhcpv6_server_option_request_handler_set(&dhcp_server_0,
         dhcpv6_option_request_handler_extended);

/* If status is NX_SUCCESS the extended handler successfully set. */
```