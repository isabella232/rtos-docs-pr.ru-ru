---
title: Глава 2. Установка стека устройства USBX в ОСРВ Azure
description: Сведения об установке стека устройства USBX в ОСРВ Azure, а также важные рекомендации по размещению, которые необходимо учитывать перед установкой.
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: dd58f77130fa252be9163bd70c29f7deee400d30
ms.sourcegitcommit: 60ad844b58639d88830f2660ab0c4ff86b92c10f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/07/2021
ms.locfileid: "106549782"
---
# <a name="chapter-2---azure-rtos-usbx-device-stack-installation"></a><span data-ttu-id="eca4a-103">Глава 2. Установка стека устройства USBX в ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="eca4a-103">Chapter 2 - Azure RTOS USBX Device Stack Installation</span></span>

## <a name="host-considerations"></a><span data-ttu-id="eca4a-104">Рекомендации по размещению</span><span class="sxs-lookup"><span data-stu-id="eca4a-104">Host Considerations</span></span>

### <a name="computer-type"></a><span data-ttu-id="eca4a-105">Тип компьютера</span><span class="sxs-lookup"><span data-stu-id="eca4a-105">Computer Type</span></span>

<span data-ttu-id="eca4a-106">Разработка внедренных решений обычно выполняется на главных компьютерах с Windows или Unix.</span><span class="sxs-lookup"><span data-stu-id="eca4a-106">Embedded development is usually performed on Windows PC or Unix host computers.</span></span> <span data-ttu-id="eca4a-107">После компиляции, связывания и размещения на узле приложение скачивается на целевое оборудование для выполнения.</span><span class="sxs-lookup"><span data-stu-id="eca4a-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

### <a name="download-interfaces"></a><span data-ttu-id="eca4a-108">Интерфейсы скачивания</span><span class="sxs-lookup"><span data-stu-id="eca4a-108">Download Interfaces</span></span>

<span data-ttu-id="eca4a-109">Как правило, скачивание на целевое оборудование выполняется через последовательный интерфейс RS-232, хотя становятся все более популярными параллельные интерфейсы, USB и Ethernet.</span><span class="sxs-lookup"><span data-stu-id="eca4a-109">Usually the target download is done over an RS-232 serial interface, although parallel interfaces, USB, and Ethernet are becoming more popular.</span></span> <span data-ttu-id="eca4a-110">Доступные варианты представлены в документации по инструменту разработки.</span><span class="sxs-lookup"><span data-stu-id="eca4a-110">See the development tool documentation for available options.</span></span>

### <a name="debugging-tools"></a><span data-ttu-id="eca4a-111">Инструменты отладки</span><span class="sxs-lookup"><span data-stu-id="eca4a-111">Debugging Tools</span></span>

<span data-ttu-id="eca4a-112">Отладка обычно выполняется по той же ссылке, что и скачивание образа программы.</span><span class="sxs-lookup"><span data-stu-id="eca4a-112">Debugging is done typically over the same link as the program image download.</span></span> <span data-ttu-id="eca4a-113">Существует множество отладчиков, от небольших программ мониторинга, выполняющихся на целевом объекте, до инструментов Background Debug Monitor (BDM) и In-Circuit Emulator (ICE).</span><span class="sxs-lookup"><span data-stu-id="eca4a-113">A variety of debuggers exist, ranging from small monitor programs running on the target through Background Debug Monitor (BDM) and In-Circuit Emulator (ICE) tools.</span></span> <span data-ttu-id="eca4a-114">Инструмент ICE обеспечивает наиболее надежную отладку фактического целевого оборудования.</span><span class="sxs-lookup"><span data-stu-id="eca4a-114">The ICE tool provides the most robust debugging of actual target hardware.</span></span>

### <a name="required-hard-disk-space"></a><span data-ttu-id="eca4a-115">Требуемое место на жестком диске</span><span class="sxs-lookup"><span data-stu-id="eca4a-115">Required Hard Disk Space</span></span>

<span data-ttu-id="eca4a-116">Исходный код USBX поставляется в формате ASCII и требует примерно 500 КБ пространства на жестком диске главного компьютера.</span><span class="sxs-lookup"><span data-stu-id="eca4a-116">The source code for USBX is delivered in ASCII format and requires approximately 500 KBytes of space on the host computer's hard disk.</span></span>

### <a name="target-considerations"></a><span data-ttu-id="eca4a-117">Рекомендации по целевому оборудованию</span><span class="sxs-lookup"><span data-stu-id="eca4a-117">Target Considerations</span></span>

