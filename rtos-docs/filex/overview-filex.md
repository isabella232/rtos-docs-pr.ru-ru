---
title: Основные сведения о FileX в ОСРВ Azure
description: FileX в ОСРВ Azure — это совместимая с FAT высокопроизводительная файловая система, полностью интегрированная с ThreadX в ОСРВ Azure и доступная для всех поддерживаемых процессоров. Как и ThreadX в ОСРВ Azure, FileX в ОСРВ Azure использует небольшой объем памяти и работает с высокой производительностью. Это делает решение идеальным для современных глубоко внедренных приложений, требующих операций управления файлами. FileX поддерживает большинство физических носителей, включая ОЗУ, USBX в ОСРВ Azure, SD-карты, а также флэш-память NAND или NOR с использованием LevelX в ОСРВ Azure.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.service: rtos
ms.topic: overview
ms.openlocfilehash: a3a20c8ced3426399ceedf6994c872ce7aec93c3
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104815600"
---
# <a name="overview-of-azure-rtos-filex"></a><span data-ttu-id="677b4-105">Общие сведения о FileX в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="677b4-105">Overview of Azure RTOS FileX</span></span>

<span data-ttu-id="677b4-106">Встроенная файловая система FileX в ОСРВ Azure — это современное решение промышленного уровня для форматов файлов Microsoft FAT, разработанное специально для глубоко встраиваемых приложений, приложений реального времени и Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="677b4-106">Azure RTOS FileX embedded file system is Azure RTOS's advanced, industrial grade solution for Microsoft FAT file formats, designed specifically for deeply embedded, real-time, and IoT applications.</span></span> <span data-ttu-id="677b4-107">FileX в ОСРВ Azure поддерживает все форматы файлов Майкрософт, в том числе FAT12, FAT16, FAT32 и exFAT.</span><span class="sxs-lookup"><span data-stu-id="677b4-107">Azure RTOS FileX supports all of Microsoft’s file formats, including FAT12, FAT16, FAT32, and exFAT.</span></span> <span data-ttu-id="677b4-108">При необходимости FileX также обеспечивает отказоустойчивость и выравнивание износа флэш-памяти с помощью дополнительного продукта под названием [LevelX для ОСРВ Azure](https://docs.microsoft.com/azure/rtos/levelx/).</span><span class="sxs-lookup"><span data-stu-id="677b4-108">FileX also offers optional fault tolerance and FLASH wear leveling via an add-on product called [Azure RTOS LevelX](https://docs.microsoft.com/azure/rtos/levelx/).</span></span> <span data-ttu-id="677b4-109">В сочетании с небольшими требованиями к ресурсам, высокой производительностью и непревзойденной простотой использования FileX для ОСРВ Azure является идеальным выбором при использовании самых требовательных внедренных приложений Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="677b4-109">All of this combined with a small footprint, fast execution, and superior ease-of-use, make Azure RTOS FileX the ideal choice for the most demanding embedded IoT applications.</span></span>

## <a name="api-protocols"></a><span data-ttu-id="677b4-110">Протоколы API</span><span class="sxs-lookup"><span data-stu-id="677b4-110">API protocols</span></span>

### <a name="azure-rtos-filex-api"></a><span data-ttu-id="677b4-111">API FileX в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="677b4-111">Azure RTOS FileX API</span></span>

- <span data-ttu-id="677b4-112">Интуитивно понятный и согласованный API</span><span class="sxs-lookup"><span data-stu-id="677b4-112">Intuitive and consistent API</span></span>
- <span data-ttu-id="677b4-113">Соглашение об именовании с использованием конструкции "существительное — глагол"</span><span class="sxs-lookup"><span data-stu-id="677b4-113">Noun-verb naming convention</span></span>
- <span data-ttu-id="677b4-114">Названия всех интерфейсов API начинаются с *fx_* , благодаря чему легко установить их принадлежность к FileX.</span><span class="sxs-lookup"><span data-stu-id="677b4-114">All APIs have leading *fx_* to easily identify as FileX</span></span>
- <span data-ttu-id="677b4-115">Блокирующие API поддерживают опциональное время ожидания потоков.</span><span class="sxs-lookup"><span data-stu-id="677b4-115">Blocking APIs have optional thread timeout</span></span>
- <span data-ttu-id="677b4-116">Необязательные обратные вызовы уведомления пользователя для операций с мультимедийными объектами и файлами.</span><span class="sxs-lookup"><span data-stu-id="677b4-116">Optional user-notification callbacks for media and file operations</span></span>
- <span data-ttu-id="677b4-117">Дополнительные сведения см. в [руководстве пользователя FileX в ОСРВ Azure](about-this-guide.md).</span><span class="sxs-lookup"><span data-stu-id="677b4-117">Please see [Azure RTOS FileX User Guide](about-this-guide.md) for more details</span></span>

