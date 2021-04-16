---
title: Глава 2. Установка и использование GUIX
description: В этой главе приведено описание различных проблем, связанных с установкой, настройкой и использованием высокопроизводительного GUIX продукта с пользовательским интерфейсом.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6527227062fc667b3f527a798d6621914c374c5c
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814980"
---
# <a name="chapter-2---installation-and-use-of-guix"></a><span data-ttu-id="45a5c-103">Глава 2. Установка и использование GUIX</span><span class="sxs-lookup"><span data-stu-id="45a5c-103">Chapter 2 - Installation and Use of GUIX</span></span>

<span data-ttu-id="45a5c-104">В этой главе приведено описание различных проблем, связанных с установкой, настройкой и использованием высокопроизводительного GUIX продукта с пользовательским интерфейсом.</span><span class="sxs-lookup"><span data-stu-id="45a5c-104">This chapter contains a description of various issues related to installation, setup, and use of the highperformance user interface product GUIX.</span></span>  

## <a name="host-considerations"></a><span data-ttu-id="45a5c-105">Рекомендации по размещению</span><span class="sxs-lookup"><span data-stu-id="45a5c-105">Host Considerations</span></span>

<span data-ttu-id="45a5c-106">Разработка внедряемых решений обычно выполняется на главных компьютерах Windows или Linux (Unix).</span><span class="sxs-lookup"><span data-stu-id="45a5c-106">Embedded development is usually performed on Windows or Linux (Unix) host computers.</span></span> <span data-ttu-id="45a5c-107">После компиляции приложения, его связывания и создания исполняемого файла на узле оно скачивается на целевое оборудование для выполнения.</span><span class="sxs-lookup"><span data-stu-id="45a5c-107">After the application is compiled, linked, and the executable is generated on the host, it is downloaded to the target hardware for execution.</span></span>

<span data-ttu-id="45a5c-108">Как правило, скачивание на целевой объект запускается из отладчика инструмента для разработки.</span><span class="sxs-lookup"><span data-stu-id="45a5c-108">Usually the target download is done from within the development tool's debugger.</span></span> <span data-ttu-id="45a5c-109">После скачивания отладчик отвечает за управление выполнением на целевом объекте (запуск, остановка, точка останова и т. д.), а также за доступ к памяти и регистрам процессора.</span><span class="sxs-lookup"><span data-stu-id="45a5c-109">After download, the debugger is responsible for providing target execution control (go, halt, breakpoint, etc.) as well as access to memory and processor registers.</span></span>

<span data-ttu-id="45a5c-110">Большинство отладчиков инструментов разработки обмениваются данными с целевым оборудованием через подключения OCD (отладка на микросхеме), например JTAG (IEEE 1149.1) и BDM (режим фоновой отладки).</span><span class="sxs-lookup"><span data-stu-id="45a5c-110">Most development tool debuggers communicate with the target hardware via on-chip debug (OCD) connections such as JTAG (IEEE 1149.1) and Background Debug Mode (BDM).</span></span> <span data-ttu-id="45a5c-111">Отладчики также взаимодействуют с целевым оборудованием через подключения ICE (внутрисхемная эмуляция).</span><span class="sxs-lookup"><span data-stu-id="45a5c-111">Debuggers also communicate with target hardware through In-Circuit Emulation (ICE) connections.</span></span> <span data-ttu-id="45a5c-112">Подключения OCD и ICE обеспечивают надежную передачу данных с минимальным влиянием на резидентное ПО на целевом объекте.</span><span class="sxs-lookup"><span data-stu-id="45a5c-112">Both OCD and ICE connections provide robust solutions with minimal intrusion on the target resident software.</span></span>

<span data-ttu-id="45a5c-113">Как и в случае с ресурсами, используемыми на узле, исходный код для GUIX предоставляется в формате ASCII и требует около 30 МБ свободного пространства на жестком диске главного компьютера.</span><span class="sxs-lookup"><span data-stu-id="45a5c-113">As for resources used on the host, the source code for GUXI is delivered in ASCII format and requires approximately 30 Mbytes of space on the host computer’s hard disk.</span></span>

## <a name="target-considerations"></a><span data-ttu-id="45a5c-114">Замечания, касающиеся целевого оборудования</span><span class="sxs-lookup"><span data-stu-id="45a5c-114">Target Considerations</span></span>

