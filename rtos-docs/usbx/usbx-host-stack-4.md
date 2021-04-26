---
title: Глава 4. Описание служб узлов USBX
description: Сведения о службах узлов USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d730658c07f3cd7cec8c75a47818314bdc63f35a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816356"
---
# <a name="chapter-4---description-of-usbx-host-services"></a><span data-ttu-id="93be9-103">Глава 4. Описание служб узлов USBX</span><span class="sxs-lookup"><span data-stu-id="93be9-103">Chapter 4 - Description of USBX Host Services</span></span>

## <a name="ux_host_stack_initialize"></a><span data-ttu-id="93be9-104">ux_host_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="93be9-104">ux_host_stack_initialize</span></span>

<span data-ttu-id="93be9-105">Инициализация USBX для операции узла.</span><span class="sxs-lookup"><span data-stu-id="93be9-105">Initialize USBX for host operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="93be9-106">Прототип</span><span class="sxs-lookup"><span data-stu-id="93be9-106">Prototype</span></span>

```c
UINT ux_host_stack_initialize(
    UINT (*system_change_function)
    (ULONG, UX_HOST_CLASS *));
```

### <a name="description"></a><span data-ttu-id="93be9-107">Описание</span><span class="sxs-lookup"><span data-stu-id="93be9-107">Description</span></span>

<span data-ttu-id="93be9-108">Эта функция будет инициализировать стек узлов USB.</span><span class="sxs-lookup"><span data-stu-id="93be9-108">This function will initialize the USB host stack.</span></span> <span data-ttu-id="93be9-109">Заданная область памяти будет настроена для внутреннего использования USBX.</span><span class="sxs-lookup"><span data-stu-id="93be9-109">The supplied memory area will be setup for USBX internal use.</span></span> <span data-ttu-id="93be9-110">Если возвращается UX_SUCCESS, USBX готов для хост-контроллера и регистрации класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-110">If UX_SUCCESS is returned, USBX is ready for host controller and class registration.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="93be9-111">Входной параметр</span><span class="sxs-lookup"><span data-stu-id="93be9-111">Input Parameter</span></span>

- <span data-ttu-id="93be9-112">**system_change_function** — указатель на необязательную подпрограмму обратного вызова для уведомления приложения об изменениях устройства.</span><span class="sxs-lookup"><span data-stu-id="93be9-112">**system_change_function** Pointer to optional callback routine for notifying application of device changes.</span></span>

### <a name="return-value"></a><span data-ttu-id="93be9-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="93be9-113">Return Value</span></span>

- <span data-ttu-id="93be9-114">**UX_SUCCESS** (0x00) — успешная инициализация.</span><span class="sxs-lookup"><span data-stu-id="93be9-114">**UX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="93be9-115">**UX_MEMORY_INSUFFICIENT** (0x12) — сбой выделения памяти.</span><span class="sxs-lookup"><span data-stu-id="93be9-115">**UX_MEMORY_INSUFFICIENT** (0x12) A memory allocation failed.</span></span>

### <a name="example"></a><span data-ttu-id="93be9-116">Пример</span><span class="sxs-lookup"><span data-stu-id="93be9-116">Example</span></span>

```c
UINT status;

/* Initialize USBX for host operation, without notification. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, USBX has been successfully initialized for host operation. */
```

## <a name="ux_host_stack_endpoint_transfer_abort"></a><span data-ttu-id="93be9-117">ux_host_stack_endpoint_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="93be9-117">ux_host_stack_endpoint_transfer_abort</span></span>

<span data-ttu-id="93be9-118">Прерывание всех транзакций, вложенных в запрос на передачу для конечной точки.</span><span class="sxs-lookup"><span data-stu-id="93be9-118">Abort all transactions attached to a transfer request for an endpoint.</span></span>

### <a name="prototype"></a><span data-ttu-id="93be9-119">Прототип</span><span class="sxs-lookup"><span data-stu-id="93be9-119">Prototype</span></span>

```c
UINT ux_host_stack_endpoint_transfer_abort(UX_ENDPOINT *endpoint);
```

### <a name="description"></a><span data-ttu-id="93be9-120">Описание</span><span class="sxs-lookup"><span data-stu-id="93be9-120">Description</span></span>

<span data-ttu-id="93be9-121">Эта функция отменит все активные или ожидающие транзакции для конкретного запроса на передачу, связанного с конечной точкой.</span><span class="sxs-lookup"><span data-stu-id="93be9-121">This function will cancel all transactions active or pending for a specific transfer request attached to an endpoint.</span></span> <span data-ttu-id="93be9-122">В запросе на передачу была вложена функция обратного вызова, которая будет вызываться с состоянием UX_TRANSACTION_ABORTED.</span><span class="sxs-lookup"><span data-stu-id="93be9-122">It the transfer request has a callback function attached, the callback function will be called with the UX_TRANSACTION_ABORTED status.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="93be9-123">Входной параметр</span><span class="sxs-lookup"><span data-stu-id="93be9-123">Input Parameter</span></span>

- <span data-ttu-id="93be9-124">**endpoint** — указатель на конечную точку.</span><span class="sxs-lookup"><span data-stu-id="93be9-124">**endpoint** Pointer to an endpoint.</span></span>

### <a name="return-values"></a><span data-ttu-id="93be9-125">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="93be9-125">Return Values</span></span>

- <span data-ttu-id="93be9-126">**UX_SUCCESS** (0X00) — без ошибок.</span><span class="sxs-lookup"><span data-stu-id="93be9-126">**UX_SUCCESS** (0x00) No errors.</span></span>
- <span data-ttu-id="93be9-127">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) — недопустимый дескриптор конечной точки.</span><span class="sxs-lookup"><span data-stu-id="93be9-127">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Endpoint handle is not valid.</span></span>

### <a name="example"></a><span data-ttu-id="93be9-128">Пример</span><span class="sxs-lookup"><span data-stu-id="93be9-128">Example</span></span>

```c
UX_HOST_CLASS_PRINTER *printer;
UINT status;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command ->
    ux_host_class_command_instance;

/* The printer is being shut down. */

printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* We need to abort transactions on the bulk out pipe. */
status = ux_host_stack_endpoint_transfer_abort
    (printer -> printer_bulk_out_endpoint);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_get"></a><span data-ttu-id="93be9-129">ux_host_stack_class_get</span><span class="sxs-lookup"><span data-stu-id="93be9-129">ux_host_stack_class_get</span></span>

<span data-ttu-id="93be9-130">Получение указателя на контейнер класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-130">Get the pointer to a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="93be9-131">Прототип</span><span class="sxs-lookup"><span data-stu-id="93be9-131">Prototype</span></span>

```c
UINT ux_host_stack_class_get(
    UCHAR *class_name,
    UX_HOST_CLASS **class);
