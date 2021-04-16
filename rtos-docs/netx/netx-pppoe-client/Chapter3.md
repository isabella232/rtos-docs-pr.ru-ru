---
title: Глава 3. Описание служб клиента PPPoE для NetX (ОСРВ Azure)
description: В этой главе описываются все службы клиента PPPoE для NetX (ОСРВ Azure), которые перечислены ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 07/13/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 246115fc97d7597246f7fd5b4fb88cb615baab33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814447"
---
# <a name="chapter-3---description-of-azure-rtos-netx-pppoe-client-services"></a><span data-ttu-id="809fd-103">Глава 3. Описание служб клиента PPPoE для NetX (ОСРВ Azure)</span><span class="sxs-lookup"><span data-stu-id="809fd-103">Chapter 3 - Description of Azure RTOS NetX PPPoE Client Services</span></span>

<span data-ttu-id="809fd-104">В этой главе описываются все службы клиента PPPoE для NetX (ОСРВ Azure), которые перечислены ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="809fd-104">This chapter contains a description of all Azure RTOS NetX PPPoE Client services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="809fd-105">В разделе "Возвращаемые значения" приведенных ниже описаний API **выделенные полужирным шрифтом** значения не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="809fd-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="809fd-106">**nx_pppoe_client_create** — *создание экземпляра клиента PPPoE*.</span><span class="sxs-lookup"><span data-stu-id="809fd-106">**nx_pppoe_client_create** *Create a PPPoE Client instance*</span></span>
- <span data-ttu-id="809fd-107">**nx_pppoe_client_delete** — *удаление экземпляра клиента PPPoE*.</span><span class="sxs-lookup"><span data-stu-id="809fd-107">**nx_pppoe_client_delete** *Delete a PPPoE Client instance*</span></span>
- <span data-ttu-id="809fd-108">**nx_pppoe_client_host_uniq_set** — *настройка значения Host-Uniq для клиента PPPoE*.</span><span class="sxs-lookup"><span data-stu-id="809fd-108">**nx_pppoe_client_host_uniq_set** *Set the host unique for PPPoE Client*</span></span>
- <span data-ttu-id="809fd-109">**nx_pppoe_client_host_uniq_set_extended** *Настройка значения Host-Uniq для клиента PPPoE*.</span><span class="sxs-lookup"><span data-stu-id="809fd-109">**nx_pppoe_client_host_uniq_set_extended** *Set the host unique for PPPoE Client*</span></span>
- <span data-ttu-id="809fd-110">**nx_pppoe_client_service_name_set** — *настройка имени службы для клиента PPPoE*</span><span class="sxs-lookup"><span data-stu-id="809fd-110">**nx_pppoe_client_service_name_set** *Set the service name for PPPoE Client*</span></span>
- <span data-ttu-id="809fd-111">**nx_pppoe_client_service_name_set_extended** — *настройка имени службы для клиента PPPoE*.</span><span class="sxs-lookup"><span data-stu-id="809fd-111">**nx_pppoe_client_service_name_set_extended** *Set the service name for PPPoE Client*</span></span>
- <span data-ttu-id="809fd-112">**nx_pppoe_client_session_connect** — *подключение сеанса клиента PPPoE к серверу PPPoE*.</span><span class="sxs-lookup"><span data-stu-id="809fd-112">**nx_pppoe_client_session_connect** *Connect PPPoE Client session to PPPoE Server*</span></span>
- <span data-ttu-id="809fd-113">**nx_pppoe_client_session_packet_send** — *отправка пакета в сеанс PPPoE*.</span><span class="sxs-lookup"><span data-stu-id="809fd-113">**nx_pppoe_client_session_packet_send** *Send PPPoE session packet*</span></span>
- <span data-ttu-id="809fd-114">**nx_pppoe_client_session_terminate** — *завершение сеанса PPPoE*.</span><span class="sxs-lookup"><span data-stu-id="809fd-114">**nx_pppoe_client_session_terminate** *Terminate the PPPoE session*</span></span>
- <span data-ttu-id="809fd-115">**nx_pppoe_client_session_get** — *получение сведений об указанном сеансе PPPoE*.</span><span class="sxs-lookup"><span data-stu-id="809fd-115">**nx_pppoe_client_session_get** *Get the specified PPPoE session inf*</span></span>

## <a name="nx_pppoe_client_create"></a><span data-ttu-id="809fd-116">nx_pppoe_client_create</span><span class="sxs-lookup"><span data-stu-id="809fd-116">nx_pppoe_client_create</span></span>

<span data-ttu-id="809fd-117">Создание экземпляра клиента PPPoE</span><span class="sxs-lookup"><span data-stu-id="809fd-117">Create a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="809fd-118">Прототип</span><span class="sxs-lookup"><span data-stu-id="809fd-118">Prototype</span></span>

