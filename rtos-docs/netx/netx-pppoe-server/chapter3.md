---
title: Глава 3. Описание служб сервера PPPoE для ОСРВ Azure
description: В этой главе описываются все службы сервера NetX PPPoE для ОСРВ Azure (перечислены ниже) в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d1137fae4dfea428d50e2defed94de6a838b01c6
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815120"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-server-services"></a><span data-ttu-id="673ee-103">Глава 3. Описание служб сервера PPPoE для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="673ee-103">Chapter 3 - Description of Azure RTOS NetX PPPoE Server Services</span></span>

<span data-ttu-id="673ee-104">В этой главе описываются все службы сервера NetX PPPoE для ОСРВ Azure (перечислены ниже) в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="673ee-104">This chapter contains a description of all Azure RTOS NetX PPPoE Server services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="673ee-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, используемым для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="673ee-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="673ee-106">**nx_pppoe_server_create**: *создание экземпляра сервера PPPoE*</span><span class="sxs-lookup"><span data-stu-id="673ee-106">**nx_pppoe_server_create**: *Create a PPPoE Server instance*</span></span>

- <span data-ttu-id="673ee-107">**nx_pppoe_server_ac_name_set**: *задание имени концентратора доступа*</span><span class="sxs-lookup"><span data-stu-id="673ee-107">**nx_pppoe_server_ac_name_set**: *Set Access Concentrator name*</span></span>

- <span data-ttu-id="673ee-108">**nx_pppoe_server_delete**: *удаление экземпляра сервера PPPoE*</span><span class="sxs-lookup"><span data-stu-id="673ee-108">**nx_pppoe_server_delete**: *Delete a PPPoE Server instance*</span></span>

- <span data-ttu-id="673ee-109">**nx_pppoe_server_enable**: *включение служб сервера PPPoE*</span><span class="sxs-lookup"><span data-stu-id="673ee-109">**nx_pppoe_server_enable**: *Enable PPPoE Server services*</span></span>

- <span data-ttu-id="673ee-110">**nx_pppoe_server_disable**: *отключение служб сервера PPPoE*</span><span class="sxs-lookup"><span data-stu-id="673ee-110">**nx_pppoe_server_disable**: *Disable PPPoE Server services*</span></span>

- <span data-ttu-id="673ee-111">**nx_pppoe_server_callback_notify_set**: *настройка функций уведомления об обратном вызове сервера PPPoE*</span><span class="sxs-lookup"><span data-stu-id="673ee-111">**nx_pppoe_server_callback_notify_set**: *Set PPPoE Server callback notify functions*</span></span>

- <span data-ttu-id="673ee-112">**nx_pppoe_server_service_name_set**: *настройка имени службы сервера PPPoE*</span><span class="sxs-lookup"><span data-stu-id="673ee-112">**nx_pppoe_server_service_name_set**: *Set PPPoE Server service name*</span></span>

- <span data-ttu-id="673ee-113">**nx_pppoe_server_session_send**: *отправка данных сервера PPPoE в указанный сеанс*</span><span class="sxs-lookup"><span data-stu-id="673ee-113">**nx_pppoe_server_session_send**: *Send PPPoE Server data to specified session*</span></span>

- <span data-ttu-id="673ee-114">**nx_pppoe_server_session_packet_send**: *отправка пакета сервера PPPoE в указанный сеанс*</span><span class="sxs-lookup"><span data-stu-id="673ee-114">**nx_pppoe_server_session_packet_send**: *Send PPPoE Server packet to specified session*</span></span>

- <span data-ttu-id="673ee-115">**nx_pppoe_server_session_terminate**: *завершение указанного сеанса PPPoE*</span><span class="sxs-lookup"><span data-stu-id="673ee-115">**nx_pppoe_server_session_terminate**: *Terminate the specified PPPoE session*</span></span>

- <span data-ttu-id="673ee-116">**nx_pppoe_server_session_get**: *получение сведений об указанных сеансах*</span><span class="sxs-lookup"><span data-stu-id="673ee-116">**nx_pppoe_server_session_get**: *Get the specified session information*</span></span>

## <a name="nx_pppoe_server_create"></a><span data-ttu-id="673ee-117">nx_pppoe_server_create</span><span class="sxs-lookup"><span data-stu-id="673ee-117">nx_pppoe_server_create</span></span>

<span data-ttu-id="673ee-118">Создание экземпляра сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-118">Create a PPPoE Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="673ee-119">Прототип</span><span class="sxs-lookup"><span data-stu-id="673ee-119">Prototype</span></span>

```c
UINT nx_pppoe_server_create(NX_PPPOE_SERVER *pppoe_server_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority);
```

### <a name="description"></a><span data-ttu-id="673ee-120">Описание</span><span class="sxs-lookup"><span data-stu-id="673ee-120">Description</span></span>

<span data-ttu-id="673ee-121">Эта служба создает экземпляр сервера PPPoE с драйвером ссылки, предоставленным пользователем для указанного экземпляра NetX IP.</span><span class="sxs-lookup"><span data-stu-id="673ee-121">This service creates a PPPoE Server instance with the user supplied link driver for the specified NetX IP instance.</span></span> <span data-ttu-id="673ee-122">Если драйвер ссылки не был инициализирован и включен, программное обеспечение сервера PPPoE выполняет инициализацию драйвера ссылки.</span><span class="sxs-lookup"><span data-stu-id="673ee-122">If link driver has not been initialized, and enabled, PPPoE sever software is responsible initializing the link driver.</span></span>

<span data-ttu-id="673ee-123">Кроме того, приложение должно предоставить созданный ранее пул пакетов для экземпляра сервера PPPoE, который будет использоваться для внутреннего распределения пакетов.</span><span class="sxs-lookup"><span data-stu-id="673ee-123">In addition, the application must supply a previously created packet pool for the PPPoE Server instance to use for internal packet allocation.</span></span>

<span data-ttu-id="673ee-124">Обратите внимание, что поток NetX IP следует создать с более высоким приоритетом, чем приоритет потока сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-124">Note that it is generally a good idea to create the NetX IP thread at a higher priority than the PPPoE Server thread priority.</span></span> <span data-ttu-id="673ee-125">Дополнительные сведения об указании приоритета потока IP см. в службе *nx_ip_create*.</span><span class="sxs-lookup"><span data-stu-id="673ee-125">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="673ee-126">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="673ee-126">Input Parameters</span></span>

