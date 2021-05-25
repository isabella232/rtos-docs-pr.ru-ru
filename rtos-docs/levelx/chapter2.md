---
title: Глава 2. Установка и использование LevelX для ОСРВ Azure
description: Установка и использование LevelX очень просты. Все необходимые процессы описываются в следующих разделах этой главы.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 34110e74e8ad0a6acd376c00c1284a3ea715c5f5
ms.sourcegitcommit: 4ebe7c51ba850951c6a9d0f15e22d07bb752bc28
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/20/2021
ms.locfileid: "110223321"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a><span data-ttu-id="f0bb2-103">Глава 2. Установка и использование LevelX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="f0bb2-103">Chapter 2 - Installation and use of Azure RTOS LevelX</span></span>

<span data-ttu-id="f0bb2-104">Установка и использование LevelX для ОСРВ Azure очень проста. Все необходимые процессы описываются в следующих разделах этой главы.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-104">Installation and use of Azure RTOS LevelX is straightforward and described in the following sections of this chapter.</span></span>

## <a name="distribution"></a><span data-ttu-id="f0bb2-105">Distribution</span><span class="sxs-lookup"><span data-stu-id="f0bb2-105">Distribution</span></span>

<span data-ttu-id="f0bb2-106">LevelX распространяется в формате ANSI на C, где каждая функция содержится в отдельном файле C.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-106">LevelX is distributed in ANSI C where each function is contained in its own separate C file.</span></span> <span data-ttu-id="f0bb2-107">Ниже перечислены файлы, входящие в дистрибутив LevelX.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-107">The files in the LevelX distribution are as follows.</span></span>
- <span data-ttu-id="f0bb2-108">lx_api.h</span><span class="sxs-lookup"><span data-stu-id="f0bb2-108">lx_api.h</span></span>
- <span data-ttu-id="f0bb2-109">lx_nand_flash_256byte_ecc_check.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-109">lx_nand_flash_256byte_ecc_check.c</span></span>
- <span data-ttu-id="f0bb2-110">lx_nand_flash_256byte_ecc_compute.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-110">lx_nand_flash_256byte_ecc_compute.c</span></span>
- <span data-ttu-id="f0bb2-111">lx_nand_flash_block_full_update.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-111">lx_nand_flash_block_full_update.c</span></span>
- <span data-ttu-id="f0bb2-112">lx_nand_flash_block_reclaim.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-112">lx_nand_flash_block_reclaim.c</span></span>
- <span data-ttu-id="f0bb2-113">lx_nand_flash_close.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-113">lx_nand_flash_close.c</span></span>
- <span data-ttu-id="f0bb2-114">lx_nand_flash_defragment.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-114">lx_nand_flash_defragment.c</span></span>  
- <span data-ttu-id="f0bb2-115">lx_nand_flash_extended_cache_enable.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-115">lx_nand_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="f0bb2-116">lx_nand_flash_initialize.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-116">lx_nand_flash_initialize.c</span></span>
- <span data-ttu-id="f0bb2-117">lx_nand_flash_logical_sector_find.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-117">lx_nand_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="f0bb2-118">lx_nand_flash_next_block_to_erase_find.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-118">lx_nand_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="f0bb2-119">lx_nand_flash_open.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-119">lx_nand_flash_open.c</span></span>
- <span data-ttu-id="f0bb2-120">lx_nand_flash_page_ecc_check.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-120">lx_nand_flash_page_ecc_check.c</span></span>
- <span data-ttu-id="f0bb2-121">lx_nand_flash_page_ecc_compute.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-121">lx_nand_flash_page_ecc_compute.c</span></span>  
- <span data-ttu-id="f0bb2-122">lx_nand_flash_partial_defragment.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-122">lx_nand_flash_partial_defragment.c</span></span>
- <span data-ttu-id="f0bb2-123">lx_nand_flash_physical_page_allocate.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-123">lx_nand_flash_physical_page_allocate.c</span></span>
- <span data-ttu-id="f0bb2-124">lx_nand_flash_sector_mapping_cache_invalidate.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-124">lx_nand_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="f0bb2-125">lx_nand_flash_sector_read.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-125">lx_nand_flash_sector_read.c</span></span>
- <span data-ttu-id="f0bb2-126">lx_nand_flash_sector_release.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-126">lx_nand_flash_sector_release.c</span></span>
- <span data-ttu-id="f0bb2-127">lx_nand_flash_sector_write.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-127">lx_nand_flash_sector_write.c</span></span>
- <span data-ttu-id="f0bb2-128">lx_nand_flash_system_error.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-128">lx_nand_flash_system_error.c</span></span>
- <span data-ttu-id="f0bb2-129">lx_nor_flash_block_reclaim.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-129">lx_nor_flash_block_reclaim.c</span></span>
- <span data-ttu-id="f0bb2-130">lx_nor_flash_close.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-130">lx_nor_flash_close.c</span></span>
- <span data-ttu-id="f0bb2-131">lx_nor_flash_defragment.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-131">lx_nor_flash_defragment.c</span></span>  
- <span data-ttu-id="f0bb2-132">lx_nor_flash_extended_cache_enable.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-132">lx_nor_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="f0bb2-133">lx_nor_flash_initialize.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-133">lx_nor_flash_initialize.c</span></span>
- <span data-ttu-id="f0bb2-134">lx_nor_flash_logical_sector_find.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-134">lx_nor_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="f0bb2-135">lx_nor_flash_next_block_to_erase_find.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-135">lx_nor_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="f0bb2-136">lx_nor_flash_open.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-136">lx_nor_flash_open.c</span></span>
- <span data-ttu-id="f0bb2-137">lx_nor_flash_partial_defragment.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-137">lx_nor_flash_partial_defragment.c</span></span>
- <span data-ttu-id="f0bb2-138">lx_nor_flash_physical_sector_allocate.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-138">lx_nor_flash_physical_sector_allocate.c</span></span>
- <span data-ttu-id="f0bb2-139">lx_nor_flash_sector_mapping_cache_invalidate.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-139">lx_nor_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="f0bb2-140">lx_nor_flash_sector_read.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-140">lx_nor_flash_sector_read.c</span></span>
- <span data-ttu-id="f0bb2-141">lx_nor_flash_sector_release.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-141">lx_nor_flash_sector_release.c</span></span>
- <span data-ttu-id="f0bb2-142">lx_nor_flash_sector_write.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-142">lx_nor_flash_sector_write.c</span></span>
- <span data-ttu-id="f0bb2-143">lx_nor_flash_system_error.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-143">lx_nor_flash_system_error.c</span></span>

