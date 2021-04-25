---
title: Глава 4. API-интерфейсы модуля
author: philmea
ms.author: philmea
description: В этой статье приведена сводка дополнительных API-интерфейсов, доступных для модуля.
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b5804e2dbb8d08a272abc85a583576f43b7204c1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814379"
---
# <a name="chapter-4---module-apis"></a><span data-ttu-id="dd88f-103">Глава 4. API-интерфейсы модуля</span><span class="sxs-lookup"><span data-stu-id="dd88f-103">Chapter 4 - Module APIs</span></span>

## <a name="summary-of-module-apis"></a><span data-ttu-id="dd88f-104">Общие сведения об API-интерфейсах модуля</span><span class="sxs-lookup"><span data-stu-id="dd88f-104">Summary of Module APIs</span></span>

<span data-ttu-id="dd88f-105">Существует несколько дополнительных функций API, которые доступны для модуля:</span><span class="sxs-lookup"><span data-stu-id="dd88f-105">There are several additional API functions available to a module, as follows:</span></span>

- <span data-ttu-id="dd88f-106">***txm_module_application_request** _ — _специфичный для приложения запрос к резидентному коду*</span><span class="sxs-lookup"><span data-stu-id="dd88f-106">***txm_module_application_request** _ - _Application-specific request to resident code*</span></span>
- <span data-ttu-id="dd88f-107">\***txm_module_object_allocate** _ — _выделение для объекта памяти вне модуля \*</span><span class="sxs-lookup"><span data-stu-id="dd88f-107">***txm_module_object_allocate** _ - _Allocate memory outside of module for object*</span></span>
- <span data-ttu-id="dd88f-108">***txm_module_object_deallocate** _ — _освобождение ранее выделенной памяти объекта*</span><span class="sxs-lookup"><span data-stu-id="dd88f-108">***txm_module_object_deallocate** _ - _Deallocate previously allocated object memory*</span></span>
- <span data-ttu-id="dd88f-109">***txm_module_object_pointer_get** _ — _поиск системного объекта и получение указателя на него*</span><span class="sxs-lookup"><span data-stu-id="dd88f-109">***txm_module_object_pointer_get** _ - _Find system object and retrieve object pointer*</span></span>
- <span data-ttu-id="dd88f-110">***txm_module_object_pointer_get_extended** _ — _поиск системного объекта и получение указателя на него, безопасность длины имени*</span><span class="sxs-lookup"><span data-stu-id="dd88f-110">***txm_module_object_pointer_get_extended** _ - _Find system object and retrieve object pointer, name length safety*</span></span>

## <a name="return-values"></a><span data-ttu-id="dd88f-111">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="dd88f-111">Return values</span></span>

<span data-ttu-id="dd88f-112">Для некоторых API-интерфейсов ОСРВ Azure возвращаются дополнительные коды ошибок.</span><span class="sxs-lookup"><span data-stu-id="dd88f-112">Additional error codes are returned for some Azure RTOS APIs.</span></span> <span data-ttu-id="dd88f-113">Эти дополнительные коды ошибок определяются следующим образом.</span><span class="sxs-lookup"><span data-stu-id="dd88f-113">These additional error codes are defined as follows:</span></span>

- <span data-ttu-id="dd88f-114">**TXM_MODULE_INVALID_PROPERTIES** (0xF3): указывает, что модуль не имеет нужных свойств для вызова API.</span><span class="sxs-lookup"><span data-stu-id="dd88f-114">**TXM_MODULE_INVALID_PROPERTIES** (0xF3): Indicates the module does not have the correct properties to make an API call.</span></span> <span data-ttu-id="dd88f-115">Например, вызов API трассировки в пользовательском режиме.</span><span class="sxs-lookup"><span data-stu-id="dd88f-115">For example, calling trace APIs in user mode.</span></span>
- <span data-ttu-id="dd88f-116">**TXM_MODULE_INVALID_MEMORY** (0xF4): указывает, что память, предоставленная модулем, недопустима или находится в недопустимом расположении.</span><span class="sxs-lookup"><span data-stu-id="dd88f-116">**TXM_MODULE_INVALID_MEMORY** (0xF4): Indicates the memory supplied by the module is invalid or is in an invalid location.</span></span> <span data-ttu-id="dd88f-117">Например, в модулях с защищенной памятью блоки управления объектами не разрешается размещать в памяти, к которой может обращаться модуль.</span><span class="sxs-lookup"><span data-stu-id="dd88f-117">For example, in memory protected modules, object control blocks are not allowed to be located in memory the module can access.</span></span>
- <span data-ttu-id="dd88f-118">**TXM_MODULE_INVALID_CALLBACK** (0xF5): обратный вызов, указанный в API, находится за пределами диапазона кода модуля и поэтому является недопустимым.</span><span class="sxs-lookup"><span data-stu-id="dd88f-118">**TXM_MODULE_INVALID_CALLBACK** (0xF5): Callback specified in the API is outside the range of the module's code and is therefore invalid.</span></span>

