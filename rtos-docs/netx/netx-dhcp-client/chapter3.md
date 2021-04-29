---
title: Глава 3. Описание служб клиента ОСРВ Azure NetX DHCP
description: В этой главе приводится описание всех служб ОСРВ Azure NetX DHCP, которые перечислены ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8a614d22eca4fe693209751d72958b7d975c64c2
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815251"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-client-services"></a><span data-ttu-id="ec169-103">Глава 3. Описание служб клиента ОСРВ Azure NetX DHCP</span><span class="sxs-lookup"><span data-stu-id="ec169-103">Chapter 3 - Description of Azure RTOS NetX DHCP Client services</span></span>

<span data-ttu-id="ec169-104">В этой главе приводится описание всех служб ОСРВ Azure NetX DHCP, которые перечислены ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="ec169-104">This chapter contains a description of all Azure RTOS NetX DHCP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="ec169-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="ec169-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="ec169-106">**nx_dhcp_create**: *создание экземпляра DHCP*.</span><span class="sxs-lookup"><span data-stu-id="ec169-106">**nx_dhcp_create**: *Create a DHCP instance*</span></span>

- <span data-ttu-id="ec169-107">**nx_dhcp_clear_broadcast_flag**: сброс флага трансляции в сообщениях клиента.</span><span class="sxs-lookup"><span data-stu-id="ec169-107">**nx_dhcp_clear_broadcast_flag**: Clear broadcast flag on Client messages</span></span>

- <span data-ttu-id="ec169-108">**nx_dhcp_delete**: *удаление экземпляра DHCP*.</span><span class="sxs-lookup"><span data-stu-id="ec169-108">**nx_dhcp_delete**: *Delete a DHCP instance*</span></span>

- <span data-ttu-id="ec169-109">**nx_dhcp_decline**: отправка *сообщения об отклонении на сервер*.</span><span class="sxs-lookup"><span data-stu-id="ec169-109">**nx_dhcp_decline**: Send *Decline message to server*</span></span>

- <span data-ttu-id="ec169-110">**nx_dhcp_force_renew**: *отправка сообщения для принудительного обновления*.</span><span class="sxs-lookup"><span data-stu-id="ec169-110">**nx_dhcp_force_renew**: *Send force renew message*</span></span>

- <span data-ttu-id="ec169-111">**nx_dhcp_packet_pool_set**: *задание пула пакетов DHCP-клиента*.</span><span class="sxs-lookup"><span data-stu-id="ec169-111">**nx_dhcp_packet_pool_set**: *Set the DHCP Client packet pool*</span></span>

- <span data-ttu-id="ec169-112">**nx_dhcp_release**: отправка *сообщения об освобождении на сервер*.</span><span class="sxs-lookup"><span data-stu-id="ec169-112">**nx_dhcp_release**: Send *Release message to server*</span></span>

- <span data-ttu-id="ec169-113">**nx_dhcp_reinitialize**: *сброс параметров сети DHCP-клиента*.</span><span class="sxs-lookup"><span data-stu-id="ec169-113">**nx_dhcp_reinitialize**: *Clear DHCP client network parameters*</span></span>

- <span data-ttu-id="ec169-114">**nx_dhcp_request_client_ip**: *указание определенного IP-адреса*.</span><span class="sxs-lookup"><span data-stu-id="ec169-114">**nx_dhcp_request_client_ip**: *Specify a specific IP address*</span></span>

- <span data-ttu-id="ec169-115">**nx_dhcp_send_request**: *отправка сообщения DHCP на сервер*.</span><span class="sxs-lookup"><span data-stu-id="ec169-115">**nx_dhcp_send_request**: *Send DHCP message to server*</span></span>

- <span data-ttu-id="ec169-116">**nx_dhcp_server_address_get**: *получение адреса DHCP-сервера для DHCP-клиента*.</span><span class="sxs-lookup"><span data-stu-id="ec169-116">**nx_dhcp_server_address_get**: *Retrieve DHCP Client’s DHCP server address*</span></span>

- <span data-ttu-id="ec169-117">**nx_dhcp_set_interface_index**: *указание сетевого интерфейса клиента*.</span><span class="sxs-lookup"><span data-stu-id="ec169-117">**nx_dhcp_set_interface_index**: *Specify the Client network interface*</span></span>

- <span data-ttu-id="ec169-118">**nx_dhcp_start**: *запуск обработки DHCP*.</span><span class="sxs-lookup"><span data-stu-id="ec169-118">**nx_dhcp_start**: *Start DHCP processing*</span></span>

- <span data-ttu-id="ec169-119">**nx_dhcp_state_change_notify**: *уведомление приложения об изменении состояния DHCP*.</span><span class="sxs-lookup"><span data-stu-id="ec169-119">**nx_dhcp_state_change_notify**: *Notify application of DHCP state change*</span></span>

- <span data-ttu-id="ec169-120">**nx_dhcp_stop**: *остановка обработки DHCP*.</span><span class="sxs-lookup"><span data-stu-id="ec169-120">**nx_dhcp_stop**: *Stop DHCP processing*</span></span>

- <span data-ttu-id="ec169-121">**nx_dhcp_user_option_retrieve**: *извлечение параметра DHCP*.</span><span class="sxs-lookup"><span data-stu-id="ec169-121">**nx_dhcp_user_option_retrieve**: *Retrieve DHCP option*</span></span>

- <span data-ttu-id="ec169-122">**nx_dhcp_user_option_convert**: *преобразование четырех байт в значение ULONG*.</span><span class="sxs-lookup"><span data-stu-id="ec169-122">**nx_dhcp_user_option_convert**: *Convert four bytes to ULONG*</span></span>

<span data-ttu-id="ec169-123">Службы DHCP-клиента, относящиеся к интерфейсу</span><span class="sxs-lookup"><span data-stu-id="ec169-123">Interface specific DHCP Client services:</span></span>

- <span data-ttu-id="ec169-124">**nx_dhcp_interface_clear_broadcast_flag**: *снятие флага трансляции в сообщениях клиента на указанном интерфейсе*.</span><span class="sxs-lookup"><span data-stu-id="ec169-124">**nx_dhcp_interface_clear_broadcast_flag**: *Clear broadcast flag on Client messages on specified interface*</span></span>

- <span data-ttu-id="ec169-125">**nx_dhcp_interface_enable**: *включение протокола DHCP для указанного интерфейса*.</span><span class="sxs-lookup"><span data-stu-id="ec169-125">**nx_dhcp_interface_enable**: *Enable interface to run DHCP on the specified interface*</span></span>

- <span data-ttu-id="ec169-126">**nx_dhcp_interface_disable**: *отключение протокола DHCP для указанного интерфейса*.</span><span class="sxs-lookup"><span data-stu-id="ec169-126">**nx_dhcp_interface_disable**: *Disable interface to run DHCP on the specified interface*</span></span>

- <span data-ttu-id="ec169-127">**nx_dhcp_interface_decline**: *отправка сообщения об отклонении на сервер через указанный интерфейс*.</span><span class="sxs-lookup"><span data-stu-id="ec169-127">**nx_dhcp_interface_decline**: *Send Decline message to server on the specified interface*</span></span>

- <span data-ttu-id="ec169-128">**nx_dhcp_interface_force_renew**: *отправка сообщения для принудительного обновления через указанный интерфейс*.</span><span class="sxs-lookup"><span data-stu-id="ec169-128">**nx_dhcp_interface_force_renew**: *Send a force renew message on the specified interface*</span></span>

- <span data-ttu-id="ec169-129">**nx_dhcp_interface_reinitialize**: *сброс параметров сети DHCP-клиента на указанном интерфейсе*.</span><span class="sxs-lookup"><span data-stu-id="ec169-129">**nx_dhcp_interface_reinitialize**: *Clear DHCP client network parameters on the specified interface*</span></span>

- <span data-ttu-id="ec169-130">**nx_dhcp_interface_release**: *отправка сообщения об освобождении на сервер через указанный интерфейс*.</span><span class="sxs-lookup"><span data-stu-id="ec169-130">**nx_dhcp_interface_release**: *Send Release message to server  on the specified interface*</span></span>

- <span data-ttu-id="ec169-131">**nx_dhcp_interface_request_client_ip**: *указание IP-адреса для указанного интерфейса*.</span><span class="sxs-lookup"><span data-stu-id="ec169-131">**nx_dhcp_interface_request_client_ip**: *Specify a specific IP address on the specified interface*</span></span>

- <span data-ttu-id="ec169-132">**nx_dhcp_interface_send_request**: *отправка сообщения DHCP на сервер через указанный интерфейс*.</span><span class="sxs-lookup"><span data-stu-id="ec169-132">**nx_dhcp_interface_send_request**: *Send DHCP message to server on the specified interface*</span></span>

- <span data-ttu-id="ec169-133">**nx_dhcp_interface_server_address_get**: *получение IP-адреса DHCP-сервера для указанного интерфейса*.</span><span class="sxs-lookup"><span data-stu-id="ec169-133">**nx_dhcp_interface_server_address_get**: *Get the DHCP server IP address on the specified interface*</span></span>

- <span data-ttu-id="ec169-134">**nx_dhcp_interface_start**: *запуск обработки DHCP-клиента на указанном интерфейсе*.</span><span class="sxs-lookup"><span data-stu-id="ec169-134">**nx_dhcp_interface_start**: *Start the DHCP Client processing on the specified interface*</span></span>

- <span data-ttu-id="ec169-135">**nx_dhcp_interface_stop**: *остановка обработки DHCP-клиента на указанном интерфейсе*.</span><span class="sxs-lookup"><span data-stu-id="ec169-135">**nx_dhcp_interface_stop**: *Stop the DHCP Client processing on the specified interface*</span></span>

- <span data-ttu-id="ec169-136">**nx_dhcp_interface_state_change_notify**: *указание функции обратного вызова при изменении состояния DHCP на указанном интерфейсе*.</span><span class="sxs-lookup"><span data-stu-id="ec169-136">**nx_dhcp_interface_state_change_notify**: *Set the callback function when DHCP state changes on the specified interface*</span></span>

- <span data-ttu-id="ec169-137">**nx_dhcp_interface_user_option_retrieve**: *получение указанного параметра DHCP для заданного интерфейса*.</span><span class="sxs-lookup"><span data-stu-id="ec169-137">**nx_dhcp_interface_user_option_retrieve**: *Retrieve the specified DHCP option on the specified interface*</span></span>

<span data-ttu-id="ec169-138">Службы DHCP-клиента, если определено значение NX_DHCP_CLIENT_RESORE_STATE.</span><span class="sxs-lookup"><span data-stu-id="ec169-138">DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="ec169-139">**nx_dhcp_resume**: *восстановление ранее заданного состояния DHCP-клиента*.</span><span class="sxs-lookup"><span data-stu-id="ec169-139">**nx_dhcp_resume**: *Resume previously established DHCP Client state*</span></span>

- <span data-ttu-id="ec169-140">**nx_dhcp_suspend**: *приостановка обработки состояния DHCP-клиента*.</span><span class="sxs-lookup"><span data-stu-id="ec169-140">**nx_dhcp_suspend**: *Suspend processing the DHCP Client state*</span></span>

- <span data-ttu-id="ec169-141">**nx_dhcp_client_get_record**: *создание записи состояния DHCP-клиента*.</span><span class="sxs-lookup"><span data-stu-id="ec169-141">**nx_dhcp_client_get_record**: *Create a record of the DHCP Client state*</span></span>

- <span data-ttu-id="ec169-142">**nx_dhcp_client_restore_record**: *восстановление ранее сохраненной записи в DHCP-клиенте*.</span><span class="sxs-lookup"><span data-stu-id="ec169-142">**nx_dhcp_client_restore_record**: *Restore a previously saved record to the DHCP Client*</span></span>

- <span data-ttu-id="ec169-143">**nx_dhcp_client_update_time_remaining**: *обновление значения оставшегося времени в текущем состоянии DHCP*.</span><span class="sxs-lookup"><span data-stu-id="ec169-143">**nx_dhcp_client_update_time_remaining**: *Update the time remaining in the current DHCP state*</span></span>

<span data-ttu-id="ec169-144">Службы DHCP-клиента, относящиеся к интерфейсу, если определен параметр NX_DHCP_CLIENT_RESORE_STATE.</span><span class="sxs-lookup"><span data-stu-id="ec169-144">Interface Specific DHCP Client Services if NX_DHCP_CLIENT_RESORE_STATE is defined:</span></span>

- <span data-ttu-id="ec169-145">**nx_dhcp_client_interface_get_record**: *создание записи состояния DHCP-клиента на указанном интерфейсе*.</span><span class="sxs-lookup"><span data-stu-id="ec169-145">**nx_dhcp_client_interface_get_record**: *Create a record of the DHCP Client state on the specified interface*</span></span>

- <span data-ttu-id="ec169-146">**nx_dhcp_client_interface_restore_record**: *восстановление ранее сохраненной записи состояния DHCP-клиента на указанном интерфейсе*.</span><span class="sxs-lookup"><span data-stu-id="ec169-146">**nx_dhcp_client_interface_restore_record**: *Restore a previously saved record to the DHCP Client on the specified interface*</span></span>

- <span data-ttu-id="ec169-147">**nx_dhcp_client_interface_update_time_remaining**: *обновление значения оставшегося времени в текущем состоянии DHCP для указанного интерфейса*.</span><span class="sxs-lookup"><span data-stu-id="ec169-147">**nx_dhcp_client_interface_update_time_remaining**: *Update the time remaining in the current DHCP state on the specified interface*</span></span>

## <a name="nx_dhcp_create"></a><span data-ttu-id="ec169-148">nx_dhcp_create</span><span class="sxs-lookup"><span data-stu-id="ec169-148">nx_dhcp_create</span></span>

<span data-ttu-id="ec169-149">Создание экземпляра DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-149">Create a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-150">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-150">Prototype</span></span>

