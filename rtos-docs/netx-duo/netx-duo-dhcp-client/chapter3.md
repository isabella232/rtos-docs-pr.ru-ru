---
title: Глава 3. Описание служб клиента DHCP для NetX Duo для ОСРВ Azure
description: Эта глава содержит описание всех служб клиента DHCP для NetX Duo для ОСРВ Azure, перечисленных ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f143a443221ae08848316a458a630a0790108198
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814799"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dhcp-client-services"></a><span data-ttu-id="195d0-103">Глава 3. Описание служб клиента DHCP для NetX Duo для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="195d0-103">Chapter 3 - Description of Azure RTOS NetX Duo DHCP Client services</span></span>

<span data-ttu-id="195d0-104">Эта глава содержит описание всех служб клиента DHCP для NetX Duo для ОСРВ Azure, перечисленных ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="195d0-104">This chapter contains a description of all Azure RTOS NetX Duo DHCP Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="195d0-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="195d0-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="195d0-106">**nx_dhcp_create**: *создание экземпляра DHCP*</span><span class="sxs-lookup"><span data-stu-id="195d0-106">**nx_dhcp_create**: *Create a DHCP instance*</span></span>
- <span data-ttu-id="195d0-107">**nx_dhcp_clear_broadcast_flag**: *сброс флага трансляции в сообщениях клиента*</span><span class="sxs-lookup"><span data-stu-id="195d0-107">**nx_dhcp_clear_broadcast_flag**: *Clear broadcast flag on Client messages*</span></span>
- <span data-ttu-id="195d0-108">**nx_dhcp_delete**: *удаление экземпляра DHCP*</span><span class="sxs-lookup"><span data-stu-id="195d0-108">**nx_dhcp_delete**: *Delete a DHCP instance*</span></span>
- <span data-ttu-id="195d0-109">**nx_dhcp_force_renew**: *отправка сообщения принудительного обновления*</span><span class="sxs-lookup"><span data-stu-id="195d0-109">**nx_dhcp_force_renew**: *Send a force renew message*</span></span>
- <span data-ttu-id="195d0-110">**nx_dhcp_packet_pool_set**: *задание пула пакетов клиента DHCP*</span><span class="sxs-lookup"><span data-stu-id="195d0-110">**nx_dhcp_packet_pool_set**: *Set the DHCP Client packet pool*</span></span>
- <span data-ttu-id="195d0-111">**nx_dhcp_decline**: отправка *сообщения об отклонении на сервер*</span><span class="sxs-lookup"><span data-stu-id="195d0-111">**nx_dhcp_decline**: Send *Decline message to server*</span></span>
- <span data-ttu-id="195d0-112">**nx_dhcp_release**: отправка *сообщения об освобождении на сервер*</span><span class="sxs-lookup"><span data-stu-id="195d0-112">**nx_dhcp_release**: Send *Release message to server*</span></span>
- <span data-ttu-id="195d0-113">**nx_dhcp_reinitialize**: *сброс сетевых параметров клиента DHCP*</span><span class="sxs-lookup"><span data-stu-id="195d0-113">**nx_dhcp_reinitialize**: *Clear DHCP client network parameters*</span></span>
- <span data-ttu-id="195d0-114">**nx_dhcp_request_client_ip**: *указание определенного IP-адреса*</span><span class="sxs-lookup"><span data-stu-id="195d0-114">**nx_dhcp_request_client_ip**: *Specify a specific IP address*</span></span>
- <span data-ttu-id="195d0-115">**nx_dhcp_send_request**: *отправка сообщения DHCP на сервер*</span><span class="sxs-lookup"><span data-stu-id="195d0-115">**nx_dhcp_send_request**: *Send DHCP message to server*</span></span>
- <span data-ttu-id="195d0-116">**nx_dhcp_start**: *запуск обработки клиента DHCP*</span><span class="sxs-lookup"><span data-stu-id="195d0-116">**nx_dhcp_start**: *Start the DHCP Client processing*</span></span>
- <span data-ttu-id="195d0-117">**nx_dhcp_stop**: *остановка обработки клиента DHCP*</span><span class="sxs-lookup"><span data-stu-id="195d0-117">**nx_dhcp_stop**: *Stop the DHCP Client processing*</span></span>
- <span data-ttu-id="195d0-118">**nx_dhcp_set_interface_index**: *задание интерфейса для запуска клиента DHCP*</span><span class="sxs-lookup"><span data-stu-id="195d0-118">**nx_dhcp_set_interface_index**: *Set the interface to run DHCP Client*</span></span>
- <span data-ttu-id="195d0-119">**nx_dhcp_server_address_get**: *получение IP-адреса DHCP-сервера*</span><span class="sxs-lookup"><span data-stu-id="195d0-119">**nx_dhcp_server_address_get**: *Get the DHCP server IP address*</span></span>
- <span data-ttu-id="195d0-120">**nx_dhcp_state_change_notify**: *задание функции обратного вызова при изменении состояния DHCP*</span><span class="sxs-lookup"><span data-stu-id="195d0-120">**nx_dhcp_state_change_notify**: *Set the callback function when DHCP state changes*</span></span>
- <span data-ttu-id="195d0-121">**nx_dhcp_user_option_retrieve**: *получение указанного параметра DHCP*</span><span class="sxs-lookup"><span data-stu-id="195d0-121">**nx_dhcp_user_option_retrieve**: *Retrieve the specified DHCP option*</span></span>
- <span data-ttu-id="195d0-122">**nx_dhcp_user_option_convert**: *преобразование четырех байт в ULONG*</span><span class="sxs-lookup"><span data-stu-id="195d0-122">**nx_dhcp_user_option_convert**: *Convert four bytes to ULONG*</span></span>

<span data-ttu-id="195d0-123">Службы клиента DHCP, относящиеся к интерфейсу</span><span class="sxs-lookup"><span data-stu-id="195d0-123">Interface specific DHCP Client services:</span></span>
 
- <span data-ttu-id="195d0-124">**nx_dhcp_interface_clear_broadcast_flag**: *снятие флага трансляции в сообщениях клиента в указанном интерфейсе*</span><span class="sxs-lookup"><span data-stu-id="195d0-124">**nx_dhcp_interface_clear_broadcast_flag**: *Clear broadcast flag on Client messages on specified interface*</span></span>
- <span data-ttu-id="195d0-125">**nx_dhcp_interface_enable**: *включение протокола DHCP для указанного интерфейса*</span><span class="sxs-lookup"><span data-stu-id="195d0-125">**nx_dhcp_interface_enable**: *Enable interface to run DHCP on the specified interface*</span></span>
- <span data-ttu-id="195d0-126">**nx_dhcp_interface_disable**: *отключение протокола DHCP для указанного интерфейса*</span><span class="sxs-lookup"><span data-stu-id="195d0-126">**nx_dhcp_interface_disable**: *Disable interface to run DHCP on the specified interface*</span></span>
- <span data-ttu-id="195d0-127">**nx_dhcp_interface_decline**: *отправка сообщения об отклонении на сервер через указанный интерфейс*</span><span class="sxs-lookup"><span data-stu-id="195d0-127">**nx_dhcp_interface_decline**: *Send Decline message to server on the specified interface*</span></span>
- <span data-ttu-id="195d0-128">**nx_dhcp_interface_force_renew**: *отправка сообщения принудительного обновления через указанный интерфейс*</span><span class="sxs-lookup"><span data-stu-id="195d0-128">**nx_dhcp_interface_force_renew**: *Send a force renew message on the specified interface*</span></span>
- <span data-ttu-id="195d0-129">**nx_dhcp_interface_reinitialize**: *сброс параметров сети клиента DHCP в указанном интерфейсе*</span><span class="sxs-lookup"><span data-stu-id="195d0-129">**nx_dhcp_interface_reinitialize**: *Clear DHCP client network parameters on the specified interface*</span></span>
- <span data-ttu-id="195d0-130">**nx_dhcp_interface_release**: *отправка сообщения об освобождении на сервер через указанный интерфейс*</span><span class="sxs-lookup"><span data-stu-id="195d0-130">**nx_dhcp_interface_release**: *Send Release message to server on the specified interface*</span></span>
- <span data-ttu-id="195d0-131">**nx_dhcp_interface_request_client_ip**: *указание IP-адреса для указанного интерфейса*</span><span class="sxs-lookup"><span data-stu-id="195d0-131">**nx_dhcp_interface_request_client_ip**: *Specify a specific IP address on the specified interface*</span></span>
- <span data-ttu-id="195d0-132">**nx_dhcp_interface_send_request**: *отправка сообщения DHCP на сервер через указанный интерфейс*</span><span class="sxs-lookup"><span data-stu-id="195d0-132">**nx_dhcp_interface_send_request**: *Send DHCP message to server on the specified interface*</span></span>
- <span data-ttu-id="195d0-133">**nx_dhcp_interface_server_address_get**: *получение IP-адреса DHCP-сервера для указанного интерфейса*</span><span class="sxs-lookup"><span data-stu-id="195d0-133">**nx_dhcp_interface_server_address_get**: *Get the DHCP server IP address on the specified interface*</span></span>
- <span data-ttu-id="195d0-134">**nx_dhcp_interface_start**: *запуск обработки клиента DHCP в указанном интерфейсе*</span><span class="sxs-lookup"><span data-stu-id="195d0-134">**nx_dhcp_interface_start**: *Start the DHCP Client processing on the specified interface*</span></span>
- <span data-ttu-id="195d0-135">**nx_dhcp_interface_stop**: *остановка обработки клиента DHCP в указанном интерфейсе*</span><span class="sxs-lookup"><span data-stu-id="195d0-135">**nx_dhcp_interface_stop**: *Stop the DHCP Client processing on the specified interface*</span></span>
- <span data-ttu-id="195d0-136">**nx_dhcp_interface_state_change_notify**: *указание функции обратного вызова при изменении состояния DHCP в указанном интерфейсе*</span><span class="sxs-lookup"><span data-stu-id="195d0-136">**nx_dhcp_interface_state_change_notify**: *Set the callback function when DHCP state changes on the specified interface*</span></span>
- <span data-ttu-id="195d0-137">**nx_dhcp_interface_user_option_retrieve**: *получение указанного параметра DHCP для заданного интерфейса*</span><span class="sxs-lookup"><span data-stu-id="195d0-137">**nx_dhcp_interface_user_option_retrieve**: *Retrieve the specified DHCP option on the specified interface*</span></span>

<span data-ttu-id="195d0-138">Службы клиента DHCP, если определено значение NX_DHCP_CLIENT_RESORE_STATE</span><span class="sxs-lookup"><span data-stu-id="195d0-138">DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="195d0-139">**nx_dhcp_resume**: *восстановление ранее заданного состояния клиента DHCP*</span><span class="sxs-lookup"><span data-stu-id="195d0-139">**nx_dhcp_resume**: *Resume previously established DHCP Client state*</span></span>
- <span data-ttu-id="195d0-140">**nx_dhcp_suspend**: *приостановка обработки состояния клиента DHCP*</span><span class="sxs-lookup"><span data-stu-id="195d0-140">**nx_dhcp_suspend**: *Suspend processing the DHCP Client state*</span></span>
- <span data-ttu-id="195d0-141">**nx_dhcp_client_get_record**: *создание записи состояния клиента DHCP*</span><span class="sxs-lookup"><span data-stu-id="195d0-141">**nx_dhcp_client_get_record**: *Create a record of the DHCP Client state*</span></span>
- <span data-ttu-id="195d0-142">**nx_dhcp_client_restore_record**: *восстановление ранее сохраненной записи в клиенте DHCP*</span><span class="sxs-lookup"><span data-stu-id="195d0-142">**nx_dhcp_client_restore_record**: *Restore a previously saved record to the DHCP Client*</span></span>
- <span data-ttu-id="195d0-143">**nx_dhcp_client_update_time_remaining**: *обновление оставшегося времени в текущем состоянии DHCP*</span><span class="sxs-lookup"><span data-stu-id="195d0-143">**nx_dhcp_client_update_time_remaining**: *Update the time remaining in the current DHCP state*</span></span>

<span data-ttu-id="195d0-144">Службы клиента DHCP, относящиеся к интерфейсу, если определено значение NX_DHCP_CLIENT_RESORE_STATE</span><span class="sxs-lookup"><span data-stu-id="195d0-144">Interface Specific DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="195d0-145">**nx_dhcp_client_interface_get_record**: *создание записи состояния клиента DHCP в указанном интерфейсе*</span><span class="sxs-lookup"><span data-stu-id="195d0-145">**nx_dhcp_client_interface_get_record**: *Create a record of the DHCP Client state on the specified interface*</span></span>
- <span data-ttu-id="195d0-146">**nx_dhcp_client_interface_restore_record**: *восстановление ранее сохраненной записи состояния клиента DHCP в указанном интерфейсе*</span><span class="sxs-lookup"><span data-stu-id="195d0-146">**nx_dhcp_client_interface_restore_record**: *Restore a previously saved record to the DHCP Client on the specified interface*</span></span>
- <span data-ttu-id="195d0-147">**nx_dhcp_client_interface_update_time_remaining**: *обновление оставшегося времени в текущем состоянии DHCP для указанного интерфейса*</span><span class="sxs-lookup"><span data-stu-id="195d0-147">**nx_dhcp_client_interface_update_time_remaining**: *Update the time remaining in the current DHCP state on the specified interface*</span></span>

## <a name="nx_dhcp_create"></a><span data-ttu-id="195d0-148">nx_dhcp_create</span><span class="sxs-lookup"><span data-stu-id="195d0-148">nx_dhcp_create</span></span>

<span data-ttu-id="195d0-149">Создание экземпляра DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-149">Create a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-150">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-150">Prototype</span></span>

