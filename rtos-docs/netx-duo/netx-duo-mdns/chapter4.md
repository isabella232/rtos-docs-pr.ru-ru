---
title: Глава 4. Описание служб mDNS
description: В этой главе приведено описание всех служб mDNS в NetX.
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 89df0ab5f09be8ad50a27d23bae8b20d71caa0b4
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814664"
---
# <a name="chapter-4---description-of-mdns-services"></a><span data-ttu-id="02e1f-103">Глава 4. Описание служб mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-103">Chapter 4 - Description of mDNS services</span></span>

<span data-ttu-id="02e1f-104">В этой главе приведено описание всех служб mDNS в NetX.</span><span class="sxs-lookup"><span data-stu-id="02e1f-104">This chapter contains a description of all NetX mDNS services (listed below).</span></span>

> [!NOTE]
> <span data-ttu-id="02e1f-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки API на предмет ошибок, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="02e1f-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_mdns_create"></a><span data-ttu-id="02e1f-106">nx_mdns_create</span><span class="sxs-lookup"><span data-stu-id="02e1f-106">nx_mdns_create</span></span>

<span data-ttu-id="02e1f-107">Создание экземпляра mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-107">Create an mDNS instance</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-108">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-108">Prototype</span></span>

```C
UINT nx_mdns_create(NX_MDNS *mdns_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool,
    UINT priority, VOID *stack_ptr,
    UINT stack_size, UCHAR *host_name,
    VOID *local_service_cache,
    UINT local_service_cache_size,
    VOID *peer_service_cache,
    UINT peer_service_cache_size,
    VOID (*probing_notify)(NX_MDNS *mdns_ptr,
        UCHAR *name, UINT probing_state));
```

### <a name="description"></a><span data-ttu-id="02e1f-109">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-109">Description</span></span>

<span data-ttu-id="02e1f-110">Эта служба создает экземпляр mDNS в определенном экземпляре IP и связанные ресурсы.</span><span class="sxs-lookup"><span data-stu-id="02e1f-110">This service creates an mDNS instance on the specific IP instance and associated resources.</span></span> <span data-ttu-id="02e1f-111">Кроме того, создается поток для обработки входящих сообщений mDNS, ответа на запросы и периодической передачи сообщений запросов.</span><span class="sxs-lookup"><span data-stu-id="02e1f-111">A thread is also created to handle incoming mDNS messages, to respond to queries, and to periodically transmit query messages.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-112">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-112">Input Parameters</span></span>

- <span data-ttu-id="02e1f-113">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-113">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="02e1f-114">**ip_ptr**: указатель на связанный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="02e1f-114">**ip_ptr** Pointer to the associated IP instance.</span></span>
- <span data-ttu-id="02e1f-115">**packet_pool**: указатель на допустимый пул пакетов</span><span class="sxs-lookup"><span data-stu-id="02e1f-115">**packet_pool** Pointer to a valid packet pool.</span></span>
- <span data-ttu-id="02e1f-116">**priority**: приоритет потока mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-116">**priority** Priority of the mDNS thread.</span></span>
- <span data-ttu-id="02e1f-117">**stack_ptr**: указатель на область стека для потока mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-117">**stack_ptr** Pointer to the stack area for the mDNS thread</span></span>
- <span data-ttu-id="02e1f-118">**stack_size**: размер области стека</span><span class="sxs-lookup"><span data-stu-id="02e1f-118">**stack_size** Size of the stack area.</span></span>
- <span data-ttu-id="02e1f-119">**host_name**: имя узла, присвоенное этому узлу</span><span class="sxs-lookup"><span data-stu-id="02e1f-119">**host_name** Host name assigned to this node.</span></span>
- <span data-ttu-id="02e1f-120">**local_service_cache**: пространство для хранения для локальных зарегистрированных служб</span><span class="sxs-lookup"><span data-stu-id="02e1f-120">**local_service_cache** Storage space for local registered services.</span></span>
- <span data-ttu-id="02e1f-121">**local_service_cache_size**: размер локального кэша служб</span><span class="sxs-lookup"><span data-stu-id="02e1f-121">**local_service_cache_size** Size of the local service cache.</span></span>
- <span data-ttu-id="02e1f-122">**peer_service_cache**: пространство для хранения полученных данных служб</span><span class="sxs-lookup"><span data-stu-id="02e1f-122">**peer_service_cache** Storage space for service information received</span></span>
- <span data-ttu-id="02e1f-123">**peer_service_cache_size**: размер однорангового кэша служб</span><span class="sxs-lookup"><span data-stu-id="02e1f-123">**peer_service_cache_size** Size of the peer service cache</span></span>
- <span data-ttu-id="02e1f-124">**probing_notify**: необязательная функция обратного вызова, вызываемая по завершении операции проверки</span><span class="sxs-lookup"><span data-stu-id="02e1f-124">**probing_notify** Optional callback function invoked at the end of the probing operation.</span></span> <span data-ttu-id="02e1f-125">Она уведомляет приложение о том, является ли имя узла (при включении mDNS в локальном интерфейсе) или имя службы (после регистрации службы) уникальным.</span><span class="sxs-lookup"><span data-stu-id="02e1f-125">It notifies the application whether or not the host name (when enabling mDNS on a local interface), or the service name (after registering a service) is unique.</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-126">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-126">Return Values</span></span>

- <span data-ttu-id="02e1f-127">**NX_SUCCESS** (0x00) — экземпляр mDNS успешно создан.</span><span class="sxs-lookup"><span data-stu-id="02e1f-127">**NX_SUCCESS** (0x00) Successfully created mDNS instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-128">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-128">Allowed From</span></span>

<span data-ttu-id="02e1f-129">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-129">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-130">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-130">Example</span></span>

```C
UCHAR stack_ptr[2048];
UCHAR local_cache_ptr[2048];
UCHAR peer_cache_ptr[8192];

/* Create a mDNS instance. */
status = nx_mdns_create(&my_mdns, &ip_0, &pool_0,
    3, stack_ptr, 2048,
    “NETX-MDNS-HOST”,
    local_cache_ptr, 2048,
    peer_cache_ptr, 8192,
    probing_notify);

/* If status is NX_SUCCESS, mDNS instance was created. */
```

## <a name="nx_mdns_delete"></a><span data-ttu-id="02e1f-131">nx_mdns_delete</span><span class="sxs-lookup"><span data-stu-id="02e1f-131">nx_mdns_delete</span></span>

<span data-ttu-id="02e1f-132">Удаление экземпляра mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-132">Delete an mDNS instance</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-133">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-133">Prototype</span></span>

```C
UINT nx_mdns_delete(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="02e1f-134">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-134">Description</span></span>

<span data-ttu-id="02e1f-135">Эта служба удаляет экземпляр mDNS и освобождает его ресурсы.</span><span class="sxs-lookup"><span data-stu-id="02e1f-135">This service deletes the mDNS instance and frees its resources.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-136">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-136">Input Parameters</span></span>

- <span data-ttu-id="02e1f-137">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-137">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-138">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-138">Return Values</span></span>

- <span data-ttu-id="02e1f-139">**NX_SUCCESS** (0x00) — экземпляр mDNS успешно удален.</span><span class="sxs-lookup"><span data-stu-id="02e1f-139">**NX_SUCCESS** (0x00) Successfully deleted the mDNS instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-140">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-140">Allowed From</span></span>

<span data-ttu-id="02e1f-141">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-141">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-142">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-142">Example</span></span>

```C
/* Delete a previously created mDNS instance. */

status = nx_mdns_delete(&my_mdns);

/* If status is NX_SUCCESS, the mDNS instance has been deleted. */
```

## <a name="nx_mdns_enable"></a><span data-ttu-id="02e1f-143">nx_mdns_enable</span><span class="sxs-lookup"><span data-stu-id="02e1f-143">nx_mdns_enable</span></span>

<span data-ttu-id="02e1f-144">Запуск службы mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-144">Start the mDNS service</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-145">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-145">Prototype</span></span>

```C
UINT nx_mdns_enable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="02e1f-146">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-146">Description</span></span>