<span data-ttu-id="eca4a-118">Для USBX требуется от 24 до 64 КБ доступной только для чтения памяти (ПЗУ) на целевом оборудовании в режиме узла.</span><span class="sxs-lookup"><span data-stu-id="eca4a-118">USBX requires between 24 KBytes and 64 KBytes of Read Only Memory (ROM) on the target in host mode.</span></span> <span data-ttu-id="eca4a-119">Необходимый объем памяти зависит от типа используемого контроллера и классов USB, связанных с USBX.</span><span class="sxs-lookup"><span data-stu-id="eca4a-119">The amount of memory required is dependent on the type of controller used and the USB classes linked to USBX.</span></span> <span data-ttu-id="eca4a-120">Для глобальных структур данных и пула памяти USBX требуется еще 32 КБ памяти (ОЗУ) на целевом оборудовании.</span><span class="sxs-lookup"><span data-stu-id="eca4a-120">Another 32 KBytes of the target's Random Access Memory (RAM) are required for USBX global data structures and memory pool.</span></span> <span data-ttu-id="eca4a-121">Этот пул памяти также может быть скорректирован в зависимости от ожидаемого количества устройств на шине USB и типа контроллера USB.</span><span class="sxs-lookup"><span data-stu-id="eca4a-121">This memory pool can also be adjusted depending on the expected number of devices on the USB and the type of USB controller.</span></span> <span data-ttu-id="eca4a-122">На стороне устройства USBX требуется примерно 10–12 КБ ПЗУ, в зависимости от типа контроллера устройства.</span><span class="sxs-lookup"><span data-stu-id="eca4a-122">The USBX device side requires roughly 10-12 K of ROM depending on the type of device controller.</span></span> <span data-ttu-id="eca4a-123">Использование памяти ОЗУ зависит от типа класса, эмулируемого устройством.</span><span class="sxs-lookup"><span data-stu-id="eca4a-123">The RAM memory usage depends on the type of class emulated by the device.</span></span>

<span data-ttu-id="eca4a-124">USBX также использует семафоры, мьютексы и потоки ThreadX для защиты многопоточности, как и приостановку ввода-вывода и периодическую обработку для мониторинга топологии шины USB.</span><span class="sxs-lookup"><span data-stu-id="eca4a-124">USBX also relies on ThreadX semaphores, mutexes, and threads for multiple thread protection, and I/O suspension and periodic processing for monitoring the USB bus topology.</span></span>

### <a name="product-distribution"></a><span data-ttu-id="eca4a-125">Дистрибутивы продукта</span><span class="sxs-lookup"><span data-stu-id="eca4a-125">Product Distribution</span></span>

<span data-ttu-id="eca4a-126">ОСРВ Azure USBX можно получить из нашего репозитория общедоступного исходного кода по адресу <https://github.com/azure-rtos/usbx/>.</span><span class="sxs-lookup"><span data-stu-id="eca4a-126">Azure RTOS USBX can be obtained from our public source code repository at <https://github.com/azure-rtos/usbx/>.</span></span>

<span data-ttu-id="eca4a-127">Ниже приведен список основных файлов в этом репозитории.</span><span class="sxs-lookup"><span data-stu-id="eca4a-127">The following is a list of several important files in the repository.</span></span>

* <span data-ttu-id="eca4a-128">***ux_api.h*** — это файл заголовка C, который содержит все системные равенства, структуры данных и прототипы служб.</span><span class="sxs-lookup"><span data-stu-id="eca4a-128">***ux_api.h***: This C header file contains all system equates, data structures, and service prototypes.</span></span>
* <span data-ttu-id="eca4a-129">***ux_port.h*** — это файл заголовка C, который содержит все определения и структуры данных, относящиеся к конкретным инструментам разработки.</span><span class="sxs-lookup"><span data-stu-id="eca4a-129">***ux_port.h***: This C header file contains all development-tool-specific data definitions and structures.</span></span>
* <span data-ttu-id="eca4a-130">***ux.lib*** — это двоичная версия библиотеки C для USBX.</span><span class="sxs-lookup"><span data-stu-id="eca4a-130">***ux.lib***:  This is the binary version of the USBX C library.</span></span> <span data-ttu-id="eca4a-131">Она распространяется с помощью стандартного пакета.</span><span class="sxs-lookup"><span data-stu-id="eca4a-131">It is distributed with the standard package.</span></span>
* <span data-ttu-id="eca4a-132">***demo_usbx.c*** — это файл C, содержащий простую демоверсию для USBX.</span><span class="sxs-lookup"><span data-stu-id="eca4a-132">***demo_usbx.c***: The C file containing a simple USBX demo</span></span>

<span data-ttu-id="eca4a-133">Все имена файлов указаны в нижнем регистре.</span><span class="sxs-lookup"><span data-stu-id="eca4a-133">All filenames are in lower-case.</span></span> <span data-ttu-id="eca4a-134">Такое соглашение об именовании упрощает преобразование команд для платформ разработки UNIX.</span><span class="sxs-lookup"><span data-stu-id="eca4a-134">This naming convention makes it easier to convert the commands to Unix development platforms.</span></span>

## <a name="usbx-installation"></a><span data-ttu-id="eca4a-135">Установка USBX</span><span class="sxs-lookup"><span data-stu-id="eca4a-135">USBX Installation</span></span>

<span data-ttu-id="eca4a-136">USBX устанавливается путем клонирования репозитория GitHub на локальный компьютер.</span><span class="sxs-lookup"><span data-stu-id="eca4a-136">USBX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="eca4a-137">Ниже приведен типичный синтаксис для создания клона репозитория USBX на вашем компьютере.</span><span class="sxs-lookup"><span data-stu-id="eca4a-137">The following is typical syntax for creating a clone of the USBX repository on your PC:</span></span>

```c
    git clone https://github.com/azure-rtos/usbx
```

<span data-ttu-id="eca4a-138">Вы также можете скачать копию репозитория с помощью соответствующей кнопки на главной странице GitHub.</span><span class="sxs-lookup"><span data-stu-id="eca4a-138">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="eca4a-139">Кроме того, вы можете найти инструкции по созданию библиотеки USBX на главной странице веб-репозитория.</span><span class="sxs-lookup"><span data-stu-id="eca4a-139">You will also find instructions for building the USBX library on the front page of the online repository.</span></span>

