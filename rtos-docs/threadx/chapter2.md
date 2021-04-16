---
title: Глава 2. Установка и использование ThreadX для ОСРВ Azure
description: В этой главе описаны различные проблемы, связанные с установкой, настройкой и использованием высокопроизводительного ядра ThreadX для ОСРВ Azure.
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: e1bf85d363b07c81f226d494107eae9ba18114a7
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/22/2021
ms.locfileid: "104814356"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-threadx"></a><span data-ttu-id="83a3d-103">Глава 2. Установка и использование ThreadX для ОСРВ Azure</span><span class="sxs-lookup"><span data-stu-id="83a3d-103">Chapter 2 - Installation and Use of Azure RTOS ThreadX</span></span>

<span data-ttu-id="83a3d-104">В этой главе описаны различные проблемы, связанные с установкой, настройкой и использованием высокопроизводительного ядра ThreadX для ОСРВ Azure.</span><span class="sxs-lookup"><span data-stu-id="83a3d-104">This chapter contains a description of various issues related to installation, setup, and usage of the high-performance Azure RTOS ThreadX kernel.</span></span>

## <a name="host-considerations"></a><span data-ttu-id="83a3d-105">Рекомендации по размещению</span><span class="sxs-lookup"><span data-stu-id="83a3d-105">Host Considerations</span></span>

<span data-ttu-id="83a3d-106">Встраиваемое программное обеспечение обычно разрабатывается на главных компьютерах Windows или Linux (UNIX).</span><span class="sxs-lookup"><span data-stu-id="83a3d-106">Embedded software is usually developed on Windows or Linux (Unix) host computers.</span></span> <span data-ttu-id="83a3d-107">После компиляции, связывания и размещения на главном компьютере приложение скачивается на целевое оборудование для выполнения.</span><span class="sxs-lookup"><span data-stu-id="83a3d-107">After the application is compiled, linked, and located on the host, it is downloaded to the target hardware for execution.</span></span>

<span data-ttu-id="83a3d-108">Как правило, скачивание на целевой объект запускается из отладчика средства разработки.</span><span class="sxs-lookup"><span data-stu-id="83a3d-108">Usually the target download is done from within the development tool debugger.</span></span> <span data-ttu-id="83a3d-109">Когда скачивание завершится, отладчик берет на себя управление выполнением на целевом объекте (запуск, остановка, точка останова и т. д.), а также доступом к памяти и регистрам процессора.</span><span class="sxs-lookup"><span data-stu-id="83a3d-109">After the download has completed, the debugger is responsible for providing target execution control (go, halt, breakpoint, etc.) as well as access to memory and processor registers.</span></span>

<span data-ttu-id="83a3d-110">Большинство отладчиков инструментов разработки обменивается данными с целевым оборудованием через подключения отладки на микросхеме (OCD), например JTAG (IEEE 1149.1) и BDM (режим фоновой отладки).</span><span class="sxs-lookup"><span data-stu-id="83a3d-110">Most development tool debuggers communicate with the target hardware via on-chip debug (OCD) connections such as JTAG (IEEE 1149.1) and Background Debug Mode (BDM).</span></span> <span data-ttu-id="83a3d-111">Кроме того, отладчики взаимодействуют с целевым оборудованием через подключения ICE (внутрисхемная эмуляция).</span><span class="sxs-lookup"><span data-stu-id="83a3d-111">Debuggers also communicate with target hardware through In-Circuit Emulation (ICE) connections.</span></span> <span data-ttu-id="83a3d-112">Подключения OCD и ICE обеспечивают надежную передачу данных с минимальным влиянием на резидентное ПО на целевом объекте.</span><span class="sxs-lookup"><span data-stu-id="83a3d-112">Both OCD and ICE connections provide robust solutions with minimal intrusion on the target resident software.</span></span>

<span data-ttu-id="83a3d-113">Как и в случае с ресурсами, используемыми на главном компьютере, исходный код для ThreadX предоставляется в формате ASCII и требует около 1 МБ свободного пространства на жестком диске главного компьютера.</span><span class="sxs-lookup"><span data-stu-id="83a3d-113">As for resources used on the host, the source code for ThreadX is delivered in ASCII format and requires approximately 1 MByte of space on the host computer's hard disk.</span></span>

## <a name="target-considerations"></a><span data-ttu-id="83a3d-114">Замечания, касающиеся целевого оборудования</span><span class="sxs-lookup"><span data-stu-id="83a3d-114">Target Considerations</span></span>

<span data-ttu-id="83a3d-115">ThreadX требует от 2 до 20 КБ доступной только для чтения памяти в целевой системе.</span><span class="sxs-lookup"><span data-stu-id="83a3d-115">ThreadX requires between 2 KBytes and 20 KBytes of Read Only Memory (ROM) on the target.</span></span> <span data-ttu-id="83a3d-116">Кроме того, в целевой системе нужно 1–2 КБ оперативной памяти (ОЗУ) для системного стека ThreadX и других глобальных структур данных.</span><span class="sxs-lookup"><span data-stu-id="83a3d-116">It also requires another 1 to 2 KBytes of the target's Random Access Memory (RAM) for the ThreadX system stack and other global data structures.</span></span>

<span data-ttu-id="83a3d-117">Для использования функций, связанных с таймером, таких как время ожидания при вызовах службы, временной срез и таймеры приложений, базовое целевое оборудование должно предоставлять источник периодических прерываний.</span><span class="sxs-lookup"><span data-stu-id="83a3d-117">For timer-related functions like service call time-outs, time-slicing, and application timers to function, the underlying target hardware must provide a periodic interrupt source.</span></span> <span data-ttu-id="83a3d-118">Если процессор поддерживает такую возможность, ThreadX использует ее.</span><span class="sxs-lookup"><span data-stu-id="83a3d-118">If the processor has this capability, it is utilized by ThreadX.</span></span> <span data-ttu-id="83a3d-119">В противном случае, когда у целевого процессора нет возможности создавать периодические прерывания, их должно обеспечивать оборудование пользователя.</span><span class="sxs-lookup"><span data-stu-id="83a3d-119">Otherwise, if the target processor does not have the ability to generate a periodic interrupt, the user's hardware must provide it.</span></span> <span data-ttu-id="83a3d-120">Установка и настройка прерываний по таймеру обычно выполняется в файле сборки ***tx_initialize_low_level*** из дистрибутива ThreadX.</span><span class="sxs-lookup"><span data-stu-id="83a3d-120">Setup and configuration of the timer interrupt is typically located in the ***tx_initialize_low_level*** assembly file in the ThreadX distribution.</span></span>

