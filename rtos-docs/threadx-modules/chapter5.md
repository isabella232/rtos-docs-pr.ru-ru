---
title: Глава 5. API-интерфейсы диспетчера модулей
author: philmea
description: Эта статья представляет сводные данные API-интерфейсов диспетчера модулей, доступных для резидентной части приложения.
ms.author: philmea
ms.date: 07/15/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: ca0fee443c23fd1bdd34651f4a7b31cf71f886f0
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814376"
---
# <a name="chapter-5---module-manager-apis"></a><span data-ttu-id="0ef6a-103">Глава 5. API-интерфейсы диспетчера модулей</span><span class="sxs-lookup"><span data-stu-id="0ef6a-103">Chapter 5 - Module Manager APIs</span></span>

## <a name="summary-of-module-manager-apis"></a><span data-ttu-id="0ef6a-104">Сводка по API-интерфейсам диспетчера модулей</span><span class="sxs-lookup"><span data-stu-id="0ef6a-104">Summary of Module Manager APIs</span></span>

<span data-ttu-id="0ef6a-105">Существует несколько дополнительных API, доступных для резидентной части приложения. Они перечислены ниже.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-105">There are several additional APIs available to the resident portion of the application, as follows.</span></span>

- <span data-ttu-id="0ef6a-106">***txm_module_manager_external_memory_enable** _ — _разрешить доступ модуля к общей памяти*</span><span class="sxs-lookup"><span data-stu-id="0ef6a-106">***txm_module_manager_external_memory_enable** _ - _Enable module access to a shared memory space*</span></span>
- <span data-ttu-id="0ef6a-107">***txm_module_manager_file_load** _ — _загрузить модуль из файла с помощью FileX*</span><span class="sxs-lookup"><span data-stu-id="0ef6a-107">***txm_module_manager_file_load** _ - _Load module from file via FileX*</span></span>
- <span data-ttu-id="0ef6a-108">***txm_module_manager_in_place_load** _ — _загрузить данные модуля, выполнение на месте*</span><span class="sxs-lookup"><span data-stu-id="0ef6a-108">***txm_module_manager_in_place_load** _ - _Load module data, execute in place*</span></span>
- <span data-ttu-id="0ef6a-109">***txm_module_manager_initialize** _ — _инициализация диспетчера модулей*</span><span class="sxs-lookup"><span data-stu-id="0ef6a-109">***txm_module_manager_initialize** _ - _Initialize the module manager*</span></span>
- <span data-ttu-id="0ef6a-110">***txm_module_manager_mm_initialize** _ — _инициализация оборудования для управления памятью*</span><span class="sxs-lookup"><span data-stu-id="0ef6a-110">***txm_module_manager_mm_initialize** _ - _Initialize the memory management hardware*</span></span>
- <span data-ttu-id="0ef6a-111">***txm_module_manager_maximum_module_priority_set** _ — _установить максимальный приоритет потока, разрешенный в модуле*</span><span class="sxs-lookup"><span data-stu-id="0ef6a-111">***txm_module_manager_maximum_module_priority_set** _ - _Set the maximum thread priority allowed in a module*</span></span>
- <span data-ttu-id="0ef6a-112">***txm_module_manager_memory_fault_notify** _ — _регистрация обратного вызова приложения при сбое памяти*</span><span class="sxs-lookup"><span data-stu-id="0ef6a-112">***txm_module_manager_memory_fault_notify** _ - _Register an application callback on memory fault*</span></span>
- <span data-ttu-id="0ef6a-113">***txm_module_manager_memory_load** _ — _загрузить модуль из памяти*</span><span class="sxs-lookup"><span data-stu-id="0ef6a-113">***txm_module_manager_memory_load** _ - _Load the module from memory*</span></span>
- <span data-ttu-id="0ef6a-114">***txm_module_manager_object_pool_create** _ — _создать пул объектов для модулей*</span><span class="sxs-lookup"><span data-stu-id="0ef6a-114">***txm_module_manager_object_pool_create** _ - _Create an object pool for modules*</span></span>
- <span data-ttu-id="0ef6a-115">***txm_module_manager_properties_get** _ — _получить свойства модуля*</span><span class="sxs-lookup"><span data-stu-id="0ef6a-115">***txm_module_manager_properties_get** _ - _Get module properties*</span></span>
- <span data-ttu-id="0ef6a-116">***txm_module_manager_start** _ — _начать выполнение указанного модуля*</span><span class="sxs-lookup"><span data-stu-id="0ef6a-116">***txm_module_manager_start** _ - _Start execution of the specified module*</span></span>
- <span data-ttu-id="0ef6a-117">***txm_module_manager_stop** _ — _прервать выполнение указанного модуля*</span><span class="sxs-lookup"><span data-stu-id="0ef6a-117">***txm_module_manager_stop** _ - _Stop execution of the specified module*</span></span>
- <span data-ttu-id="0ef6a-118">***txm_module_manager_unload** _ — _выгрузить модуль*</span><span class="sxs-lookup"><span data-stu-id="0ef6a-118">***txm_module_manager_unload** _ - _Unload the module*</span></span>

---

## <a name="txm_module_manager_external_memory_enable"></a><span data-ttu-id="0ef6a-119">txm_module_manager_external_memory_enable</span><span class="sxs-lookup"><span data-stu-id="0ef6a-119">txm_module_manager_external_memory_enable</span></span>

<span data-ttu-id="0ef6a-120">Разрешить модулю доступ к общему пространству памяти.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-120">Enable module to access a shared memory space.</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef6a-121">Прототип</span><span class="sxs-lookup"><span data-stu-id="0ef6a-121">Prototype</span></span>

```c
UINT txm_module_manager_external_memory_enable(
     TXM_MODULE_INSTANCE *module_instance,
     VOID *start_address,
     ULONG length,
     UINT attributes);
```

