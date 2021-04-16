---
title: Глава 3. Описание служб клиента SNTP для NetX для ОСРВ Azure
description: Эта глава содержит описание всех служб клиента SNTP для NetX Duo, перечисленных ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 75b2b878cd084ca1c1cdd1eed4333d303fe32ad6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814551"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-sntp-client-services"></a><span data-ttu-id="62fa7-103">Глава 3. Описание служб клиента SNTP для NetX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="62fa7-103">Chapter 3 - Description of Azure RTOS NetX Duo SNTP Client Services</span></span>

<span data-ttu-id="62fa7-104">Эта глава содержит описание всех служб клиента SNTP для NetX Duo для ОСРВ Azure, перечисленных ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="62fa7-104">This chapter contains a description of all Azure RTOS NetX Duo SNTP Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="62fa7-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="62fa7-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="62fa7-106">**nx_sntp_client_create**: *создание клиента SNTP*</span><span class="sxs-lookup"><span data-stu-id="62fa7-106">**nx_sntp_client_create**: *Create the SNTP Client*</span></span>
- <span data-ttu-id="62fa7-107">**nx_sntp_client_delete**: *удаление клиента SNTP*</span><span class="sxs-lookup"><span data-stu-id="62fa7-107">**nx_sntp_client_delete**: *Delete the SNTP Client*</span></span>
- <span data-ttu-id="62fa7-108">**nx_sntp_client_get_local_time**: *получение местного времени клиента SNTP*</span><span class="sxs-lookup"><span data-stu-id="62fa7-108">**nx_sntp_client_get_local_time**: *Get SNTP Client local time*</span></span>
- <span data-ttu-id="62fa7-109">**nx_sntp_client_get_local_time_extended**: *получение местного времени клиента SNTP*</span><span class="sxs-lookup"><span data-stu-id="62fa7-109">**nx_sntp_client_get_local_time_extended**: *Get SNTP Client local time*</span></span>
- <span data-ttu-id="62fa7-110">**nx_sntp_client_initialize_broadcast**: *инициализация клиента для широковещательной рассылки по IPv4*</span><span class="sxs-lookup"><span data-stu-id="62fa7-110">**nx_sntp_client_initialize_broadcast**: *Initialize Client for IPv4 broadcast operation*</span></span>
- <span data-ttu-id="62fa7-111">**nxd_sntp_client_initialize_broadcast**: *инициализация клиента для широковещательной рассылки по IPv6 или IPv4*</span><span class="sxs-lookup"><span data-stu-id="62fa7-111">**nxd_sntp_client_initialize_broadcast**: *Initialize Client for IPv6 or IPv4 broadcast operation*</span></span>
- <span data-ttu-id="62fa7-112">**nx_sntp_client_initialize_unicast**: *инициализация клиента для одноадресной передачи данных по IPv4*</span><span class="sxs-lookup"><span data-stu-id="62fa7-112">**nx_sntp_client_initialize_unicast**: *Initialize Client for IPv4 unicast operation*</span></span>
- <span data-ttu-id="62fa7-113">**nxd_sntp_client_initialize_unicast**: *инициализация клиента для одноадресной передачи данных по IPv4 или IPv6*</span><span class="sxs-lookup"><span data-stu-id="62fa7-113">**nxd_sntp_client_initialize_unicast**: *Initialize Client for IPv4 or IPv6 unicast operation*</span></span>
- <span data-ttu-id="62fa7-114">**nx_sntp_client_receiving_udpates**: *клиент в настоящее время получает допустимые обновления SNTP*</span><span class="sxs-lookup"><span data-stu-id="62fa7-114">**nx_sntp_client_receiving_udpates**: *Client is currently receiving valid SNTP updates*</span></span>
- <span data-ttu-id="62fa7-115">**nx_sntp_client_request_unicast_time**: *отправка одноадресного запроса непосредственно на NTP-сервер*</span><span class="sxs-lookup"><span data-stu-id="62fa7-115">**nx_sntp_client_request_unicast_time**: *Send a unicast request directly to the NTP Server*</span></span>
- <span data-ttu-id="62fa7-116">**nx_sntp_client_run_broadcast**: *выполнение клиента в широковещательном режиме*</span><span class="sxs-lookup"><span data-stu-id="62fa7-116">**nx_sntp_client_run_broadcast**: *Run the Client in broadcast mode*</span></span>
- <span data-ttu-id="62fa7-117">**nx_sntp_client_run_unicast**: *выполнение клиента в одноадресном режиме*</span><span class="sxs-lookup"><span data-stu-id="62fa7-117">**nx_sntp_client_run_unicast**: *Run the Client in unicast mode*</span></span>
- <span data-ttu-id="62fa7-118">**nx_sntp_client_set_local_time**: *настройка исходного местного времени для клиента SNTP*</span><span class="sxs-lookup"><span data-stu-id="62fa7-118">**nx_sntp_client_set_local_time**: *Set SNTP Client initial local time*</span></span>
- <span data-ttu-id="62fa7-119">**nx_sntp_client_set_time_update_notify**: *настройка обратного вызова для обновления SNTP*</span><span class="sxs-lookup"><span data-stu-id="62fa7-119">**nx_sntp_client_set_time_update_notify**: *Set the SNTP update callback*</span></span>
- <span data-ttu-id="62fa7-120">**nx_sntp_client_stop**: *остановка потока клиента SNTP*</span><span class="sxs-lookup"><span data-stu-id="62fa7-120">**nx_sntp_client_stop**: *Stop the SNTP Client thread*</span></span>
- <span data-ttu-id="62fa7-121">**nx_sntp_client_utility_display_date_and_time**: *отображение времени NTP в секундах*</span><span class="sxs-lookup"><span data-stu-id="62fa7-121">**nx_sntp_client_utility_display_date_and_time**: *Display NTP time in seconds*</span></span>
- <span data-ttu-id="62fa7-122">**nx_sntp_client_utility_msecs_to_fraction**: *преобразование миллисекунд в дробный компонент NTP*</span><span class="sxs-lookup"><span data-stu-id="62fa7-122">**nx_sntp_client_utility_msecs_to_fraction**: *Convert milliseconds to an NTP fraction component*</span></span>
- <span data-ttu-id="62fa7-123">**nx_sntp_client_utility_usecs_to_fraction**: *преобразование микросекунд в дробный компонент NTP*</span><span class="sxs-lookup"><span data-stu-id="62fa7-123">**nx_sntp_client_utility_usecs_to_fraction**: *Convert microseconds to an NTP fraction component*</span></span>
- <span data-ttu-id="62fa7-124">**nx_sntp_client_utility_fraction_to_usecs**: *преобразование дробного компонента NTP в микросекунды*</span><span class="sxs-lookup"><span data-stu-id="62fa7-124">**nx_sntp_client_utility_fraction_to_usecs**: *Convert an NTP fraction component to microseconds*</span></span>


## <a name="nx_sntp_client_create"></a><span data-ttu-id="62fa7-125">nx_sntp_client_create</span><span class="sxs-lookup"><span data-stu-id="62fa7-125">nx_sntp_client_create</span></span>

<span data-ttu-id="62fa7-126">Создание клиента SNTP</span><span class="sxs-lookup"><span data-stu-id="62fa7-126">Create an SNTP Client</span></span>

### <a name="prototype"></a><span data-ttu-id="62fa7-127">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-127">Prototype</span></span>

```C
UINT nx_sntp_client_create(NX_SNTP_CLIENT *client_ptr, NX_IP *ip_ptr,  
                                     UINT iface_index, 
                                     NX_PACKET_POOL *packet_pool_ptr, 
UINT (*leap_second_handler)(NX_SNTP_CLIENT *client_ptr, 
                                        UINT indicator), 
UINT (*kiss_of_death_handler)(NX_SNTP_CLIENT *client_ptr, 
                               NX_SNTP_TIME_MESSAGE *server_time_msg),
VOID (random_number_generator)(struct NX_SNTP_CLIENT_STRUCT 
                                *client_ptr, ULONG *rand));

```

### <a name="description"></a><span data-ttu-id="62fa7-128">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-128">Description</span></span>

<span data-ttu-id="62fa7-129">Эта служба создает экземпляр клиента SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-129">This service creates an SNTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-130">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-130">Input Parameters</span></span>

- <span data-ttu-id="62fa7-131">**client_ptr**: указатель на блок управления клиентом SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-131">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="62fa7-132">**ip_ptr**: указатель на экземпляр IP-адреса для клиента.</span><span class="sxs-lookup"><span data-stu-id="62fa7-132">**ip_ptr** Pointer to Client IP instance</span></span>

- <span data-ttu-id="62fa7-133">**iface_index**: индекс сетевого интерфейса SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-133">**iface_index** Index to SNTP network interface</span></span>

- <span data-ttu-id="62fa7-134">**packet_pool_ptr**: указатель на пул пакетов клиента.</span><span class="sxs-lookup"><span data-stu-id="62fa7-134">**packet_pool_ptr** Pointer to Client packet pool</span></span>