### <a name="media-services"></a><span data-ttu-id="677b4-118">Службы мультимедиа</span><span class="sxs-lookup"><span data-stu-id="677b4-118">Media Services</span></span>

- <span data-ttu-id="677b4-119">Поддержка FAT12, FAT16, FAT32 и exFAT</span><span class="sxs-lookup"><span data-stu-id="677b4-119">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="677b4-120">Минимальный размер флэш-памяти 6 КБ, ОЗУ 2,5 КБ</span><span class="sxs-lookup"><span data-stu-id="677b4-120">Minimal 6KB FLASH, 2.5KB RAM</span></span>
- <span data-ttu-id="677b4-121">Полный набор служб доступа к носителям</span><span class="sxs-lookup"><span data-stu-id="677b4-121">Complete media access services</span></span>
- <span data-ttu-id="677b4-122">Неограниченное число экземпляров носителей</span><span class="sxs-lookup"><span data-stu-id="677b4-122">Unlimited number of media instance</span></span>
- <span data-ttu-id="677b4-123">Простой интерфейс драйвера для чтения и записи логических секторов</span><span class="sxs-lookup"><span data-stu-id="677b4-123">Simple read/write logical sector driver interface</span></span>
- <span data-ttu-id="677b4-124">Поддержка нескольких разделов</span><span class="sxs-lookup"><span data-stu-id="677b4-124">Multiple partition support</span></span>
- <span data-ttu-id="677b4-125">Кэш логических секторов</span><span class="sxs-lookup"><span data-stu-id="677b4-125">Logical sector cache</span></span>
- <span data-ttu-id="677b4-126">Кэш записей FAT</span><span class="sxs-lookup"><span data-stu-id="677b4-126">FAT entry cache</span></span>
- <span data-ttu-id="677b4-127">Дополнительная поддержка отказоустойчивости</span><span class="sxs-lookup"><span data-stu-id="677b4-127">Optional fault tolerance support</span></span>
- <span data-ttu-id="677b4-128">Отложенное обновление дополнительной системы FAT</span><span class="sxs-lookup"><span data-stu-id="677b4-128">Deferred Secondary FAT update</span></span>
- <span data-ttu-id="677b4-129">Трассировка на уровне системы через TraceX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="677b4-129">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="677b4-130">Интуитивно понятные интерфейсы API для доступа к носителям, включая следующие:</span><span class="sxs-lookup"><span data-stu-id="677b4-130">Intuitive media access APIs, including:</span></span>
  - <span data-ttu-id="677b4-131">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="677b4-131">fx_media_open</span></span>
  - <span data-ttu-id="677b4-132">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="677b4-132">fx_media_close</span></span>
  - <span data-ttu-id="677b4-133">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="677b4-133">fx_media_format</span></span>
  - <span data-ttu-id="677b4-134">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="677b4-134">fx_media_space_available</span></span>

### <a name="directory-services"></a><span data-ttu-id="677b4-135">Служба каталогов</span><span class="sxs-lookup"><span data-stu-id="677b4-135">Directory Services</span></span>

- <span data-ttu-id="677b4-136">До 256 байтовых путей</span><span class="sxs-lookup"><span data-stu-id="677b4-136">Up to 256 byte paths</span></span>
- <span data-ttu-id="677b4-137">Поддерживаются длинные имена каталогов и имена версии 8.3</span><span class="sxs-lookup"><span data-stu-id="677b4-137">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="677b4-138">Создание и удаление каталогов</span><span class="sxs-lookup"><span data-stu-id="677b4-138">Directory create & delete</span></span>
- <span data-ttu-id="677b4-139">Навигация по каталогам и их обход</span><span class="sxs-lookup"><span data-stu-id="677b4-139">Directory navigation and traversal</span></span>
- <span data-ttu-id="677b4-140">Управление атрибутами каталога</span><span class="sxs-lookup"><span data-stu-id="677b4-140">Directory attributes management</span></span>
- <span data-ttu-id="677b4-141">Трассировка на уровне системы через TraceX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="677b4-141">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="677b4-142">Интуитивно понятные интерфейсы API доступа к каталогам, включая следующие:</span><span class="sxs-lookup"><span data-stu-id="677b4-142">Intuitive directory access APIs, including:</span></span>
  - <span data-ttu-id="677b4-143">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="677b4-143">fx_directory_create</span></span>
  - <span data-ttu-id="677b4-144">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="677b4-144">fx_directory_delete</span></span>
  - <span data-ttu-id="677b4-145">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="677b4-145">fx_directory_attributes_set</span></span>
  - <span data-ttu-id="677b4-146">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="677b4-146">fx_directory_attributes_read</span></span>
  - <span data-ttu-id="677b4-147">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="677b4-147">fx_directory_first_entry_find</span></span>
  - <span data-ttu-id="677b4-148">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="677b4-148">fx_directory_next_entry_find</span></span>