```c
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="195d0-151">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-151">Description</span></span>

<span data-ttu-id="195d0-152">Эта служба создает экземпляр DHCP для ранее созданного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="195d0-152">This service creates a DHCP instance for the previously created IP instance.</span></span> <span data-ttu-id="195d0-153">По умолчанию протокол DHCP включается для основного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-153">By default the primary interface is enabled for running DHCP.</span></span> <span data-ttu-id="195d0-154">Введенное имя, хотя и не используется в реализации клиента DHCP в NetX Duo, должно соответствовать требованиям RFC 1035 к именам узлов.</span><span class="sxs-lookup"><span data-stu-id="195d0-154">The name input, while not used in the NetX Duo implementation of DHCP Client, must follow RFC 1035 criteria for host names.</span></span> <span data-ttu-id="195d0-155">Общая длина не должна превышать 255 символов, а элементы, разделяемые точками, должны начинаться с буквы, заканчиваться буквой или цифрой и могут содержать только буквы, цифры и дефисы.</span><span class="sxs-lookup"><span data-stu-id="195d0-155">The total length must not exceed 255 characters, the labels separate by dots must begin with a letter, and end with a letter or number, and may contain hyphens but no other non-alphanumeric character.</span></span>

<span data-ttu-id="195d0-156">Если приложению требуется запустить протокол DHCP в другом интерфейсе, зарегистрированном в экземпляре IP (с помощью *nx_ip_interface_attach*), оно может вызвать *nx_dhcp_set_interface_index* для запуска протокола DHCP только в этом интерфейсе или *nx_dhcp_interface_enable* для запуска протокола DHCP в этом интерфейсе в дополнение к другим.</span><span class="sxs-lookup"><span data-stu-id="195d0-156">If the application would like to run DHCP another interface registered with the IP instance, (using *nx_ip_interface_attach*), the application can call *nx_dhcp_set_interface_index* to run DHCP on just that interface, or *nx_dhcp_interface_enable* to run DHCP on that interface as well.</span></span> <span data-ttu-id="195d0-157">Дополнительные сведения см. в описании этих служб.</span><span class="sxs-lookup"><span data-stu-id="195d0-157">See description of these services for more details.</span></span>

>[!NOTE]
> <span data-ttu-id="195d0-158">Приложение должно убедиться в том, что полезные данные пула пакетов клиента DHCP поддерживают минимальный размер сообщения DHCP, указанный в разделе 2 спецификации RFC 2131 (548 байт данных сообщения DHCP плюс заголовки UDP, IP и кадра физической сети).</span><span class="sxs-lookup"><span data-stu-id="195d0-158">The application must make sure the DHCP Client packet pool payload can support the minimum DHCP message size specified by the RFC 2131 Section 2 (548 bytes of DHCP message data plus UDP, IP and physical network frame headers).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-159">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-159">Input Parameters</span></span>

- <span data-ttu-id="195d0-160">**dhcp_ptr**: указатель на блок управления DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-160">**dhcp_ptr**: Pointer to DHCP control block.</span></span> 
- <span data-ttu-id="195d0-161">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="195d0-161">**ip_ptr**: Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="195d0-162">**name_ptr**: указатель на имя узла для экземпляра DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-162">**name_ptr**: Pointer to host name for DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-163">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-163">Return Values</span></span>

- <span data-ttu-id="195d0-164">**NX_SUCCESS** (0x00) — успешное создание DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-164">**NX_SUCCESS**: (0x00) Successful DHCP create</span></span>
- <span data-ttu-id="195d0-165">**NX_DHCP_INVALID_NAME** (0xA8) — недопустимое имя узла.</span><span class="sxs-lookup"><span data-stu-id="195d0-165">**NX_DHCP_INVALID_NAME**: (0xA8) Invalid host name</span></span>
- <span data-ttu-id="195d0-166">**NX_DHCP_INVALID_PAYLOAD** (0x9C) — недостаточно полезных данных для сообщения DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-166">**NX_DHCP_INVALID_PAYLOAD**: (0x9C) Payload too small for DHCP message</span></span>
- <span data-ttu-id="195d0-167">NX_PTR_ERROR (0x16) — недопустимый указатель IP или DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-167">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-168">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-168">Allowed From</span></span>

<span data-ttu-id="195d0-169">Потоки, инициализация</span><span class="sxs-lookup"><span data-stu-id="195d0-169">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="195d0-170">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-170">Example</span></span>

```c
/* Create a DHCP instance.  */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created.  */
```

## <a name="nx_dhcp_interface_enable"></a><span data-ttu-id="195d0-171">nx_dhcp_interface_enable</span><span class="sxs-lookup"><span data-stu-id="195d0-171">nx_dhcp_interface_enable</span></span>

<span data-ttu-id="195d0-172">Включение протокола DHCP для указанного интерфейса</span><span class="sxs-lookup"><span data-stu-id="195d0-172">Enable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="195d0-173">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-173">Prototype</span></span>

```c
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="195d0-174">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-174">Description</span></span>

<span data-ttu-id="195d0-175">Эта служба включает протокол DHCP для указанного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-175">This service enables the specified interface for running DHCP.</span></span> <span data-ttu-id="195d0-176">По умолчанию клиент DHCP включен для основного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-176">By default the primary interface is enabled for DHCP Client.</span></span> <span data-ttu-id="195d0-177">На этом этапе можно запустить DHCP либо в этом интерфейсе путем вызова *nx_dhcp_interface_start*, либо во всех включенных интерфейсах с помощью *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="195d0-177">At this point, DHCP can be started on this interface either by calling *nx_dhcp_interface_start* or to start DHCP on all enabled interfaces *nx_dhcp_start*.</span></span>

>[!NOTE] 
> <span data-ttu-id="195d0-178">Приложение должно сначала зарегистрировать этот интерфейс в экземпляре IP с помощью *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="195d0-178">The application must first register this interface with the IP instance, using *nx_ip_interface_attach.*</span></span>

<span data-ttu-id="195d0-179">Кроме того, для добавления этого интерфейса в список включенных должна быть доступная запись клиентского интерфейса DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-179">Further, there must be an available DHCP Client interface ‘record’ to add this interface to the list of enabled interfaces.</span></span> <span data-ttu-id="195d0-180">По умолчанию параметр NX_DHCP_CLIENT_MAX_RECORDS имеет значение 1.</span><span class="sxs-lookup"><span data-stu-id="195d0-180">By default NX_DHCP_CLIENT_MAX_RECORDS is defined to 1.</span></span> <span data-ttu-id="195d0-181">Задайте в этом параметре максимальное число интерфейсов, которое может выполняться в клиенте DHCP одновременно.</span><span class="sxs-lookup"><span data-stu-id="195d0-181">Set this option to the maximum number of interfaces expected to run DHCP Client simultaneously.</span></span> <span data-ttu-id="195d0-182">Обычно значение NX_DHCP_CLIENT_MAX_RECORDS равно NX_MAX_PHYSICAL_INTERFACES. Однако, если у устройства больше физических интерфейсов, чем требуется для работы клиента DHCP, можно сэкономить память, задав в параметре NX_DHCP_CLIENT_MAX_RECORDS меньшее число.</span><span class="sxs-lookup"><span data-stu-id="195d0-182">Typically NX_DHCP_CLIENT_MAX_RECORDS will equal NX_MAX_PHYSICAL_INTERFACES; however, if a device has more physical interfaces than it expects to run DHCP Client, it can save memory by setting NX_DHCP_CLIENT_MAX_RECORDS to less than that number.</span></span> <span data-ttu-id="195d0-183">Не существует однозначного сопоставления между физическими интерфейсами и записями клиентских интерфейсов DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-183">There is not a one to one mapping of physical interfaces with DHCP Client interface records.</span></span>

<span data-ttu-id="195d0-184">Разница между этой службой и *nx_dhcp_set_interface_index* в том, что последняя включает протокол DHCP только для одного интерфейса, тогда как данная служба просто добавляет указанный интерфейс в список клиентских интерфейсов с поддержкой DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-184">The difference between this service and *nx_dhcp_set_interface_index* is the latter sets only a single interface to run DHCP whereas this service simply adds the specified interface to the list of Client interfaces enabled for DHCP.</span></span>

<span data-ttu-id="195d0-185">Чтобы отключить протокол DHCP для интерфейса, приложение может вызвать службу</span><span class="sxs-lookup"><span data-stu-id="195d0-185">To disable an interface for DHCP, the application can call the</span></span>

<span data-ttu-id="195d0-186">*nx_dhcp_interface_disable*.</span><span class="sxs-lookup"><span data-stu-id="195d0-186">*nx_dhcp_interface_disable* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-187">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-187">Input Parameters</span></span>

- <span data-ttu-id="195d0-188">**dhcp_ptr**: указатель на блок управления DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-188">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="195d0-189">**interface_index**: индекс интерфейса, для которого нужно включить протокол DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-189">**interface_index**: Index of interface to enable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-190">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-190">Return Values</span></span>

- <span data-ttu-id="195d0-191">**NX_SUCCESS** (0x00) — протокол DHCP успешно включен.</span><span class="sxs-lookup"><span data-stu-id="195d0-191">**NX_SUCCESS**: (0x00) Successful DHCP enable</span></span>
- <span data-ttu-id="195d0-192">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) — нет доступной записи для другого интерфейса, для которого следует включить протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-192">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) No record available for another Interface to be enabled for DHCP</span></span>
- <span data-ttu-id="195d0-193">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) — протокол DHCP включен для интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-193">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) Interface enabled for DHCP</span></span>
- <span data-ttu-id="195d0-194">NX_PTR_ERROR (0x16) — недопустимый указатель IP или DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-194">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="195d0-195">NX_INVALID_INTERFACE (0x4C) — недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="195d0-195">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-196">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-196">Allowed From</span></span>

<span data-ttu-id="195d0-197">Потоки, инициализация</span><span class="sxs-lookup"><span data-stu-id="195d0-197">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="195d0-198">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-198">Example</span></span>

```c
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface.  NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled.  */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1.  */
```

## <a name="nx_dhcp_interface_disable"></a><span data-ttu-id="195d0-199">nx_dhcp_interface_disable</span><span class="sxs-lookup"><span data-stu-id="195d0-199">nx_dhcp_interface_disable</span></span>

<span data-ttu-id="195d0-200">Отключение протокола DHCP для указанного интерфейса</span><span class="sxs-lookup"><span data-stu-id="195d0-200">Disable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="195d0-201">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-201">Prototype</span></span>

```c

UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr, 
                               UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="195d0-202">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-202">Description</span></span>

<span data-ttu-id="195d0-203">Эта служба отключает протокол DHCP для указанного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-203">This service disables the specified interface for running DHCP.</span></span> <span data-ttu-id="195d0-204">Она повторно инициализирует клиент DHCP для этого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-204">It reinitializes the DHCP Client on this interface.</span></span>

<span data-ttu-id="195d0-205">Чтобы перезапустить клиент DHCP, приложение должно повторно включить интерфейс с помощью *nx_dhcp_interface_enable* и перезапустить DHCP, вызвав *nx_dhcp_interface_start*.</span><span class="sxs-lookup"><span data-stu-id="195d0-205">To restart the DHCP Client the application must re-enable the interface using *nx_dhcp_interface_enable* and restart DHCP by calling *nx_dhcp_interface_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-206">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-206">Input Parameters</span></span>

- <span data-ttu-id="195d0-207">**dhcp_ptr**: указатель на блок управления DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-207">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="195d0-208">**interface_index**: индекс интерфейса, для которого нужно отключить протокол DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-208">**interface_index**: Index of interface to disable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-209">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-209">Return Values</span></span>

- <span data-ttu-id="195d0-210">**NX_SUCCESS** (0x00) — успешное создание DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-210">**NX_SUCCESS**: (0x00) Successful DHCP create</span></span>
- <span data-ttu-id="195d0-211">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) — протокол DHCP не включен для интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-211">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="195d0-212">NX_PTR_ERROR (0x16) — недопустимый указатель IP или DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-212">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="195d0-213">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-213">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="195d0-214">NX_INVALID_INTERFACE (0x4C) — недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="195d0-214">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-215">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-215">Allowed From</span></span>

<span data-ttu-id="195d0-216">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-216">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-217">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-217">Example</span></span>

```c
/* Disable DHCP on a secondary interface. */

status =  nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled.  */
```
## <a name="nx_dhcp_clear_broadcast_flag"></a><span data-ttu-id="195d0-218">nx_dhcp_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="195d0-218">nx_dhcp_clear_broadcast_flag</span></span>

<span data-ttu-id="195d0-219">Установка флага широковещательного режима DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-219">Set the DHCP broadcast flag</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-220">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-220">Prototype</span></span>

```c
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="195d0-221">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-221">Description</span></span>

<span data-ttu-id="195d0-222">Эта служба устанавливает или снимает флаг широковещательного режима в заголовке сообщения DHCP для всех интерфейсов, для которых включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-222">This service sets or clears the broadcast flag the DHCP message header for all interfaces enabled for DHCP.</span></span> <span data-ttu-id="195d0-223">Для некоторых сообщений DHCP (например, DISCOVER) флаг широковещательного режима установлен, так как у клиента нет IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="195d0-223">For some DHCP messages (e.g. DISCOVER) the broadcast flag is set to broadcast because the Client does not have an IP address.</span></span>

<span data-ttu-id="195d0-224">Значения clear_flag</span><span class="sxs-lookup"><span data-stu-id="195d0-224">clear_flag values:</span></span> 

- <span data-ttu-id="195d0-225">**NX_TRUE** — флаг широковещательного режима снят (запрашивается одноадресный ответ).</span><span class="sxs-lookup"><span data-stu-id="195d0-225">**NX_TRUE**: broadcast flag is cleared (request unicast response)</span></span>
- <span data-ttu-id="195d0-226">**NX_FALSE** — флаг широковещательного режима установлен (запрашивается широковещательный ответ).</span><span class="sxs-lookup"><span data-stu-id="195d0-226">**NX_FALSE**: broadcast flag is set (request broadcast response)</span></span>