### <a name="description"></a><span data-ttu-id="0ef6a-122">Описание</span><span class="sxs-lookup"><span data-stu-id="0ef6a-122">Description</span></span>

<span data-ttu-id="0ef6a-123">Эта служба создает запись в таблице оборудования управления памятью для области общей памяти, к которой модуль может получить доступ.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-123">This service creates an entry in the memory management hardware table for a shared memory region that the module can access.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0ef6a-124">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0ef6a-124">Input parameters</span></span>

- <span data-ttu-id="0ef6a-125">**module_instance** — указатель на экземпляр модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-125">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="0ef6a-126">**start_address** — начальный адрес области общей памяти.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-126">**start_address** Starting address of shared memory region.</span></span>
- <span data-ttu-id="0ef6a-127">**length** — длина области общей памяти.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-127">**length** Length of shared memory region.</span></span>
- <span data-ttu-id="0ef6a-128">**attributes** — атрибуты области памяти (кэш, чтение, запись и т. д.).</span><span class="sxs-lookup"><span data-stu-id="0ef6a-128">**attributes** Attributes of memory region (cache, read, write, etc.).</span></span> <span data-ttu-id="0ef6a-129">Атрибуты зависят от конкретного порта. Формат атрибутов см. в [приложении](appendix.md).</span><span class="sxs-lookup"><span data-stu-id="0ef6a-129">Attributes are port-specific; see [appendix](appendix.md) for attributes format.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef6a-130">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0ef6a-130">Return values</span></span>

- <span data-ttu-id="0ef6a-131">**TX_SUCCESS** (0x00) — запись в памяти успешно создана.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-131">**TX_SUCCESS** (0x00) Memory entry created successfully.</span></span>
- <span data-ttu-id="0ef6a-132">**TX_NOT_AVAILABLE** (0x1D) — диспетчер не инициализирован или функция недоступна.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-132">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized or feature not available.</span></span>
- <span data-ttu-id="0ef6a-133">**TX_PTR_ERROR** (0x03) — недопустимый экземпляр модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-133">**TX_PTR_ERROR** (0x03) Invalid module instance.</span></span>
- <span data-ttu-id="0ef6a-134">**TX_START_ERROR** (0x10) — модуль не находится в загруженном состоянии.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-134">**TX_START_ERROR** (0x10) Module not in loaded state.</span></span>
- <span data-ttu-id="0ef6a-135">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) — недопустимое выравнивание начального адреса.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-135">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid start address alignment.</span></span>
- <span data-ttu-id="0ef6a-136">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) — несовместимые свойства.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-136">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef6a-137">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0ef6a-137">Allowed from</span></span>

<span data-ttu-id="0ef6a-138">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="0ef6a-138">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="0ef6a-139">Например, .</span><span class="sxs-lookup"><span data-stu-id="0ef6a-139">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Create a shared memory space 256 bytes long at address 0x64005000
   with read & write, no execute, outer & inner write back cache
   attributes. Note that these attributes are port-specific. */
