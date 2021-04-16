---
title: Глава 4. Описание служб NAT
description: Эта глава содержит описание всех служб API NAT для NetX Duo в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8bdbdfcb2da6425fb99cadc7b2f6815dedc12953
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814620"
---
# <a name="chapter-4---description-of-nat-services"></a><span data-ttu-id="2b0df-103">Глава 4. Описание служб NAT</span><span class="sxs-lookup"><span data-stu-id="2b0df-103">Chapter 4 - Description of NAT services</span></span>

<span data-ttu-id="2b0df-104">Эта глава содержит описание всех служб API NAT для NetX Duo, перечисленных ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="2b0df-104">This chapter contains a description of all NetX Duo NAT API services (listed below) in alphabetical order.</span></span>

> [!NOTE]
> <span data-ttu-id="2b0df-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, которое используется для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="2b0df-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

## <a name="nx_nat_create"></a><span data-ttu-id="2b0df-106">nx_nat_create</span><span class="sxs-lookup"><span data-stu-id="2b0df-106">nx_nat_create</span></span>

<span data-ttu-id="2b0df-107">Создание сервера NAT</span><span class="sxs-lookup"><span data-stu-id="2b0df-107">Create a NAT Server</span></span>

### <a name="prototype"></a><span data-ttu-id="2b0df-108">Прототип</span><span class="sxs-lookup"><span data-stu-id="2b0df-108">Prototype</span></span>

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

### <a name="description"></a><span data-ttu-id="2b0df-109">Описание</span><span class="sxs-lookup"><span data-stu-id="2b0df-109">Description</span></span>

<span data-ttu-id="2b0df-110">Эта служба создает экземпляр сервера NAT.</span><span class="sxs-lookup"><span data-stu-id="2b0df-110">This service creates an instance of the NAT server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b0df-111">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2b0df-111">Input Parameters</span></span>

- <span data-ttu-id="2b0df-112">**nat_ptr** — указатель на создаваемый экземпляр NAT.</span><span class="sxs-lookup"><span data-stu-id="2b0df-112">**nat_ptr** Pointer to NAT instance to create</span></span>
- <span data-ttu-id="2b0df-113">**ip_ptr** — указатель на экземпляр IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="2b0df-113">**ip_ptr Pointer** to IP instance</span></span>
- <span data-ttu-id="2b0df-114">**global_interface_index** — индекс глобального сетевого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="2b0df-114">**global_interface_index** Index to the global network interface</span></span>
- <span data-ttu-id="2b0df-115">**dynamic_cache_memory** — указатель на зону памяти для таблицы NAT.</span><span class="sxs-lookup"><span data-stu-id="2b0df-115">**dynamic_cache_memory** Pointer memory area to NAT table</span></span>
- <span data-ttu-id="2b0df-116">**dynamic_cache_size** — размер зоны памяти для таблицы NAT.</span><span class="sxs-lookup"><span data-stu-id="2b0df-116">**dynamic_cache_size** Size of memory area for NAT table</span></span>

### <a name="return-values"></a><span data-ttu-id="2b0df-117">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2b0df-117">Return Values</span></span>

- <span data-ttu-id="2b0df-118">**NX_SUCCESS** (0x00) — сервер NAT успешно создан.</span><span class="sxs-lookup"><span data-stu-id="2b0df-118">**NX_SUCCESS** (0x00) NAT server successfully created</span></span>
- <span data-ttu-id="2b0df-119">NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="2b0df-119">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="2b0df-120">NX_NAT_PARAM_ERROR (0xD01) — недопустимые входные данные (без указателя).</span><span class="sxs-lookup"><span data-stu-id="2b0df-120">NX_NAT_PARAM_ERROR (0xD01) Invalid non pointer input</span></span>
- <span data-ttu-id="2b0df-121">NX_NAT_CACHE_ERROR (0xD02) — недопустимые входные данные указателя на кэш.</span><span class="sxs-lookup"><span data-stu-id="2b0df-121">NX_NAT_CACHE_ERROR (0xD02) Invalid cache pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b0df-122">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2b0df-122">Allowed From</span></span>

