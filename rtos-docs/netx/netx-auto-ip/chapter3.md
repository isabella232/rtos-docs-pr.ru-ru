---
title: Глава 3. Описание служб ОСРВ Azure NetX AutoIP
description: В этой главе приведено описание всех служб ОСРВ Azure NetX AutoIP, которые перечислены ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 22cc06c32cc9f1857b32d1d2b44a506ea1652cfd
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815284"
---
# <a name="chapter-3---description-of-azure-rtos-netx-autoip-services"></a><span data-ttu-id="5bc2e-103">Глава 3. Описание служб ОСРВ Azure NetX AutoIP</span><span class="sxs-lookup"><span data-stu-id="5bc2e-103">Chapter 3 - Description of Azure RTOS NetX AutoIP services</span></span>

<span data-ttu-id="5bc2e-104">В этой главе приведено описание всех служб ОСРВ Azure NetX AutoIP, которые перечислены ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-104">This chapter contains a description of all Azure RTOS NetX AutoIP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="5bc2e-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, используемым для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="5bc2e-106">**nx_auto_ip_create**: *создание экземпляра AutoIP*.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-106">**nx_auto_ip_create**: *Create AutoIP instance*</span></span>
- <span data-ttu-id="5bc2e-107">**nx_auto_ip_delete**: *удаление экземпляра AutoIP*.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-107">**nx_auto_ip_delete**: *Delete AutoIP instance*</span></span>
- <span data-ttu-id="5bc2e-108">**nx_auto_ip_get_address**: *получение текущего адреса AutoIP*.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-108">**nx_auto_ip_get_address**: *Get current AutoIP address*</span></span>
- <span data-ttu-id="5bc2e-109">**nx_auto_ip_set_interface**: *настройка интерфейса IP, требующего адрес AutoIP*.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-109">**nx_auto_ip_set_interface**: *Set IP interface needing an AutoIP address*</span></span>
- <span data-ttu-id="5bc2e-110">**nx_auto_ip_start**: *запуск обработки AutoIP*.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-110">**nx_auto_ip_start**: *Start AutoIP processing*</span></span>
- <span data-ttu-id="5bc2e-111">**nx_auto_ip_stop**: *завершение обработки AutoIP*.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-111">**nx_auto_ip_stop**: *Stop AutoIP processing*</span></span>

## <a name="nx_auto_ip_create"></a><span data-ttu-id="5bc2e-112">nx_auto_ip_create</span><span class="sxs-lookup"><span data-stu-id="5bc2e-112">nx_auto_ip_create</span></span>

<span data-ttu-id="5bc2e-113">Создание экземпляра AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-113">Create AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5bc2e-114">Прототип</span><span class="sxs-lookup"><span data-stu-id="5bc2e-114">Prototype</span></span>

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
            NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
            UINT priority);