```c
UINT  nx_pppoe_client_create(NX_PPPOE_CLIENT *pppoe_client_ptr,
                            CHAR *name, NX_IP *ip_ptr,
                            UINT interface_index,
                            NX_PACKET_POOL *pool_ptr,
                            VOID *stack_ptr, ULONG stack_size,
                            UINT priority,
                            VOID (*pppoe_link_driver)
                            (struct NX_IP_DRIVER_STRUCT *)
                            VOID (*pppoe_packet_receive)
                            (NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="809fd-119">Описание</span><span class="sxs-lookup"><span data-stu-id="809fd-119">Description</span></span>

<span data-ttu-id="809fd-120">Эта служба создает экземпляр клиента PPPoE с драйвером канала, предоставленным пользователем для указанного экземпляра NetX IP.</span><span class="sxs-lookup"><span data-stu-id="809fd-120">This service creates a PPPoE Client instance with the user supplied link driver for the specified NetX IP instance.</span></span> <span data-ttu-id="809fd-121">Если драйвер канала не был инициализирован и включен, программное обеспечение клиента PPPoE выполняет инициализацию драйвера канала.</span><span class="sxs-lookup"><span data-stu-id="809fd-121">If link driver has not been initialized, and enabled, PPPoE Client software is responsible initializing the link driver.</span></span>

<span data-ttu-id="809fd-122">Кроме того, приложение должно предоставить созданный ранее пул пакетов для экземпляра клиента PPPoE, который будет использоваться для внутреннего распределения пакетов.</span><span class="sxs-lookup"><span data-stu-id="809fd-122">In addition, the application must supply a previously created packet pool for the PPPoE Client instance to use for internal packet allocation.</span></span>

> [!NOTE]
> <span data-ttu-id="809fd-123">Обычно считается, что поток NetX IP следует создавать с более высоким приоритетом, чем у потока клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-123">Generally a good idea to create the NetX IP thread at a higher priority than the PPPoE Client thread priority.</span></span> <span data-ttu-id="809fd-124">Дополнительные сведения об указании приоритета для потока IP см. в описании службы *nx_ip_create*.</span><span class="sxs-lookup"><span data-stu-id="809fd-124">Please refer to the *nx_ip_create* service for more information on specifying the IP thread priority.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="809fd-125">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="809fd-125">Input Parameters</span></span>

 - <span data-ttu-id="809fd-126">**pppoe_client_ptr** — указатель на блок управления для клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-126">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="809fd-127">**name** — имя текущего экземпляра клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-127">**name** Name of this PPPoE Client instance.</span></span>
 - <span data-ttu-id="809fd-128">**ip_ptr** — указатель на блок управления для экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="809fd-128">**ip_ptr** Pointer to control block for IP instance.</span></span>
 - <span data-ttu-id="809fd-129">**interface_index** — индекс интерфейса.</span><span class="sxs-lookup"><span data-stu-id="809fd-129">**interface_index** Interface index.</span></span>
 - <span data-ttu-id="809fd-130">**pool_ptr** — указатель на пул пакетов.</span><span class="sxs-lookup"><span data-stu-id="809fd-130">**pool_ptr** Pointer to packet pool.</span></span>
 - <span data-ttu-id="809fd-131">**stack_ptr** — указатель на начало области стека потока клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-131">**stack_ptr** Pointer to start of PPPoE Client thread’s stack area.</span></span>
 - <span data-ttu-id="809fd-132">**stack_size** — размер в байтах в стеке потока.</span><span class="sxs-lookup"><span data-stu-id="809fd-132">**stack_size** Size in bytes in the thread’s stack.</span></span>
 - <span data-ttu-id="809fd-133">**priority** — приоритет внутренних потоков клиента PPPoE (1–31).</span><span class="sxs-lookup"><span data-stu-id="809fd-133">**priority** Priority of internal PPPoE Client threads (1-31).</span></span>
 - <span data-ttu-id="809fd-134">**pppoe_link_driver** — драйвер канала, предоставленный пользователем.</span><span class="sxs-lookup"><span data-stu-id="809fd-134">**pppoe_link_driver** User supplied link driver.</span></span>
 - <span data-ttu-id="809fd-135">**pppoe_packet_receive** — предоставленная пользователем функция приема пакетов.</span><span class="sxs-lookup"><span data-stu-id="809fd-135">**pppoe_packet_receive** User supplied packet receive function.</span></span>

### <a name="return-values"></a><span data-ttu-id="809fd-136">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="809fd-136">Return Values</span></span>

 - <span data-ttu-id="809fd-137">**NX_PPPOE_CLIENT_SUCCESS** (0x00) — клиент PPPoE успешно создан.</span><span class="sxs-lookup"><span data-stu-id="809fd-137">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client create.</span></span>
 - <span data-ttu-id="809fd-138">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) — недопустимый клиент PPPoE, IP, пул пакетов или указатель стека.</span><span class="sxs-lookup"><span data-stu-id="809fd-138">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client, IP, packet pool, or stack pointer.</span></span>
 - <span data-ttu-id="809fd-139">NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) — недопустимый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="809fd-139">NX_PPPOE_CLIENT_INVALID_INTERFACE (0xD2) Invalid interface.</span></span>
 - <span data-ttu-id="809fd-140">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) — недопустимый объем полезных данных пула пакетов.</span><span class="sxs-lookup"><span data-stu-id="809fd-140">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Invalid payload size of packet pool.</span></span>
 - <span data-ttu-id="809fd-141">NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) — недопустимый объем памяти.</span><span class="sxs-lookup"><span data-stu-id="809fd-141">NX_PPPOE_CLIENT_MEMORY_SIZE_ERROR (0xD4) Invalid memory size.</span></span>
 - <span data-ttu-id="809fd-142">NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) — недопустимый приоритет потока клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-142">NX_PPPOE_CLIENT_PRIORITY_ERROR (0xD5) Invalid priority of PPPoE Client thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="809fd-143">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="809fd-143">Allowed From</span></span>

<span data-ttu-id="809fd-144">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="809fd-144">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="809fd-145">Например, .</span><span class="sxs-lookup"><span data-stu-id="809fd-145">Example</span></span>

```c
/* Create “my_pppoe_client” for IP instance “my_ip”. */
status =  nx_pppoe_client_create(&my_pppoe_client, “my PPPoE Client”, &my_ip,
0, &my_pool, stack_start, 1024, 2,
link_driver, packet_receive);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully created. */
```

## <a name="nx_pppoe_client_delete"></a><span data-ttu-id="809fd-146">nx_pppoe_client_delete</span><span class="sxs-lookup"><span data-stu-id="809fd-146">nx_pppoe_client_delete</span></span>

<span data-ttu-id="809fd-147">Удаление экземпляра клиента PPPoE</span><span class="sxs-lookup"><span data-stu-id="809fd-147">Delete a PPPoE Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="809fd-148">Прототип</span><span class="sxs-lookup"><span data-stu-id="809fd-148">Prototype</span></span>

```c
UINT nx_pppoe_client_delete(NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a><span data-ttu-id="809fd-149">Описание</span><span class="sxs-lookup"><span data-stu-id="809fd-149">Description</span></span>

<span data-ttu-id="809fd-150">Эта служба удаляет созданный ранее экземпляр клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-150">This service deletes the previously created PPPoE Client instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="809fd-151">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="809fd-151">Input Parameters</span></span>

 - <span data-ttu-id="809fd-152">**pppoe_client_ptr** — указатель на блок управления для клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-152">**pppoe_client_ptr** Pointer to PPPoE Client control block</span></span>

### <a name="return-values"></a><span data-ttu-id="809fd-153">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="809fd-153">Return Values</span></span>

 - <span data-ttu-id="809fd-154">**NX_PPPOE_CLIENT_SUCCESS** (0x00) — клиент PPPoE успешно удален.</span><span class="sxs-lookup"><span data-stu-id="809fd-154">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client delete.</span></span>
 - <span data-ttu-id="809fd-155">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) — недопустимый указатель на клиент PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-155">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="809fd-156">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="809fd-156">Allowed From</span></span>

