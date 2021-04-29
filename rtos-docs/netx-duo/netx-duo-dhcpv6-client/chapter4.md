---
title: Глава 4. Службы клиента DHCPv6 в NetX Duo для ОСРВ Azure
description: Эта глава содержит описание всех служб клиента DHCPv6 для NetX Duo в ОСРВ Azure, перечисленных ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 40fbfa7319ca95af65c92b12582d4bbb05005dc0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814768"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-client-services"></a><span data-ttu-id="ea09d-103">Глава 4. Службы клиента DHCPv6 в NetX Duo для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="ea09d-103">Chapter 4 - Azure RTOS NetX Duo DHCPv6 Client services</span></span>

<span data-ttu-id="ea09d-104">Эта глава содержит описание всех служб клиента DHCPv6 для NetX Duo в ОСРВ Azure, перечисленных ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="ea09d-104">This chapter contains a description of all Azure RTOS NetX Duo DHCPv6 Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="ea09d-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="ea09d-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="ea09d-106">**nx_dhcpv6_client_create:** *создание экземпляра клиента DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ea09d-106">**nx_dhcpv6_client_create:** *Create a DHCPv6 Client instance*</span></span> 

- <span data-ttu-id="ea09d-107">**nx_dhcpv6_client_delete:** *удаление экземпляра клиента DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ea09d-107">**nx_dhcpv6_client_delete:** *Delete a DHCPv6 Client instance*</span></span> 

- <span data-ttu-id="ea09d-108">**nx_dhcpv6_create_client_duid:** *создание идентификатора DUID клиента DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ea09d-108">**nx_dhcpv6_create_ client_duid:** *Create a DHCPv6 Client DUID*</span></span> 

- <span data-ttu-id="ea09d-109">**nx_dhcpv6_add_client_ia:** *добавление адреса удостоверения (IA) для клиента DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ea09d-109">**nx_dhcpv6 _add_client_ia:** *Add a DHCPv6 Client Identity Address (IA)*</span></span> 

- <span data-ttu-id="ea09d-110">**nx_dhcpv6 _create_client_ia:** *добавление адреса удостоверения (IA) для клиента DHCPv6 — устаревшая операция*</span><span class="sxs-lookup"><span data-stu-id="ea09d-110">**nx_dhcpv6 _create_client_ia:** (*Legacy Add a DHCPv6 Client Identity Address (IA))*</span></span> 

- <span data-ttu-id="ea09d-111">**nx_dhcpv6_create_client_iana:** *создание ассоциации удостоверений для невременных адресов (IANA) для клиента DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ea09d-111">**nx_dhcpv6_create_client_iana:** *Create a DHCPv6 Client Identity Association for Non Temporary Addresses (IANA)*</span></span> 

- <span data-ttu-id="ea09d-112">**nx_dhcpv6_get_client_duid_time_id:** *получение идентификатора времени из идентификатора DUID клиента DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ea09d-112">**nx_dhcpv6_get_client_duid_time_id:** *Get the time ID from DHCPv6 Client DUID*</span></span> 

- <span data-ttu-id="ea09d-113">**nx_dhcpv6_client_set_interface:** *задание сетевого интерфейса клиента для связи с DHCPv6-сервером*</span><span class="sxs-lookup"><span data-stu-id="ea09d-113">**nx_dhcpv6_client_set_interface:** *Set the Client network interface for communications with the DHCPv6 Server*</span></span> 

- <span data-ttu-id="ea09d-114">**nx_dhcpv6_get_IP_address:** *получение глобального IPv6-адреса, назначенного клиенту DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ea09d-114">**nx_dhcpv6_get_IP_address:** *Get the global IPv6 address assigned to the DHCPv6 client*</span></span> 

- <span data-ttu-id="ea09d-115">**nx_dhcpv6_get_lease_time_data:** *получение времени существования T1, T2, а также допустимого и предпочтительного времени существования для глобального IPv6-адреса клиента*</span><span class="sxs-lookup"><span data-stu-id="ea09d-115">**nx_dhcpv6_get_lease_time_data:** *Get T1, T2, valid and preferred lifetimes for the Client global IPv6 address*</span></span>

- <span data-ttu-id="ea09d-116">**nx_dhcpv6_get_valid_ip_address_lease_time:** *получение времени существования T1, T2, а также допустимого и предпочтительного времени существования для IPv6-адреса клиента DHCPv6 по индексу адреса*</span><span class="sxs-lookup"><span data-stu-id="ea09d-116">**nx_dhcpv6_get_valid_ip_address_lease_time:** *Get T1, T2, valid and preferred lifetimes for the DHCPv6 Client IPv6 address by address index*</span></span> 

- <span data-ttu-id="ea09d-117">**nx_dhcpv6_get_iana_lease_time:** *получение значений T1 и T2 из ассоциации удостоверений (IANA), выданной в аренду клиенту DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ea09d-117">**nx_dhcpv6_get_iana_lease_time:** *Get T1 and T2 in the Identity Association (IANA) leased to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="ea09d-118">**nx_dhcpv6_get_other_option_data:** *получение данных указанного параметра, например доменного имени или сервера часовых поясов*</span><span class="sxs-lookup"><span data-stu-id="ea09d-118">**nx_dhcpv6_get_other_option_data:** *Get the specified option data e.g. domain name or time zone server*</span></span> 

- <span data-ttu-id="ea09d-119">**nx_dhcpv6_get_DNS_server_address:** *получение адреса DNS-сервера по указанному индексу в списке DNS-серверов клиента DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ea09d-119">**nx_dhcpv6_get_DNS_server_address:** *Get DNS Server address at the specified index into the DHCPv6 Client DNS server list*</span></span> 

- <span data-ttu-id="ea09d-120">**nx_dhcpv6_get_time_accrued:** *получение совокупного времени, в течение которого аренда глобального IPv6-адреса была привязана к клиенту DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ea09d-120">**nx_dhcpv6_get_time_accrued:** *Get the time accrued the global IPv6 address lease has been bound to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="ea09d-121">**nx_dhcpv6_get_time_server_address:** *получение адреса сервера времени по указанному индексу в списке серверов времени клиента DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ea09d-121">**nx_dhcpv6_get_time_server_address:** *Get Time Server address at the specified index into the DHCPv6 Client Time server list*</span></span>

- <span data-ttu-id="ea09d-122">**nx_dhcpv6_get_valid_ip_address_count:** *получение числа IPv6-адресов, назначенных клиенту DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ea09d-122">**nx_dhcpv6_get_valid_ip_address_count:** *Get the number of IPv6 addresses assigned to the DHCPv6 Client*</span></span> 

- <span data-ttu-id="ea09d-123">**nx_dhcpv6_reinitialize:** *повторная инициализация DHCPv6 для перезапуска конечного автомата клиента DHCPv6 и протокола DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ea09d-123">**nx_dhcpv6_reinitialize:** *Reinitialize the DHCPv6 for restarting the DHCPv6 Client state machine and rerunning the DHCPv6 protocol*</span></span> 

- <span data-ttu-id="ea09d-124">**nx_dhcpv6_request_confirm:** *отправка запроса CONFIRM на сервер*</span><span class="sxs-lookup"><span data-stu-id="ea09d-124">**nx_dhcpv6_request_confirm:** *Send a CONFIRM request to the Server*</span></span> 

- <span data-ttu-id="ea09d-125">**nx_dhcpv6_request_inform_request:** *отправка сообщения INFORM REQUEST на сервер*</span><span class="sxs-lookup"><span data-stu-id="ea09d-125">**nx_dhcpv6_request_inform_request:** S *end an INFORM REQUEST message to the Server*</span></span> 

- <span data-ttu-id="ea09d-126">**nx_dhcpv6_request_release:** *отправка запроса RELEASE на сервер*</span><span class="sxs-lookup"><span data-stu-id="ea09d-126">**nx_dhcpv6_request_release:** *Send a RELEASE request to the Server*</span></span> 

- <span data-ttu-id="ea09d-127">**nx_dhcpv6_request_option_DNS_server:** *добавление параметра DNS-сервера в данные клиентского запроса параметра в сообщениях запроса на сервер*</span><span class="sxs-lookup"><span data-stu-id="ea09d-127">**nx_dhcpv6_request_option_DNS_server:** *Add the DNS server option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="ea09d-128">**nx_dhcpv6_request_option_FQDN:** *добавление параметра FQDN в данные клиентского запроса параметра в сообщениях запроса на сервер*</span><span class="sxs-lookup"><span data-stu-id="ea09d-128">**nx_dhcpv6_request_option_FQDN:** *Add the FQDN option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="ea09d-129">**nx_dhcpv6_request_option_domain_name:** *добавление параметра доменного имени в данные клиентского запроса параметра в сообщениях запроса на сервер*</span><span class="sxs-lookup"><span data-stu-id="ea09d-129">**nx_dhcpv6_request_option_domain_name:** *Add the domain name option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="ea09d-130">**nx_dhcpv6_request_option_time_server:** *добавление параметра сервера времени в данные клиентского запроса параметра в сообщениях запроса на сервер*</span><span class="sxs-lookup"><span data-stu-id="ea09d-130">**nx_dhcpv6_request_option_time_server:** *Add the time server option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="ea09d-131">**nx_dhcpv6_request_option_timezone:** *добавление параметра часового пояса в данные клиентского запроса параметра в сообщениях запроса на сервер*</span><span class="sxs-lookup"><span data-stu-id="ea09d-131">**nx_dhcpv6_request_option_timezone:** *Add the time zone option to the Client option request data in request messages to the Server*</span></span> 

- <span data-ttu-id="ea09d-132">**nx_dhcpv6_request_solicit:** *отправка запроса DHCPv6 SOLICIT на любой сервер в сети клиента (широковещательный режим)*</span><span class="sxs-lookup"><span data-stu-id="ea09d-132">**nx_dhcpv6_request_solicit:** *Send a DHCPv6 SOLICIT request to any Server on the Client network (broadcast)*</span></span> 

- <span data-ttu-id="ea09d-133">**nx_dhcpv6_request_solicit_rapid:** *отправка запроса DHCPv6 SOLICIT на любой сервер в сети клиента (широковещательный режим) с заданным параметром "Быстрая фиксация"*</span><span class="sxs-lookup"><span data-stu-id="ea09d-133">**nx_dhcpv6_request_solicit_rapid:** *Send a DHCPv6 SOLICIT request to any Server on the Client network (broadcast) with the Rapid Commit option set*</span></span> 

- <span data-ttu-id="ea09d-134">**nx_dhcpv6_resume:** *возобновление обработки DHCPv6 в клиенте*</span><span class="sxs-lookup"><span data-stu-id="ea09d-134">**nx_dhcpv6_resume:** *Resume DHCPv6 Client processing*</span></span> 

- <span data-ttu-id="ea09d-135">**nx_dhcpv6_start:** *запуск задачи клиентского потока DHCPv6. Обратите внимание, что это не эквивалентно запуску конечного автомата DHCPv6 и запрос SOLICIT при этом не отправляется.*</span><span class="sxs-lookup"><span data-stu-id="ea09d-135">**nx_dhcpv6_start:** *Start the DHCPv6 Client thread task. Note this is not equivalent to starting the DHCPv6 state machine and does not send a SOLICIT request*</span></span> 

- <span data-ttu-id="ea09d-136">**nx_dhcpv6_stop:** *остановка задачи клиентского потока DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ea09d-136">**nx_dhcpv6_stop:** *Stop the DHCPv6 Client thread task*</span></span> 

- <span data-ttu-id="ea09d-137">**nx_dhcpv6_suspend:** *приостановка задачи клиентского потока DHCPv6*</span><span class="sxs-lookup"><span data-stu-id="ea09d-137">**nx_dhcpv6_suspend:** *Suspend the DHCPv6 Client thread task*</span></span> 

- <span data-ttu-id="ea09d-138">**nx_dhcpv6_set_time_accrued:** *задание совокупного времени аренды глобального IPv6-адреса клиента в записи клиента*</span><span class="sxs-lookup"><span data-stu-id="ea09d-138">**nx_dhcpv6_set_time_accrued:** *Set the time accrued on the global Client IPv6 address lease in the Client record.*</span></span>

## <a name="nx_dhcpv6_client_create"></a><span data-ttu-id="ea09d-139">nx_dhcpv6_client_create</span><span class="sxs-lookup"><span data-stu-id="ea09d-139">nx_dhcpv6_client_create</span></span>

<span data-ttu-id="ea09d-140">Создание экземпляра клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-140">Create a DHCPv6 client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-141">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-141">Prototype</span></span>

```C
UINT  nx_dhcpv6_client_create(NX_DHCPV6 *dhcpv6_ptr, 
                        NX_IP *ip_ptr, CHAR *name_ptr, 
                        NX_PACKET_POOL *packet_pool_ptr, 
                        VOID *stack_ptr, ULONG stack_size,
                        VOID (*dhcpv6_state_change_notify)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                  UINT old_state, UINT new_state), 
                        VOID (*dhcpv6_server_error_handler)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                 UINT op_code, UINT status_code, 
                                 UINT message_type));
```

### <a name="description"></a><span data-ttu-id="ea09d-142">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-142">Description</span></span>

<span data-ttu-id="ea09d-143">Эта служба создает экземпляр клиента DHCPv6, включая функции обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="ea09d-143">This service creates a DHCPv6 client instance including callback functions.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-144">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-144">Input Parameters</span></span>

- <span data-ttu-id="ea09d-145">**dhcpv6_ptr**: указатель на блок управления DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-145">**dhcpv6_ptr** Pointer to DHCPv6 control block</span></span>  

- <span data-ttu-id="ea09d-146">**ip_ptr**: указатель на экземпляр IP для клиента</span><span class="sxs-lookup"><span data-stu-id="ea09d-146">**ip_ptr** Pointer to Client IP instance</span></span>  

- <span data-ttu-id="ea09d-147">**name_ptr**: указатель на имя экземпляра DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-147">**name_ptr** Pointer to name for DHCPv6 instance</span></span>

- <span data-ttu-id="ea09d-148">**packet_pool_ptr**: указатель на пул пакетов клиента</span><span class="sxs-lookup"><span data-stu-id="ea09d-148">**packet_pool_ptr** Pointer to Client packet pool</span></span>

- <span data-ttu-id="ea09d-149">**stack_ptr**: указатель на память стека клиента</span><span class="sxs-lookup"><span data-stu-id="ea09d-149">**stack_ptr** Pointer to Client stack memory</span></span>

- <span data-ttu-id="ea09d-150">**stack_size**: размер памяти стека клиента</span><span class="sxs-lookup"><span data-stu-id="ea09d-150">**stack_size** Size of Client stack memory</span></span>

- <span data-ttu-id="ea09d-151">**dhcpv6_state_change_notify**: указатель на функцию обратного вызова, вызываемую при инициации клиентом нового DHCPv6-запроса к серверу</span><span class="sxs-lookup"><span data-stu-id="ea09d-151">**dhcpv6_state_change_notify** Pointer to callback function invoked when the Client initiates a new DHCPv6 request to the server</span></span>

