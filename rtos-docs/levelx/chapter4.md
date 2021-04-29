---
title: Глава 4. API-интерфейсы NAND для LevelX в ОСРВ Azure
description: API-интерфейсы NAND для LevelX в ОСРВ Azure, доступные для приложения.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 73bb94768396b4b8461791a164a102d1f8ef159f
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815428"
---
# <a name="chapter-4---azure-rtos-levelx-nand-apis"></a><span data-ttu-id="19c51-103">Глава 4. API-интерфейсы NAND для LevelX в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="19c51-103">Chapter 4 - Azure RTOS LevelX NAND APIs</span></span>

<span data-ttu-id="19c51-104">Приложению доступны следующие API-интерфейсы NAND для LevelX в ОСРВ Azure:</span><span class="sxs-lookup"><span data-stu-id="19c51-104">The Azure RTOS LevelX NAND APIs available to the application are:</span></span>

- <span data-ttu-id="19c51-105">***lx_nand_flash_close** _: _закрытие экземпляра флэш-памяти NAND*;</span><span class="sxs-lookup"><span data-stu-id="19c51-105">***lx_nand_flash_close** _: _Close NAND flash instance*</span></span>
- <span data-ttu-id="19c51-106">***lx_nand_flash_defragment** _: _дефрагментация экземпляра флэш-памяти NAND*;</span><span class="sxs-lookup"><span data-stu-id="19c51-106">***lx_nand_flash_defragment** _: _Defragment NAND flash instance*</span></span>
- <span data-ttu-id="19c51-107">***lx_nand_flash_extended_cache_enable** _: _включение и отключение расширенного кэша NAND*;</span><span class="sxs-lookup"><span data-stu-id="19c51-107">***lx_nand_flash_extended_cache_enable** _: _Enable/disable extended NAND cache*</span></span>
- <span data-ttu-id="19c51-108">***lx_nand_flash_initialize** _: _инициализация поддержки флэш-памяти NAND*;</span><span class="sxs-lookup"><span data-stu-id="19c51-108">***lx_nand_flash_initialize** _: _Initialize NAND flash support*</span></span>
- <span data-ttu-id="19c51-109">***lx_nand_flash_open** _: _открытие экземпляра флэш-памяти NAND*;</span><span class="sxs-lookup"><span data-stu-id="19c51-109">***lx_nand_flash_open** _: _Open NAND flash instance*</span></span>
- <span data-ttu-id="19c51-110">***lx_nand_flash_page_ecc_check** _: _проверка страницы на наличие ошибок ECC с коррекцией*;</span><span class="sxs-lookup"><span data-stu-id="19c51-110">***lx_nand_flash_page_ecc_check** _: _Check page for ECC errors with correction*</span></span>
- <span data-ttu-id="19c51-111">***lx_nand_flash_page_ecc_compute** _: _вычисление ECC для страницы*;</span><span class="sxs-lookup"><span data-stu-id="19c51-111">***lx_nand_flash_page_ecc_compute** _: _Computes ECC for page*</span></span>
- <span data-ttu-id="19c51-112">***lx_nand_flash_partial_defragment** _: _частичная дефрагментация экземпляра флэш-памяти NAND*;</span><span class="sxs-lookup"><span data-stu-id="19c51-112">***lx_nand_flash_partial_defragment** _: _Partial defragment of NAND flash instance*</span></span>
- <span data-ttu-id="19c51-113">***lx_nand_flash_sector_read** _: _чтение сектора флэш-памяти NAND*;</span><span class="sxs-lookup"><span data-stu-id="19c51-113">***lx_nand_flash_sector_read** _: _Read NAND flash sector*</span></span>
- <span data-ttu-id="19c51-114">***lx_nand_flash_sector_release** _: _освобождение сектора флэш-памяти NAND*;</span><span class="sxs-lookup"><span data-stu-id="19c51-114">***lx_nand_flash_sector_release** _: _Release NAND flash sector*</span></span>
- <span data-ttu-id="19c51-115">***lx_nand_flash_sector_write** _: _запись сектора флэш-памяти NAND*.</span><span class="sxs-lookup"><span data-stu-id="19c51-115">***lx_nand_flash_sector_write** _: _Write NAND flash sector*</span></span>

## <a name="lx_nand_flash_close"></a><span data-ttu-id="19c51-116">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="19c51-116">lx_nand_flash_close</span></span>

<span data-ttu-id="19c51-117">Закрытие экземпляра флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-117">Close NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="19c51-118">Прототип</span><span class="sxs-lookup"><span data-stu-id="19c51-118">Prototype</span></span>