<span data-ttu-id="45a5c-115">GUIX требует 5–80 КБ доступной только для чтения памяти на целевом объекте.</span><span class="sxs-lookup"><span data-stu-id="45a5c-115">GUIX requires between 5 KBytes and 80 Kbytes of Read-Only Memory (ROM) on the target.</span></span> <span data-ttu-id="45a5c-116">Еще 5–10 КБ ОЗУ целевого объекта необходимо для стека потока GUIX и других глобальных структур данных.</span><span class="sxs-lookup"><span data-stu-id="45a5c-116">Another 5 to 10KBytes of the target’s Random Access Memory (RAM) are required for the GUIX thread stack and other global data structures.</span></span>

<span data-ttu-id="45a5c-117">Кроме того, GUIX требует использования таймера ThreadX и объекта мьютекса ThreadX.</span><span class="sxs-lookup"><span data-stu-id="45a5c-117">In addition, GUIX requires the use of a ThreadX timer and a ThreadX mutex object.</span></span> <span data-ttu-id="45a5c-118">Эти средства используются для периодической обработки и защиты потоков в GUIX.</span><span class="sxs-lookup"><span data-stu-id="45a5c-118">These facilities are used for periodic processing needs and thread protection inside GUIX.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="45a5c-119">Дистрибутивы продукта</span><span class="sxs-lookup"><span data-stu-id="45a5c-119">Product Distribution</span></span>

<span data-ttu-id="45a5c-120">GUIX для ОСРВ Azure можно получить в нашем общедоступном репозитории исходного кода по адресу <https://github.com/azure-rtos/guix/>.</span><span class="sxs-lookup"><span data-stu-id="45a5c-120">Azure RTOS GUIX can be obtained from our public source code repository at <https://github.com/azure-rtos/guix/>.</span></span>

<span data-ttu-id="45a5c-121">Ниже приведен список важных файлов, которые присутствуют в большинстве дистрибутивов продукта:</span><span class="sxs-lookup"><span data-stu-id="45a5c-121">The following is a list of the important files common to most product distributions:</span></span>

| <span data-ttu-id="45a5c-122">Имя файла&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span class="sxs-lookup"><span data-stu-id="45a5c-122">Filename&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span></span>| <span data-ttu-id="45a5c-123">Описание</span><span class="sxs-lookup"><span data-stu-id="45a5c-123">Description</span></span>   |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="45a5c-124">gx_api.h</span><span class="sxs-lookup"><span data-stu-id="45a5c-124">gx_api.h</span></span>        | <span data-ttu-id="45a5c-125">Этот файл заголовка на C включает все системные равенства, структуры данных и прототипы служб.</span><span class="sxs-lookup"><span data-stu-id="45a5c-125">This C header file contains all system equates, data structures, and service prototypes.</span></span> |
| <span data-ttu-id="45a5c-126">gx_port.h</span><span class="sxs-lookup"><span data-stu-id="45a5c-126">gx_port.h</span></span>       | <span data-ttu-id="45a5c-127">Этот файл заголовка на C включает все определения и структуры данных, относящиеся к конкретным целевым объектам и инструментам разработки.</span><span class="sxs-lookup"><span data-stu-id="45a5c-127">This C header file contains all target-specific and development tool-specific data definitions and structures.</span></span>                                                                                                                                         |
| <span data-ttu-id="45a5c-128">gx.a (или gx.lib)</span><span class="sxs-lookup"><span data-stu-id="45a5c-128">gx.a (or gx.lib)</span></span> | <span data-ttu-id="45a5c-129">Это двоичная версия библиотеки GUIX на C.</span><span class="sxs-lookup"><span data-stu-id="45a5c-129">This is the binary version of the GUIX C library.</span></span> <span data-ttu-id="45a5c-130">Обычно она создается путем компиляции и архивации предоставленных исходных файлов библиотеки GUIX, но эта библиотека может быть предоставлена в готовом виде в зависимости от целевого оборудования и типа лицензии.</span><span class="sxs-lookup"><span data-stu-id="45a5c-130">This is normally built by compiling and archiving the provided GUIX library source files, however this library may be provided in pre-built form depending on your hardware target and license type.</span></span> |
|

> [!IMPORTANT]
> <span data-ttu-id="45a5c-131">*Для имен всех файлов используется нижний регистр, что упрощает преобразование команд для платформ разработки Linux (UNIX).*</span><span class="sxs-lookup"><span data-stu-id="45a5c-131">*All files are in lower-case, making it easy to convert the commands to Linux (Unix) development platforms.*</span></span>

## <a name="guix-installation"></a><span data-ttu-id="45a5c-132">Установка GUIX</span><span class="sxs-lookup"><span data-stu-id="45a5c-132">GUIX Installation</span></span>