<span data-ttu-id="195d0-227">Эта служба предназначена для клиентов DHCP, которые должны обращаться к DHCP-серверу через маршрутизатор, который отклоняет переадресацию широковещательных сообщений.</span><span class="sxs-lookup"><span data-stu-id="195d0-227">This service is intended for DHCP Clients that must go through a router to get to the DHCP Server, where the router rejects forwarding broadcast messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-228">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-228">Input Parameters</span></span>

- <span data-ttu-id="195d0-229">**dhcp_ptr**: указатель на блок управления DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-229">**dhcp_ptr**: Pointer to DHCP control block</span></span>  
- <span data-ttu-id="195d0-230">**clear_flag**: значение, в которое устанавливается флаг широковещательного режима</span><span class="sxs-lookup"><span data-stu-id="195d0-230">**clear_flag**: Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-231">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-231">Return Values</span></span>

- <span data-ttu-id="195d0-232">**NX_SUCCESS** (0x00) — флаг успешно установлен.</span><span class="sxs-lookup"><span data-stu-id="195d0-232">**NX_SUCCESS**: (0x00) Successfully set flag</span></span>
- <span data-ttu-id="195d0-233">NX_PTR_ERROR (0x16) — недопустимый указатель IP или DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-233">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-234">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-234">Allowed From</span></span>

<span data-ttu-id="195d0-235">Потоки, инициализация</span><span class="sxs-lookup"><span data-stu-id="195d0-235">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="195d0-236">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-236">Example</span></span>

```c
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response).  */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated.  */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a><span data-ttu-id="195d0-237">nx_dhcp_interface_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="195d0-237">nx_dhcp_interface_clear_broadcast_flag</span></span>

<span data-ttu-id="195d0-238">Установка или снятие флага широковещательного режима для указанного интерфейса</span><span class="sxs-lookup"><span data-stu-id="195d0-238">Set or clear the broadcast flag on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-239">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-239">Prototype</span></span>

```c
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr, 
                                            UINT interface_index, 
                                            UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="195d0-240">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-240">Description</span></span>

<span data-ttu-id="195d0-241">Эта служба позволяет ведущему приложению клиента DHCP устанавливать или снимать флаг широковещательного режима в сообщениях клиента DHCP к DHCP-серверу через указанный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="195d0-241">This service enables the DHCP Client host application to set or clear the broadcast flag in DHCP Client messages to the DHCP Server on the specified interface.</span></span> <span data-ttu-id="195d0-242">Дополнительные сведения см. в описании службы **nx_dhcp_clear_broadcast_flag**.</span><span class="sxs-lookup"><span data-stu-id="195d0-242">For more details see **nx_dhcp_clear_broadcast_flag**.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-243">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-243">Input Parameters</span></span>

- <span data-ttu-id="195d0-244">**dhcp_ptr**: указатель на блок управления DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-244">**dhcp_ptr**: Pointer to DHCP control block</span></span>
- <span data-ttu-id="195d0-245">**interface_index**: индекс интерфейса, для которого нужно установить флаг широковещательного режима</span><span class="sxs-lookup"><span data-stu-id="195d0-245">**interface_index**: Index of interface to set the broadcast flag</span></span>
- <span data-ttu-id="195d0-246">**clear_flag**: значение, в которое устанавливается флаг широковещательного режима</span><span class="sxs-lookup"><span data-stu-id="195d0-246">**clear_flag**: Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-247">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-247">Return Values</span></span>

- <span data-ttu-id="195d0-248">**NX_SUCCESS** (0x00) — флаг успешно установлен.</span><span class="sxs-lookup"><span data-stu-id="195d0-248">**NX_SUCCESS**: (0x00) Successfully set flag</span></span>
- <span data-ttu-id="195d0-249">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) — протокол DHCP не включен для интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-249">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="195d0-250">NX_PTR_ERROR (0x16) — недопустимый указатель IP или DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-250">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="195d0-251">NX_INVALID_INTERFACE (0x4C) — недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="195d0-251">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-252">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-252">Allowed From</span></span>

<span data-ttu-id="195d0-253">Потоки, инициализация</span><span class="sxs-lookup"><span data-stu-id="195d0-253">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="195d0-254">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-254">Example</span></span>

```c
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface.  */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated.  */
```

## <a name="nx_dhcp_delete"></a><span data-ttu-id="195d0-255">nx_dhcp_delete</span><span class="sxs-lookup"><span data-stu-id="195d0-255">nx_dhcp_delete</span></span>

<span data-ttu-id="195d0-256">Удаление экземпляра DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-256">Delete a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-257">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-257">Prototype</span></span>

```c
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="195d0-258">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-258">Description</span></span>

<span data-ttu-id="195d0-259">Эта служба удаляет ранее созданный экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-259">This service deletes a previously created DHCP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-260">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-260">Input Parameters</span></span>

- <span data-ttu-id="195d0-261">**dhcp_ptr**: указатель на ранее созданный экземпляр DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-261">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-262">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-262">Return Values</span></span>

- <span data-ttu-id="195d0-263">**NX_SUCCESS** (0x00) — экземпляр DHCP успешно удален.</span><span class="sxs-lookup"><span data-stu-id="195d0-263">**NX_SUCCESS**: (0x00) Successful DHCP delete.</span></span>
- <span data-ttu-id="195d0-264">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-264">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="195d0-265">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-265">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-266">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-266">Allowed From</span></span>

<span data-ttu-id="195d0-267">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-268">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-268">Example</span></span>

```c
/* Delete a DHCP instance.  */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted.  */
```

## <a name="nx_dhcp_-force_renew"></a><span data-ttu-id="195d0-269">nx_dhcp_force_renew</span><span class="sxs-lookup"><span data-stu-id="195d0-269">nx_dhcp_ force_renew</span></span>

<span data-ttu-id="195d0-270">Отправка сообщения о принудительном обновлении</span><span class="sxs-lookup"><span data-stu-id="195d0-270">Send a force renew message</span></span> 

### <a name="prototype"></a><span data-ttu-id="195d0-271">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-271">Prototype</span></span>

```c
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="195d0-272">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-272">Description</span></span>

<span data-ttu-id="195d0-273">Эта служба позволяет ведущему приложению отправлять сообщение о принудительном обновлении для всех интерфейсов, для которых включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-273">This service enables the host application to send a force renew message on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="195d0-274">Клиент DHCP должен находиться в состоянии ПРИВЯЗКИ.</span><span class="sxs-lookup"><span data-stu-id="195d0-274">The DHCP Client must be in a BOUND state.</span></span> <span data-ttu-id="195d0-275">Эта функция устанавливает состояние RENEW, чтобы клиент DHCP пытался выполнить обновление до истечения времени ожидания T1.</span><span class="sxs-lookup"><span data-stu-id="195d0-275">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

<span data-ttu-id="195d0-276">Чтобы отправить сообщение о принудительном обновлении на определенный интерфейс, когда протокол DHCP включен для нескольких интерфейсов, используйте *nx_dhcp_interface_force_renew*.</span><span class="sxs-lookup"><span data-stu-id="195d0-276">To send a force renew on a specific interface when multiple interfaces are DHCP-enabled, use *nx_dhcp_interface_force_renew*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-277">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-277">Input Parameters</span></span>

- <span data-ttu-id="195d0-278">**dhcp_ptr**: указатель на ранее созданный экземпляр DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-278">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-279">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-279">Return Values</span></span>

- <span data-ttu-id="195d0-280">**NX_SUCCESS** (0x00) — сообщение о принудительном обновлении успешно отправлено.</span><span class="sxs-lookup"><span data-stu-id="195d0-280">**NX_SUCCESS**: (0x00) Successfully sent force renew.</span></span>
- <span data-ttu-id="195d0-281">**NX_DHCP_NOT_BOUND** (0x94) — IP-адрес клиента не привязан.</span><span class="sxs-lookup"><span data-stu-id="195d0-281">**NX_DHCP_NOT_BOUND**: (0x94) Client IP address not bound.</span></span>  
- <span data-ttu-id="195d0-282">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-282">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="195d0-283">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-283">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-284">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-284">Allowed From</span></span>

<span data-ttu-id="195d0-285">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-285">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-286">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-286">Example</span></span>

```c
/* Send a force renew message from the Client.  */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired.  */
```

## <a name="nx_dhcp_interface_force_renew"></a><span data-ttu-id="195d0-287">nx_dhcp_interface_force_renew</span><span class="sxs-lookup"><span data-stu-id="195d0-287">nx_dhcp_interface_force_renew</span></span>

<span data-ttu-id="195d0-288">Отправка сообщения о принудительном обновлении на указанный интерфейс</span><span class="sxs-lookup"><span data-stu-id="195d0-288">Send a force renew message on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-289">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-289">Prototype</span></span>

```c
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr, 
                                   UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="195d0-290">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-290">Description</span></span>

<span data-ttu-id="195d0-291">Эта служба позволяет ведущему приложению отправлять сообщение о принудительном обновлении на указанный интерфейс, если для него включен протокол DHCP (см. описание службы *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="195d0-291">This service enables the host application to send a force renew message on the input interface as long as that interface has been enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="195d0-292">Клиент DHCP в указанном интерфейсе должен находиться в состоянии ПРИВЯЗКИ.</span><span class="sxs-lookup"><span data-stu-id="195d0-292">The DHCP Client on the specified interface must be in a BOUND state.</span></span> <span data-ttu-id="195d0-293">Эта функция устанавливает состояние RENEW, чтобы клиент DHCP пытался выполнить обновление до истечения времени ожидания T1.</span><span class="sxs-lookup"><span data-stu-id="195d0-293">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-294">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-294">Input Parameters</span></span>

- <span data-ttu-id="195d0-295">**dhcp_ptr**: указатель на ранее созданный экземпляр DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-295">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-296">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-296">Return Values</span></span>

- <span data-ttu-id="195d0-297">**NX_SUCCESS** (0x00) — сообщение о принудительном обновлении успешно отправлено.</span><span class="sxs-lookup"><span data-stu-id="195d0-297">**NX_SUCCESS**: (0x00) Successfully sent force renew.</span></span>  
- <span data-ttu-id="195d0-298">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) — протокол DHCP не включен для интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-298">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="195d0-299">NX_PTR_ERROR (0x16) — недопустимый указатель IP или DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-299">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="195d0-300">NX_INVALID_INTERFACE (0x4C) — недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="195d0-300">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-301">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-301">Allowed From</span></span>

<span data-ttu-id="195d0-302">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-302">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-303">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-303">Example</span></span>

```c
/* Send a force renew message to the server on interface 1.  */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);


/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired.  */
```

## <a name="nx_dhcp_packet_pool_set"></a><span data-ttu-id="195d0-304">nx_dhcp_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="195d0-304">nx_dhcp_packet_pool_set</span></span>

<span data-ttu-id="195d0-305">Задание пула пакетов клиента DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-305">Set the DHCP Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-306">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-306">Prototype</span></span>

```c
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr, NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="195d0-307">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-307">Description</span></span>

<span data-ttu-id="195d0-308">Эта служба позволяет приложению создать пул пакетов клиента DHCP путем передачи указателя на ранее созданный пул пакетов в этом вызове службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-308">This service allows the application to create the DHCP Client packet pool by passing in a pointer to a previously created packet pool in this service call.</span></span> <span data-ttu-id="195d0-309">Чтобы использовать эту функцию, ведущее приложение должно задать параметр NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="195d0-309">To use this feature, the host application must define NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span></span> <span data-ttu-id="195d0-310">Если этот параметр определен, служба *nx_dhcp_create* не создаст пул пакетов клиента.</span><span class="sxs-lookup"><span data-stu-id="195d0-310">When defined, the *nx_dhcp_create* service will not create the Client’s packet pool.</span></span> 

>[!NOTE] 
> <span data-ttu-id="195d0-311">В приложении рекомендуется использовать значения по умолчанию для полезных данных пула пакетов клиента DHCP, которые определяются в параметре NX_DHCP_PACKET_PAYLOAD в файле *nxd_dhcp_client.h* при создании пула пакетов.</span><span class="sxs-lookup"><span data-stu-id="195d0-311">The application is recommended to use the default values for the DHCP client packet pool payload, defined as NX_DHCP_PACKET_PAYLOAD in *nxd_dhcp_client.h* when creating the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-312">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-312">Input Parameters</span></span>

- <span data-ttu-id="195d0-313">**dhcp_ptr**: указатель на блок управления DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-313">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="195d0-314">**packet_pool_ptr**: указатель на ранее созданный пул пакетов</span><span class="sxs-lookup"><span data-stu-id="195d0-314">**packet_pool_ptr**: Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-315">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-315">Return Values</span></span>

- <span data-ttu-id="195d0-316">**NX_SUCCESS** (0x00) — пул пакетов клиента DHCP задан.</span><span class="sxs-lookup"><span data-stu-id="195d0-316">**NX_SUCCESS**: (0x00) DHCP Client packet pool is set</span></span>
- <span data-ttu-id="195d0-317">**NX_NOT_ENABLED** (0x14) — служба не включена.</span><span class="sxs-lookup"><span data-stu-id="195d0-317">**NX_NOT_ENABLED**: (0x14) Service is not enabled</span></span>
- <span data-ttu-id="195d0-318">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-318">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="195d0-319">NX_DHCP_INVALID_PAYLOAD (0x9C) — полезные данные слишком малы.</span><span class="sxs-lookup"><span data-stu-id="195d0-319">NX_DHCP_INVALID_PAYLOAD: (0x9C) Payload is too small</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-320">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-320">Allowed From</span></span>

<span data-ttu-id="195d0-321">Код приложения</span><span class="sxs-lookup"><span data-stu-id="195d0-321">Application code</span></span>

### <a name="example"></a><span data-ttu-id="195d0-322">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-322">Example</span></span>

```c
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
                                 NX_DHCP_PACKET_PAYLOAD, pointer, 
                                 (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool.  */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set.  */

```