### <a name="file-services"></a><span data-ttu-id="677b4-149">Файловые службы</span><span class="sxs-lookup"><span data-stu-id="677b4-149">File Services</span></span>

- <span data-ttu-id="677b4-150">Минимальный размер флэш-памяти 3,3 КБ</span><span class="sxs-lookup"><span data-stu-id="677b4-150">Minimal 3.3KB FLASH</span></span>
- <span data-ttu-id="677b4-151">Неограниченное число открытых файлов</span><span class="sxs-lookup"><span data-stu-id="677b4-151">Unlimited open files</span></span>
- <span data-ttu-id="677b4-152">Файлы, доступные только для чтения, можно открывать несколько раз</span><span class="sxs-lookup"><span data-stu-id="677b4-152">Read-only files can be opened multiple times</span></span>
- <span data-ttu-id="677b4-153">Поддерживаются длинные имена каталогов и имена версии 8.3</span><span class="sxs-lookup"><span data-stu-id="677b4-153">Long and 8.3 directory names supported</span></span>
- <span data-ttu-id="677b4-154">Поддержка смежных файлов</span><span class="sxs-lookup"><span data-stu-id="677b4-154">Contiguous file support</span></span>
- <span data-ttu-id="677b4-155">Логика быстрого поиска</span><span class="sxs-lookup"><span data-stu-id="677b4-155">Fast seek logic</span></span>
- <span data-ttu-id="677b4-156">Предварительное выделение кластеров</span><span class="sxs-lookup"><span data-stu-id="677b4-156">Pre-allocation of clusters</span></span>
- <span data-ttu-id="677b4-157">Создание, удаление и переименование файлов</span><span class="sxs-lookup"><span data-stu-id="677b4-157">File create, delete, and rename</span></span>
- <span data-ttu-id="677b4-158">Чтение, запись и просмотр файлов</span><span class="sxs-lookup"><span data-stu-id="677b4-158">File read, write, and see</span></span>
- <span data-ttu-id="677b4-159">Управление атрибутами файлов</span><span class="sxs-lookup"><span data-stu-id="677b4-159">File attributes management</span></span>
- <span data-ttu-id="677b4-160">Трассировка на уровне системы через TraceX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="677b4-160">System-level Trace via Azure RTOS TraceX</span></span>
- <span data-ttu-id="677b4-161">Интуитивно понятные интерфейсы API для доступа к файлам, включая следующие:</span><span class="sxs-lookup"><span data-stu-id="677b4-161">Intuitive file access APIs, including:</span></span>
  - <span data-ttu-id="677b4-162">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="677b4-162">fx_file_create</span></span>
  - <span data-ttu-id="677b4-163">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="677b4-163">fx_file_delete</span></span>
  - <span data-ttu-id="677b4-164">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="677b4-164">fx_file_attributes_set</span></span>
  - <span data-ttu-id="677b4-165">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="677b4-165">fx_file_attributes_read</span></span>
  - <span data-ttu-id="677b4-166">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="677b4-166">fx_file_read</span></span>
  - <span data-ttu-id="677b4-167">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="677b4-167">fx_file_seek</span></span>
  - <span data-ttu-id="677b4-168">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="677b4-168">fx_file_write</span></span>

## <a name="small-footprint"></a><span data-ttu-id="677b4-169">Небольшой объем занимаемой памяти</span><span class="sxs-lookup"><span data-stu-id="677b4-169">Small-footprint</span></span>