txm_module_manager_external_memory_enable(&my_module, (VOID*)0x64005000, 256, 0x3F);
```

---

## <a name="txm_module_manager_file_load"></a><span data-ttu-id="0ef6a-140">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="0ef6a-140">txm_module_manager_file_load</span></span>

<span data-ttu-id="0ef6a-141">Загрузка модуля из файла с помощью FileX.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-141">Load module from file via FileX.</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef6a-142">Прототип</span><span class="sxs-lookup"><span data-stu-id="0ef6a-142">Prototype</span></span>

```c
UINT txm_module_manager_file_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```

### <a name="description"></a><span data-ttu-id="0ef6a-143">Описание</span><span class="sxs-lookup"><span data-stu-id="0ef6a-143">Description</span></span>

<span data-ttu-id="0ef6a-144">Эта служба загружает двоичный образ модуля, содержащегося в указанном файле, в область памяти модуля и готовит его к выполнению.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-144">This service loads the binary image of the module contained in the specified file into the module memory area and prepares it for execution.</span></span> <span data-ttu-id="0ef6a-145">Предполагается, что указанный носитель уже открыт.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-145">It is assumed that the supplied media is already opened.</span></span>

> [!NOTE]
> <span data-ttu-id="0ef6a-146">Для загрузки файла используется система FileX.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-146">The FileX system is utilized to load the file.</span></span> <span data-ttu-id="0ef6a-147">Чтобы включить доступ к FileX, модуль, библиотека модулей, диспетчер модулей и библиотека ThreadX (с исходным кодом диспетчера модулей) должны быть построены с параметром **FX_FILEX_PRESENT**, определенным в проектах.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-147">In order to enable FileX access, the module, module library, Module Manager and the ThreadX library (with the Module Manager sources) must be built with **FX_FILEX_PRESENT** defined in the projects.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0ef6a-148">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0ef6a-148">Input parameters</span></span>

- <span data-ttu-id="0ef6a-149">**module_instance** — указатель на экземпляр модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-149">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="0ef6a-150">**module_name** — имя модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-150">**module_name** Name of the module.</span></span>
- <span data-ttu-id="0ef6a-151">**media_ptr** — указатель на уже открытый носитель FileX.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-151">**media_ptr** Pointer to already opened FileX media.</span></span>
- <span data-ttu-id="0ef6a-152">**file_name** — имя двоичного файла модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-152">**file_name** Name of module's binary file.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef6a-153">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0ef6a-153">Return values</span></span>

- <span data-ttu-id="0ef6a-154">**TX_SUCCESS** (0x00) — успешная загрузка модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-154">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="0ef6a-155">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-155">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="0ef6a-156">**TX_NOT_AVAILABLE** (0x1D) — диспетчер не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-156">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="0ef6a-157">**TX_NO_MEMORY** (0x10) — недостаточно памяти для загрузки модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-157">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="0ef6a-158">**TX_NOT_DONE** (0x20) — не удалось открыть носитель, файл не найден или недопустимый файл.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-158">**TX_NOT_DONE** (0x20) Media not open, file not found or file is invalid.</span></span>
- <span data-ttu-id="0ef6a-159">**TX_PTR_ERROR** (0x03) — недопустимый указатель на модуль.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-159">**TX_PTR_ERROR** (0x03) Invalid module pointer.</span></span>
- <span data-ttu-id="0ef6a-160">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) — недопустимое выравнивание.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-160">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="0ef6a-161">**TXM_MODULE_ALREADY_LOADED** (0xF1) — модуль уже загружен.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-161">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="0ef6a-162">**TXM_MODULE_INVALID** (0xF2) — недопустимая преамбула модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-162">**TXM_MODULE_INVALID** (0xF2) | Invalid module preamble.</span></span>
- <span data-ttu-id="0ef6a-163">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) — несовместимые свойства.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-163">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef6a-164">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0ef6a-164">Allowed from</span></span>

<span data-ttu-id="0ef6a-165">Потоки</span><span class="sxs-lookup"><span data-stu-id="0ef6a-165">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0ef6a-166">Пример</span><span class="sxs-lookup"><span data-stu-id="0ef6a-166">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager. */
status = txm_module_manager_initialize((VOID*)0x64010000,0x10000);

/* Load the module from a binary file. */
status = txm_module_manager_file_load(&my_module, "my module",
                                      &sdio_disk, "demo_thread_module.bin");

/* Start the module. */
status = txm_module_manager_start(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="0ef6a-167">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0ef6a-167">See also</span></span>

- <span data-ttu-id="0ef6a-168">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="0ef6a-168">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="0ef6a-169">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="0ef6a-169">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="0ef6a-170">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="0ef6a-170">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_in_place_load"></a><span data-ttu-id="0ef6a-171">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="0ef6a-171">txm_module_manager_in_place_load</span></span>

<span data-ttu-id="0ef6a-172">Загружать только данные модуля, выполнять модуль в существующем расположении.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-172">Load module data only, execute module in existing location.</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef6a-173">Прототип</span><span class="sxs-lookup"><span data-stu-id="0ef6a-173">Prototype</span></span>

```c
UINT txm_module_manager_in_place_load(
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a><span data-ttu-id="0ef6a-174">Описание</span><span class="sxs-lookup"><span data-stu-id="0ef6a-174">Description</span></span>

<span data-ttu-id="0ef6a-175">Эта служба загружает область данных модуля только в область памяти модуля и готовит ее к выполнению.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-175">This service loads the module's data area only into the module memory area and prepares it for execution.</span></span> <span data-ttu-id="0ef6a-176">Выполнение кода модуля будет выполняться на месте, то есть из смещения адреса, указанного в преамбуле модуля в указанном расположении.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-176">Module code execution will be in-place, that is, from the address offset specified by the module preamble at the supplied location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0ef6a-177">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0ef6a-177">Input parameters</span></span>

- <span data-ttu-id="0ef6a-178">**module_instance** — указатель на экземпляр модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-178">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="0ef6a-179">**module_name** — имя модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-179">**module_name** Name of the module.</span></span>
- <span data-ttu-id="0ef6a-180">**location** — указатель на область кода модуля, сначала преамбула.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-180">**location** Pointer to module's code area, preamble first.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef6a-181">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0ef6a-181">Return values</span></span>

- <span data-ttu-id="0ef6a-182">**TX_SUCCESS** (0x00) — успешная загрузка модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-182">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="0ef6a-183">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-183">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="0ef6a-184">**TX_NOT_AVAILABLE** (0x1D) — диспетчер не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-184">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="0ef6a-185">**TX_NO_MEMORY** (0x10) — недостаточно памяти для загрузки модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-185">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="0ef6a-186">**TX_PTR_ERROR** (0x03) — недопустимый указатель, экземпляр модуля или преамбула модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-186">**TX_PTR_ERROR** (0x03) Invalid pointer, module instance, or module preamble.</span></span>
- <span data-ttu-id="0ef6a-187">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) — недопустимое выравнивание.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-187">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="0ef6a-188">**TXM_MODULE_ALREADY_LOADED** (0xF1) — модуль уже загружен.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-188">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="0ef6a-189">**TXM_MODULE_INVALID** (0xF2) — недопустимая преамбула модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-189">**TXM_MODULE_INVALID** (0xF2) Invalid module preamble.</span></span>
- <span data-ttu-id="0ef6a-190">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) — несовместимые свойства.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-190">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef6a-191">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0ef6a-191">Allowed from</span></span>

