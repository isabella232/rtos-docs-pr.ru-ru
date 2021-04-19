---
title: Глава 4. Описание служб устройства USBX
description: Ознакомьтесь с информацией о службах устройства USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d4aea7470ba2d9075296164b9d1fb61db4f88523
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104816144"
---
# <a name="description-of-usbx-device-services"></a><span data-ttu-id="eb54c-103">Описание служб устройства USBX</span><span class="sxs-lookup"><span data-stu-id="eb54c-103">Description of USBX Device Services</span></span>

### <a name="ux_device_stack_alternate_setting_get"></a><span data-ttu-id="eb54c-104">ux_device_stack_alternate_setting_get</span><span class="sxs-lookup"><span data-stu-id="eb54c-104">ux_device_stack_alternate_setting_get</span></span>

<span data-ttu-id="eb54c-105">Получение текущего переменного параметра для значения интерфейса</span><span class="sxs-lookup"><span data-stu-id="eb54c-105">Get current alternate setting for an interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="eb54c-106">Прототип</span><span class="sxs-lookup"><span data-stu-id="eb54c-106">Prototype</span></span>

```c
UINT ux_device_stack_alternate_setting_get(ULONG interface_value);
```

### <a name="description"></a><span data-ttu-id="eb54c-107">Описание</span><span class="sxs-lookup"><span data-stu-id="eb54c-107">Description</span></span>

<span data-ttu-id="eb54c-108">Эта функция используется узлом USB для получения текущего переменного параметра для определенного значения интерфейса.</span><span class="sxs-lookup"><span data-stu-id="eb54c-108">This function is used by the USB host to obtain the current alternate setting for a specific interface value.</span></span> <span data-ttu-id="eb54c-109">Она вызывается драйвером контроллера при получении запроса **GET_INTERFACE**.</span><span class="sxs-lookup"><span data-stu-id="eb54c-109">It is called by the controller driver when a **GET_INTERFACE** request is received.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="eb54c-110">Входной параметр</span><span class="sxs-lookup"><span data-stu-id="eb54c-110">Input Parameter</span></span>

- <span data-ttu-id="eb54c-111">**Interface_value** Значение интерфейса, для которого запрашивается текущий переменный параметр</span><span class="sxs-lookup"><span data-stu-id="eb54c-111">**Interface_value** Interface value for which the current alternate setting is queried</span></span>

### <a name="return-values"></a><span data-ttu-id="eb54c-112">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="eb54c-112">Return Values</span></span>

- <span data-ttu-id="eb54c-113">**UX_SUCCESS** (0x00) – передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="eb54c-113">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="eb54c-114">**UX_ERROR** (0xFF) – неправильное значение интерфейса.</span><span class="sxs-lookup"><span data-stu-id="eb54c-114">**UX_ERROR** (0xFF) Wrong interface value.</span></span>

### <a name="example"></a><span data-ttu-id="eb54c-115">Пример</span><span class="sxs-lookup"><span data-stu-id="eb54c-115">Example</span></span>

```c
ULONG interface_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_alternate_setting_set"></a><span data-ttu-id="eb54c-116">ux_device_stack_alternate_setting_set</span><span class="sxs-lookup"><span data-stu-id="eb54c-116">ux_device_stack_alternate_setting_set</span></span>

<span data-ttu-id="eb54c-117">Установка текущего переменного параметра для значения интерфейса</span><span class="sxs-lookup"><span data-stu-id="eb54c-117">Set current alternate setting for an interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="eb54c-118">Прототип</span><span class="sxs-lookup"><span data-stu-id="eb54c-118">Prototype</span></span>

```c
UINT ux_device_stack_alternate_setting_set(
    ULONG interface_value, 
    ULONG alternate_setting_value);
```

### <a name="description"></a><span data-ttu-id="eb54c-119">Описание</span><span class="sxs-lookup"><span data-stu-id="eb54c-119">Description</span></span>

<span data-ttu-id="eb54c-120">Эта функция используется узлом USB для установки текущего переменного параметра для определенного значения интерфейса.</span><span class="sxs-lookup"><span data-stu-id="eb54c-120">This function is used by the USB host to set the current alternate setting for a specific interface value.</span></span> <span data-ttu-id="eb54c-121">Она вызывается драйвером контроллера при получении запроса **SET_INTERFACE**.</span><span class="sxs-lookup"><span data-stu-id="eb54c-121">It is called by the controller driver when a **SET_INTERFACE** request is received.</span></span> <span data-ttu-id="eb54c-122">После завершения **SET_INTERFACE** к классу применяются значения переменных параметров.</span><span class="sxs-lookup"><span data-stu-id="eb54c-122">When the **SET_INTERFACE** is completed, the values of the alternate settings are applied to the class.</span></span>

<span data-ttu-id="eb54c-123">Стек устройства даст команду **UX_SLAVE_CLASS_COMMAND_CHANGE** классу, владеющему этим интерфейсом, чтобы отразить изменение переменного параметра.</span><span class="sxs-lookup"><span data-stu-id="eb54c-123">The device stack will issue a **UX_SLAVE_CLASS_COMMAND_CHANGE** to the class that owns this interface to reflect the change of alternate setting.</span></span>

### <a name="parameters"></a><span data-ttu-id="eb54c-124">Параметры</span><span class="sxs-lookup"><span data-stu-id="eb54c-124">Parameters</span></span>

- <span data-ttu-id="eb54c-125">**Interface_value**: значение интерфейса, для которого установлен текущий переменный параметр.</span><span class="sxs-lookup"><span data-stu-id="eb54c-125">**interface_value**: Interface value for which the current alternate setting is set.</span></span>
- <span data-ttu-id="eb54c-126">**alternate_setting_value**: новое значение переменного параметра.</span><span class="sxs-lookup"><span data-stu-id="eb54c-126">**alternate_setting_value**: The new alternate setting value.</span></span>

### <a name="return-values"></a><span data-ttu-id="eb54c-127">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="eb54c-127">Return Values</span></span>

- <span data-ttu-id="eb54c-128">**UX_SUCCESS** (0x00) – передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="eb54c-128">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="eb54c-129">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) – интерфейс не подключен.</span><span class="sxs-lookup"><span data-stu-id="eb54c-129">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) No interface attached.</span></span>
- <span data-ttu-id="eb54c-130">**UX_FUNCTION_NOT_SUPPORTED** (0x54) – устройство не настроено.</span><span class="sxs-lookup"><span data-stu-id="eb54c-130">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Device is not configured.</span></span>
- <span data-ttu-id="eb54c-131">**UX_ERROR** (0xFF) – неправильное значение интерфейса.</span><span class="sxs-lookup"><span data-stu-id="eb54c-131">**UX_ERROR** (0xFF) Wrong interface value.</span></span>

### <a name="example"></a><span data-ttu-id="eb54c-132">Пример</span><span class="sxs-lookup"><span data-stu-id="eb54c-132">Example</span></span>

```c
ULONG interface_value;