<span data-ttu-id="809fd-157">Потоки</span><span class="sxs-lookup"><span data-stu-id="809fd-157">Threads</span></span>

### <a name="example"></a><span data-ttu-id="809fd-158">Например, .</span><span class="sxs-lookup"><span data-stu-id="809fd-158">Example</span></span>

```c
/* Delete PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_delete(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” was successfully deleted. */
```

## <a name="nx_pppoe_client_host_uniq_set"></a><span data-ttu-id="809fd-159">nx_pppoe_client_host_uniq_set</span><span class="sxs-lookup"><span data-stu-id="809fd-159">nx_pppoe_client_host_uniq_set</span></span>

<span data-ttu-id="809fd-160">Настройка значения Host-Uniq для клиента PPPoE</span><span class="sxs-lookup"><span data-stu-id="809fd-160">Set PPPoE Client host unique</span></span>

### <a name="prototype"></a><span data-ttu-id="809fd-161">Прототип</span><span class="sxs-lookup"><span data-stu-id="809fd-161">Prototype</span></span>

```c
UINT nx_pppoe_client_host_uniq_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq);
```

### <a name="description"></a><span data-ttu-id="809fd-162">Описание</span><span class="sxs-lookup"><span data-stu-id="809fd-162">Description</span></span>

<span data-ttu-id="809fd-163">Эта служба задает значение Host-Uniq для клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-163">This service sets PPPoE Client host unique.</span></span> <span data-ttu-id="809fd-164">Host-Uniq используется узлом для уникальной привязки концентратора доступа к определенному запросу узла.</span><span class="sxs-lookup"><span data-stu-id="809fd-164">Host-Uniq is used by a host to uniquely associate an Access Concentrator to a particular Host request.</span></span>
<span data-ttu-id="809fd-165">Это могут быть двоичные данные с любыми значениями и любой длины, которые выбирает узел.</span><span class="sxs-lookup"><span data-stu-id="809fd-165">It can be binary data of any value and length that the Host chooses.</span></span>