<span data-ttu-id="02e1f-147">Этот интерфейс API включает службу mDNS в конкретном физическом интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="02e1f-147">This API enables mDNS service on specific physical interface.</span></span> <span data-ttu-id="02e1f-148">После включения службы модуль mDNS сначала проверяет все уникальные имена служб в сети, прежде чем отвечать на запросы, полученные через интерфейс.</span><span class="sxs-lookup"><span data-stu-id="02e1f-148">Once the service is enabled, the mDNS module first probes all its unique service names on the network before responding to queries received on the interface.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-149">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-149">Input Parameters</span></span>

- <span data-ttu-id="02e1f-150">**mdns_ptr**: указатель на блок управления экземпляра mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-150">**mdns_ptr** Pointer to the mDNS instance control block.</span></span>
- <span data-ttu-id="02e1f-151">**interface_index**: индекс интерфейса, в котором должна быть включена служба</span><span class="sxs-lookup"><span data-stu-id="02e1f-151">**interface_index** Index to the interface where the service is to be enabled</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-152">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-152">Return Values</span></span>

- <span data-ttu-id="02e1f-153">**NX_SUCCESS** (0x00) — служба успешно включена.</span><span class="sxs-lookup"><span data-stu-id="02e1f-153">**NX_SUCCESS** (0x00) Successfully enabled the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-154">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-154">Allowed From</span></span>

<span data-ttu-id="02e1f-155">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-155">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-156">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-156">Example</span></span>

```C
/* Enable mDNS service on specific interface. */

status = nx_mdns_enable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was enabled. */
```

## <a name="nx_mdns_disable"></a><span data-ttu-id="02e1f-157">nx_mdns_disable</span><span class="sxs-lookup"><span data-stu-id="02e1f-157">nx_mdns_disable</span></span>

<span data-ttu-id="02e1f-158">Отключение службы mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-158">Disable the mDNS service</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-159">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-159">Prototype</span></span>

```C
UINT nx_mdns_disable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="02e1f-160">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-160">Description</span></span>

<span data-ttu-id="02e1f-161">Этот интерфейс API отключает службу mDNS в указанном физическом интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="02e1f-161">This API disables mDNS service on the specific physical interface.</span></span> <span data-ttu-id="02e1f-162">После отключения службы mDNS отправляет сообщение о завершении каждой локальной службе в сети, подключенной к интерфейсу, чтобы уведомить соседние узлы.</span><span class="sxs-lookup"><span data-stu-id="02e1f-162">Once the service is disabled, the mDNS sends "goodbye" messages for every local service to the network that is attached to the interface, so the neighboring nodes are notified.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-163">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-163">Input Parameters</span></span>

- <span data-ttu-id="02e1f-164">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-164">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="02e1f-165">**interface_index**: индекс интерфейса, в котором должна быть отключена служба</span><span class="sxs-lookup"><span data-stu-id="02e1f-165">**interface_index** Index to the interface where the service is to be disabled</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-166">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-166">Return Values</span></span>

- <span data-ttu-id="02e1f-167">**NX_SUCCESS** (0x00) — служба успешно отключена.</span><span class="sxs-lookup"><span data-stu-id="02e1f-167">**NX_SUCCESS** (0x00) Successfully disabled the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-168">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-168">Allowed From</span></span>

<span data-ttu-id="02e1f-169">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-169">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-170">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-170">Example</span></span>

```C
/* Disable mDNS service on specific interface. */

status = nx_mdns_disable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was disabled. */
```

## <a name="nx_mdns_cache_notify_set"></a><span data-ttu-id="02e1f-171">nx_mdns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="02e1f-171">nx_mdns_cache_notify_set</span></span>

<span data-ttu-id="02e1f-172">Устанавливает функцию уведомления о заполнении кэша mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-172">Installs the mDNS cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-173">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-173">Prototype</span></span>

```c
UINT nx_mdns_cache_notify_set(NX_MDNS *mdns_ptr,
    VOID (*cache_full_notify_cb)(NX_MDNS *mdns_ptr,
        UINT state, UINT cache_type));
```

### <a name="description"></a><span data-ttu-id="02e1f-174">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-174">Description</span></span>

<span data-ttu-id="02e1f-175">Эта служба устанавливает предоставленную пользователем функцию обратного вызова, которая вызывается, когда заполняется локальный кэш служб или одноранговый кэш служб.</span><span class="sxs-lookup"><span data-stu-id="02e1f-175">This service installs a user-supplied callback function, which is invoked when either the local service cache or peer service cache becomes full.</span></span> <span data-ttu-id="02e1f-176">При заполнении кэша служб больше нельзя добавлять записи ресурсов mDNS.</span><span class="sxs-lookup"><span data-stu-id="02e1f-176">When the service cache is full, no more mDNS Resource Record can be added.</span></span> <span data-ttu-id="02e1f-177">Обратите внимание, что кэш служб может заполниться в результате внутренней фрагментации, когда добавляются и удаляются службы с различной длиной строк.</span><span class="sxs-lookup"><span data-stu-id="02e1f-177">Note that the service cache may become full as a result of internal fragmentation, when services with various string lengths are added and removed.</span></span> <span data-ttu-id="02e1f-178">При получении уведомления о заполнении однорангового кэша служб приложение может использовать службу *nx_mdns_service_cache_clear* для удаления всех записей в нем.</span><span class="sxs-lookup"><span data-stu-id="02e1f-178">On receiving a cache full notification on peer service cache, the application may use the service "*nx_mdns_service_cache_clear"* to erase all entries in the peer service cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-179">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-179">Input Parameters</span></span>

- <span data-ttu-id="02e1f-180">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-180">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-181">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-181">Return Values</span></span>

- <span data-ttu-id="02e1f-182">**NX_SUCCESS** (0x00) — функция обратного вызова для уведомления о заполнении кэша mDNS успешно установлена.</span><span class="sxs-lookup"><span data-stu-id="02e1f-182">**NX_SUCCESS** (0x00) Successfully installed the mDNS cache notify callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-183">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-183">Allowed From</span></span>

<span data-ttu-id="02e1f-184">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-184">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-185">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-185">Example</span></span>

```C
/* Set mDNS cache notify callback. */

status = nx_mdns_cache_notify_set(&my_mdns, cache_full_nofiy_cb);

/* If status is NX_SUCCESS, mDNS cache notify callback was set. */
```

## <a name="nx_mdns_cache_notify_clear"></a><span data-ttu-id="02e1f-186">nx_mdns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="02e1f-186">nx_mdns_cache_notify_clear</span></span>

<span data-ttu-id="02e1f-187">Очистка функции уведомления о заполнении кэша служб mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-187">Clear the mDNS service cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-188">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-188">Prototype</span></span>

```C
UINT nx_mdns_cache_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="02e1f-189">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-189">Description</span></span>

<span data-ttu-id="02e1f-190">Эта служба очищает предоставленную пользователем функцию обратного вызова для уведомления о заполнении кэша служб.</span><span class="sxs-lookup"><span data-stu-id="02e1f-190">This service clears a user-supplied service cache notify callback function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-191">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-191">Input Parameters</span></span>

- <span data-ttu-id="02e1f-192">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-192">**mdns_ptr** Pointer to the mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-193">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-193">Return Values</span></span>

- <span data-ttu-id="02e1f-194">**NX_SUCCESS** (0x00) — функция обратного вызова для уведомления о заполнении кэша служб mDNS успешно очищена.</span><span class="sxs-lookup"><span data-stu-id="02e1f-194">**NX_SUCCESS** (0x00) Successfully cleared the mDNS service cache notify callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-195">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-195">Allowed From</span></span>

<span data-ttu-id="02e1f-196">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-196">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-197">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-197">Example</span></span>

```C
/* Clear mDNS cache notify callback. */

status = nx_mdns_cache_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, mDNS cache notify callback clear. */
```

## <a name="nx_mdns_domain_name_set"></a><span data-ttu-id="02e1f-198">nx_mdns_domain_name_set</span><span class="sxs-lookup"><span data-stu-id="02e1f-198">nx_mdns_domain_name_set</span></span>