- <span data-ttu-id="62fa7-135">**leap_second_handler**: обратный вызов, позволяющий приложению отреагировать на предстоящее применение корректировочной секунды.</span><span class="sxs-lookup"><span data-stu-id="62fa7-135">**leap_second_handler** Callback for application response to impending leap second</span></span>

- <span data-ttu-id="62fa7-136">**kiss_of_death_handler**: обратный вызов, позволяющий приложению отреагировать на получение пакета KoD (Kiss of Death).</span><span class="sxs-lookup"><span data-stu-id="62fa7-136">**kiss_of_death_handler** Callback for application response to receiving Kiss of Death packet</span></span>

- <span data-ttu-id="62fa7-137">**random_number_generator**: обратный вызов к службе создания случайных чисел.</span><span class="sxs-lookup"><span data-stu-id="62fa7-137">**random_number_generator** Callback to random number generator service</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-138">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-138">Return Values</span></span>

- <span data-ttu-id="62fa7-139">**NX_SUCCESS** (0x00): успешное создание клиента.</span><span class="sxs-lookup"><span data-stu-id="62fa7-139">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="62fa7-140">**NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0xD2A): недопустимые входные данные, кроме указателей.</span><span class="sxs-lookup"><span data-stu-id="62fa7-140">**NX_SNTP_INSUFFICIENT_PACKET_PAYLOAD** (0xD2A) Invalid non pointer input</span></span>

- <span data-ttu-id="62fa7-141">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="62fa7-141">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="62fa7-142">NX_INVALID_INTERFACE (0x4C): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="62fa7-142">NX_INVALID_INTERFACE (0x4C) Invalid network interface</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62fa7-143">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-143">Allowed From</span></span>

<span data-ttu-id="62fa7-144">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="62fa7-144">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-145">Например, .</span><span class="sxs-lookup"><span data-stu-id="62fa7-145">Example</span></span>

```C
/* Create the SNTP Client on the primary interface. */
UINT iface_index = 0;
status =  nx_sntp_client_create(&demo_client, 
                     iface_index, &client_ip, 
&client_packet_pool, leap_second_handler, 
                    kiss_of_death_handler, 
NULL /* no random_number_generator callback */);

/* If status is NX_SUCCESS an SNTP Client instance was successfully
   created.  */

```

## <a name="nx_sntp_client_delete"></a><span data-ttu-id="62fa7-146">nx_sntp_client_delete</span><span class="sxs-lookup"><span data-stu-id="62fa7-146">nx_sntp_client_delete</span></span>

<span data-ttu-id="62fa7-147">Удаление клиента SNTP</span><span class="sxs-lookup"><span data-stu-id="62fa7-147">Delete an SNTP Client</span></span>

### <a name="prototype"></a><span data-ttu-id="62fa7-148">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-148">Prototype</span></span>

```C
UINT nx_sntp_client_delete(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="62fa7-149">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-149">Description</span></span>

<span data-ttu-id="62fa7-150">Эта служба удаляет экземпляр клиента SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-150">This service deletes an SNTP Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-151">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-151">Input Parameters</span></span>

- <span data-ttu-id="62fa7-152">**client_ptr**: указатель на блок управления клиентом SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-152">**client_ptr** Pointer to SNTP Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-153">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-153">Return Values</span></span>

- <span data-ttu-id="62fa7-154">**NX_SUCCESS** (0x00): успешное создание клиента.</span><span class="sxs-lookup"><span data-stu-id="62fa7-154">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="62fa7-155">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="62fa7-155">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="62fa7-156">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="62fa7-156">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62fa7-157">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-157">Allowed From</span></span>

<span data-ttu-id="62fa7-158">Потоки</span><span class="sxs-lookup"><span data-stu-id="62fa7-158">Threads</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-159">Например, .</span><span class="sxs-lookup"><span data-stu-id="62fa7-159">Example</span></span>

```C
/* Delete the SNTP Client. */
status =  nx_sntp_client_delete(&demo_client);

/* If status is NX_SUCCESS an SNTP Client 
   instance was successfully deleted.  */

```

## <a name="nx_sntp_client_get_local_time"></a><span data-ttu-id="62fa7-160">nx_sntp_client_get_local_time</span><span class="sxs-lookup"><span data-stu-id="62fa7-160">nx_sntp_client_get_local_time</span></span>

<span data-ttu-id="62fa7-161">Получение местного времени клиента SNTP</span><span class="sxs-lookup"><span data-stu-id="62fa7-161">Get the SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="62fa7-162">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-162">Prototype</span></span>

```C
UINT nx_sntp_client_get_local_time(NX_SNTP_CLIENT *client_ptr , 
                                                ULONG *seconds, 
                                                ULONG *fraction, 
                                                CHAR *buffer);

```

### <a name="description"></a><span data-ttu-id="62fa7-163">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-163">Description</span></span>

<span data-ttu-id="62fa7-164">Эта служба получает местное время клиента SNTP и принимает входной указатель на буфер параметров, позволяющий получить данные в формате строкового сообщения.</span><span class="sxs-lookup"><span data-stu-id="62fa7-164">This service gets the SNTP Client local time with an option buffer pointer input to receive the data in string message format.</span></span>

<span data-ttu-id="62fa7-165">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="62fa7-165">This service is deprecated.</span></span> <span data-ttu-id="62fa7-166">Мы рекомендуем разработчикам перейти на службу *nx_sntp_client_get_local_time_extended*().</span><span class="sxs-lookup"><span data-stu-id="62fa7-166">Developers are encouraged to migrate to *nx_sntp_client_get_local_time_extended*().</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-167">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-167">Input Parameters</span></span>

- <span data-ttu-id="62fa7-168">**client_ptr**: указатель на блок управления клиентом SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-168">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="62fa7-169">**seconds**: указатель на секунды местного времени.</span><span class="sxs-lookup"><span data-stu-id="62fa7-169">**seconds** Pointer to local time seconds</span></span>

- <span data-ttu-id="62fa7-170">**fraction**: дробный компонент местного времени.</span><span class="sxs-lookup"><span data-stu-id="62fa7-170">**fraction** Local time fraction component</span></span>

- <span data-ttu-id="62fa7-171">**buffer**: указатель на буфер для записи данных о времени.</span><span class="sxs-lookup"><span data-stu-id="62fa7-171">**buffer** Pointer to buffer to write time data</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-172">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-172">Return Values</span></span>

- <span data-ttu-id="62fa7-173">**NX_SUCCESS** (0x00): успешное создание клиента.</span><span class="sxs-lookup"><span data-stu-id="62fa7-173">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="62fa7-174">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="62fa7-174">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="62fa7-175">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="62fa7-175">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62fa7-176">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-176">Allowed From</span></span>

<span data-ttu-id="62fa7-177">Потоки</span><span class="sxs-lookup"><span data-stu-id="62fa7-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-178">Например, .</span><span class="sxs-lookup"><span data-stu-id="62fa7-178">Example</span></span>

```C
/* Get the SNTP Client local time without the 
   string message option. */

ULONG base_seconds;
ULONG base_fraction;

status =  nx_sntp_client_get_local_time(&demo_client, 
                                       &base_seconds, 
                                       &base_fraction, 
                                       NX_NULL);
/* If status is NX_SUCCESS an SNTP Client time was successfully
   retrieved.  */

```

## <a name="nx_sntp_client_get_local_time_extended"></a><span data-ttu-id="62fa7-179">nx_sntp_client_get_local_time_extended</span><span class="sxs-lookup"><span data-stu-id="62fa7-179">nx_sntp_client_get_local_time_extended</span></span>

<span data-ttu-id="62fa7-180">Получение местного времени клиента SNTP в расширенном формате</span><span class="sxs-lookup"><span data-stu-id="62fa7-180">Get the extended SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="62fa7-181">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-181">Prototype</span></span>

```C
UINT nx_sntp_client_get_local_time_extended(
                 NX_SNTP_CLIENT *client_ptr,
                 ULONG *seconds, 
                 ULONG *fraction, 
                 CHAR *buffer
                 UINT buffer_size);