```

### <a name="description"></a><span data-ttu-id="5bc2e-115">Описание</span><span class="sxs-lookup"><span data-stu-id="5bc2e-115">Description</span></span>

<span data-ttu-id="5bc2e-116">Эта служба создает экземпляр AutoIP по указанному экземпляру IP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-116">This service creates an AutoIP instance on the specified IP instance.</span></span>

- <span data-ttu-id="5bc2e-117">**auto_ip_ptr**: указатель на блок управления AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-117">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="5bc2e-118">**name**: имя экземпляра AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-118">**name**: Name of AutoIP instance.</span></span>
- <span data-ttu-id="5bc2e-119">**ip_ptr**: указатель на экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-119">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="5bc2e-120">**stack_ptr**: указатель на область стека потоков AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-120">**stack_ptr**: Pointer to AutoIP thread stack area.</span></span>
- <span data-ttu-id="5bc2e-121">**stack_size**: размер области стека потоков AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-121">**stack_size**: Size of the AutoIP thread stack area.</span></span>
- <span data-ttu-id="5bc2e-122">**priority**: приоритет потока AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-122">**priority**: Priority of the AutoIP thread.</span></span>

> [!NOTE]
> <span data-ttu-id="5bc2e-123">Если используется протокол DHCP, то поток DHCP должен иметь более высокий приоритет, чем поток экземпляра IP и поток AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-123">If DHCP is used, the DHCP thread must have a higher priority than the IP instance thread and the AutoIP thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="5bc2e-124">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5bc2e-124">Return Values</span></span>

- <span data-ttu-id="5bc2e-125">**NX_SUCCESS** (0x00): экземпляр AutoIP успешно создан.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-125">**NX_SUCCESS**: (0x00) Successful AutoIP create.</span></span>
- <span data-ttu-id="5bc2e-126">**NX_AUTO_IP_ERROR** (0XA00): ошибка создания AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-126">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP create error.</span></span>
- <span data-ttu-id="5bc2e-127">NX_PTR_ERROR: (0x16): недопустимый указатель AutoIP, ip_ptr или указатель стека.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-127">NX_PTR_ERROR: (0x16) Invalid AutoIP, ip_ptr, or stack pointer.</span></span>
- <span data-ttu-id="5bc2e-128">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-128">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5bc2e-129">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5bc2e-129">Allowed From</span></span>

<span data-ttu-id="5bc2e-130">Инициализация, потоки.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-130">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="5bc2e-131">Пример</span><span class="sxs-lookup"><span data-stu-id="5bc2e-131">Example</span></span>

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a><span data-ttu-id="5bc2e-132">См. также:</span><span class="sxs-lookup"><span data-stu-id="5bc2e-132">See Also</span></span>

<span data-ttu-id="5bc2e-133">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="5bc2e-133">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_delete"></a><span data-ttu-id="5bc2e-134">nx_auto_ip_delete</span><span class="sxs-lookup"><span data-stu-id="5bc2e-134">nx_auto_ip_delete</span></span>

<span data-ttu-id="5bc2e-135">Удаление экземпляра AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-135">Delete AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="5bc2e-136">Прототип</span><span class="sxs-lookup"><span data-stu-id="5bc2e-136">Prototype</span></span>

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="5bc2e-137">Описание</span><span class="sxs-lookup"><span data-stu-id="5bc2e-137">Description</span></span>

<span data-ttu-id="5bc2e-138">Эта служба удаляет созданный ранее экземпляр AutoIP по указанному экземпляру IP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-138">This service deletes a previously created AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5bc2e-139">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="5bc2e-139">Input Parameters</span></span>

- <span data-ttu-id="5bc2e-140">**auto_ip_ptr**: указатель на блок управления AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-140">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5bc2e-141">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5bc2e-141">Return Values</span></span>

- <span data-ttu-id="5bc2e-142">**NX_SUCCESS** (0x00): экземпляр AutoIP успешно удален.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-142">**NX_SUCCESS**: (0x00) Successful AutoIP delete.</span></span>
- <span data-ttu-id="5bc2e-143">**NX_AUTO_IP_ERROR** (0XA00): ошибка удаления AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-143">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP delete error.</span></span>
- <span data-ttu-id="5bc2e-144">NX_PTR_ERROR (0x16): недопустимый указатель AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-144">NX_PTR_ERROR (0x16): Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="5bc2e-145">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект этой службы.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-145">NX_CALLER_ERROR (0x11): Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5bc2e-146">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5bc2e-146">Allowed From</span></span>

<span data-ttu-id="5bc2e-147">Потоки</span><span class="sxs-lookup"><span data-stu-id="5bc2e-147">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5bc2e-148">Пример</span><span class="sxs-lookup"><span data-stu-id="5bc2e-148">Example</span></span>

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="5bc2e-149">См. также:</span><span class="sxs-lookup"><span data-stu-id="5bc2e-149">See Also</span></span>

<span data-ttu-id="5bc2e-150">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="5bc2e-150">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_get_address"></a><span data-ttu-id="5bc2e-151">nx_auto_ip_get_address</span><span class="sxs-lookup"><span data-stu-id="5bc2e-151">nx_auto_ip_get_address</span></span>

<span data-ttu-id="5bc2e-152">Получение текущего адреса AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-152">Get current AutoIP address</span></span>

### <a name="prototype"></a><span data-ttu-id="5bc2e-153">Прототип</span><span class="sxs-lookup"><span data-stu-id="5bc2e-153">Prototype</span></span>

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a><span data-ttu-id="5bc2e-154">Описание</span><span class="sxs-lookup"><span data-stu-id="5bc2e-154">Description</span></span>

<span data-ttu-id="5bc2e-155">Эта служба получает текущий адрес конфигурации AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-155">This service retrieves the currently setup AutoIP address.</span></span> <span data-ttu-id="5bc2e-156">Если его нет, возвращается IP-адрес 0.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-156">If there isn't one, an IP address of 0.0.0.0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5bc2e-157">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="5bc2e-157">Input Parameters</span></span>

- <span data-ttu-id="5bc2e-158">**auto_ip_ptr**: указатель на блок управления AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-158">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="5bc2e-159">**local_ip_address**: назначение для обратного IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-159">**local_ip_address**: Destination for return IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="5bc2e-160">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5bc2e-160">Return Values</span></span>

- <span data-ttu-id="5bc2e-161">**NX_SUCCESS** (0x00): адрес AutoIP успешно получен.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-161">**NX_SUCCESS**: (0x00) Successful AutoIP address get.</span></span>
- <span data-ttu-id="5bc2e-162">**NX_AUTO_IP_NO_LOCAL** (0XA01): допустимый адрес AutoIP отсутствует.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-162">**NX_AUTO_IP_NO_LOCAL**: (0xA01) No valid AutoIP address.</span></span>
- <span data-ttu-id="5bc2e-163">NX_PTR_ERROR (0x16): недопустимый указатель AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-163">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="5bc2e-164">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-164">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5bc2e-165">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5bc2e-165">Allowed From</span></span>

<span data-ttu-id="5bc2e-166">Инициализация, таймеры, потоки, подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="5bc2e-166">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="5bc2e-167">Пример</span><span class="sxs-lookup"><span data-stu-id="5bc2e-167">Example</span></span>

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a><span data-ttu-id="5bc2e-168">См. также:</span><span class="sxs-lookup"><span data-stu-id="5bc2e-168">See Also</span></span>

<span data-ttu-id="5bc2e-169">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="5bc2e-169">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_set_interface"></a><span data-ttu-id="5bc2e-170">nx_auto_ip_set_interface</span><span class="sxs-lookup"><span data-stu-id="5bc2e-170">nx_auto_ip_set_interface</span></span>

<span data-ttu-id="5bc2e-171">Настройка сетевого интерфейса для AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-171">Set network interface for AutoIP</span></span>

### <a name="prototype"></a><span data-ttu-id="5bc2e-172">Прототип</span><span class="sxs-lookup"><span data-stu-id="5bc2e-172">Prototype</span></span>

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                                UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="5bc2e-173">Описание</span><span class="sxs-lookup"><span data-stu-id="5bc2e-173">Description</span></span>

<span data-ttu-id="5bc2e-174">Эта служба задает индекс для сетевого интерфейса, с помощью которого AutoIP который будет отправлять пробу на IP-адрес в сети.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-174">This service sets the index for the network interface AutoIP will probe for a network IP address.</span></span> <span data-ttu-id="5bc2e-175">Значение по умолчанию равно нулю (основной сетевой интерфейс).</span><span class="sxs-lookup"><span data-stu-id="5bc2e-175">The default is zero (the primary network interface).</span></span> <span data-ttu-id="5bc2e-176">Применимо только к многосетевым устройствам.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-176">Only applicable for multihomed devices.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5bc2e-177">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="5bc2e-177">Input Parameters</span></span>

- <span data-ttu-id="5bc2e-178">**auto_ip_ptr**: указатель на блок управления AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-178">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="5bc2e-179">**interface_index**: интерфейс для проверки IP-адреса с помощью пробы.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-179">**interface_index**: Interface to probe IP address for</span></span>

### <a name="return-values"></a><span data-ttu-id="5bc2e-180">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5bc2e-180">Return Values</span></span>

- <span data-ttu-id="5bc2e-181">**NX_SUCCESS** (0x00): интерфейс AutoIP успешно задан.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-181">**NX_SUCCESS**: (0x00) Successful AutoIP interface set</span></span>
- <span data-ttu-id="5bc2e-182">**NX_AUTO_IP_BAD_INTERFACE_INDEX** (0xA02): недопустимый сетевой интерфейс.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-182">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) Invalid network interface</span></span> 
- <span data-ttu-id="5bc2e-183">NX_PTR_ERROR (0x16): недопустимый указатель AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-183">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="5bc2e-184">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-184">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5bc2e-185">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5bc2e-185">Allowed From</span></span>

<span data-ttu-id="5bc2e-186">Инициализация, таймеры, потоки, подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="5bc2e-186">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="5bc2e-187">Пример</span><span class="sxs-lookup"><span data-stu-id="5bc2e-187">Example</span></span>

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block auto_ip_0. */
```