ULONG alternate_setting_value;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_set(interface_value, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_class_register"></a><span data-ttu-id="eb54c-133">ux_device_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="eb54c-133">ux_device_stack_class_register</span></span>

<span data-ttu-id="eb54c-134">Регистрация нового класса USB-устройств</span><span class="sxs-lookup"><span data-stu-id="eb54c-134">Register a new USB device class</span></span>

### <a name="prototype"></a><span data-ttu-id="eb54c-135">Прототип</span><span class="sxs-lookup"><span data-stu-id="eb54c-135">Prototype</span></span>

```c
UINT ux_device_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT *),
    ULONG configuration_number, 
    ULONG interface_number,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="eb54c-136">Описание</span><span class="sxs-lookup"><span data-stu-id="eb54c-136">Description</span></span>

<span data-ttu-id="eb54c-137">Эта функция используется приложением для регистрации нового класса USB-устройств.</span><span class="sxs-lookup"><span data-stu-id="eb54c-137">This function is used by the application to register a new USB device class.</span></span> <span data-ttu-id="eb54c-138">При регистрации запускается контейнер класса, а не экземпляр класса.</span><span class="sxs-lookup"><span data-stu-id="eb54c-138">This registration starts a class container and not an instance of the class.</span></span> <span data-ttu-id="eb54c-139">Класс должен иметь активный поток и быть присоединен к определенному интерфейсу.</span><span class="sxs-lookup"><span data-stu-id="eb54c-139">A class should have an active thread and be attached to a specific interface.</span></span>

<span data-ttu-id="eb54c-140">Некоторые классы предполагают наличие параметра или списка параметров.</span><span class="sxs-lookup"><span data-stu-id="eb54c-140">Some classes expect a parameter or parameter list.</span></span> <span data-ttu-id="eb54c-141">Например, класс хранения устройств ожидает геометрию устройства хранения, которое он пытается эмулировать.</span><span class="sxs-lookup"><span data-stu-id="eb54c-141">For instance, the device storage class would expect the geometry of the storage device it is trying to emulate.</span></span> <span data-ttu-id="eb54c-142">Поэтому поле параметра зависит от требования к классу и может быть значением или указателем на структуру, заполненную значениями класса.</span><span class="sxs-lookup"><span data-stu-id="eb54c-142">The parameter field is therefore dependent on the class requirement and can be a value or a pointer to a structure filled with the class values.</span></span>

> [!NOTE]
> <span data-ttu-id="eb54c-143">Строка C объекта class_name должна завершаться нулем и ее длина (без конечного нуля) не должна быть больше, чем **UX_MAX_CLASS_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="eb54c-143">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="eb54c-144">Параметры</span><span class="sxs-lookup"><span data-stu-id="eb54c-144">Parameters</span></span>

- <span data-ttu-id="eb54c-145">**class_name** – имя класса</span><span class="sxs-lookup"><span data-stu-id="eb54c-145">**class_name** Class Name</span></span>
- <span data-ttu-id="eb54c-146">**class_entry_function** – функция записи класса.</span><span class="sxs-lookup"><span data-stu-id="eb54c-146">**class_entry_function** The entry function of the class.</span></span>
- <span data-ttu-id="eb54c-147">**configuration_number** – номер конфигурации, к которому присоединен этот класс.</span><span class="sxs-lookup"><span data-stu-id="eb54c-147">**configuration_number** The configuration number this class is attached to.</span></span>
- <span data-ttu-id="eb54c-148">**interface_number** – номер интерфейса, к которому присоединен этот класс.</span><span class="sxs-lookup"><span data-stu-id="eb54c-148">**interface_number** The interface number this class is attached to.</span></span>
- <span data-ttu-id="eb54c-149">**parameter** – указатель на список параметров конкретного класса.</span><span class="sxs-lookup"><span data-stu-id="eb54c-149">**parameter** A pointer to a class specific parameter list.</span></span>

### <a name="return-values"></a><span data-ttu-id="eb54c-150">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="eb54c-150">Return Values</span></span>

- <span data-ttu-id="eb54c-151">**UX_SUCCESS** (0x00) – класс зарегистрирован</span><span class="sxs-lookup"><span data-stu-id="eb54c-151">**UX_SUCCESS** (0x00) The class was registered</span></span>
- <span data-ttu-id="eb54c-152">**UX_MEMORY_INSUFFICIENT** (0x12) – в таблице классов не осталось записей.</span><span class="sxs-lookup"><span data-stu-id="eb54c-152">**UX_MEMORY_INSUFFICIENT** (0x12) No entries left in class table.</span></span>
- <span data-ttu-id="eb54c-153">**UX_THREAD_ERROR** (0X16) – не удается создать поток класса.</span><span class="sxs-lookup"><span data-stu-id="eb54c-153">**UX_THREAD_ERROR** (0x16) Cannot create a class thread.</span></span>

### <a name="example"></a><span data-ttu-id="eb54c-154">Пример</span><span class="sxs-lookup"><span data-stu-id="eb54c-154">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

/* Initialize the device storage class. The class is connected with interface 1 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name ux_device_class_storage_entry,
    1, 1, (VOID *)&parameter);
```

### <a name="ux_device_stack_class_unregister"></a><span data-ttu-id="eb54c-155">ux_device_stack_class_unregister</span><span class="sxs-lookup"><span data-stu-id="eb54c-155">ux_device_stack_class_unregister</span></span>

<span data-ttu-id="eb54c-156">Отмена регистрации класса USB-устройств</span><span class="sxs-lookup"><span data-stu-id="eb54c-156">Unregister a USB device class</span></span>

### <a name="prototype"></a><span data-ttu-id="eb54c-157">Прототип</span><span class="sxs-lookup"><span data-stu-id="eb54c-157">Prototype</span></span>

```c
UINT ux_device_stack_class_unregister(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT*));
```

### <a name="description"></a><span data-ttu-id="eb54c-158">Описание</span><span class="sxs-lookup"><span data-stu-id="eb54c-158">Description</span></span>

<span data-ttu-id="eb54c-159">Эта функция используется приложением для отмены регистрации класса USB-устройств.</span><span class="sxs-lookup"><span data-stu-id="eb54c-159">This function is used by the application to unregister a USB device class.</span></span>

> [!NOTE]
> <span data-ttu-id="eb54c-160">Строка C объекта class_name должна завершаться нулем и ее длина (без конечного нуля) не должна быть больше, чем **UX_MAX_CLASS_NAME_LENGTH**.</span><span class="sxs-lookup"><span data-stu-id="eb54c-160">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="eb54c-161">Параметры</span><span class="sxs-lookup"><span data-stu-id="eb54c-161">Parameters</span></span>

- <span data-ttu-id="eb54c-162">**class_name**: имя класса</span><span class="sxs-lookup"><span data-stu-id="eb54c-162">**class_name**: Class Name</span></span>
- <span data-ttu-id="eb54c-163">**class_entry_function**: функция записи класса.</span><span class="sxs-lookup"><span data-stu-id="eb54c-163">**class_entry_function**: The entry function of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="eb54c-164">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="eb54c-164">Return Values</span></span>

- <span data-ttu-id="eb54c-165">**UX_SUCCESS** (0x00) – регистрация класса отменена.</span><span class="sxs-lookup"><span data-stu-id="eb54c-165">**UX_SUCCESS** (0x00) The class was unregistered.</span></span>
- <span data-ttu-id="eb54c-166">**UX_NO_CLASS_MATCH** (0x57) – класс не зарегистрирован.</span><span class="sxs-lookup"><span data-stu-id="eb54c-166">**UX_NO_CLASS_MATCH** (0x57) The class isn't registered.</span></span>

### <a name="example"></a><span data-ttu-id="eb54c-167">Пример</span><span class="sxs-lookup"><span data-stu-id="eb54c-167">Example</span></span>

```c
/* The following example illustrates this service. */

/* Unitialize the device storage class. */
status = ux_device_stack_class_unregister(_ux_system_slave_class_storage_name, ux_device_class_storage_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_get"></a><span data-ttu-id="eb54c-168">ux_device_stack_configuration_get</span><span class="sxs-lookup"><span data-stu-id="eb54c-168">ux_device_stack_configuration_get</span></span>

<span data-ttu-id="eb54c-169">Получение текущей конфигурации</span><span class="sxs-lookup"><span data-stu-id="eb54c-169">Get the current configuration</span></span>

### <a name="prototype"></a><span data-ttu-id="eb54c-170">Прототип</span><span class="sxs-lookup"><span data-stu-id="eb54c-170">Prototype</span></span>

```c
UINT ux_device_stack_configuration_get(VOID);
```

### <a name="description"></a><span data-ttu-id="eb54c-171">Описание</span><span class="sxs-lookup"><span data-stu-id="eb54c-171">Description</span></span>

<span data-ttu-id="eb54c-172">Эта функция используется узлом для получения текущей конфигурации, используемой на устройстве.</span><span class="sxs-lookup"><span data-stu-id="eb54c-172">This function is used by the host to obtain the current configuration running in the device.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="eb54c-173">Входной параметр</span><span class="sxs-lookup"><span data-stu-id="eb54c-173">Input Parameter</span></span>

<span data-ttu-id="eb54c-174">Нет</span><span class="sxs-lookup"><span data-stu-id="eb54c-174">None</span></span>

### <a name="return-value"></a><span data-ttu-id="eb54c-175">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="eb54c-175">Return Value</span></span>

- <span data-ttu-id="eb54c-176">**UX_SUCCESS** (0x00) – передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="eb54c-176">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>

### <a name="example"></a><span data-ttu-id="eb54c-177">Пример</span><span class="sxs-lookup"><span data-stu-id="eb54c-177">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_get();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_set"></a><span data-ttu-id="eb54c-178">ux_device_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="eb54c-178">ux_device_stack_configuration_set</span></span>

<span data-ttu-id="eb54c-179">Установка текущей конфигурации</span><span class="sxs-lookup"><span data-stu-id="eb54c-179">Set the current configuration</span></span>

### <a name="prototype"></a><span data-ttu-id="eb54c-180">Прототип</span><span class="sxs-lookup"><span data-stu-id="eb54c-180">Prototype</span></span>

```c
UINT ux_device_stack_configuration_set(ULONG configuration_value);
```

### <a name="description"></a><span data-ttu-id="eb54c-181">Описание</span><span class="sxs-lookup"><span data-stu-id="eb54c-181">Description</span></span>

<span data-ttu-id="eb54c-182">Эта функция используется узлом для установки текущей конфигурации, используемой на устройстве.</span><span class="sxs-lookup"><span data-stu-id="eb54c-182">This function is used by the host to set the current configuration running in the device.</span></span> <span data-ttu-id="eb54c-183">При получении этой команды стек USB-устройств активирует переменный параметр 0 каждого интерфейса, подключенного к этой конфигурации.</span><span class="sxs-lookup"><span data-stu-id="eb54c-183">Upon reception of this command, the USB device stack will activate the alternate setting 0 of each interface connected to this configuration.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="eb54c-184">Входной параметр</span><span class="sxs-lookup"><span data-stu-id="eb54c-184">Input Parameter</span></span>

- <span data-ttu-id="eb54c-185">**configuration_value** – значение конфигурации, выбранное узлом.</span><span class="sxs-lookup"><span data-stu-id="eb54c-185">**configuration_value** The configuration value selected by the host.</span></span>

### <a name="return-value"></a><span data-ttu-id="eb54c-186">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="eb54c-186">Return Value</span></span>

- <span data-ttu-id="eb54c-187">**UX_SUCCESS** (0x00) – конфигурация выполнена успешно.</span><span class="sxs-lookup"><span data-stu-id="eb54c-187">**UX_SUCCESS** (0x00) The configuration was successfully set.</span></span>

### <a name="example"></a><span data-ttu-id="eb54c-188">Пример</span><span class="sxs-lookup"><span data-stu-id="eb54c-188">Example</span></span>

```c
ULONG configuration_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_set(configuration_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_descriptor_send"></a><span data-ttu-id="eb54c-189">ux_device_stack_descriptor_send</span><span class="sxs-lookup"><span data-stu-id="eb54c-189">ux_device_stack_descriptor_send</span></span>

<span data-ttu-id="eb54c-190">Отправка дескриптора на узел</span><span class="sxs-lookup"><span data-stu-id="eb54c-190">Send a descriptor to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="eb54c-191">Прототип</span><span class="sxs-lookup"><span data-stu-id="eb54c-191">Prototype</span></span>

```c
UINT ux_device_stack_descriptor_send(
    ULONG descriptor_type, 
    ULONG request_index, 
    ULONG host_length);
```

### <a name="description"></a><span data-ttu-id="eb54c-192">Описание</span><span class="sxs-lookup"><span data-stu-id="eb54c-192">Description</span></span>

<span data-ttu-id="eb54c-193">Эта функция используется на стороне устройства для возврата дескриптора в узел.</span><span class="sxs-lookup"><span data-stu-id="eb54c-193">This function is used by the device side to return a descriptor to the host.</span></span> <span data-ttu-id="eb54c-194">Этот дескриптор может быть дескриптором устройства, конфигурации или строки.</span><span class="sxs-lookup"><span data-stu-id="eb54c-194">This descriptor can be a device descriptor, a configuration descriptor or a string descriptor.</span></span>

### <a name="parameters"></a><span data-ttu-id="eb54c-195">Параметры</span><span class="sxs-lookup"><span data-stu-id="eb54c-195">Parameters</span></span>

- <span data-ttu-id="eb54c-196">**descriptor_type**: тип дескриптора.</span><span class="sxs-lookup"><span data-stu-id="eb54c-196">**descriptor_type**: The type of the descriptor.</span></span> <span data-ttu-id="eb54c-197">Необходимо установить одно из следующих значений.</span><span class="sxs-lookup"><span data-stu-id="eb54c-197">Must be one of the following values.</span></span>
  - <span data-ttu-id="eb54c-198">**UX_DEVICE_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="eb54c-198">**UX_DEVICE_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="eb54c-199">**UX_CONFIGURATION_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="eb54c-199">**UX_CONFIGURATION_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="eb54c-200">**UX_STRING_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="eb54c-200">**UX_STRING_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="eb54c-201">**UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="eb54c-201">**UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="eb54c-202">**UX_OTHER_SPEED_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="eb54c-202">**UX_OTHER_SPEED_DESCRIPTOR_ITEM**</span></span>
- <span data-ttu-id="eb54c-203">**request_index**: индекс дескриптора.</span><span class="sxs-lookup"><span data-stu-id="eb54c-203">**request_index**: The index of the descriptor.</span></span>
- <span data-ttu-id="eb54c-204">**host_length**: требуемая длина узла.</span><span class="sxs-lookup"><span data-stu-id="eb54c-204">**host_length**: The length required by the host.</span></span>

### <a name="return-values"></a><span data-ttu-id="eb54c-205">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="eb54c-205">Return Values</span></span>

- <span data-ttu-id="eb54c-206">**UX_SUCCESS** (0x00) – передача данных завершена.</span><span class="sxs-lookup"><span data-stu-id="eb54c-206">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="eb54c-207">**UX_ERROR** (0xFF) перемещение не завершено.</span><span class="sxs-lookup"><span data-stu-id="eb54c-207">**UX_ERROR** (0xFF) The transfer was not completed.</span></span>

### <a name="example"></a><span data-ttu-id="eb54c-208">Пример</span><span class="sxs-lookup"><span data-stu-id="eb54c-208">Example</span></span>

```c
ULONG descriptor_type;
ULONG request_index;
ULONG host_length;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_descriptor_send(descriptor_type, request_index, host_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_disconnect"></a><span data-ttu-id="eb54c-209">ux_device_stack_disconnect</span><span class="sxs-lookup"><span data-stu-id="eb54c-209">ux_device_stack_disconnect</span></span>

<span data-ttu-id="eb54c-210">Отключение стека устройства</span><span class="sxs-lookup"><span data-stu-id="eb54c-210">Disconnect device stack</span></span>

### <a name="prototype"></a><span data-ttu-id="eb54c-211">Прототип</span><span class="sxs-lookup"><span data-stu-id="eb54c-211">Prototype</span></span>

```c
UINT ux_device_stack_disconnect(VOID);
```

### <a name="description"></a><span data-ttu-id="eb54c-212">Описание</span><span class="sxs-lookup"><span data-stu-id="eb54c-212">Description</span></span>

<span data-ttu-id="eb54c-213">Менеджер VBUS вызывает эту функцию при отключении устройства.</span><span class="sxs-lookup"><span data-stu-id="eb54c-213">The VBUS manager calls this function when there is a device disconnection.</span></span> <span data-ttu-id="eb54c-214">Стек устройства оповестит все классы, зарегистрированные на этом устройстве, и затем освободит все ресурсы устройства.</span><span class="sxs-lookup"><span data-stu-id="eb54c-214">The device stack will inform all classes registered to this device and will thereafter release all the device resources.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="eb54c-215">Входной параметр</span><span class="sxs-lookup"><span data-stu-id="eb54c-215">Input Parameter</span></span>

<span data-ttu-id="eb54c-216">Нет</span><span class="sxs-lookup"><span data-stu-id="eb54c-216">None</span></span>

### <a name="return-value"></a><span data-ttu-id="eb54c-217">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="eb54c-217">Return Value</span></span>

- <span data-ttu-id="eb54c-218">**UX_SUCCESS** (0x00) – устройство отключено.</span><span class="sxs-lookup"><span data-stu-id="eb54c-218">**UX_SUCCESS** (0x00) The device was disconnected.</span></span>

### <a name="example"></a><span data-ttu-id="eb54c-219">Пример</span><span class="sxs-lookup"><span data-stu-id="eb54c-219">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_disconnect();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_endpoint_stall"></a><span data-ttu-id="eb54c-220">ux_device_stack_endpoint_stall</span><span class="sxs-lookup"><span data-stu-id="eb54c-220">ux_device_stack_endpoint_stall</span></span>

<span data-ttu-id="eb54c-221">Условие остановки конечной точки запроса</span><span class="sxs-lookup"><span data-stu-id="eb54c-221">Request endpoint Stall condition</span></span>

### <a name="prototype"></a><span data-ttu-id="eb54c-222">Прототип</span><span class="sxs-lookup"><span data-stu-id="eb54c-222">Prototype</span></span>

```c
UINT ux_device_stack_endpoint_stall(UX_SLAVE_ENDPOINT*endpoint);
```

### <a name="description"></a><span data-ttu-id="eb54c-223">Описание</span><span class="sxs-lookup"><span data-stu-id="eb54c-223">Description</span></span>

<span data-ttu-id="eb54c-224">Эта функция вызывается классом USB-устройства, когда конечная точка должна вернуть узлу условие остановки.</span><span class="sxs-lookup"><span data-stu-id="eb54c-224">This function is called by the USB device class when an endpoint should return a Stall condition to the host.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="eb54c-225">Входной параметр</span><span class="sxs-lookup"><span data-stu-id="eb54c-225">Input Parameter</span></span>

- <span data-ttu-id="eb54c-226">**endpoint** – конечная точка, в которой запрашивается условие остановки.</span><span class="sxs-lookup"><span data-stu-id="eb54c-226">**endpoint** The endpoint on which the Stall condition is requested.</span></span>

### <a name="return-value"></a><span data-ttu-id="eb54c-227">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="eb54c-227">Return Value</span></span>

- <span data-ttu-id="eb54c-228">**UX_SUCCESS** (0x00) – операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="eb54c-228">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eb54c-229">**UX_ERROR** (0xFF) устройство находится в недопустимом состоянии.</span><span class="sxs-lookup"><span data-stu-id="eb54c-229">**UX_ERROR** (0xFF) The device is in an invalid state.</span></span>

### <a name="example"></a><span data-ttu-id="eb54c-230">Пример</span><span class="sxs-lookup"><span data-stu-id="eb54c-230">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_endpoint_stall(endpoint);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_host_wakeup"></a><span data-ttu-id="eb54c-231">ux_device_stack_host_wakeup</span><span class="sxs-lookup"><span data-stu-id="eb54c-231">ux_device_stack_host_wakeup</span></span>

<span data-ttu-id="eb54c-232">Активизация узла</span><span class="sxs-lookup"><span data-stu-id="eb54c-232">Wake up the host</span></span>

### <a name="prototype"></a><span data-ttu-id="eb54c-233">Прототип</span><span class="sxs-lookup"><span data-stu-id="eb54c-233">Prototype</span></span>

```c
UINT ux_device_stack_host_wakeup(VOID);
```

### <a name="description"></a><span data-ttu-id="eb54c-234">Описание</span><span class="sxs-lookup"><span data-stu-id="eb54c-234">Description</span></span>

<span data-ttu-id="eb54c-235">Эта функция вызывается, когда устройству требуется активизировать узел.</span><span class="sxs-lookup"><span data-stu-id="eb54c-235">This function is called when the device wants to wake up the host.</span></span> <span data-ttu-id="eb54c-236">Эта команда допустима, только если устройство находится в режиме приостановки.</span><span class="sxs-lookup"><span data-stu-id="eb54c-236">This command is only valid when the device is in suspend mode.</span></span> <span data-ttu-id="eb54c-237">Приложение устройства может решить, когда требуется активизировать USB-узел.</span><span class="sxs-lookup"><span data-stu-id="eb54c-237">It is up to the device application to decide when it wants to wake up the USB host.</span></span> <span data-ttu-id="eb54c-238">Например, USB-модем может активизировать узел при обнаружении сигнала вызова по телефонной линии.</span><span class="sxs-lookup"><span data-stu-id="eb54c-238">For instance, a USB modem can wake up a host when it detects a RING signal on the telephone line.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="eb54c-239">Входной параметр</span><span class="sxs-lookup"><span data-stu-id="eb54c-239">Input Parameter</span></span>

<span data-ttu-id="eb54c-240">Нет</span><span class="sxs-lookup"><span data-stu-id="eb54c-240">None</span></span>

### <a name="return-values"></a><span data-ttu-id="eb54c-241">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="eb54c-241">Return values</span></span>

- <span data-ttu-id="eb54c-242">**UX_SUCCESS** (0x00) – вызов успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="eb54c-242">**UX_SUCCESS** (0x00) The call was successful.</span></span>
- <span data-ttu-id="eb54c-243">**UX_FUNCTION_NOT_SUPPORTED** (0x54) – сбой вызова (возможно, устройство не находится в приостановленном режиме).</span><span class="sxs-lookup"><span data-stu-id="eb54c-243">**UX_FUNCTION_NOT_SUPPORTED** (0x54) The call failed (the device was probably not in the suspended mode).</span></span>

### <a name="example"></a><span data-ttu-id="eb54c-244">Пример</span><span class="sxs-lookup"><span data-stu-id="eb54c-244">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_host_wakeup();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_initialize"></a><span data-ttu-id="eb54c-245">ux_device_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="eb54c-245">ux_device_stack_initialize</span></span>

<span data-ttu-id="eb54c-246">Инициализация стека устройств USB</span><span class="sxs-lookup"><span data-stu-id="eb54c-246">Initialize USB device stack</span></span>

### <a name="prototype"></a><span data-ttu-id="eb54c-247">Прототип</span><span class="sxs-lookup"><span data-stu-id="eb54c-247">Prototype</span></span>

```c
UINT ux_device_stack_initialize(
    UCHAR *device_framework_high_speed,
    ULONG device_framework_length_high_speed,
    UCHAR *device_framework_full_speed,
    ULONG device_framework_length_full_speed,
    UCHAR *string_framework,
    ULONG string_framework_length,
    UCHAR *language_id_framework,
    ULONG language_id_framework_length),
    UINT (*ux_system_slave_change_function)(ULONG)));