```

### <a name="description"></a><span data-ttu-id="62fa7-182">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-182">Description</span></span>

<span data-ttu-id="62fa7-183">Эта служба получает местное время клиента SNTP в расширенном формате и принимает входной указатель на буфер параметров, позволяющий получить данные в формате строкового сообщения.</span><span class="sxs-lookup"><span data-stu-id="62fa7-183">This service gets the extended SNTP Client local time with an option buffer pointer input to receive the data in string message format.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-184">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-184">Input Parameters</span></span>

- <span data-ttu-id="62fa7-185">**client_ptr**: указатель на блок управления клиентом SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-185">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="62fa7-186">**seconds**: указатель на секунды местного времени.</span><span class="sxs-lookup"><span data-stu-id="62fa7-186">**seconds** Pointer to local time seconds</span></span>

- <span data-ttu-id="62fa7-187">**fraction**: указатель на дробный компонент.</span><span class="sxs-lookup"><span data-stu-id="62fa7-187">**fraction** Pointer to fraction component</span></span>

- <span data-ttu-id="62fa7-188">**buffer**: указатель на буфер для записи данных о времени.</span><span class="sxs-lookup"><span data-stu-id="62fa7-188">**buffer** Pointer to buffer to write time data</span></span>

- <span data-ttu-id="62fa7-189">**buffer_size**: длина буфера.</span><span class="sxs-lookup"><span data-stu-id="62fa7-189">**buffer_size** Length of buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-190">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-190">Return Values</span></span>

- <span data-ttu-id="62fa7-191">**NX_SUCCESS** (0x00): успешное создание клиента.</span><span class="sxs-lookup"><span data-stu-id="62fa7-191">**NX_SUCCESS** (0x00) Successful Client creation</span></span>

- <span data-ttu-id="62fa7-192">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="62fa7-192">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="62fa7-193">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="62fa7-193">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

- <span data-ttu-id="62fa7-194">NX_SIZE_ERROR (0x09): сбой проверки размера буфера.</span><span class="sxs-lookup"><span data-stu-id="62fa7-194">NX_SIZE_ERROR (0x09) Check buffer_size fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62fa7-195">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-195">Allowed From</span></span>

<span data-ttu-id="62fa7-196">Потоки</span><span class="sxs-lookup"><span data-stu-id="62fa7-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-197">Например, .</span><span class="sxs-lookup"><span data-stu-id="62fa7-197">Example</span></span>

```C
/* Get the SNTP Client local time without the 
   string message option. */

#define BUFSIZE 50

ULONG seconds;
ULONG fraction;
CHAR  buffer[BUFSIZE];

status =  nx_sntp_client_get_local_time_extended(&demo_client, 
                                                &seconds, 
                                                &fraction, 
                                                buffer, 
                                                BUFSIZE);

/* If status is NX_SUCCESS an SNTP Client 
   time was successfully retrieved.  */

```

## <a name="nx_sntp_client_initialize_broadcast"></a><span data-ttu-id="62fa7-198">nx_sntp_client_initialize_broadcast</span><span class="sxs-lookup"><span data-stu-id="62fa7-198">nx_sntp_client_initialize_broadcast</span></span>

<span data-ttu-id="62fa7-199">Инициализация клиента для широковещательной рассылки</span><span class="sxs-lookup"><span data-stu-id="62fa7-199">Initialize the Client for broadcast operation</span></span>

### <a name="prototype"></a><span data-ttu-id="62fa7-200">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-200">Prototype</span></span>

```C
UINT nx_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                                    ULONG multicast_server_address, 
                                    ULONG broadcast_time_servers);