<span data-ttu-id="02e1f-199">Задание доменного имени</span><span class="sxs-lookup"><span data-stu-id="02e1f-199">Sets the domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-200">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-200">Prototype</span></span>

```C
UINT nx_mdns_domain_name_set(NX_MDNS *mdns_ptr, CHAR *domain_name);
```

### <a name="description"></a><span data-ttu-id="02e1f-201">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-201">Description</span></span>

<span data-ttu-id="02e1f-202">Эта служба задает локальное доменное имя по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="02e1f-202">This service sets up the default local domain name.</span></span> <span data-ttu-id="02e1f-203">При создании экземпляра mDNS локальное доменное имя по умолчанию устанавливается в значение .local.</span><span class="sxs-lookup"><span data-stu-id="02e1f-203">When the mDNS instance is created, the default local domain name is set to “.local”.</span></span> <span data-ttu-id="02e1f-204">Этот интерфейс API позволяет приложению перезаписать локальное доменное имя по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="02e1f-204">This API allows an application to overwrite the default local domain name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-205">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-205">Input Parameters</span></span>

- <span data-ttu-id="02e1f-206">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-206">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="02e1f-207">**domain_name**: доменное имя, которое следует использовать</span><span class="sxs-lookup"><span data-stu-id="02e1f-207">**domain_name** The domain name to be used.</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-208">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-208">Return Values</span></span>

- <span data-ttu-id="02e1f-209">**NX_SUCCESS** (0x00) — локальный домен успешно настроен.</span><span class="sxs-lookup"><span data-stu-id="02e1f-209">**NX_SUCCESS** (0x00) Successfully configured local domain.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-210">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-210">Allowed From</span></span>

<span data-ttu-id="02e1f-211">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-211">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-212">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-212">Example</span></span>

```C
/* Set the domain name. */

status = nx_mdns_domain_name_set(&my_mdns, “home”);

/* If status is NX_SUCCESS, the “home” domain name was set. */
```

## <a name="nx_mdns_service_announcement_timing_set"></a><span data-ttu-id="02e1f-213">nx_mdns_service_announcement_timing_set</span><span class="sxs-lookup"><span data-stu-id="02e1f-213">nx_mdns_service_announcement_timing_set</span></span>

<span data-ttu-id="02e1f-214">Задание параметров времени для сообщений с объявлениями служб</span><span class="sxs-lookup"><span data-stu-id="02e1f-214">Sets the timing parameters for service announcement messages</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-215">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-215">Prototype</span></span>

```C
UINT nx_mdns_service_announcement_timing_set(NX_MDNS *mdns_ptr,
    UINT t, UINT p, UINT k, UINT retrans_interval,
    UINT period_interval, UINT max_time);
```

### <a name="description"></a><span data-ttu-id="02e1f-216">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-216">Description</span></span>

<span data-ttu-id="02e1f-217">Эта служба перенастраивает параметры времени, используемые mDNS при отправке объявлений служб.</span><span class="sxs-lookup"><span data-stu-id="02e1f-217">This service reconfigures the timing parameters employed by mDNS when sending the service announcements.</span></span> <span data-ttu-id="02e1f-218">Период публикации начинается с *t* тактов, и его можно увеличивать с коэффициентом 2 в степени *k*.</span><span class="sxs-lookup"><span data-stu-id="02e1f-218">Publish period starts from *t* ticks and can be expanded telescopically with 2 to the power of *k* factor.</span></span> <span data-ttu-id="02e1f-219">Число повторов на объявление составляет *p*, интервал между повторными объявлениями — *interval*, а период объявления — max_time.</span><span class="sxs-lookup"><span data-stu-id="02e1f-219">The number of repetitions per advertisement is *p*, the interval between each repeated advertisement is *interval* ticks, and the number of announcement period is max_time.</span></span> <span data-ttu-id="02e1f-220">По умолчанию начальный период равен 1 секунде, k = 1 (период каждый раз удваивается), *p = 1* (без повторения), retrans_interval = 0 (без интервала времени), period_interval = 0xFFFFFFFF (максимальный интервал периода), а max_time = 3 (число объявлений).</span><span class="sxs-lookup"><span data-stu-id="02e1f-220">By default, the initial period is set to 1 second, with k = 1 (the period doubles each time), *p = 1* (no repetition), retrans_interval = 0(no time interval), period_interval = 0xFFFFFFFF(max period interval) and max_time = 3(number of advertisement).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-221">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-221">Input Parameters</span></span>

- <span data-ttu-id="02e1f-222">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-222">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="02e1f-223">**t**: число тактов начального периода</span><span class="sxs-lookup"><span data-stu-id="02e1f-223">**t** Number of ticks for the initial period.</span></span> <span data-ttu-id="02e1f-224">Значение по умолчанию — 100 тактов в течение 1 секунды.</span><span class="sxs-lookup"><span data-stu-id="02e1f-224">Default is 100 ticks for 1 second.</span></span>
- <span data-ttu-id="02e1f-225">**p**: число повторений</span><span class="sxs-lookup"><span data-stu-id="02e1f-225">**p** Number of repetitions.</span></span> <span data-ttu-id="02e1f-226">Значение по умолчанию — 1.</span><span class="sxs-lookup"><span data-stu-id="02e1f-226">Default value is 1.</span></span>
- <span data-ttu-id="02e1f-227">**k**: коэффициент увеличения</span><span class="sxs-lookup"><span data-stu-id="02e1f-227">**k** Telescopic factor.</span></span> <span data-ttu-id="02e1f-228">Значение по умолчанию — 1.</span><span class="sxs-lookup"><span data-stu-id="02e1f-228">Default value is 1.</span></span>
- <span data-ttu-id="02e1f-229">**retrans_interval**: число тактов, которое нужно прождать перед отправкой повторного сообщения с объявлением</span><span class="sxs-lookup"><span data-stu-id="02e1f-229">**retrans_interval** Number of ticks to wait before sending out repeated announcement messages.</span></span> <span data-ttu-id="02e1f-230">По умолчанию установлено значение 0.</span><span class="sxs-lookup"><span data-stu-id="02e1f-230">Default value is 0.</span></span>
- <span data-ttu-id="02e1f-231">**period_interval**: число тактов между двумя периодами объявления</span><span class="sxs-lookup"><span data-stu-id="02e1f-231">**period_interval** Number of ticks between two announcement period.</span></span> <span data-ttu-id="02e1f-232">Значение по умолчанию — 0xFFFFFFFF.</span><span class="sxs-lookup"><span data-stu-id="02e1f-232">Default value is 0xFFFFFFFF.</span></span>
- <span data-ttu-id="02e1f-233">**max_time**: число периодов, которое следует использовать для объявления</span><span class="sxs-lookup"><span data-stu-id="02e1f-233">**max_time** Number of announcement period to use for the advertisement.</span></span> <span data-ttu-id="02e1f-234">После *max_time* периодов сообщения объявления больше не отправляются.</span><span class="sxs-lookup"><span data-stu-id="02e1f-234">After the *max_time* announcement periods, no more announcement messages are sent.</span></span> <span data-ttu-id="02e1f-235">Значение по умолчанию — 3.</span><span class="sxs-lookup"><span data-stu-id="02e1f-235">Default value is 3.</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-236">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-236">Return Values</span></span>

- <span data-ttu-id="02e1f-237">**NX_SUCCESS** (0x00) — значения времени успешно заданы.</span><span class="sxs-lookup"><span data-stu-id="02e1f-237">**NX_SUCCESS** (0x00) Successfully sets the timing values.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-238">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-238">Allowed From</span></span>

<span data-ttu-id="02e1f-239">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-239">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-240">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-240">Example</span></span>

```C
/* Set the service announcement timing. */

status = nx_mdns_service_announcement_timing_set(&my_mdns, 100,
    1, 1, 0, 0xFFFFFFFF, 3);

/* If status is NX_SUCCESS, the service announcement timing was set. */
```

## <a name="nx_mdns_service_add"></a><span data-ttu-id="02e1f-241">nx_mdns_service_add</span><span class="sxs-lookup"><span data-stu-id="02e1f-241">nx_mdns_service_add</span></span>

