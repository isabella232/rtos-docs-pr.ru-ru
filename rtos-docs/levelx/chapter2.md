---
title: Глава 2. Установка и использование LevelX для ОСРВ Azure
description: Установка и использование LevelX очень просты. Все необходимые процессы описываются в следующих разделах этой главы.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 575776875452cfc718401556a6440d787cb18893
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815431"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-levelx"></a><span data-ttu-id="4320e-103">Глава 2. Установка и использование LevelX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="4320e-103">Chapter 2 - Installation and use of Azure RTOS LevelX</span></span>

<span data-ttu-id="4320e-104">Установка и использование LevelX для ОСРВ Azure очень проста. Все необходимые процессы описываются в следующих разделах этой главы.</span><span class="sxs-lookup"><span data-stu-id="4320e-104">Installation and use of Azure RTOS LevelX is straightforward and described in the following sections of this chapter.</span></span>

## <a name="distribution"></a><span data-ttu-id="4320e-105">Distribution</span><span class="sxs-lookup"><span data-stu-id="4320e-105">Distribution</span></span>

<span data-ttu-id="4320e-106">LevelX распространяется в формате ANSI на C, где каждая функция содержится в отдельном файле C.</span><span class="sxs-lookup"><span data-stu-id="4320e-106">LevelX is distributed in ANSI C where each function is contained in its own separate C file.</span></span> <span data-ttu-id="4320e-107">Ниже перечислены файлы, входящие в дистрибутив LevelX.</span><span class="sxs-lookup"><span data-stu-id="4320e-107">The files in the LevelX distribution are as follows.</span></span>
- <span data-ttu-id="4320e-108">lx_api.h</span><span class="sxs-lookup"><span data-stu-id="4320e-108">lx_api.h</span></span>
- <span data-ttu-id="4320e-109">lx_nand_flash_256byte_ecc_check.c</span><span class="sxs-lookup"><span data-stu-id="4320e-109">lx_nand_flash_256byte_ecc_check.c</span></span>
- <span data-ttu-id="4320e-110">lx_nand_flash_256byte_ecc_compute.c</span><span class="sxs-lookup"><span data-stu-id="4320e-110">lx_nand_flash_256byte_ecc_compute.c</span></span>
- <span data-ttu-id="4320e-111">lx_nand_flash_block_full_update.c</span><span class="sxs-lookup"><span data-stu-id="4320e-111">lx_nand_flash_block_full_update.c</span></span>
- <span data-ttu-id="4320e-112">lx_nand_flash_block_reclaim.c</span><span class="sxs-lookup"><span data-stu-id="4320e-112">lx_nand_flash_block_reclaim.c</span></span>
- <span data-ttu-id="4320e-113">lx_nand_flash_close.c</span><span class="sxs-lookup"><span data-stu-id="4320e-113">lx_nand_flash_close.c</span></span>
- <span data-ttu-id="4320e-114">lx_nand_flash_defragment.c</span><span class="sxs-lookup"><span data-stu-id="4320e-114">lx_nand_flash_defragment.c</span></span>  
- <span data-ttu-id="4320e-115">lx_nand_flash_extended_cache_enable.c</span><span class="sxs-lookup"><span data-stu-id="4320e-115">lx_nand_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="4320e-116">lx_nand_flash_initialize.c</span><span class="sxs-lookup"><span data-stu-id="4320e-116">lx_nand_flash_initialize.c</span></span>
- <span data-ttu-id="4320e-117">lx_nand_flash_logical_sector_find.c</span><span class="sxs-lookup"><span data-stu-id="4320e-117">lx_nand_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="4320e-118">lx_nand_flash_next_block_to_erase_find.c</span><span class="sxs-lookup"><span data-stu-id="4320e-118">lx_nand_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="4320e-119">lx_nand_flash_open.c</span><span class="sxs-lookup"><span data-stu-id="4320e-119">lx_nand_flash_open.c</span></span>
- <span data-ttu-id="4320e-120">lx_nand_flash_page_ecc_check.c</span><span class="sxs-lookup"><span data-stu-id="4320e-120">lx_nand_flash_page_ecc_check.c</span></span>
- <span data-ttu-id="4320e-121">lx_nand_flash_page_ecc_compute.c</span><span class="sxs-lookup"><span data-stu-id="4320e-121">lx_nand_flash_page_ecc_compute.c</span></span>  
- <span data-ttu-id="4320e-122">lx_nand_flash_partial_defragment.c</span><span class="sxs-lookup"><span data-stu-id="4320e-122">lx_nand_flash_partial_defragment.c</span></span>
- <span data-ttu-id="4320e-123">lx_nand_flash_physical_page_allocate.c</span><span class="sxs-lookup"><span data-stu-id="4320e-123">lx_nand_flash_physical_page_allocate.c</span></span>
- <span data-ttu-id="4320e-124">lx_nand_flash_sector_mapping_cache_invalidate.c</span><span class="sxs-lookup"><span data-stu-id="4320e-124">lx_nand_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="4320e-125">lx_nand_flash_sector_read.c</span><span class="sxs-lookup"><span data-stu-id="4320e-125">lx_nand_flash_sector_read.c</span></span>
- <span data-ttu-id="4320e-126">lx_nand_flash_sector_release.c</span><span class="sxs-lookup"><span data-stu-id="4320e-126">lx_nand_flash_sector_release.c</span></span>
- <span data-ttu-id="4320e-127">lx_nand_flash_sector_write.c</span><span class="sxs-lookup"><span data-stu-id="4320e-127">lx_nand_flash_sector_write.c</span></span>
- <span data-ttu-id="4320e-128">lx_nand_flash_system_error.c</span><span class="sxs-lookup"><span data-stu-id="4320e-128">lx_nand_flash_system_error.c</span></span>
- <span data-ttu-id="4320e-129">lx_nor_flash_block_reclaim.c</span><span class="sxs-lookup"><span data-stu-id="4320e-129">lx_nor_flash_block_reclaim.c</span></span>
- <span data-ttu-id="4320e-130">lx_nor_flash_close.c</span><span class="sxs-lookup"><span data-stu-id="4320e-130">lx_nor_flash_close.c</span></span>
- <span data-ttu-id="4320e-131">lx_nor_flash_defragment.c</span><span class="sxs-lookup"><span data-stu-id="4320e-131">lx_nor_flash_defragment.c</span></span>  
- <span data-ttu-id="4320e-132">lx_nor_flash_extended_cache_enable.c</span><span class="sxs-lookup"><span data-stu-id="4320e-132">lx_nor_flash_extended_cache_enable.c</span></span>
- <span data-ttu-id="4320e-133">lx_nor_flash_initialize.c</span><span class="sxs-lookup"><span data-stu-id="4320e-133">lx_nor_flash_initialize.c</span></span>
- <span data-ttu-id="4320e-134">lx_nor_flash_logical_sector_find.c</span><span class="sxs-lookup"><span data-stu-id="4320e-134">lx_nor_flash_logical_sector_find.c</span></span>
- <span data-ttu-id="4320e-135">lx_nor_flash_next_block_to_erase_find.c</span><span class="sxs-lookup"><span data-stu-id="4320e-135">lx_nor_flash_next_block_to_erase_find.c</span></span>
- <span data-ttu-id="4320e-136">lx_nor_flash_open.c</span><span class="sxs-lookup"><span data-stu-id="4320e-136">lx_nor_flash_open.c</span></span>
- <span data-ttu-id="4320e-137">lx_nor_flash_partial_defragment.c</span><span class="sxs-lookup"><span data-stu-id="4320e-137">lx_nor_flash_partial_defragment.c</span></span>
- <span data-ttu-id="4320e-138">lx_nor_flash_physical_sector_allocate.c</span><span class="sxs-lookup"><span data-stu-id="4320e-138">lx_nor_flash_physical_sector_allocate.c</span></span>
- <span data-ttu-id="4320e-139">lx_nor_flash_sector_mapping_cache_invalidate.c</span><span class="sxs-lookup"><span data-stu-id="4320e-139">lx_nor_flash_sector_mapping_cache_invalidate.c</span></span>
- <span data-ttu-id="4320e-140">lx_nor_flash_sector_read.c</span><span class="sxs-lookup"><span data-stu-id="4320e-140">lx_nor_flash_sector_read.c</span></span>
- <span data-ttu-id="4320e-141">lx_nor_flash_sector_release.c</span><span class="sxs-lookup"><span data-stu-id="4320e-141">lx_nor_flash_sector_release.c</span></span>
- <span data-ttu-id="4320e-142">lx_nor_flash_sector_write.c</span><span class="sxs-lookup"><span data-stu-id="4320e-142">lx_nor_flash_sector_write.c</span></span>
- <span data-ttu-id="4320e-143">lx_nor_flash_system_error.c</span><span class="sxs-lookup"><span data-stu-id="4320e-143">lx_nor_flash_system_error.c</span></span>