```

### <a name="description"></a><span data-ttu-id="62fa7-201">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-201">Description</span></span>

<span data-ttu-id="62fa7-202">Эта служба инициализирует клиент для широковещательной рассылки, позволяя задать IP-адрес сервера SNTP, настроить параметры запуска и время ожидания SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-202">This service initializes the Client for broadcast operation by setting the the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="62fa7-203">Если оба адреса (многоадресной и широковещательной рассылки) не равны NULL, выбирается адрес многоадресной рассылки.</span><span class="sxs-lookup"><span data-stu-id="62fa7-203">If both multicast and broadcast addresses are non-null, the multicast address is selected.</span></span> <span data-ttu-id="62fa7-204">Если оба этих адреса равны NULL, возвращается ошибка.</span><span class="sxs-lookup"><span data-stu-id="62fa7-204">If both addresses are null an error is returned.</span></span> <span data-ttu-id="62fa7-205">Обратите внимание, что для серверов поддерживаются только IPv4-адреса.</span><span class="sxs-lookup"><span data-stu-id="62fa7-205">Note this supports IPv4 server addresses only.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-206">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-206">Input Parameters</span></span>

- <span data-ttu-id="62fa7-207">**client_ptr**: указатель на блок управления клиентом SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-207">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="62fa7-208">**multicast_server_address**: адрес SNTP для многоадресной рассылки.</span><span class="sxs-lookup"><span data-stu-id="62fa7-208">**multicast_server_address** SNTP multicast address</span></span>

- <span data-ttu-id="62fa7-209">**broadcast_time_server**: адрес сервера SNTP для широковещательной рассылки.</span><span class="sxs-lookup"><span data-stu-id="62fa7-209">**broadcast_time_server** SNTP server broadcast address</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-210">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-210">Return Values</span></span>

- <span data-ttu-id="62fa7-211">**NX_SUCCESS** (0x00): успешное создание клиента.</span><span class="sxs-lookup"><span data-stu-id="62fa7-211">**NX_SUCCESS** (0x00) Successful Client Creation</span></span>

- <span data-ttu-id="62fa7-212">**NX_INVALID_PARAMETERS** (0x4D): недопустимые входные данные, кроме указателей.</span><span class="sxs-lookup"><span data-stu-id="62fa7-212">**NX_INVALID_PARAMETERS** (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="62fa7-213">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="62fa7-213">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="62fa7-214">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="62fa7-214">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62fa7-215">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-215">Allowed From</span></span>

<span data-ttu-id="62fa7-216">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="62fa7-216">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-217">Например, .</span><span class="sxs-lookup"><span data-stu-id="62fa7-217">Example</span></span>

```C
/* Initialize the client for broadcast operation.  */
status =  nx_sntp_client_initialize_broadcast(client_ptr,0x0,
                            NX_NULL, IP_ADDRESS(192,2,2,255);

/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nxd_sntp_client_initialize_broadcast"></a><span data-ttu-id="62fa7-218">nxd_sntp_client_initialize_broadcast</span><span class="sxs-lookup"><span data-stu-id="62fa7-218">nxd_sntp_client_initialize_broadcast</span></span>

<span data-ttu-id="62fa7-219">Инициализация клиента для широковещательной рассылки по IPv4 или IPv6</span><span class="sxs-lookup"><span data-stu-id="62fa7-219">Initialize the Client for IPv4 or IPv6 broadcast operation</span></span>

### <a name="prototype"></a><span data-ttu-id="62fa7-220">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-220">Prototype</span></span>

```C
UINT nxd_sntp_client_initialize_broadcast(NX_SNTP_CLIENT *client_ptr,
                            NXD_ADDRESS *multicast_server_address, 
                            NXD_ADDRESS *broadcast_server_address);

```

### <a name="description"></a><span data-ttu-id="62fa7-221">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-221">Description</span></span>

<span data-ttu-id="62fa7-222">Эта служба инициализирует клиент для операции широковещательной рассылки, позволяя задать IP-адрес сервера SNTP, настроить параметры запуска и время ожидания SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-222">This service initializes the Client for broadcast operation by setting up the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="62fa7-223">Если оба указателя (многоадресной и широковещательной рассылки) не равны NULL, выбирается адрес многоадресной рассылки.</span><span class="sxs-lookup"><span data-stu-id="62fa7-223">If both broadcast and multicast address pointers are non null, the multicast address is selected.</span></span> <span data-ttu-id="62fa7-224">Если оба этих указателя равны NULL, возвращается ошибка.</span><span class="sxs-lookup"><span data-stu-id="62fa7-224">If both address pointers are null, an error is returned.</span></span> <span data-ttu-id="62fa7-225">Поддерживаются типы адресов IPv4 и IPv6.</span><span class="sxs-lookup"><span data-stu-id="62fa7-225">This supports both IPv4 and IPv6 address types.</span></span> <span data-ttu-id="62fa7-226">Обратите внимание, что IPv6 не поддерживает широковещательную рассылку. Если указатель на широковещательный адрес имеет значение IPv6, возвращается ошибка.</span><span class="sxs-lookup"><span data-stu-id="62fa7-226">Note that IPv6 does not support broadcast, so the broadcast address pointer is set to IPv6, an error is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-227">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-227">Input Parameters</span></span>

- <span data-ttu-id="62fa7-228">**client_ptr**: указатель на блок управления клиентом SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-228">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="62fa7-229">**multicast_server_address**: адрес многоадресной рассылки сервера SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-229">**multicast_server_address** SNTP server multicast address</span></span>

- <span data-ttu-id="62fa7-230">**broadcast_server_address**: адрес широковещательной рассылки сервера SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-230">**broadcast_server_address** SNTP server broadcast address</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-231">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-231">Return Values</span></span>

- <span data-ttu-id="62fa7-232">**NX_SUCCESS** (0x00): клиент успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="62fa7-232">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="62fa7-233">NX_SNTP_PARAM_ERROR (0xD0D): недопустимые входные данные, кроме указателей.</span><span class="sxs-lookup"><span data-stu-id="62fa7-233">NX_SNTP_PARAM_ERROR (0xD0D) Invalid non pointer input</span></span>

- <span data-ttu-id="62fa7-234">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="62fa7-234">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="62fa7-235">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="62fa7-235">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>


### <a name="allowed-from"></a><span data-ttu-id="62fa7-236">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-236">Allowed From</span></span>

<span data-ttu-id="62fa7-237">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="62fa7-237">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-238">Например, .</span><span class="sxs-lookup"><span data-stu-id="62fa7-238">Example</span></span>

```C
/* Initialize the client for broadcast operation.  */
NXD_ADDRESS broadcast_server;

Broadcast_server.nxd_ip_address = NX_IP_VERSION_V6;
Broadcast_server.nxd_ip_address.v6[0] = 0x20010db1;
Broadcast_server.nxd_ip_address.v6[1] = 0x0f101;
Broadcast_server.nxd_ip_address.v6[2] = 0x0;
Broadcast_server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_broadcast(client_ptr,0x0,
                                  NX_NULL, &broadcast_server)


/* If status is NX_SUCCESS the Client 
   was successfully initialized.  */

```

## <a name="nx_sntp_client_initialize_unicast"></a><span data-ttu-id="62fa7-239">nx_sntp_client_initialize_unicast</span><span class="sxs-lookup"><span data-stu-id="62fa7-239">nx_sntp_client_initialize_unicast</span></span>

<span data-ttu-id="62fa7-240">Настройка клиента SNTP для работы в одноадресном режиме</span><span class="sxs-lookup"><span data-stu-id="62fa7-240">Set up the SNTP Client to run in unicast</span></span>

### <a name="prototype"></a><span data-ttu-id="62fa7-241">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-241">Prototype</span></span>

```C
UINT nx_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                        ULONG unicast_time_server);

```
### <a name="description"></a><span data-ttu-id="62fa7-242">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-242">Description</span></span>

<span data-ttu-id="62fa7-243">Эта служба инициализирует клиент для одноадресной передачи данных, позволяя задать IP-адрес сервера SNTP, настроить параметры запуска и время ожидания SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-243">This service initializes the Client for unicast operation by setting the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="62fa7-244">Обратите внимание, что для серверов поддерживаются только IPv4-адреса.</span><span class="sxs-lookup"><span data-stu-id="62fa7-244">Note this supports IPv4 server addresses only.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-245">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-245">Input Parameters</span></span>

- <span data-ttu-id="62fa7-246">**client_ptr**: указатель на блок управления клиентом SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-246">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="62fa7-247">**unicast_time_server**: IP-адрес сервера SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-247">**unicast_time_server** SNTP server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-248">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-248">Return Values</span></span>

- <span data-ttu-id="62fa7-249">**NX_SUCCESS** (0x00): клиент успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="62fa7-249">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="62fa7-250">NX_INVALID_PARAMETERS (0x4D): недопустимые входные данные, кроме указателей.</span><span class="sxs-lookup"><span data-stu-id="62fa7-250">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="62fa7-251">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="62fa7-251">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="62fa7-252">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="62fa7-252">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62fa7-253">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-253">Allowed From</span></span>

<span data-ttu-id="62fa7-254">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="62fa7-254">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-255">Например, .</span><span class="sxs-lookup"><span data-stu-id="62fa7-255">Example</span></span>

```C
/* Initialize the Client for unicast operation.  */
status =  nx_sntp_client_initialize_unicast(&client_ptr, 
                                 IP_ADDRESS(192,2,2,1));


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```


## <a name="nxd_sntp_client_initialize_unicast"></a><span data-ttu-id="62fa7-256">nxd_sntp_client_initialize_unicast</span><span class="sxs-lookup"><span data-stu-id="62fa7-256">nxd_sntp_client_initialize_unicast</span></span>

<span data-ttu-id="62fa7-257">Настройка клиента SNTP для работы в одноадресном режиме IPv4 или IPv6</span><span class="sxs-lookup"><span data-stu-id="62fa7-257">Set up the SNTP Client to run in IPv4 or IPv6 unicast</span></span>

### <a name="prototype"></a><span data-ttu-id="62fa7-258">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-258">Prototype</span></span>

```C
UINT nxd_sntp_client_initialize_unicast(NX_SNTP_CLIENT * client_ptr, 
                                  NXD_ADDRESS *unicast_time_server);

```

### <a name="description"></a><span data-ttu-id="62fa7-259">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-259">Description</span></span>

<span data-ttu-id="62fa7-260">Эта служба инициализирует клиент для одноадресной передачи данных, позволяя задать IP-адрес сервера SNTP, настроить параметры запуска и время ожидания SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-260">This service initializes the Client for unicast operation by setting up the SNTP Server IP address and initializing SNTP startup parameters and timeouts.</span></span> <span data-ttu-id="62fa7-261">Поддерживаются типы адресов IPv4 и IPv6.</span><span class="sxs-lookup"><span data-stu-id="62fa7-261">This supports both IPv4 and IPv6 address types.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-262">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-262">Input Parameters</span></span>

- <span data-ttu-id="62fa7-263">**client_ptr**: указатель на блок управления клиентом SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-263">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="62fa7-264">**unicast_time_server**: IP-адрес сервера SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-264">**unicast_time_server** SNTP server IP address</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-265">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-265">Return Values</span></span>

- <span data-ttu-id="62fa7-266">**NX_SUCCESS** (0x00): клиент успешно инициализирован.</span><span class="sxs-lookup"><span data-stu-id="62fa7-266">**NX_SUCCESS** (0x00) Client successfully initialized</span></span>

- <span data-ttu-id="62fa7-267">NX_INVALID_PARAMETERS (0x4D): недопустимые входные данные, кроме указателей.</span><span class="sxs-lookup"><span data-stu-id="62fa7-267">NX_INVALID_PARAMETERS (0x4D) Invalid non pointer input</span></span>

- <span data-ttu-id="62fa7-268">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="62fa7-268">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="62fa7-269">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="62fa7-269">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62fa7-270">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-270">Allowed From</span></span>

<span data-ttu-id="62fa7-271">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="62fa7-271">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-272">Например, .</span><span class="sxs-lookup"><span data-stu-id="62fa7-272">Example</span></span>

```C
/* Initialize the Client for unicast operation.  */
NXD_ADDRESS unicast_server;

unicast _server.nxd_ip_address = NX_IP_VERSION_V6;
unicast _server.nxd_ip_address.v6[0] = 0x20010db1;
unicast _server.nxd_ip_address.v6[1] = 0x0f101;
unicast _server.nxd_ip_address.v6[2] = 0x0;
unicast _server.nxd_ip_address.v6[3] = 0x101;

status =  nxd_sntp_client_initialize_unicast(&client_ptr, 
                                        *unicast_server); 


/* If status is NX_SUCCESS the Client 
   is initialized for unicast operation.  */

```

## <a name="nx_sntp_client_receiving_updates"></a><span data-ttu-id="62fa7-273">nx_sntp_client_receiving_updates</span><span class="sxs-lookup"><span data-stu-id="62fa7-273">nx_sntp_client_receiving_updates</span></span>

<span data-ttu-id="62fa7-274">Сведения о том, получает ли клиент допустимые обновления</span><span class="sxs-lookup"><span data-stu-id="62fa7-274">Indicate if Client is receiving valid updates</span></span>

### <a name="prototype"></a><span data-ttu-id="62fa7-275">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-275">Prototype</span></span>

```C
UINT nx_sntp_client_receiving_updates(NX_SNTP_CLIENT *client_ptr, 
                                           UINT *receive_status);

```

### <a name="description"></a><span data-ttu-id="62fa7-276">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-276">Description</span></span>

<span data-ttu-id="62fa7-277">Эта служба сообщает, получает ли клиент допустимые обновления SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-277">This service indicates if the Client is receiving valid SNTP updates.</span></span> <span data-ttu-id="62fa7-278">Если превышен максимальный промежуток времени без допустимого обновления или превышено ограничение на количество последовательных недопустимых обновлений, в качестве состояния получения возвращается значение false.</span><span class="sxs-lookup"><span data-stu-id="62fa7-278">If the maximum time lapse without a valid update or limit on consecutive invalid updates is exceeded, the receive status is returned as false.</span></span> <span data-ttu-id="62fa7-279">Обратите внимание, что клиент SNTP будет работать и дальше. Если приложению нужно перезапустить клиент SNTP с другим сервером в одноадресном, широковещательном или многоадресном режиме, придется отключить текущий клиент SNTP с помощью службы *nx_sntp_client_stop* и повторно инициализировать клиент с помощью любой из служб инициализации, указав другой сервер.</span><span class="sxs-lookup"><span data-stu-id="62fa7-279">Note that the SNTP Client is still running and if the application wishes to restart the SNTP Client with another unicast or broadcast/multicast server it must stop the SNTP Client using the *nx_sntp_client_stop* service, reinitialize the Client using one of the initialize services with another server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-280">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-280">Input Parameters</span></span>

- <span data-ttu-id="62fa7-281">**client_ptr**: указатель на блок управления клиентом SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-281">**client_ptr** Pointer to SNTP Client control block.</span></span>

- <span data-ttu-id="62fa7-282">**receive_status**: указатель на сведения о том, получает ли клиент допустимые обновления.</span><span class="sxs-lookup"><span data-stu-id="62fa7-282">**receive_status** Pointer to indicator if Client is receiving valid updates.</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-283">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-283">Return Values</span></span>

- <span data-ttu-id="62fa7-284">**NX_SUCCESS** (0x00): клиент успешно получил состояние обновления.</span><span class="sxs-lookup"><span data-stu-id="62fa7-284">**NX_SUCCESS** (0x00) Client successfully received update status</span></span>

- <span data-ttu-id="62fa7-285">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="62fa7-285">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62fa7-286">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-286">Allowed From</span></span>

<span data-ttu-id="62fa7-287">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="62fa7-287">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-288">Например, .</span><span class="sxs-lookup"><span data-stu-id="62fa7-288">Example</span></span>

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_receiving_updates(client_ptr, 
                                     &receive_status);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is currently receiving valid updates.  */

```

## <a name="nx_sntp_client_request_unicast_time"></a><span data-ttu-id="62fa7-289">nx_sntp_client_request_unicast_time</span><span class="sxs-lookup"><span data-stu-id="62fa7-289">nx_sntp_client_request_unicast_time</span></span>

<span data-ttu-id="62fa7-290">Отправка одноадресного запроса непосредственно на сервер NTP</span><span class="sxs-lookup"><span data-stu-id="62fa7-290">Send a unicast request directly to the NTP Server</span></span>


### <a name="prototype"></a><span data-ttu-id="62fa7-291">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-291">Prototype</span></span>

```C
UINT nx_sntp_client_request_unicast_time(NX_SNTP_CLIENT *client_ptr, 
                                                  UINT wait_option);
```

### <a name="description"></a><span data-ttu-id="62fa7-292">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-292">Description</span></span>

<span data-ttu-id="62fa7-293">Эта служба позволяет приложению асинхронно отправить одноадресный запрос серверу NTP напрямую из задачи потока клиента SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-293">This service allows the application to directly send a unicast request to the NTP server asynchronously from the SNTP Client thread task.</span></span> <span data-ttu-id="62fa7-294">Параметр wait задает время ожидания ответа.</span><span class="sxs-lookup"><span data-stu-id="62fa7-294">The wait option specifies how long to wait for a response.</span></span> <span data-ttu-id="62fa7-295">Если запрос выполнен успешно, приложение может использовать другие службы клиента SNTP для получения последнего времени.</span><span class="sxs-lookup"><span data-stu-id="62fa7-295">If successful, the application can use other SNTP Client services to obtain the latest time.</span></span> <span data-ttu-id="62fa7-296">Дополнительные сведения см. в разделе **Асинхронные одноадресные запросы SNTP**.</span><span class="sxs-lookup"><span data-stu-id="62fa7-296">See section **SNTP Asynchronous Unicast Requests** for more details.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-297">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-297">Input Parameters</span></span>

- <span data-ttu-id="62fa7-298">**client_ptr**: указатель на блок управления клиентом SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-298">**client_ptr** Pointer to SNTP Client control block.</span></span>

- <span data-ttu-id="62fa7-299">**Wait_option**: время ожидания ответа NTP, выраженное в тактах таймера.</span><span class="sxs-lookup"><span data-stu-id="62fa7-299">**Wait_option** Wait option for NTP response in timer ticks.</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-300">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-300">Return Values</span></span>

- <span data-ttu-id="62fa7-301">**NX_SUCCESS** (0x00): клиент успешно отправляет и получает обновления в одноадресном режиме.</span><span class="sxs-lookup"><span data-stu-id="62fa7-301">**NX_SUCCESS** (0x00) Client successfully sends and receives unicast update</span></span>

- <span data-ttu-id="62fa7-302">**NX_SNTP_CLIENT_NOT_STARTED** (0xD0B): поток клиента не запущен.</span><span class="sxs-lookup"><span data-stu-id="62fa7-302">**NX_SNTP_CLIENT_NOT_STARTED** (0xD0B) Client thread not started</span></span>

- <span data-ttu-id="62fa7-303">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="62fa7-303">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="62fa7-304">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="62fa7-304">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62fa7-305">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-305">Allowed From</span></span>

<span data-ttu-id="62fa7-306">Потоки</span><span class="sxs-lookup"><span data-stu-id="62fa7-306">Threads</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-307">Например, .</span><span class="sxs-lookup"><span data-stu-id="62fa7-307">Example</span></span>

```C
/* Determine if the SNTP Client is receiving valid udpates.  */
UINT receive_status;

status =  nx_sntp_client_request_unicast_time(client_ptr, 400);

/* If status is NX_SUCCESS and receive_status is NX_TRUE, 
   the client is received a valid response to the unicast request.  */

```

## <a name="nx_sntp_client_run_broadcast"></a><span data-ttu-id="62fa7-308">nx_sntp_client_run_broadcast</span><span class="sxs-lookup"><span data-stu-id="62fa7-308">nx_sntp_client_run_broadcast</span></span>

<span data-ttu-id="62fa7-309">Запуск клиента в широковещательном режиме</span><span class="sxs-lookup"><span data-stu-id="62fa7-309">Run the Client in broadcast mode</span></span>

### <a name="prototype"></a><span data-ttu-id="62fa7-310">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-310">Prototype</span></span>

```C
UINT nx_sntp_client_run_broadcast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="62fa7-311">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-311">Description</span></span>

<span data-ttu-id="62fa7-312">Эта служба запускает клиент в широковещательном режиме, то есть в режиме ожидания широковещательной передачи данных от сервера SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-312">This service starts the Client in broadcast mode where it will wait to receive broadcasts from the SNTP server.</span></span> <span data-ttu-id="62fa7-313">При получении допустимого широковещательного сообщения SNTP сбрасываются счетчики максимального времени ожидания сведений от клиента SNTP и последовательных недопустимых сообщений.</span><span class="sxs-lookup"><span data-stu-id="62fa7-313">If a valid broadcast SNTP message is received, the SNTP client timeout for maximum lapse without an update and count of consecutive invalid messages received are reset.</span></span> <span data-ttu-id="62fa7-314">Если любое из этих ограничений превышено, клиент SNTP устанавливает для сервера состояние "недопустимо", но при этом продолжает ожидать обновления.</span><span class="sxs-lookup"><span data-stu-id="62fa7-314">If the either of these limits are exceeded, the SNTP Client sets the server status to invalid although it will still wait to receive updates.</span></span> <span data-ttu-id="62fa7-315">Приложение может получить состояние сервера от задачи клиента SNTP, в случае наличия проблем остановить клиент SNTP и повторно инициализировать его с другим адресом широковещательной рассылки SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-315">The application can poll the SNTP Client task for server status, and if invalid stop the SNTP Client and reinitialize it with another SNTP broadcast address.</span></span> <span data-ttu-id="62fa7-316">Также можно переключиться на одноадресный сервер SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-316">It can also switch to a unicast SNTP server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-317">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-317">Input Parameters</span></span>

- <span data-ttu-id="62fa7-318">**client_ptr**: указатель на блок управления клиентом SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-318">**client_ptr** Pointer to SNTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-319">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-319">Return Values</span></span>

- <span data-ttu-id="62fa7-320">**status**: фактическое состояние завершения.</span><span class="sxs-lookup"><span data-stu-id="62fa7-320">**status** -------- Actual completion status</span></span>

- <span data-ttu-id="62fa7-321">**NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C): клиент уже запущен.</span><span class="sxs-lookup"><span data-stu-id="62fa7-321">**NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) Client already started</span></span>