> [!NOTE]
> <span data-ttu-id="809fd-166">Значение Host-Uniq должно быть строковым и заканчиваться нулем.</span><span class="sxs-lookup"><span data-stu-id="809fd-166">host unique must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="809fd-167">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="809fd-167">This service is deprecated.</span></span> <span data-ttu-id="809fd-168">Мы рекомендуем разработчикам перейти на использование *nx_pppoe_client_host_uniq_set_extended()* .</span><span class="sxs-lookup"><span data-stu-id="809fd-168">Developers are encouraged to migrate to *nx_pppoe_client_host_uniq_set_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="809fd-169">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="809fd-169">Input Parameters</span></span>

 - <span data-ttu-id="809fd-170">**pppoe_client_ptr** — указатель на блок управления для клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-170">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="809fd-171">**host_uniq** — указатель на значение Host-Uniq.</span><span class="sxs-lookup"><span data-stu-id="809fd-171">**host_uniq** Pointer to an host unique.</span></span> <span data-ttu-id="809fd-172">Значение Host-Uniq должно быть строковым и заканчиваться нулем.</span><span class="sxs-lookup"><span data-stu-id="809fd-172">Host unique must be Null-terminated string.</span></span>

### <a name="return-values"></a><span data-ttu-id="809fd-173">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="809fd-173">Return Values</span></span>

 - <span data-ttu-id="809fd-174">**NX_PPPOE_CLIENT_SUCCESS** (0x00) — значение Host-Uniq для клиента PPPoE успешно установлено.</span><span class="sxs-lookup"><span data-stu-id="809fd-174">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client host unique set.</span></span>
 - <span data-ttu-id="809fd-175">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) — недопустимый указатель на клиент PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-175">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="809fd-176">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="809fd-176">Allowed From</span></span>

<span data-ttu-id="809fd-177">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="809fd-177">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="809fd-178">Например, .</span><span class="sxs-lookup"><span data-stu-id="809fd-178">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set(&my_pppoe_client,
“220000000000000041000000”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_host_uniq_set_extended"></a><span data-ttu-id="809fd-179">nx_pppoe_client_host_uniq_set_extended</span><span class="sxs-lookup"><span data-stu-id="809fd-179">nx_pppoe_client_host_uniq_set_extended</span></span>

<span data-ttu-id="809fd-180">Настройка значения Host-Uniq для клиента PPPoE</span><span class="sxs-lookup"><span data-stu-id="809fd-180">Set PPPoE Client host unique</span></span>

### <a name="prototype"></a><span data-ttu-id="809fd-181">Прототип</span><span class="sxs-lookup"><span data-stu-id="809fd-181">Prototype</span></span>

```c
UINT nx_pppoe_client_host_uniq_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *host_uniq,UINT host_uniq_length);
```

### <a name="description"></a><span data-ttu-id="809fd-182">Описание</span><span class="sxs-lookup"><span data-stu-id="809fd-182">Description</span></span>

<span data-ttu-id="809fd-183">Эта служба задает значение Host-Uniq для клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-183">This service sets PPPoE Client host unique.</span></span> <span data-ttu-id="809fd-184">Host-Uniq используется узлом для уникальной привязки концентратора доступа к определенному запросу узла.</span><span class="sxs-lookup"><span data-stu-id="809fd-184">Host-Uniq is used by a host to uniquely associate an Access Concentrator to a particular Host request.</span></span>
<span data-ttu-id="809fd-185">Это могут быть двоичные данные с любыми значениями и любой длины, которые выбирает узел.</span><span class="sxs-lookup"><span data-stu-id="809fd-185">It can be binary data of any value and length that the Host chooses.</span></span>

> [!NOTE]
> <span data-ttu-id="809fd-186">Значение Host-Uniq должно быть строковым и заканчиваться нулем.</span><span class="sxs-lookup"><span data-stu-id="809fd-186">host unique must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="809fd-187">Эта служба заменяет устаревшую *nx_pppoe_client_host_uniq_set()* .</span><span class="sxs-lookup"><span data-stu-id="809fd-187">This service replaces *nx_pppoe_client_host_uniq_set()*.</span></span> <span data-ttu-id="809fd-188">Эта версия предоставляет службе дополнительные сведения о длине.</span><span class="sxs-lookup"><span data-stu-id="809fd-188">This version supplies additional length information to the service.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="809fd-189">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="809fd-189">Input Parameters</span></span>

 - <span data-ttu-id="809fd-190">**pppoe_client_ptr** — указатель на блок управления для клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-190">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="809fd-191">**host_uniq** — указатель на значение Host-Uniq.</span><span class="sxs-lookup"><span data-stu-id="809fd-191">**host_uniq** Pointer to an host unique.</span></span> <span data-ttu-id="809fd-192">Значение Host-Uniq должно быть строковым и заканчиваться нулем.</span><span class="sxs-lookup"><span data-stu-id="809fd-192">Host unique must be Null-terminated string.</span></span>
 - <span data-ttu-id="809fd-193">**host_uniq_length** — длина значения Host-Uniq</span><span class="sxs-lookup"><span data-stu-id="809fd-193">**host_uniq_length** Length of host_uniq</span></span>

### <a name="return-values"></a><span data-ttu-id="809fd-194">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="809fd-194">Return Values</span></span>

 - <span data-ttu-id="809fd-195">**NX_PPPOE_CLIENT_SUCCESS** (0x00) — значение Host-Uniq для клиента PPPoE успешно установлено.</span><span class="sxs-lookup"><span data-stu-id="809fd-195">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client host unique set.</span></span>
 - <span data-ttu-id="809fd-196">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) — недопустимый указатель на клиент PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-196">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="809fd-197">**NX_SIZE_ERROR** (0x09) — проверка host_uniq_length не прошла.</span><span class="sxs-lookup"><span data-stu-id="809fd-197">**NX_SIZE_ERROR** (0x09) Check host_uniq_length fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="809fd-198">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="809fd-198">Allowed From</span></span>