> [!NOTE]
> <span data-ttu-id="83a3d-121">*ThreadX будет нормально работать и без источника периодических прерываний, но вы не сможете использовать службы, связанные с таймером.*</span><span class="sxs-lookup"><span data-stu-id="83a3d-121">*ThreadX is still functional even if no periodic timer interrupt source is available. However, none of the timer-related services are functional.*</span></span>

## <a name="product-distribution"></a><span data-ttu-id="83a3d-122">Распространение продукта</span><span class="sxs-lookup"><span data-stu-id="83a3d-122">Product Distribution</span></span>

<span data-ttu-id="83a3d-123">ThreadX для ОСРВ Azure можно получить из нашего общедоступного репозитория исходного кода, расположенного по адресу <https://github.com/azure-rtos/threadx/>.</span><span class="sxs-lookup"><span data-stu-id="83a3d-123">Azure RTOS ThreadX can be obtained from our public source code repository at <https://github.com/azure-rtos/threadx/>.</span></span>

<span data-ttu-id="83a3d-124">Ниже приведен список основных файлов в этом репозитории.</span><span class="sxs-lookup"><span data-stu-id="83a3d-124">The following is a list of several important files in the repository.</span></span>

| <span data-ttu-id="83a3d-125">Имя файла</span><span class="sxs-lookup"><span data-stu-id="83a3d-125">Filename</span></span> | <span data-ttu-id="83a3d-126">Описание</span><span class="sxs-lookup"><span data-stu-id="83a3d-126">Description</span></span> |
|------------------- | ----------- |
| <span data-ttu-id="83a3d-127">**tx_api.h**</span><span class="sxs-lookup"><span data-stu-id="83a3d-127">**tx_api.h**</span></span>                      | <span data-ttu-id="83a3d-128">Файл заголовка на C включает все системные равенства, структуры данных и прототипы служб.</span><span class="sxs-lookup"><span data-stu-id="83a3d-128">C header file containing all system equates, data structures, and service prototypes.</span></span>                                                             |
| <span data-ttu-id="83a3d-129">**tx_port.h**</span><span class="sxs-lookup"><span data-stu-id="83a3d-129">**tx_port.h**</span></span>                     | <span data-ttu-id="83a3d-130">Файл заголовка на C включает все определения и структуры данных для средств разработки и целевой системы.</span><span class="sxs-lookup"><span data-stu-id="83a3d-130">C header file containing all development-tool and targetspecific data definitions and structures.</span></span>                                                 |
| <span data-ttu-id="83a3d-131">**demo_threadx.c**</span><span class="sxs-lookup"><span data-stu-id="83a3d-131">**demo_threadx.c**</span></span>                | <span data-ttu-id="83a3d-132">Файл на C содержит небольшое демонстрационное приложение.</span><span class="sxs-lookup"><span data-stu-id="83a3d-132">C file containing a small demo application.</span></span>                                                                                                       |
| <span data-ttu-id="83a3d-133">**tx.a (или tx.lib)**</span><span class="sxs-lookup"><span data-stu-id="83a3d-133">**tx.a (or tx.lib)**</span></span>              | <span data-ttu-id="83a3d-134">Двоичная версия библиотеки ThreadX для C, распространяемая со *стандартным* пакетом.</span><span class="sxs-lookup"><span data-stu-id="83a3d-134">Binary version of the ThreadX C library that is distributed with the *standard* package.</span></span>                                                          |
|                                   |                                                                                                                                                   |

>[!NOTE]
><span data-ttu-id="83a3d-135">*Все имена файлов содержат только буквы нижнего регистра. Это соглашение об именовании упрощает преобразование команд для использования на платформах разработки в среде Linux (UNIX).*</span><span class="sxs-lookup"><span data-stu-id="83a3d-135">*All file names are in lower-case. This naming convention makes it easier to convert the commands to Linux (Unix) development platforms.*</span></span>

## <a name="threadx-installation"></a><span data-ttu-id="83a3d-136">Установка ThreadX</span><span class="sxs-lookup"><span data-stu-id="83a3d-136">ThreadX Installation</span></span>

<span data-ttu-id="83a3d-137">ThreadX устанавливается путем клонирования репозитория GitHub на локальный компьютер.</span><span class="sxs-lookup"><span data-stu-id="83a3d-137">ThreadX is installed by cloning the GitHub repository to your local machine.</span></span> <span data-ttu-id="83a3d-138">Ниже приведен типичный синтаксис для создания клона репозитория ThreadX на локальном компьютере:</span><span class="sxs-lookup"><span data-stu-id="83a3d-138">The following is typical syntax for creating a clone of the ThreadX repository on your PC.</span></span>

```c
    git clone https://github.com/azure-rtos/threadx
```

<span data-ttu-id="83a3d-139">Также вы можете скачать копию репозитория с помощью соответствующей кнопки на главной странице GitHub.</span><span class="sxs-lookup"><span data-stu-id="83a3d-139">Alternatively you can download a copy of the repository using the download button on the GitHub main page.</span></span>

<span data-ttu-id="83a3d-140">Кроме того, вы можете найти инструкции по созданию библиотеки ThreadX на главной странице онлайн-репозитория.</span><span class="sxs-lookup"><span data-stu-id="83a3d-140">You will also find instructions for building the ThreadX library on the front page of the online repository.</span></span>

> [!NOTE]
> <span data-ttu-id="83a3d-141">* Программному обеспечению требуется доступ к файлу библиотеки ThreadX (обычно это **tx.a** или **tx.lib**) и к включаемым файлам на C **_tx_api.h_* _ и _*_tx_port.h_*_.</span><span class="sxs-lookup"><span data-stu-id="83a3d-141">*Application software needs access to the ThreadX library file (usually **tx.a** or **tx.lib**) and the C include files **_tx_api.h_* _ and _*_tx_port.h_*_.</span></span> <span data-ttu-id="83a3d-142">Для этого задайте путь к файлам в средствах разработки или скопируйте файлы в область разработки приложения.</span><span class="sxs-lookup"><span data-stu-id="83a3d-142">This is accomplished either by setting the appropriate path for the development tools or by copying these files into the application development area._</span></span>

## <a name="using-threadx"></a><span data-ttu-id="83a3d-143">Использование ThreadX</span><span class="sxs-lookup"><span data-stu-id="83a3d-143">Using ThreadX</span></span>