- <span data-ttu-id="673ee-127">**pppoe_server_ptr**: указатель на блок управления сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-127">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="673ee-128">**name**: имя этого экземпляра сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-128">**name**: Name of this PPPoE Server instance.</span></span>
- <span data-ttu-id="673ee-129">**ip_ptr**: указатель на блок управления для экземпляра IP</span><span class="sxs-lookup"><span data-stu-id="673ee-129">**ip_ptr**: Pointer to control block for IP instance.</span></span>
- <span data-ttu-id="673ee-130">**interface_index**: индекс интерфейса</span><span class="sxs-lookup"><span data-stu-id="673ee-130">**interface_index**: Interface index.</span></span>
- <span data-ttu-id="673ee-131">**pppoe_link_driver**: драйвер ссылки, предоставленный пользователем</span><span class="sxs-lookup"><span data-stu-id="673ee-131">**pppoe_link_driver**: User supplied link driver.</span></span>
- <span data-ttu-id="673ee-132">**pool_ptr**: указатель на пул пакетов</span><span class="sxs-lookup"><span data-stu-id="673ee-132">**pool_ptr**: Pointer to packet pool.</span></span>
- <span data-ttu-id="673ee-133">**stack_ptr**: указатель на начало области стека потока сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-133">**stack_ptr**: Pointer to start of PPPoE Server thread's stack area.</span></span>
- <span data-ttu-id="673ee-134">**stack_size**: размер в байтах в стеке потока</span><span class="sxs-lookup"><span data-stu-id="673ee-134">**stack_size**: Size in bytes in the thread's stack.</span></span>
- <span data-ttu-id="673ee-135">**priority**: приоритет внутренних потоков сервера PPPoE (1–31)</span><span class="sxs-lookup"><span data-stu-id="673ee-135">**priority**: Priority of internal PPPoE Server threads (1-31).</span></span>

### <a name="return-values"></a><span data-ttu-id="673ee-136">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="673ee-136">Return Values</span></span>

- <span data-ttu-id="673ee-137">**NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное создание сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-137">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server create.</span></span>
- <span data-ttu-id="673ee-138">NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый сервер PPPoE, IP, пул пакетов или указатель стека.</span><span class="sxs-lookup"><span data-stu-id="673ee-138">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server, IP, packet pool, or stack pointer.</span></span>
- <span data-ttu-id="673ee-139">NX_PPPOE_SERVER_INVALID_INTERFACE (0xC2) — недопустимый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="673ee-139">NX_PPPOE_SERVER_INVALID_INTERFACE: (0xC2) Invalid interface.</span></span>
- <span data-ttu-id="673ee-140">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR (0xC3) — недопустимый размер полезных данных пула пакетов.</span><span class="sxs-lookup"><span data-stu-id="673ee-140">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Invalid payload size of packet pool.</span></span>
- <span data-ttu-id="673ee-141">NX_PPPOE_SERVER_MEMORY_SIZE_ERROR (0xC4) — недопустимый размер памяти.</span><span class="sxs-lookup"><span data-stu-id="673ee-141">NX_PPPOE_SERVER_MEMORY_SIZE_ERROR: (0xC4) Invalid memory size.</span></span>
- <span data-ttu-id="673ee-142">NX_PPPOE_SERVER_PRIORITY_ERROR (0xC5) — недопустимый приоритет потока сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-142">NX_PPPOE_SERVER_PRIORITY_ERROR: (0xC5) Invalid priority of PPPoE Server thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="673ee-143">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="673ee-143">Allowed From</span></span>

<span data-ttu-id="673ee-144">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="673ee-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="673ee-145">Например, .</span><span class="sxs-lookup"><span data-stu-id="673ee-145">Example</span></span>

```c
/* Create "my_pppoe_server" for IP instance "my_ip". */
status = nx_pppoe_server_create(&my_pppoe_server, "my PPPoE Server", &my_ip,
                                &my_pool, stack_start, 1024, 2);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully created. */
```

## <a name="nx_pppoe_server_delete"></a><span data-ttu-id="673ee-146">nx_pppoe_server_delete</span><span class="sxs-lookup"><span data-stu-id="673ee-146">nx_pppoe_server_delete</span></span>

<span data-ttu-id="673ee-147">Удаление экземпляра сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-147">Delete a PPPoE Server instance</span></span>

### <a name="prototype"></a><span data-ttu-id="673ee-148">Прототип</span><span class="sxs-lookup"><span data-stu-id="673ee-148">Prototype</span></span>

```c
UINT nx_pppoe_server_delete(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="673ee-149">Описание</span><span class="sxs-lookup"><span data-stu-id="673ee-149">Description</span></span>

<span data-ttu-id="673ee-150">Эта служба удаляет созданный ранее экземпляр сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-150">This service deletes the previously created PPPoE Server instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="673ee-151">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="673ee-151">Input Parameters</span></span>

- <span data-ttu-id="673ee-152">**pppoe_server_ptr**: указатель на блок управления сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-152">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="673ee-153">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="673ee-153">Return Values</span></span>

- <span data-ttu-id="673ee-154">**NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное удаление сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-154">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="673ee-155">NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый указатель сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-155">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="673ee-156">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="673ee-156">Allowed From</span></span>

<span data-ttu-id="673ee-157">Потоки</span><span class="sxs-lookup"><span data-stu-id="673ee-157">Threads</span></span>

### <a name="example"></a><span data-ttu-id="673ee-158">Например, .</span><span class="sxs-lookup"><span data-stu-id="673ee-158">Example</span></span>

```c
/* Delete PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_delete(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" was successfully deleted. */
```

## <a name="nx_pppoe_server_enable"></a><span data-ttu-id="673ee-159">nx_pppoe_server_enable</span><span class="sxs-lookup"><span data-stu-id="673ee-159">nx_pppoe_server_enable</span></span>

<span data-ttu-id="673ee-160">Включение службы сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-160">Enable PPPoE Server service</span></span>

### <a name="prototype"></a><span data-ttu-id="673ee-161">Прототип</span><span class="sxs-lookup"><span data-stu-id="673ee-161">Prototype</span></span>

```c
UINT nx_pppoe_server_enable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="673ee-162">Описание</span><span class="sxs-lookup"><span data-stu-id="673ee-162">Description</span></span>

<span data-ttu-id="673ee-163">Эта служба включает службы сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-163">This service enables the PPPoE Server services.</span></span>

> [!NOTE]
> <span data-ttu-id="673ee-164">Эта функция должна вызываться после *nx_pppoe_server_create* и *nx_pppoe_server_callback_notify_set*.</span><span class="sxs-lookup"><span data-stu-id="673ee-164">This function must be called after *nx_pppoe_server_create* and *nx_pppoe_server_callback_notify_set*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="673ee-165">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="673ee-165">Input Parameters</span></span>

- <span data-ttu-id="673ee-166">**pppoe_server_ptr**: указатель на блок управления сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-166">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="673ee-167">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="673ee-167">Return Values</span></span>

- <span data-ttu-id="673ee-168">**NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное удаление сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-168">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="673ee-169">NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый указатель сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-169">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="673ee-170">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="673ee-170">Allowed From</span></span>

<span data-ttu-id="673ee-171">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="673ee-171">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="673ee-172">Например, .</span><span class="sxs-lookup"><span data-stu-id="673ee-172">Example</span></span>

```c
/* Enable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_enable(&my_pppoe_server);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has enabled. */
```

## <a name="nx_pppoe_server_disable"></a><span data-ttu-id="673ee-173">nx_pppoe_server_disable</span><span class="sxs-lookup"><span data-stu-id="673ee-173">nx_pppoe_server_disable</span></span>

<span data-ttu-id="673ee-174">Отключение службы сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-174">Disable PPPoE Server service</span></span>

### <a name="prototype"></a><span data-ttu-id="673ee-175">Прототип</span><span class="sxs-lookup"><span data-stu-id="673ee-175">Prototype</span></span>

```c
UINT nx_pppoe_server_disable(NX_PPPOE_SERVER *pppoe_server_ptr);
```