<span data-ttu-id="0ef6a-192">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="0ef6a-192">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="0ef6a-193">Пример</span><span class="sxs-lookup"><span data-stu-id="0ef6a-193">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Start the module. */
txm_module_manager_start(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="0ef6a-194">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0ef6a-194">See also</span></span>

- <span data-ttu-id="0ef6a-195">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="0ef6a-195">txm_module_manager_file_load</span></span>
- <span data-ttu-id="0ef6a-196">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="0ef6a-196">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="0ef6a-197">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="0ef6a-197">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_initialize"></a><span data-ttu-id="0ef6a-198">txm_module_manager_initialize</span><span class="sxs-lookup"><span data-stu-id="0ef6a-198">txm_module_manager_initialize</span></span>

<span data-ttu-id="0ef6a-199">Инициализация диспетчера модулей.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-199">Initialize the module manager.</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef6a-200">Прототип</span><span class="sxs-lookup"><span data-stu-id="0ef6a-200">Prototype</span></span>

```c
UINT txm_module_manager_initialize(
    VOID *module_memory_start,
    ULONG module_memory_size);
```

### <a name="description"></a><span data-ttu-id="0ef6a-201">Описание</span><span class="sxs-lookup"><span data-stu-id="0ef6a-201">Description</span></span>

<span data-ttu-id="0ef6a-202">Эта служба инициализирует внутренние ресурсы диспетчера модулей, включая область памяти, используемую для загрузки модулей.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-202">This service initializes the Module Manager's internal resources, including the memory area used for loading modules.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0ef6a-203">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0ef6a-203">Input parameters</span></span>

- <span data-ttu-id="0ef6a-204">**module_memory_start** — указатель на начало памяти модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-204">**module_memory_start** Pointer to the start of module memory.</span></span>
- <span data-ttu-id="0ef6a-205">**module_memory_size** — размер памяти модуля в байтах.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-205">**module_memory_size** Size in bytes of the module memory.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef6a-206">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0ef6a-206">Return values</span></span>

- <span data-ttu-id="0ef6a-207">**TX_SUCCESS** (0x00) — успешная инициализация.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-207">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="0ef6a-208">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-208">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef6a-209">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0ef6a-209">Allowed from</span></span>

<span data-ttu-id="0ef6a-210">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="0ef6a-210">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="0ef6a-211">Пример</span><span class="sxs-lookup"><span data-stu-id="0ef6a-211">Example</span></span>

```c
/* Initialize the module manager with 64KB of RAM starting at
   address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);
```

### <a name="see-also"></a><span data-ttu-id="0ef6a-212">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0ef6a-212">See also</span></span>

- <span data-ttu-id="0ef6a-213">txm_module_manager_object_pool_create</span><span class="sxs-lookup"><span data-stu-id="0ef6a-213">txm_module_manager_object_pool_create</span></span>

---

## <a name="txm_module_manager_initialize_mmu"></a><span data-ttu-id="0ef6a-214">txm_module_manager_initialize_mmu</span><span class="sxs-lookup"><span data-stu-id="0ef6a-214">txm_module_manager_initialize_mmu</span></span>

<span data-ttu-id="0ef6a-215">Инициализация оборудования для управления памятью.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-215">Initialize the memory management hardware.</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef6a-216">Прототип</span><span class="sxs-lookup"><span data-stu-id="0ef6a-216">Prototype</span></span>

```c
UINT txm_module_manager_initialize_mmu(VOID);
```

### <a name="description"></a><span data-ttu-id="0ef6a-217">Описание</span><span class="sxs-lookup"><span data-stu-id="0ef6a-217">Description</span></span>

<span data-ttu-id="0ef6a-218">Эта служба инициализирует MMU.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-218">This service initializes the MMU.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0ef6a-219">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0ef6a-219">Input parameters</span></span>

<span data-ttu-id="0ef6a-220">нет</span><span class="sxs-lookup"><span data-stu-id="0ef6a-220">none</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef6a-221">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0ef6a-221">Return values</span></span>

- <span data-ttu-id="0ef6a-222">**TX_SUCCESS** (0x00) — успешная инициализация.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-222">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="0ef6a-223">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-223">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef6a-224">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0ef6a-224">Allowed from</span></span>

<span data-ttu-id="0ef6a-225">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="0ef6a-225">Initialization and Threads</span></span>

### <a name="example"></a><span data-ttu-id="0ef6a-226">Например, .</span><span class="sxs-lookup"><span data-stu-id="0ef6a-226">Example</span></span>

```c
/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Initialize the MMU. */
txm_module_manager_initialize_mmu();
```

---

## <a name="txm_module_manager_maximum_module_priority_set"></a><span data-ttu-id="0ef6a-227">txm_module_manager_maximum_module_priority_set</span><span class="sxs-lookup"><span data-stu-id="0ef6a-227">txm_module_manager_maximum_module_priority_set</span></span>

<span data-ttu-id="0ef6a-228">Установка максимального приоритета потока, разрешенного в модуле.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-228">Set the maximum thread priority allowed in a module.</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef6a-229">Прототип</span><span class="sxs-lookup"><span data-stu-id="0ef6a-229">Prototype</span></span>

```c
UINT txm_module_manager_maximum_module_priority_set(
         TXM_MODULE_INSTANCE *module_instance,
         UINT priority);
```

### <a name="description"></a><span data-ttu-id="0ef6a-230">Описание</span><span class="sxs-lookup"><span data-stu-id="0ef6a-230">Description</span></span>

<span data-ttu-id="0ef6a-231">Эта служба устанавливает максимальный приоритет потока, разрешенный в модуле.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-231">This service sets the maximum thread priority allowed in a module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0ef6a-232">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0ef6a-232">Input parameters</span></span>

- <span data-ttu-id="0ef6a-233">**module_instance** — указатель на экземпляр модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-233">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="0ef6a-234">**priority** — максимальный приоритет потока.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-234">**priority** Maximum thread priority.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef6a-235">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0ef6a-235">Return values</span></span>

- <span data-ttu-id="0ef6a-236">**TX_SUCCESS** (0x00) — успешная инициализация.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-236">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="0ef6a-237">**TX_NOT_AVAILABLE** (0x1D) — диспетчер не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-237">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="0ef6a-238">**TX_PTR_ERROR** (0x03) — недопустимый экземпляр модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-238">**TX_PTR_ERROR** (0x03) Invalid module instance.</span></span>
- <span data-ttu-id="0ef6a-239">**TX_START_ERROR** (0x10) — модуль не находится в загруженном состоянии.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-239">**TX_START_ERROR** (0x10) Module not in loaded state.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef6a-240">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0ef6a-240">Allowed from</span></span>

<span data-ttu-id="0ef6a-241">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="0ef6a-241">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="0ef6a-242">Например, .</span><span class="sxs-lookup"><span data-stu-id="0ef6a-242">Example</span></span>

```c
/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Set the maximum thread priority in my_module to 5. */
txm_module_manager_maximum_module_priority_set(&my_module, 5);
```

---

## <a name="txm_module_manager_memory_fault_notify"></a><span data-ttu-id="0ef6a-243">txm_module_manager_memory_fault_notify</span><span class="sxs-lookup"><span data-stu-id="0ef6a-243">txm_module_manager_memory_fault_notify</span></span>

<span data-ttu-id="0ef6a-244">Регистрация обратного вызова приложения при сбое памяти.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-244">Register an application callback on memory fault.</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef6a-245">Прототип</span><span class="sxs-lookup"><span data-stu-id="0ef6a-245">Prototype</span></span>

```c
UINT txm_module_manager_memory_fault_notify(
     VOID (*notify_function)(TX_THREAD *, MODULE_INSTANCE *));
```

### <a name="description"></a><span data-ttu-id="0ef6a-246">Описание</span><span class="sxs-lookup"><span data-stu-id="0ef6a-246">Description</span></span>

<span data-ttu-id="0ef6a-247">Эта служба регистрирует указанную функцию обратного вызова уведомления о сбое в памяти приложения в диспетчере модулей.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-247">This service registers the specified application memory fault notification callback function with the Module Manager.</span></span> <span data-ttu-id="0ef6a-248">В случае сбоя памяти эта функция вызывается с указателем на вызывающий ошибку поток и экземпляр модуля, соответствующий вызывающему ошибку потоку.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-248">If a memory fault occurs, this function is called with a pointer to the offending thread and the module instance corresponding to the offending thread.</span></span> <span data-ttu-id="0ef6a-249">Обработка диспетчера модулей автоматически завершает вызывающий ошибку поток, но оставляет все остальные потоки в модуле нетронутыми.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-249">The Module Manager processing automatically terminates the offending thread, but leaves any other threads in the module untouched.</span></span> <span data-ttu-id="0ef6a-250">Приложение может решить, что делать с модулем, связанным с ошибкой памяти.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-250">It is up to the application to decide what to do with the module associated with the memory fault.</span></span>

<span data-ttu-id="0ef6a-251">Дополнительные сведения об ошибках в памяти см. во внутренней структуре **_txm_module_manager_memory_fault_info**.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-251">Please see the internal **_txm_module_manager_memory_fault_info** struct for specific information on the memory fault itself.</span></span>

> [!NOTE]
> <span data-ttu-id="0ef6a-252">Функция обратного вызова для уведомления о сбое в памяти выполняется непосредственно из исключения ошибки памяти, поэтому можно вызывать только API-интерфейсы ThreadX, разрешенные из подпрограмм службы прерываний.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-252">The memory fault notification callback function is executed directly from the memory fault exception, so only ThreadX APIs Allowed from interrupt service routines can be called.</span></span> <span data-ttu-id="0ef6a-253">Таким образом, для остановки и выгрузки модуля, вызывающего ошибку, обратный вызов уведомления приложения должен отправить сигнал задаче приложения, чтобы модуль можно было остановить и выгрузить.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-253">Thus, in order to stop and unload the offending module, the application notification callback must send a signal to an application task so that the module can be stopped and unloaded.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0ef6a-254">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0ef6a-254">Input parameters</span></span>

- <span data-ttu-id="0ef6a-255">**notify_function** — указатель на функцию обратного вызова уведомления о сбое в памяти приложения.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-255">**notify_function** Function pointer to the application's memory fault notification callback.</span></span> <span data-ttu-id="0ef6a-256">При указании значения NULL уведомление о сбое в памяти отключается.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-256">Supplying a NULL value disables the memory fault notification.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef6a-257">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0ef6a-257">Return values</span></span>

- <span data-ttu-id="0ef6a-258">**TX_SUCCESS** (0x00) — успешная регистрация функции уведомления.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-258">**TX_SUCCESS** (0x00) Successful notification function registration.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef6a-259">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0ef6a-259">Allowed from</span></span>

<span data-ttu-id="0ef6a-260">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="0ef6a-260">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="0ef6a-261">Например, .</span><span class="sxs-lookup"><span data-stu-id="0ef6a-261">Example</span></span>

```c
/* Register a memory fault callback. */
txm_module_manager_memory_fault_notify(my_memory_fault_handler);
```

---

## <a name="txm_module_manager_memory_load"></a><span data-ttu-id="0ef6a-262">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="0ef6a-262">txm_module_manager_memory_load</span></span>

<span data-ttu-id="0ef6a-263">Загрузка модуля из памяти.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-263">Load module from memory.</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef6a-264">Прототип</span><span class="sxs-lookup"><span data-stu-id="0ef6a-264">Prototype</span></span>

```c
UINT txm_module_manager_memory_load (
    TXM_MODULE_INSTANCE *module_instance,
    CHAR *module_name,
    VOID *location);
```

### <a name="description"></a><span data-ttu-id="0ef6a-265">Описание</span><span class="sxs-lookup"><span data-stu-id="0ef6a-265">Description</span></span>

<span data-ttu-id="0ef6a-266">Эта служба загружает код модуля и область данных в область памяти модуля, настроенную с помощью ***txm_module_manager_initialize***, и готовит его к выполнению.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-266">This service loads the module's code and data area into the module memory area set up by ***txm_module_manager_initialize*** and prepares it for execution.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0ef6a-267">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0ef6a-267">Input parameters</span></span>

- <span data-ttu-id="0ef6a-268">**module_instance** — указатель на экземпляр модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-268">**module_instance** Pointer to the instance of the module.</span></span>
- <span data-ttu-id="0ef6a-269">**module_name** — имя модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-269">**module_name** Name of the module.</span></span>
- <span data-ttu-id="0ef6a-270">**location** — указатель на область кода модуля, сначала преамбула.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-270">**location** Pointer to module's code area, preamble first.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef6a-271">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0ef6a-271">Return values</span></span>

- <span data-ttu-id="0ef6a-272">**TX_SUCCESS** (0x00) — успешная загрузка модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-272">**TX_SUCCESS** (0x00) Successful module load.</span></span>
- <span data-ttu-id="0ef6a-273">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-273">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="0ef6a-274">**TX_NOT_AVAILABLE** (0x1D) — диспетчер не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-274">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="0ef6a-275">**TX_NO_MEMORY** (0x10) — недостаточно памяти для загрузки модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-275">**TX_NO_MEMORY** (0x10) Not enough memory to load module.</span></span>
- <span data-ttu-id="0ef6a-276">**TX_PTR_ERROR** (0x03) — недопустимый указатель, экземпляр модуля или преамбула модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-276">**TX_PTR_ERROR** (0x03) Invalid pointer, module instance, or module preamble.</span></span>
- <span data-ttu-id="0ef6a-277">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) — недопустимое выравнивание.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-277">**TXM_MODULE_ALIGNMENT_ERROR** (0xF0) Invalid alignment.</span></span>
- <span data-ttu-id="0ef6a-278">**TXM_MODULE_ALREADY_LOADED** (0xF1) — модуль уже загружен.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-278">**TXM_MODULE_ALREADY_LOADED** (0xF1) Module already loaded.</span></span>
- <span data-ttu-id="0ef6a-279">**TXM_MODULE_INVALID** (0xF2) — недопустимая преамбула модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-279">**TXM_MODULE_INVALID** (0xF2) Invalid module preamble.</span></span>
- <span data-ttu-id="0ef6a-280">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) — несовместимые свойства.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-280">**TXM_MODULE_INVALID_PROPERTIES** (0xF3) Incompatible properties.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef6a-281">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0ef6a-281">Allowed from</span></span>