<span data-ttu-id="eca4a-140">Приведенные ниже общие инструкции применимы практически к любой установке.</span><span class="sxs-lookup"><span data-stu-id="eca4a-140">The following general instructions apply to virtually any installation:</span></span>

1. <span data-ttu-id="eca4a-141">Используйте тот же каталог на жестком диске узла, в который вы ранее установили ThreadX.</span><span class="sxs-lookup"><span data-stu-id="eca4a-141">Use the same directory in which you previously installed ThreadX on the host hard drive.</span></span> <span data-ttu-id="eca4a-142">Все имена USBX уникальны и не повлияют на предыдущую установку USBX.</span><span class="sxs-lookup"><span data-stu-id="eca4a-142">All USBX names are unique and will not interfere with the previous USBX installation.</span></span>
1. <span data-ttu-id="eca4a-143">Добавьте вызов ***ux_system_initialize** _ в начало _*_tx_application_define_\*\* или рядом.</span><span class="sxs-lookup"><span data-stu-id="eca4a-143">Add a call to ***ux_system_initialize** _ at or near the beginning of _*_tx_application_define_\*\*.</span></span> <span data-ttu-id="eca4a-144">Именно здесь инициализируются ресурсы USBX.</span><span class="sxs-lookup"><span data-stu-id="eca4a-144">This is where the USBX resources are initialized.</span></span>
1. <span data-ttu-id="eca4a-145">Добавьте вызов в \***ux_device_stack_initialize\*.**</span><span class="sxs-lookup"><span data-stu-id="eca4a-145">Add a call to \***ux_device_stack_initialize\*.**</span></span>
1. <span data-ttu-id="eca4a-146">Добавьте один или несколько вызовов для инициализации требуемых классов USBX (классов узла и (или) устройств).</span><span class="sxs-lookup"><span data-stu-id="eca4a-146">Add one or more calls to initialize the required USBX classes (either host and/or devices classes)</span></span>
1. <span data-ttu-id="eca4a-147">Добавьте один или несколько вызовов для инициализации контроллера устройства, доступного в системе.</span><span class="sxs-lookup"><span data-stu-id="eca4a-147">Add one or more calls to initialize the device controller available in the system.</span></span>
1. <span data-ttu-id="eca4a-148">Возможно нужно будет изменить файл tx_low_level_initialize.c, чтобы добавить инициализацию низкого уровня для оборудования и маршрутизацию векторов прерывания.</span><span class="sxs-lookup"><span data-stu-id="eca4a-148">It may be required to modify the tx_low_level_initialize.c file to add low-level hardware initialization and interrupt vector routing.</span></span> <span data-ttu-id="eca4a-149">Это относится к особенностям аппаратной платформы и не будет рассматриваться в этом документе.</span><span class="sxs-lookup"><span data-stu-id="eca4a-149">This is specific to the hardware platform and will not be discussed here.|</span></span>
1. <span data-ttu-id="eca4a-150">Выполните компиляцию исходного кода приложения и связывание с библиотеками времени выполнения USBX и ThreadX — ux.a (или ux.lib) и tx.a (или tx.lib). Могут также потребоваться FileX и (или) NetX, если требуется скомпилировать класс хранения USB и (или) классы сети USB.</span><span class="sxs-lookup"><span data-stu-id="eca4a-150">Compile application source code and link with the USBX and ThreadX run time libraries (FileX and/or Netx may also be required if the USB storage class and/or USB network classes are to be compiled in), ux.a (or ux.lib) and tx.a (or tx.lib).</span></span> <span data-ttu-id="eca4a-151">Полученный пакет можно скачать на целевой объект и выполнить.</span><span class="sxs-lookup"><span data-stu-id="eca4a-151">The resulting can be downloaded to the target and executed!</span></span>

## <a name="configuration-options"></a><span data-ttu-id="eca4a-152">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="eca4a-152">Configuration Options</span></span>

<span data-ttu-id="eca4a-153">Существует ряд параметров конфигурации для сборки библиотеки USBX.</span><span class="sxs-lookup"><span data-stu-id="eca4a-153">There are several configuration options for building the USBX library.</span></span> <span data-ttu-id="eca4a-154">Все параметры находятся в файле ***ux_user.h***.</span><span class="sxs-lookup"><span data-stu-id="eca4a-154">All options are located in the ***ux_user.h***.</span></span>

<span data-ttu-id="eca4a-155">Каждый параметр конфигурации подробно описан в списке ниже.</span><span class="sxs-lookup"><span data-stu-id="eca4a-155">The list below details each configuration option.</span></span>