### <a name="description"></a><span data-ttu-id="673ee-176">Описание</span><span class="sxs-lookup"><span data-stu-id="673ee-176">Description</span></span>

<span data-ttu-id="673ee-177">Эта служба отключает службы сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-177">This service disables the PPPoE Server services.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="673ee-178">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="673ee-178">Input Parameters</span></span>

- <span data-ttu-id="673ee-179">**pppoe_server_ptr**: указатель на блок управления сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-179">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="673ee-180">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="673ee-180">Return Values</span></span>

- <span data-ttu-id="673ee-181">**NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное удаление сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-181">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="673ee-182">NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый указатель сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-182">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="673ee-183">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="673ee-183">Allowed From</span></span>

<span data-ttu-id="673ee-184">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="673ee-184">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="673ee-185">Например, .</span><span class="sxs-lookup"><span data-stu-id="673ee-185">Example</span></span>

```c
/* Disable PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_disable(&my_pppoe_server);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service has disabled. */
```

## <a name="nx_pppoe_server_callback_notify_set"></a><span data-ttu-id="673ee-186">nx_pppoe_server_callback_notify_set</span><span class="sxs-lookup"><span data-stu-id="673ee-186">nx_pppoe_server_callback_notify_set</span></span>

<span data-ttu-id="673ee-187">Настройка функций уведомления об обратном вызове сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-187">Set PPPoE Server callback notify functions</span></span> 

### <a name="prototype"></a><span data-ttu-id="673ee-188">Прототип</span><span class="sxs-lookup"><span data-stu-id="673ee-188">Prototype</span></span>

```c
UINT nx_pppoe_server_callback_notify_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        VOID (* pppoe_discover_initiation_notify)(UINT session_index,
                ULONG length, UCHAR *data),
        VOID (* pppoe_discover_request_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_notify)(UINT session_index),
        VOID (* pppoe_discover_terminate_confirm)(UINT session_index),
        VOID (* pppoe_data_receive_notify)(UINT session_index,
                ULONG length, UCHAR *data, UINT packet_id),
        VOID (* pppoe_discover_notify)(UINT session_index, UCHAR *data))
```

### <a name="description"></a><span data-ttu-id="673ee-189">Описание</span><span class="sxs-lookup"><span data-stu-id="673ee-189">Description</span></span>

<span data-ttu-id="673ee-190">Эта служба задает функции уведомления об обратном вызове сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-190">This service sets PPPoE Server callback notify functions.</span></span>

> [!NOTE]
> <span data-ttu-id="673ee-191">Эта функция должна вызываться до *nx_pppoe_server_enabl*, а также должен быть установлен указатель на функцию pppoe_data_receive_notify, в противном случае *nx_pppoe_server_enable* завершится сбоем.</span><span class="sxs-lookup"><span data-stu-id="673ee-191">This function must be called before *nx_pppoe_server_enabl, and* the pppoe_data_receive_notify function pointer must be set, if not, *nx_pppoe_server_enable* will be failure.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="673ee-192">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="673ee-192">Input Parameters</span></span>

- <span data-ttu-id="673ee-193">**pppoe_server_ptr**: указатель на блок управления сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-193">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="673ee-194">**pppoe_discover_initiation_notify**: функция приложения, которая вызывается при получении сообщения об инициации обнаружения PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-194">**pppoe_discover_initiation_notify**: Application function that is called whenever PPPoE discover initiation message is received.</span></span> <span data-ttu-id="673ee-195">Если это значение равно NULL, функция обратного вызова инициации обнаружения отключена.</span><span class="sxs-lookup"><span data-stu-id="673ee-195">If this value is NULL, discover initiation callback function is disabled.</span></span>
- <span data-ttu-id="673ee-196">**pppoe_discover_request_notify**: функция приложения, которая вызывается при получении сообщения запроса на обнаружение PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-196">**pppoe_discover_request_notify**: Application function that is called whenever PPPoE discover request message is received.</span></span> <span data-ttu-id="673ee-197">Если это значение равно NULL, функция обратного вызова запроса обнаружения отключена.</span><span class="sxs-lookup"><span data-stu-id="673ee-197">If this value is NULL, discover request callback function is disabled.</span></span>
- <span data-ttu-id="673ee-198">**pppoe_discover_terminate_notify**: функция приложения, которая вызывается при получении сообщения о прекращении обнаружения PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-198">**pppoe_discover_terminate_notify**: Application function that is called whenever PPPoE discover terminate message is received.</span></span> <span data-ttu-id="673ee-199">Если это значение равно NULL, функция обратного вызова для завершения обнаружения отключена.</span><span class="sxs-lookup"><span data-stu-id="673ee-199">If this value is NULL, discover terminate callback function is disabled.</span></span>
- <span data-ttu-id="673ee-200">**pppoe_discover_terminate_confirm**: функция приложения, которая вызывается при отправке сообщения о прекращении обнаружения PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-200">**pppoe_discover_terminate_confirm**: Application function that is called whenever PPPoE discover terminate message is sent.</span></span> <span data-ttu-id="673ee-201">Если это значение равно NULL, функция обратного вызова для завершения обнаружения отключена.</span><span class="sxs-lookup"><span data-stu-id="673ee-201">If this value is NULL, discover terminate callback function is disabled.</span></span>
- <span data-ttu-id="673ee-202">**pppoe_data_receive_notify**: функция приложения, которая вызывается при получении сообщения с данными PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-202">**pppoe_data_receive_notify**: Application function that is called whenever PPPoE data message is received.</span></span> <span data-ttu-id="673ee-203">Это значение должно быть равно нулю.</span><span class="sxs-lookup"><span data-stu-id="673ee-203">This value must not be zero.</span></span>
- <span data-ttu-id="673ee-204">**pppoe_data_send_notify**: функция приложения, которая вызывается при отправке сообщения с данными PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-204">**pppoe_data_send_notify**: Application function that is called whenever PPPoE data message is sent.</span></span> <span data-ttu-id="673ee-205">Если это значение равно NULL, функция обратного вызова для отправки данных отключена.</span><span class="sxs-lookup"><span data-stu-id="673ee-205">If this value is NULL, data send callback function is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="673ee-206">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="673ee-206">Return Values</span></span>

- <span data-ttu-id="673ee-207">**NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное удаление сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-207">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="673ee-208">NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый указатель сервера PPPoE или указатель функции.</span><span class="sxs-lookup"><span data-stu-id="673ee-208">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer or function pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="673ee-209">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="673ee-209">Allowed From</span></span>

<span data-ttu-id="673ee-210">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="673ee-210">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="673ee-211">Например, .</span><span class="sxs-lookup"><span data-stu-id="673ee-211">Example</span></span>

```c
/* Set PPPoE Server callback notify functions, PPPoE Server instance "my_pppoe_server". */

status = nx_pppoe_server_disable(&my_pppoe_server,
                pppoe_discovery_initiation_notify,
                pppoe_discovery_request_notify,
                pppoe_discovery_terminate_notify,
                pppoe_discovery_terminate_confirm,
                pppoe_data_receive_notify,
                pppoe_data_send_notify);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the callback notify functions for "my_pppoe_server" service has set. */
```