```C
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a><span data-ttu-id="ec169-151">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-151">Description</span></span>

<span data-ttu-id="ec169-152">Эта служба создает экземпляр DHCP для созданного ранее экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="ec169-152">This service creates a DHCP instance for the previously created IP instance.</span></span> <span data-ttu-id="ec169-153">По умолчанию протокол DHCP включается для основного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ec169-153">By default the primary interface is enabled for running DHCP.</span></span> <span data-ttu-id="ec169-154">Введенное имя, хотя и не используется в реализации DHCP-клиента в NetX, должно соответствовать требованиям RFC 1035 к именам узлов.</span><span class="sxs-lookup"><span data-stu-id="ec169-154">The name input, while not used in the NetX implementation of DHCP Client, must follow RFC 1035 criteria for host names.</span></span> <span data-ttu-id="ec169-155">Общая длина не должна превышать 255 символов, а элементы, разделяемые точками, должны начинаться с буквы, заканчиваться буквой или цифрой и могут содержать только буквы, цифры и дефисы.</span><span class="sxs-lookup"><span data-stu-id="ec169-155">The total length must not exceed 255 characters, the labels separate by dots must begin with a letter, and end with a letter or number, and may contain hyphens but no other non-alphanumeric character.</span></span>

<span data-ttu-id="ec169-156">Если приложению требуется запустить протокол DHCP на другом интерфейсе, зарегистрированном в экземпляре IP (с помощью *nx_ip_interface_attach*), оно может вызвать *nx_dhcp_set_interface_index* для запуска протокола DHCP только на этом интерфейсе или *nx_dhcp_interface_enable* для запуска протокола DHCP на этом интерфейсе в дополнение к другим.</span><span class="sxs-lookup"><span data-stu-id="ec169-156">If the application would like to run DHCP another interface registered with the IP instance, (using *nx_ip_interface_attach*), the application can call *nx_dhcp_set_interface_index* to run DHCP on just that interface, or *nx_dhcp_interface_enable* to run DHCP on that interface as well.</span></span> <span data-ttu-id="ec169-157">Дополнительные сведения см. в описании этих служб.</span><span class="sxs-lookup"><span data-stu-id="ec169-157">See description of these services for more details.</span></span>

> [!NOTE]
> <span data-ttu-id="ec169-158">Приложение должно убедиться в том, что полезные данные пула пакетов DHCP-клиента соответствуют минимальному размеру сообщения DHCP, указанному в разделе 2 спецификации RFC 2131 (548 байт данных сообщения DHCP плюс заголовки UDP, IP и кадра физической сети).</span><span class="sxs-lookup"><span data-stu-id="ec169-158">The application must make sure the DHCP Client packet pool payload can support the minimum DHCP message size specified by the RFC 2131 Section 2 (548 bytes of DHCP message data plus UDP, IP and physical network frame headers).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-159">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-159">Input Parameters</span></span>

- <span data-ttu-id="ec169-160">**dhcp_ptr**: указатель на блок управления DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-160">**dhcp_ptr** Pointer to DHCP control block.</span></span>  
- <span data-ttu-id="ec169-161">**ip_ptr**: указатель на созданный ранее экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="ec169-161">**ip_ptr** Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="ec169-162">**name_ptr**: указатель на имя узла для экземпляра DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-162">**name_ptr** Pointer to host name for DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-163">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-163">Return Values</span></span>

- <span data-ttu-id="ec169-164">**NX_SUCCESS** (0x00): экземпляр DHCP успешно создан.</span><span class="sxs-lookup"><span data-stu-id="ec169-164">**NX_SUCCESS** (0x00) Successful DHCP create</span></span>

- <span data-ttu-id="ec169-165">**NX_DHCP_INVALID_NAME** (0xA8): недопустимое имя узла.</span><span class="sxs-lookup"><span data-stu-id="ec169-165">**NX_DHCP_INVALID_NAME** (0xA8) Invalid host name</span></span>

- <span data-ttu-id="ec169-166">**NX_DHCP_INVALID_PAYLOAD** (0x9C): слишком маленький размер полезных данных для сообщения DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-166">**NX_DHCP_INVALID_PAYLOAD** (0x9C) Payload too small for DHCP message</span></span>

- <span data-ttu-id="ec169-167">NX_PTR_ERROR (0x16): недопустимый указатель IP или DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-167">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-168">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-168">Allowed From</span></span>

<span data-ttu-id="ec169-169">**Потоки**, инициализация.</span><span class="sxs-lookup"><span data-stu-id="ec169-169">**Threads,** Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ec169-170">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-170">Example</span></span>

```C
/* Create a DHCP instance. */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created. */
```

## <a name="nx_dhcp_interface_enable"></a><span data-ttu-id="ec169-171">nx_dhcp_interface_enable</span><span class="sxs-lookup"><span data-stu-id="ec169-171">nx_dhcp_interface_enable</span></span>

<span data-ttu-id="ec169-172">Включение протокола DHCP для указанного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ec169-172">Enable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="ec169-173">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-173">Prototype</span></span>

```C
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ec169-174">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-174">Description</span></span>

<span data-ttu-id="ec169-175">Эта служба включает протокол DHCP для указанного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ec169-175">This service enables the specified interface for running DHCP.</span></span> <span data-ttu-id="ec169-176">По умолчанию для DHCP-клиента включен основной интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-176">By default the primary interface is enabled for DHCP Client.</span></span> <span data-ttu-id="ec169-177">На этом этапе можно запустить DHCP либо на этом интерфейсе, вызвав *nx_dhcp_interface_start*, либо на всех интерфейсах с поддержкой DHCP, вызвав *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="ec169-177">At this point, DHCP can be started on this interface either by calling *nx_dhcp_interface_start* or to start DHCP on all enabled interfaces *nx_dhcp_start*.</span></span>

<span data-ttu-id="ec169-178">Обратите внимание на то, что приложение должно сначала зарегистрировать этот интерфейс в экземпляре IP с помощью *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="ec169-178">Note the application must first register this interface with the IP instance, using *nx_ip_interface_attach.*</span></span>

<span data-ttu-id="ec169-179">Кроме того, для добавления этого интерфейса в список включенных должна быть доступная запись интерфейса DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="ec169-179">Further, there must be an available DHCP Client interface ‘record’ to add this interface to the list of enabled interfaces.</span></span> <span data-ttu-id="ec169-180">По умолчанию параметр NX_DHCP_CLIENT_MAX_RECORDS имеет значение 1.</span><span class="sxs-lookup"><span data-stu-id="ec169-180">By default NX_DHCP_CLIENT_MAX_RECORDS is defined to 1.</span></span> <span data-ttu-id="ec169-181">Задайте для этого параметра максимальное число интерфейсов для одновременного выполнения DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="ec169-181">Set this option to the maximum number of interfaces expected to run DHCP Client simultaneously.</span></span> <span data-ttu-id="ec169-182">Обычно значение NX_DHCP_CLIENT_MAX_RECORDS равно NX_MAX_PHYSICAL_INTERFACES. Но если у устройства больше физических интерфейсов, чем требуется для работы DHCP-клиента, можно сэкономить память, задав для параметра NX_DHCP_CLIENT_MAX_RECORDS меньшее число.</span><span class="sxs-lookup"><span data-stu-id="ec169-182">Typically NX_DHCP_CLIENT_MAX_RECORDS will equal NX_MAX_PHYSICAL_INTERFACES; however, if a device has more physical interfaces than it expects to run DHCP Client, it can save memory by setting NX_DHCP_CLIENT_MAX_RECORDS to less than that number.</span></span> <span data-ttu-id="ec169-183">Не существует однозначного сопоставления между физическими интерфейсами и записями интерфейсов DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="ec169-183">There is not a one to one mapping of physical interfaces with DHCP Client interface records.</span></span>

<span data-ttu-id="ec169-184">Разница между этой службой и *nx_dhcp_set_interface_index* состоит в том, что последняя включает протокол DHCP только для одного интерфейса, тогда как данная служба просто добавляет указанный интерфейс в список интерфейсов клиента с поддержкой DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-184">The difference between this service and *nx_dhcp_set_interface_index* is the latter sets only a single interface to run DHCP whereas this service simply adds the specified interface to the list of Client interfaces enabled for DHCP.</span></span>

<span data-ttu-id="ec169-185">Чтобы отключить протокол DHCP для интерфейса, приложение может вызвать службу *nx_dhcp_interface_disable*.</span><span class="sxs-lookup"><span data-stu-id="ec169-185">To disable an interface for DHCP, the application can call the *nx_dhcp_interface_disable* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-186">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-186">Input Parameters</span></span>

- <span data-ttu-id="ec169-187">**dhcp_ptr**: указатель на блок управления DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-187">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="ec169-188">**interface_index**: индекс интерфейса, для которого нужно включить протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-188">**interface_index** Index of interface to enable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-189">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-189">Return Values</span></span>

- <span data-ttu-id="ec169-190">**NX_SUCCESS** (0x00): протокол DHCP успешно включен.</span><span class="sxs-lookup"><span data-stu-id="ec169-190">**NX_SUCCESS** (0x00) Successful DHCP enable</span></span>

- <span data-ttu-id="ec169-191">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7): нет доступной записи для другого интерфейса, для которого следует включить протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-191">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) No record available for another Interface to be enabled for DHCP</span></span>

- <span data-ttu-id="ec169-192">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3): для интерфейса включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-192">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) Interface enabled for DHCP</span></span>

- <span data-ttu-id="ec169-193">NX_PTR_ERROR (0x16): недопустимый указатель IP или DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-193">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="ec169-194">NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-194">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-195">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-195">Allowed From</span></span>

<span data-ttu-id="ec169-196">Потоки, инициализация.</span><span class="sxs-lookup"><span data-stu-id="ec169-196">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ec169-197">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-197">Example</span></span>

```C
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface. NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled. */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1. */
```

## <a name="nx_dhcp_interface_disable"></a><span data-ttu-id="ec169-198">nx_dhcp_interface_disable</span><span class="sxs-lookup"><span data-stu-id="ec169-198">nx_dhcp_interface_disable</span></span>

<span data-ttu-id="ec169-199">Отключение протокола DHCP для указанного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ec169-199">Disable the specified interface to run DHCP</span></span> 

### <a name="prototype"></a><span data-ttu-id="ec169-200">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-200">Prototype</span></span>

```C
UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ec169-201">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-201">Description</span></span>

<span data-ttu-id="ec169-202">Эта служба отключает протокол DHCP для указанного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ec169-202">This service disables the specified interface for running DHCP.</span></span> <span data-ttu-id="ec169-203">Она повторно инициализирует DHCP-клиент для этого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ec169-203">It reinitializes the DHCP Client on this interface.</span></span>

<span data-ttu-id="ec169-204">Чтобы перезапустить DHCP-клиент, приложение должно повторно включить интерфейс с помощью *nx_dhcp_interface_enable* и перезапустить DHCP, вызвав *nx_dhcp_interface_start*.</span><span class="sxs-lookup"><span data-stu-id="ec169-204">To restart the DHCP Client the application must re-enable the interface using *nx_dhcp_interface_enable* and restart DHCP by calling *nx_dhcp_interface_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-205">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-205">Input Parameters</span></span>

- <span data-ttu-id="ec169-206">**dhcp_ptr**: указатель на блок управления DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-206">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="ec169-207">**interface_index**: индекс интерфейса, для которого нужно отключить протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-207">**interface_index** Index of interface to disable DHCP on</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-208">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-208">Return Values</span></span>

- <span data-ttu-id="ec169-209">**NX_SUCCESS** (0x00): экземпляр DHCP успешно создан.</span><span class="sxs-lookup"><span data-stu-id="ec169-209">**NX_SUCCESS** (0x00) Successful DHCP create</span></span>

- <span data-ttu-id="ec169-210">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4): для интерфейса не включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-210">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="ec169-211">NX_PTR_ERROR (0x16): недопустимый указатель IP или DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-211">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="ec169-212">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-212">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

- <span data-ttu-id="ec169-213">NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-213">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-214">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-214">Allowed From</span></span>

<span data-ttu-id="ec169-215">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-215">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-216">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-216">Example</span></span>

```C
/* Disable DHCP on a secondary interface.
. */

status = nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled. */
```

## <a name="nx_dhcp_clear_broadcast_flag"></a><span data-ttu-id="ec169-217">nx_dhcp_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="ec169-217">nx_dhcp_clear_broadcast_flag</span></span>

<span data-ttu-id="ec169-218">Установка флага широковещательного режима DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-218">Set the DHCP broadcast flag</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-219">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-219">Prototype</span></span>

```C
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="ec169-220">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-220">Description</span></span>

<span data-ttu-id="ec169-221">Эта служба устанавливает или снимает флаг широковещательного режима в заголовке сообщения DHCP для всех интерфейсов, для которых включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-221">This service sets or clears the broadcast flag the DHCP message header for all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ec169-222">Для некоторых сообщений DHCP (например, DISCOVER) флаг широковещательного режима установлен, так как у клиента нет IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="ec169-222">For some DHCP messages (e.g. DISCOVER) the broadcast flag is set to broadcast because the Client does not have an IP address.</span></span>

<span data-ttu-id="ec169-223">__clear_flag__</span><span class="sxs-lookup"><span data-stu-id="ec169-223">__clear_flag__</span></span>


- <span data-ttu-id="ec169-224">**NX_TRUE**: флаг широковещательного режима снят (запрашивается одноадресный ответ).</span><span class="sxs-lookup"><span data-stu-id="ec169-224">**NX_TRUE** broadcast flag is cleared (request unicast response)</span></span>

- <span data-ttu-id="ec169-225">**NX_FALSE**: флаг широковещательного режима установлен (запрашивается широковещательный ответ).</span><span class="sxs-lookup"><span data-stu-id="ec169-225">**NX_FALSE** broadcast flag is set (request broadcast response)</span></span>