```

### <a name="description"></a><span data-ttu-id="eb54c-248">Описание</span><span class="sxs-lookup"><span data-stu-id="eb54c-248">Description</span></span>

<span data-ttu-id="eb54c-249">Эта функция вызывается приложением для инициализации стека USB-устройства.</span><span class="sxs-lookup"><span data-stu-id="eb54c-249">This function is called by the application to initialize the USB device stack.</span></span> <span data-ttu-id="eb54c-250">Она не инициализирует классы или контроллеры.</span><span class="sxs-lookup"><span data-stu-id="eb54c-250">It does not initialize any classes or any controllers.</span></span> <span data-ttu-id="eb54c-251">Для этого необходимо выполнить отдельные вызовы функций.</span><span class="sxs-lookup"><span data-stu-id="eb54c-251">This should be done with separate function calls.</span></span> <span data-ttu-id="eb54c-252">Этот вызов в основном предназначен для создания платформы устройства для функции USB в стеке.</span><span class="sxs-lookup"><span data-stu-id="eb54c-252">This call mainly provides the stack with the device framework for the USB function.</span></span> <span data-ttu-id="eb54c-253">Он поддерживает как высокую, так и полную скорость с возможностью полного разделения платформ устройств для каждой скорости.</span><span class="sxs-lookup"><span data-stu-id="eb54c-253">It supports both high and full speeds with the possibility to have completely separate device framework for each speed.</span></span> <span data-ttu-id="eb54c-254">Поддерживается строковая платформа и различные языки.</span><span class="sxs-lookup"><span data-stu-id="eb54c-254">String framework and multiple languages are supported.</span></span>

### <a name="parameters"></a><span data-ttu-id="eb54c-255">Параметры</span><span class="sxs-lookup"><span data-stu-id="eb54c-255">Parameters</span></span>

- <span data-ttu-id="eb54c-256">**device_framework_high_speed**: указатель на платформу высокой скорости.</span><span class="sxs-lookup"><span data-stu-id="eb54c-256">**device_framework_high_speed**: Pointer to the high speed framework.</span></span>
- <span data-ttu-id="eb54c-257">**device_framework_length_high_speed**: длина платформы высокой скорости.</span><span class="sxs-lookup"><span data-stu-id="eb54c-257">**device_framework_length_high_speed**: Length of the high speed framework.</span></span>
- <span data-ttu-id="eb54c-258">**device_framework_full_speed**: указатель на платформу максимальной скорости.</span><span class="sxs-lookup"><span data-stu-id="eb54c-258">**device_framework_full_speed**: Pointer to the full speed framework.</span></span>
- <span data-ttu-id="eb54c-259">**device_framework_length_full_speed**: длина платформы максимальной скорости.</span><span class="sxs-lookup"><span data-stu-id="eb54c-259">**device_framework_length_full_speed**: Length of the full speed framework.</span></span>
- <span data-ttu-id="eb54c-260">**string_framework**: указатель на строковую платформу.</span><span class="sxs-lookup"><span data-stu-id="eb54c-260">**string_framework**: Pointer to string framework.</span></span>
- <span data-ttu-id="eb54c-261">**string_framework**: указатель на строковую платформу.</span><span class="sxs-lookup"><span data-stu-id="eb54c-261">**string_framework_length**: Length of string framework.</span></span>
- <span data-ttu-id="eb54c-262">**language_id_framework**: указатель на строковую языковую платформу.</span><span class="sxs-lookup"><span data-stu-id="eb54c-262">**language_id_framework**: Pointer to string language framework.</span></span>
- <span data-ttu-id="eb54c-263">**language_id_framework_length**: длина строковой языковой платформы.</span><span class="sxs-lookup"><span data-stu-id="eb54c-263">**language_id_framework_length**: Length of the string language framework.</span></span>
- <span data-ttu-id="eb54c-264">**ux_system_slave_change_function**: функция, вызываемая при изменении состояния устройства.</span><span class="sxs-lookup"><span data-stu-id="eb54c-264">**ux_system_slave_change_function**: Function to be called when the device state changes.</span></span>

### <a name="return-values"></a><span data-ttu-id="eb54c-265">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="eb54c-265">Return Values</span></span>

- <span data-ttu-id="eb54c-266">**UX_SUCCESS** (0x00) – операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="eb54c-266">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eb54c-267">**UX_MEMORY_INSUFFICIENT** (0x12) – недостаточно памяти для инициализации стека.</span><span class="sxs-lookup"><span data-stu-id="eb54c-267">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to initialize the stack.</span></span>
- <span data-ttu-id="eb54c-268">**UX_DESCRIPTOR_CORRUPTED** (0x42) — недопустимый дескриптор.</span><span class="sxs-lookup"><span data-stu-id="eb54c-268">**UX_DESCRIPTOR_CORRUPTED** (0x42) The descriptor is invalid.</span></span>

### <a name="example"></a><span data-ttu-id="eb54c-269">Пример</span><span class="sxs-lookup"><span data-stu-id="eb54c-269">Example</span></span>

```c
/* Example of a device framework */