## <a name="nx_pppoe_server_ac_name_set"></a><span data-ttu-id="673ee-212">nx_pppoe_server_ac_name_set</span><span class="sxs-lookup"><span data-stu-id="673ee-212">nx_pppoe_server_ac_name_set</span></span>

<span data-ttu-id="673ee-213">Задание имени концентратора доступа</span><span class="sxs-lookup"><span data-stu-id="673ee-213">Set Access Concentrator name</span></span>

### <a name="prototype"></a><span data-ttu-id="673ee-214">Прототип</span><span class="sxs-lookup"><span data-stu-id="673ee-214">Prototype</span></span>

```c
UINT nx_pppoe_server_ac_name_set(
    NX_PPPOE_SERVER *pppoe_server_ptr,
    CHAR *ac_name, UINT ac_name_length,
);
```

### <a name="description"></a><span data-ttu-id="673ee-215">Описание</span><span class="sxs-lookup"><span data-stu-id="673ee-215">Description</span></span>

<span data-ttu-id="673ee-216">Эта функция задает вызов функции имени концентратора доступа.</span><span class="sxs-lookup"><span data-stu-id="673ee-216">This function set Access Concentrator name function call.</span></span>

> [!NOTE]
> <span data-ttu-id="673ee-217">В конце строки ac_name должно быть указано NULL, а длина ac_name соответствует длине, указанной в списке аргументов.</span><span class="sxs-lookup"><span data-stu-id="673ee-217">The string of ac_name must be NULL-terminated and length of ac_name matches the length specified in the argument list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="673ee-218">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="673ee-218">Input Parameters</span></span>

- <span data-ttu-id="673ee-219">**pppoe_server_ptr**: указатель на блок управления сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-219">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="673ee-220">**ac_name**: имя концентратора доступа</span><span class="sxs-lookup"><span data-stu-id="673ee-220">**ac_name**: Access Concentrator name.</span></span>
- <span data-ttu-id="673ee-221">**ac_name_length**: длина параметра ac_ame</span><span class="sxs-lookup"><span data-stu-id="673ee-221">**ac_name_length**: Length of ac_ame.</span></span>

### <a name="return-values"></a><span data-ttu-id="673ee-222">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="673ee-222">Return Values</span></span>

- <span data-ttu-id="673ee-223">**NX_PPPOE_SERVER_SUCCESS** (0x00) — сервер PPPoE успешно задан.</span><span class="sxs-lookup"><span data-stu-id="673ee-223">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server set.</span></span>
- <span data-ttu-id="673ee-224">**NX_PPPOE_SERVER_PTR_ERROR** (0xC1) — недопустимый сервер PPPoE, IP, пул пакетов или указатель стека.</span><span class="sxs-lookup"><span data-stu-id="673ee-224">**NX_PPPOE_SERVER_PTR_ERROR**: (0xC1) Invalid PPPoE Server, IP, packet pool, or stack pointer.</span></span>
- <span data-ttu-id="673ee-225">**NX_SIZE_ERROR** (0x09) — сбой проверки name_length.</span><span class="sxs-lookup"><span data-stu-id="673ee-225">**NX_SIZE_ERROR**: (0x09) Check name_length fail.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="673ee-226">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="673ee-226">Allowed From</span></span>

<span data-ttu-id="673ee-227">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="673ee-227">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="673ee-228">Например, .</span><span class="sxs-lookup"><span data-stu-id="673ee-228">Example</span></span>

```c
/* Set "my PPPoE ac name" for Server instance "my_pppoe_server". */
status = nx_pppoe_server_ac_name_set(&my_pppoe_server, "my PPPoE ac name",16);

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my PPPoE ac name" was successfully set. */
```

## <a name="nx_pppoe_server_service_name_set"></a><span data-ttu-id="673ee-229">nx_pppoe_server_service_name_set</span><span class="sxs-lookup"><span data-stu-id="673ee-229">nx_pppoe_server_service_name_set</span></span>

<span data-ttu-id="673ee-230">Задание имени службы сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-230">Set PPPoE Server service name</span></span>

### <a name="prototype"></a><span data-ttu-id="673ee-231">Прототип</span><span class="sxs-lookup"><span data-stu-id="673ee-231">Prototype</span></span>

```c
UINT nx_pppoe_server_service_name_set(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UCHAR **service_name, UINT service_name_count);
```

### <a name="description"></a><span data-ttu-id="673ee-232">Описание</span><span class="sxs-lookup"><span data-stu-id="673ee-232">Description</span></span>

<span data-ttu-id="673ee-233">Эта служба задает имя службы сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-233">This service sets PPPoE Server service name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="673ee-234">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="673ee-234">Input Parameters</span></span>

- <span data-ttu-id="673ee-235">**pppoe_server_ptr**: указатель на блок управления сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-235">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="673ee-236">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="673ee-236">Return Values</span></span>

- <span data-ttu-id="673ee-237">**NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное удаление сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-237">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="673ee-238">NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый указатель сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-238">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="673ee-239">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="673ee-239">Allowed From</span></span>

<span data-ttu-id="673ee-240">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="673ee-240">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="673ee-241">Например, .</span><span class="sxs-lookup"><span data-stu-id="673ee-241">Example</span></span>

```c
CHAR *nx_pppoe_service_name[] =
{
    "XBB",
    "PRINTER",
    NX_NULL
};

/* Set service name for PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_service_namet_set(&my_pppoe_server,
                                    nx_pppoe_service_name, 2);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" service name has set. */
```

## <a name="nx_pppoe_server_session_send"></a><span data-ttu-id="673ee-242">nx_pppoe_server_session_send</span><span class="sxs-lookup"><span data-stu-id="673ee-242">nx_pppoe_server_session_send</span></span>

<span data-ttu-id="673ee-243">Отправка данных сервера PPPoE в указанный сеанс</span><span class="sxs-lookup"><span data-stu-id="673ee-243">Send PPPoE Server data to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="673ee-244">Прототип</span><span class="sxs-lookup"><span data-stu-id="673ee-244">Prototype</span></span>

```c
UINT nx_pppoe_server_session_send (NX_PPPOE_SERVER *pppoe_server_ptr,
                UINT session_index, UCHAR *data_ptr, UINT data_length);
```

### <a name="description"></a><span data-ttu-id="673ee-245">Описание</span><span class="sxs-lookup"><span data-stu-id="673ee-245">Description</span></span>

<span data-ttu-id="673ee-246">Эта служба отправляет кадр PPPoE, используя указанный идентификатор сеанса.</span><span class="sxs-lookup"><span data-stu-id="673ee-246">This service sends PPPoE frame using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="673ee-247">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="673ee-247">Input Parameters</span></span>

- <span data-ttu-id="673ee-248">**pppoe_server_ptr**: указатель на блок управления сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-248">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="673ee-249">**session_index**: индекс сеанса</span><span class="sxs-lookup"><span data-stu-id="673ee-249">**session_index**: The index of session.</span></span>
- <span data-ttu-id="673ee-250">**data_ptr**: указатель на начало кадра данных сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-250">**data_ptr**: Pointer to start of PPPoE Server data frame.</span></span>
- <span data-ttu-id="673ee-251">**data_length**: длина кадра данных сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-251">**data_length**: Length of PPPoE Server data frame.</span></span>