<span data-ttu-id="677b4-170">Встроенная файловая система FileX в ОСРВ Azure занимает всего 8,6–12 КБ памяти для базовой поддержки чтения и записи файлов.</span><span class="sxs-lookup"><span data-stu-id="677b4-170">Azure RTOS FileX embedded file system has a remarkably small minimal footprint of 8.6 KB to 12 KB for basic file read/write support.</span></span> <span data-ttu-id="677b4-171">Минимальный используемый объем ОЗУ для FileX в ОСРВ Azure составляет порядка 1,8 КБ для одного экземпляра носителя. При этом достаточно кэша логических секторов размером 512 байт.</span><span class="sxs-lookup"><span data-stu-id="677b4-171">Minimal Azure RTOS FileX RAM usage is on the order of 1.8 KB for one media instance and with only a 512-byte logical sector cache.</span></span> <span data-ttu-id="677b4-172">Как и в случае с ThreadX в ОСРВ Azure, размер FileX в ОСРВ Azure масштабируется автоматически в зависимости от служб, используемых приложением.</span><span class="sxs-lookup"><span data-stu-id="677b4-172">Like Azure RTOS ThreadX, the size of Azure RTOS FileX automatically scales based on the services used by the application.</span></span> <span data-ttu-id="677b4-173">Это практически устраняет потребность в сложной настройке и параметрах сборки, что упрощает работу разработчика.</span><span class="sxs-lookup"><span data-stu-id="677b4-173">This virtually eliminates the need for complicated configuration and builds parameters, making things easier for the developer.</span></span>

## <a name="fast-execution"></a><span data-ttu-id="677b4-174">Быстрое выполнение</span><span class="sxs-lookup"><span data-stu-id="677b4-174">Fast execution</span></span>

<span data-ttu-id="677b4-175">FileX в ОСРВ Azure предоставляет кэш логических секторов, а также кэш записей FAT.</span><span class="sxs-lookup"><span data-stu-id="677b4-175">Azure RTOS FileX provides a logical sector cache as well as a FAT entry cache.</span></span> <span data-ttu-id="677b4-176">Размеры обоих кэшей напрямую контролируются приложением.</span><span class="sxs-lookup"><span data-stu-id="677b4-176">The sizes of both are under direct control of the application.</span></span> <span data-ttu-id="677b4-177">Кроме того, FileX в ОСРВ Azure обеспечивает непрерывное выделение кластера, а также прямое последовательное чтение кластера и запись в него.</span><span class="sxs-lookup"><span data-stu-id="677b4-177">In addition, Azure RTOS FileX provides contiguous cluster allocation and direct consecutive cluster reading and writing.</span></span> <span data-ttu-id="677b4-178">Запросы на чтение и запись целых секторов выполняются непосредственно между буфером приложения и носителем, то есть промежуточная буферизация не производится.</span><span class="sxs-lookup"><span data-stu-id="677b4-178">Read/write requests of whole sectors are done directly between the application buffer and the media – that is, no intermediate buffering is done.</span></span> <span data-ttu-id="677b4-179">Благодаря этому, а также проекту, ориентированному на обеспечение высокого быстродействия, FileX в ОСРВ Azure способна достигать максимально высокого уровня производительности.</span><span class="sxs-lookup"><span data-stu-id="677b4-179">All of this and a general performance-oriented design philosophy helps Azure RTOS FileX achieve the fastest possible performance.</span></span>

## <a name="advanced-technology"></a><span data-ttu-id="677b4-180">Усовершенствованные технологии</span><span class="sxs-lookup"><span data-stu-id="677b4-180">Advanced technology</span></span>

<span data-ttu-id="677b4-181">FileX в ОСРВ Azure — это современная технология, включающая указанные ниже возможности.</span><span class="sxs-lookup"><span data-stu-id="677b4-181">Azure RTOS FileX is advanced technology, including the following.</span></span>