| <span data-ttu-id="eca4a-156">Параметр&nbsp;конфигурации</span><span class="sxs-lookup"><span data-stu-id="eca4a-156">Configuration&nbsp;Option</span></span> | <span data-ttu-id="eca4a-157">Описание</span><span class="sxs-lookup"><span data-stu-id="eca4a-157">Description</span></span> |
| --- | --- |
| <span data-ttu-id="eca4a-158">**UX_PERIODIC_RATE**</span><span class="sxs-lookup"><span data-stu-id="eca4a-158">**UX_PERIODIC_RATE**</span></span> | <span data-ttu-id="eca4a-159">Это значение представляет число тактов в секунду для конкретной аппаратной платформы.</span><span class="sxs-lookup"><span data-stu-id="eca4a-159">This value represents how many ticks per seconds for a specific hardware platform.</span></span> <span data-ttu-id="eca4a-160">Значение по умолчанию — 1000. Оно задает 1 такт на миллисекунду.</span><span class="sxs-lookup"><span data-stu-id="eca4a-160">The default is 1000 indicating 1 tick per millisecond.</span></span> |
| <span data-ttu-id="eca4a-161">**UX_THREAD_STACK_SIZE**</span><span class="sxs-lookup"><span data-stu-id="eca4a-161">**UX_THREAD_STACK_SIZE**</span></span> | <span data-ttu-id="eca4a-162">Это значение размера стека в байтах для потоков USBX.</span><span class="sxs-lookup"><span data-stu-id="eca4a-162">This value is the size of the stack in bytes for the USBX threads.</span></span> <span data-ttu-id="eca4a-163">Обычно это может быть 1024 байт или 2048 байт, в зависимости от используемого процессора и хост-контроллера.</span><span class="sxs-lookup"><span data-stu-id="eca4a-163">It can be typically 1024 bytes or 2048 bytes depending on the processor used and the host controller.</span></span> |
| <span data-ttu-id="eca4a-164">**UX_THREAD_PRIORITY_ENUM**</span><span class="sxs-lookup"><span data-stu-id="eca4a-164">**UX_THREAD_PRIORITY_ENUM**</span></span> | <span data-ttu-id="eca4a-165">Это значение приоритета ThreadX для потоков перечисления USBX, которые отслеживают топологию шины.</span><span class="sxs-lookup"><span data-stu-id="eca4a-165">This is the ThreadX priority value for the USBX enumeration threads that monitors the bus topology.</span></span> |
| <span data-ttu-id="eca4a-166">**UX_THREAD_PRIORITY_CLASS**</span><span class="sxs-lookup"><span data-stu-id="eca4a-166">**UX_THREAD_PRIORITY_CLASS**</span></span> | <span data-ttu-id="eca4a-167">Это значение приоритета ThreadX для стандартных потоков USBX.</span><span class="sxs-lookup"><span data-stu-id="eca4a-167">This is the ThreadX priority value for the standard USBX threads.</span></span> |
| <span data-ttu-id="eca4a-168">**UX_THREAD_PRIORITY_KEYBOARD**</span><span class="sxs-lookup"><span data-stu-id="eca4a-168">**UX_THREAD_PRIORITY_KEYBOARD**</span></span> | <span data-ttu-id="eca4a-169">Это значение приоритета ThreadX для класса HID клавиатуры USBX.</span><span class="sxs-lookup"><span data-stu-id="eca4a-169">This is the ThreadX priority value for the USBX HID keyboard class.</span></span> |
| <span data-ttu-id="eca4a-170">**UX_THREAD_PRIORITY_DCD**</span><span class="sxs-lookup"><span data-stu-id="eca4a-170">**UX_THREAD_PRIORITY_DCD**</span></span> | <span data-ttu-id="eca4a-171">Это значение приоритета ThreadX для потока контроллера устройства.</span><span class="sxs-lookup"><span data-stu-id="eca4a-171">This is the ThreadX priority value for the device controller thread.</span></span> |
| <span data-ttu-id="eca4a-172">**UX_NO_TIME_SLICE**</span><span class="sxs-lookup"><span data-stu-id="eca4a-172">**UX_NO_TIME_SLICE**</span></span> | <span data-ttu-id="eca4a-173">Это значение фактически определяет интервал времени, который будет использоваться для потоков.</span><span class="sxs-lookup"><span data-stu-id="eca4a-173">This value actually defines the time slice that will be used for threads.</span></span> <span data-ttu-id="eca4a-174">Например, если задано значение 0, то целевой порт ThreadX не будет использовать интервалы времени.</span><span class="sxs-lookup"><span data-stu-id="eca4a-174">For example, if defined to 0, the ThreadX target port does not use time slices.</span></span> |
| <span data-ttu-id="eca4a-175">**UX_MAX_SLAVE_CLASS_DRIVER**</span><span class="sxs-lookup"><span data-stu-id="eca4a-175">**UX_MAX_SLAVE_CLASS_DRIVER**</span></span> | <span data-ttu-id="eca4a-176">Это максимальное количество классов USBX, которые можно зарегистрировать с помощью ux_device_stack_class_register.</span><span class="sxs-lookup"><span data-stu-id="eca4a-176">This is the maximum number of USBX classes that can be registered via ux_device_stack_class_register.</span></span> |
| <span data-ttu-id="eca4a-177">**UX_MAX_SLAVE_LUN**</span><span class="sxs-lookup"><span data-stu-id="eca4a-177">**UX_MAX_SLAVE_LUN**</span></span> | <span data-ttu-id="eca4a-178">Это значение представляет текущее количество логических единиц SCSI в драйвере класса хранения устройства.</span><span class="sxs-lookup"><span data-stu-id="eca4a-178">This value represents the current number of SCSI logical units represented in the device storage class driver.</span></span> |
| <span data-ttu-id="eca4a-179">**UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC**</span><span class="sxs-lookup"><span data-stu-id="eca4a-179">**UX_SLAVE_CLASS_STORAGE_INCLUDE_MMC**</span></span> | <span data-ttu-id="eca4a-180">Если этот параметр определен, класс хранения будет работать с несколькими мультимедийными командами (MMC), например DVD-диск.</span><span class="sxs-lookup"><span data-stu-id="eca4a-180">If defined, the storage class will handle Multi-Media Commands (MMC) that is, DVD-ROM.</span></span> |
| <span data-ttu-id="eca4a-181">**UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**</span><span class="sxs-lookup"><span data-stu-id="eca4a-181">**UX_DEVICE_CLASS_CDC_ECM_NX_PKPOOL_ENTRIES**</span></span> | <span data-ttu-id="eca4a-182">Это значение представляет количество пакетов NetX в пуле пакетов класса CDC-ECM.</span><span class="sxs-lookup"><span data-stu-id="eca4a-182">This value represents the number of NetX packets in the CDC-ECM class' packet pool.</span></span> <span data-ttu-id="eca4a-183">Значение по умолчанию равно 16.</span><span class="sxs-lookup"><span data-stu-id="eca4a-183">The default is 16.</span></span> |
| <span data-ttu-id="eca4a-184">**UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="eca4a-184">**UX_SLAVE_REQUEST_CONTROL_MAX_LENGTH**</span></span> | <span data-ttu-id="eca4a-185">Это значение представляет максимальное количество байтов, полученных в конечной точке элемента управления в стеке устройств.</span><span class="sxs-lookup"><span data-stu-id="eca4a-185">This value represents the maximum number of bytes received on a control endpoint in the device stack.</span></span> <span data-ttu-id="eca4a-186">Значение по умолчанию — 256 байт, но его можно уменьшить в окружении с ограничением памяти.</span><span class="sxs-lookup"><span data-stu-id="eca4a-186">The default is 256 bytes but can be reduced in memory constraint environments.</span></span> |
| <span data-ttu-id="eca4a-187">**UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="eca4a-187">**UX_DEVICE_CLASS_HID_EVENT_BUFFER_LENGTH**</span></span> | <span data-ttu-id="eca4a-188">Это значение представляет максимальную длину в байтах для отчета HID.</span><span class="sxs-lookup"><span data-stu-id="eca4a-188">This value represents the maximum length in bytes of a HID report.</span></span> |
| <span data-ttu-id="eca4a-189">**UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE**</span><span class="sxs-lookup"><span data-stu-id="eca4a-189">**UX_DEVICE_CLASS_HID_MAX_EVENTS_QUEUE**</span></span> | <span data-ttu-id="eca4a-190">Это значение представляет максимальное количество отчетов HID, которые могут быть поставлены в очередь одновременно.</span><span class="sxs-lookup"><span data-stu-id="eca4a-190">This value represents the maximum number of HID reports that can be queued at once.</span></span> |
| <span data-ttu-id="eca4a-191">**UX_SLAVE_REQUEST_DATA_MAX_LENGTH**</span><span class="sxs-lookup"><span data-stu-id="eca4a-191">**UX_SLAVE_REQUEST_DATA_MAX_LENGTH**</span></span> | <span data-ttu-id="eca4a-192">Это значение представляет максимальное количество байтов, полученных в групповой конечной точке в стеке устройств.</span><span class="sxs-lookup"><span data-stu-id="eca4a-192">This value represents the maximum number of bytes received on a bulk endpoint in the device stack.</span></span> <span data-ttu-id="eca4a-193">Значение по умолчанию — 4096 байт, но его можно уменьшить в окружении с ограничением памяти.</span><span class="sxs-lookup"><span data-stu-id="eca4a-193">The default is 4096 bytes but can be reduced in memory constraint environments.</span></span> |