## <a name="nx_dhcp_request_client_ip"></a><span data-ttu-id="195d0-323">nx_dhcp_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="195d0-323">nx_dhcp_request_client_ip</span></span>

<span data-ttu-id="195d0-324">Задание запрошенного IP-адреса для экземпляра DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-324">Set requested IP address for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-325">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-325">Prototype</span></span>

```c
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr, 
                               ULONG client_ip_address, 
                               UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="195d0-326">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-326">Description</span></span>

<span data-ttu-id="195d0-327">Эта служба настраивает запрос IP-адреса клиента DHCP с DHCP-сервера через первый интерфейс, для которого включен протокол DHCP в записи клиента DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-327">This service sets the IP address for the DHCP Client to request from the DHCP Server on the first interface enabled for DHCP in the DHCP Client record.</span></span> <span data-ttu-id="195d0-328">Если установлен флаг *skip_discover_message*, клиент DHCP пропускает сообщение об обнаружении и отправляет сообщение запроса.</span><span class="sxs-lookup"><span data-stu-id="195d0-328">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

<span data-ttu-id="195d0-329">Чтобы настроить запрос определенного IP-адреса для сообщений DHCP через определенный интерфейс, используйте службу *nx_dhcp_interface_request_client_ip*.</span><span class="sxs-lookup"><span data-stu-id="195d0-329">To set the request for a specific IP for DHCP messages on a specific interface, use the *nx_dhcp_interface_request_client_ip* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-330">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-330">Input Parameters</span></span>

- <span data-ttu-id="195d0-331">**dhcp_ptr**: указатель на блок управления DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-331">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="195d0-332">**client_ip_address**: IP-адрес, запрашиваемый с DHCP-сервера</span><span class="sxs-lookup"><span data-stu-id="195d0-332">**client_ip_address**: IP address to request from DHCP server</span></span>
- <span data-ttu-id="195d0-333">**skip_discover_message**:</span><span class="sxs-lookup"><span data-stu-id="195d0-333">**skip_discover_message**:</span></span> 
    - <span data-ttu-id="195d0-334">если значение равно true, клиент DHCP отправляет сообщение запроса;</span><span class="sxs-lookup"><span data-stu-id="195d0-334">If true, DHCP Client sends Request message</span></span>
    - <span data-ttu-id="195d0-335">если значение равно false, отправляется сообщение об обнаружении</span><span class="sxs-lookup"><span data-stu-id="195d0-335">If false, it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-336">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-336">Return Values</span></span>

- <span data-ttu-id="195d0-337">**NX_SUCCESS** (0x00) — запрошенный IP-адрес задан.</span><span class="sxs-lookup"><span data-stu-id="195d0-337">**NX_SUCCESS**: (0x00) Requested IP address is set.</span></span>
- <span data-ttu-id="195d0-338">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-338">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="195d0-339">NX_DHCP_INVALID_IP_REQUEST (0x9D) — запрошен IP-адрес со значением NULL.</span><span class="sxs-lookup"><span data-stu-id="195d0-339">NX_DHCP_INVALID_IP_REQUEST: (0x9D) NULL IP address requested</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-340">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-340">Allowed From</span></span>

<span data-ttu-id="195d0-341">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-341">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-342">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-342">Example</span></span>

```c
/* Set the DHCP Client requested IP address and skip the discover message.  */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set.  */

```

## <a name="nx_dhcp_interface_request_client_ip"></a><span data-ttu-id="195d0-343">nx_dhcp_interface_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="195d0-343">nx_dhcp_interface_request_client_ip</span></span>

<span data-ttu-id="195d0-344">Задание запрошенного IP-адреса для экземпляра DHCP в указанном интерфейсе</span><span class="sxs-lookup"><span data-stu-id="195d0-344">Set requested IP address for DHCP instance on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-345">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-345">Prototype</span></span>

```c
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr, UINT  interface_index, 
                                         ULONG client_ip_address, UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="195d0-346">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-346">Description</span></span>

<span data-ttu-id="195d0-347">Эта служба настраивает запрос IP-адреса клиента DHCP с DHCP-сервера через указанный интерфейс, если для него включен протокол DHCP (см. описание службы *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="195d0-347">This service sets the IP address for the DHCP Client to request from the DHCP Server on the specified interface, if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="195d0-348">Если установлен флаг *skip_discover_message*, клиент DHCP пропускает сообщение об обнаружении и отправляет сообщение запроса.</span><span class="sxs-lookup"><span data-stu-id="195d0-348">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-349">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-349">Input Parameters</span></span>

- <span data-ttu-id="195d0-350">**dhcp_ptr**: указатель на блок управления DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-350">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="195d0-351">**Interface_index**: индекс интерфейса для запроса IP-адреса</span><span class="sxs-lookup"><span data-stu-id="195d0-351">**Interface_index**: Index of interface to request IP address on</span></span>
- <span data-ttu-id="195d0-352">**client_ip_address**: IP-адрес, запрашиваемый с DHCP-сервера</span><span class="sxs-lookup"><span data-stu-id="195d0-352">**client_ip_address**: IP address to request from DHCP server</span></span>
- <span data-ttu-id="195d0-353">**skip_discover_message** — если задано значение true, клиент DHCP отправляет сообщение запроса; в противном случае отправляется сообщение об обнаружении</span><span class="sxs-lookup"><span data-stu-id="195d0-353">**skip_discover_message**: If true, DHCP Client sends Request message; else it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-354">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-354">Return Values</span></span>

- <span data-ttu-id="195d0-355">**NX_SUCCESS** (0x00) — запрошенный IP-адрес задан.</span><span class="sxs-lookup"><span data-stu-id="195d0-355">**NX_SUCCESS**: (0x00) Requested IP address is set.</span></span>
- <span data-ttu-id="195d0-356">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) — протокол DHCP не включен для интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-356">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="195d0-357">NX_PTR_ERROR (0x16) — недопустимый указатель IP или DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-357">NX_PTR_ERROR: (0x16) Invalid IP or DHCP pointer</span></span>
- <span data-ttu-id="195d0-358">NX_INVALID_INTERFACE (0x4C) — недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="195d0-358">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-359">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-359">Allowed From</span></span>

<span data-ttu-id="195d0-360">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-360">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-361">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-361">Example</span></span>

```c
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0.  */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set.  */
```

## <a name="nx_dhcp_reinitialize"></a><span data-ttu-id="195d0-362">nx_dhcp_reinitialize</span><span class="sxs-lookup"><span data-stu-id="195d0-362">nx_dhcp_reinitialize</span></span>

<span data-ttu-id="195d0-363">Сброс параметров сети клиента DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-363">Clear the DHCP client network parameters</span></span> 

### <a name="prototype"></a><span data-ttu-id="195d0-364">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-364">Prototype</span></span>

```c
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="195d0-365">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-365">Description</span></span>

<span data-ttu-id="195d0-366">Эта служба сбрасывает параметры сети ведущего приложения (IP-адрес, сетевой адрес и маску сети) и очищает состояние клиента DHCP во всех интерфейсах, для которых включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-366">This service clears the host application network parameters (IP address, network address and network mask), and clears the DHCP Client state on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="195d0-367">Она используется в сочетании с *nx_dhcp_stop* и *nx_dhcp_start* для перезапуска конечного автомата DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-367">It is used in combination with *nx_dhcp_stop* and *nx_dhcp_start* to ‘restart’ the DHCP state machine:</span></span>

```c
nx_dhcp_stop(&my_dhcp);
nx_dhcp_reinitialize(&my_dhcp);
nx_dhcp_start(&my_dhcp);
```

<span data-ttu-id="195d0-368">Для повторной инициализации клиента DHCP на определенном интерфейсе, когда протокол DHCP включен для нескольких интерфейсов, используйте службу *nx_dhcp_interface_reinitialize*.</span><span class="sxs-lookup"><span data-stu-id="195d0-368">To reinitialize the DHCP Client on a specific interface when multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_reinitialize* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-369">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-369">Input Parameters</span></span>

- <span data-ttu-id="195d0-370">**dhcp_ptr**: указатель на ранее созданный экземпляр DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-370">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-371">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-371">Return Values</span></span>

- <span data-ttu-id="195d0-372">**NX_SUCCESS** (0x00) — протокол DHCP инициализирован повторно.</span><span class="sxs-lookup"><span data-stu-id="195d0-372">**NX_SUCCESS**: (0x00) DHCP successfully reinitialized</span></span> 
- <span data-ttu-id="195d0-373">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-373">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-374">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-374">Allowed From</span></span>

<span data-ttu-id="195d0-375">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-375">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-376">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-376">Example</span></span>

```c
/* Reinitialize the previously started DHCP client.  */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a><span data-ttu-id="195d0-377">nx_dhcp_interface_reinitialize</span><span class="sxs-lookup"><span data-stu-id="195d0-377">nx_dhcp_interface_reinitialize</span></span>

<span data-ttu-id="195d0-378">Сброс параметров сети клиента DHCP для указанного интерфейса</span><span class="sxs-lookup"><span data-stu-id="195d0-378">Clear the DHCP client network parameters on the specified interface</span></span> 

### <a name="prototype"></a><span data-ttu-id="195d0-379">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-379">Prototype</span></span>

```c
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr, 
                                     UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="195d0-380">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-380">Description</span></span>

<span data-ttu-id="195d0-381">Эта служба сбрасывает параметры сети (IP-адрес, сетевой адрес и маску сети) для указанного интерфейса, если для него включен протокол DHCP (см. описание службы *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="195d0-381">This service clears the network parameters (IP address, network address and network mask) on the specified interface if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="195d0-382">Дополнительные сведения см. в описании службы *nx_dhcp_reinitialize*.</span><span class="sxs-lookup"><span data-stu-id="195d0-382">See *nx_dhcp_reinitialize* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-383">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-383">Input Parameters</span></span>

- <span data-ttu-id="195d0-384">**dhcp_ptr**: указатель на ранее созданный экземпляр DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-384">**dhcp_ptr**: Pointer to previously created DHCP instance</span></span>
- <span data-ttu-id="195d0-385">**interface_index**: индекс интерфейса, который нужно инициализировать повторно</span><span class="sxs-lookup"><span data-stu-id="195d0-385">**interface_index**: Index of interface to reinitialize</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-386">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-386">Return Values</span></span>

- <span data-ttu-id="195d0-387">**NX_SUCCESS** (0x00) — интерфейс инициализирован повторно.</span><span class="sxs-lookup"><span data-stu-id="195d0-387">**NX_SUCCESS**: (0x00) Interface successfully reinitialized</span></span>
- <span data-ttu-id="195d0-388">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) — протокол DHCP не включен для интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-388">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="195d0-389">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-389">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="195d0-390">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-390">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="195d0-391">NX_INVALID_INTERFACE (0x4C) — недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="195d0-391">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-392">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-392">Allowed From</span></span>

<span data-ttu-id="195d0-393">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-393">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-394">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-394">Example</span></span>

```c
/* Reinitialize the previously started DHCP client on interface 1.  */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a><span data-ttu-id="195d0-395">nx_dhcp_release</span><span class="sxs-lookup"><span data-stu-id="195d0-395">nx_dhcp_release</span></span>

<span data-ttu-id="195d0-396">Освобождение арендованного IP-адреса</span><span class="sxs-lookup"><span data-stu-id="195d0-396">Release Leased IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-397">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-397">Prototype</span></span>

```c
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="195d0-398">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-398">Description</span></span>

<span data-ttu-id="195d0-399">Эта служба освобождает IP-адрес, полученный от DHCP-сервера, отправляя на него сообщение RELEASE.</span><span class="sxs-lookup"><span data-stu-id="195d0-399">This service releases the IP address obtained from a DHCP server by sending the RELEASE message to that server.</span></span> <span data-ttu-id="195d0-400">Затем она повторно инициализирует клиент DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-400">It then reinitializes the DHCP Client.</span></span> <span data-ttu-id="195d0-401">Эта служба применяется ко всем интерфейсам, для которых включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-401">This service is applied to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="195d0-402">Приложение может перезапустить клиент DHCP, вызвав *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="195d0-402">The application can restart the DHCP Client by calling *nx_dhcp_start*.</span></span>

<span data-ttu-id="195d0-403">Чтобы вернуть адрес DHCP-серверу в определенном интерфейсе, используйте службу *nx_dhcp_interface_release*.</span><span class="sxs-lookup"><span data-stu-id="195d0-403">To release an address back to the DHCP server on a specific interface, use the *nx_dhcp_interface_release* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-404">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-404">Input Parameters</span></span>

- <span data-ttu-id="195d0-405">**dhcp_ptr**: указатель на ранее созданный экземпляр DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-405">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-406">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-406">Return Values</span></span>

- <span data-ttu-id="195d0-407">**NX_SUCCESS** (0x00) — успешное освобождение DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-407">**NX_SUCCESS**: (0x00) Successful DHCP release.</span></span>  
- <span data-ttu-id="195d0-408">**NX_DHCP_NOT_BOUND** (0x94) — IP-адрес не был арендован, поэтому его невозможно освободить.</span><span class="sxs-lookup"><span data-stu-id="195d0-408">**NX_DHCP_NOT_BOUND**: (0x94) The IP address has not been leased so it can’t be released.</span></span>
- <span data-ttu-id="195d0-409">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-409">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="195d0-410">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-410">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-411">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-411">Allowed From</span></span>

<span data-ttu-id="195d0-412">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-412">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-413">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-413">Example</span></span>

```c
/* Release the previously leased IP address.  */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released.  */
```

## <a name="nx_dhcp_interface_release"></a><span data-ttu-id="195d0-414">nx_dhcp_interface_release</span><span class="sxs-lookup"><span data-stu-id="195d0-414">nx_dhcp_interface_release</span></span>

<span data-ttu-id="195d0-415">Освобождение IP-адреса в указанном интерфейсе</span><span class="sxs-lookup"><span data-stu-id="195d0-415">Release IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-416">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-416">Prototype</span></span>

```c
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="195d0-417">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-417">Description</span></span>