```

### <a name="description"></a><span data-ttu-id="93be9-132">Описание</span><span class="sxs-lookup"><span data-stu-id="93be9-132">Description</span></span>

<span data-ttu-id="93be9-133">Эта функция возвращает указатель на контейнер класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-133">This function returns a pointer to the class container.</span></span> <span data-ttu-id="93be9-134">Класс должен получить свой контейнер из стека USB для поиска экземпляров, когда класс или приложение хотят открыть устройство.</span><span class="sxs-lookup"><span data-stu-id="93be9-134">A class needs to obtain its container from the USB stack to search for instances when a class or an application wants to open a device.</span></span>

> [!NOTE]
> <span data-ttu-id="93be9-135">Строка C объекта class_name должна завершаться нулем, и ее длина (без конечного нуля) не должна быть больше, чем UX_MAX_CLASS_NAME_LENGTH.</span><span class="sxs-lookup"><span data-stu-id="93be9-135">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than UX_MAX_CLASS_NAME_LENGTH.</span></span>

### <a name="parameters"></a><span data-ttu-id="93be9-136">Параметры</span><span class="sxs-lookup"><span data-stu-id="93be9-136">Parameters</span></span>

- <span data-ttu-id="93be9-137">**class_name** — указатель на имя класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-137">**class_name** Pointer to the class name.</span></span>
- <span data-ttu-id="93be9-138">**class** — указатель, обновленный вызовом функции, который содержит контейнер класса для имени класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-138">**class** A pointer updated by the function call that contains the class container for the name of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="93be9-139">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="93be9-139">Return Values</span></span>

- <span data-ttu-id="93be9-140">**UX_SUCCESS** (0X00) — успешный возврат поля класса, заполненного указателем на контейнер класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-140">**UX_SUCCESS** (0x00) No errors, on return the class field is filed with the pointer to the class container.</span></span>
- <span data-ttu-id="93be9-141">**UX_HOST_CLASS_UNKNOWN** (0x59) — класс неизвестен стеку.</span><span class="sxs-lookup"><span data-stu-id="93be9-141">**UX_HOST_CLASS_UNKNOWN** (0x59) Class is unknown by the stack.</span></span>

### <a name="example"></a><span data-ttu-id="93be9-142">Пример</span><span class="sxs-lookup"><span data-stu-id="93be9-142">Example</span></span>

```c
UX_HOST_CLASS *printer_container;
UINT status;

/* Get the container for this class. */
status = ux_host_stack_class_get("ux_host_class_printer", &printer_container);

/* If status equals UX_SUCCESS, the operation was successful */
```

## <a name="ux_host_stack_class_register"></a><span data-ttu-id="93be9-143">ux_host_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="93be9-143">ux_host_stack_class_register</span></span>

<span data-ttu-id="93be9-144">Регистрация класса USB в стеке USB.</span><span class="sxs-lookup"><span data-stu-id="93be9-144">Register a USB class to the USB stack.</span></span>

### <a name="prototype"></a><span data-ttu-id="93be9-145">Прототип</span><span class="sxs-lookup"><span data-stu-id="93be9-145">Prototype</span></span>

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

### <a name="description"></a><span data-ttu-id="93be9-146">Описание</span><span class="sxs-lookup"><span data-stu-id="93be9-146">Description</span></span>

<span data-ttu-id="93be9-147">Эта функция регистрирует класс USB в стеке USB.</span><span class="sxs-lookup"><span data-stu-id="93be9-147">This function registers a USB class to the USB stack.</span></span> <span data-ttu-id="93be9-148">Класс должен указывать точку входа для стека USB, чтобы отправить перечисленные ниже команды.</span><span class="sxs-lookup"><span data-stu-id="93be9-148">The class must specify an entry point for the USB stack to send commands such as the following.</span></span>

- <span data-ttu-id="93be9-149">**UX_HOST_CLASS_COMMAND_QUERY**</span><span class="sxs-lookup"><span data-stu-id="93be9-149">**UX_HOST_CLASS_COMMAND_QUERY**</span></span>
- <span data-ttu-id="93be9-150">**UX_HOST_CLASS_COMMAND_ACTIVATE**</span><span class="sxs-lookup"><span data-stu-id="93be9-150">**UX_HOST_CLASS_COMMAND_ACTIVATE**</span></span>
- <span data-ttu-id="93be9-151">**UX_HOST_CLASS_COMMAND_DESTROY**</span><span class="sxs-lookup"><span data-stu-id="93be9-151">**UX_HOST_CLASS_COMMAND_DESTROY**</span></span>

> [!NOTE]
> <span data-ttu-id="93be9-152">Строка C объекта *class_name* должна завершаться нулем, и ее длина (без конечного нуля) не должна быть больше, чем **UX_MAX_CLASS_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="93be9-152">The C string of *class_name* must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="93be9-153">Параметры</span><span class="sxs-lookup"><span data-stu-id="93be9-153">Parameters</span></span>

- <span data-ttu-id="93be9-154">**class_name** — указатель на имя класса; допустимые записи находятся в файле ux_system_initialize.c в классах USB для USBX.</span><span class="sxs-lookup"><span data-stu-id="93be9-154">**class_name** Pointer to the name of the class, valid entries are found in the file ux_system_initialize.c under the USB Classes of USBX.</span></span>
- <span data-ttu-id="93be9-155">**class_entry_address** — адрес функции входа класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-155">**class_entry_address** Address of the entry function of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="93be9-156">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="93be9-156">Return Values</span></span>

- <span data-ttu-id="93be9-157">**UX_SUCCESS** (0x00) — класс успешно установлен.</span><span class="sxs-lookup"><span data-stu-id="93be9-157">**UX_SUCCESS** (0x00) Class installed successfully.</span></span>
- <span data-ttu-id="93be9-158">**UX_MEMORY_ARRAY_FULL** (0X1a) — недостаточно памяти для хранения этого класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-158">**UX_MEMORY_ARRAY_FULL** (0x1a) No more memory to store this class.</span></span>
- <span data-ttu-id="93be9-159">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) — класс узла уже установлен.</span><span class="sxs-lookup"><span data-stu-id="93be9-159">**UX_HOST_CLASS_ALREADY_INSTALLED** (0x58) Host class already installed.</span></span>

### <a name="example"></a><span data-ttu-id="93be9-160">Пример.</span><span class="sxs-lookup"><span data-stu-id="93be9-160">Example:</span></span>

```c
UINT status;