<span data-ttu-id="0ef6a-282">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="0ef6a-282">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="0ef6a-283">Пример</span><span class="sxs-lookup"><span data-stu-id="0ef6a-283">Example</span></span>

```c
TXM_MODULE_INSTANCE     my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
 txm_module_manager_memory_load(&my_module, "my module", (VOID *) 0x080F0000);
```

### <a name="see-also"></a><span data-ttu-id="0ef6a-284">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0ef6a-284">See also</span></span>

- <span data-ttu-id="0ef6a-285">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="0ef6a-285">txm_module_manager_file_load</span></span>
- <span data-ttu-id="0ef6a-286">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="0ef6a-286">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="0ef6a-287">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="0ef6a-287">txm_module_manager_unload</span></span>

---

## <a name="txm_module_manager_object_pool_create"></a><span data-ttu-id="0ef6a-288">txm_module_manager_object_pool_create</span><span class="sxs-lookup"><span data-stu-id="0ef6a-288">txm_module_manager_object_pool_create</span></span>

<span data-ttu-id="0ef6a-289">Создание пула объектов для модулей.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-289">Create an object pool for modules.</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef6a-290">Прототип</span><span class="sxs-lookup"><span data-stu-id="0ef6a-290">Prototype</span></span>

```c
UINT txm_module_manager_object_pool_create(
    VOID *pool_memory_start,
    ULONG pool_memory_size);
```