<span data-ttu-id="45a5c-133">GUIX устанавливается путем клонирования репозитория GitHub на локальный компьютер.</span><span class="sxs-lookup"><span data-stu-id="45a5c-133">GUIX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="45a5c-134">Ниже приведен типичный синтаксис для создания клона репозитория GUIX на вашем компьютере:</span><span class="sxs-lookup"><span data-stu-id="45a5c-134">The following is typical syntax for creating a clone of the GUIX repository on your PC:</span></span>

```c
    git clone https://github.com/azure-rtos/guix
```

<span data-ttu-id="45a5c-135">Или вы можете скачать копию репозитория с помощью соответствующей кнопки на главной странице GitHub.</span><span class="sxs-lookup"><span data-stu-id="45a5c-135">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="45a5c-136">Вы также можете найти инструкции по созданию библиотеки GUIX на главной странице онлайн-репозитория.</span><span class="sxs-lookup"><span data-stu-id="45a5c-136">You will also find instructions for building the GUIX library on the front page of the online repository.</span></span>

>[!NOTE]  
> <span data-ttu-id="45a5c-137">*Программному обеспечению приложений требуется доступ к файлу библиотеки GUIX, который обычно имеет имя **gx.a** (или **gx.lib**), а также к включаемым файлам на C **gx_api.h** и **gx_port.h**. Это можно реализовать, задав соответствующий путь в инструментах разработки или скопировав такие файлы в область разработки приложения.*</span><span class="sxs-lookup"><span data-stu-id="45a5c-137">*Application software needs access to the GUIX library file, usually called **gx.a** (or **gx.lib**), and the C include files **gx_api.h** and **gx_port.h**. This is accomplished either by setting the appropriate path for the development tools or by copying these files into the application development area.*</span></span>

## <a name="using-guix"></a><span data-ttu-id="45a5c-138">Использование GUIX</span><span class="sxs-lookup"><span data-stu-id="45a5c-138">Using GUIX</span></span>

<span data-ttu-id="45a5c-139">Использовать GUIX просто.</span><span class="sxs-lookup"><span data-stu-id="45a5c-139">Using GUIX is easy.</span></span> <span data-ttu-id="45a5c-140">В сущности, код приложения должен включать ***gx_api.h** _ во время компиляции и связь с библиотекой GUIX _*_gx.a_*_ (или _ *_gx.lib_*)*.</span><span class="sxs-lookup"><span data-stu-id="45a5c-140">Basically, the application code must include ***gx_api.h** _ during compilation and link with the GUIX library _*_gx.a_*_ (or _ *_gx.lib_*)*.</span></span>

<span data-ttu-id="45a5c-141">Для создания приложения GUIX нужно выполнить четыре простых шага.</span><span class="sxs-lookup"><span data-stu-id="45a5c-141">There are four easy steps required to build a GUIX application:</span></span>

| <span data-ttu-id="45a5c-142">Шаги</span><span class="sxs-lookup"><span data-stu-id="45a5c-142">Steps</span></span>   | <span data-ttu-id="45a5c-143">Описание</span><span class="sxs-lookup"><span data-stu-id="45a5c-143">Description</span></span>    |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| <span data-ttu-id="45a5c-144">Шаг&nbsp;1.</span><span class="sxs-lookup"><span data-stu-id="45a5c-144">Step&nbsp;1:</span></span> | <span data-ttu-id="45a5c-145">Включите файл ***gx_api.h*** во все файлы приложения, которые используют службы или структуры данных GUIX.</span><span class="sxs-lookup"><span data-stu-id="45a5c-145">Include the ***gx_api.h*** file in all application files that use GUIX services or data structures.</span></span>                                                               |
| <span data-ttu-id="45a5c-146">Шаг&nbsp;2.</span><span class="sxs-lookup"><span data-stu-id="45a5c-146">Step&nbsp;2:</span></span> | <span data-ttu-id="45a5c-147">Инициализируйте систему GUIX, вызвав ***gx_system_initialize** _ из функции _ *_tx_application_define_** или потока приложения.</span><span class="sxs-lookup"><span data-stu-id="45a5c-147">Initialize the GUIX system by calling ***gx_system_initialize** _ from the _ *_tx_application_define_** function or an application thread.</span></span>                       |
| <span data-ttu-id="45a5c-148">Шаг&nbsp;3.</span><span class="sxs-lookup"><span data-stu-id="45a5c-148">Step&nbsp;3:</span></span> | <span data-ttu-id="45a5c-149">Создайте экземпляр отображения, холст для отображения и корневое окно, а также любые другие необходимые окна или мини-приложения.</span><span class="sxs-lookup"><span data-stu-id="45a5c-149">Create a display instance, create a canvas for the display, and create the root window and any other windows or widgets necessary.</span></span>                                 |
| <span data-ttu-id="45a5c-150">Шаг&nbsp;4.</span><span class="sxs-lookup"><span data-stu-id="45a5c-150">Step&nbsp;4:</span></span> | <span data-ttu-id="45a5c-151">Выполните компиляцию исходного кода и свяжите его с библиотекой среды выполнения GUIX ***gx.a** _ (или _*_gx.lib_\*\*).</span><span class="sxs-lookup"><span data-stu-id="45a5c-151">Compile application source and link with the GUIX runtime library ***gx.a** _ (or _*_gx.lib_\*\*).</span></span> <span data-ttu-id="45a5c-152">Полученный образ можно скачать на целевой объект и запустить.</span><span class="sxs-lookup"><span data-stu-id="45a5c-152">The resulting image can be downloaded to the target and executed!</span></span> |