/* Register all the classes for this implementation. */
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, class was successfully installed. */
```

## <a name="ux_host_stack_class_instance_create"></a><span data-ttu-id="93be9-161">ux_host_stack_class_instance_create</span><span class="sxs-lookup"><span data-stu-id="93be9-161">ux_host_stack_class_instance_create</span></span>

<span data-ttu-id="93be9-162">Создание нового экземпляра класса для контейнера класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-162">Create a new class instance for a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="93be9-163">Прототип</span><span class="sxs-lookup"><span data-stu-id="93be9-163">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_create(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a><span data-ttu-id="93be9-164">Описание</span><span class="sxs-lookup"><span data-stu-id="93be9-164">Description</span></span>

<span data-ttu-id="93be9-165">Эта функция создает новый экземпляр класса для контейнера класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-165">This function creates a new class instance for a class container.</span></span> <span data-ttu-id="93be9-166">Экземпляр класса не содержится в коде класса для упрощения класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-166">The instance of a class is not contained in the class code to reduce the class complexity.</span></span> <span data-ttu-id="93be9-167">Вместо этого каждый экземпляр класса вкладывается в контейнер класса, расположенный в главном стеке.</span><span class="sxs-lookup"><span data-stu-id="93be9-167">Rather, each class instance is attached to the class container located in the main stack.</span></span>

### <a name="parameters"></a><span data-ttu-id="93be9-168">Параметры</span><span class="sxs-lookup"><span data-stu-id="93be9-168">Parameters</span></span>

- <span data-ttu-id="93be9-169">**class** — указатель на контейнер класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-169">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="93be9-170">**class_instance** — указатель на экземпляр класса, который нужно создать.</span><span class="sxs-lookup"><span data-stu-id="93be9-170">**class_instance** Pointer to the class instance to be created.</span></span>

### <a name="return-value"></a><span data-ttu-id="93be9-171">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="93be9-171">Return Value</span></span>

- <span data-ttu-id="93be9-172">**UX_SUCCESS** (0x00) — экземпляр класса был вложен в контейнер класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-172">**UX_SUCCESS** (0x00) The class instance was attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="93be9-173">Пример</span><span class="sxs-lookup"><span data-stu-id="93be9-173">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */

printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL)
    return(UX_MEMORY_INSUFFICIENT);

/* Store the class container into this instance. */
printer -> printer_class = command -> ux_host_class;

/* Create this class instance. */
status = ux_host_stack_class_instance_create(printer -> printer_class, (VOID *)printer);

/* If status equals UX_SUCCESS, the class instance was successfully created and attached to the class container. */
```

## <a name="ux_host_stack_class_instance_destroy"></a><span data-ttu-id="93be9-174">ux_host_stack_class_instance_destroy</span><span class="sxs-lookup"><span data-stu-id="93be9-174">ux_host_stack_class_instance_destroy</span></span>

<span data-ttu-id="93be9-175">Уничтожение экземпляра класса для контейнера класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-175">Destroy a class instance for a class container.</span></span>

### <a name="prototype"></a><span data-ttu-id="93be9-176">Прототип</span><span class="sxs-lookup"><span data-stu-id="93be9-176">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_destroy(
    UX_HOST_CLASS *class, 
    VOID *class_instance);
```

### <a name="description"></a><span data-ttu-id="93be9-177">Описание</span><span class="sxs-lookup"><span data-stu-id="93be9-177">Description</span></span>

<span data-ttu-id="93be9-178">Эта функция уничтожает экземпляр класса для контейнера класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-178">This function destroys a class instance for a class container.</span></span>

### <a name="parameters"></a><span data-ttu-id="93be9-179">Параметры</span><span class="sxs-lookup"><span data-stu-id="93be9-179">Parameters</span></span>

- <span data-ttu-id="93be9-180">**class** — указатель на контейнер класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-180">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="93be9-181">**class_instance** — указатель на экземпляр, который нужно уничтожить.</span><span class="sxs-lookup"><span data-stu-id="93be9-181">**class_instance** Pointer to the instance to destroy.</span></span>

### <a name="return-values"></a><span data-ttu-id="93be9-182">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="93be9-182">Return Values</span></span>

- <span data-ttu-id="93be9-183">**UX_SUCCESS** (0x00) — экземпляр класса уничтожен.</span><span class="sxs-lookup"><span data-stu-id="93be9-183">**UX_SUCCESS** (0x00) The class instance was destroyed.</span></span>
- <span data-ttu-id="93be9-184">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — экземпляр класса не вложен в контейнер класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-184">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) The class instance is not attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="93be9-185">Пример</span><span class="sxs-lookup"><span data-stu-id="93be9-185">Example</span></span>

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

/* Get the instance for this class. */
printer = (UX_HOST_CLASS_PRINTER *) command -> ux_host_class_command_instance;

/* The printer is being shut down. */
printer -> printer_state = UX_HOST_CLASS_INSTANCE_SHUTDOWN;

/* Destroy the instance. */
status = ux_host_stack_class_instance_destroy(printer -> printer_class, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was successfully destroyed. */
```

## <a name="ux_host_stack_class_instance_get"></a><span data-ttu-id="93be9-186">ux_host_stack_class_instance_get</span><span class="sxs-lookup"><span data-stu-id="93be9-186">ux_host_stack_class_instance_get</span></span>

<span data-ttu-id="93be9-187">Получение указателя экземпляра класса для определенного класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-187">Get a class instance pointer for a specific class.</span></span>

### <a name="prototype"></a><span data-ttu-id="93be9-188">Прототип</span><span class="sxs-lookup"><span data-stu-id="93be9-188">Prototype</span></span>

```c
UINT ux_host_stack_class_instance_get(
    UX_HOST_CLASS *class,
    UINT class_index, 
    VOID **class_instance);
```

### <a name="description"></a><span data-ttu-id="93be9-189">Описание</span><span class="sxs-lookup"><span data-stu-id="93be9-189">Description</span></span>

<span data-ttu-id="93be9-190">Эта функция возвращает указатель экземпляра класса для определенного класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-190">This function returns a class instance pointer for a specific class.</span></span> <span data-ttu-id="93be9-191">Экземпляр класса не содержится в коде класса для упрощения класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-191">The instance of a class is not contained in the class code to reduce the class complexity.</span></span> <span data-ttu-id="93be9-192">Вместо этого каждый экземпляр класса вкладывается в контейнер класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-192">Rather, each class instance is attached to the class container.</span></span> <span data-ttu-id="93be9-193">Эта функция используется для поиска экземпляров класса в контейнере класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-193">This function is used to search for class instances within a class container.</span></span>

### <a name="parameters"></a><span data-ttu-id="93be9-194">Параметры</span><span class="sxs-lookup"><span data-stu-id="93be9-194">Parameters</span></span>

- <span data-ttu-id="93be9-195">**class** — указатель на контейнер класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-195">**class** Pointer to the class container.</span></span>
- <span data-ttu-id="93be9-196">**class_index** — индекс, используемый вызовом функции в списке вложенных в контейнер классов.</span><span class="sxs-lookup"><span data-stu-id="93be9-196">**class_index** An index to be used by the function call within the list of attached classes to the container.</span></span>
- <span data-ttu-id="93be9-197">**class_instance** — указатель на экземпляр, возвращаемый вызовом функции.</span><span class="sxs-lookup"><span data-stu-id="93be9-197">**class_instance** Pointer to the instance to be returned by the function call.</span></span>

### <a name="return-values"></a><span data-ttu-id="93be9-198">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="93be9-198">Return Values</span></span>

- <span data-ttu-id="93be9-199">**UX_SUCCESS** (0x00) — экземпляр класса найден.</span><span class="sxs-lookup"><span data-stu-id="93be9-199">**UX_SUCCESS** (0x00) The class instance was found.</span></span>