- <span data-ttu-id="ea09d-152">**dhcpv6_server_error_handler**: указатель на функцию обратного вызова, вызываемую при получении клиентом состояния ошибки с сервера</span><span class="sxs-lookup"><span data-stu-id="ea09d-152">**dhcpv6_server_error_handler** Pointer to callback function invoked when the Client receives an error status from the server</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-153">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-153">Return Values</span></span>

- <span data-ttu-id="ea09d-154">**NX_SUCCESS** (0x00) — успешное создание клиента.</span><span class="sxs-lookup"><span data-stu-id="ea09d-154">**NX_SUCCESS** (0x00) Successful Client create</span></span>

- <span data-ttu-id="ea09d-155">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-155">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-156">NX_DHCPV6_PARAM_ERROR (0xE93) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-156">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-157">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-157">Allowed From</span></span>

<span data-ttu-id="ea09d-158">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-158">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-159">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-159">Example</span></span>

```C
/* Create a DHCPv6 client instance without specifying link local or preferred
   global IP address.  */
status =  nx_dhcpv6_client_create(&dhcp_0, &ip_0, "DHCPv6 Client", &pool_0,
                                  NULL, NULL, pointer, 2048,        
                                  dhcpv6_state_change_notify, 
                                  dhcpv6_server_error_handler);

/* If status is NX_SUCCESS a DHCPv6 client instance was successfully
   created.  */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-160">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-160">See Also</span></span>

- <span data-ttu-id="ea09d-161">nx_dhcpv6_client_delete</span><span class="sxs-lookup"><span data-stu-id="ea09d-161">nx_dhcpv6_client_delete</span></span>

## <a name="nx_dhcpv6_client_delete"></a><span data-ttu-id="ea09d-162">nx_dhcpv6_client_delete</span><span class="sxs-lookup"><span data-stu-id="ea09d-162">nx_dhcpv6_client_delete</span></span>

<span data-ttu-id="ea09d-163">Удаление экземпляра клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-163">Delete a DHCPv6 Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-164">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-164">Prototype</span></span>

```C
UINT nx_dhcpv6_client_delete(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="ea09d-165">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-165">Description</span></span>

<span data-ttu-id="ea09d-166">Эта служба удаляет ранее созданный экземпляр клиента DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ea09d-166">This service deletes a previously created DHCPv6 client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-167">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-167">Input Parameters</span></span>

- <span data-ttu-id="ea09d-168">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-168">**dhcpv6_ptr** Pointer to DHCPv6 client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-169">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-169">Return Values</span></span>

- <span data-ttu-id="ea09d-170">**NX_SUCCESS** (0x00) — успешное удаление DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ea09d-170">**NX_SUCCESS** (0x00) Successful DHCPv6 deletion</span></span>

- <span data-ttu-id="ea09d-171">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-171">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-172">NX_DHCPV6_PARAM_ERROR (0xE93) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-172">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-173">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-173">Allowed From</span></span>

<span data-ttu-id="ea09d-174">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-174">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-175">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-175">Example</span></span>

```C
/* Delete a DHCPv6 client instance.  */
status =  nx_dhcpv6_client_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCPv6 client instance was successfully
   deleted.  */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-176">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-176">See Also</span></span>

- <span data-ttu-id="ea09d-177">nx_dhcpv6_client_create</span><span class="sxs-lookup"><span data-stu-id="ea09d-177">nx_dhcpv6_client_create</span></span>

## <a name="nx_dhcpv6_client_set_interface"></a><span data-ttu-id="ea09d-178">nx_dhcpv6_client_set_interface</span><span class="sxs-lookup"><span data-stu-id="ea09d-178">nx_dhcpv6_client_set_interface</span></span>

<span data-ttu-id="ea09d-179">Задание сетевого интерфейса клиента для DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-179">Sets Client’s Network Interface for DHCPv6</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-180">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-180">Prototype</span></span>

```C
UINT    nx_dhcpv6_client_set_interface(NX_DHCPV6 *dhcpv6_ptr, 
                                       UINT *interface_index);
```

### <a name="description"></a><span data-ttu-id="ea09d-181">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-181">Description</span></span>

<span data-ttu-id="ea09d-182">Эта служба задает сетевой интерфейс клиента для взаимодействия с DHCPv6-серверами по указанному входному индексу интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ea09d-182">This service sets the Client’s network interface for communicating with the DHCPv6 Server(s) to the specified input interface index.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-183">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-183">Input Parameters</span></span>

- <span data-ttu-id="ea09d-184">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-184">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="ea09d-185">**interface_index**: индекс, указывающий сетевой интерфейс</span><span class="sxs-lookup"><span data-stu-id="ea09d-185">**interface_index** Index indicating network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-186">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-186">Return Values</span></span>

- <span data-ttu-id="ea09d-187">**NX_SUCCESS** (0x00) — интерфейс успешно задан.</span><span class="sxs-lookup"><span data-stu-id="ea09d-187">**NX_SUCCESS** (0x00) Interface successfully set</span></span>

- <span data-ttu-id="ea09d-188">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-188">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-189">NX_INVALID_INTERFACE (0x4C) — недопустимый входной индекс интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ea09d-189">NX_INVALID_INTERFACE (0x4C) Invalid interface index input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-190">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-190">Allowed From</span></span>

<span data-ttu-id="ea09d-191">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-192">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-192">Example</span></span>

```C
/* Set the client interface for DHCPv6 communication with the Server to 
   the secondary interface (1). */

UINT index = 1;
status = nx_dhcpv6_client_set_interface(&dhcp_0, index);

/* If status is NX_SUCCESS, the Client successfully set 
   the DHCPv6 network interface.  */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-193">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-193">See Also</span></span>

- <span data-ttu-id="ea09d-194">nx_dhcpv6_client_create</span><span class="sxs-lookup"><span data-stu-id="ea09d-194">nx_dhcpv6_client _create</span></span>
- <span data-ttu-id="ea09d-195">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="ea09d-195">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_client_set_destination_address"></a><span data-ttu-id="ea09d-196">nx_dhcpv6_client_set_destination_address</span><span class="sxs-lookup"><span data-stu-id="ea09d-196">nx_dhcpv6_client_set_destination_address</span></span>

<span data-ttu-id="ea09d-197">Задание адреса назначения, по которому необходимо отправить сообщение DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-197">Sets the destination address where DHCPv6 message should be sent to</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-198">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-198">Prototype</span></span>

```C
UINT nx_dhcpv6_client_set_destination_address(NX_DHCPV6 *dhcpv6_ptr,
                                              NXD_ADDRESS *destination_address);
```

### <a name="description"></a><span data-ttu-id="ea09d-199">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-199">Description</span></span>

<span data-ttu-id="ea09d-200">Эта служба задает адрес назначения, по которому необходимо отправить сообщение DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ea09d-200">This service sets the destination address where DHCPv6 message should be sent to.</span></span> <span data-ttu-id="ea09d-201">Значение по умолчанию — ALL_DHCP_Relay_Agents_and_Servers (FF02::1:2).</span><span class="sxs-lookup"><span data-stu-id="ea09d-201">By default is ALL_DHCP_Relay_Agents_and_Servers(FF02::1:2).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-202">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-202">Input Parameters</span></span>

- <span data-ttu-id="ea09d-203">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-203">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="ea09d-204">**destination_address**: адрес назначения</span><span class="sxs-lookup"><span data-stu-id="ea09d-204">**destination_address** Destination address</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-205">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-205">Return Values</span></span>

- <span data-ttu-id="ea09d-206">**NX_SUCCESS** (0x00) — интерфейс успешно задан.</span><span class="sxs-lookup"><span data-stu-id="ea09d-206">**NX_SUCCESS** (0x00) Interface successfully set</span></span>

- <span data-ttu-id="ea09d-207">NX_PTR_ERROR (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-207">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-208">NX_DHCPV6_PARAM_ERROR (0xE93) — ошибка в параметре.</span><span class="sxs-lookup"><span data-stu-id="ea09d-208">NX_DHCPV6_PARAM_ERROR (0xE93) Parament error</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-209">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-209">Allowed From</span></span>

<span data-ttu-id="ea09d-210">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-210">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-211">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-211">Example</span></span>

```C
/* Set the destination address where DHCPv6 message should be sent to. */

NXD_ADDRESS dest_address; /* Set the destination address.  */

status = nx_dhcpv6_client_set_destination_address(&dhcp_0, &dest_address);

/* If status is NX_SUCCESS, the Client successfully set the destination address. */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-212">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-212">See Also</span></span>

- <span data-ttu-id="ea09d-213">nx_dhcpv6_client_create</span><span class="sxs-lookup"><span data-stu-id="ea09d-213">nx_dhcpv6_client _create</span></span>
- <span data-ttu-id="ea09d-214">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="ea09d-214">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_create_client_duid"></a><span data-ttu-id="ea09d-215">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="ea09d-215">nx_dhcpv6_create_client_duid</span></span>

<span data-ttu-id="ea09d-216">Создание объекта DUID для клиента</span><span class="sxs-lookup"><span data-stu-id="ea09d-216">Create Client DUID object</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-217">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-217">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr,
                                  UINT duid_type, UINT hardware_type,
                                  ULONG time);
```

### <a name="description"></a><span data-ttu-id="ea09d-218">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-218">Description</span></span>

<span data-ttu-id="ea09d-219">Эта служба создает идентификатор DUID клиента на основе входных параметров.</span><span class="sxs-lookup"><span data-stu-id="ea09d-219">This service creates the Client DUID with the input parameters.</span></span> <span data-ttu-id="ea09d-220">Если входные данные времени не указаны и задан тип DUID канального уровня с временем, эта функция сама задаст уникальное время, используя случайный фактор.</span><span class="sxs-lookup"><span data-stu-id="ea09d-220">If the time input is not supplied and the duid type indicates link layer with time, this function will supply a time which includes a randomizing factor for uniqueness.</span></span> <span data-ttu-id="ea09d-221">Типы DUID, назначенные поставщиком (корпоративные), не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="ea09d-221">Vendor assigned (enterprise) duid types are not supported.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-222">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-222">Input Parameters</span></span>

- <span data-ttu-id="ea09d-223">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-223">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="ea09d-224">**duid_type**: тип идентификатора DUID (аппаратный, корпоративный и т. д.)</span><span class="sxs-lookup"><span data-stu-id="ea09d-224">**duid_type** Type of DUID (hardware, enterprise etc)</span></span>

- <span data-ttu-id="ea09d-225">**hardware_type**: сетевое оборудование, например IEEE 802</span><span class="sxs-lookup"><span data-stu-id="ea09d-225">**hardware_type** Network hardware e.g. IEEE 802</span></span>

- <span data-ttu-id="ea09d-226">**time**: значение, используемое при создании уникального идентификатора</span><span class="sxs-lookup"><span data-stu-id="ea09d-226">**time** Value used in creating unique identifier</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-227">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-227">Return Values</span></span>

- <span data-ttu-id="ea09d-228">**NX_SUCCESS** (0x00) — идентификатор DUID клиента успешно создан.</span><span class="sxs-lookup"><span data-stu-id="ea09d-228">**NX_SUCCESS** (0x00) Successful Client DUID created</span></span>

- <span data-ttu-id="ea09d-229">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-229">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-230">NX_DHCPV6_PARAM_ERROR (0xE93) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-230">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

- <span data-ttu-id="ea09d-231">NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) — неизвестный или неподдерживаемый тип DUID.</span><span class="sxs-lookup"><span data-stu-id="ea09d-231">NX_DHCPV6_UNSUPPORTED_DUID_TYPE (0xE98) DUID type unknown or not supported</span></span> 

- <span data-ttu-id="ea09d-232">NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) — неизвестный или неподдерживаемый аппаратный тип DUID.</span><span class="sxs-lookup"><span data-stu-id="ea09d-232">NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE (0xE99) DUID hardware type unknown or not supported</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-233">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-233">Allowed From</span></span>

<span data-ttu-id="ea09d-234">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-234">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-235">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-235">Example</span></span>