## <a name="source-code-tree"></a><span data-ttu-id="eca4a-194">Дерево исходного кода</span><span class="sxs-lookup"><span data-stu-id="eca4a-194">Source Code Tree</span></span>

<span data-ttu-id="eca4a-195">Файлы USBX предоставлены в нескольких каталогах.</span><span class="sxs-lookup"><span data-stu-id="eca4a-195">The USBX files are provided in several directories.</span></span>

![Дерево исходного кода](media/usbx-device-stack/source-code-tree.png)

<span data-ttu-id="eca4a-197">Чтобы файлы можно было распознавать по именам, принято приведенное ниже соглашение.</span><span class="sxs-lookup"><span data-stu-id="eca4a-197">In order to make the files recognizable by their names, the following convention has been adopted:</span></span>

| <span data-ttu-id="eca4a-198">Имя суффикса файла</span><span class="sxs-lookup"><span data-stu-id="eca4a-198">File Suffix Name</span></span>  | <span data-ttu-id="eca4a-199">Описание файла</span><span class="sxs-lookup"><span data-stu-id="eca4a-199">File description</span></span>                          |
| ----------------- | ----------------------------------------- |
| <span data-ttu-id="eca4a-200">ux_host_stack</span><span class="sxs-lookup"><span data-stu-id="eca4a-200">ux_host_stack</span></span>   | <span data-ttu-id="eca4a-201">Основные файлы стека узлов USBX</span><span class="sxs-lookup"><span data-stu-id="eca4a-201">usbx host stack core files</span></span>                |
| <span data-ttu-id="eca4a-202">ux_host_class</span><span class="sxs-lookup"><span data-stu-id="eca4a-202">ux_host_class</span></span>   | <span data-ttu-id="eca4a-203">Файлы классов стека узлов USBX</span><span class="sxs-lookup"><span data-stu-id="eca4a-203">usbx host stack classes files</span></span>             |
| <span data-ttu-id="eca4a-204">ux_hcd</span><span class="sxs-lookup"><span data-stu-id="eca4a-204">ux_hcd</span></span>           | <span data-ttu-id="eca4a-205">Файлы драйвера контроллера стека узлов USBX</span><span class="sxs-lookup"><span data-stu-id="eca4a-205">usbx host stack controller driver files</span></span>   |
| <span data-ttu-id="eca4a-206">ux_device_stack</span><span class="sxs-lookup"><span data-stu-id="eca4a-206">ux_device_stack</span></span> | <span data-ttu-id="eca4a-207">Основные файлы стека устройств USBX</span><span class="sxs-lookup"><span data-stu-id="eca4a-207">usbx device stack core files</span></span>              |
| <span data-ttu-id="eca4a-208">ux_device_class</span><span class="sxs-lookup"><span data-stu-id="eca4a-208">ux_device_class</span></span> | <span data-ttu-id="eca4a-209">Файлы классов стека устройств USBX</span><span class="sxs-lookup"><span data-stu-id="eca4a-209">usbx device stack classes files</span></span>           |
| <span data-ttu-id="eca4a-210">ux_dcd</span><span class="sxs-lookup"><span data-stu-id="eca4a-210">ux_dcd</span></span>           | <span data-ttu-id="eca4a-211">Файлы драйвера контроллера стека устройств USBX</span><span class="sxs-lookup"><span data-stu-id="eca4a-211">usbx device stack controller driver files</span></span> |
| <span data-ttu-id="eca4a-212">ux_otg</span><span class="sxs-lookup"><span data-stu-id="eca4a-212">ux_otg</span></span>           | <span data-ttu-id="eca4a-213">Файлы, связанные с драйвером контроллера OTG для USBX</span><span class="sxs-lookup"><span data-stu-id="eca4a-213">usbx otg controller driver related files</span></span>  |
| <span data-ttu-id="eca4a-214">ux_pictbridge</span><span class="sxs-lookup"><span data-stu-id="eca4a-214">ux_pictbridge</span></span>    | <span data-ttu-id="eca4a-215">Файлы PictBridge для USBX</span><span class="sxs-lookup"><span data-stu-id="eca4a-215">usbx pictbridge files</span></span>                     |
| <span data-ttu-id="eca4a-216">ux_utility</span><span class="sxs-lookup"><span data-stu-id="eca4a-216">ux_utility</span></span>       | <span data-ttu-id="eca4a-217">Служебные функции USBX</span><span class="sxs-lookup"><span data-stu-id="eca4a-217">usbx utility functions</span></span>                    |
| <span data-ttu-id="eca4a-218">demo_usbx</span><span class="sxs-lookup"><span data-stu-id="eca4a-218">demo_usbx</span></span>        | <span data-ttu-id="eca4a-219">Демонстрационные файлы для USBX</span><span class="sxs-lookup"><span data-stu-id="eca4a-219">demonstration files for USBX</span></span>              |