- <span data-ttu-id="93be9-200">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) — в контейнер класса не вложено ни одного экземпляра класса.</span><span class="sxs-lookup"><span data-stu-id="93be9-200">**UX_HOST_CLASS_INSTANCE_UNKNOWN** (0x5b) There are no more class instances attached to the class container.</span></span>

### <a name="example"></a><span data-ttu-id="93be9-201">Пример</span><span class="sxs-lookup"><span data-stu-id="93be9-201">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* Obtain memory for this class instance. */
printer = ux_memory_allocate(UX_NO_ALIGN, sizeof(UX_HOST_CLASS_PRINTER));

if (printer == UX_NULL) return(UX_MEMORY_INSUFFICIENT);

/* Search for instance index 2. */
status = ux_host_stack_class_instance_get(class, 2, (VOID *) printer);

/* If status equals UX_SUCCESS, the class instance was found. */
```

## <a name="ux_host_stack_device_configuration_get"></a><span data-ttu-id="93be9-202">ux_host_stack_device_configuration_get</span><span class="sxs-lookup"><span data-stu-id="93be9-202">ux_host_stack_device_configuration_get</span></span>

<span data-ttu-id="93be9-203">Получение указателя на контейнер конфигурации.</span><span class="sxs-lookup"><span data-stu-id="93be9-203">Get a pointer to a configuration container.</span></span>

### <a name="prototype"></a><span data-ttu-id="93be9-204">Прототип</span><span class="sxs-lookup"><span data-stu-id="93be9-204">Prototype</span></span>

```c
UINT ux_host_stack_device_configuration_get(
    UX_DEVICE *device,
    UINT configuration_index, 
    UX_CONFIGURATION *configuration);
```

### <a name="description"></a><span data-ttu-id="93be9-205">Описание</span><span class="sxs-lookup"><span data-stu-id="93be9-205">Description</span></span>

<span data-ttu-id="93be9-206">Эта функция возвращает контейнер конфигурации на основе дескриптора устройства и индекса конфигурации.</span><span class="sxs-lookup"><span data-stu-id="93be9-206">This function returns a configuration container based on a device handle and a configuration index.</span></span>

### <a name="parameters"></a><span data-ttu-id="93be9-207">Параметры</span><span class="sxs-lookup"><span data-stu-id="93be9-207">Parameters</span></span>

- <span data-ttu-id="93be9-208">**device** — указатель на контейнер устройства, которому принадлежит запрошенная конфигурация.</span><span class="sxs-lookup"><span data-stu-id="93be9-208">**device** Pointer to the device container that owns the configuration requested.</span></span>
- <span data-ttu-id="93be9-209">**configuration_index** — индекс конфигурации, которую нужно найти.</span><span class="sxs-lookup"><span data-stu-id="93be9-209">**configuration_index** Index of the configuration to be searched.</span></span>
- <span data-ttu-id="93be9-210">**configuration** — адрес указателя на возвращаемый контейнер конфигурации.</span><span class="sxs-lookup"><span data-stu-id="93be9-210">**configuration** Address of the pointer to the configuration container to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="93be9-211">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="93be9-211">Return Values</span></span>

- <span data-ttu-id="93be9-212">**UX_SUCCESS** (0x00) — конфигурация найдена.</span><span class="sxs-lookup"><span data-stu-id="93be9-212">**UX_SUCCESS** (0x00) The configuration was found.</span></span>
- <span data-ttu-id="93be9-213">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) — контейнер устройства не существует.</span><span class="sxs-lookup"><span data-stu-id="93be9-213">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) The device container does not exist.</span></span>
- <span data-ttu-id="93be9-214">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) — дескриптор конфигурации для индекса не существует.</span><span class="sxs-lookup"><span data-stu-id="93be9-214">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration handle for the index does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="93be9-215">Пример</span><span class="sxs-lookup"><span data-stu-id="93be9-215">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it
again. */

if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration, retrieve 1st configuration only. */

status = ux_host_stack_device_configuration_get(printer -> printer_device,
    0, configuration);

/* If status equals UX_SUCCESS, the configuration was found. */
```

## <a name="ux_host_stack_device_configuration_select"></a><span data-ttu-id="93be9-216">ux_host_stack_device_configuration_select</span><span class="sxs-lookup"><span data-stu-id="93be9-216">ux_host_stack_device_configuration_select</span></span>

<span data-ttu-id="93be9-217">Выбор определенной конфигурации для устройства.</span><span class="sxs-lookup"><span data-stu-id="93be9-217">Select a specific configuration for a device.</span></span>

### <a name="prototype"></a><span data-ttu-id="93be9-218">Прототип</span><span class="sxs-lookup"><span data-stu-id="93be9-218">Prototype</span></span>

```c
UINT ux_host_stack_device_configuration_select (UX_CONFIGURATION *configuration);
```

### <a name="description"></a><span data-ttu-id="93be9-219">Описание</span><span class="sxs-lookup"><span data-stu-id="93be9-219">Description</span></span>

<span data-ttu-id="93be9-220">Эта функция выбирает определенную конфигурацию для устройства.</span><span class="sxs-lookup"><span data-stu-id="93be9-220">This function selects a specific configuration for a device.</span></span> <span data-ttu-id="93be9-221">Если эта конфигурация задана для устройства, по умолчанию на устройстве активируется каждый интерфейс устройства и связанный с ним альтернативный параметр 0.</span><span class="sxs-lookup"><span data-stu-id="93be9-221">When this configuration is set to the device, by default, each device interface and its associated alternate setting 0 is activated on the device.</span></span> <span data-ttu-id="93be9-222">Если класс устройства или интерфейса хочет изменить параметр определенного интерфейса, он должен выполнить вызов службы **ux_host_stack_interface_setting_select**.</span><span class="sxs-lookup"><span data-stu-id="93be9-222">If the device/interface class wishes to change the setting of a particular interface, it needs to issue a **ux_host_stack_interface_setting_select** service call.</span></span>

### <a name="parameters"></a><span data-ttu-id="93be9-223">Параметры</span><span class="sxs-lookup"><span data-stu-id="93be9-223">Parameters</span></span>

- <span data-ttu-id="93be9-224">**configuration** — указатель на контейнер конфигурации, который нужно включить для этого устройства.</span><span class="sxs-lookup"><span data-stu-id="93be9-224">**configuration** Pointer to the configuration container that is to be enabled for this device.</span></span>

### <a name="return-values"></a><span data-ttu-id="93be9-225">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="93be9-225">Return Values</span></span>

- <span data-ttu-id="93be9-226">**UX_SUCCESS** (0x00) — выбор конфигурации выполнен успешно.</span><span class="sxs-lookup"><span data-stu-id="93be9-226">**UX_SUCCESS** (0x00) The configuration selection was successful.</span></span>
- <span data-ttu-id="93be9-227">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) — дескриптор конфигурации не существует.</span><span class="sxs-lookup"><span data-stu-id="93be9-227">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration handle does not exist.</span></span>
- <span data-ttu-id="93be9-228">**UX_OVER_CURRENT_CONDITION** (0x43) — для этой конфигурации на шине существует перегрузка по току.</span><span class="sxs-lookup"><span data-stu-id="93be9-228">**UX_OVER_CURRENT_CONDITION** (0x43) An over current condition exists on the bus for this configuration.</span></span>