---

## <a name="txm_module_application_request"></a><span data-ttu-id="dd88f-119">txm_module_application_request</span><span class="sxs-lookup"><span data-stu-id="dd88f-119">txm_module_application_request</span></span>

<span data-ttu-id="dd88f-120">Специфичный для приложения запрос к резидентному коду.</span><span class="sxs-lookup"><span data-stu-id="dd88f-120">Application-specific request to resident code.</span></span>

### <a name="prototype"></a><span data-ttu-id="dd88f-121">Прототип</span><span class="sxs-lookup"><span data-stu-id="dd88f-121">Prototype</span></span>

```c
UINT txm_module_application_request(
    ULONG request, 
    ULONG param_1,
    ULONG param_2,
    ULONG param_3);
```

### <a name="description"></a><span data-ttu-id="dd88f-122">Описание</span><span class="sxs-lookup"><span data-stu-id="dd88f-122">Description</span></span>

<span data-ttu-id="dd88f-123">Эта служба выполняет указанный запрос в резидентной части приложения.</span><span class="sxs-lookup"><span data-stu-id="dd88f-123">This service makes the specified request to the resident portion of the application.</span></span> <span data-ttu-id="dd88f-124">Предполагается, что структура запроса подготовлена перед вызовом.</span><span class="sxs-lookup"><span data-stu-id="dd88f-124">It is assumed that the request structure is prepared prior to the call.</span></span> <span data-ttu-id="dd88f-125">Фактическая обработка запроса происходит в резидентном коде в функции ***_txm_module_manager_application_request***.</span><span class="sxs-lookup"><span data-stu-id="dd88f-125">The actual processing of the request takes place in the resident code in the function ***_txm_module_manager_application_request***.</span></span> <span data-ttu-id="dd88f-126">По умолчанию эта функция оставлена пустой и предназначена для изменения разработчиком резидентных приложений.</span><span class="sxs-lookup"><span data-stu-id="dd88f-126">By default, this function is left empty and is designed for the resident application developer to modify.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dd88f-127">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="dd88f-127">Input parameters</span></span>

- <span data-ttu-id="dd88f-128">**request** — идентификатор запроса (определяется приложением).</span><span class="sxs-lookup"><span data-stu-id="dd88f-128">**request** Request ID (application defined)</span></span>
- <span data-ttu-id="dd88f-129">**param_1** — первый параметр.</span><span class="sxs-lookup"><span data-stu-id="dd88f-129">**param_1** First parameter</span></span>
- <span data-ttu-id="dd88f-130">**param_2** — второй параметр.</span><span class="sxs-lookup"><span data-stu-id="dd88f-130">**param_2** Second parameter</span></span>
- <span data-ttu-id="dd88f-131">**param_3** — третий параметр.</span><span class="sxs-lookup"><span data-stu-id="dd88f-131">**param_3** Third parameter</span></span>

### <a name="return-values"></a><span data-ttu-id="dd88f-132">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="dd88f-132">Return values</span></span>

- <span data-ttu-id="dd88f-133">**TX_SUCCESS** (0x00) — успешный запрос.</span><span class="sxs-lookup"><span data-stu-id="dd88f-133">**TX_SUCCESS** (0x00) Successful request.</span></span>
- <span data-ttu-id="dd88f-134">**TX_NOT_AVAILABLE** (0x1D) — запрос не поддерживается резидентным кодом.</span><span class="sxs-lookup"><span data-stu-id="dd88f-134">**TX_NOT_AVAILABLE** (0x1D) Request not supported by resident code.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dd88f-135">Разрешено из</span><span class="sxs-lookup"><span data-stu-id="dd88f-135">Allowed from</span></span>

<span data-ttu-id="dd88f-136">Потоки модулей</span><span class="sxs-lookup"><span data-stu-id="dd88f-136">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="dd88f-137">Например, .</span><span class="sxs-lookup"><span data-stu-id="dd88f-137">Example</span></span>

