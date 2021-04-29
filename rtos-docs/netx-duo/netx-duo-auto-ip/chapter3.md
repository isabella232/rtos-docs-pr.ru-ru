---
title: Глава 3. Описание служб ОСРВ Azure NetX Duo AutoIP
description: В этой главе приведено описание всех служб ОСРВ Azure NetX Duo AutoIP, которые перечислены ниже в алфавитном порядке.
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 0935295ef9f7255c0851e1f64013884dce4c52f1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814831"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-autoip-services"></a><span data-ttu-id="a4c2d-103">Глава 3. Описание служб ОСРВ Azure NetX Duo AutoIP</span><span class="sxs-lookup"><span data-stu-id="a4c2d-103">Chapter 3 - Description of Azure RTOS NetX Duo AutoIP services</span></span>

<span data-ttu-id="a4c2d-104">В этой главе приведено описание всех служб ОСРВ Azure NetX Duo AutoIP, которые перечислены ниже в алфавитном порядке.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-104">This chapter contains a description of all Azure RTOS NetX Duo AutoIP services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="a4c2d-105">В разделе "Возвращаемые значения" для приведенных ниже описаний API значения, **выделенные полужирным шрифтом**, не затрагиваются определением **NX_DISABLE_ERROR_CHECKING**, используемым для отключения проверки ошибок API, в то время как значения, не выделенные полужирным шрифтом, полностью отключены.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-105">In the "Return Values" section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="a4c2d-106">**nx_auto_ip_create**: *создание экземпляра AutoIP*.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-106">**nx_auto_ip_create**: *Create AutoIP instance*</span></span>
- <span data-ttu-id="a4c2d-107">**nx_auto_ip_delete**: *удаление экземпляра AutoIP*.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-107">**nx_auto_ip_delete**: *Delete AutoIP instance*</span></span>
- <span data-ttu-id="a4c2d-108">**nx_auto_ip_get_address**: *получение текущего адреса AutoIP*.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-108">**nx_auto_ip_get_address**: *Get current AutoIP address*</span></span>
- <span data-ttu-id="a4c2d-109">**nx_auto_ip_set_interface**: *настройка интерфейса IP, требующего адрес AutoIP*.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-109">**nx_auto_ip_set_interface**: *Set IP interface needing an AutoIP address*</span></span>
- <span data-ttu-id="a4c2d-110">**nx_auto_ip_start**: *запуск обработки AutoIP*.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-110">**nx_auto_ip_start**: *Start AutoIP processing*</span></span>
- <span data-ttu-id="a4c2d-111">**nx_auto_ip_stop**: *завершение обработки AutoIP*.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-111">**nx_auto_ip_stop**: *Stop AutoIP processing*</span></span>

## <a name="nx_auto_ip_create"></a><span data-ttu-id="a4c2d-112">nx_auto_ip_create</span><span class="sxs-lookup"><span data-stu-id="a4c2d-112">nx_auto_ip_create</span></span>

<span data-ttu-id="a4c2d-113">Создание экземпляра AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-113">Create AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a4c2d-114">Прототип</span><span class="sxs-lookup"><span data-stu-id="a4c2d-114">Prototype</span></span>

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
                    NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
                    UINT priority);