```C
/* Create the Client DUID from the supplied input.
   The time field is left NULL so the DHCPv6 client will provide one.  */
status = nx_dhcpv6_create_client_duid(&dhcp_0, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                      NX_DHCPV6_HW_TYPE_IEEE_802, 0)

/* If status is NX_SUCCESS the client DUID was successfully created.  */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-236">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-236">See Also</span></span>

- <span data-ttu-id="ea09d-237">nx_dhcpv6_create_client_ia</span><span class="sxs-lookup"><span data-stu-id="ea09d-237">nx_dhcpv6_create_client_ia</span></span>
- <span data-ttu-id="ea09d-238">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="ea09d-238">nx_dhcpv6_create_client_iana</span></span>
- <span data-ttu-id="ea09d-239">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="ea09d-239">nx_dhcpv6_create_server_duid</span></span>

## <a name="nx_dhcpv6_create_client_ia"></a><span data-ttu-id="ea09d-240">nx_dhcpv6_create_client_ia</span><span class="sxs-lookup"><span data-stu-id="ea09d-240">nx_dhcpv6_create_client_ia</span></span>

<span data-ttu-id="ea09d-241">Добавление ассоциации удостоверений в клиент</span><span class="sxs-lookup"><span data-stu-id="ea09d-241">Add an Identity Association to the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-242">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-242">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_ia(NX_DHCPV6 *dhcpv6_ptr,
                                NXD_ADDRESS *ipv6_address,
                                ULONG preferred_lifetime,
                                ULONG valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="ea09d-243">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-243">Description</span></span>

<span data-ttu-id="ea09d-244">Эта служба идентична службе *nx_dhcpv6_add_client_ia*.</span><span class="sxs-lookup"><span data-stu-id="ea09d-244">This service is identical to the *nx_dhcpv6_add_client_ia* service.</span></span> <span data-ttu-id="ea09d-245">Она добавляет ассоциацию удостоверений клиента, заполняя запись клиента указанными параметрами.</span><span class="sxs-lookup"><span data-stu-id="ea09d-245">It adds a Client Identity Association by filling in the Client record with the supplied parameters.</span></span> <span data-ttu-id="ea09d-246">Чтобы запросить максимальное предпочтительное и допустимое время существования, задайте для этих параметров бесконечное значение.</span><span class="sxs-lookup"><span data-stu-id="ea09d-246">To request the maximum preferred and valid lifetimes, set these parameters to infinity.</span></span> <span data-ttu-id="ea09d-247">Чтобы добавить несколько адресов IA для клиента DHCPv6, присвойте параметру NX_DHCPV6_MAX_IA_ADDRESS значение, превышающее значение по умолчанию, равное 1.</span><span class="sxs-lookup"><span data-stu-id="ea09d-247">To add more than one IA to a DHCPv6 Client, set the NX_DHCPV6_MAX_IA_ADDRESS to a value higher than the default value of 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-248">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-248">Input Parameters</span></span>

- <span data-ttu-id="ea09d-249">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-249">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="ea09d-250">**ipv6_address**: указатель на блок IP-адресов NetX Duo</span><span class="sxs-lookup"><span data-stu-id="ea09d-250">**ipv6_address** Pointer to NetX Duo IP address block</span></span>

- <span data-ttu-id="ea09d-251">**preferred_lifetime**: время до устаревания IP-адреса</span><span class="sxs-lookup"><span data-stu-id="ea09d-251">**preferred_lifetime** Length of time before IP address is deprecated</span></span>

- <span data-ttu-id="ea09d-252">**valid_lifetime**: время до истечения срока действия IP-адреса</span><span class="sxs-lookup"><span data-stu-id="ea09d-252">**valid_lifetime** Length of time before IP address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-253">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-253">Return Values</span></span>

- <span data-ttu-id="ea09d-254">**NX_SUCCESS** (0x00) — адрес IA клиента успешно добавлен.</span><span class="sxs-lookup"><span data-stu-id="ea09d-254">**NX_SUCCESS** (0x00) Successful Client IA added</span></span>

- <span data-ttu-id="ea09d-255">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) — повторяющийся адрес IA.</span><span class="sxs-lookup"><span data-stu-id="ea09d-255">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Duplicate IA address</span></span> 

- <span data-ttu-id="ea09d-256">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) — превышено максимальное количество адресов IA, которое может храниться в клиенте.</span><span class="sxs-lookup"><span data-stu-id="ea09d-256">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA exceeds the max IAs Client can store</span></span>

- <span data-ttu-id="ea09d-257">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-257">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-258">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) — недопустимый (например, равный NULL) адрес IA.</span><span class="sxs-lookup"><span data-stu-id="ea09d-258">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Invalid (e.g. null) IA address in IA</span></span>

- <span data-ttu-id="ea09d-259">NX_DHCPV6_PARAM_ERROR (0xE93) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-259">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>


### <a name="allowed-from"></a><span data-ttu-id="ea09d-260">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-260">Allowed From</span></span>

<span data-ttu-id="ea09d-261">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-261">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-262">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-262">Example</span></span>

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_create_client_ia(&dhcp_0, &ipv6_address, 
NX_DHCPV6_PREFERRED_LIFETIME, NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-263">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-263">See Also</span></span>

- <span data-ttu-id="ea09d-264">nx_dhcpv6_add_client_duid</span><span class="sxs-lookup"><span data-stu-id="ea09d-264">nx_dhcpv6_add_client_duid</span></span>
- <span data-ttu-id="ea09d-265">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="ea09d-265">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="ea09d-266">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="ea09d-266">nx_dhcpv6_create_client_iana</span></span>

## <a name="nx_dhcpv6_create_client_iana"></a><span data-ttu-id="ea09d-267">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="ea09d-267">nx_dhcpv6_create_client_iana</span></span>

<span data-ttu-id="ea09d-268">Создание ассоциации удостоверений (невременной) для клиента</span><span class="sxs-lookup"><span data-stu-id="ea09d-268">Create an Identity Association (Non Temporary) for the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-269">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-269">Prototype</span></span>

```C
UINT nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT IA_ident, ULONG T1, ULONG T2);
```

### <a name="description"></a><span data-ttu-id="ea09d-270">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-270">Description</span></span>

<span data-ttu-id="ea09d-271">Эта служба создает для клиента невременную ассоциацию удостоверений (IANA) на основе переданных параметров.</span><span class="sxs-lookup"><span data-stu-id="ea09d-271">This service creates a Client Non Temporary Identity Association (IANA) from the supplied parameters.</span></span> <span data-ttu-id="ea09d-272">Чтобы задать для параметров T1 и T2 максимальное значение (бесконечность) в запросах клиента DHCPv6, присвойте им значение NX_DHCPV6_INFINITE_LEASE.</span><span class="sxs-lookup"><span data-stu-id="ea09d-272">To set the T1 and T2 times to maximum (infinity) in the DHCPv6 Client requests, set these parameters to NX_DHCPV6_INFINITE_LEASE.</span></span> 

> [!NOTE]
> <span data-ttu-id="ea09d-273">Клиент имеет только одну ассоциацию IANA.</span><span class="sxs-lookup"><span data-stu-id="ea09d-273">A Client has only one IANA.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-274">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-274">Input Parameters</span></span>

- <span data-ttu-id="ea09d-275">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-275">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="ea09d-276">**IA_ident**: уникальный идентификатор ассоциации удостоверений</span><span class="sxs-lookup"><span data-stu-id="ea09d-276">**IA_ident** Identity Association unique identifier</span></span>

- <span data-ttu-id="ea09d-277">**T1** — когда клиент должен начать продление IPv6-адреса.</span><span class="sxs-lookup"><span data-stu-id="ea09d-277">**T1** When the Client must start the IPv6 address renewal</span></span>

- <span data-ttu-id="ea09d-278">**T2** — когда клиент должен начать повторную привязку IPv6-адреса.</span><span class="sxs-lookup"><span data-stu-id="ea09d-278">**T2** When the Client must start theIPv6 address rebinding</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-279">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-279">Return Values</span></span>

- <span data-ttu-id="ea09d-280">**NX_SUCCESS** (0x00) — ассоциация IANA успешно создана.</span><span class="sxs-lookup"><span data-stu-id="ea09d-280">**NX_SUCCESS** (0x00) Successfully created the IANA</span></span>

- <span data-ttu-id="ea09d-281">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-281">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-282">NX_DHCPV6_PARAM_ERROR (0xE93) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-282">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-283">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-283">Allowed From</span></span>

<span data-ttu-id="ea09d-284">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-285">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-285">Example</span></span>

```C
/* Create the Client IANA from the supplied input.  */
status = nx_dhcpv6_create_client_iana(&dhcp_0, DHCPV6_IA_ID, DHCPV6_T1,   
                                      DHCPV6_T2);

/* If status is NX_SUCCESS the client IANA was successfully created.  */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-286">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-286">See Also</span></span>

- <span data-ttu-id="ea09d-287">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="ea09d-287">nx_dhcpv6_create_client_duid</span></span>
- <span data-ttu-id="ea09d-288">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="ea09d-288">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="ea09d-289">nx_dhcpv6_add_client_ia</span><span class="sxs-lookup"><span data-stu-id="ea09d-289">nx_dhcpv6_add_client_ia</span></span>

## <a name="nx_dhcpv6_add_client_ia"></a><span data-ttu-id="ea09d-290">nx_dhcpv6_add_client_ia</span><span class="sxs-lookup"><span data-stu-id="ea09d-290">nx_dhcpv6_add_client_ia</span></span> 

<span data-ttu-id="ea09d-291">Добавление ассоциации удостоверений в клиент</span><span class="sxs-lookup"><span data-stu-id="ea09d-291">Add an Identity Association to the Client</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-292">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-292">Prototype</span></span>

```C
UINT nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                             NXD_ADDRESS *ipv6_address, 
                             ULONG preferred_lifetime, 
                             ULONG valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="ea09d-293">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-293">Description</span></span>

<span data-ttu-id="ea09d-294">Эта служба добавляет ассоциацию удостоверений клиента, заполняя запись клиента указанными параметрами.</span><span class="sxs-lookup"><span data-stu-id="ea09d-294">This service adds a Client Identity Association by filling in the Client record with the supplied parameters.</span></span> <span data-ttu-id="ea09d-295">Чтобы запросить максимальное предпочтительное и допустимое время существования, задайте для этих параметров бесконечное значение.</span><span class="sxs-lookup"><span data-stu-id="ea09d-295">To request the maximum preferred and valid lifetimes, set these parameters to infinity.</span></span> <span data-ttu-id="ea09d-296">Чтобы добавить несколько адресов IA для клиента DHCPv6, присвойте параметру NX_DHCPV6_MAX_IA_ADDRESS значение, превышающее значение по умолчанию, равное 1.</span><span class="sxs-lookup"><span data-stu-id="ea09d-296">To add more than one IA to a DHCPv6 Client, set the NX_DHCPV6_MAX_IA_ADDRESS to a value higher than the default value of 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-297">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-297">Input Parameters</span></span>

- <span data-ttu-id="ea09d-298">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-298">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="ea09d-299">**ipv6_address**: указатель на блок IP-адресов NetX Duo</span><span class="sxs-lookup"><span data-stu-id="ea09d-299">**ipv6_address** Pointer to NetX Duo IP address block</span></span>

- <span data-ttu-id="ea09d-300">**preferred_lifetime**: время до устаревания IP-адреса</span><span class="sxs-lookup"><span data-stu-id="ea09d-300">**preferred_lifetime** Length of time before IP address is deprecated</span></span>

- <span data-ttu-id="ea09d-301">**valid_lifetime**: время до истечения срока действия IP-адреса</span><span class="sxs-lookup"><span data-stu-id="ea09d-301">**valid_lifetime** Length of time before IP address is expired</span></span> 

### <a name="return-values"></a><span data-ttu-id="ea09d-302">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-302">Return Values</span></span>

- <span data-ttu-id="ea09d-303">**NX_SUCCESS** (0x00) — адрес IA клиента успешно добавлен.</span><span class="sxs-lookup"><span data-stu-id="ea09d-303">**NX_SUCCESS** (0x00) Successful Client IA added</span></span>

- <span data-ttu-id="ea09d-304">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) — повторяющийся адрес IA.</span><span class="sxs-lookup"><span data-stu-id="ea09d-304">**NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST** (0xEAF) Duplicate IA address</span></span> 

- <span data-ttu-id="ea09d-305">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) — превышено максимальное количество адресов IA, которое может храниться в клиенте.</span><span class="sxs-lookup"><span data-stu-id="ea09d-305">**NX_DHCPV6_REACHED_MAX_IA_ADDRESS** (0xEAE) IA exceeds the max IAs Client can store</span></span>

- <span data-ttu-id="ea09d-306">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-306">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-307">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) — недопустимый (например, равный NULL) адрес IA.</span><span class="sxs-lookup"><span data-stu-id="ea09d-307">NX_DHCPV6_INVALID_IA_ADDRESS (0xEA4) Invalid (e.g. null) IA address in IA</span></span>

- <span data-ttu-id="ea09d-308">NX_DHCPV6_PARAM_ERROR (0xE93) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-308">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

 
### <a name="allowed-from"></a><span data-ttu-id="ea09d-309">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-309">Allowed From</span></span>

<span data-ttu-id="ea09d-310">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-310">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-311">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-311">Example</span></span>

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_add_client_ia(&dhcp_0, &ipv6_address, 
                                 NX_DHCPV6_PREFERRED_LIFETIME,
                                 NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-312">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-312">See Also</span></span>

- <span data-ttu-id="ea09d-313">nx_dhcpv6_create_client_duid</span><span class="sxs-lookup"><span data-stu-id="ea09d-313">nx_dhcpv6_create_client_duid</span></span>
- <span data-ttu-id="ea09d-314">nx_dhcpv6_create_server_duid</span><span class="sxs-lookup"><span data-stu-id="ea09d-314">nx_dhcpv6_create_server_duid</span></span>
- <span data-ttu-id="ea09d-315">nx_dhcpv6_create_client_iana</span><span class="sxs-lookup"><span data-stu-id="ea09d-315">nx_dhcpv6_create_client_iana</span></span>

## <a name="nx_dhcpv6_get_client_duid_time_id"></a><span data-ttu-id="ea09d-316">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="ea09d-316">nx_dhcpv6_get_client_duid_time_id</span></span>

<span data-ttu-id="ea09d-317">Извлечение идентификатора времени из идентификатора DUID клиента</span><span class="sxs-lookup"><span data-stu-id="ea09d-317">Retrieves time ID from Client DUID</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-318">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-318">Prototype</span></span>

```C
UINT nx_dhcpv6_get_client_duid_time_id(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_id);
```

### <a name="description"></a><span data-ttu-id="ea09d-319">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-319">Description</span></span>

<span data-ttu-id="ea09d-320">Эта служба извлекает поле идентификатора времени из идентификатора DUID клиента.</span><span class="sxs-lookup"><span data-stu-id="ea09d-320">This service retrieves the time ID field from the Client DUID.</span></span> <span data-ttu-id="ea09d-321">Приложение должно сначала вызвать *nx_dhcpv6_create_client_duid*, чтобы заполнить идентификатор DUID клиента в экземпляре клиента DHCPv6, иначе это поле будет иметь значение NULL.</span><span class="sxs-lookup"><span data-stu-id="ea09d-321">If the application must first call *nx_dhcpv6_create_client_duid*, to fill in the Client DUID in the DHCPv6 Client instance or it will have a null value for this field.</span></span> <span data-ttu-id="ea09d-322">Цель состоит в том, чтобы приложение сохраняло эти данные и предоставляло серверу один и тот же идентификатор DUID клиента, включая поле времени, после перезагрузки.</span><span class="sxs-lookup"><span data-stu-id="ea09d-322">The intent is for the application to save this data and present the same Client DUID to the server, including the time field, across reboots.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-323">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-323">Input Parameters</span></span>

- <span data-ttu-id="ea09d-324">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-324">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="ea09d-325">**time_id**: указатель на поле времени в идентификаторе DUID клиента</span><span class="sxs-lookup"><span data-stu-id="ea09d-325">**time_id** Pointer to Client DUID time field</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-326">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-326">Return Values</span></span>

- <span data-ttu-id="ea09d-327">**NX_SUCCESS** (0x00) — данные по аренде IP-адреса успешно получены.</span><span class="sxs-lookup"><span data-stu-id="ea09d-327">**NX_SUCCESS** (0x00) IP lease data successfully retrieved</span></span>

- <span data-ttu-id="ea09d-328">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-328">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-329">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-329">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-330">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-330">Allowed From</span></span>

<span data-ttu-id="ea09d-331">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-331">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-332">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-332">Example</span></span>

```C
/* Retrieve the time ID from the Client DUID.  */
status = nx_dhcpv6_get_client_duid_time_id(&dhcp_0, &time_ID);