<span data-ttu-id="195d0-418">Эта служба освобождает IP-адрес, полученный от DHCP-сервера, в указанном интерфейсе и повторно инициализирует клиент DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-418">This service releases the IP address obtained from a DHCP server on the specified interface and reinitializes the DHCP Client.</span></span> <span data-ttu-id="195d0-419">Клиент DHCP можно перезапустить, вызвав *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="195d0-419">The DHCP Client can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-420">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-420">Input Parameters</span></span>

- <span data-ttu-id="195d0-421">**dhcp_ptr**: указатель на ранее созданный экземпляр DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-421">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-422">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-422">Return Values</span></span>

- <span data-ttu-id="195d0-423">**NX_SUCCESS** (0x00) — успешное освобождение DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-423">**NX_SUCCESS**: (0x00) Successful DHCP release.</span></span>
- <span data-ttu-id="195d0-424">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) — протокол DHCP не включен для интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-424">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="195d0-425">**NX_DHCP_NOT_BOUND** (0x94) — IP-адрес не был арендован, поэтому его невозможно освободить.</span><span class="sxs-lookup"><span data-stu-id="195d0-425">**NX_DHCP_NOT_BOUND**: (0x94) The IP address has not been leased so it can’t be released.</span></span>
- <span data-ttu-id="195d0-426">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-426">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="195d0-427">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-427">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="195d0-428">NX_INVALID_INTERFACE (0x4C) — недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="195d0-428">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-429">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-429">Allowed From</span></span>

<span data-ttu-id="195d0-430">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-430">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-431">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-431">Example</span></span>

```c
/* Release the previously leased IP address on interface 1.  */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released.  */
```

## <a name="nx_dhcp_decline"></a><span data-ttu-id="195d0-432">nx_dhcp_decline</span><span class="sxs-lookup"><span data-stu-id="195d0-432">nx_dhcp_decline</span></span>

<span data-ttu-id="195d0-433">Отклонение IP-адреса от DHCP-сервера</span><span class="sxs-lookup"><span data-stu-id="195d0-433">Decline IP address from DHCP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-434">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-434">Prototype</span></span>

```c
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="195d0-435">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-435">Description</span></span>

<span data-ttu-id="195d0-436">Эта служба отклоняет IP-адрес, арендованный у DHCP-сервера, во всех интерфейсах, для которых включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-436">This service declines an IP address leased from the DHCP server on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="195d0-437">Когда задан параметр NX_DHCP_CLIENT_SEND_ARP_PROBE, клиент DHCP отправляет сообщение DECLINE, если обнаруживает, что IP-адрес уже занят.</span><span class="sxs-lookup"><span data-stu-id="195d0-437">If NX_DHCP_CLIENT_ SEND_ ARP_PROBE is defined, the DHCP Client will send a DECLINE message if it detects that the IP address is already in use.</span></span> <span data-ttu-id="195d0-438">Дополнительные сведения о настройке проверки ARP в клиенте DHCP NetX Duo см. в разделе **Проверки ARP** главы 1.</span><span class="sxs-lookup"><span data-stu-id="195d0-438">See **ARP Probes** in Chapter One for more information on ARP probe configuration in the NetX Duo DHCP Client.</span></span>

<span data-ttu-id="195d0-439">Приложение может использовать эту службу для отклонения IP-адреса, если обнаруживает, что адрес используется иным образом.</span><span class="sxs-lookup"><span data-stu-id="195d0-439">The application can use this service to decline its IP address if it discovers the address is in use by other means.</span></span>

<span data-ttu-id="195d0-440">Эта служба повторно инициализирует клиент DHCP, чтобы его можно было перезапустить, вызвав *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="195d0-440">This service reinitializes the DHCP Client to that it can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-441">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-441">Input Parameters</span></span>

- <span data-ttu-id="195d0-442">**dhcp_ptr**: указатель на ранее созданный экземпляр DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-442">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-443">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-443">Return Values</span></span>

- <span data-ttu-id="195d0-444">**NX_SUCCESS** (0x00) — отклонение успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="195d0-444">**NX_SUCCESS**: (0x00) Decline successfully sent</span></span>  
- <span data-ttu-id="195d0-445">**NX_DHCP_NOT_BOUND** (0x94) — клиент DHCP не привязан.</span><span class="sxs-lookup"><span data-stu-id="195d0-445">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="195d0-446">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-446">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="195d0-447">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-447">NX_CALLER_ERROR: (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-448">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-448">Allowed From</span></span>

<span data-ttu-id="195d0-449">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-449">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-450">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-450">Example</span></span>

```c

/* Decline the IP address offered by the DHCP server.  */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was successfully trasnmitted.  */
```

## <a name="nx_dhcp_interface_decline"></a><span data-ttu-id="195d0-451">nx_dhcp_interface_decline</span><span class="sxs-lookup"><span data-stu-id="195d0-451">nx_dhcp_interface_decline</span></span>

<span data-ttu-id="195d0-452">Отклонение IP-адреса от DHCP-сервера в указанном интерфейсе</span><span class="sxs-lookup"><span data-stu-id="195d0-452">Decline IP address from DHCP Server on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-453">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-453">Prototype</span></span>

```c
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr, 
                               UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="195d0-454">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-454">Description</span></span>

<span data-ttu-id="195d0-455">Эта служба отправляет сообщение DECLINE на сервер, чтобы отклонить IP-адрес, назначенный DHCP-сервером.</span><span class="sxs-lookup"><span data-stu-id="195d0-455">This service sends the DECLINE message to the server to decline an IP address assigned by the DHCP server.</span></span> <span data-ttu-id="195d0-456">Она также повторно инициализирует клиент DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-456">It also reinitializes the DHCP Client.</span></span> <span data-ttu-id="195d0-457">Дополнительные сведения см. в описании службы *nx_dhcp_decline*.</span><span class="sxs-lookup"><span data-stu-id="195d0-457">See *nx_dhcp_decline* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-458">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-458">Input Parameters</span></span>

- <span data-ttu-id="195d0-459">**dhcp_ptr**: указатель на ранее созданный экземпляр DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-459">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="195d0-460">**Interface_index**: индекс интерфейса для отклонения IP-адреса</span><span class="sxs-lookup"><span data-stu-id="195d0-460">**Interface_index**: Index of interface to decline IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-461">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-461">Return Values</span></span>

- <span data-ttu-id="195d0-462">**NX_SUCCESS** (0x00) — отправлено сообщение об отклонении DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-462">**NX_SUCCESS**: (0x00) DHCP decline message sent</span></span>  
- <span data-ttu-id="195d0-463">**NX_DHCP_NOT_BOUND** (0x94) — клиент DHCP не привязан.</span><span class="sxs-lookup"><span data-stu-id="195d0-463">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="195d0-464">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) — протокол DHCP не включен для интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-464">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="195d0-465">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-465">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="195d0-466">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-466">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="195d0-467">NX_INVALID_INTERFACE (0x4C) — недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="195d0-467">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-468">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-468">Allowed From</span></span>

<span data-ttu-id="195d0-469">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-469">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-470">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-470">Example</span></span>

```c
/* Decline the IP address offered by the DHCP server on interface 2.  */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was successfully trasnmitted.  */
```
## <a name="nx_dhcp_send_request"></a><span data-ttu-id="195d0-471">nx_dhcp_send_request</span><span class="sxs-lookup"><span data-stu-id="195d0-471">nx_dhcp_send_request</span></span>

<span data-ttu-id="195d0-472">Отправка сообщения DHCP на сервер</span><span class="sxs-lookup"><span data-stu-id="195d0-472">Send DHCP message to Server</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-473">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-473">Prototype</span></span>

```c
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);

```

### <a name="description"></a><span data-ttu-id="195d0-474">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-474">Description</span></span>

<span data-ttu-id="195d0-475">Эта служба отправляет указанное сообщение DHCP на DHCP-сервер через первый интерфейс с включенным протоколом DHCP, найденный в записи клиента DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-475">This service sends the specified DHCP message to the DHCP server on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="195d0-476">Чтобы отправить сообщение RELEASE или DECLINE, приложение должно использовать службу *nx_dhcp[_interface]_release*() или *nx_dhcp_interface_decline()* соответственно.</span><span class="sxs-lookup"><span data-stu-id="195d0-476">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="195d0-477">Для использования этой службы клиент DHCP должен быть запущен, за исключением отправки сообщений типа INFORM_REQUEST.</span><span class="sxs-lookup"><span data-stu-id="195d0-477">The DHCP Client must be started to use this service except for sending the INFORM_REQUEST message type.</span></span>

>[!NOTE]
> <span data-ttu-id="195d0-478">Эта служба не предназначена для запуска конечного автомата клиента DHCP ведущим приложением.</span><span class="sxs-lookup"><span data-stu-id="195d0-478">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-479">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-479">Input Parameters</span></span>

- <span data-ttu-id="195d0-480">**dhcp_ptr**: указатель на блок управления DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-480">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="195d0-481">**dhcp_message_type**: запрос сообщения (определен в *nxd_dhcp_client.h*)</span><span class="sxs-lookup"><span data-stu-id="195d0-481">**dhcp_message_type**: Message request (defined in *nxd_dhcp_client.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-482">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-482">Return Values</span></span>

- <span data-ttu-id="195d0-483">**NX_SUCCESS** (0x00) — сообщений DHCP отправлено.</span><span class="sxs-lookup"><span data-stu-id="195d0-483">**NX_SUCCESS**: (0x00) DHCP message sent</span></span>  
- <span data-ttu-id="195d0-484">**NX_DHCP_NOT_STARTED** (0x96) — недопустимый индекс интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-484">**NX_DHCP_NOT_STARTED**: (0x96) Invalid interface index</span></span>
- <span data-ttu-id="195d0-485">**NX_DHCP_INVALID_MESSAGE** (0x9B) — недопустимый тип отправляемого сообщения.</span><span class="sxs-lookup"><span data-stu-id="195d0-485">**NX_DHCP_INVALID_MESSAGE**: (0x9B) Invalid message type to send</span></span>
- <span data-ttu-id="195d0-486">NX_PTR_ERROR (0x16) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="195d0-486">NX_PTR_ERROR: (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-487">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-487">Allowed From</span></span>

<span data-ttu-id="195d0-488">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-488">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-489">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-489">Example</span></span>

```c
/* Send the DHCP INFORM REQUEST message to the server.  */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent.  */
```

## <a name="nx_dhcp_interface_send_request"></a><span data-ttu-id="195d0-490">nx_dhcp_interface_send_request</span><span class="sxs-lookup"><span data-stu-id="195d0-490">nx_dhcp_interface_send_request</span></span>

<span data-ttu-id="195d0-491">Отправка сообщения DHCP на сервер через указанный интерфейс</span><span class="sxs-lookup"><span data-stu-id="195d0-491">Send DHCP message to Server on a specific interface</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-492">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-492">Prototype</span></span>

```c
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr, 
                                    UINT interface_index, 
                                    UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="195d0-493">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-493">Description</span></span>

<span data-ttu-id="195d0-494">Эта служба отправляет сообщение на DHCP-сервер через указанный интерфейс, если для него включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-494">This service sends a message to the DHCP server on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="195d0-495">Чтобы отправить сообщение RELEASE или DECLINE, приложение должно использовать службу *nx_dhcp[_interface]_release*() или *nx_dhcp_interface_decline()* соответственно.</span><span class="sxs-lookup"><span data-stu-id="195d0-495">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="195d0-496">Для использования этой службы клиент DHCP должен быть запущен, за исключением отправки сообщений DHCP типа INFORM_REQUEST.</span><span class="sxs-lookup"><span data-stu-id="195d0-496">The DHCP Client must be started to use this service except for sending the DHCP INFORM REQUEST message type.</span></span>

<span data-ttu-id="195d0-497">Эта служба не предназначена для запуска конечного автомата клиента DHCP ведущим приложением.</span><span class="sxs-lookup"><span data-stu-id="195d0-497">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-498">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-498">Input Parameters</span></span>

- <span data-ttu-id="195d0-499">**dhcp_ptr**: указатель на блок управления DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-499">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="195d0-500">**Interface_index**: индекс интерфейса для отправки сообщения</span><span class="sxs-lookup"><span data-stu-id="195d0-500">**Interface_index**: Index of interface to send message on</span></span>
- <span data-ttu-id="195d0-501">**dhcp_message_type**: запрос сообщения (определен в nxd_dhcp_client.h)</span><span class="sxs-lookup"><span data-stu-id="195d0-501">**dhcp_message_type**: Message request (defined in nxd_dhcp_client.h)</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-502">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-502">Return Values</span></span>

- <span data-ttu-id="195d0-503">**NX_SUCCESS** (0x00) — сообщений DHCP отправлено.</span><span class="sxs-lookup"><span data-stu-id="195d0-503">**NX_SUCCESS**: (0x00) DHCP message sent</span></span>  
- <span data-ttu-id="195d0-504">**NX_DHCP_NOT_STARTED** (0x96) — недопустимый индекс интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-504">**NX_DHCP_NOT_STARTED**: (0x96) Invalid interface index</span></span>
- <span data-ttu-id="195d0-505">**NX_DHCP_INVALID_MESSAGE** (0x9B) — недопустимый тип отправляемого сообщения.</span><span class="sxs-lookup"><span data-stu-id="195d0-505">**NX_DHCP_INVALID_MESSAGE**: (0x9B) Invalid message type to send</span></span>
- <span data-ttu-id="195d0-506">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) — протокол DHCP не включен для интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-506">**NX_DHCP_INTERFACE_NOT_ENABLED**: (0xA4) Interface not enabled for DHCP</span></span>
- <span data-ttu-id="195d0-507">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-507">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="195d0-508">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-508">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="195d0-509">NX_INVALID_INTERFACE (0x4C) — недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="195d0-509">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-510">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-510">Allowed From</span></span>

<span data-ttu-id="195d0-511">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-511">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-512">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-512">Example</span></span>

```c
/* Send the INFORM REQUEST message to the server on the primary interface.  */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent.  */
```

## <a name="nx_dhcp_server_address_get"></a><span data-ttu-id="195d0-513">nx_dhcp_server_address_get</span><span class="sxs-lookup"><span data-stu-id="195d0-513">nx_dhcp_server_address_get</span></span>

<span data-ttu-id="195d0-514">Получение IP-адреса DHCP-сервера для клиента DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-514">Get the DHCP Client’s DHCP server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-515">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-515">Prototype</span></span>

```c
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr, 
                                ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="195d0-516">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-516">Description</span></span>

<span data-ttu-id="195d0-517">Эта служба получает IP-адрес DHCP-сервера для клиента DHCP через первый интерфейс с включенным протоколом DHCP, найденный в записи клиента DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-517">This service retrieves the DHCP Client DHCP server IP address on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="195d0-518">Вызывающая сторона может использовать эту службу только после привязки клиента DHCP к IP-адресу, назначенному DHCP-сервером.</span><span class="sxs-lookup"><span data-stu-id="195d0-518">The caller can only use this service after the DHCP Client is bound to an IP address assigned by the DHCP Server.</span></span> <span data-ttu-id="195d0-519">Ведущее приложение может использовать службу *nx_ip_status_check* для проверки того, задан ли IP-адрес, или использовать nx *_dhcp_state_change_notify* и проверить, находится ли клиент DHCP в состоянии NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="195d0-519">The host application can use the *nx_ip_status_check* service to verify IP address is set, or it can use the nx *_dhcp_state_change_notify* and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="195d0-520">Дополнительные сведения о настройке функции обратного вызова для изменения состояния см. в описании функции *nx_dhcp_state_change_notify*.</span><span class="sxs-lookup"><span data-stu-id="195d0-520">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

<span data-ttu-id="195d0-521">Чтобы найти DHCP-сервер в определенном интерфейсе, когда для клиента DHCP включено несколько интерфейсов, используйте службу *nx_dhcp_interface_server_address_get*.</span><span class="sxs-lookup"><span data-stu-id="195d0-521">To find the DHCP server on a specific interface when multiple interfaces are enabled for DHCP Client, use the *nx_dhcp_interface_server_address_get* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-522">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-522">Input Parameters</span></span>

- <span data-ttu-id="195d0-523">**dhcp_ptr**: указатель на блок управления DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-523">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="195d0-524">**server_address**: указатель на IP-адрес сервера</span><span class="sxs-lookup"><span data-stu-id="195d0-524">**server_address**: Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-525">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-525">Return Values</span></span>

- <span data-ttu-id="195d0-526">**NX_SUCCESS** (0x00) — адрес DHCP-сервера возвращен.</span><span class="sxs-lookup"><span data-stu-id="195d0-526">**NX_SUCCESS**: (0x00) DHCP server address returned</span></span>
- <span data-ttu-id="195d0-527">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) — протокол DHCP не включен ни для одного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-527">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="195d0-528">NX_PTR_ERROR (0x16) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="195d0-528">NX_PTR_ERROR: (0x16) Invalid input pointer</span></span>
- <span data-ttu-id="195d0-529">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-529">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-530">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-530">Allowed From</span></span>