### <a name="example"></a><span data-ttu-id="93be9-229">Пример</span><span class="sxs-lookup"><span data-stu-id="93be9-229">Example</span></span>

```c
UINT status;

UX_HOST_CLASS_PRINTER *printer;

/* If the device has been configured already, we don't need to do it again. */
if (printer -> printer_device -> ux_device_state == UX_DEVICE_CONFIGURED)
    return(UX_SUCCESS);

/* A printer normally has one configuration - retrieve 1st configuration only. */
status = ux_host_stack_device_configuration_get(printer -> printer_device, 0,configuration);

/* If status equals UX_SUCCESS, the configuration selection was successful. */

/* If valid configuration, ask USBX to set this configuration. */
status = ux_host_stack_device_configuration_select(configuration);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_device_get"></a><span data-ttu-id="93be9-230">ux_host_stack_device_get</span><span class="sxs-lookup"><span data-stu-id="93be9-230">ux_host_stack_device_get</span></span>

<span data-ttu-id="93be9-231">Получение указателя на контейнер устройства.</span><span class="sxs-lookup"><span data-stu-id="93be9-231">Get a pointer to a device container.</span></span>

### <a name="prototype"></a><span data-ttu-id="93be9-232">Прототип</span><span class="sxs-lookup"><span data-stu-id="93be9-232">Prototype</span></span>

```c
UINT ux_host_stack_device_get(
    ULONG device_index, 
    UX_DEVICE *device);
```

### <a name="description"></a><span data-ttu-id="93be9-233">Описание</span><span class="sxs-lookup"><span data-stu-id="93be9-233">Description</span></span>

<span data-ttu-id="93be9-234">Эта функция возвращает контейнер устройства на основе его индекса.</span><span class="sxs-lookup"><span data-stu-id="93be9-234">This function returns a device container based on its index.</span></span> <span data-ttu-id="93be9-235">Индекс устройства начинается с 0.</span><span class="sxs-lookup"><span data-stu-id="93be9-235">The device index starts with 0.</span></span> <span data-ttu-id="93be9-236">Обратите внимание, что индекс имеет тип ULONG, так как у нас может быть несколько контроллеров и индекса байта может быть недостаточно.</span><span class="sxs-lookup"><span data-stu-id="93be9-236">Note that the index is a ULONG because we could have several controllers and a byte index might not be enough.</span></span> <span data-ttu-id="93be9-237">Индекс устройства не следует путать с адресом устройства, относящимся к определенной шине.</span><span class="sxs-lookup"><span data-stu-id="93be9-237">The device index should not be confused with the device address that is bus specific.</span></span>

### <a name="parameters"></a><span data-ttu-id="93be9-238">Параметры</span><span class="sxs-lookup"><span data-stu-id="93be9-238">Parameters</span></span>

- <span data-ttu-id="93be9-239">**device_index** — индекс устройства.</span><span class="sxs-lookup"><span data-stu-id="93be9-239">**device_index** Index of the device.</span></span>
- <span data-ttu-id="93be9-240">**device** — адрес указателя для возвращаемого контейнера устройства.</span><span class="sxs-lookup"><span data-stu-id="93be9-240">**device** Address of the pointer for the device container to return.</span></span>

### <a name="return-values"></a><span data-ttu-id="93be9-241">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="93be9-241">Return Values</span></span>

- <span data-ttu-id="93be9-242">**UX_SUCCESS** (0x00) — контейнер устройства существует и возвращается.</span><span class="sxs-lookup"><span data-stu-id="93be9-242">**UX_SUCCESS** (0x00) The device container exists and is returned</span></span>
- <span data-ttu-id="93be9-243">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) — неизвестное устройство.</span><span class="sxs-lookup"><span data-stu-id="93be9-243">**UX_DEVICE_HANDLE_UNKNOWN** (0x50) Device unknown</span></span>

### <a name="example"></a><span data-ttu-id="93be9-244">Пример</span><span class="sxs-lookup"><span data-stu-id="93be9-244">Example</span></span>

```c
UINT status;

/* Locate the first device in USBX. */
status = ux_host_stack_device_get(0, device);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_endpoint_get"></a><span data-ttu-id="93be9-245">ux_host_stack_interface_endpoint_get</span><span class="sxs-lookup"><span data-stu-id="93be9-245">ux_host_stack_interface_endpoint_get</span></span>

<span data-ttu-id="93be9-246">Получение контейнера конечной точки.</span><span class="sxs-lookup"><span data-stu-id="93be9-246">Get an endpoint container.</span></span>

### <a name="prototype"></a><span data-ttu-id="93be9-247">Прототип</span><span class="sxs-lookup"><span data-stu-id="93be9-247">Prototype</span></span>

```c
UINT ux_host_stack_interface_endpoint_get(
    UX_INTERFACE *interface,
    UINT endpoint_index,
    UX_ENDPOINT *endpoint);
```

### <a name="description"></a><span data-ttu-id="93be9-248">Описание</span><span class="sxs-lookup"><span data-stu-id="93be9-248">Description</span></span>

<span data-ttu-id="93be9-249">Эта функция возвращает контейнер конечной точки на основе дескриптора интерфейса и индекса конечной точки.</span><span class="sxs-lookup"><span data-stu-id="93be9-249">This function returns an endpoint container based on the interface handle and an endpoint index.</span></span> <span data-ttu-id="93be9-250">Предполагается, что до начала поиска конечных точек альтернативный параметр для интерфейса уже выбран или используется параметр по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="93be9-250">It is assumed that the alternate setting for the interface has been selected or the default setting is being used prior to the endpoint(s) being searched.</span></span>

### <a name="parameters"></a><span data-ttu-id="93be9-251">Параметры</span><span class="sxs-lookup"><span data-stu-id="93be9-251">Parameters</span></span>

- <span data-ttu-id="93be9-252">**interface** — указатель на контейнер интерфейса, содержащий запрошенную конечную точку.</span><span class="sxs-lookup"><span data-stu-id="93be9-252">**interface** Pointer to the interface container that contains the endpoint requested.</span></span>
- <span data-ttu-id="93be9-253">**endpoint_index** — индекс конечной точки в этом интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="93be9-253">**endpoint_index** Index of the endpoint in this interface.</span></span>
- <span data-ttu-id="93be9-254">**endpoint** — адрес возвращаемого контейнера конечной точки.</span><span class="sxs-lookup"><span data-stu-id="93be9-254">**endpoint** Address of the endpoint container to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="93be9-255">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="93be9-255">Return Values</span></span>