<span data-ttu-id="83a3d-144">Чтобы использовать ThreadX, код приложения должен включить файл ***tx_api.h** _ во время компиляции и выполнить связывание с библиотекой ThreadX времени выполнения (_*_tx.a_*_ или _*_tx.lib_\*\*).</span><span class="sxs-lookup"><span data-stu-id="83a3d-144">To use ThreadX, the application code must include ***tx_api.h** _ during compilation and link with the ThreadX run-time library _*_tx.a_*_ (or _*_tx.lib_\*\*).</span></span>

<span data-ttu-id="83a3d-145">Для создания приложения ThreadX необходимо выполнить четыре действия.</span><span class="sxs-lookup"><span data-stu-id="83a3d-145">There are four steps required to build a ThreadX application.</span></span>

1. <span data-ttu-id="83a3d-146">Включите файл ***gx_api.h*** во все файлы приложения, которые используют службы или структуры данных ThreadX.</span><span class="sxs-lookup"><span data-stu-id="83a3d-146">Include the ***tx_api.h*** file in all application files that use ThreadX services or data structures.</span></span>

1. <span data-ttu-id="83a3d-147">Создайте стандартную функцию \***main** _ на C.</span><span class="sxs-lookup"><span data-stu-id="83a3d-147">Create the standard C \***main** _ function.</span></span> <span data-ttu-id="83a3d-148">Эта функция должна в конце выполнения вызывать _ *_tx_kernel_enter_*\* для запуска ядра ThreadX.</span><span class="sxs-lookup"><span data-stu-id="83a3d-148">This function must eventually call _ *_tx_kernel_enter_*\* to start ThreadX.</span></span> <span data-ttu-id="83a3d-149">Перед входом в ядро допускается выполнить инициализацию конкретного приложения, которая не имеет отношения к ThreadX.</span><span class="sxs-lookup"><span data-stu-id="83a3d-149">Application-specific initialization that does not involve ThreadX may be added prior to entering the kernel.</span></span>

      > [!IMPORTANT]
      > <span data-ttu-id="83a3d-150">\* Функция \***tx_kernel_enter** _ для входа в ThreadX не выполняет возврат.</span><span class="sxs-lookup"><span data-stu-id="83a3d-150">\*The ThreadX entry function \***tx_kernel_enter** _ does not return.</span></span> <span data-ttu-id="83a3d-151">Поэтому не размещайте после нее никакие вызовы функций и процедуры вычислений.</span><span class="sxs-lookup"><span data-stu-id="83a3d-151">So be sure not to place any processing or function calls after it._</span></span>

1. <span data-ttu-id="83a3d-152">Создайте функцию ***tx_application_define***.</span><span class="sxs-lookup"><span data-stu-id="83a3d-152">Create the ***tx_application_define*** function.</span></span> <span data-ttu-id="83a3d-153">Именно здесь создаются исходные системные ресурсы.</span><span class="sxs-lookup"><span data-stu-id="83a3d-153">This is where the initial system resources are created.</span></span> <span data-ttu-id="83a3d-154">К таким системным ресурсам могут относиться потоки, очереди, пулы памяти, группы флагов событий, мьютексы и семафоры.</span><span class="sxs-lookup"><span data-stu-id="83a3d-154">Examples of system resources include threads, queues, memory pools, event flags groups, mutexes, and semaphores.</span></span>

1. <span data-ttu-id="83a3d-155">Скомпилируйте исходный код приложения и свяжите его с библиотекой ThreadX времени выполнения (***tx.lib***).</span><span class="sxs-lookup"><span data-stu-id="83a3d-155">Compile application source and link with the ThreadX run-time library ***tx.lib***.</span></span> <span data-ttu-id="83a3d-156">Полученный образ можно скачать в целевую систему и запустить.</span><span class="sxs-lookup"><span data-stu-id="83a3d-156">The resulting image can be downloaded to the target and executed!</span></span>

## <a name="small-example-system"></a><span data-ttu-id="83a3d-157">Пример небольшой системы</span><span class="sxs-lookup"><span data-stu-id="83a3d-157">Small Example System</span></span>

<span data-ttu-id="83a3d-158">В этом примере небольшой системы, который представлен на рис. 1, создается один поток с приоритетом 3.</span><span class="sxs-lookup"><span data-stu-id="83a3d-158">The small example system in Figure 1 shows the creation of a single thread with a priority of 3.</span></span> <span data-ttu-id="83a3d-159">Этот поток выполняется и увеличивает значение счетчика, а затем переходит в спящий режим и остается в нем в течение такта длительностью в один час.</span><span class="sxs-lookup"><span data-stu-id="83a3d-159">The thread executes, increments a counter, then sleeps for one clock tick.</span></span>
<span data-ttu-id="83a3d-160">Этот процесс повторяется неограниченно долго.</span><span class="sxs-lookup"><span data-stu-id="83a3d-160">This process continues forever.</span></span>

```c
#include "tx_api.h"
unsigned long my_thread_counter = 0;
TX_THREAD my_thread;
main( )
{
    /* Enter the ThreadX kernel. */
    tx_kernel_enter( );
}
void tx_application_define(void *first_unused_memory)
{
    /* Create my_thread! */
    tx_thread_create(&my_thread, "My Thread",
    my_thread_entry, 0x1234, first_unused_memory, 1024,
    3, 3, TX_NO_TIME_SLICE, TX_AUTO_START);
}
void my_thread_entry(ULONG thread_input)
{
    /* Enter into a forever loop. */
    while(1)
    {
        /* Increment thread counter. */
        my_thread_counter++;
        /* Sleep for 1 tick. */
        tx_thread_sleep(1);
    }
}
```

<span data-ttu-id="83a3d-161">**РИС. 1. Шаблон для разработки приложения**</span><span class="sxs-lookup"><span data-stu-id="83a3d-161">**FIGURE 1. Template for Application Development**</span></span>

<span data-ttu-id="83a3d-162">Это очень простой пример, но он предоставляет хороший шаблон для разработки реальных приложений.</span><span class="sxs-lookup"><span data-stu-id="83a3d-162">Although this is a simple example, it provides a good template for real application development.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="83a3d-163">Устранение неполадок</span><span class="sxs-lookup"><span data-stu-id="83a3d-163">Troubleshooting</span></span>

<span data-ttu-id="83a3d-164">Версии ThreadX для любой системы включают демонстрационное приложение.</span><span class="sxs-lookup"><span data-stu-id="83a3d-164">Each ThreadX port is delivered with a demonstration application.</span></span> <span data-ttu-id="83a3d-165">Мы рекомендуем всегда начинать с запуска этой демонстрационной системы, как на реальном оборудовании, так и в имитированной среде.</span><span class="sxs-lookup"><span data-stu-id="83a3d-165">It is always a good idea to first get the demonstration system running—either on actual target hardware or simulated environment.</span></span>