### <a name="description"></a><span data-ttu-id="0ef6a-291">Описание</span><span class="sxs-lookup"><span data-stu-id="0ef6a-291">Description</span></span>

<span data-ttu-id="0ef6a-292">Эта служба создает пул памяти объектов диспетчера модулей, из которого модули могут распределять объекты ThreadX и NetX, тем самым оставляя системный объект вне области памяти модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-292">This service creates a Module Manager object memory pool that the modules can allocate ThreadX/NetX objects from, thereby keeping the system object out of the module's memory area.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0ef6a-293">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0ef6a-293">Input parameters</span></span>

- <span data-ttu-id="0ef6a-294">**pool_memory_start** — указатель на начало памяти объекта.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-294">**pool_memory_start** Pointer to the start of object memory.</span></span>
- <span data-ttu-id="0ef6a-295">**pool_memory_size** — размер пула памяти объектов в байтах.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-295">**pool_memory_size** Size in bytes of the object memory pool.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef6a-296">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0ef6a-296">Return values</span></span>

- <span data-ttu-id="0ef6a-297">**TX_SUCCESS** (0x00) — успешная инициализация.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-297">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="0ef6a-298">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-298">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef6a-299">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0ef6a-299">Allowed from</span></span>

<span data-ttu-id="0ef6a-300">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="0ef6a-300">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="0ef6a-301">Пример</span><span class="sxs-lookup"><span data-stu-id="0ef6a-301">Example</span></span>

```c
TXM_MODULE_INSTANCE my_module;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);
```

### <a name="see-also"></a><span data-ttu-id="0ef6a-302">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0ef6a-302">See also</span></span>

- <span data-ttu-id="0ef6a-303">txm_module_manager_initialize</span><span class="sxs-lookup"><span data-stu-id="0ef6a-303">txm_module_manager_initialize</span></span>

---

## <a name="txm_module_manager_properties_get"></a><span data-ttu-id="0ef6a-304">txm_module_manager_properties_get</span><span class="sxs-lookup"><span data-stu-id="0ef6a-304">txm_module_manager_properties_get</span></span>

<span data-ttu-id="0ef6a-305">Получение свойств модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-305">Get module properties.</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef6a-306">Прототип</span><span class="sxs-lookup"><span data-stu-id="0ef6a-306">Prototype</span></span>