<span data-ttu-id="2b0df-123">Код приложения</span><span class="sxs-lookup"><span data-stu-id="2b0df-123">Application code</span></span>

### <a name="example"></a><span data-ttu-id="2b0df-124">Например, .</span><span class="sxs-lookup"><span data-stu-id="2b0df-124">Example</span></span>

```C
#define NX_NAT_ENTRY_CACHE_SIZE 20480

static UCHAR nat_cache[NX_NAT_ENTRY_CACHE_SIZE];
UINT global_interface_index = 0;

/* Create a NAT Server and cache with a global interface index. */
status = nx_nat_create(nat_ptr, ip_ptr, global_interface_index,
    nat_cache, NX_NAT_ENTRY_CACHE_SIZE);

/* If status = NX_SUCCESS, the NAT instance was successfully
    created. */
```

## <a name="nx_nat_delete"></a><span data-ttu-id="2b0df-125">nx_nat_delete</span><span class="sxs-lookup"><span data-stu-id="2b0df-125">nx_nat_delete</span></span>

<span data-ttu-id="2b0df-126">Удаление сервера NAT</span><span class="sxs-lookup"><span data-stu-id="2b0df-126">Delete a NAT Server</span></span>

### <a name="prototype"></a><span data-ttu-id="2b0df-127">Прототип</span><span class="sxs-lookup"><span data-stu-id="2b0df-127">Prototype</span></span>

```C
UINT nx_nat_delete(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a><span data-ttu-id="2b0df-128">Описание</span><span class="sxs-lookup"><span data-stu-id="2b0df-128">Description</span></span>

<span data-ttu-id="2b0df-129">Эта служба удаляет созданный ранее сервер NAT.</span><span class="sxs-lookup"><span data-stu-id="2b0df-129">This service deletes a previously created NAT Server.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b0df-130">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2b0df-130">Input Parameters</span></span>

- <span data-ttu-id="2b0df-131">**nat_ptr** — указатель на удаляемый экземпляр NAT.</span><span class="sxs-lookup"><span data-stu-id="2b0df-131">**nat_ptr** Pointer to NAT instance to delete</span></span>

### <a name="return-values"></a><span data-ttu-id="2b0df-132">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2b0df-132">Return Values</span></span>

- <span data-ttu-id="2b0df-133">**NX_SUCCESS** — (0x00) экземпляр NAT успешно удален.</span><span class="sxs-lookup"><span data-stu-id="2b0df-133">**NX_SUCCESS** (0x00) NAT successfully deleted</span></span>
- <span data-ttu-id="2b0df-134">NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="2b0df-134">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b0df-135">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2b0df-135">Allowed From</span></span>

<span data-ttu-id="2b0df-136">Код приложения</span><span class="sxs-lookup"><span data-stu-id="2b0df-136">Application code</span></span>

### <a name="example"></a><span data-ttu-id="2b0df-137">Например, .</span><span class="sxs-lookup"><span data-stu-id="2b0df-137">Example</span></span>

```C
/* Delete the NAT instance. */
status = nx_nat_delete (nat_ptr);

