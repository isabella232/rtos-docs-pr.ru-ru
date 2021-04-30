---
title: Глава 2. Установка стека узлов ОСРВ Azure USBX
description: Узнайте, как установить стек узлов USBX.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 4c33f95b8ac268c557fd947a1303ec3af315a37e
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377090"
---
# <a name="chapter-2---azure-rtos-usbx-host-stack-installation"></a><span data-ttu-id="d41c6-103">Глава 2. Установка стека узлов ОСРВ Azure USBX</span><span class="sxs-lookup"><span data-stu-id="d41c6-103">Chapter 2 - Azure RTOS USBX Host Stack Installation</span></span>

## <a name="host-considerations"></a><span data-ttu-id="d41c6-104">Рекомендации по размещению</span><span class="sxs-lookup"><span data-stu-id="d41c6-104">Host Considerations</span></span>

### <a name="computer-type"></a><span data-ttu-id="d41c6-105">Тип компьютера</span><span class="sxs-lookup"><span data-stu-id="d41c6-105">Computer Type</span></span>

<span data-ttu-id="d41c6-106">Разработка внедренных решений обычно выполняется на главных компьютерах с Windows или Unix.</span><span class="sxs-lookup"><span data-stu-id="d41c6-106">Embedded development is usually performed on Windows PC or Unix host computers.</span></span> <span data-ttu-id="d41c6-107">После компиляции, связывания и размещения на узле приложение скачивается на целевое оборудование для выполнения.</span><span class="sxs-lookup"><span data-stu-id="d41c6-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

### <a name="download-interfaces"></a><span data-ttu-id="d41c6-108">Интерфейсы скачивания</span><span class="sxs-lookup"><span data-stu-id="d41c6-108">Download Interfaces</span></span>

<span data-ttu-id="d41c6-109">Как правило, скачивание на целевое оборудование выполняется через последовательный интерфейс RS-232, хотя становятся все более популярными параллельные интерфейсы, USB и Ethernet.</span><span class="sxs-lookup"><span data-stu-id="d41c6-109">Usually, the target download is done over an RS-232 serial interface, although parallel interfaces, USB, and Ethernet are becoming more popular.</span></span> <span data-ttu-id="d41c6-110">Доступные варианты представлены в документации по инструменту разработки.</span><span class="sxs-lookup"><span data-stu-id="d41c6-110">See the development tool documentation for available options.</span></span>

### <a name="debugging-tools"></a><span data-ttu-id="d41c6-111">Инструменты отладки</span><span class="sxs-lookup"><span data-stu-id="d41c6-111">Debugging Tools</span></span>

<span data-ttu-id="d41c6-112">Отладка обычно выполняется по той же ссылке, что и скачивание образа программы.</span><span class="sxs-lookup"><span data-stu-id="d41c6-112">Debugging is done typically over the same link as the program image download.</span></span> <span data-ttu-id="d41c6-113">Существует множество отладчиков, от небольших программ мониторинга, выполняющихся на целевом объекте, до инструментов Background Debug Monitor (BDM) и In-Circuit Emulator (ICE).</span><span class="sxs-lookup"><span data-stu-id="d41c6-113">A variety of debuggers exist, ranging from small monitor programs running on the target through Background Debug Monitor (BDM) and In-Circuit Emulator (ICE) tools.</span></span> <span data-ttu-id="d41c6-114">Инструмент ICE обеспечивает наиболее надежную отладку фактического целевого оборудования.</span><span class="sxs-lookup"><span data-stu-id="d41c6-114">The ICE tool provides the most robust debugging of actual target hardware.</span></span>

### <a name="required-hard-disk-space"></a><span data-ttu-id="d41c6-115">Требуемое место на жестком диске</span><span class="sxs-lookup"><span data-stu-id="d41c6-115">Required Hard Disk Space</span></span>

<span data-ttu-id="d41c6-116">Исходный код USBX поставляется в формате ASCII и требует примерно 500 КБ пространства на жестком диске главного компьютера.</span><span class="sxs-lookup"><span data-stu-id="d41c6-116">The source code for USBX is delivered in ASCII format and requires approximately 500 KBytes of space on the host computer's hard disk.</span></span>

## <a name="target-considerations"></a><span data-ttu-id="d41c6-117">Рекомендации по целевому оборудованию</span><span class="sxs-lookup"><span data-stu-id="d41c6-117">Target Considerations</span></span>

<span data-ttu-id="d41c6-118">Для USBX требуется от 24 до 64 КБ доступной только для чтения памяти (ПЗУ) на целевом оборудовании в режиме узла.</span><span class="sxs-lookup"><span data-stu-id="d41c6-118">USBX requires between 24 KBytes and 64 KBytes of Read Only Memory (ROM) on the target in host mode.</span></span> <span data-ttu-id="d41c6-119">Необходимый объем памяти зависит от типа используемого контроллера и классов USB, связанных с USBX.</span><span class="sxs-lookup"><span data-stu-id="d41c6-119">The amount of memory required is dependent on the type of controller used and the USB classes linked to USBX.</span></span> <span data-ttu-id="d41c6-120">Для глобальных структур данных и пула памяти USBX требуется еще 32 КБ памяти (ОЗУ) на целевом оборудовании.</span><span class="sxs-lookup"><span data-stu-id="d41c6-120">Another 32 KBytes of the target's Random Access Memory (RAM) are required for USBX global data structures and memory pool.</span></span> <span data-ttu-id="d41c6-121">Этот пул памяти также может быть скорректирован в зависимости от ожидаемого количества устройств на шине USB и типа контроллера USB.</span><span class="sxs-lookup"><span data-stu-id="d41c6-121">This memory pool can also be adjusted depending on the expected number of devices on the USB and the type of USB controller.</span></span> <span data-ttu-id="d41c6-122">На стороне устройства USBX требуется примерно 10–12 КБ ПЗУ, в зависимости от типа контроллера устройства.</span><span class="sxs-lookup"><span data-stu-id="d41c6-122">The USBX device side requires roughly 10-12 K of ROM depending on the type of device controller.</span></span> <span data-ttu-id="d41c6-123">Использование памяти ОЗУ зависит от типа класса, эмулируемого устройством.</span><span class="sxs-lookup"><span data-stu-id="d41c6-123">The RAM memory usage depends on the type of class emulated by the device.</span></span>