- <span data-ttu-id="677b4-182">Поддержка FAT12, FAT16, FAT32 и exFAT</span><span class="sxs-lookup"><span data-stu-id="677b4-182">FAT 12/16/32 and exFAT support</span></span>
- <span data-ttu-id="677b4-183">Поддержка нескольких разделов</span><span class="sxs-lookup"><span data-stu-id="677b4-183">Multiple partition support</span></span>
- <span data-ttu-id="677b4-184">Автоматическое масштабирование</span><span class="sxs-lookup"><span data-stu-id="677b4-184">Automatic scaling</span></span>
- <span data-ttu-id="677b4-185">Независимость от порядка байтов</span><span class="sxs-lookup"><span data-stu-id="677b4-185">Endian neutral</span></span>
- <span data-ttu-id="677b4-186">Поддержка длинных имен файлов и имен версии 8.3</span><span class="sxs-lookup"><span data-stu-id="677b4-186">Long file name and 8.3 support</span></span>
- <span data-ttu-id="677b4-187">Дополнительная поддержка отказоустойчивости</span><span class="sxs-lookup"><span data-stu-id="677b4-187">Optional fault tolerance support</span></span>
- <span data-ttu-id="677b4-188">Кэш логических секторов</span><span class="sxs-lookup"><span data-stu-id="677b4-188">Logical sector cache</span></span>
- <span data-ttu-id="677b4-189">Кэш записей FAT</span><span class="sxs-lookup"><span data-stu-id="677b4-189">FAT entry cache</span></span>
- <span data-ttu-id="677b4-190">Предварительное выделение кластеров</span><span class="sxs-lookup"><span data-stu-id="677b4-190">Pre-allocation of clusters</span></span>
- <span data-ttu-id="677b4-191">Поддержка смежных файлов</span><span class="sxs-lookup"><span data-stu-id="677b4-191">Contiguous file support</span></span>
- <span data-ttu-id="677b4-192">Дополнительные метрики производительности</span><span class="sxs-lookup"><span data-stu-id="677b4-192">Optional performance metrics</span></span>
- <span data-ttu-id="677b4-193">Поддержка системного анализа TraceX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="677b4-193">Azure RTOS TraceX system analysis support</span></span>

## <a name="nornand-wear-leveling-azure-rtos-levelx"></a><span data-ttu-id="677b4-194">Выравнивание износа NOR/NAND (LevelX в ОСРВ Azure)</span><span class="sxs-lookup"><span data-stu-id="677b4-194">NOR/NAND Wear Leveling (Azure RTOS LevelX)</span></span>

<span data-ttu-id="677b4-195">LevelX в ОСРВ Azure — это решение Майкрософт для выравнивания износа флэш-памяти NOR/NAND.</span><span class="sxs-lookup"><span data-stu-id="677b4-195">Azure RTOS LevelX is Microsoft’s NOR/NAND FLASH wear leveling product.</span></span> <span data-ttu-id="677b4-196">LevelX в ОСРВ Azure можно использовать в сочетании с FileX или как отдельную библиотеку для прямого чтения и записи секторов флэш-памяти в приложении.</span><span class="sxs-lookup"><span data-stu-id="677b4-196">Azure RTOS LevelX can be used in conjunction with FileX or as a stand-alone, direct read/write FLASH sector library for the application.</span></span>

## <a name="fastest-time-to-market"></a><span data-ttu-id="677b4-197">Минимальное время выхода на рынок</span><span class="sxs-lookup"><span data-stu-id="677b4-197">Fastest time-to-market</span></span>

<span data-ttu-id="677b4-198">FileX в ОСРВ Azure легко устанавливать, изучать, использовать, отлаживать, проверять, сертифицировать и обслуживать.</span><span class="sxs-lookup"><span data-stu-id="677b4-198">Azure RTOS FileX is easy to install, learn, use, debug, verify, certify, and maintain.</span></span> <span data-ttu-id="677b4-199">В результате FileX в ОСРВ Azure является одной из наиболее популярных файловых систем FAT для внедренных устройств Интернета вещей.</span><span class="sxs-lookup"><span data-stu-id="677b4-199">As a result, Azure RTOS FileX is one of the most popular FAT file systems for embedded IoT devices.</span></span> <span data-ttu-id="677b4-200">Ниже приведены некоторые причины, обеспечившие наши преимущества при выходе на рынок:</span><span class="sxs-lookup"><span data-stu-id="677b4-200">The following are some reasons for our consistent time-to-market advantage:</span></span>

- <span data-ttu-id="677b4-201">документация высокого качества — ознакомьтесь с нашим [руководством пользователя FileX в ОСРВ Azure](about-this-guide.md) и убедитесь в этом сами;</span><span class="sxs-lookup"><span data-stu-id="677b4-201">Quality Documentation – please review our [Azure RTOS FileX User Guide](about-this-guide.md) and see for yourself!</span></span>
- <span data-ttu-id="677b4-202">полная доступность исходного кода;</span><span class="sxs-lookup"><span data-stu-id="677b4-202">Complete Source Code Availability</span></span>
- <span data-ttu-id="677b4-203">простые в использовании API-интерфейсы;</span><span class="sxs-lookup"><span data-stu-id="677b4-203">Easy-to-use API</span></span>
- <span data-ttu-id="677b4-204">комплексный и широкий набор функций.</span><span class="sxs-lookup"><span data-stu-id="677b4-204">Comprehensive and Advanced Feature Set</span></span>