<span data-ttu-id="02e1f-242">Добавление локальной службы</span><span class="sxs-lookup"><span data-stu-id="02e1f-242">Add a local service</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-243">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-243">Prototype</span></span>

```C
UINT nx_mdns_service_add(NX_MDNS *mdns_ptr, CHAR *instance,
    CHAR *service, CHAR *subtype, UINT ttl, USHORT priority,
    USHORT weight, USHORT port, UCHAR *text, UCHAR is_unique,
    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="02e1f-244">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-244">Description</span></span>

<span data-ttu-id="02e1f-245">Этот интерфейс API регистрирует службу, предлагаемую приложением.</span><span class="sxs-lookup"><span data-stu-id="02e1f-245">This API registers a service offered by the application.</span></span> <span data-ttu-id="02e1f-246">Если установлен флаг *is_unique*, mDNS проверяет уникальность имени службы в локальной сети, прежде чем приступать к объявлению службы.</span><span class="sxs-lookup"><span data-stu-id="02e1f-246">If the flag *is_unique* is set, mDNS probes the service name to make sure it is unique on the local network before starting to announce the service on the network.</span></span> <span data-ttu-id="02e1f-247">*instance* — это часть имени службы, указывающая экземпляр.</span><span class="sxs-lookup"><span data-stu-id="02e1f-247">*Instance* is the instance portion of the service name.</span></span> <span data-ttu-id="02e1f-248">*service* — это часть имени службы, указывающая службу.</span><span class="sxs-lookup"><span data-stu-id="02e1f-248">The *service* is the service portion of the service name.</span></span> <span data-ttu-id="02e1f-249">Например, _http._tcp — это служба.</span><span class="sxs-lookup"><span data-stu-id="02e1f-249">For example “_http._tcp” is a service.</span></span> <span data-ttu-id="02e1f-250">Для описания службы с подтипом вызывающая сторона должна использовать параметр *subtype*.</span><span class="sxs-lookup"><span data-stu-id="02e1f-250">To describe a service with subtype, caller must use the *subtype* parameter.</span></span> <span data-ttu-id="02e1f-251">Например, если нужная служба — _printer._sub._http._tcp, поле service имеет значение _http._tcp:, а поле subtype — _printer.</span><span class="sxs-lookup"><span data-stu-id="02e1f-251">For example, if the desired service is “_printer._sub._http._tcp”, the service field is “_http._tcp:, and the subtype field is “_printer”.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-252">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-252">Input Parameters</span></span>

- <span data-ttu-id="02e1f-253">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-253">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="02e1f-254">**instance**: указатель на имя экземпляра службы</span><span class="sxs-lookup"><span data-stu-id="02e1f-254">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="02e1f-255">**service**: указатель на тип службы mDNS без сведений о подтипе</span><span class="sxs-lookup"><span data-stu-id="02e1f-255">**service** Pointer to the mDNS service type, excluding subtype information.</span></span>
- <span data-ttu-id="02e1f-256">**subtype**: указатель на подтип службы mDNS, если применимо</span><span class="sxs-lookup"><span data-stu-id="02e1f-256">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="02e1f-257">**priority**: приоритет службы</span><span class="sxs-lookup"><span data-stu-id="02e1f-257">**priority** Service priority</span></span>
- <span data-ttu-id="02e1f-258">**weight**: вес службы</span><span class="sxs-lookup"><span data-stu-id="02e1f-258">**weight** Service weight</span></span>
- <span data-ttu-id="02e1f-259">**port**: номер TCP- или UDP-порта, используемого службой</span><span class="sxs-lookup"><span data-stu-id="02e1f-259">**port** TCP or UDP port number the service uses</span></span>
- <span data-ttu-id="02e1f-260">**text**: дополнительные текстовые сведения</span><span class="sxs-lookup"><span data-stu-id="02e1f-260">**text** Additional text information</span></span>
- <span data-ttu-id="02e1f-261">**is_unique**: логический флаг, указывающий, является ли служба общей или уникальной</span><span class="sxs-lookup"><span data-stu-id="02e1f-261">**is_unique** Boolean flag indicating whether the service is shared or unique.</span></span> <span data-ttu-id="02e1f-262">Для служб, зарегистрированных как уникальные, mDNS должен проверить службу в сети, прежде чем предлагать ее.</span><span class="sxs-lookup"><span data-stu-id="02e1f-262">For services registered as unique, mDNS must probe the service on the network before starting offering it.</span></span>
- <span data-ttu-id="02e1f-263">**Interface_index**: физический интерфейс, через который предоставляется служба</span><span class="sxs-lookup"><span data-stu-id="02e1f-263">**Interface_index** Physical interface the service is offered through.</span></span> <span data-ttu-id="02e1f-264">Для службы, предоставляемой любыми связанными службами, используется значение *NX_MDNS_ALL_INTERFACES*.</span><span class="sxs-lookup"><span data-stu-id="02e1f-264">For a service that is offered through any of the attached services, the value *NX_MDNS_ALL_INTERFACES* is used.</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-265">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-265">Return Values</span></span>

- <span data-ttu-id="02e1f-266">**NX_SUCCESS** (0x00) — служба успешно зарегистрирована.</span><span class="sxs-lookup"><span data-stu-id="02e1f-266">**NX_SUCCESS** (0x00) Successfully registered the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-267">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-267">Allowed From</span></span>

<span data-ttu-id="02e1f-268">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-268">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-269">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-269">Example</span></span>

```C
/* Add local service. */

status = nx_mdns_service_add(&my_mdns, “NETX-SERVICE”,
    “_http._tcp”, NX_NULL,
    NX_NULL, 0, 0, 0, 80, NX_TRUE, 0);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was added. */