<span data-ttu-id="d41c6-124">USBX также использует семафоры, мьютексы и потоки ThreadX для защиты многопоточности, как и приостановку ввода-вывода и периодическую обработку для мониторинга топологии шины USB.</span><span class="sxs-lookup"><span data-stu-id="d41c6-124">USBX also relies on ThreadX semaphores, mutexes, and threads for multiple thread protection, and I/O suspension and periodic processing for monitoring the USB bus topology.</span></span>

### <a name="product-distribution"></a><span data-ttu-id="d41c6-125">Дистрибутивы продукта</span><span class="sxs-lookup"><span data-stu-id="d41c6-125">Product Distribution</span></span>

<span data-ttu-id="d41c6-126">ОСРВ Azure USBX можно получить из нашего репозитория общедоступного исходного кода по адресу <https://github.com/azure-rtos/usbx/>.</span><span class="sxs-lookup"><span data-stu-id="d41c6-126">Azure RTOS USBX can be obtained from our public source code repository at <https://github.com/azure-rtos/usbx/>.</span></span>

<span data-ttu-id="d41c6-127">Ниже приведен список важных файлов в этом репозитории.</span><span class="sxs-lookup"><span data-stu-id="d41c6-127">The following is a list of several important files in the repository:</span></span>

- <span data-ttu-id="d41c6-128">***ux_api.h***: это файл заголовка C, который содержит все системные равенства, структуры данных и прототипы служб.</span><span class="sxs-lookup"><span data-stu-id="d41c6-128">***ux_api.h***: This C header file contains all system equates, data structures, and service prototypes.</span></span>
- <span data-ttu-id="d41c6-129">***ux_port.h***: это файл заголовка C, который содержит все определения и структуры данных, относящиеся к конкретным инструментам разработки.</span><span class="sxs-lookup"><span data-stu-id="d41c6-129">***ux_port.h***: This C header file contains all development-tool-specific data definitions and structures.</span></span>
- <span data-ttu-id="d41c6-130">***ux.lib***: это двоичная версия библиотеки C для USBX.</span><span class="sxs-lookup"><span data-stu-id="d41c6-130">***ux.lib***: This is the binary version of the USBX C library.</span></span> <span data-ttu-id="d41c6-131">Она распространяется с помощью стандартного пакета.</span><span class="sxs-lookup"><span data-stu-id="d41c6-131">It is distributed with the standard package.</span></span>
- <span data-ttu-id="d41c6-132">***demo_usbx.c*** — это файл C, содержащий простую демоверсию для USBX.</span><span class="sxs-lookup"><span data-stu-id="d41c6-132">***demo_usbx.c***: The C file containing a simple USBX demo</span></span>

<span data-ttu-id="d41c6-133">Все имена файлов указаны в нижнем регистре.</span><span class="sxs-lookup"><span data-stu-id="d41c6-133">All filenames are in lower-case.</span></span> <span data-ttu-id="d41c6-134">Такое соглашение об именовании упрощает преобразование команд для платформ разработки UNIX.</span><span class="sxs-lookup"><span data-stu-id="d41c6-134">This naming convention makes it easier to convert the commands to Unix development platforms.</span></span>

## <a name="usbx-installation"></a><span data-ttu-id="d41c6-135">Установка USBX</span><span class="sxs-lookup"><span data-stu-id="d41c6-135">USBX Installation</span></span>

<span data-ttu-id="d41c6-136">USBX устанавливается путем клонирования репозитория GitHub на локальный компьютер.</span><span class="sxs-lookup"><span data-stu-id="d41c6-136">USBX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="d41c6-137">Ниже приведен типичный синтаксис для создания клона репозитория USBX на вашем компьютере.</span><span class="sxs-lookup"><span data-stu-id="d41c6-137">The following is typical syntax for creating a clone of the USBX repository on your PC:</span></span>

```powershell
    git clone https://github.com/azure-rtos/usbx
```

<span data-ttu-id="d41c6-138">Вы также можете скачать копию репозитория с помощью соответствующей кнопки на главной странице GitHub.</span><span class="sxs-lookup"><span data-stu-id="d41c6-138">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="d41c6-139">Кроме того, вы можете найти инструкции по созданию библиотеки USBX на главной странице веб-репозитория.</span><span class="sxs-lookup"><span data-stu-id="d41c6-139">You will also find instructions for building the USBX library on the front page of the online repository.</span></span>

<span data-ttu-id="d41c6-140">Приведенные ниже общие инструкции применимы практически к любой установке.</span><span class="sxs-lookup"><span data-stu-id="d41c6-140">The following general instructions apply to virtually any installation:</span></span>

1. <span data-ttu-id="d41c6-141">Используйте тот же каталог на жестком диске узла, в который вы ранее установили ThreadX.</span><span class="sxs-lookup"><span data-stu-id="d41c6-141">Use the same directory in which you previously installed ThreadX on the host hard drive.</span></span> <span data-ttu-id="d41c6-142">Все имена USBX уникальны и не повлияют на предыдущую установку USBX.</span><span class="sxs-lookup"><span data-stu-id="d41c6-142">All USBX names are unique and will not interfere with the previous USBX installation.</span></span>
2. <span data-ttu-id="d41c6-143">Добавьте вызов \***ux_system_initialize** _ в начало _ *_tx_application_define_.* \* На этом этапе инициализируются ресурсы USBX.</span><span class="sxs-lookup"><span data-stu-id="d41c6-143">Add a call to ***ux_system_initialize** _ at or near the beginning of _ *_tx_application_define_.** This is where the USBX resources are initialized.</span></span>
3. <span data-ttu-id="d41c6-144">Добавьте вызов ***ux_host_stack_initialize*** .</span><span class="sxs-lookup"><span data-stu-id="d41c6-144">Add a call to \***ux_host_stack_initialize\*.**</span></span>
4. <span data-ttu-id="d41c6-145">Добавьте один или несколько вызовов для инициализации требуемого экземпляра USBX.</span><span class="sxs-lookup"><span data-stu-id="d41c6-145">Add one or more calls to initialize the required USBX.</span></span>
5. <span data-ttu-id="d41c6-146">Добавьте один или несколько вызовов для инициализации хост-контроллеров, доступных в системе.</span><span class="sxs-lookup"><span data-stu-id="d41c6-146">Add one or more calls to initialize the host controllers available in the system.</span></span>
6. <span data-ttu-id="d41c6-147">Может потребоваться изменить файл tx_low_level_initialize.c, чтобы добавить инициализацию низкого уровня для оборудования и маршрутизацию векторов прерывания.</span><span class="sxs-lookup"><span data-stu-id="d41c6-147">It may be required to modify the tx_low_level_initialize.c file to add low-level hardware initialization and interrupt vector routing.</span></span> <span data-ttu-id="d41c6-148">Это относится к особенностям аппаратной платформы и не будет рассматриваться в этом документе.</span><span class="sxs-lookup"><span data-stu-id="d41c6-148">This is specific to the hardware platform and will not be discussed here.</span></span>
7. <span data-ttu-id="d41c6-149">Выполните компиляцию исходного кода приложения и связывание с библиотеками времени выполнения USBX и ThreadX — ux.a (или ux.lib) и tx.a (или tx.lib) (могут также потребоваться FileX и (или) NetX, если требуется скомпилировать класс хранения USB и (или) классы сети USB).</span><span class="sxs-lookup"><span data-stu-id="d41c6-149">Compile application source code and link with the USBX and ThreadX run time libraries (FileX and/or Netx may also be required if the USB storage class and/or USB network classes are to be compiled in), ux.a (or ux.lib) and tx.a (or tx.lib).</span></span> <span data-ttu-id="d41c6-150">Полученный пакет можно скачать на целевое оборудование и выполнить.</span><span class="sxs-lookup"><span data-stu-id="d41c6-150">The resulting can be downloaded to the target and executed.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="d41c6-151">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="d41c6-151">Configuration Options</span></span>