<span data-ttu-id="4320e-144">Существуют также симуляторы и примеры драйверов FileX для работы экземпляров LevelX с флэш-памятью NAND и NOR, которые перечислены ниже.</span><span class="sxs-lookup"><span data-stu-id="4320e-144">There are also simulator and FileX driver samples for both LevelX NAND and NOR instances, as follows.</span></span>

- <span data-ttu-id="4320e-145">demo_filex_nand_flash.c</span><span class="sxs-lookup"><span data-stu-id="4320e-145">demo_filex_nand_flash.c</span></span>  
- <span data-ttu-id="4320e-146">fx_nand_flash_simulated_driver.c</span><span class="sxs-lookup"><span data-stu-id="4320e-146">fx_nand_flash_simulated_driver.c</span></span>
- <span data-ttu-id="4320e-147">lx_nand_flash_simulator.c</span><span class="sxs-lookup"><span data-stu-id="4320e-147">lx_nand_flash_simulator.c</span></span>
- <span data-ttu-id="4320e-148">demo_filex_nor_flash.c</span><span class="sxs-lookup"><span data-stu-id="4320e-148">demo_filex_nor_flash.c</span></span>  
- <span data-ttu-id="4320e-149">fx_nor_flash_simulated_driver.c</span><span class="sxs-lookup"><span data-stu-id="4320e-149">fx_nor_flash_simulated_driver.c</span></span>
- <span data-ttu-id="4320e-150">lx_nor_flash_simulator.c</span><span class="sxs-lookup"><span data-stu-id="4320e-150">lx_nor_flash_simulator.c</span></span>