- <span data-ttu-id="93be9-256">**UX_SUCCESS** (0x00) — контейнер конечной точки существует и возвращается.</span><span class="sxs-lookup"><span data-stu-id="93be9-256">**UX_SUCCESS** (0x00) The endpoint container exists and is returned.</span></span>
- <span data-ttu-id="93be9-257">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) — указанный интерфейс не существует.</span><span class="sxs-lookup"><span data-stu-id="93be9-257">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) Interface specified does not exist.</span></span>
- <span data-ttu-id="93be9-258">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) — индекс конечной точки не существует.</span><span class="sxs-lookup"><span data-stu-id="93be9-258">**UX_ENDPOINT_HANDLE_UNKNOWN** (0x53) Endpoint index does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="93be9-259">Пример</span><span class="sxs-lookup"><span data-stu-id="93be9-259">Example</span></span>

```c
UINT status;
UX_HOST_CLASS_PRINTER *printer;

for(endpoint_index = 0;
    endpoint_index < printer -> printer_interface ->
        ux_interface_descriptor.bNumEndpoints;
    endpoint_index++)
{
    status = ux_host_stack_interface_endpoint_get (printer -> printer_interface,
        endpoint_index, &endpoint);

    if (status == UX_SUCCESS)
    {
        /* Check if endpoint is bulk and OUT. */
        if (((endpoint -> ux_endpoint_descriptor.bEndpointAddress &
            UX_ENDPOINT_DIRECTION) == UX_ENDPOINT_OUT) &&
            ((endpoint -> ux_endpoint_descriptor.bmAttributes &
            UX_MASK_ENDPOINT_TYPE) == UX_BULK_ENDPOINT))
        return(UX_SUCCESS);
    }
}
```

## <a name="ux_host_stack_hcd_register"></a><span data-ttu-id="93be9-260">ux_host_stack_hcd_register</span><span class="sxs-lookup"><span data-stu-id="93be9-260">ux_host_stack_hcd_register</span></span>

<span data-ttu-id="93be9-261">Регистрация контроллера USB в стеке USB.</span><span class="sxs-lookup"><span data-stu-id="93be9-261">Register a USB controller to the USB stack.</span></span>

### <a name="prototype"></a><span data-ttu-id="93be9-262">Прототип</span><span class="sxs-lookup"><span data-stu-id="93be9-262">Prototype</span></span>

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

### <a name="description"></a><span data-ttu-id="93be9-263">Описание</span><span class="sxs-lookup"><span data-stu-id="93be9-263">Description</span></span>

<span data-ttu-id="93be9-264">Эта функция регистрирует контроллер USB в стеке USB.</span><span class="sxs-lookup"><span data-stu-id="93be9-264">This function registers a USB controller to the USB stack.</span></span> <span data-ttu-id="93be9-265">Она в основном выделяет память, используемую этим контроллером, и передает команду инициализации контроллеру.</span><span class="sxs-lookup"><span data-stu-id="93be9-265">It mainly allocates the memory used by this controller and passes the initialization command to the controller.</span></span>

### <a name="parameters"></a><span data-ttu-id="93be9-266">Параметры</span><span class="sxs-lookup"><span data-stu-id="93be9-266">Parameters</span></span>

- <span data-ttu-id="93be9-267">**hcd_name** — имя хост-контроллера.</span><span class="sxs-lookup"><span data-stu-id="93be9-267">**hcd_name** Name of the host controller</span></span>
- <span data-ttu-id="93be9-268">**hcd_function** — функция в хост-контроллере, отвечающая за инициализацию.</span><span class="sxs-lookup"><span data-stu-id="93be9-268">**hcd_function** The function in the host controller responsible for the initialization.</span></span>
- <span data-ttu-id="93be9-269">**hcd_param1** — ресурс ввода-вывода или памяти, используемый HCD.</span><span class="sxs-lookup"><span data-stu-id="93be9-269">**hcd_param1** The IO or memory resource used by the hcd.</span></span>
- <span data-ttu-id="93be9-270">**hcd_param2** — значение IRQ, используемое хост-контроллером.</span><span class="sxs-lookup"><span data-stu-id="93be9-270">**hcd_param2** The IRQ used by the host controller.</span></span>

### <a name="return-values"></a><span data-ttu-id="93be9-271">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="93be9-271">Return Values</span></span>

- <span data-ttu-id="93be9-272">**UX_SUCCESS** (0x00) — контроллер инициализирован правильно.</span><span class="sxs-lookup"><span data-stu-id="93be9-272">**UX_SUCCESS** (0x00) The controller was initialized properly.</span></span>
- <span data-ttu-id="93be9-273">**UX_MEMORY_INSUFFICIENT** (0x12) — недостаточно памяти для этого контроллера.</span><span class="sxs-lookup"><span data-stu-id="93be9-273">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory for this controller.</span></span>
- <span data-ttu-id="93be9-274">**UX_PORT_RESET_FAILED** (0x31) — не удалось выполнить сброс контроллера.</span><span class="sxs-lookup"><span data-stu-id="93be9-274">**UX_PORT_RESET_FAILED** (0x31) The reset of the controller failed.</span></span>
- <span data-ttu-id="93be9-275">**UX_CONTROLLER_INIT_FAILED** (0x32) — не удалось правильно инициализировать контроллер.</span><span class="sxs-lookup"><span data-stu-id="93be9-275">**UX_CONTROLLER_INIT_FAILED** (0x32) The controller failed to initialize properly.</span></span>

### <a name="example"></a><span data-ttu-id="93be9-276">Пример</span><span class="sxs-lookup"><span data-stu-id="93be9-276">Example</span></span>

```c
UINT status;

/* Initialize a host controller mapped at address 0xd0000 and using IRQ 10. */

status = ux_host_stack_hcd_register("ux_hcd_controller",
    ux_hcd_controller_initialize, 0xd0000, 0x0a);

/* If status equals UX_SUCCESS, the controller was initialized properly. */

/* Note that the application must also setup a call to the
    interrupt handler for the controller.
    The function for the controller is called _ux_hch_controller_interrupt_handler. */
```

## <a name="ux_host_stack_configuration_interface_get"></a><span data-ttu-id="93be9-277">ux_host_stack_configuration_interface_get</span><span class="sxs-lookup"><span data-stu-id="93be9-277">ux_host_stack_configuration_interface_get</span></span>

<span data-ttu-id="93be9-278">Получение указателя для контейнера интерфейса.</span><span class="sxs-lookup"><span data-stu-id="93be9-278">Get an interface container pointer.</span></span>

### <a name="prototype"></a><span data-ttu-id="93be9-279">Прототип</span><span class="sxs-lookup"><span data-stu-id="93be9-279">Prototype</span></span>

```c
UINT ux_host_stack_configuration_interface_get (
    UX_CONFIGURATION *configuration,
    UINT interface_index, 
    UINT alternate_setting_index, 
    UX_INTERFACE **interface);
```

### <a name="description"></a><span data-ttu-id="93be9-280">Описание</span><span class="sxs-lookup"><span data-stu-id="93be9-280">Description</span></span>