#define DEVICE_FRAMEWORK_LENGTH_FULL_SPEED 50

UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0xec, 0x08, 0x10, 0x00, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00
};

#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60

UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};

/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string */

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72,0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};

/* Multiple languages are supported on the device, to add a language besides English, 
  the Unicode language code must be appended to the language_id_framework array 
  and the length adjusted accordingly. */

#define LANGUAGE_ID_FRAMEWORK_LENGTH 2

UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

<span data-ttu-id="eb54c-270">Приложение может запросить обратный вызов, когда контроллер изменит свое состояние.</span><span class="sxs-lookup"><span data-stu-id="eb54c-270">The application can request a call back when the controller changes its state.</span></span> <span data-ttu-id="eb54c-271">Два основных состояния контроллера:</span><span class="sxs-lookup"><span data-stu-id="eb54c-271">The two main states for the controller are:</span></span>

- <span data-ttu-id="eb54c-272">**UX_DEVICE_SUSPENDED**</span><span class="sxs-lookup"><span data-stu-id="eb54c-272">**UX_DEVICE_SUSPENDED**</span></span>
- <span data-ttu-id="eb54c-273">**UX_DEVICE_RESUMED**</span><span class="sxs-lookup"><span data-stu-id="eb54c-273">**UX_DEVICE_RESUMED**</span></span>

