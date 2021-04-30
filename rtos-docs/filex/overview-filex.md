---
title: Основные сведения о FileX в ОСРВ Azure
description: FileX в ОСРВ Azure — это совместимая с FAT высокопроизводительная файловая система, полностью интегрированная с ThreadX в ОСРВ Azure и доступная для всех поддерживаемых процессоров. Как и ThreadX в ОСРВ Azure, FileX в ОСРВ Azure использует небольшой объем памяти и работает с высокой производительностью. Это делает решение идеальным для современных глубоко внедренных приложений, требующих операций управления файлами. FileX поддерживает большинство физических носителей, включая ОЗУ, USBX в ОСРВ Azure, SD-карты, а также флэш-память NAND или NOR с использованием LevelX в ОСРВ Azure.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: 0a54f160c96fb3e90c2295ae72020c121d367a12
ms.sourcegitcommit: 19d50693d8f5287ba6938ae1d23eef88435ed7b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2021
ms.locfileid: "108171359"
---
# <a name="overview-of-azure-rtos-filex"></a><span data-ttu-id="2e957-105">Общие сведения о FileX в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="2e957-105">Overview of Azure RTOS FileX</span></span>

<span data-ttu-id="2e957-106">Встроенная файловая система FileX в ОСРВ Azure — это современное решение промышленного уровня для форматов файлов Microsoft FAT, разработанное специально для глубоко встраиваемых приложений, приложений реального времени и Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="2e957-106">Azure RTOS FileX embedded file system is Azure RTOS's advanced, industrial grade solution for Microsoft FAT file formats, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="2e957-107">FileX в ОСРВ Azure поддерживает все форматы файлов Майкрософт, в том числе FAT12, FAT16, FAT32 и exFAT.</span><span class="sxs-lookup"><span data-stu-id="2e957-107">Azure RTOS FileX supports all of Microsoft’s file formats, including FAT12, FAT16, FAT32, and exFAT.</span></span> <span data-ttu-id="2e957-108">При необходимости FileX также обеспечивает отказоустойчивость и выравнивание износа флэш-памяти с помощью дополнительного продукта под названием [LevelX для ОСРВ Azure](https://docs.microsoft.com/azure/rtos/levelx/).</span><span class="sxs-lookup"><span data-stu-id="2e957-108">FileX also offers optional fault tolerance and FLASH wear leveling via an add-on product called [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span></span> <span data-ttu-id="2e957-109">В сочетании с небольшими требованиями к ресурсам, высокой производительностью и непревзойденной простотой использования FileX для ОСРВ Azure является идеальным выбором при использовании самых требовательных внедренных приложений Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="2e957-109">All of this combined with a small footprint, fast execution, and superior ease-of-use, make Azure RTOS FileX the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="2e957-110">Протоколы API</span><span class="sxs-lookup"><span data-stu-id="2e957-110">API protocols</span></span>

### <a name="media-services"></a><span data-ttu-id="2e957-111">Службы мультимедиа</span><span class="sxs-lookup"><span data-stu-id="2e957-111">Media Services</span></span>

- <span data-ttu-id="2e957-112">Поддержка FAT12, FAT16, FAT32 и exFAT</span><span class="sxs-lookup"><span data-stu-id="2e957-112">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="2e957-113">Минимальный размер флэш-памяти 6 КБ, ОЗУ 2,5 КБ</span><span class="sxs-lookup"><span data-stu-id="2e957-113">Minimal 6KB FLASH, 2.5KB RAM</span></span>
- <span data-ttu-id="2e957-114">Полный набор служб доступа к носителям</span><span class="sxs-lookup"><span data-stu-id="2e957-114">Complete media access services</span></span>
- <span data-ttu-id="2e957-115">Неограниченное число экземпляров носителей</span><span class="sxs-lookup"><span data-stu-id="2e957-115">Unlimited number of media instance</span></span>
- <span data-ttu-id="2e957-116">Простой интерфейс драйвера для чтения и записи логических секторов</span><span class="sxs-lookup"><span data-stu-id="2e957-116">Simple read/write logical sector driver interface</span></span>
- <span data-ttu-id="2e957-117">Поддержка нескольких разделов</span><span class="sxs-lookup"><span data-stu-id="2e957-117">Multiple partition support</span></span>
- <span data-ttu-id="2e957-118">Кэш логических секторов</span><span class="sxs-lookup"><span data-stu-id="2e957-118">Logical sector cache</span></span>
- <span data-ttu-id="2e957-119">Кэш записей FAT</span><span class="sxs-lookup"><span data-stu-id="2e957-119">FAT entry cache</span></span>
- <span data-ttu-id="2e957-120">Дополнительная поддержка отказоустойчивости</span><span class="sxs-lookup"><span data-stu-id="2e957-120">Optional fault tolerance support</span></span>
- <span data-ttu-id="2e957-121">Отложенное обновление дополнительной системы FAT</span><span class="sxs-lookup"><span data-stu-id="2e957-121">Deferred Secondary FAT update</span></span>
- <span data-ttu-id="2e957-122">Трассировка на уровне системы через TraceX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="2e957-122">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="2e957-123">Интуитивно понятные интерфейсы API для доступа к носителям, включая следующие:</span><span class="sxs-lookup"><span data-stu-id="2e957-123">Intuitive media access APIs, including:</span></span>
  - <span data-ttu-id="2e957-124">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="2e957-124">fx_media_open</span></span>
  - <span data-ttu-id="2e957-125">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="2e957-125">fx_media_close</span></span>
  - <span data-ttu-id="2e957-126">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="2e957-126">fx_media_format</span></span>
  - <span data-ttu-id="2e957-127">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="2e957-127">fx_media_space_available</span></span>