<span data-ttu-id="809fd-199">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="809fd-199">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="809fd-200">Например, .</span><span class="sxs-lookup"><span data-stu-id="809fd-200">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_host_uniq_set_extended(&my_pppoe_client,
“220000000000000041000000”,24);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” host unique has set. */
```

## <a name="nx_pppoe_client_service_name_set"></a><span data-ttu-id="809fd-201">nx_pppoe_client_service_name_set</span><span class="sxs-lookup"><span data-stu-id="809fd-201">nx_pppoe_client_service_name_set</span></span>

<span data-ttu-id="809fd-202">Настройка имени службы клиента PPPoE</span><span class="sxs-lookup"><span data-stu-id="809fd-202">Set PPPoE Client service name</span></span>

### <a name="prototype"></a><span data-ttu-id="809fd-203">Прототип</span><span class="sxs-lookup"><span data-stu-id="809fd-203">Prototype</span></span>

```c
UINT nx_pppoe_client_service_name_set(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name);
```

### <a name="description"></a><span data-ttu-id="809fd-204">Описание</span><span class="sxs-lookup"><span data-stu-id="809fd-204">Description</span></span>

<span data-ttu-id="809fd-205">Эта служба задает имя службы клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-205">This service sets PPPoE Client service name.</span></span> <span data-ttu-id="809fd-206">Значение Service-Name обозначает службу, которую запрашивает узел.</span><span class="sxs-lookup"><span data-stu-id="809fd-206">The Service-Name indicating the service the Host is requesting.</span></span> <span data-ttu-id="809fd-207">Если значение Service-Name не задано, узел примет любое количество служб.</span><span class="sxs-lookup"><span data-stu-id="809fd-207">If Service-Name is not set, indicating Host will accept any number of services.</span></span>

> [!NOTE]
> <span data-ttu-id="809fd-208">Имя службы должно быть строковым и заканчиваться нулем.</span><span class="sxs-lookup"><span data-stu-id="809fd-208">service name must be Null-terminated string</span></span>

> [!NOTE]
> <span data-ttu-id="809fd-209">использовать эту службу больше не рекомендуется.</span><span class="sxs-lookup"><span data-stu-id="809fd-209">This service is deprecated.</span></span> <span data-ttu-id="809fd-210">Мы рекомендуем разработчикам перейти на использование *nx_pppoe_client_service_name_set_extended()* .</span><span class="sxs-lookup"><span data-stu-id="809fd-210">Developers are encouraged to migrate to *nx_pppoe_client_service_name_set_extended()*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="809fd-211">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="809fd-211">Input Parameters</span></span>

 - <span data-ttu-id="809fd-212">**pppoe_client_ptr** — указатель на блок управления для клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-212">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="809fd-213">**service_name** — указатель на имя службы.</span><span class="sxs-lookup"><span data-stu-id="809fd-213">**service_name** Pointer to an service name.</span></span> <span data-ttu-id="809fd-214">Имя службы должно быть строковым и заканчиваться нулем.</span><span class="sxs-lookup"><span data-stu-id="809fd-214">Service name must be Null-terminated string.</span></span>

### <a name="return-values"></a><span data-ttu-id="809fd-215">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="809fd-215">Return Values</span></span>

 - <span data-ttu-id="809fd-216">**NX_PPPOE_CLIENT_SUCCESS** (0x00) — имя службы для клиента PPPoE успешно задано.</span><span class="sxs-lookup"><span data-stu-id="809fd-216">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client service name set.</span></span>
 - <span data-ttu-id="809fd-217">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) — недопустимый указатель на клиент PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-217">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="809fd-218">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="809fd-218">Allowed From</span></span>

<span data-ttu-id="809fd-219">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="809fd-219">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="809fd-220">Например, .</span><span class="sxs-lookup"><span data-stu-id="809fd-220">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set(&my_pppoe_client,
“BRAS”);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_service_name_set_extended"></a><span data-ttu-id="809fd-221">nx_pppoe_client_service_name_set_extended</span><span class="sxs-lookup"><span data-stu-id="809fd-221">nx_pppoe_client_service_name_set_extended</span></span>

<span data-ttu-id="809fd-222">Настройка имени службы клиента PPPoE</span><span class="sxs-lookup"><span data-stu-id="809fd-222">Set PPPoE Client service name</span></span>

### <a name="prototype"></a><span data-ttu-id="809fd-223">Прототип</span><span class="sxs-lookup"><span data-stu-id="809fd-223">Prototype</span></span>

```c
UINT nx_pppoe_client_service_name_set_extended(
                        NX_PPPOE_CLIENT *pppoe_client_ptr,
                        UCHAR *service_name,UINT service_name_length);