```c
/* Call application resident code with ID=77 and the
   parameters set to 1, 2, 3. */
status = txm_module_application_request(77, 1, 2, 3);

/* If status is TX_SUCCESS the request was successful. */
```

---

## <a name="txm_module_object_allocate"></a><span data-ttu-id="dd88f-138">txm_module_object_allocate</span><span class="sxs-lookup"><span data-stu-id="dd88f-138">txm_module_object_allocate</span></span>

<span data-ttu-id="dd88f-139">Выделение памяти в пуле объектов (созданном резидентным приложением) для блока управления объекта модуля.</span><span class="sxs-lookup"><span data-stu-id="dd88f-139">Allocate memory in the object pool (created by the resident application) for a module object control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="dd88f-140">Прототип</span><span class="sxs-lookup"><span data-stu-id="dd88f-140">Prototype</span></span>

```c
UINT txm_module_object_allocate(
   VOID **object_ptr, 
   ULONG object_size);
```

### <a name="description"></a><span data-ttu-id="dd88f-141">Описание</span><span class="sxs-lookup"><span data-stu-id="dd88f-141">Description</span></span>

<span data-ttu-id="dd88f-142">Эта служба выделяет память для объекта модуля из памяти за пределами модуля, что помогает предотвратить повреждение блока управления объектами кодом модуля.</span><span class="sxs-lookup"><span data-stu-id="dd88f-142">This service allocates memory for a module object from memory outside of the module, which helps prevent corruption of the object control block by the module's code.</span></span> <span data-ttu-id="dd88f-143">В системах с защитой памяти все блоки управления объектами должны быть выделены с помощью этого API, прежде чем их можно будет создать.</span><span class="sxs-lookup"><span data-stu-id="dd88f-143">In memory protected systems, all object control blocks must be allocated with this API before they can be created.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dd88f-144">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="dd88f-144">Input parameters</span></span>

- <span data-ttu-id="dd88f-145">**object_ptr** — назначение указателя объекта при успешном выделении.</span><span class="sxs-lookup"><span data-stu-id="dd88f-145">**object_ptr** Destination of object pointer on successful allocation.</span></span>
- <span data-ttu-id="dd88f-146">**object_size** — размер выделяемого объекта в байтах.</span><span class="sxs-lookup"><span data-stu-id="dd88f-146">**object_size** Size in bytes of the object to be allocated.</span></span>

### <a name="return-values"></a><span data-ttu-id="dd88f-147">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="dd88f-147">Return values</span></span>

- <span data-ttu-id="dd88f-148">**TX_SUCCESS** (0x00) — успешное выделение объекта.</span><span class="sxs-lookup"><span data-stu-id="dd88f-148">**TX_SUCCESS** (0x00) Successful object allocate.</span></span>
- <span data-ttu-id="dd88f-149">**TX_NO_MEMORY** (0x10) — недостаточно памяти.</span><span class="sxs-lookup"><span data-stu-id="dd88f-149">**TX_NO_MEMORY** (0x10) Not enough memory.</span></span>
- <span data-ttu-id="dd88f-150">**TX_NOT_AVAILABLE** (0x1D) — диспетчер модулей не создал пул объектов для выделения.</span><span class="sxs-lookup"><span data-stu-id="dd88f-150">**TX_NOT_AVAILABLE** (0x1D) Module manager has not created an object pool to allocate from</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dd88f-151">Разрешено из</span><span class="sxs-lookup"><span data-stu-id="dd88f-151">Allowed from</span></span>

<span data-ttu-id="dd88f-152">Потоки модулей</span><span class="sxs-lookup"><span data-stu-id="dd88f-152">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="dd88f-153">Пример</span><span class="sxs-lookup"><span data-stu-id="dd88f-153">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Allocate a control block for a module message queue. */
status = txm_module_object_allocate(&queue_pointer, sizeof(TX_QUEUE));

/* If status is TX_SUCCESS the queue_pointer points to
   memory allocated outside of the module and can be supplied
   to tx_queue_create to create a queue for the module. */