/* If the NAT instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_nat_enable"></a><span data-ttu-id="2b0df-138">nx_nat_enable</span><span class="sxs-lookup"><span data-stu-id="2b0df-138">nx_nat_enable</span></span>

<span data-ttu-id="2b0df-139">Включение NAT для экземпляра IP</span><span class="sxs-lookup"><span data-stu-id="2b0df-139">Enable the IP instance for NAT</span></span>

### <a name="prototype"></a><span data-ttu-id="2b0df-140">Прототип</span><span class="sxs-lookup"><span data-stu-id="2b0df-140">Prototype</span></span>

```C
UINT nx_nat_enable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a><span data-ttu-id="2b0df-141">Описание</span><span class="sxs-lookup"><span data-stu-id="2b0df-141">Description</span></span>

<span data-ttu-id="2b0df-142">Эта служба включает NAT для экземпляра IP (для отправки пакетов на сервер NAT).</span><span class="sxs-lookup"><span data-stu-id="2b0df-142">This service enables the IP instance for NAT (e.g. forward received packets to the NAT server).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b0df-143">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2b0df-143">Input Parameters</span></span>

- <span data-ttu-id="2b0df-144">**nat_ptr** — указатель на экземпляр NAT.</span><span class="sxs-lookup"><span data-stu-id="2b0df-144">**nat_ptr** Pointer to NAT instance</span></span>

### <a name="return-values"></a><span data-ttu-id="2b0df-145">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2b0df-145">Return Values</span></span>

- <span data-ttu-id="2b0df-146">**NX_SUCCESS** (0x00) — экземпляр NAT успешно включен.</span><span class="sxs-lookup"><span data-stu-id="2b0df-146">**NX_SUCCESS** (0x00) NAT successfully enabled</span></span>
- <span data-ttu-id="2b0df-147">NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="2b0df-147">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b0df-148">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2b0df-148">Allowed From</span></span>

<span data-ttu-id="2b0df-149">Код приложения</span><span class="sxs-lookup"><span data-stu-id="2b0df-149">Application code</span></span>

### <a name="example"></a><span data-ttu-id="2b0df-150">Например, .</span><span class="sxs-lookup"><span data-stu-id="2b0df-150">Example</span></span>

```C
/* Enable the NAT server. */
status = nx_nat_enable (nat_ptr);

/* If status = NX_SUCCESS, the IP instance was successfully enabled for NAT. */
```

## <a name="nx_nat_disable"></a><span data-ttu-id="2b0df-151">nx_nat_disable</span><span class="sxs-lookup"><span data-stu-id="2b0df-151">nx_nat_disable</span></span>

<span data-ttu-id="2b0df-152">Отключение NAT для экземпляра IP</span><span class="sxs-lookup"><span data-stu-id="2b0df-152">Disable the IP instance for NAT</span></span>

### <a name="prototype"></a><span data-ttu-id="2b0df-153">Прототип</span><span class="sxs-lookup"><span data-stu-id="2b0df-153">Prototype</span></span>

```C
UINT nx_nat_disable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a><span data-ttu-id="2b0df-154">Описание</span><span class="sxs-lookup"><span data-stu-id="2b0df-154">Description</span></span>

<span data-ttu-id="2b0df-155">Эта служба отключает NAT для экземпляра IP.</span><span class="sxs-lookup"><span data-stu-id="2b0df-155">This service disables NAT on the IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b0df-156">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2b0df-156">Input Parameters</span></span>

- <span data-ttu-id="2b0df-157">**nat_ptr** — указатель на экземпляр NAT.</span><span class="sxs-lookup"><span data-stu-id="2b0df-157">**nat_ptr** Pointer to NAT instance</span></span>

### <a name="return-values"></a><span data-ttu-id="2b0df-158">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2b0df-158">Return Values</span></span>

- <span data-ttu-id="2b0df-159">**NX_SUCCESS** (0x00) — экземпляр NAT успешно отключен.</span><span class="sxs-lookup"><span data-stu-id="2b0df-159">**NX_SUCCESS** (0x00) NAT successfully disabled</span></span>
- <span data-ttu-id="2b0df-160">NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="2b0df-160">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b0df-161">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2b0df-161">Allowed From</span></span>

<span data-ttu-id="2b0df-162">Код приложения</span><span class="sxs-lookup"><span data-stu-id="2b0df-162">Application code</span></span>

### <a name="example"></a><span data-ttu-id="2b0df-163">Например, .</span><span class="sxs-lookup"><span data-stu-id="2b0df-163">Example</span></span>

```C
/* Disable the NAT server. */
status = nx_nat_disable (nat_ptr);

/* If status = NX_SUCCESS the NAT operation successfully disable. */
```