```

### <a name="description"></a><span data-ttu-id="a4c2d-115">Описание</span><span class="sxs-lookup"><span data-stu-id="a4c2d-115">Description</span></span>

<span data-ttu-id="a4c2d-116">Эта служба создает экземпляр AutoIP по указанному экземпляру IP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-116">This service creates an AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a4c2d-117">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="a4c2d-117">Input Parameters</span></span>

- <span data-ttu-id="a4c2d-118">**auto_ip_ptr**: указатель на блок управления AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-118">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="a4c2d-119">**name**: имя экземпляра AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-119">**name**: Name of AutoIP instance.</span></span>
- <span data-ttu-id="a4c2d-120">**ip_ptr**: указатель на экземпляр IP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-120">**ip_ptr**: Pointer to IP instance.</span></span>
- <span data-ttu-id="a4c2d-121">**stack_ptr**: указатель на область стека потоков AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-121">**stack_ptr**: Pointer to AutoIP thread stack area.</span></span>
- <span data-ttu-id="a4c2d-122">**stack_size**: размер области стека потоков AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-122">**stack_size**: Size of the AutoIP thread stack area.</span></span>
- <span data-ttu-id="a4c2d-123">**priority**: приоритет потока AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-123">**priority**: Priority of the AutoIP thread.</span></span>

> [!NOTE]
> <span data-ttu-id="a4c2d-124">Если используется протокол DHCP, то поток DHCP должен иметь более высокий приоритет, чем поток экземпляра IP и поток AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-124">If DHCP is used, the DHCP thread must have a higher priority than the IP instance thread and the AutoIP thread.</span></span>

### <a name="return-values"></a><span data-ttu-id="a4c2d-125">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="a4c2d-125">Return Values</span></span>

- <span data-ttu-id="a4c2d-126">**NX_SUCCESS** (0x00): экземпляр AutoIP успешно создан.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-126">**NX_SUCCESS**: (0x00) Successful AutoIP create.</span></span>
- <span data-ttu-id="a4c2d-127">**NX_AUTO_IP_ERROR** (0XA00): ошибка создания AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-127">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP create error.</span></span>
- <span data-ttu-id="a4c2d-128">NX_PTR_ERROR: (0x16): недопустимый указатель AutoIP, ip_ptr или указатель стека.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-128">NX_PTR_ERROR: (0x16) Invalid AutoIP, ip_ptr, or stack pointer.</span></span>
- <span data-ttu-id="a4c2d-129">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-129">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a4c2d-130">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="a4c2d-130">Allowed From</span></span>

<span data-ttu-id="a4c2d-131">Инициализация, потоки.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-131">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a4c2d-132">Пример</span><span class="sxs-lookup"><span data-stu-id="a4c2d-132">Example</span></span>

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a><span data-ttu-id="a4c2d-133">См. также:</span><span class="sxs-lookup"><span data-stu-id="a4c2d-133">See Also</span></span>

<span data-ttu-id="a4c2d-134">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="a4c2d-134">nx_auto_ip_delete, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_delete"></a><span data-ttu-id="a4c2d-135">nx_auto_ip_delete</span><span class="sxs-lookup"><span data-stu-id="a4c2d-135">nx_auto_ip_delete</span></span>

<span data-ttu-id="a4c2d-136">Удаление экземпляра AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-136">Delete AutoIP instance</span></span>

### <a name="prototype"></a><span data-ttu-id="a4c2d-137">Прототип</span><span class="sxs-lookup"><span data-stu-id="a4c2d-137">Prototype</span></span>

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a4c2d-138">Описание</span><span class="sxs-lookup"><span data-stu-id="a4c2d-138">Description</span></span>

<span data-ttu-id="a4c2d-139">Эта служба удаляет созданный ранее экземпляр AutoIP по указанному экземпляру IP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-139">This service deletes a previously created AutoIP instance on the specified IP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a4c2d-140">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="a4c2d-140">Input Parameters</span></span>

- <span data-ttu-id="a4c2d-141">**auto_ip_ptr**: указатель на блок управления AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-141">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a4c2d-142">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="a4c2d-142">Return Values</span></span>

- <span data-ttu-id="a4c2d-143">**NX_SUCCESS** (0x00): экземпляр AutoIP успешно удален.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-143">**NX_SUCCESS**: (0x00) Successful AutoIP delete.</span></span>
- <span data-ttu-id="a4c2d-144">**NX_AUTO_IP_ERROR** (0XA00): ошибка удаления AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-144">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP delete error.</span></span>
- <span data-ttu-id="a4c2d-145">NX_PTR_ERROR (0x16): недопустимый указатель AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-145">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="a4c2d-146">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-146">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a4c2d-147">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="a4c2d-147">Allowed From</span></span>

<span data-ttu-id="a4c2d-148">Потоки</span><span class="sxs-lookup"><span data-stu-id="a4c2d-148">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a4c2d-149">Пример</span><span class="sxs-lookup"><span data-stu-id="a4c2d-149">Example</span></span>

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a><span data-ttu-id="a4c2d-150">См. также:</span><span class="sxs-lookup"><span data-stu-id="a4c2d-150">See Also</span></span>

<span data-ttu-id="a4c2d-151">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="a4c2d-151">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_get_address, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_get_address"></a><span data-ttu-id="a4c2d-152">nx_auto_ip_get_address</span><span class="sxs-lookup"><span data-stu-id="a4c2d-152">nx_auto_ip_get_address</span></span>

<span data-ttu-id="a4c2d-153">Получение текущего адреса AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-153">Get current AutoIP address</span></span>

### <a name="prototype"></a><span data-ttu-id="a4c2d-154">Прототип</span><span class="sxs-lookup"><span data-stu-id="a4c2d-154">Prototype</span></span>

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a><span data-ttu-id="a4c2d-155">Описание</span><span class="sxs-lookup"><span data-stu-id="a4c2d-155">Description</span></span>

<span data-ttu-id="a4c2d-156">Эта служба получает текущий адрес конфигурации AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-156">This service retrieves the currently setup AutoIP address.</span></span> <span data-ttu-id="a4c2d-157">Если его нет, возвращается IP-адрес 0.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-157">If there isn't one, an IP address of 0.0.0.0 is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a4c2d-158">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="a4c2d-158">Input Parameters</span></span>

- <span data-ttu-id="a4c2d-159">**auto_ip_ptr**: указатель на блок управления AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-159">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="a4c2d-160">**local_ip_address**: назначение для обратного IP-адреса.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-160">**local_ip_address**: Destination for return IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="a4c2d-161">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="a4c2d-161">Return Values</span></span>

- <span data-ttu-id="a4c2d-162">**NX_SUCCESS** (0x00): адрес AutoIP успешно получен.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-162">**NX_SUCCESS**: (0x00) Successful AutoIP address get.</span></span>
- <span data-ttu-id="a4c2d-163">**NX_AUTO_IP_NO_LOCAL** (0XA01): допустимый адрес AutoIP отсутствует.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-163">**NX_AUTO_IP_NO_LOCAL**: (0xA01) No valid AutoIP address.</span></span>
- <span data-ttu-id="a4c2d-164">NX_PTR_ERROR (0x16): недопустимый указатель AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-164">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="a4c2d-165">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-165">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a4c2d-166">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="a4c2d-166">Allowed From</span></span>

<span data-ttu-id="a4c2d-167">Инициализация, таймеры, потоки, подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="a4c2d-167">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="a4c2d-168">Пример</span><span class="sxs-lookup"><span data-stu-id="a4c2d-168">Example</span></span>

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a><span data-ttu-id="a4c2d-169">См. также:</span><span class="sxs-lookup"><span data-stu-id="a4c2d-169">See Also</span></span>

<span data-ttu-id="a4c2d-170">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="a4c2d-170">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_set_interface"></a><span data-ttu-id="a4c2d-171">nx_auto_ip_set_interface</span><span class="sxs-lookup"><span data-stu-id="a4c2d-171">nx_auto_ip_set_interface</span></span>

<span data-ttu-id="a4c2d-172">Настройка сетевого интерфейса для AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-172">Set network interface for AutoIP</span></span>

### <a name="prototype"></a><span data-ttu-id="a4c2d-173">Прототип</span><span class="sxs-lookup"><span data-stu-id="a4c2d-173">Prototype</span></span>

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                            UINT interface_index);
```