```

### <a name="description"></a><span data-ttu-id="809fd-224">Описание</span><span class="sxs-lookup"><span data-stu-id="809fd-224">Description</span></span>

<span data-ttu-id="809fd-225">Эта служба задает имя службы клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-225">This service sets PPPoE Client service name.</span></span> <span data-ttu-id="809fd-226">Значение Service-Name обозначает службу, которую запрашивает узел.</span><span class="sxs-lookup"><span data-stu-id="809fd-226">The Service-Name indicating the service the Host is requesting.</span></span> <span data-ttu-id="809fd-227">Если значение Service-Name не задано, узел примет любое количество служб.</span><span class="sxs-lookup"><span data-stu-id="809fd-227">If Service-Name is not set, indicating Host will accept any number of services.</span></span>

> [!NOTE]
> <span data-ttu-id="809fd-228">Имя службы должно быть строковым и завершаться заканчиваться нулем.</span><span class="sxs-lookup"><span data-stu-id="809fd-228">service name must be Null-terminated string.</span></span>

> [!NOTE]
> <span data-ttu-id="809fd-229">Эта служба заменяет *nx_pppoe_client_service_name_set()* .</span><span class="sxs-lookup"><span data-stu-id="809fd-229">This service replaces *nx_pppoe_client_service_name_set()*.</span></span> <span data-ttu-id="809fd-230">Эта версия предоставляет функции дополнительные сведения о длине имени службы.</span><span class="sxs-lookup"><span data-stu-id="809fd-230">This version supplies additional service name length information to the function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="809fd-231">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="809fd-231">Input Parameters</span></span>

 - <span data-ttu-id="809fd-232">**pppoe_client_ptr** — указатель на блок управления для клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-232">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="809fd-233">**service_name** — указатель на имя службы.</span><span class="sxs-lookup"><span data-stu-id="809fd-233">**service_name** Pointer to an service name.</span></span> <span data-ttu-id="809fd-234">Имя службы должно быть строковым и заканчиваться нулем.</span><span class="sxs-lookup"><span data-stu-id="809fd-234">Service name must be Null-terminated string.</span></span>
 - <span data-ttu-id="809fd-235">**service_name_length** — длина имени службы.</span><span class="sxs-lookup"><span data-stu-id="809fd-235">**service_name_length** Length of service_name</span></span>

### <a name="return-values"></a><span data-ttu-id="809fd-236">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="809fd-236">Return Values</span></span>

 - <span data-ttu-id="809fd-237">**NX_PPPOE_CLIENT_SUCCESS** (0x00) — имя службы для клиента PPPoE успешно задано.</span><span class="sxs-lookup"><span data-stu-id="809fd-237">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client service name set.</span></span>
 - <span data-ttu-id="809fd-238">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) — недопустимый указатель на клиент PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-238">**NX_PPPOE_CLIENT_PTR_ERROR** (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="809fd-239">**NX_SIZE_ERROR** (0x09) — проверка service_name_length не пройдена.</span><span class="sxs-lookup"><span data-stu-id="809fd-239">**NX_SIZE_ERROR** (0x09) Check service_name_length fail</span></span>

### <a name="allowed-from"></a><span data-ttu-id="809fd-240">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="809fd-240">Allowed From</span></span>

<span data-ttu-id="809fd-241">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="809fd-241">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="809fd-242">Например, .</span><span class="sxs-lookup"><span data-stu-id="809fd-242">Example</span></span>

```c
/* Set service name for PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_service_name_set_extended(&my_pppoe_client,
“BRAS”,4);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” service name has set. */
```

## <a name="nx_pppoe_client_session_connect"></a><span data-ttu-id="809fd-243">nx_pppoe_client_session_connect</span><span class="sxs-lookup"><span data-stu-id="809fd-243">nx_pppoe_client_session_connect</span></span>

<span data-ttu-id="809fd-244">Подключение к сеансу клиента PPPoE</span><span class="sxs-lookup"><span data-stu-id="809fd-244">Connect PPPoE Client session</span></span>

### <a name="prototype"></a><span data-ttu-id="809fd-245">Прототип</span><span class="sxs-lookup"><span data-stu-id="809fd-245">Prototype</span></span>

```c
UINT nx_pppoe_client_session_connect(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="809fd-246">Описание</span><span class="sxs-lookup"><span data-stu-id="809fd-246">Description</span></span>

<span data-ttu-id="809fd-247">Эта служба создает подключение сеанса PPPoE к указанному серверу PPPoE с помощью ранее созданного клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-247">This service makes PPPoE session connection using a previously created PPPoE Client to the specified PPPoE Server.</span></span>

> [!NOTE]
> <span data-ttu-id="809fd-248">Эта функция должна вызываться после *nx_pppoe_client_create*, *nx_pppoe_client_host_uniq_set* и *nx_pppoe_client_service_name_set*.</span><span class="sxs-lookup"><span data-stu-id="809fd-248">This function must be called after *nx_pppoe_client_create*, *nx_pppoe_client_host_uniq_set* and *nx_pppoe_client_service_name_set*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="809fd-249">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="809fd-249">Input Parameters</span></span>

 - <span data-ttu-id="809fd-250">**pppoe_client_ptr** — указатель на блок управления для клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-250">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="809fd-251">**wait_option** — параметр ожидания до установления соединения</span><span class="sxs-lookup"><span data-stu-id="809fd-251">**wait_option** Wait option while the connection is being established.</span></span>

### <a name="return-values"></a><span data-ttu-id="809fd-252">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="809fd-252">Return Values</span></span>

 - <span data-ttu-id="809fd-253">**NX_PPPOE_CLIENT_SUCCESS** (0x00) — сеанс клиента PPPoE успешно подключен.</span><span class="sxs-lookup"><span data-stu-id="809fd-253">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session connect.</span></span>
 - <span data-ttu-id="809fd-254">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) — недопустимый указатель на клиент PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-254">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="809fd-255">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="809fd-255">Allowed From</span></span>