/* If status is NX_SUCCESS the time ID was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-333">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-333">See Also</span></span>

- <span data-ttu-id="ea09d-334">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="ea09d-334">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="ea09d-335">nx_dhcpv6_get_time_lease_data</span><span class="sxs-lookup"><span data-stu-id="ea09d-335">nx_dhcpv6_get_time_lease_data</span></span>
- <span data-ttu-id="ea09d-336">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="ea09d-336">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="ea09d-337">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="ea09d-337">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_ip_address"></a><span data-ttu-id="ea09d-338">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="ea09d-338">nx_dhcpv6_get_IP_address</span></span>

<span data-ttu-id="ea09d-339">Получение глобального IPv6-адреса клиента</span><span class="sxs-lookup"><span data-stu-id="ea09d-339">Retrieves Client’s global IPv6 address</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-340">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-340">Prototype</span></span>

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address);
```

### <a name="description"></a><span data-ttu-id="ea09d-341">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-341">Description</span></span>

<span data-ttu-id="ea09d-342">Эта служба получает глобальный IPv6-адрес клиента.</span><span class="sxs-lookup"><span data-stu-id="ea09d-342">This service retrieves the Client’s global IPv6 address.</span></span> <span data-ttu-id="ea09d-343">Если у клиента нет допустимого адреса, возвращается состояние ошибки.</span><span class="sxs-lookup"><span data-stu-id="ea09d-343">If the Client does not have a valid address, an error status is returned.</span></span> <span data-ttu-id="ea09d-344">Если у клиента более одного глобального IPv6-адреса, возвращается основной IPv6-адрес.</span><span class="sxs-lookup"><span data-stu-id="ea09d-344">If a Client has more than one global IPv6 address, the primary IPv6 address is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-345">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-345">Input Parameters</span></span>

- <span data-ttu-id="ea09d-346">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-346">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="ea09d-347">**ip_address**: указатель на IPv6-адрес</span><span class="sxs-lookup"><span data-stu-id="ea09d-347">**ip_address** Pointer to IPv6 address</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-348">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-348">Return Values</span></span>

- <span data-ttu-id="ea09d-349">**NX_SUCCESS** (0x00) — IPv6-адрес успешно назначен.</span><span class="sxs-lookup"><span data-stu-id="ea09d-349">**NX_SUCCESS** (0x00) IPv6 address successfully assigned</span></span>

- <span data-ttu-id="ea09d-350">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) — недопустимый IPv6-адрес.</span><span class="sxs-lookup"><span data-stu-id="ea09d-350">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) IPv6 address is not valid</span></span>

- <span data-ttu-id="ea09d-351">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-351">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-352">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-352">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-353">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-353">Allowed From</span></span>

<span data-ttu-id="ea09d-354">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-354">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-355">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-355">Example</span></span>

```C
UINT address_status;
UINT address_index;

/* Retrieve the client’s assigned IP address.  */
status = nx_dhcpv6_get_IP_address(&dhcp_0, &ipv6_address);

/* If status is NX_SUCCESS the client IP address was assigned.
   Now register it with NetX Duo on the primary interface (index zero). 
   The address index is returned in the address_index field*/
status = nxd_ipv6_address_set(&ip_0, 0, &ipv6_address, 64, &address_index);
```

### <a name="see-also"></a><span data-ttu-id="ea09d-356">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-356">See Also</span></span>

- <span data-ttu-id="ea09d-357">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="ea09d-357">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="ea09d-358">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="ea09d-358">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="ea09d-359">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="ea09d-359">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="ea09d-360">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="ea09d-360">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_lease_time_data"></a><span data-ttu-id="ea09d-361">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="ea09d-361">nx_dhcpv6_get_lease_time_data</span></span>

<span data-ttu-id="ea09d-362">Получение данных о времени аренды адреса IA клиента</span><span class="sxs-lookup"><span data-stu-id="ea09d-362">Retrieves Client’s IA address lease time data</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-363">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-363">Prototype</span></span>

```C
UINT nx_dhcpv6_get_lease_time_data(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                   ULONG *T2, ULONG *preferred_lifetime, 
                                   ULONG *valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="ea09d-364">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-364">Description</span></span>

<span data-ttu-id="ea09d-365">Эта служба получает данные о времени аренды глобального адреса IA клиента.</span><span class="sxs-lookup"><span data-stu-id="ea09d-365">This service retrieves the Client’s global IA address time data.</span></span> <span data-ttu-id="ea09d-366">Если адрес IA клиента находится в недопустимом состоянии, то время устанавливается в значение 0 и возвращается состояние успешного завершения.</span><span class="sxs-lookup"><span data-stu-id="ea09d-366">If the Client IA address status is invalid, time data is set to zero and a successful completion status is returned.</span></span> <span data-ttu-id="ea09d-367">Если у клиента более одного глобального IPv6-адреса, возвращаются данные основного адреса IA.</span><span class="sxs-lookup"><span data-stu-id="ea09d-367">If a Client has more than one global IPv6 address, the primary IA address data is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-368">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-368">Input Parameters</span></span>

- <span data-ttu-id="ea09d-369">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-369">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="ea09d-370">**T1**: указатель на время продления адреса IA</span><span class="sxs-lookup"><span data-stu-id="ea09d-370">**T1** Pointer to IA address renew time</span></span>

- <span data-ttu-id="ea09d-371">**T2**: указатель на время повторной привязки адреса IA</span><span class="sxs-lookup"><span data-stu-id="ea09d-371">**T2** Pointer to IA address rebind time</span></span>

- <span data-ttu-id="ea09d-372">**preferred_lifetime**: указатель на время, когда адрес IA устаревает</span><span class="sxs-lookup"><span data-stu-id="ea09d-372">**preferred_lifetime** Pointer to time when IA address is deprecated</span></span>

- <span data-ttu-id="ea09d-373">**valid_lifetime**: указатель на время, когда истекает срок действия адреса IA</span><span class="sxs-lookup"><span data-stu-id="ea09d-373">**valid_lifetime** Pointer to time when IA address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-374">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-374">Return Values</span></span>

- <span data-ttu-id="ea09d-375">**NX_SUCCESS** (0x00) — данные по аренде адреса IA успешно получены.</span><span class="sxs-lookup"><span data-stu-id="ea09d-375">**NX_SUCCESS** (0x00) IA lease data successfully retrieved</span></span>

- <span data-ttu-id="ea09d-376">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-376">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-377">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-377">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-378">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-378">Allowed From</span></span>

<span data-ttu-id="ea09d-379">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-380">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-380">Example</span></span>

```C
/* Retrieve the client’s assigned IA lease data.  */
status = nx_dhcpv6_get_lease_time_data(&dhcp_0, &T1, &T2, &preferred_lifetime, 
                                       &valid_lifetime);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-381">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-381">See Also</span></span>

- <span data-ttu-id="ea09d-382">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="ea09d-382">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="ea09d-383">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="ea09d-383">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="ea09d-384">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="ea09d-384">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="ea09d-385">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="ea09d-385">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="ea09d-386">nx_dhcpv6_get_iana_lease_time</span><span class="sxs-lookup"><span data-stu-id="ea09d-386">nx_dhcpv6_get_iana_lease_time</span></span>

## <a name="nx_dhcpv6_get_iana-lease_time"></a><span data-ttu-id="ea09d-387">nx_dhcpv6_get_iana lease_time</span><span class="sxs-lookup"><span data-stu-id="ea09d-387">nx_dhcpv6_get_iana lease_time</span></span>

<span data-ttu-id="ea09d-388">Получение данных о времени аренды IANA клиента</span><span class="sxs-lookup"><span data-stu-id="ea09d-388">Retrieve the Client’s IANA lease time data</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-389">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-389">Prototype</span></span>

```C
UINT nx_dhcpv6_get_iana_lease_time(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                    ULONG *T2);
```

### <a name="description"></a><span data-ttu-id="ea09d-390">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-390">Description</span></span>

<span data-ttu-id="ea09d-391">Эта служба получает данные о времени аренды глобальной ассоциации IANA клиента (T1 и T2).</span><span class="sxs-lookup"><span data-stu-id="ea09d-391">This service retrieves the Client’s global IA-NA lease time data (T1 and T2).</span></span> <span data-ttu-id="ea09d-392">Если ни один из адресов IANA клиента не находится в допустимом состоянии, время устанавливается в нулевое значение и возвращается состояние успешного завершения.</span><span class="sxs-lookup"><span data-stu-id="ea09d-392">If none of the Client IA-NA addresses have a valid address status, time data is set to zero and a successful completion status is returned.</span></span> <span data-ttu-id="ea09d-393">Если у клиента более одного глобального IPv6-адреса, возвращаются данные основного адреса IA.</span><span class="sxs-lookup"><span data-stu-id="ea09d-393">If a Client has more than one global IPv6 address, the primary IA address data is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-394">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-394">Input Parameters</span></span>

- <span data-ttu-id="ea09d-395">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-395">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="ea09d-396">**T1**: указатель на время, когда должно быть начато продление аренды</span><span class="sxs-lookup"><span data-stu-id="ea09d-396">**T1** Pointer to time for starting lease renewal</span></span>

- <span data-ttu-id="ea09d-397">**T2**: указатель на время, когда должна быть начата повторная привязка аренды</span><span class="sxs-lookup"><span data-stu-id="ea09d-397">**T2** Pointer to time for starting lease rebinding</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-398">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-398">Return Values</span></span>

- <span data-ttu-id="ea09d-399">**NX_SUCCESS** (0x00) — данные по аренде IANA успешно получены.</span><span class="sxs-lookup"><span data-stu-id="ea09d-399">**NX_SUCCESS** (0x00) IANA lease data successfully retrieved</span></span>

- <span data-ttu-id="ea09d-400">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-400">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-401">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-401">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-402">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-402">Allowed From</span></span>

<span data-ttu-id="ea09d-403">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-403">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-404">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-404">Example</span></span>

```C
/* Retrieve the client’s assigned IANA lease data.  */
status = nx_dhcpv6_get_iana_lease_time(&dhcp_0, &T1, &T2);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-405">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-405">See Also</span></span>

- <span data-ttu-id="ea09d-406">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="ea09d-406">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="ea09d-407">nx_dhcpv6_get_client_duid_time_id</span><span class="sxs-lookup"><span data-stu-id="ea09d-407">nx_dhcpv6_get_client_duid_time_id</span></span>
- <span data-ttu-id="ea09d-408">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="ea09d-408">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="ea09d-409">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="ea09d-409">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="ea09d-410">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="ea09d-410">nx_dhcpv6_get_lease_time_data</span></span>

## <a name="nx_dhcpv6_get_valid_ip_address_count"></a><span data-ttu-id="ea09d-411">nx_dhcpv6_get_valid_ip_address_count</span><span class="sxs-lookup"><span data-stu-id="ea09d-411">nx_dhcpv6_get_valid_ip_address_count</span></span>

<span data-ttu-id="ea09d-412">Получение числа допустимых адресов IA клиента</span><span class="sxs-lookup"><span data-stu-id="ea09d-412">Retrieve a count of Client’s valid IA addresses</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-413">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-413">Prototype</span></span>

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count);
```

### <a name="description"></a><span data-ttu-id="ea09d-414">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-414">Description</span></span>

<span data-ttu-id="ea09d-415">Эта служба получает количество допустимых IPv6-адресов клиента.</span><span class="sxs-lookup"><span data-stu-id="ea09d-415">This service retrieves the count of the Client’s valid IPv6 addresses.</span></span> <span data-ttu-id="ea09d-416">Допустимый IPv6-адрес привязывается к клиенту (назначается ему) и регистрируется в экземпляре IP.</span><span class="sxs-lookup"><span data-stu-id="ea09d-416">A valid IPv6 address is bound (assigned) to the Client and registered with the IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-417">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-417">Input Parameters</span></span>

- <span data-ttu-id="ea09d-418">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-418">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="ea09d-419">**address_count**: указатель на число возвращаемых адресов</span><span class="sxs-lookup"><span data-stu-id="ea09d-419">**address_count** Pointer to address count to return</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-420">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-420">Return Values</span></span>

- <span data-ttu-id="ea09d-421">**NX_SUCCESS** (0x00) — данные по аренде IANA успешно получены.</span><span class="sxs-lookup"><span data-stu-id="ea09d-421">**NX_SUCCESS** (0x00) IANA lease data successfully retrieved</span></span>

- <span data-ttu-id="ea09d-422">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-422">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-423">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-423">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-424">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-424">Allowed From</span></span>

<span data-ttu-id="ea09d-425">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-425">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-426">Например, .</span><span class="sxs-lookup"><span data-stu-id="ea09d-426">Example</span></span>

```C
UINT address_count; 

/* Retrieve the count of valid IA-NA addresses.  */
status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_0, &address_count);

/* If status is NX_SUCCESS the client IA address count was retrieved.  */
```

## <a name="nx_dhcpv6_get_valid_ip_address_lease_time"></a><span data-ttu-id="ea09d-427">nx_dhcpv6_get_valid_ip_address_lease_time</span><span class="sxs-lookup"><span data-stu-id="ea09d-427">nx_dhcpv6_get_valid_ip_address_lease_time</span></span>

<span data-ttu-id="ea09d-428">Получение данных об адресе IA клиента по индексу адреса</span><span class="sxs-lookup"><span data-stu-id="ea09d-428">Retrieve the Client IA data by address index</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-429">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-429">Prototype</span></span>

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                               UINT address_index,
                                               NXD_ADDRESS *ip_address,
                                               ULONG *preferred_lifetime,
                                               ULONG *valid_lifetime);
```

### <a name="description"></a><span data-ttu-id="ea09d-430">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-430">Description</span></span>

<span data-ttu-id="ea09d-431">Эта служба получает адрес IA клиента и данные по аренде по индексу адреса.</span><span class="sxs-lookup"><span data-stu-id="ea09d-431">This service retrieves the Client’s IA address and lease data by address index.</span></span> <span data-ttu-id="ea09d-432">Если указан недопустимый индекс или если IPv6-адрес по этому индексу недопустим, служба возвращает состояние ошибки NX_DHCPV6_IA_ADDRESS_NOT_VALID.</span><span class="sxs-lookup"><span data-stu-id="ea09d-432">If an invalid index is supplied, or the IPv6 address at that index is not valid, the service returns an NX_DHCPV6_IA_ADDRESS_NOT_VALID error status.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-433">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-433">Input Parameters</span></span>

- <span data-ttu-id="ea09d-434">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-434">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="ea09d-435">**address_index**: индекс в таблице адресов IA DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-435">**address_index** Index into DHCPv6 IA table</span></span>

- <span data-ttu-id="ea09d-436">**ip_address**: указатель на получаемый IPv6-адрес</span><span class="sxs-lookup"><span data-stu-id="ea09d-436">**ip_address** Pointer to IPv6 address to retrieve</span></span>

- <span data-ttu-id="ea09d-437">**preferred_lifetime**: указатель на время, когда адрес IA устаревает</span><span class="sxs-lookup"><span data-stu-id="ea09d-437">**preferred_lifetime** Pointer to time when IA address is deprecated</span></span>

- <span data-ttu-id="ea09d-438">**valid_lifetime**: указатель на время, когда истекает срок действия адреса IA</span><span class="sxs-lookup"><span data-stu-id="ea09d-438">**valid_lifetime** Pointer to time when IA address is expired</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-439">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-439">Return Values</span></span>

- <span data-ttu-id="ea09d-440">**NX_SUCCESS** (0x00) — данные IANA успешно получены.</span><span class="sxs-lookup"><span data-stu-id="ea09d-440">**NX_SUCCESS** (0x00) IANA data successfully retrieved</span></span>

- <span data-ttu-id="ea09d-441">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) — недопустимый индекс, или нет недопустимого IPv6-адреса по указанному индексу.</span><span class="sxs-lookup"><span data-stu-id="ea09d-441">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) An invalid index or no valid IPv6 address at the supplied index</span></span> 