## <a name="pre-certified--by-tuv-and-ul-to-many-safety-standards"></a><span data-ttu-id="677b4-205">Предварительная сертификация TUV и UL на соответствие множеству стандартов безопасности</span><span class="sxs-lookup"><span data-stu-id="677b4-205">Pre-certified  by TUV and UL to many safety standards</span></span>

![SGS-TUV Saar](./media/overview-filex/partener-logo-sgs-tuv-saar-2.png)

<span data-ttu-id="677b4-207">Система FileX в ОСРВ Azure сертифицирована организацией SGS-TUV Saar для использования в системах со строгими требованиями к безопасности в соответствии со стандартами IEC-61508 SIL 4, IEC-62304 SW (класс безопасности C), ISO 26262 ASIL D и EN 50128.</span><span class="sxs-lookup"><span data-stu-id="677b4-207">Azure RTOS FileX has been certified by SGS-TUV Saar for use in safety-critical systems, according to IEC-61508 SIL 4, IEC-62304  SW Safety Class C, ISO 26262 ASIL D and EN 50128.</span></span> <span data-ttu-id="677b4-208">Такая сертификация гарантирует, что FileX можно использовать при разработке ПО с особыми требованиями к функциональной безопасности, соответствующего высочайшим уровням целостности по стандартам IEC-61508, IEC-62304, ISO 26262 и EN 50128 для "функциональной безопасности электрических, электронных и программируемых электронных систем, связанных с безопасностью".</span><span class="sxs-lookup"><span data-stu-id="677b4-208">The certification confirms that FileX can be used in the development of safety-related software for the highest safety integrity levels of IEC-61508, IEC-62304, ISO 26262 and EN 50128 for the “Functional Safety of electrical, electronic, and programmable electronic safety-related systems.”</span></span> <span data-ttu-id="677b4-209">Компания SGS-TUV Saar, основанная совместно немецкими компаниями SGS-Group и TUV Saarland, стала ведущей аккредитованной и независимой компанией, выполняющей тестирование, аудит, проверку и сертификацию внедренного ПО для связанных с безопасностью систем.</span><span class="sxs-lookup"><span data-stu-id="677b4-209">SGS-TUV Saar, formed through a joint venture of Germany’s SGS-Group and TUV Saarland, has become the leading accredited, independent company for testing, auditing, verifying, and certifying embedded software for safety-related systems worldwide.</span></span> <span data-ttu-id="677b4-210">Соответствие промышленному стандарту безопасности IEC 61508 и всем его производным стандартам, в том числе IEC-62304, ISO 26262 и EN 50128, гарантирует функциональную безопасность электрических, электронных и программируемых электронных медицинских изделий, систем управления процессами, промышленного оборудования, автомобилей и систем управления железнодорожными перевозками с высоким уровнем безопасности.</span><span class="sxs-lookup"><span data-stu-id="677b4-210">The industrial safety standard IEC 61508, and all standards that are derived from it, including IEC-62304, ISO 26262 and EN 50128, are used to assure the functional safety of electrical, electronic, and programmable electronic safety-related medical devices, process control systems, industrial machinery, automobiles, and railway control systems.</span></span>

:::image type="content" source="media/overview-filex/cru-logo-certification.png" alt-text="Сертификация CRU UL":::

<span data-ttu-id="677b4-212">Система FileX в ОСРВ Azure отмечена UL как соответствующая стандартам безопасности UL 60730-1 (приложение H), CSA E60730-1 (приложение H), IEC 60730-1 (приложение H), UL 60335-1 (приложение R), IEC 60335-1 (приложение R) и UL 1998 для ПО в программируемых компонентах.</span><span class="sxs-lookup"><span data-stu-id="677b4-212">Azure RTOS FileX has been recognized by UL for compliance with UL 60730-1 Annex H, CSA E60730-1 Annex H, IEC 60730-1 Annex H, UL 60335-1 Annex R, IEC 60335-1 Annex R, and UL 1998 safety standards for software in programmable components.</span></span> <span data-ttu-id="677b4-213">UL — это глобальная независимая компания, работающая в сфере науки безопасности. Уже более ста лет она создает инновационные решения безопасности в разных областях — от повсеместного внедрения электричества до прорывов в сферах экологической устойчивости, возобновляемых источников энергии и нанотехнологий.</span><span class="sxs-lookup"><span data-stu-id="677b4-213">UL is a global, independent, safety-science company with more than a century of expertise innovating safety solutions, ranging from the public adoption of electricity to breakthroughs in sustainability, renewable energy, and nanotechnology.</span></span>