## <a name="troubleshooting"></a><span data-ttu-id="45a5c-153">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="45a5c-153">Troubleshooting</span></span>

<span data-ttu-id="45a5c-154">Каждый порт GUIX предоставляется с демонстрационным приложением, которое выполняется на определенном оборудовании для отображения.</span><span class="sxs-lookup"><span data-stu-id="45a5c-154">Each GUIX port is delivered with a demonstration application that executes on specific display hardware.</span></span> <span data-ttu-id="45a5c-155">Со всеми версиями GUIX предоставляется одна базовая демонстрация.</span><span class="sxs-lookup"><span data-stu-id="45a5c-155">The same basic demonstration is delivered with all versions of GUIX.</span></span> <span data-ttu-id="45a5c-156">Рекомендуется первой запускать именно демонстрационную систему.</span><span class="sxs-lookup"><span data-stu-id="45a5c-156">It is always a good idea to get the demonstration system running first.</span></span>

<span data-ttu-id="45a5c-157">Если демонстрационная система не работает надлежащим образом, выполните следующие операции, чтобы определить проблему:</span><span class="sxs-lookup"><span data-stu-id="45a5c-157">If the demonstration system does not run properly, perform the following operations to narrow the problem:</span></span>

1. <span data-ttu-id="45a5c-158">Определите, на каком этапе демонстрации возникает ошибка.</span><span class="sxs-lookup"><span data-stu-id="45a5c-158">Determine how much of the demonstration is running.</span></span>

2. <span data-ttu-id="45a5c-159">Увеличьте размер стека для потока GUIX, изменив константу времени компиляции **GX_THREAD_STACK_SIZE** и повторно выполнив компиляцию библиотеки GUIX.</span><span class="sxs-lookup"><span data-stu-id="45a5c-159">Increase the stack size of the GUIX thread by changing the  compile-time constant **GX_THREAD_STACK_SIZE** and recompiling  the GUIX library</span></span>

3. <span data-ttu-id="45a5c-160">Повторно скомпилируйте библиотеку GUIX с соответствующими параметрами отладки, которые приведены в разделе параметров конфигурации.</span><span class="sxs-lookup"><span data-stu-id="45a5c-160">Recompile the GUIX library with the appropriate debug options listed  in the configuration option section.</span></span>

4. <span data-ttu-id="45a5c-161">Изучите возвращаемое состояние от всех вызовов API.</span><span class="sxs-lookup"><span data-stu-id="45a5c-161">Examine the return status from all API calls.</span></span>

5. <span data-ttu-id="45a5c-162">Определите, присутствует ли внутренняя системная ошибка, задав точку останова в функции ***_gx_system_error_process***.</span><span class="sxs-lookup"><span data-stu-id="45a5c-162">Determine if there is an internal system error by setting a breakpoint at the function ***_gx_system_error_process***.</span></span> <span data-ttu-id="45a5c-163">Код ошибки и сведения о вызывающем объекте должны дать достаточно информации для определения проблемы.</span><span class="sxs-lookup"><span data-stu-id="45a5c-163">There error code and caller should give clues as to what might be going wrong.</span></span>

6. <span data-ttu-id="45a5c-164">Временно обойдите все недавние изменения, чтобы понять, как при этом меняется проблема.</span><span class="sxs-lookup"><span data-stu-id="45a5c-164">Temporarily bypass any recent changes to see if the problem disappears or changes.</span></span> <span data-ttu-id="45a5c-165">Такая информация будет полезной специалистам службы поддержки Майкрософт.</span><span class="sxs-lookup"><span data-stu-id="45a5c-165">Such information should prove useful to Microsoft support engineers.</span></span>