## <a name="initialization-of-usbx-resources"></a><span data-ttu-id="eca4a-220">Инициализация ресурсов USBX</span><span class="sxs-lookup"><span data-stu-id="eca4a-220">Initialization of USBX resources</span></span>

<span data-ttu-id="eca4a-221">В USBX имеется собственный диспетчер памяти.</span><span class="sxs-lookup"><span data-stu-id="eca4a-221">USBX has its own memory manager.</span></span> <span data-ttu-id="eca4a-222">Память для USBX необходимо выделить перед инициализацией узла или устройства USBX.</span><span class="sxs-lookup"><span data-stu-id="eca4a-222">The memory needs to be allocated to USBX before the host or device side of USBX is initialized.</span></span> <span data-ttu-id="eca4a-223">Диспетчер памяти USBX поддерживает системы с кэшированием памяти.</span><span class="sxs-lookup"><span data-stu-id="eca4a-223">USBX memory manager can accommodate systems where memory can be cached.</span></span>

<span data-ttu-id="eca4a-224">Приведенная ниже функция инициализирует ресурсы памяти USBX: 128 КБ обычной памяти без отдельного пула для некэшируемой памяти:</span><span class="sxs-lookup"><span data-stu-id="eca4a-224">The following function initializes USBX memory resources with 128 K of regular memory and no separate pool for cache safe memory:</span></span>

```c
/* Initialize USBX Memory */
ux_system_initialize(memory_pointer,(128*1024),UX_NULL,0);
```

<span data-ttu-id="eca4a-225">Прототип для ux_system_initialize выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="eca4a-225">The prototype for the ux_system_initialize is as follows:</span></span>

```c
UINT ux_system_initialize(VOID *regular_memory_pool_start,
        ULONG regular_memory_size,
        VOID *cache_safe_memory_pool_start,
        ULONG cache_safe_memory_size);
```

<span data-ttu-id="eca4a-226">Входные параметры:</span><span class="sxs-lookup"><span data-stu-id="eca4a-226">Input parameters:</span></span>