### <a name="directory-services"></a><span data-ttu-id="2e957-128">Служба каталогов</span><span class="sxs-lookup"><span data-stu-id="2e957-128">Directory Services</span></span>

- <span data-ttu-id="2e957-129">До 256 байтовых путей</span><span class="sxs-lookup"><span data-stu-id="2e957-129">Up to 256 byte paths</span></span>
- <span data-ttu-id="2e957-130">Поддерживаются длинные имена каталогов и имена версии 8.3</span><span class="sxs-lookup"><span data-stu-id="2e957-130">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="2e957-131">Создание и удаление каталогов</span><span class="sxs-lookup"><span data-stu-id="2e957-131">Directory create & delete</span></span>
- <span data-ttu-id="2e957-132">Навигация по каталогам и их обход</span><span class="sxs-lookup"><span data-stu-id="2e957-132">Directory navigation and traversal</span></span>
- <span data-ttu-id="2e957-133">Управление атрибутами каталога</span><span class="sxs-lookup"><span data-stu-id="2e957-133">Directory attributes management</span></span>
- <span data-ttu-id="2e957-134">Трассировка на уровне системы через TraceX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="2e957-134">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="2e957-135">Интуитивно понятные интерфейсы API доступа к каталогам, включая следующие:</span><span class="sxs-lookup"><span data-stu-id="2e957-135">Intuitive directory access APIs, including:</span></span>
  - <span data-ttu-id="2e957-136">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="2e957-136">fx_directory_create</span></span>
  - <span data-ttu-id="2e957-137">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="2e957-137">fx_directory_delete</span></span>
  - <span data-ttu-id="2e957-138">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2e957-138">fx_directory_attributes_set</span></span>
  - <span data-ttu-id="2e957-139">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2e957-139">fx_directory_attributes_read</span></span>
  - <span data-ttu-id="2e957-140">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="2e957-140">fx_directory_first_entry_find</span></span>
  - <span data-ttu-id="2e957-141">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="2e957-141">fx_directory_next_entry_find</span></span>

### <a name="file-services"></a><span data-ttu-id="2e957-142">Файловые службы</span><span class="sxs-lookup"><span data-stu-id="2e957-142">File Services</span></span>

- <span data-ttu-id="2e957-143">Минимальный размер флэш-памяти 3,3 КБ</span><span class="sxs-lookup"><span data-stu-id="2e957-143">Minimal 3.3KB FLASH</span></span>
- <span data-ttu-id="2e957-144">Неограниченное число открытых файлов</span><span class="sxs-lookup"><span data-stu-id="2e957-144">Unlimited open files</span></span>
- <span data-ttu-id="2e957-145">Файлы, доступные только для чтения, можно открывать несколько раз</span><span class="sxs-lookup"><span data-stu-id="2e957-145">Read-only files can be opened multiple times</span></span>
- <span data-ttu-id="2e957-146">Поддерживаются длинные имена каталогов и имена версии 8.3</span><span class="sxs-lookup"><span data-stu-id="2e957-146">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="2e957-147">Поддержка смежных файлов</span><span class="sxs-lookup"><span data-stu-id="2e957-147">Contiguous file support</span></span>
- <span data-ttu-id="2e957-148">Логика быстрого поиска</span><span class="sxs-lookup"><span data-stu-id="2e957-148">Fast seek logic</span></span>
- <span data-ttu-id="2e957-149">Предварительное выделение кластеров</span><span class="sxs-lookup"><span data-stu-id="2e957-149">Pre-allocation of clusters</span></span>
- <span data-ttu-id="2e957-150">Создание, удаление и переименование файлов</span><span class="sxs-lookup"><span data-stu-id="2e957-150">File create, delete, and rename</span></span>
- <span data-ttu-id="2e957-151">Чтение, запись и просмотр файлов</span><span class="sxs-lookup"><span data-stu-id="2e957-151">File read, write, and see</span></span>
- <span data-ttu-id="2e957-152">Управление атрибутами файлов</span><span class="sxs-lookup"><span data-stu-id="2e957-152">File attributes management</span></span>
- <span data-ttu-id="2e957-153">Трассировка на уровне системы через TraceX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="2e957-153">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="2e957-154">Интуитивно понятные интерфейсы API для доступа к файлам, включая следующие:</span><span class="sxs-lookup"><span data-stu-id="2e957-154">Intuitive file access APIs, including:</span></span>
  - <span data-ttu-id="2e957-155">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="2e957-155">fx_file_create</span></span>
  - <span data-ttu-id="2e957-156">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="2e957-156">fx_file_delete</span></span>
  - <span data-ttu-id="2e957-157">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="2e957-157">fx_file_attributes_set</span></span>
  - <span data-ttu-id="2e957-158">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="2e957-158">fx_file_attributes_read</span></span>
  - <span data-ttu-id="2e957-159">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="2e957-159">fx_file_read</span></span>
  - <span data-ttu-id="2e957-160">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="2e957-160">fx_file_seek</span></span>
  - <span data-ttu-id="2e957-161">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="2e957-161">fx_file_write</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="2e957-162">Усовершенствованные технологии</span><span class="sxs-lookup"><span data-stu-id="2e957-162">Advanced technology</span></span>