<span data-ttu-id="4320e-151">Конечно, если вам нужна только флэш-память NAND, достаточно использовать файлы LevelX для NAND (***lx_nand_\*.c***).</span><span class="sxs-lookup"><span data-stu-id="4320e-151">Of course, if only NAND flash is required, only the LevelX NAND flash files (***lx_nand_\*.c***) are needed.</span></span> <span data-ttu-id="4320e-152">Аналогично, если нужна только флэш-память NOR, достаточно использовать файлы LevelX для NOR (\*\*_lx_nor_\_.c\*\*\*).</span><span class="sxs-lookup"><span data-stu-id="4320e-152">Similarly, if only NOR flash is required, only the NOR flash files (\*\*_lx_nor_\_.c\*\*\*) are needed.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="4320e-153">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="4320e-153">Configuration Options</span></span>

<span data-ttu-id="4320e-154">Для LevelX во время компиляции можно настроить перечисленные ниже условные определения.</span><span class="sxs-lookup"><span data-stu-id="4320e-154">LevelX can be configured at compile time via the conditional defines described below.</span></span> <span data-ttu-id="4320e-155">Чтобы использовать любой из этих параметров, просто добавьте требуемое определение в процесс компиляции исходного кода LevelX.</span><span class="sxs-lookup"><span data-stu-id="4320e-155">Simply add the desired define to the compilation of each LevelX source to use the option.</span></span>