<span data-ttu-id="83a3d-166">Если демонстрационная система не работает должным образом, воспользуйтесь приведенными ниже советами по устранению неполадок.</span><span class="sxs-lookup"><span data-stu-id="83a3d-166">If the demonstration system does not execute properly, the following are some troubleshooting tips.</span></span>

1. <span data-ttu-id="83a3d-167">Определите, на каком этапе демонстрации возникает ошибка.</span><span class="sxs-lookup"><span data-stu-id="83a3d-167">Determine how much of the demonstration is running.</span></span>
1. <span data-ttu-id="83a3d-168">Увеличьте размеры стека (это с большей вероятностью принесет пользу в фактическом коде приложения, чем в демонстрации).</span><span class="sxs-lookup"><span data-stu-id="83a3d-168">Increase stack sizes (this is more important in actual application code than it is for the demonstration).</span></span>
1. <span data-ttu-id="83a3d-169">Перестройте библиотеку ThreadX, определив параметр TX_ENABLE_STACK_CHECKING.</span><span class="sxs-lookup"><span data-stu-id="83a3d-169">Rebuild the ThreadX library with TX_ENABLE_STACK_CHECKING defined.</span></span> <span data-ttu-id="83a3d-170">Это позволит активировать встроенную проверку стека ThreadX.</span><span class="sxs-lookup"><span data-stu-id="83a3d-170">This enables the built-in ThreadX stack checking.</span></span>
1. <span data-ttu-id="83a3d-171">Временно отключите все недавно внесенные изменения и проверьте, сохраняется ли проблема и изменяется ли ее проявление.</span><span class="sxs-lookup"><span data-stu-id="83a3d-171">Temporarily bypass any recent changes to see if the problem disappears or changes.</span></span> <span data-ttu-id="83a3d-172">Такая информация будет полезной специалистам поддержки.</span><span class="sxs-lookup"><span data-stu-id="83a3d-172">Such information should prove useful to support engineers.</span></span>