<span data-ttu-id="677b4-214">Информационные продукты (сертификат, руководство по безопасности, отчет о тестировании и т. д.) для сертификаций TUV и UL доступны для продажи.</span><span class="sxs-lookup"><span data-stu-id="677b4-214">Artifacts (Certificate, Safety Manual, Test Report, etc.) associated with the TUV and UL certifications are available for sale.</span></span>

<span data-ttu-id="677b4-215">В тех случаях, когда для приложения требуется дополнительная сертификация, Майкрософт предлагает услугу по сертификации, которая позволяет получить готовую сертификацию по различным стандартам с учетом реальной аппаратной платформы, распространяющуюся даже на код приложения.</span><span class="sxs-lookup"><span data-stu-id="677b4-215">In cases where the application needs additional certification, a certification service is available through Microsoft for providing turn-key certification to various standards using the actual hardware platform and even covering the application code.</span></span>

## <a name="one-simple-license"></a><span data-ttu-id="677b4-216">Одна простая лицензия</span><span class="sxs-lookup"><span data-stu-id="677b4-216">One Simple License</span></span>

<span data-ttu-id="677b4-217">Использование и тестирование исходного кода не требуют каких-либо затрат, как и производственные лицензии при развертывании на предварительно лицензированных устройствах. Для всех других устройств требуется лишь простая лицензия сроком на один год.</span><span class="sxs-lookup"><span data-stu-id="677b4-217">There is no cost to use and test the source code and no cost for production licenses when deployed to pre-licensed devices, all other devices need a simple annual license.</span></span>

## <a name="full-highest-quality-source-code"></a><span data-ttu-id="677b4-218">Полный и высококачественный исходный код</span><span class="sxs-lookup"><span data-stu-id="677b4-218">Full, highest-quality source code</span></span>

<span data-ttu-id="677b4-219">Уже несколько лет исходный код FileX задает стандарт качества и простоты понимания.</span><span class="sxs-lookup"><span data-stu-id="677b4-219">Throughout the years, FileX source code has set the bar in quality and ease of understanding.</span></span> <span data-ttu-id="677b4-220">Кроме того, соглашение по применению отдельного файла для каждой функции упрощает навигацию по исходному коду.</span><span class="sxs-lookup"><span data-stu-id="677b4-220">In addition, the convention of having one function per file provides for easy source navigation.</span></span>

## <a name="supports-most-popular-architectures"></a><span data-ttu-id="677b4-221">Поддержка большинства популярных архитектур</span><span class="sxs-lookup"><span data-stu-id="677b4-221">Supports most popular architectures</span></span>

<span data-ttu-id="677b4-222">Система FileX в ОСРВ Azure работает на большинстве популярных 32- и 64-разрядных микропроцессоров. Она не требует дополнительной настройки, полностью протестирована и поддерживается на разных архитектурах, включая следующие:</span><span class="sxs-lookup"><span data-stu-id="677b4-222">Azure RTOS FileX runs on most popular 32/64-bit microprocessors, out-of-the-box, fully tested and fully supported, including the following:</span></span>

<span data-ttu-id="677b4-223">**Analog Devices**: SHARC, Blackfin, CM4xx;</span><span class="sxs-lookup"><span data-stu-id="677b4-223">**Analog Devices**: SHARC, Blackfin, CM4xx</span></span>

<span data-ttu-id="677b4-224">**Andes Core**: RISC-V;</span><span class="sxs-lookup"><span data-stu-id="677b4-224">**Andes Core**: RISC-V</span></span>

<span data-ttu-id="677b4-225">**Ambiqmicro**: микроконтроллеры Apollo;</span><span class="sxs-lookup"><span data-stu-id="677b4-225">**Ambiqmicro**: Apollo MCUs</span></span>