<span data-ttu-id="ec169-226">Эта служба предназначена для DHCP-клиентов, которые должны обращаться к DHCP-серверу через маршрутизатор, который отклоняет переадресацию широковещательных сообщений.</span><span class="sxs-lookup"><span data-stu-id="ec169-226">This service is intended for DHCP Clients that must go through a router to get to the DHCP Server, where the router rejects forwarding broadcast messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-227">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-227">Input Parameters</span></span>

- <span data-ttu-id="ec169-228">**dhcp_ptr**: указатель на блок управления DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-228">**dhcp_ptr** Pointer to DHCP control block</span></span>  

- <span data-ttu-id="ec169-229">**clear_flag**: значение, устанавливаемое для флага широковещательного режима.</span><span class="sxs-lookup"><span data-stu-id="ec169-229">**clear_flag** Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-230">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-230">Return Values</span></span>

- <span data-ttu-id="ec169-231">**NX_SUCCESS** (0X00): флаг широковещательного режима успешно обновлен.</span><span class="sxs-lookup"><span data-stu-id="ec169-231">**NX_SUCCESS** (0x00) Successfully updated the broadcast flag</span></span>

- <span data-ttu-id="ec169-232">NX_PTR_ERROR (0x16): недопустимый указатель IP или DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-232">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="ec169-233">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-233">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-234">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-234">Allowed From</span></span>

<span data-ttu-id="ec169-235">Потоки, инициализация.</span><span class="sxs-lookup"><span data-stu-id="ec169-235">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ec169-236">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-236">Example</span></span>

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response). */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a><span data-ttu-id="ec169-237">nx_dhcp_interface_clear_broadcast_flag</span><span class="sxs-lookup"><span data-stu-id="ec169-237">nx_dhcp_interface_clear_broadcast_flag</span></span>

<span data-ttu-id="ec169-238">Установка или снятие флага широковещательного режима для указанного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ec169-238">Set or clear the broadcast flag on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-239">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-239">Prototype</span></span>

```C
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT clear_flag);
```

### <a name="description"></a><span data-ttu-id="ec169-240">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-240">Description</span></span>

<span data-ttu-id="ec169-241">Эта служба позволяет ведущему приложению DHCP-клиента устанавливать или снимать флаг широковещательного режима в сообщениях DHCP-клиента, передаваемых DHCP-серверу через указанный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-241">This service enables the DHCP Client host application to set or clear the broadcast flag in DHCP Client messages to the DHCP Server on the specified interface.</span></span> <span data-ttu-id="ec169-242">Дополнительные сведения см. в описании службы **nx_dhcp_clear_broadcast_flag**.</span><span class="sxs-lookup"><span data-stu-id="ec169-242">For more details see **nx_dhcp_clear_broadcast_flag**</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-243">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-243">Input Parameters</span></span>

- <span data-ttu-id="ec169-244">**dhcp_ptr**: указатель на блок управления DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-244">**dhcp_ptr** Pointer to DHCP control block</span></span>

- <span data-ttu-id="ec169-245">**interface_index**: индекс интерфейса, для которого нужно установить флаг широковещательного режима.</span><span class="sxs-lookup"><span data-stu-id="ec169-245">**interface_index** Index of interface to set the broadcast flag</span></span>  

- <span data-ttu-id="ec169-246">**clear_flag**: значение, устанавливаемое для флага широковещательного режима.</span><span class="sxs-lookup"><span data-stu-id="ec169-246">**clear_flag** Value to set the broadcast flag to</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-247">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-247">Return Values</span></span>

- <span data-ttu-id="ec169-248">**NX_SUCCESS** (0X00): флаг широковещательного режима успешно обновлен.</span><span class="sxs-lookup"><span data-stu-id="ec169-248">**NX_SUCCESS** (0x00) Successfully updated the broadcast flag</span></span>

- <span data-ttu-id="ec169-249">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4): для интерфейса не включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-249">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="ec169-250">NX_PTR_ERROR (0x16): недопустимый указатель IP или DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-250">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="ec169-251">NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-251">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-252">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-252">Allowed From</span></span>

<span data-ttu-id="ec169-253">Потоки, инициализация.</span><span class="sxs-lookup"><span data-stu-id="ec169-253">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ec169-254">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-254">Example</span></span>

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface. */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_delete"></a><span data-ttu-id="ec169-255">nx_dhcp_delete</span><span class="sxs-lookup"><span data-stu-id="ec169-255">nx_dhcp_delete</span></span>

<span data-ttu-id="ec169-256">Удаление экземпляра DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-256">Delete a DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-257">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-257">Prototype</span></span>

```C
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ec169-258">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-258">Description</span></span>

<span data-ttu-id="ec169-259">Эта служба удаляет созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-259">This service deletes a previously created DHCP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-260">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-260">Input Parameters</span></span>

- <span data-ttu-id="ec169-261">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-261">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-262">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-262">Return Values</span></span>

- <span data-ttu-id="ec169-263">**NX_SUCCESS** (0x00): экземпляр DHCP успешно удален.</span><span class="sxs-lookup"><span data-stu-id="ec169-263">**NX_SUCCESS** (0x00) Successful DHCP delete.</span></span>

- <span data-ttu-id="ec169-264">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-264">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="ec169-265">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-265">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-266">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-266">Allowed From</span></span>

<span data-ttu-id="ec169-267">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-267">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-268">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-268">Example</span></span>

```C
/* Delete a DHCP instance. */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted. */
```

## <a name="nx_dhcp_-force_renew"></a><span data-ttu-id="ec169-269">nx_dhcp_ force_renew</span><span class="sxs-lookup"><span data-stu-id="ec169-269">nx_dhcp_ force_renew</span></span>

<span data-ttu-id="ec169-270">Отправка сообщения о принудительном обновлении.</span><span class="sxs-lookup"><span data-stu-id="ec169-270">Send a force renew message</span></span> 

### <a name="prototype"></a><span data-ttu-id="ec169-271">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-271">Prototype</span></span>

```C
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ec169-272">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-272">Description</span></span>

<span data-ttu-id="ec169-273">Эта служба позволяет ведущему приложению отправлять сообщение о принудительном обновлении для всех интерфейсов, для которых включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-273">This service enables the host application to send a force renew message on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ec169-274">DHCP-клиент должен находиться в состоянии BOUND.</span><span class="sxs-lookup"><span data-stu-id="ec169-274">The DHCP Client must be in a BOUND state.</span></span> <span data-ttu-id="ec169-275">Эта функция устанавливает состояние "RENEW" (Продление), чтобы DHCP-клиент пытался выполнить обновление до истечения времени ожидания T1.</span><span class="sxs-lookup"><span data-stu-id="ec169-275">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

<span data-ttu-id="ec169-276">Чтобы отправить сообщение о принудительном обновлении на определенный интерфейс, когда протокол DHCP включен для нескольких интерфейсов, используйте *nx_dhcp_interface_force_renew*.</span><span class="sxs-lookup"><span data-stu-id="ec169-276">To send a force renew on a specific interface when multiple interfaces are DHCP-enabled, use *nx_dhcp_interface_force_renew*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-277">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-277">Input Parameters</span></span>

- <span data-ttu-id="ec169-278">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-278">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-279">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-279">Return Values</span></span>

- <span data-ttu-id="ec169-280">**NX_SUCCESS** (0x00): сообщение о принудительном обновлении успешно отправлено.</span><span class="sxs-lookup"><span data-stu-id="ec169-280">**NX_SUCCESS** (0x00) Successfully sent force renew.</span></span>  

- <span data-ttu-id="ec169-281">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-281">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="ec169-282">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-282">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-283">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-283">Allowed From</span></span>

<span data-ttu-id="ec169-284">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-285">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-285">Example</span></span>

```C
/* Send a force renew message from the Client. */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_interface_force_renew"></a><span data-ttu-id="ec169-286">nx_dhcp_interface_force_renew</span><span class="sxs-lookup"><span data-stu-id="ec169-286">nx_dhcp_interface_force_renew</span></span>

<span data-ttu-id="ec169-287">Отправка сообщения о принудительном обновлении на указанный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-287">Send a force renew message on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-288">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-288">Prototype</span></span>

```C
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ec169-289">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-289">Description</span></span>

<span data-ttu-id="ec169-290">Эта служба позволяет ведущему приложению отправлять сообщение о принудительном обновлении на указанный интерфейс, если для него включен протокол DHCP (см. описание службы *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="ec169-290">This service enables the host application to send a force renew message on the input interface as long as that interface has been enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="ec169-291">DHCP-клиент на указанном интерфейсе должен находиться в состоянии BOUND.</span><span class="sxs-lookup"><span data-stu-id="ec169-291">The DHCP Client on the specified interface must be in a BOUND state.</span></span> <span data-ttu-id="ec169-292">Эта функция устанавливает состояние "RENEW" (Продление), чтобы DHCP-клиент пытался выполнить обновление до истечения времени ожидания T1.</span><span class="sxs-lookup"><span data-stu-id="ec169-292">This function sets the state to RENEW such that the DHCP Client will try to renew before the T1 timeout expires.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-293">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-293">Input Parameters</span></span>

- <span data-ttu-id="ec169-294">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-294">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-295">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-295">Return Values</span></span>

- <span data-ttu-id="ec169-296">**NX_SUCCESS** (0x00): сообщение о принудительном обновлении успешно отправлено.</span><span class="sxs-lookup"><span data-stu-id="ec169-296">**NX_SUCCESS** (0x00) Successfully sent force renew.</span></span>  

- <span data-ttu-id="ec169-297">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4): для интерфейса не включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-297">**NX_DHCP_INTERFACE_NOT_ENABLED**  (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="ec169-298">NX_PTR_ERROR (0x16): недопустимый указатель IP или DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-298">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="ec169-299">NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-299">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-300">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-300">Allowed From</span></span>

<span data-ttu-id="ec169-301">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-302">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-302">Example</span></span>

```C
/* Send a force renew message to the server on interface 1. */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_packet_pool_set"></a><span data-ttu-id="ec169-303">nx_dhcp_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="ec169-303">nx_dhcp_packet_pool_set</span></span>

<span data-ttu-id="ec169-304">Задание пула пакетов DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="ec169-304">Set the DHCP Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-305">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-305">Prototype</span></span>

```C
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr,
                            NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a><span data-ttu-id="ec169-306">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-306">Description</span></span>

<span data-ttu-id="ec169-307">Эта служба позволяет приложению создать пул пакетов DHCP-клиента путем передачи указателя на ранее созданный пул пакетов в этом вызове службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-307">This service allows the application to create the DHCP Client packet pool by passing in a pointer to a previously created packet pool in this service call.</span></span> <span data-ttu-id="ec169-308">Чтобы использовать эту функцию, ведущее приложение должно задать параметр NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span><span class="sxs-lookup"><span data-stu-id="ec169-308">To use this feature, the host application must define NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL.</span></span> <span data-ttu-id="ec169-309">Если этот параметр определен, служба *nx_dhcp_create* не создаст пул пакетов клиента.</span><span class="sxs-lookup"><span data-stu-id="ec169-309">When defined, the *nx_dhcp_create* service will not create the Client’s packet pool.</span></span> <span data-ttu-id="ec169-310">В приложении рекомендуется использовать значения по умолчанию для полезных данных пула пакетов DHCP-клиента, которые определяются в параметре NX_DHCP_PACKET_PAYLOAD в файле *nxd_dhcp_client.h* при создании пула пакетов.</span><span class="sxs-lookup"><span data-stu-id="ec169-310">Note that the application is recommended to use the default values for the DHCP client packet pool payload, defined as NX_DHCP_PACKET_PAYLOAD in *nx_dhcp.h* when creating the packet pool.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-311">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-311">Input Parameters</span></span>

- <span data-ttu-id="ec169-312">**dhcp_ptr**: указатель на блок управления DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-312">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="ec169-313">**packet_pool_ptr**: указатель на созданный ранее пул пакетов.</span><span class="sxs-lookup"><span data-stu-id="ec169-313">**packet_pool_ptr** Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-314">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-314">Return Values</span></span>

- <span data-ttu-id="ec169-315">**NX_SUCCESS** (0x00): пул пакетов DHCP-клиента задан.</span><span class="sxs-lookup"><span data-stu-id="ec169-315">**NX_SUCCESS** (0x00) DHCP Client packet pool is set</span></span>

- <span data-ttu-id="ec169-316">**NX_NOT_ENABLED** (0x14): служба не включена.</span><span class="sxs-lookup"><span data-stu-id="ec169-316">**NX_NOT_ENABLED** (0x14) Service is not enabled</span></span>

- <span data-ttu-id="ec169-317">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-317">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="ec169-318">NX_DHCP_INVALID_PAYLOAD (0x9C): слишком маленький размер полезных данных.</span><span class="sxs-lookup"><span data-stu-id="ec169-318">NX_DHCP_INVALID_PAYLOAD (0x9C) Payload is too small</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-319">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-319">Allowed From</span></span>

<span data-ttu-id="ec169-320">Код приложения</span><span class="sxs-lookup"><span data-stu-id="ec169-320">Application code</span></span>

### <a name="example"></a><span data-ttu-id="ec169-321">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-321">Example</span></span>

```C
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
        NX_DHCP_PACKET_PAYLOAD, pointer, (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool. */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set. */
```

## <a name="nx_dhcp_request_client_ip"></a><span data-ttu-id="ec169-322">nx_dhcp_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="ec169-322">nx_dhcp_request_client_ip</span></span>

<span data-ttu-id="ec169-323">Задание запрошенного IP-адреса для экземпляра DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-323">Set requested IP address for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-324">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-324">Prototype</span></span>