<span data-ttu-id="45a5c-166">Выполните инструкции, приведенные в разделе "Что нам нужно", чтобы отправить информацию, собранную на этапе устранения неполадок.</span><span class="sxs-lookup"><span data-stu-id="45a5c-166">Follow the procedures outlined in the section titled “What We Need From You” to send the information gathered from the troubleshooting steps.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="45a5c-167">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="45a5c-167">Configuration Options</span></span>

<span data-ttu-id="45a5c-168">При сборке библиотеки GUIX и приложения, использующего GUIX, доступно несколько параметров конфигурации.</span><span class="sxs-lookup"><span data-stu-id="45a5c-168">There are several configuration options when building the GUIX library and the application using GUIX.</span></span> <span data-ttu-id="45a5c-169">Такие параметры используются для настройки размера библиотеки и набора функций в соответствии с требованиями вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="45a5c-169">These options are used to tune the library size and feature set to best fit your application requirements.</span></span> <span data-ttu-id="45a5c-170">Например, если ваше приложение работает только с одним потоком, использующим службы API GUIX, нужно определить флаг конфигурации **GX_DISABLE_MULTITHREAD_SUPPORT**, чтобы устранить издержки, связанные с защитой критически важных разделов кода от вытеснения несколькими потоками.</span><span class="sxs-lookup"><span data-stu-id="45a5c-170">For example, if your application will have only one thread utilizing the GUIX API services, the configuration flag **GX_DISABLE_MULTITHREAD_SUPPORT** should be defined to eliminate the overhead associated with protecting critical code sections from pre-emption by multiple threads.</span></span> <span data-ttu-id="45a5c-171">Вы можете определить различные флаги конфигурации в исходном коде приложения, в командной строке или во включаемом файле **_gx_user.h_**.</span><span class="sxs-lookup"><span data-stu-id="45a5c-171">The various configuration flags can be defined in the application source, on the command line, or within the **_gx_user.h_** include file.</span></span>

<span data-ttu-id="45a5c-172">При изменении флагов конфигурации для библиотеки GUIX вам потребуется повторно выполнить сборку библиотеки GUIX и модулей приложений, чтобы применить такие изменения конфигурации.</span><span class="sxs-lookup"><span data-stu-id="45a5c-172">Whenever the GUIX library configuration flags are modified, it is required to rebuild both the GUIX library and your application modules for the configuration changes to take effect.</span></span>

<span data-ttu-id="45a5c-173">Полный список флагов конфигурации приведен в Приложении З "Флаги конфигурации GUIX во время сборки".</span><span class="sxs-lookup"><span data-stu-id="45a5c-173">The complete list of configuration flags is documented in Appendix H: GUIX Build-Time Configuration Flags.</span></span>

## <a name="guix-version-id"></a><span data-ttu-id="45a5c-174">Идентификатор версии GUIX</span><span class="sxs-lookup"><span data-stu-id="45a5c-174">GUIX Version ID</span></span>

<span data-ttu-id="45a5c-175">Сведения о текущей версии GUIX доступны во время выполнения как пользователю, так и ПО приложения.</span><span class="sxs-lookup"><span data-stu-id="45a5c-175">The current version of GUIX is available to both the user and the application software during runtime.</span></span> <span data-ttu-id="45a5c-176">Программист может получить данные о версии GUIX, изучив файл \***gx_port.h** _.</span><span class="sxs-lookup"><span data-stu-id="45a5c-176">The programmer can obtain the GUIX version from examination of the \***gx_port.h** _ file.</span></span> <span data-ttu-id="45a5c-177">Кроме того, этот файл также включает историю версий для соответствующего порта. ПО приложения может получить данные о версии GUIX, обратившись к глобальной строке _ *_ _gx_version_id_* _ в файле _\*_gx_port.h_\*\*.</span><span class="sxs-lookup"><span data-stu-id="45a5c-177">In addition, this file also contains a version history of the corresponding port Application software can obtain the GUIX version by examining the global string _ *_ _gx_version_id_* _ in _\*_gx_port.h_\*\*.</span></span>

<span data-ttu-id="45a5c-178">ПО приложения также может получить данные о выпуске из приведенных ниже констант, определенных в файле \***gx_api.h**.\* Такие константы указывают текущий выпуск продукта по имени, а также основную и дополнительную версии продукта.</span><span class="sxs-lookup"><span data-stu-id="45a5c-178">Application software can also obtain release information from the constants shown below defined in \***gx_api.h**.\* These constants identify the current product release by name and the product major and minor version.</span></span>

```C
#define __PRODUCT_GUIX__

#define __GUIX_MAJOR_VERSION__

#define __GUIX_MINOR_VERSION__
```