### <a name="description"></a><span data-ttu-id="a4c2d-174">Описание</span><span class="sxs-lookup"><span data-stu-id="a4c2d-174">Description</span></span>

<span data-ttu-id="a4c2d-175">Эта служба задает индекс для сетевого интерфейса, с помощью которого AutoIP который будет отправлять пробу на IP-адрес в сети.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-175">This service sets the index for the network interface AutoIP will probe for a network IP address.</span></span> <span data-ttu-id="a4c2d-176">Значение по умолчанию равно нулю (основной сетевой интерфейс).</span><span class="sxs-lookup"><span data-stu-id="a4c2d-176">The default is zero (the primary network interface).</span></span> <span data-ttu-id="a4c2d-177">Применимо только к многосетевым устройствам.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-177">Only applicable for multihomed devices.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a4c2d-178">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="a4c2d-178">Input Parameters</span></span>

- <span data-ttu-id="a4c2d-179">**auto_ip_ptr**: указатель на блок управления AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-179">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="a4c2d-180">**interface_index**: интерфейс для проверки IP-адреса с помощью пробы.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-180">**interface_index**: Interface to probe IP address for</span></span>

### <a name="return-values"></a><span data-ttu-id="a4c2d-181">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="a4c2d-181">Return Values</span></span>

- <span data-ttu-id="a4c2d-182">**NX_SUCCESS** (0x00): интерфейс AutoIP успешно задан.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-182">**NX_SUCCESS**: (0x00) Successful AutoIP interface set</span></span>
- <span data-ttu-id="a4c2d-183">**NX_AUTO_IP_BAD_INTERFACE_INDEX** (0xA02): недопустимый сетевой интерфейс. NX_PTR_ERROR (0x16): недопустимый указатель AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-183">**NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) Invalid network interface NX_PTR_ERROR (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="a4c2d-184">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-184">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a4c2d-185">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="a4c2d-185">Allowed From</span></span>