```C
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr,
                                ULONG client_ip_address,
                                UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="ec169-325">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-325">Description</span></span>

<span data-ttu-id="ec169-326">Эта служба задает IP-адрес, запрашиваемый DHCP-клиентом у DHCP-сервера, для первого интерфейса, для которого включен протокол DHCP в записи DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="ec169-326">This service sets the IP address for the DHCP Client to request from the DHCP Server on the first interface enabled for DHCP in the DHCP Client record.</span></span> <span data-ttu-id="ec169-327">Если установлен флаг *skip_discover_message*, DHCP-клиент пропускает сообщение об обнаружении и отправляет сообщение запроса.</span><span class="sxs-lookup"><span data-stu-id="ec169-327">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

<span data-ttu-id="ec169-328">Чтобы настроить запрос определенного IP-адреса для сообщений DHCP через определенный интерфейс, используйте службу *nx_dhcp_interface_request_client_ip*.</span><span class="sxs-lookup"><span data-stu-id="ec169-328">To set the request for a specific IP for DHCP messages on a specific interface, use the *nx_dhcp_interface_request_client_ip* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-329">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-329">Input Parameters</span></span>

- <span data-ttu-id="ec169-330">**dhcp_ptr**: указатель на блок управления DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-330">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="ec169-331">**client_ip_address**: IP-адрес, запрашиваемый у DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="ec169-331">**client_ip_address** IP address to request from DHCP server</span></span>

- <span data-ttu-id="ec169-332">**skip_discover_message**: если задано значение true, DHCP-клиент отправляет сообщение запроса.</span><span class="sxs-lookup"><span data-stu-id="ec169-332">**skip_discover_message** If true, DHCP Client sends Request message</span></span>  
<span data-ttu-id="ec169-333">Если значение равно false, отправляется сообщение об обнаружении.</span><span class="sxs-lookup"><span data-stu-id="ec169-333">If false, it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-334">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-334">Return Values</span></span>

- <span data-ttu-id="ec169-335">**NX_SUCCESS** (0x00): запрошенный IP-адрес задан.</span><span class="sxs-lookup"><span data-stu-id="ec169-335">**NX_SUCCESS** (0x00) Requested IP address is set.</span></span>

- <span data-ttu-id="ec169-336">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4): для интерфейса не включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-336">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="ec169-337">NX_PTR_ERROR (0x16): недопустимый указатель IP или DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-337">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="ec169-338">NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-338">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>
 
### <a name="allowed-from"></a><span data-ttu-id="ec169-339">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-339">Allowed From</span></span>

<span data-ttu-id="ec169-340">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-340">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-341">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-341">Example</span></span>

```C
/* Set the DHCP Client requested IP address and skip the discover message. */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_interface_request_client_ip"></a><span data-ttu-id="ec169-342">nx_dhcp_interface_request_client_ip</span><span class="sxs-lookup"><span data-stu-id="ec169-342">nx_dhcp_interface_request_client_ip</span></span>

<span data-ttu-id="ec169-343">Задание запрошенного IP-адреса для экземпляра DHCP на указанном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="ec169-343">Set requested IP address for DHCP instance on specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-344">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-344">Prototype</span></span>

```C
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr,
                                        UINT interface_index,
                                        ULONG client_ip_address,
                                        UINT skip_discover_message);
```

### <a name="description"></a><span data-ttu-id="ec169-345">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-345">Description</span></span>

<span data-ttu-id="ec169-346">Эта служба задает IP-адрес, запрашиваемый DHCP-клиентом у DHCP-сервера, для указанного интерфейса, если для него включен протокол DHCP (см. описание службы *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="ec169-346">This service sets the IP address for the DHCP Client to request from the DHCP Server on the specified interface, if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="ec169-347">Если установлен флаг *skip_discover_message*, DHCP-клиент пропускает сообщение об обнаружении и отправляет сообщение запроса.</span><span class="sxs-lookup"><span data-stu-id="ec169-347">If the *skip_discover_message* flag is set, the DHCP Client skips the Discover message and sends a Request message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-348">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-348">Input Parameters</span></span>

- <span data-ttu-id="ec169-349">**dhcp_ptr**: указатель на блок управления DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-349">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="ec169-350">**Interface_index**: индекс интерфейса для запроса IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="ec169-350">**Interface_index** Index of interface to request IP address on</span></span>

- <span data-ttu-id="ec169-351">**client_ip_address**: IP-адрес, запрашиваемый у DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="ec169-351">**client_ip_address** IP address to request from DHCP server</span></span>

- <span data-ttu-id="ec169-352">**skip_discover_message**: если задано значение true, DHCP-клиент отправляет сообщение запроса; в противном случае отправляется сообщение об обнаружении.</span><span class="sxs-lookup"><span data-stu-id="ec169-352">**skip_discover_message** If true, DHCP Client sends Request message; else it sends the Discover message.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-353">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-353">Return Values</span></span>

- <span data-ttu-id="ec169-354">**NX_SUCCESS** (0x00): запрошенный IP-адрес задан.</span><span class="sxs-lookup"><span data-stu-id="ec169-354">**NX_SUCCESS** (0x00) Requested IP address is set.</span></span>

- <span data-ttu-id="ec169-355">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4): для интерфейса не включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-355">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="ec169-356">NX_PTR_ERROR (0x16): недопустимый указатель IP или DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-356">NX_PTR_ERROR (0x16) Invalid IP or DHCP pointer</span></span>

- <span data-ttu-id="ec169-357">NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-357">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>


### <a name="allowed-from"></a><span data-ttu-id="ec169-358">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-358">Allowed From</span></span>

<span data-ttu-id="ec169-359">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-359">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-360">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-360">Example</span></span>

```C
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0. */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_reinitialize"></a><span data-ttu-id="ec169-361">nx_dhcp_reinitialize</span><span class="sxs-lookup"><span data-stu-id="ec169-361">nx_dhcp_reinitialize</span></span>

<span data-ttu-id="ec169-362">Сброс параметров сети DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="ec169-362">Clear the DHCP client network parameters</span></span> 

### <a name="prototype"></a><span data-ttu-id="ec169-363">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-363">Prototype</span></span>

```C
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ec169-364">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-364">Description</span></span>

<span data-ttu-id="ec169-365">Эта служба сбрасывает параметры сети ведущего приложения (IP-адрес, сетевой адрес и маску сети) и очищает состояние DHCP-клиента на всех интерфейсах, для которых включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-365">This service clears the host application network parameters (IP address, network address and network mask), and clears the DHCP Client state on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ec169-366">Она используется в сочетании с *nx_dhcp_stop* и *nx_dhcp_start* для перезапуска конечного автомата DHCP:</span><span class="sxs-lookup"><span data-stu-id="ec169-366">It is used in combination with *nx_dhcp_stop* and *nx_dhcp_start* to ‘restart’ the DHCP state machine:</span></span> 

<span data-ttu-id="ec169-367">nx_dhcp_stop(&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="ec169-367">nx_dhcp_stop(&my_dhcp);</span></span>  
<span data-ttu-id="ec169-368">nx_dhcp_reinitialize(&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="ec169-368">nx_dhcp_reinitialize(&my_dhcp);</span></span>  
<span data-ttu-id="ec169-369">nx_dhcp_start(&my_dhcp);</span><span class="sxs-lookup"><span data-stu-id="ec169-369">nx_dhcp_start(&my_dhcp);</span></span>


<span data-ttu-id="ec169-370">Для повторной инициализации DHCP-клиента на определенном интерфейсе, когда протокол DHCP включен для нескольких интерфейсов, используйте службу *nx_dhcp_interface_reinitialize*.</span><span class="sxs-lookup"><span data-stu-id="ec169-370">To reinitialize the DHCP Client on a specific interface when multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_reinitialize* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-371">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-371">Input Parameters</span></span>

- <span data-ttu-id="ec169-372">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-372">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-373">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-373">Return Values</span></span>

- <span data-ttu-id="ec169-374">**NX_SUCCESS** (0x00): протокол DHCP инициализирован повторно.</span><span class="sxs-lookup"><span data-stu-id="ec169-374">**NX_SUCCESS** (0x00) DHCP successfully reinitialized</span></span> 

- <span data-ttu-id="ec169-375">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-375">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-376">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-376">Allowed From</span></span>

<span data-ttu-id="ec169-377">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-377">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-378">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-378">Example</span></span>

```C
/* Reinitialize the previously started DHCP client. */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a><span data-ttu-id="ec169-379">nx_dhcp_interface_reinitialize</span><span class="sxs-lookup"><span data-stu-id="ec169-379">nx_dhcp_interface_reinitialize</span></span>

<span data-ttu-id="ec169-380">Сброс параметров сети DHCP-клиента для указанного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ec169-380">Clear the DHCP client network parameters on the specified interface</span></span> 

### <a name="prototype"></a><span data-ttu-id="ec169-381">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-381">Prototype</span></span>

```C
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ec169-382">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-382">Description</span></span>

<span data-ttu-id="ec169-383">Эта служба сбрасывает параметры сети (IP-адрес, сетевой адрес и маску сети) для указанного интерфейса, если для него включен протокол DHCP (см. описание службы *nx_dhcp_interface_enable*).</span><span class="sxs-lookup"><span data-stu-id="ec169-383">This service clears the network parameters (IP address, network address and network mask) on the specified interface if that interface is enabled for DHCP (see *nx_dhcp_interface_enable*).</span></span> <span data-ttu-id="ec169-384">Дополнительные сведения см. в описании службы *nx_dhcp_reinitialize*.</span><span class="sxs-lookup"><span data-stu-id="ec169-384">See *nx_dhcp_reinitialize* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-385">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-385">Input Parameters</span></span>

- <span data-ttu-id="ec169-386">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-386">**dhcp_ptr** Pointer to previously created DHCP instance</span></span>

- <span data-ttu-id="ec169-387">**interface_index**: индекс интерфейса, который нужно инициализировать повторно.</span><span class="sxs-lookup"><span data-stu-id="ec169-387">**interface_index** Index of interface to reinitialize.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-388">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-388">Return Values</span></span>

- <span data-ttu-id="ec169-389">**NX_SUCCESS** (0x00): интерфейс инициализирован повторно.</span><span class="sxs-lookup"><span data-stu-id="ec169-389">**NX_SUCCESS** (0x00) Interface successfully reinitialized</span></span>

- <span data-ttu-id="ec169-390">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4): для интерфейса не включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-390">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="ec169-391">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-391">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="ec169-392">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-392">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="ec169-393">NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-393">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-394">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-394">Allowed From</span></span>

<span data-ttu-id="ec169-395">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-395">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-396">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-396">Example</span></span>

```C
/* Reinitialize the previously started DHCP client on interface 1. */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a><span data-ttu-id="ec169-397">nx_dhcp_release</span><span class="sxs-lookup"><span data-stu-id="ec169-397">nx_dhcp_release</span></span>

<span data-ttu-id="ec169-398">Освобождение арендованного IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="ec169-398">Release Leased IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-399">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-399">Prototype</span></span>

```C
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ec169-400">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-400">Description</span></span>

<span data-ttu-id="ec169-401">Эта служба освобождает IP-адрес, полученный от DHCP-сервера, отправляя на него сообщение RELEASE.</span><span class="sxs-lookup"><span data-stu-id="ec169-401">This service releases the IP address obtained from a DHCP server by sending the RELEASE message to that server.</span></span> <span data-ttu-id="ec169-402">Затем она повторно инициализирует DHCP-клиент.</span><span class="sxs-lookup"><span data-stu-id="ec169-402">It then reinitializes the DHCP Client.</span></span> <span data-ttu-id="ec169-403">Эта служба применяется ко всем интерфейсам, для которых включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-403">This service is applied to all interfaces enabled for DHCP.</span></span>

<span data-ttu-id="ec169-404">Приложение может перезапустить DHCP-клиент, вызвав *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="ec169-404">The application can restart the DHCP Client by calling *nx_dhcp_start*.</span></span>

<span data-ttu-id="ec169-405">Чтобы вернуть адрес DHCP-серверу на определенном интерфейсе, используйте службу *nx_dhcp_interface_release*.</span><span class="sxs-lookup"><span data-stu-id="ec169-405">To release an address back to the DHCP server on a specific interface, use the *nx_dhcp_interface_release* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-406">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-406">Input Parameters</span></span>

- <span data-ttu-id="ec169-407">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-407">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-408">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-408">Return Values</span></span>

- <span data-ttu-id="ec169-409">**NX_SUCCESS** (0x00): экземпляр DHCP успешно освобожден.</span><span class="sxs-lookup"><span data-stu-id="ec169-409">**NX_SUCCESS** (0x00) Successful DHCP release.</span></span>  

- <span data-ttu-id="ec169-410">**NX_DHCP_NOT_BOUND** (0x94): IP-адрес не был арендован, поэтому его невозможно освободить.</span><span class="sxs-lookup"><span data-stu-id="ec169-410">**NX_DHCP_NOT_BOUND** (0x94) The IP address has not been leased so it can’t be released.</span></span>

- <span data-ttu-id="ec169-411">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-411">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="ec169-412">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-412">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-413">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-413">Allowed From</span></span>

<span data-ttu-id="ec169-414">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-414">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-415">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-415">Example</span></span>

```C
/* Release the previously leased IP address. */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_interface_release"></a><span data-ttu-id="ec169-416">nx_dhcp_interface_release</span><span class="sxs-lookup"><span data-stu-id="ec169-416">nx_dhcp_interface_release</span></span>

<span data-ttu-id="ec169-417">Освобождение IP-адреса на указанном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="ec169-417">Release IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-418">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-418">Prototype</span></span>

```C
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ec169-419">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-419">Description</span></span>

<span data-ttu-id="ec169-420">Эта служба освобождает IP-адрес, полученный от DHCP-сервера, на указанном интерфейсе и повторно инициализирует DHCP-клиент.</span><span class="sxs-lookup"><span data-stu-id="ec169-420">This service releases the IP address obtained from a DHCP server on the specified interface and reinitializes the DHCP Client.</span></span> <span data-ttu-id="ec169-421">DHCP-клиент можно перезапустить, вызвав *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="ec169-421">The DHCP Client can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-422">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-422">Input Parameters</span></span>

- <span data-ttu-id="ec169-423">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-423">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-424">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-424">Return Values</span></span>

- <span data-ttu-id="ec169-425">**NX_SUCCESS** (0x00): экземпляр DHCP успешно освобожден.</span><span class="sxs-lookup"><span data-stu-id="ec169-425">**NX_SUCCESS** (0x00) Successful DHCP release.</span></span>

- <span data-ttu-id="ec169-426">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4): для интерфейса не включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-426">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="ec169-427">**NX_DHCP_NOT_BOUND** (0x94): IP-адрес не был арендован, поэтому его невозможно освободить.</span><span class="sxs-lookup"><span data-stu-id="ec169-427">**NX_DHCP_NOT_BOUND** (0x94) The IP address has not been leased so it can’t be released.</span></span>