```

### <a name="see-also"></a><span data-ttu-id="dd88f-154">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="dd88f-154">See also</span></span>

- <span data-ttu-id="dd88f-155">txm_module_object_deallocate</span><span class="sxs-lookup"><span data-stu-id="dd88f-155">txm_module_object_deallocate</span></span>
- <span data-ttu-id="dd88f-156">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="dd88f-156">txm_module_object_pointer_get</span></span>

---

## <a name="txm_module_object_deallocate"></a><span data-ttu-id="dd88f-157">txm_module_object_deallocate</span><span class="sxs-lookup"><span data-stu-id="dd88f-157">txm_module_object_deallocate</span></span>

<span data-ttu-id="dd88f-158">Освобождение памяти выделенного ранее объекта</span><span class="sxs-lookup"><span data-stu-id="dd88f-158">Deallocate previously allocated object memory</span></span>

### <a name="prototype"></a><span data-ttu-id="dd88f-159">Прототип</span><span class="sxs-lookup"><span data-stu-id="dd88f-159">Prototype</span></span>

```c
UINT txm_module_object_deallocate(VOID *object_ptr);
```

### <a name="description"></a><span data-ttu-id="dd88f-160">Описание</span><span class="sxs-lookup"><span data-stu-id="dd88f-160">Description</span></span>

<span data-ttu-id="dd88f-161">***Эта служба устарела, так как в ней нет больше необходимости***.</span><span class="sxs-lookup"><span data-stu-id="dd88f-161">***This service has been deprecated because it is no longer needed***.</span></span>

<span data-ttu-id="dd88f-162">Память, выделенная ранее с помощью \*\**txm_module_object_allocate* *_, освобождается в службе _* _tx_\__delete\*\*\*.</span><span class="sxs-lookup"><span data-stu-id="dd88f-162">The memory that was previously allocated via ***txm_module_object_allocate\**_ is deallocated in the _*_tx_\__delete service***.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dd88f-163">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="dd88f-163">Input parameters</span></span>

- <span data-ttu-id="dd88f-164">**object_ptr** — указатель объекта для освобождения.</span><span class="sxs-lookup"><span data-stu-id="dd88f-164">**object_ptr** Object pointer to deallocate.</span></span>

### <a name="return-values"></a><span data-ttu-id="dd88f-165">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="dd88f-165">Return values</span></span>

- <span data-ttu-id="dd88f-166">**TX_SUCCESS** (0x00) — успешное выделение объекта.</span><span class="sxs-lookup"><span data-stu-id="dd88f-166">**TX_SUCCESS** (0x00) Successful object allocate.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dd88f-167">Разрешено из</span><span class="sxs-lookup"><span data-stu-id="dd88f-167">Allowed from</span></span>

<span data-ttu-id="dd88f-168">Потоки модулей</span><span class="sxs-lookup"><span data-stu-id="dd88f-168">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="dd88f-169">Пример</span><span class="sxs-lookup"><span data-stu-id="dd88f-169">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Deallocate control block for a module message queue. */
status = txm_module_object_deallocate(queue_pointer);

/* If status is TX_SUCCESS the object memory associated
   with queue_pointer is deallocated. */
```

### <a name="see-also"></a><span data-ttu-id="dd88f-170">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="dd88f-170">See also</span></span>

- <span data-ttu-id="dd88f-171">txm_module_object_allocate</span><span class="sxs-lookup"><span data-stu-id="dd88f-171">txm_module_object_allocate</span></span>
- <span data-ttu-id="dd88f-172">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="dd88f-172">txm_module_object_pointer_get</span></span>

---

## <a name="txm_module_object_pointer_get"></a><span data-ttu-id="dd88f-173">txm_module_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="dd88f-173">txm_module_object_pointer_get</span></span>

<span data-ttu-id="dd88f-174">Поиск системного объекта и получение указателя на него</span><span class="sxs-lookup"><span data-stu-id="dd88f-174">Find system object and retrieve object pointer</span></span>

### <a name="prototype"></a><span data-ttu-id="dd88f-175">Прототип</span><span class="sxs-lookup"><span data-stu-id="dd88f-175">Prototype</span></span>

```c
UINT txm_module_object_pointer_get(
   UINT object_type, CHAR *name, 
   VOID **object_ptr);
```

### <a name="description"></a><span data-ttu-id="dd88f-176">Описание</span><span class="sxs-lookup"><span data-stu-id="dd88f-176">Description</span></span>