<span data-ttu-id="93be9-281">Эта функция возвращает контейнер интерфейса на основе дескриптора конфигурации, индекса интерфейса и индекса альтернативного параметра.</span><span class="sxs-lookup"><span data-stu-id="93be9-281">This function returns an interface container based on a configuration handle, an interface index, and an alternate setting index.</span></span>

### <a name="parameters"></a><span data-ttu-id="93be9-282">Параметры</span><span class="sxs-lookup"><span data-stu-id="93be9-282">Parameters</span></span>

- <span data-ttu-id="93be9-283">**configuration** — указатель на контейнер конфигурации, которому принадлежит интерфейс.</span><span class="sxs-lookup"><span data-stu-id="93be9-283">**configuration** Pointer to the configuration container that owns the interface.</span></span>
- <span data-ttu-id="93be9-284">**interface_index** — индекс интерфейса, который нужно найти.</span><span class="sxs-lookup"><span data-stu-id="93be9-284">**interface_index** Interface index to be searched.</span></span>
- <span data-ttu-id="93be9-285">**alternate_setting_index** — альтернативный параметр в интерфейсе для поиска.</span><span class="sxs-lookup"><span data-stu-id="93be9-285">**alternate_setting_index** Alternate setting within the interface to search.</span></span>
- <span data-ttu-id="93be9-286">**interface** — адрес указателя возвращаемого контейнера интерфейса.</span><span class="sxs-lookup"><span data-stu-id="93be9-286">**interface** Address of the interface container pointer to be returned.</span></span>

### <a name="return-values"></a><span data-ttu-id="93be9-287">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="93be9-287">Return Values</span></span>

- <span data-ttu-id="93be9-288">**UX_SUCCESS** (0x00) — контейнер интерфейса для индекса интерфейса и альтернативный параметр найдены и возвращены.</span><span class="sxs-lookup"><span data-stu-id="93be9-288">**UX_SUCCESS** (0x00) The interface container for the interface index and the alternate setting was found and returned.</span></span>
- <span data-ttu-id="93be9-289">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) — конфигурация не существует.</span><span class="sxs-lookup"><span data-stu-id="93be9-289">**UX_CONFIGURATION_HANDLE_UNKNOWN** (0x51) The configuration does not exist.</span></span>
- <span data-ttu-id="93be9-290">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) — интерфейс не существует.</span><span class="sxs-lookup"><span data-stu-id="93be9-290">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) The interface does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="93be9-291">Пример</span><span class="sxs-lookup"><span data-stu-id="93be9-291">Example</span></span>

```c
UINT status;

/* Search for the default alternate setting on the first interface for the printer. */
status = ux_host_stack_configuration_interface_get(configuration, 0, 0,
    &printer -> printer_interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_interface_setting_select"></a><span data-ttu-id="93be9-292">ux_host_stack_interface_setting_select</span><span class="sxs-lookup"><span data-stu-id="93be9-292">ux_host_stack_interface_setting_select</span></span>

<span data-ttu-id="93be9-293">Выбор альтернативного параметра для интерфейса.</span><span class="sxs-lookup"><span data-stu-id="93be9-293">Select an alternate setting for an interface.</span></span>

### <a name="prototype"></a><span data-ttu-id="93be9-294">Прототип</span><span class="sxs-lookup"><span data-stu-id="93be9-294">Prototype</span></span>

```c
UINT ux_host_stack_interface_setting_select(UX_INTERFACE *interface);
```

### <a name="description"></a><span data-ttu-id="93be9-295">Описание</span><span class="sxs-lookup"><span data-stu-id="93be9-295">Description</span></span>

<span data-ttu-id="93be9-296">Эта функция выбирает определенный альтернативный параметр для данного интерфейса выбранной конфигурации.</span><span class="sxs-lookup"><span data-stu-id="93be9-296">This function selects a specific alternate setting for a given interface belonging to the selected configuration.</span></span> <span data-ttu-id="93be9-297">Эта функция используется для изменения альтернативного параметра по умолчанию на новый параметр или для возврата к альтернативному параметру по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="93be9-297">This function is used to change from the default alternate setting to a new setting or to go back to the default alternate setting.</span></span> <span data-ttu-id="93be9-298">Если выбран новый альтернативный параметр, предыдущие характеристики конечной точки являются недопустимыми, поэтому их следует перезагрузить.</span><span class="sxs-lookup"><span data-stu-id="93be9-298">When a new alternate setting is selected, the previous endpoint characteristics are invalid and should be reloaded.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="93be9-299">Входной параметр</span><span class="sxs-lookup"><span data-stu-id="93be9-299">Input Parameter</span></span>

- <span data-ttu-id="93be9-300">**interface** — указатель на контейнер интерфейса, для которого выбирается альтернативный параметр.</span><span class="sxs-lookup"><span data-stu-id="93be9-300">**interface** Pointer to the interface container whose alternate setting is to be selected.</span></span>

### <a name="return-values"></a><span data-ttu-id="93be9-301">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="93be9-301">Return Values</span></span>

- <span data-ttu-id="93be9-302">**UX_SUCCESS** (0x00) — альтернативный параметр для этого интерфейса успешно выбран.</span><span class="sxs-lookup"><span data-stu-id="93be9-302">**UX_SUCCESS** (0x00) The alternate setting for this interface has been successfully selected.</span></span>
- <span data-ttu-id="93be9-303">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) — интерфейс не существует.</span><span class="sxs-lookup"><span data-stu-id="93be9-303">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) The interface does not exist.</span></span>

### <a name="example"></a><span data-ttu-id="93be9-304">Пример</span><span class="sxs-lookup"><span data-stu-id="93be9-304">Example</span></span>

```c
UINT status;