<span data-ttu-id="195d0-531">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-531">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-532">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-532">Example</span></span>

```c
/* Use the state change notify service to determine the Client transition to the bound state and get its DHCP server IP address.*/

void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{
ULONG server_address;
UINT  status;

/* Increment state changes counter.  */
state_changes++;

if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
        {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
        }

}
```

## <a name="nx_dhcp_interface_server_address_get"></a><span data-ttu-id="195d0-533">nx_dhcp_interface_server_address_get</span><span class="sxs-lookup"><span data-stu-id="195d0-533">nx_dhcp_interface_server_address_get</span></span>

<span data-ttu-id="195d0-534">Получение IP-адреса DHCP-сервера для клиента DHCP в указанном интерфейсе</span><span class="sxs-lookup"><span data-stu-id="195d0-534">Get the DHCP Client’s DHCP server IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-535">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-535">Prototype</span></span>

```c
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr, 
                                          UINT interface_index,
                                          ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="195d0-536">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-536">Description</span></span>

<span data-ttu-id="195d0-537">Эта служба получает IP-адрес DHCP-сервера для клиента DHCP в указанном интерфейсе, если для него включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-537">This service retrieves the DHCP Client DHCP server IP address on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="195d0-538">Клиент DHCP должен находиться в состоянии привязки.</span><span class="sxs-lookup"><span data-stu-id="195d0-538">The DHCP Client must be in the Bound state.</span></span> <span data-ttu-id="195d0-539">После запуска клиента DHCP в этом интерфейсе ведущее приложение может либо использовать службу *nx_ip_status_check*, чтобы проверить, задан ли IP-адрес, либо использовать обратный вызов для изменения состояния клиента DHCP и проверить, находится ли клиент DHCP в состоянии NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="195d0-539">After starting the DHCP Client on that interface, the host application can either use the *nx_ip_status_check* service to verify the IP address is set, or it can use the DHCP Client state change callback and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="195d0-540">Дополнительные сведения о настройке функции обратного вызова для изменения состояния см. в описании функции *nx_dhcp_state_change_notify*.</span><span class="sxs-lookup"><span data-stu-id="195d0-540">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-541">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-541">Input Parameters</span></span>

- <span data-ttu-id="195d0-542">**dhcp_ptr**: указатель на блок управления DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-542">**dhcp_ptr**: Pointer to DHCP control block.</span></span>
- <span data-ttu-id="195d0-543">**Interface_index**: индекс интерфейса для получения IP-адреса</span><span class="sxs-lookup"><span data-stu-id="195d0-543">**Interface_index**: Index of interface to obtain IP address</span></span>
- <span data-ttu-id="195d0-544">**server_address**: указатель на IP-адрес сервера</span><span class="sxs-lookup"><span data-stu-id="195d0-544">**server_address**: Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-545">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-545">Return Values</span></span>

- <span data-ttu-id="195d0-546">**NX_SUCCESS** (0x00) — адрес DHCP-сервера возвращен.</span><span class="sxs-lookup"><span data-stu-id="195d0-546">**NX_SUCCESS**: (0x00) DHCP server address returned</span></span>
- <span data-ttu-id="195d0-547">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) — протокол DHCP не включен ни для одного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-547">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="195d0-548">**NX_DHCP_NOT_BOUND** (0x94) — клиент DHCP не привязан.</span><span class="sxs-lookup"><span data-stu-id="195d0-548">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound</span></span>
- <span data-ttu-id="195d0-549">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-549">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>
- <span data-ttu-id="195d0-550">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-550">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="195d0-551">NX_INVALID_INTERFACE (0x4C) — недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="195d0-551">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-552">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-552">Allowed From</span></span>

<span data-ttu-id="195d0-553">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-553">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-554">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-554">Example</span></span>

```c
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. */

void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter.  */
state_changes++;

/* Get the DHCP server IP address on interface 1 */
if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
        {
         status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                       &server_address);
        }
}
```

## <a name="nx_dhcp_set_interface_index"></a><span data-ttu-id="195d0-555">nx_dhcp_set_interface_index</span><span class="sxs-lookup"><span data-stu-id="195d0-555">nx_dhcp_set_interface_index</span></span>

<span data-ttu-id="195d0-556">Задание сетевого интерфейса для экземпляра DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-556">Set network interface for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-557">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-557">Prototype</span></span>

```c
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a><span data-ttu-id="195d0-558">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-558">Description</span></span>

<span data-ttu-id="195d0-559">Эта служба задает сетевой интерфейс для подключения экземпляра DHCP к DHCP-серверу, когда для клиента DHCP настроен один сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="195d0-559">This service sets the network interface for the DHCP instance to connect to the DHCP Server on when running DHCP Client configured for a single network interface.</span></span>

<span data-ttu-id="195d0-560">По умолчанию клиент DHCP выполняется на основном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="195d0-560">By default the DHCP Client runs on the primary interface.</span></span> <span data-ttu-id="195d0-561">Чтобы запустить клиент DHCP на дополнительном интерфейсе, с помощью этой службы установите дополнительный интерфейс в качестве интерфейса клиента DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-561">To run DHCP on a secondary service, use this service to set the secondary interface as the DHCP Client interface.</span></span> <span data-ttu-id="195d0-562">Приложение должно предварительно зарегистрировать указанный интерфейс в экземпляре IP с помощью службы *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="195d0-562">The application must previously register the specified interface to the IP instance using the *nx_ip_interface_attach* service.</span></span>

>[!NOTE]
> <span data-ttu-id="195d0-563">Эта служба предназначена для приложений, которые будут запускать клиент DHCP только в одном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="195d0-563">This service is intended for applications that intend to run the DHCP Client on only one interface.</span></span> <span data-ttu-id="195d0-564">Дополнительные сведения о запуске DHCP в нескольких интерфейсах см. в описании службы *nx_dhcp_interface_enable*.</span><span class="sxs-lookup"><span data-stu-id="195d0-564">To run DHCP on multiple interfaces see *nx_dhcp_interface_enable* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-565">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-565">Input Parameters</span></span>

- <span data-ttu-id="195d0-566">**dhcp_ptr**: указатель на блок управления DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-566">**dhcp_ptr**: Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="195d0-567">**index**: индекс сетевого интерфейса устройства</span><span class="sxs-lookup"><span data-stu-id="195d0-567">**index**: Index of device network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-568">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-568">Return Values</span></span>

- <span data-ttu-id="195d0-569">**NX_SUCCESS** (0x00) — интерфейс успешно задан.</span><span class="sxs-lookup"><span data-stu-id="195d0-569">**NX_SUCCESS**: (0x00) Interface is successfully set.</span></span>
- <span data-ttu-id="195d0-570">**NX_INVALID_INTERFACE** (0x4C) — недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="195d0-570">**NX_INVALID_INTERFACE**: (0x4C) Invalid network interface</span></span>
- <span data-ttu-id="195d0-571">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) — протокол DHCP включен для интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-571">**NX_DHCP_INTERFACE_ALREADY_ENABLED**: (0xA3) Interface enabled for DHCP</span></span>
- <span data-ttu-id="195d0-572">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) — нет доступной записи.</span><span class="sxs-lookup"><span data-stu-id="195d0-572">**NX_DHCP_NO_RECORDS_AVAILABLE**: (0xA7) No record available for another</span></span> 
- <span data-ttu-id="195d0-573">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-573">NX_PTR_ERROR: (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-574">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-574">Allowed From</span></span>

<span data-ttu-id="195d0-575">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-575">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-576">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-576">Example</span></span>

```c
/* Set the DHCP Client interface to the secondary interface (index 1).  */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set.  */
```

## <a name="nx_dhcp_start"></a><span data-ttu-id="195d0-577">nx_dhcp_start</span><span class="sxs-lookup"><span data-stu-id="195d0-577">nx_dhcp_start</span></span>

<span data-ttu-id="195d0-578">Запуск обработки DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-578">Start DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-579">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-579">Prototype</span></span>

```c
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="195d0-580">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-580">Description</span></span>

<span data-ttu-id="195d0-581">Эта служба запускает обработку DHCP для всех интерфейсов, для которых включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-581">This service starts DHCP processing on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="195d0-582">По умолчанию протокол DHCP включен для основного интерфейса, когда приложение вызывает *nx_dhcp_create*.</span><span class="sxs-lookup"><span data-stu-id="195d0-582">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="195d0-583">Чтобы проверить, привязан ли экземпляр IP к IP-адресу в интерфейсе клиента DHCP, используйте *nx_ip_status_check* для подтверждения допустимости IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="195d0-583">To verify when the IP instance is bound to an IP address on the DHCP Client interface, use *nx_ip_status_check* to see confirm the IP address is valid.</span></span>

<span data-ttu-id="195d0-584">Если протокол DHCP уже выполняется в других интерфейсах, эта служба не повлияет на них.</span><span class="sxs-lookup"><span data-stu-id="195d0-584">If there are other interfaces already running DHCP, this service will not affect them.</span></span>

<span data-ttu-id="195d0-585">Чтобы запустить DHCP для определенного интерфейса, когда включено несколько интерфейсов, используйте службу *nx_dhcp_interface_start*.</span><span class="sxs-lookup"><span data-stu-id="195d0-585">To start DHCP on a specific interface when multiple interfaces are enabled, use the *nx_dhcp_interface_start* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-586">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-586">Input Parameters</span></span>

- <span data-ttu-id="195d0-587">**dhcp_ptr**: указатель на ранее созданный экземпляр DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-587">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-588">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-588">Return Values</span></span>

- <span data-ttu-id="195d0-589">**NX_SUCCESS** (0x00) — успешный запуск DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-589">**NX_SUCCESS**: (0x00) Successful DHCP start.</span></span>  
- <span data-ttu-id="195d0-590">**NX_DHCP_ALREADY_STARTED** (0x93) — протокол DHCP уже запущен.</span><span class="sxs-lookup"><span data-stu-id="195d0-590">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="195d0-591">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-591">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="195d0-592">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-592">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-593">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-593">Allowed From</span></span>

<span data-ttu-id="195d0-594">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-594">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-595">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-595">Example</span></span>

```c
/* Start the DHCP processing for this IP instance.  */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started.  */
```

## <a name="nx_dhcp_interface_start"></a><span data-ttu-id="195d0-596">nx_dhcp_interface_start</span><span class="sxs-lookup"><span data-stu-id="195d0-596">nx_dhcp_interface_start</span></span>

<span data-ttu-id="195d0-597">Запуск обработки DHCP в указанном интерфейсе</span><span class="sxs-lookup"><span data-stu-id="195d0-597">Start DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-598">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-598">Prototype</span></span>

```c
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="195d0-599">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-599">Description</span></span>