<span data-ttu-id="dd88f-177">Эта служба получает указатель объекта определенного типа с определенным именем.</span><span class="sxs-lookup"><span data-stu-id="dd88f-177">This service retrieves the object pointer of a particular type with a particular name.</span></span> <span data-ttu-id="dd88f-178">Если объект не найден, возвращается ошибка.</span><span class="sxs-lookup"><span data-stu-id="dd88f-178">If the object is not found, an error is returned.</span></span> <span data-ttu-id="dd88f-179">В противном случае, если объект найден, адрес этого объекта помещается в "object_ptr".</span><span class="sxs-lookup"><span data-stu-id="dd88f-179">Otherwise, if the object is found, the address of that object is placed in "object_ptr."</span></span> <span data-ttu-id="dd88f-180">Этот указатель можно затем использовать для вызова системных служб, взаимодействия с резидентным кодом и (или) другими загруженными модулями в системе.</span><span class="sxs-lookup"><span data-stu-id="dd88f-180">This pointer can then be used to make system service calls, to interact with the resident code, and/or other loaded modules in the system.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dd88f-181">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="dd88f-181">Input parameters</span></span>

- <span data-ttu-id="dd88f-182">**object_type** — тип запрошенного объекта ThreadX.</span><span class="sxs-lookup"><span data-stu-id="dd88f-182">**object_type** Type of ThreadX object requested.</span></span> <span data-ttu-id="dd88f-183">Допустимые типы:</span><span class="sxs-lookup"><span data-stu-id="dd88f-183">Valid types are as follows:</span></span>
  - <span data-ttu-id="dd88f-184">TXM_BLOCK_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-184">TXM_BLOCK_POOL_OBJECT</span></span>
  - <span data-ttu-id="dd88f-185">TXM_BYTE_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-185">TXM_BYTE_POOL_OBJECT</span></span>
  - <span data-ttu-id="dd88f-186">TXM_EVENT_FLAGS_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-186">TXM_EVENT_FLAGS_OBJECT</span></span>
  - <span data-ttu-id="dd88f-187">TXM_MUTEX_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-187">TXM_MUTEX_OBJECT</span></span>
  - <span data-ttu-id="dd88f-188">TXM_QUEUE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-188">TXM_QUEUE_OBJECT</span></span>
  - <span data-ttu-id="dd88f-189">TXM_SEMAPHORE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-189">TXM_SEMAPHORE_OBJECT</span></span>
  - <span data-ttu-id="dd88f-190">TXM_THREAD_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-190">TXM_THREAD_OBJECT</span></span>
  - <span data-ttu-id="dd88f-191">TXM_TIMER_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-191">TXM_TIMER_OBJECT</span></span>
  - <span data-ttu-id="dd88f-192">TXM_IP_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-192">TXM_IP_OBJECT</span></span>
  - <span data-ttu-id="dd88f-193">TXM_PACKET_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-193">TXM_PACKET_POOL_OBJECT</span></span>
  - <span data-ttu-id="dd88f-194">TXM_UDP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-194">TXM_UDP_SOCKET_OBJECT</span></span>
  - <span data-ttu-id="dd88f-195">TXM_TCP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-195">TXM_TCP_SOCKET_OBJECT</span></span>
- <span data-ttu-id="dd88f-196">**name** — имя объекта, специфичное для приложения, как определено при создании объекта.</span><span class="sxs-lookup"><span data-stu-id="dd88f-196">**name** Application-specific object name as defined when the object was created.</span></span>
- <span data-ttu-id="dd88f-197">**object_ptr** — назначение для указателя объекта.</span><span class="sxs-lookup"><span data-stu-id="dd88f-197">**object_ptr** Destination for object pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="dd88f-198">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="dd88f-198">Return values</span></span>

- <span data-ttu-id="dd88f-199">**TX_SUCCESS** (0x00) — успешное получение объекта.</span><span class="sxs-lookup"><span data-stu-id="dd88f-199">**TX_SUCCESS** (0x00) Successful object get.</span></span>
- <span data-ttu-id="dd88f-200">**TX_OPTION_ERROR** (0x08) — недопустимый тип объекта.</span><span class="sxs-lookup"><span data-stu-id="dd88f-200">**TX_OPTION_ERROR** (0x08) Invalid object type.</span></span>
- <span data-ttu-id="dd88f-201">**TX_PTR_ERROR** (0x03) — недопустимое назначение.</span><span class="sxs-lookup"><span data-stu-id="dd88f-201">**TX_PTR_ERROR** (0x03) Invalid destination.</span></span>
- <span data-ttu-id="dd88f-202">**TX_SIZE_ERROR** (0x05) — недопустимый размер.</span><span class="sxs-lookup"><span data-stu-id="dd88f-202">**TX_SIZE_ERROR** (0x05) Invalid size.</span></span>
- <span data-ttu-id="dd88f-203">**TX_NO_INSTANCE** (0x0D) — объект не найден.</span><span class="sxs-lookup"><span data-stu-id="dd88f-203">**TX_NO_INSTANCE** (0x0D) Object not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dd88f-204">Разрешено из</span><span class="sxs-lookup"><span data-stu-id="dd88f-204">Allowed from</span></span>