/* Select a new alternate setting for this interface. */
status = ux_host_stack_interface_setting_select(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request_abort"></a><span data-ttu-id="93be9-305">ux_host_stack_transfer_request_abort</span><span class="sxs-lookup"><span data-stu-id="93be9-305">ux_host_stack_transfer_request_abort</span></span>

<span data-ttu-id="93be9-306">Прерывание ожидающего запроса на передачу.</span><span class="sxs-lookup"><span data-stu-id="93be9-306">Abort a pending transfer request.</span></span>

### <a name="prototype"></a><span data-ttu-id="93be9-307">Прототип</span><span class="sxs-lookup"><span data-stu-id="93be9-307">Prototype</span></span>

```c
UINT ux_host_stack_transfer_request_abort(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a><span data-ttu-id="93be9-308">Описание</span><span class="sxs-lookup"><span data-stu-id="93be9-308">Description</span></span>

<span data-ttu-id="93be9-309">Эта функция прерывает отправленный ранее ожидающий запрос на передачу.</span><span class="sxs-lookup"><span data-stu-id="93be9-309">This function aborts a pending transfer request that has been previously submitted.</span></span> <span data-ttu-id="93be9-310">Эта функция отменяет только конкретный запрос на передачу.</span><span class="sxs-lookup"><span data-stu-id="93be9-310">This function only cancels a specific transfer request.</span></span> <span data-ttu-id="93be9-311">Обратный вызов функции будет иметь состояние UX_TRANSFER REQUEST_STATUS_ABORT.</span><span class="sxs-lookup"><span data-stu-id="93be9-311">The call back to the function will have the UX_TRANSFER REQUEST_STATUS_ABORT status.</span></span>

### <a name="parameters"></a><span data-ttu-id="93be9-312">Параметры</span><span class="sxs-lookup"><span data-stu-id="93be9-312">Parameters</span></span>

- <span data-ttu-id="93be9-313">**transfer_request** — указатель на запрос на передачу, который нужно прервать.</span><span class="sxs-lookup"><span data-stu-id="93be9-313">**transfer request** Pointer to the transfer request to be aborted.</span></span>

### <a name="return-values"></a><span data-ttu-id="93be9-314">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="93be9-314">Return Values</span></span>

- <span data-ttu-id="93be9-315">**UX_SUCCESS** (0x00) — передача по USB для этого запроса на передачу отменена.</span><span class="sxs-lookup"><span data-stu-id="93be9-315">**UX_SUCCESS** (0x00) The USB transfer for this transfer request was canceled.</span></span>

### <a name="example"></a><span data-ttu-id="93be9-316">Пример</span><span class="sxs-lookup"><span data-stu-id="93be9-316">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_host_stack_transfer_request_abort(transfer request);

/* If status equals UX_SUCCESS, the operation was successful. */
```

## <a name="ux_host_stack_transfer_request"></a><span data-ttu-id="93be9-317">ux_host_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="93be9-317">ux_host_stack_transfer_request</span></span>

<span data-ttu-id="93be9-318">Запрос передачи по USB.</span><span class="sxs-lookup"><span data-stu-id="93be9-318">Request a USB transfer.</span></span>

### <a name="prototype"></a><span data-ttu-id="93be9-319">Прототип</span><span class="sxs-lookup"><span data-stu-id="93be9-319">Prototype</span></span>

```c
UINT ux_host_stack_transfer_request(UX_TRANSFER REQUEST *transfer request);
```

### <a name="description"></a><span data-ttu-id="93be9-320">Описание</span><span class="sxs-lookup"><span data-stu-id="93be9-320">Description</span></span>

<span data-ttu-id="93be9-321">Эта функция выполняет транзакцию по USB.</span><span class="sxs-lookup"><span data-stu-id="93be9-321">This function performs a USB transaction.</span></span> <span data-ttu-id="93be9-322">На входе запрос на передачу задает канал конечной точки, выбранный для этой транзакции, и параметры, связанные с передачей (полезные данные, длина транзакции).</span><span class="sxs-lookup"><span data-stu-id="93be9-322">On entry the transfer request gives the endpoint pipe selected for this transaction and the parameters associated with the transfer (data payload, length of transaction).</span></span> <span data-ttu-id="93be9-323">Для канала управления транзакция блокируется и будет возвращаться только по завершении трех этапов передачи управления или при возникновении предыдущей ошибки.</span><span class="sxs-lookup"><span data-stu-id="93be9-323">For Control pipe, the transaction is blocking and will only return when the three phases of the control transfer have been completed or if there is a previous error.</span></span> <span data-ttu-id="93be9-324">Для других каналов стек USB будет планировать транзакцию по USB, но не будет ждать ее завершения.</span><span class="sxs-lookup"><span data-stu-id="93be9-324">For other pipes, the USB stack will schedule the transaction on the USB but will not wait for its completion.</span></span> <span data-ttu-id="93be9-325">Каждый запрос на передачу для каналов без блокировки должен указывать обработчик подпрограммы завершения.</span><span class="sxs-lookup"><span data-stu-id="93be9-325">Each transfer request for non-blocking pipes has to specify a completion routine handler.</span></span>

<span data-ttu-id="93be9-326">При возвращении вызова функции следует проверять состояние запроса на передачу, так как в нем содержится результат транзакции.</span><span class="sxs-lookup"><span data-stu-id="93be9-326">When the function call returns, the status of the transfer request should be examined as it contains the result of the transaction.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="93be9-327">Входной параметр</span><span class="sxs-lookup"><span data-stu-id="93be9-327">Input Parameter</span></span>

- <span data-ttu-id="93be9-328">**transfer_request** — указатель на запрос на передачу.</span><span class="sxs-lookup"><span data-stu-id="93be9-328">**transfer_request** Pointer to the transfer request.</span></span> <span data-ttu-id="93be9-329">Запрос на передачу содержит все необходимые сведения, требуемые для переноса.</span><span class="sxs-lookup"><span data-stu-id="93be9-329">The transfer request contains all the necessary information required for the transfer.</span></span>

### <a name="return-values"></a><span data-ttu-id="93be9-330">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="93be9-330">Return Values</span></span>

- <span data-ttu-id="93be9-331">**UX_SUCCESS** (0x00) — перенос по USB для этого запроса на передачу запланирован правильно.</span><span class="sxs-lookup"><span data-stu-id="93be9-331">**UX_SUCCESS** (0x00) The USB transfer for this transfer request was scheduled properly.</span></span> <span data-ttu-id="93be9-332">Код состояния запроса на передачу следует проверить после завершения запроса на передачу.</span><span class="sxs-lookup"><span data-stu-id="93be9-332">The status code of the transfer request should be examined when the transfer request completes.</span></span>
- <span data-ttu-id="93be9-333">**UX_MEMORY_INSUFFICIENT** (0x12) — недостаточно памяти для выделения необходимых ресурсов контроллера.</span><span class="sxs-lookup"><span data-stu-id="93be9-333">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to allocate the necessary controller resources.</span></span>
- <span data-ttu-id="93be9-334">**UX_TRANSFER_NOT_READY** (0x25) — устройство находилось в недопустимом состоянии (допустимые состояния: ATTACHED, ADDRESSED или CONFIGURED).</span><span class="sxs-lookup"><span data-stu-id="93be9-334">**UX_TRANSFER_NOT_READY** (0x25) The device was in an invalid state – must be ATTACHED,ADDRESSED, or CONFIGURED.</span></span>

### <a name="example"></a><span data-ttu-id="93be9-335">Пример</span><span class="sxs-lookup"><span data-stu-id="93be9-335">Example:</span></span>

```c
UINT status;

/* Create a transfer request for the SET_CONFIGURATION request. No data for this request. */
transfer_request -> ux_transfer_request_requested_length = 0;
transfer_request -> ux_transfer_request_function = UX_SET_CONFIGURATION;
transfer_request -> ux_transfer_request_type =
    UX_REQUEST_OUT |
    UX_REQUEST_TYPE_STANDARD |
    UX_REQUEST_TARGET_DEVICE;

transfer_request -> ux_transfer_request_value = (USHORT)
    configuration -> ux_configuration_descriptor.bConfigurationValue;
transfer_request -> ux_transfer_request_index = 0;

/* Send request to HCD layer. */
status = ux_host_stack_transfer_request(transfer_request);

/* If status equals UX_SUCCESS, the operation was successful. */
```