- <span data-ttu-id="ec169-428">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-428">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="ec169-429">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-429">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="ec169-430">NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-430">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-431">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-431">Allowed From</span></span>

<span data-ttu-id="ec169-432">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-432">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-433">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-433">Example</span></span>

```C
/* Release the previously leased IP address on interface 1. */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_decline"></a><span data-ttu-id="ec169-434">nx_dhcp_decline</span><span class="sxs-lookup"><span data-stu-id="ec169-434">nx_dhcp_decline</span></span>

<span data-ttu-id="ec169-435">Отклонение IP-адреса от DHCP-сервера.</span><span class="sxs-lookup"><span data-stu-id="ec169-435">Decline IP address from DHCP Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-436">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-436">Prototype</span></span>

```C
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ec169-437">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-437">Description</span></span>

<span data-ttu-id="ec169-438">Эта служба отклоняет IP-адрес, арендованный у DHCP-сервера, на всех интерфейсах, для которых включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-438">This service declines an IP address leased from the DHCP server on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ec169-439">Когда задан параметр NX_DHCP_CLIENT_SEND_ARP_PROBE, DHCP-клиент отправляет сообщение DECLINE, если обнаруживает, что IP-адрес уже занят.</span><span class="sxs-lookup"><span data-stu-id="ec169-439">If NX_DHCP_CLIENT_ SEND_ ARP_PROBE is defined, the DHCP Client will send a DECLINE message if it detects that the IP address is already in use.</span></span> <span data-ttu-id="ec169-440">Дополнительные сведения о настройке проб ARP в клиенте NetX DHCP см. в разделе **Пробы ARP** главы 1.</span><span class="sxs-lookup"><span data-stu-id="ec169-440">See **ARP Probes** in Chapter One for more information on ARP probe configuration in the NetX DHCP Client.</span></span>

<span data-ttu-id="ec169-441">Приложение может использовать эту службу для отклонения IP-адреса, если обнаруживает, что адрес используется каким-либо иным образом.</span><span class="sxs-lookup"><span data-stu-id="ec169-441">The application can use this service to decline its IP address if it discovers the address is in use by other means.</span></span>

<span data-ttu-id="ec169-442">Эта служба повторно инициализирует DHCP-клиент, чтобы его можно было перезапустить, вызвав *nx_dhcp_start*.</span><span class="sxs-lookup"><span data-stu-id="ec169-442">This service reinitializes the DHCP Client to that it can be restarted by calling *nx_dhcp_start*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-443">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-443">Input Parameters</span></span>

- <span data-ttu-id="ec169-444">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-444">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-445">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-445">Return Values</span></span>

- <span data-ttu-id="ec169-446">**NX_SUCCESS** (0x00): отклонение успешно выполнено.</span><span class="sxs-lookup"><span data-stu-id="ec169-446">**NX_SUCCESS** (0x00) Decline successfully sent</span></span>  

- <span data-ttu-id="ec169-447">**NX_DHCP_NOT_STARTED** (0x96): экземпляр DHCP не запущен.</span><span class="sxs-lookup"><span data-stu-id="ec169-447">**NX_DHCP_NOT_STARTED** (0x96) The DHCP instance not started</span></span>

- <span data-ttu-id="ec169-448">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-448">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="ec169-449">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-449">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-450">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-450">Allowed From</span></span>

<span data-ttu-id="ec169-451">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-451">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-452">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-452">Example</span></span>

```C
/* Decline the IP address offered by the DHCP server. */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was 
   successfully trasnmitted. */
```

## <a name="nx_dhcp_interface_decline"></a><span data-ttu-id="ec169-453">nx_dhcp_interface_decline</span><span class="sxs-lookup"><span data-stu-id="ec169-453">nx_dhcp_interface_decline</span></span>

<span data-ttu-id="ec169-454">Отклонение IP-адреса от DHCP-сервера на указанном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="ec169-454">Decline IP address from DHCP Server on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-455">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-455">Prototype</span></span>

```C
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ec169-456">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-456">Description</span></span>

<span data-ttu-id="ec169-457">Эта служба отправляет сообщение DECLINE на сервер, чтобы отклонить IP-адрес, назначенный DHCP-сервером.</span><span class="sxs-lookup"><span data-stu-id="ec169-457">This service sends the DECLINE message to the server to decline an IP address assigned by the DHCP server.</span></span> <span data-ttu-id="ec169-458">Она также повторно инициализирует DHCP-клиент.</span><span class="sxs-lookup"><span data-stu-id="ec169-458">It also reinitializes the DHCP Client.</span></span> <span data-ttu-id="ec169-459">Дополнительные сведения см. в описании службы *nx_dhcp_decline*.</span><span class="sxs-lookup"><span data-stu-id="ec169-459">See *nx_dhcp_decline* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-460">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-460">Input Parameters</span></span>

- <span data-ttu-id="ec169-461">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-461">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="ec169-462">**Interface_index**: индекс интерфейса для отклонения IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="ec169-462">**Interface_index** Index of interface to decline IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-463">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-463">Return Values</span></span>

- <span data-ttu-id="ec169-464">**NX_SUCCESS** (0x00): отправлено сообщение об отклонении DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-464">**NX_SUCCESS** (0x00) DHCP decline message sent</span></span>  

- <span data-ttu-id="ec169-465">**NX_DHCP_NOT_BOUND** (0x94): DHCP-клиент не привязан.</span><span class="sxs-lookup"><span data-stu-id="ec169-465">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound</span></span>

- <span data-ttu-id="ec169-466">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4): для интерфейса не включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-466">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="ec169-467">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-467">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="ec169-468">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-468">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="ec169-469">NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-469">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-470">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-470">Allowed From</span></span>

<span data-ttu-id="ec169-471">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-471">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-472">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-472">Example</span></span>
```C
/* Decline the IP address offered by the DHCP server on interface 2. */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was
   successfully trasnmitted. */
```

## <a name="nx_dhcp_send_request"></a><span data-ttu-id="ec169-473">nx_dhcp_send_request</span><span class="sxs-lookup"><span data-stu-id="ec169-473">nx_dhcp_send_request</span></span>

<span data-ttu-id="ec169-474">Отправка сообщения DHCP на сервер.</span><span class="sxs-lookup"><span data-stu-id="ec169-474">Send DHCP message to Server</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-475">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-475">Prototype</span></span>

```C
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="ec169-476">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-476">Description</span></span>

<span data-ttu-id="ec169-477">Эта служба отправляет указанное сообщение DHCP на DHCP-сервер через первый интерфейс, для которого включен протокол DHCP, найденный в записи DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="ec169-477">This service sends the specified DHCP message to the DHCP server on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="ec169-478">Чтобы отправить сообщение RELEASE или DECLINE, приложение должно использовать службу *nx_dhcp[_interface]_release()* или *nx_dhcp_interface_decline()* соответственно.</span><span class="sxs-lookup"><span data-stu-id="ec169-478">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="ec169-479">Для использования этой службы DHCP-клиент должен быть запущен, за исключением отправки сообщений типа INFORM_REQUEST.</span><span class="sxs-lookup"><span data-stu-id="ec169-479">The DHCP Client must be started to use this service except for sending the INFORM_REQUEST message type.</span></span>

> [!NOTE] 
> <span data-ttu-id="ec169-480">Эта служба не предназначена для запуска конечного автомата DHCP-клиента ведущим приложением.</span><span class="sxs-lookup"><span data-stu-id="ec169-480">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-481">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-481">Input Parameters</span></span>

- <span data-ttu-id="ec169-482">**dhcp_ptr**: указатель на блок управления DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-482">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="ec169-483">**dhcp_message_type**: запрос сообщения (определен в *nx_dhcp.h*).</span><span class="sxs-lookup"><span data-stu-id="ec169-483">**dhcp_message_type** Message request (defined in *nx_dhcp.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-484">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-484">Return Values</span></span>

- <span data-ttu-id="ec169-485">**NX_SUCCESS** (0x00): сообщение DHCP отправлено.</span><span class="sxs-lookup"><span data-stu-id="ec169-485">**NX_SUCCESS** (0x00) DHCP message sent</span></span>  

- <span data-ttu-id="ec169-486">**NX_DHCP_NOT_STARTED** (0x96): недопустимый индекс интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ec169-486">**NX_DHCP_NOT_STARTED** (0x96) Invalid interface index</span></span>

- <span data-ttu-id="ec169-487">**NX_DHCP_INVALID_MESSAGE** (0x9B): недопустимый тип отправляемого сообщения.</span><span class="sxs-lookup"><span data-stu-id="ec169-487">**NX_DHCP_INVALID_MESSAGE** (0x9B) Invalid message type to send</span></span>

- <span data-ttu-id="ec169-488">NX_PTR_ERROR (0x16): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="ec169-488">NX_PTR_ERROR (0x16) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-489">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-489">Allowed From</span></span>

<span data-ttu-id="ec169-490">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-490">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-491">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-491">Example</span></span>

```C
/* Send the DHCP INFORM REQUEST message to the server. */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_interface_send_request"></a><span data-ttu-id="ec169-492">nx_dhcp_interface_send_request</span><span class="sxs-lookup"><span data-stu-id="ec169-492">nx_dhcp_interface_send_request</span></span>

<span data-ttu-id="ec169-493">Отправка сообщения DHCP на сервер через указанный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-493">Send DHCP message to Server on a specific interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-494">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-494">Prototype</span></span>

```C
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr,
                                    UINT interface_index,
                                    UINT dhcp_message_type);
```

### <a name="description"></a><span data-ttu-id="ec169-495">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-495">Description</span></span>

<span data-ttu-id="ec169-496">Эта служба отправляет сообщение на DHCP-сервер через указанный интерфейс, если для него включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-496">This service sends a message to the DHCP server on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="ec169-497">Чтобы отправить сообщение RELEASE или DECLINE, приложение должно использовать службу *nx_dhcp[_interface]_release()* или *nx_dhcp_interface_decline()* соответственно.</span><span class="sxs-lookup"><span data-stu-id="ec169-497">To send a RELEASE or DECLINE message, the application must use the *nx_dhcp[_interface]_release*() or *nx_dhcp_interface_decline()* services respectively.</span></span>

<span data-ttu-id="ec169-498">Для использования этой службы DHCP-клиент должен быть запущен, за исключением отправки сообщений DHCP типа INFORM_REQUEST.</span><span class="sxs-lookup"><span data-stu-id="ec169-498">The DHCP Client must be started to use this service except for sending the DHCP INFORM REQUEST message type.</span></span>

<span data-ttu-id="ec169-499">Эта служба не предназначена для запуска конечного автомата DHCP-клиента ведущим приложением.</span><span class="sxs-lookup"><span data-stu-id="ec169-499">This service is not intended for the host application to ‘drive’ the DHCP Client state machine.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-500">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-500">Input Parameters</span></span>

- <span data-ttu-id="ec169-501">**dhcp_ptr**: указатель на блок управления DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-501">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="ec169-502">**interface_index**: индекс интерфейса для отправки сообщения.</span><span class="sxs-lookup"><span data-stu-id="ec169-502">**Interface_index** Index of interface to send message on</span></span>  

- <span data-ttu-id="ec169-503">**dhcp_message_type**: запрос сообщения (определен в *nx_dhcp.h*).</span><span class="sxs-lookup"><span data-stu-id="ec169-503">**dhcp_message_type** Message request (defined in *nx_dhcp.h*)</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-504">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-504">Return Values</span></span>

- <span data-ttu-id="ec169-505">**NX_SUCCESS** (0x00): сообщение DHCP отправлено.</span><span class="sxs-lookup"><span data-stu-id="ec169-505">**NX_SUCCESS** (0x00) DHCP message sent</span></span>  

- <span data-ttu-id="ec169-506">**NX_DHCP_NOT_STARTED** (0x96): недопустимый индекс интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ec169-506">**NX_DHCP_NOT_STARTED** (0x96) Invalid interface index</span></span>

- <span data-ttu-id="ec169-507">**NX_DHCP_INVALID_MESSAGE** (0x9B): недопустимый тип отправляемого сообщения.</span><span class="sxs-lookup"><span data-stu-id="ec169-507">**NX_DHCP_INVALID_MESSAGE** (0x9B) Invalid message type to send</span></span>

- <span data-ttu-id="ec169-508">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4): для интерфейса не включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-508">**NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) Interface not enabled for DHCP</span></span>

- <span data-ttu-id="ec169-509">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-509">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="ec169-510">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-510">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="ec169-511">NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-511">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-512">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-512">Allowed From</span></span>

<span data-ttu-id="ec169-513">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-513">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-514">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-514">Example</span></span>

```C
/* Send the INFORM REQUEST message to the server on the primary interface. */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_server_address_get"></a><span data-ttu-id="ec169-515">nx_dhcp_server_address_get</span><span class="sxs-lookup"><span data-stu-id="ec169-515">nx_dhcp_server_address_get</span></span>

<span data-ttu-id="ec169-516">Получение IP-адреса DHCP-сервера для DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="ec169-516">Get the DHCP Client’s DHCP server IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-517">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-517">Prototype</span></span>