### <a name="see-also"></a><span data-ttu-id="5bc2e-188">См. также:</span><span class="sxs-lookup"><span data-stu-id="5bc2e-188">See Also</span></span>

<span data-ttu-id="5bc2e-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="5bc2e-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_start"></a><span data-ttu-id="5bc2e-190">nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="5bc2e-190">nx_auto_ip_start</span></span>

<span data-ttu-id="5bc2e-191">Начало обработки AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-191">Start AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="5bc2e-192">Прототип</span><span class="sxs-lookup"><span data-stu-id="5bc2e-192">Prototype</span></span>

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a><span data-ttu-id="5bc2e-193">Описание</span><span class="sxs-lookup"><span data-stu-id="5bc2e-193">Description</span></span>

<span data-ttu-id="5bc2e-194">Эта служба запускает протокол AutoIP на созданном ранее экземпляре AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-194">This service starts the AutoIP protocol on a previously created AutoIP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5bc2e-195">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="5bc2e-195">Input Parameters</span></span>

- <span data-ttu-id="5bc2e-196">**auto_ip_ptr**: указатель на блок управления AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-196">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="5bc2e-197">**starting_local_address**: необязательный начальный адрес AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-197">**starting_local_address**: Optional AutoIP starting address.</span></span> <span data-ttu-id="5bc2e-198">Значение IP_ADDRESS (0,0,0,0) указывает, что случайный адрес AutoIP должен быть производным.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-198">A value of IP_ADDRESS(0,0,0,0) specifies that a random AutoIP address should be derived.</span></span> <span data-ttu-id="5bc2e-199">В противном случае, если указан допустимый адрес AutoIP, NetX AutoIP попытается назначить этот адрес.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-199">Otherwise, if a valid AutoIP address is specified, NetX AutoIP attempts to assign that address.</span></span>