## <a name="nx_nat_cache_notify_set"></a><span data-ttu-id="2b0df-164">nx_nat_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="2b0df-164">nx_nat_cache_notify_set</span></span>

<span data-ttu-id="2b0df-165">Настройка функции обратного вызова для информирования о заполнении кэша</span><span class="sxs-lookup"><span data-stu-id="2b0df-165">Set a cache full notify callback function</span></span>

### <a name="prototype"></a><span data-ttu-id="2b0df-166">Прототип</span><span class="sxs-lookup"><span data-stu-id="2b0df-166">Prototype</span></span>

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)
    (NX_NAT_DEVICE *nat_ptr)));
```

### <a name="description"></a><span data-ttu-id="2b0df-167">Описание</span><span class="sxs-lookup"><span data-stu-id="2b0df-167">Description</span></span>

<span data-ttu-id="2b0df-168">Эта служба регистрирует обратный вызов для информирования о заполнении кэша, принимая в качестве входных данных указатель на определяемую пользователем функцию cache_full_notify_cb, используемую для информирования о заполнении кэша.</span><span class="sxs-lookup"><span data-stu-id="2b0df-168">This service registers the cache full callback with the input function pointer cache_full_notify_cb which points to a user defined cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b0df-169">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2b0df-169">Input Parameters</span></span>

- <span data-ttu-id="2b0df-170">**nat_ptr** — указатель на экземпляр NAT.</span><span class="sxs-lookup"><span data-stu-id="2b0df-170">**nat_ptr** Pointer to NAT instance</span></span>
- <span data-ttu-id="2b0df-171">**cache_full_notify_cb** — указатель на функцию для информирования о заполнении кэша.</span><span class="sxs-lookup"><span data-stu-id="2b0df-171">**cache_full_notify_cb** Pointer to cache full notify function</span></span>

### <a name="return-values"></a><span data-ttu-id="2b0df-172">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2b0df-172">Return Values</span></span>

- <span data-ttu-id="2b0df-173">**NX_SUCCESS** (0x00) — информирование о заполнении кэша успешно настроено.</span><span class="sxs-lookup"><span data-stu-id="2b0df-173">**NX_SUCCESS** (0x00) Cache full notify function successfully set</span></span>
- <span data-ttu-id="2b0df-174">NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="2b0df-174">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="2b0df-175">NX_NAT_PARAM_ERROR (0xD01) — недопустимые входные данные (без указателя).</span><span class="sxs-lookup"><span data-stu-id="2b0df-175">NX_NAT_PARAM_ERROR (0xD01) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b0df-176">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2b0df-176">Allowed From</span></span>

<span data-ttu-id="2b0df-177">Код приложения</span><span class="sxs-lookup"><span data-stu-id="2b0df-177">Application code</span></span>

### <a name="example"></a><span data-ttu-id="2b0df-178">Например, .</span><span class="sxs-lookup"><span data-stu-id="2b0df-178">Example</span></span>

```C
/* Set the cache full notify callback function to the NAT instance. */
status = nx_nat_cache_notify_set(nat_ptr, cache_full_notify_cb);