<span data-ttu-id="d41c6-152">Существует ряд параметров конфигурации для сборки библиотеки USBX.</span><span class="sxs-lookup"><span data-stu-id="d41c6-152">There are several configuration options for building the USBX library.</span></span> <span data-ttu-id="d41c6-153">Все параметры находятся в файле ***ux_user.h***.</span><span class="sxs-lookup"><span data-stu-id="d41c6-153">All options are located in the ***ux_user.h***.</span></span>

<span data-ttu-id="d41c6-154">Эти параметры подробно описаны в списке ниже.</span><span class="sxs-lookup"><span data-stu-id="d41c6-154">The list below details each configuration option.</span></span>


- <span data-ttu-id="d41c6-155">**UX_PERIODIC_RATE**: это значение представляет число тактов в секунду для конкретной аппаратной платформы.</span><span class="sxs-lookup"><span data-stu-id="d41c6-155">**UX_PERIODIC_RATE**: This value represents how many ticks per seconds for a specific hardware platform.</span></span> <span data-ttu-id="d41c6-156">Значение по умолчанию — 1000, оно задает 1 такт на миллисекунду.</span><span class="sxs-lookup"><span data-stu-id="d41c6-156">The default is 1000 indicating one tick per millisecond.</span></span>
- <span data-ttu-id="d41c6-157">**UX_MAX_CLASS_DRIVER**: это максимальное число классов, которое может быть загружено USBX.</span><span class="sxs-lookup"><span data-stu-id="d41c6-157">**UX_MAX_CLASS_DRIVER**: This value is the maximum number of classes that can be loaded by USBX.</span></span> <span data-ttu-id="d41c6-158">Это значение представляет контейнер классов, а не число экземпляров класса.</span><span class="sxs-lookup"><span data-stu-id="d41c6-158">This value represents the class container and not the number of instances of a class.</span></span> <span data-ttu-id="d41c6-159">Например, если конкретной реализации USBX требуется класс концентраторов, класс принтеров и класс хранилищ, то значение UX_MAX_CLASS_DRIVER может быть равно 3 независимо от числа устройств, принадлежащих к этим классам.</span><span class="sxs-lookup"><span data-stu-id="d41c6-159">For instance, if a particular implementation of USBX needs the hub class, the printer class, and the storage class, then the UX_MAX_CLASS_DRIVER value can be set to 3 regardless of the number of devices that belong to these classes.</span></span>
- <span data-ttu-id="d41c6-160">**UX_MAX_HCD**: это значение представляет число разных хост-контроллеров, доступных в системе.</span><span class="sxs-lookup"><span data-stu-id="d41c6-160">**UX_MAX_HCD**: This value represents the number of different host controllers that are available in the system.</span></span> <span data-ttu-id="d41c6-161">Для поддержки USB 1.1 это значение обычно равно 1.</span><span class="sxs-lookup"><span data-stu-id="d41c6-161">For USB 1.1 support, this value will mostly be 1.</span></span> <span data-ttu-id="d41c6-162">Для поддержки USB 2.0 это значение может быть больше 1.</span><span class="sxs-lookup"><span data-stu-id="d41c6-162">For USB 2.0 support this value can be more than 1.</span></span> <span data-ttu-id="d41c6-163">Это значение представляет количество одновременно работающих хост-контроллеров.</span><span class="sxs-lookup"><span data-stu-id="d41c6-163">This value represents the number of concurrent host controllers running at the same time.</span></span> <span data-ttu-id="d41c6-164">Например, если выполняются два экземпляра OHCI или один контроллер EHCI и один контроллер OHCI, то для UX_MAX_HCD должно быть задано значение 2.</span><span class="sxs-lookup"><span data-stu-id="d41c6-164">If for instance, there are two instances of OHCI running or one EHCI and one OHCI controllers running, the UX_MAX_HCD should be set to 2.</span></span> 
- <span data-ttu-id="d41c6-165">**UX_MAX_DEVICES**: это значение представляет максимальное число устройств, которые могут быть подключены к USB.</span><span class="sxs-lookup"><span data-stu-id="d41c6-165">**UX_MAX_DEVICES**: This value represents the maximum number of devices that can be attached to the USB.</span></span> <span data-ttu-id="d41c6-166">Как правило, теоретически максимальное число устройств, которые можно подключить к одному USB-устройству, равно 127.</span><span class="sxs-lookup"><span data-stu-id="d41c6-166">Normally, the theoretical maximum number on a single USB is 127 devices.</span></span> <span data-ttu-id="d41c6-167">Это значение можно уменьшить, чтобы уменьшить снизить потребление памяти.</span><span class="sxs-lookup"><span data-stu-id="d41c6-167">This value can be scaled down to conserve memory.</span></span> <span data-ttu-id="d41c6-168">Следует отметить, что это значение представляет общее количество устройств независимо от числа шин USB в системе.</span><span class="sxs-lookup"><span data-stu-id="d41c6-168">It should be noted that this value represents the total number of devices regardless of the number of USB buses in the system.</span></span>
- <span data-ttu-id="d41c6-169">**UX_MAX_ED**: это значение представляет максимальное число дескрипторов ED в пуле контроллеров.</span><span class="sxs-lookup"><span data-stu-id="d41c6-169">**UX_MAX_ED**: This value represents the maximum number of EDs in the controller pool.</span></span> <span data-ttu-id="d41c6-170">Это число назначается только одному контроллеру.</span><span class="sxs-lookup"><span data-stu-id="d41c6-170">This number is assigned to one controller only.</span></span> <span data-ttu-id="d41c6-171">Если имеется несколько экземпляров контроллера, то для каждого контроллера используется отдельное значение.</span><span class="sxs-lookup"><span data-stu-id="d41c6-171">If multiple instances of controllers are present, this value is used by each individual controller.</span></span>
- <span data-ttu-id="d41c6-172">**UX_MAX_TD и UX_MAX_ISO_TD**: эти значения представляют максимальное число обычных и изохронных дескрипторов передачи (TD) в пуле контроллера.</span><span class="sxs-lookup"><span data-stu-id="d41c6-172">**UX_MAX_TD and UX_MAX_ISO_TD**: This value represents the maximum number of regular and isochronous TDs in the controller pool.</span></span> <span data-ttu-id="d41c6-173">Это число назначается только одному контроллеру.</span><span class="sxs-lookup"><span data-stu-id="d41c6-173">This number is assigned to one controller only.</span></span> <span data-ttu-id="d41c6-174">Если имеется несколько экземпляров контроллера, то для каждого контроллера используется отдельное значение.</span><span class="sxs-lookup"><span data-stu-id="d41c6-174">If multiple instances of controllers are present, this value is used by each individual controller.</span></span>
- <span data-ttu-id="d41c6-175">**UX_THREAD_STACK_SIZE**: это размер стека в байтах для потоков USBX.</span><span class="sxs-lookup"><span data-stu-id="d41c6-175">**UX_THREAD_STACK_SIZE**: This value is the size of the stack in bytes for the USBX threads.</span></span> <span data-ttu-id="d41c6-176">Обычно это может быть 1024 байт или 2048 байт, в зависимости от используемого процессора и хост-контроллера.</span><span class="sxs-lookup"><span data-stu-id="d41c6-176">It can be typically 1024 bytes or 2048 bytes depending on the processor used and the host controller.</span></span>
- <span data-ttu-id="d41c6-177">**UX_HOST_ENUM_THREAD_STACK_SIZE**: это размер стека потоков перечисления узлов USB.</span><span class="sxs-lookup"><span data-stu-id="d41c6-177">**UX_HOST_ENUM_THREAD_STACK_SIZE**: This value is the stack size of the USB host enumeration thread.</span></span> <span data-ttu-id="d41c6-178">Если этот параметр не задан, то размер стека потоков перечисления узлов USBX задается равным **UX_THREAD_STACK_SIZE**.</span><span class="sxs-lookup"><span data-stu-id="d41c6-178">If this symbol I not set, the USBX host enumeration thread stack size is set to **UX_THREAD_STACK_SIZE**.</span></span> 
- <span data-ttu-id="d41c6-179">**UX_HOST_HCD_THREAD_STACK_SIZE**: это размер стека потоков HCD узлов USB.</span><span class="sxs-lookup"><span data-stu-id="d41c6-179">**UX_HOST_HCD_THREAD_STACK_SIZE**: This value is the stack size of the USB host HCD thread.</span></span> <span data-ttu-id="d41c6-180">Если этот параметр не задан, то размер стека потоков HCD узлов USBX задается равным **UX_THREAD_STACK_SIZE**.</span><span class="sxs-lookup"><span data-stu-id="d41c6-180">If this symbol I not set, the USBX host HCD thread stack size is set to **UX_THREAD_STACK_SIZE**.</span></span>
- <span data-ttu-id="d41c6-181">**UX_THREAD_PRIORITY_ENUM**: это значение приоритета ThreadX для потоков перечисления USBX, которые отслеживают топологию шины.</span><span class="sxs-lookup"><span data-stu-id="d41c6-181">**UX_THREAD_PRIORITY_ENUM**: This is the ThreadX priority value for the USBX enumeration threads that monitors the bus topology.</span></span>
- <span data-ttu-id="d41c6-182">**UX_THREAD_PRIORITY_CLASS**: это значение приоритета ThreadX для стандартных потоков USBX.</span><span class="sxs-lookup"><span data-stu-id="d41c6-182">**UX_THREAD_PRIORITY_CLASS**: This is the ThreadX priority value for the standard USBX threads.</span></span>
- <span data-ttu-id="d41c6-183">**UX_THREAD_PRIORITY_KEYBOARD**: это значение приоритета ThreadX для класса HID-клавиатур USBX.</span><span class="sxs-lookup"><span data-stu-id="d41c6-183">**UX_THREAD_PRIORITY_KEYBOARD**: This is the ThreadX priority value for the USBX HID keyboard class.</span></span>
- <span data-ttu-id="d41c6-184">**UX_THREAD_PRIORITY_HCD**: это значение приоритета ThreadX для потока хост-контроллера.</span><span class="sxs-lookup"><span data-stu-id="d41c6-184">**UX_THREAD_PRIORITY_HCD**: This is the ThreadX priority value for the host controller thread.</span></span>
- <span data-ttu-id="d41c6-185">**UX_NO_TIME_SLICE**: это значение фактически определяет временной срез, который будет использоваться для потоков.</span><span class="sxs-lookup"><span data-stu-id="d41c6-185">**UX_NO_TIME_SLICE**: This value actually defines the time slice that will be used for threads.</span></span> <span data-ttu-id="d41c6-186">Например, если задано значение 0, то целевой порт ThreadX не будет использовать временные срезы.</span><span class="sxs-lookup"><span data-stu-id="d41c6-186">For example, if defined to 0, the ThreadX target port does not use time slices.</span></span>
- <span data-ttu-id="d41c6-187">**UX_MAX_HOST_LUN**: это значение представляет максимальное число логических устройств SCSI, представленных в драйвере класса хранилищ узла.</span><span class="sxs-lookup"><span data-stu-id="d41c6-187">**UX_MAX_HOST_LUN**: This value represents the maximum number of SCSI logical units represented in the host storage class driver.</span></span>
- <span data-ttu-id="d41c6-188">**UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: если этот параметр определен, то он включает в себя код для работы с устройствами хранения, использующими протокол CB или CBI (например, это могут быть гибкие диски).</span><span class="sxs-lookup"><span data-stu-id="d41c6-188">**UX_HOST_CLASS_STORAGE_INCLUDE_LEGACY_PROTOCOL_SUPPORT**: If defined, this value includes code to handle storage devices that use the CB or CBI protocol (such as floppy disks).</span></span> <span data-ttu-id="d41c6-189">По умолчанию он отключен, так как эти протоколы устарели. Их заменил протокол BOT, который используют практически все современные устройства хранения.</span><span class="sxs-lookup"><span data-stu-id="d41c6-189">It is off by default because these protocols are obsolete, being superseded by the Bulk Only Transport (BOT protocol, which virtually all modern storage devices use.</span></span>
- <span data-ttu-id="d41c6-190">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: если этот параметр определен, то служба ux_host_class_hid_keyboard_key_get будет сообщать только об изменениях состояния клавиш, то есть об их нажатии и отпускании.</span><span class="sxs-lookup"><span data-stu-id="d41c6-190">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**: If defined, this value causes ux_host_class_hid_keyboard_key_get to only report key changes that is, key presses and key releases.</span></span> <span data-ttu-id="d41c6-191">По умолчанию она сообщает только о нажатии клавиш.</span><span class="sxs-lookup"><span data-stu-id="d41c6-191">By default, it only reports when a key is down.</span></span>
- <span data-ttu-id="d41c6-192">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: используется, только если определен параметр **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**.</span><span class="sxs-lookup"><span data-stu-id="d41c6-192">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_KEY_DOWN_ONLY**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="d41c6-193">Если этот параметр определен, то служба ux_host_class_hid_keyboard_key_get сообщает только о нажатии клавиш, но не об их отпускании.</span><span class="sxs-lookup"><span data-stu-id="d41c6-193">If defined, causes ux_host_class_hid_keyboard_key_get to only report key pressed/down changes; key released/up changes are not reported.</span></span>
- <span data-ttu-id="d41c6-194">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS**: используется, только если определен параметр **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**.</span><span class="sxs-lookup"><span data-stu-id="d41c6-194">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_LOCK_KEYS**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="d41c6-195">Если этот параметр определен, то служба ux_host_class_hid_keyboard_key_get сообщает об изменения состояния клавиш переключения режима (CAPS LOCK, NUM LOCK, SCROLL LOCK).</span><span class="sxs-lookup"><span data-stu-id="d41c6-195">If defined, causes ux_host_class_hid_keyboard_key_get to report lock key (CapsLock/NumLock/ScrollLock) changes.</span></span>
- <span data-ttu-id="d41c6-196">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: используется, только если определен параметр **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE**.</span><span class="sxs-lookup"><span data-stu-id="d41c6-196">**UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE_REPORT_MODIFIER_KEYS**: Only used if **UX_HOST_CLASS_HID_KEYBOARD_EVENTS_KEY_CHANGES_MODE** is defined.</span></span> <span data-ttu-id="d41c6-197">Если этот параметр определен, то служба ux_host_class_hid_keyboard_key_get сообщает об изменении состояния клавиш-модификаторов (CTRL, ALT, SHIFT, GUI).</span><span class="sxs-lookup"><span data-stu-id="d41c6-197">If defined, causes ux_host_class_hid_keyboard_key_get to report modifier key (Ctrl/Alt/Shift/GUI) changes.</span></span>
- <span data-ttu-id="d41c6-198">**UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: если этот параметр определен, его значение представляет количество пакетов в классе узлов CDC-ECM.</span><span class="sxs-lookup"><span data-stu-id="d41c6-198">**UX_HOST_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**: If defined, this value represents the number of packets in the CDC-ECM host class.</span></span> <span data-ttu-id="d41c6-199">Значение по умолчанию равно 16.</span><span class="sxs-lookup"><span data-stu-id="d41c6-199">The default is 16.</span></span>

## <a name="source-code-tree"></a><span data-ttu-id="d41c6-200">Дерево исходного кода</span><span class="sxs-lookup"><span data-stu-id="d41c6-200">Source Code Tree</span></span>

<span data-ttu-id="d41c6-201">Файлы USBX предоставлены в нескольких каталогах.</span><span class="sxs-lookup"><span data-stu-id="d41c6-201">The USBX files are provided in several directories.</span></span>

![Дерево исходного кода](media/usbx-host-stack/source-code-tree.png)

<span data-ttu-id="d41c6-203">Чтобы файлы можно было распознавать по именам, принято приведенное ниже соглашение.</span><span class="sxs-lookup"><span data-stu-id="d41c6-203">In order to make the files recognizable by their names, the following convention has been adopted:</span></span>

| <span data-ttu-id="d41c6-204">Имя суффикса файла</span><span class="sxs-lookup"><span data-stu-id="d41c6-204">File Suffix Name</span></span> | <span data-ttu-id="d41c6-205">Описание файла</span><span class="sxs-lookup"><span data-stu-id="d41c6-205">File description</span></span>                          |
| ---------------- | ----------------------------------------- |
| <span data-ttu-id="d41c6-206">ux_host_stack</span><span class="sxs-lookup"><span data-stu-id="d41c6-206">ux_host_stack</span></span>    | <span data-ttu-id="d41c6-207">Основные файлы стека узлов USBX</span><span class="sxs-lookup"><span data-stu-id="d41c6-207">usbx host stack core files</span></span>                |
| <span data-ttu-id="d41c6-208">ux_host_class</span><span class="sxs-lookup"><span data-stu-id="d41c6-208">ux_host_class</span></span>    | <span data-ttu-id="d41c6-209">Файлы классов стека узлов USBX</span><span class="sxs-lookup"><span data-stu-id="d41c6-209">usbx host stack classes files</span></span>             |
| <span data-ttu-id="d41c6-210">ux_hcd</span><span class="sxs-lookup"><span data-stu-id="d41c6-210">ux_hcd</span></span>           | <span data-ttu-id="d41c6-211">Файлы драйвера контроллера стека узлов USBX</span><span class="sxs-lookup"><span data-stu-id="d41c6-211">usbx host stack controller driver files</span></span>   |
| <span data-ttu-id="d41c6-212">ux_device_stack</span><span class="sxs-lookup"><span data-stu-id="d41c6-212">ux_device_stack</span></span>  | <span data-ttu-id="d41c6-213">Основные файлы стека устройств USBX</span><span class="sxs-lookup"><span data-stu-id="d41c6-213">usbx device stack core files</span></span>              |
| <span data-ttu-id="d41c6-214">ux_device_class</span><span class="sxs-lookup"><span data-stu-id="d41c6-214">ux_device_class</span></span>  | <span data-ttu-id="d41c6-215">Файлы классов стека устройств USBX</span><span class="sxs-lookup"><span data-stu-id="d41c6-215">usbx device stack classes files</span></span>           |
| <span data-ttu-id="d41c6-216">ux_dcd</span><span class="sxs-lookup"><span data-stu-id="d41c6-216">ux_dcd</span></span>           | <span data-ttu-id="d41c6-217">Файлы драйвера контроллера стека устройств USBX</span><span class="sxs-lookup"><span data-stu-id="d41c6-217">usbx device stack controller driver files</span></span> |
| <span data-ttu-id="d41c6-218">ux_otg</span><span class="sxs-lookup"><span data-stu-id="d41c6-218">ux_otg</span></span>           | <span data-ttu-id="d41c6-219">Файлы, связанные с драйвером контроллера OTG для USBX</span><span class="sxs-lookup"><span data-stu-id="d41c6-219">usbx otg controller driver related files</span></span>  |
| <span data-ttu-id="d41c6-220">ux_pictbridge</span><span class="sxs-lookup"><span data-stu-id="d41c6-220">ux_pictbridge</span></span>    | <span data-ttu-id="d41c6-221">Файлы PictBridge для USBX</span><span class="sxs-lookup"><span data-stu-id="d41c6-221">usbx pictbridge files</span></span>                     |
| <span data-ttu-id="d41c6-222">ux_utility</span><span class="sxs-lookup"><span data-stu-id="d41c6-222">ux_utility</span></span>       | <span data-ttu-id="d41c6-223">Служебные функции USBX</span><span class="sxs-lookup"><span data-stu-id="d41c6-223">usbx utility functions</span></span>                    |
| <span data-ttu-id="d41c6-224">demo_usbx</span><span class="sxs-lookup"><span data-stu-id="d41c6-224">demo_usbx</span></span>        | <span data-ttu-id="d41c6-225">Демонстрационные файлы для USBX</span><span class="sxs-lookup"><span data-stu-id="d41c6-225">demonstration files for USBX</span></span>              |

## <a name="initialization-of-usbx-resources"></a><span data-ttu-id="d41c6-226">Инициализация ресурсов USBX</span><span class="sxs-lookup"><span data-stu-id="d41c6-226">Initialization of USBX resources</span></span>

<span data-ttu-id="d41c6-227">В USBX имеется собственный диспетчер памяти.</span><span class="sxs-lookup"><span data-stu-id="d41c6-227">USBX has its own memory manager.</span></span> <span data-ttu-id="d41c6-228">Память для USBX необходимо выделить перед инициализацией узла или устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="d41c6-228">The memory needs to be allocated to USBX before the host or device side of USBX is initialized.</span></span> <span data-ttu-id="d41c6-229">Диспетчер памяти USBX поддерживает системы с кэшированием памяти.</span><span class="sxs-lookup"><span data-stu-id="d41c6-229">USBX memory manager can accommodate systems where memory can be cached.</span></span>

<span data-ttu-id="d41c6-230">Приведенная ниже функция инициализирует ресурсы памяти USBX: 128 КБ обычной памяти без отдельного пула для некэшируемой памяти:</span><span class="sxs-lookup"><span data-stu-id="d41c6-230">The following function initializes USBX memory resources with 128K of regular memory and no separate pool for cache safe memory:</span></span>

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

<span data-ttu-id="d41c6-231">Прототип для ux_system_initialize выглядит показан ниже.</span><span class="sxs-lookup"><span data-stu-id="d41c6-231">The prototype for the ux_system_initialize is as follows.</span></span>

```c
UINT ux_system_initialize( 
    VOID *regular_memory_pool_start,
    ULONG regular_memory_size,
    VOID *cache_safe_memory_pool_start,
    ULONG cache_safe_memory_size);
```

### <a name="input-parameters"></a><span data-ttu-id="d41c6-232">Входные параметры:</span><span class="sxs-lookup"><span data-stu-id="d41c6-232">Input parameters:</span></span>

- <span data-ttu-id="d41c6-233">**regular_memory_pool_start**: начало обычного пула памяти.</span><span class="sxs-lookup"><span data-stu-id="d41c6-233">**regular_memory_pool_start** Beginning of the regular memory pool.</span></span>
- <span data-ttu-id="d41c6-234">**regular_memory_size**: размер обычного пула памяти.</span><span class="sxs-lookup"><span data-stu-id="d41c6-234">**regular_memory_size** Size of the regular memory pool.</span></span>
- <span data-ttu-id="d41c6-235">**cache_safe_memory_pool_start**: начало пула некэшируемой памяти.</span><span class="sxs-lookup"><span data-stu-id="d41c6-235">**cache_safe_memory_pool_start** Beginning of the cache safe memory pool.</span></span>
- <span data-ttu-id="d41c6-236">**cache_safe_memory_size**: размер пула некэшируемой памяти.</span><span class="sxs-lookup"><span data-stu-id="d41c6-236">**cache_safe_memory_size** Size of the cache safe memory pool.</span></span>    |

<span data-ttu-id="d41c6-237">Не для всех систем нужно определять некэшируемую память.</span><span class="sxs-lookup"><span data-stu-id="d41c6-237">Not all systems require the definition of cache safe memory.</span></span> <span data-ttu-id="d41c6-238">В такой системе во время инициализации для указателя памяти будут переданы значения UX_NULL, а размер пула будет равен 0.</span><span class="sxs-lookup"><span data-stu-id="d41c6-238">In such a system, the values passed during the initialization for the memory pointer will be set to UX_NULL and the size of the pool to 0.</span></span> <span data-ttu-id="d41c6-239">После этого USBX будет использовать стандартный пул памяти вместо некэшируемого пула.</span><span class="sxs-lookup"><span data-stu-id="d41c6-239">USBX will then use the regular memory pool in lieu of the cache safe pool.</span></span>

<span data-ttu-id="d41c6-240">В системе, где обычная память не является некэшируемой и для контроллера требуется память с прямым доступом (например, контроллеры OHCI, EHCI и пр.), необходимо определить пул памяти в некэшируемой зоне.</span><span class="sxs-lookup"><span data-stu-id="d41c6-240">In a system where the regular memory is not cache safe and a controller requires to perform DMA memory (like OHCI, EHCI controllers amongst others) it is necessary to define a memory pool in a cache safe zone.</span></span>

## <a name="uninitialization-of-usbx-resources"></a><span data-ttu-id="d41c6-241">Отмена инициализации ресурсов USBX</span><span class="sxs-lookup"><span data-stu-id="d41c6-241">Uninitialization of USBX resources</span></span>

<span data-ttu-id="d41c6-242">Работу экземпляра USBX можно завершить, освободив его ресурсы.</span><span class="sxs-lookup"><span data-stu-id="d41c6-242">USBX can be terminated by releasing its resources.</span></span> <span data-ttu-id="d41c6-243">Перед завершением экземпляра USBX нужно правильно завершить все ресурсы классов и контроллеров.</span><span class="sxs-lookup"><span data-stu-id="d41c6-243">Prior to terminating usbx, all classes and controller resources need to be terminated properly.</span></span> <span data-ttu-id="d41c6-244">Приведенная ниже функция отменяет инициализацию ресурсов памяти USBX.</span><span class="sxs-lookup"><span data-stu-id="d41c6-244">The following function uninitializes USBX memory resources :</span></span>

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

<span data-ttu-id="d41c6-245">Прототип для ux_system_initialize выглядит показан ниже.</span><span class="sxs-lookup"><span data-stu-id="d41c6-245">The prototype for the ux_system_initialize is as follows.</span></span>

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-host-controllers"></a><span data-ttu-id="d41c6-246">Определение хост-контроллеров USB</span><span class="sxs-lookup"><span data-stu-id="d41c6-246">Definition of USB Host Controllers</span></span>

<span data-ttu-id="d41c6-247">Для работы USBX в режиме узла необходимо определить по крайней мере один хост-контроллер USB.</span><span class="sxs-lookup"><span data-stu-id="d41c6-247">It is required to define at least one USB host controller for USBX to operate in host mode.</span></span> <span data-ttu-id="d41c6-248">Это определение должно находиться в файле инициализации приложения.</span><span class="sxs-lookup"><span data-stu-id="d41c6-248">The application initialization file should contain this definition.</span></span> <span data-ttu-id="d41c6-249">Следующая строка выполняет определение универсального хост-контроллера.</span><span class="sxs-lookup"><span data-stu-id="d41c6-249">The following line performs the definition of a generic host controller.</span></span>

```c
ux_host_stack_hcd_register("ux_hcd_controller",
        ux_hcd_controller_initialize, 0xd0000, 0x0a);
```

<span data-ttu-id="d41c6-250">Прототип ux_host_stack_hcd_register приведен ниже.</span><span class="sxs-lookup"><span data-stu-id="d41c6-250">The ux_host_stack_hcd_register has the following prototype.</span></span>

```c
UINT ux_host_stack_hcd_register(
    UCHAR *hcd_name,
    UINT (*hcd_initialize_function)(struct UX_HCD_STRUCT *),
    ULONG hcd_param1, ULONG hcd_param2);
```

<span data-ttu-id="d41c6-251">Функция ux_host_stack_hcd_register использует следующие параметры.</span><span class="sxs-lookup"><span data-stu-id="d41c6-251">The ux_host_stack_hcd_register function has the following parameters.</span></span>

- <span data-ttu-id="d41c6-252">**hcd_name**: строка имени контроллера.</span><span class="sxs-lookup"><span data-stu-id="d41c6-252">**hcd_name**: string of the controller name</span></span>
- <span data-ttu-id="d41c6-253">**hcd_initialize_function**: функция инициализации контроллера.</span><span class="sxs-lookup"><span data-stu-id="d41c6-253">**hcd_initialize_function**: initialization function of the controller</span></span>
- <span data-ttu-id="d41c6-254">**hcd_param1**: обычно это значение ввода-вывода или объем памяти, используемой контроллером.</span><span class="sxs-lookup"><span data-stu-id="d41c6-254">**hcd_param1**: usually the IO value or Memory used by the controller</span></span>
- <span data-ttu-id="d41c6-255">**hcd_param2**: обычно это значение IRQ, используемое контроллером.</span><span class="sxs-lookup"><span data-stu-id="d41c6-255">**hcd_param2**: usually the IRQ used by the controller</span></span>

<span data-ttu-id="d41c6-256">В предыдущем примере:</span><span class="sxs-lookup"><span data-stu-id="d41c6-256">In our previous example:</span></span>

- <span data-ttu-id="d41c6-257">ux_hcd_controller: имя контроллера.</span><span class="sxs-lookup"><span data-stu-id="d41c6-257">"ux_hcd_controller" is the name of the controller</span></span>
- <span data-ttu-id="d41c6-258">ux_hcd_controller_initialize: подпрограмма инициализации хост-контроллера.</span><span class="sxs-lookup"><span data-stu-id="d41c6-258">"ux_hcd_controller_initialize" is the initialization routine for the host controller</span></span>
- <span data-ttu-id="d41c6-259">0xd0000 — это адрес, по которому регистры хост-контроллера отображаются в памяти.</span><span class="sxs-lookup"><span data-stu-id="d41c6-259">0xd0000 is the address at which the host controller registers are visible in memory</span></span>
- <span data-ttu-id="d41c6-260">0x0A — это значение IRQ, используемое хост-контроллером.</span><span class="sxs-lookup"><span data-stu-id="d41c6-260">and 0x0a is the IRQ used by the host controller.</span></span>

<span data-ttu-id="d41c6-261">Ниже приведен пример инициализации USBX в режиме узла с одним хост-контроллером и несколькими классами.</span><span class="sxs-lookup"><span data-stu-id="d41c6-261">Following is an example of the initialization of USBX in host mode with one host controller and several classes.</span></span>

```c
UINT status;

/* Initialize USBX. */
ux_system_initialize(memory_ptr, (128*1024),0,0);

/* The code below is required for installing the USBX host stack. */
status = ux_host_stack_initialize(UX_NULL);

/* If status equals UX_SUCCESS, host stack has been initialized. */

/* Register all the host classes for this USBX implementation. */
status = ux_host_class_register("ux_host_class_hub", ux_host_class_hub_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_storage", ux_host_class_storage_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_printer", ux_host_class_printer_entry);

/* If status equals UX_SUCCESS, host class has been registered. */
status = ux_host_class_register("ux_host_class_audio", ux_host_class_audio_entry);

/* If status equals UX_SUCCESS, host class has been registered. */

/* Register all the USB host controllers available in this system. */ 
status = ux_host_stack_hcd_register("ux_hcd_controller", ux_hcd_controller_initialize, 0x300000, 0x0a);

/* If status equals UX_SUCCESS, USB host controllers have been registered. */
```

## <a name="definition-of-host-classes"></a><span data-ttu-id="d41c6-262">Определение классов узлов</span><span class="sxs-lookup"><span data-stu-id="d41c6-262">Definition of Host Classes</span></span>

<span data-ttu-id="d41c6-263">Необходимо определить один или несколько классов узлов с помощью USBX.</span><span class="sxs-lookup"><span data-stu-id="d41c6-263">It is required to define one or more host classes with USBX.</span></span> <span data-ttu-id="d41c6-264">Класс USB необходим для управления USB-устройством после того, как оно будет настроено в стеке USB.</span><span class="sxs-lookup"><span data-stu-id="d41c6-264">A USB class is required to drive a USB device after the USB stack has configured the USB device.</span></span> <span data-ttu-id="d41c6-265">Класс USB зависит от устройства.</span><span class="sxs-lookup"><span data-stu-id="d41c6-265">A USB class is specific to the device.</span></span> <span data-ttu-id="d41c6-266">Для работы с USB-устройством может потребоваться один или несколько классов в зависимости от числа интерфейсов, указанных в дескрипторах USB-устройства.</span><span class="sxs-lookup"><span data-stu-id="d41c6-266">One or more classes may be required to drive a USB device depending on the number of interfaces contained in the USB device descriptors.</span></span>

<span data-ttu-id="d41c6-267">Ниже приведен пример регистрации класса концентраторов.</span><span class="sxs-lookup"><span data-stu-id="d41c6-267">This is an example of the registration of the HUB class.</span></span>

```c
status = ux_host_stack_class_register("ux_host_class_hub", ux_host_class_hub_entry);
```

<span data-ttu-id="d41c6-268">Ниже приведен прототип функции ux_host_class_register.</span><span class="sxs-lookup"><span data-stu-id="d41c6-268">The function ux_host_class_register has the following prototype.</span></span>

```c
UINT ux_host_stack_class_register(
    UCHAR *class_name, 
    UINT (*class_entry_address) (struct UX_HOST_CLASS_COMMAND_STRUCT *));
```

- <span data-ttu-id="d41c6-269">**class_name**: имя класса.</span><span class="sxs-lookup"><span data-stu-id="d41c6-269">**class_name** is the name of the class</span></span>
- <span data-ttu-id="d41c6-270">**class_entry_address**: точка входа класса.</span><span class="sxs-lookup"><span data-stu-id="d41c6-270">**class_entry_address** is the entry point of the class</span></span>

<span data-ttu-id="d41c6-271">В примере инициализации класса концентраторов:</span><span class="sxs-lookup"><span data-stu-id="d41c6-271">In the example of the HUB class initialization:</span></span>

- <span data-ttu-id="d41c6-272">ux_host_class_hub: имя класса концентратора;</span><span class="sxs-lookup"><span data-stu-id="d41c6-272">"ux_host_class_hub" is the name of the hub class</span></span>
- <span data-ttu-id="d41c6-273">ux_host_class_hub_entry: точка входа класса концентраторов.</span><span class="sxs-lookup"><span data-stu-id="d41c6-273">ux_host_class_hub_entry is the entry point of the HUB class.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="d41c6-274">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="d41c6-274">Troubleshooting</span></span>

<span data-ttu-id="d41c6-275">USBX поставляется с демонстрационным файлом и окружением моделирования.</span><span class="sxs-lookup"><span data-stu-id="d41c6-275">USBX is delivered with a demonstration file and a simulation environment.</span></span> <span data-ttu-id="d41c6-276">Рекомендуется сначала запустить демонстрационную систему — на целевом оборудовании или соответствующей демонстрационной платформе.</span><span class="sxs-lookup"><span data-stu-id="d41c6-276">It is always a good idea to get the demonstration platform running first—either on the target hardware or a specific demonstration platform.</span></span>

<span data-ttu-id="d41c6-277">Если демонстрационная система не работает, попробуйте выполнить приведенные ниже действия, чтобы устранить проблему.</span><span class="sxs-lookup"><span data-stu-id="d41c6-277">If the demonstration system does not work, try the following things to narrow the problem.</span></span>

## <a name="usbx-version-id"></a><span data-ttu-id="d41c6-278">Идентификатор версии USBX</span><span class="sxs-lookup"><span data-stu-id="d41c6-278">USBX Version ID</span></span>

<span data-ttu-id="d41c6-279">Сведения о текущей версии USBX доступны во время выполнения как пользователю, так и программному обеспечению приложения.</span><span class="sxs-lookup"><span data-stu-id="d41c6-279">The current version of USBX is available both to the user and the application software during run-time.</span></span> <span data-ttu-id="d41c6-280">Программист может получить данные о версии USBX, ознакомившись с файлом \***ux_port.h** _.</span><span class="sxs-lookup"><span data-stu-id="d41c6-280">The programmer can obtain the USBX version from examination of the \***ux_port.h** _ file.</span></span> <span data-ttu-id="d41c6-281">Кроме того, этот файл содержит журнал версий для соответствующей платформы.</span><span class="sxs-lookup"><span data-stu-id="d41c6-281">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="d41c6-282">Программное обеспечение приложения может получить версию USBX, проанализировав глобальную строку _ *_ _ux_version_id_* _, которая определена в файле _\*_ux_port.h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="d41c6-282">Application software can obtain the USBX version by examining the global string _ *_ _ux_version_id_* _, which is defined in _\*_ux_port.h_\*\*.</span></span>
