---
title: Глава 6. API-интерфейсы NOR для LevelX для ОСРВ Azure
description: API-интерфейсы NOR для LevelX для ОСРВ Azure, доступные для приложения.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3ab7d3a7e431d7c8f49ef4f5cab9216dc77c8d33
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815420"
---
# <a name="chapter-6---azure-rtos-levelx-nor-apis"></a><span data-ttu-id="1569c-103">Глава 6. API-интерфейсы NOR для LevelX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="1569c-103">Chapter 6 - Azure RTOS LevelX NOR APIs</span></span>

<span data-ttu-id="1569c-104">Приложениям доступны следующие функции API NOR для LevelX для ОСРВ Azure:</span><span class="sxs-lookup"><span data-stu-id="1569c-104">The Azure RTOS LevelX NOR API functions available to the application are as follows.</span></span>

- <span data-ttu-id="1569c-105">***lx_nor_flash_close** _: _закрытие экземпляра флэш-памяти NOR*;</span><span class="sxs-lookup"><span data-stu-id="1569c-105">***lx_nor_flash_close** _: _Close NOR flash instance*</span></span>
- <span data-ttu-id="1569c-106">***lx_nor_flash_defragment** _: _дефрагментация экземпляра флэш-памяти NOR*;</span><span class="sxs-lookup"><span data-stu-id="1569c-106">***lx_nor_flash_defragment** _: _Defragment NOR flash instance*</span></span>
- <span data-ttu-id="1569c-107">***lx_nor_flash_extended_cache_enable** _: _включение и выключение расширенного кэша NOR*;</span><span class="sxs-lookup"><span data-stu-id="1569c-107">***lx_nor_flash_extended_cache_enable** _: _Enable/disable extended NOR cache*</span></span>
- <span data-ttu-id="1569c-108">***lx_nor_flash_initialize** _: _инициализация поддержки флэш-памяти NOR*;</span><span class="sxs-lookup"><span data-stu-id="1569c-108">***lx_nor_flash_initialize** _: _Initialize NOR flash support*</span></span>
- <span data-ttu-id="1569c-109">***lx_nor_flash_open** _: _открытие экземпляра флэш-памяти NOR*;</span><span class="sxs-lookup"><span data-stu-id="1569c-109">***lx_nor_flash_open** _: _Open NOR flash instance*</span></span>
- <span data-ttu-id="1569c-110">***lx_nor_flash_partial_defragment** _: _частичная дефрагментация экземпляра флэш-памяти NOR*;</span><span class="sxs-lookup"><span data-stu-id="1569c-110">***lx_nor_flash_partial_defragment** _: _Partial defragment of NOR flash instance*</span></span>
- <span data-ttu-id="1569c-111">***lx_nor_flash_sector_read** _: _чтение сектора флэш-памяти NOR*;</span><span class="sxs-lookup"><span data-stu-id="1569c-111">***lx_nor_flash_sector_read** _: _Read NOR flash sector*</span></span>
- <span data-ttu-id="1569c-112">***lx_nor_flash_sector_release** _: _освобождение сектора флэш-памяти NOR*;</span><span class="sxs-lookup"><span data-stu-id="1569c-112">***lx_nor_flash_sector_release** _: _Release NOR flash sector*</span></span>
- <span data-ttu-id="1569c-113">***lx_nor_flash_sector_write** _: _запись сектора флэш-памяти NOR*.</span><span class="sxs-lookup"><span data-stu-id="1569c-113">***lx_nor_flash_sector_write** _: _Write NOR flash sector*</span></span>

## <a name="lx_nor_flash_close"></a><span data-ttu-id="1569c-114">lx_nor_flash_close</span><span class="sxs-lookup"><span data-stu-id="1569c-114">lx_nor_flash_close</span></span>

<span data-ttu-id="1569c-115">Закрытие экземпляра флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-115">Close NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="1569c-116">Прототип</span><span class="sxs-lookup"><span data-stu-id="1569c-116">Prototype</span></span>