```c
UINT lx_nand_flash_close(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a><span data-ttu-id="19c51-119">Описание</span><span class="sxs-lookup"><span data-stu-id="19c51-119">Description</span></span>

<span data-ttu-id="19c51-120">Эта служба закрывает ранее открытый экземпляр флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-120">This service closes the previously opened NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="19c51-121">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="19c51-121">Input Parameters</span></span>

- <span data-ttu-id="19c51-122">**nand_flash**: указатель на экземпляр флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-122">**nand_flash**: NAND flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="19c51-123">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="19c51-123">Return Values</span></span>

- <span data-ttu-id="19c51-124">**LX_SUCCESS** (0x00): запрос успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="19c51-124">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="19c51-125">**LX_ERROR** (0x01): ошибка закрытия экземпляра флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="19c51-125">**LX_ERROR**: (0x01) Error closing flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="19c51-126">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="19c51-126">Allowed From</span></span>

<span data-ttu-id="19c51-127">Потоки</span><span class="sxs-lookup"><span data-stu-id="19c51-127">Threads</span></span>

### <a name="example"></a><span data-ttu-id="19c51-128">Пример</span><span class="sxs-lookup"><span data-stu-id="19c51-128">Example</span></span>

```c
/* Close NAND flash instance "my_nand_flash". */
status = lx_nand_flash_close(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="19c51-129">См. также:</span><span class="sxs-lookup"><span data-stu-id="19c51-129">See Also</span></span>

- <span data-ttu-id="19c51-130">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-130">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="19c51-131">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="19c51-131">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="19c51-132">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="19c51-132">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="19c51-133">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="19c51-133">lx_nand_flash_open</span></span>
- <span data-ttu-id="19c51-134">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="19c51-134">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="19c51-135">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="19c51-135">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="19c51-136">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-136">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="19c51-137">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="19c51-137">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="19c51-138">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="19c51-138">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="19c51-139">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="19c51-139">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_defragment"></a><span data-ttu-id="19c51-140">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-140">lx_nand_flash_defragment</span></span>

<span data-ttu-id="19c51-141">Дефрагментация экземпляра флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-141">Defragment NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="19c51-142">Прототип</span><span class="sxs-lookup"><span data-stu-id="19c51-142">Prototype</span></span>

```c
UINT lx_nand_flash_defragment(LX_NAND_FLASH *nand_flash);
```

### <a name="description"></a><span data-ttu-id="19c51-143">Описание</span><span class="sxs-lookup"><span data-stu-id="19c51-143">Description</span></span>

<span data-ttu-id="19c51-144">Эта служба дефрагментирует ранее открытый экземпляр флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-144">This service defragments the previously opened NAND flash instance.</span></span> <span data-ttu-id="19c51-145">Процесс дефрагментации позволяет максимально увеличить количество свободных страниц и блоков.</span><span class="sxs-lookup"><span data-stu-id="19c51-145">The defragment process maximizes the number of free pages and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="19c51-146">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="19c51-146">Input Parameters</span></span>

- <span data-ttu-id="19c51-147">**nand_flash**: указатель на экземпляр флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-147">**nand_flash**: NAND flash instance pointer.</span></span>

### <a name="return-values"></a><span data-ttu-id="19c51-148">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="19c51-148">Return Values</span></span>

- <span data-ttu-id="19c51-149">**LX_SUCCESS** (0x00): запрос успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="19c51-149">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="19c51-150">**LX_ERROR** (0x01): ошибка дефрагментации экземпляра флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="19c51-150">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="19c51-151">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="19c51-151">Allowed From</span></span>

<span data-ttu-id="19c51-152">Потоки</span><span class="sxs-lookup"><span data-stu-id="19c51-152">Threads</span></span>

### <a name="example"></a><span data-ttu-id="19c51-153">Пример</span><span class="sxs-lookup"><span data-stu-id="19c51-153">Example</span></span>

```c
/* Defragment NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_defragment(&my_nand_flash);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="19c51-154">См. также:</span><span class="sxs-lookup"><span data-stu-id="19c51-154">See Also</span></span>

- <span data-ttu-id="19c51-155">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="19c51-155">lx_nand_flash_close</span></span>
- <span data-ttu-id="19c51-156">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="19c51-156">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="19c51-157">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="19c51-157">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="19c51-158">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="19c51-158">lx_nand_flash_open</span></span>
- <span data-ttu-id="19c51-159">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="19c51-159">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="19c51-160">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="19c51-160">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="19c51-161">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-161">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="19c51-162">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="19c51-162">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="19c51-163">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="19c51-163">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="19c51-164">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="19c51-164">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_extended_cache_enable"></a><span data-ttu-id="19c51-165">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="19c51-165">lx_nand_flash_extended_cache_enable</span></span>

<span data-ttu-id="19c51-166">Включение и выключение расширенного кэша NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-166">Enable/disable extended NAND cache</span></span>

### <a name="prototype"></a><span data-ttu-id="19c51-167">Прототип</span><span class="sxs-lookup"><span data-stu-id="19c51-167">Prototype</span></span>

```c
UINT lx_nand_flash_extended_cache_enable(
    LX_NAND_FLASH
    *nand_flash,  
    VOID *memory, 
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="19c51-168">Описание</span><span class="sxs-lookup"><span data-stu-id="19c51-168">Description</span></span>

<span data-ttu-id="19c51-169">Эта служба реализует в ОЗУ уровень кэша, используя предоставленную приложением память.</span><span class="sxs-lookup"><span data-stu-id="19c51-169">This service implements a cache layer in RAM using the memory supplied by the application.</span></span> <span data-ttu-id="19c51-170">Общий объем памяти, необходимый для операции полного кэширования, можно вычислить следующим образом:</span><span class="sxs-lookup"><span data-stu-id="19c51-170">The total amount of memory required for full cache operation can be calculated as follows:</span></span>

```c
size (in_bytes) = number_of_blocks (rounded up to be divisible by 4) +  
    ((number_of_blocks * pages_per_block) * 4)  +  
    ((number_of_blocks * (pages_per_block + 1)) * 4)
```

<span data-ttu-id="19c51-171">Если предоставленная память недостаточно велика для размещения полного кэша NAND, эта подпрограмма включит как можно большую часть кэша флэш-памяти NAND, основываясь на предоставленной памяти.</span><span class="sxs-lookup"><span data-stu-id="19c51-171">If the supplied memory is not large enough to accommodate the full NAND cache, this routine will enable as much of the NAND flash cache as possible based on the memory supplied.</span></span>

<span data-ttu-id="19c51-172">Кэш NAND отключается, если указанный адрес памяти имеет значение NULL.</span><span class="sxs-lookup"><span data-stu-id="19c51-172">The NAND cache is disabled if the memory address specified is NULL.</span></span> <span data-ttu-id="19c51-173">Таким образом, возможно временное использование кэша NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-173">Hence, the NAND cache maybe be used in a temporary fashion.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="19c51-174">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="19c51-174">Input Parameters</span></span>

- <span data-ttu-id="19c51-175">**nand_flash**: указатель на экземпляр флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-175">**nand_flash**: NAND flash instance pointer.</span></span>  
- <span data-ttu-id="19c51-176">**memory**: начальный адрес памяти для кэша с выравниванием для адресации в формате ULONG.</span><span class="sxs-lookup"><span data-stu-id="19c51-176">**memory**: Starting address for cache memory aligned for ULONG access.</span></span> <span data-ttu-id="19c51-177">Значение LX_NULL позволяет отключить кэш.</span><span class="sxs-lookup"><span data-stu-id="19c51-177">A value of LX_NULL disables the cache.</span></span>  
- <span data-ttu-id="19c51-178">**size**: размер предоставленной памяти в байтах.</span><span class="sxs-lookup"><span data-stu-id="19c51-178">**size**: The size in bytes of the memory supplied.</span></span>

### <a name="return-values"></a><span data-ttu-id="19c51-179">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="19c51-179">Return Values</span></span>

- <span data-ttu-id="19c51-180">**LX_SUCCESS** (0x00): запрос успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="19c51-180">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="19c51-181">**LX_ERROR** (0x01): недостаточно памяти для одного элемента кэша NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-181">**LX_ERROR**: (0x01) Not enough memory for one element of the NAND cache.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="19c51-182">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="19c51-182">Allowed From</span></span>

<span data-ttu-id="19c51-183">Потоки</span><span class="sxs-lookup"><span data-stu-id="19c51-183">Threads</span></span>

### <a name="example"></a><span data-ttu-id="19c51-184">Пример</span><span class="sxs-lookup"><span data-stu-id="19c51-184">Example</span></span>

```c
/* Enable the NAND flash cache for the instance "my_nand_flash". */
status = lx_nand_flash_extended_cache_enable(&my_nand_flash,  
    &my_memory, sizeof(my_memory));  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="19c51-185">См. также:</span><span class="sxs-lookup"><span data-stu-id="19c51-185">See Also</span></span>

- <span data-ttu-id="19c51-186">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="19c51-186">lx_nand_flash_close</span></span>
- <span data-ttu-id="19c51-187">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-187">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="19c51-188">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="19c51-188">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="19c51-189">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="19c51-189">lx_nand_flash_open</span></span>
- <span data-ttu-id="19c51-190">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="19c51-190">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="19c51-191">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="19c51-191">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="19c51-192">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-192">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="19c51-193">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="19c51-193">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="19c51-194">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="19c51-194">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="19c51-195">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="19c51-195">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_initialize"></a><span data-ttu-id="19c51-196">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="19c51-196">lx_nand_flash_initialize</span></span>

<span data-ttu-id="19c51-197">Инициализация поддержки флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-197">Initialize NAND flash support</span></span>

### <a name="prototype"></a><span data-ttu-id="19c51-198">Прототип</span><span class="sxs-lookup"><span data-stu-id="19c51-198">Prototype</span></span>

```c
UINT lx_nand_flash_initialize(void);
```

### <a name="description"></a><span data-ttu-id="19c51-199">Описание</span><span class="sxs-lookup"><span data-stu-id="19c51-199">Description</span></span>

<span data-ttu-id="19c51-200">Эта служба инициализирует поддержку флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-200">This service initializes LevelX NAND flash support.</span></span> <span data-ttu-id="19c51-201">Ее необходимо вызывать раньше любых других API-интерфейсов NAND для LevelX.</span><span class="sxs-lookup"><span data-stu-id="19c51-201">It must be called before any other LevelX NAND APIs.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="19c51-202">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="19c51-202">Input Parameters</span></span>

- <span data-ttu-id="19c51-203">**Нет**</span><span class="sxs-lookup"><span data-stu-id="19c51-203">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="19c51-204">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="19c51-204">Return Values</span></span>

- <span data-ttu-id="19c51-205">**LX_SUCCESS** (0x00): запрос успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="19c51-205">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="19c51-206">**LX_ERROR** (0x01): ошибка инициализации поддержки флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-206">**LX_ERROR**: (0x01) Error initializing NAND flash support.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="19c51-207">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="19c51-207">Allowed From</span></span>

<span data-ttu-id="19c51-208">Инициализация, потоки.</span><span class="sxs-lookup"><span data-stu-id="19c51-208">Initialization, Threads</span></span>

### <a name="example"></a><span data-ttu-id="19c51-209">Пример</span><span class="sxs-lookup"><span data-stu-id="19c51-209">Example</span></span>

```c
/* Initialize NAND flash support. */
status = lx_nand_flash_initialize();  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="19c51-210">См. также:</span><span class="sxs-lookup"><span data-stu-id="19c51-210">See Also</span></span>

- <span data-ttu-id="19c51-211">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="19c51-211">lx_nand_flash_close</span></span>
- <span data-ttu-id="19c51-212">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-212">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="19c51-213">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="19c51-213">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="19c51-214">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="19c51-214">lx_nand_flash_open</span></span>
- <span data-ttu-id="19c51-215">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="19c51-215">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="19c51-216">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="19c51-216">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="19c51-217">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-217">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="19c51-218">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="19c51-218">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="19c51-219">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="19c51-219">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="19c51-220">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="19c51-220">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_open"></a><span data-ttu-id="19c51-221">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="19c51-221">lx_nand_flash_open</span></span>

<span data-ttu-id="19c51-222">Открытие экземпляра флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-222">Open NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="19c51-223">Прототип</span><span class="sxs-lookup"><span data-stu-id="19c51-223">Prototype</span></span>

```c
UINT lx_nand_flash_open(
    LX_NAND_FLASH *nand_flash, 
    CHAR *name,  
    UINT (*nand_driver_initialize) (LX_NAND_FLASH *));
```

### <a name="description"></a><span data-ttu-id="19c51-224">Описание</span><span class="sxs-lookup"><span data-stu-id="19c51-224">Description</span></span>

<span data-ttu-id="19c51-225">Эта служба открывает экземпляр флэш-памяти NAND с использованием предоставленного блока управления флэш-памятью NAND и функции инициализации драйвера.</span><span class="sxs-lookup"><span data-stu-id="19c51-225">This service opens a NAND flash instance with the specified NAND flash control block and driver initialization function.</span></span> <span data-ttu-id="19c51-226">Обратите внимание, что функция инициализации драйвера отвечает за установку указателей на функции чтения, записи и стирания блоков или страниц в оборудовании NAND, сопоставленным с этим экземпляром флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-226">Note that the driver initialization function is responsible for installing various function pointers for reading, writing, and erasing blocks/pages of the NAND hardware associated with this NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="19c51-227">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="19c51-227">Input Parameters</span></span>

- <span data-ttu-id="19c51-228">**nand_flash**: указатель на экземпляр флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-228">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="19c51-229">**name**: имя экземпляра флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-229">**name**: Name of NAND flash instance.</span></span>
- <span data-ttu-id="19c51-230">**nand_driver_initialize**: указатель на функцию для инициализации драйвера флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-230">**nand_driver_initialize**: Function pointer to NAND flash driver initialization function.</span></span> <span data-ttu-id="19c51-231">Дополнительные сведения о функциях, которые должен реализовать драйвер флэш-памяти NAND, см. в главе 3 этого руководства.</span><span class="sxs-lookup"><span data-stu-id="19c51-231">Please refer to Chapter 3 of this guide for more details on NAND flash driver responsibilities.</span></span>

### <a name="return-values"></a><span data-ttu-id="19c51-232">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="19c51-232">Return Values</span></span>

- <span data-ttu-id="19c51-233">**LX_SUCCESS** (0x00): запрос успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="19c51-233">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="19c51-234">**LX_ERROR** (0x01): ошибка открытия экземпляра флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-234">**LX_ERROR**: (0x01) Error opening NAND flash instance.</span></span>
- <span data-ttu-id="19c51-235">**LX_NO_MEMORY** (0x08): драйвер не предоставил буфер для считывания одной страницы в ОЗУ.</span><span class="sxs-lookup"><span data-stu-id="19c51-235">**LX_NO_MEMORY**: (0x08) Driver did not provide buffer for reading one page into RAM.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="19c51-236">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="19c51-236">Allowed From</span></span>

<span data-ttu-id="19c51-237">Потоки</span><span class="sxs-lookup"><span data-stu-id="19c51-237">Threads</span></span>

### <a name="example"></a><span data-ttu-id="19c51-238">Пример</span><span class="sxs-lookup"><span data-stu-id="19c51-238">Example</span></span>

```c
/* Open NAND flash instance "my_nand_flash" with the driver "my_nand_driver_initialize". */ 
status = lx_nand_flash_open(&my_nand_flash,"my nand flash",  
    my_nand_driver_initialize);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="19c51-239">См. также:</span><span class="sxs-lookup"><span data-stu-id="19c51-239">See Also</span></span>

- <span data-ttu-id="19c51-240">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="19c51-240">lx_nand_flash_close</span></span>
- <span data-ttu-id="19c51-241">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-241">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="19c51-242">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="19c51-242">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="19c51-243">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="19c51-243">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="19c51-244">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="19c51-244">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="19c51-245">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="19c51-245">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="19c51-246">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-246">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="19c51-247">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="19c51-247">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="19c51-248">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="19c51-248">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="19c51-249">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="19c51-249">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_page_ecc_check"></a><span data-ttu-id="19c51-250">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="19c51-250">lx_nand_flash_page_ecc_check</span></span>

<span data-ttu-id="19c51-251">Проверка страницы на наличие ошибок ECC с коррекцией</span><span class="sxs-lookup"><span data-stu-id="19c51-251">Check page for ECC errors with correction</span></span>

### <a name="prototype"></a><span data-ttu-id="19c51-252">Прототип</span><span class="sxs-lookup"><span data-stu-id="19c51-252">Prototype</span></span>

```c
UINT lx_nand_flash_page_ecc_check(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a><span data-ttu-id="19c51-253">Описание</span><span class="sxs-lookup"><span data-stu-id="19c51-253">Description</span></span>

<span data-ttu-id="19c51-254">Эта служба проверяет целостность предоставленного буфера страниц NAND с помощью заданного кода ECC.</span><span class="sxs-lookup"><span data-stu-id="19c51-254">This service verifies the integrity of the supplied NAND page buffer with the supplied ECC.</span></span> <span data-ttu-id="19c51-255">Предполагается, что размер страницы (определенный в указателе экземпляра флэш-памяти NAND) является кратным 256 байтам, а указанный код ECC способен исправить ошибку в 1 бит в каждой из 256-байтовой части страницы.</span><span class="sxs-lookup"><span data-stu-id="19c51-255">Page size (defined in the NAND flash instance pointer) is assumed to be a multiple of 256-bytes and the ECC code supplied is capable of correcting a 1 bit error in each 256-byte portion of the page.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="19c51-256">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="19c51-256">Input Parameters</span></span>

- <span data-ttu-id="19c51-257">**nand_flash**: указатель на экземпляр флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-257">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="19c51-258">**page_buffer**: указатель на буфер флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-258">**page_buffer**: Pointer to NAND flash page buffer.</span></span>
- <span data-ttu-id="19c51-259">**ecc_buffer**: указатель на ECC для страницы флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-259">**ecc_buffer**: Pointer to ECC for NAND flash page.</span></span> <span data-ttu-id="19c51-260">Обратите внимание, что для каждой 256-байтовой части страницы имеется 3 байта ECC.</span><span class="sxs-lookup"><span data-stu-id="19c51-260">Note that there are 3 ECC bytes per 256-byte portion of the page.</span></span>

### <a name="return-values"></a><span data-ttu-id="19c51-261">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="19c51-261">Return Values</span></span>

- <span data-ttu-id="19c51-262">**LX_SUCCESS** (0x00): страница NAND не содержит ошибки.</span><span class="sxs-lookup"><span data-stu-id="19c51-262">**LX_SUCCESS**: (0x00) NAND page has no errors.</span></span>
- <span data-ttu-id="19c51-263">**LX_NAND_ERROR_CORRECTED** (0x06): одна или несколько 1-байтовых ошибок были исправлены на странице NAND — исправления находятся в буфере страниц.</span><span class="sxs-lookup"><span data-stu-id="19c51-263">**LX_NAND_ERROR_CORRECTED**: (0x06) One or more 1-bit errors were corrected in the NAND page—correction(s) are in the page buffer.</span></span>
- <span data-ttu-id="19c51-264">**LX_NAND_ERROR_NOT_CORRECTED** (0x07): слишком много ошибок для исправления на странице NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-264">**LX_NAND_ERROR_NOT_CORRECTED**: (0x07) Too many errors to correct on the NAND page.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="19c51-265">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="19c51-265">Allowed From</span></span>

<span data-ttu-id="19c51-266">Драйвер LevelX</span><span class="sxs-lookup"><span data-stu-id="19c51-266">LevelX Driver</span></span>

### <a name="example"></a><span data-ttu-id="19c51-267">Пример</span><span class="sxs-lookup"><span data-stu-id="19c51-267">Example</span></span>

```c
/* Check the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash" . */
status = lx_nand_flash_page_ecc_check(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the page is valid. */
```

### <a name="see-also"></a><span data-ttu-id="19c51-268">См. также:</span><span class="sxs-lookup"><span data-stu-id="19c51-268">See Also</span></span>

- <span data-ttu-id="19c51-269">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="19c51-269">lx_nand_flash_close</span></span>
- <span data-ttu-id="19c51-270">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-270">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="19c51-271">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="19c51-271">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="19c51-272">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="19c51-272">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="19c51-273">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="19c51-273">lx_nand_flash_open</span></span>
- <span data-ttu-id="19c51-274">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="19c51-274">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="19c51-275">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-275">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="19c51-276">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="19c51-276">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="19c51-277">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="19c51-277">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="19c51-278">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="19c51-278">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_page_ecc_compute"></a><span data-ttu-id="19c51-279">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="19c51-279">lx_nand_flash_page_ecc_compute</span></span>

<span data-ttu-id="19c51-280">Вычисление ECC для страницы.</span><span class="sxs-lookup"><span data-stu-id="19c51-280">Compute ECC for page</span></span>

### <a name="prototype"></a><span data-ttu-id="19c51-281">Прототип</span><span class="sxs-lookup"><span data-stu-id="19c51-281">Prototype</span></span>

```c
UINT lx_nand_flash_page_ecc_compute(
    LX_NAND_FLASH *nand_flash,  
    UCHAR *page_buffer, 
    UCHAR *ecc_buffer);
```

### <a name="description"></a><span data-ttu-id="19c51-282">Описание</span><span class="sxs-lookup"><span data-stu-id="19c51-282">Description</span></span>

<span data-ttu-id="19c51-283">Эта служба вычисляет код ECC для заданного буфера страниц NAND и возвращает код ECC в заданном буфере ECC.</span><span class="sxs-lookup"><span data-stu-id="19c51-283">This service computes the ECC of the supplied NAND page buffer and returns the ECC in the supplied ECC buffer.</span></span> <span data-ttu-id="19c51-284">Предполагается, что размер страницы кратен 256 байтам (что определено в указателе экземпляра флэш-памяти NAND).</span><span class="sxs-lookup"><span data-stu-id="19c51-284">Page size is assume to be a multiple of 256-bytes (defined in the NAND flash instance pointer).</span></span> <span data-ttu-id="19c51-285">Код ECC используется для проверки целостности страницы при ее последующем считывании.</span><span class="sxs-lookup"><span data-stu-id="19c51-285">The ECC code is used to verify the integrity of the page when it is read at a later time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="19c51-286">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="19c51-286">Input Parameters</span></span>

- <span data-ttu-id="19c51-287">**nand_flash**: указатель на экземпляр флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-287">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="19c51-288">**page_buffer**: указатель на буфер флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-288">**page_buffer**: Pointer to NAND flash page buffer.</span></span>
- <span data-ttu-id="19c51-289">**ecc_buffer**: указатель на назначение для ECC страницы флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-289">**ecc_buffer**: Pointer to destination for ECC of the NAND flash page.</span></span> <span data-ttu-id="19c51-290">Обратите внимание, что на 256-байтовую часть страницы должно быть сохранено 3 байта ECC.</span><span class="sxs-lookup"><span data-stu-id="19c51-290">Note that must be 3 bytes of ECC storage per 256-byte portion of the page.</span></span> <span data-ttu-id="19c51-291">Например, 2048-байтовая страница потребовала бы 24 байта для ECC.</span><span class="sxs-lookup"><span data-stu-id="19c51-291">For example, a 2048 byte page would require 24 bytes for the ECC.</span></span>

### <a name="return-values"></a><span data-ttu-id="19c51-292">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="19c51-292">Return Values</span></span>

- <span data-ttu-id="19c51-293">**LX_SUCCESS** (0x00): код ECC успешно вычислен.</span><span class="sxs-lookup"><span data-stu-id="19c51-293">**LX_SUCCESS**: (0x00) ECC successfully calculated.</span></span>
- <span data-ttu-id="19c51-294">**LX_ERROR** (0x01): ошибка при вычислении ECC.</span><span class="sxs-lookup"><span data-stu-id="19c51-294">**LX_ERROR**: (0x01) Error calculating ECC.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="19c51-295">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="19c51-295">Allowed From</span></span>

<span data-ttu-id="19c51-296">Драйвер LevelX</span><span class="sxs-lookup"><span data-stu-id="19c51-296">LevelX Driver</span></span>

### <a name="example"></a><span data-ttu-id="19c51-297">Пример</span><span class="sxs-lookup"><span data-stu-id="19c51-297">Example</span></span>

```c
/* Compute ECC for the NAND page pointed to by "page_pointer" of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_page_ecc_compute(&my_nand_flash, page_pointer, ecc_pointer);  
  
/* If status is LX_SUCCESS the ECC was calculated and Can be found in the memory pointed to by "ecc_pointer." */
```

### <a name="see-also"></a><span data-ttu-id="19c51-298">См. также:</span><span class="sxs-lookup"><span data-stu-id="19c51-298">See Also</span></span>

- <span data-ttu-id="19c51-299">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="19c51-299">lx_nand_flash_close</span></span>
- <span data-ttu-id="19c51-300">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-300">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="19c51-301">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="19c51-301">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="19c51-302">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="19c51-302">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="19c51-303">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="19c51-303">lx_nand_flash_open</span></span>
- <span data-ttu-id="19c51-304">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="19c51-304">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="19c51-305">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-305">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="19c51-306">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="19c51-306">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="19c51-307">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="19c51-307">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="19c51-308">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="19c51-308">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_partial_defragment"></a><span data-ttu-id="19c51-309">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-309">lx_nand_flash_partial_defragment</span></span>

<span data-ttu-id="19c51-310">Частичная дефрагментация экземпляра флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-310">Partial defragment of NAND flash instance</span></span>

### <a name="prototype"></a><span data-ttu-id="19c51-311">Прототип</span><span class="sxs-lookup"><span data-stu-id="19c51-311">Prototype</span></span>

```c
UINT lx_nand_flash_partial_defragment(
    LX_NAND_FLASH *nand_flash,  
    UINT max_blocks);
```

### <a name="description"></a><span data-ttu-id="19c51-312">Описание</span><span class="sxs-lookup"><span data-stu-id="19c51-312">Description</span></span>

<span data-ttu-id="19c51-313">Эта служба выполняет дефрагментацию ранее открытого экземпляра флэш-памяти NAND вплоть до максимального указанного числа блоков.</span><span class="sxs-lookup"><span data-stu-id="19c51-313">This service defragments the previously opened NAND flash instance up to the maximum number of blocks specified.</span></span> <span data-ttu-id="19c51-314">Процесс дефрагментации позволяет максимально увеличить количество свободных страниц и блоков.</span><span class="sxs-lookup"><span data-stu-id="19c51-314">The defragment process maximizes the number of free pages and blocks.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="19c51-315">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="19c51-315">Input Parameters</span></span>

- <span data-ttu-id="19c51-316">**nand_flash**: указатель на экземпляр флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-316">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="19c51-317">**max_blocks**: максимальное количество блоков.</span><span class="sxs-lookup"><span data-stu-id="19c51-317">**max_blocks**: Maximum number of blocks.</span></span>

### <a name="return-values"></a><span data-ttu-id="19c51-318">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="19c51-318">Return Values</span></span>

- <span data-ttu-id="19c51-319">**LX_SUCCESS** (0x00): запрос успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="19c51-319">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="19c51-320">**LX_ERROR** (0x01): ошибка дефрагментации экземпляра флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="19c51-320">**LX_ERROR**: (0x01) Error defragmenting flash instance.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="19c51-321">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="19c51-321">Allowed From</span></span>

<span data-ttu-id="19c51-322">Потоки</span><span class="sxs-lookup"><span data-stu-id="19c51-322">Threads</span></span>

### <a name="example"></a><span data-ttu-id="19c51-323">Пример</span><span class="sxs-lookup"><span data-stu-id="19c51-323">Example</span></span>

```c
/* Defragment 1 block of NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_partial_defragment(&my_nand_flash, 1);  
  
/* If status is LX_SUCCESS the request was successful. */
```

### <a name="see-also"></a><span data-ttu-id="19c51-324">См. также:</span><span class="sxs-lookup"><span data-stu-id="19c51-324">See Also</span></span>

- <span data-ttu-id="19c51-325">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="19c51-325">lx_nand_flash_close</span></span>
- <span data-ttu-id="19c51-326">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-326">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="19c51-327">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="19c51-327">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="19c51-328">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="19c51-328">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="19c51-329">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="19c51-329">lx_nand_flash_open</span></span>
- <span data-ttu-id="19c51-330">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="19c51-330">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="19c51-331">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="19c51-331">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="19c51-332">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="19c51-332">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="19c51-333">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="19c51-333">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="19c51-334">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="19c51-334">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_read"></a><span data-ttu-id="19c51-335">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="19c51-335">lx_nand_flash_sector_read</span></span>

<span data-ttu-id="19c51-336">Чтение сектора флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-336">Read NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="19c51-337">Прототип</span><span class="sxs-lookup"><span data-stu-id="19c51-337">Prototype</span></span>

```c
UINT lx_nand_flash_sector_read(
    LX_NAND_FLASH *nand_flash,  
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="19c51-338">Описание</span><span class="sxs-lookup"><span data-stu-id="19c51-338">Description</span></span>

<span data-ttu-id="19c51-339">Эта служба считывает логический сектор из экземпляра флэш-памяти NAND, а при успешном выполнении возвращает содержимое в предоставленном буфере.</span><span class="sxs-lookup"><span data-stu-id="19c51-339">This service reads the logical sector from the NAND flash instance and if successful returns the contents in the supplied buffer.</span></span> <span data-ttu-id="19c51-340">Обратите внимание, что размер сектора NAND всегда равен размеру страницы базового оборудования NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-340">Note that NAND sector size is always the page size of the underlying NAND hardware.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="19c51-341">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="19c51-341">Input Parameters</span></span>

- <span data-ttu-id="19c51-342">**nand_flash**: указатель на экземпляр флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-342">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="19c51-343">**logical_sector**: логический сектор для считывания.</span><span class="sxs-lookup"><span data-stu-id="19c51-343">**logical_sector**: Logical sector to read.</span></span>
- <span data-ttu-id="19c51-344">**buffer**: указатель на место назначения для содержимого логического сектора.</span><span class="sxs-lookup"><span data-stu-id="19c51-344">**buffer**: Pointer to destination for contents of the logical sector.</span></span> <span data-ttu-id="19c51-345">Обратите внимание, что ожидается буфер размером, равным размеру страницы флэш-памяти NAND, и с выравниванием для адресации в формате ULONG.</span><span class="sxs-lookup"><span data-stu-id="19c51-345">Note that the buffer is assumed to be the size of the NAND flash page size and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="19c51-346">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="19c51-346">Return Values</span></span>

- <span data-ttu-id="19c51-347">**LX_SUCCESS** (0x00): запрос успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="19c51-347">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="19c51-348">**LX_ERROR** (0x01): ошибка чтения сектора флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-348">**LX_ERROR**: (0x01) Error reading NAND flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="19c51-349">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="19c51-349">Allowed From</span></span>

<span data-ttu-id="19c51-350">Потоки</span><span class="sxs-lookup"><span data-stu-id="19c51-350">Threads</span></span>

### <a name="example"></a><span data-ttu-id="19c51-351">Пример</span><span class="sxs-lookup"><span data-stu-id="19c51-351">Example</span></span>

```c
/* Read logical sector 20 of the NAND flash instance "my_nand_flash" and place contents in "buffer". */
status = lx_nand_flash_sector_read(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, "buffer" contains the contentsnof logical sector 20. */
```

### <a name="see-also"></a><span data-ttu-id="19c51-352">См. также:</span><span class="sxs-lookup"><span data-stu-id="19c51-352">See Also</span></span>

- <span data-ttu-id="19c51-353">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="19c51-353">lx_nand_flash_close</span></span>
- <span data-ttu-id="19c51-354">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-354">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="19c51-355">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="19c51-355">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="19c51-356">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="19c51-356">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="19c51-357">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="19c51-357">lx_nand_flash_open</span></span>
- <span data-ttu-id="19c51-358">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="19c51-358">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="19c51-359">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="19c51-359">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="19c51-360">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-360">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="19c51-361">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="19c51-361">lx_nand_flash_sector_release</span></span>
- <span data-ttu-id="19c51-362">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="19c51-362">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_release"></a><span data-ttu-id="19c51-363">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="19c51-363">lx_nand_flash_sector_release</span></span>

<span data-ttu-id="19c51-364">Освобождение сектора флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-364">Release NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="19c51-365">Прототип</span><span class="sxs-lookup"><span data-stu-id="19c51-365">Prototype</span></span>

```c
UINT lx_nand_flash_sector_release(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector);
```

### <a name="description"></a><span data-ttu-id="19c51-366">Описание</span><span class="sxs-lookup"><span data-stu-id="19c51-366">Description</span></span>

<span data-ttu-id="19c51-367">Эта служба освобождает сопоставление для логического сектора в экземпляре флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-367">This service releases the logical sector mapping in the NAND flash instance.</span></span> <span data-ttu-id="19c51-368">Освобождение логического сектора, который не используется, повышает эффективность выравнивания износа в LevelX.</span><span class="sxs-lookup"><span data-stu-id="19c51-368">Releasing a logical sector when not used makes the LevelX wear leveling more efficient.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="19c51-369">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="19c51-369">Input Parameters</span></span>

- <span data-ttu-id="19c51-370">**nand_flash**: указатель на экземпляр флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-370">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="19c51-371">**logical_sector**: логический сектор для освобождения.</span><span class="sxs-lookup"><span data-stu-id="19c51-371">**logical_sector**: Logical sector to release.</span></span>

### <a name="return-values"></a><span data-ttu-id="19c51-372">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="19c51-372">Return Values</span></span>

- <span data-ttu-id="19c51-373">**LX_SUCCESS** (0x00): запрос успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="19c51-373">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="19c51-374">**LX_ERROR** (0x01): ошибка записи в сектор флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-374">**LX_ERROR**: (0x01) Error NAND flash sector write.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="19c51-375">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="19c51-375">Allowed From</span></span>

<span data-ttu-id="19c51-376">Потоки</span><span class="sxs-lookup"><span data-stu-id="19c51-376">Threads</span></span>

### <a name="example"></a><span data-ttu-id="19c51-377">Пример</span><span class="sxs-lookup"><span data-stu-id="19c51-377">Example</span></span>

```c
/* Release logical sector 20 of the NAND flash instance "my_nand_flash". */  
status = lx_nand_flash_sector_release(&my_nand_flash, 20);  
  
/* If status is LX_SUCCESS, logical sector 20 has been released. */
```

### <a name="see-also"></a><span data-ttu-id="19c51-378">См. также:</span><span class="sxs-lookup"><span data-stu-id="19c51-378">See Also</span></span>

- <span data-ttu-id="19c51-379">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="19c51-379">lx_nand_flash_close</span></span>
- <span data-ttu-id="19c51-380">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-380">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="19c51-381">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="19c51-381">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="19c51-382">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="19c51-382">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="19c51-383">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="19c51-383">lx_nand_flash_open</span></span>
- <span data-ttu-id="19c51-384">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="19c51-384">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="19c51-385">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="19c51-385">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="19c51-386">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-386">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="19c51-387">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="19c51-387">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="19c51-388">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="19c51-388">lx_nand_flash_sector_write</span></span>

## <a name="lx_nand_flash_sector_write"></a><span data-ttu-id="19c51-389">lx_nand_flash_sector_write</span><span class="sxs-lookup"><span data-stu-id="19c51-389">lx_nand_flash_sector_write</span></span>

<span data-ttu-id="19c51-390">Запись сектора флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-390">Write NAND flash sector</span></span>

### <a name="prototype"></a><span data-ttu-id="19c51-391">Прототип</span><span class="sxs-lookup"><span data-stu-id="19c51-391">Prototype</span></span>

```c
UINT lx_nand_flash_sector_write(
    LX_NAND_FLASH *nand_flash,
    ULONG logical_sector, 
    VOID *buffer);
```

### <a name="description"></a><span data-ttu-id="19c51-392">Описание</span><span class="sxs-lookup"><span data-stu-id="19c51-392">Description</span></span>

<span data-ttu-id="19c51-393">Эта служба записывает указанный логический сектор в экземпляр флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-393">This service writes the specified logical sector in the NAND flash instance.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="19c51-394">Входные параметры</span><span class="sxs-lookup"><span data-stu-id="19c51-394">Input Parameters</span></span>

- <span data-ttu-id="19c51-395">**nand_flash**: указатель на экземпляр флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-395">**nand_flash**: NAND flash instance pointer.</span></span>
- <span data-ttu-id="19c51-396">**logical_sector**: логический сектор для записи.</span><span class="sxs-lookup"><span data-stu-id="19c51-396">**logical_sector**: Logical sector to write.</span></span>
- <span data-ttu-id="19c51-397">**buffer**: указатель на содержимое логического сектора.</span><span class="sxs-lookup"><span data-stu-id="19c51-397">**buffer**: Pointer to the contents of the logical sector.</span></span> <span data-ttu-id="19c51-398">Обратите внимание, что ожидается буфер размером, равным размеру страницы флэш-памяти NAND, и с выравниванием для адресации в формате ULONG.</span><span class="sxs-lookup"><span data-stu-id="19c51-398">Note that the buffer is assumed to be the size of the NAND flash page size and aligned for ULONG access.</span></span>

### <a name="return-values"></a><span data-ttu-id="19c51-399">Возвращаемые значения</span><span class="sxs-lookup"><span data-stu-id="19c51-399">Return Values</span></span>

- <span data-ttu-id="19c51-400">**LX_SUCCESS** (0x00): запрос успешно выполнен.</span><span class="sxs-lookup"><span data-stu-id="19c51-400">**LX_SUCCESS**: (0x00) Successful request.</span></span>
- <span data-ttu-id="19c51-401">**LX_NO_SECTORS** (0x02): больше нет свободных секторов для выполнения записи.</span><span class="sxs-lookup"><span data-stu-id="19c51-401">**LX_NO_SECTORS**: (0x02) No more free sectors are available to perform the write.</span></span>
- <span data-ttu-id="19c51-402">**LX_ERROR** (0x01): ошибка освобождения сектора флэш-памяти NAND.</span><span class="sxs-lookup"><span data-stu-id="19c51-402">**LX_ERROR**: (0x01) Error releasing NAND flash sector.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="19c51-403">Допустимые источники</span><span class="sxs-lookup"><span data-stu-id="19c51-403">Allowed From</span></span>

<span data-ttu-id="19c51-404">Потоки</span><span class="sxs-lookup"><span data-stu-id="19c51-404">Threads</span></span>

### <a name="example"></a><span data-ttu-id="19c51-405">Пример</span><span class="sxs-lookup"><span data-stu-id="19c51-405">Example</span></span>

```c
/* Write logical sector 20 of the NAND flash instance "my_nand_flash" with the contents pointed to by "buffer". */  
status = lx_nand_flash_sector_write(&my_nand_flash, 20, buffer);  
  
/* If status is LX_SUCCESS, logical sector 20 has been written with the contents of "buffer". */
```

### <a name="see-also"></a><span data-ttu-id="19c51-406">См. также:</span><span class="sxs-lookup"><span data-stu-id="19c51-406">See Also</span></span>

- <span data-ttu-id="19c51-407">lx_nand_flash_close</span><span class="sxs-lookup"><span data-stu-id="19c51-407">lx_nand_flash_close</span></span>
- <span data-ttu-id="19c51-408">lx_nand_flash_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-408">lx_nand_flash_defragment</span></span>
- <span data-ttu-id="19c51-409">lx_nand_flash_extended_cache_enable</span><span class="sxs-lookup"><span data-stu-id="19c51-409">lx_nand_flash_extended_cache_enable</span></span>
- <span data-ttu-id="19c51-410">lx_nand_flash_initialize</span><span class="sxs-lookup"><span data-stu-id="19c51-410">lx_nand_flash_initialize</span></span>
- <span data-ttu-id="19c51-411">lx_nand_flash_open</span><span class="sxs-lookup"><span data-stu-id="19c51-411">lx_nand_flash_open</span></span>
- <span data-ttu-id="19c51-412">lx_nand_flash_page_ecc_check</span><span class="sxs-lookup"><span data-stu-id="19c51-412">lx_nand_flash_page_ecc_check</span></span>
- <span data-ttu-id="19c51-413">lx_nand_flash_page_ecc_compute</span><span class="sxs-lookup"><span data-stu-id="19c51-413">lx_nand_flash_page_ecc_compute</span></span>
- <span data-ttu-id="19c51-414">lx_nand_flash_partial_defragment</span><span class="sxs-lookup"><span data-stu-id="19c51-414">lx_nand_flash_partial_defragment</span></span>
- <span data-ttu-id="19c51-415">lx_nand_flash_sector_read</span><span class="sxs-lookup"><span data-stu-id="19c51-415">lx_nand_flash_sector_read</span></span>
- <span data-ttu-id="19c51-416">lx_nand_flash_sector_release</span><span class="sxs-lookup"><span data-stu-id="19c51-416">lx_nand_flash_sector_release</span></span>