<span data-ttu-id="eb54c-274">Если приложению не требуются сигналы приостановки / возобновления работы, то будет выполнена функция UX_NULL.</span><span class="sxs-lookup"><span data-stu-id="eb54c-274">If the application does not need Suspend/Resume signals, it would supply a UX_NULL function.</span></span>

```c
UINT status;

/* The code below is required for installing the device portion of USBX. 
    There is no call back for device status change in this example. */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, initialization was successful. */
```

### <a name="ux_device_stack_interface_delete"></a><span data-ttu-id="eb54c-275">ux_device_stack_interface_delete</span><span class="sxs-lookup"><span data-stu-id="eb54c-275">ux_device_stack_interface_delete</span></span>

<span data-ttu-id="eb54c-276">Удаление интерфейса стека</span><span class="sxs-lookup"><span data-stu-id="eb54c-276">Delete a stack interface</span></span>

### <a name="prototype"></a><span data-ttu-id="eb54c-277">Прототип</span><span class="sxs-lookup"><span data-stu-id="eb54c-277">Prototype</span></span>

```c
UINT ux_device_stack_interface_delete(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a><span data-ttu-id="eb54c-278">Описание</span><span class="sxs-lookup"><span data-stu-id="eb54c-278">Description</span></span>

<span data-ttu-id="eb54c-279">Эта функция вызывается для удаления интерфейса.</span><span class="sxs-lookup"><span data-stu-id="eb54c-279">This function is called when an interface should be removed.</span></span> <span data-ttu-id="eb54c-280">Интерфейс либо удаляется при извлечении устройства или после сброса шины, либо при наличии нового альтернативного параметра.</span><span class="sxs-lookup"><span data-stu-id="eb54c-280">An interface is either removed when a device is extracted, or following a bus reset, or when there is a new alternate setting.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="eb54c-281">Входной параметр</span><span class="sxs-lookup"><span data-stu-id="eb54c-281">Input Parameter</span></span>

- <span data-ttu-id="eb54c-282">**interface**: указатель на интерфейс, который необходимо удалить.</span><span class="sxs-lookup"><span data-stu-id="eb54c-282">**interface**: Pointer to the interface to remove.</span></span>

### <a name="return-value"></a><span data-ttu-id="eb54c-283">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="eb54c-283">Return Value</span></span>

- <span data-ttu-id="eb54c-284">**UX_SUCCESS** (0x00) – операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="eb54c-284">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="eb54c-285">Пример</span><span class="sxs-lookup"><span data-stu-id="eb54c-285">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_delete(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_get"></a><span data-ttu-id="eb54c-286">ux_device_stack_interface_get</span><span class="sxs-lookup"><span data-stu-id="eb54c-286">ux_device_stack_interface_get</span></span>

<span data-ttu-id="eb54c-287">Получение значения текущего интерфейса</span><span class="sxs-lookup"><span data-stu-id="eb54c-287">Get the current interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="eb54c-288">Прототип</span><span class="sxs-lookup"><span data-stu-id="eb54c-288">Prototype</span></span>

```c
UINT ux_device_stack_interface_get(UINT interface_value);
```

### <a name="description"></a><span data-ttu-id="eb54c-289">Описание</span><span class="sxs-lookup"><span data-stu-id="eb54c-289">Description</span></span>

<span data-ttu-id="eb54c-290">Эта функция вызывается, когда узел запрашивает текущий интерфейс.</span><span class="sxs-lookup"><span data-stu-id="eb54c-290">This function is called when the host queries the current interface.</span></span> <span data-ttu-id="eb54c-291">Устройство возвращает текущее значение интерфейса.</span><span class="sxs-lookup"><span data-stu-id="eb54c-291">The device returns the current interface value.</span></span>

> [!NOTE]
> <span data-ttu-id="eb54c-292">Эта функция является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="eb54c-292">This function is deprecated.</span></span> <span data-ttu-id="eb54c-293">Он доступен для устаревшего программного обеспечения, но новое программное обеспечение должно использовать функцию ***ux_device_stack_alternate_setting_get***.</span><span class="sxs-lookup"><span data-stu-id="eb54c-293">It is available for legacy software, but new software should use the ***ux_device_stack_alternate_setting_get*** function instead.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="eb54c-294">Входной параметр</span><span class="sxs-lookup"><span data-stu-id="eb54c-294">Input Parameter</span></span>

- <span data-ttu-id="eb54c-295">**interface_value** – возвращаемое значение интерфейса.</span><span class="sxs-lookup"><span data-stu-id="eb54c-295">**interface_value** Interface value to return.</span></span>

### <a name="return-values"></a><span data-ttu-id="eb54c-296">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="eb54c-296">Return Values</span></span>

- <span data-ttu-id="eb54c-297">**UX_SUCCESS** (0x00) – операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="eb54c-297">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eb54c-298">**UX_ERROR** (0xFF) – интерфейс не существует.</span><span class="sxs-lookup"><span data-stu-id="eb54c-298">**UX_ERROR** (0xFF) No interface exists.</span></span>

### <a name="example"></a><span data-ttu-id="eb54c-299">Пример</span><span class="sxs-lookup"><span data-stu-id="eb54c-299">Example</span></span>

```c
ULONG interface_value;

UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_set"></a><span data-ttu-id="eb54c-300">ux_device_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="eb54c-300">ux_device_stack_interface_set</span></span>

<span data-ttu-id="eb54c-301">Изменение альтернативного параметра интерфейса</span><span class="sxs-lookup"><span data-stu-id="eb54c-301">Change the alternate setting of the interface</span></span>

### <a name="prototype"></a><span data-ttu-id="eb54c-302">Прототип</span><span class="sxs-lookup"><span data-stu-id="eb54c-302">Prototype</span></span>

```c
UINT ux_device_stack_interface_set(
    UCHAR *device_framework,
    ULONG device_framework_length, 
    ULONG alternate_setting_value);
```

### <a name="description"></a><span data-ttu-id="eb54c-303">Описание</span><span class="sxs-lookup"><span data-stu-id="eb54c-303">Description</span></span>

<span data-ttu-id="eb54c-304">Эта функция вызывается, когда узел запрашивает изменение альтернативного параметра для интерфейса.</span><span class="sxs-lookup"><span data-stu-id="eb54c-304">This function is called when the host requests a change of the alternate setting for the interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="eb54c-305">Параметры</span><span class="sxs-lookup"><span data-stu-id="eb54c-305">Parameters</span></span>

- <span data-ttu-id="eb54c-306">**device_framework**: адрес платформы устройства для этого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="eb54c-306">**device_framework**: Address of the device framework for this interface.</span></span>
- <span data-ttu-id="eb54c-307">**device_framework_length**: длина платформы устройства.</span><span class="sxs-lookup"><span data-stu-id="eb54c-307">**device_framework_length**: Length of the device framework.</span></span>
- <span data-ttu-id="eb54c-308">**alternate_setting_value**: значение альтернативного параметра, которое будет использоваться этим интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="eb54c-308">**alternate_setting_value**: Alternate setting value to be used by this interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="eb54c-309">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="eb54c-309">Return Values</span></span>