<span data-ttu-id="dd88f-205">Потоки модулей</span><span class="sxs-lookup"><span data-stu-id="dd88f-205">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="dd88f-206">Пример</span><span class="sxs-lookup"><span data-stu-id="dd88f-206">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
status = txm_module_object_pointer_get(TXM_QUEUE_OBJECT,
         "fft_queue", &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a><span data-ttu-id="dd88f-207">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="dd88f-207">See also</span></span>

- <span data-ttu-id="dd88f-208">txm_module_manager_object_pointer_get_extended</span><span class="sxs-lookup"><span data-stu-id="dd88f-208">txm_module_manager_object_pointer_get_extended</span></span>

---

## <a name="txm_module_object_pointer_get_extended"></a><span data-ttu-id="dd88f-209">txm_module_object_pointer_get_extended</span><span class="sxs-lookup"><span data-stu-id="dd88f-209">txm_module_object_pointer_get_extended</span></span>

<span data-ttu-id="dd88f-210">Поиск системного объекта и получение указателя на него</span><span class="sxs-lookup"><span data-stu-id="dd88f-210">Find system object and retrieve object pointer</span></span>

### <a name="prototype"></a><span data-ttu-id="dd88f-211">Прототип</span><span class="sxs-lookup"><span data-stu-id="dd88f-211">Prototype</span></span>

```c
UINT txm_module_object_pointer_get_extended(UINT object_type,
                                            CHAR *name,
                                            UINT name_length,
                                            VOID **object_ptr);
```

### <a name="description"></a><span data-ttu-id="dd88f-212">Описание</span><span class="sxs-lookup"><span data-stu-id="dd88f-212">Description</span></span>

<span data-ttu-id="dd88f-213">Эта служба получает указатель объекта определенного типа с определенным именем.</span><span class="sxs-lookup"><span data-stu-id="dd88f-213">This service retrieves the object pointer of a particular type with a particular name.</span></span> <span data-ttu-id="dd88f-214">Если объект не найден, возвращается ошибка.</span><span class="sxs-lookup"><span data-stu-id="dd88f-214">If the object is not found, an error is returned.</span></span> <span data-ttu-id="dd88f-215">В противном случае, если объект найден, адрес этого объекта помещается в "object_ptr".</span><span class="sxs-lookup"><span data-stu-id="dd88f-215">Otherwise, if the object is found, the address of that object is placed in "object_ptr."</span></span> <span data-ttu-id="dd88f-216">Этот указатель можно затем использовать для вызова системных служб, взаимодействия с резидентным кодом и (или) другими загруженными модулями в системе.</span><span class="sxs-lookup"><span data-stu-id="dd88f-216">This pointer can then be used to make system service calls, to interact with the resident code, and/or other loaded modules in the system.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="dd88f-217">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="dd88f-217">Input parameters</span></span>

- <span data-ttu-id="dd88f-218">**object_type** — тип запрошенного объекта ThreadX.</span><span class="sxs-lookup"><span data-stu-id="dd88f-218">**object_type** Type of ThreadX object requested.</span></span> <span data-ttu-id="dd88f-219">Допустимые типы:</span><span class="sxs-lookup"><span data-stu-id="dd88f-219">Valid types are as follows:</span></span>
  - <span data-ttu-id="dd88f-220">TXM_BLOCK_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-220">TXM_BLOCK_POOL_OBJECT</span></span>
  - <span data-ttu-id="dd88f-221">TXM_BYTE_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-221">TXM_BYTE_POOL_OBJECT</span></span>
  - <span data-ttu-id="dd88f-222">TXM_EVENT_FLAGS_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-222">TXM_EVENT_FLAGS_OBJECT</span></span>
  - <span data-ttu-id="dd88f-223">TXM_MUTEX_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-223">TXM_MUTEX_OBJECT</span></span>
  - <span data-ttu-id="dd88f-224">TXM_QUEUE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-224">TXM_QUEUE_OBJECT</span></span>
  - <span data-ttu-id="dd88f-225">TXM_SEMAPHORE_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-225">TXM_SEMAPHORE_OBJECT</span></span>
  - <span data-ttu-id="dd88f-226">TXM_THREAD_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-226">TXM_THREAD_OBJECT</span></span>
  - <span data-ttu-id="dd88f-227">TXM_TIMER_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-227">TXM_TIMER_OBJECT</span></span>
  - <span data-ttu-id="dd88f-228">TXM_IP_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-228">TXM_IP_OBJECT</span></span>
  - <span data-ttu-id="dd88f-229">TXM_PACKET_POOL_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-229">TXM_PACKET_POOL_OBJECT</span></span>
  - <span data-ttu-id="dd88f-230">TXM_UDP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-230">TXM_UDP_SOCKET_OBJECT</span></span>
  - <span data-ttu-id="dd88f-231">TXM_TCP_SOCKET_OBJECT</span><span class="sxs-lookup"><span data-stu-id="dd88f-231">TXM_TCP_SOCKET_OBJECT</span></span>
- <span data-ttu-id="dd88f-232">**name** — имя объекта, специфичное для приложения, как определено при создании объекта.</span><span class="sxs-lookup"><span data-stu-id="dd88f-232">**name** Application-specific object name as defined when the object was created.</span></span>
- <span data-ttu-id="dd88f-233">**name_length** — длина имени.</span><span class="sxs-lookup"><span data-stu-id="dd88f-233">**name_length** Length of name.</span></span>
- <span data-ttu-id="dd88f-234">**object_ptr** — назначение для указателя объекта.</span><span class="sxs-lookup"><span data-stu-id="dd88f-234">**object_ptr** Destination for object pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="dd88f-235">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="dd88f-235">Return values</span></span>

- <span data-ttu-id="dd88f-236">**TX_SUCCESS** (0x00) — успешное получение объекта.</span><span class="sxs-lookup"><span data-stu-id="dd88f-236">**TX_SUCCESS** (0x00) Successful object get.</span></span>
- <span data-ttu-id="dd88f-237">**TX_OPTION_ERROR** (0x08) — недопустимый тип объекта.</span><span class="sxs-lookup"><span data-stu-id="dd88f-237">**TX_OPTION_ERROR** (0x08) Invalid object type.</span></span>
- <span data-ttu-id="dd88f-238">**TX_PTR_ERROR** (0x03) — недопустимое назначение.</span><span class="sxs-lookup"><span data-stu-id="dd88f-238">**TX_PTR_ERROR** (0x03) Invalid destination.</span></span>
- <span data-ttu-id="dd88f-239">**TX_SIZE_ERROR** (0x05) — недопустимый размер.</span><span class="sxs-lookup"><span data-stu-id="dd88f-239">**TX_SIZE_ERROR** (0x05) Invalid size.</span></span>
- <span data-ttu-id="dd88f-240">**TX_NO_INSTANCE** (0x0D) — объект не найден.</span><span class="sxs-lookup"><span data-stu-id="dd88f-240">**TX_NO_INSTANCE** (0x0D) Object not found.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="dd88f-241">Разрешено из</span><span class="sxs-lookup"><span data-stu-id="dd88f-241">Allowed from</span></span>

<span data-ttu-id="dd88f-242">Потоки модулей</span><span class="sxs-lookup"><span data-stu-id="dd88f-242">Module threads</span></span>

### <a name="example"></a><span data-ttu-id="dd88f-243">Пример</span><span class="sxs-lookup"><span data-stu-id="dd88f-243">Example</span></span>

```c
TX_QUEUE *queue_pointer;

/* Find the pointer for "fft_queue" in the resident part
   of the application. */
   status = txm_module_object_pointer_get_extended(TXM_QUEUE_OBJECT,
            "fft_queue", 9, &queue_pointer);

/* If status is TX_SUCCESS the found queue pointer is in
   "queue_pointer". This queue pointer can then be used to
   send messages to the "fft_queue." */
```

### <a name="see-also"></a><span data-ttu-id="dd88f-244">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="dd88f-244">See also</span></span>

- <span data-ttu-id="dd88f-245">txm_module_manager_object_pointer_get</span><span class="sxs-lookup"><span data-stu-id="dd88f-245">txm_module_manager_object_pointer_get</span></span>