### <a name="return-values"></a><span data-ttu-id="673ee-252">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="673ee-252">Return Values</span></span>

- <span data-ttu-id="673ee-253">**NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное удаление сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-253">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="673ee-254">NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый указатель сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-254">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="673ee-255">NX_PPPOE_SERVER_NOT_ENABLED (0xC6) — служба сервера PPPoE не включена.</span><span class="sxs-lookup"><span data-stu-id="673ee-255">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="673ee-256">NX_PPPOE_SERVER_INVALID_SESSION (0xC7) — недопустимый индекс сеанса PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-256">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="673ee-257">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED (0xC8) — сеанс PPPoE не установлен.</span><span class="sxs-lookup"><span data-stu-id="673ee-257">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="673ee-258">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="673ee-258">Allowed From</span></span>

<span data-ttu-id="673ee-259">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="673ee-259">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="673ee-260">Например, .</span><span class="sxs-lookup"><span data-stu-id="673ee-260">Example</span></span>

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0, my_data_ptr, 1400);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" data has sent. */
```

## <a name="nx_pppoe_server_session_packet_send"></a><span data-ttu-id="673ee-261">nx_pppoe_server_session_packet_send</span><span class="sxs-lookup"><span data-stu-id="673ee-261">nx_pppoe_server_session_packet_send</span></span>

<span data-ttu-id="673ee-262">Отправка пакета сервера PPPoE в указанный сеанс</span><span class="sxs-lookup"><span data-stu-id="673ee-262">Send PPPoE Server packet to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="673ee-263">Прототип</span><span class="sxs-lookup"><span data-stu-id="673ee-263">Prototype</span></span>

```c
UINT nx_pppoe_server_session_packet_send (
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index, NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="673ee-264">Описание</span><span class="sxs-lookup"><span data-stu-id="673ee-264">Description</span></span>

<span data-ttu-id="673ee-265">Эта служба отправляет пакет PPPoE, используя указанный идентификатор сеанса.</span><span class="sxs-lookup"><span data-stu-id="673ee-265">This service sends PPPoE packet using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="673ee-266">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="673ee-266">Input Parameters</span></span>

- <span data-ttu-id="673ee-267">**pppoe_server_ptr**: указатель на блок управления сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-267">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="673ee-268">**session_index**: индекс сеанса</span><span class="sxs-lookup"><span data-stu-id="673ee-268">**session_index**: The index of session.</span></span>
- <span data-ttu-id="673ee-269">**packet_ptr**: указатель на пакет PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-269">**packet_ptr**: Pointer to PPPoE packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="673ee-270">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="673ee-270">Return Values</span></span>

- <span data-ttu-id="673ee-271">**NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное удаление сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-271">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="673ee-272">NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый указатель сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-272">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="673ee-273">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR (0xC3) — недопустимый пакет сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-273">NX_PPPOE_SERVER_PACKET_PAYLOAD_ERROR: (0xC3) Invalid PPPoE Server packet.</span></span>
- <span data-ttu-id="673ee-274">NX_PPPOE_SERVER_NOT_ENABLED (0xC6) — служба сервера PPPoE не включена.</span><span class="sxs-lookup"><span data-stu-id="673ee-274">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="673ee-275">NX_PPPOE_SERVER_INVALID_SESSION (0xC7) — недопустимый индекс сеанса PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-275">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="673ee-276">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED (0xC8) — сеанс PPPoE не установлен.</span><span class="sxs-lookup"><span data-stu-id="673ee-276">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="673ee-277">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="673ee-277">Allowed From</span></span>

<span data-ttu-id="673ee-278">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="673ee-278">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="673ee-279">Например, .</span><span class="sxs-lookup"><span data-stu-id="673ee-279">Example</span></span>

```c
/* Send PPPoE Server data to specified session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_packet_send(&my_pppoe_server, 0, packet_ptr);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the "my_pppoe_server" packet has sent. */
```

## <a name="nx_pppoe_server_session_terminate"></a><span data-ttu-id="673ee-280">nx_pppoe_server_session_terminate</span><span class="sxs-lookup"><span data-stu-id="673ee-280">nx_pppoe_server_session_terminate</span></span>

<span data-ttu-id="673ee-281">Завершение указанного сеанса PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-281">Terminate the specified PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="673ee-282">Прототип</span><span class="sxs-lookup"><span data-stu-id="673ee-282">Prototype</span></span>

```c
UINT nx_pppoe_server_session_terminate(
        NX_PPPOE_SERVER *pppoe_server_ptr,
        UINT session_index);
```

### <a name="description"></a><span data-ttu-id="673ee-283">Описание</span><span class="sxs-lookup"><span data-stu-id="673ee-283">Description</span></span>

<span data-ttu-id="673ee-284">Эта служба завершает указанный сеанс PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-284">This service terminates the specified PPPoE session.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="673ee-285">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="673ee-285">Input Parameters</span></span>

- <span data-ttu-id="673ee-286">**pppoe_server_ptr**: указатель на блок управления сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-286">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="673ee-287">**session_index**: индекс сеанса</span><span class="sxs-lookup"><span data-stu-id="673ee-287">**session_index**: The index of session.</span></span>

### <a name="return-values"></a><span data-ttu-id="673ee-288">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="673ee-288">Return Values</span></span>

- <span data-ttu-id="673ee-289">**NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное удаление сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-289">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="673ee-290">NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый указатель сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-290">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="673ee-291">NX_PPPOE_SERVER_NOT_ENABLED (0xC6) — служба сервера PPPoE не включена.</span><span class="sxs-lookup"><span data-stu-id="673ee-291">NX_PPPOE_SERVER_NOT_ENABLED: (0xC6) PPPoE Server service is not enabled.</span></span>
- <span data-ttu-id="673ee-292">NX_PPPOE_SERVER_INVALID_SESSION (0xC7) — недопустимый индекс сеанса PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-292">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="673ee-293">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED (0xC8) — сеанс PPPoE не установлен.</span><span class="sxs-lookup"><span data-stu-id="673ee-293">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="673ee-294">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="673ee-294">Allowed From</span></span>

<span data-ttu-id="673ee-295">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="673ee-295">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="673ee-296">Например, .</span><span class="sxs-lookup"><span data-stu-id="673ee-296">Example</span></span>

```c
/* Terminates the specified PPPoE session, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_send(&my_pppoe_server, 0);  

/* If status is NX_PPPOE_SERVER_SUCCESS, the session indexed with 0 has terminated. */
```

## <a name="nx_pppoe_server_session_get"></a><span data-ttu-id="673ee-297">nx_pppoe_server_session_get</span><span class="sxs-lookup"><span data-stu-id="673ee-297">nx_pppoe_server_session_get</span></span>

<span data-ttu-id="673ee-298">Получение сведений об указанном сеансе PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-298">Get the specified PPPoE session information</span></span>

### <a name="prototype"></a><span data-ttu-id="673ee-299">Прототип</span><span class="sxs-lookup"><span data-stu-id="673ee-299">Prototype</span></span>

```c
UINT nx_pppoe_server_session_get(NX_PPPOE_SERVER *pppoe_server_ptr,
                                UINT session_index
                                ULONG *client_mac_msw,
                                ULONG *client_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a><span data-ttu-id="673ee-300">Описание</span><span class="sxs-lookup"><span data-stu-id="673ee-300">Description</span></span>

<span data-ttu-id="673ee-301">Эта служба получает сведения об указанном сеансе PPPoE, физическом адресе клиента и идентификаторе сеанса.</span><span class="sxs-lookup"><span data-stu-id="673ee-301">This service gets the specified PPPoE session information, client physical address and session id.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="673ee-302">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="673ee-302">Input Parameters</span></span>

- <span data-ttu-id="673ee-303">**pppoe_server_ptr**: указатель на блок управления сервера PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-303">**pppoe_server_ptr**: Pointer to PPPoE Server control block.</span></span>
- <span data-ttu-id="673ee-304">**session_index**: индекс сеанса</span><span class="sxs-lookup"><span data-stu-id="673ee-304">**session_index**: The index of session.</span></span>
- <span data-ttu-id="673ee-305">**client_mac_msw**: указатель MSW на физический адрес клиента.</span><span class="sxs-lookup"><span data-stu-id="673ee-305">**client_mac_msw**: Client Physical address MSW pointer.</span></span>
- <span data-ttu-id="673ee-306">**client_mac_lsw**: указатель MSW на физический адрес клиента.</span><span class="sxs-lookup"><span data-stu-id="673ee-306">**client_mac_lsw**: Client Physical address MSW pointer.</span></span>
- <span data-ttu-id="673ee-307">**session_id**: указатель идентификатора сеанса.</span><span class="sxs-lookup"><span data-stu-id="673ee-307">**session_id**: Session ID pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="673ee-308">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="673ee-308">Return Values</span></span>

- <span data-ttu-id="673ee-309">**NX_PPPOE_SERVER_SUCCESS** (0x00) — успешное удаление сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-309">**NX_PPPOE_SERVER_SUCCESS**: (0x00) Successful PPPoE Server delete.</span></span>
- <span data-ttu-id="673ee-310">NX_PPPOE_SERVER_PTR_ERROR (0xC1) — недопустимый указатель сервера PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-310">NX_PPPOE_SERVER_PTR_ERROR: (0xC1) Invalid PPPoE Server pointer.</span></span>
- <span data-ttu-id="673ee-311">NX_PPPOE_SERVER_INVALID_SESSION (0xC7) — недопустимый индекс сеанса PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-311">NX_PPPOE_SERVER_INVALID_SESSION: (0xC7) Invalid PPPoE session index.</span></span>
- <span data-ttu-id="673ee-312">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED (0xC8) — сеанс PPPoE не установлен.</span><span class="sxs-lookup"><span data-stu-id="673ee-312">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED: (0xC8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="673ee-313">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="673ee-313">Allowed From</span></span>

<span data-ttu-id="673ee-314">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="673ee-314">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="673ee-315">Например, .</span><span class="sxs-lookup"><span data-stu-id="673ee-315">Example</span></span>

```c
/* Gets the specified PPPoE session information, PPPoE Server instance "my_pppoe_server". */
status = nx_pppoe_server_session_get (&my_pppoe_server, 0, &client_mac_msw, &client_mac_lsw, &session_id);

/* If status is NX_PPPOE_SERVER_SUCCESS, the client physical address and session id of the session indexed with 0 has got. */
```

## <a name="pppinitind"></a><span data-ttu-id="673ee-316">PppInitInd</span><span class="sxs-lookup"><span data-stu-id="673ee-316">PppInitInd</span></span>

<span data-ttu-id="673ee-317">Настройка имени службы по умолчанию</span><span class="sxs-lookup"><span data-stu-id="673ee-317">Configure the default Service Name</span></span>

### <a name="prototype"></a><span data-ttu-id="673ee-318">Прототип</span><span class="sxs-lookup"><span data-stu-id="673ee-318">Prototype</span></span>

```c
VOID PppInitnd(UINT length, UCHAR *aData);
```

### <a name="description"></a><span data-ttu-id="673ee-319">Описание</span><span class="sxs-lookup"><span data-stu-id="673ee-319">Description</span></span>

<span data-ttu-id="673ee-320">Программное обеспечение PPPoE предоставит эту функцию, чтобы разрешить программному обеспечению TTP настройку имени службы по умолчанию, которое PPPoE будет использовать для фильтрации входящих запросов PADI.</span><span class="sxs-lookup"><span data-stu-id="673ee-320">The PPPoE software will expose this function to allow TTP's software to configure the 'default Service Name' that the PPPoE should use to filter incoming PADI requests.</span></span> <span data-ttu-id="673ee-321">Программное обеспечение PPPoE должно запомнить эти сведения, и, если получен пакет PADI, содержащий имя службы, которое соответствует, оно должно вызывать PppDiscoverReq.</span><span class="sxs-lookup"><span data-stu-id="673ee-321">The PPPoE software should remember this information, and if a PADI packet is received containing a service name that matches then it should call PppDiscoverReq.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="673ee-322">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="673ee-322">Input Parameters</span></span>

- <span data-ttu-id="673ee-323">**length**: длина имени службы по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="673ee-323">**length**: Length of default service name.</span></span>
- <span data-ttu-id="673ee-324">**aData**: имя службы по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="673ee-324">**aData**: Default service name.</span></span>

### <a name="return-values"></a><span data-ttu-id="673ee-325">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="673ee-325">Return Values</span></span>

<span data-ttu-id="673ee-326">**Нет**</span><span class="sxs-lookup"><span data-stu-id="673ee-326">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="673ee-327">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="673ee-327">Allowed From</span></span>

<span data-ttu-id="673ee-328">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="673ee-328">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="673ee-329">Например, .</span><span class="sxs-lookup"><span data-stu-id="673ee-329">Example</span></span>

```c
/* Configure the default Service Name. */
PppInitInd (3, "XBB");
```

## <a name="pppdiscovercnf"></a><span data-ttu-id="673ee-330">PppDiscoverCnf</span><span class="sxs-lookup"><span data-stu-id="673ee-330">PppDiscoverCnf</span></span>

<span data-ttu-id="673ee-331">Определение поля имени службы пакета PADO</span><span class="sxs-lookup"><span data-stu-id="673ee-331">Define the Service Name field of the PADO packet</span></span>

### <a name="prototype"></a><span data-ttu-id="673ee-332">Прототип</span><span class="sxs-lookup"><span data-stu-id="673ee-332">Prototype</span></span>

```c
VOID PppDiscoverCnf (UINT length, UCHAR *aData, UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="673ee-333">Описание</span><span class="sxs-lookup"><span data-stu-id="673ee-333">Description</span></span>

<span data-ttu-id="673ee-334">Программное обеспечение PPPoE предоставит эту функцию, чтобы разрешить программному обеспечению TTP определять поле имени службы пакета PADO.</span><span class="sxs-lookup"><span data-stu-id="673ee-334">The PPPoE software will expose this function to allow TTP's software to define the Service Name field of the PADO packet.</span></span> <span data-ttu-id="673ee-335">Программное обеспечение PPPoE не должно отправлять PADO до вызова PppDiscoverCnf.</span><span class="sxs-lookup"><span data-stu-id="673ee-335">The PPPoE software should not send the PADO until the PppDiscoverCnf is called.</span></span>

<span data-ttu-id="673ee-336">Пакет PADO должен содержать имя концентратора доступа (с использованием идентификатора тега 0x0102, как определено в RFC2516), определенного для инициализации программного обеспечения PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-336">The PADO packet shall contain an access concentrator name (using the tag id 0x0102 as defined in RFC2516), defined on initialisation of the PPPoE software.</span></span>

<span data-ttu-id="673ee-337">В aData можно передать несколько имен служб, при этом в конце каждого имени должно быть указано NULL.</span><span class="sxs-lookup"><span data-stu-id="673ee-337">Multiple service names can be passed in aData, with each name to be null terminated.</span></span>

<span data-ttu-id="673ee-338">Символ NULL используется в качестве разделителя для обеспечения максимальной гибкости в случае, если другие команды необходимо передать в качестве части имени службы.</span><span class="sxs-lookup"><span data-stu-id="673ee-338">Null character is used as a separator to provide maximum flexibility in case other commands need to be passed in as part of the service name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="673ee-339">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="673ee-339">Input Parameters</span></span>

- <span data-ttu-id="673ee-340">**length**: длина имени службы по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="673ee-340">**length**: Length of default service name.</span></span>
- <span data-ttu-id="673ee-341">**aData**: имя службы по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="673ee-341">**aData**: Default service name.</span></span>
- <span data-ttu-id="673ee-342">**interfaceHandle**: дескриптор интерфейса.</span><span class="sxs-lookup"><span data-stu-id="673ee-342">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="673ee-343">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="673ee-343">Return Values</span></span>

<span data-ttu-id="673ee-344">**Нет**</span><span class="sxs-lookup"><span data-stu-id="673ee-344">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="673ee-345">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="673ee-345">Allowed From</span></span>

<span data-ttu-id="673ee-346">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="673ee-346">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="673ee-347">Например, .</span><span class="sxs-lookup"><span data-stu-id="673ee-347">Example</span></span>

```c
/* Define the Service Name field of the PADO packet. */
PppDiscoverCnf (3, "XBB", 0);
```

## <a name="pppopencnf"></a><span data-ttu-id="673ee-348">PppOpenCnf</span><span class="sxs-lookup"><span data-stu-id="673ee-348">PppOpenCnf</span></span>

<span data-ttu-id="673ee-349">Принятие или отклонение сеанса PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-349">Accept or reject the PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="673ee-350">Прототип</span><span class="sxs-lookup"><span data-stu-id="673ee-350">Prototype</span></span>

```c
VOID PppOpenCnf (UCHAR accept, UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="673ee-351">Описание</span><span class="sxs-lookup"><span data-stu-id="673ee-351">Description</span></span>

<span data-ttu-id="673ee-352">Программное обеспечение PPPoE предоставит эту функцию, чтобы разрешить программному обеспечению TTP принимать или отклонять сеансы PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-352">The PPPoE software will expose this function to allow TTP's software to accept or reject the PPPoE session.</span></span>  <span data-ttu-id="673ee-353">В ответ стек PPPoE должен принять подключение и назначить уникальный номер Session_ID PPPoE, связанный с interfaceHandle.</span><span class="sxs-lookup"><span data-stu-id="673ee-353">In response to this the PPPoE stack should accept the connection and assign a unique PPPoE Session_ID number associated with the interfaceHandle.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="673ee-354">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="673ee-354">Input Parameters</span></span>

- <span data-ttu-id="673ee-355">**accept**: NX_TRUE, если подключение должно быть принято.</span><span class="sxs-lookup"><span data-stu-id="673ee-355">**accept**: NX_TRUE if the connection is to be accepted.</span></span>
- <span data-ttu-id="673ee-356">**interfaceHandle**: дескриптор интерфейса.</span><span class="sxs-lookup"><span data-stu-id="673ee-356">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="673ee-357">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="673ee-357">Return Values</span></span>

<span data-ttu-id="673ee-358">**Нет**</span><span class="sxs-lookup"><span data-stu-id="673ee-358">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="673ee-359">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="673ee-359">Allowed From</span></span>

<span data-ttu-id="673ee-360">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="673ee-360">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="673ee-361">Например, .</span><span class="sxs-lookup"><span data-stu-id="673ee-361">Example</span></span>

```c
/* Accept the connection. */
PppOpenCnf(NX_TRUE, 0);
```

## <a name="pppcloseind"></a><span data-ttu-id="673ee-362">PppCloseInd</span><span class="sxs-lookup"><span data-stu-id="673ee-362">PppCloseInd</span></span>

<span data-ttu-id="673ee-363">Закрытие сеанса PPPoE</span><span class="sxs-lookup"><span data-stu-id="673ee-363">Close a PPPoE session</span></span>

### <a name="prototype"></a><span data-ttu-id="673ee-364">Прототип</span><span class="sxs-lookup"><span data-stu-id="673ee-364">Prototype</span></span>

```c
VOID PppCloseInd (UINT interfaceHandle, UCHAR *causeCode);
```

### <a name="description"></a><span data-ttu-id="673ee-365">Описание</span><span class="sxs-lookup"><span data-stu-id="673ee-365">Description</span></span>

<span data-ttu-id="673ee-366">Программное обеспечение PPPoE предоставит эту функцию, чтобы разрешить программному обеспечению TTP закрыть сеанс PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-366">The PPPoE software will expose this function to allow TTP's software to close a PPPoE session.</span></span>

<span data-ttu-id="673ee-367">Программное обеспечение PPPoE укажет строку кода причины в теге Generic-Error (0x0203) в сообщении PADT.</span><span class="sxs-lookup"><span data-stu-id="673ee-367">The PPPoE software will indicate the cause code string in the Generic-Error tag (0x0203) in the PADT message</span></span>

### <a name="input-parameters"></a><span data-ttu-id="673ee-368">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="673ee-368">Input Parameters</span></span>

- <span data-ttu-id="673ee-369">**interfaceHandle**: дескриптор интерфейса.</span><span class="sxs-lookup"><span data-stu-id="673ee-369">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="673ee-370">**causeCode**: строка, заканчивающаяся NULL, для отправки сведений о причине закрытия соединения с сервером PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-370">**causeCode**: Null terminated string for sending information about the reason for closing the connection from the PPPoE Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="673ee-371">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="673ee-371">Return Values</span></span>

<span data-ttu-id="673ee-372">**Нет**</span><span class="sxs-lookup"><span data-stu-id="673ee-372">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="673ee-373">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="673ee-373">Allowed From</span></span>

<span data-ttu-id="673ee-374">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="673ee-374">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="673ee-375">Например, .</span><span class="sxs-lookup"><span data-stu-id="673ee-375">Example</span></span>

```c
/* Close a PPPoE session. */
PppCloseInd(0, NX_NULL);
```

## <a name="pppclosecnf"></a><span data-ttu-id="673ee-376">PppCloseCnf</span><span class="sxs-lookup"><span data-stu-id="673ee-376">PppCloseCnf</span></span>

<span data-ttu-id="673ee-377">Подтверждение того, что дескриптор освобожден</span><span class="sxs-lookup"><span data-stu-id="673ee-377">Confirm that the handle has been freed</span></span>

### <a name="prototype"></a><span data-ttu-id="673ee-378">Прототип</span><span class="sxs-lookup"><span data-stu-id="673ee-378">Prototype</span></span>

```c
VOID PppCloseCnf (UINT interfaceHandle);
```

### <a name="description"></a><span data-ttu-id="673ee-379">Описание</span><span class="sxs-lookup"><span data-stu-id="673ee-379">Description</span></span>

<span data-ttu-id="673ee-380">Программное обеспечение PPPoE предоставит эту функцию, чтобы разрешить программному обеспечению TTP подтверждение того, что этот дескриптор был освобожден.</span><span class="sxs-lookup"><span data-stu-id="673ee-380">The PPPoE software will expose this function to allow TTP's software to confirm that the handle has been freed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="673ee-381">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="673ee-381">Input Parameters</span></span>

- <span data-ttu-id="673ee-382">**interfaceHandle**: дескриптор интерфейса.</span><span class="sxs-lookup"><span data-stu-id="673ee-382">**interfaceHandle**: Interface handle.</span></span>

### <a name="return-values"></a><span data-ttu-id="673ee-383">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="673ee-383">Return Values</span></span>

<span data-ttu-id="673ee-384">**Нет**</span><span class="sxs-lookup"><span data-stu-id="673ee-384">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="673ee-385">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="673ee-385">Allowed From</span></span>

<span data-ttu-id="673ee-386">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="673ee-386">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="673ee-387">Например, .</span><span class="sxs-lookup"><span data-stu-id="673ee-387">Example</span></span>

```c
/* Confirm that the handle has been freed. */
PppCloseCnf(0);
```

## <a name="ppptransmitdatacnf"></a><span data-ttu-id="673ee-388">PppTransmitDataCnf</span><span class="sxs-lookup"><span data-stu-id="673ee-388">PppTransmitDataCnf</span></span>

<span data-ttu-id="673ee-389">Разрешение подтверждения предыдущих данных PPP</span><span class="sxs-lookup"><span data-stu-id="673ee-389">Allow a preceding PPP data to be acknowledged</span></span>

### <a name="prototype"></a><span data-ttu-id="673ee-390">Прототип</span><span class="sxs-lookup"><span data-stu-id="673ee-390">Prototype</span></span>

```c
VOID PppTransmitDataCnf (UINT interfaceHandle, UCHAR *aData,
                        UINT packet_id);
```

### <a name="description"></a><span data-ttu-id="673ee-391">Описание</span><span class="sxs-lookup"><span data-stu-id="673ee-391">Description</span></span>

<span data-ttu-id="673ee-392">Программное обеспечение PPPoE предоставит эту функцию, чтобы разрешить подтверждение предыдущего PppTransmitDataReq.</span><span class="sxs-lookup"><span data-stu-id="673ee-392">The PPPoE software will expose this function to allow a preceding PppTransmitDataReq to be acknowledged.</span></span>  <span data-ttu-id="673ee-393">Это означает, что программное обеспечение TTP готово к созданию нового кадра PPP из PPPoE.</span><span class="sxs-lookup"><span data-stu-id="673ee-393">It implies that TTP's software is ready for a new PPP frame from PPPoE.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="673ee-394">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="673ee-394">Input Parameters</span></span>

- <span data-ttu-id="673ee-395">**interfaceHandle**: дескриптор интерфейса.</span><span class="sxs-lookup"><span data-stu-id="673ee-395">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="673ee-396">**aData**: указатель принятия буфера данных PPP.</span><span class="sxs-lookup"><span data-stu-id="673ee-396">**aData**: Pointer the PPP data buffer that has been accepted.</span></span>
- <span data-ttu-id="673ee-397">**Packet_id**: идентификатор пакета.</span><span class="sxs-lookup"><span data-stu-id="673ee-397">**Packet_id**: Packet identifier.</span></span>

### <a name="return-values"></a><span data-ttu-id="673ee-398">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="673ee-398">Return Values</span></span>

<span data-ttu-id="673ee-399">**Нет**</span><span class="sxs-lookup"><span data-stu-id="673ee-399">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="673ee-400">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="673ee-400">Allowed From</span></span>

<span data-ttu-id="673ee-401">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="673ee-401">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="673ee-402">Например, .</span><span class="sxs-lookup"><span data-stu-id="673ee-402">Example</span></span>

```c
UINT packet_id = 0x20015429

/* Allow a preceding PPP data to be acknowledged, let PPPoE Server release the packet with same packet identifier. */
PppTransmitDataCnf(0, NX_NULL, packet_id);
```

## <a name="pppreceivedataind"></a><span data-ttu-id="673ee-403">PppReceiveDataInd</span><span class="sxs-lookup"><span data-stu-id="673ee-403">PppReceiveDataInd</span></span>

<span data-ttu-id="673ee-404">Получение данных из передачи по Ethernet</span><span class="sxs-lookup"><span data-stu-id="673ee-404">Receive data from transmission over Ethernet</span></span>

### <a name="prototype"></a><span data-ttu-id="673ee-405">Прототип</span><span class="sxs-lookup"><span data-stu-id="673ee-405">Prototype</span></span>

```c
VOID PppReceiveDataInd(UINT interfaceHandle, UINT length, UCHAR *aData);
```

### <a name="description"></a><span data-ttu-id="673ee-406">Описание</span><span class="sxs-lookup"><span data-stu-id="673ee-406">Description</span></span>

<span data-ttu-id="673ee-407">Программное обеспечение PPPoE предоставит эту функцию для получения данных для передачи по Ethernet.</span><span class="sxs-lookup"><span data-stu-id="673ee-407">The PPPoE software will expose this function to receive data for transmission over Ethernet</span></span>

### <a name="input-parameters"></a><span data-ttu-id="673ee-408">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="673ee-408">Input Parameters</span></span>

- <span data-ttu-id="673ee-409">**interfaceHandle**: дескриптор интерфейса.</span><span class="sxs-lookup"><span data-stu-id="673ee-409">**interfaceHandle**: Interface handle.</span></span>
- <span data-ttu-id="673ee-410">**length**: число байтов в aData.</span><span class="sxs-lookup"><span data-stu-id="673ee-410">**length**: The number of bytes in aData.</span></span>
- <span data-ttu-id="673ee-411">**aData**: буфер данных, содержащий кадр данных PPP.</span><span class="sxs-lookup"><span data-stu-id="673ee-411">**aData**: Data buffer containing the frame of PPP data.</span></span>

### <a name="return-values"></a><span data-ttu-id="673ee-412">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="673ee-412">Return Values</span></span>

<span data-ttu-id="673ee-413">**Нет**</span><span class="sxs-lookup"><span data-stu-id="673ee-413">**None**</span></span>

### <a name="allowed-from"></a><span data-ttu-id="673ee-414">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="673ee-414">Allowed From</span></span>

<span data-ttu-id="673ee-415">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="673ee-415">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="673ee-416">Пример</span><span class="sxs-lookup"><span data-stu-id="673ee-416">Example</span></span>

```c
/* Receive data from transmission over Ethernet, data start pointer is aData.
The number of bytes in aData is 1480. */
PppReceiveDataInd (0, 1480, aData);
```