<span data-ttu-id="195d0-600">Эта служба запускает обработку DHCP в указанном интерфейсе, если для него включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-600">This service starts DHCP processing on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="195d0-601">Дополнительные сведения о включении протокола DHCP для интерфейса см. в описании службы *nx_dhcp_interface_enable*().</span><span class="sxs-lookup"><span data-stu-id="195d0-601">See *nx_dhcp_interface_enable*() for more details about enabling an interface for DHCP.</span></span> <span data-ttu-id="195d0-602">По умолчанию протокол DHCP включен для основного интерфейса, когда приложение вызывает *nx_dhcp_create*.</span><span class="sxs-lookup"><span data-stu-id="195d0-602">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="195d0-603">Если нет других интерфейсов, в которых выполняется клиент DHCP, эта служба запустит или возобновит выполнение потока клиента DHCP и (повторно) активирует таймер клиента DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-603">If there are no other interfaces running DHCP Client this service will start/resume the DHCP Client thread and (re)activate the DHCP Client timer.</span></span>  
  
<span data-ttu-id="195d0-604">Приложение должно использовать *nx_ip_status_check* для проверки того, получен ли IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="195d0-604">The application should use *nx_ip_status_check* to verify if an IP address is obtained.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-605">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-605">Input Parameters</span></span>

- <span data-ttu-id="195d0-606">**dhcp_ptr**: указатель на ранее созданный экземпляр DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-606">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="195d0-607">**Interface_index**: индекс, по которому следует запустить клиент DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-607">**Interface_index**: Index on which to start the DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-608">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-608">Return Values</span></span>

- <span data-ttu-id="195d0-609">**NX_SUCCESS** (0x00) — успешный запуск DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-609">**NX_SUCCESS**: (0x00) Successful DHCP start.</span></span> 
- <span data-ttu-id="195d0-610">**NX_DHCP_ALREADY_STARTED** (0x93) — протокол DHCP уже запущен.</span><span class="sxs-lookup"><span data-stu-id="195d0-610">**NX_DHCP_ALREADY_STARTED**: (0x93) DHCP already started.</span></span>
- <span data-ttu-id="195d0-611">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-611">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="195d0-612">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-612">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="195d0-613">NX_INVALID_INTERFACE (0x4C) — недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="195d0-613">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-614">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-614">Allowed From</span></span>

<span data-ttu-id="195d0-615">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-615">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-616">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-616">Example</span></span>

```c
/* Start the DHCP processing for this IP instance on interface 1.  */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started.  */
```

## <a name="nx_dhcp_state_change_notify"></a><span data-ttu-id="195d0-617">nx_dhcp_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="195d0-617">nx_dhcp_state_change_notify</span></span>

<span data-ttu-id="195d0-618">Задание функции обратного вызова для изменения состояния DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-618">Set DHCP state change callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-619">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-619">Prototype</span></span>

```c
UINT nx_dhcp_state_change_notify(NX_DHCP *dhcp_ptr, 
                                 VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="195d0-620">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-620">Description</span></span>

<span data-ttu-id="195d0-621">Эта служба регистрирует указанную функцию обратного вызова dhcp_state_change_notify для уведомления приложения об изменениях состояния DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-621">This service registers the specified callback function dhcp_state_change_notify for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="195d0-622">Функция обратного вызова предоставляет состояние, в которое перешел клиент DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-622">The callback function supplies the state the DHCP Client has transitioned into.</span></span>

<span data-ttu-id="195d0-623">Ниже приведены значения, связанные с различными состояниями DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-623">Following are values associated with the various DHCP states:</span></span>

- <span data-ttu-id="195d0-624">NX_DHCP_STATE_BOOT: 1</span><span class="sxs-lookup"><span data-stu-id="195d0-624">NX_DHCP_STATE_BOOT: 1</span></span>
- <span data-ttu-id="195d0-625">NX_DHCP_STATE_INIT: 2</span><span class="sxs-lookup"><span data-stu-id="195d0-625">NX_DHCP_STATE_INIT: 2</span></span>
- <span data-ttu-id="195d0-626">NX_DHCP_STATE_SELECTING: 3</span><span class="sxs-lookup"><span data-stu-id="195d0-626">NX_DHCP_STATE_SELECTING: 3</span></span>
- <span data-ttu-id="195d0-627">NX_DHCP_STATE_REQUESTING: 4</span><span class="sxs-lookup"><span data-stu-id="195d0-627">NX_DHCP_STATE_REQUESTING: 4</span></span>
- <span data-ttu-id="195d0-628">NX_DHCP_STATE_BOUND: 5</span><span class="sxs-lookup"><span data-stu-id="195d0-628">NX_DHCP_STATE_BOUND: 5</span></span>
- <span data-ttu-id="195d0-629">NX_DHCP_STATE_RENEWING: 6</span><span class="sxs-lookup"><span data-stu-id="195d0-629">NX_DHCP_STATE_RENEWING: 6</span></span>
- <span data-ttu-id="195d0-630">NX_DHCP_STATE_REBINDING: 7</span><span class="sxs-lookup"><span data-stu-id="195d0-630">NX_DHCP_STATE_REBINDING: 7</span></span>
- <span data-ttu-id="195d0-631">NX_DHCP_STATE_FORCERENEW: 8</span><span class="sxs-lookup"><span data-stu-id="195d0-631">NX_DHCP_STATE_FORCERENEW: 8</span></span>
- <span data-ttu-id="195d0-632">NX_DHCP_STATE_ADDRESS_PROBING: 9</span><span class="sxs-lookup"><span data-stu-id="195d0-632">NX_DHCP_STATE_ADDRESS_PROBING: 9</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-633">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-633">Input Parameters</span></span>

- <span data-ttu-id="195d0-634">**dhcp_ptr**: указатель на ранее созданный экземпляр DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-634">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="195d0-635">**dhcp_state_change_notify**: указатель функции обратного вызова для изменения состояния</span><span class="sxs-lookup"><span data-stu-id="195d0-635">**dhcp_state_change_notify**: State change callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-636">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-636">Return Values</span></span>

- <span data-ttu-id="195d0-637">**NX_SUCCESS** (0x00) — обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="195d0-637">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>  
- <span data-ttu-id="195d0-638">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-638">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="195d0-639">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-639">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-640">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-640">Allowed From</span></span>

<span data-ttu-id="195d0-641">Потоки, инициализация</span><span class="sxs-lookup"><span data-stu-id="195d0-641">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="195d0-642">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-642">Example</span></span>

```c
/* Register the “my_state_change” function to be called on any DHCP state change, assuming DHCP has alreadybeen created.  */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered.  */
```

## <a name="nx_dhcp_interface_state_change_notify"></a><span data-ttu-id="195d0-643">nx_dhcp_interface_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="195d0-643">nx_dhcp_interface_state_change_notify</span></span>

<span data-ttu-id="195d0-644">Задание функции обратного вызова для изменения состояния DHCP в указанном интерфейсе</span><span class="sxs-lookup"><span data-stu-id="195d0-644">Set DHCP state change callback function on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-645">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-645">Prototype</span></span>

```c
UINT nx_dhcp_interface_state_change_notify(NX_DHCP *dhcp_ptr, UINT interface_index,
                                           VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                                                            UINT interface_index,
                                                                            UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="195d0-646">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-646">Description</span></span>

<span data-ttu-id="195d0-647">Эта служба регистрирует указанную функцию обратного вызова для уведомления приложения об изменениях состояния DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-647">This service registers the specified callback function for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="195d0-648">Входные аргументы функции обратного вызова — это индекс интерфейса и состояние, в которое клиент DHCP перешел в этом интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="195d0-648">The callback funciton input arguments are the interface index and the state the DHCP Client has transitioned to on that interface.</span></span>

<span data-ttu-id="195d0-649">Дополнительные сведения о функциях изменения состояния см. в описании функции *nx_dhcp_state_change_notify*().</span><span class="sxs-lookup"><span data-stu-id="195d0-649">For more information about state change functions, see *nx_dhcp_state_change_notify*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-650">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-650">Input Parameters</span></span>

- <span data-ttu-id="195d0-651">**dhcp_ptr**: указатель на ранее созданный экземпляр DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-651">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="195d0-652">**dhcp_interface_state_change_notify**: указатель функции обратного вызова приложения</span><span class="sxs-lookup"><span data-stu-id="195d0-652">**dhcp_interface_state_change_notify**: Application callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-653">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-653">Return Values</span></span>

- <span data-ttu-id="195d0-654">**NX_SUCCESS** (0x00) — обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="195d0-654">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>  
- <span data-ttu-id="195d0-655">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-655">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-656">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-656">Allowed From</span></span>

<span data-ttu-id="195d0-657">Потоки, инициализация</span><span class="sxs-lookup"><span data-stu-id="195d0-657">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="195d0-658">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-658">Example</span></span>

```c
/* Register the “my_state_change” function to be called on any DHCP state change,   
   assuming DHCP has alreadybeen created.  */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                  UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered.  */
```

## <a name="nx_dhcp_stop"></a><span data-ttu-id="195d0-659">nx_dhcp_stop</span><span class="sxs-lookup"><span data-stu-id="195d0-659">nx_dhcp_stop</span></span>

<span data-ttu-id="195d0-660">Остановка обработки DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-660">Stops DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-661">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-661">Prototype</span></span>

```c
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="195d0-662">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-662">Description</span></span>

<span data-ttu-id="195d0-663">Эта служба останавливает обработку DHCP во всех интерфейсах, в которых она запущена.</span><span class="sxs-lookup"><span data-stu-id="195d0-663">This service stops DHCP processing on all interfaces that have started DHCP processing.</span></span> <span data-ttu-id="195d0-664">Если протокол DHCP не обрабатывается ни одним интерфейсом, эта служба приостанавливает поток клиента DHCP и отключает таймер клиента DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-664">If there are no interfaces processing DHCP, this service will suspend the DHCP Client thread, and inactivate the DHCP Client timer.</span></span>

<span data-ttu-id="195d0-665">Чтобы остановить обработку DHCP для определенного интерфейса, когда протокол DHCP включен для нескольких интерфейсов, используйте службу *nx_dhcp_interface_stop*.</span><span class="sxs-lookup"><span data-stu-id="195d0-665">To stop DHCP on a specific interface if multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_stop* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-666">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-666">Input Parameters</span></span>

- <span data-ttu-id="195d0-667">**dhcp_ptr**: указатель на ранее созданный экземпляр DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-667">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-668">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-668">Return Values</span></span>

- <span data-ttu-id="195d0-669">**NX_SUCCESS** (0x00) — обработка DHCP успешно остановлена.</span><span class="sxs-lookup"><span data-stu-id="195d0-669">**NX_SUCCESS**: (0x00) Successful DHCP stop</span></span>
- <span data-ttu-id="195d0-670">**NX_DHCP_NOT_STARTED** (0x96) — экземпляр DHCP не запущен.</span><span class="sxs-lookup"><span data-stu-id="195d0-670">**NX_DHCP_NOT_STARTED**: (0x96) The DHCP instance not started.</span></span>
- <span data-ttu-id="195d0-671">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-671">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="195d0-672">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-672">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-673">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-673">Allowed From</span></span>

<span data-ttu-id="195d0-674">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-674">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-675">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-675">Example</span></span>

```c
/* Stop the DHCP processing for this IP instance.  */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped.  */
```

## <a name="nx_dhcp_interface_stop"></a><span data-ttu-id="195d0-676">nx_dhcp_interface_stop</span><span class="sxs-lookup"><span data-stu-id="195d0-676">nx_dhcp_interface_stop</span></span>

<span data-ttu-id="195d0-677">Остановка обработки DHCP в указанном интерфейсе</span><span class="sxs-lookup"><span data-stu-id="195d0-677">Stop DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-678">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-678">Prototype</span></span>

```c
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="195d0-679">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-679">Description</span></span>

<span data-ttu-id="195d0-680">Эта служба останавливает обработку DHCP в указанном интерфейсе, если она уже запущена.</span><span class="sxs-lookup"><span data-stu-id="195d0-680">This service stops DHCP processing on the specified interface if DHCP is already started.</span></span> <span data-ttu-id="195d0-681">Если нет других интерфейсов, использующих DHCP, поток и таймер DHCP приостанавливаются.</span><span class="sxs-lookup"><span data-stu-id="195d0-681">If there are no other interfaces running DHCP, the DHCP thread and timer are suspended.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-682">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-682">Input Parameters</span></span>

- <span data-ttu-id="195d0-683">**dhcp_ptr**: указатель на ранее созданный экземпляр DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-683">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="195d0-684">**Interface_index**: интерфейс, для которого необходимо остановить обработку DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-684">**Interface_index**: Interface on which to stop DHCP processing</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-685">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-685">Return Values</span></span>

- <span data-ttu-id="195d0-686">**NX_SUCCESS** (0x00) — обработка DHCP успешно остановлена.</span><span class="sxs-lookup"><span data-stu-id="195d0-686">**NX_SUCCESS**: (0x00) Successful DHCP stop</span></span>
- <span data-ttu-id="195d0-687">**NX_DHCP_NOT_STARTED** (0x96) — обработка DHCP не запущена.</span><span class="sxs-lookup"><span data-stu-id="195d0-687">**NX_DHCP_NOT_STARTED**: (0x96) DHCP not started.</span></span>
- <span data-ttu-id="195d0-688">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-688">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="195d0-689">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-689">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="195d0-690">NX_INVALID_INTERFACE (0x4C) — недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="195d0-690">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-691">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-691">Allowed From</span></span>

<span data-ttu-id="195d0-692">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-692">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-693">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-693">Example</span></span>

```c
/* Stop DHCP processing for this IP instance on interface 1.  */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped.  */
```

## <a name="nx_dhcp_user_option_retrieve"></a><span data-ttu-id="195d0-694">nx_dhcp_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="195d0-694">nx_dhcp_user_option_retrieve</span></span>

<span data-ttu-id="195d0-695">Получение параметра DHCP из последнего ответа сервера</span><span class="sxs-lookup"><span data-stu-id="195d0-695">Retrieve a DHCP option from last server response</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-696">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-696">Prototype</span></span>

```c
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, UINT request_option, 
                                  UCHAR *destination_ptr, UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="195d0-697">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-697">Description</span></span>

<span data-ttu-id="195d0-698">Эта служба извлекает указанный параметр DHCP из буфера параметров DHCP в первом интерфейсе с включенным протоколом DHCP, найденным в записи клиента DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-698">This service retrieves the specified DHCP option from the DHCP options buffer on the first interface enabled for DHCP found on the DHCP Client record.</span></span> <span data-ttu-id="195d0-699">В случае успешного выполнения данные параметра копируются в указанный буфер.</span><span class="sxs-lookup"><span data-stu-id="195d0-699">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-700">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-700">Input Parameters</span></span>

- <span data-ttu-id="195d0-701">**dhcp_ptr**: указатель на ранее созданный экземпляр DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-701">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>  
- <span data-ttu-id="195d0-702">**request_option**: параметр DHCP согласно RFC</span><span class="sxs-lookup"><span data-stu-id="195d0-702">**request_option**: DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="195d0-703">См. описание параметра NX_DHCP_OPTION в *nxd_dhcp_client.h*.</span><span class="sxs-lookup"><span data-stu-id="195d0-703">See the NX_DHCP_OPTION option in *nxd_dhcp_client.h*.</span></span>
- <span data-ttu-id="195d0-704">**destination_ptr**: указатель на место назначения для строки ответа</span><span class="sxs-lookup"><span data-stu-id="195d0-704">**destination_ptr**: Pointer to the destination for the response string.</span></span>  
- <span data-ttu-id="195d0-705">**destination_size**: указатель на размер места назначения и, при возврате, место назначения для размещения числа возвращенных байтов</span><span class="sxs-lookup"><span data-stu-id="195d0-705">**destination_size**: Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-706">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-706">Return Values</span></span>

- <span data-ttu-id="195d0-707">**NX_SUCCESS** (0x00) — успешное извлечение параметра.</span><span class="sxs-lookup"><span data-stu-id="195d0-707">**NX_SUCCESS**: (0x00) Successful option retrieval.</span></span>  
- <span data-ttu-id="195d0-708">**NX_DHCP_NOT_BOUND** (0x94) — клиент DHCP не привязан.</span><span class="sxs-lookup"><span data-stu-id="195d0-708">**NX_DHCP_NOT_BOUND**: (0x94) DHCP Client not bound.</span></span>
- <span data-ttu-id="195d0-709">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) — протокол DHCP не включен ни для одного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="195d0-709">**NX_DHCP_NO_INTERFACES_ENABLED**: (0xA5) No interfaces enabled for DHCP</span></span>
- <span data-ttu-id="195d0-710">**NX_DHCP_DEST_TO_SMALL** (0x95) — место назначения слишком мало для сохранения ответа.</span><span class="sxs-lookup"><span data-stu-id="195d0-710">**NX_DHCP_DEST_TO_SMALL**: (0x95) Destination is too small to hold response.</span></span>
- <span data-ttu-id="195d0-711">**NX_DHCP_PARSE_ERROR** (0x97) — параметр не найден в ответе сервера.</span><span class="sxs-lookup"><span data-stu-id="195d0-711">**NX_DHCP_PARSE_ERROR**: (0x97) Option not found in Server response.</span></span>
- <span data-ttu-id="195d0-712">NX_PTR_ERROR (0x16) — недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="195d0-712">NX_PTR_ERROR: (0x16) Invalid input pointer.</span></span>
- <span data-ttu-id="195d0-713">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-713">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-714">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-714">Allowed From</span></span>

<span data-ttu-id="195d0-715">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-715">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-716">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-716">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server.  */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
                                        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string.  */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a><span data-ttu-id="195d0-717">nx_dhcp_interface_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="195d0-717">nx_dhcp_interface_user_option_retrieve</span></span>

<span data-ttu-id="195d0-718">Получение параметра DHCP из последнего ответа сервера в указанном интерфейсе</span><span class="sxs-lookup"><span data-stu-id="195d0-718">Retrieve a DHCP option from last server response on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-719">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-719">Prototype</span></span>

```c
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT request_option, UCHAR *destination_ptr,
                                            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="195d0-720">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-720">Description</span></span>

<span data-ttu-id="195d0-721">Эта служба извлекает указанный параметр DHCP из буфера параметров DHCP в указанном интерфейсе, если для него включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-721">This service retrieves the specified DHCP option from the DHCP options buffer on the specified interface, if that interface is enabled for DHCP.</span></span> <span data-ttu-id="195d0-722">В случае успешного выполнения данные параметра копируются в указанный буфер.</span><span class="sxs-lookup"><span data-stu-id="195d0-722">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-723">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-723">Input Parameters</span></span>

- <span data-ttu-id="195d0-724">**dhcp_ptr**: указатель на ранее созданный экземпляр DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-724">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="195d0-725">**Interface_index**: индекс, по которому извлекается указанный параметр</span><span class="sxs-lookup"><span data-stu-id="195d0-725">**Interface_index**: Index on which to retrieve the specified option</span></span>
- <span data-ttu-id="195d0-726">**request_option**: параметр DHCP согласно RFC</span><span class="sxs-lookup"><span data-stu-id="195d0-726">**request_option**: DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="195d0-727">См. описание параметра NX_DHCP_OPTION в *nxd_dhcp_client.h*.</span><span class="sxs-lookup"><span data-stu-id="195d0-727">See the NX_DHCP_OPTION option: in *nxd_dhcp_client.h*.</span></span>  
- <span data-ttu-id="195d0-728">**destination_ptr**: указатель на место назначения для строки ответа</span><span class="sxs-lookup"><span data-stu-id="195d0-728">**destination_ptr**: Pointer to the destination for the response string.</span></span>  
- <span data-ttu-id="195d0-729">**destination_size**: указатель на размер места назначения и, при возврате, место назначения для размещения числа возвращенных байтов</span><span class="sxs-lookup"><span data-stu-id="195d0-729">**destination_size**: Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-730">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-730">Return Values</span></span>

- <span data-ttu-id="195d0-731">**NX_SUCCESS** (0x00) — успешное извлечение параметра.</span><span class="sxs-lookup"><span data-stu-id="195d0-731">**NX_SUCCESS**: (0x00) Successful option retrieval.</span></span>  
- <span data-ttu-id="195d0-732">**NX_DHCP_NOT_BOUND** (0x94) — IP-адрес не назначен.</span><span class="sxs-lookup"><span data-stu-id="195d0-732">**NX_DHCP_NOT_BOUND**: (0x94) IP address not assigned</span></span>
- <span data-ttu-id="195d0-733">**NX_DHCP_DEST_TO_SMALL** (0x95) — слишком маленький буфер.</span><span class="sxs-lookup"><span data-stu-id="195d0-733">**NX_DHCP_DEST_TO_SMALL**: (0x95) Buffer is too small</span></span>
- <span data-ttu-id="195d0-734">**NX_DHCP_PARSE_ERROR** (0x97) — параметр DHCP не найден в ответе сервера.</span><span class="sxs-lookup"><span data-stu-id="195d0-734">**NX_DHCP_PARSE_ERROR**: (0x97) DHCP Option not found in Server response.</span></span>
- <span data-ttu-id="195d0-735">NX_PTR_ERROR (0x16) — недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-735">NX_PTR_ERROR: (0x16) Invalid DHCP pointer.</span></span>
- <span data-ttu-id="195d0-736">NX_CALLER_ERROR (0x11) — недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="195d0-736">NX_CALLER_ERROR: (0x11) Invalid caller of service.</span></span>
- <span data-ttu-id="195d0-737">NX_INVALID_INTERFACE (0x4C) — недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="195d0-737">NX_INVALID_INTERFACE: (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-738">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-738">Allowed From</span></span>

<span data-ttu-id="195d0-739">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-739">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-740">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-740">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface.  */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
                                                  dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string.  */
```

## <a name="nx_dhcp_user_option_convert"></a><span data-ttu-id="195d0-741">nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="195d0-741">nx_dhcp_user_option_convert</span></span>

<span data-ttu-id="195d0-742">Преобразование четырех байт в ULONG</span><span class="sxs-lookup"><span data-stu-id="195d0-742">Convert four bytes to ULONG</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-743">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-743">Prototype</span></span>

```c
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a><span data-ttu-id="195d0-744">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-744">Description</span></span>

<span data-ttu-id="195d0-745">Эта служба преобразует четыре символа, на которые указывает option_string_ptr, в длинное целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="195d0-745">This service converts the four characters pointed to by “option_string_ptr” into an unsigned long value.</span></span> <span data-ttu-id="195d0-746">Она особенно полезна при наличии</span><span class="sxs-lookup"><span data-stu-id="195d0-746">It is especially useful when IP addresses are</span></span>  
<span data-ttu-id="195d0-747">IP-адресов.</span><span class="sxs-lookup"><span data-stu-id="195d0-747">present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-748">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-748">Input Parameters</span></span>

- <span data-ttu-id="195d0-749">**option_string_ptr**: указатель на ранее извлеченную строку параметра</span><span class="sxs-lookup"><span data-stu-id="195d0-749">**option_string_ptr**: Pointer to previously retrieved option string.</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-750">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-750">Return Values</span></span>

- <span data-ttu-id="195d0-751">**Value** — значение первых четырех байт.</span><span class="sxs-lookup"><span data-stu-id="195d0-751">**Value**: Value of first four bytes.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-752">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-752">Allowed From</span></span>

<span data-ttu-id="195d0-753">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-753">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-754">Например, .</span><span class="sxs-lookup"><span data-stu-id="195d0-754">Example</span></span>

```c
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a><span data-ttu-id="195d0-755">nx_dhcp_user_option_add_callback_set</span><span class="sxs-lookup"><span data-stu-id="195d0-755">nx_dhcp_user_option_add_callback_set</span></span>

<span data-ttu-id="195d0-756">Задание функции обратного вызова для добавления параметров, предоставленных пользователем</span><span class="sxs-lookup"><span data-stu-id="195d0-756">Set callback function for adding user supplied options</span></span>

### <a name="prototype"></a><span data-ttu-id="195d0-757">Прототип</span><span class="sxs-lookup"><span data-stu-id="195d0-757">Prototype</span></span>

```c
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
                                           UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                                                        UINT iface_index, 
                                                                        UINT message_type, 
                                                                        UCHAR *user_option_ptr, 
                                                                        UINT *user_option_length));