<span data-ttu-id="a4c2d-186">Инициализация, таймеры, потоки, подпрограммы ISR</span><span class="sxs-lookup"><span data-stu-id="a4c2d-186">Initialization, Timers, Threads, ISRs</span></span>

### <a name="example"></a><span data-ttu-id="a4c2d-187">Пример</span><span class="sxs-lookup"><span data-stu-id="a4c2d-187">Example</span></span>

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block *auto_ip_0*. */
```

### <a name="see-also"></a><span data-ttu-id="a4c2d-188">См. также:</span><span class="sxs-lookup"><span data-stu-id="a4c2d-188">See Also</span></span>

<span data-ttu-id="a4c2d-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="a4c2d-189">nx_auto_ip_create, nx_auto_ip_get_address, nx_auto_ip_delete, nx_auto_ip_start, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_start"></a><span data-ttu-id="a4c2d-190">nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="a4c2d-190">nx_auto_ip_start</span></span>

<span data-ttu-id="a4c2d-191">Начало обработки AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-191">Start AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="a4c2d-192">Прототип</span><span class="sxs-lookup"><span data-stu-id="a4c2d-192">Prototype</span></span>

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a><span data-ttu-id="a4c2d-193">Описание</span><span class="sxs-lookup"><span data-stu-id="a4c2d-193">Description</span></span>

<span data-ttu-id="a4c2d-194">Эта служба запускает протокол AutoIP на созданном ранее экземпляре AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-194">This service starts the AutoIP protocol on a previously created AutoIP instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a4c2d-195">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="a4c2d-195">Input Parameters</span></span>

- <span data-ttu-id="a4c2d-196">**auto_ip_ptr**: указатель на блок управления AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-196">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>
- <span data-ttu-id="a4c2d-197">**starting_local_address**: необязательный начальный адрес AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-197">**starting_local_address**: Optional AutoIP starting address.</span></span> <span data-ttu-id="a4c2d-198">Значение IP_ADDRESS (0,0,0,0) указывает, что случайный адрес AutoIP должен быть производным.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-198">A value of IP_ADDRESS(0,0,0,0) specifies that a random AutoIP address should be derived.</span></span> <span data-ttu-id="a4c2d-199">В противном случае, если указан допустимый адрес AutoIP, NetX AutoIP попытается назначить этот адрес.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-199">Otherwise, if a valid AutoIP address is specified, NetX AutoIP attempts to assign that address.</span></span>

### <a name="return-values"></a><span data-ttu-id="a4c2d-200">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="a4c2d-200">Return Values</span></span>

- <span data-ttu-id="a4c2d-201">**NX_SUCCESS** (0x00): протокол AutoIP успешно запущен.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-201">**NX_SUCCESS**: (0x00) Successful AutoIP start.</span></span>
- <span data-ttu-id="a4c2d-202">**NX_AUTO_IP_ERROR** (0XA00): ошибка запуска протокола AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-202">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP start error.</span></span>
- <span data-ttu-id="a4c2d-203">NX_PTR_ERROR (0x16): недопустимый указатель AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-203">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="a4c2d-204">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-204">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a4c2d-205">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="a4c2d-205">Allowed From</span></span>

<span data-ttu-id="a4c2d-206">Инициализация, потоки.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-206">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="a4c2d-207">Пример</span><span class="sxs-lookup"><span data-stu-id="a4c2d-207">Example</span></span>

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a><span data-ttu-id="a4c2d-208">См. также:</span><span class="sxs-lookup"><span data-stu-id="a4c2d-208">See Also</span></span>

<span data-ttu-id="a4c2d-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="a4c2d-209">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_stop</span></span>

## <a name="nx_auto_ip_stop"></a><span data-ttu-id="a4c2d-210">nx_auto_ip_stop</span><span class="sxs-lookup"><span data-stu-id="a4c2d-210">nx_auto_ip_stop</span></span>

<span data-ttu-id="a4c2d-211">Остановка обработки AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-211">Stop AutoIP processing</span></span>

### <a name="prototype"></a><span data-ttu-id="a4c2d-212">Прототип</span><span class="sxs-lookup"><span data-stu-id="a4c2d-212">Prototype</span></span>

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a><span data-ttu-id="a4c2d-213">Описание</span><span class="sxs-lookup"><span data-stu-id="a4c2d-213">Description</span></span>

<span data-ttu-id="a4c2d-214">Эта служба останавливает протокол AutoIP на созданном ранее и запущенном экземпляре AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-214">This service stops the AutoIP protocol on a previously created and started AutoIP instance.</span></span> <span data-ttu-id="a4c2d-215">Эта служба обычно используется при изменении IP-адреса с помощью DHCP или вручную на адрес, отличный от AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-215">This service is typically used when the IP address is changed via DHCP or manually to a non-AutoIP address.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="a4c2d-216">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="a4c2d-216">Input Parameters</span></span>

- <span data-ttu-id="a4c2d-217">**auto_ip_ptr**: указатель на блок управления AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-217">**auto_ip_ptr**: Pointer to AutoIP control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="a4c2d-218">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="a4c2d-218">Return Values</span></span>

- <span data-ttu-id="a4c2d-219">**NX_SUCCESS** (0x00): протокол AutoIP успешно остановлен.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-219">**NX_SUCCESS**: (0x00) Successful AutoIP stop.</span></span>
- <span data-ttu-id="a4c2d-220">**NX_AUTO_IP_ERROR** (0XA00): ошибка остановки протокола AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-220">**NX_AUTO_IP_ERROR**: (0xA00) AutoIP stop error.</span></span>
- <span data-ttu-id="a4c2d-221">NX_PTR_ERROR (0x16): недопустимый указатель AutoIP.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-221">NX_PTR_ERROR: (0x16) Invalid AutoIP pointer.</span></span>
- <span data-ttu-id="a4c2d-222">NX_CALLER_ERROR (0x11): недопустимый вызывающий объект для этой службы.</span><span class="sxs-lookup"><span data-stu-id="a4c2d-222">NX_CALLER_ERROR: (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="a4c2d-223">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="a4c2d-223">Allowed From</span></span>

<span data-ttu-id="a4c2d-224">Потоки</span><span class="sxs-lookup"><span data-stu-id="a4c2d-224">Threads</span></span>

### <a name="example"></a><span data-ttu-id="a4c2d-225">Пример</span><span class="sxs-lookup"><span data-stu-id="a4c2d-225">Example</span></span>

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a><span data-ttu-id="a4c2d-226">См. также:</span><span class="sxs-lookup"><span data-stu-id="a4c2d-226">See Also</span></span>

<span data-ttu-id="a4c2d-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span><span class="sxs-lookup"><span data-stu-id="a4c2d-227">nx_auto_ip_create, nx_auto_ip_set_interface, nx_auto_ip_delete, nx_auto_ip_get_address, nx_auto_ip_start</span></span>