<span data-ttu-id="f0bb2-144">Существуют также симуляторы и примеры драйверов FileX для работы экземпляров LevelX с флэш-памятью NAND и NOR, которые перечислены ниже.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-144">There are also simulator and FileX driver samples for both LevelX NAND and NOR instances, as follows.</span></span>

- <span data-ttu-id="f0bb2-145">demo_filex_nand_flash.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-145">demo_filex_nand_flash.c</span></span>  
- <span data-ttu-id="f0bb2-146">fx_nand_flash_simulated_driver.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-146">fx_nand_flash_simulated_driver.c</span></span>
- <span data-ttu-id="f0bb2-147">lx_nand_flash_simulator.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-147">lx_nand_flash_simulator.c</span></span>
- <span data-ttu-id="f0bb2-148">demo_filex_nor_flash.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-148">demo_filex_nor_flash.c</span></span>  
- <span data-ttu-id="f0bb2-149">fx_nor_flash_simulated_driver.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-149">fx_nor_flash_simulated_driver.c</span></span>
- <span data-ttu-id="f0bb2-150">lx_nor_flash_simulator.c</span><span class="sxs-lookup"><span data-stu-id="f0bb2-150">lx_nor_flash_simulator.c</span></span>

<span data-ttu-id="f0bb2-151">Конечно, если вам нужна только флэш-память NAND, достаточно использовать файлы LevelX для NAND (***lx_nand_\*.c***).</span><span class="sxs-lookup"><span data-stu-id="f0bb2-151">Of course, if only NAND flash is required, only the LevelX NAND flash files (***lx_nand_\*.c***) are needed.</span></span> <span data-ttu-id="f0bb2-152">Аналогично, если нужна только флэш-память NOR, достаточно использовать файлы LevelX для NOR (\*\*_lx_nor_\_.c\*\*\*).</span><span class="sxs-lookup"><span data-stu-id="f0bb2-152">Similarly, if only NOR flash is required, only the NOR flash files (\*\*_lx_nor_\_.c\*\*\*) are needed.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="f0bb2-153">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="f0bb2-153">Configuration Options</span></span>

<span data-ttu-id="f0bb2-154">Для LevelX во время компиляции можно настроить перечисленные ниже условные определения.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-154">LevelX can be configured at compile time via the conditional defines described below.</span></span> <span data-ttu-id="f0bb2-155">Чтобы использовать любой из этих параметров, просто добавьте требуемое определение в процесс компиляции исходного кода LevelX.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-155">Simply add the desired define to the compilation of each LevelX source to use the option.</span></span>