### <a name="return-values"></a><span data-ttu-id="5bc2e-200">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5bc2e-200">Return Values</span></span>

- <span data-ttu-id="5bc2e-201">**NX_SUCCESS** (0x00): протокол AutoIP успешно запущен.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-201">**NX_SUCCESS**: (0x00) Successful AutoIP start.</span></span>
- <span data-ttu-id="5bc2e-202">**NX_AUTO_IP_ERROR** (0XA00): ошибка запуска протокола AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-202">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP start error.</span></span>
- <span data-ttu-id="5bc2e-203">NX_PTR_ERROR (0x16): недопустимый указатель AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-203">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="5bc2e-204">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5bc2e-205">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5bc2e-205">Allowed From</span></span>

<span data-ttu-id="5bc2e-206">Инициализация, потоки.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-206">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="5bc2e-207">Пример</span><span class="sxs-lookup"><span data-stu-id="5bc2e-207">Example</span></span>

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="5bc2e-208">См. также:</span><span class="sxs-lookup"><span data-stu-id="5bc2e-208">See Also</span></span>

<span data-ttu-id="5bc2e-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="5bc2e-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_stop"></a><span data-ttu-id="5bc2e-210">nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="5bc2e-210">nx_auto_ip_stop</span></span>

<span data-ttu-id="5bc2e-211">Остановка обработки AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-211">Stop AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="5bc2e-212">Прототип</span><span class="sxs-lookup"><span data-stu-id="5bc2e-212">Prototype</span></span>

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="5bc2e-213">Описание</span><span class="sxs-lookup"><span data-stu-id="5bc2e-213">Description</span></span>

<span data-ttu-id="5bc2e-214">Эта служба останавливает протокол AutoIP на созданном ранее и запущенном экземпляре AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-214">This service stops the AutoIP protocol on a previously created and started AutoIP instance.</span></span> <span data-ttu-id="5bc2e-215">Эта служба обычно используется при изменении IP-адреса с помощью DHCP или вручную на адрес, отличный от AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-215">This service is typically used when the IP address is changed via DHCP or manually to a non-AutoIP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="5bc2e-216">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="5bc2e-216">Input Parameters</span></span>

- <span data-ttu-id="5bc2e-217">**auto_ip_ptr**: указатель на блок управления AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-217">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="5bc2e-218">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="5bc2e-218">Return Values</span></span>

- <span data-ttu-id="5bc2e-219">**NX_SUCCESS** (0x00): протокол AutoIP успешно остановлен.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-219">**NX_SUCCESS**: (0x00) Successful AutoIP stop.</span></span>
- <span data-ttu-id="5bc2e-220">**NX_AUTO_IP_ERROR** (0XA00): ошибка остановки протокола AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-220">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP stop error.</span></span>
- <span data-ttu-id="5bc2e-221">NX_PTR_ERROR (0x16): недопустимый указатель AutoIP.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-221">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="5bc2e-222">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="5bc2e-222">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="5bc2e-223">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="5bc2e-223">Allowed From</span></span>

<span data-ttu-id="5bc2e-224">Потоки</span><span class="sxs-lookup"><span data-stu-id="5bc2e-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="5bc2e-225">Пример</span><span class="sxs-lookup"><span data-stu-id="5bc2e-225">Example</span></span>

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="5bc2e-226">См. также:</span><span class="sxs-lookup"><span data-stu-id="5bc2e-226">See Also</span></span>

<span data-ttu-id="5bc2e-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="5bc2e-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span></span>