- <span data-ttu-id="ea09d-442">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-442">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-443">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-443">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-444">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-444">Allowed From</span></span>

<span data-ttu-id="ea09d-445">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-445">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-446">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-446">Example</span></span>

```C
UINT address_index = 1; 
NXD_ADDRESS *ip_address;

/* Retrieve the IPv6 address, and valid and preferred lifetime for the IA record
   Saved at index 1 in the DHCPv6 table.  */
status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_0, address_index, 
                                                   &ip_address, 
                                                   &preferred_lifetime,  
                                                   &valid_lifetime);

/* If status is NX_SUCCESS the client IA address and lease data were retrieved.  */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-447">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-447">See Also</span></span>

- <span data-ttu-id="ea09d-448">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="ea09d-448">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="ea09d-449">nx_dhcpv6_get_iana_lease_time</span><span class="sxs-lookup"><span data-stu-id="ea09d-449">nx_dhcpv6_get_iana_lease_time</span></span>
- <span data-ttu-id="ea09d-450">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="ea09d-450">nx_dhcpv6_get_lease_time_data</span></span>

## <a name="nx_dhcpv6_get_dns_server_address"></a><span data-ttu-id="ea09d-451">nx_dhcpv6_get_DNS_server_address</span><span class="sxs-lookup"><span data-stu-id="ea09d-451">nx_dhcpv6_get_DNS_server_address</span></span>

<span data-ttu-id="ea09d-452">Получение адреса DNS-сервера</span><span class="sxs-lookup"><span data-stu-id="ea09d-452">Retrieves DNS Server address</span></span> 

### <a name="prototype"></a><span data-ttu-id="ea09d-453">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-453">Prototype</span></span>

```C
UINT nx_dhcpv6_get_DNS_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index,
                                      NXD_ADDRESS *server_address);
```

### <a name="description"></a><span data-ttu-id="ea09d-454">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-454">Description</span></span>

<span data-ttu-id="ea09d-455">Эта служба получает IPv6-адрес DNS-сервера по указанному индексу в списке клиента.</span><span class="sxs-lookup"><span data-stu-id="ea09d-455">This service retrieves the DNS server IPv6 address data at the specified index in the Client list.</span></span> <span data-ttu-id="ea09d-456">Если в списке нет адреса сервера по данному индексу, возвращается ошибка.</span><span class="sxs-lookup"><span data-stu-id="ea09d-456">If the list does not contain a server address at the index, an error is returned.</span></span> <span data-ttu-id="ea09d-457">Индекс не может превышать размер списка DNS-серверов, заданный в настраиваемом пользователем параметре NX_DHCPV6_NUM_DNS_SERVERS.</span><span class="sxs-lookup"><span data-stu-id="ea09d-457">The index may not exceed the size of the DNS Server list is specified by the user configurable option NX_DHCPV6_NUM_DNS_SERVERS.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-458">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-458">Input Parameters</span></span>

- <span data-ttu-id="ea09d-459">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-459">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="ea09d-460">**index**: индекс в списке DNS-серверов</span><span class="sxs-lookup"><span data-stu-id="ea09d-460">**index** Index into the DNS Server list</span></span>

- <span data-ttu-id="ea09d-461">**server_address**: указатель на буфер адресов сервера</span><span class="sxs-lookup"><span data-stu-id="ea09d-461">**server_address** Pointer to Server address buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-462">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-462">Return Values</span></span>

- <span data-ttu-id="ea09d-463">**NX_SUCCESS** (0x00) — адрес успешно получен.</span><span class="sxs-lookup"><span data-stu-id="ea09d-463">**NX_SUCCESS** (0x00) Address successfully retrieved</span></span>

- <span data-ttu-id="ea09d-464">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-464">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-465">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-465">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-466">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-466">Allowed From</span></span>

<span data-ttu-id="ea09d-467">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-467">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-468">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-468">Example</span></span>

```C
/* Retrieve the DNS server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


        status = nx_dhcpv6_get_DNS_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the DNS server IP address successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-469">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-469">See Also</span></span>

- <span data-ttu-id="ea09d-470">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="ea09d-470">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="ea09d-471">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="ea09d-471">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="ea09d-472">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="ea09d-472">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_other_option_data"></a><span data-ttu-id="ea09d-473">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="ea09d-473">nx_dhcpv6_get_other_option_data</span></span>

<span data-ttu-id="ea09d-474">Получение данных параметра DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-474">Retrieves DHCPv6 option data</span></span> 

### <a name="prototype"></a><span data-ttu-id="ea09d-475">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-475">Prototype</span></span>

```C
UINT  nx_dhcpv6_get_other_option_data(NX_DHCPV6 *dhcpv6_ptr, 
                                      UINT option_code, UCHAR *buffer);
```

### <a name="description"></a><span data-ttu-id="ea09d-476">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-476">Description</span></span>

<span data-ttu-id="ea09d-477">Эта служба получает данные параметра DHCPv6 из сообщения DHCPv6 по указанному коду параметра.</span><span class="sxs-lookup"><span data-stu-id="ea09d-477">This service retrieves DHCPv6 option data from a DHCPv6 message for the specified option code.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-478">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-478">Input Parameters</span></span>

- <span data-ttu-id="ea09d-479">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-479">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="ea09d-480">**option_code**: код параметра, данные которого нужно получить</span><span class="sxs-lookup"><span data-stu-id="ea09d-480">**option** code Option code for which data to retrieve</span></span>

- <span data-ttu-id="ea09d-481">**buffer**: указатель на буфер для копирования данных</span><span class="sxs-lookup"><span data-stu-id="ea09d-481">**buffer** Pointer to buffer to copy data to</span></span> 

### <a name="return-values"></a><span data-ttu-id="ea09d-482">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-482">Return Values</span></span>

- <span data-ttu-id="ea09d-483">**NX_SUCCESS** (0x00) — данные параметра успешно получены.</span><span class="sxs-lookup"><span data-stu-id="ea09d-483">**NX_SUCCESS** (0x00) Option data successfully retrieved</span></span>

- <span data-ttu-id="ea09d-484">**NX_DHCPV6_UNKNOWN_OPTION** (0xEAB) — неизвестный или неподдерживаемый код параметра.</span><span class="sxs-lookup"><span data-stu-id="ea09d-484">**NX_DHCPV6_UNKNOWN_OPTION** (0xEAB) Unknown/unsupported option code</span></span>

- <span data-ttu-id="ea09d-485">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-485">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-486">NX_DHCPV6_PARAM_ERROR (0xE93) — недопустимые входные данные без указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-486">NX_DHCPV6_PARAM_ERROR (0xE93) Invalid non pointer input</span></span>

- <span data-ttu-id="ea09d-487">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-487">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-488">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-488">Allowed From</span></span>

<span data-ttu-id="ea09d-489">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-489">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-490">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-490">Example</span></span>

```C
/* Retrieve the option data specified by the input option code. */
status = nx_dhcpv6_get_other_option_data(&dhcp_0, option_code, buffer);