- <span data-ttu-id="62fa7-322">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01): клиент не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="62fa7-322">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Client not initialized</span></span>

- <span data-ttu-id="62fa7-323">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="62fa7-323">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="62fa7-324">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="62fa7-324">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62fa7-325">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-325">Allowed From</span></span>

<span data-ttu-id="62fa7-326">Потоки</span><span class="sxs-lookup"><span data-stu-id="62fa7-326">Threads</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-327">Например, .</span><span class="sxs-lookup"><span data-stu-id="62fa7-327">Example</span></span>

```C
/* Start Client running in broadcast mode.  */
status =  nx_sntp_client_run_broadcast(client_ptr);

/* If status is NX_SUCCESS, the client is successfully started.  */

```

## <a name="nx_sntp_client_run_unicast"></a><span data-ttu-id="62fa7-328">nx_sntp_client_run_unicast</span><span class="sxs-lookup"><span data-stu-id="62fa7-328">nx_sntp_client_run_unicast</span></span>

<span data-ttu-id="62fa7-329">Запуск клиента в одноадресном режиме</span><span class="sxs-lookup"><span data-stu-id="62fa7-329">Run the Client in unicast mode</span></span>

### <a name="prototype"></a><span data-ttu-id="62fa7-330">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-330">Prototype</span></span>