```C
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr,
                                ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="ec169-518">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-518">Description</span></span>

<span data-ttu-id="ec169-519">Эта служба получает IP-адрес DHCP-сервера для DHCP-клиента через первый интерфейс, для которого включен протокол DHCP, найденный в записи DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="ec169-519">This service retrieves the DHCP Client DHCP server IP address on the first interface enabled for DHCP found in the DHCP Client record.</span></span> <span data-ttu-id="ec169-520">Вызывающая сторона может использовать эту службу только после привязки DHCP-клиента к IP-адресу, назначенному DHCP-сервером.</span><span class="sxs-lookup"><span data-stu-id="ec169-520">The caller can only use this service after the DHCP Client is bound to an IP address assigned by the DHCP Server.</span></span> <span data-ttu-id="ec169-521">Ведущее приложение может использовать службу *nx_ip_status_check* для проверки того, задан ли IP-адрес, или использовать nx *_dhcp_state_change_notify* и проверить, находится ли DHCP-клиент в состоянии NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="ec169-521">The host application can use the *nx_ip_status_check* service to verify IP address is set, or it can use the *nx_dhcp_state_change_notify* and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="ec169-522">Дополнительные сведения о настройке функции обратного вызова для изменения состояния см. в описании функции *nx_dhcp_state_change_notify*.</span><span class="sxs-lookup"><span data-stu-id="ec169-522">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

<span data-ttu-id="ec169-523">Чтобы найти DHCP-сервер на определенном интерфейсе, когда для DHCP-клиента включено несколько интерфейсов, используйте службу *nx_dhcp_interface_server_address_get*.</span><span class="sxs-lookup"><span data-stu-id="ec169-523">To find the DHCP server on a specific interface when multiple interfaces are enabled for DHCP Client, use the *nx_dhcp_interface_server_address_get* service</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-524">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-524">Input Parameters</span></span>

- <span data-ttu-id="ec169-525">**dhcp_ptr**: указатель на блок управления DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-525">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="ec169-526">**server_address**: указатель на IP-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="ec169-526">**server_address** Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-527">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-527">Return Values</span></span>

- <span data-ttu-id="ec169-528">**NX_SUCCESS** (0x00): адрес DHCP-сервера возвращен.</span><span class="sxs-lookup"><span data-stu-id="ec169-528">**NX_SUCCESS** (0x00) DHCP server address returned</span></span>

- <span data-ttu-id="ec169-529">NX_PTR_ERROR (0x16): недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="ec169-529">NX_PTR_ERROR (0x16) Invalid input pointer</span></span>

- <span data-ttu-id="ec169-530">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-530">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-531">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-531">Allowed From</span></span>

<span data-ttu-id="ec169-532">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-532">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-533">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-533">Example</span></span>

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
    }
```

## <a name="nx_dhcp_interface_server_address_get"></a><span data-ttu-id="ec169-534">nx_dhcp_interface_server_address_get</span><span class="sxs-lookup"><span data-stu-id="ec169-534">nx_dhcp_interface_server_address_get</span></span>

<span data-ttu-id="ec169-535">Получение IP-адреса DHCP-сервера для DHCP-клиента на указанном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="ec169-535">Get the DHCP Client’s DHCP server IP address on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-536">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-536">Prototype</span></span>

```C
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            ULONG server_address);
```

### <a name="description"></a><span data-ttu-id="ec169-537">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-537">Description</span></span>

<span data-ttu-id="ec169-538">Эта служба получает IP-адрес DHCP-сервера для DHCP-клиента на указанном интерфейсе, если для него включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-538">This service retrieves the DHCP Client DHCP server IP address on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="ec169-539">DHCP-клиент должен находиться в состоянии BOUND.</span><span class="sxs-lookup"><span data-stu-id="ec169-539">The DHCP Client must be in the Bound state.</span></span> <span data-ttu-id="ec169-540">После запуска DHCP-клиента на этом интерфейсе ведущее приложение может либо использовать службу *nx_ip_status_check*, чтобы проверить, задан ли IP-адрес, либо использовать обратный вызов для изменения состояния DHCP-клиента и проверить, находится ли DHCP-клиент в состоянии NX_DHCP_STATE_BOUND.</span><span class="sxs-lookup"><span data-stu-id="ec169-540">After starting the DHCP Client on that interface, the host application can either use the *nx_ip_status_check* service to verify the IP address is set, or it can use the DHCP Client state change callback and query the DHCP Client state is NX_DHCP_STATE_BOUND.</span></span> <span data-ttu-id="ec169-541">Дополнительные сведения о настройке функции обратного вызова для изменения состояния см. в описании функции *nx_dhcp_state_change_notify*.</span><span class="sxs-lookup"><span data-stu-id="ec169-541">See *nx_dhcp_state_change_notify* for more details about setting the state change callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-542">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-542">Input Parameters</span></span>

- <span data-ttu-id="ec169-543">**dhcp_ptr**: указатель на блок управления DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-543">**dhcp_ptr** Pointer to DHCP control block.</span></span>

- <span data-ttu-id="ec169-544">**interface_index**: индекс интерфейса для получения IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="ec169-544">**Interface_index** Index of interface to obtain IP address</span></span>  

- <span data-ttu-id="ec169-545">**server_address**: указатель на IP-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="ec169-545">**server_address** Pointer to server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-546">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-546">Return Values</span></span>

- <span data-ttu-id="ec169-547">**NX_SUCCESS** (0x00): адрес DHCP-сервера возвращен.</span><span class="sxs-lookup"><span data-stu-id="ec169-547">**NX_SUCCESS** (0x00) DHCP server address returned</span></span>

- <span data-ttu-id="ec169-548">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5): протокол DHCP не включен ни для одного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ec169-548">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces enabled for DHCP</span></span>

- <span data-ttu-id="ec169-549">**NX_DHCP_NOT_BOUND** (0x94): DHCP-клиент не привязан.</span><span class="sxs-lookup"><span data-stu-id="ec169-549">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound</span></span>

- <span data-ttu-id="ec169-550">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-550">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

- <span data-ttu-id="ec169-551">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-551">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

- <span data-ttu-id="ec169-552">NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-552">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-553">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-553">Allowed From</span></span>

<span data-ttu-id="ec169-554">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-554">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-555">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-555">Example</span></span>

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    /* Get the DHCP server IP address on interface 1 */
    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                    &server_address);
    }
```

## <a name="nx_dhcp_set_interface_index"></a><span data-ttu-id="ec169-556">nx_dhcp_set_interface_index</span><span class="sxs-lookup"><span data-stu-id="ec169-556">nx_dhcp_set_interface_index</span></span>

<span data-ttu-id="ec169-557">Задание сетевого интерфейса для экземпляра DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-557">Set network interface for DHCP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-558">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-558">Prototype</span></span>

```C
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a><span data-ttu-id="ec169-559">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-559">Description</span></span>

<span data-ttu-id="ec169-560">Эта служба задает сетевой интерфейс для подключения экземпляра DHCP к DHCP-серверу, когда для DHCP-клиента настроен один сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-560">This service sets the network interface for the DHCP instance to connect to the DHCP Server on when running DHCP Client configured for a single network interface.</span></span>

<span data-ttu-id="ec169-561">По умолчанию DHCP-клиент выполняется на основном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="ec169-561">By default the DHCP Client runs on the primary interface.</span></span> <span data-ttu-id="ec169-562">Чтобы запустить DHCP-клиент на дополнительном интерфейсе, с помощью этой службы установите дополнительный интерфейс в качестве интерфейса DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="ec169-562">To run DHCP on a secondary service, use this service to set the secondary interface as the DHCP Client interface.</span></span> <span data-ttu-id="ec169-563">Приложение должно предварительно зарегистрировать указанный интерфейс в экземпляре IP с помощью службы *nx_ip_interface_attach*.</span><span class="sxs-lookup"><span data-stu-id="ec169-563">The application must previously register the specified interface to the IP instance using the *nx_ip_interface_attach* service.</span></span>

<span data-ttu-id="ec169-564">Эта служба предназначена для приложений, которые будут запускать DHCP-клиент только на одном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="ec169-564">Note that this service is intended for applications that intend to run the DHCP Client on only one interface.</span></span> <span data-ttu-id="ec169-565">Дополнительные сведения о запуске DHCP на нескольких интерфейсах см. в описании службы *nx_dhcp_interface_enable*.</span><span class="sxs-lookup"><span data-stu-id="ec169-565">To run DHCP on multiple interfaces see *nx_dhcp_interface_enable* for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-566">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-566">Input Parameters</span></span>

- <span data-ttu-id="ec169-567">**dhcp_ptr**: указатель на блок управления DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-567">**dhcp_ptr** Pointer to DHCP control block.</span></span>  

- <span data-ttu-id="ec169-568">**index**: индекс сетевого интерфейса устройства.</span><span class="sxs-lookup"><span data-stu-id="ec169-568">**index** Index of device network interface</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-569">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-569">Return Values</span></span>

- <span data-ttu-id="ec169-570">**NX_SUCCESS** (0x00): интерфейс успешно задан.</span><span class="sxs-lookup"><span data-stu-id="ec169-570">**NX_SUCCESS** (0x00) Interface is successfully set.</span></span>

- <span data-ttu-id="ec169-571">**NX_INVALID_INTERFACE** (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-571">**NX_INVALID_INTERFACE** (0x4C) Invalid network interface</span></span>

- <span data-ttu-id="ec169-572">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3): для интерфейса включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-572">**NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) Interface enabled for DHCP</span></span>

- <span data-ttu-id="ec169-573">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7): доступная запись отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ec169-573">**NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) No record available for another</span></span>

- <span data-ttu-id="ec169-574">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-574">NX_PTR_ERROR (0x16) Invalid DHCP pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-575">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-575">Allowed From</span></span>

<span data-ttu-id="ec169-576">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-576">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-577">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-577">Example</span></span>

```C
/* Set the DHCP Client interface to the secondary interface (index 1). */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set. */
```

## <a name="nx_dhcp_start"></a><span data-ttu-id="ec169-578">nx_dhcp_start</span><span class="sxs-lookup"><span data-stu-id="ec169-578">nx_dhcp_start</span></span>

<span data-ttu-id="ec169-579">Запуск обработки DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-579">Start DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-580">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-580">Prototype</span></span>

```C
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ec169-581">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-581">Description</span></span>

<span data-ttu-id="ec169-582">Эта служба запускает обработку DHCP на всех интерфейсах, для которых включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-582">This service starts DHCP processing on all interfaces enabled for DHCP.</span></span> <span data-ttu-id="ec169-583">По умолчанию протокол DHCP включен для основного интерфейса, когда приложение вызывает *nx_dhcp_create*.</span><span class="sxs-lookup"><span data-stu-id="ec169-583">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="ec169-584">Чтобы проверить, привязан ли экземпляр IP к IP-адресу на интерфейсе DHCP-клиента, используйте *nx_ip_status_check* для подтверждения допустимости IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="ec169-584">To verify when the IP instance is bound to an IP address on the DHCP Client interface, use *nx_ip_status_check* to see confirm the IP address is valid.</span></span>

<span data-ttu-id="ec169-585">Если протокол DHCP уже выполняется на других интерфейсах, эта служба не повлияет на них.</span><span class="sxs-lookup"><span data-stu-id="ec169-585">If there are other interfaces already running DHCP, this service will not affect them.</span></span>

<span data-ttu-id="ec169-586">Чтобы запустить DHCP на определенном интерфейсе, когда включено несколько интерфейсов, используйте службу *nx_dhcp_interface_start*.</span><span class="sxs-lookup"><span data-stu-id="ec169-586">To start DHCP on a specific interface when multiple interfaces are enabled, use the *nx_dhcp_interface_start* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-587">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-587">Input Parameters</span></span>

- <span data-ttu-id="ec169-588">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-588">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-589">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-589">Return Values</span></span>

- <span data-ttu-id="ec169-590">**NX_SUCCESS** (0x00): протокол DHCP успешно запущен.</span><span class="sxs-lookup"><span data-stu-id="ec169-590">**NX_SUCCESS** (0x00) Successful DHCP start.</span></span>  

- <span data-ttu-id="ec169-591">**NX_DHCP_ALREADY_STARTED** (0x93): протокол DHCP уже запущен.</span><span class="sxs-lookup"><span data-stu-id="ec169-591">**NX_DHCP_ALREADY_STARTED** (0x93) DHCP already started.</span></span>

- <span data-ttu-id="ec169-592">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-592">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="ec169-593">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-593">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-594">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-594">Allowed From</span></span>

<span data-ttu-id="ec169-595">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-595">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-596">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-596">Example</span></span>

```C
/* Start the DHCP processing for this IP instance. */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_interface_start"></a><span data-ttu-id="ec169-597">nx_dhcp_interface_start</span><span class="sxs-lookup"><span data-stu-id="ec169-597">nx_dhcp_interface_start</span></span>

<span data-ttu-id="ec169-598">Запуск обработки DHCP на указанном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="ec169-598">Start DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-599">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-599">Prototype</span></span>