```c
UINT txm_module_manager_properties_get(
    TXM_MODULE_INSTANCE *module_instance,
    ULONG *module_properties_ptr);
```

### <a name="description"></a><span data-ttu-id="0ef6a-307">Описание</span><span class="sxs-lookup"><span data-stu-id="0ef6a-307">Description</span></span>

<span data-ttu-id="0ef6a-308">Эта служба возвращает свойства модуля (указанные в преамбуле).</span><span class="sxs-lookup"><span data-stu-id="0ef6a-308">This service returns the properties (specified in the preamble) of a module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0ef6a-309">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0ef6a-309">Input parameters</span></span>

- <span data-ttu-id="0ef6a-310">**module_instance** — указатель на экземпляр модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-310">**module_instance** Pointer to the module instance.</span></span>
- <span data-ttu-id="0ef6a-311">**module_properties_ptr** — указатель на назначение для свойств модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-311">**module_properties_ptr** Pointer to destination for module's properties.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef6a-312">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0ef6a-312">Return values</span></span>

- <span data-ttu-id="0ef6a-313">**TX_SUCCESS** (0x00) — успешная инициализация.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-313">**TX_SUCCESS** (0x00) Successful initialization.</span></span>
- <span data-ttu-id="0ef6a-314">**TX_PTR_ERROR** (0x03) — недопустимый указатель.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-314">**TX_PTR_ERROR** (0x03) Invalid pointer.</span></span>
- <span data-ttu-id="0ef6a-315">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-315">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef6a-316">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0ef6a-316">Allowed from</span></span>

<span data-ttu-id="0ef6a-317">Потоки</span><span class="sxs-lookup"><span data-stu-id="0ef6a-317">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0ef6a-318">Например, .</span><span class="sxs-lookup"><span data-stu-id="0ef6a-318">Example</span></span>

```c
TXM_MODULE_INSTANCE     my_module;
ULONG                   module_properties;

/* Initialize the module manager with 64KB of RAM starting at address 0x64010000. */
txm_module_manager_initialize((VOID *) 0x64010000, 0x10000);

/* Create an object memory pool in the next 64KB of memory. */
txm_module_manager_object_pool_create((VOID *) 0x64020000, 0x10000);

/* Load the module that has its code area at address 0x080F0000. */
txm_module_manager_in_place_load(&my_module, "my module", (VOID *) 0x080F0000);

/* Get module properties. */
txm_module_manager_properties_get(&my_module, &module_properties);
```

---

## <a name="txm_module_manager_start"></a><span data-ttu-id="0ef6a-319">txm_module_manager_start</span><span class="sxs-lookup"><span data-stu-id="0ef6a-319">txm_module_manager_start</span></span>

<span data-ttu-id="0ef6a-320">Запуск выполнения модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-320">Start execution of the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef6a-321">Прототип</span><span class="sxs-lookup"><span data-stu-id="0ef6a-321">Prototype</span></span>