```C
UINT nx_sntp_client_run_unicast(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="62fa7-331">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-331">Description</span></span>

<span data-ttu-id="62fa7-332">Эта служба запускает клиент в одноадресном режиме, в котором он периодически отправляет одноадресный запрос на сервер SNTP для обновления времени.</span><span class="sxs-lookup"><span data-stu-id="62fa7-332">This service starts the Client in unicast mode where it periodically sends a unicast request to its SNTP Server for a time update.</span></span> <span data-ttu-id="62fa7-333">При получении допустимого сообщения SNTP сбрасываются счетчики максимального времени ожидания сведений от клиента SNTP, начального интервала опроса и последовательных недопустимых сообщений.</span><span class="sxs-lookup"><span data-stu-id="62fa7-333">If a valid SNTP message is received, the SNTP client timeout for maximum lapse without an update, initial polling interval and count of consecutive invalid messages received are reset.</span></span> <span data-ttu-id="62fa7-334">Если любое из этих ограничений превышено, клиент SNTP устанавливает для сервера состояние "недопустимо", но при этом продолжает опрашивать сервер и получать обновления.</span><span class="sxs-lookup"><span data-stu-id="62fa7-334">If the either of these limits are exceeded, the SNTP Client sets the Server status to invalid although it will still poll and wait to receive updates.</span></span> <span data-ttu-id="62fa7-335">Приложение может получить состояние сервера от задачи клиента SNTP, в случае наличия проблем остановить клиент SNTP и повторно инициализировать его с другим адресом одноадресной передачи данных SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-335">The application can poll the SNTP Client task for server status, and if invalid stop the SNTP Client and reinitialize it with another SNTP unicast address.</span></span> <span data-ttu-id="62fa7-336">Также можно переключиться на широковещательный сервер SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-336">It can also switch to a broadcast SNTP server.</span></span>

<span data-ttu-id="62fa7-337">.</span><span class="sxs-lookup"><span data-stu-id="62fa7-337">.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-338">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-338">Input Parameters</span></span>

- <span data-ttu-id="62fa7-339">**client_ptr**: указатель на блок управления клиентом SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-339">**client_ptr** Pointer to SNTP Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-340">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-340">Return Values</span></span>

- <span data-ttu-id="62fa7-341">**NX_SUCCESS** (0x00): клиент успешно запущен в одноадресном режиме.</span><span class="sxs-lookup"><span data-stu-id="62fa7-341">**NX_SUCCESS** (0x00) Successfully started Client in unicast mode</span></span>

- <span data-ttu-id="62fa7-342">**NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C): клиент уже запущен.</span><span class="sxs-lookup"><span data-stu-id="62fa7-342">**NX_SNTP_CLIENT_ALREADY_STARTED** (0xD0C) Client already started</span></span>

- <span data-ttu-id="62fa7-343">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01): клиент не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="62fa7-343">**NX_SNTP_CLIENT_NOT_INITIALIZED** (0xD01) Client not initialized</span></span>

- <span data-ttu-id="62fa7-344">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="62fa7-344">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

- <span data-ttu-id="62fa7-345">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект службы.</span><span class="sxs-lookup"><span data-stu-id="62fa7-345">NX_CALLER_ERROR (0x11) Invalid caller of service</span></span>


### <a name="allowed-from"></a><span data-ttu-id="62fa7-346">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-346">Allowed From</span></span>

<span data-ttu-id="62fa7-347">Потоки</span><span class="sxs-lookup"><span data-stu-id="62fa7-347">Threads</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-348">Например, .</span><span class="sxs-lookup"><span data-stu-id="62fa7-348">Example</span></span>

```C
/* Start the Client in unicast mode. */
status =  nx_sntp_client_run_unicast(client_ptr);

/* If status = NX_SUCCESS, the Client was successfully started.  */

```

## <a name="nx_sntp_client_set_local_time"></a><span data-ttu-id="62fa7-349">nx_sntp_client_set_local_time</span><span class="sxs-lookup"><span data-stu-id="62fa7-349">nx_sntp_client_set_local_time</span></span>

<span data-ttu-id="62fa7-350">Настройка местного времени клиента SNTP</span><span class="sxs-lookup"><span data-stu-id="62fa7-350">Set the SNTP Client local time</span></span>

### <a name="prototype"></a><span data-ttu-id="62fa7-351">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-351">Prototype</span></span>

```C
UINT nx_sntp_client_set_local_time(NX_SNTP_CLIENT *client_ptr , 
                                ULONG seconds, ULONG fraction);

```

### <a name="description"></a><span data-ttu-id="62fa7-352">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-352">Description</span></span>

<span data-ttu-id="62fa7-353">Эта служба задает полученное время в качестве местного времени для клиента SNTP в формате SNTP (секунды и дробный компонент, который обозначает доли секунды в шестнадцатеричном формате).</span><span class="sxs-lookup"><span data-stu-id="62fa7-353">This service sets the SNTP Client local time with the input time, in SNTP format e.g. seconds and ‘fraction’ which is the format for putting fractions of a second in hexadecimal format.</span></span> <span data-ttu-id="62fa7-354">Она предназначена для обновления местного времени клиента SNTP по данным от независимого источника, например часов реального времени.</span><span class="sxs-lookup"><span data-stu-id="62fa7-354">It is intended for updating the SNTP Client local time from an independent time keeper, e.g. a real time clock.</span></span> <span data-ttu-id="62fa7-355">Протокол SNTP поддерживает обновление времени SNTP, чтобы показания локальных часов не отклонялись от истинного времени.</span><span class="sxs-lookup"><span data-stu-id="62fa7-355">The SNTP protocol is intended for SNTP time updates to keep local clock time from ‘drifting’.</span></span> <span data-ttu-id="62fa7-356">Хотя этот режим и не рекомендуется, обновления времени с сервера SNTP могут являться единственным источником местного времени для клиента SNTP, если на устройстве приложения нет независимого источника времени.</span><span class="sxs-lookup"><span data-stu-id="62fa7-356">SNTP server time updates can be, but are not intended to be the sole input to the SNTP Client local time if there is no independent time keeper on the application device.</span></span>

<span data-ttu-id="62fa7-357">Этот API также можно использовать для предоставления клиенту SNTP базового времени перед запуском потока клиента SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-357">This API can also be used to give the SNTP Client a base time before starting the SNTP Client thread.</span></span> <span data-ttu-id="62fa7-358">Местное время клиента SNTP сравнивается с полученными обновлениями для проверки допустимости данных.</span><span class="sxs-lookup"><span data-stu-id="62fa7-358">The SNTP Client local time is compared to received updates for valid time data.</span></span> <span data-ttu-id="62fa7-359">При первом получении обновления может возникнуть очень большое несоответствие.</span><span class="sxs-lookup"><span data-stu-id="62fa7-359">For the first time update received, there might be a very large discrepancy.</span></span> <span data-ttu-id="62fa7-360">Поэтому у клиента SNTP есть параметр, позволяющий игнорировать расхождение при первом обновлении.</span><span class="sxs-lookup"><span data-stu-id="62fa7-360">Therefore there is an option for the SNTP Client to ignore the discrepancy on the first update.</span></span> <span data-ttu-id="62fa7-361">Это позволяет запустить клиент SNTP без указания базового времени.</span><span class="sxs-lookup"><span data-stu-id="62fa7-361">In this manner, the SNTP Client can start without a base time.</span></span> <span data-ttu-id="62fa7-362">Входное значение времени можно получить от известных источников времени эпохи (доступны через Интернет), которое выражается в количестве секунд, прошедших с 1-го января 1900 года (эта дата актуальна до начала следующей эпохи, то есть до 2036 года).</span><span class="sxs-lookup"><span data-stu-id="62fa7-362">Input time can be obtained from known epoch times (usually available on the Internet) and are computed as the number of seconds since January 1, 1900 (until 2036 when a new ‘epoch’ will be started.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-363">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-363">Input Parameters</span></span>

- <span data-ttu-id="62fa7-364">**client_ptr**: указатель на блок управления клиентом SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-364">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="62fa7-365">**seconds**: компонент секунд во входных данных времени.</span><span class="sxs-lookup"><span data-stu-id="62fa7-365">**seconds** Seconds component of the time input</span></span>

- <span data-ttu-id="62fa7-366">**fraction**: компонент с долей секунды в дробном формате SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-366">**fraction** Subseconds component in the SNTP fraction format</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-367">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-367">Return Values</span></span>

- <span data-ttu-id="62fa7-368">**NX_SUCCESS** (0x00): местное время успешно задано.</span><span class="sxs-lookup"><span data-stu-id="62fa7-368">**NX_SUCCESS** (0x00) Successfully set local time</span></span>

- <span data-ttu-id="62fa7-369">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="62fa7-369">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62fa7-370">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-370">Allowed From</span></span>

<span data-ttu-id="62fa7-371">Инициализация</span><span class="sxs-lookup"><span data-stu-id="62fa7-371">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-372">Например, .</span><span class="sxs-lookup"><span data-stu-id="62fa7-372">Example</span></span>

```C
/* Set the SNTP Client local time. */
base_seconds =  0xd2c50b71;
base_fraction = 0xa132db1e;

status =  nx_sntp_client_set_local_time(&demo_client, 
                                        base_seconds, 
                                        base_fraction);

/* If status is NX_SUCCESS an SNTP Client time 
   was successfully set.  */

```

## <a name="nx_sntp_client_set_time_update_notify"></a><span data-ttu-id="62fa7-373">nx_sntp_client_set_time_update_notify</span><span class="sxs-lookup"><span data-stu-id="62fa7-373">nx_sntp_client_set_time_update_notify</span></span>

<span data-ttu-id="62fa7-374">Настройка обратного вызова для обновления SNTP</span><span class="sxs-lookup"><span data-stu-id="62fa7-374">Set the SNTP update callback</span></span>

### <a name="prototype"></a><span data-ttu-id="62fa7-375">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-375">Prototype</span></span>

```C
UINT nx_sntp_client_set_time_update_notify(NX_SNTP_CLIENT *client_ptr, 
                           VOID (time_update_cb)(NX_SNTP_TIME_MESSAGE 
                        *time_update_ptr, NX_SNTP_TIME *local_time)));