```C
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ec169-600">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-600">Description</span></span>

<span data-ttu-id="ec169-601">Эта служба запускает обработку DHCP на указанном интерфейсе, если для него включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-601">This service starts DHCP processing on the specified interface if that interface is enabled for DHCP.</span></span> <span data-ttu-id="ec169-602">Дополнительные сведения о включении протокола DHCP на интерфейсе см. в описании службы *nx_dhcp_interface_enable()* .</span><span class="sxs-lookup"><span data-stu-id="ec169-602">See *nx_dhcp_interface_enable*() for more details about enabling an interface for DHCP.</span></span> <span data-ttu-id="ec169-603">По умолчанию протокол DHCP включен для основного интерфейса, когда приложение вызывает *nx_dhcp_create*.</span><span class="sxs-lookup"><span data-stu-id="ec169-603">By default the primary interface is enabled for DHCP when the application calls *nx_dhcp_create.*</span></span>

<span data-ttu-id="ec169-604">Если нет других интерфейсов, на которых выполняется DHCP-клиент, эта служба запустит или возобновит выполнение потока DHCP-клиента и (повторно) активирует таймер DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="ec169-604">If there are no other interfaces running DHCP Client this service will start/resume the DHCP Client thread and (re)activate the DHCP Client timer.</span></span>  
  
<span data-ttu-id="ec169-605">Приложение должно использовать *nx_ip_status_check*, чтобы проверить, получен ли IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="ec169-605">The application should use *nx_ip_status_check* to verify if an IP address is obtained.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-606">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-606">Input Parameters</span></span>

- <span data-ttu-id="ec169-607">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-607">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="ec169-608">**Interface_index**: индекс, по которому следует запустить DHCP-клиент.</span><span class="sxs-lookup"><span data-stu-id="ec169-608">**Interface_index** Index on which to start the DHCP Client</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-609">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-609">Return Values</span></span>

- <span data-ttu-id="ec169-610">**NX_SUCCESS** (0x00): протокол DHCP успешно запущен.</span><span class="sxs-lookup"><span data-stu-id="ec169-610">**NX_SUCCESS** (0x00) Successful DHCP start.</span></span>  

- <span data-ttu-id="ec169-611">**NX_DHCP_ALREADY_STARTED** (0X93): экземпляр DHCP уже запущен.</span><span class="sxs-lookup"><span data-stu-id="ec169-611">**NX_DHCP_ALREADY_STARTED** (0x93) The DHCP instance has already been started.</span></span>

- <span data-ttu-id="ec169-612">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-612">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="ec169-613">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-613">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="ec169-614">NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-614">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-615">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-615">Allowed From</span></span>

<span data-ttu-id="ec169-616">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-616">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-617">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-617">Example</span></span>

```C
/* Start the DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_state_change_notify"></a><span data-ttu-id="ec169-618">nx_dhcp_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="ec169-618">nx_dhcp_state_change_notify</span></span>

<span data-ttu-id="ec169-619">Задание функции обратного вызова для изменения состояния DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-619">Set DHCP state change callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-620">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-620">Prototype</span></span>

```C
UINT nx_dhcp_state_change_notify(
          NX_DHCP *dhcp_ptr, 
          VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                           UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="ec169-621">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-621">Description</span></span>

<span data-ttu-id="ec169-622">Эта служба регистрирует указанную функцию обратного вызова dhcp_state_change_notify для уведомления приложения об изменениях состояния DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-622">This service registers the specified callback function dhcp_state_change_notify for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="ec169-623">Функция обратного вызова предоставляет состояние, в которое перешел DHCP-клиент.</span><span class="sxs-lookup"><span data-stu-id="ec169-623">The callback function supplies the state the DHCP Client has transitioned into.</span></span>

<span data-ttu-id="ec169-624">Ниже приведены значения, связанные с различными состояниями DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-624">Following are values associated with the various DHCP states:</span></span>

| <span data-ttu-id="ec169-625">Состояние</span><span class="sxs-lookup"><span data-stu-id="ec169-625">State</span></span>                             | <span data-ttu-id="ec169-626">Значение</span><span class="sxs-lookup"><span data-stu-id="ec169-626">Value</span></span> |
|-----------------------------------|-------|
| <span data-ttu-id="ec169-627">NX\_DHCP\_STATE\_BOOT</span><span class="sxs-lookup"><span data-stu-id="ec169-627">NX\_DHCP\_STATE\_BOOT</span></span>             | <span data-ttu-id="ec169-628">1</span><span class="sxs-lookup"><span data-stu-id="ec169-628">1</span></span>     |
| <span data-ttu-id="ec169-629">NX\_DHCP\_STATE\_INIT</span><span class="sxs-lookup"><span data-stu-id="ec169-629">NX\_DHCP\_STATE\_INIT</span></span>             | <span data-ttu-id="ec169-630">2</span><span class="sxs-lookup"><span data-stu-id="ec169-630">2</span></span>     |
| <span data-ttu-id="ec169-631">NX\_DHCP\_STATE\_SELECTING</span><span class="sxs-lookup"><span data-stu-id="ec169-631">NX\_DHCP\_STATE\_SELECTING</span></span>        | <span data-ttu-id="ec169-632">3</span><span class="sxs-lookup"><span data-stu-id="ec169-632">3</span></span>     |
| <span data-ttu-id="ec169-633">NX\_DHCP\_STATE\_REQUESTING</span><span class="sxs-lookup"><span data-stu-id="ec169-633">NX\_DHCP\_STATE\_REQUESTING</span></span>       | <span data-ttu-id="ec169-634">4</span><span class="sxs-lookup"><span data-stu-id="ec169-634">4</span></span>     |
| <span data-ttu-id="ec169-635">NX\_DHCP\_STATE\_BOUND</span><span class="sxs-lookup"><span data-stu-id="ec169-635">NX\_DHCP\_STATE\_BOUND</span></span>            | <span data-ttu-id="ec169-636">5</span><span class="sxs-lookup"><span data-stu-id="ec169-636">5</span></span>     |
| <span data-ttu-id="ec169-637">NX\_DHCP\_STATE\_RENEWING</span><span class="sxs-lookup"><span data-stu-id="ec169-637">NX\_DHCP\_STATE\_RENEWING</span></span>         | <span data-ttu-id="ec169-638">6</span><span class="sxs-lookup"><span data-stu-id="ec169-638">6</span></span>     |
| <span data-ttu-id="ec169-639">NX\_DHCP\_STATE\_REBINDING</span><span class="sxs-lookup"><span data-stu-id="ec169-639">NX\_DHCP\_STATE\_REBINDING</span></span>        | <span data-ttu-id="ec169-640">7</span><span class="sxs-lookup"><span data-stu-id="ec169-640">7</span></span>     |
| <span data-ttu-id="ec169-641">NX_DHCP_STATE_FORCERENEW</span><span class="sxs-lookup"><span data-stu-id="ec169-641">NX_DHCP_STATE_FORCERENEW</span></span>          | <span data-ttu-id="ec169-642">8</span><span class="sxs-lookup"><span data-stu-id="ec169-642">8</span></span>     |
| <span data-ttu-id="ec169-643">NX\_DHCP\_STATE\_ADDRESS\_PROBING</span><span class="sxs-lookup"><span data-stu-id="ec169-643">NX\_DHCP\_STATE\_ADDRESS\_PROBING</span></span> | <span data-ttu-id="ec169-644">9</span><span class="sxs-lookup"><span data-stu-id="ec169-644">9</span></span>     |


### <a name="input-parameters"></a><span data-ttu-id="ec169-645">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-645">Input Parameters</span></span>

- <span data-ttu-id="ec169-646">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-646">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="ec169-647">**dhcp_state_change_notify**: указатель функции обратного вызова для изменения состояния.</span><span class="sxs-lookup"><span data-stu-id="ec169-647">**dhcp_state_change_notify** State change callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-648">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-648">Return Values</span></span>

- <span data-ttu-id="ec169-649">**NX_SUCCESS** (0x00): обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="ec169-649">**NX_SUCCESS** (0x00) Successful callback set.</span></span>  

- <span data-ttu-id="ec169-650">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-650">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="ec169-651">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-651">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-652">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-652">Allowed From</span></span>

<span data-ttu-id="ec169-653">Потоки, инициализация.</span><span class="sxs-lookup"><span data-stu-id="ec169-653">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ec169-654">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-654">Example</span></span>

```C
/* Register the “my_state_change” function to be called on any DHCP state change, 
   assuming DHCP has alreadybeen created. */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_interface_state_change_notify"></a><span data-ttu-id="ec169-655">nx_dhcp_interface_state_change_notify</span><span class="sxs-lookup"><span data-stu-id="ec169-655">nx_dhcp_interface_state_change_notify</span></span>

<span data-ttu-id="ec169-656">Задание функции обратного вызова для изменения состояния DHCP на указанном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="ec169-656">Set DHCP state change callback function on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-657">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-657">Prototype</span></span>

```C
UINT nx_dhcp_interface_state_change_notify(
              NX_DHCP *dhcp_ptr, 
              UINT interface_index,
              VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                               UINT interface_index,
                                               UCHAR new_state));
```

### <a name="description"></a><span data-ttu-id="ec169-658">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-658">Description</span></span>

<span data-ttu-id="ec169-659">Эта служба регистрирует указанную функцию обратного вызова для уведомления приложения об изменениях состояния DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-659">This service registers the specified callback function for notifying an application of DHCP state changes.</span></span> <span data-ttu-id="ec169-660">Входные аргументы функции обратного вызова — это индекс интерфейса и состояние, в которое DHCP-клиент перешел на этом интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="ec169-660">The callback funciton input arguments are the interface index and the state the DHCP Client has transitioned to on that interface.</span></span>

<span data-ttu-id="ec169-661">Дополнительные сведения о функциях изменения состояния см. в описании функции *nx_dhcp_state_change_notify()* .</span><span class="sxs-lookup"><span data-stu-id="ec169-661">For more information about state change functions, see *nx_dhcp_state_change_notify*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-662">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-662">Input Parameters</span></span>

- <span data-ttu-id="ec169-663">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-663">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="ec169-664">**dhcp_interface_state_change_notify**: указатель функции обратного вызова приложения.</span><span class="sxs-lookup"><span data-stu-id="ec169-664">**dhcp_interface_state_change_notify** Application callback function pointer</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-665">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-665">Return Values</span></span>

- <span data-ttu-id="ec169-666">**NX_SUCCESS** (0x00): обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="ec169-666">**NX_SUCCESS** (0x00) Successful callback set.</span></span>  

- <span data-ttu-id="ec169-667">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-667">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-668">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-668">Allowed From</span></span>

<span data-ttu-id="ec169-669">Потоки, инициализация.</span><span class="sxs-lookup"><span data-stu-id="ec169-669">Threads, Initialization</span></span>

### <a name="example"></a><span data-ttu-id="ec169-670">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-670">Example</span></span>

```C
/* Register the “my_state_change” function to be called on any DHCP state 
   change, assuming DHCP has alreadybeen created. */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                 UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_stop"></a><span data-ttu-id="ec169-671">nx_dhcp_stop</span><span class="sxs-lookup"><span data-stu-id="ec169-671">nx_dhcp_stop</span></span>

<span data-ttu-id="ec169-672">Остановка обработки DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-672">Stops DHCP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-673">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-673">Prototype</span></span>

```C
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a><span data-ttu-id="ec169-674">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-674">Description</span></span>

<span data-ttu-id="ec169-675">Эта служба останавливает обработку DHCP на всех интерфейсах, на которых она запущена.</span><span class="sxs-lookup"><span data-stu-id="ec169-675">This service stops DHCP processing on all interfaces that have started DHCP processing.</span></span> <span data-ttu-id="ec169-676">Если протокол DHCP не обрабатывается ни одним интерфейсом, эта служба приостанавливает поток DHCP-клиента и отключает таймер DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="ec169-676">If there are no interfaces processing DHCP, this service will suspend the DHCP Client thread, and inactivate the DHCP Client timer.</span></span>

<span data-ttu-id="ec169-677">Чтобы остановить обработку DHCP на определенном интерфейсе, когда протокол DHCP включен для нескольких интерфейсов, используйте службу *nx_dhcp_interface_stop*.</span><span class="sxs-lookup"><span data-stu-id="ec169-677">To stop DHCP on a specific interface if multiple interfaces are enabled for DHCP, use the *nx_dhcp_interface_stop* service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-678">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-678">Input Parameters</span></span>

- <span data-ttu-id="ec169-679">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-679">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-680">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-680">Return Values</span></span>

- <span data-ttu-id="ec169-681">**NX_SUCCESS** (0x00): протокол DHCP успешно остановлен.</span><span class="sxs-lookup"><span data-stu-id="ec169-681">**NX_SUCCESS** (0x00) Successful DHCP stop</span></span>

- <span data-ttu-id="ec169-682">**NX_DHCP_NOT_STARTED** (0x96): экземпляр DHCP не запущен.</span><span class="sxs-lookup"><span data-stu-id="ec169-682">**NX_DHCP_NOT_STARTED** (0x96) The DHCP instance not started.</span></span>

- <span data-ttu-id="ec169-683">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-683">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="ec169-684">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-684">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-685">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-685">Allowed From</span></span>

<span data-ttu-id="ec169-686">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-686">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-687">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-687">Example</span></span>

```C
/* Stop the DHCP processing for this IP instance. */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_interface_stop"></a><span data-ttu-id="ec169-688">nx_dhcp_interface_stop</span><span class="sxs-lookup"><span data-stu-id="ec169-688">nx_dhcp_interface_stop</span></span>

<span data-ttu-id="ec169-689">Остановка обработки DHCP на указанном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="ec169-689">Stop DHCP processing on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-690">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-690">Prototype</span></span>

```C
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="ec169-691">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-691">Description</span></span>

<span data-ttu-id="ec169-692">Эта служба останавливает обработку DHCP на указанном интерфейсе, если она запущена.</span><span class="sxs-lookup"><span data-stu-id="ec169-692">This service stops DHCP processing on the specified interface if DHCP is already started.</span></span> <span data-ttu-id="ec169-693">Если нет других интерфейсов, использующих DHCP, поток и таймер DHCP приостанавливаются.</span><span class="sxs-lookup"><span data-stu-id="ec169-693">If there are no other interfaces running DHCP, the DHCP thread and timer are suspended.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-694">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-694">Input Parameters</span></span>

- <span data-ttu-id="ec169-695">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-695">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="ec169-696">**Interface_index**: интерфейс, для которого необходимо остановить обработку DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-696">**Interface_index** Interface on which to stop DHCP processing</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-697">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-697">Return Values</span></span>

- <span data-ttu-id="ec169-698">**NX_SUCCESS** (0x00): протокол DHCP успешно остановлен.</span><span class="sxs-lookup"><span data-stu-id="ec169-698">**NX_SUCCESS** (0x00) Successful DHCP stop</span></span>

- <span data-ttu-id="ec169-699">**NX_DHCP_NOT_STARTED** (0x96): обработка DHCP не запущена.</span><span class="sxs-lookup"><span data-stu-id="ec169-699">**NX_DHCP_NOT_STARTED** (0x96) DHCP not started.</span></span>

- <span data-ttu-id="ec169-700">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-700">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="ec169-701">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-701">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="ec169-702">NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-702">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-703">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-703">Allowed From</span></span>

