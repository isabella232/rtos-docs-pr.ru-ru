---
title: Глава 4. Описание служб NetX для ОСРВ Azure
description: В этой главе содержится описание всех служб NetX для ОСРВ Azure в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 720e573b53070a754618830134f63a8421b9fd29
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814480"
---
# <a name="chapter-4---description-of-azure-rtos-netx-services"></a><span data-ttu-id="d7262-103">Глава 4. Описание служб NetX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="d7262-103">Chapter 4 - Description of Azure RTOS NetX Services</span></span>

<span data-ttu-id="d7262-104">В этой главе содержится описание всех служб NetX для ОСРВ Azure в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="d7262-104">This chapter contains a description of all Azure RTOS NetX services in alphabetic order.</span></span> <span data-ttu-id="d7262-105">Имена служб реализованы так, что все аналогичные службы группируются вместе.</span><span class="sxs-lookup"><span data-stu-id="d7262-105">Service names are designed so all similar services are grouped together.</span></span> <span data-ttu-id="d7262-106">Например, все службы ARP указаны в начале этой главы.</span><span class="sxs-lookup"><span data-stu-id="d7262-106">For example, all ARP services are found at the beginning of this chapter.</span></span>

> [!NOTE]
> <span data-ttu-id="d7262-107">*Обратите внимание, что сокет API, совместимый с BSD, доступен для устаревшего кода приложения, который не может использовать все преимущества высокопроизводительного API NetX. Дополнительные сведения о сокете API, совместимом с BSD, см. в приложении D*.</span><span class="sxs-lookup"><span data-stu-id="d7262-107">*Note that a BSD-Compatible Socket API is available for legacy application code that cannot take full advantage of the high-performance NetX API. Refer to Appendix D for more information on the BSD-Compatible Socket API.*</span></span>

<span data-ttu-id="d7262-108">В разделе "Возвращаемые значения" каждого описания значения, **выделенные полужирным шрифтом**, не затрагиваются параметром NX_DISABLE_ERROR_CHECKING, используемым для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="d7262-108">In the "Return Values" section of each description, values in **BOLD** are not affected by the NX_DISABLE_ERROR_CHECKING option used to disable the API error checking, while values in non-bold are completely disabled.</span></span> <span data-ttu-id="d7262-109">В разделах "Разрешено из" указывается, откуда можно вызывать каждую службу NetX.</span><span class="sxs-lookup"><span data-stu-id="d7262-109">The "Allowed From" sections indicate from which each NetX service can be called.</span></span>

## <a name="nx_arp_dynamic_entries_invalidate"></a><span data-ttu-id="d7262-110">nx_arp_dynamic_entries_invalidate</span><span class="sxs-lookup"><span data-stu-id="d7262-110">nx_arp_dynamic_entries_invalidate</span></span>

<span data-ttu-id="d7262-111">Делает недействительными все динамические записи в кэше ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-111">Invalidate all dynamic entries in the ARP cache</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-112">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-112">Prototype</span></span>

```C
UINT nx_arp_dynamic_entries_invalidate(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-113">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-113">Description</span></span>

<span data-ttu-id="d7262-114">Эта служба делает недействительными все динамические записи ARP, находящиеся в кэше ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-114">This service invalidates all dynamic ARP entries currently in the ARP cache.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-115">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-115">Parameters</span></span>

- <span data-ttu-id="d7262-116">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-116">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-117">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-117">Return Values</span></span>

- <span data-ttu-id="d7262-118">**NX_SUCCESS** (0x00) — недействительность кэша ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-118">**NX_SUCCESS** (0x00) Successful ARP cache invalidate.</span></span>
- <span data-ttu-id="d7262-119">**NX_NOT_ENABLED** (0x14) — ARP не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-119">**NX_NOT_ENABLED** (0x14) ARP is not enabled.</span></span>
- <span data-ttu-id="d7262-120">**NX_PTR_ERROR** (0x07) — недопустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d7262-120">**NX_PTR_ERROR** (0x07) Invalid IP address.</span></span>
- <span data-ttu-id="d7262-121">**NX_CALLER_ERROR** (0x11) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="d7262-121">**NX_CALLER_ERROR** (0x11) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-122">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-122">Allowed From</span></span>

<span data-ttu-id="d7262-123">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-123">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-124">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-124">Preemption Possible</span></span>

<span data-ttu-id="d7262-125">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-125">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-126">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-126">Example</span></span>

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);
/* If status is NX_SUCCESS the dynamic ARP entries were successfully invalidated. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-127">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-127">See Also</span></span>

- <span data-ttu-id="d7262-128">nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-128">nx_arp_dynamic_entry_set, nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="d7262-129">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-129">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="d7262-130">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="d7262-130">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="d7262-131">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-131">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_dynamic_entry_set"></a><span data-ttu-id="d7262-132">nx_arp_dynamic_entry_set</span><span class="sxs-lookup"><span data-stu-id="d7262-132">nx_arp_dynamic_entry_set</span></span>

<span data-ttu-id="d7262-133">Задание динамической записи ARP</span><span class="sxs-lookup"><span data-stu-id="d7262-133">Set dynamic ARP entry</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-134">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-134">Prototype</span></span>

```C
UINT nx_arp_dynamic_entry_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="d7262-135">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-135">Description</span></span>

<span data-ttu-id="d7262-136">Эта служба выделяет динамическую запись из кэша ARP и устанавливает сопоставление указанного IP-адреса с физическим адресом.</span><span class="sxs-lookup"><span data-stu-id="d7262-136">This service allocates a dynamic entry from the ARP cache and sets up the specified IP to physical address mapping.</span></span> <span data-ttu-id="d7262-137">Если указан нулевой физический адрес, в сеть отправляется фактический запрос ARP, чтобы разрешить физический адрес.</span><span class="sxs-lookup"><span data-stu-id="d7262-137">If a zero physical address is specified, an actual ARP request is sent to the network in order to have the physical address resolved.</span></span> <span data-ttu-id="d7262-138">Также обратите внимание, что эта запись будет удалена, если активно устаревание по протоколу ARP или если кэш ARP исчерпан, а это наименее недавно использованная запись ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-138">Also note that this entry will be removed if ARP aging is active or if the ARP cache is exhausted and this is the least recently used ARP entry.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-139">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-139">Parameters</span></span>

- <span data-ttu-id="d7262-140">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-140">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-141">**ip_address**: IP-адрес для сопоставления</span><span class="sxs-lookup"><span data-stu-id="d7262-141">**ip_address** IP address to map.</span></span>
- <span data-ttu-id="d7262-142">**physical_msw**: старшие 16 бит (47–32) физического адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-142">**physical_msw** Top 16 bits (47-32) of the physical address.</span></span>
- <span data-ttu-id="d7262-143">**physical_msw**: младшие 32 бит (31–0) физического адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-143">**physical_lsw** Lower 32 bits (31-0) of the physical address.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-144">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-144">Return Values</span></span>

- <span data-ttu-id="d7262-145">**NX_SUCCESS** (0x00) — успешный динамический набор записей ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-145">**NX_SUCCESS** (0x00) Successful ARP dynamic entry set.</span></span>
- <span data-ttu-id="d7262-146">**NX_NO_MORE_ENTRIES** (0x17) — в кэше ARP больше нет доступных записей ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-146">**NX_NO_MORE_ENTRIES** (0x17) No more ARP entries are available in the ARP cache.</span></span>
- <span data-ttu-id="d7262-147">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d7262-147">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="d7262-148">**NX_PTR_ERROR** (0x07) — недопустимый указатель на экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-148">**NX_PTR_ERROR** (0x07) Invalid IP instance pointer.</span></span>
- <span data-ttu-id="d7262-149">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-149">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="d7262-150">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-150">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-151">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-151">Allowed From</span></span>

<span data-ttu-id="d7262-152">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-152">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-153">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-153">Preemption Possible</span></span>

<span data-ttu-id="d7262-154">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-154">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-155">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-155">Example</span></span>

```C
/* Setup a dynamic ARP entry on the previously created IP Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
    0x1022, 0x1234);
/* If status is NX_SUCCESS, there is now a dynamic mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    10:22:00:00:12:34. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-156">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-156">See Also</span></span>

- <span data-ttu-id="d7262-157">nx_arp_dynamic_entries_invalidate, nx_arp_enable,</span><span class="sxs-lookup"><span data-stu-id="d7262-157">nx_arp_dynamic_entries_invalidate, nx_arp_enable,</span></span>
- <span data-ttu-id="d7262-158">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span><span class="sxs-lookup"><span data-stu-id="d7262-158">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span></span>
- <span data-ttu-id="d7262-159">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="d7262-159">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="d7262-160">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-160">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_enable"></a><span data-ttu-id="d7262-161">nx_arp_enable</span><span class="sxs-lookup"><span data-stu-id="d7262-161">nx_arp_enable</span></span>

<span data-ttu-id="d7262-162">Включает протокол определения адреса (ARP).</span><span class="sxs-lookup"><span data-stu-id="d7262-162">Enables Address Resolution Protocol (ARP).</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-163">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-163">Prototype</span></span>

```C
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory, 
    ULONG arp_cache_size);
```

### <a name="description"></a><span data-ttu-id="d7262-164">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-164">Description</span></span>

<span data-ttu-id="d7262-165">Эта служба инициализирует компонент ARP определенного экземпляра IP в NetX.</span><span class="sxs-lookup"><span data-stu-id="d7262-165">This service initializes the ARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="d7262-166">Инициализация ARP включает в себя настройку кэша ARP и различные процедуры обработки ARP, необходимые для отправки и получения сообщений ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-166">ARP initialization includes setting up the ARP cache and various ARP processing routines necessary for sending and receiving ARP messages.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-167">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-167">Parameters</span></span>

- <span data-ttu-id="d7262-168">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-168">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-169">**arp_cache_memory**: указатель на область памяти для размещения кэша ARP</span><span class="sxs-lookup"><span data-stu-id="d7262-169">**arp_cache_memory** Pointer to memory area to place ARP cache.</span></span>
- <span data-ttu-id="d7262-170">**arp_cache_size**: каждая запись в ARP состоит из 52 байт, а общее количество записей ARP равно размеру, деленному на 52.</span><span class="sxs-lookup"><span data-stu-id="d7262-170">**arp_cache_size** Each ARP entry is 52 bytes, the total number of ARP entries is, therefore, the size divided by 52.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-171">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-171">Return Values</span></span>

- <span data-ttu-id="d7262-172">**NX_SUCCESS** (0x00) — успешное включение ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-172">**NX_SUCCESS** (0x00) Successful ARP enable.</span></span>
- <span data-ttu-id="d7262-173">**NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель кэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="d7262-173">**NX_PTR_ERROR** (0x07) Invalid IP or cache memory pointer.</span></span>
- <span data-ttu-id="d7262-174">**NX_SIZE_ERROR** (0x09) — размер кэша ARP, указанный пользователем, слишком мал.</span><span class="sxs-lookup"><span data-stu-id="d7262-174">**NX_SIZE_ERROR** (0x09) User supplied ARP cache memory is too small.</span></span>
- <span data-ttu-id="d7262-175">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-175">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-176">**NX_ALREADY_ENABLED** (0x15) — этот компонент уже включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-176">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-177">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-177">Allowed From</span></span>

<span data-ttu-id="d7262-178">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-178">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-179">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-179">Preemption Possible</span></span>

<span data-ttu-id="d7262-180">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-180">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-181">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-181">Example</span></span>

```C
/* Enable ARP and supply 1024 bytes of ARP cache memory for
    previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);
/* If status is NX_SUCCESS, ARP was successfully enabled for this IP instance.*/
```

### <a name="see-also"></a><span data-ttu-id="d7262-182">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-182">See Also</span></span>

- <span data-ttu-id="d7262-183">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-183">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="d7262-184">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span><span class="sxs-lookup"><span data-stu-id="d7262-184">nx_arp_gratuitous_send, nx_arp_hardware_address_find,</span></span>
- <span data-ttu-id="d7262-185">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="d7262-185">nx_arp_info_get, nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="d7262-186">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-186">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_gratuitous_send"></a><span data-ttu-id="d7262-187">nx_arp_gratuitous_send</span><span class="sxs-lookup"><span data-stu-id="d7262-187">nx_arp_gratuitous_send</span></span>

<span data-ttu-id="d7262-188">Отправка необязательного запроса ARP</span><span class="sxs-lookup"><span data-stu-id="d7262-188">Send gratuitous ARP request</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-189">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-189">Prototype</span></span>

```C
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler) (NX_IP *ip_ptr, NX_PACKET *packet_ptr));
```

### <a name="description"></a><span data-ttu-id="d7262-190">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-190">Description</span></span>

<span data-ttu-id="d7262-191">Эта служба использует все физические интерфейсы для передачи невыполненных запросов ARP, если IP-адрес интерфейса является допустимым.</span><span class="sxs-lookup"><span data-stu-id="d7262-191">This service goes through all the physical interfaces to transmit gratuitous ARP requests as long as the interface IP address is valid.</span></span> <span data-ttu-id="d7262-192">При последующем получении ответа ARP вызывается обработчик ответов для обработки ответа на необязательный ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-192">If an ARP response is subsequently received, the supplied response handler is called to process the response to the gratuitous ARP.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-193">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-193">Parameters</span></span>

- <span data-ttu-id="d7262-194">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-194">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-195">**response_handler**: указатель функции обработки ответа</span><span class="sxs-lookup"><span data-stu-id="d7262-195">**response_handler** Pointer to response handling function.</span></span> <span data-ttu-id="d7262-196">Если указано значение NX_NULL, ответы игнорируются.</span><span class="sxs-lookup"><span data-stu-id="d7262-196">If NX_NULL is supplied, responses are ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-197">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-197">Return Values</span></span>

- <span data-ttu-id="d7262-198">**NX_SUCCESS** (0x00) — успешная отправка необязательного запроса ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-198">**NX_SUCCESS** (0x00) Successful gratuitous ARP send.</span></span>
- <span data-ttu-id="d7262-199">**NX_NO_PACKET** (0x01) — нет доступных пакетов.</span><span class="sxs-lookup"><span data-stu-id="d7262-199">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="d7262-200">**NX_NOT_ENABLED** (0x14) — ARP не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-200">**NX_NOT_ENABLED** (0x14) ARP is not enabled.</span></span>
- <span data-ttu-id="d7262-201">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый текущий IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d7262-201">**NX_IP_ADDRESS_ERROR** (0x21) Current IP address is invalid.</span></span>
- <span data-ttu-id="d7262-202">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-202">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-203">**NX_CALLER_ERROR** (0x11) — вызывающий объект не является потоком.</span><span class="sxs-lookup"><span data-stu-id="d7262-203">**NX_CALLER_ERROR** (0x11) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-204">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-204">Allowed From</span></span>

<span data-ttu-id="d7262-205">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-205">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-206">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-206">Preemption Possible</span></span>

<span data-ttu-id="d7262-207">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-207">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-208">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-208">Example</span></span>

```C
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully sent. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-209">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-209">See Also</span></span>

- <span data-ttu-id="d7262-210">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-210">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="d7262-211">nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-211">nx_arp_enable, nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="d7262-212">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="d7262-212">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="d7262-213">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-213">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_hardware_address_find"></a><span data-ttu-id="d7262-214">nx_arp_hardware_address_find</span><span class="sxs-lookup"><span data-stu-id="d7262-214">nx_arp_hardware_address_find</span></span>

<span data-ttu-id="d7262-215">Обнаружение физического аппаратного адреса по IP-адресу</span><span class="sxs-lookup"><span data-stu-id="d7262-215">Locate physical hardware address given an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-216">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-216">Prototype</span></span>

```C
UINT nx_arp_hardware_address_find(
    NX_IP *ip_ptr,
    ULONG ip_address, 
    ULONG *physical_msw, 
    ULONG *physical_lsw);
```

### <a name="description"></a><span data-ttu-id="d7262-217">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-217">Description</span></span>

<span data-ttu-id="d7262-218">Эта служба пытается найти физический адрес оборудования в кэше ARP, связанном с заданным IP-адресом.</span><span class="sxs-lookup"><span data-stu-id="d7262-218">This service attempts to find a physical hardware address in the ARP cache that is associated with the supplied IP address.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-219">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-219">Parameters</span></span>

- <span data-ttu-id="d7262-220">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-220">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-221">**ip_address**: IP-адрес для поиска</span><span class="sxs-lookup"><span data-stu-id="d7262-221">**ip_address** IP address to search for.</span></span>
- <span data-ttu-id="d7262-222">**physical_msw**: указатель переменной для возврата старших 16 бит (47–32) физического адреса</span><span class="sxs-lookup"><span data-stu-id="d7262-222">**physical_msw** Pointer to the variable for returning the top 16 bits (47-32) of the physical address.</span></span>
- <span data-ttu-id="d7262-223">**physical_lsw**: указатель переменной для возврата младших 32 бит (31–0) физического адреса</span><span class="sxs-lookup"><span data-stu-id="d7262-223">**physical_lsw** Pointer to the variable for returning the lower 32 bits (31-0) of the physical address.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-224">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-224">Return Values</span></span>

- <span data-ttu-id="d7262-225">**NX_SUCCESS** (0x00) — успешный поиск адреса оборудования ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-225">**NX_SUCCESS** (0x00) Successful ARP hardware address find.</span></span>
- <span data-ttu-id="d7262-226">**NX_ENTRY_NOT_FOUND** (0x16) — сопоставление не найдено в кэше ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-226">**NX_ENTRY_NOT_FOUND** (0x16) Mapping was not found in the ARP cache.</span></span>
- <span data-ttu-id="d7262-227">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d7262-227">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="d7262-228">**NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель памяти.</span><span class="sxs-lookup"><span data-stu-id="d7262-228">**NX_PTR_ERROR** (0x07) Invalid IP or memory pointer.</span></span>
- <span data-ttu-id="d7262-229">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-229">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-230">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-230">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-231">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-231">Allowed From</span></span>

<span data-ttu-id="d7262-232">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-232">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-233">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-233">Preemption Possible</span></span>

<span data-ttu-id="d7262-234">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-234">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-235">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-235">Example</span></span>

```C
/* Search for the hardware address associated with the IP address of
    1.2.3.4 in the ARP cache of the previously created IP
    Instance 0. */
status = nx_arp_hardware_address_find(
    &ip_0, 
    IP_ADDRESS(1,2,3,4),
    &physical_msw, 
    &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
    physical_lsw contain the hardware address.*/
```

### <a name="see-also"></a><span data-ttu-id="d7262-236">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-236">See Also</span></span>

- <span data-ttu-id="d7262-237">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-237">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="d7262-238">nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-238">nx_arp_enable, nx_arp_gratuitous_send, nx_arp_info_get,</span></span>
- <span data-ttu-id="d7262-239">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="d7262-239">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="d7262-240">nx_arp_static_entry_create, nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-240">nx_arp_static_entry_create, nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_info_get"></a><span data-ttu-id="d7262-241">nx_arp_info_get</span><span class="sxs-lookup"><span data-stu-id="d7262-241">nx_arp_info_get</span></span>

<span data-ttu-id="d7262-242">Получение сведений о действиях ARP</span><span class="sxs-lookup"><span data-stu-id="d7262-242">Retrieve information about ARP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-243">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-243">Prototype</span></span>

```C
UINT nx_arp_info_get(
    NX_IP *ip_ptr,
    ULONG *arp_requests_sent,
    ULONG *arp_requests_received,
    ULONG *arp_responses_sent,
    ULONG *arp_responses_received,
    ULONG *arp_dynamic_entries,
    ULONG *arp_static_entries,
    ULONG *arp_aged_entries,
    ULONG *arp_invalid_messages);
```

### <a name="description"></a><span data-ttu-id="d7262-244">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-244">Description</span></span>

<span data-ttu-id="d7262-245">Эта служба получает сведения о действиях ARP для соответствующего экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-245">This service retrieves information about ARP activities for the associated IP instance.</span></span>

<span data-ttu-id="d7262-246">*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.</span><span class="sxs-lookup"><span data-stu-id="d7262-246">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-247">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-247">Parameters</span></span>

- <span data-ttu-id="d7262-248">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-248">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-249">**arp_requests_sent**: указатель места назначения для общего числа запросов ARP, отправленных из этого экземпляра IP</span><span class="sxs-lookup"><span data-stu-id="d7262-249">**arp_requests_sent** Pointer to destination for the total ARP requests sent from this IP instance.</span></span>
- <span data-ttu-id="d7262-250">**arp_requests_received**: указатель места назначения для общего числа запросов ARP, полученных от сети</span><span class="sxs-lookup"><span data-stu-id="d7262-250">**arp_requests_received** Pointer to destination for the total ARP requests received from the network.</span></span>
- <span data-ttu-id="d7262-251">**arp_responses_sent**: указатель места назначения для общего числа ответов ARP, отправленных из этого экземпляра IP</span><span class="sxs-lookup"><span data-stu-id="d7262-251">**arp_responses_sent** Pointer to destination for the total ARP responses sent from this IP instance.</span></span>
- <span data-ttu-id="d7262-252">**arp_responses_received**: указатель места назначения для общего числа ответов ARP, полученных от сети</span><span class="sxs-lookup"><span data-stu-id="d7262-252">**arp_responses_received** Pointer to the destination for the total ARP responses received from the network.</span></span>
- <span data-ttu-id="d7262-253">**arp_dynamic_entries**: указатель места назначения для текущего числа динамических записей ARP</span><span class="sxs-lookup"><span data-stu-id="d7262-253">**arp_dynamic_entries** Pointer to the destination for the current number of dynamic ARP entries.</span></span>
- <span data-ttu-id="d7262-254">**arp_static_entries**: указатель места назначения для текущего числа статических записей ARP</span><span class="sxs-lookup"><span data-stu-id="d7262-254">**arp_static_entries** Pointer to the destination for the current number of static ARP entries.</span></span>
- <span data-ttu-id="d7262-255">**arp_aged_entries**: указатель места назначения общего числа записей ARP, которые устарели и стали недопустимыми</span><span class="sxs-lookup"><span data-stu-id="d7262-255">**arp_aged_entries** Pointer to the destination of the total number of ARP entries that have aged and became invalid.</span></span>
- <span data-ttu-id="d7262-256">**arp_invalid_messages**: указатель места назначения общего числа полученных недопустимых сообщений ARP</span><span class="sxs-lookup"><span data-stu-id="d7262-256">**arp_invalid_messages** Pointer to the destination of the total invalid ARP messages received.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-257">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-257">Return Values</span></span>

- <span data-ttu-id="d7262-258">**NX_SUCCESS** (0x00) — успешное получение сведений ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-258">**NX_SUCCESS** (0x00) Successful ARP information retrieval.</span></span>
- <span data-ttu-id="d7262-259">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-259">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-260">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-260">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-261">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-261">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-262">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-262">Allowed From</span></span>

<span data-ttu-id="d7262-263">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-263">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-264">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-264">Preemption Possible</span></span>

<span data-ttu-id="d7262-265">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-265">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-266">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-266">Example</span></span>

```C
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(
    &ip_0, 
    &arp_requests_sent,
    &arp_requests_received,
    &arp_responses_sent,
    &arp_responses_received,
    &arp_dynamic_entries,
    &arp_static_entries,
    &arp_aged_entries,
    &arp_invalid_messages);
/* If status is NX_SUCCESS, the ARP information has been stored in
    the supplied variables. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-267">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-267">See Also</span></span>

- <span data-ttu-id="d7262-268">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-268">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="d7262-269">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-269">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="d7262-270">nx_arp_hardware_address_find, nx_arp_ip_address_find,</span><span class="sxs-lookup"><span data-stu-id="d7262-270">nx_arp_hardware_address_find, nx_arp_ip_address_find,</span></span>
- <span data-ttu-id="d7262-271">nx_arp_static_entries_delete, nx_arp_static_entry_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-271">nx_arp_static_entries_delete, nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="d7262-272">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-272">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_ip_address_find"></a><span data-ttu-id="d7262-273">nx_arp_ip_address_find</span><span class="sxs-lookup"><span data-stu-id="d7262-273">nx_arp_ip_address_find</span></span>

<span data-ttu-id="d7262-274">Нахождение IP-адреса по физическому адресу</span><span class="sxs-lookup"><span data-stu-id="d7262-274">Locate IP address given a physical address</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-275">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-275">Prototype</span></span>

```C
UINT nx_arp_ip_address_find(
    NX_IP *ip_ptr, 
    ULONG *ip_address,
    ULONG physical_msw, 
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="d7262-276">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-276">Description</span></span>

<span data-ttu-id="d7262-277">Эта служба пытается найти IP-адрес в кэше ARP, связанном с переданным физическим адресом.</span><span class="sxs-lookup"><span data-stu-id="d7262-277">This service attempts to find an IP address in the ARP cache that is associated with the supplied physical address.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-278">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-278">Parameters</span></span>

- <span data-ttu-id="d7262-279">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-279">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-280">**ip_address**: указатель для возврата IP-адреса, если он найден и сопоставлен</span><span class="sxs-lookup"><span data-stu-id="d7262-280">**ip_address** Pointer to return IP address, if one is found that has been mapped.</span></span>
- <span data-ttu-id="d7262-281">**physical_msw**: старшие 16 бит (47–32) физического адреса для поиска</span><span class="sxs-lookup"><span data-stu-id="d7262-281">**physical_msw** Top 16 bits (47-32) of the physical address to search for.</span></span>
- <span data-ttu-id="d7262-282">**physical_lsw**: младшие 32 бит (31–0) физического адреса для поиска</span><span class="sxs-lookup"><span data-stu-id="d7262-282">**physical_lsw** Lower 32 bits (31-0) of the physical address to search for.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-283">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-283">Return Values</span></span>

- <span data-ttu-id="d7262-284">**NX_SUCCESS** (0x00) — успешный поиск IP-адреса ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-284">**NX_SUCCESS** (0x00) Successful ARP IP address find</span></span>
- <span data-ttu-id="d7262-285">**NX_ENTRY_NOT_FOUND** (0x16) — сопоставление не найдено в кэше ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-285">**NX_ENTRY_NOT_FOUND** (0x16) Mapping was not found in the ARP cache.</span></span>
- <span data-ttu-id="d7262-286">**NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель памяти.</span><span class="sxs-lookup"><span data-stu-id="d7262-286">**NX_PTR_ERROR** (0x07) Invalid IP or memory pointer.</span></span>
- <span data-ttu-id="d7262-287">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-287">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-288">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-288">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="d7262-289">**NX_INVALID_PARAMETERS** (0x4D) — значения physical_msw и physical_lsw равны 0.</span><span class="sxs-lookup"><span data-stu-id="d7262-289">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-290">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-290">Allowed From</span></span>

<span data-ttu-id="d7262-291">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-291">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-292">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-292">Preemption Possible</span></span>

<span data-ttu-id="d7262-293">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-293">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-294">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-294">Example</span></span>

```C
/* Search for the IP address associated with the hardware address of
    0x0:0x01234 in the ARP cache of the previously created IP
    Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
    associated IP address.*/
```

### <a name="see-also"></a><span data-ttu-id="d7262-295">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-295">See Also</span></span>

- <span data-ttu-id="d7262-296">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-296">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="d7262-297">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-297">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="d7262-298">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-298">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="d7262-299">nx_arp_static_entries_delete,nx_arp_static_entry_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-299">nx_arp_static_entries_delete,nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="d7262-300">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-300">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entries_delete"></a><span data-ttu-id="d7262-301">nx_arp_static_entries_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-301">nx_arp_static_entries_delete</span></span>

<span data-ttu-id="d7262-302">Удаление всех статических записей ARP</span><span class="sxs-lookup"><span data-stu-id="d7262-302">Delete all static ARP entries</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-303">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-303">Prototype</span></span>

```C
UINT nx_arp_static_entries_delete(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-304">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-304">Description</span></span>

<span data-ttu-id="d7262-305">Эта служба удаляет все статические записи в кэше ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-305">This service deletes all static entries in the ARP cache.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-306">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-306">Parameters</span></span>

- <span data-ttu-id="d7262-307">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-307">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-308">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-308">Return Values</span></span>

- <span data-ttu-id="d7262-309">**NX_SUCCESS** (0x00) — статические записи удалены.</span><span class="sxs-lookup"><span data-stu-id="d7262-309">**NX_SUCCESS** (0x00) Static entries are deleted.</span></span>
- <span data-ttu-id="d7262-310">**NX_PTR_ERROR** (0x07) — недопустимый указатель ip_ptr.</span><span class="sxs-lookup"><span data-stu-id="d7262-310">**NX_PTR_ERROR** (0x07) Invalid ip_ptr pointer.</span></span>
- <span data-ttu-id="d7262-311">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-311">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-312">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-312">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-313">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-313">Allowed From</span></span>

<span data-ttu-id="d7262-314">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-314">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-315">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-315">Preemption Possible</span></span>

<span data-ttu-id="d7262-316">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-316">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-317">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-317">Example</span></span>

```C
/* Delete all the static ARP entries for IP Instance 0, assuming
    "ip_0" is the NX_IP structure for IP Instance 0. */

status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
have been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-318">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-318">See Also</span></span>

- <span data-ttu-id="d7262-319">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-319">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="d7262-320">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-320">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="d7262-321">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-321">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="d7262-322">nx_arp_ip_address_find, nx_arp_static_entry_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-322">nx_arp_ip_address_find, nx_arp_static_entry_create,</span></span>
- <span data-ttu-id="d7262-323">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-323">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entry_create"></a><span data-ttu-id="d7262-324">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="d7262-324">nx_arp_static_entry_create</span></span>

<span data-ttu-id="d7262-325">Создание статического IP-адреса для аппаратного сопоставления в кэше ARP</span><span class="sxs-lookup"><span data-stu-id="d7262-325">Create static IP to hardware mapping in ARP cache</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-326">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-326">Prototype</span></span>

```C
UINT nx_arp_static_entry_create(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="d7262-327">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-327">Description</span></span>

<span data-ttu-id="d7262-328">Эта служба создает сопоставление статического IP-адреса с физическим в кэше ARP для указанного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-328">This service creates a static IP-to-physical address mapping in the ARP cache for the specified IP instance.</span></span> <span data-ttu-id="d7262-329">На статические записи ARP не распространяются периодические обновления протокола ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-329">Static ARP entries are not subject to ARP periodic updates.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-330">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-330">Parameters</span></span>

- <span data-ttu-id="d7262-331">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-331">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-332">**ip_address**: IP-адрес для сопоставления</span><span class="sxs-lookup"><span data-stu-id="d7262-332">**ip_address** IP address to map.</span></span>
- <span data-ttu-id="d7262-333">**physical_msw**: старшие 16 бит (47–32) физического адреса для сопоставления</span><span class="sxs-lookup"><span data-stu-id="d7262-333">**physical_msw** Top 16 bits (47-32) of the physical address to map.</span></span>
- <span data-ttu-id="d7262-334">**physical_lsw**: младшие 32 бит (31–0) физического адреса для сопоставления</span><span class="sxs-lookup"><span data-stu-id="d7262-334">**physical_lsw** Lower 32 bits (31-0) of the physical address to map.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-335">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-335">Return Values</span></span>

- <span data-ttu-id="d7262-336">**NX_SUCCESS** (0x00) — успешное создание статической записи ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-336">**NX_SUCCESS** (0x00) Successful ARP static entry create.</span></span>
- <span data-ttu-id="d7262-337">**NX_NO_MORE_ENTRIES** (0x17) — в кэше ARP больше нет доступных записей ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-337">**NX_NO_MORE_ENTRIES** (0x17) No more ARP entries are available in the ARP cache.</span></span>
- <span data-ttu-id="d7262-338">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d7262-338">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="d7262-339">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-339">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-340">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-340">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-341">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-341">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="d7262-342">**NX_INVALID_PARAMETERS** (0x4D) — значения physical_msw и physical_lsw равны 0.</span><span class="sxs-lookup"><span data-stu-id="d7262-342">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-343">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-343">Allowed From</span></span>

<span data-ttu-id="d7262-344">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-344">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-345">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-345">Preemption Possible</span></span>

<span data-ttu-id="d7262-346">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-346">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-347">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-347">Example</span></span>

```C
/* Create a static ARP entry on the previously created IP
    Instance 0. */

status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
    the IP address of 1.2.3.4 and the physical hardware address of
    00:00:00:00:12:34. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-348">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-348">See Also</span></span>

- <span data-ttu-id="d7262-349">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-349">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="d7262-350">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-350">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="d7262-351">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-351">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="d7262-352">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="d7262-352">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="d7262-353">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-353">nx_arp_static_entry_delete</span></span>

## <a name="nx_arp_static_entry_delete"></a><span data-ttu-id="d7262-354">nx_arp_static_entry_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-354">nx_arp_static_entry_delete</span></span>

<span data-ttu-id="d7262-355">Удаление статического IP-адреса для сопоставления оборудования в кэше ARP</span><span class="sxs-lookup"><span data-stu-id="d7262-355">Delete static IP to hardware mapping in ARP cache</span></span>


### <a name="prototype"></a><span data-ttu-id="d7262-356">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-356">Prototype</span></span>

```C
UINT nx_arp_static_entry_delete(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```

### <a name="description"></a><span data-ttu-id="d7262-357">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-357">Description</span></span>

<span data-ttu-id="d7262-358">Эта служба находит и удаляет ранее созданное статическое сопоставление IP-адреса с физическим адресом в кэше ARP для указанного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-358">This service finds and deletes a previously created static IP-to-physical address mapping in the ARP cache for the specified IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-359">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-359">Parameters</span></span>

- <span data-ttu-id="d7262-360">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-360">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-361">**ip_address** IP-адрес, который был сопоставлен статически</span><span class="sxs-lookup"><span data-stu-id="d7262-361">**ip_address** IP address that was mapped statically.</span></span>
- <span data-ttu-id="d7262-362">**physical_msw**: старшие 16 бит (47–32) физического адреса, который был сопоставлен статически</span><span class="sxs-lookup"><span data-stu-id="d7262-362">**physical_msw** Top 16 bits (47 - 32) of the physical address that was mapped statically.</span></span>
- <span data-ttu-id="d7262-363">**physical_lsw**: младшие 32 бит (31–0) физического адреса, который был сопоставлен статически</span><span class="sxs-lookup"><span data-stu-id="d7262-363">**physical_lsw** Lower 32 bits (31 - 0) of the physical address that was mapped statically.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-364">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-364">Return Values</span></span>

- <span data-ttu-id="d7262-365">**NX_SUCCESS** (0x00) — успешное удаление статической записи ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-365">**NX_SUCCESS** (0x00) Successful ARP static entry delete.</span></span>
- <span data-ttu-id="d7262-366">**NX_ENTRY_NOT_FOUND** (0x16) — статическая запись ARP не найдена в кэше ARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-366">**NX_ENTRY_NOT_FOUND** (0x16) Static ARP entry was not found in the ARP cache.</span></span>
- <span data-ttu-id="d7262-367">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-367">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-368">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-368">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-369">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-369">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="d7262-370">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d7262-370">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="d7262-371">**NX_INVALID_PARAMETERS** (0x4D) — значения physical_msw и physical_lsw равны 0.</span><span class="sxs-lookup"><span data-stu-id="d7262-371">**NX_INVALID_PARAMETERS** (0x4D) Physical_msw and physical_lsw are both 0.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-372">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-372">Allowed From</span></span>

<span data-ttu-id="d7262-373">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-373">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-374">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-374">Preemption Possible</span></span>

<span data-ttu-id="d7262-375">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-375">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-376">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-376">Example</span></span>

```C
/* Delete a static ARP entry on the previously created IP
    instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
    0x0, 0x1234);
/* If status is NX_SUCCESS, the previously created static ARP entry
    was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-377">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-377">See Also</span></span>

- <span data-ttu-id="d7262-378">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-378">nx_arp_dynamic_entries_invalidate, nx_arp_dynamic_entry_set,</span></span>
- <span data-ttu-id="d7262-379">nx_arp_enable, nx_arp_gratuitous_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-379">nx_arp_enable, nx_arp_gratuitous_send,</span></span>
- <span data-ttu-id="d7262-380">nx_arp_hardware_address_find, nx_arp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-380">nx_arp_hardware_address_find, nx_arp_info_get,</span></span>
- <span data-ttu-id="d7262-381">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span><span class="sxs-lookup"><span data-stu-id="d7262-381">nx_arp_ip_address_find, nx_arp_static_entries_delete,</span></span>
- <span data-ttu-id="d7262-382">nx_arp_static_entry_create</span><span class="sxs-lookup"><span data-stu-id="d7262-382">nx_arp_static_entry_create</span></span>

## <a name="nx_icmp_enable"></a><span data-ttu-id="d7262-383">nx_icmp_enable</span><span class="sxs-lookup"><span data-stu-id="d7262-383">nx_icmp_enable</span></span>

<span data-ttu-id="d7262-384">Включение протокола ICMP</span><span class="sxs-lookup"><span data-stu-id="d7262-384">Enable Internet Control Message Protocol (ICMP)</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-385">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-385">Prototype</span></span>

```C
UINT nx_icmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-386">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-386">Description</span></span>

<span data-ttu-id="d7262-387">Эта служба включает компонент ICMP для указанного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-387">This service enables the ICMP component for the specified IP instance.</span></span>
<span data-ttu-id="d7262-388">Компонент ICMP отвечает за обработку сообщений об ошибках в Интернете, а также запросов и ответов проверки связи.</span><span class="sxs-lookup"><span data-stu-id="d7262-388">The ICMP component is responsible for handling Internet error messages and ping requests and replies.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-389">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-389">Parameters</span></span>

- <span data-ttu-id="d7262-390">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-390">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-391">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-391">Return Values</span></span>

- <span data-ttu-id="d7262-392">**NX_SUCCESS** (0x00) — успешное включение протокола ICMP.</span><span class="sxs-lookup"><span data-stu-id="d7262-392">**NX_SUCCESS** (0x00) Successful ICMP enable.</span></span>
- <span data-ttu-id="d7262-393">**NX_ALREADY_ENABLED** (0x15) — протокол ICMP уже включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-393">**NX_ALREADY_ENABLED** (0x15) ICMP is already enabled.</span></span>
- <span data-ttu-id="d7262-394">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-394">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-395">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-395">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-396">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-396">Allowed From</span></span>

<span data-ttu-id="d7262-397">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-397">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-398">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-398">Preemption Possible</span></span>

<span data-ttu-id="d7262-399">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-399">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-400">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-400">Example</span></span>

```C
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-401">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-401">See Also</span></span>

- <span data-ttu-id="d7262-402">nx_icmp_info_get, nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="d7262-402">nx_icmp_info_get, nx_icmp_ping</span></span>

## <a name="nx_icmp_info_get"></a><span data-ttu-id="d7262-403">nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="d7262-403">nx_icmp_info_get</span></span>

<span data-ttu-id="d7262-404">Получение сведений о действиях ICMP</span><span class="sxs-lookup"><span data-stu-id="d7262-404">Retrieve information about ICMP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-405">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-405">Prototype</span></span>

```C
UINT nx_icmp_info_get(
    NX_IP *ip_ptr,
    ULONG *pings_sent,
    ULONG *ping_timeouts,
    ULONG *ping_threads_suspended,
    ULONG *ping_responses_received,
    ULONG *icmp_checksum_errors,
    ULONG *icmp_unhandled_messages);
```

### <a name="description"></a><span data-ttu-id="d7262-406">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-406">Description</span></span>

<span data-ttu-id="d7262-407">Эта служба получает сведения о действиях протокола ICMP для указанного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-407">This service retrieves information about ICMP activities for the specified IP instance.</span></span>

<span data-ttu-id="d7262-408">*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.</span><span class="sxs-lookup"><span data-stu-id="d7262-408">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-409">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-409">Parameters</span></span>

- <span data-ttu-id="d7262-410">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-410">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-411">**pings_sent**: указатель места назначения для общего числа отправленных проверок связи.</span><span class="sxs-lookup"><span data-stu-id="d7262-411">**pings_sent** Pointer to destination for the total number of pings sent.</span></span>
- <span data-ttu-id="d7262-412">**ping_timeouts**: указатель места назначения для общего числа таймаутов проверки связи.</span><span class="sxs-lookup"><span data-stu-id="d7262-412">**ping_timeouts** Pointer to destination for the total number of ping timeouts.</span></span>
- <span data-ttu-id="d7262-413">**ping_threads_suspended**: указатель места назначения общего числа потоков, приостановленных по запросам проверки связи.</span><span class="sxs-lookup"><span data-stu-id="d7262-413">**ping_threads_suspended** Pointer to destination of the total number of threads suspended on ping requests.</span></span>
- <span data-ttu-id="d7262-414">**ping_responses_received**: указатель места назначения общего числа полученных ответов проверки связи.</span><span class="sxs-lookup"><span data-stu-id="d7262-414">**ping_responses_received** Pointer to estination of the total number of ping responses received.</span></span>
- <span data-ttu-id="d7262-415">**icmp_checksum_errors**: указатель места назначения общего числа ошибок контрольной суммы протокола ICMP.</span><span class="sxs-lookup"><span data-stu-id="d7262-415">**icmp_checksum_errors** Pointer to destination of the total number of ICMP checksum errors.</span></span>
- <span data-ttu-id="d7262-416">**icmp_unhandled_messages**: указатель места назначения общего числа необработанных сообщений ICMP.</span><span class="sxs-lookup"><span data-stu-id="d7262-416">**icmp_unhandled_messages** Pointer to estination of the total number of un-handled ICMP messages.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-417">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-417">Return Values</span></span>

- <span data-ttu-id="d7262-418">**NX_SUCCESS** (0x00) — успешное получение сведений ICMP.</span><span class="sxs-lookup"><span data-stu-id="d7262-418">**NX_SUCCESS** (0x00) Successful ICMP information retrieval.</span></span>
- <span data-ttu-id="d7262-419">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-419">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-420">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-420">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-421">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-421">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-422">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-422">Allowed From</span></span>

<span data-ttu-id="d7262-423">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-423">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-424">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-424">Preemption Possible</span></span>

<span data-ttu-id="d7262-425">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-425">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-426">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-426">Example</span></span>

```C
/* Retrieve ICMP information from previously created IP
    instance ip_0. */
status = nx_icmp_info_get(
    &ip_0, 
    &pings_sent, 
    &ping_timeouts,
    &ping_threads_suspended,
    &ping_responses_received,
    &icmp_checksum_errors,
    &icmp_unhandled_messages);

/* If status is NX_SUCCESS, ICMP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-427">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-427">See Also</span></span>

- <span data-ttu-id="d7262-428">nx_icmp_enable, nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="d7262-428">nx_icmp_enable, nx_icmp_ping</span></span>

## <a name="nx_icmp_ping"></a><span data-ttu-id="d7262-429">nx_icmp_ping</span><span class="sxs-lookup"><span data-stu-id="d7262-429">nx_icmp_ping</span></span>

<span data-ttu-id="d7262-430">Отправка запроса проверки связи на указанный IP-адрес</span><span class="sxs-lookup"><span data-stu-id="d7262-430">Send ping request to specified IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-431">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-431">Prototype</span></span>

```C
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d7262-432">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-432">Description</span></span>

<span data-ttu-id="d7262-433">Эта служба отправляет запрос проверки связи по указанному IP-адресу и ожидает сообщение ответа проверки связи в течение заданного количества времени.</span><span class="sxs-lookup"><span data-stu-id="d7262-433">This service sends a ping request to the specified IP address and waits for the specified amount of time for a ping response message.</span></span> <span data-ttu-id="d7262-434">Если ответ не получен, возвращается ошибка.</span><span class="sxs-lookup"><span data-stu-id="d7262-434">If no response is received, an error is returned.</span></span> <span data-ttu-id="d7262-435">В противном случае в переменной, на которую указывает response_ptr, возвращается полное ответное сообщение.</span><span class="sxs-lookup"><span data-stu-id="d7262-435">Otherwise, the entire response message is returned in the variable pointed to by response_ptr.</span></span>

<span data-ttu-id="d7262-436">*Если возвращается NX_SUCCESS, приложение отвечает за освобождение полученного пакета после того, как он больше не нужен*.</span><span class="sxs-lookup"><span data-stu-id="d7262-436">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet after it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-437">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-437">Parameters</span></span>

- <span data-ttu-id="d7262-438">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-438">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-439">**ip_address**: IP-адрес в порядке байтов узла для проверки связи</span><span class="sxs-lookup"><span data-stu-id="d7262-439">**ip_address** IP address, in host byte order, to ping.</span></span> <span data-ttu-id="d7262-440">data: указатель области данных для сообщения проверки связи</span><span class="sxs-lookup"><span data-stu-id="d7262-440">data Pointer to data area for ping message.</span></span>
- <span data-ttu-id="d7262-441">**data_size**: число байтов в данных проверки связи</span><span class="sxs-lookup"><span data-stu-id="d7262-441">**data_size** Number of bytes in the ping data</span></span>
- <span data-ttu-id="d7262-442">**response_ptr**: указатель на указатель пакета, в котором нужно вернуть ответное сообщение проверки связи</span><span class="sxs-lookup"><span data-stu-id="d7262-442">**response_ptr** Pointer to packet pointer to return the ping response message in.</span></span>
- <span data-ttu-id="d7262-443">**wait_option** определяет время ожидания ответа проверки связи</span><span class="sxs-lookup"><span data-stu-id="d7262-443">**wait_option** Defines how long to wait for a ping response.</span></span> <span data-ttu-id="d7262-444">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d7262-444">wait options are defined as follows:</span></span>

  - <span data-ttu-id="d7262-445">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-445">NX_NO_WAIT (0x00000000)</span></span>
  - <span data-ttu-id="d7262-446">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-446">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
  - <span data-ttu-id="d7262-447">Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d7262-447">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-448">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-448">Return Values</span></span>

- <span data-ttu-id="d7262-449">**NX_SUCCESS** (0x00) — успешная проверка связи.</span><span class="sxs-lookup"><span data-stu-id="d7262-449">**NX_SUCCESS** (0x00) Successful ping.</span></span> <span data-ttu-id="d7262-450">Указатель сообщения ответа был помещен в переменную, на которую указывает response_ptr.</span><span class="sxs-lookup"><span data-stu-id="d7262-450">Response message pointer was placed in the variable pointed to by response_ptr.</span></span>
- <span data-ttu-id="d7262-451">**NX_NO_PACKET** (0x01) — не удалось выделить пакет запроса проверки связи.</span><span class="sxs-lookup"><span data-stu-id="d7262-451">**NX_NO_PACKET** (0x01) Unable to allocate a ping request packet.</span></span>
- <span data-ttu-id="d7262-452">**NX_OVERFLOW** (0x03) — заданная область данных превышает размер пакета по умолчанию для этого экземпляра IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-452">**NX_OVERFLOW** (0x03) Specified data area exceeds the default packet size for this IP instance.</span></span>
- <span data-ttu-id="d7262-453">**NX_NO_RESPONSE** (0x29) — запрошенный IP-адрес не ответил.</span><span class="sxs-lookup"><span data-stu-id="d7262-453">**NX_NO_RESPONSE** (0x29) Requested IP did not respond.</span></span>
- <span data-ttu-id="d7262-454">**NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="d7262-454">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="d7262-455">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d7262-455">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="d7262-456">**NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель ответа.</span><span class="sxs-lookup"><span data-stu-id="d7262-456">**NX_PTR_ERROR** (0x07) Invalid IP or response pointer.</span></span>
- <span data-ttu-id="d7262-457">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-457">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-458">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-458">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-459">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-459">Allowed From</span></span>

<span data-ttu-id="d7262-460">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-460">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-461">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-461">Preemption Possible</span></span>

<span data-ttu-id="d7262-462">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-462">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-463">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-463">Example</span></span>

```C
/* Issue a ping to IP address 1.2.3.5 from the previously created IP
    Instance ip_0. */
status = nx_icmp_ping(&ip_0, IP_ADDRESS(1,2,3,5), "abcd", 4,
    &response_ptr, 10);

/* If status is NX_SUCCESS, a ping response was received from IP
    address 1.2.3.5 and the response packet is contained in the
    packet pointed to by response_ptr. It should have the same "abcd"
    four bytes of data. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-464">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-464">See Also</span></span>

- <span data-ttu-id="d7262-465">nx_icmp_enable, nx_icmp_info_get</span><span class="sxs-lookup"><span data-stu-id="d7262-465">nx_icmp_enable, nx_icmp_info_get</span></span>

## <a name="nx_igmp_enable"></a><span data-ttu-id="d7262-466">nx_igmp_enable</span><span class="sxs-lookup"><span data-stu-id="d7262-466">nx_igmp_enable</span></span>

<span data-ttu-id="d7262-467">Включение протокола IGMP</span><span class="sxs-lookup"><span data-stu-id="d7262-467">Enable Internet Group Management Protocol (IGMP)</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-468">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-468">Prototype</span></span>

```C
UINT nx_igmp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-469">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-469">Description</span></span>

<span data-ttu-id="d7262-470">Эта служба включает компонент IGMP для указанного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-470">This service enables the IGMP component on the specified IP instance.</span></span>
<span data-ttu-id="d7262-471">Компонент IGMP отвечает за поддержку операций управления группами многоадресной рассылки IP-адресов.</span><span class="sxs-lookup"><span data-stu-id="d7262-471">The IGMP component is responsible for providing support for IP multicast group management operations.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-472">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-472">Parameters</span></span>

- <span data-ttu-id="d7262-473">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-473">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-474">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-474">Return Values</span></span>

- <span data-ttu-id="d7262-475">**NX_SUCCESS** (0x00) — успешное включение протокола IGMP.</span><span class="sxs-lookup"><span data-stu-id="d7262-475">**NX_SUCCESS** (0x00) Successful IGMP enable.</span></span>
- <span data-ttu-id="d7262-476">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-476">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-477">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-477">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-478">**NX_ALREADY_ENABLED** (0x15) — этот компонент уже включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-478">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-479">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-479">Allowed From</span></span>

<span data-ttu-id="d7262-480">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-480">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-481">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-481">Preemption Possible</span></span>

<span data-ttu-id="d7262-482">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-482">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-483">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-483">Example</span></span>

```C
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-484">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-484">See Also</span></span>

- <span data-ttu-id="d7262-485">nx_igmp_info_get,nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-485">nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="d7262-486">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span><span class="sxs-lookup"><span data-stu-id="d7262-486">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="d7262-487">nx_igmp_multicast_join, nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="d7262-487">nx_igmp_multicast_join, nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_info_get"></a><span data-ttu-id="d7262-488">nx_igmp_info_get</span><span class="sxs-lookup"><span data-stu-id="d7262-488">nx_igmp_info_get</span></span>

<span data-ttu-id="d7262-489">Получение сведений о действиях IGMP</span><span class="sxs-lookup"><span data-stu-id="d7262-489">Retrieve information about IGMP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-490">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-490">Prototype</span></span>

```C
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```

### <a name="description"></a><span data-ttu-id="d7262-491">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-491">Description</span></span>

<span data-ttu-id="d7262-492">Эта служба получает сведения о действиях протокола IGMP для указанного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-492">This service retrieves information about IGMP activities for the specified IP instance.</span></span>

<span data-ttu-id="d7262-493">*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.</span><span class="sxs-lookup"><span data-stu-id="d7262-493">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-494">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-494">Parameters</span></span>

- <span data-ttu-id="d7262-495">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-495">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-496">**igmp_reports_sent**: указатель места назначения для общего числа отправленных отчетов ICMP</span><span class="sxs-lookup"><span data-stu-id="d7262-496">**igmp_reports_sent** Pointer to destination for the total number of ICMP reports sent.</span></span>
- <span data-ttu-id="d7262-497">**igmp_queries_received**:указатель места назначения для общего числа запросов, полученных маршрутизатором многоадресной рассылки</span><span class="sxs-lookup"><span data-stu-id="d7262-497">**igmp_queries_received** Pointer to destination for the total number of queries received by multicast router.</span></span>
- <span data-ttu-id="d7262-498">**igmp_checksum_errors**: указатель места назначения общего числа ошибок контрольной суммы IGMP для полученных пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-498">**igmp_checksum_errors** Pointer to destination of the total number of IGMP checksum errors on receive packets.</span></span>
- <span data-ttu-id="d7262-499">**current_groups_joined**: указатель места назначения текущего числа групп, соединяемых через этот экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-499">**current_groups_joined** Pointer to destination of the current number of groups joined through this IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-500">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-500">Return Values</span></span>

- <span data-ttu-id="d7262-501">**NX_SUCCESS** (0x00) — успешное получение сведений IGMP.</span><span class="sxs-lookup"><span data-stu-id="d7262-501">**NX_SUCCESS** (0x00) Successful IGMP information retrieval.</span></span>
- <span data-ttu-id="d7262-502">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-502">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-503">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-503">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-504">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-504">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-505">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-505">Allowed From</span></span>

<span data-ttu-id="d7262-506">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-506">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-507">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-507">Preemption Possible</span></span>

<span data-ttu-id="d7262-508">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-508">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-509">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-509">Example</span></span>

```C
/* Retrieve IGMP information
    from previously created IP Instance ip_0. */
status = nx_igmp_info_get(
    &ip_0, 
    &igmp_reports_sent,
    &igmp_queries_received,
    &igmp_checksum_errors,
    &current_groups_joined);
/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-510">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-510">See Also</span></span>

- <span data-ttu-id="d7262-511">nx_igmp_enable, nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-511">nx_igmp_enable, nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="d7262-512">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span><span class="sxs-lookup"><span data-stu-id="d7262-512">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="d7262-513">nx_igmp_multicast_join, nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="d7262-513">nx_igmp_multicast_join, nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_loopback_disable"></a><span data-ttu-id="d7262-514">nx_igmp_loopback_disable</span><span class="sxs-lookup"><span data-stu-id="d7262-514">nx_igmp_loopback_disable</span></span>

<span data-ttu-id="d7262-515">Отключение петлевого адреса IGMP</span><span class="sxs-lookup"><span data-stu-id="d7262-515">Disable IGMP loopback</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-516">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-516">Prototype</span></span>

```C
UINT nx_igmp_loopback_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-517">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-517">Description</span></span>

<span data-ttu-id="d7262-518">Эта служба отключает петлевой адрес IGMP для всех последующих присоединенных групп многоадресной рассылки.</span><span class="sxs-lookup"><span data-stu-id="d7262-518">This service disables IGMP loopback for all subsequent multicast groups joined.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-519">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-519">Parameters</span></span>

- <span data-ttu-id="d7262-520">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-520">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-521">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-521">Return Values</span></span>
- <span data-ttu-id="d7262-522">**NX_SUCCESS** (0x00) — успешное отключение петлевого адреса IGMP.</span><span class="sxs-lookup"><span data-stu-id="d7262-522">**NX_SUCCESS** (0x00) Successful IGMP loopback disable.</span></span>
- <span data-ttu-id="d7262-523">**NX_NOT_ENABLED** (0x14) — протокол IGMP не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-523">**NX_NOT_ENABLED** (0x14) IGMP is not enabled.</span></span>
- <span data-ttu-id="d7262-524">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-524">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-525">**NX_CALLER_ERROR** (0x11) — вызывающий объект не является потоком или инициализацией.</span><span class="sxs-lookup"><span data-stu-id="d7262-525">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-526">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-526">Allowed From</span></span>

<span data-ttu-id="d7262-527">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-527">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-528">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-528">Preemption Possible</span></span>

<span data-ttu-id="d7262-529">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-529">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-530">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-530">Example</span></span>

```C
/* Disable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-531">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-531">See Also</span></span>

- <span data-ttu-id="d7262-532">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable,</span><span class="sxs-lookup"><span data-stu-id="d7262-532">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_enable,</span></span>
- <span data-ttu-id="d7262-533">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span><span class="sxs-lookup"><span data-stu-id="d7262-533">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="d7262-534">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="d7262-534">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_loopback_enable"></a><span data-ttu-id="d7262-535">nx_igmp_loopback_enable</span><span class="sxs-lookup"><span data-stu-id="d7262-535">nx_igmp_loopback_enable</span></span>

<span data-ttu-id="d7262-536">Включение петлевого адреса IGMP</span><span class="sxs-lookup"><span data-stu-id="d7262-536">Enable IGMP loopback</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-537">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-537">Prototype</span></span>

```C
UINT nx_igmp_loopback_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-538">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-538">Description</span></span>

<span data-ttu-id="d7262-539">Эта служба включает петлевой адрес IGMP для всех последующих присоединенных групп многоадресной рассылки.</span><span class="sxs-lookup"><span data-stu-id="d7262-539">This service enables IGMP loopback for all subsequent multicast groups joined.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-540">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-540">Parameters</span></span>

- <span data-ttu-id="d7262-541">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-541">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-542">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-542">Return Values</span></span>
- <span data-ttu-id="d7262-543">**NX_SUCCESS** (0x00) — успешное отключение петлевого адреса IGMP.</span><span class="sxs-lookup"><span data-stu-id="d7262-543">**NX_SUCCESS** (0x00) Successful IGMP loopback disable.</span></span>
- <span data-ttu-id="d7262-544">**NX_NOT_ENABLED** (0x14) — протокол IGMP не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-544">**NX_NOT_ENABLED** (0x14) IGMP is not enabled.</span></span>
- <span data-ttu-id="d7262-545">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-545">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-546">**NX_CALLER_ERROR** (0x11) — вызывающий объект не является потоком или инициализацией.</span><span class="sxs-lookup"><span data-stu-id="d7262-546">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-547">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-547">Allowed From</span></span>

<span data-ttu-id="d7262-548">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-548">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-549">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-549">Preemption Possible</span></span>

<span data-ttu-id="d7262-550">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-550">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-551">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-551">Example</span></span>

```C
/* Enable IGMP loopback for all subsequent multicast groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-552">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-552">See Also</span></span>

- <span data-ttu-id="d7262-553">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-553">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="d7262-554">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span><span class="sxs-lookup"><span data-stu-id="d7262-554">nx_igmp_multicast_interface_join, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="d7262-555">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="d7262-555">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_interface_join"></a><span data-ttu-id="d7262-556">nx_igmp_multicast_interface_join</span><span class="sxs-lookup"><span data-stu-id="d7262-556">nx_igmp_multicast_interface_join</span></span>

<span data-ttu-id="d7262-557">Присоединение экземпляра IP к указанной группе многоадресной рассылки через интерфейс</span><span class="sxs-lookup"><span data-stu-id="d7262-557">Join IP instance to specified multicast group via an interface</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-558">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-558">Prototype</span></span>

```C
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="d7262-559">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-559">Description</span></span>

<span data-ttu-id="d7262-560">Эта служба присоединяет экземпляр IP к указанной группе многоадресной рассылки через указанный сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d7262-560">This service joins an IP instance to the specified multicast group via a specified network interface.</span></span> <span data-ttu-id="d7262-561">Внутренний счетчик поддерживается для наблюдения за тем, сколько раз была присоединена одна и та же группа.</span><span class="sxs-lookup"><span data-stu-id="d7262-561">An internal counter is maintained to keep track of the number of times the same group has been joined.</span></span> <span data-ttu-id="d7262-562">После присоединения к группе многоадресной рассылки компонент IGMP разрешит получение IP-пакетов с этим адресом группы через указанный сетевой интерфейс, а также сообщает маршрутизаторам, что этот IP-адрес является участником этой группы рассылки.</span><span class="sxs-lookup"><span data-stu-id="d7262-562">After joining the multicast group, the IGMP component will allow reception of IP packets with this group address via the specified network interface and also report to routers that this IP is a member of this multicast group.</span></span> <span data-ttu-id="d7262-563">Сообщения об участии в IGMP, отчетах и выходе также отправляются через указанный сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d7262-563">The IGMP membership join, report, and leave messages are also sent via the specified network interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-564">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-564">Parameters</span></span>

- <span data-ttu-id="d7262-565">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-565">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-566">**group_address**: адрес группы многоадресной рассылки IP-адресов класса D для присоединение в порядке байтов узла</span><span class="sxs-lookup"><span data-stu-id="d7262-566">**group_address** Class D IP multicast group address to join in host byte order.</span></span>
- <span data-ttu-id="d7262-567">**interface_index**: индекс интерфейса, присоединенного к экземпляру NetX</span><span class="sxs-lookup"><span data-stu-id="d7262-567">**interface_index** Index of the Interface attached to the NetX instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-568">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-568">Return Values</span></span>

- <span data-ttu-id="d7262-569">**NX_SUCCESS** (0x00) — успешное присоединение к группе многоадресной рассылки.</span><span class="sxs-lookup"><span data-stu-id="d7262-569">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="d7262-570">**NX_NO_MORE_ENTRIES** (0x17) — дополнительные группы многоадресной рассылки не могут быть присоединены (превышено максимальное значение).</span><span class="sxs-lookup"><span data-stu-id="d7262-570">**NX_NO_MORE_ENTRIES** (0x17) No more multicast groups can be joined, maximum exceeded.</span></span>
- <span data-ttu-id="d7262-571">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-571">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-572">**NX_INVALID_INTERFACE** (0x4C) — индекс устройства указывает на недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d7262-572">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="d7262-573">**NX_IP_ADDRESS_ERROR** (0x21) — указанный адрес группы многоадресной рассылки не является допустимым адресом класса D.</span><span class="sxs-lookup"><span data-stu-id="d7262-573">**NX_IP_ADDRESS_ERROR** (0x21) Multicast group address provided is not a valid class D address.</span></span>
- <span data-ttu-id="d7262-574">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-574">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-575">**NX_NOT_ENABLED** (0x14) — поддержка многоадресной рассылки IP не включена.</span><span class="sxs-lookup"><span data-stu-id="d7262-575">**NX_NOT_ENABLED** (0x14) IP multicast support is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-576">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-576">Allowed From</span></span>

<span data-ttu-id="d7262-577">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-577">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-578">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-578">Preemption Possible</span></span>

<span data-ttu-id="d7262-579">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-579">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-580">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-580">Example</span></span>

```C
/* Previously created IP Instance joins the multicast group
    244.0.0.200, via the interface at index 1 in the IP interface list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
    (&ip, IP_ADDRESS(244,0,0,200),
    INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
    the multicast group. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-581">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-581">See Also</span></span>

- <span data-ttu-id="d7262-582">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-582">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="d7262-583">nx_igmp_loopback_enable, nx_igmp_multicast_join,</span><span class="sxs-lookup"><span data-stu-id="d7262-583">nx_igmp_loopback_enable, nx_igmp_multicast_join,</span></span>
- <span data-ttu-id="d7262-584">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="d7262-584">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_join"></a><span data-ttu-id="d7262-585">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="d7262-585">nx_igmp_multicast_join</span></span>

<span data-ttu-id="d7262-586">Присоединение экземпляра IP к указанной группе многоадресной рассылки</span><span class="sxs-lookup"><span data-stu-id="d7262-586">Join IP instance to specified multicast group</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-587">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-587">Prototype</span></span>

```C
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a><span data-ttu-id="d7262-588">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-588">Description</span></span>

<span data-ttu-id="d7262-589">Эта служба присоединяет экземпляр IP-адреса к указанной группе многоадресной рассылки.</span><span class="sxs-lookup"><span data-stu-id="d7262-589">This service joins an IP instance to the specified multicast group.</span></span> <span data-ttu-id="d7262-590">Внутренний счетчик поддерживается для наблюдения за тем, сколько раз была присоединена одна и та же группа.</span><span class="sxs-lookup"><span data-stu-id="d7262-590">An internal counter is maintained to keep track of the number of times the same group has been joined.</span></span> <span data-ttu-id="d7262-591">Драйвер получает команду отправить отчет IGMP, если это первый запрос на присоединение в сети, указывающий на намерение узла присоединиться к группе.</span><span class="sxs-lookup"><span data-stu-id="d7262-591">The driver is commanded to send an IGMP report if this is the first join request out on the network indicating the host's intention to join the group.</span></span> <span data-ttu-id="d7262-592">После присоединения компонент IGMP разрешит прием IP-пакетов с этим адресом группы и сообщит маршрутизаторам, что этот IP-адрес является членом этой группы многоадресной рассылки.</span><span class="sxs-lookup"><span data-stu-id="d7262-592">After joining, the IGMP component will allow reception of IP packets with this group address and report to routers that this IP is a member of this multicast group.</span></span>

> [!NOTE]
> <span data-ttu-id="d7262-593">\*Чтобы присоединить группу многоадресной рассылки на неосновном устройстве, используйте службу \*\*nx_igmp_multicast_interface_join\*\*\*.</span><span class="sxs-lookup"><span data-stu-id="d7262-593">*To join a multicast group on a non-primary device, use the service **nx_igmp_multicast_interface_join.***</span></span>

- <span data-ttu-id="d7262-594">**Параметры**</span><span class="sxs-lookup"><span data-stu-id="d7262-594">**Parameters**</span></span>

- <span data-ttu-id="d7262-595">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-595">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-596">**group_address**: адрес группы многоадресной рассылки IP-адресов класса D для присоединения</span><span class="sxs-lookup"><span data-stu-id="d7262-596">**group_address** Class D IP multicast group address to join.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-597">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-597">Return Values</span></span>

- <span data-ttu-id="d7262-598">**NX_SUCCESS** (0x00) — успешное присоединение к группе многоадресной рассылки.</span><span class="sxs-lookup"><span data-stu-id="d7262-598">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="d7262-599">**NX_NO_MORE_ENTRIES** (0x17) — дополнительные группы многоадресной рассылки не могут быть присоединены (превышено максимальное значение).</span><span class="sxs-lookup"><span data-stu-id="d7262-599">**NX_NO_MORE_ENTRIES** (0x17) No more multicast groups can be joined, maximum exceeded.</span></span>
- <span data-ttu-id="d7262-600">**NX_INVALID_INTERFACE** (0x4C) — индекс устройства указывает на недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d7262-600">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="d7262-601">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый адрес группы IP-адресов.</span><span class="sxs-lookup"><span data-stu-id="d7262-601">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP group address.</span></span>
- <span data-ttu-id="d7262-602">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-602">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-603">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-603">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-604">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-604">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-605">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-605">Allowed From</span></span>

<span data-ttu-id="d7262-606">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-606">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-607">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-607">Preemption Possible</span></span>

<span data-ttu-id="d7262-608">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-608">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-609">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-609">Example</span></span>

```C
/* Previously created IP Instance ip_0 joins the multicast group
    224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200));

/* If status is NX_SUCCESS, this IP instance has successfully
    joined the multicast group 224.0.0.200. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-610">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-610">See Also</span></span>

- <span data-ttu-id="d7262-611">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-611">nx_igmp_enable, nx_igmp_info_get,nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="d7262-612">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span><span class="sxs-lookup"><span data-stu-id="d7262-612">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="d7262-613">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="d7262-613">nx_igmp_multicast_leave</span></span>

## <a name="nx_igmp_multicast_leave"></a><span data-ttu-id="d7262-614">nx_igmp_multicast_leave</span><span class="sxs-lookup"><span data-stu-id="d7262-614">nx_igmp_multicast_leave</span></span>

<span data-ttu-id="d7262-615">Экземпляр IP покидает указанную группу многоадресной рассылки</span><span class="sxs-lookup"><span data-stu-id="d7262-615">Cause IP instance to leave specified multicast group</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-616">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-616">Prototype</span></span>

```C
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```

### <a name="description"></a><span data-ttu-id="d7262-617">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-617">Description</span></span>

<span data-ttu-id="d7262-618">Эта служба приводит к тому, что экземпляр IP покидает указанную группу многоадресной рассылки, если число запросов на выход соответствует числу запросов на присоединение.</span><span class="sxs-lookup"><span data-stu-id="d7262-618">This service causes an IP instance to leave the specified multicast group, if the number of leave requests matches the number of join requests.</span></span> <span data-ttu-id="d7262-619">В противном случае число внутренних присоединений просто уменьшается.</span><span class="sxs-lookup"><span data-stu-id="d7262-619">Otherwise, the internal join count is simply decremented.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-620">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-620">Parameters</span></span>

- <span data-ttu-id="d7262-621">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-621">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-622">**group_address**: группа многоадресной рассылки для выхода</span><span class="sxs-lookup"><span data-stu-id="d7262-622">**group_address** Multicast group to leave.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-623">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-623">Return Values</span></span>

- <span data-ttu-id="d7262-624">**NX_SUCCESS** (0x00) — успешное присоединение к группе многоадресной рассылки.</span><span class="sxs-lookup"><span data-stu-id="d7262-624">**NX_SUCCESS** (0x00) Successful multicast group join.</span></span>
- <span data-ttu-id="d7262-625">**NX_ENTRY_NOT_FOUND** (0x16) — предыдущий запрос на присоединение не найден.</span><span class="sxs-lookup"><span data-stu-id="d7262-625">**NX_ENTRY_NOT_FOUND** (0x16) Previous join request was not found.</span></span>
- <span data-ttu-id="d7262-626">**NX_INVALID_INTERFACE** (0x4C) — индекс устройства указывает на недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d7262-626">**NX_INVALID_INTERFACE** (0x4C) Device index points to an invalid network interface.</span></span>
- <span data-ttu-id="d7262-627">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый адрес группы IP-адресов.</span><span class="sxs-lookup"><span data-stu-id="d7262-627">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP group address.</span></span>
- <span data-ttu-id="d7262-628">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-628">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-629">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-629">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-630">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-630">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-631">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-631">Allowed From</span></span>

<span data-ttu-id="d7262-632">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-632">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-633">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-633">Preemption Possible</span></span>

<span data-ttu-id="d7262-634">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-634">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-635">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-635">Example</span></span>

```C
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
    the multicast group 224.0.0.200. */
```
### <a name="see-also"></a><span data-ttu-id="d7262-636">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-636">See Also</span></span>

- <span data-ttu-id="d7262-637">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-637">nx_igmp_enable, nx_igmp_info_get, nx_igmp_loopback_disable,</span></span>
- <span data-ttu-id="d7262-638">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span><span class="sxs-lookup"><span data-stu-id="d7262-638">nx_igmp_loopback_enable, nx_igmp_multicast_interface_join,</span></span>
- <span data-ttu-id="d7262-639">nx_igmp_multicast_join</span><span class="sxs-lookup"><span data-stu-id="d7262-639">nx_igmp_multicast_join</span></span>

## <a name="nx_ip_address_change_notifiy"></a><span data-ttu-id="d7262-640">nx_ip_address_change_notifiy</span><span class="sxs-lookup"><span data-stu-id="d7262-640">nx_ip_address_change_notifiy</span></span>

<span data-ttu-id="d7262-641">Уведомление приложения при изменении IP-адреса</span><span class="sxs-lookup"><span data-stu-id="d7262-641">Notify application if IP address changes</span></span>


### <a name="prototype"></a><span data-ttu-id="d7262-642">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-642">Prototype</span></span>

```C
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *,VOID *),
    VOID *additional_info);
```

### <a name="description"></a><span data-ttu-id="d7262-643">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-643">Description</span></span>

<span data-ttu-id="d7262-644">Эта служба регистрирует функцию уведомления приложения, которая вызывается при каждом изменении IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-644">This service registers an application notification function that is called whenever the IP address is changed.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-645">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-645">Parameters</span></span>

- <span data-ttu-id="d7262-646">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-646">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-647">**change_notify**: указатель функции уведомления об изменении IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-647">**change_notify** Pointer to IP change notification function.</span></span> <span data-ttu-id="d7262-648">Если этот параметр имеет значение NX_NULL, уведомление об изменении IP-адреса отключается.</span><span class="sxs-lookup"><span data-stu-id="d7262-648">If this parameter is NX_NULL, IP address change notification is disabled.</span></span>
- <span data-ttu-id="d7262-649">**additional_info**: указатель необязательных дополнительных сведений, который также предоставляется функции уведомления при изменении IP-адреса</span><span class="sxs-lookup"><span data-stu-id="d7262-649">**additional_info** Pointer to optional additional information that is also supplied to the notification function when the IP address is changed.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-650">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-650">Return Values</span></span>

- <span data-ttu-id="d7262-651">**NX_SUCCESS** (0x00) — уведомление об изменении IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-651">**NX_SUCCESS** (0x00) Successful IP address change notification.</span></span>
- <span data-ttu-id="d7262-652">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-652">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-653">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-653">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-654">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-654">Allowed From</span></span>

<span data-ttu-id="d7262-655">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-655">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-656">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-656">Preemption Possible</span></span>

<span data-ttu-id="d7262-657">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-657">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-658">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-658">Example</span></span>

```C
/* Register the function "my_ip_changed" to be called whenever
the IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed, NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
    called whenever the IP address changes. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-659">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-659">See Also</span></span>

- <span data-ttu-id="d7262-660">nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete,</span><span class="sxs-lookup"><span data-stu-id="d7262-660">nx_ip_address_get, nx_ip_address_set, nx_ip_create, nx_ip_delete,</span></span>
- <span data-ttu-id="d7262-661">nx_ip_driver_direct_command, nx_ip_driver_interface_direct_command,</span><span class="sxs-lookup"><span data-stu-id="d7262-661">nx_ip_driver_direct_command, nx_ip_driver_interface_direct_command,</span></span>
- <span data-ttu-id="d7262-662">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span><span class="sxs-lookup"><span data-stu-id="d7262-662">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="d7262-663">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-663">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="d7262-664">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="d7262-664">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_address_get"></a><span data-ttu-id="d7262-665">nx_ip_address_get</span><span class="sxs-lookup"><span data-stu-id="d7262-665">nx_ip_address_get</span></span>

<span data-ttu-id="d7262-666">Получение IP-адреса и маски сети</span><span class="sxs-lookup"><span data-stu-id="d7262-666">Retrieve IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-667">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-667">Prototype</span></span>

```C
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a><span data-ttu-id="d7262-668">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-668">Description</span></span>

<span data-ttu-id="d7262-669">Эта служба извлекает IP-адрес и маску подсети основного сетевого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d7262-669">This service retrieves IP address and its subnet mask of the primary network interface.</span></span>

<span data-ttu-id="d7262-670">\* Чтобы получить сведения о вторичном устройстве, используйте службу</span><span class="sxs-lookup"><span data-stu-id="d7262-670">\*To obtain information of the secondary device, use the service</span></span>
- <span data-ttu-id="d7262-671">**nx_ip_interface_address_get**.\*</span><span class="sxs-lookup"><span data-stu-id="d7262-671">**nx_ip_interface_address_get**.\*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-672">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-672">Parameters</span></span>

- <span data-ttu-id="d7262-673">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-673">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-674">**ip_address**: указатель назначения IP-адреса</span><span class="sxs-lookup"><span data-stu-id="d7262-674">**ip_address** Pointer to destination for IP address.</span></span>
- <span data-ttu-id="d7262-675">**network_mask**: указатель места назначения для маски сети</span><span class="sxs-lookup"><span data-stu-id="d7262-675">**network_mask** Pointer to destination for network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-676">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-676">Return Values</span></span>

- <span data-ttu-id="d7262-677">**NX_SUCCESS** (0x00) — успешное получение IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-677">**NX_SUCCESS** (0x00) Successful IP address get.</span></span>
- <span data-ttu-id="d7262-678">**NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель возвращаемой переменной.</span><span class="sxs-lookup"><span data-stu-id="d7262-678">**NX_PTR_ERROR** (0x07) Invalid IP or return variable pointer.</span></span>
- <span data-ttu-id="d7262-679">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-679">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-680">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-680">Allowed From</span></span>

<span data-ttu-id="d7262-681">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-681">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-682">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-682">Preemption Possible</span></span>

<span data-ttu-id="d7262-683">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-683">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-684">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-684">Example</span></span>

```C
/* Get the IP address and network mask from the previously created
    IP Instance ip_0. */
status = nx_ip_address_get(&ip_0,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
    network_mask contain the IP and network mask respectively. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-685">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-685">See Also</span></span>

- <span data-ttu-id="d7262-686">nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-686">nx_ip_address_change_notify, nx_ip_address_set, nx_ip_create,</span></span>
- <span data-ttu-id="d7262-687">nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="d7262-687">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="d7262-688">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-688">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="d7262-689">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-689">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="d7262-690">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span><span class="sxs-lookup"><span data-stu-id="d7262-690">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="d7262-691">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="d7262-691">nx_system_initialize</span></span>

## <a name="nx_ip_address_set"></a><span data-ttu-id="d7262-692">nx_ip_address_set</span><span class="sxs-lookup"><span data-stu-id="d7262-692">nx_ip_address_set</span></span>

<span data-ttu-id="d7262-693">Получение IP-адреса и маски сети</span><span class="sxs-lookup"><span data-stu-id="d7262-693">Set IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-694">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-694">Prototype</span></span>

```C
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a><span data-ttu-id="d7262-695">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-695">Description</span></span>

<span data-ttu-id="d7262-696">Эта служба задает IP-адрес и маску сети для основного сетевого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d7262-696">This service sets IP address and network mask for the primary network interface.</span></span>

<span data-ttu-id="d7262-697">*Чтобы задать IP-адрес и маску сети для вторичного устройства, используйте службу **nx_ip_interface_address_set**.*</span><span class="sxs-lookup"><span data-stu-id="d7262-697">*To set IP address and network mask for the secondary device, use the service **nx_ip_interface_address_set**.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-698">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-698">Parameters</span></span>

- <span data-ttu-id="d7262-699">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-699">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-700">**ip_address**: новый IP-адрес</span><span class="sxs-lookup"><span data-stu-id="d7262-700">**ip_address** New IP address.</span></span>
- <span data-ttu-id="d7262-701">**network_mask**: новая маска сети</span><span class="sxs-lookup"><span data-stu-id="d7262-701">**network_mask** New network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-702">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-702">Return Values</span></span>

- <span data-ttu-id="d7262-703">**NX_SUCCESS** (0x00) — успешный набор IP-адресов.</span><span class="sxs-lookup"><span data-stu-id="d7262-703">**NX_SUCCESS** (0x00) Successful IP address set.</span></span>
- <span data-ttu-id="d7262-704">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d7262-704">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="d7262-705">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-705">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-706">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-706">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-707">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-707">Allowed From</span></span>

<span data-ttu-id="d7262-708">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-708">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-709">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-709">Preemption Possible</span></span>

<span data-ttu-id="d7262-710">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-710">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-711">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-711">Example</span></span>

```C
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00
    for the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4), 0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address
    of 1.2.3.4 and a network mask of 0xFFFFFF00. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-712">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-712">See Also</span></span>

- <span data-ttu-id="d7262-713">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-713">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_create,</span></span>
- <span data-ttu-id="d7262-714">nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="d7262-714">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="d7262-715">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-715">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="d7262-716">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-716">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="d7262-717">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span><span class="sxs-lookup"><span data-stu-id="d7262-717">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="d7262-718">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="d7262-718">nx_system_initialize</span></span>

## <a name="nx_ip_create"></a><span data-ttu-id="d7262-719">nx_ip_create</span><span class="sxs-lookup"><span data-stu-id="d7262-719">nx_ip_create</span></span>

<span data-ttu-id="d7262-720">Создание экземпляра IP</span><span class="sxs-lookup"><span data-stu-id="d7262-720">Create an IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-721">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-721">Prototype</span></span>

```C
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, 
    ULONG ip_address,
    ULONG network_mask, 
    NX_PACKET_POOL *default_pool,
    VOID (*ip_network_driver)(NX_IP_DRIVER *),
    VOID *memory_ptr, 
    ULONG memory_size,
    UINT priority);
```

### <a name="description"></a><span data-ttu-id="d7262-722">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-722">Description</span></span>

<span data-ttu-id="d7262-723">Эта служба создает экземпляр IP с пользовательским IP-адресом и сетевым драйвером.</span><span class="sxs-lookup"><span data-stu-id="d7262-723">This service creates an IP instance with the user supplied IP address and network driver.</span></span> <span data-ttu-id="d7262-724">Кроме того, приложение должно предоставить созданный ранее пул пакетов для экземпляра клиента PPPoE, который будет использоваться для внутреннего распределения пакетов.</span><span class="sxs-lookup"><span data-stu-id="d7262-724">In addition, the application must supply a previously created packet pool for the IP instance to use for internal packet allocation.</span></span> <span data-ttu-id="d7262-725">Обратите внимание, что указанный сетевой драйвер приложения не вызывается до тех пор, пока не будет выполнен поток этого IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-725">Note that the supplied application network driver is not called until this IP's thread executes.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-726">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-726">Parameters</span></span>

- <span data-ttu-id="d7262-727">**ip_ptr**: указатель на блок управления для создания экземпляра IP</span><span class="sxs-lookup"><span data-stu-id="d7262-727">**ip_ptr** Pointer to control block to create a new IP instance.</span></span>
- <span data-ttu-id="d7262-728">**name**: имя нового экземпляра IP</span><span class="sxs-lookup"><span data-stu-id="d7262-728">**name** Name of this new IP instance.</span></span>
- <span data-ttu-id="d7262-729">**ip_address**: IP-адрес для этого нового экземпляра IP</span><span class="sxs-lookup"><span data-stu-id="d7262-729">**ip_address** IP address for this new IP instance.</span></span>
- <span data-ttu-id="d7262-730">**network_mask**: маска для отделения сетевой части IP-адреса для подсетей и суперсетей</span><span class="sxs-lookup"><span data-stu-id="d7262-730">**network_mask** Mask to delineate the network portion of the IP address for sub-netting and super-netting uses.</span></span>
- <span data-ttu-id="d7262-731">**default_pool**: указатель на управляющий блок ранее созданного пула пакетов NetX</span><span class="sxs-lookup"><span data-stu-id="d7262-731">**default_pool** Pointer to control block of previously created NetX packet pool.</span></span>
- <span data-ttu-id="d7262-732">**ip_network_driver**: предоставленный пользователем драйвер сети, используемый для отправки и получения IP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-732">**ip_network_driver** User-supplied network driver used to send and receive IP packets.</span></span>
- <span data-ttu-id="d7262-733">**memory_ptr**: указатель на область памяти для стека вспомогательного потока IP</span><span class="sxs-lookup"><span data-stu-id="d7262-733">**memory_ptr** Pointer to memory area for the IP helper thread’s stack area.</span></span>
- <span data-ttu-id="d7262-734">**memory_size**: число байтов в области памяти для стека вспомогательного потока IP</span><span class="sxs-lookup"><span data-stu-id="d7262-734">**memory_size** Number of bytes in the memory area for the IP helper thread’s stack.</span></span>
- <span data-ttu-id="d7262-735">**priority**: приоритет вспомогательного потока IP</span><span class="sxs-lookup"><span data-stu-id="d7262-735">**priority** Priority of IP helper thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-736">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-736">Return Values</span></span>
- <span data-ttu-id="d7262-737">**NX_SUCCESS** (0x00) — успешное создание экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-737">**NX_SUCCESS** (0x00) Successful IP instance creation.</span></span>
- <span data-ttu-id="d7262-738">**NX_NOT_IMPLEMENTED** (0x4A) — библиотека NetX настроена неправильно.</span><span class="sxs-lookup"><span data-stu-id="d7262-738">**NX_NOT_IMPLEMENTED** (0x4A) NetX library is configured incorrectly.</span></span>
- <span data-ttu-id="d7262-739">**NX_PTR_ERROR** (0x07) — недопустимый IP-адрес, указатель функции сетевого драйвера, пул пакетов или указатель на память.</span><span class="sxs-lookup"><span data-stu-id="d7262-739">**NX_PTR_ERROR** (0x07) Invalid IP, network driver function pointer, packet pool, or memory pointer.</span></span>
- <span data-ttu-id="d7262-740">**NX_SIZE_ERROR** (0x09) — указанный размер стека слишком мал.</span><span class="sxs-lookup"><span data-stu-id="d7262-740">**NX_SIZE_ERROR** (0x09) The supplied stack size is too small.</span></span>
- <span data-ttu-id="d7262-741">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-741">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-742">**NX_IP_ADDRESS_ERROR** (0x21) — указан недопустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d7262-742">**NX_IP_ADDRESS_ERROR** (0x21) The supplied IP address is invalid.</span></span>
- <span data-ttu-id="d7262-743">**NX_OPTION_ERROR** (0x21) — указан недопустимый приоритет потока IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-743">**NX_OPTION_ERROR** (0x21) The supplied IP thread priority is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-744">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-744">Allowed From</span></span>

<span data-ttu-id="d7262-745">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-745">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-746">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-746">Preemption Possible</span></span>

<span data-ttu-id="d7262-747">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-747">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-748">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-748">Example</span></span>

```C
/* Create an IP instance with an IP address of 1.2.3.4 and a network
    mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
    point of the application specific network driver and the
    "stack_memory_ptr" specifies the start of a 1024 byte memory
    area that is used for this IP instance’s helper thread.  */
status = nx_ip_create(
    &ip_0, 
    "NetX IP Instance ip_0",
    IP_ADDRESS(1, 2, 3, 4),
    0xFFFFFF00UL, &pool_0, 
    ethernet_driver,
    stack_memory_ptr, 
    1024, 
    1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-749">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-749">See Also</span></span>

- <span data-ttu-id="d7262-750">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-750">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="d7262-751">nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="d7262-751">nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="d7262-752">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-752">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="d7262-753">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-753">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="d7262-754">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span><span class="sxs-lookup"><span data-stu-id="d7262-754">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="d7262-755">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="d7262-755">nx_system_initialize</span></span>

## <a name="nx_ip_delete"></a><span data-ttu-id="d7262-756">nx_ip_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-756">nx_ip_delete</span></span>

<span data-ttu-id="d7262-757">Удаление ранее созданного экземпляра IP</span><span class="sxs-lookup"><span data-stu-id="d7262-757">Delete previously created IP instance</span></span>


### <a name="prototype"></a><span data-ttu-id="d7262-758">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-758">Prototype</span></span>

```C
UINT nx_ip_delete(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-759">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-759">Description</span></span>

<span data-ttu-id="d7262-760">Эта служба удаляет ранее созданный экземпляр IP и освобождает все принадлежащие ему ресурсы системы.</span><span class="sxs-lookup"><span data-stu-id="d7262-760">This service deletes a previously created IP instance and releases all of the system resources owned by the IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-761">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-761">Parameters</span></span>
- <span data-ttu-id="d7262-762">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-762">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-763">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-763">Return Values</span></span>

- <span data-ttu-id="d7262-764">**NX_SUCCESS** (0x00) — экземпляр IP успешно удален.</span><span class="sxs-lookup"><span data-stu-id="d7262-764">**NX_SUCCESS** (0x00) Successful IP deletion.</span></span>
- <span data-ttu-id="d7262-765">**NX_SOCKETS_BOUND** (0x28) — к этому экземпляру IP все еще привязаны сокеты UDP или TCP.</span><span class="sxs-lookup"><span data-stu-id="d7262-765">**NX_SOCKETS_BOUND** (0x28) This IP instance still has UDP or TCP sockets bound to it.</span></span> <span data-ttu-id="d7262-766">Перед удалением экземпляра IP необходимо отвязать и удалить все сокеты.</span><span class="sxs-lookup"><span data-stu-id="d7262-766">All sockets must be unbound and deleted prior to deleting the IP instance.</span></span>
- <span data-ttu-id="d7262-767">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-767">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-768">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-768">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-769">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-769">Allowed From</span></span>

<span data-ttu-id="d7262-770">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-770">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-771">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-771">Preemption Possible</span></span>

<span data-ttu-id="d7262-772">Да</span><span class="sxs-lookup"><span data-stu-id="d7262-772">Yes</span></span>

### <a name="example"></a><span data-ttu-id="d7262-773">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-773">Example</span></span>

```C
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-774">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-774">See Also</span></span>

- <span data-ttu-id="d7262-775">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-775">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="d7262-776">nx_ip_create, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="d7262-776">nx_ip_create, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="d7262-777">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-777">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="d7262-778">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-778">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="d7262-779">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span><span class="sxs-lookup"><span data-stu-id="d7262-779">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check,</span></span>
- <span data-ttu-id="d7262-780">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="d7262-780">nx_system_initialize</span></span>

## <a name="nx_ip_driver_direct_command"></a><span data-ttu-id="d7262-781">nx_ip_driver_direct_command</span><span class="sxs-lookup"><span data-stu-id="d7262-781">nx_ip_driver_direct_command</span></span>

<span data-ttu-id="d7262-782">Отправка команды сетевому драйверу</span><span class="sxs-lookup"><span data-stu-id="d7262-782">Issue command to network driver</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-783">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-783">Prototype</span></span>

```C
UINT nx_ip_driver_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-784">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-784">Description</span></span>

<span data-ttu-id="d7262-785">Эта служба предоставляет интерфейс для прямого взаимодействия с драйвером основного сетевого интерфейса приложения, указанным во время вызова ***nx_ip_create***.</span><span class="sxs-lookup"><span data-stu-id="d7262-785">This service provides a direct interface to the application's primary network interface driver specified during the ***nx_ip_create*** call.</span></span>

<span data-ttu-id="d7262-786">Можно использовать команды для конкретного приложения, если их числовые значения больше или равны NX_LINK_USER_COMMAND.</span><span class="sxs-lookup"><span data-stu-id="d7262-786">Application-specific commands can be used providing their numeric value is greater than or equal to NX_LINK_USER_COMMAND.</span></span>

<span data-ttu-id="d7262-787">*Чтобы отправить команду дополнительному устройству, используйте службу **nx_ip_driver_interface_direct_command**.*</span><span class="sxs-lookup"><span data-stu-id="d7262-787">*To issue command for the secondary device, use the **nx_ip_driver_interface_direct_command** service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-788">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-788">Parameters</span></span>

- <span data-ttu-id="d7262-789">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-789">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-790">**command**: числовой код команды</span><span class="sxs-lookup"><span data-stu-id="d7262-790">**command** Numeric command code.</span></span> <span data-ttu-id="d7262-791">Стандартные команды определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d7262-791">Standard commands are defined as follows:</span></span>

- <span data-ttu-id="d7262-792">NX_LINK_GET_STATUS (10)</span><span class="sxs-lookup"><span data-stu-id="d7262-792">NX_LINK_GET_STATUS (10)</span></span>
- <span data-ttu-id="d7262-793">NX_LINK_GET_SPEED (11)</span><span class="sxs-lookup"><span data-stu-id="d7262-793">NX_LINK_GET_SPEED (11)</span></span>
- <span data-ttu-id="d7262-794">NX_LINK_GET_DUPLEX_TYPE (12)</span><span class="sxs-lookup"><span data-stu-id="d7262-794">NX_LINK_GET_DUPLEX_TYPE (12)</span></span>
- <span data-ttu-id="d7262-795">NX_LINK_GET_ERROR_COUNT (13)</span><span class="sxs-lookup"><span data-stu-id="d7262-795">NX_LINK_GET_ERROR_COUNT (13)</span></span>
- <span data-ttu-id="d7262-796">NX_LINK_GET_RX_COUNT (14)</span><span class="sxs-lookup"><span data-stu-id="d7262-796">NX_LINK_GET_RX_COUNT (14)</span></span>
- <span data-ttu-id="d7262-797">NX_LINK_GET_TX_COUNT (15)</span><span class="sxs-lookup"><span data-stu-id="d7262-797">NX_LINK_GET_TX_COUNT (15)</span></span>
- <span data-ttu-id="d7262-798">NX_LINK_GET_ALLOC_ERRORS (16)</span><span class="sxs-lookup"><span data-stu-id="d7262-798">NX_LINK_GET_ALLOC_ERRORS (16)</span></span>
- <span data-ttu-id="d7262-799">NX_LINK_USER_COMMAND (50)</span><span class="sxs-lookup"><span data-stu-id="d7262-799">NX_LINK_USER_COMMAND (50)</span></span>

- <span data-ttu-id="d7262-800">**return_value_ptr**: указатель возвращаемой переменной в вызывающем объекте</span><span class="sxs-lookup"><span data-stu-id="d7262-800">**return_value_ptr** Pointer to return variable in the caller.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-801">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-801">Return Values</span></span>

- <span data-ttu-id="d7262-802">**NX_SUCCESS** (0x00) — успешная прямая команда сетевого драйвера.</span><span class="sxs-lookup"><span data-stu-id="d7262-802">**NX_SUCCESS** (0x00) Successful network driver direct command.</span></span>
- <span data-ttu-id="d7262-803">**NX_UNHANDLED_COMMAND** (0x44) — необработанная или нереализованная команда сетевого драйвера.</span><span class="sxs-lookup"><span data-stu-id="d7262-803">**NX_UNHANDLED_COMMAND** (0x44) Unhandled or unimplemented network driver command.</span></span>
- <span data-ttu-id="d7262-804">**NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="d7262-804">**NX_PTR_ERROR** (0x07) Invalid IP or return value pointer.</span></span>
- <span data-ttu-id="d7262-805">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-805">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-806">**NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d7262-806">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-807">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-807">Allowed From</span></span>

<span data-ttu-id="d7262-808">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-808">Threads</span></span>

- <span data-ttu-id="d7262-809">**Возможно вытеснение**</span><span class="sxs-lookup"><span data-stu-id="d7262-809">**Preemption Possible**</span></span>

<span data-ttu-id="d7262-810">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-810">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-811">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-811">Example</span></span>

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(
    &ip_0, NX_LINK_GET_STATUS,
    &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-812">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-812">See Also</span></span>

- <span data-ttu-id="d7262-813">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-813">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="d7262-814">nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command,</span><span class="sxs-lookup"><span data-stu-id="d7262-814">nx_ip_create, nx_ip_delete, nx_ip_driver_interface_direct_command,</span></span>
- <span data-ttu-id="d7262-815">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span><span class="sxs-lookup"><span data-stu-id="d7262-815">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="d7262-816">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-816">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="d7262-817">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="d7262-817">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_driver_interface_direct_command"></a><span data-ttu-id="d7262-818">nx_ip_driver_interface_direct_command</span><span class="sxs-lookup"><span data-stu-id="d7262-818">nx_ip_driver_interface_direct_command</span></span>

<span data-ttu-id="d7262-819">Отправка команды сетевому драйверу</span><span class="sxs-lookup"><span data-stu-id="d7262-819">Issue command to network driver</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-820">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-820">Prototype</span></span>

```C
UINT nx_ip_driver_interface_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    UINT interface_index,
    ULONG *return_value_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-821">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-821">Description</span></span>

<span data-ttu-id="d7262-822">Эта служба предоставляет прямую команду для драйвера сетевого устройства приложения в экземпляре IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-822">This service provides a direct command to the application's network device driver in the IP instance.</span></span> <span data-ttu-id="d7262-823">Можно использовать команды для конкретного приложения, если их числовые значения больше или равны *NX_LINK_USER_COMMAND*.</span><span class="sxs-lookup"><span data-stu-id="d7262-823">Application-specific commands can be used providing their numeric value is greater than or equal to *NX_LINK_USER_COMMAND*.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-824">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-824">Parameters</span></span>

- <span data-ttu-id="d7262-825">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-825">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-826">**command**: числовой код команды</span><span class="sxs-lookup"><span data-stu-id="d7262-826">**command** Numeric command code.</span></span> <span data-ttu-id="d7262-827">Стандартные команды определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d7262-827">Standard commands are defined as follows:</span></span>
- <span data-ttu-id="d7262-828">NX_LINK_GET_STATUS (10)</span><span class="sxs-lookup"><span data-stu-id="d7262-828">NX_LINK_GET_STATUS (10)</span></span>
- <span data-ttu-id="d7262-829">NX_LINK_GET_SPEED (11)</span><span class="sxs-lookup"><span data-stu-id="d7262-829">NX_LINK_GET_SPEED (11)</span></span>
- <span data-ttu-id="d7262-830">NX_LINK_GET_DUPLEX_TYPE (12)</span><span class="sxs-lookup"><span data-stu-id="d7262-830">NX_LINK_GET_DUPLEX_TYPE (12)</span></span>
- <span data-ttu-id="d7262-831">NX_LINK_GET_ERROR_COUNT (13)</span><span class="sxs-lookup"><span data-stu-id="d7262-831">NX_LINK_GET_ERROR_COUNT (13)</span></span>
- <span data-ttu-id="d7262-832">NX_LINK_GET_RX_COUNT (14)</span><span class="sxs-lookup"><span data-stu-id="d7262-832">NX_LINK_GET_RX_COUNT (14)</span></span>
- <span data-ttu-id="d7262-833">NX_LINK_GET_TX_COUNT (15)</span><span class="sxs-lookup"><span data-stu-id="d7262-833">NX_LINK_GET_TX_COUNT (15)</span></span>
- <span data-ttu-id="d7262-834">NX_LINK_GET_ALLOC_ERRORS (16)</span><span class="sxs-lookup"><span data-stu-id="d7262-834">NX_LINK_GET_ALLOC_ERRORS (16)</span></span>
- <span data-ttu-id="d7262-835">NX_LINK_USER_COMMAND (50)</span><span class="sxs-lookup"><span data-stu-id="d7262-835">NX_LINK_USER_COMMAND (50)</span></span>
- <span data-ttu-id="d7262-836">**interface_index**: индекс сетевого интерфейса, которому необходимо отправить команду.</span><span class="sxs-lookup"><span data-stu-id="d7262-836">**interface_index** Index of the network interface the command should be sent to.</span></span>
- <span data-ttu-id="d7262-837">**return_value_ptr**: указатель возвращаемой переменной в вызывающем объекте</span><span class="sxs-lookup"><span data-stu-id="d7262-837">**return_value_ptr** Pointer to return variable in the caller.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-838">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-838">Return Values</span></span>
- <span data-ttu-id="d7262-839">**NX_SUCCESS** (0x00) — успешная прямая команда сетевого драйвера.</span><span class="sxs-lookup"><span data-stu-id="d7262-839">**NX_SUCCESS** (0x00) Successful network driver direct command.</span></span>
- <span data-ttu-id="d7262-840">**NX_UNHANDLED_COMMAND** (0x44) — необработанная или нереализованная команда сетевого драйвера.</span><span class="sxs-lookup"><span data-stu-id="d7262-840">**NX_UNHANDLED_COMMAND** (0x44) Unhandled or unimplemented network driver command.</span></span>
- <span data-ttu-id="d7262-841">**NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d7262-841">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index</span></span>
- <span data-ttu-id="d7262-842">**NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель возвращаемого значения.</span><span class="sxs-lookup"><span data-stu-id="d7262-842">**NX_PTR_ERROR** (0x07) Invalid IP or return value pointer.</span></span>
- <span data-ttu-id="d7262-843">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-843">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-844">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-844">Allowed From</span></span>

<span data-ttu-id="d7262-845">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-845">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-846">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-846">Preemption Possible</span></span>

<span data-ttu-id="d7262-847">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-847">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-848">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-848">Example</span></span>

```C
/* Make a direct call to the application-specific network driver
    for the previously created IP instance. For this example, the
    network driver is interrogated for the link status. */

/* Set the interface index to the primary device. */
UINT interface_index = 0;
    status = nx_ip_driver_interface_direct_command(&ip_0,
    NX_LINK_GET_STATUS,
    interface_index,
    &link_status);
/* If status is NX_SUCCESS, the link_status variable contains a
    NX_TRUE or NX_FALSE value representing the status of the
    physical link. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-849">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-849">See Also</span></span>

- <span data-ttu-id="d7262-850">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-850">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="d7262-851">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="d7262-851">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="d7262-852">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span><span class="sxs-lookup"><span data-stu-id="d7262-852">nx_ip_forwarding_disable, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="d7262-853">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-853">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="d7262-854">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="d7262-854">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_forwarding_disable"></a><span data-ttu-id="d7262-855">nx_ip_forwarding_disable</span><span class="sxs-lookup"><span data-stu-id="d7262-855">nx_ip_forwarding_disable</span></span>

<span data-ttu-id="d7262-856">Отключение переадресации IP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-856">Disable IP packet forwarding</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-857">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-857">Prototype</span></span>

```C
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-858">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-858">Description</span></span>

<span data-ttu-id="d7262-859">Эта служба отключает переадресацию IP-пакетов внутри IP-компонента NetX.</span><span class="sxs-lookup"><span data-stu-id="d7262-859">This service disables forwarding IP packets inside the NetX IP component.</span></span> <span data-ttu-id="d7262-860">При создании задачи IP эта служба автоматически отключается.</span><span class="sxs-lookup"><span data-stu-id="d7262-860">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-861">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-861">Parameters</span></span>

- <span data-ttu-id="d7262-862">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-862">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-863">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-863">Return Values</span></span>

- <span data-ttu-id="d7262-864">**NX_SUCCESS** (0x00) — успешное отключение переадресации IP-пакетов.</span><span class="sxs-lookup"><span data-stu-id="d7262-864">**NX_SUCCESS** (0x00) Successful IP forwarding disable.</span></span>
- <span data-ttu-id="d7262-865">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-865">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-866">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-866">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-867">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-867">Allowed From</span></span>

<span data-ttu-id="d7262-868">Инициализация, потоки, таймеры</span><span class="sxs-lookup"><span data-stu-id="d7262-868">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-869">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-869">Preemption Possible</span></span>

<span data-ttu-id="d7262-870">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-870">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-871">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-871">Example</span></span>

```C
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-872">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-872">See Also</span></span>

- <span data-ttu-id="d7262-873">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-873">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="d7262-874">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="d7262-874">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="d7262-875">nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable,</span><span class="sxs-lookup"><span data-stu-id="d7262-875">nx_ip_driver_interface_direct_command, nx_ip_forwarding_enable,</span></span>
- <span data-ttu-id="d7262-876">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-876">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="d7262-877">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="d7262-877">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_forwarding_enable"></a><span data-ttu-id="d7262-878">nx_ip_forwarding_enable</span><span class="sxs-lookup"><span data-stu-id="d7262-878">nx_ip_forwarding_enable</span></span>

<span data-ttu-id="d7262-879">Включение переадресации IP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-879">Enable IP packet forwarding</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-880">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-880">Prototype</span></span>

```C
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-881">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-881">Description</span></span>

<span data-ttu-id="d7262-882">Эта служба включает переадресацию IP-пакетов внутри IP-компонента NetX.</span><span class="sxs-lookup"><span data-stu-id="d7262-882">This service enables forwarding IP packets inside the NetX IP component.</span></span> <span data-ttu-id="d7262-883">При создании задачи IP эта служба автоматически отключается.</span><span class="sxs-lookup"><span data-stu-id="d7262-883">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-884">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-884">Parameters</span></span>

- <span data-ttu-id="d7262-885">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-885">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-886">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-886">Return Values</span></span>
- <span data-ttu-id="d7262-887">**NX_SUCCESS** (0x00) — успешное включение переадресации IP-пакетов.</span><span class="sxs-lookup"><span data-stu-id="d7262-887">**NX_SUCCESS** (0x00) Successful IP forwarding enable.</span></span>
- <span data-ttu-id="d7262-888">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-888">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-889">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-889">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-890">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-890">Allowed From</span></span>

<span data-ttu-id="d7262-891">Инициализация, потоки, таймеры</span><span class="sxs-lookup"><span data-stu-id="d7262-891">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-892">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-892">Preemption Possible</span></span>

<span data-ttu-id="d7262-893">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-893">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-894">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-894">Example</span></span>

```C
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-895">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-895">See Also</span></span>

- <span data-ttu-id="d7262-896">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-896">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="d7262-897">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="d7262-897">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="d7262-898">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-898">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="d7262-899">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-899">nx_ip_fragment_disable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="d7262-900">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="d7262-900">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_fragment_disable"></a><span data-ttu-id="d7262-901">nx_ip_fragment_disable</span><span class="sxs-lookup"><span data-stu-id="d7262-901">nx_ip_fragment_disable</span></span>

<span data-ttu-id="d7262-902">Отключение фрагментации IP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-902">Disable IP packet fragmenting</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-903">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-903">Prototype</span></span>

```C
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-904">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-904">Description</span></span>

<span data-ttu-id="d7262-905">Эта служба отключает возможность фрагментации и повторной сборки IP-пакетов.</span><span class="sxs-lookup"><span data-stu-id="d7262-905">This service disables IP packet fragmenting and reassembling functionality.</span></span> <span data-ttu-id="d7262-906">Пакеты, ожидающие повторной сборки, освобождаются.</span><span class="sxs-lookup"><span data-stu-id="d7262-906">For packets waiting to be reassembled, this service releases these packets.</span></span> <span data-ttu-id="d7262-907">При создании задачи IP эта служба автоматически отключается.</span><span class="sxs-lookup"><span data-stu-id="d7262-907">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-908">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-908">Parameters</span></span>

- <span data-ttu-id="d7262-909">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-909">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-910">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-910">Return Values</span></span>
- <span data-ttu-id="d7262-911">**NX_SUCCESS** (0x00) — успешное отключение фрагментации IP-пакетов.</span><span class="sxs-lookup"><span data-stu-id="d7262-911">**NX_SUCCESS** (0x00) Successful IP fragment disable.</span></span>
- <span data-ttu-id="d7262-912">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-912">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-913">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-913">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-914">**NX_NOT_ENABLED** (0x14) — фрагментация IP-пакетов не включена в экземпляре IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-914">**NX_NOT_ENABLED** (0x14) IP Fragmentation is not enabled on the IP instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-915">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-915">Allowed From</span></span>

<span data-ttu-id="d7262-916">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-916">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-917">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-917">Preemption Possible</span></span>

<span data-ttu-id="d7262-918">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-918">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-919">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-919">Example</span></span>

```C
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-920">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-920">See Also</span></span>

- <span data-ttu-id="d7262-921">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-921">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="d7262-922">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="d7262-922">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="d7262-923">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-923">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="d7262-924">nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-924">nx_ip_forwarding_enable, nx_ip_fragment_enable, nx_ip_info_get,</span></span>
- <span data-ttu-id="d7262-925">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="d7262-925">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_fragment_enable"></a><span data-ttu-id="d7262-926">nx_ip_fragment_enable</span><span class="sxs-lookup"><span data-stu-id="d7262-926">nx_ip_fragment_enable</span></span>

<span data-ttu-id="d7262-927">Включение фрагментации IP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-927">Enable IP packet fragmenting</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-928">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-928">Prototype</span></span>

```C
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-929">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-929">Description</span></span>

<span data-ttu-id="d7262-930">Эта служба включает возможность фрагментации и повторной сборки IP-пакетов.</span><span class="sxs-lookup"><span data-stu-id="d7262-930">This service enables IP packet fragmenting and reassembling functionality.</span></span> <span data-ttu-id="d7262-931">При создании задачи IP эта служба автоматически отключается.</span><span class="sxs-lookup"><span data-stu-id="d7262-931">On creation of the IP task, this service is automatically disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-932">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-932">Parameters</span></span>

- <span data-ttu-id="d7262-933">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-933">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-934">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-934">Return Values</span></span>

- <span data-ttu-id="d7262-935">**NX_SUCCESS** (0x00) — успешное включение фрагментации IP-пакетов.</span><span class="sxs-lookup"><span data-stu-id="d7262-935">**NX_SUCCESS** (0x00) Successful IP fragment enable.</span></span>
- <span data-ttu-id="d7262-936">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-936">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-937">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-937">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-938">**NX_NOT_ENABLED** (0x14) — функции фрагментации IP-пакетов не компилируются в NetX.</span><span class="sxs-lookup"><span data-stu-id="d7262-938">**NX_NOT_ENABLED** (0x14) IP Fragmentation features is not compiled into NetX.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-939">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-939">Allowed From</span></span>

<span data-ttu-id="d7262-940">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-940">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-941">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-941">Preemption Possible</span></span>

<span data-ttu-id="d7262-942">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-942">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-943">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-943">Example</span></span>

```C
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
    previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-944">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-944">See Also</span></span>

- <span data-ttu-id="d7262-945">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-945">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="d7262-946">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="d7262-946">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="d7262-947">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-947">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="d7262-948">nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-948">nx_ip_forwarding_enable, nx_ip_fragment_disable, nx_ip_info_get,</span></span>
- <span data-ttu-id="d7262-949">nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="d7262-949">nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_gateway_address_set"></a><span data-ttu-id="d7262-950">nx_ip_gateway_address_set</span><span class="sxs-lookup"><span data-stu-id="d7262-950">nx_ip_gateway_address_set</span></span>

<span data-ttu-id="d7262-951">Задание IP-адреса шлюза</span><span class="sxs-lookup"><span data-stu-id="d7262-951">Set Gateway IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-952">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-952">Prototype</span></span>

```C
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```

### <a name="description"></a><span data-ttu-id="d7262-953">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-953">Description</span></span>

<span data-ttu-id="d7262-954">Эта служба задает IP-адрес шлюза IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-954">This service sets the IP gateway IP address.</span></span> <span data-ttu-id="d7262-955">Весь трафик, исходящий из сети, направляется в этот шлюз для передачи.</span><span class="sxs-lookup"><span data-stu-id="d7262-955">All out-of-network traffic are routed to this gateway for transmission.</span></span> <span data-ttu-id="d7262-956">Шлюз должен быть доступен напрямую через один из сетевых интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="d7262-956">The gateway must be directly accessible through one of the network interfaces.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-957">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-957">Parameters</span></span>

- <span data-ttu-id="d7262-958">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-958">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-959">**ip_address**: IP-адрес шлюза</span><span class="sxs-lookup"><span data-stu-id="d7262-959">**ip_address** IP address of the gateway.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-960">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-960">Return Values</span></span>

- <span data-ttu-id="d7262-961">**NX_SUCCESS** (0x00) — IP-адрес шлюза успешно задан.</span><span class="sxs-lookup"><span data-stu-id="d7262-961">**NX_SUCCESS** (0x00) Successful Gateway IP address set.</span></span>
- <span data-ttu-id="d7262-962">**NX_PTR_ERROR** (0x07) — недопустимый указатель на экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-962">**NX_PTR_ERROR** (0x07) Invalid IP instance pointer.</span></span>
- <span data-ttu-id="d7262-963">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d7262-963">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="d7262-964">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-964">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-965">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-965">Allowed From</span></span>

<span data-ttu-id="d7262-966">Инициализация, поток</span><span class="sxs-lookup"><span data-stu-id="d7262-966">Initialization, thread</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-967">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-967">Preemption Possible</span></span>

<span data-ttu-id="d7262-968">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-968">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-969">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-969">Example</span></span>

```C
/* Setup the Gateway address for previously created IP
    Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99));

/* If status is NX_SUCCESS, all out-of-network send requests are
    routed to 1.2.3.99. */
```
### <a name="see-also"></a><span data-ttu-id="d7262-970">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-970">See Also</span></span>

- <span data-ttu-id="d7262-971">nx_ip_info_get, nx_ip_static_route_add, nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-971">nx_ip_info_get, nx_ip_static_route_add, nx_ip_static_route_delete</span></span>

## <a name="nx_ip_info_get"></a><span data-ttu-id="d7262-972">nx_ip_info_get</span><span class="sxs-lookup"><span data-stu-id="d7262-972">nx_ip_info_get</span></span>

<span data-ttu-id="d7262-973">Получение сведений о действиях IP</span><span class="sxs-lookup"><span data-stu-id="d7262-973">Retrieve information about IP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-974">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-974">Prototype</span></span>

```C
UINT nx_ip_info_get(
    NX_IP *ip_ptr,
    ULONG *ip_total_packets_sent,
    ULONG *ip_total_bytes_sent,
    ULONG *ip_total_packets_received,
    ULONG *ip_total_bytes_received,
    ULONG *ip_invalid_packets,
    ULONG *ip_receive_packets_dropped,
    ULONG *ip_receive_checksum_errors,
    ULONG *ip_send_packets_dropped,
    ULONG *ip_total_fragments_sent,
    ULONG *ip_total_fragments_received);
```

### <a name="description"></a><span data-ttu-id="d7262-975">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-975">Description</span></span>

<span data-ttu-id="d7262-976">Эта служба получает сведения о действиях протокола IP для указанного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-976">This service retrieves information about IP activities for the specified IP instance.</span></span>

<span data-ttu-id="d7262-977">*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.</span><span class="sxs-lookup"><span data-stu-id="d7262-977">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-978">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-978">Parameters</span></span>

- <span data-ttu-id="d7262-979">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-979">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-980">**ip_total_packets_sent**: указатель на место назначения для общего числа отправленных IP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-980">**ip_total_packets_sent** Pointer to destination for the total number of IP packets sent.</span></span>
- <span data-ttu-id="d7262-981">**ip_total_bytes_sent**: указатель на место назначения для общего числа отправленных байтов</span><span class="sxs-lookup"><span data-stu-id="d7262-981">**ip_total_bytes_sent** Pointer to destination for the total number of bytes sent.</span></span>
- <span data-ttu-id="d7262-982">**ip_total_packets_received**: указатель на место назначения для общего числа полученных IP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-982">**ip_total_packets_received** Pointer to destination of the total number of IP receive packets.</span></span>
- <span data-ttu-id="d7262-983">**ip_total_bytes_received**: указатель на место назначения для общего числа полученных по IP байтов</span><span class="sxs-lookup"><span data-stu-id="d7262-983">**ip_total_bytes_received** Pointer to destination of the total number of IP bytes received.</span></span>
- <span data-ttu-id="d7262-984">**ip_invalid_packets**: указатель на место назначения для общего числа недопустимых IP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-984">**ip_invalid_packets** Pointer to destination of the total number of invalid IP packets.</span></span>
- <span data-ttu-id="d7262-985">**ip_receive_packets_dropped**: указатель на место назначения для общего числа полученных и отброшенных пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-985">**ip_receive_packets_dropped** Pointer to destination of the total number of receive packets dropped.</span></span>
- <span data-ttu-id="d7262-986">**ip_receive_checksum_errors**: указатель на место назначения для общего числа ошибок контрольной суммы в полученных пакетах</span><span class="sxs-lookup"><span data-stu-id="d7262-986">**ip_receive_checksum_errors** Pointer to destination of the total number of checksum errors in receive packets.</span></span>
- <span data-ttu-id="d7262-987">**ip_send_packets_dropped**: указатель на место назначения для общего числа отправленных и отброшенных пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-987">**ip_send_packets_dropped** Pointer to destination of the total number of send packets dropped.</span></span>
- <span data-ttu-id="d7262-988">**ip_total_fragments_sent**: указатель на место назначения для общего числа отправленных фрагментов</span><span class="sxs-lookup"><span data-stu-id="d7262-988">**ip_total_fragments_sent** Pointer to destination of the total number of fragments sent.</span></span>
- <span data-ttu-id="d7262-989">**ip_total_fragments_received**: указатель на место назначения для общего числа полученных фрагментов</span><span class="sxs-lookup"><span data-stu-id="d7262-989">**ip_total_fragments_received** Pointer to destination of the total number of fragments received.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-990">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-990">Return Values</span></span>

- <span data-ttu-id="d7262-991">**NX_SUCCESS** (0x00) — успешное получение сведений IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-991">**NX_SUCCESS** (0x00) Successful IP information retrieval.</span></span>
- <span data-ttu-id="d7262-992">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-992">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-993">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-993">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-994">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-994">Allowed From</span></span>

<span data-ttu-id="d7262-995">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-995">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-996">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-996">Preemption Possible</span></span>

<span data-ttu-id="d7262-997">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-997">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-998">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-998">Example</span></span>

```C
/* Retrieve IP information from previously created IP
Instance 0. */
status = nx_ip_info_get(&ip_0,
    &ip_total_packets_sent,
    &ip_total_bytes_sent,
    &ip_total_packets_received,
    &ip_total_bytes_received,
    &ip_invalid_packets,
    &ip_receive_packets_dropped,
    &ip_receive_checksum_errors,
    &ip_send_packets_dropped,
    &ip_total_fragments_sent,
    &ip_total_fragments_received);

/* If status is NX_SUCCESS, IP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-999">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-999">See Also</span></span>

- <span data-ttu-id="d7262-1000">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-1000">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="d7262-1001">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="d7262-1001">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="d7262-1002">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-1002">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="d7262-1003">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-1003">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="d7262-1004">nx_ip_fragment_enable, nx_ip_status_check, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="d7262-1004">nx_ip_fragment_enable, nx_ip_status_check, nx_system_initialize</span></span>

## <a name="nx_ip_interface_address_get"></a><span data-ttu-id="d7262-1005">nx_ip_interface_address_get</span><span class="sxs-lookup"><span data-stu-id="d7262-1005">nx_ip_interface_address_get</span></span>

<span data-ttu-id="d7262-1006">Получение IP-адреса интерфейса</span><span class="sxs-lookup"><span data-stu-id="d7262-1006">Retrieve interface IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1007">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1007">Prototype</span></span>

```C
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```

### <a name="description"></a><span data-ttu-id="d7262-1008">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1008">Description</span></span>

<span data-ttu-id="d7262-1009">Эта служба получает IP-адрес указанного сетевого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d7262-1009">This service retrieves the IP address of a specified network interface.</span></span>

<span data-ttu-id="d7262-1010">*Указанное устройство, если оно не является основным, должно быть предварительно подключено к экземпляру IP.*</span><span class="sxs-lookup"><span data-stu-id="d7262-1010">*The specified device, if not the primary device, must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1011">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1011">Parameters</span></span>

- <span data-ttu-id="d7262-1012">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1012">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-1013">**interface_index**: индекс интерфейса; совпадает с индексом сетевого интерфейса, подключенного к экземпляру IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1013">**interface_index** Interface index, the same value as the index to the network interface attached to the IP instance.</span></span>
- <span data-ttu-id="d7262-1014">**ip_address**: указатель на место назначения для IP-адреса интерфейса устройства</span><span class="sxs-lookup"><span data-stu-id="d7262-1014">**ip_address** Pointer to destination for the device interface IP address.</span></span>
- <span data-ttu-id="d7262-1015">**network_mask**: указатель на место назначения для маски сети интерфейса устройства</span><span class="sxs-lookup"><span data-stu-id="d7262-1015">**network_mask** Pointer to destination for the device interface network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1016">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1016">Return Values</span></span>

- <span data-ttu-id="d7262-1017">**NX_SUCCESS** (0x00) — успешное получение IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-1017">**NX_SUCCESS** (0x00) Successful IP address get.</span></span>
- <span data-ttu-id="d7262-1018">**NX_INVALID_INTERFACE** (0x4C) — указан недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d7262-1018">**NX_INVALID_INTERFACE** (0x4C) Specified network interface is invalid.</span></span>
- <span data-ttu-id="d7262-1019">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1019">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-1020">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-1020">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1021">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1021">Allowed From</span></span>

<span data-ttu-id="d7262-1022">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1022">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1023">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1023">Preemption Possible</span></span>

<span data-ttu-id="d7262-1024">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1024">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1025">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1025">Example</span></span>

```C
#define INTERFACE_INDEX 1
/* Get device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
    &ip_address, &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
    retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1026">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1026">See Also</span></span>

- <span data-ttu-id="d7262-1027">nx_ip_interface_address_set, nx_ip_interface_attach,</span><span class="sxs-lookup"><span data-stu-id="d7262-1027">nx_ip_interface_address_set, nx_ip_interface_attach,</span></span>
- <span data-ttu-id="d7262-1028">nx_ip_interface_info_get, nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="d7262-1028">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="d7262-1029">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="d7262-1029">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_address_set"></a><span data-ttu-id="d7262-1030">nx_ip_interface_address_set</span><span class="sxs-lookup"><span data-stu-id="d7262-1030">nx_ip_interface_address_set</span></span>

<span data-ttu-id="d7262-1031">Задание IP-адреса и маски сети интерфейса</span><span class="sxs-lookup"><span data-stu-id="d7262-1031">Set interface IP address and network mask</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1032">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1032">Prototype</span></span>

```C
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```

### <a name="description"></a><span data-ttu-id="d7262-1033">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1033">Description</span></span>

<span data-ttu-id="d7262-1034">Эта служба задает IP-адрес и маску сети для указанного интерфейса IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-1034">This service sets the IP address and network mask for the specified IP interface.</span></span>

<span data-ttu-id="d7262-1035">*Указанный интерфейс должен быть предварительно подключен к экземпляру IP.*</span><span class="sxs-lookup"><span data-stu-id="d7262-1035">*The specified interface must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1036">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1036">Parameters</span></span>

- <span data-ttu-id="d7262-1037">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1037">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-1038">**interface_index**: индекс интерфейса, присоединенного к экземпляру NetX</span><span class="sxs-lookup"><span data-stu-id="d7262-1038">**interface_index** Index of the interface attached to the NetX instance.</span></span>
- <span data-ttu-id="d7262-1039">**ip_address**: новый IP-адрес сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="d7262-1039">**ip_address** New network interface IP address.</span></span>
- <span data-ttu-id="d7262-1040">**network_mask**: новая маска сети интерфейса</span><span class="sxs-lookup"><span data-stu-id="d7262-1040">**network_mask** New interface network mask.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1041">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1041">Return Values</span></span>

- <span data-ttu-id="d7262-1042">**NX_SUCCESS** (0x00) — успешный набор IP-адресов.</span><span class="sxs-lookup"><span data-stu-id="d7262-1042">**NX_SUCCESS** (0x00) Successful IP address set.</span></span>
- <span data-ttu-id="d7262-1043">**NX_INVALID_INTERFACE** (0x4C) — указан недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d7262-1043">**NX_INVALID_INTERFACE** (0x4C) Specified network interface is invalid.</span></span>
- <span data-ttu-id="d7262-1044">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1044">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-1045">**NX_PTR_ERROR** (0x07) — недопустимые указатели.</span><span class="sxs-lookup"><span data-stu-id="d7262-1045">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="d7262-1046">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d7262-1046">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1047">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1047">Allowed From</span></span>

<span data-ttu-id="d7262-1048">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1048">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1049">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1049">Preemption Possible</span></span>

<span data-ttu-id="d7262-1050">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1050">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1051">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1051">Example</span></span>

```C
#define INTERFACE_INDEX 1
/* Set device IP address and network mask for the specified
    interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
    ip_address, network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1052">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1052">See Also</span></span>

- <span data-ttu-id="d7262-1053">nx_ip_interface_address_get, nx_ip_interface_attach,</span><span class="sxs-lookup"><span data-stu-id="d7262-1053">nx_ip_interface_address_get, nx_ip_interface_attach,</span></span>
- <span data-ttu-id="d7262-1054">nx_ip_interface_info_get, nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="d7262-1054">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="d7262-1055">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="d7262-1055">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_attach"></a><span data-ttu-id="d7262-1056">nx_ip_interface_attach</span><span class="sxs-lookup"><span data-stu-id="d7262-1056">nx_ip_interface_attach</span></span>

<span data-ttu-id="d7262-1057">Подключение сетевого интерфейса к экземпляру IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1057">Attach network interface to IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1058">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1058">Prototype</span></span>

```C
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)
    (struct NX_IP_DRIVER_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="d7262-1059">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1059">Description</span></span>

<span data-ttu-id="d7262-1060">Эта служба добавляет физический сетевой интерфейс к интерфейсу IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-1060">This service adds a physical network interface to the IP interface.</span></span> <span data-ttu-id="d7262-1061">Обратите внимание, что экземпляр IP создается с основным интерфейсом, поэтому каждый следующий интерфейс является дополнительным для него.</span><span class="sxs-lookup"><span data-stu-id="d7262-1061">Note the IP instance is created with the primary interface so each additional interface is secondary to the primary interface.</span></span> <span data-ttu-id="d7262-1062">Общее число сетевых интерфейсов, подключенных к экземпляру IP (включая основной интерфейс), не может превышать **NX_MAX_PHYSICAL_INTERFACES**.</span><span class="sxs-lookup"><span data-stu-id="d7262-1062">The total number of network interfaces attached to the IP instance (including the primary interface) cannot exceed **NX_MAX_PHYSICAL_INTERFACES**.</span></span>

<span data-ttu-id="d7262-1063">Если поток IP еще не запущен, дополнительные интерфейсы будут инициализированы в процессе запуска потока IP, который инициализирует все физические интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1063">If the IP thread has not been running yet, the secondary interfaces will be initialized as part of the IP thread startup process that initializes all physical interfaces.</span></span>

<span data-ttu-id="d7262-1064">Если поток IP еще не запущен, дополнительный интерфейс инициализируется службой ***nx_ip_interface_attach***.</span><span class="sxs-lookup"><span data-stu-id="d7262-1064">If the IP thread is not running yet, the secondary interface is initialized as part of the ***nx_ip_interface_attach*** service.</span></span>

<span data-ttu-id="d7262-1065">*ip_ptr должен указывать на допустимую структуру IP в NetX.*</span><span class="sxs-lookup"><span data-stu-id="d7262-1065">*ip_ptr must point to a valid NetX IP structure.*</span></span>

- <span data-ttu-id="d7262-1066">*В **NX_MAX_PHYSICAL_INTERFACES** необходимо указать количество сетевых интерфейсов для экземпляра IP. Значение по умолчанию — 1.*</span><span class="sxs-lookup"><span data-stu-id="d7262-1066">***NX_MAX_PHYSICAL_INTERFACES** must be configured for the number of network interfaces for the IP instance. The default value is one.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1067">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1067">Parameters</span></span>

- <span data-ttu-id="d7262-1068">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1068">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-1069">**interface_name**: указатель на строку с именем интерфейса</span><span class="sxs-lookup"><span data-stu-id="d7262-1069">**interface_name** Pointer to interface name string.</span></span>
- <span data-ttu-id="d7262-1070">**ip_address**: IP-адрес устройства в порядке байтов узла</span><span class="sxs-lookup"><span data-stu-id="d7262-1070">**ip_address** Device IP address in host byte order.</span></span>
- <span data-ttu-id="d7262-1071">**network_mask**: маска сети устройства в порядке байтов узла</span><span class="sxs-lookup"><span data-stu-id="d7262-1071">**network_mask** Device network mask in host byte order.</span></span>
- <span data-ttu-id="d7262-1072">**ip_link_driver**: драйвер Ethernet для интерфейса</span><span class="sxs-lookup"><span data-stu-id="d7262-1072">**ip_link_driver** Ethernet driver for the interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1073">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1073">Return Values</span></span>

- <span data-ttu-id="d7262-1074">**NX_SUCCESS** (0x00) — запись добавлена в таблицу статической маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="d7262-1074">**NX_SUCCESS** (0x00) Entry is added to static routing table.</span></span>
- <span data-ttu-id="d7262-1075">**NX_NO_MORE_ENTRIES** (0x17) — максимальное число интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="d7262-1075">**NX_NO_MORE_ENTRIES** (0x17) Max number of interfaces.</span></span>
- <span data-ttu-id="d7262-1076">Превышено значение **NX_MAX_PHYSICAL_INTERFACES**.</span><span class="sxs-lookup"><span data-stu-id="d7262-1076">**NX_MAX_PHYSICAL_INTERFACES** is exceeded.</span></span>
- <span data-ttu-id="d7262-1077">**NX_DUPLICATED_ENTRY** (0x52) — указанный IP-адрес уже используется в этом экземпляре IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-1077">**NX_DUPLICATED_ENTRY** (0x52) The supplied IP address is already used on this IP instance.</span></span>
- <span data-ttu-id="d7262-1078">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1078">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-1079">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="d7262-1079">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="d7262-1080">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимые входные данные IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-1080">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address input.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1081">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1081">Allowed From</span></span>

<span data-ttu-id="d7262-1082">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1082">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1083">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1083">Preemption Possible</span></span>

<span data-ttu-id="d7262-1084">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1084">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1085">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1085">Example</span></span>

```C
/* Attach secondary device for device IP address 192.168.1.68 with
    the specified Ethernet driver. */
status = nx_ip_interface_attach(ip_ptr, “secondary_port”,
    IP_ADDRESS(192,168,1,68),
    0xFFFFFF00UL,
    nx_etherDriver);
/* If status is NX_SUCCESS the interface was successfully added to
    the IP instance interface table. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1086">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1086">See Also</span></span>

- <span data-ttu-id="d7262-1087">nx_ip_interface_address_get, nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-1087">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="d7262-1088">nx_ip_interface_info_get, nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="d7262-1088">nx_ip_interface_info_get, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="d7262-1089">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="d7262-1089">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_info_get"></a><span data-ttu-id="d7262-1090">nx_ip_interface_info_get</span><span class="sxs-lookup"><span data-stu-id="d7262-1090">nx_ip_interface_info_get</span></span>

<span data-ttu-id="d7262-1091">Получение параметров сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="d7262-1091">Retrieve network interface parameters</span></span>


### <a name="prototype"></a><span data-ttu-id="d7262-1092">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1092">Prototype</span></span>

```C
UINT nx_ip_interface_info_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    CHAR **interface_name,
    ULONG *ip_address,
    ULONG *network_mask,
    ULONG *mtu_size,
    ULONG *physical_address_msw,
    ULONG *physical_address_lsw);
```

### <a name="description"></a><span data-ttu-id="d7262-1093">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1093">Description</span></span>

<span data-ttu-id="d7262-1094">Эта служба получает сведения о параметрах сети для указанного сетевого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d7262-1094">This service retrieves information on network parameters for the specified network interface.</span></span> <span data-ttu-id="d7262-1095">Все данные извлекаются в порядке байтов узла.</span><span class="sxs-lookup"><span data-stu-id="d7262-1095">All data are retrieved in host byte order.</span></span>

<span data-ttu-id="d7262-1096">*Указатель ip_ptr должен указывать на допустимую структуру IP в NetX. Указанный интерфейс, если он не является основным, должен быть предварительно подключен к экземпляру IP.*</span><span class="sxs-lookup"><span data-stu-id="d7262-1096">*ip_ptr must point to a valid NetX IP structure. The specified interface, if not the primary interface, must be previously attached to the IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1097">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1097">Parameters</span></span>

- <span data-ttu-id="d7262-1098">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1098">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-1099">**interface_index**: индекс, указывающий сетевой интерфейс</span><span class="sxs-lookup"><span data-stu-id="d7262-1099">**interface_index** Index specifying network interface.</span></span>
- <span data-ttu-id="d7262-1100">**interface_name**: указатель на буфер, содержащий имя сетевого интерфейса</span><span class="sxs-lookup"><span data-stu-id="d7262-1100">**interface_name** Pointer to the buffer that holds the name of the network interface.</span></span>
- <span data-ttu-id="d7262-1101">**ip_address**: указатель на место назначения для IP-адреса интерфейса</span><span class="sxs-lookup"><span data-stu-id="d7262-1101">**ip_address** Pointer to the destination for the IP address of the interface.</span></span>
- <span data-ttu-id="d7262-1102">**network_mask**: указатель места назначения для маски сети</span><span class="sxs-lookup"><span data-stu-id="d7262-1102">**network_mask** Pointer to destination for network mask.</span></span>
- <span data-ttu-id="d7262-1103">**mtu_size**: указатель на место назначения максимальной единицы передачи для этого интерфейса</span><span class="sxs-lookup"><span data-stu-id="d7262-1103">**mtu_size** Pointer to destination for maximum transfer unit for this interface.</span></span>
- <span data-ttu-id="d7262-1104">**physical_address_msw**: указатель места назначения для старших 16 бит MAC-адреса устройства</span><span class="sxs-lookup"><span data-stu-id="d7262-1104">**physical_address_msw** Pointer to destination for top 16 bits of the device MAC address.</span></span>
- <span data-ttu-id="d7262-1105">**physical_address_lsw**: указатель места назначения для младших 32 бит MAC-адреса устройства</span><span class="sxs-lookup"><span data-stu-id="d7262-1105">**physical_address_lsw** Pointer to destination for lower 32 bits of the device MAC address.</span></span>


### <a name="return-values"></a><span data-ttu-id="d7262-1106">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1106">Return Values</span></span>
- <span data-ttu-id="d7262-1107">**NX_SUCCESS** (0x00) — сведения об интерфейсе получены.</span><span class="sxs-lookup"><span data-stu-id="d7262-1107">**NX_SUCCESS** (0x00) Interface information has been obtained.</span></span>
- <span data-ttu-id="d7262-1108">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="d7262-1108">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="d7262-1109">**NX_INVALID_INTERFACE** (0x4C) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-1109">**NX_INVALID_INTERFACE** (0x4C) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-1110">**NX_CALLER_ERROR** (0x11) — служба не вызывается из инициализации системы или контекста потока.</span><span class="sxs-lookup"><span data-stu-id="d7262-1110">**NX_CALLER_ERROR** (0x11) Service is not called from system initialization or thread context.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1111">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1111">Allowed From</span></span>

<span data-ttu-id="d7262-1112">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1112">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1113">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1113">Preemption Possible</span></span>

<span data-ttu-id="d7262-1114">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1114">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1115">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1115">Example</span></span>

```C
/* Retrieve interface parameters for the specified interface (index
    1 in IP instance list of interfaces). */
#define INTERFACE_INDEX 1

status = nx_ip_interface_info_get(ip_ptr, INTERFACE_INDEX,
    &name_ptr, &ip_address,
    &network_mask,
    &mtu_size,
    &physical_address_msw,
    &physical_address_lsw);

/* If status is NX_SUCCESS the interface information is
    successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1116">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1116">See Also</span></span>

- <span data-ttu-id="d7262-1117">nx_ip_interface_address_get, nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-1117">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="d7262-1118">nx_ip_interface_attach, nx_ip_interface_status_check,</span><span class="sxs-lookup"><span data-stu-id="d7262-1118">nx_ip_interface_attach, nx_ip_interface_status_check,</span></span>
- <span data-ttu-id="d7262-1119">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="d7262-1119">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_interface_status_check"></a><span data-ttu-id="d7262-1120">nx_ip_interface_status_check</span><span class="sxs-lookup"><span data-stu-id="d7262-1120">nx_ip_interface_status_check</span></span>

<span data-ttu-id="d7262-1121">Проверка состояния экземпляра IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1121">Check status of an IP instance</span></span>


### <a name="prototype"></a><span data-ttu-id="d7262-1122">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1122">Prototype</span></span>

```C
UINT nx_ip_interface_status_check(
    NX_IP *ip_ptr,
    UINT interface_index
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d7262-1123">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1123">Description</span></span>

<span data-ttu-id="d7262-1124">Эта служба проверяет и при необходимости ожидает указанное состояние сетевого интерфейса ранее созданного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-1124">This service checks and optionally waits for the specified status of the network interface of a previously created IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1125">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1125">Parameters</span></span>

- <span data-ttu-id="d7262-1126">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1126">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-1127">**interface_index**: номер индекса интерфейса</span><span class="sxs-lookup"><span data-stu-id="d7262-1127">**interface_index** Interface index number</span></span>
- <span data-ttu-id="d7262-1128">**needed_status**: запрошенное состояние IP, определенное в виде битовой карты следующим образом</span><span class="sxs-lookup"><span data-stu-id="d7262-1128">**needed_status** IP status requested, defined in bit-map form as follows:</span></span>
    - <span data-ttu-id="d7262-1129">NX_IP_INITIALIZE_DONE (0x0001)</span><span class="sxs-lookup"><span data-stu-id="d7262-1129">NX_IP_INITIALIZE_DONE (0x0001)</span></span>
    - <span data-ttu-id="d7262-1130">NX_IP_ADDRESS_RESOLVED (0x0002)</span><span class="sxs-lookup"><span data-stu-id="d7262-1130">NX_IP_ADDRESS_RESOLVED (0x0002)</span></span>
    - <span data-ttu-id="d7262-1131">NX_IP_LINK_ENABLED (0x0004)</span><span class="sxs-lookup"><span data-stu-id="d7262-1131">NX_IP_LINK_ENABLED (0x0004)</span></span>
    - <span data-ttu-id="d7262-1132">NX_IP_ARP_ENABLED (0x0008)</span><span class="sxs-lookup"><span data-stu-id="d7262-1132">NX_IP_ARP_ENABLED (0x0008)</span></span>
    - <span data-ttu-id="d7262-1133">NX_IP_UDP_ENABLED (0x0010)</span><span class="sxs-lookup"><span data-stu-id="d7262-1133">NX_IP_UDP_ENABLED (0x0010)</span></span>
    - <span data-ttu-id="d7262-1134">NX_IP_TCP_ENABLED (0x0020)</span><span class="sxs-lookup"><span data-stu-id="d7262-1134">NX_IP_TCP_ENABLED (0x0020)</span></span>
    - <span data-ttu-id="d7262-1135">NX_IP_IGMP_ENABLED (0x0040)</span><span class="sxs-lookup"><span data-stu-id="d7262-1135">NX_IP_IGMP_ENABLED (0x0040)</span></span>
    - <span data-ttu-id="d7262-1136">NX_IP_RARP_COMPLETE (0x0080)</span><span class="sxs-lookup"><span data-stu-id="d7262-1136">NX_IP_RARP_COMPLETE (0x0080)</span></span>
    - <span data-ttu-id="d7262-1137">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span><span class="sxs-lookup"><span data-stu-id="d7262-1137">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span></span>
- <span data-ttu-id="d7262-1138">**actual_status**: указатель на место назначения фактического набора битов</span><span class="sxs-lookup"><span data-stu-id="d7262-1138">**actual_status** Pointer to destination of actual bits set.</span></span>
- <span data-ttu-id="d7262-1139">**wait_option**: определяет поведение службы в случае, если запрошенные биты состояния недоступны</span><span class="sxs-lookup"><span data-stu-id="d7262-1139">**wait_option** Defines how the service behaves if the requested status bits are not available.</span></span> <span data-ttu-id="d7262-1140">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d7262-1140">The wait options are defined as follows:</span></span>
    - <span data-ttu-id="d7262-1141">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-1141">NX_NO_WAIT (0x00000000)</span></span>
    - <span data-ttu-id="d7262-1142">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-1142">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
    - <span data-ttu-id="d7262-1143">Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d7262-1143">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1144">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1144">Return Values</span></span>

- <span data-ttu-id="d7262-1145">**NX_SUCCESS** (0x00) — успешная проверка состояния IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-1145">**NX_SUCCESS** (0x00) Successful IP status check.</span></span>
- <span data-ttu-id="d7262-1146">**NX_NOT_SUCCESSFUL** (0x43) — запрос состояния не был выполнен в течение указанного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="d7262-1146">**NX_NOT_SUCCESSFUL** (0x43) Status request was not satisfied within the timeout specified.</span></span>
- <span data-ttu-id="d7262-1147">**NX_PTR_ERROR** (0x07) — указатель IP является или стал недопустимым, либо недопустимый указатель фактического состояния.</span><span class="sxs-lookup"><span data-stu-id="d7262-1147">**NX_PTR_ERROR** (0x07) IP pointer is or has become invalid, or actual status pointer is invalid.</span></span>
- <span data-ttu-id="d7262-1148">**NX_OPTION_ERROR** (0x0a) — недопустимый параметр требуемого состояния.</span><span class="sxs-lookup"><span data-stu-id="d7262-1148">**NX_OPTION_ERROR** (0x0a) Invalid needed status option.</span></span>
- <span data-ttu-id="d7262-1149">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1149">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-1150">**NX_INVALID_INTERFACE** (0x4C) — индекс интерфейса за пределами допустимого диапазона,</span><span class="sxs-lookup"><span data-stu-id="d7262-1150">**NX_INVALID_INTERFACE** (0x4C) Interface_index is out of range.</span></span> <span data-ttu-id="d7262-1151">либо недопустимый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d7262-1151">or the interface is not valid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1152">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1152">Allowed From</span></span>

<span data-ttu-id="d7262-1153">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1153">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1154">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1154">Preemption Possible</span></span>

<span data-ttu-id="d7262-1155">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1155">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1156">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1156">Example</span></span>

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
    instance is up. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1157">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1157">See Also</span></span>

- <span data-ttu-id="d7262-1158">nx_ip_interface_address_get, nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-1158">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="d7262-1159">nx_ip_interface_attach, nx_ip_interface_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-1159">nx_ip_interface_attach, nx_ip_interface_info_get,</span></span>
- <span data-ttu-id="d7262-1160">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="d7262-1160">nx_ip_link_status_change_notify_set</span></span>

## <a name="nx_ip_link_status_change_notify_set"></a><span data-ttu-id="d7262-1161">nx_ip_link_status_change_notify_set</span><span class="sxs-lookup"><span data-stu-id="d7262-1161">nx_ip_link_status_change_notify_set</span></span>

<span data-ttu-id="d7262-1162">Задание функции обратного вызова для уведомления об изменении состояния канала</span><span class="sxs-lookup"><span data-stu-id="d7262-1162">Set the link status change notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1163">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1163">Prototype</span></span>

```C
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID (*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
```

### <a name="description"></a><span data-ttu-id="d7262-1164">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1164">Description</span></span>

<span data-ttu-id="d7262-1165">Эта служба настраивает функцию обратного вызова для уведомления об изменении состояния канала.</span><span class="sxs-lookup"><span data-stu-id="d7262-1165">This service configures the link status change notify callback function.</span></span> <span data-ttu-id="d7262-1166">Указанная пользователем подпрограмма *link_status_change_notify* вызывается при изменении состояния основного или дополнительного интерфейса (например, при изменении IP-адреса). Если *link_status_change_notify* имеет значение NULL, функция обратного вызова для уведомления об изменении состояния канала отключена.</span><span class="sxs-lookup"><span data-stu-id="d7262-1166">The user-supplied *link_status_change_notify* routine is invoked when either the primary or secondary interface status is changed (such as IP address is changed.) If *link_status_change_notify* is NULL, the link status change notify callback feature is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1167">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1167">Parameters</span></span>

- <span data-ttu-id="d7262-1168">**ip_ptr**: указатель блока управления IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1168">**ip_ptr** IP control block pointer</span></span>
- <span data-ttu-id="d7262-1169">**link_status_change_notify**: указанная пользователем функция обратного вызова, вызываемая при изменении физического интерфейса</span><span class="sxs-lookup"><span data-stu-id="d7262-1169">**link_status_change_notify** User-supplied callback function to be called upon a change to the physical interface.</span></span>


### <a name="return-values"></a><span data-ttu-id="d7262-1170">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1170">Return Values</span></span>

- <span data-ttu-id="d7262-1171">**NX_SUCCESS** (0x00) — успешное задание.</span><span class="sxs-lookup"><span data-stu-id="d7262-1171">**NX_SUCCESS** (0x00) Successful set</span></span>
- <span data-ttu-id="d7262-1172">**NX_PTR_ERROR** (0x07) — недопустимый указатель управляющего блока IP или новый указатель на физический адрес</span><span class="sxs-lookup"><span data-stu-id="d7262-1172">**NX_PTR_ERROR** (0x07) Invalid IP control block pointer or new physical address pointer</span></span>
- <span data-ttu-id="d7262-1173">**NX_CALLER_ERROR** (0x11) — служба не вызывается из инициализации системы или контекста потока.</span><span class="sxs-lookup"><span data-stu-id="d7262-1173">**NX_CALLER_ERROR** (0x11) Service is not called from system initialization or thread context.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="d7262-1174">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1174">Allowed From</span></span>

<span data-ttu-id="d7262-1175">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1175">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1176">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1176">Preemption Possible</span></span>

<span data-ttu-id="d7262-1177">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1177">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1178">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1178">Example</span></span>

```C
/* Configure a callback function to be used when the physical
    interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0, my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
    is set. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1179">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1179">See Also</span></span>

- <span data-ttu-id="d7262-1180">nx_ip_interface_address_get, nx_ip_interface_address_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-1180">nx_ip_interface_address_get, nx_ip_interface_address_set,</span></span>
- <span data-ttu-id="d7262-1181">nx_ip_interface_attach, nx_ip_interface_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-1181">nx_ip_interface_attach, nx_ip_interface_info_get,</span></span>
- <span data-ttu-id="d7262-1182">nx_ip_interface_status_check</span><span class="sxs-lookup"><span data-stu-id="d7262-1182">nx_ip_interface_status_check</span></span>

## <a name="nx_ip_raw_packet_disable"></a><span data-ttu-id="d7262-1183">nx_ip_raw_packet_disable</span><span class="sxs-lookup"><span data-stu-id="d7262-1183">nx_ip_raw_packet_disable</span></span>

<span data-ttu-id="d7262-1184">Отключение отправки и получения необработанных пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-1184">Disable raw packet sending/receiving</span></span>


### <a name="prototype"></a><span data-ttu-id="d7262-1185">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1185">Prototype</span></span>

```C
UINT nx_ip_raw_packet_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-1186">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1186">Description</span></span>

<span data-ttu-id="d7262-1187">Эта служба отключает передачу и получение необработанных IP-пакетов для данного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-1187">This service disables transmission and reception of raw IP packets for this IP instance.</span></span> <span data-ttu-id="d7262-1188">Если служба необработанных пакетов была включена ранее и в очереди приема есть необработанные пакеты, эта служба освобождает все полученные необработанные пакеты.</span><span class="sxs-lookup"><span data-stu-id="d7262-1188">If the raw packet service was previously enabled, and there are raw packets in the receive queue, this service will release any received raw packets.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1189">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1189">Parameters</span></span>

- <span data-ttu-id="d7262-1190">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1190">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1191">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1191">Return Values</span></span>

- <span data-ttu-id="d7262-1192">**NX_SUCCESS** (0x00) — успешное отключение необработанных IP-пакетов.</span><span class="sxs-lookup"><span data-stu-id="d7262-1192">**NX_SUCCESS** (0x00) Successful IP raw packet disable.</span></span>
- <span data-ttu-id="d7262-1193">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-1193">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-1194">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1194">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1195">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1195">Allowed From</span></span>

<span data-ttu-id="d7262-1196">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1196">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1197">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1197">Preemption Possible</span></span>

<span data-ttu-id="d7262-1198">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1198">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1199">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1199">Example</span></span>

```C
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been disabled for the previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1200">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1200">See Also</span></span>

- <span data-ttu-id="d7262-1201">nx_ip_raw_packet_enable, nx_ip_raw_packet_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-1201">nx_ip_raw_packet_enable, nx_ip_raw_packet_receive,</span></span>
- <span data-ttu-id="d7262-1202">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="d7262-1202">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_enable"></a><span data-ttu-id="d7262-1203">nx_ip_raw_packet_enable</span><span class="sxs-lookup"><span data-stu-id="d7262-1203">nx_ip_raw_packet_enable</span></span>

<span data-ttu-id="d7262-1204">Включение обработки необработанных пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-1204">Enable raw packet processing</span></span>


### <a name="prototype"></a><span data-ttu-id="d7262-1205">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1205">Prototype</span></span>

```C
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-1206">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1206">Description</span></span>

<span data-ttu-id="d7262-1207">Эта служба включает передачу и получение необработанных IP-пакетов для данного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-1207">This service enables transmission and reception of raw IP packets for this IP instance.</span></span> <span data-ttu-id="d7262-1208">Входящие пакеты TCP, UDP, ICMP и IGMP по-прежнему обрабатываются NetX.</span><span class="sxs-lookup"><span data-stu-id="d7262-1208">Incoming TCP, UDP, ICMP, and IGMP packets are still processed by NetX.</span></span> <span data-ttu-id="d7262-1209">Пакеты с неизвестными типами протоколов верхнего уровня обрабатываются подпрограммой приема необработанных пакетов.</span><span class="sxs-lookup"><span data-stu-id="d7262-1209">Packets with unknown upper layer protocol types are processed by raw packet reception routine.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1210">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1210">Parameters</span></span>

- <span data-ttu-id="d7262-1211">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1211">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1212">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1212">Return Values</span></span>

- <span data-ttu-id="d7262-1213">**NX_SUCCESS** (0x00) — успешное включение необработанных IP-пакетов.</span><span class="sxs-lookup"><span data-stu-id="d7262-1213">**NX_SUCCESS** (0x00) Successful IP raw packet enable.</span></span>
- <span data-ttu-id="d7262-1214">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-1214">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-1215">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1215">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1216">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1216">Allowed From</span></span>

<span data-ttu-id="d7262-1217">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1217">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1218">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1218">Preemption Possible</span></span>

<span data-ttu-id="d7262-1219">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1219">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1220">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1220">Example</span></span>

```C
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
    been enabled for the previously created IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1221">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1221">See Also</span></span>

- <span data-ttu-id="d7262-1222">nx_ip_raw_packet_disable, nx_ip_raw_packet_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-1222">nx_ip_raw_packet_disable, nx_ip_raw_packet_receive,</span></span>
- <span data-ttu-id="d7262-1223">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="d7262-1223">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_interface_send"></a><span data-ttu-id="d7262-1224">nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="d7262-1224">nx_ip_raw_packet_interface_send</span></span>

<span data-ttu-id="d7262-1225">Отправка необработанного IP-пакета через указанный сетевой интерфейс</span><span class="sxs-lookup"><span data-stu-id="d7262-1225">Send raw IP packet through specified network interface</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1226">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1226">Prototype</span></span>

```C
UINT nx_ip_raw_packet_interface_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```

### <a name="description"></a><span data-ttu-id="d7262-1227">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1227">Description</span></span>

<span data-ttu-id="d7262-1228">Эта служба отправляет необработанный IP-пакет на конечный IP-адрес через связанный сетевой интерфейс, используя указанный локальный IP-адрес в качестве исходного.</span><span class="sxs-lookup"><span data-stu-id="d7262-1228">This service sends a raw IP packet to the destination IP address using the specified local IP address as the source address, and through the associated network interface.</span></span> <span data-ttu-id="d7262-1229">Обратите внимание, что эта подпрограмма возвращает управление немедленно. Поэтому неизвестно, был ли IP-пакет отправлен на самом деле.</span><span class="sxs-lookup"><span data-stu-id="d7262-1229">Note that this routine returns immediately, and it is, therefore, not known if the IP packet has actually been sent.</span></span> <span data-ttu-id="d7262-1230">Сетевой драйвер отвечает за освобождение пакета по завершении передачи.</span><span class="sxs-lookup"><span data-stu-id="d7262-1230">The network driver will be responsible for releasing the packet when the transmission is complete.</span></span> <span data-ttu-id="d7262-1231">Эта служба отличается от других служб тем, что узнать, был ли пакет на самом деле отправлен, невозможно.</span><span class="sxs-lookup"><span data-stu-id="d7262-1231">This service differs from other services in that there is no way of knowing if the packet was actually sent.</span></span> <span data-ttu-id="d7262-1232">Он мог быть потерян в процессе передачи через Интернет.</span><span class="sxs-lookup"><span data-stu-id="d7262-1232">It could get lost on the Internet.</span></span>

<span data-ttu-id="d7262-1233">*Обратите внимание, что должна быть включена обработка необработанных IP-адресов.*</span><span class="sxs-lookup"><span data-stu-id="d7262-1233">*Note that raw IP processing must be enabled.*</span></span>

<span data-ttu-id="d7262-1234">*Эта служба аналогична **nx_ip_raw_packet_send**, за исключением того, что она позволяет приложению отправлять необработанные IP-пакеты из указанных физических интерфейсов.*</span><span class="sxs-lookup"><span data-stu-id="d7262-1234">*This service is similar to **nx_ip_raw_packet_send**, except that this service allows an application to send raw IP packet from a specified physical interfaces.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1235">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1235">Parameters</span></span>

- <span data-ttu-id="d7262-1236">**ip_ptr**: указатель на ранее созданную задачу IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1236">**ip_ptr** Pointer to previously created IP task.</span></span>
- <span data-ttu-id="d7262-1237">**packet_ptr**: указатель на передаваемый пакет</span><span class="sxs-lookup"><span data-stu-id="d7262-1237">**packet_ptr** Pointer to packet to transmit.</span></span>
- <span data-ttu-id="d7262-1238">**destination_ip**: IP-адрес, на который нужно отправить пакет</span><span class="sxs-lookup"><span data-stu-id="d7262-1238">**destination_ip** IP address to send packet.</span></span>
- <span data-ttu-id="d7262-1239">**address_index**: индекс адреса интерфейса, из которого нужно отправить пакет</span><span class="sxs-lookup"><span data-stu-id="d7262-1239">**address_index** Index of the address of the interface to send packet out on.</span></span>
- <span data-ttu-id="d7262-1240">**type_of_service**: тип службы для пакета</span><span class="sxs-lookup"><span data-stu-id="d7262-1240">**type_of_service** Type of service for packet.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1241">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1241">Return Values</span></span>

- <span data-ttu-id="d7262-1242">**NX_SUCCESS** (0x00) — пакет успешно передан.</span><span class="sxs-lookup"><span data-stu-id="d7262-1242">**NX_SUCCESS** (0x00) Packet successfully transmitted.</span></span>
- <span data-ttu-id="d7262-1243">**NX_IP_ADDRESS_ERROR** (0x21) — нет подходящего исходящего интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d7262-1243">**NX_IP_ADDRESS_ERROR** (0x21) No suitable outgoing interface available.</span></span>
- <span data-ttu-id="d7262-1244">**NX_NOT_ENABLED** (0x14) — обработка необработанных IP-пакетов не включена.</span><span class="sxs-lookup"><span data-stu-id="d7262-1244">**NX_NOT_ENABLED** (0x14) Raw IP packet processing not enabled.</span></span>
- <span data-ttu-id="d7262-1245">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1245">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-1246">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="d7262-1246">**NX_PTR_ERROR** (0x07) Invalid pointer input.</span></span>
- <span data-ttu-id="d7262-1247">**NX_OPTION_ERROR** (0x0A) — указан недопустимый тип службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1247">**NX_OPTION_ERROR** (0x0A) Invalid type of service specified.</span></span>
- <span data-ttu-id="d7262-1248">**NX_OVERFLOW** (0x03) — недопустимый указатель префикса пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1248">**NX_OVERFLOW** (0x03) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="d7262-1249">**NX_UNDERFLOW** (0x02) — недопустимый указатель префикса пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1249">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="d7262-1250">**NX_INVALID_INTERFACE** (0x4C) — указан недопустимый индекс интерфейса.</span><span class="sxs-lookup"><span data-stu-id="d7262-1250">**NX_INVALID_INTERFACE** (0x4C) Invalid interface index specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1251">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1251">Allowed From</span></span>

<span data-ttu-id="d7262-1252">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1252">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1253">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1253">Preemption Possible</span></span>

<span data-ttu-id="d7262-1254">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1254">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1255">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1255">Example</span></span>

```C
#define ADDRESS_IDNEX 1
/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_interface_send(ip_ptr, packet_ptr,
    destination_ip,
    ADDRESS_INDEX,
    NX_IP_NORMAL);
/* If status is NX_SUCCESS the packet was successfully transmitted. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1256">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1256">See Also</span></span>

- <span data-ttu-id="d7262-1257">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span><span class="sxs-lookup"><span data-stu-id="d7262-1257">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="d7262-1258">nx_ip_raw_packet_receive, nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="d7262-1258">nx_ip_raw_packet_receive, nx_ip_raw_packet_send</span></span>

## <a name="nx_ip_raw_packet_receive"></a><span data-ttu-id="d7262-1259">nx_ip_raw_packet_receive</span><span class="sxs-lookup"><span data-stu-id="d7262-1259">nx_ip_raw_packet_receive</span></span>

<span data-ttu-id="d7262-1260">Получение необработанного IP-пакета</span><span class="sxs-lookup"><span data-stu-id="d7262-1260">Receive raw IP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1261">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1261">Prototype</span></span>

```C
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d7262-1262">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1262">Description</span></span>

<span data-ttu-id="d7262-1263">Эта служба получает необработанный IP-пакет из указанного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-1263">This service receives a raw IP packet from the specified IP instance.</span></span> <span data-ttu-id="d7262-1264">При наличии IP-пакетов в очереди приема необработанных пакетов вызывающему объекту возвращается первый (самый старый) пакет.</span><span class="sxs-lookup"><span data-stu-id="d7262-1264">If there are IP packets on the raw packet receive queue, the first (oldest) packet is returned to the caller.</span></span> <span data-ttu-id="d7262-1265">В противном случае, если пакеты недоступны, вызывающий объект может приостановить работу согласно значению параметра wait.</span><span class="sxs-lookup"><span data-stu-id="d7262-1265">Otherwise, if no packets are available, the caller may suspend as specified by the wait option.</span></span>

<span data-ttu-id="d7262-1266">*Если возвращается значение NX_SUCCESS, приложение отвечает за освобождение полученного пакета, когда он больше не нужен*.</span><span class="sxs-lookup"><span data-stu-id="d7262-1266">*If NX_SUCCESS, is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1267">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1267">Parameters</span></span>

- <span data-ttu-id="d7262-1268">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1268">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-1269">**packet_ptr**: указатель на место размещения полученного необработанного IP-пакета</span><span class="sxs-lookup"><span data-stu-id="d7262-1269">**packet_ptr** Pointer to pointer to place the received raw IP packet in.</span></span>
- <span data-ttu-id="d7262-1270">**wait_option** определяет поведение службы в случае, если нет доступных необработанных IP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-1270">**wait_option** Defines how the service behaves if there are no raw IP packets available.</span></span> <span data-ttu-id="d7262-1271">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d7262-1271">The wait options are defined as follows:</span></span>
- <span data-ttu-id="d7262-1272">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-1272">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="d7262-1273">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-1273">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="d7262-1274">Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d7262-1274">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1275">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1275">Return Values</span></span>

- <span data-ttu-id="d7262-1276">**NX_SUCCESS** (0x00) — успешное получение необработанного IP-пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1276">**NX_SUCCESS** (0x00) Successful IP raw packet receive.</span></span>
- <span data-ttu-id="d7262-1277">**NX_NO_PACKET** (0x01) — нет доступных пакетов.</span><span class="sxs-lookup"><span data-stu-id="d7262-1277">**NX_NO_PACKET** (0x01) No packet was available.</span></span>
- <span data-ttu-id="d7262-1278">**NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="d7262-1278">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="d7262-1279">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-1279">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="d7262-1280">**NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель возвращаемого пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1280">**NX_PTR_ERROR** (0x07) Invalid IP or return packet pointer.</span></span>
- <span data-ttu-id="d7262-1281">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1281">**NX_CALLER_ERROR** (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1282">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1282">Allowed From</span></span>

<span data-ttu-id="d7262-1283">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1283">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1284">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1284">Preemption Possible</span></span>

<span data-ttu-id="d7262-1285">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1285">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1286">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1286">Example</span></span>

```C
/* Receive a raw IP packet for this IP instance, wait for a maximum
    of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
    variable packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1287">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1287">See Also</span></span>

- <span data-ttu-id="d7262-1288">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span><span class="sxs-lookup"><span data-stu-id="d7262-1288">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="d7262-1289">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="d7262-1289">nx_ip_raw_packet_send, nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_raw_packet_send"></a><span data-ttu-id="d7262-1290">nx_ip_raw_packet_send</span><span class="sxs-lookup"><span data-stu-id="d7262-1290">nx_ip_raw_packet_send</span></span>

<span data-ttu-id="d7262-1291">Отправка необработанного IP-пакета</span><span class="sxs-lookup"><span data-stu-id="d7262-1291">Send raw IP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1292">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1292">Prototype</span></span>

```C
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```

### <a name="description"></a><span data-ttu-id="d7262-1293">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1293">Description</span></span>

<span data-ttu-id="d7262-1294">Эта служба отправляет необработанный IP-пакет на целевой IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d7262-1294">This service sends a raw IP packet to the destination IP address.</span></span> <span data-ttu-id="d7262-1295">Обратите внимание, что эта подпрограмма возвращает управление немедленно. Поэтому неизвестно, был ли IP-пакет отправлен на самом деле.</span><span class="sxs-lookup"><span data-stu-id="d7262-1295">Note that this routine returns immediately, and it is therefore not known whether the IP packet has actually been sent.</span></span> <span data-ttu-id="d7262-1296">Сетевой драйвер отвечает за освобождение пакета по завершении передачи.</span><span class="sxs-lookup"><span data-stu-id="d7262-1296">The network driver will be responsible for releasing the packet when the transmission is complete.</span></span>

<span data-ttu-id="d7262-1297">В системе с множественной адресацией NetX ищет соответствующий сетевой интерфейс по IP-адресу назначения и использует IP-адрес интерфейса в качестве исходного адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-1297">For a multihome system, NetX uses the destination IP address to find an appropriate network interface and uses the IP address of the interface as the source address.</span></span> <span data-ttu-id="d7262-1298">Если IP-адрес назначения является широковещательным или многоадресным, используется первый допустимый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d7262-1298">If the destination IP address is broadcast or multicast, the first valid interface is used.</span></span> <span data-ttu-id="d7262-1299">В этом случае приложения используют ***nx_ip_raw_packet_interface_send***.</span><span class="sxs-lookup"><span data-stu-id="d7262-1299">Applications use the ***nx_ip_raw_packet_interface_send*** in this case.</span></span>

<span data-ttu-id="d7262-1300">*Если не возвращается ошибка, приложение не должно освобождать пакет после этого вызова. Это приведет к непредсказуемым результатам, так как сетевой драйвер освободит пакет после передачи.*</span><span class="sxs-lookup"><span data-stu-id="d7262-1300">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1301">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1301">Parameters</span></span>

- <span data-ttu-id="d7262-1302">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1302">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-1303">**packet_ptr**: указатель на отправляемый IP-пакет</span><span class="sxs-lookup"><span data-stu-id="d7262-1303">**packet_ptr** Pointer to the raw IP packet to send.</span></span>
- <span data-ttu-id="d7262-1304">**destination_ip**: конечный IP-адрес, которым может быть IP-адрес конкретного узла, сетевой широковещательный адрес, петлевой адрес или адрес многоадресной рассылки</span><span class="sxs-lookup"><span data-stu-id="d7262-1304">**destination_ip** Destination IP address, which can be a specific host IP address, a network broadcast, an internal loop-back, or a multicast address.</span></span>
- <span data-ttu-id="d7262-1305">**type_of_service** определяет тип службы для передачи. Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="d7262-1305">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>
- <span data-ttu-id="d7262-1306">NX_IP_NORMAL (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-1306">NX_IP_NORMAL (0x00000000)</span></span>
- <span data-ttu-id="d7262-1307">NX_IP_MIN_DELAY (0x00100000)</span><span class="sxs-lookup"><span data-stu-id="d7262-1307">NX_IP_MIN_DELAY (0x00100000)</span></span>
- <span data-ttu-id="d7262-1308">NX_IP_MAX_DATA (0x00080000)</span><span class="sxs-lookup"><span data-stu-id="d7262-1308">NX_IP_MAX_DATA (0x00080000)</span></span>
- <span data-ttu-id="d7262-1309">NX_IP_MAX_RELIABLE (0x00040000)</span><span class="sxs-lookup"><span data-stu-id="d7262-1309">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
- <span data-ttu-id="d7262-1310">NX_IP_MIN_COST (0x00020000)</span><span class="sxs-lookup"><span data-stu-id="d7262-1310">NX_IP_MIN_COST (0x00020000)</span></span>


### <a name="return-values"></a><span data-ttu-id="d7262-1311">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1311">Return Values</span></span>

- <span data-ttu-id="d7262-1312">**NX_SUCCESS** (0x00) — успешная инициация отправки необработанного IP-пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1312">**NX_SUCCESS** (0x00) Successful IP raw packet send initiated.</span></span>
- <span data-ttu-id="d7262-1313">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d7262-1313">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="d7262-1314">**NX_NOT_ENABLED** (0x14) — функция необработанных IP-пакетов не включена.</span><span class="sxs-lookup"><span data-stu-id="d7262-1314">**NX_NOT_ENABLED** (0x14) Raw IP feature is not enabled.</span></span>
- <span data-ttu-id="d7262-1315">**NX_OPTION_ERROR** (0x0A) — недопустимый тип службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1315">**NX_OPTION_ERROR** (0x0A) Invalid type of service.</span></span>
- <span data-ttu-id="d7262-1316">**NX_UNDERFLOW** (0x02) — недостаточно места для добавления заголовка IP в начало пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1316">**NX_UNDERFLOW** (0x02) Not enough room to prepend an IP header on the packet.</span></span>
- <span data-ttu-id="d7262-1317">**NX_OVERFLOW** (0x03) — недопустимый указатель для добавления пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1317">**NX_OVERFLOW** (0x03) Packet append pointer is invalid.</span></span>
- <span data-ttu-id="d7262-1318">**NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1318">**NX_PTR_ERROR** (0x07) Invalid IP or packet pointer.</span></span>
- <span data-ttu-id="d7262-1319">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1319">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1320">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1320">Allowed From</span></span>

<span data-ttu-id="d7262-1321">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1321">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1322">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1322">Preemption Possible</span></span>

<span data-ttu-id="d7262-1323">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1323">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1324">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1324">Example</span></span>

```C
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
    IP_ADDRESS(1,2,3,5),
    NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
    packet_ptr has been sent. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1325">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1325">See Also</span></span>

- <span data-ttu-id="d7262-1326">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span><span class="sxs-lookup"><span data-stu-id="d7262-1326">nx_ip_raw_packet_disable, nx_ip_raw_packet_enable,</span></span>
- <span data-ttu-id="d7262-1327">nx_ip_raw_packet_receive, nx_ip_raw_packet_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-1327">nx_ip_raw_packet_receive, nx_ip_raw_packet_send,</span></span>
- <span data-ttu-id="d7262-1328">nx_ip_raw_packet_interface_send</span><span class="sxs-lookup"><span data-stu-id="d7262-1328">nx_ip_raw_packet_interface_send</span></span>

## <a name="nx_ip_static_route_add"></a><span data-ttu-id="d7262-1329">nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="d7262-1329">nx_ip_static_route_add</span></span>

<span data-ttu-id="d7262-1330">Добавление статического маршрута в таблицу маршрутизации</span><span class="sxs-lookup"><span data-stu-id="d7262-1330">Add static route to the routing table</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1331">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1331">Prototype</span></span>

```C
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```

### <a name="description"></a><span data-ttu-id="d7262-1332">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1332">Description</span></span>

<span data-ttu-id="d7262-1333">Эта служба добавляет запись в таблицу статической маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="d7262-1333">This service adds an entry to the static routing table.</span></span> <span data-ttu-id="d7262-1334">Обратите внимание, что адрес *next_hop* должен быть доступен напрямую с одного из локальных сетевых устройств.</span><span class="sxs-lookup"><span data-stu-id="d7262-1334">Note that the *next_hop* address must be directly accessible from one of the local network devices.</span></span>

<span data-ttu-id="d7262-1335">*Обратите внимание, что указатель ip_ptr должен указывать на допустимую структуру IP в NetX, а сборка библиотеки NetX должна выполняться с параметром NX_ENABLE_IP_STATIC_ROUTING, предписывающим использование этой службы. По умолчанию сборка NetX выполняется без задания параметра NX_ENABLE_IP_STATIC_ROUTING.*</span><span class="sxs-lookup"><span data-stu-id="d7262-1335">*Note that ip_ptr must point to a valid NetX IP structure and the NetX library must be built with NX_ENABLE_IP_STATIC_ROUTING defined to use this service. By default NetX is built without NX_ENABLE_IP_STATIC_ROUTING defined.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1336">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1336">Parameters</span></span>

- <span data-ttu-id="d7262-1337">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1337">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-1338">**network_address**: целевой сетевой адрес в порядке байтов узла</span><span class="sxs-lookup"><span data-stu-id="d7262-1338">**network_address** Target network address, in host byte order</span></span>
- <span data-ttu-id="d7262-1339">**net_mask**: маска целевой сети в порядке байтов узла</span><span class="sxs-lookup"><span data-stu-id="d7262-1339">**net_mask** Target network mask, in host byte order</span></span>
- <span data-ttu-id="d7262-1340">**next_hop**: адрес следующего прыжка для целевой сети в порядке байтов узла</span><span class="sxs-lookup"><span data-stu-id="d7262-1340">**next_hop** Next hop address for the target network, in host byte order</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1341">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1341">Return Values</span></span>

- <span data-ttu-id="d7262-1342">**NX_SUCCESS** (0x00) — запись добавлена в таблицу статической маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="d7262-1342">**NX_SUCCESS** (0x00) Entry is added to the static routing table.</span></span>
- <span data-ttu-id="d7262-1343">**NX_OVERFLOW** (0x03) — таблица статической маршрутизации заполнена.</span><span class="sxs-lookup"><span data-stu-id="d7262-1343">**NX_OVERFLOW** (0x03) Static routing table is full.</span></span>
- <span data-ttu-id="d7262-1344">**NX_NOT_SUPPORTED** (0x4B) — эта функция не компилируется.</span><span class="sxs-lookup"><span data-stu-id="d7262-1344">**NX_NOT_SUPPORTED** (0x4B) This feature is not compiled in.</span></span>
- <span data-ttu-id="d7262-1345">**NX_IP_ADDRESS_ERROR** (0x21) — следующий прыжок недоступен напрямую через локальные интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1345">**NX_IP_ADDRESS_ERROR** (0x21) Next hop is not directly accessible via local interfaces.</span></span>
- <span data-ttu-id="d7262-1346">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1346">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-1347">**NX_PTR_ERROR** (0x07) — недопустимый указатель ip_ptr.</span><span class="sxs-lookup"><span data-stu-id="d7262-1347">**NX_PTR_ERROR** (0x07) Invalid ip_ptr pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1348">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1348">Allowed From</span></span>

<span data-ttu-id="d7262-1349">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1349">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1350">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1350">Preemption Possible</span></span>

<span data-ttu-id="d7262-1351">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1351">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1352">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1352">Example</span></span>

```C
/* Specify the next hop for the 192.168.10.0 through the gateway
    192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,10,0),
    0xFFFFFF00UL,
    IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
    static routing table. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1353">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1353">See Also</span></span>

- <span data-ttu-id="d7262-1354">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-1354">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_delete</span></span>

## <a name="nx_ip_static_route_delete"></a><span data-ttu-id="d7262-1355">nx_ip_static_route_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-1355">nx_ip_static_route_delete</span></span>

<span data-ttu-id="d7262-1356">Удаление статического маршрута из таблицы маршрутизации</span><span class="sxs-lookup"><span data-stu-id="d7262-1356">Delete static route from routing table</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1357">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1357">Prototype</span></span>

```C
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address, 
    ULONG net_mask);
```

### <a name="description"></a><span data-ttu-id="d7262-1358">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1358">Description</span></span>

<span data-ttu-id="d7262-1359">Эта служба удаляет запись из таблицы статической маршрутизации.</span><span class="sxs-lookup"><span data-stu-id="d7262-1359">This service deletes an entry from the static routing table.</span></span>

<span data-ttu-id="d7262-1360">*Обратите внимание, что указатель ip_ptr должен указывать на допустимую структуру IP в NetX, а сборка библиотеки NetX должна выполняться с параметром NX_ENABLE_IP_STATIC_ROUTING, предписывающим использование этой службы. По умолчанию сборка NetX выполняется без задания параметра NX_ENABLE_IP_STATIC_ROUTING.*</span><span class="sxs-lookup"><span data-stu-id="d7262-1360">*Note that ip_ptr must point to a valid NetX IP structure and the NetX library must be built with NX_ENABLE_IP_STATIC_ROUTING defined to use this service. By default NetX is built without NX_ENABLE_IP_STATIC_ROUTING defined.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1361">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1361">Parameters</span></span>

- <span data-ttu-id="d7262-1362">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1362">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-1363">**network_address**: целевой сетевой адрес в порядке байтов узла</span><span class="sxs-lookup"><span data-stu-id="d7262-1363">**network_address** Target network address, in host byte order.</span></span>
- <span data-ttu-id="d7262-1364">**net_mask**: маска целевой сети в порядке байтов узла</span><span class="sxs-lookup"><span data-stu-id="d7262-1364">**net_mask** Target network mask, in host byte order.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1365">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1365">Allowed From</span></span>

<span data-ttu-id="d7262-1366">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1366">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1367">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1367">Preemption Possible</span></span>

<span data-ttu-id="d7262-1368">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1368">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1369">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1369">Example</span></span>

```C
/* Remove the static route for 192.168.10.0 from the routing table.*/
status = nx_ip_static_route_delete(ip_ptr,
    IP_ADDRESS(192,168,10,0), 0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
    the static routing table. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1370">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1370">See Also</span></span>

- <span data-ttu-id="d7262-1371">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_add</span><span class="sxs-lookup"><span data-stu-id="d7262-1371">nx_ip_gateway_address_set, nx_ip_info_get, nx_ip_static_route_add</span></span>

## <a name="nx_ip_status_check"></a><span data-ttu-id="d7262-1372">nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="d7262-1372">nx_ip_status_check</span></span>

<span data-ttu-id="d7262-1373">Проверка состояния экземпляра IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1373">Check status of an IP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1374">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1374">Prototype</span></span>

```C
UINT nx_ip_status_check(
    NX_IP *ip_ptr,
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d7262-1375">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1375">Description</span></span>

<span data-ttu-id="d7262-1376">Эта служба проверяет и при необходимости ожидает указанное состояние основного сетевого интерфейса ранее созданного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-1376">This service checks and optionally waits for the specified status of the primary network interface of a previously created IP instance.</span></span> <span data-ttu-id="d7262-1377">Чтобы получить состояние дополнительных интерфейсов, приложения должны использовать службу ***nx_ip_interface_status_check***.</span><span class="sxs-lookup"><span data-stu-id="d7262-1377">To obtain status on secondary interfaces, applications shall use the service ***nx_ip_interface_status_check.***</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1378">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1378">Parameters</span></span>

- <span data-ttu-id="d7262-1379">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1379">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-1380">**needed_status**: запрошенное состояние IP, определенное в виде битовой карты следующим образом</span><span class="sxs-lookup"><span data-stu-id="d7262-1380">**needed_status** IP status requested, defined in bit-map form as follows:</span></span>
- <span data-ttu-id="d7262-1381">NX_IP_INITIALIZE_DONE (0x0001)</span><span class="sxs-lookup"><span data-stu-id="d7262-1381">NX_IP_INITIALIZE_DONE (0x0001)</span></span>
- <span data-ttu-id="d7262-1382">NX_IP_ADDRESS_RESOLVED (0x0002)</span><span class="sxs-lookup"><span data-stu-id="d7262-1382">NX_IP_ADDRESS_RESOLVED (0x0002)</span></span>
- <span data-ttu-id="d7262-1383">NX_IP_LINK_ENABLED (0x0004)</span><span class="sxs-lookup"><span data-stu-id="d7262-1383">NX_IP_LINK_ENABLED (0x0004)</span></span>
- <span data-ttu-id="d7262-1384">NX_IP_ARP_ENABLED (0x0008)</span><span class="sxs-lookup"><span data-stu-id="d7262-1384">NX_IP_ARP_ENABLED (0x0008)</span></span>
- <span data-ttu-id="d7262-1385">NX_IP_UDP_ENABLED (0x0010)</span><span class="sxs-lookup"><span data-stu-id="d7262-1385">NX_IP_UDP_ENABLED (0x0010)</span></span>
- <span data-ttu-id="d7262-1386">NX_IP_TCP_ENABLED (0x0020)</span><span class="sxs-lookup"><span data-stu-id="d7262-1386">NX_IP_TCP_ENABLED (0x0020)</span></span>
- <span data-ttu-id="d7262-1387">NX_IP_IGMP_ENABLED (0x0040)</span><span class="sxs-lookup"><span data-stu-id="d7262-1387">NX_IP_IGMP_ENABLED (0x0040)</span></span>
- <span data-ttu-id="d7262-1388">NX_IP_RARP_COMPLETE (0x0080)</span><span class="sxs-lookup"><span data-stu-id="d7262-1388">NX_IP_RARP_COMPLETE (0x0080)</span></span>
- <span data-ttu-id="d7262-1389">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span><span class="sxs-lookup"><span data-stu-id="d7262-1389">NX_IP_INTERFACE_LINK_ENABLED (0x0100)</span></span>
- <span data-ttu-id="d7262-1390">**actual_status**: указатель на место назначения фактического набора битов</span><span class="sxs-lookup"><span data-stu-id="d7262-1390">**actual_status** Pointer to destination of actual bits set.</span></span>
- <span data-ttu-id="d7262-1391">**wait_option**: определяет поведение службы в случае, если запрошенные биты состояния недоступны</span><span class="sxs-lookup"><span data-stu-id="d7262-1391">**wait_option** Defines how the service behaves if the requested status bits are not available.</span></span> <span data-ttu-id="d7262-1392">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d7262-1392">The wait options are defined as follows:</span></span>
- <span data-ttu-id="d7262-1393">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-1393">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="d7262-1394">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-1394">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="d7262-1395">Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d7262-1395">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1396">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1396">Return Values</span></span>

- <span data-ttu-id="d7262-1397">**NX_SUCCESS** (0x00) — успешная проверка состояния IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-1397">**NX_SUCCESS** (0x00) Successful IP status check.</span></span>
- <span data-ttu-id="d7262-1398">**NX_NOT_SUCCESSFUL** (0x43) — запрос состояния не был выполнен в течение указанного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="d7262-1398">**NX_NOT_SUCCESSFUL** (0x43) Status request was not satisfied within the timeout specified.</span></span>
- <span data-ttu-id="d7262-1399">**NX_PTR_ERROR** (0x07) — указатель IP является или стал недопустимым, либо недопустимый указатель фактического состояния.</span><span class="sxs-lookup"><span data-stu-id="d7262-1399">**NX_PTR_ERROR** (0x07) IP pointer is or has become invalid, or actual status pointer is invalid.</span></span>
- <span data-ttu-id="d7262-1400">**NX_OPTION_ERROR** (0x0a) — недопустимый параметр требуемого состояния.</span><span class="sxs-lookup"><span data-stu-id="d7262-1400">**NX_OPTION_ERROR** (0x0a) Invalid needed status option.</span></span>
- <span data-ttu-id="d7262-1401">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1401">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1402">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1402">Allowed From</span></span>

<span data-ttu-id="d7262-1403">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1403">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1404">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1404">Preemption Possible</span></span>

<span data-ttu-id="d7262-1405">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1405">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1406">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1406">Example</span></span>

```C
/* Wait 10 ticks for the link up status on the previously created IP
    instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
    &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
    is up. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1407">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1407">See Also</span></span>

- <span data-ttu-id="d7262-1408">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-1408">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="d7262-1409">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="d7262-1409">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="d7262-1410">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-1410">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="d7262-1411">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-1411">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="d7262-1412">nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="d7262-1412">nx_ip_fragment_enable, nx_ip_info_get, nx_system_initialize</span></span>

## <a name="nx_packet_allocate"></a><span data-ttu-id="d7262-1413">nx_packet_allocate</span><span class="sxs-lookup"><span data-stu-id="d7262-1413">nx_packet_allocate</span></span>

<span data-ttu-id="d7262-1414">Выделение пакета из указанного пула</span><span class="sxs-lookup"><span data-stu-id="d7262-1414">Allocate packet from specified pool</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1415">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1415">Prototype</span></span>

```C
UINT nx_packet_allocate(
    NX_PACKET_POOL *pool_ptr,
    NX_PACKET **packet_ptr,
    ULONG packet_type,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d7262-1416">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1416">Description</span></span>

<span data-ttu-id="d7262-1417">Эта служба выделяет пакет из указанного пула и корректирует положение начального указателя в пакете в соответствии с указанным типом пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1417">This service allocates a packet from the specified pool and adjusts the prepend pointer in the packet according to the type of packet specified.</span></span> <span data-ttu-id="d7262-1418">Если пакет недоступен, служба приостанавливает работу в соответствии с указанным параметром ожидания.</span><span class="sxs-lookup"><span data-stu-id="d7262-1418">If no packet is available, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1419">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1419">Parameters</span></span>

- <span data-ttu-id="d7262-1420">**pool_ptr**: указатель на ранее созданный пул пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-1420">**pool_ptr** Pointer to previously created packet pool.</span></span>
- <span data-ttu-id="d7262-1421">**packet_ptr**: указатель на указатель выделенного пакета</span><span class="sxs-lookup"><span data-stu-id="d7262-1421">**packet_ptr** Pointer to the pointer of the allocated packet pointer.</span></span>
- <span data-ttu-id="d7262-1422">**packet_type**: определяет тип запрошенного пакета</span><span class="sxs-lookup"><span data-stu-id="d7262-1422">**packet_type** Defines the type of packet requested.</span></span> <span data-ttu-id="d7262-1423">Список поддерживаемых типов пакетов см. в разделе "Пулы пакетов" главы 3 на стр. 49.</span><span class="sxs-lookup"><span data-stu-id="d7262-1423">See “Packet Pools” on page 49 in Chapter 3 for a list of supported packet types.</span></span>
- <span data-ttu-id="d7262-1424">**wait_option** определяет время ожидания в тактах, если в пуле пакетов нет доступных пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-1424">**wait_option** Defines the wait time in ticks if there are no packets available in the packet pool.</span></span> <span data-ttu-id="d7262-1425">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d7262-1425">The wait options are defined as follows:</span></span>
- <span data-ttu-id="d7262-1426">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-1426">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="d7262-1427">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-1427">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="d7262-1428">Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d7262-1428">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1429">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1429">Return Values</span></span>

- <span data-ttu-id="d7262-1430">**NX_SUCCESS** (0x00) — пакет выделен успешно.</span><span class="sxs-lookup"><span data-stu-id="d7262-1430">**NX_SUCCESS** (0x00) Successful packet allocate.</span></span>
- <span data-ttu-id="d7262-1431">**NX_NO_PACKET** (0x01) — нет доступных пакетов.</span><span class="sxs-lookup"><span data-stu-id="d7262-1431">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="d7262-1432">**NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="d7262-1432">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="d7262-1433">**NX_INVALID_PARAMETERS** (0x4D) — размер пакета не поддерживается протоколом.</span><span class="sxs-lookup"><span data-stu-id="d7262-1433">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="d7262-1434">**NX_OPTION_ERROR** (0x0A) — недопустимый тип пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1434">**NX_OPTION_ERROR** (0x0A) Invalid packet type.</span></span>
- <span data-ttu-id="d7262-1435">**NX_PTR_ERROR** (0x07) — недопустимый возвращаемый указатель на пул или пакет.</span><span class="sxs-lookup"><span data-stu-id="d7262-1435">**NX_PTR_ERROR** (0x07) Invalid pool or packet return pointer.</span></span>
- <span data-ttu-id="d7262-1436">**NX_CALLER_ERROR** (0x11) — недопустимый параметр ожидания не из потока.</span><span class="sxs-lookup"><span data-stu-id="d7262-1436">**NX_CALLER_ERROR** (0x11) Invalid wait option from nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1437">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1437">Allowed From</span></span>

<span data-ttu-id="d7262-1438">Инициализация, потоки, таймеры и запросы ISR (сетевые драйверы приложений).</span><span class="sxs-lookup"><span data-stu-id="d7262-1438">Initialization, threads, timers, and ISRs (application network drivers).</span></span> <span data-ttu-id="d7262-1439">Параметр ожидания должен иметь значение NX_NO_WAIT при использовании в ISR или контексте таймера.</span><span class="sxs-lookup"><span data-stu-id="d7262-1439">Wait option must be NX_NO_WAIT when used in ISR or in timer context.</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1440">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1440">Preemption Possible</span></span>

<span data-ttu-id="d7262-1441">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1441">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1442">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1442">Example</span></span>

```C
/* Allocate a new UDP packet from the previously created packet pool
    and suspend for a maximum of 5 timer ticks if the pool is
    empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr, NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
    found in the variable packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1443">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1443">See Also</span></span>

- <span data-ttu-id="d7262-1444">nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="d7262-1444">nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="d7262-1445">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="d7262-1445">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="d7262-1446">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="d7262-1446">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="d7262-1447">nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="d7262-1447">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="d7262-1448">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="d7262-1448">nx_packet_transmit_release</span></span>

## <a name="nx_packet_copy"></a><span data-ttu-id="d7262-1449">nx_packet_copy</span><span class="sxs-lookup"><span data-stu-id="d7262-1449">nx_packet_copy</span></span>

<span data-ttu-id="d7262-1450">Копирование пакета</span><span class="sxs-lookup"><span data-stu-id="d7262-1450">Copy packet</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1451">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1451">Prototype</span></span>

```C
UINT nx_packet_copy(
    NX_PACKET *packet_ptr,
    NX_PACKET **new_packet_ptr,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d7262-1452">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1452">Description</span></span>

<span data-ttu-id="d7262-1453">Эта служба копирует сведения из предоставленного пакета в один новый пакет, выделенный из указанного пула пакетов, или несколько.</span><span class="sxs-lookup"><span data-stu-id="d7262-1453">This service copies the information in the supplied packet to one or more new packets that are allocated from the supplied packet pool.</span></span> <span data-ttu-id="d7262-1454">В случае успеха возвращается указатель на новый пакет в месте назначения, на которое указывает **new_packet_ptr**.</span><span class="sxs-lookup"><span data-stu-id="d7262-1454">If successful, the pointer to the new packet is returned in destination pointed to by **new_packet_ptr**.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1455">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1455">Parameters</span></span>

- <span data-ttu-id="d7262-1456">**packet_ptr**: указатель на исходный пакет</span><span class="sxs-lookup"><span data-stu-id="d7262-1456">**packet_ptr** Pointer to the source packet.</span></span>
- <span data-ttu-id="d7262-1457">**new_packet_ptr**: указатель на место назначения, где нужно вернуть указатель на новую копию пакета</span><span class="sxs-lookup"><span data-stu-id="d7262-1457">**new_packet_ptr** Pointer to the destination of where to return the pointer to the new copy of the packet.</span></span>
- <span data-ttu-id="d7262-1458">**pool_ptr**: указатель на ранее созданный пул пакетов, который используется для выделения одного копируемого пакета или нескольких</span><span class="sxs-lookup"><span data-stu-id="d7262-1458">**pool_ptr** Pointer to the previously created packet pool that is used to allocate one or more packets for the copy.</span></span>
- <span data-ttu-id="d7262-1459">**wait_option** определяет поведение службы в случае, если нет доступных пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-1459">**wait_option** Defines how the service waits if there are no packets available.</span></span> <span data-ttu-id="d7262-1460">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d7262-1460">The wait options are defined as follows:</span></span>
- <span data-ttu-id="d7262-1461">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-1461">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="d7262-1462">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-1462">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="d7262-1463">Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d7262-1463">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1464">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1464">Return Values</span></span>
- <span data-ttu-id="d7262-1465">**NX_SUCCESS** (0x00) — пакет успешно скопирован.</span><span class="sxs-lookup"><span data-stu-id="d7262-1465">**NX_SUCCESS** (0x00) Successful packet copy.</span></span>
- <span data-ttu-id="d7262-1466">**NX_NO_PACKET** (0x01) — пакет недоступен для копирования.</span><span class="sxs-lookup"><span data-stu-id="d7262-1466">**NX_NO_PACKET** (0x01) Packet not available for copy.</span></span>
- <span data-ttu-id="d7262-1467">**NX_INVALID_PACKET** (0x12) — пустой исходный пакет, или не удалось выполнить копирование.</span><span class="sxs-lookup"><span data-stu-id="d7262-1467">**NX_INVALID_PACKET** (0x12) Empty source packet or copy failed.</span></span>
- <span data-ttu-id="d7262-1468">**NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="d7262-1468">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="d7262-1469">**NX_INVALID_PARAMETERS** (0x4D) — размер пакета не поддерживается протоколом.</span><span class="sxs-lookup"><span data-stu-id="d7262-1469">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="d7262-1470">**NX_PTR_ERROR** (0x07) — недопустимый пул, пакет или указатель на место назначения.</span><span class="sxs-lookup"><span data-stu-id="d7262-1470">**NX_PTR_ERROR** (0x07) Invalid pool, packet, or destination pointer.</span></span>
- <span data-ttu-id="d7262-1471">**NX_UNDERFLOW** (0x02) — недопустимый указатель префикса пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1471">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="d7262-1472">**NX_OVERFLOW** (0x03) — недопустимый указатель для добавления пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1472">**NX_OVERFLOW** (0x03) Invalid packet append pointer.</span></span>
- <span data-ttu-id="d7262-1473">**NX_CALLER_ERROR** (0x11) — параметр ожидания был указан при инициализации или в ISR.</span><span class="sxs-lookup"><span data-stu-id="d7262-1473">**NX_CALLER_ERROR** (0x11) A wait option was specified in initialization or in an ISR.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1474">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1474">Allowed From</span></span>

<span data-ttu-id="d7262-1475">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="d7262-1475">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1476">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1476">Preemption Possible</span></span>

<span data-ttu-id="d7262-1477">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1477">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1478">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1478">Example</span></span>

```C
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
    previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1479">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1479">See Also</span></span>

- <span data-ttu-id="d7262-1480">nx_packet_allocate, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="d7262-1480">nx_packet_allocate, nx_packet_data_append,</span></span>
- <span data-ttu-id="d7262-1481">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="d7262-1481">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="d7262-1482">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="d7262-1482">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="d7262-1483">nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="d7262-1483">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="d7262-1484">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="d7262-1484">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_append"></a><span data-ttu-id="d7262-1485">nx_packet_data_append</span><span class="sxs-lookup"><span data-stu-id="d7262-1485">nx_packet_data_append</span></span>

<span data-ttu-id="d7262-1486">Добавление данных в конец пакета</span><span class="sxs-lookup"><span data-stu-id="d7262-1486">Append data to end of packet</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1487">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1487">Prototype</span></span>

```C
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, 
    ULONG data_size,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d7262-1488">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1488">Description</span></span>

<span data-ttu-id="d7262-1489">Эта служба добавляет данные в конец указанного пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1489">This service appends data to the end of the specified packet.</span></span> <span data-ttu-id="d7262-1490">Указанная область данных копируется в пакет.</span><span class="sxs-lookup"><span data-stu-id="d7262-1490">The supplied data area is copied into the packet.</span></span> <span data-ttu-id="d7262-1491">Если недостаточно памяти и включена функция сцепления пакетов, для выполнения запроса будет выделен один пакет или несколько.</span><span class="sxs-lookup"><span data-stu-id="d7262-1491">If there is not enough memory available, and the chained packet feature is enabled, one or more packets will be allocated to satisfy the request.</span></span> <span data-ttu-id="d7262-1492">Если функция сцепления пакетов не включена, возвращается *NX_SIZE_ERROR*.</span><span class="sxs-lookup"><span data-stu-id="d7262-1492">If the chained packet feature is not enabled, *NX_SIZE_ERROR* is returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1493">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1493">Parameters</span></span>

- <span data-ttu-id="d7262-1494">**packet_ptr**: указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="d7262-1494">**packet_ptr** Packet pointer.</span></span>
- <span data-ttu-id="d7262-1495">**data_start**: указатель на начало пользовательской области данных для добавления к пакету</span><span class="sxs-lookup"><span data-stu-id="d7262-1495">**data_start** Pointer to the start of the user’s data area to append to the packet.</span></span>
- <span data-ttu-id="d7262-1496">**data_size**: размер пользовательской области данных</span><span class="sxs-lookup"><span data-stu-id="d7262-1496">**data_size** Size of user’s data area.</span></span>
- <span data-ttu-id="d7262-1497">**pool_ptr**: указатель на пул пакетов, из которого нужно выделить другой пакет, если в текущем пакете недостаточно места</span><span class="sxs-lookup"><span data-stu-id="d7262-1497">**pool_ptr** Pointer to packet pool from which to allocate another packet if there is not enough room in the current packet.</span></span>
- <span data-ttu-id="d7262-1498">**wait_option** определяет поведение службы в случае, если нет доступных пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-1498">**wait_option** Defines how the service behaves if there are no packets available.</span></span> <span data-ttu-id="d7262-1499">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d7262-1499">The wait options are defined as follows:</span></span>
- <span data-ttu-id="d7262-1500">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-1500">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="d7262-1501">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-1501">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="d7262-1502">Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d7262-1502">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1503">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1503">Return Values</span></span>

- <span data-ttu-id="d7262-1504">**NX_SUCCESS** (0x00) — пакет успешно добавлен.</span><span class="sxs-lookup"><span data-stu-id="d7262-1504">**NX_SUCCESS** (0x00) Successful packet append.</span></span>
- <span data-ttu-id="d7262-1505">**NX_NO_PACKET** (0x01) — нет доступных пакетов.</span><span class="sxs-lookup"><span data-stu-id="d7262-1505">**NX_NO_PACKET** (0x01) No packet available.</span></span>
- <span data-ttu-id="d7262-1506">**NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="d7262-1506">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="d7262-1507">**NX_INVALID_PARAMETERS** (0x4D) — размер пакета не поддерживается протоколом.</span><span class="sxs-lookup"><span data-stu-id="d7262-1507">**NX_INVALID_PARAMETERS** (0x4D) Packet size cannot support protocol.</span></span>
- <span data-ttu-id="d7262-1508">**NX_UNDERFLOW** (0x02) — начальный указатель меньше, чем начало полезных данных.</span><span class="sxs-lookup"><span data-stu-id="d7262-1508">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="d7262-1509">**NX_OVERFLOW** (0x03) — конечный указатель меньше, чем конец полезных данных.</span><span class="sxs-lookup"><span data-stu-id="d7262-1509">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>
- <span data-ttu-id="d7262-1510">**NX_PTR_ERROR** (0x07) — недопустимый пул, пакет или указатель на данные.</span><span class="sxs-lookup"><span data-stu-id="d7262-1510">**NX_PTR_ERROR** (0x07) Invalid pool, packet, or data Pointer.</span></span>
- <span data-ttu-id="d7262-1511">**NX_SIZE_ERROR** (0x09) — недопустимый размер данных.</span><span class="sxs-lookup"><span data-stu-id="d7262-1511">**NX_SIZE_ERROR** (0x09) Invalid data size.</span></span>
- <span data-ttu-id="d7262-1512">**NX_CALLER_ERROR** (0x11) — недопустимый параметр ожидания не из потока.</span><span class="sxs-lookup"><span data-stu-id="d7262-1512">**NX_CALLER_ERROR** (0x11) Invalid wait option from nonthread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1513">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1513">Allowed From</span></span>

<span data-ttu-id="d7262-1514">Инициализация, потоки, таймеры и запросы ISR (сетевые драйверы приложений)</span><span class="sxs-lookup"><span data-stu-id="d7262-1514">Initialization, threads, timers, and ISRs (application network drivers)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1515">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1515">Preemption Possible</span></span>

<span data-ttu-id="d7262-1516">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1516">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1517">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1517">Example</span></span>

```C
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
    been appended to the packet. */
```


### <a name="see-also"></a><span data-ttu-id="d7262-1518">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1518">See Also</span></span>

- <span data-ttu-id="d7262-1519">nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset,</span><span class="sxs-lookup"><span data-stu-id="d7262-1519">nx_packet_allocate, nx_packet_copy, nx_packet_data_extract_offset,</span></span>
- <span data-ttu-id="d7262-1520">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-1520">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="d7262-1521">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="d7262-1521">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="d7262-1522">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="d7262-1522">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_extract_offset"></a><span data-ttu-id="d7262-1523">nx_packet_data_extract_offset</span><span class="sxs-lookup"><span data-stu-id="d7262-1523">nx_packet_data_extract_offset</span></span>

<span data-ttu-id="d7262-1524">Извлечение данных из пакета по смещению</span><span class="sxs-lookup"><span data-stu-id="d7262-1524">Extract data from packet via an offset</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1525">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1525">Prototype</span></span>

```C
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```

### <a name="description"></a><span data-ttu-id="d7262-1526">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1526">Description</span></span>

<span data-ttu-id="d7262-1527">Эта служба копирует данные из пакета NetX (или из цепочки пакетов), начиная с указанного смещения от начального указателя пакета указанного размера в байтах в заданный буфер.</span><span class="sxs-lookup"><span data-stu-id="d7262-1527">This service copies data from a NetX packet (or packet chain) starting at the specified offset from the packet prepend pointer of the specified size in bytes into the specified buffer.</span></span> <span data-ttu-id="d7262-1528">Число фактически скопированных байтов возвращается в *bytes_copied*.</span><span class="sxs-lookup"><span data-stu-id="d7262-1528">The number of bytes actually copied is returned in *bytes_copied.*</span></span> <span data-ttu-id="d7262-1529">Эта служба не удаляет данные из пакета и не настраивает начальный указатель или другую информацию о внутреннем состоянии.</span><span class="sxs-lookup"><span data-stu-id="d7262-1529">This service does not remove data from the packet, nor does it adjust the prepend pointer or other internal state information.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1530">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1530">Parameters</span></span>

- <span data-ttu-id="d7262-1531">**packet_ptr**: указатель на извлекаемый пакет</span><span class="sxs-lookup"><span data-stu-id="d7262-1531">**packet_ptr** Pointer to packet to extract</span></span>
- <span data-ttu-id="d7262-1532">**offset**: смещение от текущего начального указателя</span><span class="sxs-lookup"><span data-stu-id="d7262-1532">**offset** Offset from the current prepend pointer.</span></span>
- <span data-ttu-id="d7262-1533">**buffer_start**: указатель на начало буфера сохранения</span><span class="sxs-lookup"><span data-stu-id="d7262-1533">**buffer_start** Pointer to start of save buffer</span></span>
- <span data-ttu-id="d7262-1534">**buffer_length**: число копируемых байтов</span><span class="sxs-lookup"><span data-stu-id="d7262-1534">**buffer_length** Number of bytes to copy</span></span>
- <span data-ttu-id="d7262-1535">**bytes_copied**: число фактически скопированных байтов</span><span class="sxs-lookup"><span data-stu-id="d7262-1535">**bytes_copied** Number of bytes actually copied</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1536">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1536">Return Values</span></span>

- <span data-ttu-id="d7262-1537">**NX_SUCCESS** (0x00) — пакет успешно скопирован.</span><span class="sxs-lookup"><span data-stu-id="d7262-1537">**NX_SUCCESS** (0x00) Successful packet copy</span></span>
- <span data-ttu-id="d7262-1538">**NX_PACKET_OFFSET_ERROR** (0x53) — указано недопустимое значение смещения.</span><span class="sxs-lookup"><span data-stu-id="d7262-1538">**NX_PACKET_OFFSET_ERROR** (0x53) Invalid offset value was supplied</span></span>
- <span data-ttu-id="d7262-1539">**NX_PTR_ERROR** (0x07) — недопустимый указатель на пакет или буфер.</span><span class="sxs-lookup"><span data-stu-id="d7262-1539">**NX_PTR_ERROR** (0x07) Invalid packet pointer or buffer pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1540">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1540">Allowed From</span></span>

<span data-ttu-id="d7262-1541">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="d7262-1541">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1542">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1542">Preemption Possible</span></span>

<span data-ttu-id="d7262-1543">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1543">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1544">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1544">Example</span></span>

```C
/* Extract 10 bytes from the start of the received packet buffer
    into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
    &bytes_copied);

/* If status is NX_SUCCESS, 10 bytes were successfully copied into
    the data buffer. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1545">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1545">See Also</span></span>

- <span data-ttu-id="d7262-1546">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="d7262-1546">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="d7262-1547">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-1547">nx_packet_data_retrieve, nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="d7262-1548">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="d7262-1548">nx_packet_pool_delete, nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="d7262-1549">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="d7262-1549">nx_packet_transmit_release</span></span>

## <a name="nx_packet_data_retrieve"></a><span data-ttu-id="d7262-1550">nx_packet_data_retrieve</span><span class="sxs-lookup"><span data-stu-id="d7262-1550">nx_packet_data_retrieve</span></span>

<span data-ttu-id="d7262-1551">Получение данных из пакета</span><span class="sxs-lookup"><span data-stu-id="d7262-1551">Retrieve data from packet</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1552">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1552">Prototype</span></span>

```C
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start, 
    ULONG *bytes_copied);
```

### <a name="description"></a><span data-ttu-id="d7262-1553">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1553">Description</span></span>

<span data-ttu-id="d7262-1554">Эта служба копирует данные из предоставленного пакета в указанный буфер.</span><span class="sxs-lookup"><span data-stu-id="d7262-1554">This service copies data from the supplied packet into the supplied buffer.</span></span> <span data-ttu-id="d7262-1555">Фактическое число скопированных байтов возвращается в месте назначения, на которое указывает **bytes_copied**.</span><span class="sxs-lookup"><span data-stu-id="d7262-1555">The actual number of bytes copied is returned in the destination pointed to by **bytes_copied**.</span></span>

<span data-ttu-id="d7262-1556">Обратите внимание, что эта служба не изменяет внутреннее состояние пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1556">Note that this service does not change internal state of the packet.</span></span> <span data-ttu-id="d7262-1557">Получаемые данные по-прежнему доступны в пакете.</span><span class="sxs-lookup"><span data-stu-id="d7262-1557">The data being retrieved is still available in the packet.</span></span>

<span data-ttu-id="d7262-1558">*Буфер назначения должен быть достаточно большим, чтобы вместить содержимое пакета. В противном случае память будет повреждена, что приведет к непредсказуемым результатам.*</span><span class="sxs-lookup"><span data-stu-id="d7262-1558">*The destination buffer must be large enough to hold the packet's contents. If not, memory will be corrupted causing unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1559">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1559">Parameters</span></span>

- <span data-ttu-id="d7262-1560">**packet_ptr**: указатель на исходный пакет</span><span class="sxs-lookup"><span data-stu-id="d7262-1560">**packet_ptr** Pointer to the source packet.</span></span>
- <span data-ttu-id="d7262-1561">**buffer_start**: указатель на начало буферной области</span><span class="sxs-lookup"><span data-stu-id="d7262-1561">**buffer_start** Pointer to the start of the buffer area.</span></span>
- <span data-ttu-id="d7262-1562">**bytes_copied**: указатель на место назначения для числа скопированных байтов</span><span class="sxs-lookup"><span data-stu-id="d7262-1562">**bytes_copied** Pointer to the destination for the number of bytes copied.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1563">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1563">Return Values</span></span>

- <span data-ttu-id="d7262-1564">**NX_SUCCESS** (0x00) — данные успешно получены из пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1564">**NX_SUCCESS** (0x00) Successful packet data retrieve.</span></span>
- <span data-ttu-id="d7262-1565">**NX_INVALID_PACKET** (0x12) — недопустимый пакет.</span><span class="sxs-lookup"><span data-stu-id="d7262-1565">**NX_INVALID_PACKET** (0x12) Invalid packet.</span></span>
- <span data-ttu-id="d7262-1566">**NX_PTR_ERROR** (0x07) — недопустимый указатель на пакет, начало буфера или копируемые байты.</span><span class="sxs-lookup"><span data-stu-id="d7262-1566">**NX_PTR_ERROR** (0x07) Invalid packet, buffer start, or bytes copied pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1567">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1567">Allowed From</span></span>

<span data-ttu-id="d7262-1568">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="d7262-1568">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1569">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1569">Preemption Possible</span></span>

<span data-ttu-id="d7262-1570">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1570">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1571">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1571">Example</span></span>

```C
UCHAR buffer[512];
ULONG bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
    packet, the size of which is contained in "bytes_copied." */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1572">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1572">See Also</span></span>

- <span data-ttu-id="d7262-1573">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="d7262-1573">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="d7262-1574">nx_packet_data_extract_offset, nx_packet_length_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-1574">nx_packet_data_extract_offset, nx_packet_length_get,</span></span>
- <span data-ttu-id="d7262-1575">nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="d7262-1575">nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="d7262-1576">nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="d7262-1576">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="d7262-1577">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="d7262-1577">nx_packet_transmit_release</span></span>

## <a name="nx_packet_length_get"></a><span data-ttu-id="d7262-1578">nx_packet_length_get</span><span class="sxs-lookup"><span data-stu-id="d7262-1578">nx_packet_length_get</span></span>

<span data-ttu-id="d7262-1579">Получение длины данных в пакете</span><span class="sxs-lookup"><span data-stu-id="d7262-1579">Get length of packet data</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1580">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1580">Prototype</span></span>

```C
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```

### <a name="description"></a><span data-ttu-id="d7262-1581">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1581">Description</span></span>

<span data-ttu-id="d7262-1582">Эта служба получает длину данных в указанном пакете.</span><span class="sxs-lookup"><span data-stu-id="d7262-1582">This service gets the length of the data in the specified packet.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1583">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1583">Parameters</span></span>

- <span data-ttu-id="d7262-1584">**packet_ptr**: указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="d7262-1584">**packet_ptr** Pointer to the packet.</span></span>
- <span data-ttu-id="d7262-1585">**length**: место назначения для длины пакета</span><span class="sxs-lookup"><span data-stu-id="d7262-1585">**length** Destination for the packet length.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1586">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1586">Allowed From</span></span>

<span data-ttu-id="d7262-1587">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="d7262-1587">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1588">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1588">Preemption Possible</span></span>

<span data-ttu-id="d7262-1589">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1589">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1590">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1590">Example</span></span>

```C
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1591">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1591">See Also</span></span>

- <span data-ttu-id="d7262-1592">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="d7262-1592">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="d7262-1593">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="d7262-1593">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="d7262-1594">nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="d7262-1594">nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="d7262-1595">nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="d7262-1595">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="d7262-1596">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="d7262-1596">nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_create"></a><span data-ttu-id="d7262-1597">nx_packet_pool_create</span><span class="sxs-lookup"><span data-stu-id="d7262-1597">nx_packet_pool_create</span></span>

<span data-ttu-id="d7262-1598">Создание пула пакетов в указанной области памяти</span><span class="sxs-lookup"><span data-stu-id="d7262-1598">Create packet pool in specified memory area</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1599">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1599">Prototype</span></span>

```C
UINT nx_packet_pool_create(
    NX_PACKET_POOL *pool_ptr,
    CHAR *name,
    ULONG payload_size,
    VOID *memory_ptr,
    ULONG memory_size);
```

### <a name="description"></a><span data-ttu-id="d7262-1600">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1600">Description</span></span>

<span data-ttu-id="d7262-1601">Эта служба создает пул пакетов указанного размера в области памяти, заданной пользователем.</span><span class="sxs-lookup"><span data-stu-id="d7262-1601">This service creates a packet pool of the specified packet size in the memory area supplied by the user.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1602">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1602">Parameters</span></span>

- <span data-ttu-id="d7262-1603">**pool_ptr**: указатель на блок управления пулом пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-1603">**pool_ptr** Pointer to packet pool control block.</span></span>
- <span data-ttu-id="d7262-1604">**name**: указатель на имя приложения для пула пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-1604">**name** Pointer to application’s name for the packet pool.</span></span>
- <span data-ttu-id="d7262-1605">**payload_size**: число байтов в каждом пакете в пуле</span><span class="sxs-lookup"><span data-stu-id="d7262-1605">**payload_size** Number of bytes in each packet in the pool.</span></span> <span data-ttu-id="d7262-1606">Это значение должно быть не менее 40 байт и кратно 4.</span><span class="sxs-lookup"><span data-stu-id="d7262-1606">This value must be at least 40 bytes and must also be evenly divisible by 4.</span></span>
- <span data-ttu-id="d7262-1607">**memory_ptr**: указатель на область памяти, в которой будет размещен пул пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-1607">**memory_ptr** Pointer to the memory area to place the packet pool in.</span></span> <span data-ttu-id="d7262-1608">Указатель должен быть выровнен по границе ULONG.</span><span class="sxs-lookup"><span data-stu-id="d7262-1608">The pointer should be aligned on an ULONG boundary.</span></span>
- <span data-ttu-id="d7262-1609">**memory_size**: размер области памяти пула</span><span class="sxs-lookup"><span data-stu-id="d7262-1609">**memory_size** Size of the pool memory area.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1610">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1610">Return Values</span></span>

- <span data-ttu-id="d7262-1611">**NX_SUCCESS** (0x00) — пул пакетов успешно создан.</span><span class="sxs-lookup"><span data-stu-id="d7262-1611">**NX_SUCCESS** (0x00) Successful packet pool create.</span></span>
- <span data-ttu-id="d7262-1612">**NX_PTR_ERROR** (0x07) — недопустимый указатель на пул или память.</span><span class="sxs-lookup"><span data-stu-id="d7262-1612">**NX_PTR_ERROR** (0x07) Invalid pool or memory pointer.</span></span>
- <span data-ttu-id="d7262-1613">**NX_SIZE_ERROR** (0x09) — недопустимый размер блока или памяти.</span><span class="sxs-lookup"><span data-stu-id="d7262-1613">**NX_SIZE_ERROR** (0x09) Invalid block or memory size.</span></span>
- <span data-ttu-id="d7262-1614">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1614">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1615">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1615">Allowed From</span></span>

<span data-ttu-id="d7262-1616">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1616">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1617">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1617">Preemption Possible</span></span>

<span data-ttu-id="d7262-1618">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1618">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1619">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1619">Example</span></span>

```C
/* Create a packet pool of 32000 bytes starting at physical
    address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
    (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
    created. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1620">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1620">See Also</span></span>

- <span data-ttu-id="d7262-1621">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="d7262-1621">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="d7262-1622">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="d7262-1622">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="d7262-1623">nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-1623">nx_packet_length_get, nx_packet_pool_delete, nx_packet_pool_info_get,</span></span>
- <span data-ttu-id="d7262-1624">nx_packet_release, nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="d7262-1624">nx_packet_release, nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_delete"></a><span data-ttu-id="d7262-1625">nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-1625">nx_packet_pool_delete</span></span>

<span data-ttu-id="d7262-1626">Удаление ранее созданного пула пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-1626">Delete previously created packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1627">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1627">Prototype</span></span>

```C
UINT nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-1628">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1628">Description</span></span>

<span data-ttu-id="d7262-1629">Эта служба удаляет ранее созданный пул пакетов.</span><span class="sxs-lookup"><span data-stu-id="d7262-1629">This service deletes a previously-created packet pool.</span></span> <span data-ttu-id="d7262-1630">NetX проверяет все потоки, приостановленные при обработке пакетов в пуле пакетов, и отменяет приостановку.</span><span class="sxs-lookup"><span data-stu-id="d7262-1630">NetX checks for any threads currently suspended on packets in the packet pool and clears the suspension.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1631">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1631">Parameters</span></span>

- <span data-ttu-id="d7262-1632">**pool_ptr**: указатель на блок управления пулом пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-1632">**pool_ptr** Packet pool control block pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1633">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1633">Return Values</span></span>

- <span data-ttu-id="d7262-1634">**NX_SUCCESS** (0x00) — пул пакетов успешно удален.</span><span class="sxs-lookup"><span data-stu-id="d7262-1634">**NX_SUCCESS** (0x00) Successful packet pool delete.</span></span>
- <span data-ttu-id="d7262-1635">**NX_PTR_ERROR** (0x07) — недопустимый указатель на пул.</span><span class="sxs-lookup"><span data-stu-id="d7262-1635">**NX_PTR_ERROR** (0x07) Invalid pool pointer.</span></span>
- <span data-ttu-id="d7262-1636">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1636">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1637">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1637">Allowed From</span></span>

<span data-ttu-id="d7262-1638">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1638">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1639">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1639">Preemption Possible</span></span>

<span data-ttu-id="d7262-1640">Да</span><span class="sxs-lookup"><span data-stu-id="d7262-1640">Yes</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1641">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1641">Example</span></span>

```C
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
    deleted. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1642">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1642">See Also</span></span>

- <span data-ttu-id="d7262-1643">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="d7262-1643">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="d7262-1644">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="d7262-1644">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="d7262-1645">nx_packet_length_get, nx_packet_pool_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-1645">nx_packet_length_get, nx_packet_pool_create,</span></span>
- <span data-ttu-id="d7262-1646">nx_packet_pool_info_get, nx_packet_release,</span><span class="sxs-lookup"><span data-stu-id="d7262-1646">nx_packet_pool_info_get, nx_packet_release,</span></span>
- <span data-ttu-id="d7262-1647">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="d7262-1647">nx_packet_transmit_release</span></span>

## <a name="nx_packet_pool_info_get"></a><span data-ttu-id="d7262-1648">nx_packet_pool_info_get</span><span class="sxs-lookup"><span data-stu-id="d7262-1648">nx_packet_pool_info_get</span></span>

<span data-ttu-id="d7262-1649">Получение сведений о пуле пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-1649">Retrieve information about a packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1650">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1650">Prototype</span></span>

```C
UINT nx_packet_pool_info_get(
    NX_PACKET_POOL *pool_ptr,
    ULONG *total_packets,
    ULONG *free_packets,
    ULONG *empty_pool_requests,
    ULONG *empty_pool_suspensions,
    ULONG *invalid_packet_releases);
```

### <a name="description"></a><span data-ttu-id="d7262-1651">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1651">Description</span></span>

<span data-ttu-id="d7262-1652">Эта служба получает сведения об указанном пуле пакетов.</span><span class="sxs-lookup"><span data-stu-id="d7262-1652">This service retrieves information about the specified packet pool.</span></span>

<span data-ttu-id="d7262-1653">*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.</span><span class="sxs-lookup"><span data-stu-id="d7262-1653">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1654">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1654">Parameters</span></span>

- <span data-ttu-id="d7262-1655">**pool_ptr**: указатель на ранее созданный пул пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-1655">**pool_ptr** Pointer to previously created packet pool.</span></span>
- <span data-ttu-id="d7262-1656">**total_packets**: указатель на место назначения для общего числа пакетов в пуле</span><span class="sxs-lookup"><span data-stu-id="d7262-1656">**total_packets** Pointer to destination for the total number of packets in the pool.</span></span>
- <span data-ttu-id="d7262-1657">**free_packets**: указатель на место назначения для общего числа пакетов, свободных в настоящее время</span><span class="sxs-lookup"><span data-stu-id="d7262-1657">**free_packets** Pointer to destination for the total number of currently free packets.</span></span>
- <span data-ttu-id="d7262-1658">**empty_pool_requests**: указатель на место назначения для общего числа запросов на выделение, если пул был пуст</span><span class="sxs-lookup"><span data-stu-id="d7262-1658">**empty_pool_requests** Pointer to destination of the total number of allocation requests when the pool was empty.</span></span>
- <span data-ttu-id="d7262-1659">**empty_pool_suspensions**: указатель на место назначения для общего числа приостановок в пустом пуле</span><span class="sxs-lookup"><span data-stu-id="d7262-1659">**empty_pool_suspensions** Pointer to destination of the total number of empty pool suspensions.</span></span>
- <span data-ttu-id="d7262-1660">**invalid_packet_releases**: указатель на место назначения для общего числа недопустимых освобождений пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-1660">**invalid_packet_releases** Pointer to destination of the total number of invalid packet releases.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1661">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1661">Return Values</span></span>

- <span data-ttu-id="d7262-1662">**NX_SUCCESS** (0x00) — сведения о пуле пакетов успешно получены.</span><span class="sxs-lookup"><span data-stu-id="d7262-1662">**NX_SUCCESS** (0x00) Successful packet pool information retrieval.</span></span>
- <span data-ttu-id="d7262-1663">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-1663">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-1664">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1664">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1665">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1665">Allowed From</span></span>

<span data-ttu-id="d7262-1666">Инициализация, потоки, таймеры</span><span class="sxs-lookup"><span data-stu-id="d7262-1666">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1667">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1667">Preemption Possible</span></span>

<span data-ttu-id="d7262-1668">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1668">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1669">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1669">Example</span></span>

```C
/* Retrieve packet pool information. */
status = nx_packet_pool_info_get(&pool_0,
    &total_packets,
    &free_packets,
    &empty_pool_requests,
    &empty_pool_suspensions,
    &invalid_packet_releases);

/* If status is NX_SUCCESS, packet pool information was
    retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1670">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1670">See Also</span></span>

- <span data-ttu-id="d7262-1671">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="d7262-1671">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="d7262-1672">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="d7262-1672">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="d7262-1673">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-1673">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete</span></span>
- <span data-ttu-id="d7262-1674">nx_packet_release, nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="d7262-1674">nx_packet_release, nx_packet_transmit_release</span></span>

## <a name="nx_packet_release"></a><span data-ttu-id="d7262-1675">nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="d7262-1675">nx_packet_release</span></span>

<span data-ttu-id="d7262-1676">Освобождение ранее выделенного пакета</span><span class="sxs-lookup"><span data-stu-id="d7262-1676">Release previously allocated packet</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1677">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1677">Prototype</span></span>

```C
UINT nx_packet_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-1678">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1678">Description</span></span>

<span data-ttu-id="d7262-1679">Эта служба освобождает пакет, а также все сцепленные с ним пакеты.</span><span class="sxs-lookup"><span data-stu-id="d7262-1679">This service releases a packet, including any additional packets chained to the specified packet.</span></span> <span data-ttu-id="d7262-1680">Если другой поток блокируется при выделении пакета, ему предоставляется пакет и его работа возобновляется.</span><span class="sxs-lookup"><span data-stu-id="d7262-1680">If another thread is blocked on packet allocation, it is given the packet and resumed.</span></span>

<span data-ttu-id="d7262-1681">*Приложение должно предотвращать многократное освобождение пакета, так как оно приведет к непредсказуемым результатам.*</span><span class="sxs-lookup"><span data-stu-id="d7262-1681">*The application must prevent releasing a packet more than once, because doing so will cause unpredictable results.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1682">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1682">Parameters</span></span>

- <span data-ttu-id="d7262-1683">**packet_ptr**: указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="d7262-1683">**packet_ptr** Packet pointer.</span></span>


### <a name="return-values"></a><span data-ttu-id="d7262-1684">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1684">Return Values</span></span>
- <span data-ttu-id="d7262-1685">**NX_SUCCESS** (0x00) — пакет успешно освобожден.</span><span class="sxs-lookup"><span data-stu-id="d7262-1685">**NX_SUCCESS** (0x00) Successful packet release.</span></span>
- <span data-ttu-id="d7262-1686">**NX_PTR_ERROR** (0x07) — недопустимый указатель пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1686">**NX_PTR_ERROR** (0x07) Invalid packet pointer.</span></span>
- <span data-ttu-id="d7262-1687">**NX_UNDERFLOW** (0x02) — начальный указатель меньше, чем начало полезных данных.</span><span class="sxs-lookup"><span data-stu-id="d7262-1687">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="d7262-1688">**NX_OVERFLOW** (0x03) — конечный указатель меньше, чем конец полезных данных.</span><span class="sxs-lookup"><span data-stu-id="d7262-1688">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1689">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1689">Allowed From</span></span>

<span data-ttu-id="d7262-1690">Инициализация, потоки, таймеры и запросы ISR (сетевые драйверы приложений)</span><span class="sxs-lookup"><span data-stu-id="d7262-1690">Initialization, threads, timers, and ISRs (application network drivers)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1691">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1691">Preemption Possible</span></span>

<span data-ttu-id="d7262-1692">Да</span><span class="sxs-lookup"><span data-stu-id="d7262-1692">Yes</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1693">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1693">Example</span></span>

```C
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
    packet pool it was allocated from. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1694">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1694">See Also</span></span>

- <span data-ttu-id="d7262-1695">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="d7262-1695">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="d7262-1696">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="d7262-1696">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="d7262-1697">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="d7262-1697">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="d7262-1698">nx_packet_pool_info_get, nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="d7262-1698">nx_packet_pool_info_get, nx_packet_transmit_release</span></span>

## <a name="nx_packet_transmit_release"></a><span data-ttu-id="d7262-1699">nx_packet_transmit_release</span><span class="sxs-lookup"><span data-stu-id="d7262-1699">nx_packet_transmit_release</span></span>

<span data-ttu-id="d7262-1700">Освобождение переданного пакета</span><span class="sxs-lookup"><span data-stu-id="d7262-1700">Release a transmitted packet</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1701">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1701">Prototype</span></span>

```C
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-1702">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1702">Description</span></span>

<span data-ttu-id="d7262-1703">Для пакетов, отличных от TCP, эта служба освобождает переданный пакет, а также все сцепленные с ним пакеты.</span><span class="sxs-lookup"><span data-stu-id="d7262-1703">For non-TCP packets, this service releases a transmitted packet, including any additional packets chained to the specified packet.</span></span> <span data-ttu-id="d7262-1704">Если другой поток блокируется при выделении пакета, ему предоставляется пакет и его работа возобновляется.</span><span class="sxs-lookup"><span data-stu-id="d7262-1704">If another thread is blocked on packet allocation, it is given the packet and resumed.</span></span> <span data-ttu-id="d7262-1705">TCP-пакет помечается как передаваемый, но не освобождается, пока не будет подтвержден.</span><span class="sxs-lookup"><span data-stu-id="d7262-1705">For a transmitted TCP packet, the packet is marked as being transmitted but not released till the packet is acknowledged.</span></span> <span data-ttu-id="d7262-1706">Эта служба обычно вызывается из сетевого драйвера приложения после передачи пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1706">This service is typically called from the application's network driver after a packet is transmitted.</span></span>

<span data-ttu-id="d7262-1707">*Сетевой драйвер должен удалить заголовок физического носителя и изменить длину пакета перед вызовом этой службы.*</span><span class="sxs-lookup"><span data-stu-id="d7262-1707">*The network driver should remove the physical media header and adjust the length of the packet before calling this service.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1708">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1708">Parameters</span></span>

- <span data-ttu-id="d7262-1709">**packet_ptr**: указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="d7262-1709">**packet_ptr** Packet pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1710">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1710">Return Values</span></span>

- <span data-ttu-id="d7262-1711">**NX_SUCCESS** (0x00) — переданный пакет успешно освобожден.</span><span class="sxs-lookup"><span data-stu-id="d7262-1711">**NX_SUCCESS** (0x00) Successful transmit packet release.</span></span>
- <span data-ttu-id="d7262-1712">**NX_PTR_ERROR** (0x07) — недопустимый указатель пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1712">**NX_PTR_ERROR** (0x07) Invalid packet pointer.</span></span>
- <span data-ttu-id="d7262-1713">**NX_UNDERFLOW** (0x02) — начальный указатель меньше, чем начало полезных данных.</span><span class="sxs-lookup"><span data-stu-id="d7262-1713">**NX_UNDERFLOW** (0x02) Prepend pointer is less than payload start.</span></span>
- <span data-ttu-id="d7262-1714">**NX_OVERFLOW** (0x03) — конечный указатель меньше, чем конец полезных данных.</span><span class="sxs-lookup"><span data-stu-id="d7262-1714">**NX_OVERFLOW** (0x03) Append pointer is greater than payload end.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1715">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1715">Allowed From</span></span>

<span data-ttu-id="d7262-1716">Инициализация, потоки, таймеры, сетевые драйверы приложений (запросы ISR)</span><span class="sxs-lookup"><span data-stu-id="d7262-1716">Initialization, threads, timers, Application network drivers (including ISRs)</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1717">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1717">Preemption Possible</span></span>

<span data-ttu-id="d7262-1718">Да</span><span class="sxs-lookup"><span data-stu-id="d7262-1718">Yes</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1719">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1719">Example</span></span>

```C
/* Release a previously allocated packet that was just transmitted
    from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
    returned to the packet pool it was allocated from. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1720">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1720">See Also</span></span>

- <span data-ttu-id="d7262-1721">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span><span class="sxs-lookup"><span data-stu-id="d7262-1721">nx_packet_allocate, nx_packet_copy, nx_packet_data_append,</span></span>
- <span data-ttu-id="d7262-1722">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span><span class="sxs-lookup"><span data-stu-id="d7262-1722">nx_packet_data_extract_offset, nx_packet_data_retrieve,</span></span>
- <span data-ttu-id="d7262-1723">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span><span class="sxs-lookup"><span data-stu-id="d7262-1723">nx_packet_length_get, nx_packet_pool_create, nx_packet_pool_delete,</span></span>
- <span data-ttu-id="d7262-1724">nx_packet_pool_info_get, nx_packet_release</span><span class="sxs-lookup"><span data-stu-id="d7262-1724">nx_packet_pool_info_get, nx_packet_release</span></span>

## <a name="nx_rarp_disable"></a><span data-ttu-id="d7262-1725">nx_rarp_disable</span><span class="sxs-lookup"><span data-stu-id="d7262-1725">nx_rarp_disable</span></span>

<span data-ttu-id="d7262-1726">Отключение протокола RARP</span><span class="sxs-lookup"><span data-stu-id="d7262-1726">Disable Reverse Address Resolution Protocol (RARP)</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1727">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1727">Prototype</span></span>

```C
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-1728">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1728">Description</span></span>

<span data-ttu-id="d7262-1729">Эта служба отключает компонент RARP для определенного экземпляра IP в NetX.</span><span class="sxs-lookup"><span data-stu-id="d7262-1729">This service disables the RARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="d7262-1730">В системе с множественной адресацией эта служба отключает протокол RARP во всех интерфейсах.</span><span class="sxs-lookup"><span data-stu-id="d7262-1730">For a multihome system, this service disables RARP on all interfaces.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1731">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1731">Parameters</span></span>

- <span data-ttu-id="d7262-1732">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1732">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1733">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1733">Return Values</span></span>

- <span data-ttu-id="d7262-1734">**NX_SUCCESS** (0x00) — успешное отключение RARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-1734">**NX_SUCCESS** (0x00) Successful RARP disable.</span></span>
- <span data-ttu-id="d7262-1735">**NX_NOT_ENABLED** (0x14) — протокол RARP не был включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-1735">**NX_NOT_ENABLED** (0x14) RARP was not enabled.</span></span>
- <span data-ttu-id="d7262-1736">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-1736">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-1737">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1737">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1738">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1738">Allowed From</span></span>

<span data-ttu-id="d7262-1739">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1739">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1740">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1740">Preemption Possible</span></span>

<span data-ttu-id="d7262-1741">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1741">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1742">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1742">Example</span></span>

```C
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1743">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1743">See Also</span></span>

- <span data-ttu-id="d7262-1744">nx_rarp_enable, nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="d7262-1744">nx_rarp_enable, nx_rarp_info_get</span></span>

## <a name="nx_rarp_enable"></a><span data-ttu-id="d7262-1745">nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="d7262-1745">nx_rarp_enable</span></span>

<span data-ttu-id="d7262-1746">Включение протокола RARP</span><span class="sxs-lookup"><span data-stu-id="d7262-1746">Enable Reverse Address Resolution Protocol (RARP)</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1747">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1747">Prototype</span></span>

```C
UINT nx_rarp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-1748">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1748">Description</span></span>

<span data-ttu-id="d7262-1749">Эта служба включает компонент RARP для определенного экземпляра IP в NetX.</span><span class="sxs-lookup"><span data-stu-id="d7262-1749">This service enables the RARP component of NetX for the specific IP instance.</span></span> <span data-ttu-id="d7262-1750">Компонент RARP выполняет поиск нулевого IP-адреса во всех подключенных сетевых интерфейсах.</span><span class="sxs-lookup"><span data-stu-id="d7262-1750">The RARP components searches through all attached network interfaces for zero IP address.</span></span> <span data-ttu-id="d7262-1751">Нулевой IP-адрес означает, что интерфейсу еще не назначен IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d7262-1751">A zero IP address indicates the interface does not have IP address assignment yet.</span></span> <span data-ttu-id="d7262-1752">Протокол RARP пытается разрешить IP-адрес, включив в нем процесс RARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-1752">RARP attempts to resolve the IP address by enabling RARP process on that interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1753">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1753">Parameters</span></span>

- <span data-ttu-id="d7262-1754">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1754">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1755">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1755">Return Values</span></span>

- <span data-ttu-id="d7262-1756">**NX_SUCCESS** (0x00) — успешное включение RARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-1756">**NX_SUCCESS** (0x00) Successful RARP enable.</span></span>
- <span data-ttu-id="d7262-1757">**NX_IP_ADDRESS_ERROR** (0x21) — уже есть действительный IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d7262-1757">**NX_IP_ADDRESS_ERROR** (0x21) IP address is already valid.</span></span>
- <span data-ttu-id="d7262-1758">**NX_ALREADY_ENABLED** (0x15) — протокол RARP уже включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-1758">**NX_ALREADY_ENABLED** (0x15) RARP was already enabled.</span></span>
- <span data-ttu-id="d7262-1759">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-1759">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-1760">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1760">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1761">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1761">Allowed From</span></span>

<span data-ttu-id="d7262-1762">Инициализация, потоки, таймеры</span><span class="sxs-lookup"><span data-stu-id="d7262-1762">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1763">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1763">Preemption Possible</span></span>

<span data-ttu-id="d7262-1764">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1764">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1765">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1765">Example</span></span>

```C
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
    resolve this IP instance’s address by querying the network. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1766">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1766">See Also</span></span>

- <span data-ttu-id="d7262-1767">nx_rarp_disable, nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="d7262-1767">nx_rarp_disable, nx_rarp_info_get</span></span>

## <a name="nx_rarp_info_get"></a><span data-ttu-id="d7262-1768">nx_rarp_info_get</span><span class="sxs-lookup"><span data-stu-id="d7262-1768">nx_rarp_info_get</span></span>

<span data-ttu-id="d7262-1769">Получение сведений о действиях RARP</span><span class="sxs-lookup"><span data-stu-id="d7262-1769">Retrieve information about RARP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1770">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1770">Prototype</span></span>

```C
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```

### <a name="description"></a><span data-ttu-id="d7262-1771">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1771">Description</span></span>

<span data-ttu-id="d7262-1772">Эта служба получает сведения о действиях протокола RARP для указанного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-1772">This service retrieves information about RARP activities for the specified IP instance.</span></span>

<span data-ttu-id="d7262-1773">*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.</span><span class="sxs-lookup"><span data-stu-id="d7262-1773">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1774">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1774">Parameters</span></span>

- <span data-ttu-id="d7262-1775">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1775">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-1776">**rarp_requests_sent**: указатель на место назначения для общего числа отправленных запросов RARP</span><span class="sxs-lookup"><span data-stu-id="d7262-1776">**rarp_requests_sent** Pointer to destination for the total number of RARP requests sent.</span></span>
- <span data-ttu-id="d7262-1777">**rarp_responses_received**: указатель на место назначения для общего числа полученных ответов RARP</span><span class="sxs-lookup"><span data-stu-id="d7262-1777">**rarp_responses_received** Pointer to destination for the total number of RARP responses received.</span></span>
- <span data-ttu-id="d7262-1778">**rarp_invalid_messages**: указатель на место назначения для общего числа недопустимых сообщений</span><span class="sxs-lookup"><span data-stu-id="d7262-1778">**rarp_invalid_messages** Pointer to destination of the total number of invalid messages.</span></span>


### <a name="return-values"></a><span data-ttu-id="d7262-1779">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1779">Return Values</span></span>
- <span data-ttu-id="d7262-1780">**NX_SUCCESS** (0x00) — успешное получение сведений RARP.</span><span class="sxs-lookup"><span data-stu-id="d7262-1780">**NX_SUCCESS** (0x00) Successful RARP information retrieval.</span></span>
- <span data-ttu-id="d7262-1781">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-1781">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-1782">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-1782">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="d7262-1783">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1783">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1784">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1784">Allowed From</span></span>

<span data-ttu-id="d7262-1785">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1785">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1786">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1786">Preemption Possible</span></span>

<span data-ttu-id="d7262-1787">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1787">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1788">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1788">Example</span></span>

```C
/* Retrieve RARP information from previously created IP
    Instance 0. */
status = nx_rarp_info_get(&ip_0,
    &rarp_requests_sent,
    &rarp_responses_received,
    &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1789">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1789">See Also</span></span>

- <span data-ttu-id="d7262-1790">nx_rarp_disable, nx_rarp_enable</span><span class="sxs-lookup"><span data-stu-id="d7262-1790">nx_rarp_disable, nx_rarp_enable</span></span>

## <a name="nx_system_initialize"></a><span data-ttu-id="d7262-1791">nx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="d7262-1791">nx_system_initialize</span></span>

<span data-ttu-id="d7262-1792">Инициализация системы NetX</span><span class="sxs-lookup"><span data-stu-id="d7262-1792">Initialize NetX System</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1793">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1793">Prototype</span></span>

```C
VOID nx_system_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="d7262-1794">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1794">Description</span></span>

<span data-ttu-id="d7262-1795">Эта служба инициализирует базовые системные ресурсы NetX в процессе подготовки к использованию.</span><span class="sxs-lookup"><span data-stu-id="d7262-1795">This service initializes the basic NetX system resources in preparation for use.</span></span> <span data-ttu-id="d7262-1796">Она должна вызываться приложением во время инициализации до выполнения других вызовов NetX.</span><span class="sxs-lookup"><span data-stu-id="d7262-1796">It should be called by the application during initialization and before any other NetX call are made.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1797">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1797">Parameters</span></span>

<span data-ttu-id="d7262-1798">None</span><span class="sxs-lookup"><span data-stu-id="d7262-1798">None</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1799">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1799">Return Values</span></span>

<span data-ttu-id="d7262-1800">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1800">None</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1801">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1801">Allowed From</span></span>

<span data-ttu-id="d7262-1802">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="d7262-1802">Initialization, threads, timers, ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1803">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1803">Preemption Possible</span></span>

<span data-ttu-id="d7262-1804">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1804">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1805">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1805">Example</span></span>

```C
/* Initialize NetX for operation. */
nx_system_initialize();

/* At this point, NetX is ready for IP creation and all subsequent
    network operations. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1806">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1806">See Also</span></span>

- <span data-ttu-id="d7262-1807">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-1807">nx_ip_address_change_notify, nx_ip_address_get, nx_ip_address_set,</span></span>
- <span data-ttu-id="d7262-1808">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span><span class="sxs-lookup"><span data-stu-id="d7262-1808">nx_ip_create, nx_ip_delete, nx_ip_driver_direct_command,</span></span>
- <span data-ttu-id="d7262-1809">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-1809">nx_ip_driver_interface_direct_command, nx_ip_forwarding_disable,</span></span>
- <span data-ttu-id="d7262-1810">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-1810">nx_ip_forwarding_enable, nx_ip_fragment_disable,</span></span>
- <span data-ttu-id="d7262-1811">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span><span class="sxs-lookup"><span data-stu-id="d7262-1811">nx_ip_fragment_enable, nx_ip_info_get, nx_ip_status_check</span></span>

## <a name="nx_tcp_client_socket_bind"></a><span data-ttu-id="d7262-1812">nx_tcp_client_socket_bind</span><span class="sxs-lookup"><span data-stu-id="d7262-1812">nx_tcp_client_socket_bind</span></span>

<span data-ttu-id="d7262-1813">Привязка клиентского сокета TCP к TCP-порту</span><span class="sxs-lookup"><span data-stu-id="d7262-1813">Bind client TCP socket to TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1814">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1814">Prototype</span></span>

```C
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d7262-1815">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1815">Description</span></span>

<span data-ttu-id="d7262-1816">Эта служба привязывает ранее созданный клиентский сокет TCP к указанному TCP-порту.</span><span class="sxs-lookup"><span data-stu-id="d7262-1816">This service binds the previously created TCP client socket to the specified TCP port.</span></span> <span data-ttu-id="d7262-1817">Допустимый диапазон сокетов TCP — от 0 до 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="d7262-1817">Valid TCP sockets range from 0 through 0xFFFF.</span></span> <span data-ttu-id="d7262-1818">Если указанный TCP-порт недоступен, служба приостанавливает выполнение в соответствии с указанным параметром ожидания.</span><span class="sxs-lookup"><span data-stu-id="d7262-1818">If the specified TCP port is unavailable, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1819">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1819">Parameters</span></span>

- <span data-ttu-id="d7262-1820">**socket_ptr**: указатель на ранее созданный экземпляр сокета TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-1820">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="d7262-1821">**port**: номер порта для привязки (от 1 до 0xFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-1821">**port** Port number to bind (1 through 0xFFFF).</span></span> <span data-ttu-id="d7262-1822">Если номер порта — NX_ANY_PORT (0x0000), экземпляр IP будет искать следующий свободный порт и использует его для привязки.</span><span class="sxs-lookup"><span data-stu-id="d7262-1822">If port number is NX_ANY_PORT (0x0000), the IP instance will search for the next free port and use that for the binding.</span></span>
- <span data-ttu-id="d7262-1823">**wait_option**: определяет поведение службы в случае, если порт уже привязан к другому сокету</span><span class="sxs-lookup"><span data-stu-id="d7262-1823">**wait_option** Defines how the service behaves if the port is already bound to another socket.</span></span> <span data-ttu-id="d7262-1824">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d7262-1824">The wait options are defined as follows:</span></span>
- <span data-ttu-id="d7262-1825">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-1825">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="d7262-1826">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-1826">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="d7262-1827">Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d7262-1827">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1828">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1828">Return Values</span></span>

- <span data-ttu-id="d7262-1829">**NX_SUCCESS** (0x00) — сокет успешно привязан.</span><span class="sxs-lookup"><span data-stu-id="d7262-1829">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="d7262-1830">**NX_ALREADY_BOUND** (0x22) — этот сокет уже привязан к другому TCP-порту.</span><span class="sxs-lookup"><span data-stu-id="d7262-1830">**NX_ALREADY_BOUND** (0x22) This socket is already bound to another TCP port.</span></span>
- <span data-ttu-id="d7262-1831">**NX_PORT_UNAVAILABLE** (0x23) — порт уже привязан к другому сокету.</span><span class="sxs-lookup"><span data-stu-id="d7262-1831">**NX_PORT_UNAVAILABLE** (0x23) Port is already bound to a different socket.</span></span>
- <span data-ttu-id="d7262-1832">**NX_NO_FREE_PORTS** (0x45) — нет свободного порта.</span><span class="sxs-lookup"><span data-stu-id="d7262-1832">**NX_NO_FREE_PORTS** (0x45) No free port.</span></span>
- <span data-ttu-id="d7262-1833">**NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="d7262-1833">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="d7262-1834">**NX_INVALID_PORT** (0x46) — недопустимый порт.</span><span class="sxs-lookup"><span data-stu-id="d7262-1834">**NX_INVALID_PORT** (0x46) Invalid port.</span></span>
- <span data-ttu-id="d7262-1835">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1835">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-1836">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1836">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-1837">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-1837">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1838">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1838">Allowed From</span></span>

<span data-ttu-id="d7262-1839">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1839">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1840">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1840">Preemption Possible</span></span>

<span data-ttu-id="d7262-1841">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1841">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1842">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1842">Example</span></span>

```C
/* Bind a previously created client socket to port 12 and wait for 7
    timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
    bound to port 12 on the associated IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1843">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1843">See Also</span></span>

- <span data-ttu-id="d7262-1844">nx_tcp_client_socket_connect, nx_tcp_client_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-1844">nx_tcp_client_socket_connect, nx_tcp_client_socket_port_get,</span></span>
- <span data-ttu-id="d7262-1845">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span><span class="sxs-lookup"><span data-stu-id="d7262-1845">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="d7262-1846">nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="d7262-1846">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="d7262-1847">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-1847">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="d7262-1848">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-1848">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="d7262-1849">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-1849">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-1850">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-1850">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-1851">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-1851">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="d7262-1852">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-1852">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="d7262-1853">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-1853">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_connect"></a><span data-ttu-id="d7262-1854">nx_tcp_client_socket_connect</span><span class="sxs-lookup"><span data-stu-id="d7262-1854">nx_tcp_client_socket_connect</span></span>

<span data-ttu-id="d7262-1855">Подключение клиентского сокета TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-1855">Connect client TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1856">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1856">Prototype</span></span>

```C
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d7262-1857">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1857">Description</span></span>

<span data-ttu-id="d7262-1858">Эта служба подключает ранее созданный и привязанный клиентский сокет TCP к указанному порту сервера.</span><span class="sxs-lookup"><span data-stu-id="d7262-1858">This service connects the previously-created and bound TCP client socket to the specified server's port.</span></span> <span data-ttu-id="d7262-1859">Допустимый диапазон портов TCP-сервера — от 0 до 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="d7262-1859">Valid TCP server ports range from 0 through 0xFFFF.</span></span> <span data-ttu-id="d7262-1860">Если подключение не завершается немедленно, служба приостанавливает выполнение в соответствии с указанным параметром ожидания.</span><span class="sxs-lookup"><span data-stu-id="d7262-1860">If the connection does not complete immediately, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1861">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1861">Parameters</span></span>

- <span data-ttu-id="d7262-1862">**socket_ptr**: указатель на ранее созданный экземпляр сокета TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-1862">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="d7262-1863">**server_ip**: IP-адрес сервера</span><span class="sxs-lookup"><span data-stu-id="d7262-1863">**server_ip** Server’s IP address.</span></span>
- <span data-ttu-id="d7262-1864">**server_port**: номер порта сервера для подключения (от 1 до 0xFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-1864">**server_port** Server port number to connect to (1 through 0xFFFF).</span></span>
- <span data-ttu-id="d7262-1865">**wait_option** определяет поведение службы во время установления соединения</span><span class="sxs-lookup"><span data-stu-id="d7262-1865">**wait_option** Defines how the service behaves while the connection is being established.</span></span> <span data-ttu-id="d7262-1866">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d7262-1866">The wait options are defined as follows:</span></span>
- <span data-ttu-id="d7262-1867">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-1867">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="d7262-1868">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-1868">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="d7262-1869">Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d7262-1869">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1870">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1870">Return Values</span></span>

- <span data-ttu-id="d7262-1871">**NX_SUCCESS** (0x00) — сокет успешно подключен.</span><span class="sxs-lookup"><span data-stu-id="d7262-1871">**NX_SUCCESS** (0x00) Successful socket connect.</span></span>
- <span data-ttu-id="d7262-1872">**NX_NOT_BOUND** (0x24) — сокет не привязан.</span><span class="sxs-lookup"><span data-stu-id="d7262-1872">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="d7262-1873">**NX_NOT_CLOSED** (0x35) — сокет не находится в закрытом состоянии.</span><span class="sxs-lookup"><span data-stu-id="d7262-1873">**NX_NOT_CLOSED** (0x35) Socket is not in a closed state.</span></span>
- <span data-ttu-id="d7262-1874">**NX_IN_PROGRESS** (0x37) — параметр ожидания не указан; выполняется попытка подключения.</span><span class="sxs-lookup"><span data-stu-id="d7262-1874">**NX_IN_PROGRESS** (0x37) No wait was specified, the connection attempt is in progress.</span></span>
- <span data-ttu-id="d7262-1875">**NX_INVALID_INTERFACE** (0x4C) — указан недопустимый интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d7262-1875">**NX_INVALID_INTERFACE** (0x4C) Invalid interface supplied.</span></span>
- <span data-ttu-id="d7262-1876">**NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="d7262-1876">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="d7262-1877">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="d7262-1877">**NX_IP_ADDRESS_ERROR** (0x21) Invalid server IP address.</span></span>
- <span data-ttu-id="d7262-1878">**NX_INVALID_PORT** (0x46) — недопустимый порт.</span><span class="sxs-lookup"><span data-stu-id="d7262-1878">**NX_INVALID_PORT** (0x46) Invalid port.</span></span>
- <span data-ttu-id="d7262-1879">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1879">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-1880">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1880">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-1881">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-1881">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1882">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1882">Allowed From</span></span>

<span data-ttu-id="d7262-1883">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1883">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1884">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1884">Preemption Possible</span></span>

<span data-ttu-id="d7262-1885">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1885">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1886">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1886">Example</span></span>

```C
/* Initiate a TCP connection from a previously created and bound
    client socket. The connection requested in this example is to
    port 12 on the server with the IP address of 1.2.3.5. This
    service will wait 300 timer ticks for the connection to take
    place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
    IP_ADDRESS(1,2,3,5), 12, 300);

/* If status is NX_SUCCESS, the previously created and bound
    client_socket is connected to port 12 on IP 1.2.3.5. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1887">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1887">See Also</span></span>

- <span data-ttu-id="d7262-1888">nx_tcp_client_socket_bind, nx_tcp_client_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-1888">nx_tcp_client_socket_bind, nx_tcp_client_socket_port_get,</span></span>
- <span data-ttu-id="d7262-1889">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span><span class="sxs-lookup"><span data-stu-id="d7262-1889">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="d7262-1890">nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="d7262-1890">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="d7262-1891">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-1891">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="d7262-1892">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-1892">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="d7262-1893">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-1893">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-1894">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-1894">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-1895">nx_tcp_socket_info_get, nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="d7262-1895">nx_tcp_socket_info_get, nx_tcp_socket_receive</span></span>
- <span data-ttu-id="d7262-1896">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-1896">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="d7262-1897">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-1897">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_port_get"></a><span data-ttu-id="d7262-1898">nx_tcp_client_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="d7262-1898">nx_tcp_client_socket_port_get</span></span>

<span data-ttu-id="d7262-1899">Получение номера порта, привязанного к клиентскому сокету TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-1899">Get port number bound to client TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1900">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1900">Prototype</span></span>

```C
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-1901">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1901">Description</span></span>

<span data-ttu-id="d7262-1902">Эта служба получает номер порта, связанного с сокетом, что может быть полезно при поиске порта, выделенного NetX, если во время привязки сокета было указано значение NX_ANY_PORT.</span><span class="sxs-lookup"><span data-stu-id="d7262-1902">This service retrieves the port number associated with the socket, which is useful to find the port allocated by NetX in situations where the NX_ANY_PORT was specified at the time the socket was bound.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1903">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1903">Parameters</span></span>

- <span data-ttu-id="d7262-1904">**socket_ptr**: указатель на ранее созданный экземпляр сокета TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-1904">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="d7262-1905">**port_ptr**: указатель на место назначения для возвращаемого номера порта</span><span class="sxs-lookup"><span data-stu-id="d7262-1905">**port_ptr** Pointer to destination for the return port number.</span></span> <span data-ttu-id="d7262-1906">Допустимые номера портов: от 1 до 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="d7262-1906">Valid port numbers are (1 through 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1907">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1907">Return Values</span></span>

- <span data-ttu-id="d7262-1908">**NX_SUCCESS** (0x00) — сокет успешно привязан.</span><span class="sxs-lookup"><span data-stu-id="d7262-1908">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="d7262-1909">**NX_NOT_BOUND** (0x24) — этот сокет не привязан к порту.</span><span class="sxs-lookup"><span data-stu-id="d7262-1909">**NX_NOT_BOUND** (0x24) This socket is not bound to a port.</span></span>
- <span data-ttu-id="d7262-1910">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета или возвращаемого порта.</span><span class="sxs-lookup"><span data-stu-id="d7262-1910">**NX_PTR_ERROR** (0x07) Invalid socket pointer or port return pointer.</span></span>
- <span data-ttu-id="d7262-1911">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1911">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-1912">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-1912">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1913">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1913">Allowed From</span></span>

<span data-ttu-id="d7262-1914">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1914">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1915">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1915">Preemption Possible</span></span>

<span data-ttu-id="d7262-1916">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1916">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1917">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1917">Example</span></span>

```C
/* Get the port number of previously created and bound client
    socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1918">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1918">See Also</span></span>

- <span data-ttu-id="d7262-1919">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="d7262-1919">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="d7262-1920">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span><span class="sxs-lookup"><span data-stu-id="d7262-1920">nx_tcp_client_socket_unbind, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="d7262-1921">nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="d7262-1921">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="d7262-1922">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-1922">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="d7262-1923">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-1923">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="d7262-1924">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-1924">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-1925">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-1925">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-1926">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-1926">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="d7262-1927">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-1927">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="d7262-1928">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-1928">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_client_socket_unbind"></a><span data-ttu-id="d7262-1929">nx_tcp_client_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="d7262-1929">nx_tcp_client_socket_unbind</span></span>

<span data-ttu-id="d7262-1930">Отмена привязки клиентского сокета TCP к TCP-порту</span><span class="sxs-lookup"><span data-stu-id="d7262-1930">Unbind TCP client socket from TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1931">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1931">Prototype</span></span>

```C
UINT nx_tcp_client_socket_unbind(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-1932">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1932">Description</span></span>

<span data-ttu-id="d7262-1933">Эта служба отменяет привязку между клиентским сокетом TCP и TCP-портом.</span><span class="sxs-lookup"><span data-stu-id="d7262-1933">This service releases the binding between the TCP client socket and a TCP port.</span></span> <span data-ttu-id="d7262-1934">Если есть другие потоки, ожидающие привязки другого сокета к тому же номеру порта, к порту привязывается первый приостановленный поток.</span><span class="sxs-lookup"><span data-stu-id="d7262-1934">If there are other threads waiting to bind another socket to the same port number, the first suspended thread is then bound to this port.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1935">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1935">Parameters</span></span>

- <span data-ttu-id="d7262-1936">**socket_ptr**: указатель на ранее созданный экземпляр сокета TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-1936">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1937">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1937">Return Values</span></span>

- <span data-ttu-id="d7262-1938">**NX_SUCCESS** (0x00) — привязка сокета успешно отменена.</span><span class="sxs-lookup"><span data-stu-id="d7262-1938">**NX_SUCCESS** (0x00) Successful socket unbind.</span></span>
- <span data-ttu-id="d7262-1939">**NX_NOT_BOUND** (0x24) — сокет не привязан ни к одному порту.</span><span class="sxs-lookup"><span data-stu-id="d7262-1939">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="d7262-1940">**NX_NOT_CLOSED** (0x35) — сокет не отключен.</span><span class="sxs-lookup"><span data-stu-id="d7262-1940">**NX_NOT_CLOSED** (0x35) Socket has not been disconnected.</span></span>
- <span data-ttu-id="d7262-1941">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-1941">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-1942">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1942">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-1943">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-1943">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1944">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1944">Allowed From</span></span>

<span data-ttu-id="d7262-1945">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-1945">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1946">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1946">Preemption Possible</span></span>

<span data-ttu-id="d7262-1947">Да</span><span class="sxs-lookup"><span data-stu-id="d7262-1947">Yes</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1948">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1948">Example</span></span>

```C
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
    bound. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1949">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1949">See Also</span></span>

- <span data-ttu-id="d7262-1950">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="d7262-1950">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="d7262-1951">nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find,</span><span class="sxs-lookup"><span data-stu-id="d7262-1951">nx_tcp_client_socket_port_get, nx_tcp_enable, nx_tcp_free_port_find,</span></span>
- <span data-ttu-id="d7262-1952">nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="d7262-1952">nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="d7262-1953">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-1953">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="d7262-1954">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-1954">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="d7262-1955">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-1955">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-1956">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-1956">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-1957">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-1957">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="d7262-1958">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-1958">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="d7262-1959">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-1959">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_enable"></a><span data-ttu-id="d7262-1960">nx_tcp_enable</span><span class="sxs-lookup"><span data-stu-id="d7262-1960">nx_tcp_enable</span></span>

<span data-ttu-id="d7262-1961">Включение компонента TCP в NetX</span><span class="sxs-lookup"><span data-stu-id="d7262-1961">Enable TCP component of NetX</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1962">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1962">Prototype</span></span>

```C
UINT nx_tcp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-1963">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1963">Description</span></span>

<span data-ttu-id="d7262-1964">Эта служба включает компонент протокола TCP в NetX.</span><span class="sxs-lookup"><span data-stu-id="d7262-1964">This service enables the Transmission Control Protocol (TCP) component of NetX.</span></span> <span data-ttu-id="d7262-1965">После включения приложение может устанавливать TCP-подключения.</span><span class="sxs-lookup"><span data-stu-id="d7262-1965">After enabled, TCP connections may be established by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1966">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1966">Parameters</span></span>

- <span data-ttu-id="d7262-1967">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1967">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-1968">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-1968">Return Values</span></span>

- <span data-ttu-id="d7262-1969">**NX_SUCCESS** (0x00) — успешное включение TCP.</span><span class="sxs-lookup"><span data-stu-id="d7262-1969">**NX_SUCCESS** (0x00) Successful TCP enable.</span></span>
- <span data-ttu-id="d7262-1970">**NX_ALREADY_ENABLED** (0x15) — протокол TCP уже включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-1970">**NX_ALREADY_ENABLED** (0x15) TCP is already enabled.</span></span>
- <span data-ttu-id="d7262-1971">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-1971">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-1972">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-1972">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-1973">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-1973">Allowed From</span></span>

<span data-ttu-id="d7262-1974">Инициализация, потоки, таймеры</span><span class="sxs-lookup"><span data-stu-id="d7262-1974">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-1975">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-1975">Preemption Possible</span></span>

<span data-ttu-id="d7262-1976">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-1976">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-1977">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-1977">Example</span></span>

```C
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-1978">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-1978">See Also</span></span>

- <span data-ttu-id="d7262-1979">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="d7262-1979">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="d7262-1980">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-1980">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="d7262-1981">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="d7262-1981">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="d7262-1982">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-1982">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="d7262-1983">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-1983">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="d7262-1984">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-1984">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-1985">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-1985">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-1986">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-1986">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="d7262-1987">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-1987">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="d7262-1988">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-1988">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_free_port_find"></a><span data-ttu-id="d7262-1989">nx_tcp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="d7262-1989">nx_tcp_free_port_find</span></span>

<span data-ttu-id="d7262-1990">Поиск следующего доступного TCP-порта</span><span class="sxs-lookup"><span data-stu-id="d7262-1990">Find next available TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-1991">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-1991">Prototype</span></span>

```C
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port, UINT *free_port_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-1992">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-1992">Description</span></span>

<span data-ttu-id="d7262-1993">Эта служба пытается найти свободный TCP-порт (без привязки) начиная с порта, указанного приложением.</span><span class="sxs-lookup"><span data-stu-id="d7262-1993">This service attempts to locate a free TCP port (unbound) starting from the application supplied port.</span></span> <span data-ttu-id="d7262-1994">Если достигнуто максимальное значение порта 0xFFFF, поиск начинается с самого начала.</span><span class="sxs-lookup"><span data-stu-id="d7262-1994">The search logic will wrap around if the search happens to reach the maximum port value of 0xFFFF.</span></span> <span data-ttu-id="d7262-1995">Если поиск завершен успешно, свободный порт возвращается в переменной, на которую указывает *free_port_ptr*.</span><span class="sxs-lookup"><span data-stu-id="d7262-1995">If the search is successful, the free port is returned in the variable pointed to by *free_port_ptr*.</span></span>

<span data-ttu-id="d7262-1996">*Если эта служба вызывается из другого потока, она может вернуть тот же порт. Чтобы предотвратить такое состояние гонки, приложение может защитить эту службу и привязку клиентского сокета мьютексом.*</span><span class="sxs-lookup"><span data-stu-id="d7262-1996">*This service can be called from another thread and have the same port returned. To prevent this race condition, the application may wish to place this service and the actual client socket bind under the protection of a mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-1997">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-1997">Parameters</span></span>

- <span data-ttu-id="d7262-1998">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-1998">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-1999">**port**: номер порта, с которого начинается поиск (от 1 до 0xFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-1999">**port** Port number to start search at (1 through 0xFFFF).</span></span>
- <span data-ttu-id="d7262-2000">**free_port_ptr**: указатель на место назначения для возвращаемого значения свободного порта</span><span class="sxs-lookup"><span data-stu-id="d7262-2000">**free_port_ptr** Pointer to the destination free port return value.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2001">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2001">Return Values</span></span>

- <span data-ttu-id="d7262-2002">**NX_SUCCESS** (0x00) — поиск свободного порта успешно завершен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2002">**NX_SUCCESS** (0x00) Successful free port find.</span></span>
- <span data-ttu-id="d7262-2003">**NX_NO_FREE_PORTS** (0x45) — нет свободного порта.</span><span class="sxs-lookup"><span data-stu-id="d7262-2003">**NX_NO_FREE_PORTS** (0x45) No free ports found.</span></span>
- <span data-ttu-id="d7262-2004">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-2004">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-2005">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2005">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2006">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2006">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="d7262-2007">**NX_INVALID_PORT** (0x46) — указан недопустимый номер порта.</span><span class="sxs-lookup"><span data-stu-id="d7262-2007">**NX_INVALID_PORT** (0x46) The specified port number is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2008">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2008">Allowed From</span></span>

<span data-ttu-id="d7262-2009">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2009">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2010">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2010">Preemption Possible</span></span>

<span data-ttu-id="d7262-2011">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2011">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2012">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2012">Example</span></span>

```C
/* Locate a free TCP port, starting at port 12, on a previously
    created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
    on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2013">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2013">See Also</span></span>

- <span data-ttu-id="d7262-2014">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2014">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="d7262-2015">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-2015">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="d7262-2016">nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="d7262-2016">nx_tcp_enable, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="d7262-2017">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-2017">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="d7262-2018">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-2018">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="d7262-2019">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-2019">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-2020">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2020">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-2021">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-2021">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="d7262-2022">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-2022">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="d7262-2023">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-2023">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_info_get"></a><span data-ttu-id="d7262-2024">nx_tcp_info_get</span><span class="sxs-lookup"><span data-stu-id="d7262-2024">nx_tcp_info_get</span></span>

<span data-ttu-id="d7262-2025">Получение сведений о действиях TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2025">Retrieve information about TCP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2026">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2026">Prototype</span></span>

```C
UINT nx_tcp_info_get(
    NX_IP *ip_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_invalid_packets,
    ULONG *tcp_receive_packets_dropped,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_connections,
    ULONG *tcp_disconnections,
    ULONG *tcp_connections_dropped,
    ULONG *tcp_retransmit_packets);
```

### <a name="description"></a><span data-ttu-id="d7262-2027">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2027">Description</span></span>

<span data-ttu-id="d7262-2028">Эта служба получает сведения о действиях протокола TCP для указанного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-2028">This service retrieves information about TCP activities for the specified IP instance.</span></span>

<span data-ttu-id="d7262-2029">*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.</span><span class="sxs-lookup"><span data-stu-id="d7262-2029">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2030">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2030">Parameters</span></span>

- <span data-ttu-id="d7262-2031">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-2031">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-2032">**tcp_packets_sent**: указатель на место назначения для общего числа отправленных TCP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-2032">**tcp_packets_sent** Pointer to destination for the total number of TCP packets sent.</span></span>
- <span data-ttu-id="d7262-2033">**tcp_bytes_sent**: указатель на место назначения для общего числа отправленных по TCP байтов</span><span class="sxs-lookup"><span data-stu-id="d7262-2033">**tcp_bytes_sent** Pointer to destination for the total number of TCP bytes sent.</span></span>
- <span data-ttu-id="d7262-2034">**tcp_packets_received**: указатель на место назначения для общего числа полученных TCP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-2034">**tcp_packets_received** Pointer to destination of the total number of TCP packets received.</span></span>
- <span data-ttu-id="d7262-2035">**tcp_bytes_received**: указатель на место назначения для общего числа полученных по TCP байтов</span><span class="sxs-lookup"><span data-stu-id="d7262-2035">**tcp_bytes_received** Pointer to destination of the total number of TCP bytes received.</span></span>
- <span data-ttu-id="d7262-2036">**tcp_invalid_packets**: указатель на место назначения для общего числа недопустимых TCP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-2036">**tcp_invalid_packets** Pointer to destination of the total number of invalid TCP packets.</span></span>
- <span data-ttu-id="d7262-2037">**tcp_receive_packets_dropped**: указатель на место назначения для общего числа полученных и отброшенных TCP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-2037">**tcp_receive_packets_dropped** Pointer to destination of the total number of TCP receive packets dropped.</span></span>
- <span data-ttu-id="d7262-2038">**tcp_checksum_errors**: указатель на место назначения для общего числа TCP-пакетов с ошибками контрольной суммы</span><span class="sxs-lookup"><span data-stu-id="d7262-2038">**tcp_checksum_errors** Pointer to destination of the total number of TCP packets with checksum errors.</span></span>
- <span data-ttu-id="d7262-2039">**tcp_connections**: указатель на место назначения для общего числа TCP-подключений</span><span class="sxs-lookup"><span data-stu-id="d7262-2039">**tcp_connections** Pointer to destination of the total number of TCP connections.</span></span>
- <span data-ttu-id="d7262-2040">**tcp_disconnections**: указатель на место назначения для общего числа прерванных TCP-подключений</span><span class="sxs-lookup"><span data-stu-id="d7262-2040">**tcp_disconnections** Pointer to destination of the total number of TCP disconnections.</span></span>
- <span data-ttu-id="d7262-2041">**tcp_connections_dropped**: указатель на место назначения для общего числа отброшенных TCP-подключений</span><span class="sxs-lookup"><span data-stu-id="d7262-2041">**tcp_connections_dropped** Pointer to destination of the total number of TCP connections dropped.</span></span>
- <span data-ttu-id="d7262-2042">**tcp_retransmit_packets**: указатель на место назначения для общего числа ретранслированных TCP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-2042">**tcp_retransmit_packets** Pointer to destination of the total number of TCP packets retransmitted.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2043">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2043">Return Values</span></span>

- <span data-ttu-id="d7262-2044">**NX_SUCCESS** (0x00) — успешное получение сведений TCP.</span><span class="sxs-lookup"><span data-stu-id="d7262-2044">**NX_SUCCESS** (0x00) Successful TCP information retrieval.</span></span>
- <span data-ttu-id="d7262-2045">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-2045">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-2046">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2046">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2047">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2047">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2048">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2048">Allowed From</span></span>

<span data-ttu-id="d7262-2049">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2049">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2050">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2050">Preemption Possible</span></span>

<span data-ttu-id="d7262-2051">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2051">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2052">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2052">Example</span></span>

```C
/* Retrieve TCP information from previously created IP Instance ip_0. */
status = nx_tcp_info_get(&ip_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_invalid_packets,
    &tcp_receive_packets_dropped,
    &tcp_checksum_errors,
    &tcp_connections,
    &tcp_disconnections
    &tcp_connections_dropped,
    &tcp_retransmit_packets);

/* If status is NX_SUCCESS, TCP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2053">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2053">See Also</span></span>

- <span data-ttu-id="d7262-2054">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2054">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="d7262-2055">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-2055">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="d7262-2056">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="d7262-2056">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="d7262-2057">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-2057">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="d7262-2058">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-2058">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="d7262-2059">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-2059">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-2060">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2060">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-2061">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-2061">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="d7262-2062">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-2062">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="d7262-2063">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-2063">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_accept"></a><span data-ttu-id="d7262-2064">nx_tcp_server_socket_accept</span><span class="sxs-lookup"><span data-stu-id="d7262-2064">nx_tcp_server_socket_accept</span></span>

<span data-ttu-id="d7262-2065">Принятие TCP-подключения</span><span class="sxs-lookup"><span data-stu-id="d7262-2065">Accept TCP connection</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2066">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2066">Prototype</span></span>

```C
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d7262-2067">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2067">Description</span></span>

<span data-ttu-id="d7262-2068">Эта служба принимает (или готовится принять) запрос на подключение к клиентскому сокету TCP для порта, который ранее был настроен для ожидания передачи данных.</span><span class="sxs-lookup"><span data-stu-id="d7262-2068">This service accepts (or prepares to accept) a TCP client socket connection request for a port that was previously set up for listening.</span></span> <span data-ttu-id="d7262-2069">Эту службу можно вызывать сразу после того, как приложение вызовет службу ожидания или повторного ожидания передачи данных, или после вызова подпрограммы обратного вызова для ожидания передачи данных при наличии клиентского подключения.</span><span class="sxs-lookup"><span data-stu-id="d7262-2069">This service may be called immediately after the application calls the listen or re-listen service, or after the listen callback routine is called when the client connection is actually present.</span></span> <span data-ttu-id="d7262-2070">Если подключение невозможно установить немедленно, служба приостанавливает выполнение в соответствии с указанным параметром ожидания.</span><span class="sxs-lookup"><span data-stu-id="d7262-2070">If a connection cannot not be established right away, the service suspends according to the supplied wait option.</span></span>

<span data-ttu-id="d7262-2071">*Когда подключение больше не требуется, приложение должно вызвать **nx_tcp_server_socket_unaccept**, чтобы удалить привязку сокета сервера к порту сервера.*</span><span class="sxs-lookup"><span data-stu-id="d7262-2071">*The application must call **nx_tcp_server_socket_unaccept** after the connection is no longer needed to remove the server socket's binding to the server port.*</span></span>

<span data-ttu-id="d7262-2072">*Подпрограммы обратного вызова приложения вызываются из вспомогательного потока IP.*</span><span class="sxs-lookup"><span data-stu-id="d7262-2072">*Application callback routines are called from within the IP's helper thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2073">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2073">Parameters</span></span>

- <span data-ttu-id="d7262-2074">**socket_ptr**: указатель на управляющий блок сокета TCP-сервера</span><span class="sxs-lookup"><span data-stu-id="d7262-2074">**socket_ptr** Pointer to the TCP server socket control block.</span></span>
- <span data-ttu-id="d7262-2075">**wait_option** определяет поведение службы во время установления соединения</span><span class="sxs-lookup"><span data-stu-id="d7262-2075">**wait_option** Defines how the service behaves while the connection is being established.</span></span> <span data-ttu-id="d7262-2076">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d7262-2076">The wait options are defined as follows:</span></span>
- <span data-ttu-id="d7262-2077">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-2077">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="d7262-2078">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-2078">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="d7262-2079">Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d7262-2079">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>


### <a name="return-values"></a><span data-ttu-id="d7262-2080">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2080">Return Values</span></span>
- <span data-ttu-id="d7262-2081">**NX_SUCCESS** (0x00) — успешное принятие сокета TCP-сервера (пассивное подключение).</span><span class="sxs-lookup"><span data-stu-id="d7262-2081">**NX_SUCCESS** (0x00) Successful TCP server socket accept (passive connect).</span></span>
- <span data-ttu-id="d7262-2082">**NX_NOT_LISTEN_STATE** (0x36) — указанный сокет сервера не находится в состоянии ожидания передачи данных.</span><span class="sxs-lookup"><span data-stu-id="d7262-2082">**NX_NOT_LISTEN_STATE** (0x36) The server socket supplied is not in a listen state.</span></span>
- <span data-ttu-id="d7262-2083">**NX_IN_PROGRESS** (0x37) — параметр ожидания не указан; выполняется попытка подключения.</span><span class="sxs-lookup"><span data-stu-id="d7262-2083">**NX_IN_PROGRESS** (0x37) No wait was specified, the connection attempt is in progress.</span></span>
- <span data-ttu-id="d7262-2084">**NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом *tx_thread_wait_abort*.</span><span class="sxs-lookup"><span data-stu-id="d7262-2084">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to *tx_thread_wait_abort*.</span></span>
- <span data-ttu-id="d7262-2085">**NX_PTR_ERROR** (0x07) — ошибка указателя сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2085">**NX_PTR_ERROR** (0x07) Socket pointer error.</span></span>
- <span data-ttu-id="d7262-2086">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2086">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2087">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2087">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2088">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2088">Allowed From</span></span>

<span data-ttu-id="d7262-2089">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2089">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2090">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2090">Preemption Possible</span></span>

<span data-ttu-id="d7262-2091">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2091">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2092">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2092">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;
void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;
    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created and the
        link is enabled "my_pool" packet pool has already been
        created */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client and then disconnecting.*/
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
                message */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called
            even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
            again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }

    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="d7262-2093">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2093">See Also</span></span>

- <span data-ttu-id="d7262-2094">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2094">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="d7262-2095">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-2095">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="d7262-2096">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2096">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="d7262-2097">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-2097">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="d7262-2098">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-2098">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="d7262-2099">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-2099">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-2100">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2100">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-2101">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-2101">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="d7262-2102">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-2102">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="d7262-2103">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-2103">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_listen"></a><span data-ttu-id="d7262-2104">nx_tcp_server_socket_listen</span><span class="sxs-lookup"><span data-stu-id="d7262-2104">nx_tcp_server_socket_listen</span></span>

<span data-ttu-id="d7262-2105">Включение ожидания передачи данных для клиентского подключения через TCP-порт</span><span class="sxs-lookup"><span data-stu-id="d7262-2105">Enable listening for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2106">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2106">Prototype</span></span>

```C
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```

### <a name="description"></a><span data-ttu-id="d7262-2107">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2107">Description</span></span>

<span data-ttu-id="d7262-2108">Эта служба включает ожидание запроса клиентского подключения через указанный TCP-порт.</span><span class="sxs-lookup"><span data-stu-id="d7262-2108">This service enables listening for a client connection request on the specified TCP port.</span></span> <span data-ttu-id="d7262-2109">При получении запроса на подключение клиента указанный сокет сервера привязывается к заданному порту и вызывается указанная функция обратного вызова для ожидания передачи данных.</span><span class="sxs-lookup"><span data-stu-id="d7262-2109">When a client connection request is received, the supplied server socket is bound to the specified port and the supplied listen callback function is called.</span></span>

<span data-ttu-id="d7262-2110">За выполнение подпрограммы обратного вызова для ожидания передачи данных полностью отвечает приложение.</span><span class="sxs-lookup"><span data-stu-id="d7262-2110">The listen callback routine's processing is completely up to the application.</span></span> <span data-ttu-id="d7262-2111">Она может включать в себя логику для пробуждения потока приложения, который затем выполняет операцию принятия.</span><span class="sxs-lookup"><span data-stu-id="d7262-2111">It may contain logic to wake up an application thread that subsequently performs an accept operation.</span></span> <span data-ttu-id="d7262-2112">Если в приложении уже есть поток, приостановленный при обработке принятия для этого сокета, подпрограмма обратного вызова для ожидания передачи данных может не потребоваться.</span><span class="sxs-lookup"><span data-stu-id="d7262-2112">If the application already has a thread suspended on accept processing for this socket, the listen callback routine may not be needed.</span></span>

<span data-ttu-id="d7262-2113">Если приложение планирует обрабатывать дополнительные клиентские подключения через тот же порт, служба ***nx_tcp_server_socket_relisten*** должна быть вызвана с доступным сокетом (в закрытом состоянии) для следующего подключения.</span><span class="sxs-lookup"><span data-stu-id="d7262-2113">If the application wishes to handle additional client connections on the same port, the ***nx_tcp_server_socket_relisten*** must be called with an available socket (a socket in the CLOSED state) for the next connection.</span></span> <span data-ttu-id="d7262-2114">Пока не будет вызвана служба повторного ожидания передачи данных, дополнительные клиентские подключения помещаются в очередь.</span><span class="sxs-lookup"><span data-stu-id="d7262-2114">Until the re-listen service is called, additional client connections are queued.</span></span> <span data-ttu-id="d7262-2115">При превышении максимальной глубины очереди самый старый запрос на подключение отбрасывается в пользу нового.</span><span class="sxs-lookup"><span data-stu-id="d7262-2115">When the maximum queue depth is exceeded, the oldest connection request is dropped in favor of queuing the new connection request.</span></span> <span data-ttu-id="d7262-2116">Максимальная глубина очереди задается данной службой.</span><span class="sxs-lookup"><span data-stu-id="d7262-2116">The maximum queue depth is specified by this service.</span></span>

<span data-ttu-id="d7262-2117">*Подпрограммы обратного вызова приложения вызываются из внутреннего вспомогательного потока IP.*</span><span class="sxs-lookup"><span data-stu-id="d7262-2117">*Application callback routines are called from the internal IP helper thread.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2118">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2118">Parameters</span></span>

- <span data-ttu-id="d7262-2119">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-2119">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-2120">**port**: номер порта для ожидания передачи данных (от 1 до 0xFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-2120">**port** Port number to listen on (1 through 0xFFFF).</span></span>
- <span data-ttu-id="d7262-2121">**socket_ptr**: указатель на сокет, который следует использовать для подключения</span><span class="sxs-lookup"><span data-stu-id="d7262-2121">**socket_ptr** Pointer to socket to use for the connection.</span></span>
- <span data-ttu-id="d7262-2122">**listen_queue_size**: число запросов на клиентское подключение, которые можно поставить в очередь</span><span class="sxs-lookup"><span data-stu-id="d7262-2122">**listen_queue_size** Number of client connection requests that can be queued.</span></span>
- <span data-ttu-id="d7262-2123">**listen_callback**: функция приложения, вызываемая при получении подключения</span><span class="sxs-lookup"><span data-stu-id="d7262-2123">**listen_callback** Application function to call when the connection is received.</span></span> <span data-ttu-id="d7262-2124">Если указано значение NULL, функция обратного вызова для ожидания передачи данных отключена.</span><span class="sxs-lookup"><span data-stu-id="d7262-2124">If a NULL is specified, the listen callback feature is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2125">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2125">Return Values</span></span>

- <span data-ttu-id="d7262-2126">**NX_SUCCESS** (0x00) — ожидание передачи данных через TCP-порт успешно включено.</span><span class="sxs-lookup"><span data-stu-id="d7262-2126">**NX_SUCCESS** (0x00) Successful TCP port listen enable.</span></span>
- <span data-ttu-id="d7262-2127">**NX_MAX_LISTEN** (0x33) — больше нет доступных структур запросов на ожидание передачи данных.</span><span class="sxs-lookup"><span data-stu-id="d7262-2127">**NX_MAX_LISTEN** (0x33) No more listen request structures are available.</span></span> <span data-ttu-id="d7262-2128">Константа NX_MAX_LISTEN_REQUESTS в nx_api.h определяет, сколько активных запросов на ожидание передачи данных возможно.</span><span class="sxs-lookup"><span data-stu-id="d7262-2128">The constant NX_MAX_LISTEN_REQUESTS in nx_api.h defines how many active listen requests are possible.</span></span>
- <span data-ttu-id="d7262-2129">**NX_NOT_CLOSED** (0x35) — указанный сокет сервера не находится в закрытом состоянии.</span><span class="sxs-lookup"><span data-stu-id="d7262-2129">**NX_NOT_CLOSED** (0x35) The supplied server socket is not in a closed state.</span></span>
- <span data-ttu-id="d7262-2130">**NX_ALREADY_BOUND** (0x22) — указанный сокет сервера уже привязан к порту.</span><span class="sxs-lookup"><span data-stu-id="d7262-2130">**NX_ALREADY_BOUND** (0x22) The supplied server socket is already bound to a port.</span></span>
- <span data-ttu-id="d7262-2131">**NX_DUPLICATE_LISTEN** (0x34) — для этого порта уже имеется активный запрос на ожидание передачи данных.</span><span class="sxs-lookup"><span data-stu-id="d7262-2131">**NX_DUPLICATE_LISTEN** (0x34) There is already an active listen request for this port.</span></span>
- <span data-ttu-id="d7262-2132">**NX_INVALID_PORT** (0x46) — указан недопустимый порт.</span><span class="sxs-lookup"><span data-stu-id="d7262-2132">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="d7262-2133">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса или сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2133">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="d7262-2134">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2134">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2135">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2135">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2136">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2136">Allowed From</span></span>

<span data-ttu-id="d7262-2137">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2137">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2138">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2138">Preemption Possible</span></span>

<span data-ttu-id="d7262-2139">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2139">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2140">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2140">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket.
        This example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created
        and the link is enabled "my_pool" packet pool has already
        been created.
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
        Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
            request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

    /* Wait for 200 ticks for the client socket connection
        to complete. */
    status = nx_tcp_server_socket_accept(&server_socket, 200);

    /* Check for a successful connection. */
    if (status == NX_SUCCESS)
    {
        /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
        nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
            NX_WAIT_FOREVER);

        /* Place "Hello_and_Goodbye" in the packet. */
        nx_packet_data_append(my_packet, "Hello_and_Goodbye",
            sizeof("Hello_and_Goodbye"),
            &my_pool,
            NX_WAIT_FOREVER);

        /* Send "Hello_and_Goodbye" to client. */
        nx_tcp_socket_send(&server_socket, my_packet, 200);

        /* Check for an error. */
        if (status)
        {
            /* Error, release the packet. */
            nx_packet_release(my_packet);
        }
        /* Now disconnect the server socket from the client. */
        nx_tcp_socket_disconnect(&server_socket, 200);
    }

    /* Unaccept the server socket. Note that unaccept is called
        even if disconnect or accept fails. */
    nx_tcp_server_socket_unaccept(&server_socket);

    /* Setup server socket for listening with this socket
    again. */
    nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
}

/* We are now done so unlisten on server port 12. */
nx_tcp_server_socket_unlisten(&my_ip, 12);

/* Delete the server socket. */
nx_tcp_socket_delete(&server_socket);
```

### <a name="see-also"></a><span data-ttu-id="d7262-2141">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2141">See Also</span></span>

- <span data-ttu-id="d7262-2142">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2142">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="d7262-2143">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-2143">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="d7262-2144">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2144">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="d7262-2145">nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-2145">nx_tcp_server_socket_accept, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="d7262-2146">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-2146">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="d7262-2147">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-2147">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-2148">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2148">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-2149">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-2149">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="d7262-2150">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-2150">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="d7262-2151">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-2151">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_relisten"></a><span data-ttu-id="d7262-2152">nx_tcp_server_socket_relisten</span><span class="sxs-lookup"><span data-stu-id="d7262-2152">nx_tcp_server_socket_relisten</span></span>

<span data-ttu-id="d7262-2153">Повторное ожидание передачи данных для клиентского подключения через TCP-порт</span><span class="sxs-lookup"><span data-stu-id="d7262-2153">Re-listen for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2154">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2154">Prototype</span></span>

```C
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-2155">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2155">Description</span></span>

<span data-ttu-id="d7262-2156">Эта служба вызывается после получения подключения через порт, который ранее был настроен для ожидания передачи данных.</span><span class="sxs-lookup"><span data-stu-id="d7262-2156">This service is called after a connection has been received on a port that was setup previously for listening.</span></span> <span data-ttu-id="d7262-2157">Основная задача этой службы — предоставление нового сокета сервера для следующего клиентского подключения.</span><span class="sxs-lookup"><span data-stu-id="d7262-2157">The main purpose of this service is to provide a new server socket for the next client connection.</span></span> <span data-ttu-id="d7262-2158">Если запрос на подключение ставится в очередь, подключение обрабатывается немедленно во время вызова этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2158">If a connection request is queued, the connection will be processed immediately during this service call.</span></span>

<span data-ttu-id="d7262-2159">*Подпрограмма обратного вызова, указанная в исходном запросе на ожидание передачи данных, вызывается и при наличии подключения для этого нового сокета сервера.*</span><span class="sxs-lookup"><span data-stu-id="d7262-2159">*The same callback routine specified by the original listen request is also called when a connection is present for this new server socket.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2160">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2160">Parameters</span></span>

- <span data-ttu-id="d7262-2161">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-2161">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-2162">**port**: номер порта для повторного ожидания передачи данных (от 1 до 0xFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-2162">**port** Port number to re-listen on (1 through 0xFFFF).</span></span>
- <span data-ttu-id="d7262-2163">**socket_ptr**: сокет, используемый для следующего клиентского подключения</span><span class="sxs-lookup"><span data-stu-id="d7262-2163">**socket_ptr** Socket to use for the next client connection.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2164">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2164">Return Values</span></span>
- <span data-ttu-id="d7262-2165">**NX_SUCCESS** (0x00) — успешное повторное ожидание передачи данных через TCP-порт.</span><span class="sxs-lookup"><span data-stu-id="d7262-2165">**NX_SUCCESS** (0x00) Successful TCP port re-listen.</span></span>
- <span data-ttu-id="d7262-2166">**NX_NOT_CLOSED** (0x35) — указанный сокет сервера не находится в закрытом состоянии.</span><span class="sxs-lookup"><span data-stu-id="d7262-2166">**NX_NOT_CLOSED** (0x35) The supplied server socket is not in a closed state.</span></span>
- <span data-ttu-id="d7262-2167">**NX_ALREADY_BOUND** (0x22) — указанный сокет сервера уже привязан к порту.</span><span class="sxs-lookup"><span data-stu-id="d7262-2167">**NX_ALREADY_BOUND** (0x22) The supplied server socket is already bound to a port.</span></span>
- <span data-ttu-id="d7262-2168">**NX_INVALID_RELISTEN** (0x47) — уже имеется допустимый указатель сокета для этого порта, или у указанного порта нет активного запроса на ожидание передачи данных.</span><span class="sxs-lookup"><span data-stu-id="d7262-2168">**NX_INVALID_RELISTEN** (0x47) There is already a valid socket pointer for this port or the port specified does not have a listen request active.</span></span>
- <span data-ttu-id="d7262-2169">**NX_CONNECTION_PENDING** (0x48) — то же, что NX_SUCCESS, за исключением наличия запроса на подключение в очереди, который был обработан во время этого вызова.</span><span class="sxs-lookup"><span data-stu-id="d7262-2169">**NX_CONNECTION_PENDING** (0x48) Same as NX_SUCCESS, except there was a queued connection request and it was processed during this call.</span></span>
- <span data-ttu-id="d7262-2170">**NX_INVALID_PORT** (0x46) — указан недопустимый порт.</span><span class="sxs-lookup"><span data-stu-id="d7262-2170">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="d7262-2171">**NX_PTR_ERROR** (0x07) — недопустимый IP-адрес или указатель обратного вызова для ожидания передачи данных.</span><span class="sxs-lookup"><span data-stu-id="d7262-2171">**NX_PTR_ERROR** (0x07) Invalid IP or listen callback pointer.</span></span>
- <span data-ttu-id="d7262-2172">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2172">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2173">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2173">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2174">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2174">Allowed From</span></span>

<span data-ttu-id="d7262-2175">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2175">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2176">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2176">Preemption Possible</span></span>

<span data-ttu-id="d7262-2177">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2177">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2178">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2178">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread.*/
    tx_semaphore_put(&port_12_semaphore);
    }

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
    example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
    "port_12_semaphore" has already been created with an initial
        count of 0.
        "my_ip" has already been created and the link is enabled.
        "my_pool" packet pool has already been created. */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);
    /* Loop to process 5 server connections, sending
        "Hello_and_Goodbye" to each client then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection
        request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
        complete. */
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye"
            message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is
        called even if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket
        again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="d7262-2179">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2179">See Also</span></span>

- <span data-ttu-id="d7262-2180">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2180">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="d7262-2181">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-2181">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="d7262-2182">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2182">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="d7262-2183">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="d7262-2183">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="d7262-2184">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-2184">nx_tcp_server_socket_unaccept, nx_tcp_server_socket_unlisten,</span></span>
- <span data-ttu-id="d7262-2185">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-2185">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-2186">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2186">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-2187">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-2187">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="d7262-2188">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-2188">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="d7262-2189">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-2189">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_unaccept"></a><span data-ttu-id="d7262-2190">nx_tcp_server_socket_unaccept</span><span class="sxs-lookup"><span data-stu-id="d7262-2190">nx_tcp_server_socket_unaccept</span></span>

<span data-ttu-id="d7262-2191">Удаление связи сокета с прослушиваемым портом</span><span class="sxs-lookup"><span data-stu-id="d7262-2191">Remove socket association with listening port</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2192">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2192">Prototype</span></span>

```C
UINT nx_tcp_server_socket_unaccept(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-2193">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2193">Description</span></span>

<span data-ttu-id="d7262-2194">Эта служба удаляет связь между сокетом сервера и указанным портом сервера.</span><span class="sxs-lookup"><span data-stu-id="d7262-2194">This service removes the association between this server socket and the specified server port.</span></span> <span data-ttu-id="d7262-2195">Приложение должно вызывать эту службу после завершения подключения или после неудачного вызова приема.</span><span class="sxs-lookup"><span data-stu-id="d7262-2195">The application must call this service after a disconnection or after an unsuccessful accept call.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2196">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2196">Parameters</span></span>

- <span data-ttu-id="d7262-2197">**socket_ptr**: указатель на ранее настроенный экземпляр сокета сервера</span><span class="sxs-lookup"><span data-stu-id="d7262-2197">**socket_ptr** Pointer to previously setup server socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2198">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2198">Return Values</span></span>

- <span data-ttu-id="d7262-2199">**NX_SUCCESS** (0x00) — принятие сокета сервера успешно отменено.</span><span class="sxs-lookup"><span data-stu-id="d7262-2199">**NX_SUCCESS** (0x00) Successful server socket unaccept.</span></span>
- <span data-ttu-id="d7262-2200">**NX_NOT_LISTEN_STATE** (0x36) — сокет сервера находится в неправильном состоянии и, возможно, не отключен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2200">**NX_NOT_LISTEN_STATE** (0x36) Server socket is in an improper state, and is probably not disconnected.</span></span>
- <span data-ttu-id="d7262-2201">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2201">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-2202">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2202">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2203">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2203">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2204">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2204">Allowed From</span></span>

<span data-ttu-id="d7262-2205">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2205">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2206">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2206">Preemption Possible</span></span>

<span data-ttu-id="d7262-2207">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2207">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2208">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2208">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
        */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
        "Port 12 Server Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,NX_NULL,
        port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
        to each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request
            is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
            complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet,
                "Hello_and_Goodbye",sizeof("Hello_and_Goodbye"),
                &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }

        /* Unaccept the server socket. Note that unaccept is called even
            if disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="d7262-2209">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2209">See Also</span></span>

- <span data-ttu-id="d7262-2210">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2210">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="d7262-2211">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable,</span><span class="sxs-lookup"><span data-stu-id="d7262-2211">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind, nx_tcp_enable,</span></span>
- <span data-ttu-id="d7262-2212">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span><span class="sxs-lookup"><span data-stu-id="d7262-2212">nx_tcp_free_port_find, nx_tcp_info_get, nx_tcp_server_socket_accept,</span></span>
- <span data-ttu-id="d7262-2213">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span><span class="sxs-lookup"><span data-stu-id="d7262-2213">nx_tcp_server_socket_listen, nx_tcp_server_socket_relisten,</span></span>
- <span data-ttu-id="d7262-2214">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="d7262-2214">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="d7262-2215">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2215">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-2216">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-2216">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="d7262-2217">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-2217">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="d7262-2218">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-2218">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_server_socket_unlisten"></a><span data-ttu-id="d7262-2219">nx_tcp_server_socket_unlisten</span><span class="sxs-lookup"><span data-stu-id="d7262-2219">nx_tcp_server_socket_unlisten</span></span>

<span data-ttu-id="d7262-2220">Отключение ожидания передачи данных для клиентского подключения через TCP-порт</span><span class="sxs-lookup"><span data-stu-id="d7262-2220">Disable listening for client connection on TCP port</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2221">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2221">Prototype</span></span>

```C
UINT nx_tcp_server_socket_unlisten(NX_IP *ip_ptr, UINT port);
```

### <a name="description"></a><span data-ttu-id="d7262-2222">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2222">Description</span></span>

<span data-ttu-id="d7262-2223">Эта служба отключает ожидание запроса клиентского подключения через указанный TCP-порт.</span><span class="sxs-lookup"><span data-stu-id="d7262-2223">This service disables listening for a client connection request on the specified TCP port.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2224">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2224">Parameters</span></span>

- <span data-ttu-id="d7262-2225">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-2225">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-2226">**port**: номер порта для отключения ожидания передачи данных (от 0 до 0xFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-2226">**port** Number of port to disable listening (0 through 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2227">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2227">Return Values</span></span>

- <span data-ttu-id="d7262-2228">**NX_SUCCESS** (0x00) — ожидание передачи данных через TCP-порт успешно отключено.</span><span class="sxs-lookup"><span data-stu-id="d7262-2228">**NX_SUCCESS** (0x00) Successful TCP listen disable.</span></span>
- <span data-ttu-id="d7262-2229">**NX_ENTRY_NOT_FOUND** (0x16) — ожидание передачи данных не было включено для указанного порта.</span><span class="sxs-lookup"><span data-stu-id="d7262-2229">**NX_ENTRY_NOT_FOUND** (0x16) Listening was not enabled for the specified port.</span></span>
- <span data-ttu-id="d7262-2230">**NX_INVALID_PORT** (0x46) — указан недопустимый порт.</span><span class="sxs-lookup"><span data-stu-id="d7262-2230">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="d7262-2231">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-2231">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-2232">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2232">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2233">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2233">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2234">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2234">Allowed From</span></span>

<span data-ttu-id="d7262-2235">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2235">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2236">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2236">Preemption Possible</span></span>

<span data-ttu-id="d7262-2237">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2237">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2238">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2238">Example</span></span>

```C
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This example
    doesn't use this callback.*/
}

void port_12_server_thread_entry(ULONG id)
{
    NX_PACKET *my_packet;
    UINT status, i;

    /* Assuming that:
        "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
        "my_pool" packet pool has already been created
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
        NX_IP_TIME_TO_LIVE, 100,
        NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
        port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye" to
        each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {
        /* Get the semaphore that indicates a client connection request is
            present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {
            /* Allocate a packet for the "Hello_and_Goodbye" message. */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                sizeof("Hello_and_Goodbye"), &my_pool,
                NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
            }
            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
        }
        /* Unaccept the server socket. Note that unaccept is called even if
        disconnect or accept fails. */
        nx_tcp_server_socket_unaccept(&server_socket);

        /* Setup server socket for listening with this socket again. */
        nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }
    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a><span data-ttu-id="d7262-2239">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2239">See Also</span></span>

- <span data-ttu-id="d7262-2240">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2240">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="d7262-2241">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-2241">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="d7262-2242">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2242">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="d7262-2243">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="d7262-2243">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="d7262-2244">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="d7262-2244">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="d7262-2245">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-2245">nx_tcp_socket_bytes_available, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-2246">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2246">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-2247">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-2247">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="d7262-2248">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-2248">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="d7262-2249">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-2249">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_bytes_available"></a><span data-ttu-id="d7262-2250">nx_tcp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="d7262-2250">nx_tcp_socket_bytes_available</span></span>

<span data-ttu-id="d7262-2251">Получает число байтов, доступных для извлечения</span><span class="sxs-lookup"><span data-stu-id="d7262-2251">Retrieves number of bytes available for retrieval</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2252">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2252">Prototype</span></span>

```C
UINT nx_tcp_socket_bytes_available(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a><span data-ttu-id="d7262-2253">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2253">Description</span></span>

<span data-ttu-id="d7262-2254">Эта служба получает число байтов, доступных для извлечения в указанном сокете TCP.</span><span class="sxs-lookup"><span data-stu-id="d7262-2254">This service obtains the number of bytes available for retrieval in the specified TCP socket.</span></span> <span data-ttu-id="d7262-2255">Обратите внимание, что сокет TCP уже должен быть подключен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2255">Note that the TCP socket must already be connected.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2256">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2256">Parameters</span></span>

- <span data-ttu-id="d7262-2257">**socket_ptr**: указатель на ранее созданный и подключенный сокет TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2257">**socket_ptr** Pointer to previously created and connected TCP socket.</span></span>
- <span data-ttu-id="d7262-2258">**bytes_available**: указатель на место назначения для доступных байтов</span><span class="sxs-lookup"><span data-stu-id="d7262-2258">**bytes_available** Pointer to destination for bytes available.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2259">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2259">Return Values</span></span>

- <span data-ttu-id="d7262-2260">**NX_SUCCESS** (0x00) — служба успешно выполняется.</span><span class="sxs-lookup"><span data-stu-id="d7262-2260">**NX_SUCCESS** (0x00) Service executes successfully.</span></span> <span data-ttu-id="d7262-2261">Число байтов, доступных для чтения, возвращается вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="d7262-2261">Number of bytes available for read is returned to the caller.</span></span>
- <span data-ttu-id="d7262-2262">**NX_NOT_CONNECTED** (0x38) — сокет не находится в подключенном состоянии.</span><span class="sxs-lookup"><span data-stu-id="d7262-2262">**NX_NOT_CONNECTED** (0x38) Socket is not in a connected state.</span></span>
- <span data-ttu-id="d7262-2263">**NX_PTR_ERROR** (0x07) — недопустимые указатели.</span><span class="sxs-lookup"><span data-stu-id="d7262-2263">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="d7262-2264">**NX_NOT_ENABLED** (0x14) — протокол TCP не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2264">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="d7262-2265">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2265">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2266">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2266">Allowed From</span></span>

<span data-ttu-id="d7262-2267">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2267">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2268">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2268">Preemption Possible</span></span>

<span data-ttu-id="d7262-2269">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2269">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2270">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2270">Example</span></span>

```C
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,
    &bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
    bytes_available. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2271">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2271">See Also</span></span>

- <span data-ttu-id="d7262-2272">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2272">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="d7262-2273">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-2273">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="d7262-2274">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2274">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="d7262-2275">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="d7262-2275">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="d7262-2276">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="d7262-2276">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="d7262-2277">nx_tcp_server_socket_unlisten, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-2277">nx_tcp_server_socket_unlisten, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-2278">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2278">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-2279">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-2279">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="d7262-2280">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-2280">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="d7262-2281">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-2281">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_create"></a><span data-ttu-id="d7262-2282">nx_tcp_socket_create</span><span class="sxs-lookup"><span data-stu-id="d7262-2282">nx_tcp_socket_create</span></span>

<span data-ttu-id="d7262-2283">Создание сокета TCP клиента или сервера</span><span class="sxs-lookup"><span data-stu-id="d7262-2283">Create TCP client or server socket</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2284">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2284">Prototype</span></span>

```C
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="d7262-2285">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2285">Description</span></span>

<span data-ttu-id="d7262-2286">Эта служба создает сокет TCP-клиента или сервера для указанного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-2286">This service creates a TCP client or server socket for the specified IP instance.</span></span>

<span data-ttu-id="d7262-2287">*Подпрограммы обратного вызова приложения вызываются из потока, связанного с этим экземпляром IP.*</span><span class="sxs-lookup"><span data-stu-id="d7262-2287">*Application callback routines are called from the thread associated with this IP instance.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2288">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2288">Parameters</span></span>

- <span data-ttu-id="d7262-2289">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-2289">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-2290">**socket_ptr**: указатель на новый управляющий блок сокета TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2290">**socket_ptr** Pointer to new TCP socket control block.</span></span>
- <span data-ttu-id="d7262-2291">**name**: имя приложения для этого сокета TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2291">**name** Application name for this TCP socket.</span></span>
- <span data-ttu-id="d7262-2292">**type_of_service** определяет тип службы для передачи. Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="d7262-2292">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>

- <span data-ttu-id="d7262-2293">NX_IP_NORMAL (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-2293">NX_IP_NORMAL (0x00000000)</span></span>
- <span data-ttu-id="d7262-2294">NX_IP_MIN_DELAY (0x00100000)</span><span class="sxs-lookup"><span data-stu-id="d7262-2294">NX_IP_MIN_DELAY (0x00100000)</span></span>
- <span data-ttu-id="d7262-2295">NX_IP_MAX_DATA (0x00080000)</span><span class="sxs-lookup"><span data-stu-id="d7262-2295">NX_IP_MAX_DATA (0x00080000)</span></span>
- <span data-ttu-id="d7262-2296">NX_IP_MAX_RELIABLE (0x00040000)</span><span class="sxs-lookup"><span data-stu-id="d7262-2296">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
- <span data-ttu-id="d7262-2297">NX_IP_MIN_COST (0x00020000)</span><span class="sxs-lookup"><span data-stu-id="d7262-2297">NX_IP_MIN_COST (0x00020000)</span></span>

- <span data-ttu-id="d7262-2298">**fragment** указывает, разрешена ли фрагментация IP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-2298">**fragment**  Specifies whether or not IP fragmenting is allowed.</span></span> <span data-ttu-id="d7262-2299">Если указано значение NX_FRAGMENT_OKAY (0x0), то фрагментация IP-пакетов разрешена.</span><span class="sxs-lookup"><span data-stu-id="d7262-2299">If NX_FRAGMENT_OKAY (0x0) is specified, IP fragmenting is allowed.</span></span> <span data-ttu-id="d7262-2300">Если указано значение NX_DONT_FRAGMENT (0x4000), то фрагментация IP-пакетов отключена.</span><span class="sxs-lookup"><span data-stu-id="d7262-2300">If  NX_DONT_FRAGMENT (0x4000) is specified, IP fragmenting is disabled.</span></span>
- <span data-ttu-id="d7262-2301">**time_to_live** задает 8-разрядное значение, определяющее, сколько маршрутизаторов этот пакет может пройти перед тем, как будет отброшен</span><span class="sxs-lookup"><span data-stu-id="d7262-2301">**time_to_live** Specifies the 8-bit value that defines how many routers this packet can pass before being thrown away.</span></span> <span data-ttu-id="d7262-2302">Значение по умолчанию задается в NX_IP_TIME_TO_LIVE.</span><span class="sxs-lookup"><span data-stu-id="d7262-2302">The default value is specified by NX_IP_TIME_TO_LIVE.</span></span>
- <span data-ttu-id="d7262-2303">**window_size** определяет максимальное допустимое число байтов в очереди приема для этого сокета</span><span class="sxs-lookup"><span data-stu-id="d7262-2303">**window_size** Defines the maximum number of bytes allowed in the receive queue for this socket</span></span>
- <span data-ttu-id="d7262-2304">**urgent_data_callback**: функция приложения, которая вызывается каждый раз при обнаружении в потоке приема срочных данных.</span><span class="sxs-lookup"><span data-stu-id="d7262-2304">**urgent_data_callback** Application function that is called whenever urgent data is detected in the receive stream.</span></span> <span data-ttu-id="d7262-2305">Если это значение равно NX_NULL, срочные данные игнорируются.</span><span class="sxs-lookup"><span data-stu-id="d7262-2305">If this value is NX_NULL, urgent data is ignored.</span></span>
- <span data-ttu-id="d7262-2306">**disconnect_callback**: функция приложения, которая вызывается каждый раз, когда сокет выдает команду на завершение подключения на другом конце соединения.</span><span class="sxs-lookup"><span data-stu-id="d7262-2306">**disconnect_callback** Application function that is called whenever a disconnect is issued by the socket at the other end of the connection.</span></span> <span data-ttu-id="d7262-2307">Если это значение равно NX_NULL, функция обратного вызова для завершения подключения отключена.</span><span class="sxs-lookup"><span data-stu-id="d7262-2307">If this value is NX_NULL, the disconnect callback function is disabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2308">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2308">Return Values</span></span>
- <span data-ttu-id="d7262-2309">**NX_SUCCESS** (0x00) — сокет TCP-клиента успешно создан.</span><span class="sxs-lookup"><span data-stu-id="d7262-2309">**NX_SUCCESS** (0x00) Successful TCP client socket create.</span></span>
- <span data-ttu-id="d7262-2310">**NX_OPTION_ERROR** (0x0A) — недопустимый тип службы, параметр фрагментации, размер окна или параметр времени существования.</span><span class="sxs-lookup"><span data-stu-id="d7262-2310">**NX_OPTION_ERROR** (0x0A) Invalid type-of-service, fragment, invalid window size, or time-tolive option.</span></span>
- <span data-ttu-id="d7262-2311">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса или сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2311">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="d7262-2312">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2312">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2313">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2313">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2314">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2314">Allowed From</span></span>

<span data-ttu-id="d7262-2315">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2315">Initialization and Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2316">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2316">Preemption Possible</span></span>

<span data-ttu-id="d7262-2317">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2317">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2318">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2318">Example</span></span>

```C
/* Create a TCP client socket on the previously created IP instance,
    with normal delivery, IP fragmentation enabled, 0x80 time to
    live, a 200-byte receive window, no urgent callback routine, and
    the "client_disconnect" routine to handle disconnection initiated
    from the other end of the connection. */
status = nx_tcp_socket_create(&ip_0, &client_socket,
    "Client Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY,
    0x80, 200, NX_NULL
    client_disconnect);

/* If status is NX_SUCCESS, the client socket is created and ready
    to be bound. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2319">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2319">See Also</span></span>

- <span data-ttu-id="d7262-2320">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2320">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="d7262-2321">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-2321">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="d7262-2322">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2322">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="d7262-2323">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="d7262-2323">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="d7262-2324">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="d7262-2324">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="d7262-2325">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="d7262-2325">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="d7262-2326">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2326">nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-2327">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-2327">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="d7262-2328">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-2328">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="d7262-2329">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-2329">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_delete"></a><span data-ttu-id="d7262-2330">nx_tcp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-2330">nx_tcp_socket_delete</span></span>

<span data-ttu-id="d7262-2331">Удаление сокета TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2331">Delete TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2332">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2332">Prototype</span></span>

```C
UINT nx_tcp_socket_delete(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-2333">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2333">Description</span></span>

<span data-ttu-id="d7262-2334">Эта служба удаляет созданный ранее сокет TCP.</span><span class="sxs-lookup"><span data-stu-id="d7262-2334">This service deletes a previously created TCP socket.</span></span> <span data-ttu-id="d7262-2335">Если сокет по-прежнему привязан или подключен, служба возвращает код ошибки.</span><span class="sxs-lookup"><span data-stu-id="d7262-2335">If the socket is still bound or connected, the service returns an error code.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2336">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2336">Parameters</span></span>

- <span data-ttu-id="d7262-2337">**socket_ptr**: ранее созданный сокет TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2337">**socket_ptr** Previously created TCP socket</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2338">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2338">Return Values</span></span>

- <span data-ttu-id="d7262-2339">**NX_SUCCESS** (0x00) — сокет успешно удален.</span><span class="sxs-lookup"><span data-stu-id="d7262-2339">**NX_SUCCESS** (0x00) Successful socket delete.</span></span>
- <span data-ttu-id="d7262-2340">**NX_NOT_CREATED** (0x27) — сокет не был создан.</span><span class="sxs-lookup"><span data-stu-id="d7262-2340">**NX_NOT_CREATED** (0x27) Socket was not created.</span></span>
- <span data-ttu-id="d7262-2341">**NX_STILL_BOUND** (0x42) — сокет все еще привязан.</span><span class="sxs-lookup"><span data-stu-id="d7262-2341">**NX_STILL_BOUND** (0x42) Socket is still bound.</span></span>
- <span data-ttu-id="d7262-2342">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2342">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-2343">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2343">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2344">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2344">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2345">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2345">Allowed From</span></span>

<span data-ttu-id="d7262-2346">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2346">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2347">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2347">Preemption Possible</span></span>

<span data-ttu-id="d7262-2348">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2348">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2349">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2349">Example</span></span>

```C
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2350">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2350">See Also</span></span>

- <span data-ttu-id="d7262-2351">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2351">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="d7262-2352">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-2352">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="d7262-2353">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2353">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="d7262-2354">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="d7262-2354">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="d7262-2355">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="d7262-2355">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="d7262-2356">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="d7262-2356">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="d7262-2357">nx_tcp_socket_create, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2357">nx_tcp_socket_create, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-2358">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-2358">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="d7262-2359">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-2359">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send,</span></span>
- <span data-ttu-id="d7262-2360">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-2360">nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_disconnect"></a><span data-ttu-id="d7262-2361">nx_tcp_socket_disconnect</span><span class="sxs-lookup"><span data-stu-id="d7262-2361">nx_tcp_socket_disconnect</span></span>

<span data-ttu-id="d7262-2362">Завершение подключений к сокетам клиента и сервера</span><span class="sxs-lookup"><span data-stu-id="d7262-2362">Disconnect client and server socket connections</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2363">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2363">Prototype</span></span>

```C
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d7262-2364">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2364">Description</span></span>

<span data-ttu-id="d7262-2365">Эта служба завершает установленное подключение к сокету клиента или сервера.</span><span class="sxs-lookup"><span data-stu-id="d7262-2365">This service disconnects an established client or server socket connection.</span></span> <span data-ttu-id="d7262-2366">После завершения подключения к сокету сервера должен выполняться запрос на отмену принятия, а отключенный сокет клиента остается в состоянии готовности к другому запросу на подключение.</span><span class="sxs-lookup"><span data-stu-id="d7262-2366">A disconnect of a server socket should be followed by an unaccept request, while a client socket that is disconnected is left in a state ready for another connection request.</span></span> <span data-ttu-id="d7262-2367">Если процесс отключения не может завершиться немедленно, служба приостанавливает выполнение в соответствии с указанным параметром ожидания.</span><span class="sxs-lookup"><span data-stu-id="d7262-2367">If the disconnect process cannot finish immediately, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2368">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2368">Parameters</span></span>

- <span data-ttu-id="d7262-2369">**socket_ptr**: указатель на ранее подключенный экземпляр сокета клиента или сервера</span><span class="sxs-lookup"><span data-stu-id="d7262-2369">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="d7262-2370">**wait_option** определяет поведение службы во время завершения соединения</span><span class="sxs-lookup"><span data-stu-id="d7262-2370">**wait_option** Defines how the service behaves while the disconnection is in progress.</span></span> <span data-ttu-id="d7262-2371">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d7262-2371">The wait options are defined as follows:</span></span>
- <span data-ttu-id="d7262-2372">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-2372">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="d7262-2373">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-2373">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="d7262-2374">Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d7262-2374">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2375">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2375">Return Values</span></span>

- <span data-ttu-id="d7262-2376">**NX_SUCCESS** (0x00) — сокет успешно отключен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2376">**NX_SUCCESS** (0x00) Successful socket disconnect.</span></span>
- <span data-ttu-id="d7262-2377">**NX_NOT_CONNECTED** (0x38) — указанный сокет не подключен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2377">**NX_NOT_CONNECTED** (0x38) Specified socket is not connected.</span></span>
- <span data-ttu-id="d7262-2378">**NX_IN_PROGRESS** (0x37) — выполняется отключение; параметр ожидания не задан.</span><span class="sxs-lookup"><span data-stu-id="d7262-2378">**NX_IN_PROGRESS** (0x37) Disconnect is in progress, no wait was specified.</span></span>
- <span data-ttu-id="d7262-2379">**NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="d7262-2379">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="d7262-2380">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2380">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-2381">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2381">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2382">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2382">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2383">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2383">Allowed From</span></span>

<span data-ttu-id="d7262-2384">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2384">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2385">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2385">Preemption Possible</span></span>

<span data-ttu-id="d7262-2386">Да</span><span class="sxs-lookup"><span data-stu-id="d7262-2386">Yes</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2387">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2387">Example</span></span>

```C
/* Disconnect from a previously established connection and wait a
    maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
    as a result of the client socket connect or the server accept) is
    disconnected. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2388">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2388">See Also</span></span>

- <span data-ttu-id="d7262-2389">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2389">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="d7262-2390">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-2390">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="d7262-2391">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2391">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="d7262-2392">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="d7262-2392">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="d7262-2393">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="d7262-2393">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="d7262-2394">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="d7262-2394">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="d7262-2395">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2395">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_info_get,</span></span>
- <span data-ttu-id="d7262-2396">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-2396">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="d7262-2397">nx_tcp_socket_send, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-2397">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_disconnect_complete_notify"></a><span data-ttu-id="d7262-2398">nx_tcp_socket_disconnect_complete_notify</span><span class="sxs-lookup"><span data-stu-id="d7262-2398">nx_tcp_socket_disconnect_complete_notify</span></span>

<span data-ttu-id="d7262-2399">Установка функции обратного вызова для уведомления о завершении подключения TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2399">Install TCP disconnect complete notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2400">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2400">Prototype</span></span>

```C
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="d7262-2401">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2401">Description</span></span>

<span data-ttu-id="d7262-2402">Эта служба регистрирует функцию обратного вызова, которая вызывается после завершения операции отключения сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2402">This service registers a callback function which is invoked after a socket disconnect operation is completed.</span></span> <span data-ttu-id="d7262-2403">Функция обратного вызова для отключения сокета TCP доступна, если сборка NetX выполнена с заданным параметром</span><span class="sxs-lookup"><span data-stu-id="d7262-2403">The TCP socket disconnect complete callback function is available if NetX is built with the option</span></span>

- <span data-ttu-id="d7262-2404">***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT***.</span><span class="sxs-lookup"><span data-stu-id="d7262-2404">***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2405">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2405">Parameters</span></span>

- <span data-ttu-id="d7262-2406">**socket_ptr**: указатель на ранее подключенный экземпляр сокета клиента или сервера</span><span class="sxs-lookup"><span data-stu-id="d7262-2406">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="d7262-2407">**tcp_disconnect_complete_notify**: функция обратного вызова, которую необходимо установить</span><span class="sxs-lookup"><span data-stu-id="d7262-2407">**tcp_disconnect_complete_notify** The callback function to be installed.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2408">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2408">Return Values</span></span>
- <span data-ttu-id="d7262-2409">**NX_SUCCESS** (0x00) — функция обратного вызова успешно зарегистрирована</span><span class="sxs-lookup"><span data-stu-id="d7262-2409">**NX_SUCCESS** (0x00) Successfully registered the callback function.</span></span>
- <span data-ttu-id="d7262-2410">**NX_NOT_SUPPORTED** (0x4B) — расширенная функция уведомления не встроена в библиотеку NetX.</span><span class="sxs-lookup"><span data-stu-id="d7262-2410">**NX_NOT_SUPPORTED** (0x4B) The extended notify feature is not built into the NetX library</span></span>
- <span data-ttu-id="d7262-2411">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2411">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-2412">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2412">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2413">**NX_NOT_ENABLED** (0x14) — функция TCP не включена.</span><span class="sxs-lookup"><span data-stu-id="d7262-2413">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2414">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2414">Allowed From</span></span>

<span data-ttu-id="d7262-2415">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2415">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2416">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2416">Preemption Possible</span></span>

<span data-ttu-id="d7262-2417">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2417">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2418">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2418">Example</span></span>

```C
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
    callback);
```

### <a name="see-also"></a><span data-ttu-id="d7262-2419">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2419">See Also</span></span>

- <span data-ttu-id="d7262-2420">nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify,</span><span class="sxs-lookup"><span data-stu-id="d7262-2420">nx_tcp_enable, nx_tcp_socket_create, nx_tcp_socket_establish_notify,</span></span>
- <span data-ttu-id="d7262-2421">nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2421">nx_tcp_socket_mss_get, nx_tcp_socket_mss_peer_get,</span></span>
- <span data-ttu-id="d7262-2422">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2422">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="d7262-2423">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="d7262-2423">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="d7262-2424">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="d7262-2424">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="d7262-2425">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="d7262-2425">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_establish_notify"></a><span data-ttu-id="d7262-2426">nx_tcp_socket_establish_notify</span><span class="sxs-lookup"><span data-stu-id="d7262-2426">nx_tcp_socket_establish_notify</span></span>

<span data-ttu-id="d7262-2427">Задание функции обратного вызова для уведомления об установке TCP-подключения</span><span class="sxs-lookup"><span data-stu-id="d7262-2427">Set TCP establish notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2428">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2428">Prototype</span></span>

```C
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="d7262-2429">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2429">Description</span></span>

<span data-ttu-id="d7262-2430">Эта служба регистрирует функцию обратного вызова, которая вызывается после установления соединения сокетом TCP.</span><span class="sxs-lookup"><span data-stu-id="d7262-2430">This service registers a callback function, which is called after a TCP socket makes a connection.</span></span> <span data-ttu-id="d7262-2431">Функция обратного вызова для установления подключения к сокету TCP доступна, если сборка NetX выполнена с заданным параметром ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT***.</span><span class="sxs-lookup"><span data-stu-id="d7262-2431">The TCP socket establish callback function is available if NetX is built with the option ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2432">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2432">Parameters</span></span>

- <span data-ttu-id="d7262-2433">**socket_ptr**: указатель на ранее подключенный экземпляр сокета клиента или сервера</span><span class="sxs-lookup"><span data-stu-id="d7262-2433">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="d7262-2434">**tcp_establish_notify**: функция обратного вызова, вызываемая после установления TCP-подключения</span><span class="sxs-lookup"><span data-stu-id="d7262-2434">**tcp_establish_notify** Callback function invoked after a TCP connection is established.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2435">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2435">Return Values</span></span>

- <span data-ttu-id="d7262-2436">**NX_SUCCESS** (0x00) — функция уведомления успешно задана.</span><span class="sxs-lookup"><span data-stu-id="d7262-2436">**NX_SUCCESS** (0x00) Successfully sets the notify function.</span></span>
- <span data-ttu-id="d7262-2437">**NX_NOT_SUPPORTED** (0x4B) — расширенная функция уведомления не встроена в библиотеку NetX.</span><span class="sxs-lookup"><span data-stu-id="d7262-2437">**NX_NOT_SUPPORTED** (0x4B) The extended notify feature is not built into the NetX library</span></span>
- <span data-ttu-id="d7262-2438">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2438">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-2439">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2439">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2440">**NX_NOT_ENABLED** (0x14) — протокол TCP не был включен приложением.</span><span class="sxs-lookup"><span data-stu-id="d7262-2440">**NX_NOT_ENABLED** (0x14) TCP has not been enabled by the application.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2441">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2441">Allowed From</span></span>

<span data-ttu-id="d7262-2442">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2442">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2443">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2443">Preemption Possible</span></span>

<span data-ttu-id="d7262-2444">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2444">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2445">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2445">Example</span></span>

```C
/* Set the function pointer "callback" as the notify function NetX
will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```

### <a name="see-also"></a><span data-ttu-id="d7262-2446">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2446">See Also</span></span>

- <span data-ttu-id="d7262-2447">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-2447">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-2448">nx_tcp_socket_disconnect_complete_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2448">nx_tcp_socket_disconnect_complete_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="d7262-2449">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-2449">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="d7262-2450">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="d7262-2450">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="d7262-2451">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="d7262-2451">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="d7262-2452">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="d7262-2452">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_info_get"></a><span data-ttu-id="d7262-2453">nx_tcp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="d7262-2453">nx_tcp_socket_info_get</span></span>

<span data-ttu-id="d7262-2454">Получение сведений о действиях сокета TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2454">Retrieve information about TCP socket activities</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2455">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2455">Prototype</span></span>

```C
UINT nx_tcp_socket_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_retransmit_packets,
    ULONG *tcp_packets_queued,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_socket_state,
    ULONG *tcp_transmit_queue_depth,
    ULONG *tcp_transmit_window,
    ULONG *tcp_receive_window);
```

### <a name="description"></a><span data-ttu-id="d7262-2456">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2456">Description</span></span>

<span data-ttu-id="d7262-2457">Эта служба получает сведения о действиях сокета TCP для указанного экземпляра сокета TCP.</span><span class="sxs-lookup"><span data-stu-id="d7262-2457">This service retrieves information about TCP socket activities for the specified TCP socket instance.</span></span>

<span data-ttu-id="d7262-2458">*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.</span><span class="sxs-lookup"><span data-stu-id="d7262-2458">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2459">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2459">Parameters</span></span>

- <span data-ttu-id="d7262-2460">**socket_ptr**: указатель на ранее созданный экземпляр сокета TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2460">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="d7262-2461">**tcp_packets_sent**: указатель на место назначения для общего числа отправленных через сокет TCP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-2461">**tcp_packets_sent** Pointer to destination for the total number of TCP packets sent on socket.</span></span>
- <span data-ttu-id="d7262-2462">**tcp_bytes_sent**: указатель на место назначения для общего числа отправленных через сокет TCP байтов</span><span class="sxs-lookup"><span data-stu-id="d7262-2462">**tcp_bytes_sent** Pointer to destination for the total number of TCP bytes sent on socket.</span></span>
- <span data-ttu-id="d7262-2463">**tcp_packets_received**: указатель на место назначения для общего числа полученных через сокет TCP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-2463">**tcp_packets_received** Pointer to destination of the total number of TCP packets received on socket.</span></span>
- <span data-ttu-id="d7262-2464">**tcp_bytes_received**: указатель на место назначения для общего числа полученных через сокет TCP байтов</span><span class="sxs-lookup"><span data-stu-id="d7262-2464">**tcp_bytes_received** Pointer to destination of the total number of TCP bytes received on socket.</span></span>
- <span data-ttu-id="d7262-2465">**tcp_retransmit_packets**: указатель на место назначения для общего числа ретранслированных TCP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-2465">**tcp_retransmit_packets** Pointer to destination of the total number of TCP packet retransmissions.</span></span>
- <span data-ttu-id="d7262-2466">**tcp_packets_queued**: указатель на место назначения для общего числа TCP-пакетов, поставленных в очередь в сокете</span><span class="sxs-lookup"><span data-stu-id="d7262-2466">**tcp_packets_queued** Pointer to destination of the total number of queued TCP packets on socket.</span></span>
- <span data-ttu-id="d7262-2467">**tcp_checksum_errors**: указатель на место назначения для общего числа TCP-пакетов с ошибками контрольной суммы в сокете</span><span class="sxs-lookup"><span data-stu-id="d7262-2467">**tcp_checksum_errors** Pointer to destination of the total number of TCP packets with checksum errors on socket.</span></span>
- <span data-ttu-id="d7262-2468">**tcp_socket_state**: указатель на место назначения для текущего состояния сокета</span><span class="sxs-lookup"><span data-stu-id="d7262-2468">**tcp_socket_state** Pointer to destination of the socket’s current state.</span></span>
- <span data-ttu-id="d7262-2469">**tcp_transmit_queue_depth**: указатель на место назначения для общего числа передаваемых пакетов, ожидающих подтверждения в очереди</span><span class="sxs-lookup"><span data-stu-id="d7262-2469">**tcp_transmit_queue_depth** Pointer to destination of the total number of transmit packets still queued waiting for ACK.</span></span>
- <span data-ttu-id="d7262-2470">**tcp_transmit_window**: указатель на место назначения для текущего размера окна передачи</span><span class="sxs-lookup"><span data-stu-id="d7262-2470">**tcp_transmit_window** Pointer to destination of the current transmit window size.</span></span>
- <span data-ttu-id="d7262-2471">**tcp_receive_window**: указатель на место назначения для текущего размера окна приема</span><span class="sxs-lookup"><span data-stu-id="d7262-2471">**tcp_receive_window** Pointer to destination of the current receive window size.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2472">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2472">Return Values</span></span>

- <span data-ttu-id="d7262-2473">**NX_SUCCESS** (0x00) — успешное получение сведений о сокете TCP.</span><span class="sxs-lookup"><span data-stu-id="d7262-2473">**NX_SUCCESS** (0x00) Successful TCP socket information retrieval.</span></span>
- <span data-ttu-id="d7262-2474">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2474">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-2475">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2475">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2476">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2476">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2477">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2477">Return Values</span></span>

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="allowed-from"></a><span data-ttu-id="d7262-2478">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2478">Allowed From</span></span>

<span data-ttu-id="d7262-2479">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2479">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2480">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2480">Preemption Possible</span></span>

<span data-ttu-id="d7262-2481">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2481">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2482">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2482">Example</span></span>

```C
/* Retrieve TCP socket information from previously created socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
    &tcp_packets_sent,
    &tcp_bytes_sent,
    &tcp_packets_received,
    &tcp_bytes_received,
    &tcp_retransmit_packets,
    &tcp_packets_queued,
    &tcp_checksum_errors,
    &tcp_socket_state,
    &tcp_transmit_queue_depth,
    &tcp_transmit_window,
    &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2483">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2483">See Also</span></span>

- <span data-ttu-id="d7262-2484">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2484">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="d7262-2485">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-2485">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="d7262-2486">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2486">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="d7262-2487">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="d7262-2487">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="d7262-2488">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="d7262-2488">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="d7262-2489">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="d7262-2489">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="d7262-2490">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2490">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-2491">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-2491">nx_tcp_socket_receive, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="d7262-2492">nx_tcp_socket_send, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-2492">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_mss_get"></a><span data-ttu-id="d7262-2493">nx_tcp_socket_mss_get</span><span class="sxs-lookup"><span data-stu-id="d7262-2493">nx_tcp_socket_mss_get</span></span>

<span data-ttu-id="d7262-2494">Получение MSS сокета</span><span class="sxs-lookup"><span data-stu-id="d7262-2494">Get MSS of socket</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2495">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2495">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a><span data-ttu-id="d7262-2496">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2496">Description</span></span>

<span data-ttu-id="d7262-2497">Эта служба получает локальный максимальный размер сегмента (MSS) для указанного сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2497">This service retrieves the specified socket's local Maximum Segment Size (MSS).</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2498">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2498">Parameters</span></span>

- <span data-ttu-id="d7262-2499">**socket_ptr**: указатель на ранее созданный сокет</span><span class="sxs-lookup"><span data-stu-id="d7262-2499">**socket_ptr** Pointer to previously created socket.</span></span>
- <span data-ttu-id="d7262-2500">**mss**: место назначения для возвращаемого значения MSS</span><span class="sxs-lookup"><span data-stu-id="d7262-2500">**mss** Destination for returning MSS.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2501">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2501">Return Values</span></span>

- <span data-ttu-id="d7262-2502">**NX_SUCCESS** (0x00) — успешное получение MSS.</span><span class="sxs-lookup"><span data-stu-id="d7262-2502">**NX_SUCCESS** (0x00) Successful MSS get.</span></span>
- <span data-ttu-id="d7262-2503">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сокет или место назначения для MSS.</span><span class="sxs-lookup"><span data-stu-id="d7262-2503">**NX_PTR_ERROR** (0x07) Invalid socket or MSS destination pointer.</span></span>
- <span data-ttu-id="d7262-2504">**NX_NOT_ENABLED** (0x14) — протокол TCP не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2504">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="d7262-2505">**NX_CALLER_ERROR** (0x11) — вызывающий объект не является потоком или инициализацией.</span><span class="sxs-lookup"><span data-stu-id="d7262-2505">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2506">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2506">Allowed From</span></span>

<span data-ttu-id="d7262-2507">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2507">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2508">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2508">Preemption Possible</span></span>

<span data-ttu-id="d7262-2509">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2509">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2510">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2510">Example</span></span>

```C
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket's current MSS value. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2511">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2511">See Also</span></span>

- <span data-ttu-id="d7262-2512">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-2512">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-2513">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="d7262-2513">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="d7262-2514">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_peer_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2514">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_peer_get,</span></span>
- <span data-ttu-id="d7262-2515">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2515">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="d7262-2516">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="d7262-2516">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="d7262-2517">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="d7262-2517">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="d7262-2518">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="d7262-2518">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_mss_peer_get"></a><span data-ttu-id="d7262-2519">nx_tcp_socket_mss_peer_get</span><span class="sxs-lookup"><span data-stu-id="d7262-2519">nx_tcp_socket_mss_peer_get</span></span>

<span data-ttu-id="d7262-2520">Получение MSS однорангового сокета TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2520">Get MSS of the peer TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2521">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2521">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_peer_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```

### <a name="description"></a><span data-ttu-id="d7262-2522">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2522">Description</span></span>

<span data-ttu-id="d7262-2523">Эта служба получает максимальный размер сегмента (MSS), объявленный одноранговым сокетом.</span><span class="sxs-lookup"><span data-stu-id="d7262-2523">This service retrieves the Maximum Segment Size (MSS) advertised by the peer socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2524">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2524">Parameters</span></span>

- <span data-ttu-id="d7262-2525">**socket_ptr**: указатель на ранее созданный и подключенный сокет</span><span class="sxs-lookup"><span data-stu-id="d7262-2525">**socket_ptr** Pointer to previously created and connected socket.</span></span>
- <span data-ttu-id="d7262-2526">**mss**: место назначения для возвращаемого значения MSS</span><span class="sxs-lookup"><span data-stu-id="d7262-2526">**mss** Destination for returning the MSS.</span></span>


### <a name="return-values"></a><span data-ttu-id="d7262-2527">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2527">Return Values</span></span>

- <span data-ttu-id="d7262-2528">**NX_SUCCESS** (0x00) — успешное получение MSS однорангового сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2528">**NX_SUCCESS** (0x00) Successful peer MSS get.</span></span>
- <span data-ttu-id="d7262-2529">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сокет или место назначения для MSS.</span><span class="sxs-lookup"><span data-stu-id="d7262-2529">**NX_PTR_ERROR** (0x07) Invalid socket or MSS destination pointer.</span></span>
- <span data-ttu-id="d7262-2530">**NX_NOT_ENABLED** (0x14) — протокол TCP не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2530">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="d7262-2531">**NX_CALLER_ERROR** (0x11) — вызывающий объект не является потоком или инициализацией.</span><span class="sxs-lookup"><span data-stu-id="d7262-2531">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2532">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2532">Allowed From</span></span>

<span data-ttu-id="d7262-2533">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2533">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2534">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2534">Preemption Possible</span></span>

<span data-ttu-id="d7262-2535">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2535">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2536">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2536">Example</span></span>

```C
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
    socket peer’s advertised MSS value. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2537">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2537">See Also</span></span>

- <span data-ttu-id="d7262-2538">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-2538">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-2539">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="d7262-2539">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="d7262-2540">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2540">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="d7262-2541">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2541">nx_tcp_socket_mss_set, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="d7262-2542">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="d7262-2542">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="d7262-2543">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="d7262-2543">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="d7262-2544">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="d7262-2544">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_mss_set"></a><span data-ttu-id="d7262-2545">nx_tcp_socket_mss_set</span><span class="sxs-lookup"><span data-stu-id="d7262-2545">nx_tcp_socket_mss_set</span></span>

<span data-ttu-id="d7262-2546">Задание MSS сокета</span><span class="sxs-lookup"><span data-stu-id="d7262-2546">Set MSS of socket</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2547">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2547">Prototype</span></span>

```C
UINT nx_tcp_socket_mss_set(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG mss);
```

### <a name="description"></a><span data-ttu-id="d7262-2548">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2548">Description</span></span>

<span data-ttu-id="d7262-2549">Эта служба задает максимальный размер сегмента (MSS) для указанного сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2549">This service sets the specified socket's Maximum Segment Size (MSS).</span></span> <span data-ttu-id="d7262-2550">Обратите внимание, что значение MSS должно быть в пределах размера MTU для сетевого IP-интерфейса, чтобы было место для заголовков IP и TCP.</span><span class="sxs-lookup"><span data-stu-id="d7262-2550">Note the MSS value must be within the network interface IP MTU, allowing room for IP and TCP headers.</span></span>

<span data-ttu-id="d7262-2551">Эту службу следует использовать до того, как сокет TCP начнет процесс подключения.</span><span class="sxs-lookup"><span data-stu-id="d7262-2551">This service should be used before a TCP socket starts the connection process.</span></span> <span data-ttu-id="d7262-2552">Если служба используется после установления соединения TCP, новое значение для него не действует.</span><span class="sxs-lookup"><span data-stu-id="d7262-2552">If the service is used after a TCP connection is established, the new value has no effect on the connection.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2553">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2553">Parameters</span></span>

- <span data-ttu-id="d7262-2554">**socket_ptr**: указатель на ранее созданный сокет</span><span class="sxs-lookup"><span data-stu-id="d7262-2554">**socket_ptr** Pointer to previously created socket.</span></span>
- <span data-ttu-id="d7262-2555">**mss**: задаваемое значение MSS</span><span class="sxs-lookup"><span data-stu-id="d7262-2555">**mss** Value of MSS to set.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2556">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2556">Return Values</span></span>

- <span data-ttu-id="d7262-2557">**NX_SUCCESS** (0x00) — успешное задание MSS.</span><span class="sxs-lookup"><span data-stu-id="d7262-2557">**NX_SUCCESS** (0x00) Successful MSS set.</span></span>
- <span data-ttu-id="d7262-2558">**NX_SIZE_ERROR** (0x09) — указано слишком большое значение MSS.</span><span class="sxs-lookup"><span data-stu-id="d7262-2558">**NX_SIZE_ERROR** (0x09) Specified MSS value is too large.</span></span>
- <span data-ttu-id="d7262-2559">**NX_NOT_CONNECTED** (0x38) — TCP-подключение не установлено.</span><span class="sxs-lookup"><span data-stu-id="d7262-2559">**NX_NOT_CONNECTED** (0x38) TCP connection has not been established</span></span>
- <span data-ttu-id="d7262-2560">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2560">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-2561">**NX_NOT_ENABLED** (0x14) — протокол TCP не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2561">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="d7262-2562">**NX_CALLER_ERROR** (0x11) — вызывающий объект не является потоком или инициализацией.</span><span class="sxs-lookup"><span data-stu-id="d7262-2562">**NX_CALLER_ERROR** (0x11) Caller is not a thread or initialization.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2563">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2563">Allowed From</span></span>

<span data-ttu-id="d7262-2564">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2564">Initialization and threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2565">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2565">Preemption Possible</span></span>

<span data-ttu-id="d7262-2566">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2566">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2567">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2567">Example</span></span>

```C
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2568">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2568">See Also</span></span>

- <span data-ttu-id="d7262-2569">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-2569">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-2570">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="d7262-2570">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="d7262-2571">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2571">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="d7262-2572">nx_tcp_socket_mss_peer_get, nx_tcp_socket_peer_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2572">nx_tcp_socket_mss_peer_get, nx_tcp_socket_peer_info_get,</span></span>
- <span data-ttu-id="d7262-2573">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="d7262-2573">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="d7262-2574">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="d7262-2574">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="d7262-2575">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="d7262-2575">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_peer_info_get"></a><span data-ttu-id="d7262-2576">nx_tcp_socket_peer_info_get</span><span class="sxs-lookup"><span data-stu-id="d7262-2576">nx_tcp_socket_peer_info_get</span></span>

<span data-ttu-id="d7262-2577">Получение сведений об одноранговом сокете TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2577">Retrieve information about peer TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2578">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2578">Prototype</span></span>

```C
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address, 
    ULONG *peer_port);
```

### <a name="description"></a><span data-ttu-id="d7262-2579">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2579">Description</span></span>

<span data-ttu-id="d7262-2580">Эта служба получает IP-адрес и сведения о порте для подключенного однорангового сокета TCP по IP-сети.</span><span class="sxs-lookup"><span data-stu-id="d7262-2580">This service retrieves peer IP address and port information for the connected TCP socket over IP network.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2581">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2581">Parameters</span></span>

- <span data-ttu-id="d7262-2582">**socket_ptr**: указатель на ранее созданный сокет TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2582">**socket_ptr** Pointer to previously created TCP socket.</span></span>
- <span data-ttu-id="d7262-2583">**peer_ip_address**: указатель на место назначения для IP-адреса однорангового сокета в порядке байтов узла</span><span class="sxs-lookup"><span data-stu-id="d7262-2583">**peer_ip_address** Pointer to destination for peer IP address, in host byte order.</span></span>
- <span data-ttu-id="d7262-2584">**peer_port**: указатель на место назначения для номера порта однорангового сокета в порядке байтов узла</span><span class="sxs-lookup"><span data-stu-id="d7262-2584">**peer_port** Pointer to destination for peer port number, in host byte order.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2585">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2585">Return Values</span></span>

- <span data-ttu-id="d7262-2586">**NX_SUCCESS** (0x00) — служба успешно выполняется.</span><span class="sxs-lookup"><span data-stu-id="d7262-2586">**NX_SUCCESS** (0x00) Service executes successfully.</span></span> <span data-ttu-id="d7262-2587">IP-адрес и номер порта однорангового сокета возвращаются вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="d7262-2587">Peer IP address and port number are returned to the caller.</span></span>
- <span data-ttu-id="d7262-2588">**NX_NOT_CONNECTED** (0x38) — сокет не находится в подключенном состоянии.</span><span class="sxs-lookup"><span data-stu-id="d7262-2588">**NX_NOT_CONNECTED** (0x38) Socket is not in a connected state.</span></span>
- <span data-ttu-id="d7262-2589">**NX_PTR_ERROR** (0x07) — недопустимые указатели.</span><span class="sxs-lookup"><span data-stu-id="d7262-2589">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="d7262-2590">**NX_NOT_ENABLED** (0x14) — протокол TCP не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2590">**NX_NOT_ENABLED** (0x14) TCP is not enabled.</span></span>
- <span data-ttu-id="d7262-2591">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2591">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2592">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2592">Allowed From</span></span>

<span data-ttu-id="d7262-2593">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2593">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2594">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2594">Preemption Possible</span></span>

<span data-ttu-id="d7262-2595">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2595">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2596">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2596">Example</span></span>

```C
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
    &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2597">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2597">See Also</span></span>

- <span data-ttu-id="d7262-2598">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-2598">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-2599">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="d7262-2599">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="d7262-2600">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2600">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="d7262-2601">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-2601">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="d7262-2602">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="d7262-2602">nx_tcp_socket_receive_notify, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="d7262-2603">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="d7262-2603">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="d7262-2604">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="d7262-2604">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_receive"></a><span data-ttu-id="d7262-2605">nx_tcp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="d7262-2605">nx_tcp_socket_receive</span></span>

<span data-ttu-id="d7262-2606">Получение данных из сокета TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2606">Receive data from TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2607">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2607">Prototype</span></span>

```C
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d7262-2608">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2608">Description</span></span>

<span data-ttu-id="d7262-2609">Эта служба получает данные TCP из указанного сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2609">This service receives TCP data from the specified socket.</span></span> <span data-ttu-id="d7262-2610">Если в указанном сокете в очереди нет данных, вызывающий объект приостанавливает выполнение на основе указанного параметра ожидания.</span><span class="sxs-lookup"><span data-stu-id="d7262-2610">If no data are queued on the specified socket, the caller suspends based on the supplied wait option.</span></span>

<span data-ttu-id="d7262-2611">*Если возвращается значение NX_SUCCESS, приложение отвечает за освобождение полученного пакета, когда он больше не нужен*.</span><span class="sxs-lookup"><span data-stu-id="d7262-2611">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2612">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2612">Parameters</span></span>

- <span data-ttu-id="d7262-2613">**socket_ptr**: указатель на ранее созданный экземпляр сокета TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2613">**socket_ptr** Pointer to previously created TCP socket instance.</span></span>
- <span data-ttu-id="d7262-2614">**packet_ptr**: указатель на указатель TCP-пакета</span><span class="sxs-lookup"><span data-stu-id="d7262-2614">**packet_ptr** Pointer to TCP packet pointer.</span></span>
- <span data-ttu-id="d7262-2615">**wait_option** определяет поведение службы в случае, если в этом сокете нет данных в очереди</span><span class="sxs-lookup"><span data-stu-id="d7262-2615">**wait_option** Defines how the service behaves if no data are currently queued on this socket.</span></span> <span data-ttu-id="d7262-2616">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d7262-2616">The wait options are defined as follows:</span></span>
- <span data-ttu-id="d7262-2617">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-2617">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="d7262-2618">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-2618">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="d7262-2619">Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d7262-2619">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2620">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2620">Return Values</span></span>
- <span data-ttu-id="d7262-2621">**NX_SUCCESS** (0x00) — данные сокета успешно получены.</span><span class="sxs-lookup"><span data-stu-id="d7262-2621">**NX_SUCCESS** (0x00) Successful socket data receive.</span></span>
- <span data-ttu-id="d7262-2622">**NX_NOT_BOUND** (0x24) — сокет еще не привязан.</span><span class="sxs-lookup"><span data-stu-id="d7262-2622">**NX_NOT_BOUND** (0x24) Socket is not bound yet.</span></span>
- <span data-ttu-id="d7262-2623">**NX_NO_PACKET** (0x01) — данные не получены.</span><span class="sxs-lookup"><span data-stu-id="d7262-2623">**NX_NO_PACKET** (0x01) No data received.</span></span>
- <span data-ttu-id="d7262-2624">**NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="d7262-2624">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="d7262-2625">**NX_NOT_CONNECTED** (0x38) — сокет больше не подключен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2625">**NX_NOT_CONNECTED** (0x38) The socket is no longer connected.</span></span>
- <span data-ttu-id="d7262-2626">**NX_PTR_ERROR** (0x07) — недопустимый указатель на сокет или возвращаемый пакет.</span><span class="sxs-lookup"><span data-stu-id="d7262-2626">**NX_PTR_ERROR** (0x07) Invalid socket or return packet pointer.</span></span>
- <span data-ttu-id="d7262-2627">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2627">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2628">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2628">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2629">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2629">Allowed From</span></span>

<span data-ttu-id="d7262-2630">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2630">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2631">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2631">Preemption Possible</span></span>

<span data-ttu-id="d7262-2632">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2632">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2633">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2633">Example</span></span>

<span data-ttu-id="d7262-2634">/\* Получение пакета из ранее созданного и подключенного сокета TCP-клиента.</span><span class="sxs-lookup"><span data-stu-id="d7262-2634">/\* Receive a packet from the previously created and connected TCP client socket.</span></span> <span data-ttu-id="d7262-2635">Если пакет недоступен, подождите 200 тактов таймера, прежде чем завершать операцию.</span><span class="sxs-lookup"><span data-stu-id="d7262-2635">If no packet is available, wait for 200 timer ticks before giving up.</span></span> <span data-ttu-id="d7262-2636">\*/ status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);</span><span class="sxs-lookup"><span data-stu-id="d7262-2636">\*/ status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);</span></span>

<span data-ttu-id="d7262-2637">/\* Если состояние — NX_SUCCESS, на полученный пакет указывает packet_ptr.</span><span class="sxs-lookup"><span data-stu-id="d7262-2637">/\* If status is NX_SUCCESS, the received packet is pointed to by "packet_ptr".</span></span> */

### <a name="see-also"></a><span data-ttu-id="d7262-2638">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2638">See Also</span></span>

- <span data-ttu-id="d7262-2639">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2639">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="d7262-2640">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-2640">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="d7262-2641">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2641">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="d7262-2642">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="d7262-2642">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="d7262-2643">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="d7262-2643">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="d7262-2644">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="d7262-2644">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="d7262-2645">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2645">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-2646">nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-2646">nx_tcp_socket_info_get, nx_tcp_socket_receive_queue_max_set,</span></span>
- <span data-ttu-id="d7262-2647">nx_tcp_socket_send, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-2647">nx_tcp_socket_send, nx_tcp_socket_state_wait</span></span>

## <a name="nx_tcp_socket_receive_notify"></a><span data-ttu-id="d7262-2648">nx_tcp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="d7262-2648">nx_tcp_socket_receive_notify</span></span>

<span data-ttu-id="d7262-2649">Уведомление приложения о полученных пакетах</span><span class="sxs-lookup"><span data-stu-id="d7262-2649">Notify application of received packets</span></span>


### <a name="prototype"></a><span data-ttu-id="d7262-2650">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2650">Prototype</span></span>

```C
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_receive_notify) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="d7262-2651">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2651">Description</span></span>

<span data-ttu-id="d7262-2652">Эта служба настраивает указатель на функцию уведомления о получении с помощью функции обратного вызова, заданной приложением.</span><span class="sxs-lookup"><span data-stu-id="d7262-2652">This service configures the receive notify function pointer with the callback function specified by the application.</span></span> <span data-ttu-id="d7262-2653">Эта функция обратного вызова затем вызывается при получении одного пакета в сокете или нескольких.</span><span class="sxs-lookup"><span data-stu-id="d7262-2653">This callback function is then called whenever one or more packets are received on the socket.</span></span> <span data-ttu-id="d7262-2654">Если задан указатель NX_NULL, функция уведомления отключена.</span><span class="sxs-lookup"><span data-stu-id="d7262-2654">If a NX_NULL pointer is supplied, the notify function is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2655">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2655">Parameters</span></span>

- <span data-ttu-id="d7262-2656">**socket_ptr**: указатель на сокет TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2656">**socket_ptr** Pointer to the TCP socket.</span></span>
- <span data-ttu-id="d7262-2657">**tcp_receive_notify**: указатель на функцию обратного вызова приложения, вызываемую при получении одного пакета в сокете или нескольких.</span><span class="sxs-lookup"><span data-stu-id="d7262-2657">**tcp_receive_notify** Application callback function pointer that is called when one or more packets are received on the socket.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2658">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2658">Return Values</span></span>

- <span data-ttu-id="d7262-2659">**NX_SUCCESS** (0x00) — успешное уведомление о получении.</span><span class="sxs-lookup"><span data-stu-id="d7262-2659">**NX_SUCCESS** (0x00) Successful socket receive notify.</span></span>
- <span data-ttu-id="d7262-2660">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2660">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-2661">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2661">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2662">**NX_NOT_ENABLED** (0x14) — функция TCP не включена.</span><span class="sxs-lookup"><span data-stu-id="d7262-2662">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2663">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2663">Allowed From</span></span>

<span data-ttu-id="d7262-2664">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2664">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2665">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2665">Preemption Possible</span></span>

<span data-ttu-id="d7262-2666">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2666">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2667">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2667">Example</span></span>

```C
/* Setup a receive packet callback function for the "client_socket"
socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever one or more packets are received for
    "client_socket". */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2668">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2668">See Also</span></span>

- <span data-ttu-id="d7262-2669">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-2669">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-2670">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="d7262-2670">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="d7262-2671">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2671">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="d7262-2672">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-2672">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="d7262-2673">nx_tcp_socket_peer_info_get, nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="d7262-2673">nx_tcp_socket_peer_info_get, nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="d7262-2674">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="d7262-2674">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="d7262-2675">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="d7262-2675">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_send"></a><span data-ttu-id="d7262-2676">nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="d7262-2676">nx_tcp_socket_send</span></span>

<span data-ttu-id="d7262-2677">Отправка данных через сокет TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2677">Send data through a TCP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2678">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2678">Prototype</span></span>

```C
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d7262-2679">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2679">Description</span></span>

<span data-ttu-id="d7262-2680">Эта служба отправляет данные TCP через подключенный ранее сокет TCP.</span><span class="sxs-lookup"><span data-stu-id="d7262-2680">This service sends TCP data through a previously connected TCP socket.</span></span> <span data-ttu-id="d7262-2681">Если последний объявленный размер окна получателя меньше, чем этот запрос, служба при необходимости приостанавливает выполнение в соответствии с указанным параметром ожидания.</span><span class="sxs-lookup"><span data-stu-id="d7262-2681">If the receiver's last advertised window size is less than this request, the service optionally suspends based on the wait option specified.</span></span> <span data-ttu-id="d7262-2682">Эта служба гарантирует, что на уровень IP будут отправлены пакеты данных объемом не более MSS.</span><span class="sxs-lookup"><span data-stu-id="d7262-2682">This service guarantees that no packet data larger than MSS is sent to the IP layer.</span></span>

<span data-ttu-id="d7262-2683">*Если не возвращается ошибка, приложение не должно освобождать пакет после этого вызова. Это приведет к непредсказуемым результатам, так как сетевой драйвер также попытается освободить пакет после передачи.*</span><span class="sxs-lookup"><span data-stu-id="d7262-2683">*Unless an error is returned, the application should not release the packet after this call. Doing so will cause unpredictable results because the network driver will also try to release the packet after transmission.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2684">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2684">Parameters</span></span>

- <span data-ttu-id="d7262-2685">**socket_ptr**: указатель на ранее подключенный экземпляр сокета TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2685">**socket_ptr** Pointer to previously connected TCP socket instance.</span></span>
- <span data-ttu-id="d7262-2686">**packet_ptr**: указатель на пакет данных TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2686">**packet_ptr** TCP data packet pointer.</span></span>
- <span data-ttu-id="d7262-2687">**wait_option** определяет поведение службы в случае, если запрос превышает размер окна получателя</span><span class="sxs-lookup"><span data-stu-id="d7262-2687">**wait_option** Defines how the service behaves if the request is greater than the window size of the receiver.</span></span> <span data-ttu-id="d7262-2688">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d7262-2688">The wait options are defined as follows:</span></span>
- <span data-ttu-id="d7262-2689">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-2689">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="d7262-2690">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-2690">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="d7262-2691">Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d7262-2691">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2692">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2692">Return Values</span></span>

- <span data-ttu-id="d7262-2693">**NX_SUCCESS** (0x00) — сокет успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2693">**NX_SUCCESS** (0x00) Successful socket send.</span></span>
- <span data-ttu-id="d7262-2694">**NX_NOT_BOUND** (0x24) — сокет не привязан ни к одному порту.</span><span class="sxs-lookup"><span data-stu-id="d7262-2694">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="d7262-2695">**NX_NO_INTERFACE_ADDRESS** (0x50) — не найден подходящий исходящий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d7262-2695">**NX_NO_INTERFACE_ADDRESS** (0x50) No suitable outgoing interface found.</span></span>
- <span data-ttu-id="d7262-2696">**NX_NOT_CONNECTED** (0x38) — сокет больше не подключен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2696">**NX_NOT_CONNECTED** (0x38) Socket is no longer connected.</span></span>
- <span data-ttu-id="d7262-2697">**NX_WINDOW_OVERFLOW** (0x39) — запрос больше объявленного размера окна получателя в байтах.</span><span class="sxs-lookup"><span data-stu-id="d7262-2697">**NX_WINDOW_OVERFLOW** (0x39) Request is greater than receiver’s advertised window size in bytes.</span></span>
- <span data-ttu-id="d7262-2698">**NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="d7262-2698">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="d7262-2699">**NX_INVALID_PACKET** (0x12) — пакет не выделен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2699">**NX_INVALID_PACKET** (0x12) Packet is not allocated.</span></span>
- <span data-ttu-id="d7262-2700">**NX_TX_QUEUE_DEPTH** (0x49) — достигнута максимальная глубина очереди передачи.</span><span class="sxs-lookup"><span data-stu-id="d7262-2700">**NX_TX_QUEUE_DEPTH** (0x49) Maximum transmit queue depth has been reached.</span></span>
- <span data-ttu-id="d7262-2701">**NX_OVERFLOW** (0x03) — недопустимый указатель для добавления пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2701">**NX_OVERFLOW** (0x03) Packet append pointer is invalid.</span></span>
- <span data-ttu-id="d7262-2702">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2702">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-2703">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2703">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2704">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2704">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="d7262-2705">**NX_UNDERFLOW** (0x02) — недопустимый указатель префикса пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2705">**NX_UNDERFLOW** (0x02) Packet prepend pointer is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2706">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2706">Allowed From</span></span>

<span data-ttu-id="d7262-2707">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2707">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2708">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2708">Preemption Possible</span></span>

<span data-ttu-id="d7262-2709">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2709">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2710">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2710">Example</span></span>

```C
/* Send a packet out on the previously created and connected TCP
    socket. If the receive window on the other side of the connection
    is less than the packet size, wait 200 timer ticks before giving up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2711">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2711">See Also</span></span>

- <span data-ttu-id="d7262-2712">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2712">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="d7262-2713">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-2713">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="d7262-2714">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2714">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="d7262-2715">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="d7262-2715">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="d7262-2716">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="d7262-2716">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="d7262-2717">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="d7262-2717">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="d7262-2718">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2718">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-2719">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-2719">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="d7262-2720">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-2720">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_state_wait</span></span>

### <a name="nx_tcp_socket_state_wait"></a><span data-ttu-id="d7262-2721">nx_tcp_socket_state_wait</span><span class="sxs-lookup"><span data-stu-id="d7262-2721">nx_tcp_socket_state_wait</span></span>

<span data-ttu-id="d7262-2722">Ожидание перехода сокета TCP в определенное состояние</span><span class="sxs-lookup"><span data-stu-id="d7262-2722">Wait for TCP socket to enter specific state</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2723">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2723">Prototype</span></span>

```C
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state, 
    ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="d7262-2724">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2724">Description</span></span>

<span data-ttu-id="d7262-2725">Эта служба ожидает перехода сокета в требуемое состояние.</span><span class="sxs-lookup"><span data-stu-id="d7262-2725">This service waits for the socket to enter the desired state.</span></span> <span data-ttu-id="d7262-2726">Если сокет не находится в нужном состоянии, служба приостанавливает выполнение в соответствии с указанным параметром ожидания.</span><span class="sxs-lookup"><span data-stu-id="d7262-2726">If the socket is not in the desired state, the service suspends according to the supplied wait option.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2727">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2727">Parameters</span></span>

- <span data-ttu-id="d7262-2728">**socket_ptr**: указатель на ранее подключенный экземпляр сокета TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2728">**socket_ptr** Pointer to previously connected TCP socket instance.</span></span>
- <span data-ttu-id="d7262-2729">**desired_state**: требуемое состояние TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2729">**desired_state** Desired TCP state.</span></span> <span data-ttu-id="d7262-2730">Допустимые состояния сокета TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2730">Valid TCP socket states are defined as follows:</span></span>
- <span data-ttu-id="d7262-2731">NX_TCP_CLOSED (0x01)</span><span class="sxs-lookup"><span data-stu-id="d7262-2731">NX_TCP_CLOSED (0x01)</span></span>
- <span data-ttu-id="d7262-2732">NX_TCP_LISTEN_STATE (0x02)</span><span class="sxs-lookup"><span data-stu-id="d7262-2732">NX_TCP_LISTEN_STATE (0x02)</span></span>
- <span data-ttu-id="d7262-2733">NX_TCP_SYN_SENT (0x03)</span><span class="sxs-lookup"><span data-stu-id="d7262-2733">NX_TCP_SYN_SENT (0x03)</span></span>
- <span data-ttu-id="d7262-2734">NX_TCP_SYN_RECEIVED (0x04)</span><span class="sxs-lookup"><span data-stu-id="d7262-2734">NX_TCP_SYN_RECEIVED (0x04)</span></span>
- <span data-ttu-id="d7262-2735">NX_TCP_ESTABLISHED (0x05)</span><span class="sxs-lookup"><span data-stu-id="d7262-2735">NX_TCP_ESTABLISHED (0x05)</span></span>
- <span data-ttu-id="d7262-2736">NX_TCP_CLOSE_WAIT (0x06)</span><span class="sxs-lookup"><span data-stu-id="d7262-2736">NX_TCP_CLOSE_WAIT (0x06)</span></span>
- <span data-ttu-id="d7262-2737">NX_TCP_FIN_WAIT_1 (0x07)</span><span class="sxs-lookup"><span data-stu-id="d7262-2737">NX_TCP_FIN_WAIT_1 (0x07)</span></span>
- <span data-ttu-id="d7262-2738">NX_TCP_FIN_WAIT_2 (0x08)</span><span class="sxs-lookup"><span data-stu-id="d7262-2738">NX_TCP_FIN_WAIT_2 (0x08)</span></span>
- <span data-ttu-id="d7262-2739">NX_TCP_CLOSING (0x09)</span><span class="sxs-lookup"><span data-stu-id="d7262-2739">NX_TCP_CLOSING (0x09)</span></span>
- <span data-ttu-id="d7262-2740">NX_TCP_TIMED_WAIT (0x0A)</span><span class="sxs-lookup"><span data-stu-id="d7262-2740">NX_TCP_TIMED_WAIT (0x0A)</span></span>
- <span data-ttu-id="d7262-2741">NX_TCP_LAST_ACK (0x0B)</span><span class="sxs-lookup"><span data-stu-id="d7262-2741">NX_TCP_LAST_ACK (0x0B)</span></span>
- <span data-ttu-id="d7262-2742">**wait_option** определяет поведение службы в случае, если запрошенное состояние отсутствует</span><span class="sxs-lookup"><span data-stu-id="d7262-2742">**wait_option** Defines how the service behaves if the requested state is not present.</span></span> <span data-ttu-id="d7262-2743">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d7262-2743">The wait options are defined as follows:</span></span>
- <span data-ttu-id="d7262-2744">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-2744">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="d7262-2745">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-2745">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="d7262-2746">Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d7262-2746">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2747">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2747">Return Values</span></span>
- <span data-ttu-id="d7262-2748">**NX_SUCCESS** (0x00) — ожидание состояния успешно завершено.</span><span class="sxs-lookup"><span data-stu-id="d7262-2748">**NX_SUCCESS** (0x00) Successful state wait.</span></span>
- <span data-ttu-id="d7262-2749">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2749">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-2750">**NX_NOT_SUCCESSFUL** (0x43) — состояние отсутствует в течение указанного времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="d7262-2750">**NX_NOT_SUCCESSFUL** (0x43) State not present within the specified wait time.</span></span>
- <span data-ttu-id="d7262-2751">**NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="d7262-2751">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="d7262-2752">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2752">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2753">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2753">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="d7262-2754">**NX_OPTION_ERROR** (0x0A) — требуемое состояние сокета недопустимо.</span><span class="sxs-lookup"><span data-stu-id="d7262-2754">**NX_OPTION_ERROR** (0x0A) The desired socket state is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2755">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2755">Allowed From</span></span>

<span data-ttu-id="d7262-2756">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2756">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2757">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2757">Preemption Possible</span></span>

<span data-ttu-id="d7262-2758">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2758">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2759">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2759">Example</span></span>

```C
/* Wait 300 timer ticks for the previously created socket to enter
    the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
    NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
    state! */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2760">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2760">See Also</span></span>

- <span data-ttu-id="d7262-2761">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2761">nx_tcp_client_socket_bind, nx_tcp_client_socket_connect,</span></span>
- <span data-ttu-id="d7262-2762">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-2762">nx_tcp_client_socket_port_get, nx_tcp_client_socket_unbind,</span></span>
- <span data-ttu-id="d7262-2763">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2763">nx_tcp_enable, nx_tcp_free_port_find, nx_tcp_info_get,</span></span>
- <span data-ttu-id="d7262-2764">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span><span class="sxs-lookup"><span data-stu-id="d7262-2764">nx_tcp_server_socket_accept, nx_tcp_server_socket_listen,</span></span>
- <span data-ttu-id="d7262-2765">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span><span class="sxs-lookup"><span data-stu-id="d7262-2765">nx_tcp_server_socket_relisten, nx_tcp_server_socket_unaccept,</span></span>
- <span data-ttu-id="d7262-2766">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="d7262-2766">nx_tcp_server_socket_unlisten, nx_tcp_socket_bytes_available,</span></span>
- <span data-ttu-id="d7262-2767">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span><span class="sxs-lookup"><span data-stu-id="d7262-2767">nx_tcp_socket_create, nx_tcp_socket_delete, nx_tcp_socket_disconnect,</span></span>
- <span data-ttu-id="d7262-2768">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-2768">nx_tcp_socket_info_get, nx_tcp_socket_receive,</span></span>
- <span data-ttu-id="d7262-2769">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span><span class="sxs-lookup"><span data-stu-id="d7262-2769">nx_tcp_socket_receive_queue_max_set, nx_tcp_socket_send</span></span>

## <a name="nx_tcp_socket_timed_wait_callback"></a><span data-ttu-id="d7262-2770">nx_tcp_socket_timed_wait_callback</span><span class="sxs-lookup"><span data-stu-id="d7262-2770">nx_tcp_socket_timed_wait_callback</span></span>

<span data-ttu-id="d7262-2771">Установка обратного вызова для состояния ожидания с привязкой ко времени</span><span class="sxs-lookup"><span data-stu-id="d7262-2771">Install callback for timed wait state</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2772">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2772">Prototype</span></span>

```C
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback) (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="d7262-2773">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2773">Description</span></span>

<span data-ttu-id="d7262-2774">Эта служба регистрирует функцию обратного вызова, которая вызывается, когда сокет TCP находится в состоянии ожидания с привязкой ко времени.</span><span class="sxs-lookup"><span data-stu-id="d7262-2774">This service registers a callback function which is invoked when the TCP socket is in timed wait state.</span></span> <span data-ttu-id="d7262-2775">Чтобы использовать эту службу, необходимо выполнить сборку библиотеки NetX с заданным параметром ***NX_ENABLE_EXTENDED_NOTIFY***.</span><span class="sxs-lookup"><span data-stu-id="d7262-2775">To use this service, the NetX library must be built with the option ***NX_ENABLE_EXTENDED_NOTIFY*** defined.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2776">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2776">Parameters</span></span>

- <span data-ttu-id="d7262-2777">**socket_ptr**: указатель на ранее подключенный экземпляр сокета клиента или сервера</span><span class="sxs-lookup"><span data-stu-id="d7262-2777">**socket_ptr** Pointer to previously connected client or server socket instance.</span></span>
- <span data-ttu-id="d7262-2778">**tcp_timed_wait_callback**: функция обратного вызова для ожидания с привязкой ко времени</span><span class="sxs-lookup"><span data-stu-id="d7262-2778">**tcp_timed_wait_callback** The timed wait callback function</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2779">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2779">Return Values</span></span>

- <span data-ttu-id="d7262-2780">**NX_SUCCESS** (0x00) — сокет функции обратного вызова успешно зарегистрирован.</span><span class="sxs-lookup"><span data-stu-id="d7262-2780">**NX_SUCCESS** (0x00) Successfully registers the callback function socket</span></span>
- <span data-ttu-id="d7262-2781">**NX_NOT_SUPPORTED** (0x4B) — сборка библиотеки NetX выполнена без включенной функции расширенного уведомления.</span><span class="sxs-lookup"><span data-stu-id="d7262-2781">**NX_NOT_SUPPORTED** (0x4B) NetX library is built without the extended notify feature enabled.</span></span>
- <span data-ttu-id="d7262-2782">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2782">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-2783">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2783">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2784">**NX_NOT_ENABLED** (0x14) — функция TCP не включена.</span><span class="sxs-lookup"><span data-stu-id="d7262-2784">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2785">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2785">Allowed From</span></span>

<span data-ttu-id="d7262-2786">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2786">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2787">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2787">Preemption Possible</span></span>

<span data-ttu-id="d7262-2788">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2788">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2789">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2789">Example</span></span>

```C
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a><span data-ttu-id="d7262-2790">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2790">See Also</span></span>

- <span data-ttu-id="d7262-2791">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-2791">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-2792">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="d7262-2792">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="d7262-2793">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2793">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="d7262-2794">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-2794">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="d7262-2795">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="d7262-2795">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="d7262-2796">nx_tcp_socket_transmit_configure,</span><span class="sxs-lookup"><span data-stu-id="d7262-2796">nx_tcp_socket_transmit_configure,</span></span>
- <span data-ttu-id="d7262-2797">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="d7262-2797">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_transmit_configure"></a><span data-ttu-id="d7262-2798">nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="d7262-2798">nx_tcp_socket_transmit_configure</span></span>

<span data-ttu-id="d7262-2799">Настройка параметров передачи для сокета</span><span class="sxs-lookup"><span data-stu-id="d7262-2799">Configure socket's transmit parameters</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2800">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2800">Prototype</span></span>

```C
UINT nx_tcp_socket_transmit_configure(
    NX_TCP_SOCKET *socket_ptr,
    ULONG max_queue_depth,
    ULONG timeout,
    ULONG max_retries,
    ULONG timeout_shift);
```

### <a name="description"></a><span data-ttu-id="d7262-2801">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2801">Description</span></span>

<span data-ttu-id="d7262-2802">Эта служба настраивает различные параметры передачи для указанного сокета TCP.</span><span class="sxs-lookup"><span data-stu-id="d7262-2802">This service configures various transmit parameters of the specified TCP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2803">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2803">Parameters</span></span>

- <span data-ttu-id="d7262-2804">**socket_ptr**: указатель на сокет TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2804">**socket_ptr** Pointer to the TCP socket.</span></span>
- <span data-ttu-id="d7262-2805">**max_queue_depth**: максимальное число пакетов, которое можно поставить в очередь для передачи</span><span class="sxs-lookup"><span data-stu-id="d7262-2805">**max_queue_depth** Maximum number of packets allowed to be queued for transmission.</span></span>
- <span data-ttu-id="d7262-2806">**timeout**: число тактов таймера ThreadX, в течение которого необходимо ожидать подтверждения перед повторной отправкой пакета</span><span class="sxs-lookup"><span data-stu-id="d7262-2806">**timeout** Number of ThreadX timer ticks an ACK is waited for before the packet is sent again.</span></span>
- <span data-ttu-id="d7262-2807">**max_retries**: максимальное допустимое число попыток</span><span class="sxs-lookup"><span data-stu-id="d7262-2807">**max_retries** Maximum number of retries allowed.</span></span>
- <span data-ttu-id="d7262-2808">**timeout_shift**: значение, на которое сдвигается время ожидания для каждой последующей попытки</span><span class="sxs-lookup"><span data-stu-id="d7262-2808">**timeout_shift** Value to shift the timeout for each subsequent retry.</span></span> <span data-ttu-id="d7262-2809">Значение 0 приводит к тому, что время ожидания между последовательными повторными попытками одинаково.</span><span class="sxs-lookup"><span data-stu-id="d7262-2809">A value of 0, results in the same timeout between successive retries.</span></span> <span data-ttu-id="d7262-2810">Значение 1 приводит к удвоению времени ожидания между попытками.</span><span class="sxs-lookup"><span data-stu-id="d7262-2810">A value of 1, doubles the timeout between retries.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2811">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2811">Return Values</span></span>
- <span data-ttu-id="d7262-2812">**NX_SUCCESS** (0x00) — настройка сокета передачи успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="d7262-2812">**NX_SUCCESS** (0x00) Successful transmit socket configure.</span></span>
- <span data-ttu-id="d7262-2813">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2813">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-2814">**NX_OPTION_ERROR** (0x0a) — недопустимый параметр глубины очереди.</span><span class="sxs-lookup"><span data-stu-id="d7262-2814">**NX_OPTION_ERROR** (0x0a) Invalid queue depth option.</span></span>
- <span data-ttu-id="d7262-2815">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2815">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2816">**NX_NOT_ENABLED** (0x14) — функция TCP не включена.</span><span class="sxs-lookup"><span data-stu-id="d7262-2816">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2817">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2817">Allowed From</span></span>

<span data-ttu-id="d7262-2818">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2818">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2819">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2819">Preemption Possible</span></span>

<span data-ttu-id="d7262-2820">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2820">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2821">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2821">Example</span></span>

```C
/* Configure the "client_socket" for a maximum transmit queue depth
    of 12, 100 tick timeouts, a maximum of 20 retries, and a timeout
    double on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,
    12,100,20, 1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
    configured. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2822">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2822">See Also</span></span>

- <span data-ttu-id="d7262-2823">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-2823">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-2824">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="d7262-2824">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="d7262-2825">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2825">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="d7262-2826">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-2826">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="d7262-2827">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="d7262-2827">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="d7262-2828">nx_tcp_socket_timed_wait_callback,</span><span class="sxs-lookup"><span data-stu-id="d7262-2828">nx_tcp_socket_timed_wait_callback,</span></span>
- <span data-ttu-id="d7262-2829">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="d7262-2829">nx_tcp_socket_window_update_notify_set</span></span>

## <a name="nx_tcp_socket_window_update_notify_set"></a><span data-ttu-id="d7262-2830">nx_tcp_socket_window_update_notify_set</span><span class="sxs-lookup"><span data-stu-id="d7262-2830">nx_tcp_socket_window_update_notify_set</span></span>

<span data-ttu-id="d7262-2831">Уведомление приложения об изменении размера окна</span><span class="sxs-lookup"><span data-stu-id="d7262-2831">Notify application of window size updates</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2832">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2832">Prototype</span></span>

```C
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET
    *socket_ptr,
    VOID (*tcp_window_update_notify)
    (NX_TCP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="d7262-2833">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2833">Description</span></span>

<span data-ttu-id="d7262-2834">Эта служба устанавливает подпрограмму обратного вызова для изменения окна сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-2834">This service installs a socket window update callback routine.</span></span> <span data-ttu-id="d7262-2835">Эта подпрограмма вызывается автоматически каждый раз, когда указанный сокет получает пакет, в котором указано увеличить размер окна для удаленного узла.</span><span class="sxs-lookup"><span data-stu-id="d7262-2835">This routine is called automatically whenever the specified socket receives a packet indicating an increase in the window size of the remote host.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2836">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2836">Parameters</span></span>

- <span data-ttu-id="d7262-2837">**socket_ptr**: указатель на ранее созданный сокет TCP</span><span class="sxs-lookup"><span data-stu-id="d7262-2837">**socket_ptr** Pointer to previously created TCP socket.</span></span>
- <span data-ttu-id="d7262-2838">**tcp_window_update_notify**: подпрограмма обратного вызова, вызываемая при изменении размера окна</span><span class="sxs-lookup"><span data-stu-id="d7262-2838">**tcp_window_update_notify** Callback routine to be called when the window size changes.</span></span> <span data-ttu-id="d7262-2839">Значение NULL отключает изменение окна.</span><span class="sxs-lookup"><span data-stu-id="d7262-2839">A value of NULL disables the window change update.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2840">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2840">Return Values</span></span>
- <span data-ttu-id="d7262-2841">**NX_SUCCESS** (0x00) — подпрограмма обратного вызова установлена в сокете.</span><span class="sxs-lookup"><span data-stu-id="d7262-2841">**NX_SUCCESS** (0x00) Callback routine is installed on the socket.</span></span>
- <span data-ttu-id="d7262-2842">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2842">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2843">**NX_PTR_ERROR** (0x07) — недопустимые указатели.</span><span class="sxs-lookup"><span data-stu-id="d7262-2843">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="d7262-2844">**NX_NOT_ENABLED** (0x14) — функция TCP не включена.</span><span class="sxs-lookup"><span data-stu-id="d7262-2844">**NX_NOT_ENABLED** (0x14) TCP feature is not enabled.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="d7262-2845">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2845">Allowed From</span></span>

<span data-ttu-id="d7262-2846">Инициализация, потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2846">Initialization, threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2847">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2847">Preemption Possible</span></span>

<span data-ttu-id="d7262-2848">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2848">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2849">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2849">Example</span></span>

```C
/* Set the function pointer to the windows update callback after creating the
socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
    my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(NX_TCP_SCOCKET *data_socket)
{
    /* Process update on increase TCP transmit socket window size. */
    return;
}
```

### <a name="see-also"></a><span data-ttu-id="d7262-2850">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2850">See Also</span></span>

- <span data-ttu-id="d7262-2851">nx_tcp_enable, nx_tcp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-2851">nx_tcp_enable, nx_tcp_socket_create,</span></span>
- <span data-ttu-id="d7262-2852">nx_tcp_socket_disconnect_complete_notify,</span><span class="sxs-lookup"><span data-stu-id="d7262-2852">nx_tcp_socket_disconnect_complete_notify,</span></span>
- <span data-ttu-id="d7262-2853">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2853">nx_tcp_socket_establish_notify, nx_tcp_socket_mss_get,</span></span>
- <span data-ttu-id="d7262-2854">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span><span class="sxs-lookup"><span data-stu-id="d7262-2854">nx_tcp_socket_mss_peer_get, nx_tcp_socket_mss_set,</span></span>
- <span data-ttu-id="d7262-2855">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="d7262-2855">nx_tcp_socket_peer_info_get, nx_tcp_socket_receive_notify,</span></span>
- <span data-ttu-id="d7262-2856">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure</span><span class="sxs-lookup"><span data-stu-id="d7262-2856">nx_tcp_socket_timed_wait_callback, nx_tcp_socket_transmit_configure</span></span>

## <a name="nx_udp_enable"></a><span data-ttu-id="d7262-2857">nx_udp_enable</span><span class="sxs-lookup"><span data-stu-id="d7262-2857">nx_udp_enable</span></span>

<span data-ttu-id="d7262-2858">Включение компонента UDP в NetX</span><span class="sxs-lookup"><span data-stu-id="d7262-2858">Enable UDP component of NetX</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2859">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2859">Prototype</span></span>

```C
UINT nx_udp_enable(NX_IP *ip_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-2860">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2860">Description</span></span>

<span data-ttu-id="d7262-2861">Эта служба включает компонент UDP в NetX.</span><span class="sxs-lookup"><span data-stu-id="d7262-2861">This service enables the User Datagram Protocol (UDP) component of NetX.</span></span> <span data-ttu-id="d7262-2862">После включения приложение может отправлять и принимать датаграммы UDP.</span><span class="sxs-lookup"><span data-stu-id="d7262-2862">After enabled, UDP datagrams may be sent and received by the application.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2863">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2863">Parameters</span></span>

- <span data-ttu-id="d7262-2864">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-2864">**ip_ptr** Pointer to previously created IP instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2865">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2865">Return Values</span></span>

- <span data-ttu-id="d7262-2866">**NX_SUCCESS** (0x00) — успешное включение UDP.</span><span class="sxs-lookup"><span data-stu-id="d7262-2866">**NX_SUCCESS** (0x00) Successful UDP enable.</span></span>
- <span data-ttu-id="d7262-2867">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-2867">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-2868">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2868">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2869">**NX_ALREADY_ENABLED** (0x15) — этот компонент уже включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2869">**NX_ALREADY_ENABLED** (0x15) This component has already been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2870">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2870">Allowed From</span></span>

<span data-ttu-id="d7262-2871">Инициализация, потоки, таймеры</span><span class="sxs-lookup"><span data-stu-id="d7262-2871">Initialization, threads, timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2872">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2872">Preemption Possible</span></span>

<span data-ttu-id="d7262-2873">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2873">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2874">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2874">Example</span></span>

```C
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
    instance. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2875">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2875">See Also</span></span>

- <span data-ttu-id="d7262-2876">nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract,</span><span class="sxs-lookup"><span data-stu-id="d7262-2876">nx_udp_free_port_find, nx_udp_info_get, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="d7262-2877">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="d7262-2877">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="d7262-2878">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="d7262-2878">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="d7262-2879">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2879">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="d7262-2880">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-2880">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="d7262-2881">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-2881">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="d7262-2882">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-2882">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="d7262-2883">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="d7262-2883">nx_udp_source_extract</span></span>

## <a name="nx_udp_free_port_find"></a><span data-ttu-id="d7262-2884">nx_udp_free_port_find</span><span class="sxs-lookup"><span data-stu-id="d7262-2884">nx_udp_free_port_find</span></span>

<span data-ttu-id="d7262-2885">Поиск следующего доступного UDP-порта</span><span class="sxs-lookup"><span data-stu-id="d7262-2885">Find next available UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2886">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2886">Prototype</span></span>

```C
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-2887">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2887">Description</span></span>

<span data-ttu-id="d7262-2888">Эта служба ищет свободный UDP-порт (без привязки), начиная с указанного приложением номера порта.</span><span class="sxs-lookup"><span data-stu-id="d7262-2888">This service looks for a free UDP port (unbound) starting from the application supplied port number.</span></span> <span data-ttu-id="d7262-2889">Если достигнуто максимальное значение порта 0xFFFF, поиск начинается с самого начала.</span><span class="sxs-lookup"><span data-stu-id="d7262-2889">The search logic will wrap around if the search reaches the maximum port value of 0xFFFF.</span></span> <span data-ttu-id="d7262-2890">Если поиск завершен успешно, свободный порт возвращается в переменной, на которую указывает *free_port_ptr*.</span><span class="sxs-lookup"><span data-stu-id="d7262-2890">If the search is successful, the free port is returned in the variable pointed to by *free_port_ptr*.</span></span>

<span data-ttu-id="d7262-2891">*Если эта служба вызывается из другого потока, она может вернуть тот же порт. Чтобы предотвратить такое состояние гонки, приложение может защитить эту службу и привязку сокета мьютексом.*</span><span class="sxs-lookup"><span data-stu-id="d7262-2891">*This service can be called from another thread and can have the same port returned. To prevent this race condition, the application may wish to place this service and the actual socket bind under the protection of a mutex.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2892">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2892">Parameters</span></span>

- <span data-ttu-id="d7262-2893">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-2893">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-2894">**port**: номер порта, с которого начинается поиск (от 1 до 0xFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-2894">**port** Port number to start search (1 through 0xFFFF).</span></span>
- <span data-ttu-id="d7262-2895">**free_port_ptr**: указатель на место назначения для возвращаемой переменной со свободным портом</span><span class="sxs-lookup"><span data-stu-id="d7262-2895">**free_port_ptr** Pointer to the destination free port return variable.</span></span>


### <a name="return-values"></a><span data-ttu-id="d7262-2896">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2896">Return Values</span></span>

- <span data-ttu-id="d7262-2897">**NX_SUCCESS** (0x00) — поиск свободного порта успешно завершен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2897">**NX_SUCCESS** (0x00) Successful free port find.</span></span>
- <span data-ttu-id="d7262-2898">**NX_NO_FREE_PORTS** (0x45) — нет свободного порта.</span><span class="sxs-lookup"><span data-stu-id="d7262-2898">**NX_NO_FREE_PORTS** (0x45) No free ports found.</span></span>
- <span data-ttu-id="d7262-2899">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-2899">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-2900">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2900">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2901">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2901">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>
- <span data-ttu-id="d7262-2902">**NX_INVALID_PORT** (0x46) — указан недопустимый номер порта.</span><span class="sxs-lookup"><span data-stu-id="d7262-2902">**NX_INVALID_PORT** (0x46) Specified port number is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2903">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2903">Allowed From</span></span>

<span data-ttu-id="d7262-2904">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2904">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2905">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2905">Preemption Possible</span></span>

<span data-ttu-id="d7262-2906">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2906">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2907">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2907">Example</span></span>

```C
/* Locate a free UDP port, starting at port 12, on a previously
    created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
    free UDP port on the IP instance. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2908">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2908">See Also</span></span>

- <span data-ttu-id="d7262-2909">nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract,</span><span class="sxs-lookup"><span data-stu-id="d7262-2909">nx_udp_enable, nx_udp_info_get, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="d7262-2910">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="d7262-2910">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="d7262-2911">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="d7262-2911">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="d7262-2912">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2912">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="d7262-2913">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-2913">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="d7262-2914">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-2914">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="d7262-2915">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-2915">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="d7262-2916">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="d7262-2916">nx_udp_source_extract</span></span>

## <a name="nx_udp_info_get"></a><span data-ttu-id="d7262-2917">nx_udp_info_get</span><span class="sxs-lookup"><span data-stu-id="d7262-2917">nx_udp_info_get</span></span>

<span data-ttu-id="d7262-2918">Получение сведений о действиях UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-2918">Retrieve information about UDP activities</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2919">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2919">Prototype</span></span>

```C
UINT nx_udp_info_get(
    NX_IP *ip_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_invalid_packets,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a><span data-ttu-id="d7262-2920">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2920">Description</span></span>

<span data-ttu-id="d7262-2921">Эта служба получает сведения о действиях протокола UDP для указанного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-2921">This service retrieves information about UDP activities for the specified IP instance.</span></span>

<span data-ttu-id="d7262-2922">*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.</span><span class="sxs-lookup"><span data-stu-id="d7262-2922">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2923">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2923">Parameters</span></span>

- <span data-ttu-id="d7262-2924">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-2924">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-2925">**udp_packets_sent**: указатель на место назначения для общего числа отправленных UDP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-2925">**udp_packets_sent** Pointer to destination for the total number of UDP packets sent.</span></span>
- <span data-ttu-id="d7262-2926">**udp_bytes_sent**: указатель на место назначения для общего числа отправленных по UDP байтов</span><span class="sxs-lookup"><span data-stu-id="d7262-2926">**udp_bytes_sent** Pointer to destination for the total number of UDP bytes sent.</span></span>
- <span data-ttu-id="d7262-2927">**udp_packets_received**: указатель на место назначения для общего числа полученных UDP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-2927">**udp_packets_received** Pointer to destination of the total number of UDP packets received.</span></span>
- <span data-ttu-id="d7262-2928">**udp_bytes_received**: указатель на место назначения для общего числа полученных по UDP байтов</span><span class="sxs-lookup"><span data-stu-id="d7262-2928">**udp_bytes_received** Pointer to destination of the total number of UDP bytes received.</span></span>
- <span data-ttu-id="d7262-2929">**udp_invalid_packets**: указатель на место назначения для общего числа недопустимых UDP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-2929">**udp_invalid_packets** Pointer to destination of the total number of invalid UDP packets.</span></span>
- <span data-ttu-id="d7262-2930">**udp_receive_packets_dropped**: указатель на место назначения для общего числа полученных и отброшенных UDP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-2930">**udp_receive_packets_dropped** Pointer to destination of the total number of UDP receive packets dropped.</span></span>
- <span data-ttu-id="d7262-2931">**udp_checksum_errors**: указатель на место назначения для общего числа UDP-пакетов с ошибками контрольной суммы</span><span class="sxs-lookup"><span data-stu-id="d7262-2931">**udp_checksum_errors** Pointer to destination of the total number of UDP packets with checksum errors.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2932">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2932">Return Values</span></span>

- <span data-ttu-id="d7262-2933">**NX_SUCCESS** (0x00) — успешное получение сведений UDP.</span><span class="sxs-lookup"><span data-stu-id="d7262-2933">**NX_SUCCESS** (0x00) Successful UDP information retrieval.</span></span>
- <span data-ttu-id="d7262-2934">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-2934">**NX_PTR_ERROR** (0x07) Invalid IP pointer.</span></span>
- <span data-ttu-id="d7262-2935">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2935">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-2936">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-2936">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="d7262-2937">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2937">Allowed From</span></span>

<span data-ttu-id="d7262-2938">Инициализация, потоки, таймеры</span><span class="sxs-lookup"><span data-stu-id="d7262-2938">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2939">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2939">Preemption Possible</span></span>

<span data-ttu-id="d7262-2940">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2940">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2941">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2941">Example</span></span>

```C
/* Retrieve UDP information from previously created IP Instance ip_0. */
status = nx_udp_info_get(&ip_0, &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_invalid_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP information was retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2942">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2942">See Also</span></span>

- <span data-ttu-id="d7262-2943">nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract,</span><span class="sxs-lookup"><span data-stu-id="d7262-2943">nx_udp_enable, nx_udp_free_port_find, nx_udp_packet_info_extract,</span></span>
- <span data-ttu-id="d7262-2944">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="d7262-2944">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="d7262-2945">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="d7262-2945">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="d7262-2946">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2946">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="d7262-2947">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-2947">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="d7262-2948">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-2948">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="d7262-2949">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-2949">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="d7262-2950">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="d7262-2950">nx_udp_source_extract</span></span>

## <a name="nx_udp_packet_info_extract"></a><span data-ttu-id="d7262-2951">nx_udp_packet_info_extract</span><span class="sxs-lookup"><span data-stu-id="d7262-2951">nx_udp_packet_info_extract</span></span>

<span data-ttu-id="d7262-2952">Извлечение параметров сети из UDP-пакета</span><span class="sxs-lookup"><span data-stu-id="d7262-2952">Extract network parameters from UDP packet</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2953">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2953">Prototype</span></span>

```C
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```

### <a name="description"></a><span data-ttu-id="d7262-2954">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2954">Description</span></span>

<span data-ttu-id="d7262-2955">Эта служба извлекает параметры сети, такие как IP-адрес, номер порта однорангового узла, тип протокола (всегда возвращается тип UDP) из пакета, полученного через входящий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d7262-2955">This service extracts network parameters, such as IP address, peer port number, protocol type (this service always returns UDP type) from a packet received on an incoming interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2956">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2956">Parameters</span></span>

- <span data-ttu-id="d7262-2957">**packet_ptr**: указатель на пакет</span><span class="sxs-lookup"><span data-stu-id="d7262-2957">**packet_ptr** Pointer to packet.</span></span>
- <span data-ttu-id="d7262-2958">**ip_address**: указатель на IP-адрес отправителя</span><span class="sxs-lookup"><span data-stu-id="d7262-2958">**ip_address** Pointer to sender IP address.</span></span>
- <span data-ttu-id="d7262-2959">**protocol**: указатель на протокол (UDP)</span><span class="sxs-lookup"><span data-stu-id="d7262-2959">**protocol** Pointer to protocol (UDP).</span></span>
- <span data-ttu-id="d7262-2960">**port**: указатель на номер порта отправителя</span><span class="sxs-lookup"><span data-stu-id="d7262-2960">**port** Pointer to sender’s port number.</span></span>
- <span data-ttu-id="d7262-2961">**interface_index**: указатель на индекс интерфейса приема</span><span class="sxs-lookup"><span data-stu-id="d7262-2961">**interface_index** Pointer to receiving interface index.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2962">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2962">Return Values</span></span>

- <span data-ttu-id="d7262-2963">**NX_SUCCESS** (0x00) — данные интерфейса пакета успешно извлечены.</span><span class="sxs-lookup"><span data-stu-id="d7262-2963">**NX_SUCCESS** (0x00) Packet interface data successfully extracted.</span></span>
- <span data-ttu-id="d7262-2964">**NX_INVALID_PACKET** (0x12) — пакет не содержит IP-кадр.</span><span class="sxs-lookup"><span data-stu-id="d7262-2964">**NX_INVALID_PACKET** (0x12) Packet does not contain IP frame.</span></span>
- <span data-ttu-id="d7262-2965">**NX_PTR_ERROR** (0x07) — недопустимые входные данные указателя.</span><span class="sxs-lookup"><span data-stu-id="d7262-2965">**NX_PTR_ERROR** (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="d7262-2966">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-2966">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-2967">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-2967">Allowed From</span></span>

<span data-ttu-id="d7262-2968">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-2968">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-2969">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-2969">Preemption Possible</span></span>

<span data-ttu-id="d7262-2970">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-2970">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-2971">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-2971">Example</span></span>

```C
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract( packet_ptr, &ip_address,
    &protocol, &port,
    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-2972">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-2972">See Also</span></span>

- <span data-ttu-id="d7262-2973">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2973">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="d7262-2974">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="d7262-2974">nx_udp_socket_bind, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="d7262-2975">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="d7262-2975">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="d7262-2976">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-2976">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="d7262-2977">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-2977">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="d7262-2978">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-2978">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="d7262-2979">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-2979">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="d7262-2980">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="d7262-2980">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_bind"></a><span data-ttu-id="d7262-2981">nx_udp_socket_bind</span><span class="sxs-lookup"><span data-stu-id="d7262-2981">nx_udp_socket_bind</span></span>

<span data-ttu-id="d7262-2982">Привязка сокета UDP к UDP-порту</span><span class="sxs-lookup"><span data-stu-id="d7262-2982">Bind UDP socket to UDP port</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-2983">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-2983">Prototype</span></span>

```C
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d7262-2984">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-2984">Description</span></span>

<span data-ttu-id="d7262-2985">Эта служба привязывает ранее созданный сокет UDP к указанному UDP-порту.</span><span class="sxs-lookup"><span data-stu-id="d7262-2985">This service binds the previously created UDP socket to the specified UDP port.</span></span> <span data-ttu-id="d7262-2986">Допустимый диапазон сокетов UDP — от 0 до 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="d7262-2986">Valid UDP sockets range from 0 through 0xFFFF.</span></span> <span data-ttu-id="d7262-2987">Если запрошенный номер порта привязан к другому сокету, эта служба ожидает в течение указанного времени, пока привязка сокета к номеру порта не будет отменена.</span><span class="sxs-lookup"><span data-stu-id="d7262-2987">If the requested port number is bound to another socket, this service waits for specified period of time for the socket to unbind from the port number.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-2988">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-2988">Parameters</span></span>

- <span data-ttu-id="d7262-2989">**socket_ptr**: указатель на ранее созданный экземпляр сокета UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-2989">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="d7262-2990">**port**: номер порта для привязки (от 1 до 0xFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-2990">**port** Port number to bind to (1 through 0xFFFF).</span></span> <span data-ttu-id="d7262-2991">Если номер порта — NX_ANY_PORT (0x0000), экземпляр IP будет искать следующий свободный порт и использует его для привязки.</span><span class="sxs-lookup"><span data-stu-id="d7262-2991">If port number is NX_ANY_PORT (0x0000), the IP instance will search for the next free port and use that for the binding.</span></span>
- <span data-ttu-id="d7262-2992">**wait_option**: определяет поведение службы в случае, если порт уже привязан к другому сокету</span><span class="sxs-lookup"><span data-stu-id="d7262-2992">**wait_option** Defines how the service behaves if the port is already bound to another socket.</span></span> <span data-ttu-id="d7262-2993">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d7262-2993">The wait options are defined as follows:</span></span>
- <span data-ttu-id="d7262-2994">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-2994">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="d7262-2995">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-2995">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="d7262-2996">Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d7262-2996">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-2997">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-2997">Return Values</span></span>

- <span data-ttu-id="d7262-2998">**NX_SUCCESS** (0x00) — сокет успешно привязан.</span><span class="sxs-lookup"><span data-stu-id="d7262-2998">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="d7262-2999">**NX_ALREADY_BOUND** (0x22) — этот сокет уже привязан к другому порту.</span><span class="sxs-lookup"><span data-stu-id="d7262-2999">**NX_ALREADY_BOUND** (0x22) This socket is already bound to another port.</span></span>
- <span data-ttu-id="d7262-3000">**NX_PORT_UNAVAILABLE** (0x23) — порт уже привязан к другому сокету.</span><span class="sxs-lookup"><span data-stu-id="d7262-3000">**NX_PORT_UNAVAILABLE** (0x23) Port is already bound to a different socket.</span></span>
- <span data-ttu-id="d7262-3001">**NX_NO_FREE_PORTS** (0x45) — нет свободного порта.</span><span class="sxs-lookup"><span data-stu-id="d7262-3001">**NX_NO_FREE_PORTS** (0x45) No free port.</span></span>
- <span data-ttu-id="d7262-3002">**NX_WAIT_ABORTED** (0x1A) — запрошенная приостановка прервана вызовом tx_thread_wait_abort.</span><span class="sxs-lookup"><span data-stu-id="d7262-3002">**NX_WAIT_ABORTED** (0x1A) Requested suspension was aborted by a call to tx_thread_wait_abort.</span></span>
- <span data-ttu-id="d7262-3003">**NX_INVALID_PORT** (0x46) — указан недопустимый порт.</span><span class="sxs-lookup"><span data-stu-id="d7262-3003">**NX_INVALID_PORT** (0x46) Invalid port specified.</span></span>
- <span data-ttu-id="d7262-3004">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-3004">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-3005">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-3005">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-3006">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-3006">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-3007">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-3007">Allowed From</span></span>

<span data-ttu-id="d7262-3008">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-3008">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-3009">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-3009">Preemption Possible</span></span>

<span data-ttu-id="d7262-3010">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-3010">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-3011">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-3011">Example</span></span>

```C
/* Bind the previously created UDP socket to port 12 on the
    previously created IP instance. If the port is already bound,
    wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
    port 12.*/
```

### <a name="see-also"></a><span data-ttu-id="d7262-3012">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-3012">See Also</span></span>

- <span data-ttu-id="d7262-3013">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3013">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="d7262-3014">nx_udp_packet_info_extract, nx_udp_socket_bytes_available,</span><span class="sxs-lookup"><span data-stu-id="d7262-3014">nx_udp_packet_info_extract, nx_udp_socket_bytes_available,</span></span>
- <span data-ttu-id="d7262-3015">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="d7262-3015">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="d7262-3016">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3016">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="d7262-3017">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-3017">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="d7262-3018">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-3018">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="d7262-3019">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-3019">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="d7262-3020">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="d7262-3020">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_bytes_available"></a><span data-ttu-id="d7262-3021">nx_udp_socket_bytes_available</span><span class="sxs-lookup"><span data-stu-id="d7262-3021">nx_udp_socket_bytes_available</span></span>

<span data-ttu-id="d7262-3022">Получает число байтов, доступных для извлечения</span><span class="sxs-lookup"><span data-stu-id="d7262-3022">Retrieves number of bytes available for retrieval</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-3023">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-3023">Prototype</span></span>

```C
UINT nx_udp_socket_bytes_available(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```

### <a name="description"></a><span data-ttu-id="d7262-3024">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-3024">Description</span></span>

<span data-ttu-id="d7262-3025">Эта служба получает число байтов, доступных для приема в указанном сокете UDP.</span><span class="sxs-lookup"><span data-stu-id="d7262-3025">This service retrieves number of bytes available for reception in the specified UDP socket.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-3026">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-3026">Parameters</span></span>

- <span data-ttu-id="d7262-3027">**socket_ptr**: указатель на ранее созданный сокет UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3027">**socket_ptr** Pointer to previously created UDP socket.</span></span>
- <span data-ttu-id="d7262-3028">**bytes_available**: указатель на место назначения для доступных байтов</span><span class="sxs-lookup"><span data-stu-id="d7262-3028">**bytes_available** Pointer to destination for bytes available.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-3029">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-3029">Return Values</span></span>

- <span data-ttu-id="d7262-3030">**NX_SUCCESS** (0x00) — успешное получение доступных байтов.</span><span class="sxs-lookup"><span data-stu-id="d7262-3030">**NX_SUCCESS** (0x00) Successful bytes available retrieval.</span></span>
- <span data-ttu-id="d7262-3031">**NX_NOT_SUCCESSFUL** (0x43) — сокет не привязан к порту.</span><span class="sxs-lookup"><span data-stu-id="d7262-3031">**NX_NOT_SUCCESSFUL** (0x43) Socket not bound to a port.</span></span>
- <span data-ttu-id="d7262-3032">**NX_PTR_ERROR** (0x07) — недопустимые указатели.</span><span class="sxs-lookup"><span data-stu-id="d7262-3032">**NX_PTR_ERROR** (0x07) Invalid pointers.</span></span>
- <span data-ttu-id="d7262-3033">**NX_NOT_ENABLED** (0x14) — функция UDP не включена.</span><span class="sxs-lookup"><span data-stu-id="d7262-3033">**NX_NOT_ENABLED** (0x14) UDP feature is not enabled.</span></span>
- <span data-ttu-id="d7262-3034">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-3034">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-3035">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-3035">Allowed From</span></span>

<span data-ttu-id="d7262-3036">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-3036">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-3037">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-3037">Preemption Possible</span></span>

<span data-ttu-id="d7262-3038">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-3038">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-3039">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-3039">Example</span></span>

```C
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket, &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
    retrieved.*/
```

### <a name="see-also"></a><span data-ttu-id="d7262-3040">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-3040">See Also</span></span>

- <span data-ttu-id="d7262-3041">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3041">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="d7262-3042">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="d7262-3042">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="d7262-3043">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span><span class="sxs-lookup"><span data-stu-id="d7262-3043">nx_udp_socket_checksum_disable, nx_udp_socket_checksum_enable,</span></span>
- <span data-ttu-id="d7262-3044">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3044">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="d7262-3045">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-3045">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="d7262-3046">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-3046">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="d7262-3047">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-3047">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="d7262-3048">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="d7262-3048">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_checksum_disable"></a><span data-ttu-id="d7262-3049">nx_udp_socket_checksum_disable</span><span class="sxs-lookup"><span data-stu-id="d7262-3049">nx_udp_socket_checksum_disable</span></span>

<span data-ttu-id="d7262-3050">Отключение контрольной суммы для сокета UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3050">Disable checksum for UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-3051">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-3051">Prototype</span></span>

```C
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-3052">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-3052">Description</span></span>

<span data-ttu-id="d7262-3053">Эта служба отключает логику проверки контрольной суммы при отправке и получении пакетов через указанный сокет UDP.</span><span class="sxs-lookup"><span data-stu-id="d7262-3053">This service disables the checksum logic for sending and receiving packets on the specified UDP socket.</span></span> <span data-ttu-id="d7262-3054">Если логика проверки контрольной суммы отключена, в поле контрольной суммы заголовка UDP загружается значение ноль для всех пакетов, отправляемых через этот сокет.</span><span class="sxs-lookup"><span data-stu-id="d7262-3054">When the checksum logic is disabled, a value of zero is loaded into the UDP header's checksum field for all packets sent through this socket.</span></span> <span data-ttu-id="d7262-3055">Нулевое значение контрольной суммы в заголовке UDP сообщает получателю о том, что контрольная сумма для этого пакета не вычисляется.</span><span class="sxs-lookup"><span data-stu-id="d7262-3055">A zero-value checksum value in the UDP header signals the receiver that checksum is not computed for this packet.</span></span>

<span data-ttu-id="d7262-3056">Обратите внимание, что эта настройка не действует, если при получении и отправке UDP-пакетов определены параметры ***NX_DISABLE_UDP_RX_CHECKSUM** _ и _ *_NX_DISABLE_UDP_TX_CHECKSUM_** соответственно.</span><span class="sxs-lookup"><span data-stu-id="d7262-3056">Also note that this has no effect if ***NX_DISABLE_UDP_RX_CHECKSUM** _ and _ *_NX_DISABLE_UDP_TX_CHECKSUM_** are defined when receiving and sending UDP packets respectively.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-3057">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-3057">Parameters</span></span>

- <span data-ttu-id="d7262-3058">**socket_ptr**: указатель на ранее созданный экземпляр сокета UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3058">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-3059">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-3059">Return Values</span></span>

- <span data-ttu-id="d7262-3060">**NX_SUCCESS** (0x00) — проверка контрольной суммы для сокета успешно отключена.</span><span class="sxs-lookup"><span data-stu-id="d7262-3060">**NX_SUCCESS** (0x00) Successful socket checksum disable.</span></span>
- <span data-ttu-id="d7262-3061">**NX_NOT_BOUND** (0x24) — сокет не привязан.</span><span class="sxs-lookup"><span data-stu-id="d7262-3061">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="d7262-3062">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-3062">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-3063">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-3063">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-3064">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-3064">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-3065">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-3065">Allowed From</span></span>

<span data-ttu-id="d7262-3066">Инициализация, потоки, таймер</span><span class="sxs-lookup"><span data-stu-id="d7262-3066">Initialization, threads, timer</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-3067">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-3067">Preemption Possible</span></span>

<span data-ttu-id="d7262-3068">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-3068">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-3069">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-3069">Example</span></span>

```C
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
    calculated. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-3070">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-3070">See Also</span></span>

- <span data-ttu-id="d7262-3071">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3071">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="d7262-3072">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="d7262-3072">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="d7262-3073">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-3073">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="d7262-3074">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3074">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="d7262-3075">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-3075">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="d7262-3076">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-3076">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="d7262-3077">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-3077">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="d7262-3078">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="d7262-3078">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_checksum_enable"></a><span data-ttu-id="d7262-3079">nx_udp_socket_checksum_enable</span><span class="sxs-lookup"><span data-stu-id="d7262-3079">nx_udp_socket_checksum_enable</span></span>

<span data-ttu-id="d7262-3080">Включение контрольной суммы для сокета UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3080">Enable checksum for UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-3081">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-3081">Prototype</span></span>

```C
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-3082">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-3082">Description</span></span>

<span data-ttu-id="d7262-3083">Эта служба включает логику проверки контрольной суммы при отправке и получении пакетов через указанный сокет UDP.</span><span class="sxs-lookup"><span data-stu-id="d7262-3083">This service enables the checksum logic for sending and receiving packets on the specified UDP socket.</span></span> <span data-ttu-id="d7262-3084">Контрольная сумма охватывает всю область данных UDP, а также псевдозаголовок IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-3084">The checksum covers the entire UDP data area as well as a pseudo IP header.</span></span>

<span data-ttu-id="d7262-3085">Обратите внимание, что эта настройка не действует, если при получении и отправке UDP-пакетов определены параметры **NX_DISABLE_UDP_RX_CHECKSUM** и **NX_DISABLE_UDP_TX_CHECKSUM** соответственно.</span><span class="sxs-lookup"><span data-stu-id="d7262-3085">Also note that this has no effect if **NX_DISABLE_UDP_RX_CHECKSUM** and **NX_DISABLE_UDP_TX_CHECKSUM** are defined when receiving and sending UDP packets respectively.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-3086">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-3086">Parameters</span></span>

- <span data-ttu-id="d7262-3087">**socket_ptr**: указатель на ранее созданный экземпляр сокета UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3087">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-3088">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-3088">Return Values</span></span>

- <span data-ttu-id="d7262-3089">**NX_SUCCESS** (0x00) — проверка контрольной суммы для сокета успешно включена.</span><span class="sxs-lookup"><span data-stu-id="d7262-3089">**NX_SUCCESS** (0x00) Successful socket checksum enable.</span></span>
- <span data-ttu-id="d7262-3090">**NX_NOT_BOUND** (0x24) — сокет не привязан.</span><span class="sxs-lookup"><span data-stu-id="d7262-3090">**NX_NOT_BOUND** (0x24) Socket is not bound.</span></span>
- <span data-ttu-id="d7262-3091">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-3091">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-3092">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-3092">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-3093">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-3093">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-3094">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-3094">Allowed From</span></span>

<span data-ttu-id="d7262-3095">Инициализация, потоки, таймер</span><span class="sxs-lookup"><span data-stu-id="d7262-3095">Initialization, threads, timer</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-3096">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-3096">Preemption Possible</span></span>

<span data-ttu-id="d7262-3097">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-3097">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-3098">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-3098">Example</span></span>

```C
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
    calculated. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-3099">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-3099">See Also</span></span>

- <span data-ttu-id="d7262-3100">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3100">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="d7262-3101">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="d7262-3101">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="d7262-3102">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-3102">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="d7262-3103">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3103">nx_udp_socket_create, nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="d7262-3104">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-3104">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="d7262-3105">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-3105">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="d7262-3106">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-3106">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="d7262-3107">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="d7262-3107">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_create"></a><span data-ttu-id="d7262-3108">nx_udp_socket_create</span><span class="sxs-lookup"><span data-stu-id="d7262-3108">nx_udp_socket_create</span></span>

<span data-ttu-id="d7262-3109">Создание сокета UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3109">Create UDP socket.</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-3110">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-3110">Prototype</span></span>

```C
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, CHAR *name,
    ULONG type_of_service, ULONG fragment,
    UINT time_to_live, ULONG queue_maximum);
```

### <a name="description"></a><span data-ttu-id="d7262-3111">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-3111">Description</span></span>

<span data-ttu-id="d7262-3112">Эта служба создает сокет UDP для указанного экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="d7262-3112">This service creates a UDP socket for the specified IP instance.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-3113">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-3113">Parameters</span></span>

- <span data-ttu-id="d7262-3114">**ip_ptr**: указатель на ранее созданный экземпляр IP</span><span class="sxs-lookup"><span data-stu-id="d7262-3114">**ip_ptr** Pointer to previously created IP instance.</span></span>
- <span data-ttu-id="d7262-3115">**socket_ptr**: указатель на новый управляющий блок сокета UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3115">**socket_ptr** Pointer to new UDP socket control bloc.</span></span>
- <span data-ttu-id="d7262-3116">**name**: имя приложения для этого сокета UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3116">**name** Application name for this UDP socket.</span></span>
- <span data-ttu-id="d7262-3117">**type_of_service** определяет тип службы для передачи. Допустимые значения:</span><span class="sxs-lookup"><span data-stu-id="d7262-3117">**type_of_service** Defines the type of service for the transmission, legal values are as follows:</span></span>
    - <span data-ttu-id="d7262-3118">NX_IP_NORMAL (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-3118">NX_IP_NORMAL (0x00000000)</span></span>
    - <span data-ttu-id="d7262-3119">NX_IP_MIN_DELAY (0x00100000)</span><span class="sxs-lookup"><span data-stu-id="d7262-3119">NX_IP_MIN_DELAY (0x00100000)</span></span>
    - <span data-ttu-id="d7262-3120">NX_IP_MAX_DATA (0x00080000)</span><span class="sxs-lookup"><span data-stu-id="d7262-3120">NX_IP_MAX_DATA (0x00080000)</span></span>
    - <span data-ttu-id="d7262-3121">NX_IP_MAX_RELIABLE (0x00040000)</span><span class="sxs-lookup"><span data-stu-id="d7262-3121">NX_IP_MAX_RELIABLE (0x00040000)</span></span>
    - <span data-ttu-id="d7262-3122">NX_IP_MIN_COST (0x00020000)</span><span class="sxs-lookup"><span data-stu-id="d7262-3122">NX_IP_MIN_COST (0x00020000)</span></span>
- <span data-ttu-id="d7262-3123">**fragment** указывает, разрешена ли фрагментация IP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-3123">**fragment** Specifies whether or not IP fragmenting is allowed.</span></span> <span data-ttu-id="d7262-3124">Если указано значение NX_FRAGMENT_OKAY (0x0), то фрагментация IP-пакетов разрешена.</span><span class="sxs-lookup"><span data-stu-id="d7262-3124">If NX_FRAGMENT_OKAY (0x0) is specified, IP fragmenting is allowed.</span></span> <span data-ttu-id="d7262-3125">Если указано значение NX_DONT_FRAGMENT (0x4000), то фрагментация IP-пакетов отключена.</span><span class="sxs-lookup"><span data-stu-id="d7262-3125">If NX_DONT_FRAGMENT (0x4000) is specified, IP fragmenting is disabled.</span></span>
- <span data-ttu-id="d7262-3126">**time_to_live** задает 8-разрядное значение, определяющее, сколько маршрутизаторов этот пакет может пройти перед тем, как будет отброшен</span><span class="sxs-lookup"><span data-stu-id="d7262-3126">**time_to_live** Specifies the 8-bit value that defines how many routers this packet can pass before being thrown away.</span></span> <span data-ttu-id="d7262-3127">Значение по умолчанию задается в NX_IP_TIME_TO_LIVE.</span><span class="sxs-lookup"><span data-stu-id="d7262-3127">The default value is specified by NX_IP_TIME_TO_LIVE.</span></span>
- <span data-ttu-id="d7262-3128">**queue_maximum** определяет максимальное число датаграмм UDP, которое можно поставить в очередь для этого сокета</span><span class="sxs-lookup"><span data-stu-id="d7262-3128">**queue_maximum** Defines the maximum number of UDP datagrams that can be queued for this socket.</span></span> <span data-ttu-id="d7262-3129">После достижения предельного размера очереди для каждого нового пакета будет освобождаться самый старый UDP-пакет.</span><span class="sxs-lookup"><span data-stu-id="d7262-3129">After the queue limit is reached, for every new packet received the oldest UDP packet is released.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-3130">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-3130">Return Values</span></span>

- <span data-ttu-id="d7262-3131">**NX_SUCCESS** (0x00) — сокет UDP успешно создан.</span><span class="sxs-lookup"><span data-stu-id="d7262-3131">**NX_SUCCESS** (0x00) Successful UDP socket create.</span></span>
- <span data-ttu-id="d7262-3132">**NX_OPTION_ERROR** (0x0A) — недопустимый тип службы, параметр фрагментации или параметр времени существования.</span><span class="sxs-lookup"><span data-stu-id="d7262-3132">**NX_OPTION_ERROR** (0x0A) Invalid type-of-service, fragment, or time-to-live option.</span></span>
- <span data-ttu-id="d7262-3133">**NX_PTR_ERROR** (0x07) — недопустимый указатель IP-адреса или сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-3133">**NX_PTR_ERROR** (0x07) Invalid IP or socket pointer.</span></span>
- <span data-ttu-id="d7262-3134">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-3134">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-3135">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-3135">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-3136">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-3136">Allowed From</span></span>

<span data-ttu-id="d7262-3137">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-3137">Initialization and Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-3138">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-3138">Preemption Possible</span></span>

<span data-ttu-id="d7262-3139">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-3139">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-3140">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-3140">Example</span></span>

```C
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
    NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80, 30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
    is ready for binding. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-3141">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-3141">See Also</span></span>

- <span data-ttu-id="d7262-3142">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3142">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="d7262-3143">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="d7262-3143">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="d7262-3144">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-3144">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="d7262-3145">nx_udp_socket_checksum_enable, nx_udp_socket_delete,</span><span class="sxs-lookup"><span data-stu-id="d7262-3145">nx_udp_socket_checksum_enable, nx_udp_socket_delete,</span></span>
- <span data-ttu-id="d7262-3146">nx_udp_socket_info_get, nx_udp_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3146">nx_udp_socket_info_get, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="d7262-3147">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="d7262-3147">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="d7262-3148">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-3148">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="d7262-3149">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="d7262-3149">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_delete"></a><span data-ttu-id="d7262-3150">nx_udp_socket_delete</span><span class="sxs-lookup"><span data-stu-id="d7262-3150">nx_udp_socket_delete</span></span>

<span data-ttu-id="d7262-3151">Удаление сокета UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3151">Delete UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-3152">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-3152">Prototype</span></span>

```C
UINT nx_udp_socket_delete(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-3153">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-3153">Description</span></span>

<span data-ttu-id="d7262-3154">Эта служба удаляет созданный ранее сокет UDP.</span><span class="sxs-lookup"><span data-stu-id="d7262-3154">This service deletes a previously created UDP socket.</span></span> <span data-ttu-id="d7262-3155">Если сокет привязан к порту, сначала необходимо отменить привязку.</span><span class="sxs-lookup"><span data-stu-id="d7262-3155">If the socket was bound to a port, the socket must be unbound first.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-3156">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-3156">Parameters</span></span>

- <span data-ttu-id="d7262-3157">**socket_ptr**: указатель на ранее созданный экземпляр сокета UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3157">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-3158">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-3158">Return Values</span></span>

- <span data-ttu-id="d7262-3159">**NX_SUCCESS** (0x00) — сокет успешно удален.</span><span class="sxs-lookup"><span data-stu-id="d7262-3159">**NX_SUCCESS** (0x00) Successful socket delete.</span></span>
- <span data-ttu-id="d7262-3160">**NX_STILL_BOUND** (0x42) — сокет все еще привязан.</span><span class="sxs-lookup"><span data-stu-id="d7262-3160">**NX_STILL_BOUND** (0x42) Socket is still bound.</span></span>
- <span data-ttu-id="d7262-3161">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-3161">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-3162">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-3162">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-3163">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-3163">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-3164">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-3164">Allowed From</span></span>

<span data-ttu-id="d7262-3165">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-3165">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-3166">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-3166">Preemption Possible</span></span>

<span data-ttu-id="d7262-3167">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-3167">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-3168">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-3168">Example</span></span>

```C
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
    been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-3169">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-3169">See Also</span></span>

- <span data-ttu-id="d7262-3170">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3170">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="d7262-3171">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="d7262-3171">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="d7262-3172">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-3172">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="d7262-3173">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-3173">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="d7262-3174">nx_udp_socket_info_get, nx_udp_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3174">nx_udp_socket_info_get, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="d7262-3175">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="d7262-3175">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="d7262-3176">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-3176">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="d7262-3177">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="d7262-3177">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_info_get"></a><span data-ttu-id="d7262-3178">nx_udp_socket_info_get</span><span class="sxs-lookup"><span data-stu-id="d7262-3178">nx_udp_socket_info_get</span></span>

<span data-ttu-id="d7262-3179">Получение сведений о действиях сокета UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3179">Retrieve information about UDP socket activities</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-3180">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-3180">Prototype</span></span>

```C
UINT nx_udp_socket_info_get(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_packets_queued,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```

### <a name="description"></a><span data-ttu-id="d7262-3181">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-3181">Description</span></span>

<span data-ttu-id="d7262-3182">Эта служба получает сведения о действиях сокета UDP для указанного экземпляра сокета UDP.</span><span class="sxs-lookup"><span data-stu-id="d7262-3182">This service retrieves information about UDP socket activities for the specified UDP socket instance.</span></span>

<span data-ttu-id="d7262-3183">*Если указатель назначения имеет значение NX_NULL, эта информация не возвращается вызывающему объекту*.</span><span class="sxs-lookup"><span data-stu-id="d7262-3183">*If a destination pointer is NX_NULL, that particular information is not returned to the caller.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-3184">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-3184">Parameters</span></span>

- <span data-ttu-id="d7262-3185">**socket_ptr**: указатель на ранее созданный экземпляр сокета UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3185">**socket_ptr** Pointer to previously-created UDP socket instance.</span></span>
- <span data-ttu-id="d7262-3186">**udp_packets_sent**: указатель на место назначения для общего числа отправленных через сокет UDP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-3186">**udp_packets_sent** Pointer to destination for the total number of UDP packets sent on socket.</span></span>
- <span data-ttu-id="d7262-3187">**udp_bytes_sent**: указатель на место назначения для общего числа отправленных через сокет UDP байтов</span><span class="sxs-lookup"><span data-stu-id="d7262-3187">**udp_bytes_sent** Pointer to destination for the total number of UDP bytes sent on socket.</span></span>
- <span data-ttu-id="d7262-3188">**udp_packets_received**: указатель на место назначения для общего числа полученных через сокет UDP-пакетов</span><span class="sxs-lookup"><span data-stu-id="d7262-3188">**udp_packets_received** Pointer to destination of the total number of UDP packets received on socket.</span></span>
- <span data-ttu-id="d7262-3189">**udp_bytes_received**: указатель на место назначения для общего числа полученных через сокет UDP байтов</span><span class="sxs-lookup"><span data-stu-id="d7262-3189">**udp_bytes_received** Pointer to destination of the total number of UDP bytes received on socket.</span></span>
- <span data-ttu-id="d7262-3190">**udp_packets_queued** Указатель на место назначения для общего числа UDP-пакетов, поставленных в очередь в сокете.</span><span class="sxs-lookup"><span data-stu-id="d7262-3190">**udp_packets_queued** Pointer to destination of the total number of queued UDP packets on socket.</span></span>
- <span data-ttu-id="d7262-3191">**udp_receive_packets_dropped**: указатель на место назначения для общего числа UDP-пакетов, полученных и отброшенных для сокета из-за превышения размера очереди</span><span class="sxs-lookup"><span data-stu-id="d7262-3191">**udp_receive_packets_dropped** Pointer to destination of the total number of UDP receive packets dropped for socket due to queue size being exceeded.</span></span>
- <span data-ttu-id="d7262-3192">**udp_checksum_errors**: указатель на место назначения для общего числа UDP-пакетов с ошибками контрольной суммы в сокете</span><span class="sxs-lookup"><span data-stu-id="d7262-3192">**udp_checksum_errors** Pointer to destination of the total number of UDP packets with checksum errors on socket.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-3193">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-3193">Return Values</span></span>

- <span data-ttu-id="d7262-3194">**NX_SUCCESS** (0x00) — успешное получение сведений о сокете UDP.</span><span class="sxs-lookup"><span data-stu-id="d7262-3194">**NX_SUCCESS** (0x00) Successful UDP socket information retrieval.</span></span>
- <span data-ttu-id="d7262-3195">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-3195">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-3196">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-3196">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-3197">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-3197">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-3198">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-3198">Allowed From</span></span>

<span data-ttu-id="d7262-3199">Инициализация, потоки, таймеры</span><span class="sxs-lookup"><span data-stu-id="d7262-3199">Initialization, threads, and timers</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-3200">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-3200">Preemption Possible</span></span>

<span data-ttu-id="d7262-3201">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-3201">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-3202">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-3202">Example</span></span>

```C
/* Retrieve UDP socket information from socket 0.*/
status = nx_udp_socket_info_get(&socket_0,
    &udp_packets_sent,
    &udp_bytes_sent,
    &udp_packets_received,
    &udp_bytes_received,
    &udp_queued_packets,
    &udp_receive_packets_dropped,
    &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP socket information was retrieved.*/
```

### <a name="see-also"></a><span data-ttu-id="d7262-3203">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-3203">See Also</span></span>

- <span data-ttu-id="d7262-3204">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3204">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="d7262-3205">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="d7262-3205">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="d7262-3206">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-3206">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="d7262-3207">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-3207">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="d7262-3208">nx_udp_socket_delete, nx_udp_socket_port_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3208">nx_udp_socket_delete, nx_udp_socket_port_get,</span></span>
- <span data-ttu-id="d7262-3209">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="d7262-3209">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="d7262-3210">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-3210">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="d7262-3211">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="d7262-3211">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_port_get"></a><span data-ttu-id="d7262-3212">nx_udp_socket_port_get</span><span class="sxs-lookup"><span data-stu-id="d7262-3212">nx_udp_socket_port_get</span></span>

<span data-ttu-id="d7262-3213">Выбор номера порта, привязанного к сокету UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3213">Pick up port number bound to UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-3214">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-3214">Prototype</span></span>

```C
UINT nx_udp_socket_port_get(NX_UDP_SOCKET *socket_ptr, UINT *port_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-3215">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-3215">Description</span></span>

<span data-ttu-id="d7262-3216">Эта служба получает номер порта, связанного с сокетом, что может быть полезно при поиске порта, выделенного NetX, если во время привязки сокета было указано значение NX_ANY_PORT.</span><span class="sxs-lookup"><span data-stu-id="d7262-3216">This service retrieves the port number associated with the socket, which is useful to find the port allocated by NetX in situations where the NX_ANY_PORT was specified at the time the socket was bound.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-3217">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-3217">Parameters</span></span>

- <span data-ttu-id="d7262-3218">**socket_ptr**: указатель на ранее созданный экземпляр сокета UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3218">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="d7262-3219">**port_ptr**: указатель на место назначения для возвращаемого номера порта</span><span class="sxs-lookup"><span data-stu-id="d7262-3219">**port_ptr** Pointer to destination for the return port number.</span></span> <span data-ttu-id="d7262-3220">Допустимые номера портов — от 1 до 0xFFFF.</span><span class="sxs-lookup"><span data-stu-id="d7262-3220">Valid port numbers are (1- 0xFFFF).</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-3221">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-3221">Return Values</span></span>

- <span data-ttu-id="d7262-3222">**NX_SUCCESS** (0x00) — сокет успешно привязан.</span><span class="sxs-lookup"><span data-stu-id="d7262-3222">**NX_SUCCESS** (0x00) Successful socket bind.</span></span>
- <span data-ttu-id="d7262-3223">**NX_NOT_BOUND** (0x24) — этот сокет не привязан к порту.</span><span class="sxs-lookup"><span data-stu-id="d7262-3223">**NX_NOT_BOUND** (0x24) This socket is not bound to a port.</span></span>
- <span data-ttu-id="d7262-3224">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета или возвращаемого порта.</span><span class="sxs-lookup"><span data-stu-id="d7262-3224">**NX_PTR_ERROR** (0x07) Invalid socket pointer or port return pointer.</span></span>
- <span data-ttu-id="d7262-3225">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-3225">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-3226">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-3226">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-3227">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-3227">Allowed From</span></span>

<span data-ttu-id="d7262-3228">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-3228">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-3229">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-3229">Preemption Possible</span></span>

<span data-ttu-id="d7262-3230">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-3230">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-3231">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-3231">Example</span></span>

```C
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
    socket is bound to. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-3232">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-3232">See Also</span></span>

- <span data-ttu-id="d7262-3233">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3233">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="d7262-3234">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="d7262-3234">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="d7262-3235">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-3235">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="d7262-3236">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-3236">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="d7262-3237">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3237">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="d7262-3238">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="d7262-3238">nx_udp_socket_receive, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="d7262-3239">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-3239">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="d7262-3240">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="d7262-3240">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_receive"></a><span data-ttu-id="d7262-3241">nx_udp_socket_receive</span><span class="sxs-lookup"><span data-stu-id="d7262-3241">nx_udp_socket_receive</span></span>

<span data-ttu-id="d7262-3242">Получение датаграммы из сокета UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3242">Receive datagram from UDP socket</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-3243">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-3243">Prototype</span></span>

```C
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr, 
    ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="d7262-3244">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-3244">Description</span></span>

<span data-ttu-id="d7262-3245">Эта служба получает датаграмму UDP из указанного сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-3245">This service receives an UDP datagram from the specified socket.</span></span> <span data-ttu-id="d7262-3246">Если в указанном сокете в очереди нет датаграмм, вызывающий объект приостанавливает выполнение на основе указанного параметра ожидания.</span><span class="sxs-lookup"><span data-stu-id="d7262-3246">If no datagram is queued on the specified socket, the caller suspends based on the supplied wait option.</span></span>

<span data-ttu-id="d7262-3247">*Если возвращается значение NX_SUCCESS, приложение отвечает за освобождение полученного пакета, когда он больше не нужен*.</span><span class="sxs-lookup"><span data-stu-id="d7262-3247">*If NX_SUCCESS is returned, the application is responsible for releasing the received packet when it is no longer needed.*</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-3248">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-3248">Parameters</span></span>

- <span data-ttu-id="d7262-3249">**socket_ptr**: указатель на ранее созданный экземпляр сокета UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3249">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>
- <span data-ttu-id="d7262-3250">**packet_ptr**: указатель на пакет датаграммы UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3250">**packet_ptr** Pointer to UDP datagram packet pointer.</span></span>
- <span data-ttu-id="d7262-3251">**wait_option** определяет поведение службы в случае, если в этом сокете нет датаграмм в очереди</span><span class="sxs-lookup"><span data-stu-id="d7262-3251">**wait_option** Defines how the service behaves if a datagram is not currently queued on this socket.</span></span> <span data-ttu-id="d7262-3252">Параметры ожидания определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="d7262-3252">The wait options are defined as follows:</span></span>
- <span data-ttu-id="d7262-3253">NX_NO_WAIT (0x00000000)</span><span class="sxs-lookup"><span data-stu-id="d7262-3253">NX_NO_WAIT (0x00000000)</span></span>
- <span data-ttu-id="d7262-3254">NX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="d7262-3254">NX_WAIT_FOREVER (0xFFFFFFFF)</span></span>
- <span data-ttu-id="d7262-3255">Значение времени ожидания в тактах (от 0x00000001 до 0xFFFFFFFE)</span><span class="sxs-lookup"><span data-stu-id="d7262-3255">timeout value in ticks (0x00000001 through 0xFFFFFFFE)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-3256">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-3256">Allowed From</span></span>

<span data-ttu-id="d7262-3257">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-3257">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-3258">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-3258">Preemption Possible</span></span>

<span data-ttu-id="d7262-3259">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-3259">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-3260">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-3260">Example</span></span>

```C
/* Receive a packet from a previously created and bound UDP socket.
    If no packets are currently available, wait for 500 timer ticks
    before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
    packet_ptr. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-3261">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-3261">See Also</span></span>

- <span data-ttu-id="d7262-3262">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3262">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="d7262-3263">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="d7262-3263">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="d7262-3264">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-3264">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="d7262-3265">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-3265">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="d7262-3266">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3266">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="d7262-3267">nx_udp_socket_port_get, nx_udp_socket_receive_notify,</span><span class="sxs-lookup"><span data-stu-id="d7262-3267">nx_udp_socket_port_get, nx_udp_socket_receive_notify,</span></span>
- <span data-ttu-id="d7262-3268">nx_udp_socket_send, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-3268">nx_udp_socket_send, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="d7262-3269">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="d7262-3269">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_receive_notify"></a><span data-ttu-id="d7262-3270">nx_udp_socket_receive_notify</span><span class="sxs-lookup"><span data-stu-id="d7262-3270">nx_udp_socket_receive_notify</span></span>

<span data-ttu-id="d7262-3271">Уведомление приложения о каждом полученном пакете</span><span class="sxs-lookup"><span data-stu-id="d7262-3271">Notify application of each received packet</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-3272">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-3272">Prototype</span></span>

```C
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)
    (NX_UDP_SOCKET *socket_ptr));
```

### <a name="description"></a><span data-ttu-id="d7262-3273">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-3273">Description</span></span>

<span data-ttu-id="d7262-3274">Эта служба задает указатель на функцию уведомления о получении с помощью функции обратного вызова, заданной приложением.</span><span class="sxs-lookup"><span data-stu-id="d7262-3274">This service sets the receive notify function pointer to the callback function specified by the application.</span></span> <span data-ttu-id="d7262-3275">Эта функция обратного вызова затем вызывается при каждом получении пакета через сокет.</span><span class="sxs-lookup"><span data-stu-id="d7262-3275">This callback function is then called whenever a packet is received on the socket.</span></span> <span data-ttu-id="d7262-3276">Если задан указатель NX_NULL, функция уведомления о получении отключена.</span><span class="sxs-lookup"><span data-stu-id="d7262-3276">If a NX_NULL pointer is supplied, the receive notify function is disabled.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-3277">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-3277">Parameters</span></span>

- <span data-ttu-id="d7262-3278">**socket_ptr**: указатель на сокет UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3278">**socket_ptr** Pointer to the UDP socket.</span></span>
- <span data-ttu-id="d7262-3279">**udp_receive_notify**: указатель на функцию обратного вызова приложения, вызываемую при получении пакета в сокете</span><span class="sxs-lookup"><span data-stu-id="d7262-3279">**udp_receive_notify** Application callback function pointer that is called when a packet is received on the socket.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-3280">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-3280">Allowed From</span></span>

<span data-ttu-id="d7262-3281">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="d7262-3281">Initialization, threads, timers, and ISRs</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-3282">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-3282">Preemption Possible</span></span>

<span data-ttu-id="d7262-3283">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-3283">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-3284">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-3284">Example</span></span>

```C
/* Setup a receive packet callback function for the "udp_socket"
socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
    my_receive_notify);

/* If status is NX_SUCCESS, NetX will call the function named
    "my_receive_notify" whenever a packet is received for
    "udp_socket". */
```

### <a name="see-also"></a><span data-ttu-id="d7262-3285">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-3285">See Also</span></span>

- <span data-ttu-id="d7262-3286">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3286">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="d7262-3287">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="d7262-3287">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="d7262-3288">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-3288">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="d7262-3289">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-3289">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="d7262-3290">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3290">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="d7262-3291">nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-3291">nx_udp_socket_port_get, nx_udp_socket_receive, nx_udp_socket_send,</span></span>
- <span data-ttu-id="d7262-3292">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span><span class="sxs-lookup"><span data-stu-id="d7262-3292">nx_udp_socket_interface_send, nx_udp_socket_unbind,</span></span>
- <span data-ttu-id="d7262-3293">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="d7262-3293">nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_send"></a><span data-ttu-id="d7262-3294">nx_udp_socket_send</span><span class="sxs-lookup"><span data-stu-id="d7262-3294">nx_udp_socket_send</span></span>

<span data-ttu-id="d7262-3295">Отправка датаграммы UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3295">Send a UDP Datagram</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-3296">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-3296">Prototype</span></span>

```C
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port);
```

### <a name="description"></a><span data-ttu-id="d7262-3297">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-3297">Description</span></span>

<span data-ttu-id="d7262-3298">Эта служба отправляет датаграмму UDP через ранее созданный и привязанный сокет UDP.</span><span class="sxs-lookup"><span data-stu-id="d7262-3298">This service sends a UDP datagram through a previously created and bound UDP socket.</span></span> <span data-ttu-id="d7262-3299">NetX находит локальный IP-адрес, подходящий в качестве исходного адреса, по IP-адресу назначения.</span><span class="sxs-lookup"><span data-stu-id="d7262-3299">NetX finds a suitable local IP address as source address based on the destination IP address.</span></span> <span data-ttu-id="d7262-3300">Чтобы указать определенный интерфейс и исходный IP-адрес, приложение должно использовать службу **nx_udp_socket_interface_send**.</span><span class="sxs-lookup"><span data-stu-id="d7262-3300">To specify a specific interface and source IP address, the application should use the **nx_udp_socket_interface_send** service.</span></span>

<span data-ttu-id="d7262-3301">Обратите внимание, что эта служба возвращает управление немедленно, независимо от того, была ли датаграмма UDP успешно отправлена.</span><span class="sxs-lookup"><span data-stu-id="d7262-3301">Note that this service returns immediately regardless of whether the UDP datagram was successfully sent.</span></span>

<span data-ttu-id="d7262-3302">Сокет должен быть привязан к локальному порту.</span><span class="sxs-lookup"><span data-stu-id="d7262-3302">The socket must be bound to a local port.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-3303">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-3303">Parameters</span></span>

- <span data-ttu-id="d7262-3304">**socket_ptr**: указатель на ранее созданный экземпляр сокета UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3304">**socket_ptr** Pointer to previously created UDP socket instance</span></span>
- <span data-ttu-id="d7262-3305">**packet_ptr**: указатель на пакет датаграммы UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3305">**packet_ptr** UDP datagram packet pointer</span></span>
- <span data-ttu-id="d7262-3306">**ip_address**: конечный IP-адрес</span><span class="sxs-lookup"><span data-stu-id="d7262-3306">**ip_address** Destination IP address</span></span>
- <span data-ttu-id="d7262-3307">**port**: допустимый конечный номер порта в диапазоне от 1 до 0xFFFF в порядке байтов узла</span><span class="sxs-lookup"><span data-stu-id="d7262-3307">**port** Valid destination port number between 1 and 0xFFFF), in host byte order</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-3308">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-3308">Return Values</span></span>

- <span data-ttu-id="d7262-3309">**NX_SUCCESS** (0x00) — отправка через сокет UDP успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="d7262-3309">**NX_SUCCESS** (0x00) Successful UDP socket send</span></span>
- <span data-ttu-id="d7262-3310">**NX_NOT_BOUND** (0x24) — сокет не привязан ни к одному порту.</span><span class="sxs-lookup"><span data-stu-id="d7262-3310">**NX_NOT_BOUND** (0x24) Socket not bound to any port</span></span>
- <span data-ttu-id="d7262-3311">**NX_NO_INTERFACE_ADDRESS** (0x50) — не найден подходящий исходящий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="d7262-3311">**NX_NO_INTERFACE_ADDRESS** (0x50) No suitable outgoing interface can be found.</span></span>
- <span data-ttu-id="d7262-3312">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес сервера.</span><span class="sxs-lookup"><span data-stu-id="d7262-3312">**NX_IP_ADDRESS_ERROR** (0x21) Invalid server IP address</span></span>
- <span data-ttu-id="d7262-3313">**NX_UNDERFLOW** (0x02) — недостаточно места для заголовка UDP в пакете.</span><span class="sxs-lookup"><span data-stu-id="d7262-3313">**NX_UNDERFLOW** (0x02) Not enough room for UDP header in the packet</span></span>
- <span data-ttu-id="d7262-3314">**NX_OVERFLOW** (0x03) — недопустимый указатель для добавления пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-3314">**NX_OVERFLOW** (0x03) Packet append pointer is invalid</span></span>
- <span data-ttu-id="d7262-3315">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-3315">**NX_PTR_ERROR** (0x07) Invalid socket pointer</span></span>
- <span data-ttu-id="d7262-3316">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-3316">**NX_CALLER_ERROR** (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="d7262-3317">**NX_NOT_ENABLED** (0x14) — протокол UDP не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-3317">**NX_NOT_ENABLED** (0x14) UDP has not been enabled</span></span>
- <span data-ttu-id="d7262-3318">**NX_INVALID_PORT** (0x46) — номер порта не входит в допустимый диапазон.</span><span class="sxs-lookup"><span data-stu-id="d7262-3318">**NX_INVALID_PORT** (0x46) Port number is not within a valid range</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-3319">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-3319">Allowed From</span></span>

<span data-ttu-id="d7262-3320">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-3320">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-3321">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-3321">Preemption Possible</span></span>

<span data-ttu-id="d7262-3322">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-3322">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-3323">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-3323">Example</span></span>

```C
ULONG server_address;

/* Set the UDP Client IP address. */
server_address = IP_ADDRESS(1,2,3,5);

/* Send a packet to the UDP server at server_address on port 12. */
status = nx_udp_socket_send(&client_socket, packet_ptr,
    server_address, 12);

/* If status == NX_SUCCESS, the application successfully transmitted
    the packet out the UDP socket to its peer. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-3324">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-3324">See Also</span></span>

- <span data-ttu-id="d7262-3325">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3325">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="d7262-3326">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="d7262-3326">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="d7262-3327">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-3327">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="d7262-3328">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-3328">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="d7262-3329">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3329">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="d7262-3330">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-3330">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="d7262-3331">nx_udp_socket_receive_notify, nx_udp_socket_interface_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-3331">nx_udp_socket_receive_notify, nx_udp_socket_interface_send,</span></span>
- <span data-ttu-id="d7262-3332">nx_udp_socket_unbind, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="d7262-3332">nx_udp_socket_unbind, nx_udp_source_extract</span></span>

## <a name="nx_udp_socket_interface_send"></a><span data-ttu-id="d7262-3333">nx_udp_socket_interface_send</span><span class="sxs-lookup"><span data-stu-id="d7262-3333">nx_udp_socket_interface_send</span></span>

<span data-ttu-id="d7262-3334">Отправка датаграммы через сокет UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3334">Send datagram through UDP socket.</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-3335">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-3335">Prototype</span></span>

```C
UINT nx_udp_socket_interface_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```

### <a name="description"></a><span data-ttu-id="d7262-3336">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-3336">Description</span></span>

<span data-ttu-id="d7262-3337">Эта служба отправляет датаграмму UDP через ранее созданный и привязанный сокет UDP и через сетевой интерфейс с IP-адресом, указанным в качестве исходного.</span><span class="sxs-lookup"><span data-stu-id="d7262-3337">This service sends a UDP datagram through a previously created and bound UDP socket through the network interface with the specified IP address as the source address.</span></span> <span data-ttu-id="d7262-3338">Обратите внимание, что эта служба возвращает управление немедленно, независимо от того, была ли датаграмма UDP успешно отправлена.</span><span class="sxs-lookup"><span data-stu-id="d7262-3338">Note that service returns immediately, regardless of whether or not the UDP datagram was successfully sent.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-3339">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-3339">Parameters</span></span>

- <span data-ttu-id="d7262-3340">**socket_ptr**: сокет для передачи пакета</span><span class="sxs-lookup"><span data-stu-id="d7262-3340">**socket_ptr** Socket to transmit the packet out on.</span></span>
- <span data-ttu-id="d7262-3341">**packet_ptr**: указатель на передаваемый пакет</span><span class="sxs-lookup"><span data-stu-id="d7262-3341">**packet_ptr** Pointer to packet to transmit.</span></span>
- <span data-ttu-id="d7262-3342">**ip_address**: конечный IP-адрес, на который нужно отправить пакет</span><span class="sxs-lookup"><span data-stu-id="d7262-3342">**ip_address** Destination IP address to send packet.</span></span>
- <span data-ttu-id="d7262-3343">**port**: конечный порт</span><span class="sxs-lookup"><span data-stu-id="d7262-3343">**port** Destination port.</span></span>
- <span data-ttu-id="d7262-3344">**address_index**: индекс адреса, связанного с интерфейсом, через который нужно отправить пакет</span><span class="sxs-lookup"><span data-stu-id="d7262-3344">**address_index** Index of the address associated with the interface to send packet on.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-3345">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-3345">Return Values</span></span>

- <span data-ttu-id="d7262-3346">**NX_SUCCESS** (0x00) — пакет успешно отправлен.</span><span class="sxs-lookup"><span data-stu-id="d7262-3346">**NX_SUCCESS** (0x00) Packet successfully sent.</span></span>
- <span data-ttu-id="d7262-3347">**NX_NOT_BOUND** (0x24) — сокет не привязан к порту.</span><span class="sxs-lookup"><span data-stu-id="d7262-3347">**NX_NOT_BOUND** (0x24) Socket not bound to a port.</span></span>
- <span data-ttu-id="d7262-3348">**NX_IP_ADDRESS_ERROR** (0x21) — недопустимый IP-адрес.</span><span class="sxs-lookup"><span data-stu-id="d7262-3348">**NX_IP_ADDRESS_ERROR** (0x21) Invalid IP address.</span></span>
- <span data-ttu-id="d7262-3349">**NX_NOT_ENABLED** (0x14) — обработка UDP не включена.</span><span class="sxs-lookup"><span data-stu-id="d7262-3349">**NX_NOT_ENABLED** (0x14) UDP processing not enabled.</span></span>
- <span data-ttu-id="d7262-3350">**NX_PTR_ERROR** (0x07) — недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="d7262-3350">**NX_PTR_ERROR** (0x07) Invalid pointer.</span></span>
- <span data-ttu-id="d7262-3351">**NX_OVERFLOW** (0x03) — недопустимый указатель для добавления пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-3351">**NX_OVERFLOW** (0x03) Invalid packet append pointer.</span></span>
- <span data-ttu-id="d7262-3352">**NX_UNDERFLOW** (0x02) — недопустимый указатель префикса пакета.</span><span class="sxs-lookup"><span data-stu-id="d7262-3352">**NX_UNDERFLOW** (0x02) Invalid packet prepend pointer.</span></span>
- <span data-ttu-id="d7262-3353">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-3353">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-3354">**NX_INVALID_INTERFACE** (0x4C) — недопустимый индекс адреса.</span><span class="sxs-lookup"><span data-stu-id="d7262-3354">**NX_INVALID_INTERFACE** (0x4C) Invalid address index.</span></span>
- <span data-ttu-id="d7262-3355">**NX_INVALID_PORT** (0x46) — номер порта превышает максимальный.</span><span class="sxs-lookup"><span data-stu-id="d7262-3355">**NX_INVALID_PORT** (0x46) Port number exceeds maximum port number.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-3356">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-3356">Allowed From</span></span>

<span data-ttu-id="d7262-3357">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-3357">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-3358">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-3358">Preemption Possible</span></span>

<span data-ttu-id="d7262-3359">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-3359">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-3360">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-3360">Example</span></span>

```C
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
interface at index 1 in the IP task interface list. */
status = nx_udp_packet_interface_send(socket_ptr, packet_ptr,
    destination_ip, 80,
    ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-3361">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-3361">See Also</span></span>

- <span data-ttu-id="d7262-3362">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3362">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="d7262-3363">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="d7262-3363">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="d7262-3364">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-3364">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="d7262-3365">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-3365">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="d7262-3366">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3366">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="d7262-3367">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-3367">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="d7262-3368">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-3368">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="d7262-3369">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="d7262-3369">nx_udp_socket_unbind</span></span>

## <a name="nx_udp_socket_unbind"></a><span data-ttu-id="d7262-3370">nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="d7262-3370">nx_udp_socket_unbind</span></span>

<span data-ttu-id="d7262-3371">Отмена привязки сокета UDP к UDP-порту</span><span class="sxs-lookup"><span data-stu-id="d7262-3371">Unbind UDP socket from UDP port.</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-3372">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-3372">Prototype</span></span>

```C
UINT nx_udp_socket_unbind(NX_UDP_SOCKET *socket_ptr);
```

### <a name="description"></a><span data-ttu-id="d7262-3373">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-3373">Description</span></span>

<span data-ttu-id="d7262-3374">Эта служба освобождает привязку между сокетом UDP и UDP-портом.</span><span class="sxs-lookup"><span data-stu-id="d7262-3374">This service releases the binding between the UDP socket and a UDP port.</span></span> <span data-ttu-id="d7262-3375">Все полученные пакеты, хранящиеся в очереди приема, освобождаются в рамках операции отмены привязки.</span><span class="sxs-lookup"><span data-stu-id="d7262-3375">Any received packets stored in the receive queue are released as part of the unbind operation.</span></span>

<span data-ttu-id="d7262-3376">Если есть другие потоки, ожидающие привязки другого сокета к освобождаемому порту, к освобожденному порту привязывается первый приостановленный поток.</span><span class="sxs-lookup"><span data-stu-id="d7262-3376">If there are other threads waiting to bind another socket to the unbound port, the first suspended thread is then bound to the newly unbound port.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-3377">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-3377">Parameters</span></span>

- <span data-ttu-id="d7262-3378">**socket_ptr**: указатель на ранее созданный экземпляр сокета UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3378">**socket_ptr** Pointer to previously created UDP socket instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-3379">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-3379">Return Values</span></span>

- <span data-ttu-id="d7262-3380">**NX_SUCCESS** (0x00) — привязка сокета успешно отменена.</span><span class="sxs-lookup"><span data-stu-id="d7262-3380">**NX_SUCCESS** (0x00) Successful socket unbind.</span></span>
- <span data-ttu-id="d7262-3381">**NX_NOT_BOUND** (0x24) — сокет не привязан ни к одному порту.</span><span class="sxs-lookup"><span data-stu-id="d7262-3381">**NX_NOT_BOUND** (0x24) Socket was not bound to any port.</span></span>
- <span data-ttu-id="d7262-3382">**NX_PTR_ERROR** (0x07) — недопустимый указатель сокета.</span><span class="sxs-lookup"><span data-stu-id="d7262-3382">**NX_PTR_ERROR** (0x07) Invalid socket pointer.</span></span>
- <span data-ttu-id="d7262-3383">**NX_CALLER_ERROR** (0x11) — недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="d7262-3383">**NX_CALLER_ERROR** (0x11) Invalid caller of this service.</span></span>
- <span data-ttu-id="d7262-3384">**NX_NOT_ENABLED** (0x14) — этот компонент не включен.</span><span class="sxs-lookup"><span data-stu-id="d7262-3384">**NX_NOT_ENABLED** (0x14) This component has not been enabled.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-3385">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-3385">Allowed From</span></span>

<span data-ttu-id="d7262-3386">Потоки</span><span class="sxs-lookup"><span data-stu-id="d7262-3386">Threads</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-3387">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-3387">Preemption Possible</span></span>

<span data-ttu-id="d7262-3388">Да</span><span class="sxs-lookup"><span data-stu-id="d7262-3388">Yes</span></span>

### <a name="example"></a><span data-ttu-id="d7262-3389">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-3389">Example</span></span>

```C
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
    unbound. */
```

### <a name="see-also"></a><span data-ttu-id="d7262-3390">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-3390">See Also</span></span>

- <span data-ttu-id="d7262-3391">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3391">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="d7262-3392">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="d7262-3392">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="d7262-3393">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-3393">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="d7262-3394">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-3394">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="d7262-3395">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3395">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="d7262-3396">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-3396">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="d7262-3397">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-3397">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="d7262-3398">nx_udp_socket_interface_send, nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="d7262-3398">nx_udp_socket_interface_send, nx_udp_source_extract</span></span>

## <a name="nx_udp_source_extract"></a><span data-ttu-id="d7262-3399">nx_udp_source_extract</span><span class="sxs-lookup"><span data-stu-id="d7262-3399">nx_udp_source_extract</span></span>

<span data-ttu-id="d7262-3400">Извлечение IP-адреса и порта отправки из датаграммы UDP</span><span class="sxs-lookup"><span data-stu-id="d7262-3400">Extract IP and sending port from UDP datagram</span></span>

### <a name="prototype"></a><span data-ttu-id="d7262-3401">Прототип</span><span class="sxs-lookup"><span data-stu-id="d7262-3401">Prototype</span></span>

```C
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, UINT *port);
```

### <a name="description"></a><span data-ttu-id="d7262-3402">Описание</span><span class="sxs-lookup"><span data-stu-id="d7262-3402">Description</span></span>

<span data-ttu-id="d7262-3403">Эта служба извлекает IP-адрес и номер порта отправителя из заголовков IP и UDP в указанной датаграмме UDP.</span><span class="sxs-lookup"><span data-stu-id="d7262-3403">This service extracts the sender's IP and port number from the IP and UDP headers of the supplied UDP datagram.</span></span>

### <a name="parameters"></a><span data-ttu-id="d7262-3404">Параметры</span><span class="sxs-lookup"><span data-stu-id="d7262-3404">Parameters</span></span>

- <span data-ttu-id="d7262-3405">**packet_ptr** Указатель на пакет датаграммы UDP.</span><span class="sxs-lookup"><span data-stu-id="d7262-3405">**packet_ptr** UDP datagram packet pointer.</span></span>
- <span data-ttu-id="d7262-3406">**ip_address**: допустимый указатель на возвращаемую переменную с IP-адресом</span><span class="sxs-lookup"><span data-stu-id="d7262-3406">**ip_address** Valid pointer to the return IP address variable.</span></span>
- <span data-ttu-id="d7262-3407">**port**: допустимый указатель на возвращаемую переменную с портом</span><span class="sxs-lookup"><span data-stu-id="d7262-3407">**port** Valid pointer to the return port variable.</span></span>

### <a name="return-values"></a><span data-ttu-id="d7262-3408">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="d7262-3408">Return Values</span></span>

- <span data-ttu-id="d7262-3409">**NX_SUCCESS** (0x00) — успешное извлечение исходного IP-адреса и порта.</span><span class="sxs-lookup"><span data-stu-id="d7262-3409">**NX_SUCCESS** (0x00) Successful source IP/port extraction.</span></span>
- <span data-ttu-id="d7262-3410">**NX_INVALID_PACKET** (0x12) — указан недопустимый пакет.</span><span class="sxs-lookup"><span data-stu-id="d7262-3410">**NX_INVALID_PACKET** (0x12) The supplied packet is invalid.</span></span>
- <span data-ttu-id="d7262-3411">**NX_PTR_ERROR** (0x07) — недопустимый пакет, IP-адрес или порт назначения.</span><span class="sxs-lookup"><span data-stu-id="d7262-3411">**NX_PTR_ERROR** (0x07) Invalid packet or IP or port destination.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="d7262-3412">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="d7262-3412">Allowed From</span></span>

<span data-ttu-id="d7262-3413">Инициализация, потоки, таймеры, запросы ISR</span><span class="sxs-lookup"><span data-stu-id="d7262-3413">Initialization, threads, timers, ISR</span></span>

### <a name="preemption-possible"></a><span data-ttu-id="d7262-3414">Возможно вытеснение</span><span class="sxs-lookup"><span data-stu-id="d7262-3414">Preemption Possible</span></span>

<span data-ttu-id="d7262-3415">Нет</span><span class="sxs-lookup"><span data-stu-id="d7262-3415">No</span></span>

### <a name="example"></a><span data-ttu-id="d7262-3416">Пример</span><span class="sxs-lookup"><span data-stu-id="d7262-3416">Example</span></span>

```C
/* Extract the IP and port information from the sender of the UPD
    packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address,
    &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has
    been stored in sender_ip_address and sender_port respectively.*/
```

### <a name="see-also"></a><span data-ttu-id="d7262-3417">См. также:</span><span class="sxs-lookup"><span data-stu-id="d7262-3417">See Also</span></span>

- <span data-ttu-id="d7262-3418">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3418">nx_udp_enable, nx_udp_free_port_find, nx_udp_info_get,</span></span>
- <span data-ttu-id="d7262-3419">nx_udp_packet_info_extract, nx_udp_socket_bind,</span><span class="sxs-lookup"><span data-stu-id="d7262-3419">nx_udp_packet_info_extract, nx_udp_socket_bind,</span></span>
- <span data-ttu-id="d7262-3420">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span><span class="sxs-lookup"><span data-stu-id="d7262-3420">nx_udp_socket_bytes_available, nx_udp_socket_checksum_disable,</span></span>
- <span data-ttu-id="d7262-3421">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span><span class="sxs-lookup"><span data-stu-id="d7262-3421">nx_udp_socket_checksum_enable, nx_udp_socket_create,</span></span>
- <span data-ttu-id="d7262-3422">nx_udp_socket_delete, nx_udp_socket_info_get,</span><span class="sxs-lookup"><span data-stu-id="d7262-3422">nx_udp_socket_delete, nx_udp_socket_info_get,</span></span>
- <span data-ttu-id="d7262-3423">nx_udp_socket_port_get, nx_udp_socket_receive,</span><span class="sxs-lookup"><span data-stu-id="d7262-3423">nx_udp_socket_port_get, nx_udp_socket_receive,</span></span>
- <span data-ttu-id="d7262-3424">nx_udp_socket_receive_notify, nx_udp_socket_send,</span><span class="sxs-lookup"><span data-stu-id="d7262-3424">nx_udp_socket_receive_notify, nx_udp_socket_send,</span></span>
- <span data-ttu-id="d7262-3425">nx_udp_socket_interface_send, nx_udp_socket_unbind</span><span class="sxs-lookup"><span data-stu-id="d7262-3425">nx_udp_socket_interface_send, nx_udp_socket_unbind</span></span>