/* If status = NX_SUCCESS the callback function was successfully set. */
```

## <a name="nx_nat_inbound_entry_create"></a><span data-ttu-id="2b0df-179">nx_nat_inbound_entry_create</span><span class="sxs-lookup"><span data-stu-id="2b0df-179">nx_nat_inbound_entry_create</span></span>

<span data-ttu-id="2b0df-180">Создание входящей записи в таблице преобразования NAT</span><span class="sxs-lookup"><span data-stu-id="2b0df-180">Create an inbound entry in the NAT translation table</span></span>

### <a name="prototype"></a><span data-ttu-id="2b0df-181">Прототип</span><span class="sxs-lookup"><span data-stu-id="2b0df-181">Prototype</span></span>

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr
    ULONG local_ip_address,
    USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

### <a name="description"></a><span data-ttu-id="2b0df-182">Описание</span><span class="sxs-lookup"><span data-stu-id="2b0df-182">Description</span></span>

<span data-ttu-id="2b0df-183">Эта служба создает статическую входную запись (постоянную с неограниченным сроком действия) и добавляет ее в таблицу преобразования NAT.</span><span class="sxs-lookup"><span data-stu-id="2b0df-183">This service creates an inbound entry as static (permanent entry, never expires) and adds it to the NAT translation table.</span></span> <span data-ttu-id="2b0df-184">Такие записи обычно создаются для серверов локальных узлов, где подключение инициируется от узла во внешней сети.</span><span class="sxs-lookup"><span data-stu-id="2b0df-184">These entries are usually created for local host servers where a connection is initiated from a host on the outside network.</span></span> <span data-ttu-id="2b0df-185">Сервер NAT проверяет, что указанный внешний порт еще не используется в таблице трансляции и не привязан к существующему сокету NetX Duo этого же протокола.</span><span class="sxs-lookup"><span data-stu-id="2b0df-185">The NAT server checks that the external port is not already in use in the translation table or bound by a previously existing NetX Duo socket of the same protocol.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b0df-186">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2b0df-186">Input Parameters</span></span>

- <span data-ttu-id="2b0df-187">**nat_ptr** — указатель на экземпляр NAT.</span><span class="sxs-lookup"><span data-stu-id="2b0df-187">**nat_ptr** Pointer to NAT instance</span></span>
- <span data-ttu-id="2b0df-188">**entry_ptr** — указатель на запись преобразования.</span><span class="sxs-lookup"><span data-stu-id="2b0df-188">**entry_ptr** Pointer to translation entry</span></span>
- <span data-ttu-id="2b0df-189">**local_ip_address** — IP-адрес локального узла.</span><span class="sxs-lookup"><span data-stu-id="2b0df-189">**local_ip_address** Local host IP address</span></span>
- <span data-ttu-id="2b0df-190">**external_port** — порт назначения во внешней сети.</span><span class="sxs-lookup"><span data-stu-id="2b0df-190">**external_port** Destination port on the external network</span></span>
- <span data-ttu-id="2b0df-191">**local_port** — порт источника (локального узла).</span><span class="sxs-lookup"><span data-stu-id="2b0df-191">**local_port** Source (local host) port</span></span>
- <span data-ttu-id="2b0df-192">**protocol** — протокол пакетов (например, TCP).</span><span class="sxs-lookup"><span data-stu-id="2b0df-192">**protocol** Packet protocol (e.g TCP)</span></span>

### <a name="return-values"></a><span data-ttu-id="2b0df-193">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2b0df-193">Return Values</span></span>

- <span data-ttu-id="2b0df-194">**NX_SUCCESS** (0x00) — запись успешно создана.</span><span class="sxs-lookup"><span data-stu-id="2b0df-194">**NX_SUCCESS** (0x00) Entry successfully created</span></span>
- <span data-ttu-id="2b0df-195">**NX_NAT_PORT_UNAVAILABLE** (0xD0D) — недопустимый внешний порт.</span><span class="sxs-lookup"><span data-stu-id="2b0df-195">**NX_NAT_PORT_UNAVAILABLE** (0xD0D) Invalid external port</span></span>
- <span data-ttu-id="2b0df-196">NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="2b0df-196">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="2b0df-197">NX_NAT_PARAM_ERROR (0xD01) — недопустимые входные данные (без указателя).</span><span class="sxs-lookup"><span data-stu-id="2b0df-197">NX_NAT_PARAM_ERROR (0xD01) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b0df-198">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2b0df-198">Allowed From</span></span>

<span data-ttu-id="2b0df-199">Код приложения</span><span class="sxs-lookup"><span data-stu-id="2b0df-199">Application code</span></span>

### <a name="example"></a><span data-ttu-id="2b0df-200">Например, .</span><span class="sxs-lookup"><span data-stu-id="2b0df-200">Example</span></span>

```C
/* Create an entry for an inbound TCP packet. */
status = nx_nat_inbound_entry_create(nat_ptr, entry_ptr,
    IP_ADDRESS(192,168,2,2), 5001, 5001,
    NX_PROTOCOL_TCP);