<span data-ttu-id="2e957-163">FileX в ОСРВ Azure — это современная технология, включающая указанные ниже возможности.</span><span class="sxs-lookup"><span data-stu-id="2e957-163">Azure RTOS FileX is advanced technology, including the following.</span></span>

- <span data-ttu-id="2e957-164">Поддержка FAT12, FAT16, FAT32 и exFAT</span><span class="sxs-lookup"><span data-stu-id="2e957-164">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="2e957-165">Поддержка нескольких разделов</span><span class="sxs-lookup"><span data-stu-id="2e957-165">Multiple partition support</span></span>
- <span data-ttu-id="2e957-166">Автоматическое масштабирование</span><span class="sxs-lookup"><span data-stu-id="2e957-166">Automatic scaling</span></span>
- <span data-ttu-id="2e957-167">Независимость от порядка байтов</span><span class="sxs-lookup"><span data-stu-id="2e957-167">Endian neutral</span></span>
- <span data-ttu-id="2e957-168">Поддержка длинных имен файлов и имен версии 8.3</span><span class="sxs-lookup"><span data-stu-id="2e957-168">Long file name and 8.3 support</span></span>
- <span data-ttu-id="2e957-169">Дополнительная поддержка отказоустойчивости</span><span class="sxs-lookup"><span data-stu-id="2e957-169">Optional fault tolerance support</span></span>
- <span data-ttu-id="2e957-170">Кэш логических секторов</span><span class="sxs-lookup"><span data-stu-id="2e957-170">Logical sector cache</span></span>
- <span data-ttu-id="2e957-171">Кэш записей FAT</span><span class="sxs-lookup"><span data-stu-id="2e957-171">FAT entry cache</span></span>
- <span data-ttu-id="2e957-172">Предварительное выделение кластеров</span><span class="sxs-lookup"><span data-stu-id="2e957-172">Pre-allocation of clusters</span></span>
- <span data-ttu-id="2e957-173">Поддержка смежных файлов</span><span class="sxs-lookup"><span data-stu-id="2e957-173">Contiguous file support</span></span>
- <span data-ttu-id="2e957-174">Дополнительные метрики производительности</span><span class="sxs-lookup"><span data-stu-id="2e957-174">Optional performance metrics</span></span>
- <span data-ttu-id="2e957-175">Поддержка системного анализа TraceX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="2e957-175">Azure RTOS TraceX system analysis support</span></span>

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a><span data-ttu-id="2e957-176">Выравнивание износа NOR/NAND (LevelX в ОСРВ Azure)</span><span class="sxs-lookup"><span data-stu-id="2e957-176">NOR/NAND Wear Leveling (Azure RTOS LevelX)</span></span>

<span data-ttu-id="2e957-177">LevelX в ОСРВ Azure — это решение Майкрософт для выравнивания износа флэш-памяти NOR/NAND.</span><span class="sxs-lookup"><span data-stu-id="2e957-177">Azure RTOS LevelX is Microsoft’s NOR/NAND FLASH wear leveling product.</span></span> <span data-ttu-id="2e957-178">LevelX в ОСРВ Azure можно использовать в сочетании с FileX или как отдельную библиотеку для прямого чтения и записи секторов флэш-памяти в приложении.</span><span class="sxs-lookup"><span data-stu-id="2e957-178">Azure RTOS LevelX can be used in conjunction with FileX or as a stand-alone, direct read/write FLASH sector library for the application.</span></span>