- <span data-ttu-id="f0bb2-156">**LX_DIRECT_READ**: если определен этот параметр, процедура чтения в драйвере флэш-памяти NOR обходится в пользу прямого чтения из памяти NOR, что дает значительное повышение производительности.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-156">**LX_DIRECT_READ**:  Defined, this option bypasses the NOR flash driver read routine in favor or reading the NOR memory directly, resulting in a significant performance increase.</span></span>
- <span data-ttu-id="f0bb2-157">**LX_FREE_SECTOR_DATA_VERIFY**: если определен этот параметр, экземпляр LevelX NOR использует "открытую логику" для проверки того, что все пустые секторы NOR состоят только из единиц.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-157">**LX_FREE_SECTOR_DATA_VERIFY**: Defined, this causes the LevelX NOR instance open logic to verify free NOR sectors are all ones.</span></span>
- <span data-ttu-id="f0bb2-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE**: определяет размер кэша для сопоставлений логических секторов. По умолчанию имеет значение 16.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE**:  By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="f0bb2-159">Более высокие значения повышают производительность, но увеличивают нагрузку на память.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-159">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="f0bb2-160">Этот размер не может быть меньше 8 и всегда должен быть степенью числа 2.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-160">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="f0bb2-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: если определен этот параметр, создается прямой кэш сопоставлений, например, для устранения промахов кэша.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: Defined, this creates a direct mapping cache, such that there are no cache misses.</span></span> <span data-ttu-id="f0bb2-162">Для этого требуется, чтобы LX_NAND_SECTOR_MAPPING_CACHE_SIZE был точно равен количеству страниц в устройстве флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-162">It also requires that LX_NAND_SECTOR_MAPPING_CACHE_SIZE represents the exact number of total pages in your flash device.</span></span>
- <span data-ttu-id="f0bb2-163">**LX_NOR_DISABLE_EXTENDED_CACHE**: если определен этот параметр, отключается расширенный кэш NOR.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-163">**LX_NOR_DISABLE_EXTENDED_CACHE**: Defined, this disabled the extended NOR cache.</span></span>
- <span data-ttu-id="f0bb2-164">**LX_NOR_EXTENDED_CACHE_SIZE**: по умолчанию имеет значение 8, что означает возможность кэшировать максимум 8 секторов для экземпляра NOR.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-164">**LX_NOR_EXTENDED_CACHE_SIZE**: By default this value is 8, which represents a maximum of 8 sectors that can be cached in a NOR instance.</span></span>
- <span data-ttu-id="f0bb2-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: определяет размер кэша для сопоставлений логических секторов. По умолчанию имеет значение 16.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="f0bb2-166">Более высокие значения повышают производительность, но увеличивают нагрузку на память.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-166">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="f0bb2-167">Этот размер не может быть меньше 8 и всегда должен быть степенью числа 2.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-167">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="f0bb2-168">**LX_THREAD_SAFE_ENABLE**: если определен этот параметр, LevelX обеспечивает потокобезопасность благодаря использованию объекта мьютекса ThreadX через соответствующий API.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-168">**LX_THREAD_SAFE_ENABLE**: Defined, this makes LevelX thread-safe by using a ThreadX mutex object throughout the API.</span></span>
- <span data-ttu-id="f0bb2-169">**LX_STANDALONE_ENABLE**: если этот параметр определен, он позволяет использовать LevelX в изолированном режиме (без ОСРВ Azure).</span><span class="sxs-lookup"><span data-stu-id="f0bb2-169">**LX_STANDALONE_ENABLE**: Defined, enables LevelX to be used in standalone mode (without Azure RTOS).</span></span> <span data-ttu-id="f0bb2-170">По умолчанию этот символ не определен.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-170">By default this symbol is not defined.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f0bb2-171">При использовании LevelX в автономном режиме (должен быть задан параметр **LX_STANDALONE_ENABLE**) файлы и библиотеки ThreadX не требуются.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-171">When using LevelX in Standalone mode (**LX_STANDALONE_ENABLE** must be defined), ThreadX files/libraries are not required.</span></span> <span data-ttu-id="f0bb2-172">В этом режиме функция потокобезопасного режима LevelX.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-172">LevelX thread-safe feature is disabled in this mode.</span></span>

## <a name="using-levelx"></a><span data-ttu-id="f0bb2-173">Использование LevelX</span><span class="sxs-lookup"><span data-stu-id="f0bb2-173">Using LevelX</span></span>

<span data-ttu-id="f0bb2-174">Чтобы использовать LevelX отдельно или в сочетании с FileX, включите файл \***lx_api.h** _ в код, который ссылается на API LevelX.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-174">To use LevelX, either by itself or with FileX, include the file \***lx_api.h** _ in the code that references the LevelX API.</span></span> <span data-ttu-id="f0bb2-175">Также обеспечьте доступность объектного кода LevelX во время компоновки.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-175">Also ensure that the LevelX object code is available at link time.</span></span> <span data-ttu-id="f0bb2-176">В файлах _*_demo_filex_nand_flash.c_*_ и _ *_demo_filex_nor_flash.c_*\* просмотрите примеры работы с LevelX.</span><span class="sxs-lookup"><span data-stu-id="f0bb2-176">Please examine the files _*_demo_filex_nand_flash.c_*_ and _ *_demo_filex_nor_flash.c_*\* for examples of how to use LevelX.</span></span>