```

### <a name="description"></a><span data-ttu-id="195d0-758">Описание</span><span class="sxs-lookup"><span data-stu-id="195d0-758">Description</span></span>

<span data-ttu-id="195d0-759">Эта служба регистрирует указанную функцию обратного вызова для добавления предоставленных пользователем параметров.</span><span class="sxs-lookup"><span data-stu-id="195d0-759">This service registers the specified callback function for adding user supplied options.</span></span>

<span data-ttu-id="195d0-760">Если эта функция обратного вызова задана, приложения могут добавлять предоставленные пользователем параметры в пакет по iface_index и message_type.</span><span class="sxs-lookup"><span data-stu-id="195d0-760">If the callback function specified, the applications can add user supplied options into the packet by iface_index and message_type.</span></span>

>[!NOTE] 
> <span data-ttu-id="195d0-761">Подпрограмма пользователя.</span><span class="sxs-lookup"><span data-stu-id="195d0-761">In user’s routine.</span></span> <span data-ttu-id="195d0-762">При добавлении параметров, предоставляемых пользователем, приложения должны следовать формату параметров DHCP.</span><span class="sxs-lookup"><span data-stu-id="195d0-762">Applications must follow the DHCP options format when add user supplied options.</span></span> <span data-ttu-id="195d0-763">Общий размер пользовательских параметров должен быть не больше user_option_length. Значение user_option_length должно обновляться в соответствии с реальной длиной параметров.</span><span class="sxs-lookup"><span data-stu-id="195d0-763">The total size of user options must be less or equal to user_option_length, and update the user_option_length as real options length.</span></span> <span data-ttu-id="195d0-764">Если параметры добавлены успешно, возвращается значение NX_TRUE. В противном случае возвращается NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="195d0-764">Return NX_TRUE if add options successfully, else return NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="195d0-765">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="195d0-765">Input Parameters</span></span>

- <span data-ttu-id="195d0-766">**dhcp_ptr**: указатель на ранее созданный экземпляр DHCP</span><span class="sxs-lookup"><span data-stu-id="195d0-766">**dhcp_ptr**: Pointer to previously created DHCP instance.</span></span>
- <span data-ttu-id="195d0-767">**dhcp_user_option_add**: указатель на функцию добавления пользовательских параметров</span><span class="sxs-lookup"><span data-stu-id="195d0-767">**dhcp_user_option_add**: Pointer to user option add function.</span></span>

### <a name="return-values"></a><span data-ttu-id="195d0-768">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="195d0-768">Return Values</span></span>

- <span data-ttu-id="195d0-769">**NX_SUCCESS** (0x00) — обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="195d0-769">**NX_SUCCESS**: (0x00) Successful callback set.</span></span>
- <span data-ttu-id="195d0-770">NX_PTR_ERROR (0x16) — недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="195d0-770">NX_PTR_ERROR: (0x16) Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="195d0-771">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="195d0-771">Allowed From</span></span>

<span data-ttu-id="195d0-772">Потоки</span><span class="sxs-lookup"><span data-stu-id="195d0-772">Threads</span></span>

### <a name="example"></a><span data-ttu-id="195d0-773">Пример</span><span class="sxs-lookup"><span data-stu-id="195d0-773">Example</span></span>

```c
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created.  */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered.  */

```