- <span data-ttu-id="eb54c-310">**UX_SUCCESS** (0x00) – операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="eb54c-310">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eb54c-311">**UX_ERROR** (0xFF) – интерфейс не существует.</span><span class="sxs-lookup"><span data-stu-id="eb54c-311">**UX_ERROR** (0xFF) No interface exists.</span></span>

### <a name="example"></a><span data-ttu-id="eb54c-312">Пример</span><span class="sxs-lookup"><span data-stu-id="eb54c-312">Example</span></span>

```c
UCHAR * device_framework
ULONG device_framework_length;
ULONG alternate_setting_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_set(device_framework,
    device_framework_length, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_start"></a><span data-ttu-id="eb54c-313">ux_device_stack_interface_start</span><span class="sxs-lookup"><span data-stu-id="eb54c-313">ux_device_stack_interface_start</span></span>

<span data-ttu-id="eb54c-314">Запуск поиска класса, к которому будет принадлежать экземпляр интерфейса</span><span class="sxs-lookup"><span data-stu-id="eb54c-314">Start search for a class to own an interface instance</span></span>

### <a name="prototype"></a><span data-ttu-id="eb54c-315">Прототип</span><span class="sxs-lookup"><span data-stu-id="eb54c-315">Prototype</span></span>

```c
UINT ux_device_stack_interface_start(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a><span data-ttu-id="eb54c-316">Описание</span><span class="sxs-lookup"><span data-stu-id="eb54c-316">Description</span></span>

<span data-ttu-id="eb54c-317">Эта функция вызывается, когда узел выбирает интерфейс и в стеке устройства необходимо найти класс устройства для этого экземпляра интерфейса.</span><span class="sxs-lookup"><span data-stu-id="eb54c-317">This function is called when an interface has been selected by the host and the device stack needs to search for a device class to own this interface instance.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="eb54c-318">Входной параметр</span><span class="sxs-lookup"><span data-stu-id="eb54c-318">Input Parameter</span></span>

- <span data-ttu-id="eb54c-319">**interface**: указатель на созданный интерфейс.</span><span class="sxs-lookup"><span data-stu-id="eb54c-319">**interface**: Pointer to the interface created.</span></span>

### <a name="return-values"></a><span data-ttu-id="eb54c-320">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="eb54c-320">Return Values</span></span>

- <span data-ttu-id="eb54c-321">**UX_SUCCESS** (0x00) – операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="eb54c-321">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eb54c-322">**UX_NO_CLASS_MATCH** (0x57) – нет класса для этого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="eb54c-322">**UX_NO_CLASS_MATCH** (0x57) No class exists for this interface.</span></span>

### <a name="example"></a><span data-ttu-id="eb54c-323">Пример</span><span class="sxs-lookup"><span data-stu-id="eb54c-323">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_start(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_transfer_request"></a><span data-ttu-id="eb54c-324">ux_device_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="eb54c-324">ux_device_stack_transfer_request</span></span>

<span data-ttu-id="eb54c-325">Запрос на перемещение данных на узел</span><span class="sxs-lookup"><span data-stu-id="eb54c-325">Request to transfer data to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="eb54c-326">Прототип</span><span class="sxs-lookup"><span data-stu-id="eb54c-326">Prototype</span></span>

```c
UINT ux_device_stack_transfer_request(
    UX_SLAVE_TRANSFER *transfer_request,
    ULONG slave_length, 
    ULONG host_length);
```

### <a name="description"></a><span data-ttu-id="eb54c-327">Описание</span><span class="sxs-lookup"><span data-stu-id="eb54c-327">Description</span></span>

<span data-ttu-id="eb54c-328">Эта функция вызывается, когда класс или стек желает передать данные на узел.</span><span class="sxs-lookup"><span data-stu-id="eb54c-328">This function is called when a class or the stack wants to transfer data to the host.</span></span> <span data-ttu-id="eb54c-329">Узел всегда опрашивает устройство, но устройство может заранее подготовить данные.</span><span class="sxs-lookup"><span data-stu-id="eb54c-329">The host always polls the device but the device can prepare data in advance.</span></span>

### <a name="parameters"></a><span data-ttu-id="eb54c-330">Параметры</span><span class="sxs-lookup"><span data-stu-id="eb54c-330">Parameters</span></span>

- <span data-ttu-id="eb54c-331">**transfer_request**: указатель на запрос на перемещение.</span><span class="sxs-lookup"><span data-stu-id="eb54c-331">**transfer_request**: Pointer to the transfer request.</span></span>
- <span data-ttu-id="eb54c-332">**slave_length**: длина данных, возвращаемых устройством.</span><span class="sxs-lookup"><span data-stu-id="eb54c-332">**slave_length**: Length the device wants to return.</span></span>
- <span data-ttu-id="eb54c-333">**host_length**: длина данных, запрашиваемых узлом.</span><span class="sxs-lookup"><span data-stu-id="eb54c-333">**host_length**: Length the host has requested.</span></span>

### <a name="return-values"></a><span data-ttu-id="eb54c-334">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="eb54c-334">Return Values</span></span>

- <span data-ttu-id="eb54c-335">**UX_SUCCESS** (0x00) – операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="eb54c-335">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="eb54c-336">**UX_TRANSFER_NOT_READY** (0x25) – устройство находится в недопустимом состоянии; допустимы состояния **ATTACHED**, **CONFIGURED** или **ADDRESSED**.</span><span class="sxs-lookup"><span data-stu-id="eb54c-336">**UX_TRANSFER_NOT_READY** (0x25) The device is in an invalid state; it must be **ATTACHED**, **CONFIGURED**, or **ADDRESSED**.</span></span>
- <span data-ttu-id="eb54c-337">**UX_ERROR** (0xFF) – ошибка передачи.</span><span class="sxs-lookup"><span data-stu-id="eb54c-337">**UX_ERROR** (0xFF) Transport error.</span></span>

### <a name="example"></a><span data-ttu-id="eb54c-338">Пример</span><span class="sxs-lookup"><span data-stu-id="eb54c-338">Example</span></span>

```c
UINT status;

/* The following example illustrates how to transfer more data than an application requests. */
while(total_length) {
    /* How much can we send in this transfer? */
    if (total_length > UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE)
        transfer_length = UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE;
    else
        transfer_length = total_length;

   /* Copy the Storage Buffer into the transfer request memory. */
   ux_utility_memory_copy(transfer_request ->  ux_slave_transfer_request_data_pointer,
       media_memory, transfer_length);

   /* Send the data payload back to the caller. */
   status = ux_device_transfer_request(transfer_request,
       transfer_length, transfer_length);

   /* If status equals UX_SUCCESS, the operation was successful. */

   /* Update the buffer address.  */
    media_memory += transfer_length;

   /* Update the length to remain. */
    total_length -= transfer_length;
}
```

### <a name="ux_device_stack_transfer_abort"></a><span data-ttu-id="eb54c-339">ux_device_stack_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="eb54c-339">ux_device_stack_transfer_abort</span></span>

<span data-ttu-id="eb54c-340">Отмена запроса на перемещение</span><span class="sxs-lookup"><span data-stu-id="eb54c-340">Cancel a transfer request</span></span>

### <a name="prototype"></a><span data-ttu-id="eb54c-341">Прототип</span><span class="sxs-lookup"><span data-stu-id="eb54c-341">Prototype</span></span>

```c
UINT ux_device_stack_transfer_abort(
    UX_SLAVE_TRANSFER *transfer_request, 
    ULONG completion_code);
```

### <a name="description"></a><span data-ttu-id="eb54c-342">Описание</span><span class="sxs-lookup"><span data-stu-id="eb54c-342">Description</span></span>

<span data-ttu-id="eb54c-343">Эта функция вызывается, когда приложению требуется отменить запрос на передачу или если стеку необходимо прервать запрос на передачу, связанный с конечной точкой.</span><span class="sxs-lookup"><span data-stu-id="eb54c-343">This function is called when an application needs to cancel a transfer request or when the stack needs to abort a transfer request associated with an endpoint.</span></span>

### <a name="parameters"></a><span data-ttu-id="eb54c-344">Параметры</span><span class="sxs-lookup"><span data-stu-id="eb54c-344">Parameters</span></span>

- <span data-ttu-id="eb54c-345">**transfer_request**: указатель на запрос на перемещение.</span><span class="sxs-lookup"><span data-stu-id="eb54c-345">**transfer_request**: Pointer to the transfer request.</span></span>
- <span data-ttu-id="eb54c-346">**completion_code**: код ошибки, возвращаемый классу, ожидающему завершения этого запроса на передачу.</span><span class="sxs-lookup"><span data-stu-id="eb54c-346">**completion_code**: Error code to be returned to the class waiting for this transfer request to complete.</span></span>

### <a name="return-value"></a><span data-ttu-id="eb54c-347">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="eb54c-347">Return Value</span></span>

- <span data-ttu-id="eb54c-348">**UX_SUCCESS** (0x00) – операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="eb54c-348">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="eb54c-349">Пример</span><span class="sxs-lookup"><span data-stu-id="eb54c-349">Example</span></span>

```c
UINT status;

/* The following example illustrates how to abort a transfer when a
    bus reset has been detected on the bus. */
status = ux_device_stack_transfer_abort(transfer_request, UX_TRANSFER_BUS_RESET);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_uninitialize"></a><span data-ttu-id="eb54c-350">ux_device_stack_uninitialize</span><span class="sxs-lookup"><span data-stu-id="eb54c-350">ux_device_stack_uninitialize</span></span>

<span data-ttu-id="eb54c-351">Отмена инициализации стека</span><span class="sxs-lookup"><span data-stu-id="eb54c-351">Unitialize stack</span></span>

### <a name="prototype"></a><span data-ttu-id="eb54c-352">Прототип</span><span class="sxs-lookup"><span data-stu-id="eb54c-352">Prototype</span></span>

```c
UINT ux_device_stack_uninitialize();
```

### <a name="description"></a><span data-ttu-id="eb54c-353">Описание</span><span class="sxs-lookup"><span data-stu-id="eb54c-353">Description</span></span>

<span data-ttu-id="eb54c-354">Эта функция вызывается, когда приложению необходимо отменить инициализацию стека устройств USBX — все ресурсы стека устройств высвобождаются.</span><span class="sxs-lookup"><span data-stu-id="eb54c-354">This function is called when an application needs to unitialize the USBX device stack – all device stack resources are freed.</span></span> <span data-ttu-id="eb54c-355">Этот метод должен вызываться после отмены регистрации всех классов с помощью функции ux_device_stack_class_unregister.</span><span class="sxs-lookup"><span data-stu-id="eb54c-355">This should be called after all classes have been unregistered via ux_device_stack_class_unregister.</span></span>

### <a name="parameters"></a><span data-ttu-id="eb54c-356">Параметры</span><span class="sxs-lookup"><span data-stu-id="eb54c-356">Parameters</span></span>

<span data-ttu-id="eb54c-357">Отсутствуют</span><span class="sxs-lookup"><span data-stu-id="eb54c-357">None</span></span>

### <a name="return-value"></a><span data-ttu-id="eb54c-358">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="eb54c-358">Return Value</span></span>

<span data-ttu-id="eb54c-359">**UX_SUCCESS** (0x00) – операция успешно выполнена.</span><span class="sxs-lookup"><span data-stu-id="eb54c-359">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