<span data-ttu-id="83a3d-173">Выполните инструкции, приведенные в разделе [Центр поддержки клиентов](about-this-guide.md#customer-support-center), чтобы отправить сведения, собранные на этапах устранения неполадок.</span><span class="sxs-lookup"><span data-stu-id="83a3d-173">Follow the procedures outlined in "[Customer Support Center](about-this-guide.md#customer-support-center)" to send the information gathered from the troubleshooting steps.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="83a3d-174">Параметры конфигурации</span><span class="sxs-lookup"><span data-stu-id="83a3d-174">Configuration Options</span></span>

<span data-ttu-id="83a3d-175">При сборке библиотеки ThreadX и приложения, использующего ThreadX, можно применить несколько параметров конфигурации.</span><span class="sxs-lookup"><span data-stu-id="83a3d-175">There are several configuration options when building the ThreadX library and the application using ThreadX.</span></span> <span data-ttu-id="83a3d-176">Указанные ниже параметры можно определить в исходном коде приложения, в командной строке или во включаемом файле ***tx_user. h***.</span><span class="sxs-lookup"><span data-stu-id="83a3d-176">The options below can be defined in the application source, on the command line, or within the ***tx_user.h*** include file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="83a3d-177">\* Параметры, определенные в файле \***tx_user.h** _, применяются только в случае сборки библиотеки ThreadX с определенным параметром _ *TX_INCLUDE_USER_DEFINE_FILE\*\*.*</span><span class="sxs-lookup"><span data-stu-id="83a3d-177">*Options defined in ***tx_user.h** _ are applied only if the application and ThreadX library are built with _ *TX_INCLUDE_USER_DEFINE_FILE** defined.*</span></span>

### <a name="smallest-configuration"></a><span data-ttu-id="83a3d-178">Наименьшая конфигурация</span><span class="sxs-lookup"><span data-stu-id="83a3d-178">Smallest Configuration</span></span>

<span data-ttu-id="83a3d-179">Чтобы получить код наименьшего размера, попробуйте применить следующие параметры конфигурации ThreadX (без всех остальных параметров):</span><span class="sxs-lookup"><span data-stu-id="83a3d-179">For the smallest code size, the following ThreadX configuration options should be considered (in absence of all other options).</span></span>

```c
TX_DISABLE_ERROR_CHECKING
TX_DISABLE_PREEMPTION_THRESHOLD
TX_DISABLE_NOTIFY_CALLBACKS
TX_DISABLE_REDUNDANT_CLEARING
TX_DISABLE_STACK_FILLING
TX_NOT_INTERRUPTABLE
TX_TIMER_PROCESS_IN_ISR
```

### <a name="fastest-configuration"></a><span data-ttu-id="83a3d-180">Самая быстрая конфигурация</span><span class="sxs-lookup"><span data-stu-id="83a3d-180">Fastest Configuration</span></span>

<span data-ttu-id="83a3d-181">Чтобы добиться наиболее быстрого выполнения, используйте те же параметры, что и для минимальной конфигурации, но с возможным добавлением следующих параметров:</span><span class="sxs-lookup"><span data-stu-id="83a3d-181">For the fastest execution, the same configuration options used for the Smallest Configuration previously, but with these options also considered.</span></span>

```c
TX_REACTIVATE_INLINE
TX_INLINE_THREAD_RESUME_SUSPEND
```

<span data-ttu-id="83a3d-182">Изучите также раздел [Подробное описание параметров конфигурации](#detailed-configuration-options).</span><span class="sxs-lookup"><span data-stu-id="83a3d-182">[Detailed configuration options](#detailed-configuration-options) are described.</span></span>

### <a name="global-time-source"></a><span data-ttu-id="83a3d-183">Глобальный источник времени</span><span class="sxs-lookup"><span data-stu-id="83a3d-183">Global Time Source</span></span>

<span data-ttu-id="83a3d-184">Для других продуктов ОСРВ Microsoft Azure (FileX, NetX, GUIX,USBX и т. д.) ThreadX вычисляет количество тактов таймера ThreadX, которое соответствует одной секунде.</span><span class="sxs-lookup"><span data-stu-id="83a3d-184">For other Microsoft Azure RTOS products (FileX, NetX, GUIX, USBX, etc.), ThreadX defines the number of ThreadX timer ticks that represents one second.</span></span> <span data-ttu-id="83a3d-185">Остальные службы определяют свои требования к времени на основе этой константы.</span><span class="sxs-lookup"><span data-stu-id="83a3d-185">Others derive their time requirements based on this constant.</span></span> <span data-ttu-id="83a3d-186">По умолчанию используется значение 100, то есть одно прерывание каждые 10 мс.</span><span class="sxs-lookup"><span data-stu-id="83a3d-186">By default, the value is 100, assuming a 10ms periodic interrupt.</span></span> <span data-ttu-id="83a3d-187">Пользователь может переопределить это значение, указав нужное значение параметра TX_TIMER_TICKS_PER_SECOND в файле ***tx_port.h***, в интегрированной среде разработки или в командной строке.</span><span class="sxs-lookup"><span data-stu-id="83a3d-187">The user may override this value by defining TX_TIMER_TICKS_PER_SECOND with the desired value in ***tx_port.h*** or within the IDE or command line.</span></span>

### <a name="detailed-configuration-options"></a><span data-ttu-id="83a3d-188">Подробное описание параметров конфигурации</span><span class="sxs-lookup"><span data-stu-id="83a3d-188">Detailed Configuration Options</span></span>

<span data-ttu-id="83a3d-189">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="83a3d-189">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="83a3d-190">Если этот параметр определен, включается сбор сведений о производительности для пулов байтов.</span><span class="sxs-lookup"><span data-stu-id="83a3d-190">When defined, this option enables the gathering of performance information on byte pools.</span></span> <span data-ttu-id="83a3d-191">По умолчанию этот параметр не определен.</span><span class="sxs-lookup"><span data-stu-id="83a3d-191">By default, this option is not defined.</span></span>

<span data-ttu-id="83a3d-192">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="83a3d-192">**TX_BYTE_POOL_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="83a3d-193">Если этот параметр определен, включается сбор сведений о производительности для пулов байтов.</span><span class="sxs-lookup"><span data-stu-id="83a3d-193">When defined, this option enables the gathering of performance information on byte pools.</span></span> <span data-ttu-id="83a3d-194">По умолчанию этот параметр не определен.</span><span class="sxs-lookup"><span data-stu-id="83a3d-194">By default, this option is not defined.</span></span>

<span data-ttu-id="83a3d-195">**TX_DISABLE_ERROR_CHECKING**</span><span class="sxs-lookup"><span data-stu-id="83a3d-195">**TX_DISABLE_ERROR_CHECKING**</span></span>

<span data-ttu-id="83a3d-196">Пропуск базовой проверки на предмет ошибок при вызове службы.</span><span class="sxs-lookup"><span data-stu-id="83a3d-196">Bypasses basic service call error checking.</span></span> <span data-ttu-id="83a3d-197">Если этот параметр определен в исходном коде приложения, отключаются все базовые проверки на предмет ошибок в параметрах.</span><span class="sxs-lookup"><span data-stu-id="83a3d-197">When defined in the application source, all basic parameter error checking is disabled.</span></span> <span data-ttu-id="83a3d-198">Это может повысить производительность на 30 % и уменьшить размер образа.</span><span class="sxs-lookup"><span data-stu-id="83a3d-198">This may improve performance by as much as 30% and may also reduce the image size.</span></span>

> [!NOTE]
> <span data-ttu-id="83a3d-199">*Проверку на предмет ошибок можно отключать, только если приложение полностью гарантирует допустимые значения всех входных параметров в любых обстоятельствах, в том числе для параметров, полученных из внешних источников. Если проверку на предмет ошибок отключить и в API будут переданы недопустимые входные данные, поведение системы будет неопределенным и может привести к повреждению памяти или аварийному завершению.*</span><span class="sxs-lookup"><span data-stu-id="83a3d-199">*It is only safe to disable error checking if the application can absolutely guarantee all input parameters are always valid under all circumstances, including input parameters derived from external input. If invalid input is supplied to the API with error checking disabled, the resulting behavior is undefined and could result in memory corruption or system crash.*</span></span>

> [!NOTE]
> <span data-ttu-id="83a3d-200">*Возвращаемые из API ThreadX значения, на которые не влияет отключение проверки на предмет ошибок, выделены полужирным шрифтом в разделе Return Values (Возвращаемые значения) в описании каждого API в главе 4. Возвращаемые значения, не выделенные полужирным шрифтом, всегда будут пустыми, если проверка на предмет ошибок отключена (при заданном параметре TX_DISABLE_ERROR_CHECKING).*</span><span class="sxs-lookup"><span data-stu-id="83a3d-200">*ThreadX API return values not affected by disabling error checking are listed in bold in the “Return Values” section of each API description in Chapter 4. The nonbold return values are void if error checking is disabled by using the TX_DISABLE_ERROR_CHECKING option.*</span></span>

<span data-ttu-id="83a3d-201">**TX_DISABLE_NOTIFY_CALLBACKS**</span><span class="sxs-lookup"><span data-stu-id="83a3d-201">**TX_DISABLE_NOTIFY_CALLBACKS**</span></span>

<span data-ttu-id="83a3d-202">Если этот параметр определен, обратные вызовы оповещения для разных объектов ThreadX отключаются.</span><span class="sxs-lookup"><span data-stu-id="83a3d-202">When defined, disables the notify callbacks for various ThreadX objects.</span></span> <span data-ttu-id="83a3d-203">Использование этого параметра немного сокращает размер кода и повышает производительность.</span><span class="sxs-lookup"><span data-stu-id="83a3d-203">Using this option slightly reduces code size and improves performance.</span></span> <span data-ttu-id="83a3d-204">По умолчанию этот параметр не определен.</span><span class="sxs-lookup"><span data-stu-id="83a3d-204">By default, this option is not defined.</span></span>

<span data-ttu-id="83a3d-205">**TX_DISABLE_PREEMPTION_THRESHOLD**</span><span class="sxs-lookup"><span data-stu-id="83a3d-205">**TX_DISABLE_PREEMPTION_THRESHOLD**</span></span>

<span data-ttu-id="83a3d-206">Если этот параметр определен, отключается функция проверки порога вытеснения, что немного уменьшает размер кода и повышает производительность.</span><span class="sxs-lookup"><span data-stu-id="83a3d-206">When defined, disables the preemption-threshold feature and slightly reduces code size and improves performance.</span></span> <span data-ttu-id="83a3d-207">Разумеется, при этом становится недоступной проверка порога вытеснения.</span><span class="sxs-lookup"><span data-stu-id="83a3d-207">Of course, the preemption-threshold capabilities are no longer available.</span></span> <span data-ttu-id="83a3d-208">По умолчанию этот параметр не определен.</span><span class="sxs-lookup"><span data-stu-id="83a3d-208">By default, this option is not defined.</span></span>

<span data-ttu-id="83a3d-209">**TX_DISABLE_REDUNDANT_CLEARING**</span><span class="sxs-lookup"><span data-stu-id="83a3d-209">**TX_DISABLE_REDUNDANT_CLEARING**</span></span>

<span data-ttu-id="83a3d-210">Если этот параметр определен, удаляется логика инициализации с обнулением для глобальных структур данных C среды ThreadX.</span><span class="sxs-lookup"><span data-stu-id="83a3d-210">When defined, removes the logic for initializing ThreadX global C data structures to zero.</span></span> <span data-ttu-id="83a3d-211">Этот параметр следует использовать, только если код инициализации компилятора устанавливает значение 0 для всех неинициализированных глобальных данных C.</span><span class="sxs-lookup"><span data-stu-id="83a3d-211">This should only be used if the compiler's initialization code sets all un-initialized C global data to zero.</span></span> <span data-ttu-id="83a3d-212">При использовании этого параметра немного сокращается размер кода и повышается производительность на этапе инициализации.</span><span class="sxs-lookup"><span data-stu-id="83a3d-212">Using this option slightly reduces code size and improves performance during initialization.</span></span> <span data-ttu-id="83a3d-213">По умолчанию этот параметр не определен.</span><span class="sxs-lookup"><span data-stu-id="83a3d-213">By default, this option is not defined.</span></span>

<span data-ttu-id="83a3d-214">**TX_DISABLE_STACK_FILLING**</span><span class="sxs-lookup"><span data-stu-id="83a3d-214">**TX_DISABLE_STACK_FILLING**</span></span>

<span data-ttu-id="83a3d-215">Если этот параметр определен, отключается присвоение значения 0xEF каждому байту стека каждого потока при его создании.</span><span class="sxs-lookup"><span data-stu-id="83a3d-215">When defined, disables placing the 0xEF value in each byte of each thread's stack when created.</span></span> <span data-ttu-id="83a3d-216">По умолчанию этот параметр не определен.</span><span class="sxs-lookup"><span data-stu-id="83a3d-216">By default, this option is not defined.</span></span>

<span data-ttu-id="83a3d-217">**TX_ENABLE_EVENT_TRACE**</span><span class="sxs-lookup"><span data-stu-id="83a3d-217">**TX_ENABLE_EVENT_TRACE**</span></span>

<span data-ttu-id="83a3d-218">Если этот параметр определен, ThreadX включает код сбора событий для создания буфера трассировки ThreadX.</span><span class="sxs-lookup"><span data-stu-id="83a3d-218">When defined, ThreadX enables the event gathering code for creating a TraceX trace buffer.</span></span>

<span data-ttu-id="83a3d-219">**TX_ENABLE_STACK_CHECKING**</span><span class="sxs-lookup"><span data-stu-id="83a3d-219">**TX_ENABLE_STACK_CHECKING**</span></span>

<span data-ttu-id="83a3d-220">Если этот параметр определен, включается проверка стека времени выполнения ThreadX, в которую входит анализ объема использованного стека и изучение "ограждений" шаблона данных до и после области стека.</span><span class="sxs-lookup"><span data-stu-id="83a3d-220">When defined, enables ThreadX run-time stack checking, which includes analysis of how much stack has been used and examination of data pattern "fences" before and after the stack area.</span></span> <span data-ttu-id="83a3d-221">При обнаружении ошибки стека вызывается зарегистрированный обработчик ошибок стека приложений.</span><span class="sxs-lookup"><span data-stu-id="83a3d-221">If a stack error is detected, the registered application stack error handler is called.</span></span> <span data-ttu-id="83a3d-222">При использовании этого параметра немного увеличиваются затраты времени и размер кода.</span><span class="sxs-lookup"><span data-stu-id="83a3d-222">This option does result in slightly increased overhead and code size.</span></span> <span data-ttu-id="83a3d-223">Дополнительные сведения см. в описании функции API ***tx_thread_stack_error_notify***.</span><span class="sxs-lookup"><span data-stu-id="83a3d-223">Review the ***tx_thread_stack_error_notify*** API function for more information.</span></span> <span data-ttu-id="83a3d-224">По умолчанию этот параметр не определен.</span><span class="sxs-lookup"><span data-stu-id="83a3d-224">By default, this option is not defined.</span></span>

<span data-ttu-id="83a3d-225">**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="83a3d-225">**TX_EVENT_FLAGS_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="83a3d-226">Если этот параметр определен, включается сбор сведений о производительности для групп флагов событий.</span><span class="sxs-lookup"><span data-stu-id="83a3d-226">When defined, enables the gathering of performance information on event flags groups.</span></span> <span data-ttu-id="83a3d-227">По умолчанию этот параметр не определен.</span><span class="sxs-lookup"><span data-stu-id="83a3d-227">By default, this option is not defined.</span></span>

<span data-ttu-id="83a3d-228">**TX_INLINE_THREAD_RESUME_SUSPEND**</span><span class="sxs-lookup"><span data-stu-id="83a3d-228">**TX_INLINE_THREAD_RESUME_SUSPEND**</span></span>

<span data-ttu-id="83a3d-229">Если этот параметр определен, ThreadX улучшает вызовы API ***tx_thread_resume** _ и _ *_tx_thread_suspend_** путем применения встроенного кода.</span><span class="sxs-lookup"><span data-stu-id="83a3d-229">When defined, ThreadX improves the ***tx_thread_resume** _ and _ *_tx_thread_suspend_** API calls via in-line code.</span></span> <span data-ttu-id="83a3d-230">Это увеличивает размер кода, но повышает производительность для этих двух вызовов API.</span><span class="sxs-lookup"><span data-stu-id="83a3d-230">This increases code size but enhances performance of these two API calls.</span></span>

<span data-ttu-id="83a3d-231">**TX_MAX_PRIORITIES**</span><span class="sxs-lookup"><span data-stu-id="83a3d-231">**TX_MAX_PRIORITIES**</span></span>

<span data-ttu-id="83a3d-232">Определяет уровни приоритета для ThreadX.</span><span class="sxs-lookup"><span data-stu-id="83a3d-232">Defines the priority levels for ThreadX.</span></span> <span data-ttu-id="83a3d-233">Допускаются значения в диапазоне от 32 до 1024 (включительно), но *строго* кратные 32.</span><span class="sxs-lookup"><span data-stu-id="83a3d-233">Legal values range from 32 through 1024 (inclusive) and *must* be evenly divisible by 32.</span></span> <span data-ttu-id="83a3d-234">При увеличении числа поддерживаемых уровней приоритета увеличивается объем использования ОЗУ на 128 байт для каждой группы из 32 уровней приоритета.</span><span class="sxs-lookup"><span data-stu-id="83a3d-234">Increasing the number of priority levels supported increases the RAM usage by 128 bytes for every group of 32 priorities.</span></span> <span data-ttu-id="83a3d-235">Но это оказывает крайне несущественное влияние на производительность.</span><span class="sxs-lookup"><span data-stu-id="83a3d-235">However, there is only a negligible effect on performance.</span></span> <span data-ttu-id="83a3d-236">По умолчанию используются 32 уровня приоритета.</span><span class="sxs-lookup"><span data-stu-id="83a3d-236">By default, this value is set to 32 priority levels.</span></span>

<span data-ttu-id="83a3d-237">**TX_MINIMUM_STACK**</span><span class="sxs-lookup"><span data-stu-id="83a3d-237">**TX_MINIMUM_STACK**</span></span>

<span data-ttu-id="83a3d-238">Определяет минимальный размер стека (в байтах).</span><span class="sxs-lookup"><span data-stu-id="83a3d-238">Defines the minimum stack size (in bytes).</span></span> <span data-ttu-id="83a3d-239">Он используется для проверки на предмет ошибок при создании потоков.</span><span class="sxs-lookup"><span data-stu-id="83a3d-239">It is used for error checking when threads are created.</span></span> <span data-ttu-id="83a3d-240">Значение по умолчанию зависит от конкретной версии и определяется в файле ***tx_port.h***.</span><span class="sxs-lookup"><span data-stu-id="83a3d-240">The default value is port-specific and is found in ***tx_port.h***.</span></span>

<span data-ttu-id="83a3d-241">**TX_MISRA_ENABLE**</span><span class="sxs-lookup"><span data-stu-id="83a3d-241">**TX_MISRA_ENABLE**</span></span>

<span data-ttu-id="83a3d-242">Если этот параметр определен, ThreadX использует соглашения, совместимые с MISRA C.</span><span class="sxs-lookup"><span data-stu-id="83a3d-242">When defined, ThreadX utilizes MISRA C compliant conventions.</span></span> <span data-ttu-id="83a3d-243">Дополнительные сведения см. в файле ***ThreadX_MISRA_Compliance.pdf***.</span><span class="sxs-lookup"><span data-stu-id="83a3d-243">Refer to  ***ThreadX_MISRA_Compliance.pdf*** for details.</span></span>

<span data-ttu-id="83a3d-244">**TX_MUTEX_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="83a3d-244">**TX_MUTEX_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="83a3d-245">Если этот параметр определен, включается сбор сведений о производительности для мьютексов.</span><span class="sxs-lookup"><span data-stu-id="83a3d-245">When defined, enables the gathering of performance information on mutexes.</span></span> <span data-ttu-id="83a3d-246">По умолчанию этот параметр не определен.</span><span class="sxs-lookup"><span data-stu-id="83a3d-246">By default, this option is not defined.</span></span>

<span data-ttu-id="83a3d-247">**TX_NO_TIMER**</span><span class="sxs-lookup"><span data-stu-id="83a3d-247">**TX_NO_TIMER**</span></span>

<span data-ttu-id="83a3d-248">Если этот параметр определен, полностью отключается логика таймера ThreadX.</span><span class="sxs-lookup"><span data-stu-id="83a3d-248">When defined, the ThreadX timer logic is completely disabled.</span></span> <span data-ttu-id="83a3d-249">Это полезно в тех случаях, когда функции таймера ThreadX не используются (режим сна для потока, время ожидания ответов API, временной срез или таймеры приложений).</span><span class="sxs-lookup"><span data-stu-id="83a3d-249">This is useful in cases where the ThreadX timer features (thread sleep, API timeouts, time-slicing, and application timers) are not utilized.</span></span> <span data-ttu-id="83a3d-250">Если определен параметр **TX_NO_TIMER**, необходимо определить и параметр **TX_TIMER_PROCESS_IN_ISR**.</span><span class="sxs-lookup"><span data-stu-id="83a3d-250">If **TX_NO_TIMER** is specified, the option **TX_TIMER_PROCESS_IN_ISR** must also be defined.</span></span>

<span data-ttu-id="83a3d-251">**TX_NOT_INTERRUPTABLE**</span><span class="sxs-lookup"><span data-stu-id="83a3d-251">**TX_NOT_INTERRUPTABLE**</span></span>

<span data-ttu-id="83a3d-252">Если этот параметр определен, ThreadX не пытается сокращать время блокировки прерываний.</span><span class="sxs-lookup"><span data-stu-id="83a3d-252">When defined, ThreadX does not attempt to minimize interrupt lockout time.</span></span> <span data-ttu-id="83a3d-253">Это приводит к ускорению выполнения, но немного увеличивает время блокировки прерываний.</span><span class="sxs-lookup"><span data-stu-id="83a3d-253">This results in faster execution but does slightly increase interrupt lockout time.</span></span>

<span data-ttu-id="83a3d-254">**TX_QUEUE_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="83a3d-254">**TX_QUEUE_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="83a3d-255">Если этот параметр определен, включается сбор сведений о производительности для очередей.</span><span class="sxs-lookup"><span data-stu-id="83a3d-255">When defined, enables the gathering of performance information on queues.</span></span> <span data-ttu-id="83a3d-256">По умолчанию этот параметр не определен.</span><span class="sxs-lookup"><span data-stu-id="83a3d-256">By default, this option is not defined.</span></span>

<span data-ttu-id="83a3d-257">**TX_REACTIVATE_INLINE**</span><span class="sxs-lookup"><span data-stu-id="83a3d-257">**TX_REACTIVATE_INLINE**</span></span>

<span data-ttu-id="83a3d-258">Если этот параметр определен, повторная активация встроенных таймеров ThreadX выполняется во встроенном коде, без вызова функции.</span><span class="sxs-lookup"><span data-stu-id="83a3d-258">When defined, performs reactivation of ThreadX timers inline instead of using a function call.</span></span> <span data-ttu-id="83a3d-259">Это повышает производительность, но немного увеличивает размер кода.</span><span class="sxs-lookup"><span data-stu-id="83a3d-259">This improves performance but slightly increases code size.</span></span> <span data-ttu-id="83a3d-260">По умолчанию этот параметр не определен.</span><span class="sxs-lookup"><span data-stu-id="83a3d-260">By default, this option is not defined.</span></span>

<span data-ttu-id="83a3d-261">**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="83a3d-261">**TX_SEMAPHORE_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="83a3d-262">Если этот параметр определен, включается сбор сведений о производительности для семафоров.</span><span class="sxs-lookup"><span data-stu-id="83a3d-262">When defined, enables the gathering of performance information on semaphores.</span></span> <span data-ttu-id="83a3d-263">По умолчанию этот параметр не определен.</span><span class="sxs-lookup"><span data-stu-id="83a3d-263">By default, this option is not defined.</span></span>

<span data-ttu-id="83a3d-264">**TX_THREAD_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="83a3d-264">**TX_THREAD_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="83a3d-265">Если этот параметр определен, включается сбор сведений о производительности для потоков.</span><span class="sxs-lookup"><span data-stu-id="83a3d-265">When defined, enables the gathering of performance information on threads.</span></span> <span data-ttu-id="83a3d-266">По умолчанию этот параметр не определен.</span><span class="sxs-lookup"><span data-stu-id="83a3d-266">By default, this option is not defined.</span></span>

<span data-ttu-id="83a3d-267">**TX_TIMER_ENABLE_PERFORMANCE_INFO**</span><span class="sxs-lookup"><span data-stu-id="83a3d-267">**TX_TIMER_ENABLE_PERFORMANCE_INFO**</span></span>

<span data-ttu-id="83a3d-268">Если этот параметр определен, включается сбор сведений о производительности для таймеров.</span><span class="sxs-lookup"><span data-stu-id="83a3d-268">When defined, enables the gathering of performance information on timers.</span></span> <span data-ttu-id="83a3d-269">По умолчанию этот параметр не определен.</span><span class="sxs-lookup"><span data-stu-id="83a3d-269">By default, this option is not defined.</span></span>

<span data-ttu-id="83a3d-270">**TX_TIMER_PROCESS_IN_ISR**</span><span class="sxs-lookup"><span data-stu-id="83a3d-270">**TX_TIMER_PROCESS_IN_ISR**</span></span>

<span data-ttu-id="83a3d-271">Если этот параметр определен, из ThreadX удаляется внутренний поток системного таймера.</span><span class="sxs-lookup"><span data-stu-id="83a3d-271">When defined, eliminates the internal system timer thread for ThreadX.</span></span> <span data-ttu-id="83a3d-272">Это приводит к повышению производительности событий таймера и уменьшению объема требований к ОЗУ, так как стек таймера и блок управления становятся не нужны.</span><span class="sxs-lookup"><span data-stu-id="83a3d-272">This results in improved performance on timer events and smaller RAM requirements because the timer stack and control block are no longer needed.</span></span> <span data-ttu-id="83a3d-273">Но при использовании этого параметра вся обработка периодов для таймера переносится на уровень таймера ISR.</span><span class="sxs-lookup"><span data-stu-id="83a3d-273">However, using this option moves all the timer expiration processing to the timer ISR level.</span></span> <span data-ttu-id="83a3d-274">По умолчанию этот параметр не определен.</span><span class="sxs-lookup"><span data-stu-id="83a3d-274">By default, this option is not defined.</span></span>

> [!NOTE]
> <span data-ttu-id="83a3d-275">*Службы, разрешенные в таймерах, могут быть запрещены в ISR, а значит, они не смогут работать при использовании этого параметра.*</span><span class="sxs-lookup"><span data-stu-id="83a3d-275">*Services allowed from timers may not be allowed from ISRs and thus might not be allowed when using this option.*</span></span>

<span data-ttu-id="83a3d-276">**TX_TIMER_THREAD_PRIORITY**</span><span class="sxs-lookup"><span data-stu-id="83a3d-276">**TX_TIMER_THREAD_PRIORITY**</span></span>

<span data-ttu-id="83a3d-277">Определяет приоритет для внутреннего потока системного таймера ThreadX.</span><span class="sxs-lookup"><span data-stu-id="83a3d-277">Defines the priority of the internal ThreadX system timer thread.</span></span> <span data-ttu-id="83a3d-278">По умолчанию используется приоритет 0, то есть максимальный возможный приоритет в ThreadX.</span><span class="sxs-lookup"><span data-stu-id="83a3d-278">The default value is priority 0—the highest priority in ThreadX.</span></span> <span data-ttu-id="83a3d-279">Значение по умолчанию определяется в файле ***tx_port.h***.</span><span class="sxs-lookup"><span data-stu-id="83a3d-279">The default value is defined in ***tx_port.h***.</span></span>

<span data-ttu-id="83a3d-280">**TX_TIMER_THREAD_STACK_SIZE**</span><span class="sxs-lookup"><span data-stu-id="83a3d-280">**TX_TIMER_THREAD_STACK_SIZE**</span></span>

<span data-ttu-id="83a3d-281">Определяет размер стека (в байтах) для внутреннего потока системного таймера ThreadX.</span><span class="sxs-lookup"><span data-stu-id="83a3d-281">Defines the stack size (in bytes) of the internal ThreadX system timer thread.</span></span> <span data-ttu-id="83a3d-282">Этот поток обрабатывает все запросы спящего режима и периоды ожидания для вызовов служб.</span><span class="sxs-lookup"><span data-stu-id="83a3d-282">This thread processes all thread sleep requests as well as all service call timeouts.</span></span> <span data-ttu-id="83a3d-283">Кроме того, из этого контекста вызываются все подпрограммы обратного вызова таймера приложений.</span><span class="sxs-lookup"><span data-stu-id="83a3d-283">In addition, all application timer callback routines are invoked from this context.</span></span> <span data-ttu-id="83a3d-284">Значение по умолчанию зависит от конкретной версии и определяется в файле ***tx_port.h***.</span><span class="sxs-lookup"><span data-stu-id="83a3d-284">The default value is port-specific and is found in ***tx_port.h***.</span></span>

## <a name="threadx-version-id"></a><span data-ttu-id="83a3d-285">Идентификатор версии ThreadX</span><span class="sxs-lookup"><span data-stu-id="83a3d-285">ThreadX Version ID</span></span>

<span data-ttu-id="83a3d-286">Программист может получить данные о версии ThreadX, изучив файл \***tx_port.h** _.</span><span class="sxs-lookup"><span data-stu-id="83a3d-286">The programmer can obtain the ThreadX version from examination of the \***tx_port.h** _ file.</span></span> <span data-ttu-id="83a3d-287">Кроме того, этот файл содержит журнал версий для соответствующей платформы.</span><span class="sxs-lookup"><span data-stu-id="83a3d-287">In addition, this file also contains a version history of the corresponding port.</span></span> <span data-ttu-id="83a3d-288">Программное обеспечение приложения может получить сведения о версии ThreadX из глобальной строки _\*_tx_version_id\*\*.</span><span class="sxs-lookup"><span data-stu-id="83a3d-288">Application software can obtain the ThreadX version by examining the global string _\*_tx_version_id\*\*.</span></span>