```c
UINT lx_nor_flash_close(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a><span data-ttu-id="1569c-117">Описание</span><span class="sxs-lookup"><span data-stu-id="1569c-117">Description</span></span>

<span data-ttu-id="1569c-118">Эта служба закрывает ранее открытый экземпляр флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-118">This service closes the previously opened NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1569c-119">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="1569c-119">Input Parameters</span></span>

- <span data-ttu-id="1569c-120">*nor_flash*: указатель на экземпляр флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-120">*nor_flash*: NOR flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="1569c-121">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1569c-121">Return Values</span></span>

- <span data-ttu-id="1569c-122">**TX_SUCCESS** (0x00): запрос успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="1569c-122">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="1569c-123">**LX_ERROR** (0x01): ошибка закрытия экземпляра флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="1569c-123">**LX_ERROR**: (0x01) Error closing flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1569c-124">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1569c-124">Allowed From</span></span>

<span data-ttu-id="1569c-125">Потоки</span><span class="sxs-lookup"><span data-stu-id="1569c-125">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1569c-126">Пример</span><span class="sxs-lookup"><span data-stu-id="1569c-126">Example</span></span>

```c
/* Close NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_close(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="1569c-127">См. также:</span><span class="sxs-lookup"><span data-stu-id="1569c-127">See Also</span></span>

- <span data-ttu-id="1569c-128">lx_nor_flash_defragment;</span><span class="sxs-lookup"><span data-stu-id="1569c-128">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="1569c-129">lx_nor_flash_extended_cache_enable;</span><span class="sxs-lookup"><span data-stu-id="1569c-129">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="1569c-130">lx_nor_flash_initialize;</span><span class="sxs-lookup"><span data-stu-id="1569c-130">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="1569c-131">lx_nor_flash_open;</span><span class="sxs-lookup"><span data-stu-id="1569c-131">lx_nor_flash_open</span></span>
- <span data-ttu-id="1569c-132">lx_nor_flash_partial_defragment;</span><span class="sxs-lookup"><span data-stu-id="1569c-132">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="1569c-133">lx_nor_flash_sector_read;</span><span class="sxs-lookup"><span data-stu-id="1569c-133">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="1569c-134">lx_nor_flash_sector_release;</span><span class="sxs-lookup"><span data-stu-id="1569c-134">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="1569c-135">lx_nor_flash_sector_write.</span><span class="sxs-lookup"><span data-stu-id="1569c-135">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_defragment"></a><span data-ttu-id="1569c-136">lx_nor_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="1569c-136">lx_nor_flash_defragment</span></span>

<span data-ttu-id="1569c-137">Дефрагментация экземпляра флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-137">Defragment NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="1569c-138">Прототип</span><span class="sxs-lookup"><span data-stu-id="1569c-138">Prototype</span></span>

```c
UINT lx_nor_flash_defragment(LX_NOR_FLASH *nor_flash);
```

### <a name="description"></a><span data-ttu-id="1569c-139">Описание</span><span class="sxs-lookup"><span data-stu-id="1569c-139">Description</span></span>

<span data-ttu-id="1569c-140">Эта служба дефрагментирует ранее открытый экземпляр флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-140">This service defragments the previously opened NOR flash instance.</span></span> <span data-ttu-id="1569c-141">Процесс дефрагментации позволяет максимально увеличить количество свободных секторов и блоков.</span><span class="sxs-lookup"><span data-stu-id="1569c-141">The defragment process maximizes the number of free sectors and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1569c-142">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="1569c-142">Input Parameters</span></span>

- <span data-ttu-id="1569c-143">*nor_flash*: указатель на экземпляр флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-143">*nor_flash*: NOR flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="1569c-144">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1569c-144">Return Values</span></span>

- <span data-ttu-id="1569c-145">**TX_SUCCESS** (0x00): запрос успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="1569c-145">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="1569c-146">**LX_ERROR** (0x01): ошибка дефрагментации экземпляра флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="1569c-146">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1569c-147">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1569c-147">Allowed From</span></span>

<span data-ttu-id="1569c-148">Потоки</span><span class="sxs-lookup"><span data-stu-id="1569c-148">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1569c-149">Пример</span><span class="sxs-lookup"><span data-stu-id="1569c-149">Example</span></span>

```c
/* Defragment NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_defragment(&my_nor_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="1569c-150">См. также:</span><span class="sxs-lookup"><span data-stu-id="1569c-150">See Also</span></span>

- <span data-ttu-id="1569c-151">lx_nor_flash_close;</span><span class="sxs-lookup"><span data-stu-id="1569c-151">lx_nor_flash_close</span></span>
- <span data-ttu-id="1569c-152">lx_nor_flash_extended_cache_enable;</span><span class="sxs-lookup"><span data-stu-id="1569c-152">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="1569c-153">lx_nor_flash_initialize;</span><span class="sxs-lookup"><span data-stu-id="1569c-153">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="1569c-154">lx_nor_flash_open;</span><span class="sxs-lookup"><span data-stu-id="1569c-154">lx_nor_flash_open</span></span>
- <span data-ttu-id="1569c-155">lx_nor_flash_partial_defragment;</span><span class="sxs-lookup"><span data-stu-id="1569c-155">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="1569c-156">lx_nor_flash_sector_read;</span><span class="sxs-lookup"><span data-stu-id="1569c-156">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="1569c-157">lx_nor_flash_sector_release;</span><span class="sxs-lookup"><span data-stu-id="1569c-157">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="1569c-158">lx_nor_flash_sector_write.</span><span class="sxs-lookup"><span data-stu-id="1569c-158">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_extended_cache_enable"></a><span data-ttu-id="1569c-159">lx_nor_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="1569c-159">lx_nor_flash_extended_cache_enable</span></span>

<span data-ttu-id="1569c-160">Включение и выключение расширенного кэша NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-160">Enable/disable extended NOR cache</span></span>

### <a name="prototype"></a><span data-ttu-id="1569c-161">Прототип</span><span class="sxs-lookup"><span data-stu-id="1569c-161">Prototype</span></span>

```c
UINT lx_nor_flash_extended_cache_enable(
    LX_NOR_FLASH *nor_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="1569c-162">Описание</span><span class="sxs-lookup"><span data-stu-id="1569c-162">Description</span></span>

<span data-ttu-id="1569c-163">Эта служба реализует в ОЗУ уровень кэша секторов NOR, используя предоставленную приложением память.</span><span class="sxs-lookup"><span data-stu-id="1569c-163">This service implements a NOR sector cache layer in RAM using the memory supplied by the application.</span></span> <span data-ttu-id="1569c-164">Каждые 512 байт предоставленной памяти преобразуются в пространство кэша для одного сектора NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-164">Each 512 bytes of memory supplied translates to one NOR sector that can be cached.</span></span> <span data-ttu-id="1569c-165">Кэшируются секторы, которые содержат сведения об управлении блоками: число удалений, карта свободных секторов, сведения о сопоставлении секторов.</span><span class="sxs-lookup"><span data-stu-id="1569c-165">The sectors cached are those that contain the block control information, e.g., erase count, free sector map, and sector mapping information.</span></span> <span data-ttu-id="1569c-166">Секторы данных в этом кэше не хранятся.</span><span class="sxs-lookup"><span data-stu-id="1569c-166">Data sectors are not stored in this cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1569c-167">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="1569c-167">Input Parameters</span></span>

- <span data-ttu-id="1569c-168">**nor_flash**: указатель на экземпляр флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-168">**nor_flash**: NOR flash instance pointer.</span></span>  
- <span data-ttu-id="1569c-169">**memory**: начальный адрес памяти для кэша с округлением для адресации в формате ULONG.</span><span class="sxs-lookup"><span data-stu-id="1569c-169">**memory**: Starting address for cache memory, aligned for ULONG access.</span></span> <span data-ttu-id="1569c-170">Значение LX_NULL позволяет отключить кэш.</span><span class="sxs-lookup"><span data-stu-id="1569c-170">A value of LX_NULL disables the cache.</span></span>  
- <span data-ttu-id="1569c-171">**size**: размер предоставленной памяти в байтах (должен быть кратным 512 байтам).</span><span class="sxs-lookup"><span data-stu-id="1569c-171">**size**: The size in bytes of the memory supplied (should be multiple of 512 bytes).</span></span>

### <a name="return-values"></a><span data-ttu-id="1569c-172">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1569c-172">Return Values</span></span>

- <span data-ttu-id="1569c-173">**TX_SUCCESS** (0x00): запрос успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="1569c-173">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="1569c-174">**LX_ERROR** (0x01): недостаточно памяти для одного сектора NOR</span><span class="sxs-lookup"><span data-stu-id="1569c-174">**LX_ERROR**: (0x01) Not enough memory for one NOR sector.</span></span>
- <span data-ttu-id="1569c-175">**LX_DISABLED** (0x09): расширенный кэш NOR отключен параметром конфигурации</span><span class="sxs-lookup"><span data-stu-id="1569c-175">**LX_DISABLED**: (0x09) NOR extended cache disabled by configuration option.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1569c-176">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1569c-176">Allowed From</span></span>

<span data-ttu-id="1569c-177">Потоки</span><span class="sxs-lookup"><span data-stu-id="1569c-177">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1569c-178">Пример</span><span class="sxs-lookup"><span data-stu-id="1569c-178">Example</span></span>

```c
/* Enable the NOR flash cache for the instance "my_nor_flash". */  
status = lx_nor_flash_extended_cache_enable(&my_nor_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="1569c-179">См. также:</span><span class="sxs-lookup"><span data-stu-id="1569c-179">See Also</span></span>

- <span data-ttu-id="1569c-180">lx_nor_flash_close;</span><span class="sxs-lookup"><span data-stu-id="1569c-180">lx_nor_flash_close</span></span>
- <span data-ttu-id="1569c-181">lx_nor_flash_defragment;</span><span class="sxs-lookup"><span data-stu-id="1569c-181">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="1569c-182">lx_nor_flash_initialize;</span><span class="sxs-lookup"><span data-stu-id="1569c-182">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="1569c-183">lx_nor_flash_open;</span><span class="sxs-lookup"><span data-stu-id="1569c-183">lx_nor_flash_open</span></span>
- <span data-ttu-id="1569c-184">lx_nor_flash_partial_defragment;</span><span class="sxs-lookup"><span data-stu-id="1569c-184">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="1569c-185">lx_nor_flash_sector_read;</span><span class="sxs-lookup"><span data-stu-id="1569c-185">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="1569c-186">lx_nor_flash_sector_release;</span><span class="sxs-lookup"><span data-stu-id="1569c-186">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="1569c-187">lx_nor_flash_sector_write.</span><span class="sxs-lookup"><span data-stu-id="1569c-187">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_initialize"></a><span data-ttu-id="1569c-188">lx_nor_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="1569c-188">lx_nor_flash_initialize</span></span>

<span data-ttu-id="1569c-189">Инициализация поддержки флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-189">Initialize NOR flash support</span></span>

### <a name="prototype"></a><span data-ttu-id="1569c-190">Прототип</span><span class="sxs-lookup"><span data-stu-id="1569c-190">Prototype</span></span>

```c
UINT lx_nor_flash_initialize(void);
```

### <a name="description"></a><span data-ttu-id="1569c-191">Описание</span><span class="sxs-lookup"><span data-stu-id="1569c-191">Description</span></span>

<span data-ttu-id="1569c-192">Эта служба инициализирует поддержку флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-192">This service initializes LevelX NOR flash support.</span></span> <span data-ttu-id="1569c-193">Ее необходимо вызывать раньше любых других API-интерфейсов NOR для LevelX.</span><span class="sxs-lookup"><span data-stu-id="1569c-193">It must be called before any other LevelX NOR APIs.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1569c-194">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="1569c-194">Input Parameters</span></span>

- <span data-ttu-id="1569c-195">**Нет**</span><span class="sxs-lookup"><span data-stu-id="1569c-195">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="1569c-196">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1569c-196">Return Values</span></span>

- <span data-ttu-id="1569c-197">**TX_SUCCESS** (0x00): запрос успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="1569c-197">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="1569c-198">**LX_ERROR** (0x01): ошибка инициализации поддержки флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-198">**LX_ERROR**: (0x01) Error initializing NOR flash support.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1569c-199">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1569c-199">Allowed From</span></span>

<span data-ttu-id="1569c-200">Инициализация, потоки.</span><span class="sxs-lookup"><span data-stu-id="1569c-200">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="1569c-201">Пример</span><span class="sxs-lookup"><span data-stu-id="1569c-201">Example</span></span>

```c
/* Initialize NOR flash support. */  
status = lx_nor_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="1569c-202">См. также:</span><span class="sxs-lookup"><span data-stu-id="1569c-202">See Also</span></span>

- <span data-ttu-id="1569c-203">lx_nor_flash_close;</span><span class="sxs-lookup"><span data-stu-id="1569c-203">lx_nor_flash_close</span></span>
- <span data-ttu-id="1569c-204">lx_nor_flash_defragment;</span><span class="sxs-lookup"><span data-stu-id="1569c-204">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="1569c-205">lx_nor_flash_extended_cache_enable;</span><span class="sxs-lookup"><span data-stu-id="1569c-205">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="1569c-206">lx_nor_flash_partial_defragment;</span><span class="sxs-lookup"><span data-stu-id="1569c-206">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="1569c-207">lx_nor_flash_open;</span><span class="sxs-lookup"><span data-stu-id="1569c-207">lx_nor_flash_open</span></span>
- <span data-ttu-id="1569c-208">lx_nor_flash_sector_read;</span><span class="sxs-lookup"><span data-stu-id="1569c-208">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="1569c-209">lx_nor_flash_sector_release;</span><span class="sxs-lookup"><span data-stu-id="1569c-209">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="1569c-210">lx_nor_flash_sector_write.</span><span class="sxs-lookup"><span data-stu-id="1569c-210">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_open"></a><span data-ttu-id="1569c-211">lx_nor_flash_open</span><span class="sxs-lookup"><span data-stu-id="1569c-211">lx_nor_flash_open</span></span>

<span data-ttu-id="1569c-212">Открытие экземпляра флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-212">Open NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="1569c-213">Прототип</span><span class="sxs-lookup"><span data-stu-id="1569c-213">Prototype</span></span>

```c
UINT lx_nor_flash_open(
    LX_NOR_FLASH *nor_flash, 
    CHAR *name,  
    UINT (*nor_driver_initialize) (LX_NOR_FLASH *));
```

### <a name="description"></a><span data-ttu-id="1569c-214">Описание</span><span class="sxs-lookup"><span data-stu-id="1569c-214">Description</span></span>

<span data-ttu-id="1569c-215">Эта служба открывает экземпляр флэш-памяти NOR с использованием предоставленного блока управления флэш-памятью NOR и функции инициализации драйвера.</span><span class="sxs-lookup"><span data-stu-id="1569c-215">This service opens a NOR flash instance with the specified NOR flash control block and driver initialization function.</span></span> <span data-ttu-id="1569c-216">Обратите внимание, что функция инициализации драйвера отвечает за установку указателей на функции чтения, записи и стирания блоков в оборудовании NOR, сопоставленным с этим экземпляром флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-216">Note that the driver initialization function is responsible for installing various function pointers for reading, writing, and erasing blocks of the NOR hardware associated with this NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1569c-217">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="1569c-217">Input Parameters</span></span>

- <span data-ttu-id="1569c-218">*nor_flash*: указатель на экземпляр флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-218">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="1569c-219">*name*: имя экземпляра флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-219">*name*: Name of NOR flash instance.</span></span>
- <span data-ttu-id="1569c-220">*nor_driver_initialize*: указатель на функцию для инициализации драйвера флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-220">*nor_driver_initialize*: Function pointer to NOR flash driver Initialization function.</span></span> <span data-ttu-id="1569c-221">Дополнительные сведения о функциях, которые должен реализовать драйвер флэш-памяти NOR, см. в главе 5 этого руководства.</span><span class="sxs-lookup"><span data-stu-id="1569c-221">Please refer to Chapter 5 of this guide for more details on NOR flash driver responsibilities.</span></span>

### <a name="return-values"></a><span data-ttu-id="1569c-222">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1569c-222">Return Values</span></span>

- <span data-ttu-id="1569c-223">**TX_SUCCESS** (0x00): запрос успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="1569c-223">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="1569c-224">**LX_ERROR** (0x01): ошибка открытия экземпляра флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-224">**LX_ERROR**: (0x01) Error opening NOR flash instance.</span></span>
- <span data-ttu-id="1569c-225">**LX_NO_MEMORY** (0x08): драйвер не предоставил буфера для считывания сектора NOR в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="1569c-225">**LX_NO_MEMORY**:  (0x08) Driver did not provide buffer for reading none sector into RAM.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1569c-226">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1569c-226">Allowed From</span></span>

<span data-ttu-id="1569c-227">Потоки</span><span class="sxs-lookup"><span data-stu-id="1569c-227">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1569c-228">Пример</span><span class="sxs-lookup"><span data-stu-id="1569c-228">Example</span></span>

```c
/* Open NOR flash instance "my_nor_flash" with the driver "my_nor_driver_initialize". */  
status = lx_nor_flash_open(&my_nor_flash,"my NOR flash",  
    my_nor_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="1569c-229">См. также:</span><span class="sxs-lookup"><span data-stu-id="1569c-229">See Also</span></span>

- <span data-ttu-id="1569c-230">lx_nor_flash_close;</span><span class="sxs-lookup"><span data-stu-id="1569c-230">lx_nor_flash_close</span></span>
- <span data-ttu-id="1569c-231">lx_nor_flash_defragment;</span><span class="sxs-lookup"><span data-stu-id="1569c-231">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="1569c-232">lx_nor_flash_extended_cache_enable;</span><span class="sxs-lookup"><span data-stu-id="1569c-232">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="1569c-233">lx_nor_flash_initialize;</span><span class="sxs-lookup"><span data-stu-id="1569c-233">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="1569c-234">lx_nor_flash_partial_defragment;</span><span class="sxs-lookup"><span data-stu-id="1569c-234">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="1569c-235">lx_nor_flash_sector_read;</span><span class="sxs-lookup"><span data-stu-id="1569c-235">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="1569c-236">lx_nor_flash_sector_release;</span><span class="sxs-lookup"><span data-stu-id="1569c-236">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="1569c-237">lx_nor_flash_sector_write.</span><span class="sxs-lookup"><span data-stu-id="1569c-237">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_partial_defragment"></a><span data-ttu-id="1569c-238">lx_nor_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="1569c-238">lx_nor_flash_partial_defragment</span></span>

<span data-ttu-id="1569c-239">Частичная дефрагментация экземпляра флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-239">Partial defragment of NOR flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="1569c-240">Прототип</span><span class="sxs-lookup"><span data-stu-id="1569c-240">Prototype</span></span>

```c
UINT lx_nor_flash_partial_defragment(
    LX_NOR_FLASH *nor_flash, 
    UINT max_blocks);
```

### <a name="description"></a><span data-ttu-id="1569c-241">Описание</span><span class="sxs-lookup"><span data-stu-id="1569c-241">Description</span></span>

<span data-ttu-id="1569c-242">Эта служба выполняет дефрагментацию ранее открытого экземпляра флэш-памяти NOR вплоть до максимального указанного числа блоков.</span><span class="sxs-lookup"><span data-stu-id="1569c-242">This service defragments the previously opened NOR flash instance up to the maximum number of blocks specified.</span></span> <span data-ttu-id="1569c-243">Процесс дефрагментации позволяет максимально увеличить количество свободных секторов и блоков.</span><span class="sxs-lookup"><span data-stu-id="1569c-243">The defragment process maximizes the number of free sectors and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1569c-244">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="1569c-244">Input Parameters</span></span>

- <span data-ttu-id="1569c-245">*nor_flash*: указатель на экземпляр флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-245">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="1569c-246">*max_blocks*: максимальное количество блоков.</span><span class="sxs-lookup"><span data-stu-id="1569c-246">*max_blocks*: Maximum number of blocks.</span></span>

### <a name="return-values"></a><span data-ttu-id="1569c-247">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1569c-247">Return Values</span></span>

- <span data-ttu-id="1569c-248">**TX_SUCCESS** (0x00): запрос успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="1569c-248">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="1569c-249">**LX_ERROR** (0x01): ошибка дефрагментации экземпляра флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="1569c-249">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1569c-250">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1569c-250">Allowed From</span></span>

<span data-ttu-id="1569c-251">Потоки</span><span class="sxs-lookup"><span data-stu-id="1569c-251">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1569c-252">Пример</span><span class="sxs-lookup"><span data-stu-id="1569c-252">Example</span></span>

```c
/* Defragment of one block in NOR flash instance* *"my_nor_flash". */  
status = lx_nor_flash_partial_defragment(&my_nor_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="1569c-253">См. также:</span><span class="sxs-lookup"><span data-stu-id="1569c-253">See Also</span></span>

- <span data-ttu-id="1569c-254">lx_nor_flash_close;</span><span class="sxs-lookup"><span data-stu-id="1569c-254">lx_nor_flash_close</span></span>
- <span data-ttu-id="1569c-255">lx_nor_flash_defragment;</span><span class="sxs-lookup"><span data-stu-id="1569c-255">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="1569c-256">lx_nor_flash_extended_cache_enable;</span><span class="sxs-lookup"><span data-stu-id="1569c-256">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="1569c-257">lx_nor_flash_initialize;</span><span class="sxs-lookup"><span data-stu-id="1569c-257">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="1569c-258">lx_nor_flash_open;</span><span class="sxs-lookup"><span data-stu-id="1569c-258">lx_nor_flash_open</span></span>
- <span data-ttu-id="1569c-259">lx_nor_flash_sector_read;</span><span class="sxs-lookup"><span data-stu-id="1569c-259">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="1569c-260">lx_nor_flash_sector_release;</span><span class="sxs-lookup"><span data-stu-id="1569c-260">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="1569c-261">lx_nor_flash_sector_write.</span><span class="sxs-lookup"><span data-stu-id="1569c-261">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_read"></a><span data-ttu-id="1569c-262">lx_nor_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="1569c-262">lx_nor_flash_sector_read</span></span>

<span data-ttu-id="1569c-263">Чтение сектора флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-263">Read NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="1569c-264">Прототип</span><span class="sxs-lookup"><span data-stu-id="1569c-264">Prototype</span></span>

```c
UINT lx_nor_flash_sector_read(
    LX_NOR_FLASH *nor_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="1569c-265">Описание</span><span class="sxs-lookup"><span data-stu-id="1569c-265">Description</span></span>

<span data-ttu-id="1569c-266">Эта служба считывает логический сектор из экземпляра флэш-памяти NOR, а при успешном выполнении возвращает содержимое в предоставленном буфере.</span><span class="sxs-lookup"><span data-stu-id="1569c-266">This service reads the logical sector from the NOR flash instance and if successful returns the contents in the supplied buffer.</span></span> <span data-ttu-id="1569c-267">Обратите внимание, что размер сектора NOR не всегда составляет 512 байт.</span><span class="sxs-lookup"><span data-stu-id="1569c-267">Note that NOR sector size is always 512 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1569c-268">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="1569c-268">Input Parameters</span></span>

- <span data-ttu-id="1569c-269">*nor_flash*: указатель на экземпляр флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-269">*nor_flash* NOR flash instance pointer.</span></span>
- <span data-ttu-id="1569c-270">*logical_sector*: логический сектор для считывания.</span><span class="sxs-lookup"><span data-stu-id="1569c-270">*logical_sector*: Logical sector to read.</span></span>
- <span data-ttu-id="1569c-271">*buffer*: указатель на место назначения для содержимого логического сектора.</span><span class="sxs-lookup"><span data-stu-id="1569c-271">*buffer*: Pointer to destination for contents of the logical sector.</span></span> <span data-ttu-id="1569c-272">Обратите внимание, что ожидается буфер размером 512 байт с округлением для адресации в формате ULONG.</span><span class="sxs-lookup"><span data-stu-id="1569c-272">Note that the buffer is assumed to be 512 bytes and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="1569c-273">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1569c-273">Return Values</span></span>

- <span data-ttu-id="1569c-274">**TX_SUCCESS** (0x00): запрос успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="1569c-274">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="1569c-275">**LX_ERROR** (0x01): ошибка чтения сектора флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-275">**LX_ERROR**: (0x01) Error reading NOR flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1569c-276">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1569c-276">Allowed From</span></span>

<span data-ttu-id="1569c-277">Потоки</span><span class="sxs-lookup"><span data-stu-id="1569c-277">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1569c-278">Пример</span><span class="sxs-lookup"><span data-stu-id="1569c-278">Example</span></span>

```c
/* Read logical sector 20 of the NOR flash instance "my_nor_flash" and place contents in "buffer". */ 
status = lx_nor_flash_sector_read(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contents of logical sector 20. */
```

### <a name="see-also"></a><span data-ttu-id="1569c-279">См. также:</span><span class="sxs-lookup"><span data-stu-id="1569c-279">See Also</span></span>

- <span data-ttu-id="1569c-280">lx_nor_flash_close;</span><span class="sxs-lookup"><span data-stu-id="1569c-280">lx_nor_flash_close</span></span>
- <span data-ttu-id="1569c-281">lx_nor_flash_defragment;</span><span class="sxs-lookup"><span data-stu-id="1569c-281">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="1569c-282">lx_nor_flash_extended_cache_enable;</span><span class="sxs-lookup"><span data-stu-id="1569c-282">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="1569c-283">lx_nor_flash_initialize;</span><span class="sxs-lookup"><span data-stu-id="1569c-283">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="1569c-284">lx_nor_flash_open;</span><span class="sxs-lookup"><span data-stu-id="1569c-284">lx_nor_flash_open</span></span>
- <span data-ttu-id="1569c-285">lx_nor_flash_partial_defragment;</span><span class="sxs-lookup"><span data-stu-id="1569c-285">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="1569c-286">lx_nor_flash_sector_release;</span><span class="sxs-lookup"><span data-stu-id="1569c-286">lx_nor_flash_sector_release</span></span>
- <span data-ttu-id="1569c-287">lx_nor_flash_sector_write.</span><span class="sxs-lookup"><span data-stu-id="1569c-287">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_release"></a><span data-ttu-id="1569c-288">lx_nor_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="1569c-288">lx_nor_flash_sector_release</span></span>

<span data-ttu-id="1569c-289">Освобождение сектора флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-289">Release NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="1569c-290">Прототип</span><span class="sxs-lookup"><span data-stu-id="1569c-290">Prototype</span></span>

```c
UINT lx_nor_flash_sector_release(
    LX_NOR_FLASH *nor_flash,
    ULONG logical_sector);
```

### <a name="description"></a><span data-ttu-id="1569c-291">Описание</span><span class="sxs-lookup"><span data-stu-id="1569c-291">Description</span></span>

<span data-ttu-id="1569c-292">Эта служба освобождает сопоставление для логического сектора в экземпляре флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-292">This service releases the logical sector mapping in the NOR flash instance.</span></span> <span data-ttu-id="1569c-293">Освобождение логического сектора, который не используется, повышает эффективность выравнивания износа в LevelX.</span><span class="sxs-lookup"><span data-stu-id="1569c-293">Releasing a logical sector when not used makes the LevelX wear leveling more efficient.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1569c-294">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="1569c-294">Input Parameters</span></span>

- <span data-ttu-id="1569c-295">*nor_flash*: указатель на экземпляр флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-295">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="1569c-296">*logical_sector*: логический сектор для освобождения.</span><span class="sxs-lookup"><span data-stu-id="1569c-296">*logical_sector*: Logical sector to release.</span></span>

### <a name="return-values"></a><span data-ttu-id="1569c-297">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1569c-297">Return Values</span></span>

- <span data-ttu-id="1569c-298">**TX_SUCCESS** (0x00): запрос успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="1569c-298">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="1569c-299">**LX_ERROR** (0x01): ошибка записи в сектор флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-299">**LX_ERROR**: (0x01) Error NOR flash sector write.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1569c-300">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1569c-300">Allowed From</span></span>

<span data-ttu-id="1569c-301">Потоки</span><span class="sxs-lookup"><span data-stu-id="1569c-301">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1569c-302">Пример</span><span class="sxs-lookup"><span data-stu-id="1569c-302">Example</span></span>

```c
/* Release logical sector 20 of the NOR flash instance "my_nor_flash". */  
status = lx_nor_flash_sector_release(&my_nor_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a><span data-ttu-id="1569c-303">См. также:</span><span class="sxs-lookup"><span data-stu-id="1569c-303">See Also</span></span>

- <span data-ttu-id="1569c-304">lx_nor_flash_close;</span><span class="sxs-lookup"><span data-stu-id="1569c-304">lx_nor_flash_close</span></span>
- <span data-ttu-id="1569c-305">lx_nor_flash_defragment;</span><span class="sxs-lookup"><span data-stu-id="1569c-305">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="1569c-306">lx_nor_flash_extended_cache_enable;</span><span class="sxs-lookup"><span data-stu-id="1569c-306">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="1569c-307">lx_nor_flash_initialize;</span><span class="sxs-lookup"><span data-stu-id="1569c-307">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="1569c-308">lx_nor_flash_open;</span><span class="sxs-lookup"><span data-stu-id="1569c-308">lx_nor_flash_open</span></span>
- <span data-ttu-id="1569c-309">lx_nor_flash_partial_defragment;</span><span class="sxs-lookup"><span data-stu-id="1569c-309">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="1569c-310">lx_nor_flash_sector_read;</span><span class="sxs-lookup"><span data-stu-id="1569c-310">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="1569c-311">lx_nor_flash_sector_write.</span><span class="sxs-lookup"><span data-stu-id="1569c-311">lx_nor_flash_sector_write</span></span>

## <a name="lx_nor_flash_sector_write"></a><span data-ttu-id="1569c-312">lx_nor_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="1569c-312">lx_nor_flash_sector_write</span></span>

<span data-ttu-id="1569c-313">Запись в сектор флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-313">Write NOR flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="1569c-314">Прототип</span><span class="sxs-lookup"><span data-stu-id="1569c-314">Prototype</span></span>

```c
UINT lx_nor_flash_sector_write(
    LX_nor_FLASH *NOR_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="1569c-315">Описание</span><span class="sxs-lookup"><span data-stu-id="1569c-315">Description</span></span>

<span data-ttu-id="1569c-316">Эта служба записывает указанный логический сектор в экземпляр флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-316">This service writes the specified logical sector in the NOR flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="1569c-317">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="1569c-317">Input Parameters</span></span>

- <span data-ttu-id="1569c-318">*nor_flash*: указатель на экземпляр флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-318">*nor_flash*: NOR flash instance pointer.</span></span>
- <span data-ttu-id="1569c-319">*logical_sector*: логический сектор для записи.</span><span class="sxs-lookup"><span data-stu-id="1569c-319">*logical_sector*: Logical sector to write.</span></span>
- <span data-ttu-id="1569c-320">*buffer*: указатель на содержимое логического сектора.</span><span class="sxs-lookup"><span data-stu-id="1569c-320">*buffer*: Pointer to the contents of the logical sector.</span></span> <span data-ttu-id="1569c-321">Обратите внимание, что ожидается буфер размером 512 байтов с округлением для адресации в формате ULONG.</span><span class="sxs-lookup"><span data-stu-id="1569c-321">Note that the buffer is assumed to be 512 bytes aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="1569c-322">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="1569c-322">Return Values</span></span>

- <span data-ttu-id="1569c-323">**TX_SUCCESS** (0x00): запрос успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="1569c-323">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="1569c-324">**LX_NO_SECTORS** (0x02): больше нет свободных секторов для выполнения записи</span><span class="sxs-lookup"><span data-stu-id="1569c-324">**LX_NO_SECTORS**: (0x02) No more free sectors are available to perform the write.</span></span>
- <span data-ttu-id="1569c-325">**LX_ERROR** (0x01): ошибка освобождения сектора флэш-памяти NOR.</span><span class="sxs-lookup"><span data-stu-id="1569c-325">**LX_ERROR**: (0x01) Error releasing NOR flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="1569c-326">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="1569c-326">Allowed From</span></span>

<span data-ttu-id="1569c-327">Потоки</span><span class="sxs-lookup"><span data-stu-id="1569c-327">Threads</span></span>

### <a name="example"></a><span data-ttu-id="1569c-328">Пример</span><span class="sxs-lookup"><span data-stu-id="1569c-328">Example</span></span>

```c
/* Write logical sector 20 of the NOR flash instance "my_nor_flash" with the contents pointed to by "buffer". */ 
status = lx_nor_flash_sector_write(&my_nor_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a><span data-ttu-id="1569c-329">См. также:</span><span class="sxs-lookup"><span data-stu-id="1569c-329">See Also</span></span>

- <span data-ttu-id="1569c-330">lx_nor_flash_close;</span><span class="sxs-lookup"><span data-stu-id="1569c-330">lx_nor_flash_close</span></span>
- <span data-ttu-id="1569c-331">lx_nor_flash_defragment;</span><span class="sxs-lookup"><span data-stu-id="1569c-331">lx_nor_flash_defragment</span></span>
- <span data-ttu-id="1569c-332">lx_nor_flash_extended_cache_enable;</span><span class="sxs-lookup"><span data-stu-id="1569c-332">lx_nor_flash_extended_cache_enable</span></span>
- <span data-ttu-id="1569c-333">lx_nor_flash_initialize;</span><span class="sxs-lookup"><span data-stu-id="1569c-333">lx_nor_flash_initialize</span></span>
- <span data-ttu-id="1569c-334">lx_nor_flash_open;</span><span class="sxs-lookup"><span data-stu-id="1569c-334">lx_nor_flash_open</span></span>
- <span data-ttu-id="1569c-335">lx_nor_flash_partial_defragment;</span><span class="sxs-lookup"><span data-stu-id="1569c-335">lx_nor_flash_partial_defragment</span></span>
- <span data-ttu-id="1569c-336">lx_nor_flash_sector_read;</span><span class="sxs-lookup"><span data-stu-id="1569c-336">lx_nor_flash_sector_read</span></span>
- <span data-ttu-id="1569c-337">lx_nor_flash_sector_release.</span><span class="sxs-lookup"><span data-stu-id="1569c-337">lx_nor_flash_sector_release</span></span>