```

### <a name="description"></a><span data-ttu-id="62fa7-376">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-376">Description</span></span>

<span data-ttu-id="62fa7-377">Эта служба задает обратный вызов, позволяющий оповестить приложение о получении допустимого обновления времени клиентом SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-377">This service sets callback to notify the application when the SNTP Client receives a valid time update.</span></span> <span data-ttu-id="62fa7-378">Она передает полученное сообщение SNTP и местное время клиента SNTP (обычно они совпадают) в формате NTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-378">It supplies the actual SNTP message and the SNTP Client’s local time (usually the same) in NTP format.</span></span> <span data-ttu-id="62fa7-379">Приложение может напрямую применить данные NTP или вызвать службу *nx_sntp_client_utility_display_date_time* для преобразования времени в удобочитаемый формат.</span><span class="sxs-lookup"><span data-stu-id="62fa7-379">The application can use the NTP data directly or call the *nx_sntp_client_utility_display_date_time service* to convert the time to human readable format.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-380">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-380">Input Parameters</span></span>

- <span data-ttu-id="62fa7-381">**client_ptr**: указатель на блок управления клиентом SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-381">**client_ptr** Pointer to SNTP Client control block</span></span>

- <span data-ttu-id="62fa7-382">**time_update_cb**: указатель на функцию обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="62fa7-382">**time_update_cb** Pointer to callback function</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-383">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-383">Return Values</span></span>

- <span data-ttu-id="62fa7-384">**NX_SUCCESS** (0X00): обратный вызов успешно задан.</span><span class="sxs-lookup"><span data-stu-id="62fa7-384">**NX_SUCCESS** (0x00) Successfully set callback</span></span>

- <span data-ttu-id="62fa7-385">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="62fa7-385">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62fa7-386">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-386">Allowed From</span></span>

<span data-ttu-id="62fa7-387">Инициализация</span><span class="sxs-lookup"><span data-stu-id="62fa7-387">Initialization</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-388">Например, .</span><span class="sxs-lookup"><span data-stu-id="62fa7-388">Example</span></span>

```C
/* Set the SNTP Client time update callback. */
VOID client_time_update_notify(NX_SNTP_TIME_MESSAGE *time_update_ptr, 
                                           NX_SNTP_TIME *local time);

NX_SNTP_CLIENT demo_client;


status = nx_sntp_client_set_time_update_notify(&demo_client, 
                                            time_update_cb);

/* If status is NX_SUCCESS an SNTP Client 
   time update callback was successfully set.  */

```

## <a name="nx_sntp_client_stop"></a><span data-ttu-id="62fa7-389">nx_sntp_client_stop</span><span class="sxs-lookup"><span data-stu-id="62fa7-389">nx_sntp_client_stop</span></span>

<span data-ttu-id="62fa7-390">Остановка потока клиента SNTP</span><span class="sxs-lookup"><span data-stu-id="62fa7-390">Stop the SNTP Client thread</span></span>

### <a name="prototype"></a><span data-ttu-id="62fa7-391">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-391">Prototype</span></span>

```C
UINT nx_sntp_client_stop(NX_SNTP_CLIENT *client_ptr);
```

### <a name="description"></a><span data-ttu-id="62fa7-392">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-392">Description</span></span>

<span data-ttu-id="62fa7-393">Эта служба останавливает поток клиента SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-393">This service stops the SNTP Client thread.</span></span> <span data-ttu-id="62fa7-394">Задачи потока клиента SNTP, который работает в бесконечном цикле, приостанавливаются при каждой итерации, чтобы передать другим службам контроль за состоянием клиента SNTP и позволить приложениям выполнять вызовы API на клиенте SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-394">The SNTP Client thread tasks, which runs in an infinite loop, pauses on every iteration to release control of the SNTP Client state and allow applications to make API calls on the SNTP Client.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-395">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-395">Input Parameters</span></span>

- <span data-ttu-id="62fa7-396">**client_ptr**: указатель на блок управления клиентом SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-396">**client_ptr** Pointer to SNTP Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-397">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-397">Return Values</span></span>

- <span data-ttu-id="62fa7-398">**NX_SUCCESS** (0x00): поток клиента успешно остановлен.</span><span class="sxs-lookup"><span data-stu-id="62fa7-398">**NX_SUCCESS** (0x00) Successful stopped Client thread</span></span>

- <span data-ttu-id="62fa7-399">**NX_SNTP_CLIENT_NOT_STARTED** (0xDB): поток клиента SNTP не запущен.</span><span class="sxs-lookup"><span data-stu-id="62fa7-399">**NX_SNTP_CLIENT_NOT_STARTED** (0xDB) SNTP Client thread not started</span></span>

- <span data-ttu-id="62fa7-400">NX_PTR_ERROR (0x07): недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="62fa7-400">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62fa7-401">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-401">Allowed From</span></span>

<span data-ttu-id="62fa7-402">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="62fa7-402">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-403">Например, .</span><span class="sxs-lookup"><span data-stu-id="62fa7-403">Example</span></span>

```C
/* Stop the SNTP Client. */
status =  nx_sntp_client_stop(&demo_client);

/* If status is NX_SUCCESS an SNTP 
   Client instance was successfully stopped.  */

```

## <a name="nx_sntp_client_utility_display_date_time"></a><span data-ttu-id="62fa7-404">nx_sntp_client_utility_display_date_time</span><span class="sxs-lookup"><span data-stu-id="62fa7-404">nx_sntp_client_utility_display_date_time</span></span>

<span data-ttu-id="62fa7-405">Преобразование времени NTP в строку даты и времени</span><span class="sxs-lookup"><span data-stu-id="62fa7-405">Convert an NTP Time to Date and Time string</span></span>

### <a name="prototype"></a><span data-ttu-id="62fa7-406">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-406">Prototype</span></span>

```C
UINT nx_sntp_client_utility_display_date_time (NX_SNTP_CLIENT 
                      *client_ptr, CHAR *buffer, UINT length);

```

### <a name="description"></a><span data-ttu-id="62fa7-407">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-407">Description</span></span>

<span data-ttu-id="62fa7-408">Эта служба преобразует местное время клиента SNTP в формат даты "год, месяц, день" и возвращает эту дату в предоставленном буфере.</span><span class="sxs-lookup"><span data-stu-id="62fa7-408">This service converts the SNTP Client local time to a year month date format and returns the date in the supplied buffer.</span></span> <span data-ttu-id="62fa7-409">Значение NX_SNTP_CURRENT_YEAR не обязано совпадать с годом в текущем времени клиента, но должно быть определено.</span><span class="sxs-lookup"><span data-stu-id="62fa7-409">The NX_SNTP_CURRENT_YEAR need not be the same year as the current Client time but it must be defined.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-410">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-410">Input Parameters</span></span>

- <span data-ttu-id="62fa7-411">**client_ptr**: указатель на клиент SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-411">**client_ptr Pointer to SNTP Client**</span></span>

- <span data-ttu-id="62fa7-412">**buffer**: указатель на буфер для хранения даты.</span><span class="sxs-lookup"><span data-stu-id="62fa7-412">**buffer** Pointer to buffer to store date</span></span>

- <span data-ttu-id="62fa7-413">**length**: размер входного буфера.</span><span class="sxs-lookup"><span data-stu-id="62fa7-413">**length** Size of input buffer</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-414">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-414">Return Values</span></span>

- <span data-ttu-id="62fa7-415">**NX_SUCCESS** (0x00): успешное преобразование</span><span class="sxs-lookup"><span data-stu-id="62fa7-415">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="62fa7-416">**NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08): значение NX_SNTP_CURRENT_YEAR не определено или местное время клиента не задано.</span><span class="sxs-lookup"><span data-stu-id="62fa7-416">**NX_SNTP_ERROR_CONVERTING_DATETIME** (0xD08) NX_SNTP_CURRENT_YEAR not defined or no local client time established</span></span>

- <span data-ttu-id="62fa7-417">**NX_SNTP_INVALID_DATETIME_BUFFER** (0xD07): недостаточная длина буфера.</span><span class="sxs-lookup"><span data-stu-id="62fa7-417">**NX_SNTP_INVALID_DATETIME_BUFFER** (0xD07) Insufficient buffer length</span></span>


### <a name="allowed-from"></a><span data-ttu-id="62fa7-418">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-418">Allowed From</span></span>

<span data-ttu-id="62fa7-419">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="62fa7-419">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-420">Например, .</span><span class="sxs-lookup"><span data-stu-id="62fa7-420">Example</span></span>

```C
/* Convert and display the Client’s local time. */

status =  nx_sntp_client_utility_display_date_time(client_ptr , 
                                        buffer, sizeof(buffer));

/* If status is NX_SUCCESS, 
   date was successfully written to buffer.  */