/* If status is NX_SUCCESS the option data was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-491">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-491">See Also</span></span>

- <span data-ttu-id="ea09d-492">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="ea09d-492">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="ea09d-493">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="ea09d-493">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="ea09d-494">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="ea09d-494">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_get_time_accrued"></a><span data-ttu-id="ea09d-495">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="ea09d-495">nx_dhcpv6_get_time_accrued</span></span>

<span data-ttu-id="ea09d-496">Получение накопленного времени аренды для IP-адреса клиента</span><span class="sxs-lookup"><span data-stu-id="ea09d-496">Retrieves time accrued on Client’s IP address lease</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-497">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-497">Prototype</span></span>

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_accrued);
```

### <a name="description"></a><span data-ttu-id="ea09d-498">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-498">Description</span></span>

<span data-ttu-id="ea09d-499">Эта служба получает накопленное время аренды IPv6-адреса клиента.</span><span class="sxs-lookup"><span data-stu-id="ea09d-499">This service retrieves the time accrued on the Client’s IPv6 address lease.</span></span> <span data-ttu-id="ea09d-500">Функция ищет первый допустимый адрес, проверяя все IPv6-адреса, назначенные клиенту.</span><span class="sxs-lookup"><span data-stu-id="ea09d-500">The function checks all the IPv6 addresses assigned to the Client for the first valid address.</span></span> <span data-ttu-id="ea09d-501">Если допустимых адресов не найдено, возвращается нулевое значение накопленного времени.</span><span class="sxs-lookup"><span data-stu-id="ea09d-501">If no valid addresses are found, a zero value for time accrued is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-502">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-502">Input Parameters</span></span>

- <span data-ttu-id="ea09d-503">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-503">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="ea09d-504">**time_accrued**: указатель на накопленное время аренды IP-адреса</span><span class="sxs-lookup"><span data-stu-id="ea09d-504">**time_accrued** Pointer to time accrued in IP lease</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-505">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-505">Return Values</span></span>

- <span data-ttu-id="ea09d-506">**NX_SUCCESS** (0x00) — накопленное время успешно получено.</span><span class="sxs-lookup"><span data-stu-id="ea09d-506">**NX_SUCCESS** (0x00) Accrued time successfully retrieved</span></span>

- <span data-ttu-id="ea09d-507">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-507">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-508">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-508">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-509">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-509">Allowed From</span></span>

<span data-ttu-id="ea09d-510">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-510">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-511">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-511">Example</span></span>

```C
/* Retrieve time accrued time on the Client address lease. */
status = nx_dhcpv6_get_time_accrued(&dhcp_0, &time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address 
   lease was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-512">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-512">See Also</span></span>

- <span data-ttu-id="ea09d-513">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="ea09d-513">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="ea09d-514">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="ea09d-514">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="ea09d-515">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="ea09d-515">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="ea09d-516">nx_dhcpv6_set_time_accrued</span><span class="sxs-lookup"><span data-stu-id="ea09d-516">nx_dhcpv6_set_time_accrued</span></span>

## <a name="nx_dhcpv6_get_time_server_address"></a><span data-ttu-id="ea09d-517">nx_dhcpv6_get_time_server_address</span><span class="sxs-lookup"><span data-stu-id="ea09d-517">nx_dhcpv6_get_time_server_address</span></span>

<span data-ttu-id="ea09d-518">Получение адреса сервера времени</span><span class="sxs-lookup"><span data-stu-id="ea09d-518">Retrieves Time Server address</span></span> 

### <a name="prototype"></a><span data-ttu-id="ea09d-519">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-519">Prototype</span></span>

```C
UINT  nx_dhcpv6_get_time_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index, 
                                        NXD_ADDRESS *server_address);
```

### <a name="description"></a><span data-ttu-id="ea09d-520">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-520">Description</span></span>

<span data-ttu-id="ea09d-521">Эта служба получает IPv6-адрес сервера времени по указанному индексу в списке клиента.</span><span class="sxs-lookup"><span data-stu-id="ea09d-521">This service retrieves the Time server IPv6 address data at the specified index in the Client list.</span></span> <span data-ttu-id="ea09d-522">Если в списке нет адреса сервера по данному индексу, возвращается ошибка.</span><span class="sxs-lookup"><span data-stu-id="ea09d-522">If the list does not contain a server address at the index, an error is returned.</span></span> <span data-ttu-id="ea09d-523">Индекс не может превышать размер списка серверов времени, заданный в настраиваемом пользователем параметре NX_DHCPV6_NUM_TIME_SERVERS.</span><span class="sxs-lookup"><span data-stu-id="ea09d-523">The index may not exceed the size of the Time Server list is specified by the user configurable option NX_DHCPV6_NUM_TIME_SERVERS.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-524">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-524">Input Parameters</span></span>

- <span data-ttu-id="ea09d-525">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-525">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="ea09d-526">**index**: индекс в списке серверов времени</span><span class="sxs-lookup"><span data-stu-id="ea09d-526">**index** Index into the Time Server list</span></span>

- <span data-ttu-id="ea09d-527">**server_address**: указатель на буфер адресов сервера</span><span class="sxs-lookup"><span data-stu-id="ea09d-527">**server_address** Pointer to Server address buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-528">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-528">Return Values</span></span>

- <span data-ttu-id="ea09d-529">**NX_SUCCESS** (0x00) — адрес успешно получен.</span><span class="sxs-lookup"><span data-stu-id="ea09d-529">**NX_SUCCESS** (0x00) Address successfully retrieved</span></span>

- <span data-ttu-id="ea09d-530">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-530">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-531">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-531">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-532">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-532">Allowed From</span></span>

<span data-ttu-id="ea09d-533">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-533">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-534">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-534">Example</span></span>

```C
/* Retrieve the Time server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


      status = nx_dhcpv6_get_time_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the Time server IP address successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-535">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-535">See Also</span></span>

- <span data-ttu-id="ea09d-536">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="ea09d-536">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="ea09d-537">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="ea09d-537">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="ea09d-538">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="ea09d-538">nx_dhcpv6_get_time_accrued</span></span>
- <span data-ttu-id="ea09d-539">nx_dhcpv6_get_DNS_server_address</span><span class="sxs-lookup"><span data-stu-id="ea09d-539">nx_dhcpv6_get_DNS_server_address</span></span>

## <a name="nx_dhcpv6_reinitialize"></a><span data-ttu-id="ea09d-540">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="ea09d-540">nx_dhcpv6_reinitialize</span></span>

<span data-ttu-id="ea09d-541">Удаление IP-адреса клиента из таблицы IP-адресов</span><span class="sxs-lookup"><span data-stu-id="ea09d-541">Remove the Client IP address from the IP table</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-542">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-542">Prototype</span></span>

```C
UINT nx_dhcpv6_reinitialize(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="ea09d-543">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-543">Description</span></span>

<span data-ttu-id="ea09d-544">Эта служба повторно инициализирует клиент для перезапуска конечного автомата и протокола DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ea09d-544">This service reinitializes the Client for restarting the DHCPv6 state machine and re-running the DHCPv6 protocol.</span></span> <span data-ttu-id="ea09d-545">Если клиент ранее не запустил конечный автомат DHPCv6 или ему не были назначены IPv6-адреса, делать это не обязательно.</span><span class="sxs-lookup"><span data-stu-id="ea09d-545">This is not necessary if the Client has not previously started the DHPCv6 state machine or been assigned any IPv6 addresses.</span></span> <span data-ttu-id="ea09d-546">Очищаются как адреса, сохраненные в клиенте DHCPv6, так и адреса, зарегистрированные в экземпляре IP.</span><span class="sxs-lookup"><span data-stu-id="ea09d-546">The addresses saved to the DHCPv6 Client as well as registered with the IP instance are both cleared.</span></span>

> [!NOTE]
> <span data-ttu-id="ea09d-547">Приложение по-прежнему должно запустить клиент DHCPv6 с помощью службы *nx_dhcpv6_start* и инициировать запрос на назначение IPv6-адреса путем вызова *nx_dhcpv6_request_solicit*.</span><span class="sxs-lookup"><span data-stu-id="ea09d-547">The application must still start the DHCPv6 Client using the *nx_dhcpv6_start service* and begin the request for IPv6 address assignment by calling *nx_dhcpv6_request_solicit*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-548">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-548">Input Parameters</span></span>

- <span data-ttu-id="ea09d-549">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-549">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-550">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-550">Return Values</span></span>

- <span data-ttu-id="ea09d-551">**NX_SUCCESS** (0x00) — адрес успешно удален.</span><span class="sxs-lookup"><span data-stu-id="ea09d-551">**NX_SUCCESS** (0x00) Address successfully removed</span></span>

- <span data-ttu-id="ea09d-552">**NX_DHCPV6_ALREADY_STARTED** (0xE91) — клиент DHCPv6 уже запущен.</span><span class="sxs-lookup"><span data-stu-id="ea09d-552">**NX_DHCPV6_ALREADY_STARTED** (0xE91) DHCPv6 Client is already running</span></span>

- <span data-ttu-id="ea09d-553">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-553">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-554">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-554">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-555">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-555">Allowed From</span></span>

<span data-ttu-id="ea09d-556">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-556">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-557">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-557">Example</span></span>

```C
/* Clear the assigned IP address(es) from the Client and the IP instance */
status = nx_dhcpv6_reinitialize(&dhcp_0);

/* If status is NX_SUCCESS the Client IP address was successfully removed. */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-558">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-558">See Also</span></span>

- <span data-ttu-id="ea09d-559">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="ea09d-559">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="ea09d-560">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="ea09d-560">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_request_confirm"></a><span data-ttu-id="ea09d-561">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="ea09d-561">nx_dhcpv6_request_confirm</span></span>

<span data-ttu-id="ea09d-562">Обработка состояния CONFIRM клиента</span><span class="sxs-lookup"><span data-stu-id="ea09d-562">Process the Client’s CONFIRM state</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-563">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-563">Prototype</span></span>

```C
UINT nx_dhcpv6_request_confirm(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="ea09d-564">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-564">Description</span></span>

<span data-ttu-id="ea09d-565">Эта служба отправляет запрос CONFIRM.</span><span class="sxs-lookup"><span data-stu-id="ea09d-565">This service sends a CONFIRM request.</span></span> <span data-ttu-id="ea09d-566">При получении ответа от сервера клиент DHCPv6 обновляет параметры аренды с использованием полученных данных.</span><span class="sxs-lookup"><span data-stu-id="ea09d-566">If a reply is received from the Server, the DHCPv6 Client updates its lease parameters with the received data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-567">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-567">Input Parameters</span></span>

- <span data-ttu-id="ea09d-568">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-568">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-569">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-569">Return Values</span></span>

- <span data-ttu-id="ea09d-570">**NX_SUCCESS** (0x00) — сообщение CONFIRM успешно отправлено и обработано.</span><span class="sxs-lookup"><span data-stu-id="ea09d-570">**NX_SUCCESS** (0x00) CONFIRM message successfully sent and processed</span></span>

- <span data-ttu-id="ea09d-571">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-571">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-572">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-572">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-573">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-573">Allowed From</span></span>

<span data-ttu-id="ea09d-574">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-574">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-575">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-575">Example</span></span>

```C
/* Send a CONFIRM message to the Server. */
status = nx_dhcpv6_request_confirm(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the CONFIRM message. */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-576">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-576">See Also</span></span>

- <span data-ttu-id="ea09d-577">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="ea09d-577">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="ea09d-578">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="ea09d-578">nx_dhcpv6_request_release</span></span>
- <span data-ttu-id="ea09d-579">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="ea09d-579">nx_dhcpv6_request_solicit</span></span>


## <a name="nx_dhcpv6_request_inform_request"></a><span data-ttu-id="ea09d-580">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="ea09d-580">nx_dhcpv6_request_inform_request</span></span>

<span data-ttu-id="ea09d-581">Обработка состояния INFORM REQUEST клиента</span><span class="sxs-lookup"><span data-stu-id="ea09d-581">Process the Client’s INFORM REQUEST state</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-582">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-582">Prototype</span></span>

```C
UINT nx_dhcpv6_request_inform_request(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="ea09d-583">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-583">Description</span></span>

<span data-ttu-id="ea09d-584">Эта служба отправляет сообщение INFORM REQUEST.</span><span class="sxs-lookup"><span data-stu-id="ea09d-584">This service sends an INFORM REQUEST message.</span></span> <span data-ttu-id="ea09d-585">Если получен ответ, он обрабатывается с целью определить, является ли он допустимым и одобрил ли сервер запрос.</span><span class="sxs-lookup"><span data-stu-id="ea09d-585">If a reply is received, When one is received, the reply is processed to determine it is valid and the server granted the request.</span></span> <span data-ttu-id="ea09d-586">Затем при необходимости экземпляр клиента обновляется с использованием сведений с сервера.</span><span class="sxs-lookup"><span data-stu-id="ea09d-586">The Client instance is then updated with the server information as needed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-587">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-587">Input Parameters</span></span>

- <span data-ttu-id="ea09d-588">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-588">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-589">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-589">Return Values</span></span>

- <span data-ttu-id="ea09d-590">**NX_SUCCESS** (0x00) — сообщение INFORM REQUEST успешно создано и обработано.</span><span class="sxs-lookup"><span data-stu-id="ea09d-590">**NX_SUCCESS** (0x00) INFORM REQUEST message successfully created and processed</span></span>

- <span data-ttu-id="ea09d-591">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-591">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-592">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-592">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-593">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-593">Allowed From</span></span>

<span data-ttu-id="ea09d-594">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-594">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-595">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-595">Example</span></span>

```C
/* Send an INFORM REQUEST message to the server. */
status = nx_dhcpv6_request_inform_request(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the INFORM REQUEST 
   message and processed the reply. */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-596">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-596">See Also</span></span>

- <span data-ttu-id="ea09d-597">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="ea09d-597">nx_dhcpv6_request_confirm</span></span>

## <a name="nx_dhcpv6_request_option_dns_server"></a><span data-ttu-id="ea09d-598">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="ea09d-598">nx_dhcpv6_request_option_DNS_server</span></span>

<span data-ttu-id="ea09d-599">Добавление DNS-сервера в запрос параметра DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-599">Add DNS Server to DHCPv6 Option request</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-600">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-600">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="ea09d-601">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-601">Description</span></span>

<span data-ttu-id="ea09d-602">Эта служба добавляет параметр для запроса сведений о DNS-сервере в запрос параметра DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ea09d-602">This service adds the option for requesting DNS server information to the DHCPv6 option request.</span></span> <span data-ttu-id="ea09d-603">Если ответ от сервера включает в себя данные о DNS-сервере, клиент сохранит DNS-сервер при наличии места.</span><span class="sxs-lookup"><span data-stu-id="ea09d-603">If the Server reply includes DNS server data, the Client will store the DNS server if it has room to do so.</span></span> <span data-ttu-id="ea09d-604">Количество DNS-серверов, которое может хранить клиент, определяется настраиваемым параметром NX_DHCPV6_NUM_DNS_SERVERS. Значение по умолчанию — 2.</span><span class="sxs-lookup"><span data-stu-id="ea09d-604">The number of DNS servers the Client can store is determined by the configurable option NX_DHCPV6_NUM_DNS_SERVERS whose default value is 2.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-605">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-605">Input Parameters</span></span>

- <span data-ttu-id="ea09d-606">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-606">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-607">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-607">Return Values</span></span>

- <span data-ttu-id="ea09d-608">**NX_SUCCESS** (0x00) — параметр DNS-сервера включен.</span><span class="sxs-lookup"><span data-stu-id="ea09d-608">**NX_SUCCESS** (0x00) DNS server option is included</span></span>

- <span data-ttu-id="ea09d-609">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-609">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-610">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-610">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-611">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-611">Allowed From</span></span>

<span data-ttu-id="ea09d-612">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-612">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-613">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-613">Example</span></span>

```C
/* Set the DNS server option in Client requests. */
nx_dhcpv6_request_option_DNS_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="ea09d-614">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-614">See Also</span></span>

- <span data-ttu-id="ea09d-615">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="ea09d-615">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="ea09d-616">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="ea09d-616">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="ea09d-617">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="ea09d-617">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_fqdn"></a><span data-ttu-id="ea09d-618">nx_dhcpv6_request_option_FQDN</span><span class="sxs-lookup"><span data-stu-id="ea09d-618">nx_dhcpv6_request_option_FQDN</span></span>

<span data-ttu-id="ea09d-619">Добавление параметра полного доменного имени в список запросов параметров</span><span class="sxs-lookup"><span data-stu-id="ea09d-619">Add Fully Qualified Domain Name option to Option request list</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-620">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-620">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_FQDN(NX_DHCPV6 *dhcpv6_ptr, UCHAR *domain_name, 
UINT op);
```

### <a name="description"></a><span data-ttu-id="ea09d-621">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-621">Description</span></span>

<span data-ttu-id="ea09d-622">Эта служба добавляет параметр для добавления полного доменного имени клиента в запрос параметра DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ea09d-622">This service adds the option for adding the Client Fully Qualified Domain Name to the DHCPv6 option request.</span></span> <span data-ttu-id="ea09d-623">Есть три варианта параметра полного доменного имени.</span><span class="sxs-lookup"><span data-stu-id="ea09d-623">There are three options for the FQDN option:</span></span>

- <span data-ttu-id="ea09d-624">NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 — обновление сопоставления полного доменного имени и IPv6-адресов, используемых клиентом.</span><span class="sxs-lookup"><span data-stu-id="ea09d-624">NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0 Update the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the Client.</span></span>

- <span data-ttu-id="ea09d-625">NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 — обновление сопоставления полного доменного имени и IPv6-адресов, используемых клиентом, на сервере.</span><span class="sxs-lookup"><span data-stu-id="ea09d-625">NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1 Update the FQDN-to-IPv6 address mapping for FQDN and address(es) used by the Client to the server.</span></span>

- <span data-ttu-id="ea09d-626">NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 — сервер не выполняет обновлений DNS от имени клиента.</span><span class="sxs-lookup"><span data-stu-id="ea09d-626">NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2 Request the server perform no DNS updates on the Client’s behalf.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-627">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-627">Input Parameters</span></span>

- <span data-ttu-id="ea09d-628">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-628">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="ea09d-629">**domain_name**: строка, содержащая доменное имя</span><span class="sxs-lookup"><span data-stu-id="ea09d-629">**domain_name** String holding the domain name</span></span>

- <span data-ttu-id="ea09d-630">**op**: тип применяемого параметра полного доменного имени (см. список выше)</span><span class="sxs-lookup"><span data-stu-id="ea09d-630">**op** Type of FQDN option to apply (see list above)</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-631">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-631">Return Values</span></span>

- <span data-ttu-id="ea09d-632">**NX_SUCCESS** (0x00) — параметр полного доменного имени включен.</span><span class="sxs-lookup"><span data-stu-id="ea09d-632">**NX_SUCCESS** (0x00) FQDN option is included</span></span>

- <span data-ttu-id="ea09d-633">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-633">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-634">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-634">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-635">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-635">Allowed From</span></span>

<span data-ttu-id="ea09d-636">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-636">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-637">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-637">Example</span></span>

```C
/* Set the FQDN option in Client DHCPv6 request. */
nx_dhcpv6_request_option_FQDN(&dhcp_0, “DHCPv6_Client”, 
                              NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE);
```

### <a name="see-also"></a><span data-ttu-id="ea09d-638">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-638">See Also</span></span>

- <span data-ttu-id="ea09d-639">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="ea09d-639">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="ea09d-640">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="ea09d-640">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="ea09d-641">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="ea09d-641">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_domain_name"></a><span data-ttu-id="ea09d-642">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="ea09d-642">nx_dhcpv6_request_option_domain_name</span></span>

<span data-ttu-id="ea09d-643">Добавление параметра доменного имени в запрос параметра DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-643">Add domain name option to DHCPv6 option request</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-644">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-644">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_domain_name(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="ea09d-645">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-645">Description</span></span>

<span data-ttu-id="ea09d-646">Эта служба добавляет параметр доменного имени в запрос параметра в сообщениях клиента.</span><span class="sxs-lookup"><span data-stu-id="ea09d-646">This service adds the domain name option to the option request in Client request messages.</span></span> <span data-ttu-id="ea09d-647">Если ответ сервера содержит данные доменного имени, клиент сохранит их при условии, что размер доменного имени не превышает размер буфера для хранения доменного имени.</span><span class="sxs-lookup"><span data-stu-id="ea09d-647">If the Server reply includes domain name data, the Client will store the domain name information if the size of the domain name is within the buffer size for holding the domain name.</span></span> <span data-ttu-id="ea09d-648">Размер буфера — это настраиваемый параметр (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) со значением по умолчанию 30 байт.</span><span class="sxs-lookup"><span data-stu-id="ea09d-648">This buffer size is a configurable option (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) with a default value of 30 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-649">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-649">Input Parameters</span></span>

- <span data-ttu-id="ea09d-650">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-650">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-651">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-651">Return Values</span></span>

- <span data-ttu-id="ea09d-652">**NX_SUCCESS** (0x00) — набор параметров доменного имени.</span><span class="sxs-lookup"><span data-stu-id="ea09d-652">**NX_SUCCESS** (0x00) Domain name option set</span></span>

- <span data-ttu-id="ea09d-653">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-653">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-654">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-654">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-655">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-655">Allowed From</span></span>

<span data-ttu-id="ea09d-656">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-656">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-657">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-657">Example</span></span>

```C
/* Set the domain name option in Client requests. */
nx_dhcpv6_request_option_domain_name(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="ea09d-658">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-658">See Also</span></span>

- <span data-ttu-id="ea09d-659">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="ea09d-659">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="ea09d-660">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="ea09d-660">nx_dhcpv6_request_option_time_server</span></span>
- <span data-ttu-id="ea09d-661">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="ea09d-661">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_time_server"></a><span data-ttu-id="ea09d-662">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="ea09d-662">nx_dhcpv6_request_option_time_server</span></span>

<span data-ttu-id="ea09d-663">Указание данных сервера времени в качестве необязательного запроса</span><span class="sxs-lookup"><span data-stu-id="ea09d-663">Set time server data as optional request</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-664">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-664">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="ea09d-665">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-665">Description</span></span>

<span data-ttu-id="ea09d-666">Эта служба добавляет параметр для сведений о сервере времени в запрос параметра в сообщениях клиента.</span><span class="sxs-lookup"><span data-stu-id="ea09d-666">This service adds the option for time server information to the option request of Client request messages.</span></span> <span data-ttu-id="ea09d-667">Если ответ от сервера включает в себя данные о сервере времени, клиент сохранит сервер времени при наличии места.</span><span class="sxs-lookup"><span data-stu-id="ea09d-667">If the Server reply includes tim server data, the Client will store the time server if it has room to do so.</span></span> <span data-ttu-id="ea09d-668">Количество серверов времени, которое может хранить клиент, определяется настраиваемым параметром</span><span class="sxs-lookup"><span data-stu-id="ea09d-668">The number of time servers the Client can store is determined by the configurable option</span></span>

<span data-ttu-id="ea09d-669">NX_DHCPV6_NUM_TIME_SERVERS. Его значение по умолчанию — 1.</span><span class="sxs-lookup"><span data-stu-id="ea09d-669">NX_DHCPV6_NUM_TIME _SERVERS whose default value is 1.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-670">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-670">Input Parameters</span></span>

- <span data-ttu-id="ea09d-671">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-671">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-672">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-672">Return Values</span></span>

- <span data-ttu-id="ea09d-673">**NX_SUCCESS** (0x00) — добавлен параметр сервера времени.</span><span class="sxs-lookup"><span data-stu-id="ea09d-673">**NX_SUCCESS** (0x00) Time server option added</span></span>

- <span data-ttu-id="ea09d-674">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-674">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-675">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-675">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-676">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-676">Allowed From</span></span>

<span data-ttu-id="ea09d-677">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-677">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-678">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-678">Example</span></span>

```C
/* Set the time server option in Client request messages. */
nx_dhcpv6_request_option_time_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="ea09d-679">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-679">See Also</span></span>

- <span data-ttu-id="ea09d-680">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="ea09d-680">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="ea09d-681">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="ea09d-681">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="ea09d-682">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="ea09d-682">nx_dhcpv6_request_option_timezone</span></span>

## <a name="nx_dhcpv6_request_option_timezone"></a><span data-ttu-id="ea09d-683">nx_dhcpv6_request_option_timezone</span><span class="sxs-lookup"><span data-stu-id="ea09d-683">nx_dhcpv6_request_option_timezone</span></span>

<span data-ttu-id="ea09d-684">Указание данных о часовом поясе в качестве необязательного запроса</span><span class="sxs-lookup"><span data-stu-id="ea09d-684">Set time zone data as optional request</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-685">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-685">Prototype</span></span>

```C
UINT nx_dhcpv6_request_option_timezone(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="ea09d-686">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-686">Description</span></span>

<span data-ttu-id="ea09d-687">Эта служба добавляет параметр для запроса сведений о часовом поясе в запрос параметра клиента.</span><span class="sxs-lookup"><span data-stu-id="ea09d-687">This service adds the option for requesting time zone information to the Client option request.</span></span> <span data-ttu-id="ea09d-688">Если ответ сервера содержит сведения о часовом поясе, клиент сохранит их при условии, что их размер не превышает размера буфера для хранения часового пояса.</span><span class="sxs-lookup"><span data-stu-id="ea09d-688">If the Server reply includes time zone data, the Client will store the time zone information if the size of the time zone is within the buffer size for holding the time zone.</span></span> <span data-ttu-id="ea09d-689">Размер буфера — это настраиваемый параметр (NX_DHCPV6_TIME_ZONE_BUFFER_SIZE) со значением по умолчанию 10 байт.</span><span class="sxs-lookup"><span data-stu-id="ea09d-689">This buffer size is a configurable option (NX_DHCPV6_ TIME_ZONE _BUFFER_SIZE) with a default value of 10 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-690">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-690">Input Parameters</span></span>

- <span data-ttu-id="ea09d-691">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-691">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-692">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-692">Return Values</span></span>

- <span data-ttu-id="ea09d-693">**NX_SUCCESS** (0x00) — добавлен параметр часового пояса.</span><span class="sxs-lookup"><span data-stu-id="ea09d-693">**NX_SUCCESS** (0x00) Time zone option added</span></span>

- <span data-ttu-id="ea09d-694">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-694">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-695">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-695">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-696">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-696">Allowed From</span></span>

<span data-ttu-id="ea09d-697">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-698">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-698">Example</span></span>

```C
/* Set time zone option in Client request messages. */
nx_dhcpv6_request_option_timezone(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a><span data-ttu-id="ea09d-699">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-699">See Also</span></span>

- <span data-ttu-id="ea09d-700">nx_dhcpv6_request_option_DNS_server</span><span class="sxs-lookup"><span data-stu-id="ea09d-700">nx_dhcpv6_request_option_DNS_server</span></span>
- <span data-ttu-id="ea09d-701">nx_dhcpv6_request_option_domain_name</span><span class="sxs-lookup"><span data-stu-id="ea09d-701">nx_dhcpv6_request_option_domain_name</span></span>
- <span data-ttu-id="ea09d-702">nx_dhcpv6_request_option_time_server</span><span class="sxs-lookup"><span data-stu-id="ea09d-702">nx_dhcpv6_request_option_time_server</span></span>

## <a name="nx_dhcpv6_request_release"></a><span data-ttu-id="ea09d-703">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="ea09d-703">nx_dhcpv6_request_release</span></span>

<span data-ttu-id="ea09d-704">Отправка сообщения DHCPv6 RELEASE</span><span class="sxs-lookup"><span data-stu-id="ea09d-704">Send a DHCPv6 RELEASE message</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-705">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-705">Prototype</span></span>

```C
UINT nx_dhcpv6_request_release(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="ea09d-706">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-706">Description</span></span>

<span data-ttu-id="ea09d-707">Эта служба отправляет сообщение RELEASE в сети клиента.</span><span class="sxs-lookup"><span data-stu-id="ea09d-707">This service sends a RELEASE message on the Client network.</span></span> <span data-ttu-id="ea09d-708">Если сообщение успешно отправлено, возвращается состояние успешного завершения.</span><span class="sxs-lookup"><span data-stu-id="ea09d-708">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="ea09d-709">Успешное завершение не означает, что клиент получил ответ или ему уже был предоставлен IPv6-адрес.</span><span class="sxs-lookup"><span data-stu-id="ea09d-709">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="ea09d-710">Задача потока клиента DHCPv6 ожидает ответа от DHCPv6-сервера.</span><span class="sxs-lookup"><span data-stu-id="ea09d-710">The DHCPv6 Client thread task waits for a reply from a DHCPv6 Server.</span></span> <span data-ttu-id="ea09d-711">Если он получен, клиент проверяет его допустимость и сохраняет данные в записи клиента.</span><span class="sxs-lookup"><span data-stu-id="ea09d-711">If one is received, it checks the reply is valid and stores the data to the Client record.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-712">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-712">Input Parameters</span></span>

- <span data-ttu-id="ea09d-713">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-713">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-714">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-714">Return Values</span></span>

- <span data-ttu-id="ea09d-715">**NX_SUCCESS** (0x00) — сообщение RELEASE успешно отправлено.</span><span class="sxs-lookup"><span data-stu-id="ea09d-715">**NX_SUCCESS** (0x00) RELEASE message successfully sent</span></span>

- <span data-ttu-id="ea09d-716">**NX_DHCPV6_NOT_STARTED** (0xE92) — задача клиента DHCPv6 не запущена.</span><span class="sxs-lookup"><span data-stu-id="ea09d-716">**NX_DHCPV6_NOT_STARTED** (0xE92) DHCPv6 Client task not started</span></span>

- <span data-ttu-id="ea09d-717">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) — адрес не привязан к клиенту.</span><span class="sxs-lookup"><span data-stu-id="ea09d-717">**NX_DHCPV6_IA_ADDRESS_NOT_VALID** (0xEAD) Address not bound to Client</span></span>

- <span data-ttu-id="ea09d-718">**NX_INVALID_INTERFACE** (0x4C) — не найдено в таблице IP-адресов.</span><span class="sxs-lookup"><span data-stu-id="ea09d-718">**NX_INVALID_INTERFACE** (0x4C) Not found in IP address table</span></span>

- <span data-ttu-id="ea09d-719">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-719">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-720">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-720">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-721">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-721">Allowed From</span></span>

<span data-ttu-id="ea09d-722">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-722">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-723">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-723">Example</span></span>

```C
/* Send an RELEASE message to the Server. */
status = nx_dhcpv6_request_release(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the RELEASE message. */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-724">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-724">See Also</span></span>

- <span data-ttu-id="ea09d-725">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="ea09d-725">nx_dhcpv6_request_confirm</span></span>
- <span data-ttu-id="ea09d-726">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="ea09d-726">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="ea09d-727">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="ea09d-727">nx_dhcpv6_request_solicit</span></span>

## <a name="nx_dhcpv6_request_solicit"></a><span data-ttu-id="ea09d-728">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="ea09d-728">nx_dhcpv6_request_solicit</span></span>

<span data-ttu-id="ea09d-729">Отправка сообщения SOLICIT</span><span class="sxs-lookup"><span data-stu-id="ea09d-729">Send a SOLICIT message</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-730">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-730">Prototype</span></span>

```C
UINT nx_dhcpv6_request_solicit(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="ea09d-731">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-731">Description</span></span>

<span data-ttu-id="ea09d-732">Эта служба отправляет сообщение SOLICIT в сеть.</span><span class="sxs-lookup"><span data-stu-id="ea09d-732">This service sends a SOLICIT message out on the network.</span></span> <span data-ttu-id="ea09d-733">Если сообщение успешно отправлено, возвращается состояние успешного завершения.</span><span class="sxs-lookup"><span data-stu-id="ea09d-733">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="ea09d-734">Успешное завершение не означает, что клиент получил ответ или ему уже был предоставлен IPv6-адрес.</span><span class="sxs-lookup"><span data-stu-id="ea09d-734">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="ea09d-735">Задача потока клиента DHCPv6 ожидает ответа (сообщения ADVERTISE) от DHCPv6-сервера.</span><span class="sxs-lookup"><span data-stu-id="ea09d-735">The DHCPv6 Client thread task waits for a reply (an ADVERTISE message) from a DHCPv6 Server.</span></span> <span data-ttu-id="ea09d-736">Если он получен, клиент проверяет его допустимость, сохраняет данные в записи клиента и переходит в состояние REQUEST.</span><span class="sxs-lookup"><span data-stu-id="ea09d-736">If one is received, it checks the reply is valid, stores the data to the Client record and promotes the Client to the REQUEST state.</span></span>

> [!NOTE] 
> <span data-ttu-id="ea09d-737">Если задан параметр быстрой фиксации, то при получении допустимого сообщения ADVERTISE от сервера клиент DHCPv6 сразу переходит в состояние привязки.</span><span class="sxs-lookup"><span data-stu-id="ea09d-737">If the Rapid Commit option is set, the DHCPv6 Client will go directly to the Bound state if it receives a valid Server ADVERTISE message.</span></span> <span data-ttu-id="ea09d-738">Дополнительные сведения см. в описании службы *nx_dhcpv6_request_solicit_rapid*.</span><span class="sxs-lookup"><span data-stu-id="ea09d-738">See the service description for *nx_dhcpv6_request_solicit_rapid* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-739">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-739">Input Parameters</span></span>

- <span data-ttu-id="ea09d-740">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-740">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-741">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-741">Return Values</span></span>

- <span data-ttu-id="ea09d-742">**NX_SUCCESS** (0x00) — сообщение SOLICIT успешно отправлено.</span><span class="sxs-lookup"><span data-stu-id="ea09d-742">**NX_SUCCESS** (0x00) SOLICIT message successfully sent</span></span>

- <span data-ttu-id="ea09d-743">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-743">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-744">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-744">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-745">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-745">Allowed From</span></span>

<span data-ttu-id="ea09d-746">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-746">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-747">Например, .</span><span class="sxs-lookup"><span data-stu-id="ea09d-747">Example</span></span>

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

## <a name="nx_dhcpv6_request_solicit_rapid"></a><span data-ttu-id="ea09d-748">nx_dhcpv6_request_solicit_rapid</span><span class="sxs-lookup"><span data-stu-id="ea09d-748">nx_dhcpv6_request_solicit_rapid</span></span>

<span data-ttu-id="ea09d-749">Отправка сообщения SOLICIT с параметром быстрой фиксации</span><span class="sxs-lookup"><span data-stu-id="ea09d-749">Send a SOLICIT message with the Rapid Commit option</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-750">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-750">Prototype</span></span>

```C
UINT nx_dhcpv6_request_solicit_rapid(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="ea09d-751">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-751">Description</span></span>

<span data-ttu-id="ea09d-752">Эта служба отправляет сообщение SOLICIT в сеть с заданным параметром быстрой фиксации.</span><span class="sxs-lookup"><span data-stu-id="ea09d-752">This service sends a SOLICIT message out on the network with the Rapid Commit option set.</span></span> <span data-ttu-id="ea09d-753">Если сообщение успешно отправлено, возвращается состояние успешного завершения.</span><span class="sxs-lookup"><span data-stu-id="ea09d-753">If the message is successfully sent, a successful status is returned.</span></span> <span data-ttu-id="ea09d-754">Успешное завершение не означает, что клиент получил ответ или ему уже был предоставлен IPv6-адрес.</span><span class="sxs-lookup"><span data-stu-id="ea09d-754">A successful completion does not mean the Client received a response or has been granted an IPv6 address yet.</span></span> <span data-ttu-id="ea09d-755">Задача потока клиента DHCPv6 ожидает ответа (сообщения ADVERTISE) от DHCPv6-сервера.</span><span class="sxs-lookup"><span data-stu-id="ea09d-755">The DHCPv6 Client thread task waits for a reply (an ADVERTISE message) from a DHCPv6 Server.</span></span> <span data-ttu-id="ea09d-756">Если он получен, клиент проверяет его допустимость, сохраняет данные в записи клиента и переходит в состояние BOUND.</span><span class="sxs-lookup"><span data-stu-id="ea09d-756">If one is received, it checks the reply is valid, stores the data to the Client record and promotes the Client to the BOUND state.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-757">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-757">Input Parameters</span></span>

- <span data-ttu-id="ea09d-758">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-758">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-759">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-759">Return Values</span></span>

- <span data-ttu-id="ea09d-760">**NX_SUCCESS** (0x00) — сообщение SOLICIT успешно отправлено.</span><span class="sxs-lookup"><span data-stu-id="ea09d-760">**NX_SUCCESS** (0x00) SOLICIT message successfully sent</span></span>

- <span data-ttu-id="ea09d-761">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-761">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-762">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-762">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-763">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-763">Allowed From</span></span>

<span data-ttu-id="ea09d-764">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-764">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-765">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-765">Example</span></span>

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit_rapid(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-766">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-766">See Also</span></span>

- <span data-ttu-id="ea09d-767">nx_dhcpv6_request_solicit</span><span class="sxs-lookup"><span data-stu-id="ea09d-767">nx_dhcpv6_request_solicit</span></span>
- <span data-ttu-id="ea09d-768">nx_dhcpv6_request_confirm</span><span class="sxs-lookup"><span data-stu-id="ea09d-768">nx_dhcpv6_request_confirm</span></span>
- <span data-ttu-id="ea09d-769">nx_dhcpv6_request_inform_request</span><span class="sxs-lookup"><span data-stu-id="ea09d-769">nx_dhcpv6_request_inform_request</span></span>
- <span data-ttu-id="ea09d-770">nx_dhcpv6_request_release</span><span class="sxs-lookup"><span data-stu-id="ea09d-770">nx_dhcpv6_request_release</span></span>

## <a name="nx_dhcpv6_resume"></a><span data-ttu-id="ea09d-771">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="ea09d-771">nx_dhcpv6_resume</span></span>

<span data-ttu-id="ea09d-772">Возобновление задачи клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-772">Resume DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="ea09d-773">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-773">Prototype</span></span>

```C
UINT nx_dhcpv6_resume(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="ea09d-774">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-774">Description</span></span>

<span data-ttu-id="ea09d-775">Эта служба возобновляет задачу потока клиента DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ea09d-775">This service resumes the DHCPv6 Client thread task.</span></span> <span data-ttu-id="ea09d-776">Текущее состояние клиента DHCPv6 обрабатывается (например, BOUND, SOLICIT).</span><span class="sxs-lookup"><span data-stu-id="ea09d-776">The current DHCPv6 Client state will be processed (e.g. Bound, Solicit)</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-777">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-777">Input Parameters</span></span>

- <span data-ttu-id="ea09d-778">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-778">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-779">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-779">Return Values</span></span>

- <span data-ttu-id="ea09d-780">**NX_SUCCESS** (0x00) — работа клиента успешно возобновлена.</span><span class="sxs-lookup"><span data-stu-id="ea09d-780">**NX_SUCCESS** (0x00) Client successfully resumed</span></span>

- <span data-ttu-id="ea09d-781">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-781">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-782">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-782">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-783">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-783">Allowed From</span></span>

<span data-ttu-id="ea09d-784">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-784">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-785">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-785">Example</span></span>

```C
/* Resume the DHCPv6 Client task. */
status = nx_dhcpv6_resume(&dhcp_0);

/* If status is NX_SUCCESS the Client thread task successfully resumed. */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-786">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-786">See Also</span></span>

- <span data-ttu-id="ea09d-787">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="ea09d-787">nx_dhcpv6_start</span></span>
- <span data-ttu-id="ea09d-788">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="ea09d-788">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="ea09d-789">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="ea09d-789">nx_dhcpv6_suspend</span></span>

## <a name="nx_dhcpv6_set_-time_accrued"></a><span data-ttu-id="ea09d-790">nx_dhcpv6_set_time_accrued</span><span class="sxs-lookup"><span data-stu-id="ea09d-790">nx_dhcpv6_set_ time_accrued</span></span>

<span data-ttu-id="ea09d-791">Задание накопленного времени аренды для IP-адреса клиента</span><span class="sxs-lookup"><span data-stu-id="ea09d-791">Sets time accrued on Client’s IP address lease</span></span>

### <a name="prototype"></a><span data-ttu-id="ea09d-792">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-792">Prototype</span></span>

```C
UINT nx_dhcpv6_set_time_accrued(NX_DHCPV6 *dhcpv6_ptr,
                                ULONG time_accrued);
```

### <a name="description"></a><span data-ttu-id="ea09d-793">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-793">Description</span></span>

<span data-ttu-id="ea09d-794">Эта служба задает накопленное время аренды глобального IP-адреса клиента с момента назначения сервером.</span><span class="sxs-lookup"><span data-stu-id="ea09d-794">This service sets the time accrued on the Client’s global IP address since it was assigned by the server.</span></span> <span data-ttu-id="ea09d-795">Следует использовать только в том случае, если клиент в настоящее время привязан к назначенному IPv6-адресу.</span><span class="sxs-lookup"><span data-stu-id="ea09d-795">This should only be used if a Client is currently bound to an assigned IPv6 address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-796">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-796">Input Parameters</span></span>

- <span data-ttu-id="ea09d-797">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-797">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

- <span data-ttu-id="ea09d-798">**time_accrued**: накопленное время аренды IP-адреса</span><span class="sxs-lookup"><span data-stu-id="ea09d-798">**time_accrued** Time accrued in IP lease</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-799">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-799">Return Values</span></span>

- <span data-ttu-id="ea09d-800">**NX_SUCCESS** (0x00) — накопленное время успешно задано.</span><span class="sxs-lookup"><span data-stu-id="ea09d-800">**NX_SUCCESS** (0x00) Time accrued successfully set</span></span>

- <span data-ttu-id="ea09d-801">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-801">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-802">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-802">Allowed From</span></span>

<span data-ttu-id="ea09d-803">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-803">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-804">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-804">Example</span></span>

```C
/* Set time accrued since client’s assigned IP address was assigned. */
status = nx_dhcpv6_set_time_accrued(&dhcp_0, time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address lease was 
   successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-805">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-805">See Also</span></span>

- <span data-ttu-id="ea09d-806">nx_dhcpv6_get_IP_address</span><span class="sxs-lookup"><span data-stu-id="ea09d-806">nx_dhcpv6_get_IP_address</span></span>
- <span data-ttu-id="ea09d-807">nx_dhcpv6_get_other_option_data</span><span class="sxs-lookup"><span data-stu-id="ea09d-807">nx_dhcpv6_get_other_option_data</span></span>
- <span data-ttu-id="ea09d-808">nx_dhcpv6_get_lease_time_data</span><span class="sxs-lookup"><span data-stu-id="ea09d-808">nx_dhcpv6_get_lease_time_data</span></span>
- <span data-ttu-id="ea09d-809">nx_dhcpv6_get_time_accrued</span><span class="sxs-lookup"><span data-stu-id="ea09d-809">nx_dhcpv6_get_time_accrued</span></span>

## <a name="nx_dhcpv6_start"></a><span data-ttu-id="ea09d-810">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="ea09d-810">nx_dhcpv6_start</span></span>

<span data-ttu-id="ea09d-811">Запуск задачи клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-811">Start the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="ea09d-812">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-812">Prototype</span></span>

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="ea09d-813">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-813">Description</span></span>

<span data-ttu-id="ea09d-814">Эта служба запускает задачу клиента DHCPv6 и подготавливает клиент к выполнению протокола DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ea09d-814">This service starts the DHCPv6 Client task and prepares the Client for running the DHCPv6 protocol.</span></span> <span data-ttu-id="ea09d-815">Она проверяет, имеет ли экземпляр клиента достаточно информации (например, DUID клиента), создает и привязывает сокет UDP для отправки и получения сообщений DHCPv6, а также активирует таймеры для отслеживания времени сеанса и истечения срока действия аренды IPv6.</span><span class="sxs-lookup"><span data-stu-id="ea09d-815">It verifies the Client instance has sufficient information (such as a Client DUID), creates and binds the UDP socket for sending and receiving DHCPv6 messages and activates timers for keeping track of session time and when the current IPv6 lease expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-816">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-816">Input Parameters</span></span>

- <span data-ttu-id="ea09d-817">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-817">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-818">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-818">Return Values</span></span>

- <span data-ttu-id="ea09d-819">**NX_SUCCESS** (0x00) — клиент успешно запущен.</span><span class="sxs-lookup"><span data-stu-id="ea09d-819">**NX_SUCCESS** (0x00) Client successfully started</span></span>

- <span data-ttu-id="ea09d-820">**NX_DHCPV6_MISSING_REQUIRED_OPTIONS** (0xEA9) — у клиента отсутствуют обязательные параметры.</span><span class="sxs-lookup"><span data-stu-id="ea09d-820">**NX_DHCPV6_MISSING_REQUIRED_OPTIONS** (0xEA9) Client missing required options</span></span>

- <span data-ttu-id="ea09d-821">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-821">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-822">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-822">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-823">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-823">Allowed From</span></span>

<span data-ttu-id="ea09d-824">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-824">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-825">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-825">Example</span></span>

```C
/* Start the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-826">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-826">See Also</span></span>

- <span data-ttu-id="ea09d-827">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="ea09d-827">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="ea09d-828">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="ea09d-828">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="ea09d-829">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="ea09d-829">nx_dhcpv6_stop</span></span>
- <span data-ttu-id="ea09d-830">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="ea09d-830">nx_dhcpv6_reinitialize</span></span>

## <a name="nx_dhcpv6_stop"></a><span data-ttu-id="ea09d-831">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="ea09d-831">nx_dhcpv6_stop</span></span>

<span data-ttu-id="ea09d-832">Остановка задачи клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-832">Stop the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="ea09d-833">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-833">Prototype</span></span>

```C
UINT nx_dhcpv6_stop(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="ea09d-834">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-834">Description</span></span>

<span data-ttu-id="ea09d-835">Эта служба останавливает задачу клиента DHCPv6 и очищает счетчик ретрансляций и максимальный интервал ретрансляции, отключает таймеры сеанса и аренды и отменяет привязку порта сокета для клиента DHCPv6.</span><span class="sxs-lookup"><span data-stu-id="ea09d-835">This service stops the DHCPv6 Client task, and clears retransmission counts, maximum retransmission intervals, deactivates the session and lease expiration timers, and unbinds the DHCPv6 Client socket port.</span></span> <span data-ttu-id="ea09d-836">Чтобы перезапустить клиент, необходимо сначала остановить и при необходимости повторно инициализировать клиент, прежде чем начинать другой сеанс с любым DHCPv6-сервером.</span><span class="sxs-lookup"><span data-stu-id="ea09d-836">To restart the Client, one must first stop and optionally reinitialize the Client before starting another session with any DHCPv6 server.</span></span> <span data-ttu-id="ea09d-837">Дополнительные сведения см. в разделе "Небольшой пример".</span><span class="sxs-lookup"><span data-stu-id="ea09d-837">See the Small Example section for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-838">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-838">Input Parameters</span></span>

- <span data-ttu-id="ea09d-839">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-839">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-840">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-840">Return Values</span></span>

- <span data-ttu-id="ea09d-841">**NX_SUCCESS** (0x00) — клиент успешно остановлен.</span><span class="sxs-lookup"><span data-stu-id="ea09d-841">**NX_SUCCESS** (0x00) Client successfully stopped</span></span>

- <span data-ttu-id="ea09d-842">**NX_DHCPV6_NOT_STARTED** (0xE92) — поток клиента не запущен.</span><span class="sxs-lookup"><span data-stu-id="ea09d-842">**NX_DHCPV6_NOT_STARTED** (0xE92) Client thread not started</span></span>

- <span data-ttu-id="ea09d-843">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-843">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-844">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-844">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>


### <a name="allowed-from"></a><span data-ttu-id="ea09d-845">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-845">Allowed From</span></span>

<span data-ttu-id="ea09d-846">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-846">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-847">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-847">Example</span></span>

```C
/* Stop the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-848">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-848">See Also</span></span>

- <span data-ttu-id="ea09d-849">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="ea09d-849">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="ea09d-850">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="ea09d-850">nx_dhcpv6_suspend</span></span>
- <span data-ttu-id="ea09d-851">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="ea09d-851">nx_dhcpv6_reinitialize</span></span>
- <span data-ttu-id="ea09d-852">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="ea09d-852">nx_dhcpv6_start</span></span>

## <a name="nx_dhcpv6_suspend"></a><span data-ttu-id="ea09d-853">nx_dhcpv6_suspend</span><span class="sxs-lookup"><span data-stu-id="ea09d-853">nx_dhcpv6_suspend</span></span>

<span data-ttu-id="ea09d-854">Приостановка задачи клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-854">Suspend the DHCPv6 Client task</span></span> 

### <a name="prototype"></a><span data-ttu-id="ea09d-855">Прототип</span><span class="sxs-lookup"><span data-stu-id="ea09d-855">Prototype</span></span>

```C
UINT nx_dhcpv6_suspend(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a><span data-ttu-id="ea09d-856">Описание</span><span class="sxs-lookup"><span data-stu-id="ea09d-856">Description</span></span>

<span data-ttu-id="ea09d-857">Эта служба приостанавливает задачу клиента DHCPv6 и все запросы, которые находились в процессе обработки.</span><span class="sxs-lookup"><span data-stu-id="ea09d-857">This service suspends the DHCPv6 client task and any request it was in the middle of processing.</span></span> <span data-ttu-id="ea09d-858">Таймеры отключаются, и клиент переводится в состояние "не выполняется".</span><span class="sxs-lookup"><span data-stu-id="ea09d-858">Timers are deactivated and the Client state is set to non-running.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ea09d-859">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ea09d-859">Input Parameters</span></span>

- <span data-ttu-id="ea09d-860">**dhcpv6_ptr**: указатель на экземпляр клиента DHCPv6</span><span class="sxs-lookup"><span data-stu-id="ea09d-860">**dhcpv6_ptr** Pointer to DHCPv6 Client instance</span></span>

### <a name="return-values"></a><span data-ttu-id="ea09d-861">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ea09d-861">Return Values</span></span>

- <span data-ttu-id="ea09d-862">**NX_SUCCESS** (0x00) — работа клиента успешно приостановлена.</span><span class="sxs-lookup"><span data-stu-id="ea09d-862">**NX_SUCCESS** (0x00) Client successfully suspended</span></span>

- <span data-ttu-id="ea09d-863">**NX_DHCPV6_NOT_STARTED** (0XE92) — не удается приостановить работу клиента, так как он не запущен.</span><span class="sxs-lookup"><span data-stu-id="ea09d-863">**NX_DHCPV6_NOT_STARTED** (0XE92) Client not running so cannot be suspended</span></span>

- <span data-ttu-id="ea09d-864">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ea09d-864">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

- <span data-ttu-id="ea09d-865">NX_CALLER_ERROR (0x11) — вызов должен выполняться из потока.</span><span class="sxs-lookup"><span data-stu-id="ea09d-865">NX_CALLER_ERROR (0x11) Must be called from thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ea09d-866">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ea09d-866">Allowed From</span></span>

<span data-ttu-id="ea09d-867">Потоки</span><span class="sxs-lookup"><span data-stu-id="ea09d-867">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ea09d-868">Пример</span><span class="sxs-lookup"><span data-stu-id="ea09d-868">Example</span></span>

```C
/* Suspend the DHCPv6 Client task. */
status = nx_dhcpv6_suspend(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully suspended. */
```

### <a name="see-also"></a><span data-ttu-id="ea09d-869">См. также:</span><span class="sxs-lookup"><span data-stu-id="ea09d-869">See Also</span></span>

- <span data-ttu-id="ea09d-870">nx_dhcpv6_resume</span><span class="sxs-lookup"><span data-stu-id="ea09d-870">nx_dhcpv6_resume</span></span>
- <span data-ttu-id="ea09d-871">nx_dhcpv6_start</span><span class="sxs-lookup"><span data-stu-id="ea09d-871">nx_dhcpv6_start</span></span>
- <span data-ttu-id="ea09d-872">nx_dhcpv6_reinitialize</span><span class="sxs-lookup"><span data-stu-id="ea09d-872">nx_dhcpv6_reinitialize</span></span>
- <span data-ttu-id="ea09d-873">nx_dhcpv6_stop</span><span class="sxs-lookup"><span data-stu-id="ea09d-873">nx_dhcpv6_stop</span></span>