```c
UINT txm_module_manager_start(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="0ef6a-322">Описание</span><span class="sxs-lookup"><span data-stu-id="0ef6a-322">Description</span></span>

<span data-ttu-id="0ef6a-323">Эта служба запускает выполнение указанного и уже загруженного модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-323">This service starts execution of the specified, already loaded module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0ef6a-324">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0ef6a-324">Input parameters</span></span>

- <span data-ttu-id="0ef6a-325">**module_instance** — указатель на ранее загруженный экземпляр модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-325">**module_instance** Pointer to previously loaded module instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef6a-326">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0ef6a-326">Return values</span></span>

- <span data-ttu-id="0ef6a-327">**TX_SUCCESS** (0x00) — успешный запуск модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-327">**TX_SUCCESS** (0x00) Successful module start.</span></span>
- <span data-ttu-id="0ef6a-328">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-328">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="0ef6a-329">**TX_NOT_AVAILABLE** (0x1D) — диспетчер не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-329">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="0ef6a-330">**TX_PTR_ERROR** (0x03) — недопустимый указатель или экземпляр модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-330">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>
- <span data-ttu-id="0ef6a-331">**TX_START_ERROR** (0x10) — модуль уже запущен.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-331">**TX_START_ERROR** (0x10) Module already started.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef6a-332">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0ef6a-332">Allowed from</span></span>

<span data-ttu-id="0ef6a-333">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="0ef6a-333">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="0ef6a-334">Пример</span><span class="sxs-lookup"><span data-stu-id="0ef6a-334">Example</span></span>

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(2000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="0ef6a-335">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0ef6a-335">See also</span></span>

- <span data-ttu-id="0ef6a-336">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="0ef6a-336">txm_module_manager_stop</span></span>

---

## <a name="txm_module_manager_stop"></a><span data-ttu-id="0ef6a-337">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="0ef6a-337">txm_module_manager_stop</span></span>

<span data-ttu-id="0ef6a-338">Прерывание выполнения модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-338">Stop execution of the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef6a-339">Прототип</span><span class="sxs-lookup"><span data-stu-id="0ef6a-339">Prototype</span></span>

```c
UINT txm_module_manager_stop(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="0ef6a-340">Описание</span><span class="sxs-lookup"><span data-stu-id="0ef6a-340">Description</span></span>

<span data-ttu-id="0ef6a-341">Эта служба останавливает ранее загруженный и запущенный модуль.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-341">This service stops a module that was previously loaded and started.</span></span> <span data-ttu-id="0ef6a-342">Остановка модуля включает в себя выполнение необязательного потока остановки модуля, завершение всех потоков и удаление всех ресурсов, связанных с модулем.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-342">Stopping a module includes executing the module's optional stop thread, terminating all threads, and deleting all resources associated with the module.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0ef6a-343">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0ef6a-343">Input parameters</span></span>

- <span data-ttu-id="0ef6a-344">**module_instance** — указатель на экземпляр модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-344">**module_instance** Pointer to module instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef6a-345">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0ef6a-345">Return values</span></span>

- <span data-ttu-id="0ef6a-346">**TX_SUCCESS** (0x00) — успешная остановка модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-346">**TX_SUCCESS** (0x00) Successful module stop.</span></span>
- <span data-ttu-id="0ef6a-347">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-347">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="0ef6a-348">**TX_NOT_AVAILABLE** (0x1D) — диспетчер не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-348">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="0ef6a-349">**TX_PTR_ERROR** (0x03) — недопустимый указатель или экземпляр модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-349">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>
- <span data-ttu-id="0ef6a-350">**TX_START_ERROR** (0x10) — модуль на запущен.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-350">**TX_START_ERROR** (0x10) Module not started.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef6a-351">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0ef6a-351">Allowed from</span></span>

<span data-ttu-id="0ef6a-352">Потоки</span><span class="sxs-lookup"><span data-stu-id="0ef6a-352">Threads</span></span>

### <a name="example"></a><span data-ttu-id="0ef6a-353">Пример</span><span class="sxs-lookup"><span data-stu-id="0ef6a-353">Example</span></span>

```c
/* Start the module. */
txm_module_manager_start(&my_module);

/* Let the module run for a while. */
tx_thread_sleep(20000);

/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="0ef6a-354">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0ef6a-354">See also</span></span>

- <span data-ttu-id="0ef6a-355">txm_module_manager_start</span><span class="sxs-lookup"><span data-stu-id="0ef6a-355">txm_module_manager_start</span></span>

---

## <a name="txm_module_manager_unload"></a><span data-ttu-id="0ef6a-356">txm_module_manager_unload</span><span class="sxs-lookup"><span data-stu-id="0ef6a-356">txm_module_manager_unload</span></span>

<span data-ttu-id="0ef6a-357">Выгрузка модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-357">Unload the module.</span></span>

### <a name="prototype"></a><span data-ttu-id="0ef6a-358">Прототип</span><span class="sxs-lookup"><span data-stu-id="0ef6a-358">Prototype</span></span>

```c
UINT txm_module_manager_unload(TXM_MODULE_INSTANCE *module_instance);
```

### <a name="description"></a><span data-ttu-id="0ef6a-359">Описание</span><span class="sxs-lookup"><span data-stu-id="0ef6a-359">Description</span></span>

<span data-ttu-id="0ef6a-360">Эта служба выгружает ранее загруженный и остановленный модуль, освобождая все связанные ресурсы памяти модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-360">This service unloads the previously loaded and stopped module, freeing all the associated module memory resources.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="0ef6a-361">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="0ef6a-361">Input parameters</span></span>

- <span data-ttu-id="0ef6a-362">**module_instance** — указатель на экземпляр модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-362">**module_instance** Pointer to the instance of the module.</span></span>

### <a name="return-values"></a><span data-ttu-id="0ef6a-363">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="0ef6a-363">Return values</span></span>

- <span data-ttu-id="0ef6a-364">**TX_SUCCESS** (0x00) — успешная выгрузка модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-364">**TX_SUCCESS** 0x00) Successful module unload.</span></span>
- <span data-ttu-id="0ef6a-365">**TX_CALLER_ERROR** (0x13) — недопустимый вызывающий объект.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-365">**TX_CALLER_ERROR** (0x13) Invalid caller.</span></span>
- <span data-ttu-id="0ef6a-366">**TX_NOT_AVAILABLE** (0x1D) — диспетчер не инициализирован.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-366">**TX_NOT_AVAILABLE** (0x1D) Manager not initialized.</span></span>
- <span data-ttu-id="0ef6a-367">**TX_NOT_DONE** (0x20) — недопустимый модуль или модуль не остановлен.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-367">**TX_NOT_DONE** (0x20) Invalid module or module not stopped.</span></span>
- <span data-ttu-id="0ef6a-368">**TX_PTR_ERROR** (0x03) — недопустимый указатель или экземпляр модуля.</span><span class="sxs-lookup"><span data-stu-id="0ef6a-368">**TX_PTR_ERROR** (0x03) Invalid pointer or module instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="0ef6a-369">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="0ef6a-369">Allowed from</span></span>

<span data-ttu-id="0ef6a-370">Инициализация и потоки</span><span class="sxs-lookup"><span data-stu-id="0ef6a-370">Initialization and threads</span></span>

### <a name="example"></a><span data-ttu-id="0ef6a-371">Пример</span><span class="sxs-lookup"><span data-stu-id="0ef6a-371">Example</span></span>

```c
/* Stop the module. */
txm_module_manager_stop(&my_module);

/* Unload the module. */
status = txm_module_manager_unload(&my_module);
```

### <a name="see-also"></a><span data-ttu-id="0ef6a-372">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0ef6a-372">See also</span></span>

- <span data-ttu-id="0ef6a-373">txm_module_manager_file_load</span><span class="sxs-lookup"><span data-stu-id="0ef6a-373">txm_module_manager_file_load</span></span>
- <span data-ttu-id="0ef6a-374">txm_module_manager_in_place_load</span><span class="sxs-lookup"><span data-stu-id="0ef6a-374">txm_module_manager_in_place_load</span></span>
- <span data-ttu-id="0ef6a-375">txm_module_manager_memory_load</span><span class="sxs-lookup"><span data-stu-id="0ef6a-375">txm_module_manager_memory_load</span></span>
- <span data-ttu-id="0ef6a-376">txm_module_manager_stop</span><span class="sxs-lookup"><span data-stu-id="0ef6a-376">txm_module_manager_stop</span></span>