| <span data-ttu-id="eca4a-227">Параметр</span><span class="sxs-lookup"><span data-stu-id="eca4a-227">Parameter</span></span>                          | <span data-ttu-id="eca4a-228">Описание</span><span class="sxs-lookup"><span data-stu-id="eca4a-228">Description</span></span>                             |
| ---------------------------------- | --------------------------------------- |
| <span data-ttu-id="eca4a-229">VOID \*regular_memory_pool_start</span><span class="sxs-lookup"><span data-stu-id="eca4a-229">VOID \*regular_memory_pool_start</span></span>    | <span data-ttu-id="eca4a-230">Начало пула обычной памяти</span><span class="sxs-lookup"><span data-stu-id="eca4a-230">Beginning of the regular memory pool</span></span>    |
| <span data-ttu-id="eca4a-231">ULONG regular_memory_size</span><span class="sxs-lookup"><span data-stu-id="eca4a-231">ULONG regular_memory_size</span></span>          | <span data-ttu-id="eca4a-232">Размер пула обычной памяти</span><span class="sxs-lookup"><span data-stu-id="eca4a-232">Size of the regular memory pool</span></span>         |
| <span data-ttu-id="eca4a-233">VOID \*cache_safe_memory_pool_start</span><span class="sxs-lookup"><span data-stu-id="eca4a-233">VOID \*cache_safe_memory_pool_start</span></span> | <span data-ttu-id="eca4a-234">Начало пула некэшируемой памяти</span><span class="sxs-lookup"><span data-stu-id="eca4a-234">Beginning of the cache safe memory pool</span></span> |
| <span data-ttu-id="eca4a-235">ULONG cache_safe_memory_size</span><span class="sxs-lookup"><span data-stu-id="eca4a-235">ULONG cache_safe_memory_size</span></span>       | <span data-ttu-id="eca4a-236">Размер пула некэшируемой памяти</span><span class="sxs-lookup"><span data-stu-id="eca4a-236">Size of the cache safe memory pool</span></span>      |

<span data-ttu-id="eca4a-237">Не для всех систем нужно определять некэшируемую память.</span><span class="sxs-lookup"><span data-stu-id="eca4a-237">Not all systems require the definition of cache safe memory.</span></span> <span data-ttu-id="eca4a-238">В такой системе во время инициализации для указателя памяти будут переданы значения UX_NULL, а размер пула будет равен 0.</span><span class="sxs-lookup"><span data-stu-id="eca4a-238">In such a system, the values passed during the initialization for the memory pointer will be set to UX_NULL and the size of the pool to 0.</span></span> <span data-ttu-id="eca4a-239">После этого USBX будет использовать стандартный пул памяти вместо некэшируемого пула.</span><span class="sxs-lookup"><span data-stu-id="eca4a-239">USBX will then use the regular memory pool in lieu of the cache safe pool.</span></span>

<span data-ttu-id="eca4a-240">В системе, где обычная память не является некэшируемой и для контроллера требуется память с прямым доступом (DMA), необходимо определить пул памяти в некэшируемой зоне.</span><span class="sxs-lookup"><span data-stu-id="eca4a-240">In a system where the regular memory is not cache safe and a controller requires to perform DMA memory it is necessary to define a memory pool in a cache safe zone.</span></span>

## <a name="uninitialization-of-usbx-resources"></a><span data-ttu-id="eca4a-241">Отмена инициализации ресурсов USBX</span><span class="sxs-lookup"><span data-stu-id="eca4a-241">Uninitialization of USBX resources</span></span>

<span data-ttu-id="eca4a-242">Работу экземпляра USBX можно завершить, освободив его ресурсы.</span><span class="sxs-lookup"><span data-stu-id="eca4a-242">USBX can be terminated by releasing its resources.</span></span> <span data-ttu-id="eca4a-243">Перед завершением работы экземпляра USBX нужно правильно завершить работу всех ресурсов классов и контроллеров.</span><span class="sxs-lookup"><span data-stu-id="eca4a-243">Prior to terminating usbx, all classes and controller resources need to be terminated properly.</span></span> <span data-ttu-id="eca4a-244">Приведенная ниже функция отменяет инициализацию ресурсов памяти USBX.</span><span class="sxs-lookup"><span data-stu-id="eca4a-244">The following function uninitializes USBX memory resources:</span></span>

```c
/* Unitialize USBX Resources */

ux_system_uninitialize();
```

<span data-ttu-id="eca4a-245">Прототип для ux_system_initialize выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="eca4a-245">The prototype for the ux_system_initialize is as follows:</span></span>

```c
UINT ux_system_uninitialize(VOID);
```

## <a name="definition-of-usb-device-controller"></a><span data-ttu-id="eca4a-246">Определение контроллера USB-устройства</span><span class="sxs-lookup"><span data-stu-id="eca4a-246">Definition of USB Device Controller</span></span>

<span data-ttu-id="eca4a-247">В режиме устройства в любое время может быть определен только один контроллер USB-устройства.</span><span class="sxs-lookup"><span data-stu-id="eca4a-247">Only one USB device controller can be defined at any time to operate in device mode.</span></span> <span data-ttu-id="eca4a-248">Это определение должно находиться в файле инициализации приложения.</span><span class="sxs-lookup"><span data-stu-id="eca4a-248">The application initialization file should contain this definition.</span></span> <span data-ttu-id="eca4a-249">Следующая строка выполняет определение универсального контроллера USB:</span><span class="sxs-lookup"><span data-stu-id="eca4a-249">The following line performs the definition of a generic usb controller:</span></span>

```c
ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);
```

<span data-ttu-id="eca4a-250">Инициализация USB-устройства имеет следующий прототип:</span><span class="sxs-lookup"><span data-stu-id="eca4a-250">The USB device initialization has the following prototype:</span></span>