<span data-ttu-id="ec169-704">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-704">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-705">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-705">Example</span></span>

```C
/* Stop DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_user_option_retrieve"></a><span data-ttu-id="ec169-706">nx_dhcp_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="ec169-706">nx_dhcp_user_option_retrieve</span></span>

<span data-ttu-id="ec169-707">Получение параметра DHCP из последнего ответа сервера.</span><span class="sxs-lookup"><span data-stu-id="ec169-707">Retrieve a DHCP option from last server response</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-708">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-708">Prototype</span></span>

```C
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="ec169-709">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-709">Description</span></span>

<span data-ttu-id="ec169-710">Эта служба извлекает указанный параметр DHCP из буфера параметров DHCP на первом интерфейсе с включенным протоколом DHCP, найденным в записи DHCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="ec169-710">This service retrieves the specified DHCP option from the DHCP options buffer on the first interface enabled for DHCP found on the DHCP Client record.</span></span> <span data-ttu-id="ec169-711">В случае успешного выполнения данные параметра копируются в указанный буфер.</span><span class="sxs-lookup"><span data-stu-id="ec169-711">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-712">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-712">Input Parameters</span></span>

- <span data-ttu-id="ec169-713">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-713">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>  

- <span data-ttu-id="ec169-714">**request_option**: параметр DHCP согласно документам RFC.</span><span class="sxs-lookup"><span data-stu-id="ec169-714">**request_option** DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="ec169-715">Ознакомьтесь с параметром NX_DHCP_OPTION в файле *nxd_dhcp_client.h*.</span><span class="sxs-lookup"><span data-stu-id="ec169-715">See the NX_DHCP_OPTION option in *nx_dhcp.h*.</span></span>

- <span data-ttu-id="ec169-716">**destination_ptr**: указатель на место назначения для строки ответа.</span><span class="sxs-lookup"><span data-stu-id="ec169-716">**destination_ptr** Pointer to the destination for the response string.</span></span>  

- <span data-ttu-id="ec169-717">**destination_size**: указатель на размер места назначения и, при возвращении, место назначения для размещения числа возвращенных байтов.</span><span class="sxs-lookup"><span data-stu-id="ec169-717">**destination_size** Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-718">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-718">Return Values</span></span>

- <span data-ttu-id="ec169-719">**NX_SUCCESS** (0x00): параметр успешно получен.</span><span class="sxs-lookup"><span data-stu-id="ec169-719">**NX_SUCCESS** (0x00) Successful option retrieval.</span></span>  

- <span data-ttu-id="ec169-720">**NX_DHCP_NOT_BOUND** (0x94): DHCP-клиент не привязан.</span><span class="sxs-lookup"><span data-stu-id="ec169-720">**NX_DHCP_NOT_BOUND** (0x94) DHCP Client not bound.</span></span>

- <span data-ttu-id="ec169-721">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5): протокол DHCP не включен ни для одного интерфейса.</span><span class="sxs-lookup"><span data-stu-id="ec169-721">**NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) No interfaces enabled for DHCP</span></span>

- <span data-ttu-id="ec169-722">**NX_DHCP_DEST_TO_SMALL** (0x95): размер места назначения слишком мал для сохранения ответа.</span><span class="sxs-lookup"><span data-stu-id="ec169-722">**NX_DHCP_DEST_TO_SMALL** (0x95) Destination is too small to hold response.</span></span>

- <span data-ttu-id="ec169-723">**NX_DHCP_PARSE_ERROR** (0x97): параметр DHCP не найден в ответе сервера.</span><span class="sxs-lookup"><span data-stu-id="ec169-723">**NX_DHCP_PARSE_ERROR** (0x97) DHCP Option not found in Server response.</span></span>

- <span data-ttu-id="ec169-724">NX_PTR_ERROR (0x16): недопустимый указатель ввода.</span><span class="sxs-lookup"><span data-stu-id="ec169-724">NX_PTR_ERROR (0x16) Invalid input pointer.</span></span>

- <span data-ttu-id="ec169-725">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-725">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-726">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-726">Allowed From</span></span>

<span data-ttu-id="ec169-727">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-727">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-728">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-728">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a><span data-ttu-id="ec169-729">nx_dhcp_interface_user_option_retrieve</span><span class="sxs-lookup"><span data-stu-id="ec169-729">nx_dhcp_interface_user_option_retrieve</span></span>

<span data-ttu-id="ec169-730">Получение параметра DHCP из последнего ответа сервера на указанном интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="ec169-730">Retrieve a DHCP option from last server response on the specified interface</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-731">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-731">Prototype</span></span>

```C
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                  UINT interface_index, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a><span data-ttu-id="ec169-732">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-732">Description</span></span>

<span data-ttu-id="ec169-733">Эта служба извлекает указанный параметр DHCP из буфера параметров DHCP на указанном интерфейсе, если для него включен протокол DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-733">This service retrieves the specified DHCP option from the DHCP options buffer on the specified interface, if that interface is enabled for DHCP.</span></span> <span data-ttu-id="ec169-734">В случае успешного выполнения данные параметра копируются в указанный буфер.</span><span class="sxs-lookup"><span data-stu-id="ec169-734">If successful, the option data is copied into the specified buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-735">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-735">Input Parameters</span></span>

- <span data-ttu-id="ec169-736">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-736">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="ec169-737">**interface_index**: индекс, по которому извлекается указанный параметр.</span><span class="sxs-lookup"><span data-stu-id="ec169-737">**Interface_index** Index on which to retrieve the specified option</span></span>  

- <span data-ttu-id="ec169-738">**request_option**: параметр DHCP согласно документам RFC.</span><span class="sxs-lookup"><span data-stu-id="ec169-738">**request_option** DHCP option, as specified by the RFCs.</span></span> <span data-ttu-id="ec169-739">Ознакомьтесь с параметром NX_DHCP_OPTION в файле *nxd_dhcp_client.h*.</span><span class="sxs-lookup"><span data-stu-id="ec169-739">See the NX_DHCP_OPTION option in *nx_dhcp.h*.</span></span>  

- <span data-ttu-id="ec169-740">**destination_ptr**: указатель на место назначения для строки ответа.</span><span class="sxs-lookup"><span data-stu-id="ec169-740">**destination_ptr** Pointer to the destination for the response string.</span></span>  

- <span data-ttu-id="ec169-741">**destination_size**: указатель на размер места назначения и, при возвращении, место назначения для размещения числа возвращенных байтов.</span><span class="sxs-lookup"><span data-stu-id="ec169-741">**destination_size** Pointer to the size of the destination and on return, the destination to place the number of bytes returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-742">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-742">Return Values</span></span>

- <span data-ttu-id="ec169-743">**NX_SUCCESS** (0x00): параметр успешно получен.</span><span class="sxs-lookup"><span data-stu-id="ec169-743">**NX_SUCCESS** (0x00) Successful option retrieval.</span></span>  

- <span data-ttu-id="ec169-744">**NX_DHCP_NOT_BOUND** (0x94): IP-адрес не назначен.</span><span class="sxs-lookup"><span data-stu-id="ec169-744">**NX_DHCP_NOT_BOUND** (0x94) IP address not assigned</span></span>

- <span data-ttu-id="ec169-745">**NX_DHCP_DEST_TO_SMALL** (0x95): слишком маленький буфер.</span><span class="sxs-lookup"><span data-stu-id="ec169-745">**NX_DHCP_DEST_TO_SMALL** (0x95) Buffer is too small</span></span>

- <span data-ttu-id="ec169-746">**NX_DHCP_PARSE_ERROR** (0x97): параметр DHCP не найден в ответе сервера.</span><span class="sxs-lookup"><span data-stu-id="ec169-746">**NX_DHCP_PARSE_ERROR** (0x97) DHCP Option not found in Server response.</span></span>

- <span data-ttu-id="ec169-747">NX_PTR_ERROR (0x16): недопустимый указатель DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-747">NX_PTR_ERROR (0x16) Invalid DHCP pointer.</span></span>

- <span data-ttu-id="ec169-748">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="ec169-748">NX_CALLER_ERROR (0x11) Invalid caller of service.</span></span>

- <span data-ttu-id="ec169-749">NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="ec169-749">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-750">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-750">Allowed From</span></span>

<span data-ttu-id="ec169-751">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-751">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-752">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-752">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_user_option_convert"></a><span data-ttu-id="ec169-753">nx_dhcp_user_option_convert</span><span class="sxs-lookup"><span data-stu-id="ec169-753">nx_dhcp_user_option_convert</span></span>

<span data-ttu-id="ec169-754">Преобразование четырех байт в значение ULONG.</span><span class="sxs-lookup"><span data-stu-id="ec169-754">Convert four bytes to ULONG</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-755">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-755">Prototype</span></span>

```C
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a><span data-ttu-id="ec169-756">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-756">Description</span></span>

<span data-ttu-id="ec169-757">Эта служба преобразовывает четыре символа, на которые указывает option_string_ptr, в длинное целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="ec169-757">This service converts the four characters pointed to by “option_string_ptr” into an unsigned long value.</span></span> <span data-ttu-id="ec169-758">Она особенно удобна при наличии IP-адресов.</span><span class="sxs-lookup"><span data-stu-id="ec169-758">It is especially useful when IP addresses are present.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-759">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-759">Input Parameters</span></span>

- <span data-ttu-id="ec169-760">**option_string_ptr**: указатель на ранее извлеченную строку параметра.</span><span class="sxs-lookup"><span data-stu-id="ec169-760">**option_string_ptr** Pointer to previously retrieved option string.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-761">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-761">Return Values</span></span>

- <span data-ttu-id="ec169-762">**value**: значение первых четырех байт.</span><span class="sxs-lookup"><span data-stu-id="ec169-762">**Value** Value of first four bytes.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-763">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-763">Allowed From</span></span>

<span data-ttu-id="ec169-764">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-764">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-765">Например, .</span><span class="sxs-lookup"><span data-stu-id="ec169-765">Example</span></span>

```C
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a><span data-ttu-id="ec169-766">nx_dhcp_user_option_add_callback_set</span><span class="sxs-lookup"><span data-stu-id="ec169-766">nx_dhcp_user_option_add_callback_set</span></span>

<span data-ttu-id="ec169-767">Задание функции обратного вызова для добавления параметров, предоставленных пользователем.</span><span class="sxs-lookup"><span data-stu-id="ec169-767">Set callback function for adding user supplied options</span></span>

### <a name="prototype"></a><span data-ttu-id="ec169-768">Прототип</span><span class="sxs-lookup"><span data-stu-id="ec169-768">Prototype</span></span>

```C
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
    UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                 UINT iface_index, 
                                 UINT message_type, 
                                 UCHAR *user_option_ptr, 
                                 UINT *user_option_length));
```

### <a name="description"></a><span data-ttu-id="ec169-769">Описание</span><span class="sxs-lookup"><span data-stu-id="ec169-769">Description</span></span>

<span data-ttu-id="ec169-770">Эта служба регистрирует указанную функцию обратного вызова для добавления предоставленных пользователем параметров.</span><span class="sxs-lookup"><span data-stu-id="ec169-770">This service registers the specified callback function for adding user supplied options.</span></span>

<span data-ttu-id="ec169-771">Если эта функция обратного вызова задана, приложения могут добавлять предоставленные пользователем параметры в пакет по iface_index и message_type.</span><span class="sxs-lookup"><span data-stu-id="ec169-771">If the callback function specified, the applications can add user supplied options into the packet by iface_index and message_type.</span></span>

> [!NOTE]
> <span data-ttu-id="ec169-772">Подпрограмма пользователя.</span><span class="sxs-lookup"><span data-stu-id="ec169-772">In user’s routine.</span></span> <span data-ttu-id="ec169-773">При добавлении параметров, предоставляемых пользователем, приложения должны соблюдать формат параметров DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-773">Applications must follow the DHCP options format when add user supplied options.</span></span> <span data-ttu-id="ec169-774">Общий размер пользовательских параметров должен быть не больше user_option_length. Значение user_option_length должно обновляться в соответствии с реальной длиной параметров.</span><span class="sxs-lookup"><span data-stu-id="ec169-774">The total size of user options must be less or equal to user_option_length, and update the user_option_length as real options length.</span></span> <span data-ttu-id="ec169-775">Если параметры добавлены успешно, возвращается значение NX_TRUE. В противном случае возвращается значение NX_FALSE.</span><span class="sxs-lookup"><span data-stu-id="ec169-775">Return NX_TRUE if add options successfully, else return NX_FALSE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="ec169-776">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="ec169-776">Input Parameters</span></span>

- <span data-ttu-id="ec169-777">**dhcp_ptr**: указатель на созданный ранее экземпляр DHCP.</span><span class="sxs-lookup"><span data-stu-id="ec169-777">**dhcp_ptr** Pointer to previously created DHCP instance.</span></span>

- <span data-ttu-id="ec169-778">**dhcp_user_option_add**: указатель на функцию добавления пользовательских параметров.</span><span class="sxs-lookup"><span data-stu-id="ec169-778">**dhcp_user_option_add** Pointer to user option add function.</span></span>

### <a name="return-values"></a><span data-ttu-id="ec169-779">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="ec169-779">Return Values</span></span>

- <span data-ttu-id="ec169-780">**NX_SUCCESS** (0x00): обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="ec169-780">**NX_SUCCESS** (0x00) Successful callback set.</span></span>

- <span data-ttu-id="ec169-781">NX_PTR_ERROR (0x16): недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="ec169-781">NX_PTR_ERROR (0x16) Invalid pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="ec169-782">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="ec169-782">Allowed From</span></span>

<span data-ttu-id="ec169-783">Потоки</span><span class="sxs-lookup"><span data-stu-id="ec169-783">Threads</span></span>

### <a name="example"></a><span data-ttu-id="ec169-784">Пример</span><span class="sxs-lookup"><span data-stu-id="ec169-784">Example</span></span>

```C
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created. */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered. */
```