<span data-ttu-id="809fd-256">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="809fd-256">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="809fd-257">Например, .</span><span class="sxs-lookup"><span data-stu-id="809fd-257">Example</span></span>

```c
/* Enable PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_connect(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” session connection has connected. */
```

## <a name="nx_pppoe_client_session_packet_send"></a><span data-ttu-id="809fd-258">nx_pppoe_client_session_packet_send</span><span class="sxs-lookup"><span data-stu-id="809fd-258">nx_pppoe_client_session_packet_send</span></span>

<span data-ttu-id="809fd-259">Отправка пакета клиента PPPoE в указанный сеанс</span><span class="sxs-lookup"><span data-stu-id="809fd-259">Send PPPoE Client packet to specified session</span></span>

### <a name="prototype"></a><span data-ttu-id="809fd-260">Прототип</span><span class="sxs-lookup"><span data-stu-id="809fd-260">Prototype</span></span>

```c
UINT nx_pppoe_client_session_packet_send(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr,
                                    NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="809fd-261">Описание</span><span class="sxs-lookup"><span data-stu-id="809fd-261">Description</span></span>

<span data-ttu-id="809fd-262">Эта служба отправляет пакет PPPoE, используя указанный идентификатор сеанса.</span><span class="sxs-lookup"><span data-stu-id="809fd-262">This service sends PPPoE packet using specified session ID.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="809fd-263">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="809fd-263">Input Parameters</span></span>

 - <span data-ttu-id="809fd-264">**pppoe_client_ptr** — указатель на блок управления для клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-264">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="809fd-265">**packet_ptr** — указатель на пакет PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-265">**packet_ptr** Pointer to PPPoE packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="809fd-266">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="809fd-266">Return Values</span></span>

 - <span data-ttu-id="809fd-267">**NX_PPPOE_CLIENT_SUCCESS** (0x00) — пакет клиента PPPoE успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="809fd-267">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client packet send.</span></span>
 - <span data-ttu-id="809fd-268">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) — недопустимый указатель на клиент PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-268">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="809fd-269">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) — недопустимый пакет клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-269">NX_PPPOE_CLIENT_PACKET_PAYLOAD_ERROR (0xD3) Invalid PPPoE Client packet.</span></span>
 - <span data-ttu-id="809fd-270">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED (0xD8) — сеанс PPPoE не установлен.</span><span class="sxs-lookup"><span data-stu-id="809fd-270">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="809fd-271">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="809fd-271">Allowed From</span></span>

<span data-ttu-id="809fd-272">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="809fd-272">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="809fd-273">Например, .</span><span class="sxs-lookup"><span data-stu-id="809fd-273">Example</span></span>

```c
/* Send PPPoE client packet to specified session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_packet_send(&my_pppoe_client, packet_ptr);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the “my_pppoe_client” packet has sent. */
```

## <a name="nx_pppoe_client_session_terminate"></a><span data-ttu-id="809fd-274">nx_pppoe_client_session_terminate</span><span class="sxs-lookup"><span data-stu-id="809fd-274">nx_pppoe_client_session_terminate</span></span>

<span data-ttu-id="809fd-275">Завершение сеанса клиента PPPoE</span><span class="sxs-lookup"><span data-stu-id="809fd-275">Terminate PPPoE Client session</span></span>

### <a name="prototype"></a><span data-ttu-id="809fd-276">Прототип</span><span class="sxs-lookup"><span data-stu-id="809fd-276">Prototype</span></span>

```c
UINT nx_pppoe_client_session_terminate(
                                    NX_PPPOE_CLIENT *pppoe_client_ptr);