```c
UINT ux_dcd_controller_initialize(ULONG dcd_io,
    ULONG dcd_irq, ULONG dcd_vbus_address);
```

<span data-ttu-id="eca4a-251">Поддерживаются следующие параметры:</span><span class="sxs-lookup"><span data-stu-id="eca4a-251">with the following parameters:</span></span>

| <span data-ttu-id="eca4a-252">Параметр</span><span class="sxs-lookup"><span data-stu-id="eca4a-252">Pararmeter</span></span>               | <span data-ttu-id="eca4a-253">Описание</span><span class="sxs-lookup"><span data-stu-id="eca4a-253">Description</span></span>                      |
| ------------------------ | -------------------------------- |
| <span data-ttu-id="eca4a-254">ULONG dcd_io</span><span class="sxs-lookup"><span data-stu-id="eca4a-254">ULONG dcd_io</span></span>            | <span data-ttu-id="eca4a-255">Адрес ввода-вывода контроллера</span><span class="sxs-lookup"><span data-stu-id="eca4a-255">Address of the controller IO</span></span>     |
| <span data-ttu-id="eca4a-256">ULONG dcd_irq</span><span class="sxs-lookup"><span data-stu-id="eca4a-256">ULONG dcd_irq</span></span>           | <span data-ttu-id="eca4a-257">Прерывание, используемое контроллером</span><span class="sxs-lookup"><span data-stu-id="eca4a-257">Interrupt used by the controller</span></span> |
| <span data-ttu-id="eca4a-258">ULONG dcd_vbus_address</span><span class="sxs-lookup"><span data-stu-id="eca4a-258">ULONG dcd_vbus_address</span></span> | <span data-ttu-id="eca4a-259">Адрес VBUS GPIO</span><span class="sxs-lookup"><span data-stu-id="eca4a-259">Address of the VBUS GPIO</span></span>         |

<span data-ttu-id="eca4a-260">В следующем примере показана инициализация USBX в режиме устройства с классом запоминающих устройств и универсальным контроллером:</span><span class="sxs-lookup"><span data-stu-id="eca4a-260">The following example is the initialization of USBX in device mode with the storage device class and a generic controller:</span></span>

```c
/* Initialize USBX Memory */

ux_system_initialize(memory_pointer,(128*1024), 0, 0);

/* The code below is required for installing the device portion of USBX */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, installation was successful. */

/* Store the number of LUN in this device storage instance: single LUN. */
storage_parameter.ux_slave_class_storage_parameter_number_lun = 1;

/* Initialize the storage class parameters for reading/writing to the Flash Disk. */
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_last_lba = 0x1e6bfe;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_block_length = 512;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_type = 0;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_removable_flag = 0x80;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_read = tx_demo_thread_flash_media_read;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_write = tx_demo_thread_flash_media_write;
storage_parameter.ux_slave_class_storage_parameter_lun[0].ux_slave_class_storage_media_status = tx_demo_thread_flash_media_status;

/* Initialize the device storage class. The class is connected with interface 0 */
status = ux_device_stack_class_register(ux_system_slave_class_storage_name ux_device_class_storage_entry,
    ux_device_class_storage_thread,0, (VOID *)&storage_parameter);

/* Register the device controllers available in this system */
status = ux_dcd_controller_initialize(0x7BB00000, 0, 0xB7A00000);

/* If status equals UX_SUCCESS, registration was successful. */
```

## <a name="troubleshooting"></a><span data-ttu-id="eca4a-261">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="eca4a-261">Troubleshooting</span></span>

<span data-ttu-id="eca4a-262">USBX поставляется с демонстрационным файлом и окружением моделирования.</span><span class="sxs-lookup"><span data-stu-id="eca4a-262">USBX is delivered with a demonstration file and a simulation environment.</span></span> <span data-ttu-id="eca4a-263">Рекомендуется сначала запустить демонстрационную систему — на целевом оборудовании или соответствующей демонстрационной платформе.</span><span class="sxs-lookup"><span data-stu-id="eca4a-263">It is always a good idea to get the demonstration platform running first—either on the target hardware or a specific demonstration platform.</span></span>

## <a name="usbx-version-id"></a><span data-ttu-id="eca4a-264">Идентификатор версии USBX</span><span class="sxs-lookup"><span data-stu-id="eca4a-264">USBX Version ID</span></span>

<span data-ttu-id="eca4a-265">Сведения о текущей версии USBX доступны во время выполнения как пользователю, так и программному обеспечению приложения.</span><span class="sxs-lookup"><span data-stu-id="eca4a-265">The current version of USBX is available both to the user and the application software during run-time.</span></span> <span data-ttu-id="eca4a-266">Программист может получить данные о версии USBX, ознакомившись с файлом \***ux_port.h** _.</span><span class="sxs-lookup"><span data-stu-id="eca4a-266">The programmer can obtain the USBX version from examination of the \***ux_port.h** _ file.</span></span> <span data-ttu-id="eca4a-267">Кроме того, этот файл содержит журнал версий для соответствующей платформы.</span><span class="sxs-lookup"><span data-stu-id="eca4a-267">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="eca4a-268">Программное обеспечение приложения может получить версию USBX, проанализировав глобальную строку _ *_ _ux_version_id_* _, которая определена в файле _\*_ux_port.h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="eca4a-268">Application software can obtain the USBX version by examining the global string _ *_ _ux_version_id_* _, which is defined in _\*_ux_port.h_\*\*.</span></span>