```

## <a name="nx_sntp_client_utility_msecs_to_fraction"></a><span data-ttu-id="62fa7-421">nx_sntp_client_utility_msecs_to_fraction</span><span class="sxs-lookup"><span data-stu-id="62fa7-421">nx_sntp_client_utility_msecs_to_fraction</span></span>

<span data-ttu-id="62fa7-422">Преобразование миллисекунд в дробный компонент NTP</span><span class="sxs-lookup"><span data-stu-id="62fa7-422">Convert milliseconds to an NTP fraction component</span></span>

### <a name="prototype"></a><span data-ttu-id="62fa7-423">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-423">Prototype</span></span>

```C
UINT nx_sntp_client_utility_msecs_to_fraction (ULONG milliseconds,   
                                                 ULONG *fraction);

```

### <a name="description"></a><span data-ttu-id="62fa7-424">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-424">Description</span></span>

<span data-ttu-id="62fa7-425">Эта служба преобразует миллисекунды из входных данных в дробный компонент NTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-425">This service converts the input milliseconds to the NTP fraction component.</span></span> <span data-ttu-id="62fa7-426">Она предназначена для использования с приложениями, которые задают для клиента SNTP базовое время в формате, отличном от стандарта NTP (секунды и дробный компонент).</span><span class="sxs-lookup"><span data-stu-id="62fa7-426">It is intended for use with applications that have a starting base time for the SNTP Client but not in NTP seconds/fraction format.</span></span> <span data-ttu-id="62fa7-427">Чтобы дробная часть была допустимой, число миллисекунд должно не превышать 1000.</span><span class="sxs-lookup"><span data-stu-id="62fa7-427">The number of milliseconds must be less than 1000 to make a valid fraction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-428">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-428">Input Parameters</span></span>

- <span data-ttu-id="62fa7-429">**milliseconds**: количество миллисекунд для преобразования.</span><span class="sxs-lookup"><span data-stu-id="62fa7-429">**milliseconds Milliseconds to convert**</span></span>

- <span data-ttu-id="62fa7-430">**fraction**: указатель на миллисекунды, преобразованные в дробный компонент.</span><span class="sxs-lookup"><span data-stu-id="62fa7-430">**fraction** Pointer to milliseconds converted to fraction</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-431">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-431">Return Values</span></span>

- <span data-ttu-id="62fa7-432">**NX_SUCCESS** (0x00): успешное преобразование</span><span class="sxs-lookup"><span data-stu-id="62fa7-432">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="62fa7-433">**NX_SNTP_OVERFLOW_ERROR** (0xD32): ошибка преобразования времени в дату.</span><span class="sxs-lookup"><span data-stu-id="62fa7-433">**NX_SNTP_OVERFLOW_ERROR** (0xD32) Error converting time to a date</span></span>

- <span data-ttu-id="62fa7-434">NX_SNTP_INVALID_TIME (0xD30): недопустимые входные данные SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-434">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62fa7-435">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-435">Allowed From</span></span>

<span data-ttu-id="62fa7-436">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="62fa7-436">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-437">Например, .</span><span class="sxs-lookup"><span data-stu-id="62fa7-437">Example</span></span>

```C
/* Convert the milliseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(milliseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, 
   data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_usecs_to_fraction"></a><span data-ttu-id="62fa7-438">nx_sntp_client_utility_usecs_to_fraction</span><span class="sxs-lookup"><span data-stu-id="62fa7-438">nx_sntp_client_utility_usecs_to_fraction</span></span>

<span data-ttu-id="62fa7-439">Преобразование микросекунд в дробный компонент NTP</span><span class="sxs-lookup"><span data-stu-id="62fa7-439">Convert microseconds to an NTP fraction component</span></span>

### <a name="prototype"></a><span data-ttu-id="62fa7-440">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-440">Prototype</span></span>

```C
UINT nx_sntp_client_utility_usecs_to_fraction (ULONG microseconds,   
                                                 ULONG *fraction);

```
### <a name="description"></a><span data-ttu-id="62fa7-441">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-441">Description</span></span>

<span data-ttu-id="62fa7-442">Эта служба преобразует микросекунды из входных данных в дробный компонент NTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-442">This service converts the input microseconds to the NTP fraction component.</span></span> <span data-ttu-id="62fa7-443">Она предназначена для использования с приложениями, которые задают для клиента SNTP базовое время в формате, отличном от стандарта NTP (секунды и дробный компонент).</span><span class="sxs-lookup"><span data-stu-id="62fa7-443">It is intended for use with applications that have a starting base time for the SNTP Client but not in NTP seconds/fraction format.</span></span> <span data-ttu-id="62fa7-444">Чтобы дробная часть была допустимой, число микросекунд должно не превышать 1 000 000.</span><span class="sxs-lookup"><span data-stu-id="62fa7-444">The number of microseconds must be less than 1000000 to make a valid fraction.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-445">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-445">Input Parameters</span></span>

- <span data-ttu-id="62fa7-446">**microseconds**: количество микросекунд для преобразования.</span><span class="sxs-lookup"><span data-stu-id="62fa7-446">**microseconds** Microseconds to convert</span></span>

- <span data-ttu-id="62fa7-447">**fraction**: указатель на микросекунды, преобразованные в дробный компонент.</span><span class="sxs-lookup"><span data-stu-id="62fa7-447">**fraction** Pointer to microseconds converted to fraction</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-448">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-448">Return Values</span></span>

- <span data-ttu-id="62fa7-449">**NX_SUCCESS** (0x00): успешное преобразование</span><span class="sxs-lookup"><span data-stu-id="62fa7-449">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="62fa7-450">**NX_SNTP_OVERFLOW_ERROR** (0xD32): ошибка преобразования времени в дату.</span><span class="sxs-lookup"><span data-stu-id="62fa7-450">**NX_SNTP_OVERFLOW_ERROR** (0xD32) Error converting time to a date</span></span>

- <span data-ttu-id="62fa7-451">NX_SNTP_INVALID_TIME (0xD30): недопустимые входные данные SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-451">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62fa7-452">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-452">Allowed From</span></span>

<span data-ttu-id="62fa7-453">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="62fa7-453">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-454">Например, .</span><span class="sxs-lookup"><span data-stu-id="62fa7-454">Example</span></span>

```C
/* Convert the microseconds to a fraction. */


status =  nx_sntp_client_utility_msecs_to_fraction(microseconds, 
                                                     &fraction);

/* If status is NX_SUCCESS, data was successfully converted.  */

```

## <a name="nx_sntp_client_utility_fraction_to_usecs"></a><span data-ttu-id="62fa7-455">nx_sntp_client_utility_fraction_to_usecs</span><span class="sxs-lookup"><span data-stu-id="62fa7-455">nx_sntp_client_utility_fraction_to_usecs</span></span>

<span data-ttu-id="62fa7-456">Преобразование дробного компонента NTP в микросекунды</span><span class="sxs-lookup"><span data-stu-id="62fa7-456">Convert an NTP fraction component to microseconds</span></span>

### <a name="prototype"></a><span data-ttu-id="62fa7-457">Прототип</span><span class="sxs-lookup"><span data-stu-id="62fa7-457">Prototype</span></span>

```C
UINT nx_sntp_client_utility_fraction_to_usecs (ULONG fraction,   
                                         ULONG *microseconds);

```

### <a name="description"></a><span data-ttu-id="62fa7-458">Описание</span><span class="sxs-lookup"><span data-stu-id="62fa7-458">Description</span></span>

<span data-ttu-id="62fa7-459">Эта служба преобразует дробный компонент NTP из входных данных в микросекунды.</span><span class="sxs-lookup"><span data-stu-id="62fa7-459">This service converts the input NTP fraction component to microseconds.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="62fa7-460">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="62fa7-460">Input Parameters</span></span>

- <span data-ttu-id="62fa7-461">**fraction**: дробный компонент для преобразования.</span><span class="sxs-lookup"><span data-stu-id="62fa7-461">**fraction Fraction to convert**</span></span>

- <span data-ttu-id="62fa7-462">**microseconds**: указатель на дробный компонент, преобразованный в микросекунды.</span><span class="sxs-lookup"><span data-stu-id="62fa7-462">**microseconds** Pointer to fraction converted to microseconds</span></span>

### <a name="return-values"></a><span data-ttu-id="62fa7-463">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="62fa7-463">Return Values</span></span>

- <span data-ttu-id="62fa7-464">**NX_SUCCESS** (0x00): успешное преобразование</span><span class="sxs-lookup"><span data-stu-id="62fa7-464">**NX_SUCCESS** (0x00) Successful conversion</span></span>

- <span data-ttu-id="62fa7-465">NX_SNTP_INVALID_TIME (0xD30): недопустимые входные данные SNTP.</span><span class="sxs-lookup"><span data-stu-id="62fa7-465">NX_SNTP_INVALID_TIME (0xD30) Invalid SNTP data input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="62fa7-466">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="62fa7-466">Allowed From</span></span>

<span data-ttu-id="62fa7-467">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="62fa7-467">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="62fa7-468">Пример</span><span class="sxs-lookup"><span data-stu-id="62fa7-468">Example</span></span>

```C
/* Convert the fraction to microseconds. */


status =  nx_sntp_client_utility_fraction_to_msecs(fraction, 
                                             &microseconds);

/* If status is NX_SUCCESS, data was successfully converted.  */
```