```

### <a name="description"></a><span data-ttu-id="809fd-277">Описание</span><span class="sxs-lookup"><span data-stu-id="809fd-277">Description</span></span>

<span data-ttu-id="809fd-278">Эта служба завершает указанный сеанс PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-278">This service terminates the specified PPPoE session.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="809fd-279">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="809fd-279">Input Parameters</span></span>

 - <span data-ttu-id="809fd-280">**pppoe_client_ptr** — указатель на блок управления для клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-280">**pppoe_client_ptr** Pointer to PPPoE Client control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="809fd-281">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="809fd-281">Return Values</span></span>

 - <span data-ttu-id="809fd-282">**NX_PPPOE_CLIENT_SUCCESS** (0x00) — сеанс клиента PPPoE успешно завершен.</span><span class="sxs-lookup"><span data-stu-id="809fd-282">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session terminate.</span></span>
 - <span data-ttu-id="809fd-283">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) — недопустимый указатель на клиент PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-283">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="809fd-284">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="809fd-284">Allowed From</span></span>

<span data-ttu-id="809fd-285">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="809fd-285">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="809fd-286">Например, .</span><span class="sxs-lookup"><span data-stu-id="809fd-286">Example</span></span>

```c
/* Terminates the specified PPPoE session, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_terminate(&my_pppoe_client);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the session has terminated. */
```

## <a name="nx_pppoe_client_session_get"></a><span data-ttu-id="809fd-287">nx_pppoe_client_session_connect</span><span class="sxs-lookup"><span data-stu-id="809fd-287">nx_pppoe_client_session_get</span></span>

<span data-ttu-id="809fd-288">Получение сведений об указанном сеансе PPPoE</span><span class="sxs-lookup"><span data-stu-id="809fd-288">Get the specified PPPoE session information</span></span>

### <a name="prototype"></a><span data-ttu-id="809fd-289">Прототип</span><span class="sxs-lookup"><span data-stu-id="809fd-289">Prototype</span></span>

```c
UINT nx_pppoe_client_session_get(NX_PPPOE_CLIENT *pppoe_client_ptr,
                                ULONG *server_mac_msw,
                                ULONG *server_mac_lsw,
                                ULONG *session_id);
```

### <a name="description"></a><span data-ttu-id="809fd-290">Описание</span><span class="sxs-lookup"><span data-stu-id="809fd-290">Description</span></span>

<span data-ttu-id="809fd-291">Эта служба получает сведения об указанном сеансе PPPoE, физическом адресе сервера и идентификаторе сеанса.</span><span class="sxs-lookup"><span data-stu-id="809fd-291">This service gets the specified PPPoE session information, server physical address and session id.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="809fd-292">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="809fd-292">Input Parameters</span></span>

 - <span data-ttu-id="809fd-293">**pppoe_server_ptr** — указатель на блок управления для клиента PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-293">**pppoe_server_ptr** Pointer to PPPoE Client control block.</span></span>
 - <span data-ttu-id="809fd-294">**server_mac_msw** — указатель MSW на физический адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="809fd-294">**server_mac_msw** Server Physical address MSW pointer.</span></span>
 - <span data-ttu-id="809fd-295">**server_mac_lsw** — указатель LSW на физический адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="809fd-295">**server_mac_lsw** Server Physical address MSW pointer.</span></span>
 - <span data-ttu-id="809fd-296">**session_id**: указатель на идентификатор сеанса.</span><span class="sxs-lookup"><span data-stu-id="809fd-296">**session_id** Session ID pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="809fd-297">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="809fd-297">Return Values</span></span>

 - <span data-ttu-id="809fd-298">**NX_PPPOE_CLIENT_SUCCESS** (0x00) — сеанс клиента PPPoE успешно получен.</span><span class="sxs-lookup"><span data-stu-id="809fd-298">**NX_PPPOE_CLIENT_SUCCESS** (0x00) Successful PPPoE Client session get.</span></span>
 - <span data-ttu-id="809fd-299">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) — недопустимый указатель на клиент PPPoE.</span><span class="sxs-lookup"><span data-stu-id="809fd-299">NX_PPPOE_CLIENT_PTR_ERROR (0xD1) Invalid PPPoE Client pointer.</span></span>
 - <span data-ttu-id="809fd-300">NX_PPPOE_SERVER_SESSION_NOT_ESTABLISHED (0xD8) — сеанс PPPoE не установлен.</span><span class="sxs-lookup"><span data-stu-id="809fd-300">NX_PPPOE_CLIENT_SESSION_NOT_ESTABLISHED (0xD8) PPPoE session is not established.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="809fd-301">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="809fd-301">Allowed From</span></span>

<span data-ttu-id="809fd-302">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="809fd-302">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="809fd-303">Пример</span><span class="sxs-lookup"><span data-stu-id="809fd-303">Example</span></span>

```c
/* Gets the specified PPPoE session information, PPPoE Client instance “my_pppoe_client”. */
status =  nx_pppoe_client_session_get (&my_pppoe_client, &server_mac_msw, &server_mac_lsw, &session_id);

/* If status is NX_PPPOE_CLIENT_SUCCESS, the server physical address and session id
   of the session has got. */
```