- <span data-ttu-id="4320e-156">**LX_DIRECT_READ**: если определен этот параметр, процедура чтения в драйвере флэш-памяти NOR обходится в пользу прямого чтения из памяти NOR, что дает значительное повышение производительности.</span><span class="sxs-lookup"><span data-stu-id="4320e-156">**LX_DIRECT_READ**:  Defined, this option bypasses the NOR flash driver read routine in favor or reading the NOR memory directly, resulting in a significant performance increase.</span></span>
- <span data-ttu-id="4320e-157">**LX_FREE_SECTOR_DATA_VERIFY**: если определен этот параметр, экземпляр LevelX NOR использует "открытую логику" для проверки того, что все пустые секторы NOR состоят только из единиц.</span><span class="sxs-lookup"><span data-stu-id="4320e-157">**LX_FREE_SECTOR_DATA_VERIFY**: Defined, this causes the LevelX NOR instance open logic to verify free NOR sectors are all ones.</span></span>
- <span data-ttu-id="4320e-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE**: определяет размер кэша для сопоставлений логических секторов. По умолчанию имеет значение 16.</span><span class="sxs-lookup"><span data-stu-id="4320e-158">**LX_NAND_SECTOR_MAPPING_CACHE_SIZE**:  By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="4320e-159">Более высокие значения повышают производительность, но увеличивают нагрузку на память.</span><span class="sxs-lookup"><span data-stu-id="4320e-159">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="4320e-160">Этот размер не может быть меньше 8 и всегда должен быть степенью числа 2.</span><span class="sxs-lookup"><span data-stu-id="4320e-160">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="4320e-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: если определен этот параметр, создается прямой кэш сопоставлений, например, для устранения промахов кэша.</span><span class="sxs-lookup"><span data-stu-id="4320e-161">**LX_NAND_FLASH_DIRECT_MAPPING_CACHE**: Defined, this creates a direct mapping cache, such that there are no cache misses.</span></span> <span data-ttu-id="4320e-162">Для этого требуется, чтобы LX_NAND_SECTOR_MAPPING_CACHE_SIZE был точно равен количеству страниц в устройстве флэш-памяти.</span><span class="sxs-lookup"><span data-stu-id="4320e-162">It also requires that LX_NAND_SECTOR_MAPPING_CACHE_SIZE represents the exact number of total pages in your flash device.</span></span>
- <span data-ttu-id="4320e-163">**LX_NOR_DISABLE_EXTENDED_CACHE**: если определен этот параметр, отключается расширенный кэш NOR.</span><span class="sxs-lookup"><span data-stu-id="4320e-163">**LX_NOR_DISABLE_EXTENDED_CACHE**: Defined, this disabled the extended NOR cache.</span></span>
- <span data-ttu-id="4320e-164">**LX_NOR_EXTENDED_CACHE_SIZE**: по умолчанию имеет значение 8, что означает возможность кэшировать максимум 8 секторов для экземпляра NOR.</span><span class="sxs-lookup"><span data-stu-id="4320e-164">**LX_NOR_EXTENDED_CACHE_SIZE**: By default this value is 8, which represents a maximum of 8 sectors that can be cached in a NOR instance.</span></span>
- <span data-ttu-id="4320e-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: определяет размер кэша для сопоставлений логических секторов. По умолчанию имеет значение 16.</span><span class="sxs-lookup"><span data-stu-id="4320e-165">**LX_NOR_SECTOR_MAPPING_CACHE_SIZE**: By default this value is 16 and defines the logical sector mapping cache size.</span></span> <span data-ttu-id="4320e-166">Более высокие значения повышают производительность, но увеличивают нагрузку на память.</span><span class="sxs-lookup"><span data-stu-id="4320e-166">Large values improve performance, but cost memory.</span></span> <span data-ttu-id="4320e-167">Этот размер не может быть меньше 8 и всегда должен быть степенью числа 2.</span><span class="sxs-lookup"><span data-stu-id="4320e-167">The minimum size is 8 and all values must be a power of 2.</span></span>
- <span data-ttu-id="4320e-168">**LX_THREAD_SAFE_ENABLE**: если определен этот параметр, LevelX обеспечивает потокобезопасность благодаря использованию объекта мьютекса ThreadX через соответствующий API.</span><span class="sxs-lookup"><span data-stu-id="4320e-168">**LX_THREAD_SAFE_ENABLE**: Defined, this makes LevelX thread-safe by using a ThreadX mutex object throughout the API.</span></span>

## <a name="using-levelx"></a><span data-ttu-id="4320e-169">Использование LevelX</span><span class="sxs-lookup"><span data-stu-id="4320e-169">Using LevelX</span></span>

<span data-ttu-id="4320e-170">Чтобы использовать LevelX отдельно или в сочетании с FileX, включите файл \***lx_api.h** _ в код, который ссылается на API LevelX.</span><span class="sxs-lookup"><span data-stu-id="4320e-170">To use LevelX, either by itself or with FileX, include the file \***lx_api.h** _ in the code that references the LevelX API.</span></span> <span data-ttu-id="4320e-171">Также обеспечьте доступность объектного кода LevelX во время компоновки.</span><span class="sxs-lookup"><span data-stu-id="4320e-171">Also ensure that the LevelX object code is available at link time.</span></span> <span data-ttu-id="4320e-172">В файлах _*_demo_filex_nand_flash.c_*_ и _ *_demo_filex_nor_flash.c_*\* просмотрите примеры работы с LevelX.</span><span class="sxs-lookup"><span data-stu-id="4320e-172">Please examine the files _*_demo_filex_nand_flash.c_*_ and _ *_demo_filex_nor_flash.c_*\* for examples of how to use LevelX.</span></span>