<span data-ttu-id="677b4-226">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M;</span><span class="sxs-lookup"><span data-stu-id="677b4-226">**ARM**: ARM7, ARM9, ARM11, Cortex-M0/M3/M4/M7/A15/A5/A7/A8/A9/A5x 64-bi/A7x 64-bit/R4/R5, TrustZone ARMv8-M</span></span>

<span data-ttu-id="677b4-227">**Cadence**: Xtensa, Diamond;</span><span class="sxs-lookup"><span data-stu-id="677b4-227">**Cadence**: Xtensa, Diamond</span></span>

<span data-ttu-id="677b4-228">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi;</span><span class="sxs-lookup"><span data-stu-id="677b4-228">**CEVA**: PSoC, PSoC 4, PSoC 5, PSoC 6, FM0+, FM3, MF4, WICED WiFi</span></span>

<span data-ttu-id="677b4-229">**Cypress**: RISC-V;</span><span class="sxs-lookup"><span data-stu-id="677b4-229">**Cypress**: RISC-V</span></span>

<span data-ttu-id="677b4-230">**EnSilica**: eSi-RISC;</span><span class="sxs-lookup"><span data-stu-id="677b4-230">**EnSilica**: eSi-RISC</span></span>

<span data-ttu-id="677b4-231">**Infineon**: XMC1000, XMC4000, TriCore;</span><span class="sxs-lookup"><span data-stu-id="677b4-231">**Infineon**: XMC1000, XMC4000, TriCore</span></span>

<span data-ttu-id="677b4-232">**Intel**; **ППВМ Intel**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10;</span><span class="sxs-lookup"><span data-stu-id="677b4-232">**Intel**; **Intel FPGA**: x36/Pentium, XScale, NIOS II, Cyclone, Arria 10</span></span>

<span data-ttu-id="677b4-233">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32;</span><span class="sxs-lookup"><span data-stu-id="677b4-233">**Microchip**: AVR32, ARM7, ARM9, Cortex-M3/M4/M7, SAM3/4/7/9/A/C/D/E/G/L/SV, PIC24/PIC32</span></span>

<span data-ttu-id="677b4-234">**Microsemi**: RISC-V;</span><span class="sxs-lookup"><span data-stu-id="677b4-234">**Microsemi**: RISC-V</span></span>

<span data-ttu-id="677b4-235">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4;</span><span class="sxs-lookup"><span data-stu-id="677b4-235">**NXP**: LPC, ARM7, ARM9, PowerPC, 68 K, i.MX, ColdFire, Kinetis Cortex-M3/M4</span></span>

<span data-ttu-id="677b4-236">**Renesas**: SH, HS, V850, RX, RZ, Synergy;</span><span class="sxs-lookup"><span data-stu-id="677b4-236">**Renesas**: SH, HS, V850, RX, RZ, Synergy</span></span>

<span data-ttu-id="677b4-237">**Silicon Labs**: EFM32;</span><span class="sxs-lookup"><span data-stu-id="677b4-237">**Silicon** Labs: EFM32</span></span>

<span data-ttu-id="677b4-238">**Synopsys**: ARC 600, 700, ARC EM, ARC HS;</span><span class="sxs-lookup"><span data-stu-id="677b4-238">**Synopsys**: ARC 600, 700, ARC EM, ARC HS</span></span>

<span data-ttu-id="677b4-239">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7;</span><span class="sxs-lookup"><span data-stu-id="677b4-239">**ST**: STM32, ARM7, ARM9, Cortex-M3/M4/M7</span></span>

<span data-ttu-id="677b4-240">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C;</span><span class="sxs-lookup"><span data-stu-id="677b4-240">**Tl**: C5xxx, C6xxx, Stellaris, Sitara, Tiva-C</span></span>

<span data-ttu-id="677b4-241">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class;</span><span class="sxs-lookup"><span data-stu-id="677b4-241">**Wave Computing**: MIPS32 4K, 24 K, 34 K, 1004 K, MIPS64 5K, microAptiv, interAptiv, proAptiv, M-Class</span></span>

<span data-ttu-id="677b4-242">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE.</span><span class="sxs-lookup"><span data-stu-id="677b4-242">**Xilinx**: MicroBlaze, PowerPC 405, ZYNQ, ZYNQ UltraSCALE</span></span>

<span data-ttu-id="677b4-243">*Все приведенные сведения о времени ожидания и размере могут отличаться от фактических. Это зависит от платформы разработки.*</span><span class="sxs-lookup"><span data-stu-id="677b4-243">*All timing and size figures listed are estimates and may be different on your development platform.*</span></span>