```

## <a name="nx_mdns_service_delete"></a><span data-ttu-id="02e1f-270">nx_mdns_service_delete</span><span class="sxs-lookup"><span data-stu-id="02e1f-270">nx_mdns_service_delete</span></span>

<span data-ttu-id="02e1f-271">Удаление ранее зарегистрированной службы</span><span class="sxs-lookup"><span data-stu-id="02e1f-271">Remove a previous registered service</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-272">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-272">Prototype</span></span>

```C
UINT nx_mdns_service_delete(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="02e1f-273">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-273">Description</span></span>

<span data-ttu-id="02e1f-274">Этот интерфейс API удаляет ранее зарегистрированную службу.</span><span class="sxs-lookup"><span data-stu-id="02e1f-274">This API deletes a previous registered service.</span></span> <span data-ttu-id="02e1f-275">После удаления службы в локальную сеть рассылаются сообщения о завершении для уведомления соседних узлов.</span><span class="sxs-lookup"><span data-stu-id="02e1f-275">As the service is deleted, "goodbye" messages are sent to the local network so the neighboring nodes are notified.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-276">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-276">Input Parameters</span></span>

- <span data-ttu-id="02e1f-277">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-277">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="02e1f-278">**instance**: указатель на имя экземпляра службы</span><span class="sxs-lookup"><span data-stu-id="02e1f-278">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="02e1f-279">**service**: указатель на тип службы mDNS без сведений о подтипе</span><span class="sxs-lookup"><span data-stu-id="02e1f-279">**service** Pointer to the mDNS service type, excluding subtype information.</span></span>
- <span data-ttu-id="02e1f-280">**subtype**: указатель на подтип службы mDNS, если применимо</span><span class="sxs-lookup"><span data-stu-id="02e1f-280">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-281">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-281">Return Values</span></span>

- <span data-ttu-id="02e1f-282">**NX_SUCCESS** (0x00) — служба успешно удалена.</span><span class="sxs-lookup"><span data-stu-id="02e1f-282">**NX_SUCCESS** (0x00) Successfully deleted the service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-283">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-283">Allowed From</span></span>

<span data-ttu-id="02e1f-284">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-284">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-285">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-285">Example</span></span>

```C
/* Delete local service. */

status = nx_mdns_service_delete(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was deleted. */
```

## <a name="nx_mdns_service_one_shot_query"></a><span data-ttu-id="02e1f-286">nx_mdns_service_one_shot_query</span><span class="sxs-lookup"><span data-stu-id="02e1f-286">nx_mdns_service_one_shot_query</span></span>

<span data-ttu-id="02e1f-287">Инициация однократного обнаружения службы</span><span class="sxs-lookup"><span data-stu-id="02e1f-287">Initiate one-shot service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-288">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-288">Prototype</span></span>

```C
UINT nx_mdns_service_one_shot_query(NX_MDNS *mdns_ptr,
    UCHAR *instance,
    UCHAR *service,
    UCHAR *subtype,
    NX_MDNS_SERVICE *service_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="02e1f-289">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-289">Description</span></span>

<span data-ttu-id="02e1f-290">Эта служба выполняет однократный запрос mDNS.</span><span class="sxs-lookup"><span data-stu-id="02e1f-290">This service performs a one-shot mDNS query.</span></span> <span data-ttu-id="02e1f-291">Если указанная служба найдена в одноранговом кэше служб, возвращается первый экземпляр.</span><span class="sxs-lookup"><span data-stu-id="02e1f-291">If the specified service is found in the peer service cache, the first instance is returned.</span></span> <span data-ttu-id="02e1f-292">Если в локальном одноранговом кэше служб службы не найдены, модуль mDNS выдает команду запроса и ожидает ответа.</span><span class="sxs-lookup"><span data-stu-id="02e1f-292">If no services are found in the local peer service cache, the mDNS module issues a query command and wait for response.</span></span> <span data-ttu-id="02e1f-293">Служба блокируется до получения первого ответа или истечения времени ожидания запроса.</span><span class="sxs-lookup"><span data-stu-id="02e1f-293">The service is blocked till either the first answer is received or the query times out.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-294">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-294">Input Parameters</span></span>

- <span data-ttu-id="02e1f-295">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-295">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="02e1f-296">**instance**: указатель на имя экземпляра службы, если применимо</span><span class="sxs-lookup"><span data-stu-id="02e1f-296">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="02e1f-297">**service**: указатель на тип службы mDNS без сведений о подтипе</span><span class="sxs-lookup"><span data-stu-id="02e1f-297">**service** Pointer to the mDNS service type, excluding subtype information.</span></span> <span data-ttu-id="02e1f-298">Приложение должно указать тип службы.</span><span class="sxs-lookup"><span data-stu-id="02e1f-298">the application must specify the service type.</span></span>
- <span data-ttu-id="02e1f-299">**subtype**: указатель на подтип службы mDNS, если применимо</span><span class="sxs-lookup"><span data-stu-id="02e1f-299">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="02e1f-300">**service_ptr**: предоставляемый пользователем указатель на структуру NX_MDNS_SERVICE, в которой хранятся результаты запроса</span><span class="sxs-lookup"><span data-stu-id="02e1f-300">**service_ptr** User provided pointer to NX_MDNS_SERVICE structure that stores the query results.</span></span>
- <span data-ttu-id="02e1f-301">**wait_option**: время ожидания ответа в тактах</span><span class="sxs-lookup"><span data-stu-id="02e1f-301">**wait_option** The amount of time, in ticks, to wait for a response.</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-302">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-302">Return Values</span></span>

- <span data-ttu-id="02e1f-303">**NX_SUCCESS** (0x00) — сведения о службе успешно получены.</span><span class="sxs-lookup"><span data-stu-id="02e1f-303">**NX_SUCCESS** (0x00) Successfully obtained service information.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-304">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-304">Allowed From</span></span>

<span data-ttu-id="02e1f-305">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-305">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-306">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-306">Example</span></span>

```C
/* Start service one shot query. */

status = nx_mdns_service_one_shot_query(&my_mdns, “NETX-SERVICE”, “_http._tcp”,
    NX_NULL, service_ptr, 500);

/* If status is NX_SUCCESS, The query with
    name: NetX-SERVICE._http._tcp.local,
     type: ANY (SRV and TXT) was sent.
    And the answer was stored in service_ptr if success. */
```

## <a name="nx_mdns_service_continuous_query"></a><span data-ttu-id="02e1f-307">nx_mdns_service_continuous_query</span><span class="sxs-lookup"><span data-stu-id="02e1f-307">nx_mdns_service_continuous_query</span></span>

<span data-ttu-id="02e1f-308">Инициация непрерывного обнаружения службы</span><span class="sxs-lookup"><span data-stu-id="02e1f-308">Initiate continuous service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-309">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-309">Prototype</span></span>

```C
UINT nx_mdns_service_continous_query(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="02e1f-310">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-310">Description</span></span>

<span data-ttu-id="02e1f-311">Эта служба запускает непрерывный запрос.</span><span class="sxs-lookup"><span data-stu-id="02e1f-311">This service starts a continuous query.</span></span> <span data-ttu-id="02e1f-312">Обратите внимание, что служба немедленно возвращает управление.</span><span class="sxs-lookup"><span data-stu-id="02e1f-312">Note that the service returns immediately.</span></span> <span data-ttu-id="02e1f-313">После отправки непрерывного запроса приложение может получить запись службы с помощью интерфейса API *nx_mdns_service_lookup*.</span><span class="sxs-lookup"><span data-stu-id="02e1f-313">After issuing a continuous query, the application may retrieve service record by using the API *nx_mdns_service_lookup*.</span></span> <span data-ttu-id="02e1f-314">Чтобы остановить выполнение непрерывного запроса, приложение может использовать интерфейс API *nx_mdns_service_query_stop*.</span><span class="sxs-lookup"><span data-stu-id="02e1f-314">To stop the continuous query, the application may use the API *nx_mdns_service_query_stop*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-315">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-315">Input Parameters</span></span>

- <span data-ttu-id="02e1f-316">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-316">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="02e1f-317">**instance**: указатель на имя экземпляра службы, если применимо</span><span class="sxs-lookup"><span data-stu-id="02e1f-317">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="02e1f-318">**service**: указатель на тип службы mDNS без сведений о подтипе, если применимо</span><span class="sxs-lookup"><span data-stu-id="02e1f-318">**service** Pointer to the mDNS service type, excluding subtype information, if applicable.</span></span>
- <span data-ttu-id="02e1f-319">**subtype**: указатель на подтип службы mDNS, если применимо</span><span class="sxs-lookup"><span data-stu-id="02e1f-319">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-320">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-320">Return Values</span></span>

- <span data-ttu-id="02e1f-321">**NX_SUCCESS** (0x00) — непрерывный запрос успешно запущен.</span><span class="sxs-lookup"><span data-stu-id="02e1f-321">**NX_SUCCESS** (0x00) Successfully started continues query.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-322">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-322">Allowed From</span></span>

<span data-ttu-id="02e1f-323">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-323">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-324">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-324">Example</span></span>

```C
/* Start service continuous query. */

status = nx_mdns_service_continuous_query(&my_mdns,
    “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was added.
    And the query will be periodically sent. */
```

## <a name="nx_mdns_service_query_stop"></a><span data-ttu-id="02e1f-325">nx_mdns_service_query_stop</span><span class="sxs-lookup"><span data-stu-id="02e1f-325">nx_mdns_service_query_stop</span></span>

<span data-ttu-id="02e1f-326">Прекращение ранее запущенного непрерывного обнаружения службы</span><span class="sxs-lookup"><span data-stu-id="02e1f-326">Cease a previously issued continuous service discovery</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-327">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-327">Prototype</span></span>

```C
UINT nx_mdns_service_query_stop(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a><span data-ttu-id="02e1f-328">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-328">Description</span></span>

<span data-ttu-id="02e1f-329">Этот интерфейс API прекращает ранее запущенное непрерывное обнаружение службы.</span><span class="sxs-lookup"><span data-stu-id="02e1f-329">This API terminates a previous issued continuous service discovery.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-330">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-330">Input Parameters</span></span>

- <span data-ttu-id="02e1f-331">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-331">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="02e1f-332">**instance**: указатель на имя экземпляра службы</span><span class="sxs-lookup"><span data-stu-id="02e1f-332">**instance** Pointer to the instance name of the service.</span></span>
- <span data-ttu-id="02e1f-333">**service**: указатель на тип службы mDNS со сведениями о подтипе</span><span class="sxs-lookup"><span data-stu-id="02e1f-333">**service** Pointer to the mDNS service type, subtype information.</span></span>
- <span data-ttu-id="02e1f-334">**subtype**: указатель на подтип службы mDNS, если применимо</span><span class="sxs-lookup"><span data-stu-id="02e1f-334">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-335">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-335">Return Values</span></span>

- <span data-ttu-id="02e1f-336">**NX_SUCCESS** (0x00) — непрерывный запрос успешно остановлен.</span><span class="sxs-lookup"><span data-stu-id="02e1f-336">**NX_SUCCESS** (0x00) Successfully stopped continues query.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-337">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-337">Allowed From</span></span>

<span data-ttu-id="02e1f-338">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-338">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-339">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-339">Example</span></span>

```C
/* Stop service continuous query. */

status = nx_mdns_service_query_stop(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was stopped. */
```

## <a name="nx_mdns_service_lookup"></a><span data-ttu-id="02e1f-340">nx_mdns_service_lookup</span><span class="sxs-lookup"><span data-stu-id="02e1f-340">nx_mdns_service_lookup</span></span>

<span data-ttu-id="02e1f-341">Получение службы из локального однорангового кэша служб</span><span class="sxs-lookup"><span data-stu-id="02e1f-341">Retrieves the service from the local peer service cache</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-342">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-342">Prototype</span></span>

```C
UINT nx_mdns_service_lookup(NXD_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype, UINT instance_index,
    NXD_MDNS_SERVICE *service_ptr);
```

### <a name="description"></a><span data-ttu-id="02e1f-343">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-343">Description</span></span>

<span data-ttu-id="02e1f-344">Эта служба ищет службы по имени экземпляра (если оно указано) и типу службы в локальном одноранговом кэше служб.</span><span class="sxs-lookup"><span data-stu-id="02e1f-344">This service looks up services matching the instance name (if provided) and the type of service in the local peer service cache.</span></span> <span data-ttu-id="02e1f-345">Чтобы найти первую службу в кэше, которая соответствует описанию, приложение должно запустить поиск с нулевым значением *instance_index*.</span><span class="sxs-lookup"><span data-stu-id="02e1f-345">Application shall start the service lookup with *instance_index* set to zero for the first service in the cache that matches the description.</span></span> <span data-ttu-id="02e1f-346">Далее приложение должно увеличивать значение *instance_index*, чтобы найти дополнительные службы в кэше, пока служба не вернет *NX_NO_MORE_ENTRIES*, что указывает на конец кэша.</span><span class="sxs-lookup"><span data-stu-id="02e1f-346">Application shall keep using this service with increasing *instance_index* value for additional services found in the cache, till the service returns *NX_NO_MORE_ENTRIES*, which indicates the end of the cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-347">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-347">Input Parameters</span></span>

- <span data-ttu-id="02e1f-348">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-348">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="02e1f-349">**instance**: указатель на имя экземпляра службы, если применимо</span><span class="sxs-lookup"><span data-stu-id="02e1f-349">**instance** Pointer to the instance name of the service, if applicable.</span></span>
- <span data-ttu-id="02e1f-350">**service**: указатель на тип службы mDNS без сведений о подтипе, если применимо</span><span class="sxs-lookup"><span data-stu-id="02e1f-350">**service** Pointer to the mDNS service type, excluding subtype information, if applicable.</span></span>
- <span data-ttu-id="02e1f-351">**subtype**: указатель на подтип службы mDNS, если применимо</span><span class="sxs-lookup"><span data-stu-id="02e1f-351">**subtype** Pointer to the subtype portion of the mDNS service, if applicable.</span></span>
- <span data-ttu-id="02e1f-352">**Instance_index**: номер индекса возвращаемого экземпляра</span><span class="sxs-lookup"><span data-stu-id="02e1f-352">**Instance_index** Index number to the instance to be returned.</span></span>
- <span data-ttu-id="02e1f-353">**service_ptr**: предоставляемый пользователем указатель на структуру NX_MDNS_SERVICE, в которой хранятся результаты поиска</span><span class="sxs-lookup"><span data-stu-id="02e1f-353">**service_ptr** User provided pointer to NX_MDNS_SERVICE structure that stores the lookup results.</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-354">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-354">Return Values</span></span>

- <span data-ttu-id="02e1f-355">**NX_SUCCESS** (0x00) — служба успешно получена.</span><span class="sxs-lookup"><span data-stu-id="02e1f-355">**NX_SUCCESS** (0x00) Successfully retrieved the service</span></span>
- <span data-ttu-id="02e1f-356">**NX_NO_MORE_ENTRIES** (0x17) — запись службы по указанному номеру индекса не найдена.</span><span class="sxs-lookup"><span data-stu-id="02e1f-356">**NX_NO_MORE_ENTRIES** (0x17) No service entry is found at the specified index number.</span></span> <span data-ttu-id="02e1f-357">Этот код ошибки указывает на конец поиска.</span><span class="sxs-lookup"><span data-stu-id="02e1f-357">This error code indicates the end of the search.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-358">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-358">Allowed From</span></span>

<span data-ttu-id="02e1f-359">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-359">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-360">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-360">Example</span></span>

```C
/* Lookup the service on specific index. */

status = nx_mdns_service_lookup(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL,
    0, service_ptr);

/* If status is NX_SUCCESS, The service with
    name: NetX-SERVICE._http._tcp.local, was retrieved. */
```

## <a name="nx_mdns_service_ignore_set"></a><span data-ttu-id="02e1f-361">nx_mdns_service_ignore_set</span><span class="sxs-lookup"><span data-stu-id="02e1f-361">nx_mdns_service_ignore_set</span></span>

<span data-ttu-id="02e1f-362">Настройка набора пропускаемых служб</span><span class="sxs-lookup"><span data-stu-id="02e1f-362">Configures a service ignore set</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-363">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-363">Prototype</span></span>

```C
UINT nx_mdns_service_ignore_set(NX_MDNS *mdns_ptr, ULONG service_mask);
```

### <a name="description"></a><span data-ttu-id="02e1f-364">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-364">Description</span></span>

<span data-ttu-id="02e1f-365">Этот интерфейс API настраивает пропуск служб, заданных битовой маской *service_mask*.</span><span class="sxs-lookup"><span data-stu-id="02e1f-365">This API configures a mask to ignore services specified by the *service_mask* bitmask.</span></span> <span data-ttu-id="02e1f-366">Пользователь может при необходимости использовать service_mask для выбора типов служб, которые не требуется кэшировать.</span><span class="sxs-lookup"><span data-stu-id="02e1f-366">User may optionally use the service_mask to select service types it does not wish to be cached.</span></span> <span data-ttu-id="02e1f-367">Список служб определяется в таблице *nx_mdns_service_types* в файле *nxd_mdns.c*.</span><span class="sxs-lookup"><span data-stu-id="02e1f-367">A list of services is defined in the table *nx_mdns_service_types* in *nxd_mdns.c.*</span></span> <span data-ttu-id="02e1f-368">Соответствующая маска первого типа службы в nx_mdns_service_types[] — 0x00000001, маска второго типа службы — 0x00000002 и т. д.</span><span class="sxs-lookup"><span data-stu-id="02e1f-368">The corresponding mask of the first service type in nx_mdns_service_types[] is 0x00000001, the mask of the second service type is 0x00000002, and so on.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-369">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-369">Input Parameters</span></span>

- <span data-ttu-id="02e1f-370">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-370">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="02e1f-371">**service_mask**: определяемые пользователем типы пропускаемых служб.</span><span class="sxs-lookup"><span data-stu-id="02e1f-371">**service_mask** User-defined service types to ignore.</span></span> <span data-ttu-id="02e1f-372">Маска представляет собой 32-разрядный тип ULONG.</span><span class="sxs-lookup"><span data-stu-id="02e1f-372">The mask is a 32-bit ULONG type.</span></span> <span data-ttu-id="02e1f-373">Каждый бит представляет запись в определяемом пользователем массиве *nx_mdns_service_types*.</span><span class="sxs-lookup"><span data-stu-id="02e1f-373">Each bit represents an entry in the user-defined *nx_mdns_service_types* array.</span></span> <span data-ttu-id="02e1f-374">Если задан бит, соответствующий тип службы в массиве *nx_mdns_service_type* не будет сохраняться в одноранговом кэше служб.</span><span class="sxs-lookup"><span data-stu-id="02e1f-374">If a bit is set, the corresponding service type specified in the *nx_mdns_service_type* array will not store in the peer service cache.</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-375">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-375">Return Values</span></span>

- <span data-ttu-id="02e1f-376">**NX_SUCCESS** (0x00) — маска пропуска служб успешно задана.</span><span class="sxs-lookup"><span data-stu-id="02e1f-376">**NX_SUCCESS** (0x00) Successfully sets the service ignore mask.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-377">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-377">Allowed From</span></span>

<span data-ttu-id="02e1f-378">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-378">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-379">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-379">Example</span></span>

```C
/* Set the service mask to ignore the specified service. */

status = nx_mdns_service_ignore_set(&my_mdns, 0x00000003);

/* If status is NX_SUCCESS, The service with
    type “_device-info” and “_http” will be ignored. */
```

## <a name="nx_mdns_service_notify_set"></a><span data-ttu-id="02e1f-380">nx_mdns_service_notify_set</span><span class="sxs-lookup"><span data-stu-id="02e1f-380">nx_mdns_service_notify_set</span></span>

<span data-ttu-id="02e1f-381">Настройка функции обратного вызова для уведомления об изменении службы</span><span class="sxs-lookup"><span data-stu-id="02e1f-381">Configures a service change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-382">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-382">Prototype</span></span>

```C
UINT nx_mdns_service_notify_set(NX_MDNS *mdns_ptr, ULONG service_mask,
    VOID (*service_change_notify)(NX_MDNS *mdns_ptr,
    NX_MDNS_SERVICE *service_ptr, UINT state));
```

### <a name="description"></a><span data-ttu-id="02e1f-383">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-383">Description</span></span>

<span data-ttu-id="02e1f-384">Этот интерфейс API настраивает функцию обратного вызова для уведомления об изменении службы.</span><span class="sxs-lookup"><span data-stu-id="02e1f-384">This API configures a service change notify callback function.</span></span> <span data-ttu-id="02e1f-385">Эта функция обратного вызова вызывается, когда служба, предлагаемая другими узлами в сети, добавляется, изменяется или перестает быть доступной.</span><span class="sxs-lookup"><span data-stu-id="02e1f-385">This callback function is invoked when a service offered by other nodes on the network is added, changed or is no longer available.</span></span> <span data-ttu-id="02e1f-386">Пользователь может при необходимости использовать service_mask для выбора типов отслеживаемых служб.</span><span class="sxs-lookup"><span data-stu-id="02e1f-386">User may optionally use the service_mask to select service types it wishes to monitor.</span></span> <span data-ttu-id="02e1f-387">Список отслеживаемых служб жестко задан в таблице *nx_mdns_service_types* в файле *nxd_mdns.c*.</span><span class="sxs-lookup"><span data-stu-id="02e1f-387">A list of services being monitored are hard-coded in the table *nx_mdns_service_types* in *nxd_mdns.c.*</span></span>

<span data-ttu-id="02e1f-388">Соответствующая маска первого типа службы в nx_mdns_service_types[] — 0x00000001, маска второго типа службы — 0x00000002 и т. д.</span><span class="sxs-lookup"><span data-stu-id="02e1f-388">The corresponding mask of the first service type in nx_mdns_service_types[] is 0x00000001, the mask of the second service type is 0x00000002, and so on.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-389">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-389">Input Parameters</span></span>

- <span data-ttu-id="02e1f-390">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-390">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="02e1f-391">**service_mask**: определяемые пользователем типы отслеживаемых служб</span><span class="sxs-lookup"><span data-stu-id="02e1f-391">**service_mask** User-defined service types to monitor.</span></span> <span data-ttu-id="02e1f-392">Маска представляет собой 32-разрядный тип ULONG.</span><span class="sxs-lookup"><span data-stu-id="02e1f-392">The mask is a 32-bit ULONG type.</span></span> <span data-ttu-id="02e1f-393">Каждый бит представляет запись в массиве *nx_mdns_service_types*.</span><span class="sxs-lookup"><span data-stu-id="02e1f-393">Each bit represents an entry in the *nx_mdns_service_types* array.</span></span>
- <span data-ttu-id="02e1f-394">**service_change_notify**: функция обратного вызова, вызываемая при изменении указанной службы</span><span class="sxs-lookup"><span data-stu-id="02e1f-394">**service_change_notify** The callback function to be invoked when the specified service is changed.</span></span> <span data-ttu-id="02e1f-395">Подробные сведения о службе возвращаются в области памяти, на которую указывает *service_ptr*.</span><span class="sxs-lookup"><span data-stu-id="02e1f-395">The detailed service information is returned in the memory pointed to by *service_ptr.*</span></span> <span data-ttu-id="02e1f-396">Обратите внимание, что после возврата управления функцией обратного вызова содержимое в памяти становится недействительным.</span><span class="sxs-lookup"><span data-stu-id="02e1f-396">Note that the content in the memory is invalid after returning from the notify callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-397">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-397">Return Values</span></span>

- <span data-ttu-id="02e1f-398">**NX_SUCCESS** (0x00) — функция обратного вызова успешно установлена.</span><span class="sxs-lookup"><span data-stu-id="02e1f-398">**NX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-399">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-399">Allowed From</span></span>

<span data-ttu-id="02e1f-400">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-400">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-401">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-401">Example</span></span>

```C
/* Set the service mask to notify the specified service. */

status = nx_mdns_service_notify_set(&my_mdns, 0x00000002, service_change_notify);

/* If status is NX_SUCCESS, the callback will be called
    if received the service with type “_http”. */
```

## <a name="nx_mdns_service_notify_clear"></a><span data-ttu-id="02e1f-402">nx_mdns_service_notify_clear</span><span class="sxs-lookup"><span data-stu-id="02e1f-402">nx_mdns_service_notify_clear</span></span>

<span data-ttu-id="02e1f-403">Очистка функции обратного вызова для уведомления об изменении службы</span><span class="sxs-lookup"><span data-stu-id="02e1f-403">Clear the service change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-404">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-404">Prototype</span></span>

```C
UINT nx_mdns_service_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="02e1f-405">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-405">Description</span></span>

<span data-ttu-id="02e1f-406">Этот интерфейс API очищает функцию обратного вызова для уведомления об изменении службы.</span><span class="sxs-lookup"><span data-stu-id="02e1f-406">This API clears the service change notify callback function and the .</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-407">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-407">Input Parameters</span></span>

- <span data-ttu-id="02e1f-408">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-408">**mdns_ptr** Pointer to mDNS control block..</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-409">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-409">Return Values</span></span>

- <span data-ttu-id="02e1f-410">**NX_SUCCESS** (0x00) — функция обратного вызова успешно очищена.</span><span class="sxs-lookup"><span data-stu-id="02e1f-410">**NX_SUCCESS** (0x00) Successfully cleared the callback function.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-411">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-411">Allowed From</span></span>

<span data-ttu-id="02e1f-412">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-412">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-413">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-413">Example</span></span>

```C
/* Clear the service notify. */

status = nx_mdns_service_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, the service notify function clear. */
```

## <a name="nx_mdns_host_address_get"></a><span data-ttu-id="02e1f-414">nx_mdns_host_address_get</span><span class="sxs-lookup"><span data-stu-id="02e1f-414">nx_mdns_host_address_get</span></span>

<span data-ttu-id="02e1f-415">Получение адреса узла</span><span class="sxs-lookup"><span data-stu-id="02e1f-415">Get the host address</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-416">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-416">Prototype</span></span>

```C
UINT nx_mdns_host_address_get(NX_MDNS *mdns_ptr,
    UCHAR *host_name, ULONG *ipv4_address,
    ULONG *ipv6_address, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="02e1f-417">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-417">Description</span></span>

<span data-ttu-id="02e1f-418">Эта служба выполняет запрос mDNS к IPv4- и IPv6-адресам узла.</span><span class="sxs-lookup"><span data-stu-id="02e1f-418">This service performs a mDNS query on host IPv4 and IPv6 addresses.</span></span> <span data-ttu-id="02e1f-419">Если адрес, связанный с указанным именем узла, найден в одноранговом кэше служб, он возвращается.</span><span class="sxs-lookup"><span data-stu-id="02e1f-419">If the address of specified host name is found in peer service cache, the address is returned.</span></span> <span data-ttu-id="02e1f-420">В противном случае модуль MDN отправляет запросы типа A и AAAA и ожидает ответа.</span><span class="sxs-lookup"><span data-stu-id="02e1f-420">If no address is found in the peer service cache, the mDNS module issues A and AAAA type queries and wait for response.</span></span> <span data-ttu-id="02e1f-421">Этот интерфейс API блокируется до получения ответа либо до истечения времени ожидания запроса.</span><span class="sxs-lookup"><span data-stu-id="02e1f-421">This API blocks until either an answer is received or the query times out.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-422">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-422">Input Parameters</span></span>

- <span data-ttu-id="02e1f-423">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-423">**mdns_ptr** Pointer to mDNS control block.</span></span>
- <span data-ttu-id="02e1f-424">**host_name**: указатель на имя узла</span><span class="sxs-lookup"><span data-stu-id="02e1f-424">**host_name** Pointer to host name.</span></span>
- <span data-ttu-id="02e1f-425">**ipv4_address**: указатель на пространство хранения IPv4-адреса, выровненное по границе 4 байт.</span><span class="sxs-lookup"><span data-stu-id="02e1f-425">**ipv4_address** Pointer to a 4-byte aligned address for IPv4 address storage space.</span></span> <span data-ttu-id="02e1f-426">Пользователь должен выделить 4 байт пространства для IPv4-адреса.</span><span class="sxs-lookup"><span data-stu-id="02e1f-426">User shall allocate 4 bytes of space for the IPv4 - address.</span></span> <span data-ttu-id="02e1f-427">Если приложению не требуется получать IPv4-адрес, в этот интерфейс API можно передать адрес NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="02e1f-427">NX_NULL address can be passed into this API if application does not need to retrieve IPv4 address.</span></span>
- <span data-ttu-id="02e1f-428">**ipv6_address**: указатель на пространство хранения IPv6-адреса, выровненное по границе 4 байт.</span><span class="sxs-lookup"><span data-stu-id="02e1f-428">**ipv6_address** Pointer to the 4-byte aligned address for IPv6 address storage space.</span></span> <span data-ttu-id="02e1f-429">Пользователь должен выделить 16 байт пространства для IPv6-адреса.</span><span class="sxs-lookup"><span data-stu-id="02e1f-429">User shall allocate 16 bytes of space for the - IPv6 address.</span></span> <span data-ttu-id="02e1f-430">Если приложению не требуется получать IPv6-адрес, в этот интерфейс API можно передать адрес NX_NULL.</span><span class="sxs-lookup"><span data-stu-id="02e1f-430">NX_NULL address can be passed into this API if application does not need to retrieve IPv6 address.</span></span>
- <span data-ttu-id="02e1f-431">**wait_option**: время ожидания ответа в тактах</span><span class="sxs-lookup"><span data-stu-id="02e1f-431">**wait_option** The amount of time, in ticks, to wait for a response.</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-432">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-432">Return Values</span></span>

- <span data-ttu-id="02e1f-433">**NX_SUCCESS** (0x00) — адрес узла успешно получен.</span><span class="sxs-lookup"><span data-stu-id="02e1f-433">**NX_SUCCESS** (0x00) Successfully obtained host address.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-434">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-434">Allowed From</span></span>

<span data-ttu-id="02e1f-435">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-435">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-436">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-436">Example</span></span>

```C
ULONG ipv4_address;
ULONG ipv6_address[4];

/* Get the IP address of specified host. */
status = nx_mdns_host_address_get(&my_mdns, “MDNS-Host”, &ipv4_address, ipv6_address, 500);

/* If status is NX_SUCCESS, the IP address of specified host was retrieved. */
```

## <a name="nx_mdns_local_cache_clear"></a><span data-ttu-id="02e1f-437">nx_mdns_local_cache_clear</span><span class="sxs-lookup"><span data-stu-id="02e1f-437">nx_mdns_local_cache_clear</span></span>

<span data-ttu-id="02e1f-438">Удаление всех локальных служб</span><span class="sxs-lookup"><span data-stu-id="02e1f-438">Erase all local services</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-439">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-439">Prototype</span></span>

```C
UINT nx_mdns_local_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="02e1f-440">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-440">Description</span></span>

<span data-ttu-id="02e1f-441">Эта служба очищает все записи в локальном кэше служб после отправки сообщения о завершении.</span><span class="sxs-lookup"><span data-stu-id="02e1f-441">This service clears all entries in the local service cache after send the Goodbye message.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-442">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-442">Input Parameters</span></span>

- <span data-ttu-id="02e1f-443">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-443">**mdns_ptr** Pointer to mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-444">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-444">Return Values</span></span>

- <span data-ttu-id="02e1f-445">**NX_SUCCESS** (0x00) — все записи в кэше успешно очищены.</span><span class="sxs-lookup"><span data-stu-id="02e1f-445">**NX_SUCCESS** (0x00) Successfully erased all entries in the cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-446">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-446">Allowed From</span></span>

<span data-ttu-id="02e1f-447">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-447">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-448">Например, .</span><span class="sxs-lookup"><span data-stu-id="02e1f-448">Example</span></span>

```C
/* Clear the local cache, delete all local service. */

status = nx_mdns_local_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of local cache were deleted. */
```

## <a name="nx_mdns_peer_cache_clear"></a><span data-ttu-id="02e1f-449">nx_mdns_peer_cache_clear</span><span class="sxs-lookup"><span data-stu-id="02e1f-449">nx_mdns_peer_cache_clear</span></span>

<span data-ttu-id="02e1f-450">Удаление всех обнаруженных служб</span><span class="sxs-lookup"><span data-stu-id="02e1f-450">Erase all the discovered services</span></span>

### <a name="prototype"></a><span data-ttu-id="02e1f-451">Прототип</span><span class="sxs-lookup"><span data-stu-id="02e1f-451">Prototype</span></span>

```C
UINT nx_mdns_peer_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a><span data-ttu-id="02e1f-452">Описание</span><span class="sxs-lookup"><span data-stu-id="02e1f-452">Description</span></span>

<span data-ttu-id="02e1f-453">Эта служба очищает все записи в одноранговом кэше служб.</span><span class="sxs-lookup"><span data-stu-id="02e1f-453">This service clears all entries in the peer service cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="02e1f-454">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="02e1f-454">Input Parameters</span></span>

- <span data-ttu-id="02e1f-455">**mdns_ptr**: указатель на блок управления mDNS</span><span class="sxs-lookup"><span data-stu-id="02e1f-455">**mdns_ptr** Pointer to mDNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="02e1f-456">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="02e1f-456">Return Values</span></span>

- <span data-ttu-id="02e1f-457">**NX_SUCCESS** (0x00) — все записи в кэше успешно очищены.</span><span class="sxs-lookup"><span data-stu-id="02e1f-457">**NX_SUCCESS** (0x00) Successfully erased all entries in the cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="02e1f-458">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="02e1f-458">Allowed From</span></span>

<span data-ttu-id="02e1f-459">Потоки</span><span class="sxs-lookup"><span data-stu-id="02e1f-459">Threads</span></span>

### <a name="example"></a><span data-ttu-id="02e1f-460">Пример</span><span class="sxs-lookup"><span data-stu-id="02e1f-460">Example</span></span>

```C
/* Clear the peer cache, delete all peer service. */

status = nx_mdns_peer_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of peer cache were deleted. */
```