/* If status = NX_SUCCESS the entry was successfully created. */
```

## <a name="nx_nat_inbound_entry_delete"></a><span data-ttu-id="2b0df-201">nx_nat_inbound_entry_delete</span><span class="sxs-lookup"><span data-stu-id="2b0df-201">nx_nat_inbound_entry_delete</span></span>

<span data-ttu-id="2b0df-202">Удаление входящей записи в таблице преобразования NAT</span><span class="sxs-lookup"><span data-stu-id="2b0df-202">Delete an inbound entry in the NAT translation table</span></span>

### <a name="prototype"></a><span data-ttu-id="2b0df-203">Прототип</span><span class="sxs-lookup"><span data-stu-id="2b0df-203">Prototype</span></span>

```C
UINT nx_nat_inbound_entry_delete(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *delete_entry_ptr)
```

### <a name="description"></a><span data-ttu-id="2b0df-204">Описание</span><span class="sxs-lookup"><span data-stu-id="2b0df-204">Description</span></span>

<span data-ttu-id="2b0df-205">Эта служба удаляет указанную входящую запись из таблицы преобразования.</span><span class="sxs-lookup"><span data-stu-id="2b0df-205">This service deletes the specified inbound entry from the translation table.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="2b0df-206">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="2b0df-206">Input Parameters</span></span>

- <span data-ttu-id="2b0df-207">**nat_ptr** — указатель на экземпляр NAT.</span><span class="sxs-lookup"><span data-stu-id="2b0df-207">**nat_ptr** Pointer to NAT instance</span></span>
- <span data-ttu-id="2b0df-208">**delete_entry_ptr** — указатель на запись преобразования NAT.</span><span class="sxs-lookup"><span data-stu-id="2b0df-208">**delete_entry_ptr** Pointer to the NAT translation entry</span></span>

### <a name="return-values"></a><span data-ttu-id="2b0df-209">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="2b0df-209">Return Values</span></span>

- <span data-ttu-id="2b0df-210">**NX_SUCCESS** (0x00) — запись успешно удалена.</span><span class="sxs-lookup"><span data-stu-id="2b0df-210">**NX_SUCCESS** (0x00) Entry successfully deleted</span></span>
- <span data-ttu-id="2b0df-211">**NX_NAT_ENTRY_NOT_FOUND** (0xD04) — запись не найдена.</span><span class="sxs-lookup"><span data-stu-id="2b0df-211">**NX_NAT_ENTRY_NOT_FOUND** (0xD04) Entry does not found</span></span>
- <span data-ttu-id="2b0df-212">NX_PTR_ERROR (0x07): недопустимый параметр указателя во входных данных.</span><span class="sxs-lookup"><span data-stu-id="2b0df-212">NX_PTR_ERROR (0x07) Invalid input pointer parameter</span></span>
- <span data-ttu-id="2b0df-213">NX_NAT_ENTRY_TYPE_ERROR (0xD0C) — недопустимый тип преобразования.</span><span class="sxs-lookup"><span data-stu-id="2b0df-213">NX_NAT_ENTRY_TYPE_ERROR (0xD0C) Invalid translation type</span></span>

### <a name="allowed-from"></a><span data-ttu-id="2b0df-214">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="2b0df-214">Allowed From</span></span>

<span data-ttu-id="2b0df-215">Код приложения</span><span class="sxs-lookup"><span data-stu-id="2b0df-215">Application code</span></span>

### <a name="example"></a><span data-ttu-id="2b0df-216">Пример</span><span class="sxs-lookup"><span data-stu-id="2b0df-216">Example</span></span>

```C
/* Delete the specified static entry from the translation table. */
status = nx_nat_inbound_entry_delete(nat_ptr, delete_entry_ptr);

/* If status = NX_SUCCESS the entry was successfully deleted. */
```
